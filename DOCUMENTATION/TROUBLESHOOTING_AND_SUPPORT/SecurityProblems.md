IBM MQ Güvenlik Sorunlarını Giderme Rehberi
IBM MQ'da karşılaşılabilecek güvenlik sorunlarını teşhis etmek ve çözmek için kapsamlı bir rehber sunuyoruz.

1. Kanal Kimlik Doğrulama Kayıtları Sorunları
Kanalın Kuyruk Yöneticisine Gösterdiği Adres
	• Kanalın kullandığı CONNAME değeri (ör. localhost veya gerçek IP adresi), kuyruk yöneticisinin farklı kimlik doğrulama kurallarını tetikleyebilir.
BLOCKADDR ile Kanal Adları Kullanımı
	• SET CHLAUTH TYPE(BLOCKADDR) komutu yalnızca CHLAUTH(*) için geçerlidir.
Z/OS Sistemlerinde CHLAUTH Kullanımı
	• Z/OS sistemlerinde kanal adı içeren yıldız işareti (*), tırnak içinde belirtilmelidir. Örnek: CHLAUTH('*').
SET CHLAUTH Komutunun Kuyruk Yöneticisi Yeniden Başlatıldığında Davranışı
	• SYSTEM.CHLAUTH.DATA.QUEUE kuyruğunun erişilemez (PUT(DISABLED)) olması durumunda, SET CHLAUTH komutu yalnızca bellek üzerinde çalışır. Kalıcı hale getirmek için:SET CHLAUTH ... ACTION(REPLACE)
IPv6 Adres Deseni Sınırları
	• Z/OS için ADDRESS veya ADDRLIST alanlarının maksimum uzunluğu 48 karakterdir. Daha uzun adresler için yıldız (*) kullanılabilir.

2. CipherSpec Uyuşmazlıkları
TLS El Sıkışma ve Kanal Başlatma Hataları
	• El Sıkışma Hataları: TLS istemcisi ve sunucusu arasında CipherSpec uyumsuzluğu.
	• Kanal Başlatma Hataları: Her iki uçta tanımlanan CipherSpec uyumsuzluğu veya eksikliği.
Çözüm:
	• Her iki uçta da uyumlu CipherSpec tanımlayın. Örneğin:DEFINE CHANNEL(...) SSLCIPH(...)
Global Sunucu Sertifikası Kullanımı
	• Global Sunucu Sertifikaları daha yüksek şifreleme gerektirir. Uyumlu bir CipherSpec tanımlayın.

3. TLS El Sıkışma Sorunları
Yaygın Sorunlar ve Çözümleri
	1. Sertifika İptali:
		○ Çözüm: Sertifikayı iptal listelerine (CRL/ARL) karşı kontrol edin.
	2. OCSP Yanıtlayıcı Sorunları:
		○ Çözüm: OCSP ile sertifikayı doğrulayın.
	3. Geçersiz veya Etkin Olmayan Sertifika:
		○ Çözüm: Sertifikanın geçerlilik tarihlerini kontrol edin.
	4. Eksik veya Zarar Görmüş Sertifika:
		○ Çözüm: Sertifikayı yenileyin veya tamamlayın.
	5. Eksik Kök Sertifika veya Zincir:
		○ Çözüm: Tam bir güven zincirini sağlayın ve gerekli tüm CA sertifikalarını ekleyin.

4. Doğrulama Belirteçleri (Authentication Token) Sorunları
Yöneticiye Özel Öneriler
	• Kuyruk Yöneticisi Yapılandırması:
		○ Kuyruk yöneticisinin belirteçleri kabul ettiğinden emin olun:REFRESH SECURITY TYPE(CONNAUTH)
	• Belirteç Deposu:
		○ AuthToken yapılandırmasındaki KeyStore ve KeyStorePwdFile yollarını kontrol edin.
	• Kök Sertifika:
		○ Belirteç verenin kök sertifikasını doğru anahtar deposuna ekleyin.
Geliştiriciye Özel Öneriler
	• Hata Kodları:
		○ Bağlantı sorunlarında, aşağıdaki hata kodlarını inceleyin:
			§ 2035 MQRC_NOT_AUTHORIZED
			§ 2063 MQRC_SECURITY_ERROR
			§ 2064 MQRC_TOKEN_TIMESTAMP_NOT_VALID
	• Belirteç Formatı:
		○ Belirteç yapısı ve içeriklerinin doğru olduğunu kontrol edin (başlık, yük, imza).

5. TLS Sistemindeki Diğer Sorunlar
Eksik Sertifika veya İmzacı
	• İstemci veya Sunucuda Eksik Sertifika:
		○ Çözüm: Sertifikaları karşılıklı güven depolarına ekleyin.
SSLPEER Uyuşmazlıkları
	• Çözüm: SSLPEER değerinin sertifika ile eşleştiğinden emin olun.
FIPS Modu Uyuşmazlığı
	• Çözüm: FIPS uyumlu bir şifreleme kullanın veya FIPS modunu devre dışı bırakın.

6. Anahtar Deposu ve Şifreleme Sorunları
Anahtar Deposu Erişim Sorunları
	• Çözüm: Anahtar deposu dosyalarının doğru yerleştirildiğinden ve erişim izinlerinin uygun olduğundan emin olun.
Şifreleme Sorunları
	• JVM özelliklerini doğru tanımlayın:javax.net.ssl.keyStore=/path/to/keystorejavax.net.ssl.keyStorePassword=password
