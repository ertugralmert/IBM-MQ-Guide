Point-to-Point Senaryosu
Amaç: Bu senaryoda, iki IBM MQ kuyruk yöneticisini (queue manager) birbirine bağlayarak, point-to-point (bir yönlü) mesajlaşmayı etkinleştiriyoruz. Bu senaryo, farklı makinelere kurulu iki kuyruk yöneticisi arasında mesaj iletimi sağlar. Ayrıca, iletilen mesajların güvenli bir şekilde iletilmesi için Transport Layer Security (TLS) kullanarak iletişim güvenliğini sağlayacağız.
Senaryo Özeti
Bu senaryoda, iki kuyruk yöneticisi (QM1 ve QM2) oluşturacağız. QM1, mesajları QM2'ye gönderecek. İletişim, bir ağ üzerinden gerçekleşecek, yani her iki kuyruk yöneticisi farklı fiziksel makinelerde bulunacak.
Planlama
	• Point-to-Point Mesajlaşma: En basit mesajlaşma türüdür. Bu türde, mesaj gönderen uygulama, mesajı alacak olan uygulamanın bilgilerine sahip olmalıdır. Gönderen uygulama, alıcı kuyruğuna adres bilgileri sağlamalıdır.
	• Güvenlik Ekleme: Mesaj iletimini daha güvenli hale getirebilmek için, kanala TLS ekleyerek verilerin güvenli bir şekilde iletilmesini sağlarız.
Temel Kavramlar ve Anahtar Terimler
Aşağıdaki temel kavramlar, bu senaryoyu başarıyla tamamlayabilmeniz için gereklidir:
	• Queue Manager (Kuyruk Yöneticisi): Kuyrukları yöneten ve mesajları doğru kuyruğa depolayan IBM MQ bileşenidir.
	• Messages (Mesajlar): Uygulamalar arasındaki veri aktarımını sağlayan baytlardan oluşur. Mesajlar, farklı bilgisayarlarda çalışan uygulamalar arasında iletilir.
	• Local Queues (Yerel Kuyruklar): Mesajları depolayan veri yapılarıdır. Yerel kuyruklar, doğrudan uygulamalara mesaj göndermek için kullanılır.
	• Remote Queues (Uzak Kuyruklar): Mesajların başka bir kuyruk yöneticisine iletilmesi için adreslenen kuyruklardır.
	• Channels (Kanallar): Mesajların kuyruk yöneticileri arasında iletilmesini sağlar.
	• Listeners (Dinleyiciler): Diğer kuyruk yöneticilerinden veya istemci uygulamalarından gelen ağ isteklerini kabul eder ve ilişkili kanalları başlatır.
Çözümü Gerçekleştirme
	1. Kuyruk Yöneticilerini Oluşturma:
		○ Her iki makineye birer kuyruk yöneticisi (QM1 ve QM2) kurun. QM1 mesajları gönderecek, QM2 ise alacaktır.
	2. Queue Yöneticisi Oluşturma:
		○ crtmqm QM1 komutunu kullanarak bir kuyruk yöneticisi oluşturun.
	3. Kuyruklar Oluşturma:
		○ define qlocal(LQ1) komutunu kullanarak bir yerel kuyruk (LQ1) oluşturun.
	4. Sender Channel (Gönderen Kanalı) Oluşturma:
		○ QM1 üzerinde bir kanal oluşturun. Bu kanal, QM1’i QM2’ye bağlayacak ve mesajları iletecektir.
	5. Dağıtık Kuyruk Yöneticisi Topolojisini Oluşturma:
		○ Point-to-Point mesajlaşma için, QM1’in QM2’ye bir mesaj gönderebilmesi için uzak kuyruklar ve kanallar gereklidir.
	6. Güvenlik Ekleyerek Yapılandırma:
		○ Transport Layer Security (TLS) ekleyerek kanal güvenliğini sağlayın. Bu, verilerin şifrelenmesini ve güvenli bir şekilde iletilmesini sağlar.
Çözümü Doğrulama
	• Mesaj Gönderme: QM1, mesajları QM2’ye gönderebilir. Gönderen kuyruk yöneticisinin, hedef kuyruk yöneticisinin adres bilgilerini bilmesi gerektiğini unutmayın.
	• Mesaj Alma: QM2, LQ1 kuyruklarına gelen mesajları alıp işleyebilir.


*******************

Bu senaryoda iki farklı IBM MQ kuyruk yöneticisi arasında mesaj iletimi sağlanır. Şimdi her adımı açıklayalım:
1. Kuyruk Yöneticisi Oluşturma
İlk olarak, mesajları gönderecek bir kuyruk yöneticisi oluşturmalıyız. Bunu yaparken aşağıdaki adımları izleriz:
1.1. Kuyruk Yöneticisi Oluşturma:
	• Komut: crtmqm QM1
		○ Bu komut, QM1 adında bir kuyruk yöneticisi oluşturur. Kuyruk yöneticisi, tüm kuyruğa yönelik işlemleri yöneten bir bileşendir.
		○ Beklenen Çıktı: Kuyruk yöneticisinin başarıyla oluşturulduğunu gösteren mesajlar ve varsayılan nesnelerin (61 nesne) başarıyla oluşturulduğu bilgisi görüntülenir.
1.2. Kuyruk Yöneticisini Başlatma:
	• Komut: strmqm QM1
		○ Bu komut, yeni oluşturduğumuz QM1 kuyruk yöneticisini başlatır.
		○ Beklenen Çıktı: Kuyruk yöneticisinin başlatıldığına dair bir mesaj görürsünüz ve kuyruk yöneticisinin başlatılma süreci tamamlanır.
2. Kuyrukları Oluşturma
Şimdi mesajların iletileceği kuyrukları oluşturmamız gerekiyor. Bu aşamada yerel ve uzaktan kuyruklar ile bağlantılar oluşturacağız.
2.1. MQSC Arayüzünü Başlatma:
	• Komut: runmqsc QM1
		○ Bu komut, QM1 kuyruk yöneticisini yönetmek için kullanılan MQSC (Message Queue Script Commands) arayüzünü başlatır.
2.2. Bir Transmission Kuyruğu Oluşturma:
	• Komut: DEFINE QLOCAL(QM2) DESCR('Transmission queue to QM2') USAGE(XMITQ)
		○ Bu komut, mesajların başka bir kuyruk yöneticisine iletilebilmesi için gerekli olan bir transmission (iletim) kuyruk oluşturur. QM2 kuyruk yöneticisine mesajları iletecek olan bu kuyruk, mesajları kuyruk yöneticisi aracılığıyla yönlendirecektir.
2.3. Uzaktan Kuyruk Tanımı Oluşturma:
	• Komut: DEFINE QREMOTE(QUEUE.ON.QM2) DESCR('Remote queue for QM2') XMITQ(QM2) RNAME(RECEIVEQUEUE) RQMNAME(QM2)
		○ Bu komut, QM2 kuyruk yöneticisinde yer alan bir uzaktan kuyruk tanımı oluşturur. Böylece mesajlar QM1 kuyruk yöneticisinden QM2 kuyruk yöneticisine yönlendirilebilir.
3. Gönderen Kanalı Oluşturma
Gönderen kuyruk yöneticisi, mesajları alacak olan hedef kuyruk yöneticisine iletmek için bir kanal oluşturmalıdır.
3.1. Gönderen Kanalı Oluşturma:
	• Komut: DEFINE CHANNEL(TO.QM2) CHLTYPE(SDR) CONNAME('remoteHost') TRPTYPE(TCP) XMITQ(QM2)
		○ Bu komut, QM1 kuyruk yöneticisinde QM2 kuyruk yöneticisine mesaj göndermek için bir gönderen kanal (sender channel) oluşturur. Bu kanal, TCP bağlantısı ile iletilen mesajları QM2'ye yönlendirecektir. remoteHost burada hedef kuyruk yöneticisinin IP adresi veya makine adıdır.
4. Dağıtılmış Kuyruk Yöneticisi Yapısını Oluşturma
Bu yapı, iki kuyruk yöneticisi arasında mesajların iletilmesini sağlayacak olan dağıtılmış bir yapıdır. İki kuyruk yöneticisinin doğru bir şekilde iletişim kurabilmesi için gerekli bağlantılar yapılır.
4.1. Hedef Kuyruk Yöneticisi Oluşturma:
	• Komut: crtmqm QM2
		○ QM2 kuyruk yöneticisi, QM1'e bağlanabilmesi için oluşturulmalıdır. Bu kuyruk yöneticisi, QM1 tarafından gönderilen mesajları alacak ve işleyecektir.
4.2. Kuyruğun Oluşturulması:
	• Komut: DEFINE QLOCAL(RECEIVEQUEUE) DESCR('Receiving queue')
		○ QM2 kuyruk yöneticisinde, gelen mesajları alacak olan yerel bir kuyruk (RECEIVEQUEUE) oluşturulur. Bu kuyruk, QM1'den gelen mesajları alacak şekilde yapılandırılacaktır.
4.3. Alıcı Kanalı Oluşturma:
	• Komut: DEFINE CHANNEL(T0.QM2) CHLTYPE(RCVR) TRPTYPE(TCP)
		○ QM2'de bir alıcı kanalı (receiver channel) oluşturulur. Bu kanal, QM1'den gelen mesajları alacak ve iletilen verilerin doğru bir şekilde iletilmesini sağlar.
5. Kanal Başlatma
	• Komut: START CHANNEL(TO.QM2)
		○ QM1 kuyruk yöneticisindeki gönderici kanal başlatıldığında, QM2 kuyruk yöneticisindeki alıcı kanal otomatik olarak başlatılır. Bu, mesajların iletilmesi için gerekli iletişimi sağlar.
6. Çözümün Doğrulanması
Son olarak, kurduğumuz yapı ile testler yaparak her şeyin düzgün çalıştığından emin oluruz.
6.1. Mesaj Gönderme:
	• Komut: amqsput QUEUE.ON.QM2 QM1
		○ QM1 kuyruk yöneticisinden, QM2 kuyruk yöneticisine bir mesaj gönderilir. Bu işlem sırasında, mesajın doğru kuyruktan iletildiği doğrulanır.
6.2. Mesaj Alma:
	• Komut: amqsget RECEIVEQUEUE QM2
		○ QM2 kuyruk yöneticisinde, gönderilen mesaj alınır. Bu işlem, iki kuyruk yöneticisi arasındaki iletişimin doğru çalıştığını doğrular.



***********

. Queue Manager Oluşturulması
	• Queue Manager Nedir? Queue Manager, IBM MQ'nin merkezinde yer alan bir bileşendir. Kuyrukları yönetir ve mesajları doğru kuyruğa yönlendirir. Bir sistemdeki tüm mesajların saklandığı, alınacağı ve gönderileceği ana bileşendir. Bu nedenle, her iletişim kanalının bir Queue Manager’a bağlanması gereklidir.
	• crtmqm QM1 Komutu: Bu komut, yeni bir Queue Manager (QM1) oluşturur. QM1 burada örnek bir isimdir, fakat siz bunu dilediğiniz gibi değiştirebilirsiniz.Ekranda Görülen Mesajlar:IBM MQ queue manager created.Creating or replacing default objects for QM1.Default objects statistics: 61 created. 0 replaced. 0 failed.Completing setup.Setup completed.Bu mesajlar, Queue Manager'ın başarıyla oluşturulduğunu ve varsayılan objelerin eklendiğini gösterir.
	• strmqm QM1 Komutu: Queue Manager'ı başlatmak için bu komut kullanılır. Başlatıldıktan sonra, mesajlaşma altyapısının aktif hale gelmesi sağlanır.Ekranda Görülen Mesajlar:IBM MQ queue manager 'QM1' starting.5 log records accessed on queue manager 'QM1' during the log replay phase.IBM MQ queue manager 'QM1' started.Bu mesajlar, Queue Manager'ın başlatıldığını ve loglarının başarılı bir şekilde yüklendiğini gösterir.
2. Queue Oluşturulması
Queue'lar, mesajları saklamak için kullanılan veri yapılarıdır. Bu adımda, iki tür kuyruk oluşturulmaktadır:
	• Local Queue (Yerel Kuyruk): QM1'de mesajların yerel olarak saklandığı kuyrukları tanımlar.
	• Remote Queue (Uzak Kuyruk): Mesajların başka bir Queue Manager'a yönlendirilmesini sağlayan kuyruktur.
	• runmqsc QM1 Komutu: Bu komut, MQSC (MQ Script Command) arayüzünü başlatır ve kuyrukları yönetmek için kullanılır.
	• Yerel Kuyruk Tanımlama: İlk olarak, yerel bir kuyruk (QM2) oluşturuluyor. Bu kuyruk, mesajları saklamak için kullanılır.Komut:DEFINE QLOCAL(QM2) DESCR('Transmission queue to QM2') USAGE(XMITQ)Bu komut ile, QM1'deki mesajları başka bir Queue Manager’a gönderebilmek için bir yerel kuyruk oluşturulur.
	• Uzak Kuyruk Tanımlama: QM1'de, başka bir Queue Manager’a mesaj gönderilmesi için bir uzak kuyruk tanımlanır.Komut:DEFINE QREMOTE(QUEUE.ON.QM2) DESCR('Remote queue for QM2') XMITQ(QM2) RNAME(RECEIVEQUEUE) RQMNAME(QM2)Bu komut, QM1'den QM2'ye mesaj göndermek için gerekli uzak kuyruk yapısını oluşturur.
3. Sender Channel Oluşturulması
	• Sender Channel Nedir? Sender Channel, bir Queue Manager'dan başka bir Queue Manager'a mesaj göndermek için kullanılan iletişim kanalını tanımlar.
	• DEFINE CHANNEL Komutu ile Sender Channel Tanımlama: TO.QM2 adlı sender channel, QM1'den QM2'ye mesaj gönderebilmek için tanımlanır.Komut:DEFINE CHANNEL(TO.QM2) CHLTYPE(SDR) CONNAME('remoteHost') TRPTYPE(TCP) XMITQ(QM2)Burada:
		○ CHLTYPE(SDR) kanal türünü belirtir (sender).
		○ CONNAME('remoteHost') parametresi, hedef Queue Manager’ın adresini belirtir (IP ya da hostname).
		○ TRPTYPE(TCP) bağlantı tipinin TCP olduğunu belirtir.
		○ XMITQ(QM2) ise mesajların QM2'ye gönderileceğini ifade eder.
4. Distributed Queue Manager Topolojisi Oluşturulması
Bu adımda, iki Queue Manager arasındaki iletişim yapılandırılır. İlk Queue Manager (QM1) diğerine (QM2) mesaj gönderir.
	• Topoloji Nasıl Çalışır?
		○ QM1'deki bir uygulama, QM2'deki bir kuyruktan mesaj alabilmek için sender channel üzerinden bağlantı kurar.
		○ Bu iletişim kanalının her iki tarafında da uygun kuyruğun ve channel’ın oluşturulmuş olması gerekir.
5. Receiver Channel Oluşturulması
Receiver Channel, mesajları alır ve hedef Queue Manager'da ilgili kuyruktan alır.
	• Komut:DEFINE CHANNEL(TO.QM2) CHLTYPE(RCVR) TRPTYPE(TCP)
		○ CHLTYPE(RCVR) ile alıcı kanal (receiver) tanımlanır.
		○ Bu kanal, mesajların hedef queue manager'a iletilmesini sağlar.
6. Sender Channel'ın Başlatılması
Sender Channel'ı başlatarak mesajların gönderilmesini sağlar.
	• START CHANNEL Komutu:START CHANNEL(TO.QM2)Bu komut, QM1'deki sender channel'ı başlatır ve otomatik olarak hedef Queue Manager’a bağlanır.
7. Çözümün Doğrulanması
Son adımda, çözümün doğru çalışıp çalışmadığını doğrulamak için aşağıdaki işlemler yapılır:
	• Mesaj Gönderme:
		○ amqsput komutuyla, QM1'den QM2'ye mesaj gönderilir.
		○ Bu işlem başarılı olduğunda, QM2'deki kuyruktan alınan mesaj doğrulanır.
	• amqsget Komutu ile Mesaj Alımı:
		○ QM2'deki kuyruğa gelen mesajlar alınır.
		○ Mesaj başarılı bir şekilde alınmışsa, işlem tamamlanmış olur.
Sonuçlar: Bu işlemler, iki Queue Manager arasında doğru bir iletişim yapılandırması kurulduğunu ve mesajların başarıyla iletilip alındığını doğrular.

*********

Point-to-Point Topolojisini Güvence Altına Alma
Genel Bakış:
Bu süreç, point-to-point (uçtan uca) mesajlaşma topolojisinin güvenliğini sağlar ve mesajların üretim ortamlarında güvenli bir şekilde iletilmesini mümkün kılar. Burada, kaynak ve hedef queue manager'larının nesneleri güvence altına alınır ve ağ bağlantıları şifrelenerek güvenli iletişim sağlanır.
Yapılacaklar:
	1. Kaynak Queue Manager Nesnelerinin Güvenceye Alınması: Kaynak queue manager'ındaki nesnelere kullanıcı gruplarına erişim yetkisi verilir.
	2. Hedef Queue Manager Nesnelerinin Güvenceye Alınması: Hedef queue manager'ındaki nesnelere kullanıcı gruplarına erişim yetkisi verilir.
	3. Ağ Bağlantılarının Güvenceye Alınması: Kaynak ve hedef queue manager'ları arasındaki ağ bağlantıları TLS (Transport Layer Security) ile güvence altına alınır. Bu, verilerin şifrelenmesini sağlar.
Kaynak Queue Manager Nesnelerinin Güvenceye Alınması
Görev:
	• Kaynak queue manager’ındaki nesneler için yetkilendirme ayarları yapılır.
Adımlar:
	• setmqaut komutu ile uygulamayı çalıştıran kullanıcı grubuna gerekli yetkiler verilir.
Örnek Komutlar:
	1. Bağlantı Yetkisi Verme (Queue Manager):
setmqaut -m QM1 -t qmgr -g userGroup +connect

-> Bu komut, QM1 queue manager’ına, userGroup grubuna bağlantı yetkisi verir.

	2. Mesaj Gönderme Yetkisi Verme (Queue):

setmqaut -m QM1 -t q -n "QUEUE.ON.QM2" -g userGroup +put
-> Bu komut, QUEUE.ON.QM2 adlı queue’ya, userGroup grubuna mesaj gönderme yetkisi verir.


Hedef Queue Manager Nesnelerinin Güvenceye Alınması
Görev:
	• Hedef queue manager’ındaki nesneler için yetkilendirme ayarları yapılır.
Adımlar:
	• setmqaut komutu ile uygulamayı çalıştıran kullanıcı grubuna gerekli yetkiler verilir.
Örnek Komutlar:
Bağlantı Yetkisi Verme (Queue Manager):

setmqaut -m QM2 -t qmgr -g userGroup +connect
-> Bu komut, QM2 queue manager’ına, userGroup grubuna bağlantı yetkisi verir.

Mesaj Alma Yetkisi Verme (Queue):


setmqaut -m QM2 -t q -n "RECEIVEQUEUE" -g userGroup +get
-> Bu komut, RECEIVEQUEUE adlı queue’ya, userGroup grubuna mesaj alma yetkisi verir.


Ağ Bağlantılarının Güvenceye Alınması
Görev:
	• Kaynak ve hedef queue manager’ları arasındaki ağ bağlantısı TLS ile güvence altına alınır. Bu, iletişim esnasında şifreleme yaparak veri güvenliğini sağlar.
Queue Manager’ları TLS İçin Hazırlamak
Adımlar:
	1. Key Repository (Anahtar Deposu) Oluşturulması:
		○ runmqakm komutuyla IBM MQ queue manager’ının kişisel sertifikası ve Kamu Sertifika Otoritesinin (CA) sertifikası depolanacak bir anahtar deposu oluşturulur.
	2. CA Sertifikasının Anahtar Deposuna Eklenmesi:
		○ runmqakm -cert -add komutu ile CA sertifikası anahtar deposuna eklenir.
	3. Kişisel Sertifika Talep Edilmesi:
		○ Queue manager’ın kişisel sertifikası için bir talep dosyası (örneğin QM1req.req) oluşturulur.
	4. Sertifikanın Sertifika Otoritesinden Alınması ve Anahtar Deposuna Eklenmesi:
		○ CA, kişisel sertifikayı dijital olarak imzalayarak geri gönderir. Bu sertifika daha sonra anahtar deposuna alınır.

TLS Kullanarak Kanal Oluşturmak
Görev:
	• TLS kullanarak yeni bir kanal oluşturulması.
Adımlar:
	1. Sender Kanalı (Gönderen Kanalı) Oluşturmak:
		○ runmqsc komutuyla, QM1 kaynak queue manager’ı için TLS ile güvenli bir gönderici kanalı oluşturulur.DEFINE CHANNEL(TO.QM2) CHLTYPE(SDR) TRPTYPE(TCP) CONNAME('remoteHost') XMITQ(QM2) SSLCIPH(TLS_RSA_WITH_AES_128_CBC_SHA256) DESCR('Sender channel using TLS from QM1 to QM2') REPLACE
	2. Receiver Kanalı (Alıcı Kanalı) Oluşturmak:
		○ QM2 hedef queue manager’ı için benzer şekilde bir alıcı kanalı oluşturulur.DEFINE CHANNEL(TO.QM2) CHLTYPE(RCVR) TRPTYPE(TCP) SSLCIPH(TLS_RSA_WITH_AES_128_CBC_SHA256) SSLCAUTH(REQUIRED) DESCR('Receiver channel using TLS from QM1 to QM2') REPLACE


