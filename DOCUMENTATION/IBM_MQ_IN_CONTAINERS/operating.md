IBM MQ'yu Konteynerlerde İşletmek
Genel Bakış
IBM MQ kuyruğ yöneticilerini konteyner ortamlarında çalışırken işletmek ve etkileşim kurmak için bu belge, başlıca özellikleri ve yöntemleri ele almaktadır.

IBM MQ Operatörü ile IBM MQ'nun İşletilmesi
IBM MQ Konsolu İçin Yetkilendirme Verilmesi
IBM MQ Konsolu'na erişim izinleri, lisans türünüe göre farklı şekillerde yönetilir.
Prosedür
	1. Keycloak üzerinden kullanıcıları ve rollerı yapılandırma:
		○ IBM Cloud Pak for Integration lisansı kullanıyorsanız, Keycloak kimlik ve erişim yönetimi için kullanılır.
		○ Keycloak yönetimi ve MQ rolleri ile ilgili ayrıntılar için Cloud Pak for Integration belgelerine bakın.
	2. Manuel olarak kullanıcıları ve rollerı yapılandırma:
		○ IBM MQ lisansı kullanıyorsanız, kullanıcıları ve rollerı kendiniz yapılandırmalısınız.
		○ Temel bir örnek için IBM MQ Konsolu'nu basit bir kayıt defteriyle yapılandırma hakkındaki belgelere bakın.
IBM MQ Konsolu'na Bağlanma
OpenShift platformunda düğümü başlatılan bir kuyruğ yöneticisinin konsoluna erişim adımları aşağıdaki gibidir:
	1. Konsol URL'sini bulma:
		○ OpenShift CLI'de şu komutu çalıştırın:oc get queuemanager QueueManagerName -n namespace --output jsonpath='{.status.adminUiUrl}'
	2. Bağlantıyı kontrol etme:
		○ IBM MQ Konsolu URL'sini tarayıcınızda açın ve kullanıcı bilgilerinizi girin.
IBM MQ Operatörü ile Monitoring
IBM MQ kuyruğ yöneticileri, Prometheus ile uyumlu metrikler üretebilir. Varsayılan olarak kuyruğ yöneticisi metrikleri etkinleştirilmiştir.
Metrikleri Görüntüleme
	1. OpenShift Metrics sekmesini açın.
	2. Observe > Metrics seçeneğine tıklayarak metrikleri görüntüleyin.
Metrikleri Devre Dışı Bırakma
	• YAML dosyasında .spec.metrics.enabled değerini false olarak ayarlayın.
Kuyruğ Yöneticisi Yedekleme ve Geri Yükleme
IBM MQ kuyruğ yöneticisinin tanımlarını yeniden oluşturmak için yedekleme yapmak kritik bir adımdır.
Yedekleme
	1. Pod ismini bulun:oc get pods --selector app.kubernetes.io/name=ibm-mq,app.kubernetes.io/instance=queue_manager_name
	2. dmpmqcfg komutunu kullanarak yedekleme yapın:oc exec -it pod_name -- dmpmqcfg > backup.mqsc
Geri Yükleme
	1. Yedek dosyasını kuyruğ yöneticisine uygulama:oc exec -i pod_name -- runmqsc < backup.mqsc

Native HA Kuyruğ Yöneticilerinin Durumunu Görüntüleme
Genel Bakış
dspmq komutunu kullanarak bir kuyruğ yöneticisinin durumunu kontrol edebilirsiniz. Bu bilgi, aktif veya replika durumuna göre farklılık gösterebilir.
Prosedür
	1. Pod'ları listeleme:oc get pod --selector app.kubernetes.io/instance=nativeha-qm
	2. dspmq komutunu çalıştırma:oc exec -t Pod dspmq
	3. Durum bilgisi kontrolü:
		○ Aktif kuyruğ yöneticisi:QMNAME(BOB) STATUS(Running)
		○ Replika kuyruğ yöneticisi:QMNAME(BOB) STATUS(Replica)

Native HA Kuyruğ Yöneticilerini Sonlandırma
Genel Bakış
endmqm komutunu kullanarak bir Native HA kuyruğ yöneticisinin aktif veya replika durumunu sonlandırabilirsiniz.
Prosedür
	1. Aktif Kuyruğ Yöneticisini Sonlandırma:endmqm -s QMgrName
	2. Replika Kuyruğ Yöneticisini Sonlandırma:endmqm -x QMgrName
Not: endmqm komutunda grup quorum kontrol edilir. Quorum düşerse, komut başarısız olur
