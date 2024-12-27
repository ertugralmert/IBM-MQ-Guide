IBM MQ'yu Konteynerlerde Çalıştırma ve IBM Cloud Pak for Integration
Son Güncelleme: 29 Ekim 2024
Konteynerler, IBM MQ kuyruğu yöneticisi (queue manager) veya IBM MQ istemci uygulamasını tüm bağımlılıklarıyla birlikte standart bir yazılım birimi olarak paketlemeye olanak tanır. IBM MQ'yu Red Hat OpenShift üzerinde çalıştırmak için IBM MQ Operatörü kullanılabilir. Bu yapılandırma şu yollarla mümkündür:
	• IBM Cloud Pak for Integration
	• IBM MQ Advanced
	• IBM MQ Advanced for Developers
Ayrıca, kendi oluşturduğunuz bir konteyner içinde IBM MQ'yu çalıştırabilirsiniz.

IBM MQ'yu Konteynerlerde Kullanmanın Avantajları
	1. Bağımsızlık ve İzolasyon: Konteynerler, uygulamanın çalışma zamanı ortamını diğer yazılımlardan izole eder ve taşınabilirlik sağlar.
	2. Ortamlar Arası Taşınabilirlik: Geliştirme (dev), test ve üretim (prod) ortamları arasında kolay geçiş sağlar.
	3. Modern Orkestratörler ile Yönetim: OpenShift veya Kubernetes gibi platformlar, kaynak izolasyonu, güvenlik ve hata yönetimi gibi avantajlar sunar.

IBM MQ Operatörü Kullanımı
IBM MQ Operatörü, IBM MQ'nun konteyner platformlarında çalıştırılmasını kolaylaştırır. OpenShift üzerinde IBM MQ Operatörü kullanılarak şu işlemler yapılabilir:
	• Yüksek Kullanılabilirlik Yönetimi: Queue manager'lar için yüksek erişilebilirlik sağlanabilir.
	• Güvenlik Yapılandırmaları: Queue manager'ların güvenliği artırılabilir.
	• Kapsamlı Konfigürasyon: Queue manager'lar detaylı şekilde yapılandırılabilir.

IBM MQ Operatörü ile Önemli Sürümler
	1. IBM MQ Operatör 3.4.0
		○ Desteklenen OpenShift Sürümleri: OpenShift Container Platform 4.12 ve üstü.
		○ Yenilikler:
			§ Eski ve desteklenmeyen operatörler kaldırılmıştır.
			§ Yeni lisans türleri eklenmiştir.
		○ Güvenlik Güncellemeleri: Bazı güvenlik açıkları giderilmiştir (Detaylar).
	2. IBM MQ Operatör 3.3.0
		○ Değişiklikler:
			§ Lisanslama kuralları web kancası (webhook) ile zorlanır.
			§ Büyük kümelerde hafıza kullanımı azaltılmıştır.

Queue Manager Konteyner İmajları
	• IBM MQ'nun farklı sürümleri için desteklenen konteyner imajları:
		○ IBM MQ Advanced: Kurumsal kullanım için uygun.
		○ IBM MQ Advanced for Developers: Geliştirme ortamlarında kullanım için tasarlanmıştır.
Örnek Queue Manager İmajları:
	1. 9.4.1.0-r2:
		○ IBM Cloud Pak for Integration ile uyumlu.
		○ Red Hat OpenShift 4.12 ve üstü desteklenir.
		○ Yeni özellikler:
			§ Native HA yapılandırmalarının dışarıdan sağlanabilmesi.
			§ Sertifika işleme sorunları çözülmüştür.
	2. 9.4.0.0-r3:
		○ IBM Cloud Pak for Integration ve IBM MQ Advanced ile kullanılabilir.
		○ Yeni özellikler:
			§ Persistent volume genişletme desteği.
			§ Queue manager'ların kolay durdurulması için yeni anotasyonlar.

IBM MQ Konteynerlerinde Sorun Giderme
IBM MQ konteynerlerindeki sorunları çözmek için şu yöntemler önerilir:
	• Log Analizi: Sistem loglarını detaylı inceleyin.
	• Yapılandırma Kontrolü: YAML dosyalarındaki yapılandırmaları doğrulayın.
	• Güvenlik Güncellemeleri: IBM'in önerdiği güncel yamaları ve sürümleri kullanın.



Konteynerlerde IBM MQ'yu Planlama
Son Güncelleme: 29 Ekim 2024
IBM MQ'yu konteynerlerde kullanmadan önce, IBM MQ'nun temel kavramlarına (IBM MQ Teknik Genel Bakış) ve Kubernetes/Red Hat OpenShift gibi konteyner platformlarının temel mimarisine (OpenShift Container Platform Mimari) aşina olmanız önerilir.

IBM MQ'yu Konteynerlerde Kullanım Seçenekleri
IBM MQ'yu konteyner ortamında kullanmak için üç temel yöntem vardır:
	1. IBM MQ Operatörü Kullanımı
		○ IBM MQ Operatörü, OpenShift API'sini genişleterek QueueManager (Kuyruk Yöneticisi) için özel bir kaynak ekler. Bu operatör, kuyruğun tanımlarını algılar ve gerekli Kubernetes kaynaklarına (StatefulSet, Service) dönüştürür.
		○ Native High Availability (HA) gibi karmaşık güncelleme işlemlerini otomatikleştirir.
	2. Önceden Hazırlanmış IBM MQ Advanced Görsellerini Kullanma
		○ IBM Container Registry'den temin edilebilen önceden hazırlanmış görseller kullanılabilir. Bu görseller, IBM MQ Advanced özelliklerini içerir.
	3. Kendi Görsellerinizi ve Dağıtım Kodunuzu Oluşturma
		○ Daha esnek bir çözüm isteyenler için kendi konteyner görüntülerinizi oluşturabilirsiniz. Ancak, bu yaklaşım güçlü bir konteyner yapılandırma bilgisi gerektirir ve oluşturulan konteynerin tüm sorumluluğunu almayı içerir.

IBM MQ Konteynerleri için Lisanslama Planlaması
Konteyner lisanslama, IBM License Service kullanılarak konteynerlerin kapasitelerine dayalı bir lisans modeli sunar. Tüm sunucuyu lisanslamak yerine, yalnızca kullanılan konteynerlerin kapasitesi lisanslanır.

Depolama Seçenekleri
	1. Ephemeral (Geçici) Depolama
		○ Konteyner yeniden başlatıldığında tüm veriler kaybolur.
		○ Demo ortamları veya bağımsız geliştirme için uygundur.
		○ Eksiler: Tüm mesajlar, işlem durumları ve yapılandırmalar sıfırlanır.
	2. Kalıcı Depolama
		○ Varsayılan olarak kullanılan bu yöntem, kuyruğun yeniden başlatıldığında mevcut mesajlarını ve yapılandırmalarını korumasını sağlar.
		○ Depolama sınıfına bağlı olarak özelleştirilebilir.

Yüksek Erişilebilirlik (HA) Seçenekleri
IBM MQ için üç ana yüksek erişilebilirlik seçeneği bulunur:
	1. Native HA Kuyruk Yöneticisi
		○ Aktif bir kopya ve iki yedekleme podu içerir. Blok depolama kullanır.
		○ Daha hızlı kurtarma süreleri sağlar.
	2. Çoklu Örnekli Kuyruk Yöneticisi
		○ Paylaşılan dosya sistemi üzerinde çalışan aktif ve yedek bir pod içerir.
		○ File locking (dosya kilitleme) ile geçiş sağlanır.
	3. Tek Dayanıklı Kuyruk Yöneticisi
		○ Bir podda çalışır ve Kubernetes tarafından izlenir. Pod başarısız olduğunda, Kubernetes yeni bir pod başlatır.

Konteynerlerde Güvenlik Planlaması
	1. Kimlik Doğrulama ve Yetkilendirme
		○ LDAP, Mutual TLS veya özel bir MQ eklentisi aracılığıyla kullanıcı kimlik doğrulaması yapılabilir.
	2. Ağ Trafiğinin Sınırlandırılması
		○ IBM MQ için ağ politikaları uygulanabilir.
	3. FIPS Uyumluluğu
		○ Çalışma sırasında, konteynerin FIPS uyumlu bir işletim sisteminde başlatılıp başlatılmadığını tespit eder ve buna göre FIPS desteği yapılandırır.

Performans ve Ölçeklenebilirlik Planlaması
	1. İşlem ve İş Parçacığı Sınırları
		○ Linux platformlarında iş parçacığı sınırları konteyner platformu tarafından sınırlandırılabilir. Örneğin, OpenShift'te varsayılan sınır konteyner başına 4096 işlemdir.
	2. Depolama Hacmi Sınırları
		○ Konteyner platformları, bir node'a bağlanabilecek maksimum hacim sayısını sınırlandırabilir (ör. AWS EC2 için maksimum 30 hacim).
	3. IBM MQ Ölçekleme Teknikleri
		○ Tek bir büyük kuyruk yöneticisi yerine, birden fazla kuyruk yöneticisi çalıştırmak avantajlı olabilir.



IBM MQ Konteyner Ortamı Hazırlama, Kurma ve Yükseltme
Son Güncelleme: 6 Aralık 2024
IBM MQ'yu konteynerlerde kullanmadan önce ortamınızı hazırlamanız, uygun aracı kurmanız ve yükseltmelerinizi doğru bir şekilde planlamanız gerekir. Bu belgede, IBM MQ'yu konteynerlerde kullanma süreci detaylı olarak anlatılmaktadır.

IBM MQ Operatörü Kurulumu ve Yükseltmesi
Görev Hakkında
Red Hat OpenShift Container Platform kullanıyorsanız, IBM MQ Operatörünü kurarak başlayabilirsiniz. Eğer kendi konteyner görüntülerinizle çalışmayı düşünüyorsanız, özel konteyner hazırlama süreci izlenmelidir.

IBM MQ Operatörünü Kurma ve Yükseltme
IBM MQ Operatörünün Kurulumu
IBM MQ Operatörünü kurmadan önce şu adımları tamamlamalısınız:
	1. Red Hat OpenShift Container Platform Kurulumu:
		○ OpenShift 4.12 veya daha üyksek bir versiyonu kullanmalısınız. CLI aracıyla OpenShift cluster'ınıza bağlanarak doğru kurulum yaptığınızdan emin olun.
	2. Depolama Yapılandırması:
		○ Tekli veya Native HA kuyruğunda ReadWriteOnce (RWO), çoklu örnekli kuyruğlarda ise ReadWriteMany (RWX) modunda çalışmalıdır.
		○ Test için IBM MQ dosya sistemleri belgelerindeki şartları kontrol edin.
	3. Operatör Kataloğu Eklemek:
		○ IBM MQ Operatör kataloğunu cluster'ınıza eklemek için CLI veya OpenShift web konsolunu kullanabilirsiniz.
IBM MQ Operatörünü CLI ile Kurmak
	1. OpenShift CLI'\ya girin ve aşağıdaki komutları kullanarak yeni bir namespace oluşturun:
oc create namespace namespace_adi
	2. IBM MQ Operatör katalog kaynağını ekleyin:
cat << EOF | oc apply -f -
apiVersion: operators.coreos.com/v1alpha1
kind: CatalogSource
metadata:
  name: ibm-mq-operator-catalog
  namespace: openshift-marketplace
spec:
  displayName: IBM MQ Operator Catalog
  image: icr.io/cpopen/ibm-mq-operator-catalog:latest
  publisher: IBM
  sourceType: grpc
EOF
	3. Operatörün kurulumunu tamamlayın:
oc apply -f ibm-mq-subscription.yaml
	4. Kurulumun başarılı olup olmadığını kontrol edin:
oc get csv -n namespace_adi | grep ibm-mq

IBM MQ Operatörünü Yükseltmek
IBM MQ Operatörünü yükseltme adımları iki farklı lisans modeline bağlıdır:
	1. IBM MQ Lisanslarıyla Kullanım:
		○ En son sürümde kanalı güncelleyin:
oc patch subscription ibm-mq --patch '{"spec":{"channel":"v3.4"}}' --type=merge
	2. IBM Cloud Pak for Integration (CP4I):
		○ CP4I lisansları için gerekli olan ek bileşenleri eklemeyi unutmayın.

IBM MQ Kuyruk Yöneticisini Dağıtma
"Quick Start" Kuyruk Yöneticisi Dağıtımı
IBM MQ Operatörü kullanarak hızlı bir şekilde kuyruğunuzun dağıtımını yapabilirsiniz. YAML şablonunda ilgili parametreleri ayarlayarak kuyruğunuzun özelliklerini belirtebilirsiniz:
apiVersion: mq.ibm.com/v1beta1
kind: QueueManager
metadata:
  name: my-queue-manager
spec:
  license:
    accept: true
    license: L-XXXXXX
  queueManager:
    resources:
      limits:
        memory: 1Gi
        cpu: 500m
Bu dosyayı kaydettikten sonra, aşağıdaki komutla dağıtın:
oc apply -f my-queue-manager.yaml

IBM MQ Konteyner İmajı Oluşturma
IBM MQ için kendi konteyner imajlarınızı oluşturmak istiyorsanız, aşağıdaki adımlar izlenmelidir:
	1. Çevresel Gereksinimler:
		○ IBM MQ özelliklerini ve lisans gereksinimlerini karşılayan bir base imaj seçin (Red Hat UBI veya Ubuntu).
	2. Konfigürasyon Dosyaları:
		○ Özel MQSC dosyaları veya INI ayar dosyaları kullanın.
	3. Native HA Grubu Oluşturma:
		○ Native HA için 3 kuyruğun yöneticisini kurun, konfigüre edin ve başlatın.
	4. Görsel Oluşturma:
FROM icr.io/cp/ibm-mqadvanced-server:9.4.1.0-r2
COPY my-mqsc-files/ /etc/mqm/
CMD ["runmqserver"]
	5. Görseli Derleme:
podman build -t my-custom-mq-image .
	6. Kullanıma Alma:
		○ Oluşturduğunuz görseli Kubernetes veya OpenShift cluster'ınızda dağıtın.



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
	1. Namespace Oluşturun:


kubectl create namespace mq-test
	2. YAML Dosyalarını Hazırlayın:
		○ Service:

apiVersion: v1
kind: Service
metadata:
  name: quickstart-ibm-mq
spec:
  ports:
  - name: qmgr
    port: 1414
  - name: metrics
    port: 9157
  selector:
    app.kubernetes.io/instance: quickstart
  type: ClusterIP
		○ ServiceAccount:

apiVersion: v1
kind: ServiceAccount
metadata:
  name: quickstart-ibm-mq
		○ StatefulSet:

apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: quickstart-ibm-mq
  namespace: mq-test
spec:
  replicas: 1
  template:
    spec:
      containers:
      - name: qmgr
        image: cp.icr.io/cp/ibm-mqadvanced-server:9.4.1.0-r1
        env:
        - name: MQ_QMGR_NAME
          value: "QUICKSTART"
	3. Kaynakları Dağıtın:

kubectl apply -f service.yaml
kubectl apply -f serviceaccount.yaml
kubectl apply -f statefulset.yaml
	4. Dağıtımı Doğrulayın:

kubectl get pods -n mq-test

Podman Üzerinde Kuyruk Yöneticisi Dağıtımı
Genel Bakış
IBM MQ Advanced konteyner görüntüsünü kullanarak Podman'da bir kuyruk yöneticisi dağıtın.
Prosedür
	1. Dosyaları ve Dizinleri Hazırlayın:
		○ Sertifikalar: qm-pki
		○ MQSC Komutları: example-tls.mqsc
		○ INI Dosyası: example-tls.ini
	2. Konteyneri Çalıştırın:

podman run --env LICENSE=accept --env MQ_QMGR_NAME=QM1 \
  -v "./mqwebuser.xml:/etc/mqm/web/installations/Installation1/servers/mqweb/mqwebuser.xml" \
  -v "./example-tls.ini:/etc/mqm/example-tls.ini" \
  -v "./example-tls.mqsc:/etc/mqm/example-tls.mqsc" \
  -v "./qm-pki:/etc/mqm/pki/keys/qmlabel" \
  --publish 1414:1414 --publish 9443:9443 --detach --name QM1 \
  cp.icr.io/cp/ibm-mqadvanced-server:9.4.1.0-r1
	3. Doğrulama:
		○ Mesajlaşma:

amqsputc EXAMPLE.QUEUE QM1
amqsgetc EXAMPLE.QUEUE QM1
		○ Konsol: Tarayıcıda https://localhost:9443/ibmmq/console adresini açın.

Doğrulama ve Sorun Giderme
	• Loglar:
		○ Müşteri Hataları: ~/IBM/MQ/data/errors/AMQERR01.LOG
		○ Kuyruk Yöneticisi Logları: exec komutunu kullanarak konteyner loglarını inceleyin.

podman exec -it QM1 /bin/bash



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
	1. Yedekleme Oluşturun:
dmpmqcfg -m QMGR_NAME > /tmp/backup.mqsc
		○ QMGR_NAME yerine mevcut kuyruk yöneticisinin adını yazın.
	2. Durumu Kontrol Edin:
		○ Kuyruk yöneticisinin çalıştığından emin olun:
dspmq
		○ Kuyruk yöneticisi duruyorsa, şu komutla başlatın:
strmqm QMGR_NAME

Kuyruk Yöneticisi Anahtarları ve Sertifikalarını Çıkarma
TLS kullanıyorsanız, mevcut sertifikaları ve anahtarları yeni kuyruk yöneticisine taşımanız gerekir.
Adımlar
	1. Mevcut TLS Sertifikalarını Kontrol Edin:
grep 'SECCOMM(ALL|SECCOMM(ANON|SSLCIPH' /tmp/backup.mqsc
2. **Anahtar Deposu Konumunu Bulun:**
```bash
grep SSLKEYR /tmp/backup.mqsc
	• Örnek çıktı:
SSLKEYR('/run/runmqserver/tls/key')
	3. Anahtar ve Sertifikaları Dışa Aktarın:
		○ Sertifikaları şu komutla dışa aktarın:
runmqakm -cert -extract -db /run/runmqserver/tls/key.kdb -label "LABEL_NAME" -target OUTPUT_FILE -stashed

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
apiVersion: mq.ibm.com/v1beta1
kind: QueueManager
metadata:
  name: qm1
spec:
  version: 9.4.1.0-r2
  license:
    accept: true
    license: L-QYVA-B365MB
    use: "Production"
  web:
    enabled: true
  queueManager:
    name: QM1
    mqsc:
      - configMap:
          name: my-mqsc-migrated
          items:
            - backup.mqsc
OpenShift’te Dağıtım
	1. Konfigürasyonu Yükleyin:
oc create configmap my-mqsc-migrated --from-file=backup.mqsc
	2. TLS Sertifikalarını Yükleyin:
oc create secret tls my-tls-migration --cert=qmgr.crt --key=qmgr.key
	3. Kuyruk Yöneticisini Dağıtın:
oc apply -f qm1.yaml

Doğrulama ve Sorun Giderme
	1. Mesaj Gönderme ve Alma:
oc exec -it qm1-ibm-mq-0 -- /opt/mqm/samp/bin/amqsputc Q1 QM1
oc exec -it qm1-ibm-mq-0 -- /opt/mqm/samp/bin/amqsgetc Q1 QM1
	2. Logları Kontrol Edin:
oc logs qm1-ibm-mq-0



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
		○ OpenShift CLI'de şu komutu çalıştırın:
oc get queuemanager QueueManagerName -n namespace --output jsonpath='{.status.adminUiUrl}'
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
	1. Pod ismini bulun:
oc get pods --selector app.kubernetes.io/name=ibm-mq,app.kubernetes.io/instance=queue_manager_name
	2. dmpmqcfg komutunu kullanarak yedekleme yapın:
oc exec -it pod_name -- dmpmqcfg > backup.mqsc
Geri Yükleme
	1. Yedek dosyasını kuyruğ yöneticisine uygulama:
oc exec -i pod_name -- runmqsc < backup.mqsc

Native HA Kuyruğ Yöneticilerinin Durumunu Görüntüleme
Genel Bakış
dspmq komutunu kullanarak bir kuyruğ yöneticisinin durumunu kontrol edebilirsiniz. Bu bilgi, aktif veya replika durumuna göre farklılık gösterebilir.
Prosedür
	1. Pod'ları listeleme:
oc get pod --selector app.kubernetes.io/instance=nativeha-qm
	2. dspmq komutunu çalıştırma:
oc exec -t Pod dspmq
	3. Durum bilgisi kontrolü:
		○ Aktif kuyruğ yöneticisi:
QMNAME(BOB) STATUS(Running)
		○ Replika kuyruğ yöneticisi:
QMNAME(BOB) STATUS(Replica)

Native HA Kuyruğ Yöneticilerini Sonlandırma
Genel Bakış
endmqm komutunu kullanarak bir Native HA kuyruğ yöneticisinin aktif veya replika durumunu sonlandırabilirsiniz.
Prosedür
	1. Aktif Kuyruğ Yöneticisini Sonlandırma:
endmqm -s QMgrName
	2. Replika Kuyruğ Yöneticisini Sonlandırma:
endmqm -x QMgrName
Not: endmqm komutunda grup quorum kontrol edilir. Quorum düşerse, komut başarısız olur



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
	1. QueueManager, namespace ve operator namespace bilgilerini ayarlayın:
export QM=QueueManager_Adi
export QM_NAMESPACE=QueueManager_Namespace
export MQ_OPERATOR_NAMESPACE=Operator_Namespace
	2. Aşağıdaki komutları çalıştırın ve çıktı dosyalarını IBM Destek'e sağlayın:
oc version -o yaml > ocversion.yaml
oc get qmgr $QM -n $QM_NAMESPACE -o yaml > queue-manager-$QM.yaml
oc get pods -n $QM_NAMESPACE -o yaml --selector "app.kubernetes.io/instance=$QM" > qm-pods-$QM.yaml
Pod Loglarını ve Olaylarını Toplama
	1. Pod logları:
oc logs Pod_Adi > pod-logs.txt
	2. Pod olayları:
oc get events -n $QM_NAMESPACE -o yaml > pod-events.yaml

Persistent Volume Claims (PVC) Üzerinde Verilere Erişim
IBM MQ Operator'ı tarafından dağıtılan bir queue manager'ın PVC dosyalarına erişim için PVC inspector aracı kullanılabilir.
Adımlar
	1. Inspector Aracını İndirin: MQ PVC Tool GitHub
	2. Cluster'ı Giriş Yapın:
oc login
	3. Inspector Pod'ı Çalıştırın:
./pvc-tool.sh queue_manager_name queue_manager_namespace_name
	4. Dosyalara Erişim:
oc rsh pvc-inspector-pod-name
	5. İlgili Pod'ı Temizleyin:
oc delete pods -l tool=mq-pvc-inspector

OpenShift Monitoring CLI ile Cluster Sorun Giderme
OpenShift CLI Kullanımı
	1. Monitoring'i Aktifleştirin:
		○ OpenShift Monitoring'in user-defined projeler için aktifleştirilmesi gerekir. Ayrıntılar için OpenShift dokümanlarına bakın.
	2. IBM MQ Metriğini Sorgulayın:
export QM_METRIC_NAME=ibmmq_qmgr_log_write_latency_seconds
export PROMQL_QUERY="$QM_METRIC_NAME{namespace=\"$QM_NAMESPACE\"} [5h:10m]"
Prometheus metriklerini sorgulamak için:
curl -G -s -k -H "Authorization: Bearer $OCP_LOGIN_TOKEN" \
--data-urlencode "query=$PROMQL_QUERY" \
"https://$THANOS_QUERIER_HOST/api/v1/query_range"

