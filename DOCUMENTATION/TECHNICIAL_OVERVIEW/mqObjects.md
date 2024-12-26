IBM MQ Nesneleri
IBM MQ'nun nesneleri, kuyruk yöneticileri tarafından tanımlanan özelliklere sahiptir. Bu özelliklerin değerleri, IBM MQ'nun bu nesneleri nasıl işlediğini etkiler. Nesneleri, IBM MQ komutları ve arabirimlerini kullanarak oluşturur ve yönetirsiniz. Uygulamalarınızda ise bu nesneleri kontrol etmek için Message Queue Interface (MQI) kullanılır. Nesneler, bir program tarafından erişildiğinde IBM MQ nesne tanımlayıcısı (MQOD) ile tanımlanır.
Nesne Yönetimi
Nesne yönetimi şu görevleri içerir:
	1. Kuyruk yöneticilerini başlatma ve durdurma.
	2. Uygulamalar için nesneler (özellikle kuyruklar) oluşturma.
	3. Nesnelerin özelliklerini görüntüleme veya değiştirme.
	4. Nesneleri silme.
	5. Diğer (uzak) sistemlerdeki kuyruk yöneticilerine iletişim yolları oluşturmak için kanallar ile çalışma.
	6. Kuyruk yöneticilerinden kümeler oluşturmak, bu sayede genel yönetim sürecini basitleştirmek ve iş yükünü dengelemek.
Dinamik kuyruklar hariç, nesnelerle çalışmaya başlamadan önce, bunlar kuyruk yöneticisine tanımlanmalıdır.
IBM MQ komutları ile nesne yönetimi yapıldığında, kuyruk yöneticisi gerekli yetkiye sahip olup olmadığınızı kontrol eder. Aynı şekilde, bir uygulama nesneyi açmak için MQOPEN çağrısını kullandığında, kuyruk yöneticisi uygulamanın nesneye erişim için gerekli yetkiye sahip olup olmadığını kontrol eder.
Nesneleri şu yöntemlerle tanımlayabilir ve yönetebilirsiniz:
	• PCF komutları (Programmable Command Format), otomatikleştirilmiş yönetim görevleri için kullanılır.
	• MQSC komutları (Message Queue Script Commands), IBM MQ'da nesneleri yönetmek için yaygın olarak kullanılır.
	• IBM MQ Explorer (Windows ve Linux® Intel sistemlerinde kullanılabilir), GUI tabanlı bir araçtır.
	• Control Commands ve IBM MQ Administration Interface (MQAI), programlar üzerinden de nesneleri yönetmeyi sağlar.
Nesne Özellikleri
Bir nesnenin özellikleri özellikler (attributes) tarafından tanımlanır. Bazı özellikleri belirleyebilirken, diğerleri sadece görüntülenebilir.
Örneğin, bir kuyruğun alabileceği maksimum mesaj uzunluğu, MaxMsgLength özelliğiyle tanımlanır; bu özellik kuyruk oluşturulurken belirlenebilir. DefinitionType özelliği, kuyruğun nasıl oluşturulduğunu belirtir; bu özellik yalnızca görüntülenebilir.
IBM MQ'da bir özelliğe şu şekilde atıfta bulunulabilir:
	• PCF adı kullanarak (örneğin MaxMsgLength).
	• MQSC komut adı kullanarak (örneğin MAXMSGL).
Kuyruk Paylaşım Grupları (Queue Sharing Groups)
Kuyruk paylaşım grubu (QSG), aynı kümeye ait olan ve aynı seti paylaşan kuyruk yöneticilerinin oluşturduğu bir gruptur. Bu kuyruk yöneticileri, bir coupling facility (CF) kullanarak birbirleriyle iletişim kurar ve paylaşılan kuyrukları depolar.
Bu kavram yalnızca IBM MQ for z/OS'da geçerlidir. QSG'ler, her biri için benzersiz bir ad taşır ve ağınızda başka bir kuyruk yöneticisinin adından farklı olmalıdır. Paylaşılan kuyruklar, birden fazla kuyruk yöneticisinin erişebileceği yerel kuyruklar olarak tanımlanır.
Sistem Varsayılan Nesneleri
Sistem varsayılan nesneleri, her kuyruk yöneticisi oluşturulduğunda otomatik olarak oluşturulan bir nesne tanımı setidir. Bu nesneleri kopyalayabilir ve kurulumunuzda uygulamalar için değiştirebilirsiniz.
Varsayılan nesne isimlerinin başında SYSTEM bulunur; örneğin, varsayılan yerel kuyruk SYSTEM.DEFAULT.LOCAL.QUEUE, varsayılan alıcı kanalı ise SYSTEM.DEF.RECEIVER'dır. Bu nesnelerin isimleri değiştirilemez.
Nesne Türleri
IBM MQ nesneleri ile ilgili yönetim görevleri, farklı nesne türlerinin manipülasyonunu içerir. Bu nesnelerin isimlendirme konvansiyonu, nesnenin türüne göre değişir. Ayrıca, kullanılan makinelerin ve kullanıcı kimliklerinin de bazı isimlendirme kısıtlamalarına tabi olduğunu unutmayın.
Not: Paylaşılan kuyruklar ve kuyruk paylaşım grupları yalnızca IBM MQ for z/OS'da desteklenir.



*************
IBM MQ Nesne Türleri
IBM MQ yönetim görevlerinin çoğu, çeşitli IBM MQ nesneleri ile çalışmayı içerir. Bu nesneler, farklı türlerdeki nesneleri kapsar ve her biri belirli işlevlere hizmet eder. Bu nesneleri anlamak, IBM MQ'nun verimli bir şekilde yönetilmesini ve kullanılması için çok önemlidir.
Kimlik Doğrulama Bilgisi Nesneleri
Kimlik doğrulama bilgisi nesneleri, sertifika iptal kontrolü yapmak için gerekli tanımlamaları sağlar. Bu nesneler, IBM MQ'nun Transport Layer Security (TLS) desteğinin bir parçasıdır. Sertifika yetkilileri, artık güvenilmeyen sertifikaları iptal eder ve bu nesne, iptal edilmiş sertifikaların kontrol edilmesi için gereklidir.
	• MQSC komutu: DEFINE AUTHINFO komutu ile kimlik doğrulama bilgisi nesnesi tanımlanabilir.
	• Kontrol komutları: setmqaut (yetki verme veya iptal etme), dspmqaut (yetki görüntüleme) gibi komutlarla bu nesnelerle işlem yapılabilir.
Kanallar
Kanallar, bir kuyruk yöneticisinden diğerine iletişim yolu sağlayan nesnelerdir. Kanallar, uygulamaların arka planda kullandığı iletişim protokollerinden soyutlanmasını sağlar. Her iki kuyruk yöneticisi arasında mesaj iletimini yönetir.
İletişim Bilgisi Nesneleri
İletişim bilgisi nesneleri (COMMINFO), IBM MQ Multicast için kullanılan nesnelerdir. Bu nesneler, düşük gecikmeli, yüksek yayılım (fan-out) ve güvenilir çoklu yayın mesajlaşma sağlamak için gereklidir.
Dinleyiciler (Listeners)
Dinleyiciler, diğer kuyruk yöneticilerinden veya istemci uygulamalarından gelen ağ isteklerini kabul eden süreçlerdir. Bu nesneler, kuyruk yöneticisi içindeki dinleyici süreçlerinin başlatılmasını ve durdurulmasını yönetir. runmqlsr komutu ile dinleyici süreçleri başlatılabilir.
Not: IBM MQ for z/OS'ta dinleyici nesneleri desteklenmemektedir. Z/OS üzerinde kanal başlatıcı kullanılarak dinleme işlemi yapılır.
Ad Listeleri (Namelists)
Ad listeleri, bir küme adı, kuyruk adı veya kimlik doğrulama bilgisi nesne adı listesi içeren nesnelerdir. Uygulamalar, ad listelerini, özellikle tetikleyici izleyiciler gibi, birçok kuyruğu tanımlamak için kullanır. Ad listeleri, uygulamalardan bağımsız olarak güncellenebilir ve bir uygulama başarısız olsa bile diğer uygulamalar bu ad listelerini kullanmaya devam edebilir.
Süreç Tanımları (Process Definitions)
Süreç tanımları, bir kuyruk yöneticisi tarafından tetiklenen uygulamaların başlatılmasını sağlar. Süreç tanımı nesnesi, uygulamanın başlatılmasında kullanılan uygulama ID'si, uygulama türü ve uygulamaya özgü verileri içerir.
	• Süreçler, tetikleyiciler aracılığıyla başlatılabilir. Bu tür başlatmalar, operatör müdahalesi olmadan gerçekleşir.
Kuyruklar (Queues)
Kuyruklar, mesajların gönderildiği ve alındığı adlandırılmış nesnelerdir. Her kuyruk bir kuyruk yöneticisi tarafından yönetilir. Uygulamalar, mesajları bir kuyruğa koyar ve bu mesajlar daha sonra başka bir uygulama tarafından alınır.
Kuyruk Yöneticileri (Queue Managers)
Kuyruk yöneticileri, kuyruklar ve bunlara ait kuyruklama hizmetlerini yöneten programlardır. Kuyruk yöneticileri, her kuyruk yöneticisinin sahip olduğu kuyruğun yönetimini üstlenir ve mesajların güvenli bir şekilde iletilmesini sağlar.
Hizmetler (Services)
Hizmetler, bir kuyruk yöneticisi başlatıldığında veya durdurulduğunda çalıştırılacak programları tanımlar. Bu hizmetler, genellikle kısa süreli görevleri yerine getiren programları içerir. Örneğin, server ve command türleri vardır:
	• Server: Kuyruk yöneticisi başlatıldığında çalışacak bir programı tanımlar.
	• Command: Kuyruk yöneticisi başlatıldığında çalışacak kısa süreli bir programı tanımlar.
Not: IBM MQ for z/OS'ta hizmet nesneleri desteklenmemektedir.
Depolama Sınıfları (Storage Classes)
Depolama sınıfları, bir veya daha fazla kuyruğun belirli bir page set'e (sayfa kümesi) eşlenmesini sağlar. Bu, mesajların bu sayfa kümesinde depolanmasını sağlar.
Not: Depolama sınıfları yalnızca IBM MQ for z/OS'ta desteklenir.
Konu Nesneleri (Topic Objects)
Konu nesneleri, publish/subscribe messaging modelinde kullanılan nesnelerdir. Bir konu, mesajların yayımlandığı veya abone olunan bir konu dizisini belirtir. Konular, genellikle bir konu ağacı şeklinde hiyerarşik olarak organize edilir.
	• TopicString özelliği ile her konu dizisi tanımlanabilir. Mesajlar, bu konularda abone olan tüm uygulamalara iletilir.
	• Konu nesneleri, konu dizisini gizleyerek, uygulamaların yalnızca konu nesnesine abone olmalarını sağlar.

*********************
IBM MQ Kuyrukları
IBM MQ'da kuyruklar, mesajların saklandığı ve uygulamaların bu mesajlara erişebildiği temel yapıdır. Bir kuyruk, bir queue manager (kuyruk yöneticisi) tarafından yönetilir ve bu yöneticinin birden fazla kuyruğa sahip olabileceği gibi, her kuyruk yöneticisi altındaki kuyruklar benzersiz bir isimle tanımlanır. Kuyruklar, mesajları depolarak, gönderen ve alan uygulamalar arasında zaman bağımsız iletişim sağlar.
Kuyruklar ve Mesajlar
Mesajlar, bir uygulama tarafından bir kuyruğa konur ve başka bir uygulama tarafından o kuyruğa erişilerek alınır. Kuyruğa mesaj koymadan önce, kuyruk zaten tanımlanmış olmalıdır. Bu işlem için Message Queue Interface (MQI) kullanılır. MQI, kuyruklara mesaj koyma, mesaj alma gibi işlemleri gerçekleştiren arayüzdür.
Kuyruk Yönetimi
Kuyrukları yönetmek için, IBM MQ çeşitli komutlar (MQSC, PCF komutları) ve platforma özel arayüzler sunar. Örneğin, IBM MQ için z/OS üzerinde özel kontrol panelleri bulunur.
Kuyruk Tanımlama: Bir kuyruk tanımlarken, aşağıdaki gibi bazı özellikleri belirlemek gereklidir:
	• Kuyruğa mesaj koyma ve alma izinleri
	• Kuyruk için belirlenen maksimum mesaj sayısı
	• Kuyruğa mesaj koyarken uygulanacak öncelikler veya kalıcılık
Kuyruk, kuyruk yöneticisi tarafından yönetilir ve genellikle kuyruk yöneticisi, kuyrukları saklar ve yönetir.
Kuyruk Türleri
	1. Yerel Kuyruklar (Local Queues): Yerel kuyruklar, IBM MQ'da en yaygın kullanılan kuyruk türüdür. Bu tür kuyruklar, bir uygulamanın mesajlarını saklamak için kullanılır.
		○ Transmission Queues: Mesaj iletimi için kullanılan kuyruklar.
		○ Initiation Queues: Tetikleyici işlemlerini başlatan kuyruklar.
		○ Dead-letter Queues: Teslim edilemeyen mesajların tutulduğu kuyruklar.
		○ Command Queues: Yönetim komutlarının bulunduğu kuyruklar.
	2. Uzak Kuyruklar (Remote Queues): Uzak kuyruklar, bir programın bağlı olduğu kuyruk yöneticisinden farklı bir kuyruk yöneticisi tarafından sahip olunan kuyruklardır. Yani, bir program başka bir sistemdeki kuyruğa erişim sağladığında, bu kuyruk uzak bir kuyruktur.
	3. Alias Kuyrukları (Alias Queues): Alias kuyrukları, bir kuyruk veya konuya (topic) erişmek için kullanılan nesnelerdir. Bu, birden fazla programın aynı kuyruğa farklı isimlerle erişmesini sağlar.
	4. Dinamik Kuyruklar (Dynamic Queues): Dinamik kuyruklar, uygulama tarafından ihtiyaç duyulduğunda dinamik olarak oluşturulabilen kuyruklardır. Bu tür kuyruklar genellikle geçici işler için kullanılır. Dinamik kuyruklar, model kuyruklardan türetilir ve geçici ya da kalıcı olabilir.
		○ Model Kuyruklar (Model Queues): Dinamik kuyruklar oluşturulurken bir şablon olarak kullanılan kuyruklardır. Model kuyruklardan alınan özellikler, dinamik kuyruklara aktarılır.
Kuyruk Özellikleri
Bir kuyruk, aşağıdaki gibi çeşitli özelliklere sahiptir:
	• QName: Kuyruğun adı
	• QType: Kuyruğun türü (Yerel, Uzak vb.)
	• QDesc: Kuyruğun açıklama metni
	• InhibitGet: Programların kuyruktan mesaj alıp almadığını kontrol eder.
	• InhibitPut: Programların kuyruğa mesaj koyup koyamayacağını belirler.
	• DefPriority: Kuyruğa konacak mesajların varsayılan önceliği
	• DefPersistence: Kuyruğa konan mesajların varsayılan kalıcılığı
	• Scope: Kuyruğun bir ad servisinde yer alıp almadığını kontrol eder.
Kuyruklara Mesaj Gönderme ve Alma
Uygulamalar, MQI kullanarak kuyruklara mesaj gönderir ve alır. Kuyruğa bir mesaj koymak için, bir uygulama MQOPEN komutu ile kuyruğu açar, ardından MQPUT komutu ile mesajı kuyruğa koyar. Başka bir uygulama ise, MQGET komutu ile bu mesajı alır.


*******
Yerel Kuyruklar (Local Queues)
Yerel kuyruklar, uygulamanın bağlandığı queue manager tarafından sahip olunan ve yönetilen kuyruklardır. Bu kuyruklar, bir programın mesaj gönderip alabileceği temel yapılardır. IBM MQ'da, yerel kuyruklar şunlarla ilgili özel türler içerir:
Yerel Kuyruk Türleri:
	1. Transmission Queues (İletim Kuyrukları):
		○ İletim kuyrukları, mesajların bir remote queue manager'a gönderileceği kuyruklardır. Mesajlar bu kuyruklarda bekler ve doğru yer hedefe ulaştırıldığında silinir.
		○ Bir Message Channel Agent (MCA), iletim kuyruğunda bekleyen mesajı alır ve bir sonraki hedefe iletmek üzere gönderir.
		○ Örneğin, büyük mesajlar için ayrı iletim kuyrukları tanımlanabilir ve böylece küçük mesajlar büyük mesajlardan önce iletilir.
		○ Cluster iletim kuyrukları SYSTEM.CLUSTER.TRANSMIT.QUEUE adıyla varsayılan olarak tanımlanır. Fakat, farklı kuyruklar kullanarak mesaj trafiğini ayırmak mümkündür.
	2. Initiation Queues (Başlatma Kuyrukları):
		○ Başlatma kuyrukları, tetikleme olaylarını izler ve bir olay meydana geldiğinde belirli bir programın çalışmasını başlatır.
		○ Tetikleme olayı, örneğin belirli sayıda mesajın kuyrukta birikmesi gibi durumları kapsar. Bu tür bir işlem triggering olarak adlandırılır ve daha fazla bilgi için IBM MQ uygulamalarını başlatma kısmına göz atılabilir.
	3. Dead-letter (Undelivered Message) Queues (Ölü Mesaj Kuyruğu):
		○ Eğer bir mesaj teslim edilemezse, bu mesajlar dead-letter queue'ya gönderilir.
		○ Bu kuyruk, teslim edilemeyen mesajları saklar ve her mesajın üzerine bir başlık eklenir. Başlık, mesajın neden teslim edilemediğini ve orijinal hedefi gibi bilgileri içerir.
	4. System Command Queues (Sistem Komut Kuyrukları):
		○ Bu kuyruklar, belirli yetkilere sahip uygulamaların IBM MQ komutlarını gönderdiği kuyruklardır.
		○ Uygulamalar bu kuyruklara PCF, MQSC, ve CL komutlarını gönderir, böylece queue manager bu komutları işler.
		○ IBM MQ for z/OS'ta bu kuyruk SYSTEM.COMMAND.INPUT olarak adlandırılır, diğer platformlarda ise SYSTEM.ADMIN.COMMAND.QUEUE olarak adlandırılır.
	5. Event Queues (Olay Kuyrukları):
		○ Olay kuyrukları, queue manager veya bir kanal tarafından bildirilen olay mesajlarını tutar.
		○ Bu tür kuyruklar, sistemdeki önemli olayları izlemek ve raporlamak için kullanılır.
Kuyrukların Tanımlanması
	• Yerel kuyruklar, queue manager tarafından yönetilir ve tanımlanır. Tanımlama işlemleri için MQSC komutları, PCF komutları ve platforma özel arayüzler kullanılabilir.
	• Yerel kuyruklar, belirli bir işlem için geçici olarak oluşturulabilir veya kalıcı olarak tanımlanabilir.
Kuyruk Özellikleri
Kuyrukların belirli özellikleri vardır, bunlar:
	• QName: Kuyruğun adı
	• QType: Kuyruğun türü
	• QDesc: Kuyruğun açıklaması
	• InhibitPut: Kuyruğa mesaj koyma izni verilip verilmediğini kontrol eder.
	• InhibitGet: Kuyruğa mesaj alma izni verilip verilmediğini kontrol eder.
	• DefPriority: Mesajların varsayılan önceliği
	• DefPersistence: Mesajların varsayılan kalıcılığı
Dinamik ve Model Kuyruklar
	• Dinamik Kuyruklar: Uygulama tarafından otomatik olarak oluşturulan geçici kuyruklardır.
	• Model Kuyruklar: Dinamik kuyrukların oluşturulmasında şablon olarak kullanılan kuyruklardır.
Özet
Yerel kuyruklar, IBM MQ'daki mesaj iletimi ve yönetim için temel bir bileşendir. Uygulamalar arasındaki mesaj iletimi, bu kuyruklar aracılığıyla yapılır ve her kuyruk, belirli işlevlere göre özelleştirilebilir.

*****
Remote Kuyruklar (Remote Queues)
Remote kuyruklar, bir programın bağlı olduğu queue manager'dan farklı bir queue manager tarafından sahip olunan kuyruklardır. Bu tür kuyruklar, genellikle iki farklı sistem arasındaki iletişimi sağlamak için kullanılır.
Remote Kuyruğa Mesaj Göndermek:
	• Bir program, bir iletişim bağlantısı kurulduğu takdirde, remote queue'ya mesaj gönderebilir.
	• Remote queue'dan mesaj almak mümkün değildir; bir program sadece bu kuyruktan mesaj gönderir, almaz.
Yerel Tanımlama:
	• Remote queue'ya mesaj gönderirken, yerel queue manager'ın mesajı göndereceği hedef kuyruk hakkında bilgi sahibi olması gerekir. Bu bilgi, remote queue'nun yerel tanımında saklanır.
	• Remote queue'nun tüm özellikleri, o kuyrukla ilişkilendirilmiş olan queue manager tarafından tutulur, çünkü o queue manager için bu kuyruk yerel bir kuyruktur.
	• Yerel tanımda yalnızca gerekli yönlendirme bilgileri bulunur: yani remote queue'nun adı, remote queue manager'ın adı ve mesajların iletileceği iletim kuyruğu (transmission queue).
Yerel Tanım Özellikleri:
Yerel tanımlama için kullanılan remote queue'nun 3 ek özelliği vardır:
	1. RemoteQName: Remote queue'yu sahiplenen queue manager tarafından bilinen isim.
	2. RemoteQMgrName: Remote queue'yu sahiplenen queue manager'ın adı.
	3. XmitQName: Mesajları diğer queue manager'lara iletmek için kullanılan yerel iletim kuyruğunun adı.
Remote Queue Oluşturma:
Bir remote queue oluşturmak için, yerel tanımını yapmak gerekir:
	• MQSC komutu (DEFINE QREMOTE) veya IBM i için CRTMQMQ komutu kullanılır.
	• Bu komutlar, yerel tanımı oluştururken, remote queue manager'a ve ona ait kuyruk adı bilgilerine yönlendirir.
Kuyruğa Erişim:
Bir remote queue'yu açarken, tanımlanan local definition (yerel tanım) kullanılır:
	• Uygulama, bir remote queue'yu açarken, bu kuyruk için yerel tanımı kullanır ve bu işlem, yerel kuyruk açmak gibi çalışır. Yani, uygulamanın remote veya local kuyruklar arasında fark yapması gerekmez.
MQINQ Çağrısı:
	• MQINQ çağrısı kullanılarak, remote queue'nun yerel tanımının özellikleri alınabilir. Ancak, bu çağrı sadece yerel tanımın özelliklerini döndürecektir, remote queue'nun kendisiyle ilgili bilgileri vermez.
Özet:
Remote queue'lar, mesajların farklı queue manager'lar arasında yönlendirilmesi için kullanılan kuyruklardır. Bu kuyruklar, yerel tanımlarla yönetilir ve iletim işlemleri için özel kuyruklar kullanılır.



**************
Alias Kuyruklar (Alias Queues)
Alias kuyrukları, bir IBM® MQ nesnesidir ve başka bir kuyruk veya konuyu (topic) erişilebilir kılmak için kullanılır. Bu sayede, aynı kuyruk birden fazla program tarafından farklı isimlerle kullanılabilir.
Alias Kuyruğunun Temel Özellikleri:
	• Alias kuyrukları, çözümleme işlemiyle bir base queue'ya (temel kuyruk) yönlendirilir. Bu base queue şunlardan biri olabilir:
		○ Yerel kuyruk (Local Queue)
		○ Remote queue'nun yerel tanımı (Local definition of remote queue)
		○ Shared queue (yalnızca IBM MQ for z/OS®'da bulunan yerel kuyruk türü)
		○ Önceden tanımlanmış kuyruk (Predefined Queue)
		○ Dinamik kuyruk (Dynamic Queue)
	• Bir alias queue, aynı zamanda bir konuyu (topic) da çözümleyebilir. Eğer bir uygulama, şu anda mesajları bir kuyruk üzerine koyuyorsa, kuyruk ismi bir alias ile bir konuya (topic) yönlendirilebilir. Böylece uygulama kodunda herhangi bir değişiklik yapmadan, kuyruk yerine konuya mesaj gönderilebilir.
Alias Kuyruklarının Kullanım Amaçları:
	1. Erişim Yetkileri Yönetimi:
		○ Alias kuyrukları, bir sistem yöneticisinin, base queue ile alias kuyruk ismi için farklı erişim yetkileri tanımlamasına olanak sağlar. Bu sayede bir program veya kullanıcı, alias kuyruk ismini kullanmaya yetkilendirilebilir, ancak base queue'yu kullanmaya yetkili olmayabilir.
	2. Put Operasyonları Üzerinde Kontrol:
		○ Alias kuyrukları, "put" işlemleri üzerinde kontrol sağlayabilir. Örneğin, alias kuyruk için put işlemi engellenebilir, ancak aynı base queue üzerinde put işlemleri yapılabilir.
	3. Kolay Değişim ve Yönetim:
		○ Alias kuyrukları, sistem yöneticilerinin alias queue nesnesinin tanımını değiştirmesini kolaylaştırır. Uygulamanın değiştirilmesine gerek kalmaz; sadece alias kuyruk tanımı değiştirilir.
Alias Kuyruklarının Özellikleri:
	• BaseQName: Alias kuyruğunun temel kuyruğa (base queue) yönlendirilmiş olduğu ismi belirten özellik.
	• InhibitGet ve InhibitPut: Alias kuyrukları, yalnızca alias adı için geçerlidir. Örneğin, alias kuyruk ismi ALIAS1'in BASE kuyruk ismine yönlendirilmesi durumunda, ALIAS1 üzerindeki engellemeler yalnızca ALIAS1'i etkiler, BASE'i etkilemez. Ancak, BASE üzerinde engellemeler varsa, ALIAS1'i de etkiler.
	• DefPriority ve DefPersistence: Alias kuyrukları, kendi öncelik (priority) ve süreklilik (persistence) ayarlarına sahip olabilir. Bu özellikler, aynı temel kuyruk için farklı alias kuyrukları üzerinden değiştirilebilir. Ayrıca, alias kuyruklarının bu özelliklerini değiştirmek, uygulama kodunda herhangi bir değişiklik yapılmasını gerektirmez.
Önemli Not:
	• Alias kuyrukları, doğrudan başka bir alias'a çözümleme yapamaz. Bir alias yalnızca bir base queue'ya veya bir konuya (topic) yönlendirilir.


*****************
Dinamik Kuyruklar (Dynamic Queues) ve Model Kuyruklar (Model Queues)
Dinamik Kuyruklar (Dynamic Queues)
Dinamik kuyruklar, uygulama tarafından oluşturulan ve model kuyrukları kullanarak tanımlanan geçici veya kalıcı kuyruğulardır. Uygulama, MQOPEN çağrısını yaparak bir model kuyruk açar ve queue manager (kuyruk yöneticisi) bu model kuyruktan türetilmiş yeni bir kuyruk oluşturur. Dinamik kuyruklar, özellikle uygulamanın sona erdikten sonra kuyruğun saklanmasına gerek olmadığı durumlarda kullanılır.
Geçici Dinamik Kuyruklar (Temporary Dynamic Queues)
	• Geçici dinamik kuyruklar yalnızca geçici mesajları tutar ve bu mesajlar kalıcı değildir.
	• Kuyruk geri alınamaz (unrecoverable) ve sadece uygulama kapatıldığında veya queue manager başlatıldığında silinir.
	• Geçici kuyruklar, uygulama tarafından açıldığı anda veya kapandığında silinir. Eğer kuyrukta henüz onaylanmamış (committed) mesajlar varsa, kuyruk "mantıksal olarak silindi" (logically deleted) olarak işaretlenir.
	• Mantıksal olarak silinen bir kuyruk üzerine başka bir işlem yapılmaya çalışılırsa, MQRC_Q_DELETED hata kodu döner.
Kalıcı Dinamik Kuyruklar (Permanent Dynamic Queues)
	• Kalıcı dinamik kuyruklar hem kalıcı hem de geçici mesajları tutabilir.
	• Sistem arızaları durumunda geri alınabilirler (recoverable).
	• Bir uygulama, bu kuyruğu başarıyla kapattığında, kalıcı kuyruk silinir.
	• Kuyruk, silinmeye çalışıldığında eğer üzerinde mesaj varsa, bir MQCO_DELETE veya MQCO_DELETE_PURGE seçeneği kullanılır. MQCO_DELETE_PURGE ile, kuyruğun üzerindeki tüm mesajlar silinir.
Dinamik Kuyrukların Kullanım Alanları
	• Dinamik kuyruklar, uygulama sonlandığında kuyruğun korunmasına gerek olmayan durumlarda kullanılır.
	• Özellikle cevap bekleyen uygulamalarda, dinamik bir cevap kuyruğu oluşturulabilir. Örneğin:
		1. Bir istemci uygulaması, dinamik bir kuyruk oluşturur.
		2. Bu kuyruğun ismini ReplyToQ alanında belirterek, bir istek mesajı gönderir.
		3. Sunucu uygulaması ise cevabı bu kuyruğa gönderir.
Dinamik Kuyruklar Kullanılırken Dikkat Edilmesi Gereken Hususlar
	• İstemci-sunucu modelinde, her istemci kendi dinamik cevap kuyruğunu oluşturmalı ve paylaşmamalıdır.
	• Kuyruk, diğer bir kullanıcı tarafından kullanıldığında, silinme işlemi ertelenebilir veya kuyruk mantıksal olarak silinir ve sonraki API çağrıları tarafından erişilemez hale gelir.
Model Kuyruklar (Model Queues)
Model kuyruklar, dinamik kuyruklar oluşturmak için kullanılan bir kuyruk şablonudur. Model kuyruk, dinamik kuyruğun özelliklerini belirler. Uygulama, model kuyruk ismini kullanarak yeni bir dinamik kuyruk oluşturabilir. Model kuyrukları şunları sağlar:
	• Kuyruk türü: Geçici veya kalıcı dinamik kuyruk oluşturulabilir.
	• Adlandırma: Dinamik kuyruk için bir isim belirlemek veya adın bir kısmını kullanıp, gerisini otomatik olarak queue manager'a bırakmak mümkündür.
Model Kuyruğun Özellikleri
	• MQOD (Object Descriptor) ile bir model kuyruk açılır ve model kuyruk özellikleriyle yeni bir kuyruk dinamik olarak oluşturulur.
	• Model kuyruklara doğrudan mesaj (MQPUT1) gönderilemez, ancak model kuyruk kullanılarak oluşturulan dinamik kuyruklara mesaj gönderilebilir.
	• MQSET ve MQINQ komutları model kuyruklar üzerinde çalışmaz. Model kuyruk açıldığında, sonrasında yapılan MQINQ ve MQSET komutları dinamik olarak oluşturulan kuyruk üzerinden çalışır.
	• Model kuyruklar, yerel kuyrukların bir alt kümesini içerir.
Özetle:
	• Dinamik kuyruklar, uygulama tarafından dinamik olarak oluşturulabilen, geçici veya kalıcı kuyruklar olup, uygulamanın ihtiyaçlarına göre özelleştirilebilir.
	• Model kuyruklar, dinamik kuyrukların oluşturulması için kullanılan şablonlardır ve kuyruk oluşturulmadan önce özelliklerini belirler.

*******************
IBM MQ Tarafından Belirli Amaçlarla Kullanılan Kuyruklar
IBM MQ, bazı yerel kuyrukları, sistem işleyişiyle ilgili belirli amaçlarla kullanır. Bu kuyruklar, genellikle sistemin düzgün çalışmasını sağlamak ve bazı özel işlevleri yerine getirmek için gereklidir. Bu kuyruklar, IBM MQ tarafından kullanılmadan önce tanımlanmalıdır.
Başlatma Kuyrukları (Initiation Queues)
Başlatma kuyrukları, tetikleme işlemleri için kullanılır. Bir tetikleme olayı meydana geldiğinde, kuyruk yöneticisi başlatma kuyruğuna bir tetikleme mesajı ekler. Bu olaylar, bir kuyruğun derinliğinin önceden tanımlanmış bir değeri aşması gibi durumları içerebilir. Tetikleme mesajı, başlatma kuyruğunda bekleyen bir tetikleme izleyicisi (trigger monitor) tarafından alınır ve ardından ilgili uygulama başlatılır.
	• Başlatma kuyruğu olmadan tetikleme yapılamaz.
İletim Kuyrukları (Transmission Queues)
İletim kuyrukları, mesajların uzak bir kuyruk yöneticisine iletilmeden önce geçici olarak saklandığı kuyruklardır. Her uzak kuyruk yöneticisine mesaj gönderileceği zaman en az bir iletim kuyruğu tanımlanmalıdır.
	• İletim kuyrukları, mesajları diğer kuyruk yöneticilerine iletmek için kullanılır.
	• Bir küme (cluster) içinde, iletim kuyruğunun adı SYSTEM.CLUSTER.TRANSMIT.QUEUE olarak belirlenir. Her kuyruk yöneticisinin bu kuyruk için bir model iletim kuyruğu (SYSTEM.CLUSTER.TRANSMIT.MODEL.QUEUE) vardır.
Ölü Mesaj Kuyrukları (Dead-letter Queues)
Ölü mesaj kuyrukları, doğru hedeflerine yönlendirilemeyen mesajları saklar. Mesajlar, hedef kuyruk dolu olduğunda veya başka bir sorun nedeniyle yönlendirilemediğinde ölü mesaj kuyruğuna yönlendirilir.
	• Bu kuyruk, SYSTEM.DEAD.LETTER.QUEUE olarak bilinir.
Komut Kuyrukları (Command Queues)
Komut kuyruğu, yetkili uygulamaların MQSC komutlarını kuyruk yöneticisine gönderebildiği yerel bir kuyruktur. Gönderilen komutlar, komut sunucusu (command server) tarafından işlenir.
	• Komutlar, komut sunucusu tarafından doğrulanır ve geçerli olanlar, kuyruk yöneticisi tarafından işlenmek üzere iletilir.
Yanıt Kuyrukları (Reply-to Queues)
Bir uygulama bir istek mesajı gönderdiğinde, bu mesaja yanıt gönderecek olan uygulama yanıt mesajını gönderen uygulamaya yanıt kuyruğu üzerinden iletir.
	• Yanıt kuyruğu, genellikle gönderici uygulamaya yerel bir kuyruk olarak tanımlanır ve istek mesajının başlık bilgisinde belirtilir.
Olay Kuyrukları (Event Queues)
Olay kuyrukları, kuyruk yöneticilerinin bağımsız bir şekilde izlenebilmesini sağlar. Bir olay meydana geldiğinde, kuyruk yöneticisi bu olayla ilgili mesajı bir olay kuyruğuna koyar.
	• Bu mesajlar, izleme uygulamaları tarafından okunabilir ve bir problem oluştuğunda yöneticilere bildirimde bulunabilir veya düzeltici işlem başlatabilir.
Özetle:
	• Başlatma Kuyrukları, tetikleme olayları için kullanılır ve uygulamaların başlatılmasını sağlar.
	• İletim Kuyrukları, uzak kuyruk yöneticilerine mesaj göndermek için kullanılır.
	• Ölü Mesaj Kuyrukları, iletilemeyen mesajları saklar.
	• Komut Kuyrukları, uygulamaların MQSC komutlarını kuyruk yöneticisine göndermesini sağlar.
	• Yanıt Kuyrukları, istek mesajlarına yanıt gönderir.
	• Olay Kuyrukları, kuyruk yöneticisi tarafından üretilen olayları izlemek için kullanılır.
Bu kuyruklar, IBM MQ'nun düzgün çalışması için önemli işlevler sağlar ve her biri farklı amaçlarla kullanılır.

************
IBM MQ Kuyruk Yöneticileri (Queue Managers)
IBM MQ kuyruğu yöneticisi, bir programın mesaj kuyruğu hizmetlerini kullanabilmesi için gerekli olan yönetici bileşenidir. Her program, bir kuyruk yöneticisi ile bağlantı kurarak bu yönetici üzerinden kuyruk hizmetlerinden yararlanabilir. Bu bağlantı, program tarafından açıkça yapılabilir (örneğin, MQCONN veya MQCONNX çağrıları ile) ya da platform ve ortam koşullarına bağlı olarak dolaylı yoldan gerçekleşebilir.
Bir IBM MQ kuyruk yöneticisi, şu işlemleri sağlar:
	1. Nesne özelliklerini değiştirme: Kuyruk yöneticisi, aldığı komutlara göre nesne özelliklerini değiştirir.
	2. Olayların üretilmesi: Tetikleme olayları veya enstrümantasyon olayları gibi özel olaylar, uygun koşullar gerçekleştiğinde üretilir.
	3. Mesajların doğru kuyruğa yerleştirilmesi: Uygulamanın MQPUT çağrısı ile belirttiği kuyruğa mesajlar eklenir. Eğer bu mümkün olursa, uygulama bilgilendirilir ve uygun bir neden kodu sağlanır.
Kuyruk Yöneticisi ve Kuyruk Türleri
	• Yerel Kuyruk (Local Queue): Bir kuyruk, ait olduğu kuyruk yöneticisi için yerel bir kuyruktur. Bir uygulama, bağlandığı kuyruk yöneticisine ait kuyrukları yerel kuyruk olarak görür.
	• Uzak Kuyruk (Remote Queue): Bir uzak kuyruk, başka bir kuyruk yöneticisinin kontrolündeki kuyruktur. Uzak kuyruklar, yerel kuyruk yöneticisinden farklı bir kuyruk yöneticisinin olduğu bir ortamda bulunabilir.
IBM MQ, birden fazla kuyruk yöneticisinin aynı makinada çalışmasına izin verir.
Kuyruk Yöneticisi Nesnesi ve Özellikleri
Her kuyruk yöneticisinin, kimliğini belirleyen bir dizi özellik (veya parametre) vardır. Bazı özellikler, kuyruk yöneticisi oluşturulurken sabittir, ancak bazıları sonradan değiştirilebilir. Kuyruk yöneticisinin tüm özelliklerinin değerleri, MQINQ çağrısı ile sorgulanabilir.
Sabit Özellikler:
	• Kuyruk yöneticisinin adı
	• Kuyruk yöneticisinin çalıştığı platform (örneğin, Windows)
	• Kuyruk yöneticisinin desteklediği sistem kontrol komutları düzeyi
	• Kuyruk yöneticisinin mesaj önceliği sınırı
	• Uygulamalara MQ komutlarını gönderebilecek kuyruk adı
	• Kuyruk yöneticisinin işleyebileceği maksimum mesaj uzunluğu
	• Kuyruk yöneticisinin programlar tarafından yapılan PUT ve GET işlemlerinde syncpointing desteği
Değiştirilebilir Özellikler:
	• Kuyruk yöneticisinin açıklama metni
	• Kuyruk yöneticisinin karakter seti tanımlayıcıları
	• Kuyruk yöneticisinin tetikleme mesajları için zaman aralığı
	• Kuyruk yöneticisinin mesaj zaman aşımına uğramış mesajları tarama aralığı (IBM MQ for z/OS)
	• Kuyruk yöneticisinin ölü mesajlar için varsayılan kuyruk adı
	• Kuyruk yöneticisinin varsayılan iletim kuyruğu adı
	• Bağlantı başına açık tutulan maksimum işlem tutamağı sayısı
	• Olay raporlamalarının etkinleştirilmesi ve devre dışı bırakılması
	• İşlem birimi içinde açık tutulabilecek maksimum sayıda onaylanmamış mesaj
Kuyruk Yöneticileri ve Yük Dengeleme
IBM MQ, kuyruk yöneticilerini bir kümeye dahil ederek aynı kuyruğun birden fazla tanımını kullanabilir. Bu kümeye dahil edilen kuyruk yöneticileri arasında yük dengelemesi yapılır. Kuyruğa ait mesajlar, kuyruk yöneticisinin yük dengeleme algoritmasına göre, kuyruk yöneticilerine dağılır ve bu sayede sistemdeki yük dağıtılır.

*************
IBM MQ Kuyruk Yöneticileri (Queue Managers)
IBM MQ kuyruğu yöneticisi, bir programın mesaj kuyruğu hizmetlerini kullanabilmesi için gerekli olan yönetici bileşenidir. Her program, bir kuyruk yöneticisi ile bağlantı kurarak bu yönetici üzerinden kuyruk hizmetlerinden yararlanabilir. Bu bağlantı, program tarafından açıkça yapılabilir (örneğin, MQCONN veya MQCONNX çağrıları ile) ya da platform ve ortam koşullarına bağlı olarak dolaylı yoldan gerçekleşebilir.
Bir IBM MQ kuyruk yöneticisi, şu işlemleri sağlar:
	1. Nesne özelliklerini değiştirme: Kuyruk yöneticisi, aldığı komutlara göre nesne özelliklerini değiştirir.
	2. Olayların üretilmesi: Tetikleme olayları veya enstrümantasyon olayları gibi özel olaylar, uygun koşullar gerçekleştiğinde üretilir.
	3. Mesajların doğru kuyruğa yerleştirilmesi: Uygulamanın MQPUT çağrısı ile belirttiği kuyruğa mesajlar eklenir. Eğer bu mümkün olursa, uygulama bilgilendirilir ve uygun bir neden kodu sağlanır.
Kuyruk Yöneticisi ve Kuyruk Türleri
	• Yerel Kuyruk (Local Queue): Bir kuyruk, ait olduğu kuyruk yöneticisi için yerel bir kuyruktur. Bir uygulama, bağlandığı kuyruk yöneticisine ait kuyrukları yerel kuyruk olarak görür.
	• Uzak Kuyruk (Remote Queue): Bir uzak kuyruk, başka bir kuyruk yöneticisinin kontrolündeki kuyruktur. Uzak kuyruklar, yerel kuyruk yöneticisinden farklı bir kuyruk yöneticisinin olduğu bir ortamda bulunabilir.
IBM MQ, birden fazla kuyruk yöneticisinin aynı makinada çalışmasına izin verir.
Kuyruk Yöneticisi Nesnesi ve Özellikleri
Her kuyruk yöneticisinin, kimliğini belirleyen bir dizi özellik (veya parametre) vardır. Bazı özellikler, kuyruk yöneticisi oluşturulurken sabittir, ancak bazıları sonradan değiştirilebilir. Kuyruk yöneticisinin tüm özelliklerinin değerleri, MQINQ çağrısı ile sorgulanabilir.
Sabit Özellikler:
	• Kuyruk yöneticisinin adı
	• Kuyruk yöneticisinin çalıştığı platform (örneğin, Windows)
	• Kuyruk yöneticisinin desteklediği sistem kontrol komutları düzeyi
	• Kuyruk yöneticisinin mesaj önceliği sınırı
	• Uygulamalara MQ komutlarını gönderebilecek kuyruk adı
	• Kuyruk yöneticisinin işleyebileceği maksimum mesaj uzunluğu
	• Kuyruk yöneticisinin programlar tarafından yapılan PUT ve GET işlemlerinde syncpointing desteği
Değiştirilebilir Özellikler:
	• Kuyruk yöneticisinin açıklama metni
	• Kuyruk yöneticisinin karakter seti tanımlayıcıları
	• Kuyruk yöneticisinin tetikleme mesajları için zaman aralığı
	• Kuyruk yöneticisinin mesaj zaman aşımına uğramış mesajları tarama aralığı (IBM MQ for z/OS)
	• Kuyruk yöneticisinin ölü mesajlar için varsayılan kuyruk adı
	• Kuyruk yöneticisinin varsayılan iletim kuyruğu adı
	• Bağlantı başına açık tutulan maksimum işlem tutamağı sayısı
	• Olay raporlamalarının etkinleştirilmesi ve devre dışı bırakılması
	• İşlem birimi içinde açık tutulabilecek maksimum sayıda onaylanmamış mesaj
Kuyruk Yöneticileri ve Yük Dengeleme
IBM MQ, kuyruk yöneticilerini bir kümeye dahil ederek aynı kuyruğun birden fazla tanımını kullanabilir. Bu kümeye dahil edilen kuyruk yöneticileri arasında yük dengelemesi yapılır. Kuyruğa ait mesajlar, kuyruk yöneticisinin yük dengeleme algoritmasına göre, kuyruk yöneticilerine dağılır ve bu sayede sistemdeki yük dağıtılır.

********
Kanallar (Channels)
	• Tanım: Kanallar, iki IBM MQ sunucusu arasındaki iletişim için kullanılan mantıksal bağlantılardır. Bu bağlantılar, MQI (Message Queue Interface) ile tanımlanabilir ve programlar arasındaki mesajları taşımada kullanılır. Ayrıca, bu kanallar uygulamaları altındaki iletişim protokollerinden soyutlar.
	• Kanalların Kategorileri:
		○ Mesaj Kanalları: Yalnızca bir yönlü olan ve mesajları bir kuyruktan diğerine ileten kanallar.
		○ MQI Kanalları: İki yönlü kanallar olup, bir IBM MQ istemcisi ile kuyruk yöneticisi arasında MQI çağrılarını taşır.
		○ AMQP Kanalları: Yine iki yönlü kanallar olup, AMQP protokolü kullanan uygulamalar ve kuyruk yöneticileri arasında mesaj iletimini sağlar.
Mesaj Kanalları (Message Channels)
	• Kullanım Amacı: Mesaj kanalları, bir kuyruk yöneticisinden diğerine mesaj taşımak için kullanılır. Uzak bir kuyruk yöneticisinden yanıt almak için ayrı bir kanal kullanmak gerekebilir.
	• Mesaj Kanalı Ajansı (MCA): Bir kanal üzerinde iki yönlü iletişimi sağlamak için kullanılır. MCA, her iki uçtaki mesajları taşır.
MQI Kanalları
	• Tanım: MQI kanalı, IBM MQ istemcisi ile bir kuyruk yöneticisi arasında, mesaj içeriği taşıyan MQPUT çağrıları ve yanıtları iletmek için kullanılır.
	• Bağlantılar: İstemci-geri yanıt almak için bir istemci bağlantısı ve sunucu-yanıtı göndermek için bir sunucu bağlantısı gereklidir.
AMQP Kanalları
	• Tanım: AMQP kanalı, AMQP mesajlaşma uygulamaları ile kuyruk yöneticisi arasında mesajların iletilmesini sağlar. Bu tür kanallar, IBM MQ'yu daha esnek ve genişletilebilir hale getirir.
MCA için Çoklu İşlem Desteği (Pipelining)
	• Pipelining: Bir mesaj kanal ajanı (MCA) birden fazla işlem ile mesajları daha verimli taşıyabilir. Bu işlem, mesajların kanal üzerindeki transferini hızlandırır ve kanalın verimli çalışmasını sağlar.

*******************
IBM MQ Communication ve Kanallar
IBM MQ, istemci ve sunucu arasındaki iletişimi sağlayan MQI (Message Queue Interface) kanallarını kullanır. Bu kanallar, istemci uygulamaları ile kuyruk yöneticisi arasındaki mesajları taşır.
Kanallar ve Bağlantılar
Bir kanal tanımı, hem IBM MQ MQI istemcisinde hem de sunucu tarafında oluşturulmalıdır. Kanal tanımlarını nasıl oluşturacağınız hakkında daha fazla bilgiye "Defining MQI channels" başlığında ulaşabilirsiniz.
İletişim Protokolleri
MQI kanalları, farklı istemci platformları ve sunucu platformları arasında çeşitli iletim protokollerini kullanabilir. Bunlar:
İstemci Platformu	LU 6.2	TCP/IP	NetBIOS	SPX
IBM i				Yes			
AIX / Linux			Yes		Yes		
Windows				Yes		Yes		Yes		Yes
	• LU 6.2: Eski bir protokoldür ve bazı platformlarda desteklenmez.
	• TCP/IP: İstemci ve sunucu arasında en yaygın kullanılan iletim protokolüdür.
	• NetBIOS ve SPX: Daha az yaygın protokollerdir, ancak bazı platformlarda kullanılabilir.
Bağlantı ve İletişim
Bir IBM MQ uygulaması, MQI istemcisi olarak, MQCONN veya MQCONNX çağrısı ile kuyruk yöneticisi ile bağlantı kurar ve bağlantı tutamağı oluşturur. Daha sonra yapılan diğer çağrılar, bağlı olan kuyruk yöneticisi tarafından işlenir.
	• MQI istemcisi ile yapılan iletişim, sürekli bir bağlantı gerektirir.
	• Kuyruk yöneticileri arasında ise bağlantı bağımsız ve zaman bağımsızdır. Yani, iki kuyruk yöneticisi birbiriyle bağlantı kurarken sürekli bir aktif bağlantıya ihtiyaç duymaz.
Performans Düşünceleri
İletim protokolü, IBM MQ istemci ve sunucu sisteminin performansını etkileyebilir. Özellikle iletim yavaş olduğunda, kanal sıkıştırma kullanarak performans iyileştirmeleri yapılabilir. Kanal sıkıştırma, iletilen mesajların boyutunu küçültür, bu da veri iletim hızını artırabilir.
Bu bilgilerle IBM MQ ile istemci-sunucu iletişimi ve kanal tanımları hakkında genel bir anlayışa sahip olabilirsiniz. Detaylı açıklamalar ve konfigürasyonlar için daha fazla bilgi arıyorsanız, belirttiğiniz platforma göre farklı kanal tanımlamaları yapılabilir.


****************
IBM MQ Nesneleri İçin Adlandırma Kuralları
IBM MQ'de nesnelerin adlandırma konvansiyonu, nesne türüne bağlıdır. Ayrıca, IBM MQ ile kullanılan makinelerin ve kullanıcı kimliklerinin de adlandırma kısıtlamalarına tabi olduğunu unutmamalısınız.
Queue Manager Adlandırması
Her bir queue manager (kuyruk yöneticisi) kendi adıyla tanımlanır ve bu ad, birbirine bağlı kuyruk yöneticileri ağında benzersiz olmalıdır. Bu, her mesajın hedef kuyruk yöneticisini açıkça tanımlamak için gereklidir.
Diğer Nesneler
Diğer nesnelerin her birinin bir adı vardır ve bu ad, o nesneyi tanımlamak için kullanılabilir. Bu isimler, her bir kuyruk yöneticisinde ve nesne türünde benzersiz olmalıdır. Örneğin, bir queue (kuyruk) ve process (işlem) aynı adı taşıyabilir, ancak iki kuyruk aynı ada sahip olamaz.
Ad Uzunluğu ve Karakter Sınırlamaları
IBM MQ nesnelerinin adları 48 karakterle sınırlıdır (kanallar için bu sınır 20 karakterdir). Bununla birlikte, nesne türüne bağlı olarak bazı karakter kısıtlamaları ve adların benzersiz olması gereken kurallar vardır. 
Makine ve Kullanıcı Kimlik Adları
IBM MQ ile kullanılan makinelerin ve kullanıcı kimliklerinin adlarında bazı sınırlamalar vardır:
	• Makine adları boşluk içermemelidir. IBM MQ, boşluk içeren makine adlarını desteklemez. Eğer bu tür bir makineye IBM MQ kurulumu yapılırsa, kuyruk yöneticisi oluşturulamaz.
	• IBM MQ yetkilendirmeleri için kullanıcı kimlikleri ve grup adları 20 karakterden uzun olmamalıdır ve boşluk içermemelidir.
	• Windows üzerinde, IBM MQ için çalışan bir istemci, kullanıcı kimliği "@" karakterini içeriyorsa bağlanamaz (örneğin, abc@d).
IBM MQ Nesneleri İçin Adlandırma Kuralları
IBM MQ nesne adları, belirli maksimum uzunluklara sahiptir ve büyük/küçük harf duyarlıdır. Tüm karakterler her nesne türü için geçerli değildir, ve bir çok nesnenin adı benzersiz olmalıdır.
IBM MQ Dosya Adları
Her bir queue manager, kuyruk, işlem tanımı, namelist, kanal, istemci bağlantı kanalı, dinleyici, hizmet ve kimlik doğrulama bilgisi nesnesi bir dosya olarak temsil edilir. Nesne adları geçerli dosya adı olmayabileceği için, kuyruk yöneticisi gerekli olduğunda nesne adını geçerli bir dosya adına dönüştürür.
IBM i'ye Özgü Nesne Adlandırma
IBM i platformunda, her bir queue manager'ın bağlı olduğu benzersiz bir queue manager kütüphanesi vardır. Queue manager ve nesne adları, IBM i'nin Entegre Dosya Sistemi (IFS) gereksinimlerini karşılamak için dönüştürülmesi gerekebilir.


****************
BM MQ Nesneleri İçin Adlandırma Kuralları
IBM MQ nesnelerinin adlandırılmasında belirli kurallar ve sınırlamalar vardır. Her nesne türü için farklı adlandırma kuralları geçerli olabilir. Aşağıda, IBM MQ nesneleri için adlandırma kuralları ve sınırlamalarına dair detaylı bilgiler bulabilirsiniz:
IBM MQ Nesne Adları Uzunluğu ve Duyarlılığı
	• IBM MQ nesnelerinin adları 48 karaktere kadar olabilir. Ancak, kanal nesneleri ve istemci bağlantı kanalları için bu uzunluk 20 karakterle sınırlıdır.
	• Topic string (konu dizileri) en fazla 10240 bayt uzunluğunda olabilir.
	• Abone (Subscription) adları da en fazla 10240 bayt uzunluğunda olup, boşluk içerebilir.
	• Storage class adları 8 karakteri geçemez.
	• CF yapı adı (Coupling Facility Structure) en fazla 12 karakter olabilir.
	• IBM MQ nesneleri büyük/küçük harf duyarlıdır.
Geçerli Karakterler
IBM MQ nesne adlarında kullanılabilen geçerli karakterler:
	• Büyük harfler (A-Z): Herhangi bir kısıtlama yok.
	• Küçük harfler (a-z): MQSC betiklerinde küçük harfler tek tırnak içine alınmalıdır. Bazı sistemlerde (örneğin EBCDIC Katakana) küçük harfler kullanılamaz.
		○ z/OS üzerinde bazı sınırlamalar olabilir, örneğin kuyruk yöneticisi isimlerinde küçük harf kullanılamaz.
	• Sayısal karakterler (0-9): Herhangi bir kısıtlama yok.
	• Nokta (.) ve Alt çizgi (_): UNIX, Linux, Windows ve IBM i sistemlerinde kısıtlama yok.
		○ z/OS üzerinde isimlerin başında veya sonunda alt çizgi kullanmaktan kaçınılmalıdır.
	• Eğik çizgi (/):
		○ Windows sistemlerinde kuyruk yöneticisi adlarının başında eğik çizgi kullanılamaz.
		○ IBM i sistemlerinde CL komutları kullanıldığında eğik çizgi içeren adlar tek tırnak içinde olmalıdır.
	• Yüzde işareti (%):
		○ AIX, Linux, ve Windows sistemlerinde kullanılabilir, ancak z/OS üzerinde RACF kullanıyorsanız yüzde işareti kullanmamaktan kaçının.
		○ IBM i sistemlerinde CL komutlarıyla kullanıldığında, yüzde işareti içeren isimler tek tırnak içine alınmalıdır.
Nesne Adlarında İzin Verilmeyen Karakterler
	• Başında veya ortasında boşluk kullanılamaz.
	• Ulusal dil karakterleri (örneğin, Türkçe, Japonca karakterler) kullanılmaz.
	• Adlar, belirtilen alan uzunluğundan kısa ise sağ tarafa boşluk eklenebilir.
Queue (Kuyruk) Adlandırması
Bir kuyruğun adı iki bileşenden oluşur:
	1. Queue Manager Adı: Kuyruğun sahibi olan kuyruk yöneticisinin adı.
	2. Queue Adı: Kuyruk yöneticisi tarafından bilinen kuyruk adı.
	• Yerel kuyruklara atıfta bulunurken, queue manager adını geçersiz kılabilirsiniz, ancak tüm kuyruk isimleri her zaman queue manager adıyla birlikte döndürülür.
	• z/OS üzerinde, shared queue (paylaşılan kuyruk) adları, aynı queue sharing group içinde yer alan diğer yerel kuyruklarla aynı olamaz. Bu, bir uygulamanın yanlışlıkla paylaşılan bir kuyruğu açmasını önler.
Yasaklı Nesne Adları
Başlangıçta SYSTEM. ile başlayan nesne adları, kuyruk yöneticisi tarafından tanımlanan nesnelere ayrılmıştır. Bu nesne adlarını değiştirebilir, yeni nesneler ekleyebilirsiniz. Ancak, SYSTEM.DEAD.LETTER.QUEUE gibi nesne isimleri IBM MQ tarafından rezervlidir.
Adlandırma Örnekleri
	• Queue Manager Adı: QMGR1
	• Queue Adı: LOCAL_QUEUE
	• Channel Adı: MY_CHANNEL

*************
IBM MQ Dosya Adları ve Nesne İsimleri Dönüşümü
IBM® MQ her bir kuyruk yöneticisi, kuyruk, işlem tanımı, namelist, kanal, istemci bağlantı kanalı, dinleyici, hizmet ve kimlik doğrulama bilgisi nesnesi için bir dosya kullanır. Çünkü nesne adları her zaman geçerli dosya adı olamayabilir, bu nedenle kuyruk yöneticisi, gerekli olduğunda nesne adlarını geçerli dosya adlarına dönüştürür.
Queue Manager (Kuyruk Yöneticisi) Dizini ve Yolu
Bir kuyruk yöneticisi için varsayılan yol aşağıdaki gibi tanımlanır:
	• AIX ve Linux: Varsayılan önek /var/mqm olup, bu ayar mqs.ini yapılandırma dosyasının DefaultPrefix bölümünde yapılır.
	• Windows:
		○ 32-bit sistemler için varsayılan önek C:\Program Files (x86)\IBM\WebSphere MQ,
		○ 64-bit sistemler için C:\Program Files\IBM\MQ olup, veri dizinleri C:\ProgramData\IBM\MQ altında bulunur. Bu ayar da mqs.ini yapılandırma dosyasının DefaultPrefix bölümünde yapılır.
Ad Dönüşümü (Name Transformation)
Bir kuyruk yöneticisi adı geçerli bir dosya adı olmayabilir. Bu yüzden IBM MQ, kuyruk yöneticisi adını geçerli bir dosya adı yapabilmek için dönüştürür. Örneğin:
	• queue.manager adı queue!manager olarak dönüşür.
Dönüşüm kuralları:
	• Nokta (.) karakteri ! olarak değiştirilir.
	• Eğik çizgi (/) karakteri & olarak değiştirilir.
	• Eğer ad hala geçerli değilse, isim 8 karaktere kısaltılır ve ardından 3 karakterli bir sayısal ek eklenir.
Örnekler:
	• Windows (NTFS ya da FAT32):
		○ queue.manager ismi dönüşür ve C:\Program Files\IBM\MQ\qmgrs\queue!manager olur.
	• Windows (FAT):
		○ queue.manager ismi dönüşür ve C:\Program Files\IBM\MQ\qmgrs\queue!ma olur.
	• AIX ve Linux:
		○ queue.manager ismi dönüşür ve /var/mqm/qmgrs/queue!manager olur.
Diğer Nesneler İçin Dönüşüm
IBM MQ'da kuyruk yöneticisi dışında diğer nesneler de dosya sistemi üzerinde temsil edilir. Kuyruklar, işlem tanımları, namelists, kanallar, istemci bağlantı kanalları, dinleyiciler, hizmetler ve kimlik doğrulama bilgisi nesneleri de dosya adlarıyla ilişkilidir ve bu adlar, dosya sistemi adlarına dönüştürülür.
Her bir nesne için dönüştürülmüş ad ile orijinal nesne adı arasında basit bir ilişki bulunmaz. Ancak, dspmqfls komutunu kullanarak gerçek ve dönüştürülmüş nesne adları arasında dönüşüm yapılabilir.
Bu dönüşüm mekanizması, nesne adlarını geçerli dosya adlarına uyumlu hale getirir ve IBM MQ'nun dosya sistemine uygun şekilde çalışmasını sağlar.
******************

IBM i'deki Nesne İsimleri ve Dönüşümü
IBM® MQ, IBM i üzerinde bazı nesneleri (örneğin, kuyruk yöneticileri) dosya sistemi üzerinde temsil eder ve nesne isimlerini geçerli dosya adı kurallarına uydurmak için dönüşüm işlemi uygular.
Queue Manager ve Nesne İsimlerinin Dönüşümü
Bir kuyruk yöneticisi, kendisiyle ilişkilendirilmiş bir kuyruk yöneticisi kütüphanesine sahip olur ve bu kütüphaneye özgün bir ad verilir. Bu ad, genellikle kullanıcı tarafından belirlenen kuyruk yöneticisi adından türetilir ve en fazla 10 karakter uzunluğunda olabilir.
Örnek olarak:
	• Queue manager name (Kuyruk yöneticisi adı): ORANGE
	• Queue manager library name (Kuyruk yöneticisi kütüphanesi adı): QMORANGE
	• Directory (Dizin): /QIBM/UserData/mqm/ORANGE
Tüm kuyruk yöneticisi adları ve kuyruk yöneticisi kütüphanesi adları, /QIBM/UserData/mqm/mqs.ini dosyasındaki stanzalarda yazılıdır.
IBM i Entegre Dosya Sistemi (IFS) ve Nesne İsimleri
IBM MQ, verileri saklamak için IBM i Entegre Dosya Sistemi'ni (IFS) yaygın bir şekilde kullanır. Her IBM MQ nesnesi (örneğin kanal veya kuyruk yöneticisi) bir dosya ile temsil edilir ve nesne adı geçerli bir dosya adı olmayabilir. Bu nedenle, kuyruk yöneticisi, nesne adını geçerli bir dosya adı yapabilmek için dönüşüm işlemi uygular.
Queue Manager Dizini Yolu ve Dönüşümü
Bir kuyruk yöneticisinin dizini yolu şu şekilde oluşturulur:
	• Önek (Prefix): qm.ini yapılandırma dosyasından tanımlanır. Varsayılan önek /QIBM/UserData/mqm'dir.
	• qmgrs (Literali): Her zaman sabit bir bölüm.
	• Queue Manager Adı: Kuyruk yöneticisinin adı dosya adı kurallarına uygun hale getirilir. Örneğin, queue/manager adı queue&manager olarak dönüşür.
Bu işlem, isim dönüşümü olarak adlandırılır.
Örnek Dönüşüm:
	• Kuyruk yöneticisi adı: queue/manager
	• Dönüştürülmüş hali: /QIBM/UserData/mqm/qmgrs/queue&manager
Nesne İsimlerinin Dönüşümü
Her bir IBM MQ nesnesi için de adlar dosya adı kurallarına uygun hale getirilir. Kuyruk yöneticisi adından farklı olarak, her kuyruk yöneticisi için birçok nesne (kuyruklar, işlem tanımları, namelist'ler) olabilir. Kanallar ise bu dönüşümden etkilenmez.
Yeni bir isim oluşturulduğunda, orijinal nesne adı ile basit bir ilişki yoktur. Nesne adlarının dönüşümünü görmek için DSPMQMOBJN komutunu kullanabilirsiniz.
Bu dönüşüm, IBM i üzerindeki dosya sistemi kısıtlamalarına uymak ve IBM MQ'nun düzgün çalışmasını sağlamak için yapılır.

