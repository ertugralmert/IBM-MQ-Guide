







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
		○ Aşağıdaki komutlarla bir kuyruk yöneticisi ve dinleyici oluşturun:crtmqm QMAstrmqm QMArunmqsc QMADEFINE LISTENER(LISTENER1) TRPTYPE(TCP) PORT(1414) CONTROL(QMGR)START LISTENER(LISTENER1)DEFINE QLOCAL(QUEUE1)end
	2. Mesaj Gönder ve Oku:
		○ Mesaj göndermek için:amqsput QUEUE1 QMA
		○ Mesaj okumak için:amqsget QUEUE1 QMA
	3. Durum Kontrolü:
		○ Kuyruk yöneticisinin durumunu kontrol etmek için:dspmq

4. Kaldırma Adımları
	1. Kuyruk Yöneticilerini Durdur:
		○ Çalışan tüm kuyruk yöneticilerini kapatın:endmqm QMA
	2. Programı Kaldır:
		○ Denetim Masası > Programlar ve Özellikler'den IBM MQ'yu kaldırabilirsiniz.
		○ Alternatif olarak, aşağıdaki komutu kullanabilirsiniz:msiexec /x {ProductCode}
	3. Gereksiz Dosyaları Temizle:
		○ Kaldırma işleminden sonra kalan dosyaları silmek için:rmdir /s /q "C:\Program Files\IBM\MQ"rmdir /s /q "C:\ProgramData\IBM\MQ"

Notlar:
	• UAC (User Account Control): Yönetici yetkileri gerektiren işlemler için UAC devre dışı bırakılmalı veya komut istemi "Yönetici olarak çalıştır" seçeneğiyle başlatılmalıdır.
	• Domain Hesapları: IBM MQ hizmetini bir Windows domain ortamında çalıştırıyorsanız, özel bir domain hesabı gerekebilir.
	• Loglama: Kurulum sırasında loglama açık bırakılırsa, hataları daha kolay çözebilirsiniz.




*******************


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
	1. Interaktif Kurulum:msiexec /i "C:\Setup\IBM MQ.msi" /l*v c:\install.log AGREETOLICENSE="yes" ADDLOCAL="Server"
	2. Sessiz Kurulum (Silent Installation):msiexec /i "C:\Setup\IBM MQ.msi" /q /l*v c:\install.log AGREETOLICENSE="yes" ADDLOCAL="Server"
	3. İkinci Bir Kurulum:msiexec /i "C:\Setup\IBM MQ.msi" /q /l*v c:\install.log AGREETOLICENSE="yes" ADDLOCAL="Server" MSINEWINSTANCE=1 TRANSFORMS=":InstanceId2.mst"

4. Kurulum Doğrulama
	1. Kurulum Loglarını Kontrol Et:
		○ Log Dosyaları: %TEMP%\MSI*.LOG veya %TEMP%\MQv9_Install_*.LOG
		○ Ayrıca C:\ProgramData\IBM\MQ\amqmjpse.txt dosyasını kontrol edin.
	2. Kuyruk Yöneticisi Oluşturma ve Başlatma:
		○ Komut istemini Administrator yetkisiyle açın ve şu komutları çalıştırın:crtmqm QMAstrmqm QMA
	3. Dinleyici ve Kuyruk Tanımlama:runmqsc QMADEFINE LISTENER(LISTENER1) TRPTYPE(TCP) PORT(1414) CONTROL(QMGR)START LISTENER(LISTENER1)DEFINE QLOCAL(QUEUE1)end
	4. Mesaj Gönder ve Oku:
		○ Mesaj göndermek için:amqsput QUEUE1 QMA
		○ Mesaj okumak için:amqsget QUEUE1 QMA
	5. Kurulumun Durumunu Kontrol Et:
		○ Yüklü kurulumları listelemek için:dspmqinst

5. Kurulum Sonrası
	1. Prepare IBM MQ Wizard Kullanımı:
		○ Kurulumdan sonra otomatik olarak başlar. IBM MQ Service’i yapılandırmak için bu sihirbazı tamamlayın.
	2. Ortam Değişkenlerini Ayarlama:MQ_INSTALLATION_PATH\bin\setmqinst -i -p MQ_INSTALLATION_PATH

Notlar
	• Hata Giderme: Hatalar için log dosyalarını kontrol edin.
	• Güvenlik: Kurulum sırasında domain kullanıcı hesaplarının yapılandırmasını dikkatlice yapın. Gerekirse setmqipw komutuyla şifreleme kullanın.
	• Lisans: IBM MQ Advanced özelliklerini yüklemeden önce lisansınızın uygun olduğundan emin olun.



*****************


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



***********************

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
		○ Setup.exe dosyasını çift tıklayın veya bir komut isteminde şu komutu çalıştırın:C:\instmqs\Windows\Setup.exe
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
	• Aynı sistemde birden fazla IBM MQ Client kurmak için MSINEWINSTANCE ve TRANSFORMS parametrelerini eklemeniz gerekir:msiexec /i "C:\path\IBM MQ.msi" /q TRANSFORMS=":InstanceId2.mst" AGREETOLICENSE="yes" ADDLOCAL="Client" MSINEWINSTANCE=1

3. Yanıt Dosyası ile Kurulum
Yanıt Dosyası (Response.ini)
	• Yanıt dosyası, kurulum sırasında ihtiyaç duyulan tüm ayarları içerir ve otomasyonu kolaylaştırır.
	• Örnek Yanıt Dosyası:[Response]PGMFOLDER="C:\Program Files\IBM\MQ"AGREETOLICENSE="yes"ADDLOCAL="Client"
Yanıt Dosyası Kullanımı
	• Yanıt dosyasını kullanarak kurulum:msiexec /i "C:\path\IBM MQ.msi" /q USEINI="C:\Response.ini"

4. Kurulum Sonrası Yapılandırma
Kurulumu Birincil Kurulum Olarak Ayarlama
	• Bir sistemde yalnızca bir birincil kurulum olabilir. Birincil kurulum yapmak için şu komutu çalıştırın:"MQ_INSTALLATION_PATH\bin\setmqinst" -i -p MQ_INSTALLATION_PATH
Çevresel Değişkenleri Ayarlama
	• setmqenv veya crtmqenv komutlarını kullanarak IBM MQ ile çalışmak için ortam değişkenlerini ayarlayın:setmqenv -s
Kurulum Testi
	• Kurulumun başarılı olduğunu doğrulamak için istemci ve sunucu arasındaki iletişimi test edin:
		○ Daha fazla bilgi için: Testing communication between a client and a server on Windows.

5. IBM MQ Client Özelliklerini Değiştirme veya Kaldırma
msiexec ile Özellik Ekleme/Kaldırma
	• IBM MQ Client'ın belirli özelliklerini eklemek veya kaldırmak için:msiexec /i {product_code} /q ADDLOCAL="Client" REMOVE="Toolkit" INSTALLATIONNAME="Installation1"


*********************


IBM MQ Client Kurulumunu Değiştirme
IBM MQ Client kurulumunu, mevcut özellikleri eklemek veya kaldırmak için aşağıdaki yöntemlerden birini kullanabilirsiniz.

1. IBM MQ Installation Wizard Kullanarak Kurulum Değişikliği
Adımlar
	1. Kurulum İmajına Erişim Sağlayın:
		○ IBM MQ kurulum imajının yerini bulun (ağ paylaşımı veya yerel dosya sistemi dizini olabilir).
			§ Örnek: C:\instmqs\Windows\Setup.exe
	2. Setup.exe Dosyasını Çalıştırın:
		○ Setup.exe dosyasını çift tıklayın veya bir komut isteminde şu komutu çalıştırın:C:\instmqs\Windows\Setup.exe
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
	1. Bir parametre dosyası oluşturun (MQParms.ini):[MSI]ADDLOCAL="JavaMsg"REMOVE=""/l*v c:\install.log
	2. MQParms Komutunu Çalıştırın:MQParms "C:\MQParms.ini" /l*v C:\install.log
Notlar:
	• Parametre dosyasında ADDLOCAL ve REMOVE alanlarını ayarlayarak değişiklikleri tanımlayın.
	• Komut satırında belirtilen parametreler, dosyadaki ayarların üzerine yazılır.



***********************


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
	1. genmqpkg betiğini çalıştırın:MQ_INSTALLATION_PATH\bin\genmqpkg
	2. Sorulara yanıt vererek uygulamanızın gereksinimlerine uygun dosyaları seçin.
	3. Dosyalar seçildikten sonra, yeni hedef dizini belirtin. Betik, gerekli dosyaları bu dizine kopyalar.

IBM MQ Kurulum Doğrulama
Kurulum Doğrulama Yöntemleri
IBM MQ kurulumu tamamlandıktan sonra, sunucu veya istemci kurulumunu doğrulamak için aşağıdaki adımları izleyebilirsiniz:
Yerel Sunucu Kurulumunu Doğrulama
	1. Ortam değişkenlerini ayarlayın:MQ_INSTALLATION_PATH\bin\setmqenv -s
	2. dspmqver komutuyla kurulum bilgilerini doğrulayın.
	3. Bir sıra yöneticisi oluşturun ve başlatın:crtmqm QMAstrmqm QMA
	4. Bir kuyruk oluşturun:runmqsc QMADEFINE QLOCAL(QUEUE1)end
	5. Mesaj gönderme ve alma için örnek programları çalıştırın:amqsput QUEUE1 QMAamqsget QUEUE1 QMA
Sunucudan Sunucuya Kurulumu Doğrulama
	1. Alıcı sunucuda bir dinleyici ve alıcı kanal tanımlayın.
	2. Gönderici sunucuda bir gönderici kanal ve uzak sıra tanımlayın.
	3. Mesaj gönderip alın.
İstemci Kurulumunu Doğrulama
	1. Sunucu tarafında bir sıra yöneticisi, kuyruk ve sunucu-bağlantı kanalı oluşturun.
	2. İstemci tarafında MQSERVER ortam değişkenini ayarlayın:cmdCopy codeSET MQSERVER=CHANNEL1/TCP/server-address(port)
	3. Örnek istemci programlarını çalıştırarak iletişimi test edin:amqsputc QUEUE1 QUEUE.MANAGER.1amqsgetc QUEUE1 QUEUE.MANAGER.1

Ulusal Dil Mesajlarının Ayarlanması
IBM MQ, kurulu sistemin diline uygun olarak mesajları görüntüleyebilir. Ancak, farklı bir dil seçmek için MQS_FORCE_NTLANGID ortam değişkenini kullanabilirsiniz.
Mesaj Dili Ayarı
	1. MQS_FORCE_NTLANGID ortam değişkenini ayarlayın:SET MQS_FORCE_NTLANGID=0x0409Not: 0x0409 değeri, İngilizce dilini ifade eder. Diğer diller için Microsoft Dil Tanımlayıcıları belgesini inceleyin.
	2. Bu değişkeni sistem çapında ayarlayın ve sisteminizi yeniden başlatın.

Sonuç
IBM MQ redistributable istemciler ve kurulum doğrulama süreçleri, mesajlaşma altyapınızın stabil bir şekilde çalışmasını sağlamak için kritik öneme sahipti


****************************

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
		○ Tüm IBM MQ Uygulamalarını Durdurun: MQ_INSTALLATION_PATH\bin\setmqenv -s komutunu çalıştırarak ortamı ayarlayın ve ardından kuyruk yöneticilerini durdurun:endmqm queue_manager_nameendmqlsr -m queue_manager_name
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
		○ Kuyruk yöneticisi verilerini kaldırma seçeneği ile:msiexec /x {product_code} /l*v "c:\removal.log" REMOVE="All" INSTALLATIONNAME="installation_name"
	2. Sessiz Kaldırma Komutları:
		○ Kuyruk yöneticisi verilerini kaldırmadan:msiexec /x {product_code} /l*v "c:\removal.log" /q REMOVE="All" INSTALLATIONNAME="installation_name"
		○ Kuyruk yöneticisi verilerini kaldırarak (son sunucu kurulumu için geçerli):msiexec /x {product_code} /l*v "c:\removal.log" /q REMOVE="All" KEEPQMDATA="delete" INSTALLATIONNAME="installation_name"
	3. Kaldırma İşlemi Takibi:
		○ Günlük kaydı (removal.log) üzerinden işlem ilerlemesini kontrol edin.

3. MQParms Kullanarak Kaldırma
MQParms komutuyla kaldırma işlemi gerçekleştirebilirsiniz:
	1. Parametre Dosyası Kullanımı:
		○ MQParms.ini dosyasını düzenleyin ve aşağıdaki değerleri ayarlayın:[MSI]ADDLOCAL=""REMOVE="ALL"
	2. Komut Satırını Kullanarak Kaldırma:MQParms.exe parameter_file /i "{product_code}"

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


***********************




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
	2. Kurulum Komutları:rpm -iv MQSeriesAMS-V.R.M-F.x86_64.rpm
		○ V, R, M, F: Sırasıyla sürüm, yayın, modifikasyon ve düzeltme paketi seviyesini belirtir.
AMS Kaldırma
	• Linux:rpm -e MQSeriesAMS-V.R.M-F
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
	2. Kurulum:rpm -iv MQSeriesFTBase*.rpm MQSeriesFTAgent*.rpm
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
	1. Gerekli Paketlerin Yüklenmesi:dnf install Advanced/RDQM/PreReqs/el8/drbd-utils-9/*dnf install Advanced/RDQM/PreReqs/el8/pacemaker-2/*
	2. IBM MQ ve RDQM Yükleme:dnf install MQSeriesGSKit* MQSeriesServer* MQSeriesRuntime*dnf install Advanced/RDQM/MQSeriesRDQM*
	3. Pacemaker Kümelenmesi ve RDQM Yapılandırması:
		○ Pacemaker ile yüksek erişilebilirlik veya felaket kurtarma senaryolarını yapılandırın.

IBM MQ Explorer ve Web Sunucusu Kurulumu
IBM MQ Explorer Kurulumu
	• Windows/Linux: Fix Central'dan bağımsız MQ Explorer paketini indirin ve yükleyin.
IBM MQ Web Sunucusu Kurulumu
	• Linux: Standalone IBM MQ Web Sunucusu indirilerek kurulum yapılabilir. Web Sunucusu, MQ Konsolunu ve REST API'sini çalıştırmak için kullanılır.

Sonuç ve Özet
Bu belge, IBM MQ Advanced bileşenlerinin kurulumu ve yönetimi için kapsamlı bir rehber sunmaktadır. Tüm kurulum ve yapılandırma süreçlerini dikkatle takip ederek, IBM MQ Advanced'ın gelişmiş özelliklerinden tam anlamıyla faydalanabilirsiniz



****************************



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
	• Manuel Geçiş: Yeni özellikleri etkinleştirmek için komutlar kullanılır.strmqm -e CMDLEVEL=940
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
	• Bakım Uygulaması:rpm -Uvh MQSeries*.rpmdnf upgrade MQSeries*
	• Bakım Kaldırma:rpm --oldpackage -Uvh MQSeries*.rpmdnf downgrade MQSeries*
	• Ubuntu için:apt-get -y --allow-downgrades install "ibmmq-*"

Çoklu Sürümler ve Geçiş Yönetimi
	• Çoklu Kurulum: Aynı sunucuda farklı IBM MQ sürümleri çalıştırılabilir (ör. test ve üretim ortamları).
	• Geçiş Sırası:
		○ Yükseltme -> Kuyruk Yöneticisi Geçişi -> Uygulama Testi.

Bakım ve Yükseltme Kapsamındaki Önemli Hususlar
	• Yedekleme her zaman önceliklidir. Kuyruk yöneticisi, kanallar ve veriler yedeklenmeden yükseltme yapılmamalıdır.
	• Yeni sürümdeki özelliklerin uygulanması öncesinde geçiş sonrası performans ve uyumluluk testleri yapılmalıdır.
	• Kod Seviyesinin Kontrolü:bashCopy codedspmqver



