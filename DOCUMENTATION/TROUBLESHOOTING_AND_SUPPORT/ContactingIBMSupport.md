Genel Veri Toplama Adımları
	1. Sorununuzu Netleştirin:
		○ Hangi sorunla karşılaşıyorsunuz?
		○ Sorun ne zaman başladı ve ne zaman sona erdi?
		○ Hangi uygulamalar, kullanıcılar veya IBM MQ objeleri etkileniyor?
	2. runmqras Komutu ile Otomatik Veri Toplama:
		○ Komut:runmqras -section defs,trace -qmlist QMA -caseno TS123456789
		○ Açıklama: defs yapılandırma bilgilerini, trace ise hata ayıklama bilgilerini toplar.
	3. Manuel Veri Toplama:
		○ Kuyruk yöneticisi yapılandırma dosyalarını ve hata günlüklerini kaydedin.
		○ mqconfig, dmpmqlog, amqsbcg gibi komutları kullanarak ek bilgiler toplayın.
		○ Sorunla ilgili ekran görüntüleri veya komut çıktıları ekleyin.
	4. Soruna Özel Ek Bilgiler Toplayın:
		○ AMS Problemleri: keystore.conf dosyaları ve sertifika detaylarını ekleyin.
		○ Kanal Problemleri: Hem yerel hem de uzak kuyruğu yöneticisinden eşzamanlı izleme verilerini alın.
		○ Java ve JMS Uygulamaları: mqjms.log, native_stdout.log, native_stderr.log gibi dosyaları ekleyin.
		○ TLS Problemleri: TLS sertifikalarının geçerlilik tarihlerini ve yapılandırma detaylarını sağlayın.
		○ Tetikleme Problemleri: Tetikleme sırasındaki izleme dosyalarını toplayın.
	5. Toplanan Verileri IBM'e Gönderin:
		○ FTP ve E-posta İle: IBM Software Support sayfasındaki talimatları takip edin.
		○ IBM My Support Site: Sorununuzu açıklayan bir vaka oluşturun ve topladığınız verileri buradan yükleyin.

****

IBM MQ Hata Günlüklerinin Kullanımı
IBM MQ, problem tanımlama ve giderme için farklı hata günlükleri sağlar. Hata günlüklerinin doğru kullanımı, sorunları hızlı bir şekilde çözmenize yardımcı olabilir. Bu belge, hata günlüklerinin nasıl kullanılacağını ve özelleştirileceğini açıklar.

Hata Günlükleri Türleri ve Konumları
	1. Genel Sistem Hata Günlükleri:
		○ Linux ve AIX: /var/mqm/errors
		○ Windows: MQ_INSTALLATION_PATH\errors
	2. Kuyruk Yöneticisi Hata Günlükleri:
		○ Kuyruk yöneticisinin adı biliniyorsa:
			§ Linux ve AIX: /var/mqm/qmgrs/qmname/errors
			§ Windows: MQ_INSTALLATION_PATH\qmgrs\qmname\errors
	3. İstemci Hata Günlükleri:
		○ İstemci uygulamaları için:
			§ Linux ve AIX: /var/mqm/errors
			§ Windows: MQ_DATA_PATH\errors
	4. Ön Yükleme Hataları:
		○ Sistem yapılandırması doğru şekilde yüklenemediğinde:
			§ Linux ve AIX: /var/mqm
			§ Windows: C:\Program Files\IBM\MQ

Hata Günlüğü Formatı
	• Hata mesajlarının detayları ISO 8601 formatında zaman damgaları ile kayıt edilir.
	• Mesajlar aşağıdaki önem seviyelerine göre sınıflandırılır:
		○ I (Informational): Bilgilendirme
		○ W (Warning): Uyarı
		○ E (Error): Hata
		○ S (Severe): Kritik Hata
		○ T (Termination): Sonlandırma
Örnek Mesaj:

AMQ7075W: Unknown attribute foo at /var/mqm/qmgrs/QM1/qm.ini in configuration data.Time(2023-12-06T10:15:30.456Z)

Günlük Yönetimi ve Özelleştirme
	1. Boyut ve Döngü Ayarları:
		○ Günlük dosyalarının varsayılan boyutu 32 MB’tır.
		○ QMErrorLog bölümünde LogSize parametresi ile değiştirilebilir.
	2. Mesajların Bastırılması:
		○ QMErrorLog Stanza:SuppressMessage=9999,9002,9209SuppressInterval=30
		○ Ortam Değişkenleri:export MQ_CHANNEL_SUPPRESS_MSGS=9999,9002,9209export MQ_CHANNEL_SUPPRESS_INTERVAL=60,5
	3. Yönlendirme ve Yetki:
		○ Hata mesajları uygun erişim izni olmayan kullanıcılar tarafından yazılamaz. Bu durumda, sistem hata günlüğüne yönlendirilir.
		○ MQ Explorer kullanarak hata mesajlarını özelleştirebilirsiniz.

Örnek Kullanım ve İnceleme
Hata Günlüğü Örneği:

plaintext
Copy code
17/11/2024 10:32:29 - Process(2132.1) User(USER_1) Program(runmqchi.exe)Host(HOST_1) Installation(Installation1)VRMF(8.0.0.0) QMgr (QM1)AMQ9542: Queue manager is ending.EXPLANATION:The program will end because the queue manager is quiescing.ACTION:None.
Hata Günlüğü İnceleme:
	• Sistem düzenleyicisi kullanarak hata günlüklerini inceleyebilirsiniz:less /var/mqm/qmgrs/QM1/errors/AMQERR01.LOG
