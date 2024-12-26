IBM MQ İzleme ve Performans Yönetimi
IBM MQ'nun performansını optimize etmek ve kuyruğunuzdaki potansiyel sorunları tespit etmek için izleme ve ayarlama tekniklerini kullanabilirsiniz. Aşağıda, IBM MQ ağınızı izleme ve performans iyileştirme yollarına dair ayrıntılar bulunmaktadır.

1. IBM MQ Ağını İzleme
a. İzleme Amaçları
	• Sorunları algılama ve kök nedenlerini belirleme.
	• Kuyruk yöneticisi ağının doğru çalıştığını doğrulama.
	• Gerçek zamanlı istatistikleri inceleme.
	• Mesaj hareketlerini ve son konumlarını kaydetme.
	• Uygulama kaynak kullanımını analiz etme.
	• Kapasite planlaması yapma.
b. İzleme Teknikleri
	• Olay İzleme: Kuyruk yöneticisi tarafından tespit edilen olaylar, özel mesajlar olarak olay kuyruklarına kaydedilir.
	• Mesaj İzleme: Mesajların kuyruk yöneticisi ağı üzerindeki rotalarını belirlemek için kullanılır.
	• Muhasebe ve İstatistik Mesajları: Uygulamaların gerçekleştirdiği MQI işlemleri veya IBM MQ sistemindeki aktiviteler hakkında bilgi sağlar.
	• Uygulama Aktivite İzleme: Uygulamaların MQ kaynaklarıyla nasıl etkileşime geçtiğini detaylı olarak izler.
	• Gerçek Zamanlı İzleme: Kuyruk ve kanalların mevcut durumunu anında incelemek için kullanılır.

2. Performans Ayarları
a. Genel Ayarlamalar
	• Sağlık Kontrolleri: Kuyruk yöneticisi, periyodik olarak sistem bileşenlerini ve performans durumunu kontrol eder. Varsayılan kontrol süresi 10 saniyedir, ancak gerekirse bu süre ayarlanabilir.
	• Dosya Sistemi Performansı: Log yazma işlemlerindeki gecikmeleri analiz etmek için AMQ_IODELAY parametresi kullanılabilir.
b. Kuyruk Yöneticisi Ayarları
	• ECHeartBeatLen: Genel sağlık kontrollerinin frekansını ayarlar (10-60 saniye).
	• LivenessHeartBeatLen: Log işlemlerinin ilerleme hızını kontrol eder (0-600 saniye).
c. Küme İzleme
	• Küme içindeki uygulama mesajlarını, kontrol mesajlarını ve logları izleyerek yük dengeleme durumunu gözlemleyin.

3. Olay İzleme
a. Olay Türleri
	• Performans Olayları: Belirli kuyruğun performansını etkileyebilecek koşulları bildirir.
	• Yapılandırma Olayları: Nesne oluşturma, değiştirme veya silme gibi işlemlerden haberdar eder.
	• Komut Olayları: Başarıyla çalıştırılan MQSC veya PCF komutlarını bildirir.
b. Olay Mesajlarının Yayınlanması
Olay mesajlarını yayımlamak için SYSTEM.ADMIN.QUEUE gibi sistem kuyrukları kullanılır.

4. Mesaj İzleme
a. Mesaj Yönlendirme Teknikleri
	• Aktivite Kaydı: Mesajın rotası üzerindeki aktiviteler raporlanır.
	• Trace-Route Mesajları: Mesajın geçtiği aktiviteleri ve rotasını detaylı olarak kaydeder.
b. IBM MQ Display Route Uygulaması
Komut satırı arayüzü ile trace-route mesajlarını görüntüleme ve analiz etme imkanı sunar:

bash
Copy code
dspmqrte -m <queue_manager_name> -q <queue_name>

5. OpenTelemetry Entegrasyonu
IBM MQ, OpenTelemetry ile entegre edilerek, birden fazla uygulama arasındaki veri akışını gözlemlemeye olanak tanır.
a. OpenTelemetry ile İzleme
	• IBM MQ, OpenTelemetry API çıkışı ile entegre olur.
	• İzleme hizmeti, IBM MQ API çıkışı olarak uygulanır.
b. Kurulum
Çıkışı etkinleştirmek için buradan indirilen dosyayı kullanabilirsiniz.

6. Aktivite Kaydı
a. Aktivite Raporları
Mesajların geçtiği aktiviteler hakkındaki bilgileri içerir. Bu bilgiler şu amaçlar için kullanılabilir:
	• Mesajın son bilinen konumunu belirleme.
	• Kuyruk yöneticisi ağı yapılandırma sorunlarını tespit etme.
b. Aktivite Kaydı Etkinleştirme
MQSC komutuyla aktivite kaydı ayarlanabilir:

bash
Copy code
ALTER QMGR ACTIVREC(QUEUE)

7. Performans İzleme Örnekleri
a. Gerçek Zamanlı İzleme
Kuyruk yöneticisinin mevcut durumunu kontrol etmek için MQSC komutları kullanabilirsiniz:

bash
Copy code
DISPLAY QSTATUS(<queue_name>) ALLDISPLAY CHSTATUS(<channel_name>) ALL
b. Uygulama Aktivite İzleme
Uygulamanın yaptığı MQI çağrılarını ve işlem sırasını analiz etmek için kullanılabilir:
	• Aktivite kaydını etkinleştirerek raporları SYSTEM.ADMIN.ACTIVITY.QUEUE kuyruğunda toplayabilirsiniz.

***

IBM MQ'de Kayıtlı Bilgilerin Edinilmesi ve Kullanımı
IBM MQ'de trace-route mesajları ve aktivite raporlarından kayıtlı bilgileri edinmek ve analiz etmek için farklı yöntemler bulunmaktadır. Bu bilgiler, sistem yöneticilerinin mesaj rotalarını ve aktivitelerini daha iyi anlamalarına yardımcı olur. Aşağıda bu bilgileri edinme ve kullanma yöntemleri detaylı bir şekilde açıklanmıştır.

1. Bilgi Edinme Teknikleri
IBM MQ’de aşağıdaki yöntemlerle kayıtlı bilgileri edinebilirsiniz:
	1. Trace-Route Yanıt Mesajları:
		○ Trace-route yanıt mesajlarını belirleyin ve içerdikleri aktivite bilgilerini analiz edin.
	2. Trace-Route Mesajları:
		○ Trace-route mesajlarını belirleyin ve içerdikleri aktivite bilgilerini inceleyin. Bu mesajlar, doğru parametrelere (örneğin, Accumulate parametresi) sahip olmalıdır.
	3. Aktivite Raporları:
		○ Aktivite raporlarını belirleyin ve analiz edin. Bu raporlar, MQRO_ACTIVITY rapor seçeneği belirtilmiş mesajlardan üretilir.

2. Trace-Route Yanıt Mesajlarından Bilgi Edinme
İşlem Adımları:
	1. Yanıt Mesajını Bulma:
		○ Mesajın descriptor’ında belirtilen reply-to kuyruğunu kontrol edin.
		○ Aşağıdaki kuyrukları kontrol edin:
			§ Hedef kuyruk yöneticisinde SYSTEM.ADMIN.TRACE.ROUTE.QUEUE.
			§ Eğer ortak bir kuyruk kuruluysa, bu ortak kuyruk.
			§ Maksimum aktivite sayısının aşılması durumunda trace-route mesajının yönlendirildiği kuyruk.
	2. Mesajı Alın:
		○ Trace-route yanıt mesajını alın.
	3. IBM MQ Display Route Uygulamasını Kullanın:
		○ Kayıtlı bilgileri görüntülemek için şu komutu kullanabilirsiniz:bashCopy codedspmqrte -m <queue_manager_name> -q <reply_queue_name>
	4. Bilgiyi Analiz Edin:
		○ Aktivite bilgilerini inceleyerek ihtiyaç duyduğunuz bilgiyi elde edin.

3. Trace-Route Mesajlarından Bilgi Edinme
İşlem Adımları:
	1. Mesajı Bulma:
		○ Trace-route mesajını hedef kuyruğunda arayın. Eğer mesaj hedef kuyruğunda değilse, aktivite kayıtları oluşturularak mesajın son bilinen konumunu belirlemeye çalışabilirsiniz.
	2. Mesajı Alın:
		○ Trace-route mesajını alın.
	3. IBM MQ Display Route Uygulamasını Kullanın:
		○ Aktivite bilgilerini analiz etmek için kullanın.
	4. Bilgiyi Analiz Edin:
		○ Mesaj rotası ve aktiviteleri hakkında detaylı bilgi edinin.

4. Aktivite Raporlarından Bilgi Edinme
İşlem Adımları:
	1. Raporları Bulun:
		○ Trace-route mesajları için oluşturulan tüm aktivite raporlarını belirleyin. Raporlar, belirli bir kuyruğa teslim edilmiş olabilir.
	2. Raporları Sıralayın:
		○ Raporları manuel olarak veya IBM MQ Display Route uygulamasını kullanarak sıralayın.
	3. Bilgiyi Analiz Edin:
		○ Raporlardaki aktivite bilgilerini inceleyerek gerekli bilgiyi çıkarın.

5. Ek Aktivite Bilgileri Kaydetme
Ek Bilgiler ve Kullanım Alanları
	• Trace-route mesajları üzerinden kullanıcı uygulamaları, aktiviteleri daha iyi tanımlamak için ek bilgileri kaydedebilir.
	• Ek bilgiler, PCF parametreleri kullanılarak yazılır. Örnekler:
		○ Renk Bilgisi (Color Info): Bir aktivitenin rengini belirtmek için kullanılır.
IBM MQ Display Route ile Görüntüleme
	• Ek bilgiler şu şekilde görüntülenebilir:plaintextCopy codeColor: 'Red'
Örnekler:
	1. Örnek 1:
		○ Renk parametresi, 65536 olarak kaydedilir ve uygulama bu değeri tanımazsa şu şekilde görüntülenir:plaintextCopy code65536: 'Red'
	2. Örnek 2:
		○ Renk parametresi tanımlanır ve şu şekilde gösterilir:plaintextCopy codeColor: 'Red'


****

IBM MQ Display Route Application (DSPMQRTE) Kullanımı
IBM MQ Display Route Application (dspmqrte), izleme (trace-route) mesajlarını ve ilişkili aktivite bilgilerini bir komut satırı arayüzü üzerinden çalıştırmak için kullanılır. Bu araç, mesajın bir kuyruk yöneticisi ağı üzerinden izlediği rotayı belirlemek ve mesaj aktivitelerini analiz etmek için güçlü bir araçtır.

Temel Kullanım Amaçları
	1. Trace-Route Mesajları Oluşturma ve Kuyruk Yöneticisi Ağına Gönderme:
		○ Mesaj rotalarını belirlemek için aktivite bilgilerini toplar.
		○ Mesajın hedefi, mesajın davranışları ve nasıl işleneceği gibi özellikler belirlenebilir.
	2. Aktivite Bilgilerini Sıralama ve Görüntüleme:
		○ Yeni oluşturulan bir trace-route mesajına ait aktiviteler veya daha önce oluşturulmuş bir mesaja ait aktiviteler görüntülenebilir.
	3. Mesaj Hatalarını Teşhis Etme:
		○ Hedef kuyruğa ulaşamayan mesajların son bilinen konumunu belirlemek için kullanılabilir.

Komut ve Parametreler
Komut Yapısı:

bash
Copy code
dspmqrte -m <QMgrName> -q <TargetQueue> [Opsiyonel Parametreler]
Temel Parametreler:
Parametre	Açıklama
-m QMgrName	Bağlanılacak kuyruk yöneticisinin adı.
-q TargetQueue	Hedef kuyruğun adı.
-rq ReplyToQueue	Yanıt mesajlarının gönderileceği kuyruk.
-ac	Aktivite bilgilerini mesajda biriktirir.
-ar	Biriktirilen bilgilerin bulunduğu bir yanıt mesajı ister.
-ro <Option>	Raporlama seçeneklerini belirler. Örneğin: activity veya discard.
-v <DisplayOption>	Görüntüleme seçeneklerini belirler: summary, all, veya outline.

Örnekler
1. Aktivite Raporları İsteme
Bu örnek, bir trace-route mesajının hedef kuyruğa ulaşması ve aktivite bilgilerinin raporlar halinde geri gönderilmesini içerir.

bash
Copy code
dspmqrte -m QM1 -q TARGET.Q -rq ACTIV.REPLY.Q
	• QM1: Bağlanılacak kuyruk yöneticisi.
	• TARGET.Q: Hedef kuyruk.
	• ACTIV.REPLY.Q: Yanıt kuyruğu.
Akış:
	1. Trace-route mesajı QM1 üzerinden gönderilir.
	2. Hedef kuyruğa ulaştığında mesaj işlenir ve ACTIV.REPLY.Q kuyruğuna aktivite raporları gönderilir.
	3. Raporlar sıralanır ve görüntülenir.

2. Trace-Route Yanıt Mesajı İsteme
Trace-route mesajındaki bilgileri toplamak için bir yanıt mesajı istemek amacıyla aşağıdaki komut kullanılır:

bash
Copy code
dspmqrte -m QM1 -q TARGET.Q -rq TR.REPLY.Q -ac -ar -ro discard
	• -ac: Aktivite bilgileri biriktirilir.
	• -ar: Yanıt mesajı oluşturulur.
	• -ro discard: Mesaj işlendikten sonra atılır.
Akış:
	1. Mesaj TARGET.Q kuyruğuna ulaşır.
	2. Aktivite bilgileri toplanır ve TR.REPLY.Q kuyruğuna gönderilir.
	3. Yanıt mesajı incelenerek tüm aktiviteler görüntülenir.

3. Kanal Problemi Teşhisi
Bir trace-route mesajının hedef kuyruğa ulaşamadığı durumları teşhis etmek için kullanılır.

bash
Copy code
dspmqrte -m QM1 -q TARGET.Q -rq ACTIV.REPLY.Q -v outline
	• -v outline: Yalnızca özet bilgiler görüntülenir.
Teşhis:
	• Gönderilen mesajın hangi noktada kaldığını belirler.
	• Kanalın çalışmaması gibi sorunlar tespit edilebilir.

Raporlama Seçenekleri
Raporlama Parametreleri:
	• -ro activity: Aktivite raporları oluşturur.
	• -ro discard: İşlenmiş mesajı atar.
	• -ro exception: Hatalar için rapor oluşturur.
Görüntüleme Seçenekleri:
	• -v summary: Özet bilgi görüntüler.
	• -v all: Tüm detayları görüntüler.
	• -v outline: Sadece temel bilgileri görüntüler.

Önemli Notlar
	1. Kuyruk Yöneticisi Ayarları:
		○ ACTIVREC veya ROUTEREC özelliklerinin doğru şekilde ayarlandığından emin olun.
	2. Mesaj ID ve Correlation ID:
		○ Belirli bir mesaj için detaylı bilgi almak amacıyla kullanılabilir.
	3. Hata Teşhisi:
		○ Gönderilen mesajın son ulaştığı noktayı ve olası sorunları belirlemek için kullanılabilir.


***

IBM MQ - Activity Report Message Data
Activity raporları, IBM MQ'ya gönderilen mesajların kuyruk yöneticisi ağı boyunca nasıl işlendiğini detaylı olarak açıklayan önemli bilgi kaynaklarıdır. Bu raporlar, Activity PCF Group ve TraceRoute PCF Group adlı iki ana bilgi grubundan oluşur.

Activity PCF Group
Bu grup, her bir aktivite için aşağıdaki bilgileri içerir:
Parametre	Açıklama	Identifier	Data Type	Geri Dönen Durum
ActivityApplName	Aktiviteyi gerçekleştiren uygulamanın adı.	MQCACF_APPL_NAME	MQCFST	Her zaman
ActivityApplType	Aktiviteyi gerçekleştiren uygulamanın türü.	MQIA_APPL_TYPE	MQCFIN	Her zaman
ActivityDescription	Aktivite hakkında kısa bir açıklama.	MQCACF_ACTIVITY_DESCRIPTION	MQCFST	Her zaman

Operation PCF Group
Bir aktivite sırasında gerçekleştirilen işlemleri açıklar. Her işlem için şu detaylar döner:
Parametre	Açıklama	Identifier	Data Type	Geri Dönen Durum
OperationType	Gerçekleştirilen işlemin türü.	MQIACF_OPERATION_TYPE	MQCFIN	Her zaman
OperationDate	İşlemin gerçekleştirildiği tarih.	MQCACF_OPERATION_DATE	MQCFST	Her zaman
OperationTime	İşlemin gerçekleştirildiği saat.	MQCACF_OPERATION_TIME	MQCFST	Her zaman
Message	İşlem sırasında işlenen mesajın detayları (uzunluk, MQMD).	MQGACF_MESSAGE	MQCFGR	Her zaman

İşlem Türüne Göre Ek Parametreler
	1. Get/Browse (MQOPER_GET/MQOPER_BROWSE):
		○ QName: Açılan kuyruğun adı.
		○ ResolvedQName: Kuyruğun çözümleme sonucu ismi.
	2. Discard (MQOPER_DISCARD):
		○ Feedback: Mesajın neden silindiğini açıklar.
		○ QName: Mesajın silindiği kuyruk.
		○ RemoteQMgrName: Mesajın gönderildiği kuyruk yöneticisinin adı.
	3. Put/Put Reply/Put Report (MQOPER_PUT/MQOPER_PUT_REPLY/MQOPER_PUT_REPORT):
		○ QName: Açılan kuyruğun adı.
		○ ResolvedQName: Kuyruğun çözümleme sonucu ismi.
		○ RemoteQName: Mesajın gönderildiği uzak kuyruk.
		○ RemoteQMgrName: Uzak kuyruk yöneticisinin adı.
	4. Send (MQOPER_SEND):
		○ ChannelName: Mesajın gönderildiği kanalın adı.
		○ ChannelType: Kanal türü.
		○ XmitQName: Mesajın alındığı iletim kuyruğu.
		○ RemoteQMgrName: Mesajın gönderildiği uzak kuyruk yöneticisinin adı.
	5. Receive (MQOPER_RECEIVE):
		○ ChannelName: Mesajın alındığı kanal.
		○ ChannelType: Kanal türü.
		○ RemoteQMgrName: Mesajın geldiği uzak kuyruk yöneticisinin adı.

TraceRoute PCF Group
Bu grup, izleme (trace-route) mesajlarının özel parametrelerini içerir. Örnek parametreler:
Parametre	Açıklama	Identifier	Geri Dönen Durum
RecordedActivities	Kaydedilen aktivitelerin sayısı.	MQIACF_RECORDED_ACTIVITIES	Trace-Route varsa
DiscontinuityCount	Süreksizlik sayısı (mesaj yönlendirmesinde).	MQIACF_DISCONTINUITY_COUNT	Trace-Route varsa

Rapor Verilerinin Kullanımı
	1. Get/Browse İşlemleri:
		○ Kuyrukta alınan veya göz atılan mesajları analiz etmek için QName ve ResolvedQName bilgileri kullanılır.
	2. Discard İşlemleri:
		○ Mesajın neden silindiğini anlamak için Feedback parametresi analiz edilir.
	3. Send/Receive İşlemleri:
		○ Mesajın hangi kanaldan gönderildiği veya alındığını belirlemek için ChannelName ve RemoteQMgrName incelenir.
	4. Trace-Route Mesajları:
		○ Mesajın geçtiği yolları analiz etmek için TraceRoute bilgileri gözden geçirilir.


****

IBM MQ - Trace-Route Message Reference
IBM MQ Trace-route mesajları, bir mesajın kuyruk yöneticisi ağı boyunca izlediği yolu ve bu süreçte gerçekleştirilen aktiviteleri anlamak için tasarlanmış standart mesajlardır. Aşağıda bu mesaj formatı, içerdiği bileşenler ve bunların kullanımı açıklanmaktadır.

1. Trace-Route Message Format
Trace-route mesajları, şu bileşenlerden oluşur:
	• MQMD (Message Descriptor): Mesajın temel meta verilerini içerir. Örneğin, mesaj türü, geçerlilik süresi ve mesaj kimlik bilgileri.
	• MQCFH veya MQEPH (Programmable Command Format Header): Mesajın içeriği hakkında bilgi verir.
	• Mesaj Verisi:
		○ TraceRoute PCF Group: İzleme bilgilerini içerir.
		○ Activity PCF Groups: Belirtilen aktivitelerin detaylarını içerir (isteğe bağlı).
Mesaj Formatı Detayları:
Bileşen	Açıklama
MQMD	Mesajın üst bilgi meta verileri.
TraceRoute PCF Group	İzleme sırasında kaydedilen aktiviteleri açıklar.
Activity PCF Groups	Mesaj üzerindeki aktivitelerin detaylı verilerini içerir.

2. MQMD (Message Descriptor) Detayları
Trace-route mesajları için kullanılan MQMD yapılandırması aşağıdaki gibidir:
Parametre	Açıklama	Değer
StrucId	Yapı tanımlayıcı.	MQMD_STRUC_ID
MsgType	Mesaj türü.	MQMT_DATAGRAM veya MQMT_REQUEST
Format	Mesaj formatı.	MQFMT_ADMIN veya MQFMT_EMBEDDED_PCF
Expiry	Mesajın geçerlilik süresi (saniye cinsinden).	İsteğe bağlı.
Report	Raporlama seçenekleri.	Örneğin, MQRO_DISCARD_MSG.
ReplyToQ	Yanıtın gönderileceği kuyruk.	İsteğe bağlı.
ReplyToQMgr	Yanıtın gönderileceği kuyruk yöneticisi.	İsteğe bağlı.

3. TraceRoute PCF Group
Bu grup, trace-route mesajlarının işlenmesini kontrol eden parametreleri içerir.
Parametre	Açıklama	Değerler
Detail	Kaydedilecek detay seviyesi.	MQROUTE_DETAIL_LOW, MEDIUM, HIGH.
RecordedActivities	Kaydedilen aktivitelerin sayısı.	Pozitif bir tamsayı.
UnrecordedActivities	Kaydedilmeyen aktivitelerin sayısı.	Pozitif bir tamsayı.
DiscontinuityCount	Desteklenmeyen kuyruk yöneticilerinden geçiş sayısı.	Pozitif bir tamsayı.
MaxActivities	Trace-route mesajının durmadan önce katılabileceği maksimum aktivite.	Pozitif bir tamsayı veya UNLIMITED.
Accumulate	Aktivite bilgilerinin nasıl kaydedileceğini belirtir.	NONE, IN_MSG, AND_REPLY.
Forward	Mesajın yönlendirileceği kuyruk yöneticilerini sınırlar.	FORWARD_IF_SUPPORTED, FORWARD_ALL.
Deliver	Mesajın hedef kuyruğa ulaştığında ne yapılacağını belirler.	DELIVER_YES, DELIVER_NO.

4. Trace-Route Reply Messages
Bir trace-route mesajı hedef kuyruğa ulaştığında, bir trace-route yanıt mesajı oluşturulabilir. Bu yanıt mesajı, orijinal trace-route mesajındaki aktivite bilgilerini kopyalar.
Trace-route Yanıt Mesaj Formatı:
	• MQMD: Mesaj kimlik bilgilerini içerir.
	• MQCFH: Programlanabilir komut formatı başlığı.
	• Activity PCF Groups: Aktivite bilgilerini içerir.

Kullanım Senaryoları
	1. Mesaj Yollarını İzleme:
		○ TraceRoute grubu, mesajın geçtiği kuyruk yöneticilerini ve aktiviteleri detaylı olarak raporlar.
	2. Sorun Giderme:
		○ DiscontinuityCount veya UnrecordedActivities değerlerini kullanarak mesajın kaydedilmediği veya desteklenmediği noktalar belirlenebilir.
	3. Aktivite Raporlama:
		○ Trace-route yanıt mesajları, aktiviteleri ve mesajın yönlendirildiği yolları incelemek için kullanılır.

****

IBM MQ - Muhasebe ve İstatistik Mesajları
IBM MQ, uygulamalarınızın yaptığı işlemler ve sistem genelindeki aktivitelerle ilgili bilgi toplamak için Muhasebe (Accounting) ve İstatistik (Statistics) mesajlarını kullanır. Bu mesajlar, sistemin performansını izlemek, sorunları tespit etmek ve kapasite planlaması yapmak için oldukça önemlidir.

Muhasebe Mesajları
Amaç
Muhasebe mesajları, IBM MQ uygulamaları tarafından yapılan MQI (Message Queue Interface) işlemleriyle ilgili detayları kaydeder.
Türleri
	1. MQI Muhasebe Mesajları:
		○ Bir bağlantı sırasında yapılan MQI çağrılarının sayısını içerir.
	2. Kuyruk Muhasebe Mesajları:
		○ Belirli bir kuyruk için yapılan MQI çağrılarını detaylandırır.
		○ Bir mesajda 100'e kadar kuyruk kaydı olabilir.
Mesaj Yapısı
	1. Mesaj Tanımlayıcısı (MQMD):
		○ Mesajın meta bilgilerini içerir (örneğin; tür, kimlik, süreklilik).
	2. Mesaj Verisi (PCF - Programmable Command Format):
		○ MQCFH (PCF Başlığı): Uygulama hakkında bilgi ve verilerin toplandığı zaman aralığını içerir.
		○ Muhasebe Verileri:
			§ MQI Muhasebe: Genel bağlantı aktivitesi.
			§ Kuyruk Muhasebe: Belirli kuyruklarla ilgili detaylar.
Oluşum Şartları
	• Bir uygulama şu durumlarda muhasebe mesajı üretir:
		1. Bağlantıyı keserse (MQDISC):
			§ Örneğin; bir işlem tamamlandığında.
		2. Uzun süre çalışıyorsa (Ara Mesajlar):
			§ Belirli aralıklarla ara mesajlar yazılır (örneğin 30 dakikada bir).
Kontrol Ayarları
	• Kuyruk Yöneticisi Ayarı: ACCTMQI:
		○ MQI muhasebe verisini toplar.
		○ Örnek:ALTER QMGR ACCTMQI(ON)
	• Kuyruk Ayarı: ACCTQ:
		○ Belirli bir kuyruğun muhasebesini kontrol eder.
		○ Örnek:ALTER QLOCAL(Q1) ACCTQ(ON)

İstatistik Mesajları
Amaç
İstatistik mesajları, sistemdeki genel aktiviteleri (örneğin; kuyruk ve kanal işlemleri) kaydeder.
Türleri
	1. MQI İstatistik Mesajları:
		○ Belirli bir zaman aralığında yapılan MQI çağrılarının sayısını kaydeder.
	2. Kuyruk İstatistik Mesajları:
		○ Bir kuyruğa yapılan mesaj gönderme, alma ve toplam bayt işlemleriyle ilgili detayları içerir.
	3. Kanal İstatistik Mesajları:
		○ Belirli bir kanal üzerinden aktarılan mesaj ve bayt bilgilerini içerir.
Mesaj Yapısı
	1. Mesaj Tanımlayıcısı (MQMD):
		○ Muhasebe mesajlarıyla benzerdir.
	2. Mesaj Verisi (PCF):
		○ MQCFH (PCF Başlığı): Zaman aralığını detaylandırır.
		○ İstatistik Verileri:
			§ MQI İstatistik: Genel çağrı aktivitesi.
			§ Kuyruk İstatistik: Belirli kuyruk aktiviteleri.
			§ Kanal İstatistik: Kanal aktiviteleri.
Oluşum Şartları
	• Belirli aralıklarla oluşturulur (örneğin; her 30 dakikada bir).
	• Kuyruk yöneticisi kapatılırken de istatistik mesajları üretilir.
Kontrol Ayarları
	• MQI İstatistik: STATMQI:
		○ Örnek:ALTER QMGR STATMQI(ON)
	• Kuyruk İstatistik: STATQ:
		○ Örnek:ALTER QLOCAL(Q1) STATQ(ON)
	• Kanal İstatistik: STATCHL:
		○ Örnek:ALTER CHANNEL(CH1) STATCHL(MEDIUM)

Kullanım Alanları
	1. Sorun Tespiti:
		○ Kuyruk ve kanal işlemleriyle ilgili problemleri tespit eder.
	2. Kapasite Planlama:
		○ Mesaj işleme oranlarını izler.
	3. Optimizasyon:
		○ Tıkanıklıkları ve performans iyileştirme noktalarını belirler.

Veri Analiz Araçları
IBM MQ, verileri analiz etmek için amqsmon adlı bir araç sunar. Bu araç, muhasebe ve istatistik mesajlarını okunabilir bir biçimde görüntüler.
Örnekler
	1. MQI istatistiklerini göster:amqsmon -m QM1 -t statistics -a
	2. Q1 kuyruğunun istatistiklerini göster:amqsmon -m QM1 -t statistics -q Q1
	3. Belirli bir tarihteki muhasebe mesajlarını göster:amqsmon -m QM1 -t accounting -s "2024-12-06"

En İyi Uygulamalar
	1. Seçici Veri Toplama:
		○ Belirli kuyruklar ve kanallar için muhasebe ve istatistik toplamayı etkinleştirin.
	2. Düzenli İzleme:
		○ amqsmon veya özel araçlarla verileri düzenli analiz edin.
	3. Aralıkları Optimum Ayarlama:
		○ Detay seviyesi ile sistem yükü arasında denge kurun (örneğin, ACCTINT ve STATINT ile).
		IBM MQ - Uygulama Aktivitesi İzleme ve Gerçek Zamanlı İzleme
		IBM MQ'de uygulamaların davranışlarını, kuyruk yöneticisi üzerindeki aktivitelerini ve sistem durumlarını detaylı şekilde izlemek için Application Activity Trace (Uygulama Aktivitesi İzleme) ve Gerçek Zamanlı İzleme araçları kullanılabilir. Bu araçlar, özellikle sorun çözme, yük dengeleme ve sistem optimizasyonu için önemlidir.
		
		Uygulama Aktivitesi İzleme (Application Activity Trace)
		Amaç
			• Uygulama Aktivitesi İzleme, bir uygulamanın IBM MQ kaynaklarıyla nasıl etkileşimde bulunduğunu gösterir.
			• Yapılan MQI çağrıları ve bu çağrılarda kullanılan parametreler detaylı şekilde izlenebilir.
			• Muhasebe, istatistik ve olay izleme araçlarından daha fazla bilgi gerektiğinde kullanılır.
		Özellikler
			1. Merkezi İzleme: İzleme verileri, SYSTEM.ADMIN.TRACE.ACTIVITY.QUEUE kuyruğuna yazılır ve buradan okunabilir.
			2. Abonelik Tabanlı İzleme: Sistem konularına abone olarak izleme verileri alınabilir.
		Merkezi İzleme Yapılandırması
			• ACTVTRC Özelliği:
				○ Kuyruk yöneticisinde izlemeyi etkinleştirmek için kullanılır.
				○ Örnek:ALTER QMGR ACTVTRC(ON)
			• Aktivite İzleme Yapılandırma Dosyası:
				○ Uygulama seviyesinde izleme ayarları yapılabilir.
		Abonelik Tabanlı İzleme
			• $SYS/MQ sistem konularına abone olarak veri alınabilir.
			• Örnek bir izleme konusu: $SYS/MQ/INFO/QMGR/<QueueManagerName>/ActivityTrace.
		
		Gerçek Zamanlı İzleme
		Amaç
		Gerçek zamanlı izleme, kuyruklar ve kanalların o anki durumunu belirlemek için kullanılır. Bu, sistem yöneticilerinin mevcut durumu anlamasını ve olası sorunları teşhis etmesini sağlar.
		İzleme Adımları
			1. Kuyruk İzleme:
				○ Kuyrukların doğru şekilde çalıştığını kontrol etmek için kullanılır.
				○ Kuyruk özellikleriyle gerçek zamanlı izleme etkinleştirilmelidir.
				○ Örnek Komut:DISPLAY QSTATUS(Q1) ALL
			2. Kanal İzleme:
				○ Kanalların düzgün çalışıp çalışmadığını kontrol etmek için kullanılır.
				○ Kanal özellikleriyle izleme etkinleştirilmelidir.
				○ Örnek Komut:DISPLAY CHSTATUS(SYSTEM.DEF.SVRCONN) ALL
			3. Küme Yük Dengesi İzleme:
				○ Bir kümedeki kuyrukların yük dağılımını ve denge durumunu kontrol etmek için kullanılır.
				○ Örnek Komut:DISPLAY APSTATUS(*) TYPE(QMGR)
		Gerçek Zamanlı İzleme Özellikleri
			• Kuyruk ve Kanal Durum Özellikleri:
				○ Kuyruk veya kanalların izleme bilgilerini tutar.
				○ Örneğin: CURDEPTH (Kuyruk derinliği), XQMSGSA (Gönderim kuyruğundaki mesaj sayısı).
			• Örnek Durum Gösterimi:DISPLAY QSTATUS(Q1) CURDEPTH
		Yük Dengesi İzleme
			• Örneğin bir uygulamanın kümelenmiş bir sistemde nasıl dağıtıldığını görmek için:DISPLAY APSTATUS(MYAPP) TYPE(QMGR)
		
		Uygulama Aktivitesi İzleme ile İlgili Önemli Noktalar
			1. İzleme Verilerinin Merkezi Toplanması:
				○ İzleme verileri SYSTEM.ADMIN.TRACE.ACTIVITY.QUEUE kuyruğuna yazılır.
				○ Buradan bir uygulama ile alınabilir ve analiz edilebilir.
			2. Dinamik Abonelik:
				○ İzleme verilerini almak için $SYS/MQ konularına abone olunabilir.
				○ Abone olma yetkisi gereklidir.
			3. İzleme Formatı:
				○ İzleme mesajları bir PCF mesajı formatındadır.
				○ Veriler genelde zaman damgaları ve yapılan işlemlerin parametrelerini içerir.
		
		Sorun Çözme ve Örnek Komutlar
		Kuyruk Derinliği İzleme
		
		DISPLAY QSTATUS(Q1) CURDEPTH
		Kanal Durumu İzleme
		
		DISPLAY CHSTATUS(SYSTEM.DEF.SVRCONN) ALL
		Küme Yük Dengesi
		
		DISPLAY APSTATUS(*) TYPE(QMGR)
		Aktivite İzleme Aboneliği
		
		SUBSCRIBE TOPICSTR('$SYS/MQ/INFO/QMGR/QM1/ActivityTrace') DEST('MY.QUEUE')

****

IBM MQ Ağ Performansını İyileştirme
IBM MQ ağı performansını optimize etmek için çeşitli ayarlamalar yapılabilir. Bu ayarlar, özellikle istemci bağlantı kanalları, yayın/abone sistemleri ve yüksek gecikmeli ağlar üzerinde önemli iyileştirmeler sağlar.

1. İstemci ve Sunucu Bağlantı Kanallarını Ayarlama
SHARECNV (Paylaşılan Konuşmalar) Parametresi
	• Varsayılan Değer: SHARECNV(10) (Her kanal örneği için 10 paylaşılan konuşma).
	• En İyi Performans İçin Ayarlar:
		○ SHARECNV(1): Paylaşılan konuşmalar kullanılmaz; daha düşük gecikme ve daha az kaynak tüketimi sağlar.
		○ SHARECNV(0): Eski istemci uygulamaları için; paylaşılan konuşmalar devre dışıdır ve modern iyileştirmeler uygulanmaz.
SHARECNV Ayarlarının Performansa Etkisi
	• SHARECNV(1):
		○ Paylaşılan konuşma yok, daha az iş parçacığı ve bellek kullanımı.
		○ Soket kullanımında artış ve kanal örneği sayısında artış.
	• SHARECNV(10) (Varsayılan):
		○ Çoğu durumda yeterlidir, ancak dağıtık sunucularda %15 performans düşüşüne neden olabilir.
Ayar Örnekleri
	• SHARECNV değerini 1 yapma:ALTER CHANNEL(MY.CHANNEL) CHLTYPE(SVRCONN) SHARECNV(1)
	• Kanal Maksimum Değerlerini Artırma (Gerekirse):ALTER QMGR MAXCHANNELS(500) MAXACTIVECHANNELS(400)

2. Yayın/Abone Sistemlerinde Performans İyileştirme
Doğrudan Yönlendirme vs. Konu Ana Bilgisayar Yönlendirme
	• Doğrudan Yönlendirme:
		○ Tüm küme üyelerine bilgi iletilir, bu da sistem yükünü artırabilir.
		○ İyileştirme Önerisi:
			§ Yoğun olmayan saatlerde güncellemeleri gerçekleştirin.
			§ Daha küçük, "örtüşen" bir küme tanımlayın.
	• Konu Ana Bilgisayar Yönlendirme:
		○ Konular belirli kuyruk yöneticilerine atanır.
		○ Daha az bağlantı ve bilgi aktarımı sağlar.
Üretici ve Tüketici Dengesini Sağlama
	• Mesaj tüketicileri ile üreticileri arasında denge kurulmazsa, tüketilmemiş mesaj birikmesi performansı etkileyebilir.
	• Öneri:
		○ Tüketim oranlarını düzenli olarak izleyin ve gerektiğinde kaynakları yeniden yönlendirin.
Konu Ağacındaki Gereksiz Konuları Azaltma
	• TREELIFE Özelliği:
		○ Kullanılmayan konular varsayılan olarak 30 dakika sonra silinir.
		○ Örnek:ALTER QMGR TREELIFE(900)
	• Konu Ağacını Görüntüleme:DISPLAY TPSTATUS('#') TYPE(TOPIC)

3. Yüksek Gecikmeli Ağlarda Performans
Aspera Gateway Kullanımı
	• Avantajlar:
		○ Yüksek gecikmeli veya paket kaybı yaşayan ağlarda veri iletimini hızlandırır.
		○ Özellikle veri merkezleri arasındaki bağlantılar için etkilidir.
	• Dikkat Edilmesi Gerekenler:
		○ Düşük gecikmeli ağlarda performansı düşürebilir.
		○ Ağ performansı Aspera bağlantısı tanımlanmadan önce ve sonra kontrol edilmelidir.

Genel Performans Ayar Önerileri
Kanal Performansı İzleme
	• Kanal performansını izlemek için:DISPLAY CHSTATUS(MY.CHANNEL) ALL
Kuyruk Derinliği İzleme
	• Kuyruk derinliğini kontrol etmek için:DISPLAY QSTATUS(MY.QUEUE) CURDEPTH
TREELIFE Ayarını Güncelleme
	• Konu yaşam süresini kısaltmak için:ALTER QMGR TREELIFE(600)

