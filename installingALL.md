IBM MQ Kurulumuna Genel Bakış
IBM MQ'nun kurulumu, hangi platformda kullanıldığına ve hangi bileşenlerin yükleneceğine bağlı olarak farklılıklar gösterebilir. IBM MQ'nun kurulumu aşağıdaki adımlarla gerçekleştirilir:
	1. Bileşenler ve Özellikler:
		○ IBM MQ'yu kurarken ihtiyacınız olan bileşenleri seçebilirsiniz. Sunucu ve istemci kurulumları farklıdır.
		○ Sunucu kurulumu: Bir veya birden fazla kuyruk yöneticisi içerir.
		○ İstemci kurulumu: Bir uygulamanın, başka bir sistemdeki kuyruk yöneticisiyle iletişim kurmasını sağlar.
	2. Lisans Gereksinimleri:
		○ IBM MQ'nun doğru şekilde çalışabilmesi için gerekli lisansların alınmış olması gerekir. Kurulum sırasında lisans anlaşması bilgileri sisteme kaydedilir.
	3. Yazılım Gereksinimleri:
		○ IBM MQ'nun desteklediği işletim sistemleri ve yazılım gereksinimleri için IBM MQ Sistem Gereksinimleri web sitesini kontrol etmelisiniz.
	4. Kurulum Resimleri:
		○ IBM MQ'nun kurulumu için gerekli dosyalar, Passport Advantage veya Fix Central gibi kaynaklardan indirilebilir.
Kurulum Adımları
IBM MQ kurulumunun her platformda nasıl yapılacağına dair detaylar aşağıda verilmiştir:
	1. Sunucu Kurulumu:
		○ AIX, Linux, Windows ve IBM i platformlarında sunucu kurulumu için özel talimatlar bulunur. Her platformda IBM MQ'nun sunucu ve istemci bileşenleri ayrı olarak yüklenebilir.
	2. İstemci Kurulumu:
		○ IBM MQ istemcisi, ayrı bir makinede kurulu bir kuyruk yöneticisiyle iletişim kuran bir bileşendir. Sunucu ve istemcinin aynı sistemde kurulu olması mümkündür, ancak her iki bileşen arasında bir MQI kanalı tanımlanmalıdır.
	3. Bileşen Seçimi:
		○ IBM MQ'nun kurulumunda Advanced Message Security, Managed File Transfer, MQ Telemetry ve RDQM gibi bileşenler de ayrıca kurulabilir. Bu bileşenlerin kurulumunda uygun lisansların alındığından emin olmalısınız.
	4. Z/OS Kurulumu:
		○ IBM MQ'nun z/OS sistemlerinde kurulumu, ShopZ web sitesinden yapılabilir.
Lisans Gereksinimleri
IBM MQ'nun kurulumunda IBM License Metric Tool (ILMT) kullanılabilir. Bu araç, IBM MQ'yu kurduğunuzda otomatik olarak lisansları izler ve her kuyruk yöneticisi başlatıldığında lisans uyumunu kontrol eder.
	• Lisans bilgileri, /licenses dizininde saklanır ve her zaman okunabilir.
	• Deneme lisansı kullanıyorsanız, belirli talimatlara uyarak bu lisansı tam bir lisansa dönüştürebilirsiniz.
Kurulum Sonrası
IBM MQ'nun başarılı bir şekilde kurulup kurulmadığını doğrulamak için aşağıdaki adımları izleyebilirsiniz:
	1. Kurulum Doğrulaması:
		○ IBM MQ kurulumunun doğru yapıldığını doğrulamak için dspmqver komutunu kullanarak kurulum bilgilerini görüntüleyebilirsiniz.
	2. Kurulum Resmi Web Siteleri:
		○ IBM MQ'nun kurulum dosyalarını ve güncellemelerini Fix Central ve Passport Advantage gibi platformlardan indirebilirsiniz.
IBM MQ Kaldırılması
IBM MQ'nun kaldırılması için, kurulum işleminin tersine yapılacak işlemler gereklidir. IBM MQ, platforma özel komutlar ile kaldırılabilir. Örneğin, Windows platformunda bir "uninstall" komutu kullanılabilir.




IBM MQ Linux Üzerinde Kurulum ve Kaldırma Rehberi
Bu bölüm, IBM MQ'nun Linux ortamına kurulumu ve kaldırılmasıyla ilgili görevleri kapsamaktadır. IBM MQ'nun kurulumu öncesinde sistem gereksinimlerinin kontrol edilmesi, sistemin hazırlanması ve kurulum adımlarının nasıl gerçekleştirileceği gibi konular ele alınmıştır.

1. Görevler Hakkında Bilgi
IBM MQ'nun Linux ortamına kurulumu sırasında aşağıdaki görevleri tamamlamanız gerekir:
	• Kurulum öncesinde gereksinimlerin kontrol edilmesi.
	• Hangi bileşenlerin kurulacağına ve nereye kurulacağına karar verilmesi.
	• Sistem hazırlık işlemlerinin yapılması.
	• Lisansın kabul edilmesi.
	• Paket yöneticileri (rpm, dnf veya Debian) kullanılarak kurulumun gerçekleştirilmesi.
	• Kurulumun doğrulanması ve gerekirse IBM MQ'nun kaldırılması.
Daha fazla bilgi için, Applying maintenance to IBM MQ dokümanına göz atabilirsiniz.

2. Gereksinimlerin Kontrolü
IBM MQ'nun Linux üzerinde kurulumuna başlamadan önce, aşağıdaki görevleri tamamlayarak sistem gereksinimlerini kontrol etmelisiniz:
2.1. Donanım ve Yazılım Gereksinimleri
Sistemin, kurulmak istenen IBM MQ bileşenlerine uygun donanım ve işletim sistemi yazılım gereksinimlerini karşıladığından emin olun.
	• Host isimleri boşluk içermemelidir.
	• 64-bit Linux sistemlerde 32-bit uygulamaları çalıştırmak için gerekli 32-bit destek paketlerinin kurulu olduğundan emin olun.
Gerekli Paketler:
	• Red Hat Enterprise Linux (x86-64):
		○ glibc.i686
		○ libgcc.i686
		○ libstdc++.i686
	• Ubuntu Linux (x86-64):
		○ libc6:i386
		○ libgcc-s1:i386
		○ libstdc++6:i386
2.2. Disk Alanı Gereksinimleri
Kurulum için yeterli disk alanına sahip olduğunuzdan emin olun. Disk alanı gereksinimleri için Disk space requirements dokümanına göz atabilirsiniz.
2.3. Lisans Gereksinimleri
Kurulumdan önce veya sonra lisansı kabul etmeniz gerekmektedir. Lisans detayları için IBM MQ license information dokümanına bakabilirsiniz.

3. Java Mesajlaşma Hizmeti (JMS ve Jakarta Messaging) Desteği
	• IBM MQ 9.3.0 ve Sonrası: Jakarta Messaging 3.0 desteklenmektedir. Mevcut uygulamalar için JMS 2.0 desteği devam etmektedir. Ancak aynı uygulamada Jakarta Messaging 3.0 API'si ve JMS 2.0 API'si kullanılamaz.
	• Geliştirme için bir JDK (Java Development Kit) ve çalıştırma için bir JRE (Java Runtime Environment) gereklidir.
Java Sürümü Kontrolü:
Sistemde kurulu Java sürümünü aşağıdaki komut ile kontrol edebilirsiniz:

java -version

4. IBM MQ Explorer Gereksinimleri
IBM MQ Explorer, Linux sistemlerde yalnızca x86-64 platformları için kullanılabilir. Minimum gereksinimleri kontrol etmek için IBM MQ Explorer Requirements dokümanına başvurabilirsiniz.

5. RDQM (Replicated Data Queue Manager) Gereksinimleri
RDQM kullanımı için Pacemaker gereklidir ve Pacemaker belirli Linux paketlerini gerektirir. RHEL 8 ve RHEL 9 için gerekli olan temel paketlerin listesi:
	• cifs-utils
	• libxslt
	• net-snmp-libs
	• nfs-utils
	• python3-lxml

IBM MQ Linux Ortamına Kurulum Planlama Rehberi
IBM MQ'yu Linux üzerinde kurmadan önce hangi bileşenleri kuracağınızı, nereye kuracağınızı ve platforma özel seçenekleri gözden geçirmeniz gerekmektedir. Bu rehber, kurulum planlaması için takip edilmesi gereken adımları ve ilgili bilgilere yönlendirmeleri içerir.

1. Donanım ve Yazılım Gereksinimlerini Gözden Geçirme
Kurulum planlamasına başlamadan önce, sisteminizin donanım ve yazılım gereksinimlerini karşıladığından emin olun. 

2. IBM MQ Bileşenleri ve Özelliklerini Seçin
Kurulum sırasında hangi bileşen ve özelliklerin yükleneceğine karar verin:
	• Bileşenler ve Özellikler: Hangi bileşenlerin ihtiyaç duyulan özellikleri karşıladığını belirleyin.
Dikkat: İşletmeniz, kurmak istediğiniz bileşenler için gerekli lisanslara sahip olmalıdır. 

3. Kurulum İsmi Seçeneklerini Gözden Geçirme
Bazı durumlarda, IBM MQ kurulumu için varsayılan isim yerine özel bir isim belirleyebilirsiniz:
	• Kurulum İsmi: AIX, Linux ve Windows platformlarındaki kurulum ismi seçenekleri için Installation name on AIX, Linux, and Windows başlığına göz atın.
	• 

4. Kurulum Konumunu Seçme
IBM MQ'yu nereye kuracağınızı belirlemek için seçenekleri ve kısıtlamaları gözden geçirin:
	• Kurulum Konumu: IBM MQ'nun Multiplatformlarda kurulum konumuyla ilgili bilgiler için Installation location on Multiplatforms başlığını inceleyin.
	• Çoklu Kurulumlar: Aynı sistemde birden fazla IBM MQ kurulumu planlıyorsanız, Multiple installations on AIX, Linux, and Windows başlığına bakın.

5. Birincil Kurulum Planlama
Eğer sistemde bir birincil kurulum varsa ya da olmasını planlıyorsanız:
	• Birincil Kurulum: Birincil kurulum hakkında bilgi almak için Primary installation on AIX, Linux, and Windows başlığına göz atın.

6. İletişim Protokolü Gereksinimlerini Kontrol Etme
Server-to-server bağlantıları için gerekli iletişim protokolünün her iki sistemde de kurulu ve yapılandırılmış olduğundan emin olun.
	• Daha fazla bilgi için Server-to-server links on AIX, Linux, and Windows başlığına bakabilirsiniz.

7. Java Runtime Environment (JRE) Gereksinimi
IBM MQ 9.1.0 ve sonrası:
Eğer mesajlaşma uygulamalarınızda Java kullanmıyorsanız ve IBM MQ'nun Java ile yazılmış bileşenlerini kullanmıyorsanız, JRE yükleme veya önceden yüklenmişse kaldırma seçeneğiniz bulunmaktadır.
Dikkat Edilmesi Gerekenler:
	• JRE yüklenmemişse, anahtar depolarını yönetmek için runmqakm komutunu kullanmanız gerekir.
	• runmqras komutunu kullanmak için sistem yolunda 7 veya üstü bir JRE'nin mevcut olması gerekir.
	• JRE yüklemeden IBM MQ'yu kurabilirsiniz; ancak bazı bileşenler JRE gerektirdiği için kurulum sırasında hata alabilirsiniz.
Not: Önceki IBM MQ sürümlerinden IBM MQ 9.1.0 veya üstüne yükseltme yapıldığında, ayrı olarak yüklenen JRE özelliği de ürüne eklenir.
Komutlar ve Daha Fazlası:
	• runmqakm ve runmqktool komutları hakkında detaylı bilgi için ilgili dokümantasyona göz atabilirsiniz.

• mqm Kullanıcısı ve Grubu
	• Eğer sistemde yoksa, IBM MQ kurulum süreci otomatik olarak mqm grubunu ve mqm kullanıcısını oluşturur. Bu kullanıcı:
		○ IBM MQ ile ilişkili kaynaklara sahip olur.
		○ Varsayılan olarak /var/mqm ana dizinine atanır.
	• Ancak, UID veya GID’nin diğer makinelerle uyumlu olması gerekiyorsa ya da merkezi bir kullanıcı yönetimi (örneğin, Active Directory) kullanılıyorsa, manuel oluşturmak gerekebilir. 
groupadd mqm
useradd -g mqm -d /var/mqm mqm

• Dosya Sistemleri
IBM MQ'nun düzgün çalışması için aşağıdaki dosya sistemleri yapılandırılmalıdır:
	• /var/mqm: Çalışma verileri.
	• /var/mqm/log: Log dosyaları.
	• /var/mqm/errors: Hata kayıtları.
	• Bunların her biri için doğru boyutlandırmayı yapmak önemlidir. Örneğin:
		○ /var/mqm: Minimum 30 MB.
		○ /var/mqm/log: Minimum 100 MB.
		○ /var/mqm/errors: Minimum 10 MB.
	• Performansı artırmak için loglar ve hata dosyaları ayrı disklerde tutulabilir.

	mkdir -p /var/mqm/log /var/mqm/errors
	chown -R mqm:mqm /var/mqm
	chmod 755 /var/mqm
• Kernel Ayarları
IBM MQ’nun başarılı bir şekilde çalışması için kernel ayarları optimize edilmelidir:
	• Minimum Parametreler:

kernel.shmmni = 4096
kernel.shmmax = 268435456
kernel.shmall = 2097152
kernel.sem = 32 4096 32 128
fs.file-max = 524288


	Kalıcı hale getirmek için /etc/sysctl.conf dosyasına şu değerleri ekleyin:
	
kernel.shmmax = 268435456
kernel.sem = 32 4096 32 128
fs.file-max = 524288

• Swap Alanı ve Performans Ayarları
Yüksek yük altında sanal belleğin tükenmesini önlemek için yeterli swap alanı ayrılmalıdır.
• Kullanıcı Limitleri (nofile ve nproc)
	• IBM MQ'nun yöneticisi olan mqm kullanıcısı için açık dosya limiti (nofile) ve işlem limiti (nproc) artırılmalıdır:

mqm       hard  nofile     10240
mqm       soft  nofile     10240
mqm       hard  nproc      4096
mqm       soft  nproc      4096
	• Bu ayarları /etc/security/limits.conf dosyasına ekleyerek kalıcı hale getirin.

Normalde bunlar otomatik oluşur.
Oluşmaması durumunda kullanıcı ve folder oluşturulur.

Kernel ayarları yapılabilir. Kalıcı olması için systctl -p yapılmalı

IBM MQ Lisansının Linux Üzerinde Kabul Edilmesi
IBM MQ’yu Linux sistemlerde kurmadan önce veya kurulum sonrasında lisansı kabul edebilirsiniz. Her iki seçenek için de farklı prosedürler ve kullanım senaryoları bulunmaktadır.

1. Lisans Kabul Etme Zamanlaması
Kurulumdan Önce Lisansı Kabul Etme
Kurulumdan önce lisansı kabul etmek, aşağıdaki durumlarda sorunlara yol açabilir:
	• IBM MQ RPM paketinin bir yum deposuna eklenmesini engeller.
	• Bulut ortamlarında, RPM'in bir görüntüyü oluştururken yüklenmesi gereken durumlarla uyumlu değildir.
	• Kod çalıştırılmadan yüklenen zip paketleriyle uyumlu değildir.
Kurulumdan Sonra Lisansı Kabul Etme
	• Kendi depolarınızı oluşturup IBM MQ'yu buradan yükleme esnekliği sağlar.
	• Ancak, IBM MQ'yu kullanmaya başlamadan önce lisansın kabul edilmesi zorunludur.

2. Lisans Kabul Etme Adımları
Kurulumdan Önce Lisansı Kabul Etme
	1. Sistem hazırlığını tamamlayın. Daha fazla bilgi için ilgili dokümanlara başvurun:
		○ rpm ile Kurulum: Installing the first IBM MQ installation on Linux using the rpm command.
		○ dnf ile Kurulum: Installing IBM MQ on Linux Red Hat using dnf.
		○ Debian ile Ubuntu Kurulumu: Installing IBM MQ on Linux Ubuntu using Debian.
	2. Kurulum sırasında lisansı kabul etmek için:

mqlicense.sh -accept
	Dikkat: Bu yöntem yalnızca kurulum öncesi lisans kabulü için kullanılır. Kurulumdan sonra kullanılamaz.

Kurulumdan Sonra Lisansı Kabul Etme
	1. Lisansı kabul etmek için aşağıdaki komutu çalıştırın:

export MQLICENSE=accept
	2. Lisansın kabul edilip edilmediğini görmek için:

export MQLICENSE=view
	3. Alternatif olarak şu komutları da kullanabilirsiniz:
		○ Lisansı Kabul Etmek için:

mqlicense -accept
		○ Lisansı Görüntülemek için:

dspmqlic
	Not: Kurulum medyasından mqlicense.sh script'ini kurulum sonrası lisans kabulü için kullanmayın. Bu script yalnızca kurulum öncesi lisans kabulü için uygundur.

3. Özel Durumlar
	• Doğru Lisansa Sahip Olma:
Kurmak istediğiniz IBM MQ bileşenleri için gerekli lisansa sahip olmalısınız. Lisans gereksinimleri için IBM dokümantasyonuna göz atabilirsiniz.
	• Deneme Lisansı Dönüşümü:
Eğer bir deneme lisansı kuruluysa, bunu tam lisansa çevirmek için gereken adımları takip edin. Daha fazla bilgi için: Converting a trial license on Linux.

Linux Üzerinde RPM Kullanarak IBM MQ Kurulumu
IBM MQ'yu RPM paket yöneticisi kullanarak Linux sistemlerine kurarken dikkat edilmesi gereken adımları ve bileşenleri aşağıdadır

1. IBM MQ RPM Bileşenleri
Kurulum sırasında seçmeniz gereken bileşenleri dikkatle belirlemelisiniz. Her bileşenin işlevi aşağıdaki gibidir:
Bileşen	Açıklama	Gerekli
MQSeriesRuntime	Server ve client kurulumları için gerekli ortak dosyaları içerir.	Zorunlu
MQSeriesGSKit	Sertifika ve TLS için IBM Global Security Kit (GSKit).	Zorunlu
MQSeriesServer	Kuyruk yöneticisi çalıştırmak ve diğer sistemlerle iletişim kurmak için gerekli dosyalar.	Zorunlu
MQSeriesClient	IBM MQ MQI istemci bağlantıları için gereken dosyalar.	İsteğe Bağlı
MQSeriesSDK	Uygulama geliştirme için gerekli olan dosyalar (ör. header dosyaları).	İsteğe Bağlı
MQSeriesJava	Java üzerinden mesajlaşma desteği sağlar.	İsteğe Bağlı
MQSeriesWeb	IBM MQ'yu REST API ve web konsolu üzerinden yönetmek için gereken dosyalar.	İsteğe Bağlı

2. İlk IBM MQ Kurulumunun Adımları
Adım 1: Sistem Gereksinimlerini Kontrol Etme
Kuruluma başlamadan önce sisteminizi hazırlamalısınız. Daha fazla bilgi için şu rehberlere göz atabilirsiniz:
	• Preparing the system on Linux
	• Kernel ayarlarını yapılandırdığınızdan emin olun. Örneğin:

sysctl -w kernel.shmmni=4096
sysctl -w kernel.shmall=2097152
sysctl -w kernel.shmmax=268435456

Adım 2: Lisansı Kabul Etme
Kurulumdan önce veya sonra lisansı kabul edebilirsiniz:
	• Önce Kabul Etmek İçin:

./mqlicense.sh

Metin tabanlı kabul için:

./mqlicense.sh -text_only
	• Sonra Kabul Etmek İçin:

export MQLICENSE=accept

Adım 3: IBM MQ RPM Paketlerini Kurma
Kurulum sırasında en az şu bileşenleri yüklemelisiniz:
	• MQSeriesRuntime
	• MQSeriesGSKit
	• MQSeriesServer
Kurulum Komutları:
	• Varsayılan Dizin İçin (Önerilen /opt/mqm):

rpm -Uvh MQSeriesRuntime-*.rpm MQSeriesServer-*.rpm MQSeriesGSKit-*.rpm
	• Farklı Bir Dizin için: Farklı bir kurulum dizini belirtmek istiyorsanız, --prefix seçeneğini kullanın:

rpm --prefix /opt/customLocation -Uvh MQSeriesRuntime-*.rpm MQSeriesServer-*.rpm
	Not: Dizin tamamen boş veya kullanılmayan bir dosya sistemi olmalıdır.

Adım 4: Kurulumu Doğrulama
Kurulumun başarılı olduğunu doğrulamak için:

rpm -qa | grep MQ
Hangi bileşenlerin yüklendiğini görmek için:

rpm -q --info MQSeriesRuntime

Adım 5: Ana Kurulum Olarak Ayarlama (Opsiyonel)
Bir sistemi birincil kurulum olarak belirlemek için:

MQ_INSTALLATION_PATH/bin/setmqinst -i -p MQ_INSTALLATION_PATH

3. IBM MQ Client Kurulumu
Eğer yalnızca IBM MQ istemciyi yüklemek istiyorsanız, aşağıdaki bileşenler gereklidir:
	• MQSeriesRuntime
	• MQSeriesClient
	• MQSeriesGSKit
Kurulum Komutu:

rpm -Uvh MQSeriesRuntime-*.rpm MQSeriesClient-*.rpm MQSeriesGSKit-*.rpm

4. Kurulum Sonrası Yapılacaklar
Çevre Değişkenlerini Ayarlama
Kurulumun ardından çevre değişkenlerini ayarlayarak IBM MQ’yu kullanıma hazır hale getirin:

source /opt/mqm/bin/setmqenv -s
Kullanıcı Yetkilendirme
mqm grubuna kullanıcı eklemek için:

usermod -aG mqm username
Kurulum Testi
Kurulumun başarıyla tamamlandığını doğrulamak için test adımlarını takip edin:

dspmqver

Linux Red Hat Üzerinde dnf Kullanarak IBM MQ Kurulumu

Bu döküman, Red Hat Linux sistemlerinde IBM MQ kurulumunu dnf paket yöneticisi kullanarak yapmanız için gereken adımları detaylandırır.

1. Hazırlık Aşamaları
Kurulum işlemlerine başlamadan önce aşağıdaki hazırlıkları yapmanız gereklidir:
1.1 Sistem Gereksinimlerini Kontrol Etme
IBM MQ'yu kurmadan önce, sisteminizin gereksinimlerini karşılayıp karşılamadığını kontrol edin. Bu kontroller şunlardır:
	• Kernel ayarlarını aşağıdaki şekilde yapılandırın:

sysctl -w kernel.shmmni=4096
sysctl -w kernel.shmall=2097152
sysctl -w kernel.shmmax=268435456
1.2 Gerekli Komutların Mevcut Olduğundan Emin Olun
IBM MQ'yu farklı bir dizine kurmak veya birden fazla sürüm kullanmak istiyorsanız, aşağıdaki komutların sistemde yüklü olduğundan emin olun:
	• pax veya rpmbuild (rpm-build paketinde bulunur)
	• createrepo
	• yum-utils
Bu komutlar, IBM MQ ile birlikte gelmez. Linux dağıtım sağlayıcınızdan yüklemelisiniz:

sudo dnf install rpm-build createrepo yum-utils
1.3 Kurulum Dosyalarını Hazırlama
Kurulum dosyalarını IBM Passport Advantage gibi bir kaynaktan indirdiyseniz, bu dosyaları aşağıdaki komutlarla açın:

gunzip CC7K6ML.tar.gz
tar -xvf CC7K6ML.tar
	Not: GNU tar (gtar) kullanmanız gereklidir.
1.4 crtmqpkg Komutunu Kullanarak Paketleri Hazırlama (Opsiyonel)
Eğer IBM MQ'yu varsayılan olmayan bir dizine kurmak istiyorsanız veya bu sistemde zaten başka bir IBM MQ kurulumu mevcutsa:

./crtmqpkg suffix installationPath
Burada:
	• suffix: Kurulumu tanımlamak için kullandığınız benzersiz bir isimdir (örneğin, "custom1").
	• installationPath: IBM MQ'yu kurmak istediğiniz dizini belirtir.
	Not: Bu işlem sırasında /var/tmp dizininde geçici dosyalar oluşturulur. Yeterli disk alanına sahip olduğunuzdan emin olun.

2. Yum Repository Yapılandırması
IBM MQ'nun kurulum paketlerini yönetmek için bir yum deposu yapılandırmanız gerekir:
2.1 Repository Dosyasını Oluşturma
/etc/yum.repos.d dizininde bir repository dosyası oluşturun (örneğin, IBM_MQ.repo):

sudo nano /etc/yum.repos.d/IBM_MQ.repo
Dosyaya şu içerikleri ekleyin:

[IBM-MQ-v.r.m-architecture]
name=IBM MQ v.r.m architecture
baseurl=file:///installationFilesLocation
enabled=1
gpgcheck=0
Değişkenlerin anlamı:
	• installationFilesLocation: Kurulum dosyalarının bulunduğu tam yol.
	• v.r.m: IBM MQ'nun sürüm, dağıtım ve modifikasyon numarası (örneğin, "9.4.0").
	• architecture: Sistem mimarisi (örneğin, "x86_64").
2.2 GPG İmzasını Doğrulama (Opsiyonel)
Repository güvenliğini artırmak için GPG imza doğrulamasını etkinleştirin:

gpgcheck=1
gpgkey=file:///directory/to/ibm_mq_public.pgp
Repository önbelleğini temizleyin:

dnf clean all
Repository'nin doğru şekilde yapılandırıldığını kontrol edin:

dnf repolist

3. Lisans Kabulü
IBM MQ lisansını kurulumdan önce veya sonra kabul edebilirsiniz.
	• Kurulumdan Önce Lisansı Kabul Etmek İçin:

./mqlicense.sh
	• Kurulumdan Sonra Lisansı Kabul Etmek İçin:

export MQLICENSE=accept

4. IBM MQ Kurulumu
IBM MQ'yu kurmak için aşağıdaki adımları izleyin:
4.1 Tüm Bileşenleri Varsayılan Dizine Kurma
Varsayılan /opt/mqm dizinine tüm bileşenleri yüklemek için:

sudo dnf -y install MQSeries*
4.2 Tüm Bileşenleri Varsayılan Olmayan Bir Dizine Kurma
Eğer crtmqpkg komutunu kullanarak özel bir dizin belirttiyseniz:

sudo dnf -y install MQSeries*suffix*
4.3 Belirli Bileşenleri Kurma
Sadece belirli bileşenleri yüklemek için bileşen adını belirtin. Örneğin, sadece sunucu bileşenlerini yüklemek için:

sudo dnf -y install MQSeriesServer*
4.4 Belirli Bir Sürümü Kurma
Birden fazla sürüm mevcutsa, belirli bir sürümü yüklemek için:

sudo dnf -y install MQSeries*-v.r.m-f

5. Kurulum Sonrası Yapılacaklar
5.1 Ana Kurulum Olarak Ayarlama
Sistemdeki bir IBM MQ kurulumunu birincil kurulum olarak ayarlamak için:

MQ_INSTALLATION_PATH/bin/setmqinst -i -p MQ_INSTALLATION_PATH
5.2 Çevre Değişkenlerini Ayarlama
IBM MQ ortamını etkinleştirmek için:

source /opt/mqm/bin/setmqenv -s
5.3 Kurulum Testi
Kurulumun başarılı olduğunu doğrulamak için:

dspmqver

5.4 Kullanıcı Yetkilendirme
mqm grubuna bir kullanıcı eklemek için:

usermod -aG mqm username

Notlar
	• IBM MQ sadece bir mqm grubuna üye kullanıcılar tarafından yönetilebilir. Yönetim komutları için kullanıcıyı bu gruba eklemelisiniz.
	• IBM MQ bileşenlerini farklı bir konuma kurarken doğru yolu ve bileşenleri seçtiğinizden emin olun.

Linux Ubuntu Üzerinde Debian Paketlerini Kullanarak IBM MQ Kurulumu
Son Güncelleme: 2024-12-06
Bu döküman, Linux Ubuntu üzerinde Debian paketleri kullanarak IBM MQ kurulumunu adım adım açıklar.

1. Kurulum Öncesi Hazırlık
1.1 Sistem Gereksinimlerini Kontrol Edin
IBM MQ’yu yüklemeden önce desteklenen yazılım seviyeleri ve sistem gereksinimlerini kontrol edin. Detaylar için IBM MQ Sistem Gereksinimleri dokümanına bakabilirsiniz.
1.2 Önceki RPM Sürümlerini Kaldırın
Eğer Ubuntu üzerinde IBM MQ’nun eski bir RPM sürümünü (örneğin 9.0.2 veya öncesi) yüklediyseniz, Debian sürümünü yüklemeden önce tüm RPM sürümlerini kaldırmanız gerekir:

sudo rpm -e MQSeriesRuntime MQSeriesServer MQSeriesClient MQSeriesGSKit
1.3 Kurulum Dosyalarını Hazırlayın
Kurulum dosyalarını IBM Passport Advantage’den indirdikten sonra, aşağıdaki komutlarla dosyaları açın:

gunzip CC7K6ML.tar.gz
tar -xvf CC7K6ML.tar
	Not: Ubuntu sürümüne özel .deb dosyalarının bulunduğundan emin olun.

2. Debian Paketlerinin Özeti
Tablo 1, Debian paketlerini ve bunların işlevlerini özetler:
Bileşen	Açıklama	Debian Paketi
Runtime	Ortak dosyalar. Zorunlu.	ibmmq-runtime
Server	Kuyruk yöneticisi işlevleri.	ibmmq-server
Client	IBM MQ istemci bağlantıları için dosyalar.	ibmmq-client
SDK	Uygulama geliştirme için başlık dosyaları.	ibmmq-sdk
Java Messaging	Java API dosyaları.	ibmmq-java
Java JRE	IBM MQ Java bileşenleri için gereklidir.	ibmmq-jre
Samples	Örnek uygulama dosyaları.	ibmmq-samples
Man Pages	Komut ve çağrı dökümantasyonu.	ibmmq-man
GSKit	TLS ve sertifika desteği için gerekli.	ibmmq-gskit
REST API & Console	REST API ve web konsolu yönetim araçları.	ibmmq-web
	Not: En azından ibmmq-runtime, ibmmq-server ve ibmmq-gskit paketlerini yüklemeniz gerekir.

3. Lisansı Kabul Etme
Lisansı, kurulumdan önce veya sonra kabul edebilirsiniz.
	• Kurulumdan Önce Lisansı Kabul Etmek İçin:

./mqlicense.sh
	• Kurulumdan Sonra Lisansı Kabul Etmek İçin:

export MQLICENSE=accept

4. IBM MQ Kurulumu
IBM MQ’yu Debian paketleriyle kurmak için iki yöntemden birini seçebilirsiniz: apt-get veya dpkg.
4.1 apt-get ile Kurulum
apt-get, bağımlılıkları otomatik olarak yükler. Aşağıdaki adımları izleyin:
	1. apt-get için Paketleri Ayarlayın: /etc/apt/sources.list.d dizininde bir liste dosyası oluşturun (örneğin, IBM_MQ.list):

sudo nano /etc/apt/sources.list.d/IBM_MQ.list

Dosyaya şu satırları ekleyin:

deb [trusted=yes] file:/kurulum/dizin ./
	2. apt-get Önbelleğini Güncelleyin:

sudo apt-get update
	3. Paketleri Kurun:
		○ Tüm Bileşenleri Kurmak İçin:

sudo apt-get install "ibmmq-*"
		○ Sunucu ve Bağımlılıklarını Kurmak İçin:

sudo apt-get install ibmmq-server

4.2 dpkg ile Kurulum
dpkg bağımlılıkları yüklemez. Bu nedenle bağımlılıkları sıralı olarak yüklemeniz gerekir:
	1. Paketleri Tek Tek Kurun: Aşağıdaki sırayla paketleri yükleyin:

sudo dpkg -i ibmmq-runtime_9.4.0.0_amd64.deb
sudo dpkg -i ibmmq-gskit_9.4.0.0_amd64.deb
sudo dpkg -i ibmmq-server_9.4.0.0_amd64.deb
	2. Bağımlılıkları Kontrol Edin: Kurulum sırasında eksik bağımlılıklar varsa şu komutu çalıştırarak tamamlayın:

sudo apt-get -f install

5. Kurulum Sonrası Yapılacaklar
5.1 Ana Kurulum Olarak Ayarlama
Bir IBM MQ kurulumunu birincil kurulum olarak ayarlayın:

/opt/mqm/bin/setmqinst -i -p /opt/mqm
5.2 Çevre Değişkenlerini Ayarlama
IBM MQ’nun çalışması için çevre değişkenlerini ayarlayın:

source /opt/mqm/bin/setmqenv -s
5.3 Kurulum Testi
Kurulumun başarıyla tamamlandığını doğrulamak için şu komutu çalıştırın:

dspmqver
5.4 Kullanıcı Yetkilendirme
mqm grubuna kullanıcı eklemek için:

sudo usermod -aG mqm username

6. Notlar ve İpuçları
	• Eğer kurulum sırasında bir hata alırsanız, bağımlılıkları kontrol edin ve eksik olanları yükleyin.
	• apt-get kullanımı, bağımlılıkları yönetmede daha kolaydır ve önerilir.
	• Debian paketleri ile sadece bir IBM MQ sürümü kurabilirsiniz. Çoklu sürümler için Docker gibi konteyner teknolojilerini kullanabilirsiniz.

IBM MQ Redistributable Client'ın Temel İşlevleri
	1. Uygulama Entegrasyonu:
		○ IBM MQ Redistributable Client, uygulamalarınızı IBM MQ sistemlerine bağlar ve mesajlaşma işlevlerini kullanmalarını sağlar.
		○ Örneğin, bir istemci uygulama, bu istemciyi kullanarak IBM MQ üzerinde kuyruklara mesaj gönderebilir veya kuyruklardan mesaj alabilir.
	2. Hafif ve Taşınabilir Çözüm:
		○ Tam bir IBM MQ kurulumu yerine daha küçük bir dosya seti sunar. Bu, istemcinin taşınabilir ve hızlı bir şekilde dağıtılabilir olmasını sağlar.
		○ Geliştiriciler, yalnızca ihtiyaç duydukları bileşenleri seçip kullanabilir.
	3. Gömülü Sistemler ve Mikro Hizmetler için Uygunluk:
		○ Redistributable client, minimum disk alanı ve kaynak kullanımı gerektirir. Bu nedenle, gömülü sistemler ve mikro hizmet tabanlı mimariler için idealdir.
	4. Kolay Dağıtım ve Özelleştirme:
		○ genmqpkg script’i, yalnızca belirli bir uygulamanın ihtiyaç duyduğu dosyaları seçerek özelleştirilmiş bir kurulum sağlar.
		○ Örneğin, yalnızca Java tabanlı bir uygulama için Java ile ilgili dosyaları seçebilirsiniz.
	5. Birden Fazla Ortamla Çalışma:
		○ Redistributable client, tam bir IBM MQ sunucusu veya başka bir IBM MQ istemcisi ile aynı sistemde çalışabilir (farklı dizinlerde kurulu olması şartıyla).

Hangi Durumlarda Kullanılır?
	1. Geliştirme ve Test Ortamları:
		○ Geliştiriciler, IBM MQ ile çalışmak için tam bir kurulum yapmadan redistributable client kullanabilir.
		○ Özellikle uygulamanızın IBM MQ özelliklerini test etmek için faydalıdır.
	2. Dağıtılmış Uygulamalar:
		○ Merkezi bir IBM MQ sunucusuna bağlanması gereken dağıtılmış uygulamalar için kullanılır.
		○ Örneğin, bir müşteri uygulaması, bir ana IBM MQ sunucusundaki kuyruklara bağlanmak için bu istemciyi kullanabilir.
	3. Kaynak Kısıtlamalı Sistemler:
		○ IBM MQ’nun tam bir kurulumunu destekleyemeyen sistemler için hafif bir çözüm sağlar.
		○ Örneğin, IoT cihazları veya gömülü cihazlar.
	4. Bulut ve Mikro Hizmet Mimarileri:
		○ Redistributable client, Docker gibi kapsayıcı ortamlarında IBM MQ işlevselliği sağlamak için kullanılabilir.
		○ Minimal konfigürasyon gerektirdiğinden, bulut tabanlı uygulamalarda idealdir.

Kimler Kullanır?
	1. Geliştiriciler:
		○ IBM MQ'yu entegre etmek isteyen yazılımcılar, kolay kurulum ve dağıtım için bu istemciyi tercih eder.
	2. Sistem Yöneticileri:
		○ Tam bir IBM MQ kurulumuna gerek kalmadan, istemcileri IBM MQ sunucularına bağlamak isteyen yöneticiler.
	3. Küçük veya Gömülü Sistemler:
		○ Kaynak kısıtlamaları olan sistemlerde IBM MQ işlevselliği gerektiren durumlar.

Kısaca Faydaları:
	• Hafif: Az yer kaplar ve taşınabilir.
	• Esnek: Sadece ihtiyaç duyulan bileşenleri seçmenize olanak tanır.
	• Kolay Dağıtım: Tam kurulum yapmadan uygulamaları hızlıca IBM MQ sistemlerine bağlar.
	• Düşük Maliyet: Tam bir IBM MQ kurulumuna ihtiyaç duymadan işletim maliyetlerini azaltır.



IBM MQ Redistributable Client Kullanımı ve Yapılandırması
IBM MQ Redistributable Client, bir uygulamaya IBM MQ işlevselliğini eklemek için tam bir IBM MQ kurulumu gerektirmeyen, hafif ve taşınabilir bir istemci çözümüdür.

1. Mevcut Redistributable Client Dosyaları
IBM MQ 9.4 için iki farklı yeniden dağıtılabilir istemci paketi sunulmaktadır:
Destek Türü	İstemci Türü	Dosya Adı
Long Term Support	Linux için C Redistributable Client	9.4.0.0-IBM-MQC-Redist-LinuxX64.tar.gz
Long Term Support	JMS ve Java Redistributable Client	9.4.0.0-IBM-MQC-Redist-Java.zip

2. genmqpkg Script'i ile Özel Dosya Seti Oluşturma
genmqpkg script’i, redistributable client içindeki bin klasöründe yer alır ve yalnızca ihtiyacınız olan dosyaları seçerek daha küçük bir dosya seti oluşturmanıza olanak tanır.
2.1 Kullanım Adımları
	1. İstemci Arşivini Çıkartın:

tar -xvf 9.4.0.0-IBM-MQC-Redist-LinuxX64.tar.gz
	2. Bin Klasörüne Girin:

cd MQC/bin
	3. Script’i Çalıştırın:

./genmqpkg
		○ Script, hangi dosyalara ihtiyacınız olduğunu anlamak için Evet/Hayır soruları sorar.
		○ İşlem tamamlandığında, dosyaların kopyalanacağı bir hedef dizin belirtmeniz istenir.
Önemli Not: Script'e tam bir dizin yolu sağlayın. Shell değişkenlerini kullanarak kısayollar oluşturmayın (örneğin, $HOME).
	4. Seçilen Dosyalar Hedef Dizine Kopyalanır.
2.2 Sınırlamalar
	• IBM yalnızca tam ve değiştirilmemiş paketleri destekler. genmqpkg ile oluşturulan özel dosya setlerine resmi destek verilmez.
	• Varsayılan veri yolu:

$HOME/IBM/MQ/data

3. Varsayılan ve Özelleştirilmiş Veri Yolu
Varsayılan Veri Yolu
Redistributable client, varsayılan olarak şu dizini kullanır:

$HOME/IBM/MQ/data
Özelleştirilmiş Veri Yolu
Varsayılan yolu değiştirmek için şu çevresel değişkeni ayarlayabilirsiniz:

export MQ_OVERRIDE_DATA_PATH=/ozel/dizin/yolu
	Dizin önceden oluşturulmalıdır. Script, dizini otomatik olarak oluşturmaz.

4. Tam IBM MQ Kurulumları ile Birlikte Kullanım
	• Redistributable client, tam IBM MQ kurulumuyla birlikte kullanılabilir ancak her iki kurulum farklı dizinlere yapılmalıdır.
	• Aynı dizine kurulması desteklenmez.

5. Classpath Konfigürasyonu
Redistributable client, aşağıdaki JAR dosyalarını otomatik olarak classpath’e ekler:
Dosya Adı	Açıklama
com.ibm.mq.allclient.jar	Tümleşik MQ istemci JAR'ı
com.ibm.mq.jakarta.client.jar	Jakarta tabanlı MQ istemci JAR'ı
com.ibm.mq.jar	Temel MQ kütüphanesi
com.ibm.mqjms.jar	JMS desteği

6. dspmqver Komutu ile Versiyon Bilgisi
Redistributable client kurulumunun doğruluğunu kontrol etmek için dspmqver komutunu çalıştırabilirsiniz. Örnek çıktı:

Name:        IBM MQ
Version:     9.4.0.0
Level:       p940-940-L220415
BuildType:   IKAP - (Production)
Platform:    IBM MQ for Linux (x86-64 platform)
Mode:        64-bit
O/S:         Linux 2.6.32.59-0.7-default
InstName:    MQNI09200004
InstDesc:    IBM MQ V9.4.0.0 (Redistributable)
Primary:     No
InstPath:    /Development/johndoe/unzip/unpack
DataPath:    /u/johndoe/IBM/MQ/data
MaxCmdLevel: 940

7. Önemli Notlar
	• Uyumluluk: Redistributable client, tam IBM MQ kurulumlarıyla uyumlu ancak yalnızca farklı dizinlerde.
	• Destek: IBM yalnızca tam ve değiştirilmemiş paketleri destekler. genmqpkg kullanılarak oluşturulan özel dosya setleri resmi destek kapsamında değildir.
	• Veri Yolu Ayarları: Varsayılan veri yolu özelleştirilebilir, ancak dizinin manuel olarak oluşturulması gerekir.


1. Yerel Sunucu Kurulumunu Doğrulama
Bu adım, tek bir makine üzerindeki IBM MQ kurulumunu kontrol eder. Queue Manager ve Queue oluşturup, bu kuyruğa mesaj gönderir ve aynı kuyruğa gönderilen mesajı geri alırsınız.
Bu neden önemlidir?
	• IBM MQ kurulumunun eksiksiz tamamlandığını doğrular.
	• Queue Manager ve kuyruğun temel işlevlerinin düzgün çalıştığını kontrol eder.
	• Mesajları kuyruğa gönderebilme (PUT) ve kuyruğa ulaşabilme (GET) yeteneğini test eder.
Kullanılan Araçlar ve Komutlar:
	• crtmqm, strmqm, runmqsc: Queue Manager ve Queue oluşturma.
	• amqsput, amqsget: Kuyruğa mesaj gönderme ve alma işlemleri.

2. Sunucular Arası Mesajlaşmayı Doğrulama
Bu adım, iki farklı IBM MQ sunucusu arasında iletişimi doğrular. Bir sunucu Gönderici (Sender), diğeri Alıcı (Receiver) olarak yapılandırılır ve iki sistem arasında mesaj alışverişi yapılır.
Bu neden önemlidir?
	• Farklı makineler veya ağlar arasında mesaj alışverişinin sorunsuz çalıştığını test eder.
	• Kurumsal mesajlaşma altyapısının düzgün çalıştığından emin olmanızı sağlar.
	• Kanal (Channel), Listener ve Port yapılandırmalarını kontrol eder.
Kullanılan Araçlar ve Komutlar:
	• DEFINE CHANNEL, DEFINE LISTENER, START LISTENER: Kanal ve dinleyici oluşturma.
	• amqsput, amqsget: Mesajları gönderme ve alma.

3. İstemci (Client) Kurulumunu Doğrulama
Bu adım, IBM MQ istemcisinin sunucuyla iletişim kurabildiğini test eder. Sunucuda bir Server-Connection Channel oluşturulur, istemci tarafında ise bu kanala bağlanarak kuyruklara mesaj gönderilir ve alınır.
Bu neden önemlidir?
	• IBM MQ istemcisinin sunucu ile iletişim kurabildiğini doğrular.
	• İstemci-sunucu mimarisinde uyumluluğu kontrol eder.
	• Ağ bağlantıları ve istemci yapılandırmasının doğru yapıldığını garanti eder.
Kullanılan Araçlar ve Komutlar:
	• export MQSERVER: İstemci tarafında bağlantı detaylarını belirtmek için kullanılan ortam değişkeni.
	• amqsputc, amqsgetc: İstemci-sunucu arasında mesaj alışverişini test etmek için kullanılır.

4. Dilde Mesaj Görüntüleme
IBM MQ tarafından üretilen hata veya bilgilendirme mesajlarını farklı bir dilde görmek için kullanılan bir süreçtir. Örneğin, mesajları Türkçe, Fransızca veya Almanca görüntülemek istiyorsanız, gerekli dil dosyasını kurmanız ve LANG ortam değişkenini ayarlamanız gerekir.
Bu neden önemlidir?
	• Kullanıcıların kendi dillerinde hata ve bilgilendirme mesajlarını görmelerini sağlar.
	• Yerel dil desteğiyle mesajları anlamayı kolaylaştırır.
Kullanılan Adımlar:
	• Dil dosyasını kurmak (ibmmq-msg-XX paketlerini yüklemek).
	• export LANG=language_code komutuyla dil ayarını yapmak.

Genel Amaç
Bu doğrulama adımları, IBM MQ’nun her seviyede (sunucu, istemci, ağ) sorunsuz çalıştığından emin olmak için kritik bir süreçtir. Eğer bu adımları tamamlayabilirseniz:
	1. IBM MQ’nun kurulumunun eksiksiz olduğunu.
	2. Sunucuların mesajları düzgün bir şekilde işlediğini.
	3. İstemci-sunucu iletişiminin sorunsuz çalıştığını.
	4. Mesajlaşma altyapınızın temel gereksinimleri karşıladığını garanti altına almış olursunuz.
***********************************************************************


1. IBM MQ Kurulum Doğrulama Süreçleri
Kurulum doğrulama, üç temel yöntemle yapılır:
	1. Yerel Sunucu Doğrulaması: Tek bir sistem üzerinde kurulu IBM MQ sunucusunun doğru çalışıp çalışmadığını test eder.
	2. Sunucular Arası Doğrulama: İki farklı sunucu arasında mesajlaşma altyapısının çalışabilirliğini doğrular.
	3. İstemci Kurulumu Doğrulaması: IBM MQ istemcisinin başarıyla kurulduğunu ve sunucu ile iletişim kurabildiğini kontrol eder.
Her doğrulama yöntemi belirli bir yapılandırma ve test sürecini içerir.

2. Yerel Sunucu Kurulum Doğrulaması
Amaç:
IBM MQ'nun yerel bir sunucu kurulumunun çalışabilirliğini kontrol etmek.
Adımlar:
	1. Ön Gereksinimler:
		○ IBM MQ'nun samples paketi kurulu olmalıdır.
		○ Gerekli tüm bileşenler yüklenmiş olmalıdır.
	2. Queue Manager ve Kuyruk Oluşturma:
		○ Queue manager oluştur:

crtmqm QMA

QMA isimli bir queue manager oluşturulur.
		○ Queue manager'ı başlat:

strmqm QMA
		○ MQSC oturumunu başlat:

runmqsc QMA
		○ Yerel bir kuyruk tanımla:

DEFINE QLOCAL (QUEUE1)

QUEUE1 isimli bir kuyruk tanımlanır.
	3. Mesaj Gönderme ve Alma:
		○ Mesaj gönder:

./amqsput QUEUE1 QMA

Kullanıcı, komut isteminde bir veya daha fazla mesaj yazarak kuyrukta mesaj bırakır.
		○ Mesaj al:

./amqsget QUEUE1 QMA

Kuyruktaki mesajlar alınır ve ekranda gösterilir.
	4. Sonuç:
		○ Mesajlar başarıyla gönderilir ve alınırsa, kurulum başarılıdır.

3. Sunucular Arası Kurulum Doğrulaması
Amaç:
İki IBM MQ sunucusu arasında mesajlaşma altyapısının çalıştığını kontrol etmek.
Adımlar:
	1. Alıcı Sunucu (Receiver):
		○ Queue manager oluştur:

crtmqm QMB

QMB isimli bir queue manager oluşturulur.
		○ Yerel bir kuyruk tanımla:

DEFINE QLOCAL (RECEIVER.Q)

Mesajları alacak RECEIVER.Q isimli kuyruk tanımlanır.
		○ Dinleyici (Listener) tanımla:

DEFINE LISTENER (LISTENER1) TRPTYPE (TCP) CONTROL (QMGR) PORT (1414)
		○ Alıcı kanal tanımla:

DEFINE CHANNEL (QMA.QMB) CHLTYPE (RCVR) TRPTYPE (TCP)
		○ Dinleyiciyi başlat:

START LISTENER (LISTENER1)
	2. Gönderen Sunucu (Sender):
		○ Queue manager oluştur:

crtmqm QMA

QMA isimli bir queue manager oluşturulur.
		○ Yerel bir iletim kuyruğu tanımla:

DEFINE QLOCAL (QMB) USAGE (XMITQ)
		○ Uzaktaki kuyruğun yerel tanımı:

DEFINE QREMOTE (LOCAL.DEF.OF.REMOTE.QUEUE) RNAME (RECEIVER.Q) RQMNAME ('QMB') XMITQ (QMB)
		○ Gönderici kanal tanımla:

DEFINE CHANNEL (QMA.QMB) CHLTYPE (SDR) CONNAME ('receiver_ip(1414)') XMITQ (QMB) TRPTYPE (TCP)
		○ Kanalı başlat:

START CHANNEL (QMA.QMB)
	3. Mesaj Gönderme ve Alma:
		○ Mesaj gönder:

./amqsput LOCAL.DEF.OF.REMOTE.QUEUE QMA
		○ Mesaj al:

./amqsget RECEIVER.Q QMB
	4. Sonuç:
		○ Gönderilen mesaj, alıcı kuyruğunda başarıyla okunuyorsa, kurulum başarılıdır.

4. İstemci Kurulumu Doğrulaması
Amaç:
Bir istemcinin sunucu ile iletişim kurabildiğini doğrulamak.
Adımlar:
	1. Sunucu Hazırlığı:
		○ Queue manager ve kuyruk oluştur:

crtmqm QUEUE.MANAGER.1
DEFINE QLOCAL (QUEUE1)
		○ Server-connection kanalı tanımla:

DEFINE CHANNEL (CHANNEL1) CHLTYPE (SVRCONN) TRPTYPE (TCP)
		○ Dinleyici tanımla ve başlat:

DEFINE LISTENER (LISTENER1) TRPTYPE (TCP) CONTROL (QMGR) PORT (1414)
START LISTENER (LISTENER1)
	2. İstemci Bağlantısı:
		○ İstemci ortam değişkenini ayarla:

export MQSERVER=CHANNEL1/TCP/'server_ip(1414)'
	3. Mesaj Gönderme ve Alma:
		○ Mesaj gönder (istemciden sunucuya):

./amqsputc QUEUE1 QUEUE.MANAGER.1
		○ Mesaj al (sunucudan istemciye):

./amqsgetc QUEUE1 QUEUE.MANAGER.1
	4. Sonuç:
		○ Mesajlar doğru şekilde iletilip alınırsa, istemci kurulumunuz başarıyla tamamlanmıştır.

5. Mesajların Dilini Seçme (LANG Ayarı)
Amaç:
IBM MQ tarafından gösterilen mesajların farklı bir dilde görüntülenmesini sağlamak.
Adımlar:
	1. Dil Dosyasını Kurma:
		○ Gerekli dil dosyalarını kurun. Örneğin, Fransızca için:

apt-get install ibmmq-msg-fr
	2. Dil Ayarını Yapma:
		○ LANG değişkenini ayarla:

export LANG=fr_FR
	3. Sonuç:
		○ IBM MQ mesajları artık seçtiğiniz dilde gösterilecektir.

1. IBM MQ’yu Kaldırma veya Değiştirme
a. Genel Hazırlık
	• Kurulumdan Önce Yapılması Gerekenler:
		○ Tüm IBM MQ uygulamaları, kuyruk yöneticileri (Queue Managers) ve dinleyiciler (Listeners) kapatılmalıdır.
		○ dspmq, endmqm, ve endmqlsr komutları kullanılarak çalışan işlemler durdurulmalıdır.
	• Kritik Not:
		○ IBM MQ 9.4.0 veya daha yeni bir sürüm kaldırılırken düzeltme paketlerini kaldırmak gerekmez. Ancak, 9.4.0 öncesi sürümler için düzeltme paketleri (fix packs) önce kaldırılmalıdır.
b. Çeşitli Paket Yönetim Araçları ile Kaldırma
	• rpm:
		○ Tüm paketleri kaldırmak için:

rpm -qa | grep MQSeries | xargs rpm -ev
		○ Belirli paketleri kaldırmak için:

rpm -ev PaketAdı
	• dnf (Red Hat):
		○ Tüm kurulumları kaldırmak için:

dnf remove MQSeries*
		○ Bireysel bileşenleri kaldırmak için:

dnf remove PaketAdı
	• apt/dpkg (Ubuntu):
		○ Tüm kurulumları kaldırmak için:

apt-get remove "ibmmq-*"
		○ Kalan yapılandırma dosyalarını temizlemek için:

apt-get purge "ibmmq-*"
		○ Bireysel bileşenleri kaldırmak için:

dpkg -r PaketAdı
dpkg -P PaketAdı
c. Kaldırma Sonrası Temizlik
	• Varsayılan olarak, /var/mqm ve /etc/opt/mqm dizinleri korunur. Ancak başka bir IBM MQ kurulumu yoksa ve gelecekte kurulum planlanmıyorsa bu dizinler güvenle silinebilir:

rm -rf /var/mqm /etc/opt/mqm

2. Fix Pack Kaldırma
a. Düzeltme Paketi Kaldırma Süreci
	• Fix pack’ler sadece uygulandığı sırada kullanılan dosyaları etkiler (genellikle /opt/mqm dizini).
	• Kaldırma işlemi, ters sırayla yapılmalıdır: İlk olarak düzeltme paketleri, ardından ana ürün kaldırılır.
	• apt komutları örneği:
		○ Fix Pack kaldırmak için:

apt remove "ibmmq-*-u9401*"
		○ Kalan yapılandırma dosyalarını temizlemek için:

apt purge "ibmmq-*-u9401*"
b. Fix Pack Kaldırma Sonrası Doğrulama
	• Kurulum sonrası sürümü kontrol etmek için:

dspmqver

3. IBM MQ’yu Değiştirme
	• Ek Bileşen Ekleme veya Kaldırma:
		○ rpm veya dnf kullanılarak yeni bileşen eklenebilir veya kaldırılabilir.
		○ Örneğin, SDK ve Runtime bileşenlerini kaldırmak için:

rpm -ev MQSeriesRuntime MQSeriesSDK

Sürecin Önemi
Bu süreç, IBM MQ’yu tamamen kaldırmak veya kurulumun bazı bölümlerini yönetmek için gereken adımları sunar. Bu işlemler:
	1. Sistemi yeniden yapılandırma veya IBM MQ’yu başka bir sistemle değiştirme planlarında yardımcı olur.
	2. Gereksiz dosya ve paketlerin sistemde kalmasını önler.
	3. Yeni bir IBM MQ sürümüne geçişi kolaylaştırır.

IBM MQ Kurulum ve Kaldırma Süreci: Önemli Adımlar
Kurulum Süreci
	1. Sistem Gereksinimlerini Kontrol Et
		○ Linux sistem gereksinimlerini karşılayın. Çekirdek ayarlarını düzenleyin:

sysctl -w kernel.shmmax=268435456
		○ Gerekli paket yöneticisi (rpm, dnf, apt/dpkg) hazır olsun.
	2. Lisansı Kabul Et
		○ Lisansı kurulumdan önce veya sonra kabul edebilirsiniz:

./mqlicense.sh -text_only
	3. Gerekli Paketleri Seç ve Yükle
		○ Minimum bileşenler:
			§ MQSeriesRuntime, MQSeriesServer, MQSeriesGSKit
		○ Yükleme komutları:
			§ rpm:

rpm -Uvh MQSeriesRuntime-*.rpm MQSeriesServer-*.rpm MQSeriesGSKit-*.rpm
			§ dnf (Red Hat):

dnf -y install MQSeries*
			§ apt (Ubuntu):

apt-get install "ibmmq-*"
	4. Kurulumu Doğrula
		○ Sürüm bilgisi için:

dspmqver
		○ Kuyruk yöneticisi oluştur ve başlat:

crtmqm QMA
strmqm QMA
		○ Test kuyruğu tanımla:

DEFINE QLOCAL(QUEUE1)
	5. Test Programları ile Doğrulama
		○ Mesaj gönder ve al:

./amqsput QUEUE1 QMA
./amqsget QUEUE1 QMA

Kaldırma Süreci
	1. Kuyruk Yöneticilerini ve Dinleyicileri Durdur

dspmq -o installation
endmqm QMgrName
endmqlsr -m QMgrName
	2. Kurulumları Kaldır
		○ rpm:

rpm -qa | grep MQSeries | xargs rpm -ev
		○ dnf (Red Hat):

dnf remove MQSeries*
		○ apt (Ubuntu):

apt-get purge "ibmmq-*"
	3. Kalan Dosyaları Temizle (Opsiyonel)
		○ Yedekleme gerekmediğinde:

rm -rf /var/mqm /etc/opt/mqm

Kurulumda ve Kaldırmada Kritik Notlar
	• Sürüm Doğrulama:
		○ Kurulum sonrası: dspmqver
		○ Fix pack kaldırmadan önce: apt list
	• Çevre Değişkenlerini Ayarla:

. MQ_INSTALLATION_PATH/bin/setmqenv -s




Başarılı Kurulum İçin Dikkat Edilmesi Gerekenler
	1. Kurulum Dizinini Doğru Seçin
		○ /opt gibi standart bir dizin kullanarak düzenli bir yapı oluşturabilirsiniz.
	2. Lisans Kabulünü Unutmayın
		○ Lisans sözleşmesini kabul etmek zorunludur. ./mqlicense.sh -text_only komutunu mutlaka çalıştırın.
	3. Kullanıcı ve Yetkiler
		○ mqm grubu ve kullanıcılarıyla çalışmak önemlidir. Yönetim işlemleri için root veya mqm grubunda bir kullanıcı kullanmalısınız.
	4. Doğru Bileşenleri Seçin
		○ Sadece ihtiyacınız olan bileşenleri yükleyin. Zorunlu olanlar:
			§ MQSeriesRuntime
			§ MQSeriesServer
			§ MQSeriesGSKit
	5. Çevre Değişkenlerini Ayarlayın
		○ setmqenv komutunu kullanarak, her oturumda IBM MQ'yu doğru bir şekilde yüklediğinizden emin olun.
	6. Kuyruk Yöneticisini ve Kuyruğu Başlatma
		○ crtmqm ve strmqm komutlarıyla kuyruk yöneticinizi oluşturup başlatmayı unutmayın.
	7. Testleri Mutlaka Yapın
		○ amqsput ve amqsget komutlarını kullanarak testler yapın. Bu testler kurulumun doğru bir şekilde tamamlandığını doğrular.
	8. Hataları Kontrol Edin
		○ Sorun yaşarsanız logları kontrol edin (/var/mqm/errors/) veya dspmq komutuyla durum bilgisi alın.
	9. Notlarınızı Güncel Tutun
		○ Her adımdaki işlemleri not alın. Özellikle yapılandırma adımlarında, kullandığınız kuyruk ve dinleyici isimlerini kaydetmek ileride kolaylık sağlar.




IBM MQ Kurulum Notları (Linux)
1. Gerekli Hazırlıklar
	1. Sistem Gereksinimlerini Kontrol Et
		○ Kernel parametrelerini kontrol et ve ayarla:

sysctl -w kernel.shmmax=268435456
sysctl -w kernel.shmall=2097152
sysctl -w kernel.shmmni=4096
		○ Önerilen dizin: /opt.
	2. Gerekli Kullanıcı ve Grup Oluştur
		○ mqm grubunu ve kullanıcıyı kontrol et veya oluştur:-> normal şartlarda otomatik oluşur burası opsiyonel

groupadd mqm
useradd -g mqm mqm
		○ Yönetim işlemleri için root veya mqm kullanıcısına ihtiyacınız olacak.
	3. Kurulum Dosyalarını İndir
		○ IBM Passport Advantage veya Fix Central’dan doğru dosyayı indir. Örneğin:
			§ IBM-MQC-LinuxX64.tar.gz
	4. Kurulum Dosyasını Kopyala ve Çıkar
		○ tar.gz dosyasını /opt/setup dizinine kopyala ve çıkar:

mkdir -p /opt/setup
cp IBM-MQC-LinuxX64.tar.gz /opt/setup
cd /opt/setup
tar -xvf IBM-MQC-LinuxX64.tar.gz

2. IBM MQ Kurulum Adımları
	1. Lisansı Kabul Et
		○ Lisans metnini kabul etmek için:

./mqlicense.sh -text_only
	2. Paketleri Yükle (rpm Kullanıyorsanız)
		○ Zorunlu bileşenler:

rpm -Uvh MQSeriesRuntime-*.rpm MQSeriesServer-*.rpm MQSeriesGSKit-*.rpm
		○ Opsiyonel bileşenler (örneğin, Java destekli mesajlaşma):

rpm -Uvh MQSeriesJava-*.rpm MQSeriesJRE-*.rpm
	3. Alternatif Paket Yönetimi (dnf Kullanıyorsanız)
		○ Varsayılan dizine yüklemek için:

dnf -y install MQSeries*
	4. Kurulumu Doğrula
		○ IBM MQ versiyonunu kontrol et:

dspmqver

3. İlk Yapılandırma Adımları
	1. Çevre Değişkenlerini Ayarla
		○ Yüklemeyi aktif hale getirmek için:

. /opt/mqm/bin/setmqenv -s
	2. Kuyruk Yöneticisi Oluştur ve Başlat
		○ Örnek bir kuyruk yöneticisi oluştur ve başlat:

crtmqm QMA
strmqm QMA
	3. Dinleyici ve Kuyruk Tanımla
		○ Dinleyici tanımla:

runmqsc QMA
DEFINE LISTENER(LISTENER1) TRPTYPE(TCP) PORT(1414) CONTROL(QMGR)
START LISTENER(LISTENER1)
		○ Örnek kuyruk oluştur:

DEFINE QLOCAL(QUEUE1)
end

4. Test ve Doğrulama
	1. Mesaj Gönder ve Oku
		○ Mesaj gönder:

./amqsput QUEUE1 QMA
		○ Mesaj oku:

./amqsget QUEUE1 QMA
	2. Kuyruk Yöneticisi Durumunu Kontrol Et
		○ Çalışan yöneticileri listele:

dspmq

5. Kaldırma Adımları
	1. Kuyruk Yöneticilerini Durdur
		○ Çalışan kuyruk yöneticilerini durdur:

endmqm QMA
	2. Paketleri Kaldır
		○ rpm ile kaldırma:

rpm -qa | grep MQSeries | xargs rpm -ev
		○ dnf ile kaldırma:

dnf remove MQSeries*
	3. Gereksiz Dosyaları Sil
		○ Kullanılmayan dosyaları temizle:

rm -rf /var/mqm /etc/opt/mqm

Notlar
	• Kurulum sırasında root kullanıcısı veya sudo yetkileri gerekli.
	• mqm kullanıcısı, kuyruk yöneticileriyle çalışırken kullanılır.
	• Her adımda, doğru bileşenlerin seçildiğinden emin olun.
	• Kurulum ve kaldırma sonrası dizinleri temizlerken dikkatli olun; yanlış dosyalar silinirse veriler kaybolabilir.











IBM MQ Kurulum ve Doğrulama Adımları (Windows)
1. Hazırlıklar
	1. Sistem Gereksinimlerini Kontrol Et:
		○ Desteklenen Windows Sürümleri: Sisteminizin IBM MQ tarafından desteklenen bir Windows sürümünde çalıştığından emin olun (örneğin, Windows Server 2016/2019/2022).
		○ Gerekli Disk Alanı: Yüklemek istediğiniz bileşenler için yeterli disk alanı olduğundan emin olun.
		○ Lisans Durumu: IBM MQ bileşenleri için gerekli lisanslara sahip olduğunuzu doğrulayın.
		○ Ön Gereksinim Yazılımları: Gerekli yazılımları yükleyin (örneğin, .NET Framework, C++ Runtime).
	2. Kurulum Dosyalarını İndir:
		○ Kaynak: IBM Passport Advantage veya Fix Central.
		○ Dosya Formatı: IBM MQ kurulum dosyası genelde bir Win64.zip dosyası olarak gelir.
		○ Hedef Dizin: Kurulum dosyalarını örneğin C:\Setup gibi bir dizine kopyalayın.
	3. Dosyaları Çıkarın:
		○ ZIP dosyasını çıkararak kurulum dosyalarını hazırlayın.
		○ Çıkarma işlemi için Windows'un yerleşik zip çıkarma aracı veya 7-Zip gibi bir üçüncü taraf yazılım kullanabilirsiniz.

2. IBM MQ Kurulum Adımları
	1. Kurulumu Başlat:
		○ setup.exe dosyasını çalıştırarak kurulum sihirbazını başlatın.
		○ Kurulum sırasında Administrator yetkisine sahip bir hesap kullanmalısınız.
	2. Kurulum Türünü Seçin:
		○ Tipik Kurulum (Typical): Sunucu ve temel bileşenler otomatik olarak yüklenir.
		○ Özelleştirilmiş Kurulum (Custom): İhtiyacınıza göre bileşenleri seçerek yükleme yapabilirsiniz. Örneğin:
			§ Server: Kuyruk yöneticileri oluşturmak için gerekli.
			§ Development Toolkit: Geliştiriciler için örnek uygulamalar ve API araçları.
			§ Web Administration: Web tabanlı yönetim ve REST API.
	3. Kurulum Konumunu Seçin:
		○ Varsayılan olarak, program dosyaları C:\Program Files\IBM\MQ dizinine yüklenir.
		○ Veri dosyaları varsayılan olarak C:\ProgramData\IBM\MQ dizininde tutulur.
	4. Lisans Sözleşmesini Kabul Edin:
		○ Kurulum sırasında lisans sözleşmesini kabul etmeniz istenir.
	5. Kurulumun Tamamlanması:
		○ Kurulum tamamlandığında, kurulumun başarılı olduğuna dair bir mesaj alırsınız.
		○ Kurulum sırasında log dosyalarının oluşturulmasını sağlayabilirsiniz. Bu, hata ayıklamada faydalıdır.

3. Çevre Ayarları ve Doğrulama
	1. Kuyruk Yöneticisi ve Dinleyici Oluştur:
		○ Komut İstemi Aç: Komut istemini Administrator yetkisiyle açın.
		○ Aşağıdaki komutlarla bir kuyruk yöneticisi ve dinleyici oluşturun:

crtmqm QMA
strmqm QMA
runmqsc QMA
DEFINE LISTENER(LISTENER1) TRPTYPE(TCP) PORT(1414) CONTROL(QMGR)
START LISTENER(LISTENER1)
DEFINE QLOCAL(QUEUE1)
end
	2. Mesaj Gönder ve Oku:
		○ Mesaj göndermek için:

amqsput QUEUE1 QMA
		○ Mesaj okumak için:

amqsget QUEUE1 QMA
	3. Durum Kontrolü:
		○ Kuyruk yöneticisinin durumunu kontrol etmek için:

dspmq

4. Kaldırma Adımları
	1. Kuyruk Yöneticilerini Durdur:
		○ Çalışan tüm kuyruk yöneticilerini kapatın:

endmqm QMA
	2. Programı Kaldır:
		○ Denetim Masası > Programlar ve Özellikler'den IBM MQ'yu kaldırabilirsiniz.
		○ Alternatif olarak, aşağıdaki komutu kullanabilirsiniz:

msiexec /x {ProductCode}
	3. Gereksiz Dosyaları Temizle:
		○ Kaldırma işleminden sonra kalan dosyaları silmek için:

rmdir /s /q "C:\Program Files\IBM\MQ"
rmdir /s /q "C:\ProgramData\IBM\MQ"

Notlar:
	• UAC (User Account Control): Yönetici yetkileri gerektiren işlemler için UAC devre dışı bırakılmalı veya komut istemi "Yönetici olarak çalıştır" seçeneğiyle başlatılmalıdır.
	• Domain Hesapları: IBM MQ hizmetini bir Windows domain ortamında çalıştırıyorsanız, özel bir domain hesabı gerekebilir.
	• Loglama: Kurulum sırasında loglama açık bırakılırsa, hataları daha kolay çözebilirsiniz.

BM MQ Server Kurulum ve Doğrulama Adımları (Windows)
1. Hazırlıklar
	1. Sistem Gereksinimlerini Kontrol Et:
		○ Desteklenen Windows sürümleri: Örneğin, Windows Server 2016/2019/2022.
		○ Gerekli disk alanını kontrol et: Varsayılan olarak yaklaşık 1 GB gereklidir.
		○ Gerekli yazılımları kontrol et: Örneğin, Microsoft .NET Framework 4.7.1 veya üstü.
		○ Kullanıcı Hesabı: Yükleme sırasında Administrator yetkisi gereklidir.
	2. Kurulum Dosyalarını İndir:
		○ Kaynak: IBM Passport Advantage veya Fix Central.
		○ Dosya Formatı: Genellikle bir Win64.zip dosyası olarak gelir.
		○ İndirme sonrası dosyaları bir dizine çıkarın (örneğin, C:\Setup).

2. Kurulum Adımları (Launchpad ile)
	1. Kurulum Başlatma:
		○ Çıkarılan dizine gidin ve setup.exe dosyasını çift tıklayarak başlatın.
		○ UAC etkinse, Run as Administrator seçeneğiyle çalıştırın.
	2. Kurulum Türü Seçimi:
		○ Typical Installation: Varsayılan bileşenleri yükler (Server, Toolkit, Web Administration).
		○ Compact Installation: Yalnızca temel bileşenleri yükler.
		○ Custom Installation: İhtiyacınıza göre bileşenleri seçin. Örneğin:
			§ Server: Kuyruk yöneticileri için gerekli.
			§ Web Administration: REST API ve web tabanlı yönetim için.
			§ Development Toolkit: Geliştirici araçları ve örnek uygulamalar.
	3. Lisans Sözleşmesini Kabul Et:
		○ Lisans metni ekranda gösterilir, kabul etmek için "Yes" seçeneğini işaretleyin.
	4. Kurulumu Tamamlama:
		○ Kurulum tamamlandığında Installation Wizard Completed Successfully mesajını görmelisiniz.
		○ "Finish" butonuna tıklayın.

3. Kurulum Adımları (msiexec ile)
Interaktif veya Sessiz Kurulum için Komut Örnekleri:
	1. Interaktif Kurulum:

msiexec /i "C:\Setup\IBM MQ.msi" /l*v c:\install.log AGREETOLICENSE="yes" ADDLOCAL="Server"
	2. Sessiz Kurulum (Silent Installation):

msiexec /i "C:\Setup\IBM MQ.msi" /q /l*v c:\install.log AGREETOLICENSE="yes" ADDLOCAL="Server"
	3. İkinci Bir Kurulum:

msiexec /i "C:\Setup\IBM MQ.msi" /q /l*v c:\install.log AGREETOLICENSE="yes" ADDLOCAL="Server" MSINEWINSTANCE=1 TRANSFORMS=":InstanceId2.mst"

4. Kurulum Doğrulama
	1. Kurulum Loglarını Kontrol Et:
		○ Log Dosyaları: %TEMP%\MSI*.LOG veya %TEMP%\MQv9_Install_*.LOG
		○ Ayrıca C:\ProgramData\IBM\MQ\amqmjpse.txt dosyasını kontrol edin.
	2. Kuyruk Yöneticisi Oluşturma ve Başlatma:
		○ Komut istemini Administrator yetkisiyle açın ve şu komutları çalıştırın:

crtmqm QMA
strmqm QMA
	3. Dinleyici ve Kuyruk Tanımlama:

runmqsc QMA
DEFINE LISTENER(LISTENER1) TRPTYPE(TCP) PORT(1414) CONTROL(QMGR)
START LISTENER(LISTENER1)
DEFINE QLOCAL(QUEUE1)
end
	4. Mesaj Gönder ve Oku:
		○ Mesaj göndermek için:

amqsput QUEUE1 QMA
		○ Mesaj okumak için:

amqsget QUEUE1 QMA
	5. Kurulumun Durumunu Kontrol Et:
		○ Yüklü kurulumları listelemek için:

dspmqinst

5. Kurulum Sonrası
	1. Prepare IBM MQ Wizard Kullanımı:
		○ Kurulumdan sonra otomatik olarak başlar. IBM MQ Service’i yapılandırmak için bu sihirbazı tamamlayın.
	2. Ortam Değişkenlerini Ayarlama:

MQ_INSTALLATION_PATH\bin\setmqinst -i -p MQ_INSTALLATION_PATH

Notlar
	• Hata Giderme: Hatalar için log dosyalarını kontrol edin.
	• Güvenlik: Kurulum sırasında domain kullanıcı hesaplarının yapılandırmasını dikkatlice yapın. Gerekirse setmqipw komutuyla şifreleme kullanın.
	• Lisans: IBM MQ Advanced özelliklerini yüklemeden önce lisansınızın uygun olduğundan emin olun.

1. IBM MQ Kullanıcı Hesapları İçin Genel Bilgiler
	• Yerel Hesaplar: Eğer sistem bir domain'e üye değilse, IBM MQ kurulum sırasında yerel bir hesap (ör. MUSR_MQADMIN) oluşturur. Bu hesap, kuyruk yöneticilerini ve IBM MQ servislerini yönetmek için kullanılır.
	• Domain Hesapları: Eğer sistem bir Windows domain'ine üye ise, IBM MQ'nun Active Directory üzerinden kullanıcı doğrulaması yapabilmesi için özel bir domain hesabına ihtiyacınız olabilir.
	• Yetki Gereksinimleri:
		○ IBM MQ servislerini çalıştıracak hesapların "Log on as a service" yetkisine sahip olması gerekir.
		○ Hesaplar, Active Directory'deki grup üyelik bilgilerini sorgulama yetkisine sahip olmalıdır.

2. Prepare IBM MQ Wizard Kullanımı
IBM MQ kurulumundan sonra, Prepare IBM MQ Wizard otomatik olarak başlar ve kullanıcı hesaplarını yapılandırmak için kullanılır.
Adımlar:
	1. Wizard'ı Başlatın:
		○ IBM MQ kurulumunu tamamladıktan sonra sihirbaz otomatik olarak açılır.
		○ Manuel olarak başlatmak için:
			§ Başlat Menüsü > IBM MQ > Prepare IBM MQ Wizard.
	2. Yapılandırma Seçeneklerini Tamamlayın:
		○ Eğer domain kullanıcısı gerekiyorsa, gerekli hesap bilgilerini (domain, kullanıcı adı, şifre) girin.
		○ "Log on as a service" yetkisi verilmesi gerekiyorsa şu adımları izleyin:
			§ secpol.msc komutunu çalıştırarak Local Security Policy ekranını açın.
			§ Security Settings > Local Policies > User Rights Assignments altında Log on as a service seçeneğini bulun.
			§ Kullanıcı hesabını ekleyin ve değişiklikleri kaydedin.
	3. Servisleri Yapılandırın:
		○ Domain hesabı doğru şekilde yapılandırıldıktan sonra, IBM MQ servisleri bu hesap altında çalıştırılır.
	4. Wizard İşlemlerini Tamamlayın:
		○ İşlemler tamamlandıktan sonra sihirbaz şu seçenekleri sunar:
			§ IBM MQ Explorer'ı başlat.
			§ Sürüm notlarını görüntüle.
			§ Sihirbaz kısayolunu masaüstünden kaldır.

3. IBM MQ Servislerini Domain Hesaplarıyla Yapılandırma
Eğer IBM MQ domain ortamında çalışıyorsa, domain yöneticisinin aşağıdaki adımları takip etmesi gerekir:
Domain Hesabı Oluşturma ve Ayarlama:
	1. Domain mqm Grubu Oluşturun:
		○ Active Directory üzerinden yeni bir grup oluşturun (ör. Domain mqm).
		○ Bu gruba, IBM MQ servislerini çalıştıracak kullanıcıları ekleyin.
	2. Gerekli Yetkileri Verin:
		○ Read group membership ve Read groupMembershipSAM izinlerini verin.
		○ Bu izinler, Active Directory kullanıcı gruplarını sorgulamak için gereklidir.
	3. Hesapları Domain mqm Grubuna Ekleyin:
		○ IBM MQ servislerinin çalışacağı domain kullanıcılarını bu gruba ekleyin.
IBM MQ Hizmetlerini Domain Kullanıcı Hesabı Altında Çalıştırma:
	1. Domain Kullanıcısını "Log on as a service" Yetkisiyle Ayarlayın:
		○ secpol.msc üzerinden kullanıcıyı Log on as a service politikasına ekleyin.
	2. Prepare IBM MQ Wizard Kullanarak Domain Hesabını Yapılandırın:
		○ Domain kullanıcı bilgilerini girerek IBM MQ'yu bu hesap altında çalıştırmak üzere yapılandırın.

4. Sorun Giderme ve Hata Kontrolü
	• Hata Durumunda:
		○ Log dosyalarını kontrol edin:
			§ %TEMP%\MSI*.LOG
			§ C:\ProgramData\IBM\MQ\amqmjpse.txt
		○ Hata mesajları:
			§ AMQ8066: Yerel mqm grubu bulunamadı.
			§ AMQ8079: Grup üyeliği bilgisi sorgulanırken erişim reddedildi.
	• Hesap Değiştirme:
		○ Hatalı veya eksik domain hesabı yapılandırıldıysa, Prepare IBM MQ Wizard'ı yeniden çalıştırarak doğru bilgileri sağlayabilirsiniz.

5. Özet
	• Yerel hesaplar, domain kullanıcısı gerekli değilse varsayılan olarak kullanılabilir.
	• Domain kullanıcıları gerekli olduğunda, IBM MQ'nun domain grup üyelik bilgilerini sorgulayabilmesi için uygun yetkilere sahip bir hesap oluşturulmalıdır.
	• Prepare IBM MQ Wizard kullanıcı dostu bir arayüzle yapılandırma işlemlerini kolaylaştırır.
	• Hatalar durumunda log dosyalarını kontrol ederek sorunları çözebilirsiniz.

1. IBM MQ Client Kurulumu
Kurulum Öncesi Hazırlıklar
	• Yetkiler: Kurulum sırasında yönetici yetkileri gereklidir. Sisteme Administrator hesabı ile giriş yapmanız önerilir.
	• Kurulum Yöntemleri:
		○ Etkileşimli Kurulum: Setup.exe kullanarak kullanıcı arayüzü üzerinden kurulum yapabilirsiniz.
		○ Sessiz Kurulum: msiexec komutu veya bir yanıt dosyası ile otomatik kurulum yapılabilir.
Kurulum Adımları
	1. Kurulum Medyasına Erişin:
		○ IBM MQ kurulum imajını bulun (ağ paylaşımı veya yerel bir dizinde olabilir).
			§ Örnek: C:\instmqs\Windows\Setup.exe.
	2. Kurulumu Başlatın:
		○ Setup.exe dosyasını çift tıklayın veya bir komut isteminde şu komutu çalıştırın:

C:\instmqs\Windows\Setup.exe
		○ UAC (User Account Control): UAC aktifse, kurulumun yükseltilmiş haklarla çalışmasına izin verin.
	3. Kurulum Tipini Seçin:
		○ Compact: Minimum özelliklerle kurulum.
		○ Typical: Önerilen özellikler ile kurulum.
		○ Custom: Özellikleri özelleştirerek kurulum.
	4. Kurulumu Tamamlayın:
		○ Ekrandaki yönergeleri takip ederek kurulumu tamamlayın.
		○ Kurulum tamamlandığında, yeni bir mqclient.ini dosyası otomatik olarak oluşturulur.

2. Sessiz Kurulum (msiexec Kullanarak)
msiexec ile Kurulum
	• msiexec komutunu kullanarak IBM MQ Client'ı sessiz bir şekilde kurabilirsiniz. Bu yöntem, yanıt dosyası veya komut satırı parametreleri ile yapılandırılabilir.
Örnek Komut

msiexec /i "C:\path\IBM MQ.msi" /q /l*v C:\install.log AGREETOLICENSE="yes" ADDLOCAL="Client"
	• Parametreler:
		○ /i: Kurulum paketi yolu.
		○ /q: Sessiz kurulum (kullanıcı arayüzü olmadan).
		○ /l*v: Kurulum log dosyası yolu.
		○ AGREETOLICENSE="yes": Lisans anlaşmasını kabul eder.
		○ ADDLOCAL="Client": Kurulacak bileşenler (ör. Client).
Çoklu Kurulum için Instance ID Kullanımı
	• Aynı sistemde birden fazla IBM MQ Client kurmak için MSINEWINSTANCE ve TRANSFORMS parametrelerini eklemeniz gerekir:

msiexec /i "C:\path\IBM MQ.msi" /q TRANSFORMS=":InstanceId2.mst" AGREETOLICENSE="yes" ADDLOCAL="Client" MSINEWINSTANCE=1

3. Yanıt Dosyası ile Kurulum
Yanıt Dosyası (Response.ini)
	• Yanıt dosyası, kurulum sırasında ihtiyaç duyulan tüm ayarları içerir ve otomasyonu kolaylaştırır.
	• Örnek Yanıt Dosyası:

[Response]
PGMFOLDER="C:\Program Files\IBM\MQ"
AGREETOLICENSE="yes"
ADDLOCAL="Client"
Yanıt Dosyası Kullanımı
	• Yanıt dosyasını kullanarak kurulum:

msiexec /i "C:\path\IBM MQ.msi" /q USEINI="C:\Response.ini"

4. Kurulum Sonrası Yapılandırma
Kurulumu Birincil Kurulum Olarak Ayarlama
	• Bir sistemde yalnızca bir birincil kurulum olabilir. Birincil kurulum yapmak için şu komutu çalıştırın:

"MQ_INSTALLATION_PATH\bin\setmqinst" -i -p MQ_INSTALLATION_PATH
Çevresel Değişkenleri Ayarlama
	• setmqenv veya crtmqenv komutlarını kullanarak IBM MQ ile çalışmak için ortam değişkenlerini ayarlayın:

setmqenv -s
Kurulum Testi
	• Kurulumun başarılı olduğunu doğrulamak için istemci ve sunucu arasındaki iletişimi test edin:
		○ Daha fazla bilgi için: Testing communication between a client and a server on Windows.

5. IBM MQ Client Özelliklerini Değiştirme veya Kaldırma
msiexec ile Özellik Ekleme/Kaldırma
	• IBM MQ Client'ın belirli özelliklerini eklemek veya kaldırmak için:

msiexec /i {product_code} /q ADDLOCAL="Client" REMOVE="Toolkit" INSTALLATIONNAME="Installation1"

IBM MQ Client Kurulumunu Değiştirme
IBM MQ Client kurulumunu, mevcut özellikleri eklemek veya kaldırmak için aşağıdaki yöntemlerden birini kullanabilirsiniz.

1. IBM MQ Installation Wizard Kullanarak Kurulum Değişikliği
Adımlar
	1. Kurulum İmajına Erişim Sağlayın:
		○ IBM MQ kurulum imajının yerini bulun (ağ paylaşımı veya yerel dosya sistemi dizini olabilir).
			§ Örnek: C:\instmqs\Windows\Setup.exe
	2. Setup.exe Dosyasını Çalıştırın:
		○ Setup.exe dosyasını çift tıklayın veya bir komut isteminde şu komutu çalıştırın:

C:\instmqs\Windows\Setup.exe
	3. Kurulum Modunu Seçin:
		○ Modify seçeneğini seçin ve Next butonuna tıklayın.
	4. Özellikleri Seçin veya Kaldırın:
		○ Özellikler panelinde, değiştirmek istediğiniz özelliğin yanındaki simgeye tıklayın ve aşağıdaki seçeneklerden birini seçin:
			§ Install this feature: Özelliği yükler.
			§ Install this feature and all its subfeatures: Özellik ve bağlı tüm alt özellikleri yükler.
			§ Do not install this feature: Özelliği kaldırır.
	5. Değişiklikleri Uygulayın:
		○ Tüm seçimlerinizi yaptıktan sonra Modify butonuna tıklayın.
		○ Kurulum değişiklikleri tamamlandığında "Installation Wizard Completed Successfully" mesajını göreceksiniz.
	6. Kurulum Penceresini Kapatın:
		○ Finish butonuna tıklayarak kurulumu tamamlayın.

2. Add/Remove Programs Kullanarak Kurulum Değişikliği
Windows 7 için Adımlar
	1. Denetim Masasını Açın:
		○ Start > Control Panel > Add/Remove Programs yolunu izleyin.
	2. IBM MQ'yu Seçin:
		○ Listeden IBM MQ'yu seçin ve Change butonuna tıklayın.
	3. Kurulum Modunu Seçin:
		○ Modify seçeneğini seçin ve Next butonuna tıklayın.
	4. Özellikleri Seçin veya Kaldırın:
		○ Özellikler panelinde, değiştirmek istediğiniz özelliği seçerek kurulum seçeneklerini güncelleyin.
	5. Değişiklikleri Uygulayın:
		○ Modify butonuna tıklayarak kurulum değişikliklerini tamamlayın.
	6. Kurulum Penceresini Kapatın:
		○ "Installation Wizard Completed Successfully" mesajını gördükten sonra Finish butonuna tıklayın.
Windows 8 ve Üstü
	• Not: Windows 8'de Add/Remove Programs seçeneği yalnızca ürünü kaldırmak için kullanılır. Bu durumda değişiklik yapmak için Setup.exe dosyasını kullanmalısınız.

3. Sessiz Modda Değişiklik (msiexec Kullanarak)
msiexec ile Değişiklik
	• Özellik eklemek veya kaldırmak için ADDLOCAL ve REMOVE parametrelerini kullanabilirsiniz.
Örnek Komut

msiexec /i {product_code} /q ADDLOCAL="JavaMsg" REMOVE="" INSTALLATIONNAME="Installation1"
	• Parametreler:
		○ ADDLOCAL: Eklemek istediğiniz özellikleri belirtir.
		○ REMOVE: Kaldırmak istediğiniz özellikleri belirtir.
		○ INSTALLATIONNAME: Hangi kurulumun değiştirileceğini belirtir.
		○ product_code: dspmqinst komutuyla öğrenilebilir.

4. Sessiz Modda Değişiklik (MQParms Kullanarak)
MQParms ile Değişiklik
	• MQParms komutunu kullanarak, bir parametre dosyasından alınan ayarlarla kurulum değişikliklerini yapabilirsiniz.
Örnek
	1. Bir parametre dosyası oluşturun (MQParms.ini):

[MSI]
ADDLOCAL="JavaMsg"
REMOVE=""
/l*v c:\install.log
	2. MQParms Komutunu Çalıştırın:

MQParms "C:\MQParms.ini" /l*v C:\install.log
Notlar:
	• Parametre dosyasında ADDLOCAL ve REMOVE alanlarını ayarlayarak değişiklikleri tanımlayın.
	• Komut satırında belirtilen parametreler, dosyadaki ayarların üzerine yazılır.

IBM MQ Redistributable Clients ve Kurulum Doğrulama Detaylı Açıklamaları
IBM MQ Redistributable Clients, IBM MQ ile çalışan uygulamalar için özel ve esnek istemci yapılandırmaları sunar. Redistributable istemciler, yalnızca uygulama gereksinimlerine göre minimum dosya setini oluşturmanıza olanak tanır. Ayrıca, IBM MQ kurulumlarının doğrulanması, istemci-sunucu iletişiminin test edilmesi ve ulusal dil desteği gibi çeşitli işlemleri içerir. Aşağıda, bu konuların detaylı açıklamaları yer almaktadır:

IBM MQ Redistributable Clients (Yeniden Dağıtılabilir İstemciler)
Redistributable Client Nedir?
IBM MQ Redistributable Clients, IBM MQ istemci uygulamaları için tasarlanmış bir dosya setidir. Bu istemciler, uygulamanın yalnızca ihtiyaç duyduğu dosyaları seçip dağıtım için bir alt küme oluşturmanıza olanak tanır. Redistributable istemciler, tam bir IBM MQ kurulumuyla birlikte yan yana çalışabilir.
Redistributable Client Özellikleri
	• Varsayılan Veri Yolu: Redistributable istemciler, varsayılan olarak %HOMEDRIVE%%HOMEPATH%\IBM\MQ\data yolunu kullanır. Bu yolu değiştirmek için MQ_OVERRIDE_DATA_PATH ortam değişkenini ayarlayabilirsiniz.
	• Önemli Notlar:
		○ Redistributable istemci dosyalarını tam bir IBM MQ kurulumunun bulunduğu dizine çıkarmak desteklenmez.
		○ Redistributable istemciler, yalnızca tam ve değiştirilmemiş dosya setiyle desteklenir.
genmqpkg Komut Dosyasını Kullanma
genmqpkg, redistributable istemci dosyalarını daraltılmış bir dosya alt kümesine dönüştürmek için kullanılan bir betiktir. Bu betik, bir dizi "Evet" veya "Hayır" sorusu sorarak uygulamanız için gerekli dosyaları belirler ve seçilen dosyaları belirtilen hedef dizine kopyalar.
Kullanım Adımları:
	1. genmqpkg betiğini çalıştırın:

MQ_INSTALLATION_PATH\bin\genmqpkg
	2. Sorulara yanıt vererek uygulamanızın gereksinimlerine uygun dosyaları seçin.
	3. Dosyalar seçildikten sonra, yeni hedef dizini belirtin. Betik, gerekli dosyaları bu dizine kopyalar.

IBM MQ Kurulum Doğrulama
Kurulum Doğrulama Yöntemleri
IBM MQ kurulumu tamamlandıktan sonra, sunucu veya istemci kurulumunu doğrulamak için aşağıdaki adımları izleyebilirsiniz:
Yerel Sunucu Kurulumunu Doğrulama
	1. Ortam değişkenlerini ayarlayın:

MQ_INSTALLATION_PATH\bin\setmqenv -s
	2. dspmqver komutuyla kurulum bilgilerini doğrulayın.
	3. Bir sıra yöneticisi oluşturun ve başlatın:

crtmqm QMA
strmqm QMA
	4. Bir kuyruk oluşturun:

runmqsc QMA
DEFINE QLOCAL(QUEUE1)
end
	5. Mesaj gönderme ve alma için örnek programları çalıştırın:

amqsput QUEUE1 QMA
amqsget QUEUE1 QMA
Sunucudan Sunucuya Kurulumu Doğrulama
	1. Alıcı sunucuda bir dinleyici ve alıcı kanal tanımlayın.
	2. Gönderici sunucuda bir gönderici kanal ve uzak sıra tanımlayın.
	3. Mesaj gönderip alın.
İstemci Kurulumunu Doğrulama
	1. Sunucu tarafında bir sıra yöneticisi, kuyruk ve sunucu-bağlantı kanalı oluşturun.
	2. İstemci tarafında MQSERVER ortam değişkenini ayarlayın:

cmd
Copy code
SET MQSERVER=CHANNEL1/TCP/server-address(port)
	3. Örnek istemci programlarını çalıştırarak iletişimi test edin:

amqsputc QUEUE1 QUEUE.MANAGER.1
amqsgetc QUEUE1 QUEUE.MANAGER.1

Ulusal Dil Mesajlarının Ayarlanması
IBM MQ, kurulu sistemin diline uygun olarak mesajları görüntüleyebilir. Ancak, farklı bir dil seçmek için MQS_FORCE_NTLANGID ortam değişkenini kullanabilirsiniz.
Mesaj Dili Ayarı
	1. MQS_FORCE_NTLANGID ortam değişkenini ayarlayın:

SET MQS_FORCE_NTLANGID=0x0409

Not: 0x0409 değeri, İngilizce dilini ifade eder. Diğer diller için Microsoft Dil Tanımlayıcıları belgesini inceleyin.
	2. Bu değişkeni sistem çapında ayarlayın ve sisteminizi yeniden başlatın.

Sonuç
IBM MQ redistributable istemciler ve kurulum doğrulama süreçleri, mesajlaşma altyapınızın stabil bir şekilde çalışmasını sağlamak için kritik öneme sahipti

IBM MQ'yu Windows Üzerinde Kaldırma
IBM MQ istemci ve sunucularını kaldırmak için birkaç yöntem bulunmaktadır. Bu yöntemler arasında denetim masası, komut satırı (msiexec veya MQParms), veya kurulum medyasını kullanarak kaldırma işlemleri yer alır. Aşağıda, IBM MQ'nun tamamen kaldırılması için detaylı bir rehber sunulmaktadır.

Ön Hazırlık
Kaldırma işlemi öncesinde aşağıdaki hazırlıkları yapmanız gerekmektedir:
	1. Günlük Kaydı Aktifleştirme: Kaldırma işlemi sırasında bir günlük kaydı almak için şu adımları izleyin:
		○ regedit komutuyla Kayıt Defteri Düzenleyicisini açın.
		○ HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Installer anahtarını bulun veya oluşturun.
		○ Bu anahtara aşağıdaki bilgileri ekleyin:
			§ Ad: Logging
			§ Veri Türü: REG_SZ
			§ Değer: voicewarmup
		○ Kayıt defteri anahtarını kaydedin.
	2. IBM MQ Programlarını ve Süreçlerini Durdurun:
		○ Kümeleme Kullanıyorsanız (MSCS): Kuyruk yöneticilerini MSCS kontrolünden çıkarın.
			§ Kuyruk yöneticisi kaynağını çevrimdışı alın.
			§ Kaynak örneğini silin.
			§ Kuyruk yöneticisi dosyalarını paylaşılan disklerden geri taşıyın.
		○ Tüm IBM MQ Uygulamalarını Durdurun: MQ_INSTALLATION_PATH\bin\setmqenv -s komutunu çalıştırarak ortamı ayarlayın ve ardından kuyruk yöneticilerini durdurun:

endmqm queue_manager_name
endmqlsr -m queue_manager_name
	3. Sistem Tepsisi Üzerinden IBM MQ'yu Durdurun:
		○ Sistem tepsisindeki IBM MQ simgesine sağ tıklayın ve "Stop IBM MQ" seçeneğini seçin.

IBM MQ'yu Kaldırma Yöntemleri
1. Denetim Masası Kullanarak Kaldırma
	1. Denetim Masası Açın:
		○ Başlat > Denetim Masası > Programlar ve Özellikler > IBM MQ (kurulum_adı)'na tıklayın.
	2. Kaldırma İşlemini Başlatın:
		○ Kaldır veya Uninstall seçeneğine tıklayın ve işlemi onaylayın.
	3. UAC Onayı:
		○ Kullanıcı Hesap Denetimi (UAC) etkinse, yükseltilmiş izinlerle çalıştırma onayını verin.
	4. Tamamlanma:
		○ Kaldırma işlemi tamamlandıktan sonra gerekli adımları bitirin.

2. msiexec ile Komut Satırından Kaldırma
Komut satırını kullanarak IBM MQ'yu sessizce veya etkileşimli olarak kaldırabilirsiniz.
	1. Etkileşimli Kaldırma Komutu:
		○ Kuyruk yöneticisi verilerini kaldırma seçeneği ile:

msiexec /x {product_code} /l*v "c:\removal.log" REMOVE="All" INSTALLATIONNAME="installation_name"
	2. Sessiz Kaldırma Komutları:
		○ Kuyruk yöneticisi verilerini kaldırmadan:

msiexec /x {product_code} /l*v "c:\removal.log" /q REMOVE="All" INSTALLATIONNAME="installation_name"
		○ Kuyruk yöneticisi verilerini kaldırarak (son sunucu kurulumu için geçerli):

msiexec /x {product_code} /l*v "c:\removal.log" /q REMOVE="All" KEEPQMDATA="delete" INSTALLATIONNAME="installation_name"
	3. Kaldırma İşlemi Takibi:
		○ Günlük kaydı (removal.log) üzerinden işlem ilerlemesini kontrol edin.

3. MQParms Kullanarak Kaldırma
MQParms komutuyla kaldırma işlemi gerçekleştirebilirsiniz:
	1. Parametre Dosyası Kullanımı:
		○ MQParms.ini dosyasını düzenleyin ve aşağıdaki değerleri ayarlayın:

[MSI]
ADDLOCAL=""
REMOVE="ALL"
	2. Komut Satırını Kullanarak Kaldırma:

MQParms.exe parameter_file /i "{product_code}"

4. Kurulum Medyası Kullanarak Kaldırma
	1. Kurulum Medyasını Başlatın:
		○ Kurulum dosyasını çift tıklayın ve IBM MQ Kurulumunu başlatın.
	2. Mevcut Kurulumu Seçin:
		○ "Mevcut örneği sürdür veya yükselt" seçeneğini seçin.
	3. Sunucu Özelliklerini Kaldırma:
		○ Kuyruk yöneticisi verilerini kaldırma veya saklama seçeneklerinden birini seçin.
	4. Kaldırma İşlemini Tamamlayın:
		○ "Kaldır" seçeneğine tıklayın ve işlemi tamamlayın.

Son Adımlar
	1. Olay Günlüğünü Kontrol Edin:
		○ Windows olay günlüğünde ID 10005 varsa sistemi yeniden başlatın.
	2. Registry ve Veri Klasörlerini Temizleme (Opsiyonel):
		○ ResetMQ.cmd komut dosyasını çalıştırarak eski kurulum bilgilerini temizleyin.
Bu adımlarla IBM MQ'yu güvenli ve doğru bir şekilde kaldırabilirsiniz.

IBM MQ Advanced for Multiplatforms Kurulumu ve Yönetimi
IBM MQ Advanced, IBM MQ'ya ek olarak gelişmiş özellikler ve araçlar sunan bir lisans seçeneğidir. Bu belgede, IBM MQ Advanced bileşenlerinin kurulumu, yönetimi ve kaldırılmasıyla ilgili kapsamlı bilgiler yer almaktadır.

IBM MQ Advanced Özellikleri
IBM MQ Advanced lisansı, aşağıdaki özelliklere erişim sağlar:
	1. Advanced Message Security (AMS): Mesaj şifreleme ve güvenlik özellikleri.
	2. Managed File Transfer (MFT): Dosya transferi için entegre çözümler.
	3. MQ Telemetry (MQTT): IoT cihazları ve MQTT protokolü üzerinden mesajlaşma desteği.
	4. Replicated Data Queue Managers (RDQM): Yalnızca Linux sistemlerinde yüksek erişilebilirlik ve felaket kurtarma için çoğaltılmış veri kuyruk yöneticileri.

Advanced Message Security (AMS) Kurulumu
Windows'ta AMS Kurulumu
	1. Kurulum Dosyalarına Erişim:
		○ IBM MQ kurulum görüntüsünü edinin.
		○ Setup.exe dosyasını çalıştırarak kurulumu başlatın.
	2. Kurulum Adımları:
		○ Kullanıcı Hesap Denetimi (UAC) aktifse, yükseltilmiş izinleri kabul edin.
		○ "IBM MQ Kurulumu" penceresinde ekrandaki talimatları izleyerek AMS bileşenini seçip yükleyin.
Linux'ta AMS Kurulumu
	1. Hazırlık:
		○ root kullanıcısı olarak oturum açın ve kurulum dosyalarının bulunduğu dizine gidin.
		○ Daha önceki bir kurulum varsa, crtmqpkg komutunu kullanarak benzersiz bir kurulum paketi oluşturun.
	2. Kurulum Komutları:

rpm -iv MQSeriesAMS-V.R.M-F.x86_64.rpm
		○ V, R, M, F: Sırasıyla sürüm, yayın, modifikasyon ve düzeltme paketi seviyesini belirtir.
AMS Kaldırma
	• Linux:

rpm -e MQSeriesAMS-V.R.M-F
	• Windows:
		○ Denetim Masası veya kurulum sihirbazını kullanarak AMS bileşenini kaldırabilirsiniz.

Managed File Transfer (MFT) Kurulumu
Kurulum Bileşenleri
	1. MFT Agent: Kuyruk yöneticisine bağlanarak dosya transferlerini yönetir.
	2. MFT Service: Ek olarak FTP/SFTP protokol desteği sunar.
	3. MFT Logger: Transfer kayıtlarını bir veri tabanına veya dosyaya kaydeder.
	4. MFT Tools: Komut satırı araçları sağlar.
Linux'ta MFT Kurulumu
	1. Hazırlık:
		○ root kullanıcısı olarak oturum açın ve gerekli sistem paketlerini yükleyin.
	2. Kurulum:

rpm -iv MQSeriesFTBase*.rpm MQSeriesFTAgent*.rpm
Windows'ta MFT Kurulumu
	• Kurulum Sihirbazı: IBM MQ kurulum görüntüsünden Setup.exe dosyasını çalıştırarak bileşenleri yükleyin.

MQ Telemetry (MQTT) Kurulumu
Kurulum Adımları
	1. IBM MQ kurulum görüntüsünü kullanarak MQTT bileşenini seçin ve yükleyin.
	2. MQTT Kanallarının Yapılandırılması:
		○ IBM MQ Explorer üzerinden MQTT kanallarını tanımlayın.
		○ define channel komutlarını kullanarak MQTT hizmetini yapılandırın.
Kurulumu Doğrulama
	1. IBM MQ Explorer Kullanarak:
		○ "Örnek Yapılandırma Sihirbazı"nı kullanarak MQTT bileşenini doğrulayabilirsiniz.
	2. Komut Satırı Kullanarak:
		○ MQTT yayın ve abonelik komutlarını test edin.

Replicated Data Queue Managers (RDQM) Kurulumu
RHEL 8/9 Sistemlerinde RDQM Kurulumu
	1. Gerekli Paketlerin Yüklenmesi:

dnf install Advanced/RDQM/PreReqs/el8/drbd-utils-9/*
dnf install Advanced/RDQM/PreReqs/el8/pacemaker-2/*
	2. IBM MQ ve RDQM Yükleme:

dnf install MQSeriesGSKit* MQSeriesServer* MQSeriesRuntime*
dnf install Advanced/RDQM/MQSeriesRDQM*
	3. Pacemaker Kümelenmesi ve RDQM Yapılandırması:
		○ Pacemaker ile yüksek erişilebilirlik veya felaket kurtarma senaryolarını yapılandırın.

IBM MQ Explorer ve Web Sunucusu Kurulumu
IBM MQ Explorer Kurulumu
	• Windows/Linux: Fix Central'dan bağımsız MQ Explorer paketini indirin ve yükleyin.
IBM MQ Web Sunucusu Kurulumu
	• Linux: Standalone IBM MQ Web Sunucusu indirilerek kurulum yapılabilir. Web Sunucusu, MQ Konsolunu ve REST API'sini çalıştırmak için kullanılır.

Sonuç ve Özet
Bu belge, IBM MQ Advanced bileşenlerinin kurulumu ve yönetimi için kapsamlı bir rehber sunmaktadır. Tüm kurulum ve yapılandırma süreçlerini dikkatle takip ederek, IBM MQ Advanced'ın gelişmiş özelliklerinden tam anlamıyla faydalanabilirsiniz

Bakım, Yükseltme ve Geçiş Tanımları
	1. Bakım (Maintenance):
		○ Fix Pack, güvenlik güncellemesi (CSU), ara düzeltme (interim fix) veya Program Geçici Düzeltmesi (PTF) uygulanmasıdır.
		○ Bakım işlemi sonrası kuyruk yöneticisi (queue manager) verileri üzerinde geçiş gerekmemektedir.
		○ Kod seviyesi bir önceki sürüme geri alınabilir.
	2. Yükseltme (Upgrade):
		○ IBM MQ kurulumunun yeni bir sürüme güncellenmesi işlemidir.
		○ Yükseltme sonrası, komut seviyesi değişiyorsa geçiş yapılması gerekir.
		○ Geçiş yapılmadıkça yükseltme geri alınabilir.
	3. Geçiş (Migration):
		○ Kuyruk yöneticisi verilerinin ve yapılandırmasının, yeni kod seviyesi ile uyumlu hale getirilmesidir.
		○ Geçiş işlemi geri alınamaz; bu nedenle eski kod seviyesi ile uyumluluk kaybolur.

IBM MQ Bakım ve Güncellemeler
Bakım Seviyesinin Uygulanması
	• Cumulative Fix Pack veya Güvenlik Güncellemeleri (CSU):
		○ Tüm ara güncellemeleri atlayarak, doğrudan en son düzeltme seviyesini uygulayabilirsiniz.
	• İnterim Düzeltmeler:
		○ IBM destek tarafından sağlanır ve bir sonraki resmi güncellemeye kadar geçici çözüm sunar.
Bakım Seviyesinin Kaldırılması
	• Bakım paketi geri alınabilir ve önceki kod seviyesi eski durumuna getirilebilir.
	• Önemli: Kuyruk yöneticisi geçişi yapılmışsa, bakım seviyesi geri alınsa bile eski kod seviyesi çalıştırılamaz.

Yükseltme Süreci
	1. Hazırlık:
		○ Yedek alın: Kuyruk yöneticisi verilerinizi ve yapılandırmanızı yedekleyin.
		○ Sistemin gereksinimleri karşıladığından emin olun: IBM MQ'nun desteklediği işletim sistemi ve bağımlılıklar için SPCR aracı kullanılabilir.
	2. Kod Seviyesinin Yükseltilmesi:
		○ Kod seviyesi yükseltme sonrası kuyruk yöneticisi geçişi gerekebilir.
		○ Kuyruk yöneticisi geçişi tamamlanana kadar eski seviyeye geri dönmek mümkün olabilir.
	3. Yükseltme Türleri:
		○ Mevcut kurulum üzerine kurulum: Aynı dizine yeni kod seviyesi yüklenir.
		○ Yan yana kurulum: Farklı bir dizine yeni kurulum yapılır ve eski sürüm korunur.
		○ Eski sürümün kaldırılması: Önceki sürüm kaldırılır, ardından yeni sürüm kurulur.

Geçiş Süreci
Kuyruk Yöneticisi Geçişi
	• Otomatik Geçiş: İlk kez yeni kod seviyesi ile başlatıldığında otomatik gerçekleşir.
	• Manuel Geçiş: Yeni özellikleri etkinleştirmek için komutlar kullanılır.

strmqm -e CMDLEVEL=940
		○ CMDLEVEL: Kuyruk yöneticisinin çalışacağı yeni komut seviyesini belirtir.
Uygulama Geçişi
	• Uygulama kodlarının yeni API'ler veya özelliklerle uyumlu hale getirilmesi gerekir.
	• Öneri: Test ortamında yeni API'ler ve parametrelerle uyumluluk kontrol edilmelidir.

Platforma Özgü Bakım ve Yükseltme İşlemleri
Windows Üzerinde IBM MQ
	• Bakım Güncellemeleri:
		○ Yeni sürümü yükseltmek için doğrudan mevcut kurulum üzerine yükleme yapabilirsiniz.
		○ Güncellemeleri kaldırmak için mevcut IBM MQ kurulumunu kaldırıp, eski sürümü yeniden yükleyin.
Linux Üzerinde IBM MQ
	• Bakım Uygulaması:

rpm -Uvh MQSeries*.rpm
dnf upgrade MQSeries*
	• Bakım Kaldırma:

rpm --oldpackage -Uvh MQSeries*.rpm
dnf downgrade MQSeries*
	• Ubuntu için:

apt-get -y --allow-downgrades install "ibmmq-*"

Çoklu Sürümler ve Geçiş Yönetimi
	• Çoklu Kurulum: Aynı sunucuda farklı IBM MQ sürümleri çalıştırılabilir (ör. test ve üretim ortamları).
	• Geçiş Sırası:
		○ Yükseltme -> Kuyruk Yöneticisi Geçişi -> Uygulama Testi.

Bakım ve Yükseltme Kapsamındaki Önemli Hususlar
	• Yedekleme her zaman önceliklidir. Kuyruk yöneticisi, kanallar ve veriler yedeklenmeden yükseltme yapılmamalıdır.
	• Yeni sürümdeki özelliklerin uygulanması öncesinde geçiş sonrası performans ve uyumluluk testleri yapılmalıdır.
	• Kod Seviyesinin Kontrolü:
dspmqver




1. Migration Nedir?
Migration, mevcut IBM MQ programlarının ve verilerinin yeni bir kod seviyesine uyarlanmasıdır. Bu, iki şekilde yapılabilir:
	• Zorunlu migration: Büyük sürüm değişiklikleri sonrası kuyruk yöneticisi (queue manager) veya istemci yapılandırmalarının güncellenmesi.
	• Opsiyonel migration: Bakım seviyesinde (maintenance level) yapılan küçük değişiklikler için, ek işlevsellik gerektiriyorsa.
Önemli Notlar:
	• Migration genellikle kuyruk yöneticisinin ilk başlatılmasında otomatik olarak gerçekleştirilir.
	• Bakım seviyeleri arasındaki geçişlerde kuyruk yöneticisi migration’ı gerekmeyebilir.

2. Migration Öncesi Hazırlık
A. Verilerinizi Yedekleyin
	• Kuyruk yöneticisi verilerini ve yapılandırmalarını yedekleyin.
	• dmpmqcfg komutuyla mevcut konfigürasyonu bir metin dosyasına kaydedin:

dmpmqcfg -m QmgrName > config_backup.txt
B. Uyumlu Sürüm ve Yolları İnceleyin
	• Mevcut sürümden hedef sürüme olan migration yollarını kontrol edin:
		○ IBM MQ 8.0 → IBM MQ 9.4 gibi doğrudan geçişler desteklenmez. Ara sürüm (interim version) kullanılmalıdır.
	• Örnek Migration Yolları:
	Kaynak Sürüm	Hedef Sürüm	Ara Sürüm
	MQ 8.0	MQ 9.4	MQ 9.0
	MQ 9.1	MQ 9.4	Yok
C. Kuyruk Yöneticisi Cluster’ları
Cluster yapılandırmalarında önce tam depo yöneticileri (full repository managers), ardından kısmi depo yöneticileri (partial repository managers) güncellenmelidir.

3. Migration Süreci
A. Kuyruk Yöneticisi Migration
	1. Tüm Kuyruk Yöneticilerini ve Uygulamaları Kapatın:

endmqm QmgrName
endmqlsr
endmqweb
	2. Migration’a Başlayın:
		○ Kuyruk yöneticisini yeni seviyede başlatın:

strmqm QmgrName
		○ Yeni işlevler kullanmak için COMMAND LEVEL değerini yükseltin:

ALTER QMGR COMMANDLEVEL(940)
	3. Migration Tamamlandıktan Sonra Kontrol Edin:
		○ dspmqver komutuyla sürümü doğrulayın.
		○ Yeni objelerin varsayılan değerlere ayarlandığını kontrol edin.
B. İstemci Migration
	• İstemci tarafında ayar dosyalarını (mqclient.ini) güncelleyin.
	• Yeni istemci bağlantı yapılandırmalarını (CCDT) test edin ve dağıtın.

4. Migration Seçenekleri
A. Tek Aşamalı Migration (Single-Stage Migration)
	• Mevcut IBM MQ kurulumu tamamen yeni sürümle değiştirilir.
	• Kuyruk yöneticileri ve uygulamalar yeni kurulumla otomatik olarak ilişkilendirilir.
B. Yan Yana Migration (Side-by-Side Migration)
	• Aynı sunucuda eski ve yeni IBM MQ sürümleri yan yana kurulur.
	• Kuyruk yöneticileri ve uygulamalar aşamalı olarak yeni sürüme geçirilir.
C. Çok Aşamalı Migration (Multi-Stage Migration)
	• Yan yana kurulumla benzer, ancak her bir kuyruk yöneticisi veya uygulama birer birer yeni sürüme geçirilir.

5. Uyum, Uyumluluk ve Çalışabilirlik
	• Coexistence: Aynı sunucuda birden fazla IBM MQ sürümünün çalışabilmesi.
	• Compatibility: Daha eski sürümlerle çalışabilirlik.
	• Interoperability: Farklı sürümler arasında mesaj alışverişi ve bağlantı sağlama yeteneği.

6. Dikkat Edilmesi Gereken Özel Durumlar
	• AMQP Migration: IBM MQ 9.4.0’dan itibaren CMS keystore kullanımı desteklenmez. PKCS12’ye dönüştürülmesi gerekir.
	• Cluster Migration: Yeni özellikler eski cluster yöneticileri tarafından saklanamayabilir. Full repositories önce güncellenmelidir.

IBM MQ'nun Windows Üzerinde Migrasyonu
IBM MQ’nun Windows ortamındaki migrasyon işlemleri, mevcut sürümden daha yeni bir sürüme geçişi ve/veya mevcut yapılandırmanın korunmasını içerir. Bu kılavuz, IBM MQ’yu Windows üzerinde nasıl migrate edeceğiniz konusunda ayrıntılı bir rehber sunar.

1. Migrasyona Başlamadan Önce
A. Ön Hazırlıklar
	1. Gereksinimleri İnceleyin:
		○ Hedef sürüm için sistem gereksinimlerini kontrol edin.
System Requirements for IBM MQ
		○ Migration yollarını inceleyin:
			§ IBM MQ 7.5 veya önceki sürümlerden IBM MQ 9.4’e doğrudan geçiş mümkün değildir. İlk olarak ara bir sürüme (ör. MQ 8.0 veya MQ 9.0) geçiş yapmalısınız.
		○ Verilerinizi Yedekleyin:
Kuyruk yöneticisi ve istemci verilerinin bir kopyasını alın. dmpmqcfg komutunu kullanarak mevcut konfigürasyonu yedekleyebilirsiniz:

dmpmqcfg -m QueueManagerName > backup_config.mqsc
	2. Yükleme Yöntemi Seçimi:
		○ Single-Stage Migration: Mevcut IBM MQ sürümünü tamamen yenisiyle değiştirir.
		○ Side-by-Side Migration: Yeni sürüm, mevcut sürümle yan yana kurulur.
		○ Multi-Stage Migration: Uygulamalar ve kuyruk yöneticileri kademeli olarak yeni sürüme geçirilir.

2. Migrasyon Süreci
A. Kuyruk Yöneticisinin Migrasyonu
	1. Tüm İşlemleri Durdurun:
Kuyruk yöneticisi ve ilişkili uygulamaları kapatın:

endmqm QueueManagerName
endmqlsr
	2. IBM MQ Kurulumunu Güncelleyin:
		○ Yeni sürümü mevcut sürüm üzerine yükleyebilir veya yan yana kurulum yapabilirsiniz.
		○ Eğer yan yana kurulum yapıyorsanız, setmqinst komutuyla yeni kurulumun birincil kurulum (primary installation) olduğunu belirtin:

setmqinst -i -n InstallationName
	3. Kuyruk Yöneticisini Başlatın ve Komut Seviyesini Güncelleyin:
Kuyruk yöneticisini başlattıktan sonra komut seviyesini yükseltin:

strmqm QueueManagerName
ALTER QMGR COMMANDLEVEL(940)
	4. Log Dosyalarını Kontrol Edin:
Eğer diskleriniz Advanced Format (4096 byte) diskler ise log dosyalarını migrate edin:

migmqlog -m QueueManagerName

B. İstemci Migrasyonu
	1. Tüm İstemci Etkinliklerini Durdurun:

endmqm -c
	2. Yeni Sürümü Kurun:
		○ Yeni istemci sürümünü yükleyin.
		○ Eğer yan yana kurulum yaptıysanız, istemci bağlantı tanım tablosunu (CCDT) kontrol edin ve gerekirse güncelleyin.

3. Özel Durumlar
A. AMQP Kullanımı
IBM MQ 9.4.0’dan itibaren AMQP kanalları CMS keystore dosyalarını desteklemez. Bu durumda:
	1. Keystore’u PKCS12 formatına dönüştürün.
	2. AMQP yapılandırmalarını uygun şekilde güncelleyin.
B. MSCS Yapılandırması
Microsoft Cluster Service (MSCS) yapılandırmalarında:
	• Her bir düğümü (node) sırayla migrate edin.
	• Pasif düğümleri güncelleme sırasında çevrimdışı (offline) tutun.

4. Migration Sonrası Kontroller
	1. Kuyruk yöneticisini ve istemcileri başlatarak işlevselliğini kontrol edin.
	2. Mevcut test senaryolarınızı kullanarak sistemin düzgün çalıştığını doğrulayın.
	3. Yeni özellikleri test edin ve kullanmaya başlayın.

AIX ve Linux'ta IBM MQ Migrasyonu
AIX ve Linux ortamlarında IBM MQ migrasyonu, genellikle daha fazla esneklik sunan bir süreçtir. Bu platformlarda, farklı sürümlerin yan yana kurulabilmesi ve çoklu kurulum desteği gibi özellikler, geçiş sürecini kolaylaştırır. İşte detaylı bir rehber:

1. Hazırlık Aşaması
Migrasyona başlamadan önce aşağıdaki adımları tamamlayın:
	1. Sistem Gereksinimlerini Doğrulayın:
		○ IBM MQ’nun yeni sürümü için donanım ve yazılım gereksinimlerini kontrol edin.
		○ Örneğin, IBM MQ 9.4 için minimum işletim sistemi sürümü gereksinimleri gibi.
	2. Mevcut Sürüm Kontrolü:
		○ dspmqver komutunu kullanarak mevcut IBM MQ sürümünüzü kontrol edin.

dspmqver
	3. Yedekleme:
		○ Kuyruk yöneticisi verilerini yedekleyin:

dmpmqcfg -m <QueueManagerName> -a > backup.mqsc
		○ Veritabanlarını ve log dosyalarını yedekleyin:

tar -czvf mq_data_backup.tar.gz /var/mqm
	4. Yükleme Dosyalarını Hazırlayın:
		○ IBM MQ'nun yeni sürümüne ait yükleme dosyalarını indirin ve doğrulayın.

2. Migrasyon Yöntemleri
AIX ve Linux'ta aşağıdaki üç yöntem kullanılabilir:
	1. Tek Aşamalı Migrasyon (Single-stage):
		○ Eski sürüm tamamen kaldırılır ve yerine yeni sürüm yüklenir.
		○ Avantajı: Basit ve hızlıdır.
		○ Dezavantajı: Downtime gerektirir.
	2. Yan Yana Migrasyon (Side-by-side):
		○ Eski ve yeni sürüm aynı anda kurulur.
		○ Yeni sürüm test edildikten sonra eski sürüm kaldırılır.
		○ Avantajı: Kesintisiz çalışma sağlar.
		○ Dezavantajı: Daha fazla disk alanı kullanımı gerektirir.
	3. Çok Aşamalı Migrasyon (Multi-stage):
		○ Eski ve yeni sürüm birlikte çalışır.
		○ Kuyruk yöneticileri ve uygulamalar kademeli olarak yeni sürüme taşınır.
		○ Avantajı: En az riskle geçiş.
		○ Dezavantajı: Daha fazla yönetim gerektirir.

3. Adım Adım Migrasyon
A. Tek Aşamalı Migrasyon
	1. Eski Sürümü Durdurun:

endmqm -i <QueueManagerName>
	2. Yedekleme Yapın:

dmpmqcfg -m <QueueManagerName> -a > backup.mqsc
tar -czvf mq_backup.tar.gz /var/mqm
	3. Eski Sürümü Kaldırın:

rpm -qa | grep MQSeries | xargs rpm -e
	4. Yeni Sürümü Yükleyin:

rpm -ivh MQSeries*.rpm
	5. Yedeklemeleri Geri Yükleyin ve Kuyruk Yöneticisini Başlatın:

tar -xzvf mq_backup.tar.gz -C /
strmqm <QueueManagerName>
B. Yan Yana Migrasyon
	1. Yeni Sürümü Yan Yana Kurun:

rpm -ivh MQSeries*.rpm --prefix=/opt/mqm_new
	2. Yeni Sürümde Test Kuyruk Yöneticisi Oluşturun ve Test Edin:

crtmqm TESTQM
strmqm TESTQM
	3. Eski Kuyruk Yöneticilerini Yeni Sürüme Taşıyın:
		○ Eski sürümde dmpmqcfg ile yapılandırmaları alın ve yeni sürüme aktarın.
C. Çok Aşamalı Migrasyon
	1. Yeni Sürümü Yan Yana Kurun.
	2. Bir Kuyruk Yöneticisini Yeni Sürüme Taşıyın:

bash
Copy code
endmqm -i <QueueManagerName>
dspmqver -m <QueueManagerName> -o all
	3. Uygulamaları Yeni Sürüme Bağlayın:
		○ setmqinst ve setmqenv komutlarını kullanarak ortam değişkenlerini ayarlayın:

setmqenv -n InstallationName

4. Önemli Noktalar
	1. AMQP ve TLS Geçişi:
		○ CMS anahtar depolarını PKCS12 formatına dönüştürün.

runmqckm -convert -type cms -new_format pkcs12 ...
	2. Performans Testi:
		○ Kuyruk yöneticilerini başlattıktan sonra amqsput ve amqsget komutlarıyla testler yapın.
	3. Geri Dönüş Planı:
		○ Gerekirse, yedekleme dosyalarınızı kullanarak eski sürüme dönün.

1. Genel Hazırlık
Migrasyon öncesinde şu adımları tamamlayın:
	1. Tam Yedekleme Yapın:
		○ Tüm kuyruk yöneticisi yapılandırmalarını ve verilerini yedekleyin:

dmpmqcfg -m <QueueManagerName> -a > cluster_backup.mqsc
tar -czvf cluster_data_backup.tar.gz /var/mqm
	2. Geçiş Planı Oluşturun:
		○ Kümeyi oluşturan tüm kuyruk yöneticilerinin rollerini belirleyin:
			§ Tam depo (Full Repository) Kuyruk Yöneticileri: Kümeye ait tüm yapılandırma bilgilerini depolar.
			§ Kısmi depo (Partial Repository) Kuyruk Yöneticileri: Sadece kendi ihtiyaç duyduğu bilgileri depolar.
	3. Yeni Sürüm Gereksinimlerini Kontrol Edin:
		○ Kümeye katılacak tüm kuyruk yöneticileri aynı sürümde olmalıdır.
		○ Tam depo kuyruk yöneticileri öncelikli olarak geçiş yapılmalıdır.

2. Migrasyon Yöntemleri
Kümedeki kuyruk yöneticileri için iki temel migrasyon yöntemi vardır:
	1. Toplu Migrasyon (All-at-Once):
		○ Tüm kuyruk yöneticileri aynı anda yükseltilir.
		○ Avantaj: Daha kısa sürede tamamlanır.
		○ Dezavantaj: Daha fazla kesinti riski taşır.
	2. Aşamalı Migrasyon (Staged):
		○ Kuyruk yöneticileri tek tek yükseltilir.
		○ Önce tam depo kuyruk yöneticileri yükseltilir, ardından kısmi depo kuyruk yöneticileri geçiş yapılır.
		○ Avantaj: Daha az kesinti riski.
		○ Dezavantaj: Daha uzun sürer.

3. Adım Adım Migrasyon
A. Tam Depo Kuyruk Yöneticilerini Migrasyon
	1. Tam Depo Kuyruk Yöneticisini Durdurun:

endmqm -i <FullRepositoryQueueManager>
	2. Tam Depo Yöneticisinin Verilerini Yedekleyin:

dmpmqcfg -m <FullRepositoryQueueManager> -a > full_repo_backup.mqsc
	3. Yeni Sürümü Yükleyin:
		○ Yeni IBM MQ sürümünü yan yana veya tek aşamalı olarak yükleyin.
	4. Tam Depo Kuyruk Yöneticisini Başlatın:

strmqm <FullRepositoryQueueManager>
	5. Küme Bilgilerini Yenileyin:
		○ Küme bilgilerinin güncellenmesi için REFRESH CLUSTER komutunu çalıştırın:

echo "REFRESH CLUSTER(<ClusterName>)" | runmqsc <FullRepositoryQueueManager>

B. Kısmi Depo Kuyruk Yöneticilerini Migrasyon
	1. Kısmi Depo Kuyruk Yöneticisini Migrasyon:
		○ Yukarıdaki adımları tekrar ederek kısmi depo kuyruk yöneticilerini sırayla yeni sürüme yükseltin.
	2. Kısmi Depoları Yenileyin:
		○ Her bir yükseltmeden sonra, kısmi depo kuyruk yöneticisini yenileyin:

echo "REFRESH CLUSTER(<ClusterName>)" | runmqsc <PartialRepositoryQueueManager>

4. Dikkat Edilmesi Gerekenler
	1. Yeni Özelliklerin Kullanımı:
		○ Migrasyon tamamlanana kadar yeni özellikleri kullanmaktan kaçının. Yeni özellikler eski sürümde uyumsuzluklara yol açabilir.
	2. REFRESH CLUSTER Komutu:
		○ Büyük kümelerde bu komut performansı geçici olarak düşürebilir. Komut sonrası otomatik güncellemeler de sistem kaynaklarını etkileyebilir.
	3. Karışık Sürüm (Mixed Version) Yönetimi:
		○ Farklı sürümlerin aynı kümede geçici olarak çalışması mümkündür. Ancak, tam depo kuyruk yöneticileri her zaman en güncel sürümde olmalıdır.

5. Özel Durumlar
A. Yeni Bir Kuyruk Yöneticisinin Eklenmesi:
Yeni kuyruk yöneticisini kümeye eklemek için şu adımları izleyin:
	1. Kuyruk Yöneticisini Oluşturun:

crtmqm <NewQueueManager>
	2. Kuyruk Yöneticisini Küme ile İlişkilendirin:

DEFINE CHANNEL('TO.<ClusterName>') CHLTYPE(CLUSRCVR) CLUSTER('<ClusterName>') ...
B. Küme Yeniden Yapılandırması:
Kümedeki yapılandırma değişiklikleri sırasında dikkatli olun. Tüm kuyruk yöneticilerinin küme bilgilerini doğru şekilde aldığından emin olun.

BM MQ Yüksek Erişilebilirlik (High Availability) Migrasyonu
Yüksek erişilebilirlik (HA) konfigurasyonları, IBM MQ kuyruk yöneticilerinin bir sunucudan diğerine kesintisiz geçiş yapmasını sağlar. Bu yapılandırmalar, uygulama kesintisini en aza indirmek için tasarlanmıştır. Migrasyon sürecinde bu yapılandırmaları düzgün bir şekilde taşımak, sistemin kararlılığını korumak açısından kritik öneme sahiptir.

1. Genel Hazırlık
Migrasyon öncesinde şu adımları tamamlayın:
	1. Tam Yedekleme Yapın:
		○ Kuyruk yöneticisi verilerini ve yapılandırmalarını yedekleyin:

dmpmqcfg -m <QueueManagerName> -a > backup.mqsc
tar -czvf /mq/backup/<QueueManagerName>_data.tar.gz /var/mqm/qmgrs/<QueueManagerName>
	2. Yeni Sürüm Gereksinimlerini Kontrol Edin:
		○ Yeni sürümle uyumluluğu sağlamak için sistem gereksinimlerini gözden geçirin:
			§ İşletim sistemi sürümü
			§ Depolama gereksinimleri
			§ Ağ ayarları
	3. HA Grubu Konfigürasyonunu Doğrulayın:
		○ Tüm düğümlerin aynı ağda ve kümede bulunduğundan emin olun.
		○ Active-Standby veya Multi-Instance yapılandırmalarını kontrol edin.

2. Multi-Instance Kuyruk Yöneticisi Migrasyonu
Multi-instance kuyruk yöneticisi yapılandırması, birincil (active) ve yedek (standby) kuyruk yöneticilerinin aynı veritabanını paylaşmasına olanak tanır.
A. Migrasyon Süreci:
	1. Standby Kuyruk Yöneticisini Durdurun:

endmqm -x <QueueManagerName>
	2. Birincil Kuyruk Yöneticisini Durdurun ve Yedek Alın:

endmqm -i <QueueManagerName>
tar -czvf /backup/<QueueManagerName>_data.tar.gz /var/mqm/qmgrs/<QueueManagerName>
	3. Yeni Sürümü Yükleyin:
		○ IBM MQ'yu yükseltilmiş sürüme kurun.
	4. Standby Düğümünü Yükseltin:
		○ Standby düğümde IBM MQ yazılımını güncelleyin.
		○ Yedek alınan verileri yeni düğüme geri yükleyin.
	5. Birincil Kuyruk Yöneticisini Başlatın:

strmqm <QueueManagerName>
	6. Standby Kuyruk Yöneticisini Yeniden Başlatın:

strmqm -x <QueueManagerName>
	7. HA Durumunu Doğrulayın:
		○ Kuyruk yöneticisi durumunu kontrol edin:

dspmq -o status

3. High Availability (HA) Kümeleri Migrasyonu
HA kümeleri, aktif ve pasif sunucular arasında yük devri (failover) sağlar.
A. Migrasyon Süreci:
	1. Pasif Sunucuyu Kümeden Çıkarın:
		○ Pasif sunucuyu devre dışı bırakın:

rdqmadm -s
	2. Pasif Sunucuyu Yükseltin:
		○ IBM MQ ve HA yazılımını (ör. Pacemaker, DRBD) yeni sürüme yükseltin.
	3. Aktif Sunucuda Yedek Alma ve Güncelleme:
		○ Aktif sunucuyu durdurun, yedek alın ve yeni sürüme yükseltin.
	4. Kümeyi Yeniden Etkinleştirin:
		○ Tüm düğümleri HA kümesine geri ekleyin:

rdqmadm -r
	5. Failover İşlemini Test Edin:
		○ Aktif sunucuya yük devrini test edin.

4. Özel Durumlar
A. Yeni Düğümler Eklemek: Yeni bir düğümü HA kümesine eklemek için şu adımları izleyin:
	1. Düğümde IBM MQ ve HA yazılımını kurun.
	2. Kuyruk yöneticisinin yapılandırmasını aktarın.
	3. Düğümü HA grubuna ekleyin:

rdqmadm -a <NodeName>
B. Disaster Recovery (DR) Migrasyonu:
	• DR konfigürasyonunda, önce ikincil (recovery) sunucuyu yükseltin.
	• Yedekleme ve geri yükleme işlemini tamamladıktan sonra, birincil sunucuyu yükseltin.

5. Dikkat Edilmesi Gerekenler
	1. Kesintisiz İşlemler İçin Öncelik:
		○ Önce standby düğümleri yükseltin.
		○ Kuyruk yöneticisi üzerinde çalışan işlemleri kesmeden aktif düğümde geçiş yapın.
	2. Yük Devri Testleri:
		○ Yük devri işlemlerini simüle ederek sistemin yeni yapılandırma ile uyumluluğunu doğrulayın.
	3. Sürüm Uyumluluğu:
		○ Tüm düğümleri aynı sürümde tutarak uyumluluk sorunlarını önleyin.

IBM MQ Replicated Data Queue Manager (RDQM) Migrasyonu
Replicated Data Queue Manager (RDQM), yüksek kullanılabilirlik ve veri replikasyonu sağlayan bir IBM MQ çözümüdür. Bu yapılandırma, aynı anda birden fazla düğümde veri tutar ve herhangi bir düğüm arızasında işlemleri hızlıca başka bir düğüme aktarır. Migrasyon süreci, tüm düğümlerin sıralı bir şekilde yükseltilmesini gerektirir.

1. RDQM Migrasyonuna Hazırlık
A. Genel Hazırlık Adımları
	1. Yedekleme Yapın:
		○ Kuyruk yöneticisi verilerini yedekleyin:

dmpmqcfg -m <QueueManagerName> -a > /backup/<QueueManagerName>.mqsc
tar -czvf /backup/<QueueManagerName>_data.tar.gz /var/mqm/qmgrs/<QueueManagerName>
	2. Yeni Sürüm Gereksinimlerini Kontrol Edin:
		○ IBM MQ'nun yeni sürümünün RDQM için desteklediği işletim sistemi ve diğer gereksinimleri sağlayın:
			§ RHEL 8 veya 9 kullanmanız gerekebilir; RHEL 7 desteği yoktur.
	3. Yedekleme ve Test:
		○ Kuyruk yöneticisi verilerini ve konfigürasyonlarını yeni bir test ortamında çalıştırarak doğrulayın.

2. RDQM Migrasyon Süreci
RDQM migrasyonu sırasında, düğümleri birer birer yükseltmeniz gerekir. Her düğümde sırasıyla RDQM servisini durdurup yükseltmeyi tamamlayabilirsiniz.
A. Adım Adım RDQM Migrasyonu:
	1. İlk Düğümü (Standby) Durdurun ve Yükseltin:
		○ HA grubunu askıya alın:

rdqmadm -s
		○ IBM MQ ve RDQM yazılımını kaldırın:

rpm -qa | grep MQSeries | xargs dnf -y remove
rpm -qa | grep linbit | xargs dnf -y remove
rpm -qa | grep drbd | xargs dnf -y remove
		○ DRBD modülünün yüklü olmadığını doğrulayın:

lsmod | grep drbd
		○ Yeni sürümü yükleyin:

dnf install MQSeriesServer MQSeriesRDQM
		○ HA grubunu yeniden başlatın:

rdqmadm -r
	2. İkinci Düğüm için Aynı İşlemleri Tekrarlayın:
		○ İlk düğümden sonra, ikinci düğümde aynı işlemleri uygulayın.
	3. Son Düğümü (Primary) Yükseltin:
		○ Son düğümde de yukarıdaki işlemleri uygulayın ve birincil düğümü aktif duruma getirin.
	4. Kuyruk Yöneticisini Kontrol Edin:
		○ Kuyruk yöneticisinin düzgün çalıştığını doğrulamak için şunları çalıştırın:

dspmq -o status

3. Disaster Recovery (DR) RDQM Migrasyonu
A. DR Konfigürasyonu Yükseltme:
	1. Yedek (Secondary) Düğümü Yükseltin:
		○ Yedek düğümde RDQM ve IBM MQ yazılımlarını kaldırın ve yeni sürümü yükleyin.
	2. Failover Yapın:
		○ DR kuyruk yöneticisini yedek düğüme aktararak çalıştırın:

rdqmadm -f
	3. Ana (Primary) Düğümü Yükseltin:
		○ Ana düğümde RDQM yazılımını kaldırıp yükseltmeyi tamamlayın.
	4. Orijinal Rolleri Geri Yükleyin:
		○ Kuyruk yöneticilerini tekrar ana düğüme aktarın:

rdqmadm -m

4. Önemli Notlar ve İpuçları
	1. Aşamalı Yükseltme:
		○ Her düğümü birer birer yükseltin. Düğümler arasında farklı sürümleri çalıştırmaktan kaçının.
	2. Replikasyon Bağlantılarını Doğrulayın:
		○ Yeni sürümden sonra replikasyonun düzgün çalıştığından emin olun:

rdqmadm -q
	3. Veri Kaybını Önleme:
		○ Tüm işlemleri durdurup mevcut verileri yedekleyin. Özellikle DR ortamlarında failover sırasında veri kaybını engelleyin.

5. Migrasyon Sonrası Testler
Migrasyon tamamlandıktan sonra şu testleri gerçekleştirin:
	• Bağlantı Testi: Kuyruk yöneticilerinin birbirine bağlanabildiğini doğrulayın.
	• Failover Testi: Yük devri işlemlerini test ederek sistemin yüksek erişilebilirlik vaatlerini sağladığını kontrol edin.
	• Performans Testleri: Yeni sürümün, beklenen performansı sağladığından emin olun.


IBM MQ Güvenliği Nedir?
IBM MQ güvenliği, mesajların gizliliğini, bütünlüğünü ve erişim yetkilendirmesini koruyarak sistemler arası güvenli iletişim sağlamayı amaçlar. IBM MQ güvenlik mekanizmaları; kimlik doğrulama, yetkilendirme, mesaj şifreleme, veri bütünlüğü ve denetleme gibi farklı alanlarda kapsamlı çözümler sunar.

IBM MQ Güvenlik Bileşenleri
1. Kimlik Doğrulama (Identification and Authentication)
Kimlik doğrulama, bir kullanıcı veya uygulamanın gerçekten iddia ettiği kişi veya uygulama olduğunu kanıtlama sürecidir.
	• X.509 Sertifikaları: Kullanıcı veya uygulamalar, X.509 dijital sertifikaları kullanarak tanımlanabilir ve doğrulanabilir. Bu sertifikalar, SSL/TLS kanallarında güvenli bir bağlantı kurmak için kullanılabilir.
	• MQCSP Yapısı: Kullanıcı adı ve şifre bilgilerini içeren MQCSP (Connection Security Parameters) yapısı, uygulamaların güvenli bir şekilde bağlanması için kullanılır. Ancak bu bilgilerin güvenli bir ağ bağlantısı üzerinden gönderilmesi önemlidir.
	• PAM Desteği: Linux ve AIX platformlarında, Pluggable Authentication Module (PAM) kimlik doğrulama mekanizması desteklenir.

2. Yetkilendirme (Authorization)
Yetkilendirme, sistemdeki kaynaklara yalnızca yetkili kullanıcıların erişmesini sağlamak için kullanılır.
	• Object Authority Manager (OAM): IBM MQ nesnelerine erişim yetkileri, OAM üzerinden yönetilir. Kullanıcılara veya gruplara, kuyruğa mesaj yazma veya okuma gibi belirli işlemleri gerçekleştirme yetkisi verilebilir.
	• Kanallar İçin Yetkilendirme: Kanalların yalnızca yetkilendirilmiş kullanıcılar tarafından yönetilmesi sağlanabilir. MCAUSER özelliği, belirli bir kanal üzerinden bağlantı yapan kullanıcıların yetkilendirilmesini sağlar.
	• LDAP Yetkilendirmesi: Yerel kullanıcı kimliklerini kullanmak yerine, LDAP sunucuları üzerinden yetkilendirme yapılabilir. Bu, özellikle büyük ve dağınık sistemlerde yönetim kolaylığı sağlar.

3. Mesaj Gizliliği (Message Confidentiality)
Mesaj gizliliği, mesajların yalnızca yetkili taraflarca görülebilmesini sağlar.
	• TLS Şifreleme: TLS protokolü, mesajların ağ üzerinden taşınırken şifrelenmesini sağlar. CipherSpec tanımlarıyla TLS bağlantıları için şifreleme algoritmaları belirlenebilir.
	• Advanced Message Security (AMS): AMS, mesajların uygulama düzeyinde şifrelenmesini ve imzalanmasını sağlar. Bu, mesajların güvenliğini yalnızca taşıma sırasında değil, aynı zamanda kuyrukta depolanırken de sağlar.
	• Z/OS Veri Şifreleme: Z/OS platformunda, veriler aktif günlük dosyaları veya paylaşılan mesaj veri setleri (SMDS) üzerinde şifrelenebilir.

4. Veri Bütünlüğü (Message Integrity)
Veri bütünlüğü, mesajların herhangi bir değişikliğe uğramadığını doğrulamak için kullanılır.
	• TLS İle Veri Bütünlüğü: TLS kullanıldığında, kullanılan CipherSpec'e bağlı olarak veri bütünlüğü sağlanır.
	• Dijital İmzalar: Mesajlara dijital imza eklenerek, mesajın gönderildiği andan itibaren değiştirilmediği kanıtlanabilir.

5. Denetleme (Auditing)
Denetleme, sistemde gerçekleşen güvenlik ihlallerini veya yetkisiz erişim girişimlerini izleme ve raporlama sürecidir.
	• Olay Mesajları: Yetki ihlalleri gibi olaylar, olay mesajları aracılığıyla raporlanabilir.
	• IBM MQ Explorer: IBM MQ Explorer, sistemin güvenlik durumunu kontrol etmek için kullanılabilir.

6. Gelişmiş Mesaj Güvenliği (Advanced Message Security - AMS)
AMS, mesajların şifrelenmesini ve imzalanmasını sağlayan ek bir güvenlik katmanıdır.
	• Mesaj Politikaları: Mesajların şifreleme ve imzalama algoritmaları, AMS güvenlik politikaları aracılığıyla belirlenir.
	• Keystore ve Sertifikalar: AMS, şifreleme için keystore ve dijital sertifikaları kullanır.

7. IBM MQ Konsol ve REST API Güvenliği
	• Kullanıcı Doğrulama: IBM MQ Konsolu ve REST API kullanıcıları, yerel işletim sistemi, LDAP veya SAF gibi farklı kayıt sistemleri aracılığıyla doğrulanabilir.
	• Yetki Seviyeleri: Kullanıcılar, yalnızca atanmış rollerine uygun işlemleri gerçekleştirebilir. Örneğin, mesajlaşma işlemleri için MQWebUser rolü atanmalıdır.
	• Token ve Sertifika Doğrulama: Kullanıcılar, LTPA token veya istemci sertifikaları ile doğrulanabilir.

8. Şifreleme Anahtarları ve Sertifika Yönetimi
IBM MQ, şifreleme anahtarları ve sertifikaların yönetimi için runmqakm ve runmqktool komutlarını sağlar.
	• Keystore Yönetimi: Şifreleme anahtarları, sertifikalar ve sertifika istekleri için CMS veya PKCS #12 formatında keystore oluşturulabilir.
	• FIPS Uyumluluğu: runmqakm komutu, FIPS uyumlu şifreleme algoritmaları sunar.

9. Kanal Güvenliği
Kanallar, iletişimde güvenlik sağlamak için aşağıdaki yöntemlerle korunabilir:
	• Kanal Yetkilendirme Kuralları (CHLAUTH): Kanallar üzerinden bağlanan kullanıcıların yetkilendirilmesi.
	• SSL/TLS Desteği: Kanallarda şifreleme ve sertifika doğrulama kullanımı.

10. Parola Koruma
IBM MQ, konfigürasyon dosyalarındaki şifreleri korumak için AES-128 şifreleme mekanizması kullanır.
	• runmqicred Komutu: Şifrelerin şifrelenmesi ve güvenli bir şekilde saklanması.
