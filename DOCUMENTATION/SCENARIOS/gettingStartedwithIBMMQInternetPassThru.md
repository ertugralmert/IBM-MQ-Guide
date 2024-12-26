IBM MQ Internet Pass-Thru (MQIPT) ile ilgili ilk adımlar
Başlangıç Öncesi Gereksinimler
IBM MQ IPT kullanmadan önce aşağıdaki adımları tamamladığınızdan emin olmalısınız:
	1. IBM MQ Bilgisi: IBM MQ'da kuyruk yöneticileri, kuyruklar ve kanallar tanımlamayı bilmelisiniz.
	2. IBM MQ Sunucusu ve İstemcisi Kurulumu: IBM MQ istemcisi ve sunucusunun kurulu olduğundan emin olun.
	3. MQIPT Kurulumu: MQIPT, Windows sistemlerinde varsayılan olarak C:\mqipt dizinine kuruludur. Diğer platformlarda da benzer şekilde çalışır.
	4. Mesaj Gönderme ve Alma: amqsputc komutuyla mesaj gönderebilmeli ve amqsgetc komutuyla mesaj alabilmelisiniz.
	5. İstemci Yetkilendirme Bilgisi: IBM MQ'da istemci yetkilendirmelerini ayarlamayı bilmelisiniz.
İlk Adımlar
MQIPT'yi yapılandırmaya başlamadan önce, sisteminizin temel yapılandırmalarını yapmak için aşağıdaki adımları izleyin:
	1. IBM MQ Sunucusunda Yapılacaklar:
		§ Kuyruk Yöneticisi Tanımlama: MQIPT.QM1 adında bir kuyruk yöneticisi tanımlayın.
		§ Sunucu Bağlantı Kanalı Tanımlama: MQIPT.CONN.CHANNEL adıyla bir bağlantı kanalı oluşturun.
		§ Yerel Kuyruk Tanımlama: MQIPT.LOCAL.QUEUE adında bir yerel kuyruk tanımlayın.
		§ Dinleyici Başlatma: MQIPT.QM1 kuyruk yöneticisi için TCP/IP dinleyicisini 1414 portunda başlatın. Eğer 1414 portu başka bir uygulama tarafından kullanılıyorsa, başka bir boş port numarası seçebilirsiniz.
		§ Bağlantı Yetkilendirmesi ve Kanal Yetkilendirmesi: Bağlantı yetkilendirmesinin ve kanal yetkilendirmesinin istemci bağlantılarından gelen bağlantılara izin verecek şekilde yapılandırıldığından emin olun. Bağlantı kimlik doğrulaması gereksizse, aşağıdaki ortam değişkenlerinden birini ayarlayın:
			□ MQSAMP_USER_ID: Kullanıcı kimliği ile bağlantı doğrulaması yapmak için.
			□ MQSAMP_TOKEN: Bir kimlik doğrulama token'ı kullanmak için.
	2. Test Edilmesi:
		§ Mesaj Gönderme ve Alma: IBM MQ istemcisinden kuyruk yöneticisine bağlantıyı test etmek için amqsputc komutuyla bir mesaj gönderin ve ardından amqsgetc komutuyla mesajı geri alın.
MQIPT Yapılandırma Dosyası (mqipt.conf) Hazırlığı
Yapılandırmaya başlamak için mqipt.conf dosyasını hazırlamanız gerekecek:
	1. Örnek Yapılandırma Dosyasını Kopyalama:
		§ mqiptSample.conf dosyasını MQIPT yükleme dizinindeki samples alt dizininden alıp, MQIPT ana dizinine mqipt.conf olarak kopyalayın.
	2. Yeni Dizinler Oluşturma:
		§ mqipt.conf dosyasının bulunduğu dizine errors ve logs adlarında iki yeni dizin oluşturun ve bu dizinlerin yazılabilir olduğundan emin olun.
	3. Yapılandırma Temizliği:
		§ mqipt.conf dosyasındaki mevcut tüm rotaları silin.
		§ [global] bölümünde, ClientAccess parametresinin true olarak ayarlandığını kontrol edin.
Sonraki Adımlar
Yukarıdaki temel yapılandırmayı tamamladıktan sonra, aşağıdaki senaryoları çalıştırarak MQIPT’nin doğru çalıştığından emin olabilirsiniz:
	1. MQIPT’nin Doğru Çalıştığını Doğrulama: Basit bir yapılandırma ile MQIPT'nin kurulumunun doğru yapıldığını test edebilirsiniz.
	2. Test Sertifikaları Oluşturma: MQIPT, kendisini uzak bir peer’e tanıtmak için kendi kendine imzalanmış bir sertifika kullanabilir.
	3. TLS Sunucu Doğrulaması: TLS bağlantısını test etmek için örnek sertifikayı kullanarak sunucu doğrulaması gerçekleştirebilirsiniz.
	4. TLS İstemci Doğrulaması: TLS bağlantısını test etmek için örnek sertifikayı kullanarak istemci ve sunucu doğrulaması gerçekleştirebilirsiniz.
	5. HTTP Tünelleme Yapılandırması: HTTP üzerinden iki MQIPT örneği arasındaki basit bir bağlantıyı test edebilirsiniz.
	6. Erişim Kontrolü Yapılandırması: Sadece belirli istemcilerden gelen bağlantıları kabul edecek şekilde MQIPT’yi yapılandırabilirsiniz.
	7. SOCKS Proxy Yapılandırması: MQIPT’yi bir SOCKS proxy olarak çalıştırabilirsiniz.
Ekstra Senaryolar
	○ MQIPT Cluster Desteği: Bir küme ortamı oluşturabilirsiniz.
	○ Port Numaralarını Tahsis Etme: Çıkış bağlantıları için kullanılacak yerel portları kontrol edebilirsiniz.
	○ LDAP Sunucusu ile CRL Alma: Sertifika iptal listelerini (CRL) almak için LDAP sunucusunu kullanabilirsiniz.
