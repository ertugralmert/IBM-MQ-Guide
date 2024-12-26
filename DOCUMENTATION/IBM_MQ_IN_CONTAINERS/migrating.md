Konteyner Ortamına IBM MQ Kuyruk Yöneticisinin Taşınması
Bu belge, mevcut bir IBM MQ kuyruk yöneticisinin Red Hat OpenShift Container Platform'da IBM MQ Operatörü kullanılarak bir konteyner ortamına taşınması için gereken adımları açıklamaktadır.
Görev Hakkında
IBM MQ'yu OpenShift'te kullanmayı düşñnen müşteriler genellikle aşağıdaki senaryolardan birine dahil olur:
	1. Yeni bir uygulama için OpenShift'te IBM MQ dağıtımı oluşturmak.
	2. IBM MQ ağını OpenShift'e genışletmek.
	3. Mevcut bir IBM MQ dağıtımını OpenShift'e taşımak.
Bu belgenin odaklandığı üçüncü senaryo, mevcut bir IBM MQ kuyruk yöneticisinin OpenShift'e taşınmasıdır.
Veri Taşıma Seçenekleri
	1. Mevcut kuyruklardaki mesajlar olmadan IBM MQ'yu taşımak.
	2. Mevcut mesajlarla birlikte IBM MQ'yu taşımak.
Genellikle mesajların kuyrukta olmadığı durumlar için birinci yöntem kullanılır. Bu yöntem, taşıma sürecini basitleştirir ve "mavi-yeşil" (blue-green) dağıtımına olanak tanır. Bu belge de bu senaryoya odaklanmıştır.
Genel Amaç
Mevcut kuyruk yöneticisinin tanımıyla uyumlu bir kuyruk yöneticisini konteyner ortamında oluşturmak, böylece mevcut uygulamaları yeniden konfigüre ederek bu yeni kuyruk yöneticisine bağlanmasını sağlamaktır.

Gereken Fonksiyonları Kontrol Etme
IBM MQ Operatörü, IBM MQ Advanced'daki tüm özellikleri desteklemez. Bu nedenle, hedef ortamda gereken özelliklerin desteklendiğinden emin olun.
Adımlar
	1. Fonksiyonları Kontrol Edin:
		○ Konteyner görüntüsündeki desteklenen fonksiyonları inceleyin.
		○ Birden fazla dinleyici (listener) tanımı varsa, bunları sadeleştirin ve tek bir dinleyici kullanın.
	2. Yüksek Erişilebilirlik Seçeneklerini Değerlendirin:
		○ Tekil Pod, çoklu Pod veya Native HA gibi mimariler arasından ihtiyacınıza uygun olanı seçin.

Kuyruk Yöneticisi Yapılandırmasını Çıkarma
IBM MQ kuyruk yöneticisindeki çoğu yapılandırma taşınabilir. Örneğin; kuyruklar, başlıklar ve kanallar gibi tanımlar bu kategoriye girer.
Adımlar
	1. Yedekleme Oluşturun:dmpmqcfg -m QMGR_NAME > /tmp/backup.mqsc
		○ QMGR_NAME yerine mevcut kuyruk yöneticisinin adını yazın.
	2. Durumu Kontrol Edin:
		○ Kuyruk yöneticisinin çalıştığından emin olun:dspmq
		○ Kuyruk yöneticisi duruyorsa, şu komutla başlatın:strmqm QMGR_NAME

Kuyruk Yöneticisi Anahtarları ve Sertifikalarını Çıkarma
TLS kullanıyorsanız, mevcut sertifikaları ve anahtarları yeni kuyruk yöneticisine taşımanız gerekir.
Adımlar
	1. Mevcut TLS Sertifikalarını Kontrol Edin:
grep 'SECCOMM(ALL|SECCOMM(ANON|SSLCIPH' /tmp/backup.mqsc
2. **Anahtar Deposu Konumunu Bulun:**```bashgrep SSLKEYR /tmp/backup.mqsc
	• Örnek çıktı:SSLKEYR('/run/runmqserver/tls/key')
	3. Anahtar ve Sertifikaları Dışa Aktarın:
		○ Sertifikaları şu komutla dışa aktarın:runmqakm -cert -extract -db /run/runmqserver/tls/key.kdb -label "LABEL_NAME" -target OUTPUT_FILE -stashed

Konteyner Ortamı için Yapılandırmayı Güncelleme
Konteyner ortamında aşağıdaki ayarları yapılandırmanız gerekir:
	1. Dinleyici Tanımlarını Kaldırın:
		○ DEFINE LISTENER ifadelerini silin.
	2. TLS Deposu Konumunu Belirleyin:
		○ CERTLABL değerini default olarak değiştirin.
		○ SSLKEYR konumunu /run/runmqserver/tls/key olarak ayarlayın.

Hedef Yüksek Erişilebilirlik Mimarisi Seçimi
IBM MQ Operatörü, aşağıdaki üç HA seçeneği sunar:
	1. Tekil Pod: Basit ve hızlı başlangıç için uygundur.
	2. Çoklu Pod: Daha hızlı failover için iki Pod ile çalışır.
	3. Native HA: Üc Pod ile tam yüksek erişilebilirlik sağlar.

OpenShift Üzerinde Yeni Kuyruk Yöneticisi Oluşturulması
Tekil Pod Kuyruk Yöneticisi Örneği
Aşağıdaki YAML dosyasını kullanarak tek bir kuyruk yöneticisi oluşturun:
apiVersion: mq.ibm.com/v1beta1kind: QueueManagermetadata:  name: qm1spec:  version: 9.4.1.0-r2  license:    accept: true    license: L-QYVA-B365MB    use: "Production"  web:    enabled: true  queueManager:    name: QM1    mqsc:      - configMap:          name: my-mqsc-migrated          items:            - backup.mqsc
OpenShift’te Dağıtım
	1. Konfigürasyonu Yükleyin:oc create configmap my-mqsc-migrated --from-file=backup.mqsc
	2. TLS Sertifikalarını Yükleyin:oc create secret tls my-tls-migration --cert=qmgr.crt --key=qmgr.key
	3. Kuyruk Yöneticisini Dağıtın:oc apply -f qm1.yaml

Doğrulama ve Sorun Giderme
	1. Mesaj Gönderme ve Alma:oc exec -it qm1-ibm-mq-0 -- /opt/mqm/samp/bin/amqsputc Q1 QM1oc exec -it qm1-ibm-mq-0 -- /opt/mqm/samp/bin/amqsgetc Q1 QM1
	2. Logları Kontrol Edin:oc logs qm1-ibm-mq-0
