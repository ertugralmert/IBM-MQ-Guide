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
	1. OpenShift CLI'\ya girin ve aşağıdaki komutları kullanarak yeni bir namespace oluşturun:oc create namespace namespace_adi
	2. IBM MQ Operatör katalog kaynağını ekleyin:cat << EOF | oc apply -f -apiVersion: operators.coreos.com/v1alpha1kind: CatalogSourcemetadata:  name: ibm-mq-operator-catalog  namespace: openshift-marketplacespec:  displayName: IBM MQ Operator Catalog  image: icr.io/cpopen/ibm-mq-operator-catalog:latest  publisher: IBM  sourceType: grpcEOF
	3. Operatörün kurulumunu tamamlayın:oc apply -f ibm-mq-subscription.yaml
	4. Kurulumun başarılı olup olmadığını kontrol edin:oc get csv -n namespace_adi | grep ibm-mq

IBM MQ Operatörünü Yükseltmek
IBM MQ Operatörünü yükseltme adımları iki farklı lisans modeline bağlıdır:
	1. IBM MQ Lisanslarıyla Kullanım:
		○ En son sürümde kanalı güncelleyin:oc patch subscription ibm-mq --patch '{"spec":{"channel":"v3.4"}}' --type=merge
	2. IBM Cloud Pak for Integration (CP4I):
		○ CP4I lisansları için gerekli olan ek bileşenleri eklemeyi unutmayın.

IBM MQ Kuyruk Yöneticisini Dağıtma
"Quick Start" Kuyruk Yöneticisi Dağıtımı
IBM MQ Operatörü kullanarak hızlı bir şekilde kuyruğunuzun dağıtımını yapabilirsiniz. YAML şablonunda ilgili parametreleri ayarlayarak kuyruğunuzun özelliklerini belirtebilirsiniz:
apiVersion: mq.ibm.com/v1beta1kind: QueueManagermetadata:  name: my-queue-managerspec:  license:    accept: true    license: L-XXXXXX  queueManager:    resources:      limits:        memory: 1Gi        cpu: 500m
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
	4. Görsel Oluşturma:FROM icr.io/cp/ibm-mqadvanced-server:9.4.1.0-r2COPY my-mqsc-files/ /etc/mqm/CMD ["runmqserver"]
	5. Görseli Derleme:podman build -t my-custom-mq-image .
	6. Kullanıma Alma:
		○ Oluşturduğunuz görseli Kubernetes veya OpenShift cluster'ınızda dağıtın.
