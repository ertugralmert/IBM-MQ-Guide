IBM MQ'nun Container Ortamında Sorun Giderilmesi
Genel Bakış
Container ortamında çalışan IBM® MQ uygulamalarında sorunlar yaşıyorsanız, bu dokümandaki teknikler tanılama ve çözüm bulma konusunda yardımcı olabilir.

Container Ortamında IBM MQ'nun Beklenmeyen Yeniden Başlamalarının Sorun Giderilmesi
Çözüm Yöntemleri
Container yönetim sistemlerinde (Red Hat® OpenShift® ve Kubernetes gibi) container'ların tekrar başlatılması olağandır. Ancak, beklenmeyen yeniden başlamaların nedenlerini anlamak için aşağıdaki adımlar izlenebilir.
IBM MQ Container'ına Gönderilen Sinyaller
Container loglarında şu şekilde bir mesaj görebilirsiniz:
Signal received: terminated
Bu, container'ı sonlandırmak için SIGTERM sinyali gönderildiğini belirtir. IBM MQ bu sinyali aldığında, queue manager'ı sonlandırmak için şu komutu çalıştırır:
endmqm -w -r -tp
Queue manager kapandıktan sonra container kapanır. Kapanma için ayrılan süre "termination grace period" olarak adlandırılır ve Kubernetes'de QueueManager veya Pod kaynağının özellikleriyle ayarlanabilir.
Pod'ların Tahliyesi (Eviction) Nedenleri
Pod'lar aşağıdaki nedenlerle tahliye edilebilir:
	1. Kubelet Tarafından Sonlandırma:
		○ Düğümün (Node) kapatılması veya yüksek kaynak kullanımı nedeniyle tahliye.
		○ Liveness probe hatası nedeniyle.
	2. Pod'ların Yeniden Önceliklendirilmesi:
		○ Kubernetes scheduler, daha öncelikli bir Pod'u çalıştırmak için mevcut Pod'ı tahliye edebilir.
	3. Tainted Node:
		○ Düğüm (Node) "taint" ile işaretlenmişse ve Pod bu tainti tolere etmiyorsa tahliye edilir.
Pod Tahliyesinin Nedenini Anlama
Pod'un tahliye edilme nedenlerini anlamak için kullanılabilecek bilgiler:
	• Cluster Olayları: OpenShift veya Kubernetes'in sistem olayları izlenebilir.
	• Düğüm Kaynak Kullanım Durumu: CPU, bellek veya disk kullanımı gibi kaynak baskısı tespit edilebilir.
	• Prometheus Gözlem Araçları: Örneğin, ibmmq_qmgr_log_write_latency_seconds metriği kullanılabilir.

IBM MQ Operatorı ile Sorun Giderme
IBM MQ Operator ile Dağıtılan Queue Manager'ları için Sorun Giderme Bilgisi Toplama
IBM MQ Operator ile dağıtılan queue manager'ı için IBM Destek'e bilgi sağlamak üzere aşağıdaki adımlar uygulanabilir.
Bulut Sağlayıcı ve Mimari Bilgisi Toplama
	• Kullanılan bulut sağlayıcısı (IBM Cloud, AWS, Azure vb.) bilgisi.
	• Red Hat OpenShift cluster'ının mimarisi (x86-64, IBM Z vb.).
IBM MQ Dağıtım Bilgisi Toplama
	1. QueueManager, namespace ve operator namespace bilgilerini ayarlayın:export QM=QueueManager_Adiexport QM_NAMESPACE=QueueManager_Namespaceexport MQ_OPERATOR_NAMESPACE=Operator_Namespace
	2. Aşağıdaki komutları çalıştırın ve çıktı dosyalarını IBM Destek'e sağlayın:oc version -o yaml > ocversion.yamloc get qmgr $QM -n $QM_NAMESPACE -o yaml > queue-manager-$QM.yamloc get pods -n $QM_NAMESPACE -o yaml --selector "app.kubernetes.io/instance=$QM" > qm-pods-$QM.yaml
Pod Loglarını ve Olaylarını Toplama
	1. Pod logları:oc logs Pod_Adi > pod-logs.txt
	2. Pod olayları:oc get events -n $QM_NAMESPACE -o yaml > pod-events.yaml

Persistent Volume Claims (PVC) Üzerinde Verilere Erişim
IBM MQ Operator'ı tarafından dağıtılan bir queue manager'ın PVC dosyalarına erişim için PVC inspector aracı kullanılabilir.
Adımlar
	1. Inspector Aracını İndirin: MQ PVC Tool GitHub
	2. Cluster'ı Giriş Yapın:oc login
	3. Inspector Pod'ı Çalıştırın:./pvc-tool.sh queue_manager_name queue_manager_namespace_name
	4. Dosyalara Erişim:oc rsh pvc-inspector-pod-name
	5. İlgili Pod'ı Temizleyin:oc delete pods -l tool=mq-pvc-inspector

OpenShift Monitoring CLI ile Cluster Sorun Giderme
OpenShift CLI Kullanımı
	1. Monitoring'i Aktifleştirin:
		○ OpenShift Monitoring'in user-defined projeler için aktifleştirilmesi gerekir. Ayrıntılar için OpenShift dokümanlarına bakın.
	2. IBM MQ Metriğini Sorgulayın:export QM_METRIC_NAME=ibmmq_qmgr_log_write_latency_secondsexport PROMQL_QUERY="$QM_METRIC_NAME{namespace=\"$QM_NAMESPACE\"} [5h:10m]"Prometheus metriklerini sorgulamak için:curl -G -s -k -H "Authorization: Bearer $OCP_LOGIN_TOKEN" \--data-urlencode "query=$PROMQL_QUERY" \"https://$THANOS_QUERIER_HOST/api/v1/query_range"

