IBM MQ Telemetri Problemleri Giderme
IBM MQ Telemetry (MQXR) hizmeti, telemetri kanallarını ve MQTT istemcilerini destekler. Ancak bu hizmetle ilgili çeşitli problemler ortaya çıkabilir. Aşağıda, belirli problemleri tanımlama ve çözme yöntemlerini içeren kapsamlı bir açıklama bulunmaktadır.

Telemetri Günlükleri, Hata Kayıtları ve Yapılandırma Dosyalarının Konumu
Sunucu Tarafı Günlükleri ve Hataları:
	• MQXR hizmeti, hata bilgilerini IBM MQ hata dizinine yazar. FDC dosyaları aşağıdaki yolda bulunabilir:WMQ data directory\errors\AMQ nnn.n.FDC
	• MQXR hizmeti ayrıca kendi günlük dosyasını oluşturur:WMQ data directory\Qmgrs\qMgrName\errors\mqxr.logJSON formatında hata günlüğü etkinleştirilirse:WMQ data directory\Qmgrs\qMgrName\errors\mqxr.json
Sunucu Tarafı Yapılandırma Dosyaları:
	• Telemetri kanalları ve hizmeti için yapılandırmalar şu dosyalarda saklanır:bashCopy codeWMQ data directory\Qmgrs\qMgrName\mqxr\mqxr_win.properties (Windows)/var/mqm/qmgrs/qMgrName/mqxr/mqxr_unix.properties (AIX veya Linux)
	• JVM yapılandırma dosyası:WMQ data directory\Qmgrs\qMgrName\mqxr\java.properties
Trace Yapılandırması:
	• İzleme yapılandırma dosyaları:WMQ data directory\Qmgrs\qMgrName\mqxr\trace.configmqxrtraceOn.propertiesmqxrtraceOff.properties

JSON Formatında Günlükleri Etkinleştirme
	1. Dosyaları Güncelleyin:
		○ mqxrtraceOn.properties ve mqxrtraceOff.properties dosyalarını düzenleyin.
		○ Sadece JSON formatında günlükler için:Copy codehandlers=com.ibm.mq.util.logging.MQJSONErrorLogFileHandler
		○ Metin tabanlı günlüklerle birlikte JSON formatını kullanmak için:handlers=com.ibm.mq.util.logging.MQErrorLogFileHandler,com.ibm.mq.util.logging.MQJSONErrorLogFileHandler
	2. Hizmeti Yeniden Başlatın:
		○ Değişikliklerin etkili olması için MQTT hizmetini yeniden başlatın.

Düşük Bellek Hataları için Java Heap Dump Üretimi
	1. JVM Yapılandırma Dosyasını Düzenleyin:
		○ java.properties dosyasına şu satırı ekleyin:-Dcom.ibm.mq.MQXR.GenerateHeapDump=true
	2. Hizmeti Yeniden Başlatın:
		○ Değişikliklerin uygulanması için hizmeti yeniden başlatın.
	3. Sonuçlar:
		○ Düşük bellek hatası oluştuğunda, bir Java heap dump dosyası oluşturulur. Dosya şu dizinde bulunur:WMQ data directory\errors

MQTT İstemcisi Bağlantı Sorunlarını Çözme
	1. Hata Kodlarını Kontrol Edin:
		○ REASON_CODE_INVALID_PROTOCOL_VERSION: Protokol sürümünü doğrulayın.
		○ REASON_CODE_INVALID_CLIENT_ID: İstemci kimliği 23 bayttan uzun olmamalıdır.
		○ REASON_CODE_SERVER_CONNECT_ERROR: MQXR hizmetinin ve kuyruk yöneticisinin düzgün çalıştığını kontrol edin.
	2. Bağlantı Sorunlarını İzole Edin:
		○ netstat kullanarak soket adreslerini doğrulayın.
		○ ping komutuyla sunucu adresine erişimi kontrol edin.

MQTT Mesaj Kaybı Sorunlarını Giderme
	1. Kalite Servisini Ayarlayın:
		○ Mesajları At least once veya At most once kalite servisleri ile gönderin.
		○ CleanSession=false ayarını yaparak oturumun korunmasını sağlayın.
	2. Abonelikleri Kontrol Edin:
		○ MQTT istemci aboneliklerini IBM MQ Explorer veya runmqsc ile kontrol edin.
	3. Yetkilendirmeyi Doğrulayın:
		○ Yayıncı ve abonenin gerekli izinlere sahip olduğunu doğrulamak için dspmqaut komutunu kullanın.

MQXR Hizmeti Başlatma Sorunları
	1. Başlangıç Hataları:
		○ Sistem nesnelerini göstermek için IBM MQ Explorer'da sistem nesnelerini görünür hale getirin.
		○ Eksik dosyalar veya yanlış izinler olup olmadığını kontrol edin.
	2. Hata Kayıtlarını Kontrol Edin:
		○ Hataları mqxr.log ve AMQERR01.LOG dosyalarından inceleyin.

JAAS Oturum Açma Modülü Sorunları
	1. Konfigürasyonu Kontrol Edin:
		○ jaas.config dosyasında doğru sınıf adını belirttiğinizden emin olun.
	2. Günlükleri Kontrol Edin:
		○ mqxr.log dosyasında javax.security.auth.login.LoginException hatasını arayın.

Bu prosedürler ve çözümler, IBM MQ Telemetry hizmetiyle ilişkili yaygın sorunları tanımlamak ve çözmek için size rehberlik edecektir. Daha karmaşık durumlar için IBM Support ile iletişime geçebilirsiniz.
