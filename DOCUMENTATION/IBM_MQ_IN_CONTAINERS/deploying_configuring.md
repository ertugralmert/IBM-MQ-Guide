IBM MQ Operatörü Kullanarak Kuyruk Yöneticilerini Dağıtma ve Yapılandırma
Genel Bakış
	• Yapılandırma Örnekleri: Yüksek erişilebilirlik (HA), CP4i dashboard entegrasyonları, Instana izleme, özel MQSC/INI dosyaları.
	• Dış Uygulama Bağlantıları: OpenShift kümesinin dışından TLS kullanarak bağlantı sağlayın.
	• Gelişmiş Ayarlar: Özel etiketler ekleyin, runtime webhook kontrollerini devre dışı bırakın veya IBM MQ Konsolu ve REST API'yi yapılandırın.
Basit Bir Kuyruk Yöneticisi Dağıtma
Bu örnek, geçici depolama (ephemeral storage) kullanan ve güvenliği devre dışı bırakan bir "hızlı başlangıç" kuyruk yöneticisini dağıtmayı gösterir.
Dağıtım Seçenekleri
	1. OpenShift Konsolu Kullanarak
	2. OpenShift CLI Kullanarak
	3. IBM Cloud Pak Entegrasyon Platformu UI Kullanarak
OpenShift Konsolu Kullanımı
	1. Giriş Yapın:
		○ OpenShift konsoluna yöneticilik yetkileriyle giriş yapın.
	2. Namespace Seçin:
		○ IBM MQ Operatörünün kurulu olduğu namespace’i seçin.
	3. Kuyruk Yöneticisi Oluşturun:
		○ Operators > Installed Operators > IBM MQ > Queue Manager yolunu izleyerek Create QueueManager butonuna tıklayın.
	4. Yapılandırma:
		○ Lisansı kabul edin (License accept değerini true yapın).
		○ Geçerli bir lisans değeri sağlayın (detaylar için mq.ibm.com/v1beta1).
	5. Doğrulayın:
		○ QueueManager durumunun Running olduğunu doğrulayın.

Kubernetes Üzerinde Kuyruk Yöneticilerinin Dağıtımı ve Yapılandırılması
Genel Bakış
	• Temel Yapılandırma: Geçici depolama kullanan basit bir kuyruk yöneticisi dağıtın.
	• Gelişmiş Yapılandırma: Yüksek erişilebilirlik (HA) ve Helm şemaları ile yapılandırma.
Örnek: Basit Bir Kuyruk Yöneticisi Dağıtma
	1. Namespace Oluşturun:bashCopy codekubectl create namespace mq-test
	2. YAML Dosyalarını Hazırlayın:
		○ Service:apiVersion: v1kind: Servicemetadata:  name: quickstart-ibm-mqspec:  ports:  - name: qmgr    port: 1414  - name: metrics    port: 9157  selector:    app.kubernetes.io/instance: quickstart  type: ClusterIP
		○ ServiceAccount:apiVersion: v1kind: ServiceAccountmetadata:  name: quickstart-ibm-mq
		○ StatefulSet:apiVersion: apps/v1kind: StatefulSetmetadata:  name: quickstart-ibm-mq  namespace: mq-testspec:  replicas: 1  template:    spec:      containers:      - name: qmgr        image: cp.icr.io/cp/ibm-mqadvanced-server:9.4.1.0-r1        env:        - name: MQ_QMGR_NAME          value: "QUICKSTART"
	3. Kaynakları Dağıtın:kubectl apply -f service.yamlkubectl apply -f serviceaccount.yamlkubectl apply -f statefulset.yaml
	4. Dağıtımı Doğrulayın:kubectl get pods -n mq-test

Podman Üzerinde Kuyruk Yöneticisi Dağıtımı
Genel Bakış
IBM MQ Advanced konteyner görüntüsünü kullanarak Podman'da bir kuyruk yöneticisi dağıtın.
Prosedür
	1. Dosyaları ve Dizinleri Hazırlayın:
		○ Sertifikalar: qm-pki
		○ MQSC Komutları: example-tls.mqsc
		○ INI Dosyası: example-tls.ini
	2. Konteyneri Çalıştırın:podman run --env LICENSE=accept --env MQ_QMGR_NAME=QM1 \  -v "./mqwebuser.xml:/etc/mqm/web/installations/Installation1/servers/mqweb/mqwebuser.xml" \  -v "./example-tls.ini:/etc/mqm/example-tls.ini" \  -v "./example-tls.mqsc:/etc/mqm/example-tls.mqsc" \  -v "./qm-pki:/etc/mqm/pki/keys/qmlabel" \  --publish 1414:1414 --publish 9443:9443 --detach --name QM1 \  cp.icr.io/cp/ibm-mqadvanced-server:9.4.1.0-r1
	3. Doğrulama:
		○ Mesajlaşma:amqsputc EXAMPLE.QUEUE QM1amqsgetc EXAMPLE.QUEUE QM1
		○ Konsol: Tarayıcıda https://localhost:9443/ibmmq/console adresini açın.

Doğrulama ve Sorun Giderme
	• Loglar:
		○ Müşteri Hataları: ~/IBM/MQ/data/errors/AMQERR01.LOG
		○ Kuyruk Yöneticisi Logları: exec komutunu kullanarak konteyner loglarını inceleyin.podman exec -it QM1 /bin/bash
