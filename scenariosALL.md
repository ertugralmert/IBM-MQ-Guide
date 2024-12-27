IBM MQ Senaryoları
IBM MQ, çok çeşitli kullanım senaryoları için yapılandırılabilir ve çeşitli görevleri gerçekleştirmek için yönlendirilmiş adımlar sunar. Her senaryo, büyük bir ürün özelliğini yapılandırmak için gerekli olan önemli adımları gösterir ve konuyla ilgili daha iyi bir anlayış kazanmanıza yardımcı olacak diğer içeriklere bağlantılar sunar. Aşağıda, IBM MQ ile ilgili bazı yaygın senaryoları bulabilirsiniz.
1. IBM MQ ile Başlarken (Windows)
Bu senaryo, IBM MQ'yu Windows platformunda kurmayı ve kullanmayı öğrenmek isteyenler için temel bir başlangıç rehberidir. IBM MQ'yu daha önce kullanmamışsanız, bu senaryo hızlıca başlamak için kullanışlıdır.
2. Point-to-Point Senaryosu
Bu senaryo, iki IBM MQ kuyruk yöneticisini bir point-to-point (nokta-noktaya) topolojisinde birbirine bağlamayı ve dağılmış kuyruklama işlemlerini nasıl etkinleştireceğinizi gösterir.
3. Streaming Kuyrukları
IBM MQ'nun streaming queues (akış kuyrukları) özelliği, her mesajın neredeyse aynı bir kopyasını ikinci bir kuyruğa koymanızı sağlar. Bu senaryo, bu özelliği nasıl yapılandıracağınızı anlatır.
4. Publish/Subscribe Senaryoları
Bu iki set senaryo, publish/subscribe (yayınla/abone ol) kümeleri ve hiyerarşileri kullanarak mesaj iletimini nasıl yapılandırabileceğinizi ve kullanabileceğinizi gösterir.
5. Transactional Destek Senaryoları
Bu senaryo, transactional support (işlem destek) kullanarak uygulamalarınızın veritabanları ile güvenilir bir şekilde nasıl çalışacağını gösterir. Bu, veritabanı işlemleri için kritik bir özelliktir.
6. Güvenlik Senaryoları
Bu set, IBM MQ yapılandırmalarınıza güvenlik uygulamayı gösteren bir dizi senaryo içerir. IBM MQ'nun çeşitli güvenlik özelliklerini nasıl uygulayabileceğiniz hakkında bilgiler sunar.
7. Windows'da Yükseltme Senaryosu
Bu senaryo, mevcut bir IBM MQ 9.3 kurulumundan IBM MQ 9.4'e geçiş yapmak için gerekli olan temel görevleri adım adım gösterir. Bu senaryoda her iki sürüm de aynı Windows ortamında yüklü olacaktır.
8. IBM MQ'nun Yeni Bir Sürümünü Kurma (Windows)
Bu senaryo, IBM MQ'nun uzun vadeli destek (LTS) sürümünü, önceki sürümüyle birlikte ("yan yana") kurmanın tüm adımlarını gösterir. Ayrıca bu sürüme bir Fix Pack yüklemeyi de içerir.
9. Managed File Transfer Senaryosu
Bu senaryo, Managed File Transfer (Yönetilen Dosya Transferi) özelliğinin nasıl yapılandırılacağını ve test mesajı gönderme sürecini gösteren yaygın topolojiler sunar. Bu, dosya aktarım işlemlerini yönetmek için kullanılan bir özellik olup, çok sayıda IBM MQ bileşeni ile entegrasyon gerektirir.
10. IBM MQ Internet Pass-Thru (MQIPT) ile Başlarken
Bu senaryo, IBM MQ Internet Pass-Thru (MQIPT) ürününü kurmak ve yapılandırmak için bazı temel görevleri gösterir. Bu senaryolar, ürünün doğru şekilde kurulduğunu doğrulamak için de kullanılabilir.
11. Kafka Connect Senaryoları
IBM MQ ve Apache Kafka, mesajlaşma alanında farklı alanlara odaklanır. MQ, bağlantı konusunda uzmanlaşırken, Kafka veri konusunda uzmanlaşır. Çoğu çözüm, bu iki sistem arasında veri akışını sağlamak için Kafka Connect kullanır. Bu senaryo, Kafka ile IBM MQ arasında veri akışını nasıl yönetebileceğinizi gösterir.

IBM MQ ile Başlarken 
IBM® MQ'yu Windows platformunda kullanmaya başlamak için gereken temel adımları anlatan bu senaryo, IBM MQ'yu daha önce kullanmamış ve hızlıca başlamak isteyenler için idealdir. Senaryo, IBM MQ'nun kurulumunu, yapılandırılmasını ve doğrulamasını basit bir şekilde yapmanıza yardımcı olacak adımları içerir.
Planlama Çözümü
IBM MQ'nun Windows'a kurulumu için aşağıdaki yöntemlerden birini seçebilirsiniz:
	• Grafiksel Kullanıcı Arayüzü (GUI) kullanarak kurulumu gerçekleştirebilirsiniz. Bu yöntem, size kurulum ve yapılandırma sürecinde yardımcı olacak sihirbazlar sunar.
	• Komut Satırı kullanarak sessiz bir kurulum yapabilirsiniz.
Çözümün Uygulanması
IBM MQ'yu Windows platformunda kurmak için aşağıdaki adımları izlersiniz:
	1. Launchpad üzerinden IBM MQ kurulumu başlatılır.
	2. IBM MQ yükleme sihirbazı ile yazılım yüklenir.
	3. Prepare IBM MQ Wizard ile gerekli hazırlıklar yapılır.
	4. IBM MQ Servisi ve IBM MQ Explorer başlatılır.
	5. IBM MQ Explorer kullanarak kuyruğa mesaj gönderilir ve alınır.
Kurulumdan Sonra Ne Yapılmalı?
Kurulum tamamlandıktan sonra IBM MQ Explorer üzerinden oluşturduğunuz kuyruğa mesaj gönderme ve alma işlemleri yapılabilir. Bu işlem, IBM MQ’nun doğru şekilde kurulduğunu ve çalıştığını doğrulamak için önemlidir.

Temel Kavramlar ve Önemli Terimler
	• Queue Managers (Kuyruk Yöneticileri): Kuyruk yöneticisi, sahip olduğu kuyrukları yönetmekten ve aldığı tüm mesajları ilgili kuyruklara depolamaktan sorumludur.
	• Messages (Mesajlar): Mesaj, bir uygulama için anlam taşıyan bayt dizisidir. Mesajlar, bir uygulama programından başka bir uygulama programına bilgi transferi yapmak için kullanılır.
	• Local Queues (Yerel Kuyruklar): Yerel kuyruk, mesajları depolamak için kullanılan veri yapılarıdır. Normal kuyruklar, mesajları uygulamanın doğrudan okuyacağı şekilde saklar. İletim kuyrukları ise bir başka kuyruk yöneticisine yönlendirilecek mesajları tutar.
Kurulum Yöntemleri
	• Grafiksel Kullanıcı Arayüzü (GUI): Kurulum sırasında size adım adım yardımcı olacak sihirbazlar kullanılır.
	• Komut Satırı Arayüzü: Komut satırını kullanarak sessiz veya etkileşimli bir kurulum yapılabilir. Bu senaryoda, sessiz kurulum üzerinden ilerlenir.


1. IBM MQ Kurulumu (Grafiksel Kullanıcı Arayüzü ile)
Kurulum Adımları:
	1. IBM MQ'yu İndirin ve Kurulum Başlatın:
		○ IBM MQ'yu indirip kurulum başlatıcısını (Launchpad) çalıştırın.
		○ Kurulum sırasında, gerekli yazılım gereksinimlerini kontrol edin ve ağ bilgilerini girin.
		○ Kurulum sihirbazını izleyin ve IBM MQ yazılımını yükleyin.
	2. Queue Manager (Kuyruk Yöneticisi) Oluşturun:
		○ IBM MQ Explorer'ı açın ve yeni bir queue manager oluşturun. Burada "QM1" adında bir kuyruk yöneticisi yaratabilirsiniz.
		○ Queue manager, mesajlaşma işlemlerini yöneten ana bileşendir.
	3. Queue (Kuyruk) Oluşturun:
		○ LQ1 adında bir yerel kuyruk oluşturun. Bu kuyruk, mesajları depolayan bir veri yapısıdır.
	4. Mesaj Gönderme (Put Message):
		○ IBM MQ Explorer üzerinden LQ1 kuyruğuna bir mesaj gönderin. Örneğin, "Hello World" gibi basit bir mesaj gönderebilirsiniz.
	5. Mesaj Alma (Get Message):
		○ LQ1 kuyruğundaki mesajı almak için IBM MQ Explorer üzerinden mesajı alın. Bu, kuyruğa eklenen mesajın doğru bir şekilde işlendiğini doğrulamak içindir.


2. IBM MQ Kurulumu (Komut Satırı ile)
Kurulum Adımları:
	1. Silent (Sessiz) Kurulum Başlatın:
		○ IBM MQ'yu sessiz kurulumla komut satırından kurabilirsiniz. Bunun için aşağıdaki komutu kullanırsınız:

msiexec /i "MQ_INSTALLATION_MEDIA\MSI\IBM MQ.msi" /l*v c:\wmqinslogs\install.log /q USEINI="MQ_INSTALLATION_MEDIA\Response.ini" TRANSFORMS="1033.mst" AGREETOLICENSE="yes" ADDLOCAL="Server"
		○ Bu komut, IBM MQ'yu sessiz bir şekilde yükler ve log dosyasına kurulum çıktısını kaydeder.
	2. Ortam Değişkenlerini Yapılandırın:
		○ IBM MQ’nun doğru çalışabilmesi için ortam değişkenlerini ayarlamanız gerekecek. Bu, setmqenv komutuyla yapılır:

"MQ_INSTALLATION_PATH/bin/setmqenv" -s
	3. Queue Manager (Kuyruk Yöneticisi) Oluşturun:
		○ Aşağıdaki komutla QM1 adında bir kuyruk yöneticisi oluşturun:

crtmqm QM1
		○ Sonrasında kuyruk yöneticisini başlatmak için şu komutu kullanın:

strmqm QM1
	4. Queue (Kuyruk) Oluşturun:
		○ Komut satırında runmqsc komutuyla kuyrukları ve diğer MQ objelerini oluşturabilirsiniz. LQ1 adında bir kuyruk oluşturmak için:
		○ runmqsc QM1
define qlocal(LQ1)
end
	5. Mesaj Gönderme (Put Message):
		○ IBM MQ'nun sağladığı amqsput örnek uygulamasıyla kuyruğa mesaj gönderin:

amqsput LQ1 QM1
		○ Bu komut ile kuyruğa "Hello World" mesajını gönderirsiniz.
	6. Mesaj Alma (Get Message):
		○ amqsget komutuyla kuyruğa eklediğiniz mesajı alabilirsiniz:

amqsget LQ1 QM1

3. IBM MQ'nun Uninstall Edilmesi
Eğer IBM MQ'yu kaldırmak isterseniz, aşağıdaki adımları izleyebilirsiniz:
	1. IBM MQ servisini durdurun.
	2. MQ'yu kaldırın ve kuyruk yöneticilerini de silin. Bu işlemle birlikte tüm IBM MQ nesneleri de silinir.

4. Özet
Bu senaryonun amacı, IBM MQ'yu Windows üzerinde kurmak ve temel yapılandırmaları (queue manager ve queue oluşturma, mesaj gönderme ve alma) yapmaktır. Kurulumun ardından:
	• IBM MQ Explorer veya komut satırı üzerinden kuyruk yöneticisini ve kuyrukları yönetebilirsiniz.
	• Mesajlaşma işlemleri gerçekleştirebilir ve verilerin doğru bir şekilde iletilip alındığını doğrulayabilirsiniz.


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

. Queue Manager Oluşturulması
	• Queue Manager Nedir? Queue Manager, IBM MQ'nin merkezinde yer alan bir bileşendir. Kuyrukları yönetir ve mesajları doğru kuyruğa yönlendirir. Bir sistemdeki tüm mesajların saklandığı, alınacağı ve gönderileceği ana bileşendir. Bu nedenle, her iletişim kanalının bir Queue Manager’a bağlanması gereklidir.
	• crtmqm QM1 Komutu: Bu komut, yeni bir Queue Manager (QM1) oluşturur. QM1 burada örnek bir isimdir, fakat siz bunu dilediğiniz gibi değiştirebilirsiniz.
Ekranda Görülen Mesajlar:

IBM MQ queue manager created.
Creating or replacing default objects for QM1.
Default objects statistics: 61 created. 0 replaced. 0 failed.
Completing setup.
Setup completed.

Bu mesajlar, Queue Manager'ın başarıyla oluşturulduğunu ve varsayılan objelerin eklendiğini gösterir.
	• strmqm QM1 Komutu: Queue Manager'ı başlatmak için bu komut kullanılır. Başlatıldıktan sonra, mesajlaşma altyapısının aktif hale gelmesi sağlanır.
Ekranda Görülen Mesajlar:

IBM MQ queue manager 'QM1' starting.
5 log records accessed on queue manager 'QM1' during the log replay phase.
IBM MQ queue manager 'QM1' started.

Bu mesajlar, Queue Manager'ın başlatıldığını ve loglarının başarılı bir şekilde yüklendiğini gösterir.
2. Queue Oluşturulması
Queue'lar, mesajları saklamak için kullanılan veri yapılarıdır. Bu adımda, iki tür kuyruk oluşturulmaktadır:
	• Local Queue (Yerel Kuyruk): QM1'de mesajların yerel olarak saklandığı kuyrukları tanımlar.
	• Remote Queue (Uzak Kuyruk): Mesajların başka bir Queue Manager'a yönlendirilmesini sağlayan kuyruktur.
	• runmqsc QM1 Komutu: Bu komut, MQSC (MQ Script Command) arayüzünü başlatır ve kuyrukları yönetmek için kullanılır.
	• Yerel Kuyruk Tanımlama: İlk olarak, yerel bir kuyruk (QM2) oluşturuluyor. Bu kuyruk, mesajları saklamak için kullanılır.
Komut:

DEFINE QLOCAL(QM2) DESCR('Transmission queue to QM2') USAGE(XMITQ)

Bu komut ile, QM1'deki mesajları başka bir Queue Manager’a gönderebilmek için bir yerel kuyruk oluşturulur.
	• Uzak Kuyruk Tanımlama: QM1'de, başka bir Queue Manager’a mesaj gönderilmesi için bir uzak kuyruk tanımlanır.
Komut:

DEFINE QREMOTE(QUEUE.ON.QM2) DESCR('Remote queue for QM2') XMITQ(QM2) RNAME(RECEIVEQUEUE) RQMNAME(QM2)

Bu komut, QM1'den QM2'ye mesaj göndermek için gerekli uzak kuyruk yapısını oluşturur.
3. Sender Channel Oluşturulması
	• Sender Channel Nedir? Sender Channel, bir Queue Manager'dan başka bir Queue Manager'a mesaj göndermek için kullanılan iletişim kanalını tanımlar.
	• DEFINE CHANNEL Komutu ile Sender Channel Tanımlama: TO.QM2 adlı sender channel, QM1'den QM2'ye mesaj gönderebilmek için tanımlanır.
Komut:

DEFINE CHANNEL(TO.QM2) CHLTYPE(SDR) CONNAME('remoteHost') TRPTYPE(TCP) XMITQ(QM2)

Burada:
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
	• Komut:

DEFINE CHANNEL(TO.QM2) CHLTYPE(RCVR) TRPTYPE(TCP)
		○ CHLTYPE(RCVR) ile alıcı kanal (receiver) tanımlanır.
		○ Bu kanal, mesajların hedef queue manager'a iletilmesini sağlar.
6. Sender Channel'ın Başlatılması
Sender Channel'ı başlatarak mesajların gönderilmesini sağlar.
	• START CHANNEL Komutu:

START CHANNEL(TO.QM2)

Bu komut, QM1'deki sender channel'ı başlatır ve otomatik olarak hedef Queue Manager’a bağlanır.
7. Çözümün Doğrulanması
Son adımda, çözümün doğru çalışıp çalışmadığını doğrulamak için aşağıdaki işlemler yapılır:
	• Mesaj Gönderme:
		○ amqsput komutuyla, QM1'den QM2'ye mesaj gönderilir.
		○ Bu işlem başarılı olduğunda, QM2'deki kuyruktan alınan mesaj doğrulanır.
	• amqsget Komutu ile Mesaj Alımı:
		○ QM2'deki kuyruğa gelen mesajlar alınır.
		○ Mesaj başarılı bir şekilde alınmışsa, işlem tamamlanmış olur.
Sonuçlar: Bu işlemler, iki Queue Manager arasında doğru bir iletişim yapılandırması kurulduğunu ve mesajların başarıyla iletilip alındığını doğrular.

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
		○ runmqsc komutuyla, QM1 kaynak queue manager’ı için TLS ile güvenli bir gönderici kanalı oluşturulur.

DEFINE CHANNEL(TO.QM2) CHLTYPE(SDR) TRPTYPE(TCP) CONNAME('remoteHost') XMITQ(QM2) SSLCIPH(TLS_RSA_WITH_AES_128_CBC_SHA256) DESCR('Sender channel using TLS from QM1 to QM2') REPLACE
	2. Receiver Kanalı (Alıcı Kanalı) Oluşturmak:
		○ QM2 hedef queue manager’ı için benzer şekilde bir alıcı kanalı oluşturulur.

DEFINE CHANNEL(TO.QM2) CHLTYPE(RCVR) TRPTYPE(TCP) SSLCIPH(TLS_RSA_WITH_AES_128_CBC_SHA256) SSLCAUTH(REQUIRED) DESCR('Receiver channel using TLS from QM1 to QM2') REPLACE



IBM MQ Streaming Queues Özelliği
Genel Bakış: IBM® MQ'nun streaming queues (akış kuyruğu) özelliği, bir kuyruğa gönderilen her mesajın hemen hemen aynı kopyasının başka bir kuyruğa iletilmesini sağlar. Bu özellik, bazı senaryolarda mesajların bir kopyasını oluşturmanız gerektiğinde faydalıdır. Örneğin:
	• Apache Kafka'ya mesaj akışı sağlamak için Kafka Connect source connector kullanarak IBM MQ'ya bağlanmak.
	• Sistemdeki verilerin analizini yapmak.
	• Mesajları gelecekteki bir zaman için kurtarma amacıyla depolamak.
	• Geliştirme ve test sistemlerinde kullanılmak üzere mesajları yakalamak.
	• IBM MQ olay mesajlarını sistem olay kuyruklarından tüketmek ve ek kopyalarını diğer kuyruklara veya konulara göndermek.
Bu senaryolarda, streaming queues yapılandırılması, orijinal mesajların akış işleminden etkilenmemesini sağlar. Bu, iş uygulamalarının akıştan etkilenmemesini garanti eder.
Streaming Queues Konfigürasyonu
Konfigürasyon:
Streaming queues, IBM MQ yöneticisi tarafından her bir kuyruk için yapılandırılır ve mesajlar, uygulama tarafından değil, queue manager (kuyruk yöneticisi) tarafından akışa alınır.
Örnek Konfigürasyon: Bir kuyruk, STREAMQ(MY.REMOTE.Q) şeklinde yapılandırılabilir; burada MY.REMOTE.Q bir uzak kuyruk tanımıdır.
Streaming Queues ile İlgili Kısıtlamalar
	• Transaction (İşlem) ile Streaming:
Streaming queues özelliği, bir kuyruktan bir mesaja kopya eklerken, iki mesajın da aynı işlem (unit of work) altında kuyruğa eklenmesini sağlar. Bu, genellikle işlemlerin tutarlılığını sağlamaya yardımcı olur.
	• Cluster Queues (Küme Kuyrukları) ile Streaming:
Mesajlar, yerel kuyruktan bir cluster kuyruğuna ve cluster kuyruk örneklerinden birine yerel kuyruğa aktarılabilir. Bu işlem, kümeleme yapılandırmalarında da çalışır.
Streaming Queues Özelliğinin Kullanım Alanları
	1. Veri Analizi:
Sistemdeki veriler üzerinden analiz yapabilmek için mesajların bir kopyasını farklı kuyruklarda saklayabilirsiniz.
	2. Mesajları Kurtarma İçin Depolama:
Mesajlar, ilerleyen zamanlarda kurtarma amacıyla saklanabilir. Bu, özellikle kritik işlemlerin kayıt altına alınması için kullanışlıdır.
	3. Geliştirme ve Test Sistemlerinde Kullanma:
Geliştirme ve test aşamalarında kullanılacak veri setlerinin oluşturulması amacıyla mesajlar kopyalanabilir.
	4. Sistem Olay Mesajları ve Ekstra Kopyalar:
IBM MQ sisteminin olay mesajlarını kullanarak, mesajlar ek kuyruklara veya konu başlıklarına yönlendirilebilir.
	5. Cluster Kuyruklarında Mesaj Akışı:
Mesajlar, küme kuyruklarına ve küme kuyruklarından yerel kuyruklara aktarılabilir. Bu, dağıtık sistemlerde etkin veri aktarımı sağlar.

Mesaj Geçmişi Saklama
CAPEXPRY (Geçerlilik Süresi) Özelliği: Streaming queues özelliği, mesajların bir geçmişinin tutulmasını sağlar. Bu özellik, mesajların belli bir süre boyunca saklanmasını sağlamak için CAPEXPRY (geçerlilik süresi) özelliği ile yapılandırılabilir. Bu sayede mesajların belirli bir süre sonra otomatik olarak silinmesi sağlanabilir.

Bu özellik, IBM MQ'yu veri akışları, veri analizi ve mesajların korunması gibi çeşitli kritik senaryolarda etkili şekilde kullanabilmenizi sağlar. Bu özellik, özellikle veri güvenliği ve sistem performansının kritik olduğu üretim ortamlarında büyük önem taşır.

Streaming Queues Configuration in IBM MQ
Genel Bakış: IBM® MQ'nun streaming queues (akış kuyruğu) özelliği, yöneticilerin her bir kuyruk için yapılandırabileceği bir özelliktir. Bu özellik sayesinde, mesajlar, kuyruk yöneticisi tarafından akışa alınır ve uygulama tarafından değil. Bu, uygulamanın orijinal kuyruğa mesaj gönderirken, akışın gerçekleştiğinden haberdar olmaması anlamına gelir. Benzer şekilde, orijinal kuyruğa mesajları tüketen uygulama da mesaj akışından haberdar değildir.
Not: IBM MQ istemci kütüphanesinin sürümünü güncellemek gerekmez ve orijinal mesajlar akış sürecinden tamamen etkilenmez.
İki Modda Yapılandırma
	1. Best Effort (En İyi Çaba)
Bu modda, kuyruk yöneticisi, orijinal mesajın teslimatının, akış mesajının teslimatından daha önemli olduğunu varsayar.
Eğer orijinal mesaj teslim edilebiliyorsa ancak akış mesajı teslim edilemiyorsa, orijinal mesaj yine de kuyruğa teslim edilir. Bu mod, iş uygulamalarının akış işleminden etkilenmemesinin önemli olduğu durumlar için uygundur.
	2. Must Duplicate (Zorunlu Kopya)
Bu modda, kuyruk yöneticisi her iki mesajın da başarılı bir şekilde teslim edilmesini sağlar.
Eğer akış mesajı teslim edilemiyorsa (örneğin, ikinci kuyruk doluysa), orijinal mesaj da teslim edilmez. Uygulama, bir hata nedeni kodu alır ve mesajı tekrar göndermeyi denemelidir. Bu mod, her iki mesajın da teslim edilmesi gerektiği senaryolar için kullanılır.
Akış Mesajları
Çoğu durumda, ikinci kuyruğa teslim edilen mesaj, orijinal mesajın bir kopyasıdır. Bu, mesajın tüm açıklama alanlarını (mesaj ID ve korelasyon ID dahil) içerir. Akış mesajları, orijinal mesajlara oldukça yakın kopyalar olarak tasarlanır, böylece daha kolay bulunabilir ve gerekirse başka bir IBM MQ sistemine tekrar aktarılabilir.
Akış Mesajlarında Yapılan Değişiklikler:
	• Mesajın son kullanma tarihi (expiry):
Akış mesajının son kullanma tarihi, orijinal mesajın son kullanma tarihinden bağımsız olarak MQEI_UNLIMITED olarak ayarlanır. Eğer ikinci kuyrukta CAPEXPRY özelliği ayarlanmışsa, bu değeri kullanarak akış mesajının son kullanma tarihi belirlenir.
	• Rapor Seçenekleri:
Orijinal mesajda belirtilen şu raporlama seçenekleri, akış mesajlarında etkinleştirilmez:
		○ Aktivite raporları
		○ Süre sonu raporları
		○ İstisna raporları
		○ Varış onayı (COA)
		○ Teslimat onayı (COD)
Bu, akış mesajlarının, beklenmedik rapor mesajlarını, bu tür raporları almak için tasarlanmamış uygulamalara iletmeyecek şekilde yapılandırılmasını sağlar.
Diğer Özellikler:
	• Akış mesajları, genellikle ikinci kuyrukla ilgili hiçbir özelliği taşımaz. Örneğin, ikinci kuyruğun DEFPSIST ve DEFPRTY gibi özellikleri, akış mesajını etkilemez.
Özel Durumlar:
	• CAPEXPRY Özelliği:
Eğer ikinci kuyruk CAPEXPRY özelliği ile yapılandırılmışsa, bu özellik akış mesajına da uygulanır.
	• Cluster Kuyruklarında DEFBIND:
Eğer ikinci kuyruk bir cluster kuyruğuysa, akış mesajı, DEFBIND özelliğinde belirtilen bağlama seçeneği kullanılarak kuyruğa iletilir.
Kullanım Senaryoları
	• Veri Depolama ve Kurtarma:
Mesajların geçmişini saklamak için akış kuyrukları kullanılabilir, bu da verilerin belirli bir süre boyunca korunmasını sağlar.
	• Veri Akışı ve Analiz:
Sistem içindeki verilerin analiz edilmesi veya başka sistemlere veri akışı yapılması için kullanılabilir.
Akış kuyrukları özelliği, IBM MQ sistemlerinde mesajların güvenli ve tutarlı bir şekilde kopyalanmasını sağlayarak, birden fazla uygulamanın aynı mesaj verisi üzerinde işlem yapmasına imkan verir.


Streaming to Remote and Alias Queues in IBM MQ
Genel Bakış: IBM® MQ'da, mesajların yerel kuyruklardan uzak kuyruklara (remote queues) veya takma ad kuyruklarına (alias queues) akışının yapılması mümkündür. Bu özellik, bir kuyruktaki mesajları başka bir kuyruktan bağımsız olarak çoğaltmanıza ve farklı sistemlere iletmenize olanak tanır.
Streaming to Remote Queues (Uzak Kuyruğa Akış)
	• Tanım:
Yerel bir kuyruktan uzak bir kuyruğa mesaj akışı yapıldığında, kopyalanmış mesajlar başka bir kuyruk yöneticisine ait bir kuyruğa gönderilebilir. Bu, mesajların birden fazla IBM MQ ağındaki kuyruğa kopyalanmasını sağlar.
	• Örnek Senaryo:
Örneğin, Q1 kuyruğu STREAMQ(MY.REMOTE.Q) şeklinde yapılandırılabilir. Burada, MY.REMOTE.Q bir uzak kuyruk tanımıdır ve mesajlar bu kuyruk üzerinden yönlendirilir.
Avantaj:
Bu özellik, mesajların merkezi bir noktada saklanmasının yanı sıra, farklı konumlar arasında veri yedekleme ve yeniden iletim sağlar.
Streaming to Alias Queues (Takma Ad Kuyruğuna Akış)
	• Tanım:
Mesajları bir alias kuyruğuna akış yapmak, çoğaltılmış mesajları alias kuyruğunun hedef kuyruğuna yönlendirmeyi sağlar. Takma ad kuyrukları, hedef olarak bir başka kuyruk ya da bir topic (yayın/abone) de olabilir. Bu durumda, çoğaltılmış mesajlar, topic'e abone olan tüm alıcılara gönderilebilir.
	• Publish/Subscribe ile Entegrasyon:
Bir alias kuyruğu hedef olarak bir topic'e işaret ediyorsa, bu durumda çoğaltılmış mesajlar, topic'e abone olan her kullanıcılara gönderilecektir. Ancak, mesajlar orijinal mesajla tamamen aynı olmayacaktır. Yayın/abone kurallarına göre şu değişiklikler olabilir:
		○ Yeni bir mesaj ID'si oluşturulur.
		○ Korelasyon ID'si, abonelik yapılandırmasına bağlı olarak oluşturulur.
		○ UserIdentifier alanı, mesajı gönderen uygulamanın kimliğinden ziyade, kuyruk yöneticisinin çalıştığı kullanıcıyı gösterir.
		○ PutApplName, mesajı koyan uygulamanın adı yerine kuyruk yöneticisinin adı olur.
Önemli Notlar:
	• STREAMQ Özelliği:
Uzak kuyruklar veya alias kuyrukları üzerinde doğrudan STREAMQ özelliği yapılandırılamaz. Yalnızca mesajlar bu kuyruklara akış yapılabilir, bu kuyruklardan mesaj akışı yapılamaz.
	• Alias Kuyruğu ve STREAMQ:
Eğer mesajlar bir alias kuyruğuna akış yapılacaksa, alias kuyruğunun hedef kuyruk üzerinde STREAMQ özelliği ayarlanmış olamaz.
Özetle:
	1. Uzak Kuyruklara Akış:
Mesajlar, orijinal kuyruktan bir uzak kuyruğa çoğaltılır ve başka bir IBM MQ sisteminde bulunan kuyruğa iletilir. Bu, çoklu sistemler arasında veri iletimi için faydalıdır.
	2. Takma Ad Kuyruklarına Akış:
Takma ad kuyrukları, topic gibi başka hedeflere yönlendirilerek çoğaltılmış mesajların daha fazla alıcıya iletilmesine olanak sağlar. Ancak, mesajlar, orijinal mesajlardan farklı olacak şekilde bazı meta verilerinde değişikliklere uğrar.
Bu özellikler, özellikle mesajların güvenli bir şekilde çoğaltılmasına, arşivlenmesine veya analiz edilmesine olanak tanır.

Streaming Queue Restrictions in IBM MQ
IBM® MQ'da streaming kuyrukları kullanırken, bazı yapılandırmalar desteklenmemektedir. Bu sınırlamalar, mesajların çoğaltılması sırasında karşılaşılabilecek çeşitli senaryoları engeller veya kısıtlar. Aşağıda, streaming kuyruğu özelliğini kullanırken karşılaşılan bazı yapılandırma kısıtlamaları bulunmaktadır:
1. Kuyruk Zinciri Tanımlaması:
	• Desteklenmeyen yapılandırma: Kuyruklar arasında bir zincir oluşturarak mesajları birbirine aktarmak, örneğin: Q1 -> Q2 -> Q3 -> Q4 şeklinde.
	• Açıklama: Bir kuyruktan diğerine sürekli akış sağlamak, her kuyruğun mesajları bir sonraki kuyruğa iletmesini sağlamak mümkün değildir. Bu tür bir yapılandırma, kaynak kuyruğa akışta bir döngü oluşturur ve bu, desteklenmez.
2. Kuyruk Döngüsü Tanımlaması:
	• Desteklenmeyen yapılandırma: Kuyruklar arasında bir döngü oluşturarak mesajların sürekli birbirine akmasını sağlamak, örneğin: Q1 -> Q2 -> Q1 şeklinde.
	• Açıklama: Aynı mesajın sürekli olarak birbirine aktarılacağı bir döngü oluşturmak, mesajın doğru bir şekilde işlenmesini engeller ve bu tür döngüler desteklenmez.
3. Abonelik Tanımlaması ile STREAMQ Özelliği:
	• Desteklenmeyen yapılandırma: Bir abonelik tanımlandığında ve hedef kuyrukta STREAMQ özelliği tanımlı olduğunda.
	• Açıklama: Eğer bir kuyruk bir topic (konu) için abone olarak yapılandırılmışsa ve bu kuyruğa STREAMQ eklenmişse, bu yapılandırma mümkün değildir.
4. XMITQ ile Yapılandırılmış Kuyruklar:
	• Desteklenmeyen yapılandırma: USAGE(XMITQ) olarak yapılandırılmış bir kuyrukta STREAMQ özelliğinin tanımlanması.
	• Açıklama: XMITQ (Transmission Queue) olarak kullanılan kuyruğa STREAMQ eklenemez. XMITQ özelliği, mesajların iletimi için özel bir yapılandırma gerektirdiğinden, STREAMQ özelliğiyle çakışır.
5. Dinamik Kuyrukların STREAMQ Özelliği:
	• Desteklenmeyen yapılandırma: Dinamik kuyruklar için STREAMQ özelliği değiştirilmesi.
	• Açıklama: Dinamik olarak oluşturulan kuyruğun STREAMQ özelliği değiştirilmek istense de, bu mümkün değildir.
6. SYSTEM Kuyrukları ile STREAMQ:
	• Desteklenmeyen yapılandırma: SYSTEM.* adıyla başlayan herhangi bir kuyruk için STREAMQ tanımlanması, ancak aşağıdaki istisnalar dışında:
		○ SYSTEM.DEFAULT.LOCAL.QUEUE
		○ SYSTEM.ADMIN.ACCOUNTING.QUEUE
		○ SYSTEM.ADMIN.ACTIVITY.QUEUE
		○ SYSTEM.ADMIN.CHANNEL.EVENT
		○ SYSTEM.ADMIN.COMMAND.EVENT
		○ SYSTEM.ADMIN.CONFIG.EVENT
		○ SYSTEM.ADMIN.LOGGER.EVENT
		○ SYSTEM.ADMIN.PERFM.EVENT
		○ SYSTEM.ADMIN.PUBSUB.EVENT
		○ SYSTEM.ADMIN.QMGR.EVENT
		○ SYSTEM.ADMIN.STATISTICS.QUEUE
		○ SYSTEM.DEFAULT.MODEL.QUEUE
		○ SYSTEM.JMS.TEMPQ.MODEL
	• Açıklama: SYSTEM.* adıyla başlayan sistem kuyruğunda STREAMQ özelliği yapılandırılamaz. Ancak, belirli sistem kuyruğu isimlerinde, bu kısıtlama geçerli değildir ve bu kuyruğa STREAMQ tanımlanabilir.
7. Model Kuyruğu Adı ile STREAMQ Tanımlanması:
	• Desteklenmeyen yapılandırma: Bir model kuyruğunun adıyla STREAMQ özelliği tanımlanması.
	• Açıklama: Model kuyrukları, mesajların şablon olarak oluşturulmasına yarar ve bu tür kuyruklarda STREAMQ özelliği tanımlanamaz.

Özet:
Bu kısıtlamalar, IBM MQ'da streaming kuyruğu özelliğini kullanırken karşılaşılan bazı yapılandırma engelleridir. Uygulamanın doğru ve verimli bir şekilde çalışabilmesi için bu sınırlamalar göz önünde bulundurulmalıdır. Özellikle kuyruklar arasında döngüler ve zincirler oluşturmak, sistem kuyruğu tanımlamaları ve dinamik kuyruklar gibi belirli durumlar, streaming kuyruğu özelliklerini kullanırken kaçınılması gereken senaryolardır.

IBM MQ Streaming Kuyrukları ve İşlemler
Streaming Kuyrukları ve İşlemler
IBM MQ’nun streaming kuyrukları özelliği, bir kuyruğa gönderilen mesajın, ikinci bir kuyruğa kopyalanmasını sağlar. Bu kopyalama işlemi, genellikle bir işlem birimi (unit of work) içerisinde yapılır. Stream edilen mesajların durumu, orijinal mesajın nasıl gönderildiğine göre farklılık gösterir:
	1. Orijinal mesaj MQPMO_SYNCPOINT ile gönderildiyse:
		○ Kopyalanan mesaj, aynı işlem birimi içerisinde stream kuyruğuna gönderilir. Bu durumda, hem orijinal mesaj hem de kopyalanan mesajın başarılı bir şekilde teslim edilmesi beklenir; aksi takdirde her iki mesaj da teslim edilmez.
	2. Orijinal mesaj MQPMO_NO_SYNCPOINT ile gönderildiyse:
		○ Bu durumda, bir işlem birimi başlatılır, ancak orijinal mesaj işlem birimi talep etmemiş olsa bile, hem orijinal mesaj hem de kopyalanan mesaj aynı işlem birimi içinde işlenir. Bu:
			§ Kopyalanan mesajın teslim edilmediği durumda orijinal mesajın da teslim edilmemesini garanti eder.
			§ Performans artışı sağlar çünkü her iki mesaj aynı işlem birimi içinde yer alır.
İstisnalar:
		○ Eğer orijinal mesaj, MQPMO_NO_SYNCPOINT ile ve STRMQOS özelliği BESTEF (best effort) olarak ayarlanmışsa, mesajlar işlem birimi içinde teslim edilmez. Bu durumda, kopyalanan mesajın teslim edilmemesi orijinal mesajı etkilemez.
Cluster Kuyruklarına Mesaj Stream Etme ve Cluster Kuyruklarından Mesaj Stream Etme
	1. Cluster Kuyruğuna Mesaj Stream Etme:
		○ Bir yerel kuyruğa gelen orijinal mesajların bir kopyasının bir veya birden fazla cluster kuyruk instance'ına gönderilmesini sağlar. Bu, iş yükü dengelemesi yapmak ya da sadece cluster'da başka bir kuyrukta kopyaların yer almasını sağlamak için kullanılabilir.
		○ Cluster Kuyruğu Çalışma Yükü Dengeleme: Mesajlar, DEFBIND özelliğine göre dağıtılır:
			§ Eğer DEFBIND(OPEN) olarak ayarlanmışsa, orijinal kuyruk açıldığında bir cluster kuyruk instance'ı seçilir ve tüm kopyalanan mesajlar bu instance'a yönlendirilir.
			§ Eğer DEFBIND(NOTFIXED) olarak ayarlanmışsa, her MQPUT işlemi için bir cluster kuyruk instance'ı seçilir.
Not: Cluster kuyrukları için tüm instance’lar aynı DEFBIND değerine sahip olmalıdır.
	2. Cluster Kuyruğundan Mesaj Stream Etme:
		○ Eğer bir cluster kuyruğunun birden fazla instance'ına mesaj gönderiyorsanız, her bir mesajın bir kopyasının aynı queue manager üzerinde bir stream kuyruğuna teslim edilmesini sağlamak için kullanılabilir.
Mesajların Tarihini Saklamak İçin Streaming Kuyruklarını Kullanma
Mesajların bir kopyasını belirli bir süre saklamak için streaming kuyrukları kullanılabilir. Bu, örneğin, orijinal mesaj bir uygulama tarafından yanlışlıkla silindiğinde, mesajları geri alabilmek için faydalıdır.
CAPEXPRY Özelliği ile Streaming Kuyruğuna Mesaj Saklama:
	• CAPEXPRY (Mesajın Süre Sonu) özelliği, stream edilen mesajların ne kadar süreyle saklanacağını belirler.
	• Adımlar:
		1. CAPEXPRY özelliğini, mesajların stream edileceği kuyruğa ayarlayın.
		2. Orijinal kuyruğun CAPEXPRY değerini değiştirmenize gerek yoktur.
		3. Şu faktörleri göz önünde bulundurun:
			§ Mesajlara ne kadar süreyle erişmeniz gerektiği.
			§ Orijinal kuyruktan gelen mesaj hızına bağlı olarak, hedef kuyruğun MAXDEPTH ve MAXFSIZE özelliklerinin nasıl ayarlanması gerektiği.
Stream Edilen Mesajlara Erişim:
Eğer bir problem meydana gelir ve bazı veya tüm stream edilen mesajlara erişmeniz gerekirse, dmpmqmsg komutunu kullanarak bu mesajlara erişebilirsiniz:
	• Kuyruktan mesajları okuyup, bir dosyaya kaydedebilirsiniz.
	• Dosyadan mesajları okuyup, tekrar kuyruğa yazabilirsiniz.
dmpmqmsg komutu ile mesaj başlıklarını düzenleyebilir ve örneğin, expiry değerini değiştirebilirsiniz.
Performans Düşünceleri:
Stream edilen mesajların bir kuyruğa kopyalanması ve daha sonra süre bitmiş mesajların silinmesi işlemi küçük bir performans maliyeti yaratır. Ancak, bu maliyet, mesajları manuel olarak başka bir kuyruğa koymak ve sonra uygulamanın bu mesajları silmesi için gereken işlem maliyetinden çok daha düşüktür. Bu konu ile ilgili daha fazla bilgi, Streaming Queues Performance Report'unda bulunmaktadır.



Publish/Subscribe Senaryoları ve Yapılandırmaları
IBM MQ'da publish/subscribe (yayınla/abone ol) modeli, uygulamaların mesajları yayınlamasına (publish) ve bu mesajlara abone olan diğer uygulamalara iletmesine olanak tanır. Bu senaryolarda, farklı publish/subscribe kümeleri ve hierarşiler oluşturularak farklı yapılandırma yöntemleri kullanılır. Aşağıda, üç farklı publish/subscribe senaryosu ve her biri için nasıl yapılandırılacağını açıklamaktadır:

Senaryo: Publish/Subscribe Kümesi Oluşturma
Bu senaryoda, publish/subscribe (yayınla/abone ol) kümesi oluşturulur. Küme, üç farklı queue manager içerir ve bu kümeyi, bir queue manager üzerinden abone olanların, başka bir queue manager üzerinden yayınlanan mesajları alabilmesini sağlayacak şekilde yapılandırır.
Başlangıç İçin Gereksinimler
	• IBM MQ'nun kurulu olması gerekir. Eğer kurulum yapılmadıysa, IBM MQ kurulumu için IBM MQ Server kurulum yönergelerine bakılabilir.
Yapılandırma Adımları
	1. Queue Manager'ları Oluşturun ve Başlatın:
		○ Üç farklı queue manager oluşturulacaktır: PS1, PS2, ve PS3.
Komutlar:

crtmqm PS1
strmqm PS1
crtmqm PS2
strmqm PS2
crtmqm PS3
strmqm PS3
	2. İlk Queue Manager'ın Yapılandırılması (PS1):
		○ PS1, küme için tam bir depo (full repository) olarak yapılandırılacaktır.
		○ Listener ve receiver channel tanımlanacak ve PS1, PS2 ile bilgi alışverişi yapmak için sender channel kurulacaktır.
Komutlar:
		○ DEFINE LISTENER(PS1_LS) TRPTYPE(TCP) CONTROL(QMGR) PORT(5000)
START LISTENER(PS1_LS)
ALTER QMGR REPOS(DEMO)
DEFINE CHANNEL(DEMO.PS1) CHLTYPE(CLUSRCVR) TRPTYPE(TCP) CONNAME('localhost(5000)') CLUSTER(DEMO)
DEFINE CHANNEL(DEMO.PS2) CHLTYPE(CLUSSDR) TRPTYPE(TCP) CONNAME('localhost(5001)') CLUSTER(DEMO)
	3. İkinci Queue Manager'ın Yapılandırılması (PS2):
		○ PS2, küme için başka bir tam depo olarak yapılandırılır.
		○ Listener ve receiver channel tanımlanır. Ayrıca, PS1 ile bilgi alışverişi yapabilmesi için sender channel oluşturulur.
Komutlar:

DEFINE LISTENER(PS2_LS) TRPTYPE(TCP) CONTROL(QMGR) PORT(5001)
START LISTENER(PS2_LS)
ALTER QMGR REPOS(DEMO)
DEFINE CHANNEL(DEMO.PS2) CHLTYPE(CLUSRCVR) TRPTYPE(TCP) CONNAME('localhost(5001)') CLUSTER(DEMO)
DEFINE CHANNEL(DEMO.PS1) CHLTYPE(CLUSSDR) TRPTYPE(TCP) CONNAME('localhost(5000)') CLUSTER(DEMO)
	4. Üçüncü Queue Manager'ın Yapılandırılması (PS3):
		○ PS3, bir kısmi depo (partial repository) olarak yapılandırılır ve diğer full repository queue manager'lar ile iletişim kurar.
		○ Listener ve receiver channel tanımlanır. PS1 veya PS2 ile iletişim kurabilmesi için sender channel oluşturulur.
Komutlar:

DEFINE LISTENER(PS3_LS) TRPTYPE(TCP) CONTROL(QMGR) PORT(5002)
START LISTENER(PS3_LS)
DEFINE CHANNEL(DEMO.PS3) CHLTYPE(CLUSRCVR) TRPTYPE(TCP) CONNAME('localhost(5002)') CLUSTER(DEMO)
DEFINE CHANNEL(DEMO.PS1) CHLTYPE(CLUSSDR) TRPTYPE(TCP) CONNAME('localhost(5000)') CLUSTER(DEMO)
	5. Cluster Konfigürasyonu:
		○ PS1, PS2, ve PS3 queue manager'lar küme (cluster) üyeleri olarak tanımlanacak.
		○ Küme konusu (cluster topic) oluşturulacak ve küme, bir publish/subscribe kümesine dönüştürülecek.
Komutlar:

DEFINE TOPIC(SCORES) TOPICSTR('/Sport/Scores') CLUSTER(DEMO) CLROUTE(DIRECT)
	6. Yayınlama ve Abonelik Testi:
		○ amqspub ve amqssub komutlarını kullanarak farklı queue manager'lar üzerinden bir konuya (topic) yayın yapılacak ve abonelik test edilecektir.
Komutlar:

amqspub /Sport/Scores/Football PS1
amqssub /Sport/Scores/Football PS2
amqssub /Sport/Scores/Football PS3

Publish/Subscribe Hierarşisi Senaryoları
Publish/subscribe hierarşisi, mesajların farklı queue manager'lar arasında daha organize ve hiyerarşik bir yapıyla dağıtılmasını sağlar. Bu senaryolarda, üç farklı yaklaşım kullanarak queue manager'lar arası bağlantılar kurulmaktadır.
Senaryo 1: Queue Manager Adı Alias'ı ile Point-to-Point Kanallar Kullanarak
Bu senaryoda, QM1 ana queue manager'ı, QM2 ve QM3 ise alt queue manager'lardır. Bağlantılar point-to-point kanallar üzerinden yapılır ve queue manager adı alias kullanılarak bağlanır.
Adımlar:
	1. Queue Manager'ları Oluşturun ve Başlatın:
		○ QM1, QM2 ve QM3 için aşağıdaki komutlar kullanılacaktır.

crtmqm QM1
strmqm QM1
crtmqm QM2
strmqm QM2
crtmqm QM3
strmqm QM3
	2. Queue Manager'ların Yapılandırılması:
		○ Her bir queue manager için listener ve channel'lar oluşturulacak.
	3. Bağlantıların Kurulması:
		○ Point-to-point kanalları ile QM1 ile QM2, QM3 arasındaki bağlantılar kurularak iletişim sağlanacak.
	4. Topic Oluşturulması ve Test:
		○ QM2 ve QM3 abone olacak, ve QM1'den yayınlanan mesajlar her iki queue manager'da da alınıp test edilecek.

Bu şekilde, publish/subscribe yapısını kurarak mesajlar arasında iletişim sağlanabilir ve kümeler arasında veri iletimi düzenli bir şekilde yapılabilir.



1. İşlem Birimi (Unit of Work) Nedir?
İşlem birimi, bir dizi işlemi tek bir birim olarak ele alır. Bu birim, işlemlerin ya tamamen başarılı olmasını ya da tamamen başarısız olmasını garanti eder. Eğer işlem sırasında bir hata oluşursa, yapılan değişiklikler geri alınır (backout). İşlem birimi şunları içerir:
	• Commit: İşlem biriminin başarıyla tamamlanıp yapılacak değişikliklerin kalıcı hale getirilmesi.
	• Backout: Hata durumunda yapılan değişikliklerin geri alınması.
2. Yerel ve Global İşlem Birimleri
	• Yerel İşlem Birimi: Yalnızca IBM MQ kuyruğunda yapılan işlemleri içerir. Bu işlem birimi MQCMIT (commit) veya MQBACK (backout) komutları ile tamamlanır. Yerel işlem birimi yalnızca IBM MQ kuyruğunda çalışır.
	• Global İşlem Birimi: Birden fazla kaynak yöneticisini (veritabanları gibi) içerir. IBM MQ, bir işlem birimini koordinasyon için birden fazla sistemde senkronize eder. Bu işlem, iki aşamalı commit (two-phase commit) süreci ile yönetilir.
3. Global İşlem Birimi Koordinasyonu
	• Queue Manager'ın Koordinasyonu: IBM MQ, global işlem birimlerini kendi başına koordine edebilir. Bu durumda, MQBEGIN komutu ile işlem başlatılır, ardından MQCMIT veya MQBACK komutları ile işlem tamamlanır veya geri alınır.
	• Dış Yazılım Koordinasyonu: IBM MQ dışında bir yazılım (örneğin TXSeries veya Tuxedo) global işlem birimini koordine edebilir. Bu durumda, dış yazılımın API'si kullanılır ve MQBEGIN ile işlem başlatılmaz.
4. İşlem Birimi İlerleme Durumu ve Kurtarma
	• IBM MQ, işlem birimleri sırasında veritabanı ile bağlantı kaybolursa, yeniden bağlantı kurulduğunda işlem birimi otomatik olarak kurtarılır. Eğer bir işlem birimi başarıyla başlatılmış fakat tamamlanmamışsa, queue manager rsvmqtrn komutuyla bu durumları yönetebilir.
5. Veritabanı Koordinasyonu
	• XA Protokolü: IBM MQ, veritabanı güncellemelerini koordine etmek için XA protokolü kullanır. Bu protokolde, her kaynak yöneticisi (veritabanı gibi) commit veya backout kararlarını verir.
	• Veritabanı Bağlantısı: IBM MQ, işlem birimi içinde veritabanına SQL sorguları gönderdiğinde, MQCMIT komutuyla bu sorguların sonucu kalıcı hale gelir.
6. İzolasyon Seviyeleri (Isolation Levels)
	• İzolasyon Seviyesi: IBM MQ, işlem biriminde, bir mesajın kuyruğa gönderilmeden önce veritabanında yapılan güncellemelerin görülebilir olup olmayacağını belirler. İki aşamalı commit işlemi ile bu sorun çözülür. Veritabanı yapılandırmasına göre, commit işlemi önce veritabanında yapılabilir, ardından IBM MQ kuyruğunda yapılabilir.
7. Güvenlik ve Yöneticilik
	• Veritabanı Bağlantı Yönetimi: IBM MQ, işlem birimi başlatıldığında, veritabanı ile bağlantıyı kurar ve bu bağlantıyı, işlem biriminin sonunda sonlandırır. Bu süreçte kullanılan kimlik doğrulama bilgileri, XAOpenString içinde belirtilir.
	• Güvenlik Önlemleri: IBM MQ ile veritabanı arasındaki güvenlik, her iki sistemde de doğru kullanıcı yetkilendirmeleri ile sağlanır. Örneğin, Db2 veya Oracle gibi veritabanlarında, IBM MQ'nun işlemi gerçekleştirebilmesi için gerekli izinler tanımlanmalıdır.
8. Veritabanı Konfigürasyonu ve Entegrasyonu
	• Switch Load Dosyaları: Veritabanı yönetimi için IBM MQ'nun switch load dosyaları oluşturulmalıdır. Bu dosyalar, IBM MQ'nun veritabanı ile iletişim kurmasını sağlar. Uygulama tarafından kullanılan veritabanı bağlantıları bu dosyalar aracılığıyla yönetilir.
9. Dinamik Kayıt (Dynamic Registration)
	• Dinamik Kayıt: IBM MQ, veritabanlarında yapılan kalıcı güncellemeleri otomatik olarak kaydeder. Bu optimizasyon, yalnızca kalıcı veritabanı güncellemeleri içeren işlem birimlerinde gerekli olan XA işlevlerini çağırır.
Sonuç:
IBM MQ ile veritabanı koordinasyonu, iki aşamalı commit protokolü kullanarak verilerin tutarlılığını sağlar. Yerel ve global işlem birimleri, farklı senaryolara göre özelleştirilebilir ve IBM MQ'nun sağladığı güçlü yönetim araçları ile güvenli ve verimli bir işlem birimi yönetimi sağlanabilir. Bu süreçlerin doğru çalışabilmesi için sistemin doğru yapılandırılması ve her bileşenin uygun şekilde senkronize olması gerekmektedir.

enaryo 2: Diğer Yazılımın Koordinasyonu Sağladığı Durum
Bu senaryoda, IBM MQ, global işlem birimlerini koordine etmek için dış bir işlem yöneticisi kullanır. IBM MQ burada işlem birimini koordine etmez; sadece işlemlere katılır. MQBEGIN, MQCMIT, ve MQBACK komutları kullanılamaz.
1. Dış Senkronizasyon Koordinasyonu
Dış bir X/Open XA uyumlu işlem yöneticisi, global işlem birimlerini koordine eder. IBM MQ, bu işlem biriminde bir kaynak yöneticisi olarak yer alır. İşlem yöneticisi (örneğin, TXSeries veya CICS), işlemi başlatır, ilgili kaynak yöneticilerine haber verir ve işlemi iki aşamalı commit süreciyle tamamlar.
İşlem Akışı:
	• Uygulama, dış senkronizasyon yöneticisine bir işlem başlatmak istediğini bildirir.
	• Senkronizasyon yöneticisi, IBM MQ gibi kaynak yöneticilerine bu işlem hakkında bilgi verir.
	• Uygulama, işlemle ilgili kaynak yöneticilerine (örneğin, MQGET komutlarıyla IBM MQ) çağrılar yapar.
	• Uygulama, commit veya backout talebini senkronizasyon yöneticisine iletir.
	• Senkronizasyon yöneticisi, işlem birimini tamamlamak için her kaynak yöneticisine uygun komutları gönderir, genellikle iki aşamalı commit protokolü ile.
2. IBM MQ XA Anahtarı Yapısı
IBM MQ'nun her kaynak yöneticisi için bir XA switch yapısı gereklidir. Bu yapı, kaynak yöneticisinin yeteneklerini ve senkronizasyon yöneticisi tarafından çağrılacak fonksiyonları tanımlar.
	• MQRMIXASwitch: Statik XA kaynak yönetimi için kullanılan yapıdır.
	• MQRMIXASwitchDynamic: Dinamik XA kaynak yönetimi için kullanılan yapıdır.
Çoğu işlem yöneticisi, dinamik XA kaynak yönetimini tercih eder. Bu, daha verimli bir işlem yönetimi sağlar.
3. Dış Senkronizasyon Yöneticisi ve IBM MQ Bağlantısı
Dış senkronizasyon yöneticisinin (örneğin, CICS veya Tuxedo) IBM MQ ile bağlantısı aşağıdaki gibi yapılır:
	• xa_open çağrısı, işlem yöneticisi tarafından yapılır ve bu çağrı, IBM MQ'nun bağlanacağı doğru kuyruğa yönlendirilir.
	• MQCONN çağrısı, işlem yöneticisi ve IBM MQ arasındaki bağlantıyı kurar.
4. CICS Kullanımı
CICS (Customer Information Control System), TXSeries'in bir parçasıdır ve IBM MQ ile iki aşamalı commit protokolüyle çalışır. CICS, IBM MQ'yu bir kaynak yöneticisi olarak kullanabilir, ancak işlemler CICS tarafından koordine edilir. Bu, işlem yöneticisinin IBM MQ işlemlerini yönetmesini sağlar.
CICS Gereksinimleri:
	• CICS ve IBM MQ aynı fiziksel makinede olmalıdır.
	• CICS, yalnızca tek bir IBM MQ kuyruğuna bağlanabilir.
	• CICS, IBM MQ ile etkileşime girmeden önce MQCONN çağrısı yapmalıdır.
5. Microsoft Transaction Server (COM+) Kullanımı
COM+ (Microsoft Transaction Server), iş mantığı uygulamalarını yönetmek için kullanılan bir teknolojidir. COM+ üzerinden yapılan işlemler, IBM MQ ve veritabanı sistemleri gibi arka uç hizmetleriyle entegrasyonu sağlar. IBM MQ, COM+ ile köprü işlevi görür.
6. Global İşlem Birimlerinin Süre Sonu
Queue Manager, işlem yöneticisinin çalışmaya başlaması ve işlemin tamamlanmaması durumunda işlemi sonlandırabilir. AMQ_XA_TRANSACTION_EXPIRY ve AMQ_TRANSACTION_EXPIRY_RESCAN gibi çevresel değişkenlerle, işlem birimlerinin sonlanma sürelerini kontrol edebilirsiniz. Bu özellik, dış işlem yöneticisinin çökmeleri durumunda önemlidir.
7. İyileştirilmiş Dış Senkronizasyon Koordinatörleri
Bazı dış işlem yöneticileri, işlem birimlerinin başarılı bir şekilde tamamlanmasını sağlamak için farklı bağlantı stratejileri kullanır. IBM MQ, genellikle yalnızca tek bir queue manager'a bağlanabilir ve yalnızca bir işlem yöneticisiyle işlem yapabilir. Ancak, CICS veya Tuxedo gibi sistemlerle bu sınırlar aşılabilir.
8. Z/OS ve Recovery Düzeyi
IBM MQ, recovery (kurtarma) süreçlerinde Unit of Recovery özelliği kullanır. Bu özellik, işlemlerin kurtarılmasını ve yeniden başlatılmasını sağlar. CICS veya diğer dış işlem yöneticileri ile yapılan işlemler, kuyruğa bağlı birden fazla sistemde yönetilebilir ve kurtarılabilir.


IBM MQ 9.3 sürümünden IBM MQ 9.4 sürümüne Windows ortamında geçiş yapmak için iki farklı yol sunulmaktadır: tek aşamalı (single-stage) geçiş ve yan yana (side-by-side) geçiş. Aşağıda her iki yöntemi de detaylı  açıklayacağım.
1. Tek Aşamalı Geçiş (Single-Stage Migration)
Tek aşamalı geçiş, eski IBM MQ sürümünün tamamen kaldırılıp, yerine yeni sürümün aynı dizine kurulum yapılmasıdır. Bu yöntemle:
	• Eski IBM MQ sürümünü kaldırmadan önce veri yedeklemesi yapmanız önemlidir.
	• Yeni sürüm kurulduktan sonra, uygulamalar otomatik olarak yeni sürümün kütüphanelerini kullanmaya başlar.
	• Sistem geçiş sırasında tamamen kapalı kalır, yani geçiş süresi boyunca işlem yapılamaz.
2. Yan Yana Geçiş (Side-by-Side Migration)
Yan yana geçiş, eski sürümün yanına yeni sürümün kurulduğu bir yöntemdir. Bu yöntemde:
	• Eski sürüm hala aktifken yeni sürüm kurulur ve test edilir.
	• Eski sürümdeki kuyruğa bağlı işlemler yeni sürüme geçiş yapılana kadar devam eder.
	• Eski sürüm, yeni sürüm test edildikten ve gerekli geçiş tamamlandıktan sonra kaldırılır.
Geçişin Temel Adımları
Adım 1: IBM MQ 9.3'ün Yedeklenmesi ve Hazırlık
	• Queue Manager'ı durdurun. Bu işlemi IBM MQ Explorer üzerinden gerçekleştirebilirsiniz.
	• Veri yedeklemesi yaparak, geçiş sırasında veri kaybı yaşamamak için gerekli tüm dosyaları (örneğin, C:\ProgramData\IBM\MQ\Qmgrs) yedekleyin.
Adım 2: IBM MQ 9.4'ü Kurma
	• IBM MQ 9.4'ü Windows için kurulum paketinden kurulum yapın. Kurulum için Launchpad kullanabilir ve gerekli yazılım gereksinimlerini kontrol edebilirsiniz.
	• Kurulum tamamlandıktan sonra, IBM MQ Explorer'ı açın ve yeni sürümdeki queue manager'ı doğrulayın.
Adım 3: JMS Konfigürasyonu ve Admin Nesneleri
	• JNDI Namespace (Java Naming and Directory Interface) ve JMS bağlantı fabrikası, kuyruğa bağlı uygulamalar için konfigüre edilmelidir.
	• IBM MQ Explorer üzerinden JMS Administered Objects kısmında bağlantı fabrikaları ve hedefler (queues) oluşturulmalıdır.
Adım 4: Örnek Uygulama ile Test Etme
	• IBM MQ 9.4 kurulduktan sonra, örnek JMS uygulamasını çalıştırarak mesajların doğru bir şekilde kuyruğa gönderilip alındığını doğrulayın.
		○ Requester ve Responder komut dosyalarını çalıştırarak, mesajlar üzerinden iletişim kurduğunuzdan emin olun.
Adım 5: Geçişi Tamamlama
	• Yeni sürümdeki queue manager'ı başarıyla test ettikten sonra, eski sürümü kaldırabilirsiniz.
	• Eski sürümü kaldırırken verilerin kaybolmaması için dikkatli olun.
Kurulum Detayları
	1. IBM MQ 9.4 Kurulumu:
		○ IBM MQ'yu kurarken, kurulum işlemini Launchpad üzerinden başlatın. Kurulum sırasında dil seçimi ve yazılım gereksinimlerini kontrol edin.
		○ Kurulum sonrası IBM MQ Explorer'ı açın ve doğru şekilde çalıştığını doğrulayın.
	2. IBM MQ'yu Yapılandırma:
		○ JMS Administered Objects için gerekli konfigürasyonları yapın. Burada, bağlantı fabrikaları ve hedeflerin doğru şekilde ayarlandığını kontrol edin.
Sonuç
IBM MQ'nun geçişi başarıyla tamamlandıktan sonra, yeni sürümdeki özelliklerden (örneğin, LDAP yetkilendirmesi, yeni sürekli teslimat sürümü) faydalanabilirsiniz. Ayrıca, eski sürümden yeni sürüme geçiş sırasında verilerin kaybolmaması için her zaman yedekleme yapmayı unutmayın. Bu şekilde, IBM MQ'nun yeni sürümüne sorunsuz bir geçiş sağlayabilirsiniz.


IBM MQ'nun daha yeni bir sürümünü, daha önceki bir sürümle aynı sistemde "yan yana" kurmak (side-by-side installation) için takip edilmesi gereken adımlar şunlardır:
1. Çoklu Kurulum Genel Bakış
IBM MQ'nun farklı sürümlerinin aynı sistemde yan yana çalışabilmesi, özellikle geçiş süreçlerini yönetmek açısından faydalıdır. Bu tür bir kurulumda, eski sürümdeki uygulamalar ve kuyruk yöneticileri durdurulmadan yeni sürüm kurulabilir.
Sistem Gereksinimleri ve Donanım
	• İşletim Sistemi: Windows 10
	• Örnek Kuyruk Yöneticileri:
		○ QM80: IBM MQ 8.0.0 ile kurulu kalacak.
		○ QMMIG: IBM MQ 8.0.0 ile oluşturulmuş, IBM MQ 9.1'e geçiş yapılacak.
		○ QM910: IBM MQ 9.1.0 ile kurulu ve değiştirilmeyecek.
2. IBM MQ 9.4'ü Yan Yana Kurma
IBM MQ 9.4 sürümünü daha eski bir sürümle aynı makinede yan yana kurmak için şu adımları takip edin:
Başlamadan Önce
IBM MQ 9.1 sürümünün kurulu olduğundan emin olun. Eğer kurulu değilse, IBM MQ 9.1'i önce kurmalısınız.
Kurulum Adımları:
	1. Yönetici Olarak Giriş Yapın: Yönetici haklarıyla giriş yapın.
	2. IBM MQ 9.4'ü İndirin ve Kurun:
		○ IBM MQ 9.4'ün kurulum dosyasını indirin ve çıkarın.
		○ setup.exe komutunu çalıştırarak kurulum başlatın.
		○ Yazılım Gereksinimlerini Kontrol Edin: Gerekli yazılımın kurulu olduğundan emin olun.
		○ Ağ Konfigürasyonunu Kontrol Edin: Bu örnekte, sistem bir alan (domain) parçası olmadığı için "Hayır" seçeneğini seçin.
		○ Kurulum Yöntemi Seçimi: "Mevcut kurulumu etkilemeden kurulum" seçeneğini seçin.
		○ Özel Kurulum: Gerekli bileşenleri seçin (örneğin, MQI istemcisi).
		○ Kurulum tamamlandığında, IBM MQ Explorer'ı başlatın.
3. setmqenv Komutunu Kullanarak İki Sürümle Çalışma
Kurulum tamamlandığında, iki sürümle de çalışmak için setmqenv komutunu kullanarak ortamı yapılandırabilirsiniz.
Komutlar:
	• dspmqinst komutunu kullanarak kurulu sürümlerin bilgilerini görüntüleyebilirsiniz.
	• dspmqver komutuyla her iki kurulumun sürüm bilgisini kontrol edin.
Örnek:

dspmqinst
Bu komut, kurulu olan her iki IBM MQ sürümünü ve kurulum yollarını gösterir.
4. Kuyruk Yöneticisi Oluşturma
Yeni sürümü kullanarak bir kuyruk yöneticisi oluşturmak için crtmqm komutunu kullanabilirsiniz. Örneğin, QM930 adında bir kuyruk yöneticisi oluşturabilirsiniz.
Komut:

crtmqm QM930
Bu komut, QM930 adlı kuyruk yöneticisini oluşturur ve ilgili dizini oluşturur.
5. Kuyruk Yöneticisini Yeni Sürüme Geçirme
IBM MQ 9.4'te yeni bir kuyruk yöneticisini kullanmaya başlamak için, önce eski sürümdeki kuyruğu yeni sürüme taşımak gerekecektir.
Geçiş Adımları:
	1. Kuyruk Yöneticisinin Yedeğini Alın:

dmpmqcfg -m QMMIG -a > QMMIG.dmpmqcfg.out.all.mqsc
	2. Kuyruk Yöneticisini Eski Sürümden Yeni Sürüme Geçirin: setmqm komutunu kullanarak kuyruk yöneticisini yeni IBM MQ sürümüne ilişkilendirin:

setmqm -m QMMIG -n Installation2
	3. Kuyruk Yöneticisini Başlatın:

strmqm QMMIG
6. Fix Pack Yükleme
IBM MQ 9.4 için bir Fix Pack yüklemek, ürününüzü güncel tutmak için önemlidir. Yükleme şu adımları içerir:
	1. IBM MQ 9.4 için en son Fix Pack’i indirin.
	2. Fix Pack yüklemek için dosyayı çalıştırın ve yükleme sihirbazını takip edin.
Sonuç:
	• IBM MQ 9.4'ü eski sürümle aynı sistemde başarıyla kurdunuz ve yeni sürüme geçiş yaptınız.
	• Kuyruk Yöneticisi Migrasyonu başarıyla tamamladınız ve yeni sürüme geçiş için hazırlık yaptınız.
	• Fix Pack yükleme işlemini başarıyla gerçekleştirdiniz.
Bu adımlar sayesinde IBM MQ'nun farklı sürümleri arasında geçiş yapabilir ve yan yana kurulumlar ile yönetim kolaylıkları sağlayabilirsiniz.


MFT Yaygın Topolojileri
	• Tek bir kuyruk yöneticisi ile temel topoloji: Bu yapı, sadece bir kuyruk yöneticisi ile dosya transferi yapılandırması yapmanızı sağlar. Genellikle geliştirme aşamasında ya da sadece aynı sunucu üzerinde dosya taşımak için kullanılır.
	• Bir partner ajanı ile temel topoloji: Bu yapı, temel sunucu ve uzak bir partner sunucu arasındaki dosya transferini mümkün kılar.
	• Koordinasyon kuyruk yöneticisi ve bir partner ajanı ile temel topoloji: Bu yapıda, koordinasyon için ayrı bir kuyruk yöneticisi (örneğin MFT5) kullanılır ve temel sunucudaki başka bir kuyruk yöneticisi, ajan ve komut rolleri için kullanılır.
	• Bir MFT Ajanı partneri ile temel topoloji: Partner sunucu, IBM MQ sunucu yerine IBM MQ istemci bağlantısı kullanarak çalışır. Bu yapı, partnerin IBM MQ sunucusu olmadığında tercih edilir.
2. Temel Sunucunun Yapılandırılması
	• Koordinasyon Kuyruk Yöneticisi: Koordinasyon kuyruk yöneticisi (örneğin MFT5), dosya transferlerini yönetir.
		○ fteSetupCoordination komutunu çalıştırarak koordinasyon kuyruk yöneticisini yapılandırın.
		○ Koordinasyon kuyruk yöneticisinde gerekli IBM MQ tanımlarını oluşturmak için MQSC komut dosyasını çalıştırın.
	• Komut Kuyruk Yöneticisi: Komut kuyruk yöneticisi (örneğin MFT4), dosya transferlerine ilişkin komutları yönetir.
		○ fteSetupCommands komutunu çalıştırarak komut kuyruk yöneticisini yapılandırın.
	• Ajanın Yapılandırılması: Ajanlar, dosya transferlerini gerçekleştiren bileşenlerdir.
		○ fteCreateAgent komutunu kullanarak bir ajan oluşturun ve gerekli IBM MQ tanımlarını oluşturun.
		○ Ajanı fteStartAgent komutuyla başlatın ve fteListAgents komutuyla durumunu kontrol edin.
3. Logger (Kayıt Tutucu) Yapılandırması
	• Dosya transfer aktivitelerinin izlenmesi ve denetimi için bir logger (kayıt tutucu) gereklidir.
	• fteCreateLogger komutunu kullanarak dosya tabanlı bir logger oluşturun, dosya boyutu ve dosya sayısı parametrelerini belirleyin.
	• Logger'ı fteStartLogger komutuyla başlatın ve output0.log dosyasını kontrol ederek kayıtların yazıldığını doğrulayın.
4. Partner Sunucusunun Yapılandırılması
	• Partner Sunucu: Temel sunucunun koordinasyon kuyruk yöneticisi ayrı bir sunucuda ise, partner sunucu yapılandırılmalıdır.
	• Koordinasyon Kuyruk Yöneticisi Bağlantısı: Partner sunucusunun koordinasyon kuyruk yöneticisine bağlanması için fteSetupCoordination komutunu kullanın.
	• Komut Kuyruk Yöneticisi Bağlantısı: Partner sunucusundaki komut kuyruk yöneticisini fteSetupCommands komutuyla yapılandırın.
	• Partner Ajanının Yapılandırılması: Partner sunucusunda bir ajan oluşturun ve fteCreateAgent komutunu kullanarak IBM MQ tanımlarını oluşturun.
	• Ajanı fteStartAgent komutuyla başlatın ve fteListAgents komutuyla durumunu kontrol edin.
5. IBM MQ Explorer ile Test Yapılması
	• IBM MQ Explorer'ı Başlatma: IBM MQ Explorer'ı başlatın ve sol pencerede "Managed File Transfer" bölümüne gidin.
	• Koordinasyon Kuyruk Yöneticisine Bağlanma: Koordinasyon kuyruk yöneticisi MFT5’e sağ tıklayın ve "Connect" seçeneğini tıklayın.
	• Dosya Transferi Testi: Sağ tıklayıp "New Transfer" seçeneği ile dosya transferi başlatın. Kaynak ajanı (örneğin MFT4AGT1) ve hedef ajanı (örneğin CSMAGT1) seçin.
	• Transferin başarılı olup olmadığını kontrol edin. Eğer yeşil renkte başarı mesajı alırsanız, transfer başarılı olmuştur. Hata alırsanız, Transfer Log kısmından hata mesajlarını inceleyerek çözüm sağlayabilirsiniz.


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


BM MQ ve Apache Kafka'nın farklı alanlarda uzmanlaşan iki mesajlaşma teknolojisi olduğu için, aralarındaki veri akışını sağlamak sıklıkla gereklidir. Bu, Kafka Connect kullanılarak yapılabilir. Kafka Connect, veri akışını sağlamak için dış bir sistemle Kafka kümesi arasında veri taşıyan bir çerçevedir ve çeşitli bağlantılar kullanır.
IBM MQ ile Kafka arasında veri akışı sağlamak için kullanılan Kafka Connect'in iki türü vardır:
	1. Source Connectors: Dış bir sistemden Kafka'ya veri aktarır.
		○ IBM MQ Source Connector: IBM MQ kuyruğundan mesajları alır ve bunları Kafka konularına (topics) aktarır.
	2. Sink Connectors: Kafka'dan dış bir sisteme veri aktarır.
		○ IBM MQ Sink Connector: Kafka konularından veri alır ve bunları IBM MQ kuyruğuna iletir.
Kafka Connect Senaryoları
	• Core Bankacılık Sistemi: IBM MQ kullanılarak, banka işlemlerinin başarıyla tamamlanmasının ardından verilerin Kafka'ya aktarılması sağlanabilir.
	• Veri Analizi için MQ'dan Kafka'ya Veri Akışı: IBM MQ üzerinden hareket eden verilerin bir kopyasının Kafka'ya aktarılması gerekebilir, özellikle analiz amaçlı.
	• z/OS Entegrasyonu: Kafka ve z/OS sistemleri arasındaki veri akışını yönetmek, örneğin IBM MQ entegrasyonuyla.
MQ ile Kafka'nın Entegrasyonu İçin Topolojiler
	1. Direct to Queue (Source):
		○ Uygulamalar verilerini doğrudan Kafka'ya göndermek için IBM MQ kullanabilir. Bu durumda, veriler zaten IBM MQ'ya gönderilmektedir, bu nedenle Kafka'ya bağlantı kurmak yerine mevcut bir IBM MQ bağlantısı kullanılabilir.
	2. Streaming Queue Copy (Source):
		○ IBM MQ'ya gelen verilerin bir kopyasını Kafka'ya iletmek için Streaming Queue özelliği kullanılabilir. Bu, verinin bir kuyruğa yazılmasını sağlar ve aynı mesaj başka bir kuyruğa kopyalanır, bu da Kafka'ya veri akışını sağlar.
	3. Direct to Queue (Sink):
		○ Kafka'dan gelen verileri doğrudan IBM MQ kuyruğuna almak için sink connector kullanılabilir. Bu, Kafka'dan gelen verilerin, örneğin bir veritabanı güncellemesi gibi işlemlerle eş zamanlı olarak IBM MQ'ya gönderilmesini sağlar.
IBM MQ Kafka Connectors
IBM MQ 9.4.0'dan itibaren, IBM MQ Advanced, IBM MQ Advanced for z/OS ve IBM MQ Advanced for Multiplatforms ile bu bağlantılar kullanılabilir. Connectors, Kafka Connect ortamına dahil edilen çeşitli dosyalarla birlikte gelir ve yapılandırmalar, JSON veya properties dosyalarıyla yapılır.
	• IBM MQ Source Connector: IBM MQ kuyruğundan Kafka'ya veri aktaran bağlantıdır.
	• IBM MQ Sink Connector: Kafka'dan IBM MQ'ya veri aktarır.
Version 2 Connector Özellikleri
Version 2 connectors, exactly-once ve at-least-once mesaj teslimatı desteği sağlar:
	• At-least-once: Bir hata durumunda, mesajlar kaybolmaz ancak Kafka'ya birden fazla kez iletilir.
	• Exactly-once: Mesajlar yalnızca bir kez iletilir, hata durumunda tekrar gönderilmez.
Kafka Connectors ve Dosya Yapısı
Kafka Connect çalıştırılmadan önce aşağıdaki dosyaların classpath'te bulunması gerekir:
	• jms.jar
	• com.ibm.mq.allclient.jar
	• org.json.jar
	• bcpkix-jdk18on.jar
	• bcprov-jdk18on.jar
	• bcutil-jdk18on.jar
	• jackson-annotations.jar
	• jackson-core.jar
	• jackson-databind.jar
	• slf4j-api.jar (Maven üzerinden temin edilebilir)
z/OS ve IBM MQ
IBM MQ Connectors, z/OS üzerinde de çalıştırılabilir. z/OS UNIX System Services (USS) kullanarak performans iyileştirmeleri sağlanabilir ve yerel bağlantılarla kuyruğa bağlanma tercih edilebilir.
Sonuç
IBM MQ ile Apache Kafka arasındaki veri akışını yönetmek için Kafka Connect kullanabilirsiniz. Source ve Sink connector’ları ile MQ’dan Kafka’ya veya Kafka’dan MQ’ya veri aktarımı sağlayabilirsiniz. Kafka Connect'in sağladığı exactly-once teslimat desteği, kritik uygulamalarda veri doğruluğunu sağlar.
