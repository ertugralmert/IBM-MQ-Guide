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




**********


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


***********************

• mqm Kullanıcısı ve Grubu
	• Eğer sistemde yoksa, IBM MQ kurulum süreci otomatik olarak mqm grubunu ve mqm kullanıcısını oluşturur. Bu kullanıcı:
		○ IBM MQ ile ilişkili kaynaklara sahip olur.
		○ Varsayılan olarak /var/mqm ana dizinine atanır.
	• Ancak, UID veya GID’nin diğer makinelerle uyumlu olması gerekiyorsa ya da merkezi bir kullanıcı yönetimi (örneğin, Active Directory) kullanılıyorsa, manuel oluşturmak gerekebilir. 
groupadd mqm
useradd -g mqm -d /var/mqm mqm

• Dosya SistemleriIBM MQ'nun düzgün çalışması için aşağıdaki dosya sistemleri yapılandırılmalıdır:
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
• Kernel AyarlarıIBM MQ’nun başarılı bir şekilde çalışması için kernel ayarları optimize edilmelidir:
	• Minimum Parametreler:kernel.shmmni = 4096kernel.shmmax = 268435456kernel.shmall = 2097152kernel.sem = 32 4096 32 128fs.file-max = 524288


	Kalıcı hale getirmek için /etc/sysctl.conf dosyasına şu değerleri ekleyin:
	
kernel.shmmax = 268435456
kernel.sem = 32 4096 32 128
fs.file-max = 524288

• Swap Alanı ve Performans AyarlarıYüksek yük altında sanal belleğin tükenmesini önlemek için yeterli swap alanı ayrılmalıdır.
• Kullanıcı Limitleri (nofile ve nproc)
	• IBM MQ'nun yöneticisi olan mqm kullanıcısı için açık dosya limiti (nofile) ve işlem limiti (nproc) artırılmalıdır:mqm       hard  nofile     10240mqm       soft  nofile     10240mqm       hard  nproc      4096mqm       soft  nproc      4096
	• Bu ayarları /etc/security/limits.conf dosyasına ekleyerek kalıcı hale getirin.


********************

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
	2. Kurulum sırasında lisansı kabul etmek için:mqlicense.sh -accept
	Dikkat: Bu yöntem yalnızca kurulum öncesi lisans kabulü için kullanılır. Kurulumdan sonra kullanılamaz.

Kurulumdan Sonra Lisansı Kabul Etme
	1. Lisansı kabul etmek için aşağıdaki komutu çalıştırın:export MQLICENSE=accept
	2. Lisansın kabul edilip edilmediğini görmek için:export MQLICENSE=view
	3. Alternatif olarak şu komutları da kullanabilirsiniz:
		○ Lisansı Kabul Etmek için:mqlicense -accept
		○ Lisansı Görüntülemek için:dspmqlic
	Not: Kurulum medyasından mqlicense.sh script'ini kurulum sonrası lisans kabulü için kullanmayın. Bu script yalnızca kurulum öncesi lisans kabulü için uygundur.

3. Özel Durumlar
	• Doğru Lisansa Sahip Olma:Kurmak istediğiniz IBM MQ bileşenleri için gerekli lisansa sahip olmalısınız. Lisans gereksinimleri için IBM dokümantasyonuna göz atabilirsiniz.
	• Deneme Lisansı Dönüşümü:Eğer bir deneme lisansı kuruluysa, bunu tam lisansa çevirmek için gereken adımları takip edin. Daha fazla bilgi için: Converting a trial license on Linux.




****************



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
	• Kernel ayarlarını yapılandırdığınızdan emin olun. Örneğin:sysctl -w kernel.shmmni=4096sysctl -w kernel.shmall=2097152sysctl -w kernel.shmmax=268435456

Adım 2: Lisansı Kabul Etme
Kurulumdan önce veya sonra lisansı kabul edebilirsiniz:
	• Önce Kabul Etmek İçin:./mqlicense.shMetin tabanlı kabul için:./mqlicense.sh -text_only
	• Sonra Kabul Etmek İçin:export MQLICENSE=accept

Adım 3: IBM MQ RPM Paketlerini Kurma
Kurulum sırasında en az şu bileşenleri yüklemelisiniz:
	• MQSeriesRuntime
	• MQSeriesGSKit
	• MQSeriesServer
Kurulum Komutları:
	• Varsayılan Dizin İçin (Önerilen /opt/mqm):rpm -Uvh MQSeriesRuntime-*.rpm MQSeriesServer-*.rpm MQSeriesGSKit-*.rpm
	• Farklı Bir Dizin için: Farklı bir kurulum dizini belirtmek istiyorsanız, --prefix seçeneğini kullanın:rpm --prefix /opt/customLocation -Uvh MQSeriesRuntime-*.rpm MQSeriesServer-*.rpm
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





*************************


Linux Red Hat Üzerinde dnf Kullanarak IBM MQ Kurulumu

Bu döküman, Red Hat Linux sistemlerinde IBM MQ kurulumunu dnf paket yöneticisi kullanarak yapmanız için gereken adımları detaylandırır.

1. Hazırlık Aşamaları
Kurulum işlemlerine başlamadan önce aşağıdaki hazırlıkları yapmanız gereklidir:
1.1 Sistem Gereksinimlerini Kontrol Etme
IBM MQ'yu kurmadan önce, sisteminizin gereksinimlerini karşılayıp karşılamadığını kontrol edin. Bu kontroller şunlardır:
	• Kernel ayarlarını aşağıdaki şekilde yapılandırın:sysctl -w kernel.shmmni=4096sysctl -w kernel.shmall=2097152sysctl -w kernel.shmmax=268435456
1.2 Gerekli Komutların Mevcut Olduğundan Emin Olun
IBM MQ'yu farklı bir dizine kurmak veya birden fazla sürüm kullanmak istiyorsanız, aşağıdaki komutların sistemde yüklü olduğundan emin olun:
	• pax veya rpmbuild (rpm-build paketinde bulunur)
	• createrepo
	• yum-utils
Bu komutlar, IBM MQ ile birlikte gelmez. Linux dağıtım sağlayıcınızdan yüklemelisiniz:

sudo dnf install rpm-build createrepo yum-utils
1.3 Kurulum Dosyalarını Hazırlama
Kurulum dosyalarını IBM Passport Advantage gibi bir kaynaktan indirdiyseniz, bu dosyaları aşağıdaki komutlarla açın:

gunzip CC7K6ML.tar.gztar -xvf CC7K6ML.tar
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

[IBM-MQ-v.r.m-architecture]name=IBM MQ v.r.m architecturebaseurl=file:///installationFilesLocationenabled=1gpgcheck=0
Değişkenlerin anlamı:
	• installationFilesLocation: Kurulum dosyalarının bulunduğu tam yol.
	• v.r.m: IBM MQ'nun sürüm, dağıtım ve modifikasyon numarası (örneğin, "9.4.0").
	• architecture: Sistem mimarisi (örneğin, "x86_64").
2.2 GPG İmzasını Doğrulama (Opsiyonel)
Repository güvenliğini artırmak için GPG imza doğrulamasını etkinleştirin:

gpgcheck=1gpgkey=file:///directory/to/ibm_mq_public.pgp
Repository önbelleğini temizleyin:

dnf clean all
Repository'nin doğru şekilde yapılandırıldığını kontrol edin:

dnf repolist

3. Lisans Kabulü
IBM MQ lisansını kurulumdan önce veya sonra kabul edebilirsiniz.
	• Kurulumdan Önce Lisansı Kabul Etmek İçin:./mqlicense.sh
	• Kurulumdan Sonra Lisansı Kabul Etmek İçin:export MQLICENSE=accept

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



*********************



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

gunzip CC7K6ML.tar.gztar -xvf CC7K6ML.tar
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
	• Kurulumdan Önce Lisansı Kabul Etmek İçin:./mqlicense.sh
	• Kurulumdan Sonra Lisansı Kabul Etmek İçin:export MQLICENSE=accept

4. IBM MQ Kurulumu
IBM MQ’yu Debian paketleriyle kurmak için iki yöntemden birini seçebilirsiniz: apt-get veya dpkg.
4.1 apt-get ile Kurulum
apt-get, bağımlılıkları otomatik olarak yükler. Aşağıdaki adımları izleyin:
	1. apt-get için Paketleri Ayarlayın: /etc/apt/sources.list.d dizininde bir liste dosyası oluşturun (örneğin, IBM_MQ.list):sudo nano /etc/apt/sources.list.d/IBM_MQ.listDosyaya şu satırları ekleyin:deb [trusted=yes] file:/kurulum/dizin ./
	2. apt-get Önbelleğini Güncelleyin:sudo apt-get update
	3. Paketleri Kurun:
		○ Tüm Bileşenleri Kurmak İçin:sudo apt-get install "ibmmq-*"
		○ Sunucu ve Bağımlılıklarını Kurmak İçin:sudo apt-get install ibmmq-server

4.2 dpkg ile Kurulum
dpkg bağımlılıkları yüklemez. Bu nedenle bağımlılıkları sıralı olarak yüklemeniz gerekir:
	1. Paketleri Tek Tek Kurun: Aşağıdaki sırayla paketleri yükleyin:sudo dpkg -i ibmmq-runtime_9.4.0.0_amd64.debsudo dpkg -i ibmmq-gskit_9.4.0.0_amd64.debsudo dpkg -i ibmmq-server_9.4.0.0_amd64.deb
	2. Bağımlılıkları Kontrol Edin: Kurulum sırasında eksik bağımlılıklar varsa şu komutu çalıştırarak tamamlayın:sudo apt-get -f install

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




******************




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
	1. İstemci Arşivini Çıkartın:tar -xvf 9.4.0.0-IBM-MQC-Redist-LinuxX64.tar.gz
	2. Bin Klasörüne Girin:cd MQC/bin
	3. Script’i Çalıştırın:./genmqpkg
		○ Script, hangi dosyalara ihtiyacınız olduğunu anlamak için Evet/Hayır soruları sorar.
		○ İşlem tamamlandığında, dosyaların kopyalanacağı bir hedef dizin belirtmeniz istenir.Önemli Not: Script'e tam bir dizin yolu sağlayın. Shell değişkenlerini kullanarak kısayollar oluşturmayın (örneğin, $HOME).
	4. Seçilen Dosyalar Hedef Dizine Kopyalanır.
2.2 Sınırlamalar
	• IBM yalnızca tam ve değiştirilmemiş paketleri destekler. genmqpkg ile oluşturulan özel dosya setlerine resmi destek verilmez.
	• Varsayılan veri yolu:$HOME/IBM/MQ/data

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

Name:        IBM MQVersion:     9.4.0.0Level:       p940-940-L220415BuildType:   IKAP - (Production)Platform:    IBM MQ for Linux (x86-64 platform)Mode:        64-bitO/S:         Linux 2.6.32.59-0.7-defaultInstName:    MQNI09200004InstDesc:    IBM MQ V9.4.0.0 (Redistributable)Primary:     NoInstPath:    /Development/johndoe/unzip/unpackDataPath:    /u/johndoe/IBM/MQ/dataMaxCmdLevel: 940

7. Önemli Notlar
	• Uyumluluk: Redistributable client, tam IBM MQ kurulumlarıyla uyumlu ancak yalnızca farklı dizinlerde.
	• Destek: IBM yalnızca tam ve değiştirilmemiş paketleri destekler. genmqpkg kullanılarak oluşturulan özel dosya setleri resmi destek kapsamında değildir.
	• Veri Yolu Ayarları: Varsayılan veri yolu özelleştirilebilir, ancak dizinin manuel olarak oluşturulması gerekir.



******************



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
		○ Queue manager oluştur:crtmqm QMAQMA isimli bir queue manager oluşturulur.
		○ Queue manager'ı başlat:strmqm QMA
		○ MQSC oturumunu başlat:runmqsc QMA
		○ Yerel bir kuyruk tanımla:DEFINE QLOCAL (QUEUE1)QUEUE1 isimli bir kuyruk tanımlanır.
	3. Mesaj Gönderme ve Alma:
		○ Mesaj gönder:./amqsput QUEUE1 QMAKullanıcı, komut isteminde bir veya daha fazla mesaj yazarak kuyrukta mesaj bırakır.
		○ Mesaj al:./amqsget QUEUE1 QMAKuyruktaki mesajlar alınır ve ekranda gösterilir.
	4. Sonuç:
		○ Mesajlar başarıyla gönderilir ve alınırsa, kurulum başarılıdır.

3. Sunucular Arası Kurulum Doğrulaması
Amaç:
İki IBM MQ sunucusu arasında mesajlaşma altyapısının çalıştığını kontrol etmek.
Adımlar:
	1. Alıcı Sunucu (Receiver):
		○ Queue manager oluştur:crtmqm QMBQMB isimli bir queue manager oluşturulur.
		○ Yerel bir kuyruk tanımla:DEFINE QLOCAL (RECEIVER.Q)Mesajları alacak RECEIVER.Q isimli kuyruk tanımlanır.
		○ Dinleyici (Listener) tanımla:DEFINE LISTENER (LISTENER1) TRPTYPE (TCP) CONTROL (QMGR) PORT (1414)
		○ Alıcı kanal tanımla:DEFINE CHANNEL (QMA.QMB) CHLTYPE (RCVR) TRPTYPE (TCP)
		○ Dinleyiciyi başlat:START LISTENER (LISTENER1)
	2. Gönderen Sunucu (Sender):
		○ Queue manager oluştur:crtmqm QMAQMA isimli bir queue manager oluşturulur.
		○ Yerel bir iletim kuyruğu tanımla:DEFINE QLOCAL (QMB) USAGE (XMITQ)
		○ Uzaktaki kuyruğun yerel tanımı:DEFINE QREMOTE (LOCAL.DEF.OF.REMOTE.QUEUE) RNAME (RECEIVER.Q) RQMNAME ('QMB') XMITQ (QMB)
		○ Gönderici kanal tanımla:DEFINE CHANNEL (QMA.QMB) CHLTYPE (SDR) CONNAME ('receiver_ip(1414)') XMITQ (QMB) TRPTYPE (TCP)
		○ Kanalı başlat:START CHANNEL (QMA.QMB)
	3. Mesaj Gönderme ve Alma:
		○ Mesaj gönder:./amqsput LOCAL.DEF.OF.REMOTE.QUEUE QMA
		○ Mesaj al:./amqsget RECEIVER.Q QMB
	4. Sonuç:
		○ Gönderilen mesaj, alıcı kuyruğunda başarıyla okunuyorsa, kurulum başarılıdır.

4. İstemci Kurulumu Doğrulaması
Amaç:
Bir istemcinin sunucu ile iletişim kurabildiğini doğrulamak.
Adımlar:
	1. Sunucu Hazırlığı:
		○ Queue manager ve kuyruk oluştur:crtmqm QUEUE.MANAGER.1DEFINE QLOCAL (QUEUE1)
		○ Server-connection kanalı tanımla:DEFINE CHANNEL (CHANNEL1) CHLTYPE (SVRCONN) TRPTYPE (TCP)
		○ Dinleyici tanımla ve başlat:DEFINE LISTENER (LISTENER1) TRPTYPE (TCP) CONTROL (QMGR) PORT (1414)START LISTENER (LISTENER1)
	2. İstemci Bağlantısı:
		○ İstemci ortam değişkenini ayarla:export MQSERVER=CHANNEL1/TCP/'server_ip(1414)'
	3. Mesaj Gönderme ve Alma:
		○ Mesaj gönder (istemciden sunucuya):./amqsputc QUEUE1 QUEUE.MANAGER.1
		○ Mesaj al (sunucudan istemciye):./amqsgetc QUEUE1 QUEUE.MANAGER.1
	4. Sonuç:
		○ Mesajlar doğru şekilde iletilip alınırsa, istemci kurulumunuz başarıyla tamamlanmıştır.

5. Mesajların Dilini Seçme (LANG Ayarı)
Amaç:
IBM MQ tarafından gösterilen mesajların farklı bir dilde görüntülenmesini sağlamak.
Adımlar:
	1. Dil Dosyasını Kurma:
		○ Gerekli dil dosyalarını kurun. Örneğin, Fransızca için:apt-get install ibmmq-msg-fr
	2. Dil Ayarını Yapma:
		○ LANG değişkenini ayarla:export LANG=fr_FR
	3. Sonuç:
		○ IBM MQ mesajları artık seçtiğiniz dilde gösterilecektir.




************************


1. IBM MQ’yu Kaldırma veya Değiştirme
a. Genel Hazırlık
	• Kurulumdan Önce Yapılması Gerekenler:
		○ Tüm IBM MQ uygulamaları, kuyruk yöneticileri (Queue Managers) ve dinleyiciler (Listeners) kapatılmalıdır.
		○ dspmq, endmqm, ve endmqlsr komutları kullanılarak çalışan işlemler durdurulmalıdır.
	• Kritik Not:
		○ IBM MQ 9.4.0 veya daha yeni bir sürüm kaldırılırken düzeltme paketlerini kaldırmak gerekmez. Ancak, 9.4.0 öncesi sürümler için düzeltme paketleri (fix packs) önce kaldırılmalıdır.
b. Çeşitli Paket Yönetim Araçları ile Kaldırma
	• rpm:
		○ Tüm paketleri kaldırmak için:rpm -qa | grep MQSeries | xargs rpm -ev
		○ Belirli paketleri kaldırmak için:rpm -ev PaketAdı
	• dnf (Red Hat):
		○ Tüm kurulumları kaldırmak için:dnf remove MQSeries*
		○ Bireysel bileşenleri kaldırmak için:dnf remove PaketAdı
	• apt/dpkg (Ubuntu):
		○ Tüm kurulumları kaldırmak için:apt-get remove "ibmmq-*"
		○ Kalan yapılandırma dosyalarını temizlemek için:apt-get purge "ibmmq-*"
		○ Bireysel bileşenleri kaldırmak için:dpkg -r PaketAdıdpkg -P PaketAdı
c. Kaldırma Sonrası Temizlik
	• Varsayılan olarak, /var/mqm ve /etc/opt/mqm dizinleri korunur. Ancak başka bir IBM MQ kurulumu yoksa ve gelecekte kurulum planlanmıyorsa bu dizinler güvenle silinebilir:rm -rf /var/mqm /etc/opt/mqm

2. Fix Pack Kaldırma
a. Düzeltme Paketi Kaldırma Süreci
	• Fix pack’ler sadece uygulandığı sırada kullanılan dosyaları etkiler (genellikle /opt/mqm dizini).
	• Kaldırma işlemi, ters sırayla yapılmalıdır: İlk olarak düzeltme paketleri, ardından ana ürün kaldırılır.
	• apt komutları örneği:
		○ Fix Pack kaldırmak için:apt remove "ibmmq-*-u9401*"
		○ Kalan yapılandırma dosyalarını temizlemek için:apt purge "ibmmq-*-u9401*"
b. Fix Pack Kaldırma Sonrası Doğrulama
	• Kurulum sonrası sürümü kontrol etmek için:dspmqver

3. IBM MQ’yu Değiştirme
	• Ek Bileşen Ekleme veya Kaldırma:
		○ rpm veya dnf kullanılarak yeni bileşen eklenebilir veya kaldırılabilir.
		○ Örneğin, SDK ve Runtime bileşenlerini kaldırmak için:rpm -ev MQSeriesRuntime MQSeriesSDK

Sürecin Önemi
Bu süreç, IBM MQ’yu tamamen kaldırmak veya kurulumun bazı bölümlerini yönetmek için gereken adımları sunar. Bu işlemler:
	1. Sistemi yeniden yapılandırma veya IBM MQ’yu başka bir sistemle değiştirme planlarında yardımcı olur.
	2. Gereksiz dosya ve paketlerin sistemde kalmasını önler.
	3. Yeni bir IBM MQ sürümüne geçişi kolaylaştırır.



**************


IBM MQ Kurulum ve Kaldırma Süreci: Önemli Adımlar
Kurulum Süreci
	1. Sistem Gereksinimlerini Kontrol Et
		○ Linux sistem gereksinimlerini karşılayın. Çekirdek ayarlarını düzenleyin:sysctl -w kernel.shmmax=268435456
		○ Gerekli paket yöneticisi (rpm, dnf, apt/dpkg) hazır olsun.
	2. Lisansı Kabul Et
		○ Lisansı kurulumdan önce veya sonra kabul edebilirsiniz:./mqlicense.sh -text_only
	3. Gerekli Paketleri Seç ve Yükle
		○ Minimum bileşenler:
			§ MQSeriesRuntime, MQSeriesServer, MQSeriesGSKit
		○ Yükleme komutları:
			§ rpm:rpm -Uvh MQSeriesRuntime-*.rpm MQSeriesServer-*.rpm MQSeriesGSKit-*.rpm
			§ dnf (Red Hat):dnf -y install MQSeries*
			§ apt (Ubuntu):apt-get install "ibmmq-*"
	4. Kurulumu Doğrula
		○ Sürüm bilgisi için:dspmqver
		○ Kuyruk yöneticisi oluştur ve başlat:crtmqm QMAstrmqm QMA
		○ Test kuyruğu tanımla:DEFINE QLOCAL(QUEUE1)
	5. Test Programları ile Doğrulama
		○ Mesaj gönder ve al:./amqsput QUEUE1 QMA./amqsget QUEUE1 QMA

Kaldırma Süreci
	1. Kuyruk Yöneticilerini ve Dinleyicileri Durdurdspmq -o installationendmqm QMgrNameendmqlsr -m QMgrName
	2. Kurulumları Kaldır
		○ rpm:rpm -qa | grep MQSeries | xargs rpm -ev
		○ dnf (Red Hat):dnf remove MQSeries*
		○ apt (Ubuntu):apt-get purge "ibmmq-*"
	3. Kalan Dosyaları Temizle (Opsiyonel)
		○ Yedekleme gerekmediğinde:rm -rf /var/mqm /etc/opt/mqm

Kurulumda ve Kaldırmada Kritik Notlar
	• Sürüm Doğrulama:
		○ Kurulum sonrası: dspmqver
		○ Fix pack kaldırmadan önce: apt list
	• Çevre Değişkenlerini Ayarla:. MQ_INSTALLATION_PATH/bin/setmqenv -s
