IBM MQ'de uygulama geliştirme, farklı programlama dillerinde mesaj göndermek, almak ve kuyruk yöneticileri ile ilişkili kaynakları yönetmek için geniş bir olanak sunar. IBM MQ ile uyumlu programlama dilleri ve araçlarla uygulama geliştirirken bilmeniz gereken temel bilgileri aşağıda bulabilirsiniz.

IBM MQ'de Uygulama Geliştirme
Desteklenen Programlama Dilleri
IBM MQ, aşağıdaki dillerde ve çerçevelerde uygulama geliştirme desteği sunar:
	1. Nesne Yönelimli Diller:
		○ Java/JMS: Jakarta Messaging 3.0 ve Java Message Service (JMS) 2.0 desteği sunar.
		○ C++: MQ nesneleriyle uyumlu sınıflar sağlar.
		○ .NET: .NET platformunda C# ve Visual Basic dilleri için destek içerir.
	2. Prosedürel Diller:
		○ C
		○ COBOL
		○ Assembler (IBM MQ for z/OS)
		○ RPG (IBM i)
	3. Modern API’ler:
		○ REST API’ler ile mesaj gönderme ve alma desteği.
		○ Node.js, Go gibi modern dillerde örnekler.

Uygulama Türleri
IBM MQ üzerinde geliştirebileceğiniz uygulama türleri:
	1. Mesaj Gönderme ve Alma:
		○ Mesajları kuyruklara gönderen veya kuyruklardan alan uygulamalar.
	2. Kuyruk Yöneticisi Yönetimi:
		○ Kuyruk yöneticileri ve diğer MQ kaynaklarını yöneten uygulamalar.
	3. Transaction Yönetimi:
		○ IBM MQ, XA Transaction Manager olarak hareket ederek, diğer kaynak yöneticileriyle uyumlu işlemler sağlar.
	4. İleri Düzey Kullanım:
		○ Çoklu kuyruk yöneticileri arasında yük dengeleme.
		○ Mesaj gruplama ve segmentasyon.

Mesaj Türleri
IBM MQ, dört temel mesaj türünü destekler:
	1. Datagram: Yanıt gerektirmeyen mesajlar.
	2. İstek Mesajı (Request): Yanıt bekleyen mesajlar.
	3. Yanıt Mesajı (Reply): Gelen istek mesajlarına yanıtlar.
	4. Rapor Mesajı (Report): Olayları bildiren mesajlar.

Nesne Yönelimli Programlama ile IBM MQ
Nesne yönelimli dillerde IBM MQ'nun nesne modelini kullanabilirsiniz:
	• MQQueueManager: Kuyruk yöneticisi bağlantısını temsil eder.
	• MQQueue: Kuyruğa mesaj gönderir veya kuyruğa gelen mesajları alır.
	• MQMessage: Mesajın içeriğini ve meta verilerini temsil eder.

Prosedürel Programlama ile IBM MQ
Prosedürel dillerde, MQI (Message Queue Interface) kullanılarak kuyruklara erişim sağlanır:
	• MQPUT: Mesaj gönderme.
	• MQGET: Mesaj alma.
Örnek:

MQMD md = {MQMD_DEFAULT};
MQPUT(queueHandle, &md, &putOptions, dataLength, data, &compCode, &reason);

Uygulama Tasarımı ve Geliştirme Konuları
	1. Mesaj Kalıcılığı (Persistence):
		○ Kalıcı mesajlar disk üzerinde saklanır ve kuyruk yöneticisi yeniden başlatıldığında kurtarılır.
		○ Performans için geçici mesajlar kullanılabilir.
	2. Güvenlik:
		○ TLS kullanarak veri şifreleme.
		○ JAAS ve kullanıcı doğrulama mekanizmaları.
	3. Yük Dengeleme ve Ölçeklenebilirlik:
		○ Uniform Clusters ile yük dengeleme ve yeniden bağlantı.
	4. Mesaj Formatı ve Dönüşüm:
		○ MQFMT_STRING gibi yerleşik formatlar.
		○ Özel dönüşüm ihtiyaçları için veri dönüşüm çıkışları (Data Conversion Exits).

Çoklu Kuyruk Yöneticisi ile Bağlantı
Birden fazla kuyruk yöneticisine bağlanmak için:
	• CCDT (Client Channel Definition Table): Farklı kuyruk yöneticilerine bağlantı bilgisi sağlar.
	• Load Balancer: Yük dengelemesi yaparak istekleri yönlendirir.

Örnek Uygulama Kodları
	1. Java JMS Örneği:

QueueConnectionFactory factory = new MQQueueConnectionFactory();
Queue queue = session.createQueue("QUEUE_NAME");
MessageProducer producer = session.createProducer(queue);
TextMessage message = session.createTextMessage("Hello MQ!");
producer.send(message);
	2. C++ Örneği:

MQQueueManager qMgr("QM1");
MQQueue queue = qMgr.AccessQueue("QUEUE1", MQOO_OUTPUT);
MQMessage msg("Hello MQ!");
queue.Put(msg);
	
	
IBM MQ Uygulamaları için Tasarım Değerlendirmeleri
IBM MQ uygulamaları tasarlarken, platformlar ve çevrelerden nasıl yararlanacağınızı belirledikten sonra, IBM MQ’nun sunduğu özellikleri en verimli şekilde kullanmayı planlamanız gerekir.

Tasarım Aşamasında Dikkat Edilmesi Gerekenler
1. Uygulama Türü
	• Server: Kuyruk yöneticileri üzerinde çalışan uygulamalar.
	• Client: IBM MQ’ya istemci olarak bağlanan uygulamalar.
	• Yayınlama/Abonelik (Publish/Subscribe): Mesajların belirli konulara (topic) gönderilmesi.
	• Web Servisleri: MQ kullanarak REST veya SOAP ile entegrasyon.
	• Kullanıcı Çıkışları (User Exits): MQ işlemlerini özelleştirmek için kullanılan API çıkışları.
2. Programlama Dili
	• IBM MQ, Java, JMS, .NET, C, C++, COBOL, RPG gibi dilleri destekler.
	• Çoklu platform uyumluluğu için standart programlama dilleri kullanılmalıdır (örn. ANSI C).
3. Kuyruk Türleri
	• Statik Kuyruklar: Önceden tanımlanmış ve tekrar kullanılabilir.
	• Dinamik Kuyruklar: Kullanıldığında oluşturulup iş bitiminde silinir.
	• Alias Kuyruklar: Uygulama bağımsızlığı için kullanılabilir.
4. Mesaj Türleri
	• Datagram: Basit, yanıt gerektirmeyen mesajlar.
	• İstek Mesajları: Yanıt beklenen durumlar için.
	• Yanıt Mesajları: İstek mesajlarına yanıt olarak gönderilir.
	• Rapor Mesajları: Olaylar veya hata durumları hakkında bilgi verir.

Mesajlaşma Modelleri
Nokta-Nokta (Point-to-Point):
	• Gönderici, mesajı doğrudan belirli bir kuyruğa gönderir.
	• Alıcı, mesajı bu kuyruğa erişerek alır.
Yayınlama/Abonelik (Publish/Subscribe):
	• Gönderici, mesajı bir konuya gönderir.
	• Abone olan uygulamalar mesajları alır.

Performans ve Verimlilik
1. Mesaj Boyutu
	• Optimum mesaj boyutu: 4 KB ile 100 KB arasıdır.
	• Çok büyük mesajlar yerine segmentasyon kullanılarak birden fazla mesaj gönderilebilir.
2. Kalıcılık (Persistence)
	• Kalıcı mesajlar disk üzerinde saklanır ve kuyruk yöneticisi yeniden başlatıldığında kurtarılır.
	• Geçici mesajlar daha hızlıdır, ancak kuyruk yöneticisi kapandığında kaybolur.
3. Mesaj Önceliği
	• Mesajlara öncelik atanarak kuyruk sıralaması yapılabilir.
4. Senkronizasyon (Syncpoint)
	• Kalıcı mesajlar: Syncpoint kullanarak işlenmelidir.
	• Geçici mesajlar: Performans için syncpoint olmadan işlenebilir.

Gelişmiş Teknikler
1. Mesaj Bağımlılıklarının Kaldırılması
	• Clustering kullanırken mesaj bağımlılıkları mümkün olduğunca azaltılmalıdır.
	• Bu, uygulamanın ölçeklenebilirliğini ve kullanılabilirliğini artırır.
2. Mesaj Bağlantıları (Affinity)
	• Mesajların belirli bir kuyruğa veya yöneticisine bağlı kalması gerekiyorsa, iş mantığı buna göre tasarlanmalıdır.
3. Mesaj Kapsamı ve Seçiciler
	• Mesaj meta verileri kullanılarak seçim yapılabilir.
	• Karmaşık seçiciler performansı etkileyebilir; bu nedenle, uygulamalar arasında basit mesaj yönlendirme tercih edilmelidir.

Uygulama Performansını Artırmak İçin İpuçları
	1. Tekrar Kullanılabilir Bağlantılar: Bağlantıları ve kuyrukları tekrar açmak yerine açık tutun.
	2. Mesajları Gruplama: Birden fazla mesajı bir işlem birimi (unit of work) içinde işleyin.
	3. MQPUT1 Kullanımı: Tek mesaj için MQPUT1, çoklu mesaj için MQPUT tercih edilmelidir.
	4. Ölçeklenebilirlik için Cluster Kullanımı: Uniform clusters ile yük dengeleme yapılabilir.

Test ve Sorun Giderme
	• MQ trace araçları, hataları izlemek ve çözümlemek için kullanılabilir.
	• Hata Durumları: Teslim edilemeyen mesajlar için raporlar oluşturun ve uygun hata işleme mekanizmalarını tasarlayın.

JMS/Jakarta Messaging ve Java Uygulamalarının Geliştirilmesi
IBM MQ, Java tabanlı uygulamalar için üç farklı arayüz sağlar:
	1. IBM MQ classes for Jakarta Messaging
	2. IBM MQ classes for JMS
	3. IBM MQ classes for Java

IBM MQ classes for Jakarta Messaging
	• Jakarta Messaging 3.0 API ile yazılmış uygulamalar için IBM MQ’yu bir mesajlaşma sağlayıcısı olarak kullanmanızı sağlar.
	• Jakarta Messaging, Java Community Process tarafından geliştirilmiş olup, JMS 2.0’a fonksiyonel olarak eşdeğerdir, ancak isimlendirme farklılıkları içerir:
		○ Örneğin, javax.jms.Connection yerine jakarta.jms.Connection.
	• Avantajlar:
		○ Mevcut Jakarta Messaging becerilerini kullanabilme.
		○ Uygulamaların Jakarta Messaging sağlayıcısından ve IBM MQ yapılandırmasından bağımsız olması.
		○ Merkezi bir havuzda saklanan bağlantı fabrikaları ve hedefler (administered objects) ile uygulama bağımsızlığı.
		○ Jakarta EE ile doğal entegrasyon.
Kullanım Senaryoları:
	• Yeni uygulamalar geliştirme.
	• Jakarta EE uyumlu bir ortamda çalışmak.
	• Bağımsız ve taşınabilir uygulamalar geliştirme.

IBM MQ classes for JMS
	• JMS 2.0 API kullanılarak yazılmış uygulamalar için IBM MQ’yu mesajlaşma sağlayıcısı olarak kullanmanızı sağlar.
	• JMS 2.0, Jakarta Messaging tarafından desteklenir ancak yeni özellikler Jakarta Messaging'de tanıtılacaktır.
	• Avantajlar:
		○ Mevcut JMS becerilerini kullanabilme.
		○ Uygulamaların JMS sağlayıcısından ve IBM MQ yapılandırmasından bağımsız olması.
		○ Merkezi bir havuzda saklanan bağlantı fabrikaları ve hedefler ile uygulama bağımsızlığı.
		○ Java EE ile doğal entegrasyon.
Kullanım Senaryoları:
	• Mevcut JMS 2.0 uygulamalarını sürdürme.
	• JMS ile uyumlu bir uygulama sunucusunda çalışma.

IBM MQ classes for Java
	• IBM MQ kaynaklarına erişmek için IBM MQ’ya özgü bir API sağlar.
	• Bu sınıflar, IBM MQ’nun Message Queue Interface (MQI) arayüzünü kapsar.
	• Not:
		○ Bu API, IBM MQ 8.0 ile işlevsel olarak stabilize edilmiştir.
		○ Yeni uygulamalar için önerilmez; mevcut uygulamalar desteklenir.

Jakarta Messaging ve JMS Karşılaştırması
Özellik	Jakarta Messaging	JMS
API	Jakarta Messaging 3.0	JMS 2.0
Uyumluluk	Jakarta EE	Java EE
Yeni Uygulamalar	Tavsiye Edilir	Mevcut Uygulamalar için Kullanılır
Bağlantı Fabrikaları	JNDI veya dinamik oluşturma	JNDI veya dinamik oluşturma

IBM MQ Resource Adapter
IBM MQ Resource Adapter, Jakarta EE veya Java EE ortamında çalışan uygulamaların IBM MQ kaynaklarına erişimini sağlar. Kaynak adaptörü, aşağıdaki özellikleri destekler:
	• Gelen ve giden iletişim.
	• Mesaj yönlendirme ve işlem yönetimi.

IBM MQ Header Paketi
IBM MQ Header paketi, mesaj başlıklarını (MQMD gibi) yönetmek için yardımcı sınıflar sağlar. Tipik olarak, aşağıdaki senaryolarda kullanılır:
	• MQ komut sunucusuna yönetim mesajları göndermek.
	• Mesaj başlıklarının özelleştirilmesi.

Geliştirme ve Dağıtım Ortamları
	• IBM MQ sınıfları, standalone veya Maven gibi yazılım yönetim araçlarıyla dağıtım için hazır JAR dosyaları sağlar.
	• JNDI kullanılarak bağlantı fabrikaları ve hedefler merkezi bir havuzda saklanabilir.
	• Jakarta Messaging: JMS30Admin aracı ile JNDI nesnelerini yönetir.
	• JMS: IBM MQ Explorer veya JMSAdmin aracı ile JNDI nesnelerini yönetir.

Geliştirme için Öneriler
	1. Yeni Uygulamalar için: Jakarta Messaging 3.0 kullanılması önerilir.
	2. Mevcut JMS Uygulamaları için: IBM MQ classes for JMS kullanmaya devam edilebilir.
	3. Java SE SDK: Geliştirme için gerekli.
	4. FIPS 140-2 Uyumluluğu: IBM MQ sınıfları JSSE sağlayıcıları ile kriptografik güvenlik sunar.

IBM MQ classes for JMS/Jakarta Messaging: Kurulum ve Yapılandırma
IBM MQ sınıfları (JMS ve Jakarta Messaging) uygulamalarını çalıştırmadan önce uygun kurulum ve yapılandırma işlemlerini gerçekleştirmeniz gerekmektedir. Aşağıda, kurulum sonrası yapılandırma adımları detaylı olarak açıklanmıştır.

1. Kurulumla Oluşturulan Dizinler ve Dosyalar
Kurulum sırasında aşağıdaki dosyalar ve dizinler oluşturulur:
	• JAR Dosyaları:
		○ com.ibm.mq.allclient.jar (JMS 2.0 için)
		○ com.ibm.mq.jakarta.client.jar (Jakarta Messaging 3.0 için)
		○ Diğer bağımlı JAR dosyaları: fscontext.jar, providerutil.jar vb.
	• Doğal Kütüphaneler (Native Libraries):
		○ Windows: MQ_INSTALLATION_PATH\java\lib (32-bit) ve MQ_INSTALLATION_PATH\java\lib64 (64-bit)
		○ Linux/AIX: Benzer şekilde lib ve lib64 dizinlerinde yer alır.
	• Örnek Uygulamalar:
		○ Örnekler, MQ_INSTALLATION_PATH/samp/jms (Linux/AIX) veya MQ_INSTALLATION_PATH\tools\jms (Windows) dizinlerinde bulunur.

2. Ortam Değişkenlerinin Ayarlanması
CLASSPATH Değişkeni
Uygulamaları çalıştırmak için CLASSPATH aşağıdaki gibi ayarlanmalıdır:
	• JMS 2.0:

CLASSPATH=MQ_INSTALLATION_PATH/java/lib/com.ibm.mq.allclient.jar:MQ_INSTALLATION_PATH/samp/jms/samples:
	• Jakarta Messaging 3.0:

CLASSPATH=MQ_INSTALLATION_PATH/java/lib/com.ibm.mq.jakarta.client.jar:
Ek Ortam Değişkenleri
	• Windows: setmqenv komutu ile ortam değişkenlerini otomatik olarak ayarlayın:

setmqenv
	• Linux/AIX: Uygun betikleri kullanın:
		○ JMS 2.0 için: setjmsenv veya setjmsenv64
		○ Jakarta Messaging için: setjms30env veya setjms30env64

3. Java Native Interface (JNI) Kütüphanelerinin Yapılandırılması
JNI kütüphaneleri, bağlama (bindings) modu kullanılarak bağlanırken gereklidir.
Kütüphane Yollarını Ayarlama
	• Linux:

export LD_LIBRARY_PATH=/opt/mqm/java/lib64:$LD_LIBRARY_PATH
	• Windows:

set PATH=C:\Program Files\IBM\MQ\java\lib64;%PATH%
JNI Hataları ve Çözümü
Eğer ortam doğru yapılandırılmamışsa şu hata ile karşılaşabilirsiniz:

Caused by: java.lang.UnsatisfiedLinkError: mqjbnd (Not found in java.library.path)
Yukarıdaki ortam değişkenlerini doğrulayarak sorunu çözebilirsiniz.

4. JMS/Jakarta Messaging Yapılandırma Dosyası
Bir jms.config yapılandırma dosyası, uygulamaların belirli özelliklerini yapılandırmak için kullanılabilir. Örnek:

java -Dcom.ibm.msg.client.config.location=file:/D:/mydir/myjms.config MyAppClass
Yapılandırma dosyasında aşağıdaki özellikler ayarlanabilir:
	• İzleme ve günlükleme (Tracing and Logging)
	• Müşteri modu özellikleri (Client-mode specifics)
	• Genel JMS istemci davranışı

5. Queue Manager Yapılandırması
Bağlantı Modları
	1. Client Mode: TCP/IP üzerinden uzak bağlantılar.
	2. Bindings Mode: Aynı sistemde yerel bağlantılar.
Queue Manager’ı Client Moduna Yapılandırma
	1. Server Connection Kanalı Oluşturma:

DEFINE CHANNEL(JAVA.CHANNEL) CHLTYPE(SVRCONN) TRPTYPE(TCP)
	2. Dinleyici (Listener) Başlatma:

DEFINE LISTENER(LISTENER.TCP) TRPTYPE(TCP) PORT(1414)
START LISTENER(LISTENER.TCP)

6. JMS Yetkilendirme (Authorization)
Yetkilendirme komutları:

setmqaut -m QM1 -t qmgr -g jmsappsgroup +connect +inq
	• Üretici Yetkileri: put
	• Tüketici Yetkileri: get, inq, browse
	• Geçici Kuyruklar: SYSTEM.TEMP.MODEL.QUEUE'ya erişim.

1. Point-to-Point ve Publish/Subscribe IVT (Kurulum Doğrulama Testi)
IVT, bir kuyruğa veya konuya mesaj göndermeyi ve ardından bu mesajı geri almayı doğrulamak için kullanılır.
	• Bindings Modu: Queue Manager doğrudan bağlanır.
	• Client Modu: Queue Manager ile TCP/IP üzerinden iletişim kurar.
Komutlar:
	• Bindings Modu:

IVTRun -nojndi [-m qmgr] [-v providerVersion] [-t]
	• Client Modu:

IVTRun -nojndi -client -m qmgr -host hostname [-port port] [-channel channel]
Sonuç: Başarılı bir test, kuyruğa mesaj gönderildiğini ve alındığını doğrulayan bir çıktı üretir.

2. Allowlisting (İzin Listesi) ile ObjectMessage Güvenliği
IBM MQ, ObjectMessage türlerini belirli bir liste ile sınırlandırarak güvenliği artırır.
Modlar:
	• Discovery Modu: Uygulama tarafından kullanılan sınıfları tespit eder ve bir dosyaya kaydeder.
	• Enforcement Modu: Sadece izin listesinde belirtilen sınıfları işleme alır.
Sistem Özellikleri:
	• Discovery:

-Dcom.ibm.mq.jms.allowlist.discover=true
-Dcom.ibm.mq.jms.allowlist=file:/path/to/allowlist.txt
	• Enforcement:

-Dcom.ibm.mq.jms.allowlist=file:/path/to/allowlist.txt
İzin Listesi Dosyası Formatı:
	• Her satırda tam sınıf adı olmalıdır.
	• Yıldız (*) kullanımı paket seviyesinde joker karakter olarak kullanılabilir (ör. com.ibm.mq.*).

3. Karakter Seti Dönüşümü ve Hata Yönetimi
IBM MQ, kodlama/çözme sırasında karakterlerin dönüştürülemediği durumları işlemek için özelleştirilebilir ayarlar sunar.
Sistem Özellikleri:
	• Hata Eylemi (UnmappableCharacterAction):

-Dcom.ibm.mq.cfg.jmqi.UnmappableCharacterAction=REPORT|REPLACE|IGNORE
	• Yedekleme Baytı (UnmappableCharacterReplacement):

-Dcom.ibm.mq.cfg.jmqi.UnmappableCharacterReplacement=decimal_value
Varsayılan: Hata raporlanır ve uygun bir istisna atılır.

4. JMS ile Temel Örnekler
IBM MQ, JMS kullanımı için örnek uygulamalar sağlar. Bu uygulamalar, kuyruğa mesaj gönderme, mesaj alma, JNDI kullanımı ve asenkron mesajlaşma gibi temel işlevleri içerir.
Örnek Çalıştırma:
	1. Çalıştırılacak örneğin bulunduğu dizine gidin.
	2. Komutu çalıştırın:

runjms SampleApplicationName -m QM1 -d QueueName

5. Sorun Giderme
	• 2059 Hata Kodu: Queue Manager çalışmıyor olabilir. Queue Manager ayarlarını kontrol edin.
	• Mesaj Okuma Hatası: Kuyruk eksik veya yazma/okuma izinleri kapalı olabilir.
	• LDAP Bağlantı Sorunları: LDAP sunucusu düzgün yapılandırılmamış olabilir.

1. JMS/Jakarta Messaging Modeli
JMS (Java Message Service) ve Jakarta Messaging, Java uygulamalarının mesajlaşma işlemleri gerçekleştirmesi için kullanılan bir API setidir. IBM MQ, JMS ve Jakarta Messaging desteği sunarak bu işlemleri gerçekleştirmenizi sağlar.
Temel Kavramlar:
	• Mesaj: Bir JMS mesajı; başlık (header), özellikler (properties) ve bir gövdeden (body) oluşur. Gövde genellikle uygulama verisini içerir.
	• Destination (Hedef): Mesajların gönderildiği veya alındığı yerdir. İki tür hedef vardır:
		○ Queue (Kuyruk): Noktadan noktaya mesajlaşma için.
		○ Topic (Konu): Yayınla/abone ol mesajlaşma için.
JMS/Jakarta Messaging Sürümleri:
	• JMS 2.0: IBM MQ 8.0 ile desteklenmeye başlandı. Daha basitleştirilmiş bir API sunar.
	• Jakarta Messaging 3.0: IBM MQ 9.3.0 itibarıyla desteklenir ve yeni uygulama geliştirmeleri için önerilir.

2. Bağlantı ve Hedeflerin Oluşturulması
IBM MQ ile JMS uygulaması geliştirmek için önce bağlantı fabrikaları ve hedefler (destinations) tanımlanır. Bu işlemler şu yöntemlerle yapılabilir:
	• JNDI (Java Naming and Directory Interface): Yönetim araçlarıyla önceden tanımlanmış nesneler alınabilir.
	• Dinamik Oluşturma: Kod içinde bağlantı fabrikaları ve hedefler dinamik olarak yaratılabilir.
Örnek: Dinamik Kuyruk Oluşturma

Queue queue = session.createQueue("queue:///MyQueue");
Bu örnek, IBM MQ'da MyQueue adında bir kuyruk temsil eden bir nesne oluşturur.

3. Mesaj Gönderimi
Bir mesaj göndermek için şu adımlar izlenir:
	1. MessageProducer (Mesaj Üreticisi) Oluşturma:

java
Copy code
MessageProducer producer = session.createProducer(destination);
	2. Mesaj Oluşturma: Örneğin, bir metin mesajı (text message):


TextMessage message = session.createTextMessage("Merhaba Dünya");
	3. Mesajı Gönderme:

producer.send(message);

4. Mesaj Alma
Mesajları almak için MessageConsumer kullanılır. İki yöntem vardır:
	• Senkron Alma: receive() metodu kullanılır ve mesajı almak için belirli bir süre beklenir.
	• Asenkron Alma: MessageListener ile mesajlar geldikçe işlenir.
Örnek: Asenkron Alma

consumer.setMessageListener(new MessageListener() {
    public void onMessage(Message message) {
        System.out.println("Mesaj alındı: " + message);
    }
});

5. Zehirli Mesajların (Poison Messages) Yönetimi
Bir uygulama, işleyemediği mesajlarla karşılaşabilir. Bu tür mesajlar "zehirli mesaj" olarak adlandırılır. IBM MQ, bu mesajları şu şekilde yönetir:
	• Backout Count (Tekrar Sayısı): Bir mesaj işlenemezse, bu sayı artırılır.
	• Backout Queue (Yedek Kuyruk): Belirli bir eşiğe ulaşıldığında mesajlar buraya taşınır.
Örnek: Backout Kuyruk Ayarları

ALTER QLOCAL(MY.QUEUE) BOTHRESH(3) BOQUEUE(MY.BACKOUT.QUEUE)
Bu komut, MY.QUEUE kuyruğundaki zehirli mesajlar 3 kez işlenemezse MY.BACKOUT.QUEUE kuyruğuna taşınmasını sağlar.

6. Önemli JMS Özellikleri
	• Paylaşılan Abonelikler (Shared Subscriptions): Birden fazla tüketici, aynı aboneliği paylaşabilir.
	• Mesaj Seçiciler (Message Selectors): Belirli kriterlere uyan mesajlar alınabilir.
	• XA Desteği: Dağıtılmış işlemler için JMS, XA protokolünü destekler.

7. Kapanış ve Kaynakların Yönetimi
JMS uygulamalarında kaynaklar zamanında serbest bırakılmalıdır:
	• Bağlantılar (Connection)
	• Oturumlar (Session)
	• Mesaj Üreticileri ve Tüketicileri (MessageProducer ve MessageConsumer)
Her birini kapatmak için close() metodu kullanılır:

connection.close();
session.close();
producer.close();

IBM MQ'nun JMS ve Jakarta Messaging Kullanımıyla Modüler Uygulamalar Konfigürasyonu
IBM MQ ile modüler uygulamalar geliştirmek için JMS veya Jakarta Messaging sınıflarını modüler yapılarla nasıl entegre edebileceğinizi anlatacağım. Bu rehberde hem modüler yapıların temel kavramlarını hem de IBM MQ sınıflarının kullanımına dair detayları bulacaksınız.

1. Modüler Uygulama ve IBM MQ Sınıfları
Modüler Paketleme:
IBM MQ sınıflarının JAR dosyaları artık modül isimleri ile sunulur. Bu modüller:
	• JMS için: com.ibm.mq.javax modülü.
	• Jakarta Messaging için: com.ibm.mq.jakarta modülü.
IBM MQ için kullanılan varsayılan MQ_HOME/java/lib dizini modüler uygulamalar için uygun değildir. Çünkü bu dizin birden fazla JAR dosyasını aynı paketlerle içerir ve modüler yapılarda aynı paket adı birden fazla yerde olamaz.
Yeni Modül Dizini:
IBM MQ, modüler uygulamalar için aşağıdaki dizinleri sağlar:
	• JMS: MQ_HOME/java/lib/modules/javax
	• Jakarta Messaging: MQ_HOME/java/lib/modules/jakarta

2. Modüler Uygulama İçin IBM MQ Konfigürasyonu
JMS Modülü Kullanımı:
	1. Modülü Tanımlayın: Uygulamanızda com.ibm.mq.javax modülünü talep edin:

requires com.ibm.mq.javax;
	2. Modül Yolunu Ayarlayın: Modül yoluna şu dizini ekleyin:

MQ_HOME/java/lib/modules/javax
Jakarta Messaging Modülü Kullanımı:
	1. Modülü Tanımlayın: Uygulamanızda com.ibm.mq.jakarta modülünü talep edin:

requires com.ibm.mq.jakarta;
	2. Modül Yolunu Ayarlayın: Modül yoluna şu dizini ekleyin:

MQ_HOME/java/lib/modules/jakarta
IBM MQ Sınıfları için Java Desteği:
IBM MQ'nun Java sınıfları hem JMS hem de Jakarta Messaging modüllerinden desteklenir. Ancak, uygulamanızda yalnızca bir modülü seçerek kullanmanız gerekir.

3. Gelişmiş Konfigürasyonlar
JMS Uygulamaları için Özel Ayarlar:
	• Bağlantı Fabrikaları ve Hedeflerin Oluşturulması: Bağlantı fabrikalarını ve hedefleri JNDI, IBM JMS Uzantıları veya URI (Uniform Resource Identifier) kullanarak tanımlayabilirsiniz.
JMS'de Oturum Yönetimi:
	• Oturumlar (Session) mesaj üretimi ve tüketimi için kullanılır.
	• Oturumun birden fazla thread tarafından aynı anda kullanılması önerilmez.
Jakarta Messaging ile Gelişmiş Kullanım:
Jakarta Messaging, JMS ile aynı yapıyı sunar, ancak javax yerine jakarta ad alanını kullanır. Bu, Jakarta EE'nin Java EE'den ayrılmasından kaynaklanır.

4. IBM MQ ve Liberty Entegrasyonu
CICS Liberty JVM Server Kullanımı:
	• IBM MQ sınıfları, CICS Liberty JVM Server içinde kullanılabilir.
	• İki mod JVM bulunur:
		○ Standard: CLIENT modunda IBM MQ ile bağlantı sağlar.
		○ Integrated: Sadece CLIENT modunda bağlantı sağlar, BINDINGS modu desteklenmez.
IMS Entegrasyonu:
IMS ortamında IBM MQ'nun JMS sınıflarını kullanabilirsiniz. Ancak şu kısıtlamalara dikkat edin:
	• CLIENT modu desteklenmez.
	• Bağlantılar yalnızca IBM MQ 8.0 kuyruk yöneticilerine yapılabilir.

5. Özel Durumlar ve Sınırlamalar
Poison Mesaj Yönetimi:
IBM MQ, işlenemeyen "zehirli mesajları" tanır ve belirli bir eşikten sonra bu mesajları yedek kuyruğa taşır.
Hata Yönetimi:
	• Hatalar için ExceptionListener kullanarak hataları dinleyebilir ve yeniden bağlantılar sağlayabilirsiniz.
Modüler Kullanımda Dikkat Edilmesi Gerekenler:
	• Aynı anda hem JMS hem de Jakarta Messaging API'lerini kullanmayın.
	• Uygulamanızın sadece bir modül ile uyumlu olduğundan emin olun.

IBM MQ Sınıfları ile Java Kullanımı
IBM MQ, Java uygulamaları için hem istemci (client) modunda hem de doğrudan bir kuyruk yöneticisine bağlanarak kullanılabilir. Aşağıda IBM MQ sınıflarının Java ortamında nasıl kullanılacağına dair temel bilgiler verilmiştir.

1. Stabilizasyon Durumu
IBM MQ sınıfları için Java, IBM MQ 8.0 sürümü ile stabilize edilmiştir. Bu sınıflar için yeni özellikler eklenmeyecektir. Mevcut uygulamalar tam destek alırken, yeni projeler için IBM MQ JMS sınıfları veya Jakarta Messaging sınıfları önerilmektedir.
	• Desteklenen Ortamlar:
		○ Java uygulamaları için tam destek sağlanır.
		○ IMS ve WebSphere Liberty ortamlarında desteklenmez.

2. IBM MQ Java Sınıflarının Kullanım Modları
a. Client (İstemci) Modu
	• Bağlantı: TCP/IP üzerinden herhangi bir desteklenen kuyruk yöneticisine bağlanabilir.
	• Konum: Uygulama, kuyruk yöneticisi ile aynı sistemde veya farklı bir sistemde çalışabilir.
	• Özellikler: Yüksek performans gerektiren dağıtık sistemlerde yaygın olarak kullanılır.
b. Bindings Modu
	• Bağlantı: Java Native Interface (JNI) kullanılarak kuyruk yöneticisine doğrudan bağlantı sağlar.
	• Konum: Uygulama, kuyruk yöneticisi ile aynı sistemde çalışmalıdır.
	• Özellikler: Ağ iletişimi maliyetlerini ortadan kaldırarak daha yüksek performans sağlar.

3. Gereksinimler
	• JRE/JDK: Java 8 veya üstü bir sürüm gereklidir.
	• IBM MQ Kuyruk Yöneticisi: Uygulamaların bağlanacağı bir kuyruk yöneticisinin yapılandırılmış olması gerekir.
	• Kütüphane Dosyaları: Uygulamanın CLASSPATH değişkeninde IBM MQ Java sınıflarına ait JAR dosyalarının yolu belirtilmelidir.

4. Kurulum ve Konfigürasyon
a. Kurulum Dizini
Platforma göre JAR dosyalarının ve kütüphanelerin kurulum yolları:
	• Windows: MQ_INSTALLATION_PATH\java\lib
	• Linux: /opt/mqm/java/lib
	• z/OS: MQ_INSTALLATION_PATH/mqm/V8R0M0/java/lib
b. Ortam Değişkenleri
Uygulamaların çalıştırılabilmesi için aşağıdaki değişkenlerin ayarlanması gereklidir:
	• MQ_JAVA_LIB_PATH: Java kütüphanelerinin yolu.
	• CLASSPATH: Gerekli JAR dosyalarının yolu.
c. Kuyruk Yöneticisinin Yapılandırılması
	1. Bir sunucu bağlantı kanalı tanımlayın.
	2. İstemci bağlantı isteklerini kabul etmek için bir dinleyici başlatın.

5. Örnek Uygulamalar
Kurulum Doğrulama Programı (MQIVP)
Kurulumun doğruluğunu test etmek için kullanılabilir.

java -Djava.library.path=library_path MQIVP
Bu program:
	1. Kuyruk yöneticisine bağlanır.
	2. SYSTEM.DEFAULT.LOCAL.QUEUE kuyruğuna mesaj ekler ve alır.
	3. Bağlantıyı kapatarak test sonuçlarını bildirir.
Basit Mesaj Gönderme ve Alma (MQSample.java)
Bir kuyruğa mesaj göndermeyi ve kuyruğu okumayı gösterir.

6. Kısıtlamalar
	• Bağlantı Havuzu: Aynı JVM içinde tüm uygulamalar tarafından paylaşılan bir bağlantı havuzu kullanır. Bu, uygulama izolasyonu için uygun olmayabilir.
	• Güvenlik: TLS yapılandırması, uygulama sunucusunun güvenlik ayarlarından bağımsızdır.
	• Bindings Modu Kısıtlamaları: Kuyruk yöneticisi ve kaynak adaptörü sürümleri farklı ise bindings modunda bağlantı sağlanamaz.

7. Öneriler
	• Yeni Uygulamalar: IBM MQ sınıfları yerine JMS veya Jakarta Messaging sınıflarını tercih edin.
	• Yüksek Performans: Bindings modu performans avantajı sağlar ancak kuyruk yöneticisi ile aynı sistemde çalışması gereklidir.
	• Hata Ayıklama: Sorun durumlarında MQIVP programı ve izleme (trace) özelliği kullanılabilir.
