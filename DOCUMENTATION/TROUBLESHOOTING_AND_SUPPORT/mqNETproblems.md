IBM MQ .NET Uygulama Problemleri Sorun Giderme
IBM MQ .NET uygulamaları çalıştırılırken karşılaşılan sorunlar, genellikle yapılandırma, SSL bağlantıları veya global assembly cache (GAC) ile ilgilidir. Bu sorunları çözmek için aşağıdaki yöntemleri izleyebilirsiniz:

1. Sorun Giderme için .NET Örnek Uygulamaları ve Hata Mesajları
Örnek Uygulamalarla Sorun Giderme
	1. Örnek Uygulama Çalıştırma:
		○ IBM MQ ile birlikte gelen .NET örnek uygulamalarını çalıştırarak sorunları tanımlayabilirsiniz.
		○ Bu örnek uygulamalar hakkında bilgi için Sample applications for .NET dokümantasyonuna bakın.
	2. Hata Mesajlarını İnceleme:
		○ Hata mesajlarını dikkatlice okuyarak önerilen adımları uygulayın.
Unhandled Exception: System.IO.FileNotFoundException
Bu hata genellikle şu dosyalara erişimle ilgili problemleri işaret eder:
	• amqmdnet.dll
	• amqmdxcs.dll
Çözüm Yöntemleri
	• Global Assembly Cache (GAC) Kaydı:
		○ Dosyaların global assembly cache’e (GAC) kayıtlı olduğundan emin olun.
	• Konfigürasyon Dosyası Oluşturma:
		○ amqmdnet.dll ve amqmdxcs.dll dosyalarını işaret eden bir konfigürasyon dosyası oluşturun.
	• Elle Kayıt:
		○ Eğer .NET Framework IBM MQ kurulumu sırasında yoksa, sınıflar GAC'e otomatik olarak kaydedilmeyebilir. Aşağıdaki komutu kullanarak kaydı manuel olarak tekrar yapabilirsiniz:amqidnet -c MQ_INSTALLATION_PATH\bin\amqidotn.txt -l logfile.txt
			§ MQ_INSTALLATION_PATH, IBM MQ'nun kurulu olduğu üst dizini temsil eder.
			§ logfile.txt, kurulum detaylarının kaydedileceği log dosyasıdır.

2. Ortak SSL Hata Kodları
IBM MQ 9.4.0'dan itibaren, .NET istemci kütüphaneleri (amqmdnetstd.dll), SSL ile ilgili sorunlar için daha spesifik hata mesajları sunar.
Senaryo	Önceki Hata Mesajı	IBM MQ 9.4.0 Sonrası Hata Mesajı
SSL anahtar deposu yanlış ayarlandığında	2059 – MQRC_Q_MGR_NOT_AVAILABLE	2381 – MQRC_KEY_REPOSITORY_ERROR
Geçersiz bir şifreleme algoritması ayarlandığında	2538 – MQRC_HOST_NOT_AVAILABLE	2393 – MQRC_SSL_INITIALIZATION_ERROR
Geçersiz bir eş adı ayarlandığında	2059 – MQRC_Q_MGR_NOT_AVAILABLE	2399 – MQRC_SSL_PEER_NAME_ERROR
Eş adları eşleşmediğinde	2059 – MQRC_Q_MGR_NOT_AVAILABLE	2398 – MQRC_SSL_PEER_NAME_MISMATCH
Geçersiz bir sertifika kullanıldığında	2059 – MQRC_Q_MGR_NOT_AVAILABLE	2393 – MQRC_SSL_INITIALIZATION_ERROR
Şifreleme algoritmaları arasında uyumsuzluk olduğunda	2059 – MQRC_Q_MGR_NOT_AVAILABLE	2393 – MQRC_SSL_INITIALIZATION_ERROR
IBM MQ anahtar deposuna erişim izni olmadığında	2059 – MQRC_Q_MGR_NOT_AVAILABLE	2393 – MQRC_SSL_INITIALIZATION_ERROR
Sorunun Tespiti
	• Kuyruk Yöneticisi Günlüklerini İnceleyin:
		○ Hataların detaylı açıklamalarını görmek için MQ_DATA_DIRECTORY/qmgrs/errors/AMQERR.log* dosyalarını kontrol edin.

3. IBM MQ .NET İstemci Bağlantı Problemleri
MQCONN veya MQCONNX Çağrısı Başarısız
Bu sorun genellikle şu nedenlerle ortaya çıkar:
	• Listener Yok:
		○ Sunucuda bir "listener" programı çalışmıyor olabilir.
	• Yanlış SSL Konfigürasyonu:
		○ Geçersiz bir şifreleme algoritması veya sertifika ayarları yapılmış olabilir.
Hata Günlüğü Dosyaları
	• Windows: C:\Program Files\IBM\MQ\errors
	• Linux: /var/mqm/errors
ECONNRESET Hatası
	• Nedenler:
		○ TCP/IP bağlantısının karşı uçtan aniden kesilmesi.
		○ Geçersiz bağlantı adresi veya port.
		○ Ağ bağlantısındaki sorunlar.
	• Çözüm:
		○ Ağ yöneticinizle iletişime geçerek TCP/IP paket izleme araçları kullanmasını isteyin.

4. İzleme ve Diagnostik
İzleme Aktifleştirme
	• İzleme özelliğini aktifleştirmek için .NET istemci uygulamalarınızda Tracing IBM MQ .NET applications dokümantasyonuna bakarak gerekli adımları izleyin.
SSL Sorunları İçin Diagnostik
	1. SSL/TLS Tanılama:set MQIPT_JVM_OPTIONS=-Djavax.net.debug=all
	2. Java Güvenlik Tanılama:set MQIPT_JVM_OPTIONS=-Djava.security.debug=access,failure
İzleme Sonuçlarını Analiz Etme
	• İzleme sonuçlarını inceleyerek sorun kaynağını belirleyin.
	• Hata dosyaları ve logları IBM Destek Ekibine sağlayarak daha fazla yardım alabilirsiniz.

Sonraki Adımlar
	• SSL ile ilgili sorunlarda, sertifikaların doğru yapılandırıldığından ve eş adlarının uyumlu olduğundan emin olun.
	• Ağ bağlantı sorunlarında, ağ ekipleri ile birlikte çalışarak altyapı sorunlarını giderin.
	• IBM MQ 9.4.0 sonrası gelen geliştirilmiş hata mesajlarını inceleyerek sorunları daha hızlı çözebilirsiniz.
