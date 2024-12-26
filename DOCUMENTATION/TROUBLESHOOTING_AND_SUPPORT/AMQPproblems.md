AMQP Sorunlarını Giderme
Log ve Konfigürasyon Dosyalarının Bulunması
	• AMQP ile ilgili hata loglarını ve yapılandırma dosyalarını kontrol edin:
		○ Varsayılan yollar:
			§ Loglar: {MQ_DATA_PATH}/errors
			§ Konfigürasyon dosyaları: amqptraceOn.properties, amqptraceOff.properties, amqp_java.properties.
JSON Loglama Aktifleştirme
	1. amqptraceOn.properties ve amqptraceOff.properties dosyalarını açın.
	2. Aşağıdaki gibi handlers ayarını değiştirin:
		○ Sadece JSON Loglama:handlers= com.ibm.mq.util.logging.MQJSONErrorLogFileHandler
		○ Hem JSON hem metin tabanlı loglama:handlers= com.ibm.mq.util.logging.MQErrorLogFileHandler, com.ibm.mq.util.logging.MQJSONErrorLogFileHandler
	3. AMQP servisini yeniden başlatın:start SERVICE(SYSTEM.AMQP.SERVICE)
Düşük Bellek Hataları için Java Heap Dump Aktifleştirme
	1. amqp_java.properties dosyasını düzenleyin:-Dcom.ibm.mq.MQXR.GenerateHeapDump=true
	2. AMQP servisini yeniden başlatın.
	3. Oluşan heap dump dosyasını {WMQ_DATA_PATH}/errors dizininde bulabilirsiniz.

Dağıtık Sıra Yönetimi Sorunlarını Giderme
Yaygın Sorunlar
	• Mesajların Kuyruğa Ulaşmaması:
		○ Kanal durumunu kontrol edin:DISPLAY CHSTATUS(*)
		○ İletim kuyruğunun dolu olmadığından emin olun.
	• Dead-letter Queue Kullanımı:
		○ Teslim edilemeyen mesajlar için dead-letter kuyruğunu inceleyin:DISPLAY QL(SYSTEM.DEAD.LETTER.QUEUE) ALL
	• Sıra Yöneticisi Bağlantı Sorunları:
		○ İki sistem arasındaki bağlantıyı doğrulamak için:PING CHANNEL(channel_name)
Önemli MQSC Komutları
	• Kanalları başlatma veya durdurma:START CHANNEL(channel_name)STOP CHANNEL(channel_name)

Java ve JMS Sorunlarını Giderme
Yaygın Sorunlar
	• Bağlantı Hataları:
		○ CONNECTION_FACTORY ve QUEUE_CONNECTION_FACTORY ayarlarını doğrulayın.
		○ JMS dinleyici portlarının doğru yapılandırıldığından emin olun.
	• ClassNotFound veya NoClassDefFoundError:
		○ Gerekli tüm IBM MQ istemci kütüphanelerinin (örn. com.ibm.mqjms) classpath'te yer aldığından emin olun.
	• İşlem Geri Alım Sorunları:
		○ Uygulama kodunda işlemlerin doğru şekilde commit edildiğini kontrol edin.

Güvenlik Sorunlarını Giderme
Sertifika veya Kimlik Doğrulama Problemleri
	• SSL ayarlarını kontrol edin:DISPLAY CHANNEL(channel_name) SSLCIPH
	• Kullanıcı yetkilerini inceleyin:DISPLAY AUTHREC
Hata Logları
	• Güvenlikle ilgili logları kontrol edin:{MQ_DATA_PATH}/errors/AMQERR01.LOG

Sıra Yöneticisi Sorunlarını Giderme
Sıra Yöneticisi Başlatılamıyor
	1. Hata loglarını kontrol edin:cat {MQ_DATA_PATH}/errors/AMQERR01.LOG
	2. Sistem kaynaklarını doğrulayın:
		○ CPU ve bellek kullanımını kontrol edin.
		○ Uygulamalar arasındaki kaynak çatışmalarını analiz edin.
