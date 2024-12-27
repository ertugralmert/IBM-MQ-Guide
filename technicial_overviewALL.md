IBM MQ Teknik Genel Bakış (2024-10-24)
IBM® MQ, uygulamalarınızı birbirine bağlayarak kuruluşunuzda bilgilerin dağıtımını yönetmenizi sağlar. IBM MQ, birbirinden farklı bileşenler (işlemciler, işletim sistemleri, alt sistemler ve iletişim protokoller) üzerinden tutarlı bir uygulama programlama arayüzü (API) kullanarak programların birbirleriyle iletişim kurmasına olanak tanır. Bu arayüzü kullanan uygulamalara mesaj kuyruğu uygulamaları denir.
Aşağıdaki başlıklar, mesaj kuyruğu ve IBM MQ tarafından sunulan diğer özellikler hakkında bilgi edinmenizi sağlar.

Mesaj Kuyruğu (Message Queuing) Tanıtımı
IBM MQ ürünleri, programların birbirleriyle iletişim kurmasını sağlar. Bu, birbirinden farklı bileşenler (farklı platformlar ve iletişim protokollerini içeren sistemler) üzerinde çalışabilir. Mesaj kuyruğu sistemi, veri iletişimini güvenli ve güvenilir bir şekilde sağlar.
İngilizce Terim: Message Queuing

IBM MQ Nesneleri (Objects)
Queue Manager (kuyruk yöneticisi), IBM MQ nesnelerinin özelliklerini tanımlar. Bu özellikler, IBM MQ'nun nesneleri nasıl işleyeceğini etkiler. Nesneler, IBM MQ komutları ve arayüzleri kullanılarak oluşturulup yönetilir. Programlardan ise Message Queue Interface (MQI) kullanılarak nesneler kontrol edilir. Nesneler, programlardan erişildiğinde bir IBM MQ Object Descriptor (MQOD) ile tanımlanır.
İngilizce Terimler:
	• Queue Manager: Kuyruk Yöneticisi
	• MQI (Message Queue Interface): Mesaj Kuyruğu Arayüzü
	• MQOD (Message Queue Object Descriptor): Mesaj Kuyruğu Nesne Tanımlayıcısı

Dağıtık Kuyruğu ve Kümeleme (Distributed Queuing and Clusters)
Dağıtık Kuyruğu (Distributed Queuing), mesajların bir kuyruk yöneticisinden diğerine gönderilmesini sağlar. Bu alıcı kuyruk yöneticisi aynı makinada veya farklı bir yerde olabilir, yakın bir yer veya dünyanın öteki tarafında olabilir. Kümeler (Clusters) oluşturularak, IBM MQ bu bağlantıların çoğunu sizin yerinize otomatik olarak yapılandırabilir.
İngilizce Terimler:
	• Cluster: Küme
	• Distributed Queuing: Dağıtık Kuyruğu

Yayın/Abone Mesajlaşma (Publish/Subscribe Messaging)
Yayın/abone mesajlaşma, bilgi sağlayıcısı ile bu bilgiyi tüketenler arasındaki bağı koparmaya olanak tanır. Gönderen ve alıcı uygulamaların birbiri hakkında herhangi bir bilgiye sahip olmadan bilgi gönderilip alınabilir.
İngilizce Terim: Publish/Subscribe Messaging

Yüksek Erişilebilirlik (High Availability - HA) Çözümleri Karşılaştırması
IBM MQ, yüksek erişilebilirlik (HA) için çeşitli yapılandırmalar sunar. Bu yapılandırmalar, desteklenen platformlar ve sunulan özellikler bakımından farklılık gösterir.
İngilizce Terim: High Availability (HA) Solutions

IBM MQ Multicast
IBM MQ Multicast, düşük gecikmeli, yüksek dağılım ve güvenilir multicast mesajlaşma sunar. Bu özellik, birden fazla alıcıya mesaj göndermeyi verimli hale getirir.
İngilizce Terimler:
	• Multicast: Multicast (Çoklu yayım)
	• Low Latency: Düşük gecikme
	• High Fan-Out: Yüksek dağılım

MQ Telemetri Tanıtımı (MQ Telemetry Overview)
MQ Telemetry, uzak cihazlardan veri toplama ve bu cihazları yönetme sürecidir. MQXR (MQ Telemetry Servisi), bir kuyruk yöneticisinin parçası olarak hizmet verir. Bu özellik, cihaz verilerinin toplanması ve kontrol edilmesi ile web uygulamaları arasında entegrasyonu sağlar.
İngilizce Terimler:
	• Telemetry: Telemetri
	• MQXR: MQ Telemetry Servisi

IBM MQ'da Güvenlik (Security in IBM MQ)
IBM MQ, yetkilendirme servis arayüzü, kanal güvenliği için TLS (Transport Layer Security), kanal doğrulama kayıtları ve mesaj güvenliği gibi çeşitli güvenlik yöntemlerini destekler.
İngilizce Terimler:
	• TLS (Transport Layer Security): Taşıma Katmanı Güvenliği
	• Authorization Service Interface: Yetkilendirme Servis Arayüzü

IBM MQ MQI Müşterileri (MQI Clients)
MQI istemcisi, kuyruk yöneticisi çalıştırmayan bir sistemde IBM MQ'nun çalışmasına olanak tanır. Bu istemci, sistemlerde kuyruk yöneticisi olmadan mesaj kuyruğu özelliklerini kullanmanıza olanak sağlar.
İngilizce Terim: MQI Clients

İşlem Yönetimi ve Destek (Transaction Management and Support)
IBM MQ, işlem yönetimi ve transaction (işlem) desteği sağlar. Bu, veri tutarlılığı ve güvenilirliği sağlamak için çok önemlidir.
İngilizce Terim: Transaction Management

Kuyruk Yöneticisi İmkanlarını Genişletme (Extending Queue Manager Facilities)
User exits, API exits veya kurulum hizmetleri kullanarak kuyruk yöneticisi işlevselliğini genişletebilirsiniz.
İngilizce Terimler:
	• User Exits: Kullanıcı Çıkışları
	• API Exits: API Çıkışları

IBM MQ Java Dil Arayüzleri (Java Language Interfaces)
IBM MQ, Java uygulamalarında kullanılmak üzere üç farklı API sağlar:
	• IBM MQ classes for Jakarta Messaging
	• IBM MQ classes for JMS (Java Message Service)
	• IBM MQ classes for Java
İngilizce Terimler:
	• API (Application Programming Interface): Uygulama Programlama Arayüzü
	• JMS (Java Message Service): Java Mesaj Hizmeti
	• Jakarta Messaging: Jakarta Mesajlaşma

IBM MQ for z/OS Kavramları
IBM MQ for z/OS platformu, kayıt tutma mekanizması, depolama yönetimi teknikleri, geri dönüşüm birimi durumu ve kuyruk paylaşımı grupları gibi z/OS platformuna özgü kavramlar sunar.
İngilizce Terimler:
	• z/OS: IBM'in büyük sistem platformu
	• Queue Sharing Groups: Kuyruk Paylaşım Grupları

IBM MQ ve Diğer z/OS Ürünleri
IBM MQ, diğer z/OS ürünleriyle entegre çalışabilir, bu sayede z/OS ortamındaki diğer sistemlerle verimli iletişim sağlar.

Managed File Transfer (MFT)
Managed File Transfer, dosyaların sistemler arasında güvenli, yönetilen ve denetlenebilir bir şekilde transfer edilmesini sağlar.
İngilizce Terim: Managed File Transfer

IBM MQ Internet Pass-Thru (MQIPT)
MQIPT, uzak siteler arasında güvenli iletişim sağlamak için kullanılan isteğe bağlı bir IBM MQ bileşenidir.
İngilizce Terim: MQ Internet Pass-Thru

IBM MQ Konsolu ve REST API
IBM MQ Konsolu ve REST API, IBM MQ'nun yönetimini sağlayan ve mesajlaşma işlemleri gerçekleştirilen HTTP tabanlı arayüzlerdir.
İngilizce Terim:
	• REST API: REST API (Representational State Transfer API)



Mesajlar ve Kuyruklar
IBM MQ'nun temel bileşenleri mesajlar ve kuyruklardır. Mesaj kuyruklama sistemi bu iki bileşen üzerine kurulur.
Mesaj Nedir?
Mesaj, bir uygulama tarafından başka bir uygulamaya (veya aynı uygulamanın farklı bölümleri arasında) bilgi aktarmak için kullanılan bir bayt dizisidir. Mesajlar, uygulamaların birbirleriyle veri transferi yapmasını sağlar. Uygulamalar, aynı platformda veya farklı platformlarda çalışıyor olabilir.
Bir IBM® MQ mesajı şunlardan oluşur:
	1. Uygulama Verisi: Mesajın içeriği ve yapısı, uygulama programları tarafından tanımlanır.
	2. Mesaj Tanımlayıcısı (Message Descriptor): Mesajı tanımlar ve mesaj tipi, gönderici tarafından atanan öncelik gibi ek kontrol bilgilerini içerir. Mesaj tanımlayıcısının formatı IBM MQ tarafından tanımlanmıştır.
	3. Mesaj Özellikleri (Message Properties): Mesajla ilgili meta-veri bilgisi. Mesaj özelliklerinin içeriği, kullanan uygulama programları tarafından belirlenir.
Mesaj Uzunluğu
Varsayılan maksimum mesaj uzunluğu 4 MB'dir, ancak bu uzunluk 100 MB'ye kadar artırılabilir (1 MB = 1.048.576 bayt). Gerçekten, mesaj uzunluğu şunlar tarafından sınırlanabilir:
	• Alıcı kuyruğu için tanımlanan maksimum mesaj uzunluğu
	• Kuyruk yöneticisi için tanımlanan maksimum mesaj uzunluğu
	• Kuyruk için tanımlanan maksimum mesaj uzunluğu
	• Gönderen veya alıcı uygulama tarafından tanımlanan maksimum mesaj uzunluğu
	• Mesaj için mevcut depolama alanı
Bir uygulamanın ihtiyacı olan tüm bilgiyi göndermek için birden fazla mesaj gönderilebilir.
Uygulamalar Mesajları Nasıl Gönderir ve Alır?
Uygulama programları, MQI (Message Queue Interface) çağrılarını kullanarak mesajları gönderir ve alır. Örneğin, bir mesajı kuyruğa koymak için bir uygulama:
	• Gerekli kuyruğu açar ve MQOPEN çağrısı yapar.
	• Mesajı kuyruğa koymak için MQPUT çağrısı yapar. Başka bir uygulama aynı kuyruktan mesajı alabilir, bunun için MQGET çağrısı yapar.
Daha fazla bilgi için MQI çağrılarına bakabilirsiniz.
Kuyruk Nedir?
Kuyruk, mesajları depolamak için kullanılan bir veri yapısıdır. Her kuyruk bir kuyruk yöneticisi tarafından sahiplenilir. Kuyruk yöneticisi, sahip olduğu kuyrukları yönetmekten sorumludur ve aldığı tüm mesajları uygun kuyruklara depolar.
Önceden Tanımlanmış Kuyruklar ve Dinamik Kuyruklar
Kuyruklar, oluşturulma şekillerine göre sınıflandırılabilir:
	• Önceden Tanımlanmış Kuyruklar: Yönetici tarafından MQSC veya PCF komutları ile oluşturulur. Bu kuyruklar kalıcıdır; uygulamalardan bağımsız olarak varlıklarını sürdürürler ve IBM MQ yeniden başlatıldığında silinmezler.
	• Dinamik Kuyruklar: Bir uygulama, bir model kuyruğun adıyla MQOPEN çağrısı yaparak dinamik kuyruk oluşturur. Model kuyrukları, kuyruğun özelliklerini belirleyen şablon kuyruk tanımlarını kullanarak dinamik kuyruklar oluşturur. Model kuyrukları DEFINE QMODEL komutuyla oluşturulabilir. Model kuyruğunun özellikleri (örneğin, üzerinde depolanabilecek maksimum mesaj sayısı) dinamik kuyruğa miras alınır.
Model kuyruklarının bir özelliği, dinamik kuyruğun kalıcı mı yoksa geçici mi olacağını belirtmektir. Kalıcı kuyruklar uygulama ve kuyruk yöneticisi yeniden başlatıldığında bile hayatta kalır; geçici kuyruklar ise yeniden başlatıldığında kaybolur.
Kuyruklardan Mesaj Almak
Uygun yetkilere sahip uygulamalar, mesajları kuyruktan aşağıdaki algoritmalara göre alabilir:
	• FIFO (İlk Giren İlk Çıkar): Kuyruğa ilk eklenen mesaj ilk alınır.
	• Mesaj Önceliği: Mesaj tanımlayıcısında belirtilen önceliğe göre mesajlar alınır. Aynı önceliğe sahip mesajlar FIFO bazında alınır.
	• Belirli Bir Mesaj: Uygulama, belirli bir mesaj almak için bir MQGET çağrısı yapabilir.
Bu sistem, mesajların güvenli ve zamanında teslim edilmesini sağlar.


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

IBM MQ Communication ve Kanallar
IBM MQ, istemci ve sunucu arasındaki iletişimi sağlayan MQI (Message Queue Interface) kanallarını kullanır. Bu kanallar, istemci uygulamaları ile kuyruk yöneticisi arasındaki mesajları taşır.
Kanallar ve Bağlantılar
Bir kanal tanımı, hem IBM MQ MQI istemcisinde hem de sunucu tarafında oluşturulmalıdır. Kanal tanımlarını nasıl oluşturacağınız hakkında daha fazla bilgiye "Defining MQI channels" başlığında ulaşabilirsiniz.
İletişim Protokolleri
MQI kanalları, farklı istemci platformları ve sunucu platformları arasında çeşitli iletim protokollerini kullanabilir. Bunlar:
İstemci Platformu	LU 6.2	TCP/IP	NetBIOS	SPX
IBM i	Yes			
AIX / Linux	Yes	Yes		
Windows	Yes	Yes	Yes	Yes
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



Dağıtık Kuyruklama (Distributed Queuing)
	• Dağıtık kuyruklama, bir kuyruk yöneticisinden diğerine mesaj gönderilmesini sağlar. Alıcı kuyruk yöneticisi, mesajların gönderildiği yerin aynı makinede veya farklı bir makinede olabileceği gibi, farklı bir platformda da olabilir.
	• MQCONN (Message Queue Connection) ve MQOPEN çağrıları kullanılarak bağlantılar yapılır.
	• Kuyruk Yöneticisi (Queue Manager - QM), her kuyruğun tanımına sahiptir ve yerel kuyruklar (local queues) ile uzaktaki kuyruklar (remote queues) arasında geçiş yapılabilir.
	• Eğer mesajlar uzaktaki bir kuyruğa gönderilirse, yerel kuyruk yöneticisi, mesajları transmission queue (iletim kuyruğu) adı verilen bir kuyruğa yerleştirir, bu kuyruk mesajları bir message store'da depolar ve ardından hedef kuyruk yöneticisine iletilmesini sağlar.
Mesaj Göndermek için Gereken Bileşenler:
	• Transmission Queue: Mesajlar uzaktaki bir kuyruk yöneticisine gönderileceği zaman, mesajlar burada bekletilir.
	• Channel: Mesajları bir kuyruk yöneticisinden diğerine iletmek için kullanılan iletişim kanalıdır. Bu kanalın her iki ucunda bir Message Channel Agent (MCA) bulunur.
	• Dead Letter Queue: Mesajların hedeflerine ulaşılamadığı durumlarda kullanılan bir kuyruktur. Mesajlar burada bekletilir ve yöneticiye bildirilir.
Mesajları Geri Döndürmek İçin Gereken Bileşenler:
	• Kanalın karşıtı yönünde çalışan ikinci bir kanal gereklidir. Bu kanal, mesajları karşı taraftan alır ve uygulamaya geri gönderir.
Küme (Cluster):
	• Kümeleme, IBM MQ'nun daha kolay bir şekilde yapılandırılmasını sağlar. Çeşitli kuyruk yöneticileri, her biri hakkında bilgi sahibi olduğu kümeye dahil edilir. Kümeye dahil olan her kuyruk yöneticisi, küme içindeki diğer kuyruk yöneticilerine mesaj gönderir.
	• Kümelenmiş Kuıruk Yöneticileri: Her kuyruk yöneticisi, küme içinde iletilen mesajları alır ve gönderir. Her kuyruk yöneticisinin bir cluster-receiver channel (küme-alıcı kanalı) ve bir cluster-sender channel (küme-gönderici kanalı) vardır.
	• Full Repository: Küme yöneticileri küme bilgilerini saklar ve kümeye ait tüm kuyruklara erişim sağlar.
	• Partial Repository: Diğer kümelerdeki kuyruk yöneticilerinin bilgi depoladığı kısımdır.
Kümeleme Avantajları:
	• Yük Dengeleme: Küme, yük dengeleme sağlamak ve mesaj trafiğini yönetmek için kullanılır.
	• Bütünsel Yönetim: Küme, IBM MQ ağlarında çok sayıda kuyruk yöneticisi gerektiren büyük sistemler için çok daha kolay yönetilebilir bir çözüm sunar.
Bu yapı, mesajları uzak bir kuyruğa iletmeyi, geri göndermeyi ve küme içinde yük dengelemesi yapmayı sağlar. Kümelemeyle ilgili diğer detaylar, tüm yöneticilerin hangi kuyruklarla etkileşimde bulunduğunu ve kuyrukların verimli şekilde yönetilmesini sağlar.

Dağıtık Kuyruklama Bileşenleri (Distributed Queuing Components)
Dağıtık kuyruklama, bir kuyruk yöneticisinden diğerine mesaj göndermek için kullanılan bileşenlerin tümünü içerir. Bu bileşenler:
	• Mesaj Kanalları (Message Channels): Mesajları bir kuyruk yöneticisinden diğerine taşır. Bu kanallar, MQI kanalları (Server-connection ve Client-connection) ile karıştırılmamalıdır. Mesaj kanalları bir yöneticiden diğerine iletilen mesajları taşıyan bağlantılardır.
	• Mesaj Kanal Ajanları (MCA): Her kanalın her iki ucunda bulunan yazılım ajanlarıdır. Her iki ucunda da iletişim için bir Message Channel Agent (MCA) bulunur.
	• İletim Kuyrukları (Transmission Queues): Mesajlar, iletmek için bir transmission queue kullanılarak bir kuyruğa gönderilir.
	• Kanal Başlatıcıları ve Dinleyiciler (Channel Initiators and Listeners): Kanalın açılması ve dinlenmesi işlemlerini başlatan bileşenlerdir.
	• Kanal Çıkış Programları (Channel-exit Programs): Mesaj kanallarındaki iş akışlarını kontrol etmek için kullanılan özel programlardır.
Mesaj Kanalları (Message Channels)
	• Mesaj kanalları, bir kuyruk yöneticisinden diğerine mesajları taşır. Mesaj kanalları, her iki uçta farklı tiplerde tanımlanabilir. Kanalın uçları şu şekilde olabilir:
		○ Sender (SDR): Mesajları gönderen uç.
		○ Receiver (RCVR): Mesajları alan uç.
		○ Server (SVR): Sunucu uç noktası.
		○ Requester (RQSTR): İstemci uç noktası.
		○ Cluster Sender (CLUSSDR): Küme gönderici kanalı.
		○ Cluster Receiver (CLUSRCVR): Küme alıcı kanalı.
Bir kanal tipi seçilerek, iki uç arasında bağlantı yapılır. Örneğin, sender-receiver kanalı mesajların bir uçtan diğerine iletilmesini sağlar. Cluster sender ve cluster receiver kanalları, küme içindeki mesaj iletimini yönetir.
Kanal Türleri
	1. Sender-Receiver Channels: Gönderen uç, kanalı başlatır ve alıcıya mesaj gönderir. Alıcı uç, mesajları hedef kuyruklara iletir.
	2. Requester-Server Channels: İstemci uç kanalı başlatır ve sunucu uç, mesajları istemciye gönderir.
	3. Requester-Sender Channels: İstemci kanalı başlatır ve sender uç mesajları göndermeye devam eder.
	4. Server-Receiver Channels: Tamamen yapılandırılmış sunucu uçlarındaki kanallar, alıcı uçlarda mesajların iletilmesini sağlar.
	5. Cluster Sender Channels: Küme içinde her kuyruk yöneticisi, başka bir yöneticiye mesaj gönderebilir. Küme bilgileri ve mesajlar bu kanallar üzerinden iletilir.
	6. Cluster Receiver Channels: Küme içindeki her kuyruk yöneticisi, küme mesajlarını alır.
Diğer Bileşenler
	• Dead-Letter Queue: Mesajların hedefe ulaşılamadığında gönderileceği kuyruktur. Mesajlar, yöneticinin incelediği ve yeniden yönlendirdiği bir kuyrukta depolanır.
	• Remote Queue Definitions: Başka bir kuyruk yöneticisine ait kuyrukların tanımlarıdır.
	• Aliases: Queue Manager Alias ve Reply-to Queue Alias gibi tanımlar, sistem yöneticilerinin kuyrukları yönlendirmesine olanak tanır. Bu sayede, uygulamaları değiştirmeden hedef kuyrukları veya kuyruk yöneticilerini değiştirmek mümkündür.
Mesaj Gönderme ve Alma
Mesajlar bir transmission queue üzerinden iletilir ve her iki uçta message channel agent (MCA) bulunur. Mesajlar, dead-letter queue'ya yönlendirilen mesajlar hariç, doğru hedeflere iletilir.
Küme (Cluster) Özellikleri
Bir küme, IBM MQ'daki kuyruk yöneticilerinin gruplandırılmasıdır. Her bir kuyruk yöneticisi, cluster-sender channel ve cluster-receiver channel kullanarak küme içindeki diğer kuyruk yöneticileri ile iletişim kurar. Küme yapılandırması, yönetim kolaylığı sağlar ve kuyruklar arası iş yükünü dengeler.
Bu bileşenler, dağıtık kuyruklama ve kümeleme özelliklerinin bir arada nasıl çalıştığını ve mesajların düzgün bir şekilde iletilmesini nasıl sağladığını anlatmaktadır.

Dead-Letter Queue (DLQ) Nedir?
Dead-Letter Queue (DLQ), "Teslim Edilemeyen Mesaj Kuyruğu" olarak da bilinir. Bir mesajın hedef kuyruğuna teslim edilemediği durumlarda, bu mesajlar Dead-Letter Queue'ya gönderilir. Genellikle şu durumlarda kullanılır:
	• Hedef kuyruk yoktur.
	• Hedef kuyruk doludur.
	• Mesajın taşınması sırasında veri dönüşüm hataları meydana gelir.
DLQ'nin Kullanım Amacı:
	• Mesajların Saklanması: Eğer bir mesaj hedef kuyruğuna teslim edilemezse, bu mesaj DLQ'ya (Dead-Letter Queue) gönderilir. Bu sayede mesaj kaybolmaz ve sonra tekrar işlenebilir.
	• Veri Dönüşüm Hataları: Eğer bir kanal üzerinden veri dönüşümü sırasında bir hata olursa, bu mesaj da DLQ'ya gider.
DLQ ile İlgili Önemli Noktalar:
	1. Mesaj Başlığı:
		○ DLQ'ya giden her mesaj, bir MQDLH (Dead Letter Header) başlığı ile işaretlenir. Bu başlık, mesajın neden DLQ'ya gönderildiğini belirtir.
		○ MQDLH başlığındaki Reason (sebep) alanı, mesajın neden teslim edilemediğine dair bir hata kodu içerir.
	2. Queue Manager (Kuyruk Yöneticisi):
		○ Her kuyruk yöneticisinin bir Dead-Letter Queue (DLQ) kuyruğu olmalıdır. Eğer bu kuyruk tanımlı değilse ve bir mesaj teslim edilemezse, bu mesaj aktarım kuyruğunda kalır ve kanal durur.
	3. Hızlı (Non-Persistent) Mesajlar:
		○ Hızlı (non-persistent) mesajlar teslim edilemezse ve hedef sistemde DLQ yoksa, bu mesajlar silinir.
	4. Teslimat Sırası Üzerindeki Etkisi:
		○ Dead-Letter Queue kullanmak, mesajların teslim sırasını etkileyebilir. Bu yüzden bazı sistemler, mesaj sırasını bozmamak için DLQ kullanmamayı tercih edebilir.
Özetle:
Dead-Letter Queue (DLQ), teslim edilemeyen mesajları güvenli bir şekilde saklar ve daha sonra bu mesajları incelemenizi sağlar. Ancak, DLQ kullanımı mesajların teslim sırasını etkileyebilir. Eğer mesaj sırasının önemli olduğu bir durumdaysanız, DLQ kullanmamak isteyebilirsiniz.

Remote Queue Definitions (Uzak Kuyruk Tanımlamaları)
Remote Queue Definitions (Uzak Kuyruk Tanımlamaları), başka bir kuyruk yöneticisi tarafından sahip olunan kuyrukların tanımlarıdır. Yani, bir kuyruk yöneticisi, yalnızca kendi yerel kuyruğuna mesaj alabilirken, aynı zamanda mesajları yerel veya uzak kuyruklara gönderebilir. Uzak kuyruk tanımlamaları, bir uygulamanın uzak bir kuyruğa mesaj göndermesini sağlar, böylece uygulamanın uzak kuyruk adı, uzak kuyruk yöneticisi adı veya iletim kuyruğu adı gibi bilgileri doğrudan belirtmesi gerekmez.
Uzak Kuyruk Tanımlarının Avantajları:
	1. Konum Bağımsızlığı (Location Independence):
		○ Uzak kuyruk tanımlamaları, uygulamalara, mesajları uzak bir kuyruğa göndermek için gerekli bilgileri belirtmeden bu işlemi yapma imkanı verir. Yani uygulama, uzak kuyruğun adı veya yöneticisinin adı gibi bilgileri bilmek zorunda kalmaz.
	2. Mesaj Yönlendirme Kolaylığı:
		○ Bir kuyruk yöneticisinin, kendi yerel kuyruğu dışında, başka kuyruk yöneticilerinin kuyruklarına mesaj gönderebilmesi için, uzak kuyruk tanımlamaları gereklidir. Bu tanımlar sayesinde, uygulamalar başka kuyruk yöneticilerine ait kuyruklara kolayca mesaj gönderebilir.
Kullanım Durumları:
	• Yerel ve Uzak Kuyruklara Mesaj Gönderme: Bir kuyruk yöneticisi, yerel kuyruğuna mesaj alırken, aynı zamanda uzak kuyruklara da mesaj gönderebilir. Uzak kuyruk tanımlamaları, bu tür bir mesajlaşmayı kolaylaştırır.
	• Uzak Kuyruklara Mesaj Gönderme: Uzak kuyruk tanımlamaları sayesinde, bir kuyruk yöneticisi, uzak bir kuyruğa mesaj gönderebilir ve mesaj ile ilgili gerekli tüm bilgileri uygulamaya açıkça belirtmek zorunda kalmaz. Bu da uygulama kodlarını basitleştirir.
Özetle:
Remote Queue Definitions, farklı kuyruk yöneticileri arasında mesaj iletimini basitleştiren ve uygulamaların uzak kuyruğa mesaj göndermesini kolaylaştıran bir yapıdır. Uzak kuyrukları kullanarak, uygulamalar herhangi bir özel uzak kuyruk adı, uzak kuyruk yöneticisi adı veya iletim kuyruğu belirtmek zorunda kalmazlar. Bu, uygulamanın ve sistem yöneticisinin işini kolaylaştırır, çünkü konumdan bağımsız bir mesajlaşma yapılabilir.

• Ara kuyruk yöneticilerinden geçiş (Multi-hopping):
	• Eğer doğrudan iletişim bağlantısı yoksa, mesajlar birden fazla ara kuyruk yöneticisinden geçerek hedef kuyruk yöneticisine ulaşabilir. Bu yöntem, "multi-hopping" olarak adlandırılır.
	• Örneğin, QM1 kuyruk yöneticisinden gelen mesajlar, QM2 aracılığıyla QM3'e iletilir. Her bir kuyruk yöneticisi, iletişimi yönlendirecek kanallara sahip olmalıdır. Bu durum, ara kuyruk yöneticilerinin kullanıldığı bir senaryodur.
• Kanal paylaşımı:
	• Mesajlar farklı uygulamalardan tek bir kuyruk yöneticisine gönderileceği zaman, kanal paylaşımı yapılabilir.
	• Bu durumda, tek bir iletim kuyruğu (transmission queue) üzerinden birden fazla uygulama mesaj gönderir. Bu yöntem, iletilen mesajların aynı iletim kuyruğu üzerinden gitmesini sağlar.
• Farklı kanallar kullanma:
	• Farklı türdeki mesajlar arasında seçim yaparken, iki kuyruk yöneticisi arasında birden fazla kanal tanımlanabilir.
	• Örneğin, güvenlik nedeniyle ya da mesajın boyutu ile hız arasında bir denge kurmak amacıyla ikinci bir kanal eklenebilir. Bu kanallar, aynı hedef kuyruğa mesajları iletecek şekilde yapılandırılır.
• Küme kullanımı (Clustering):
	• IBM MQ, kümeleme (clustering) ile birden fazla kuyruk yöneticisi arasında yük dengelemesi yapar.
	• Her kuyruk yöneticisi bir "cluster-receiver" kanalı tanımlar ve mesaj gönderildiğinde, ilgili "cluster-sender" kanalı otomatik olarak tanımlanır. Yük dengeleme algoritması, bir kuyruk yöneticisinin mevcut olup olmadığına göre mesajı yönlendirir.

Addressing Information (Adresleme Bilgisi)
Bir uygulama, mesajlarını uzak bir kuyruk yöneticisine göndereceğinde, yerel kuyruk yöneticisi bu mesajlara bir iletim başlığı ekler ve bunları iletim kuyruğuna yerleştirir. Bu başlık, hedef kuyruk ve kuyruk yöneticisinin adını, yani adresleme bilgisini içerir.
	• Tek bir kuyruk yöneticisi ortamında, hedef kuyruğun adresi, bir uygulama bir kuyruğu açarak mesajlarını göndermeye çalıştığında belirlenir. Çünkü hedef kuyruk aynı kuyruk yöneticisinde bulunur ve herhangi bir adresleme bilgisi gerekmez.
	• Dağıtılmış kuyruklama ortamında, kuyruk yöneticisinin yalnızca hedef kuyruk adını değil, aynı zamanda bu kuyruğun konumunu (yani kuyruk yöneticisinin adını) ve o uzak konuma (yani iletim kuyruğuna) nasıl ulaşılacağını bilmesi gerekir. Bu adresleme bilgisi iletim başlığında yer alır. Alıcı kanal, iletim başlığını kaldırır ve bu bilgiyi kullanarak hedef kuyruğu bulur.
Eğer uzak kuyruk yöneticisinin adı ve hedef kuyruk bilgilerini uygulamanızın belirtmesini engellemek istiyorsanız, bir remote queue definition (uzak kuyruk tanımı) kullanabilirsiniz. Bu tanım, uzak kuyruğun adını, mesajların yönlendirileceği uzak kuyruk yöneticisinin adını ve mesajları taşıyan iletim kuyruğunun adını belirtir.
What are Aliases? (Alias Nedir?)
Alias'lar, mesajlar için hizmet kalitesini sağlamak amacıyla kullanılır. Kuyruk yöneticisi alias'ı, bir sistem yöneticisinin hedef kuyruk yöneticisinin adını değiştirmesine olanak tanır, böylece uygulamalarınızda herhangi bir değişiklik yapmanıza gerek kalmaz. Ayrıca, sistem yöneticisi, hedef kuyruk yöneticisine giden rotayı değiştirebilir veya birden fazla kuyruk yöneticisi aracılığıyla geçiş yapacak bir rota kurabilir (multi-hopping). Reply-to queue alias (cevap kuyruğu alias'ı), yanıtlar için hizmet kalitesini sağlar.
Kuyruk yöneticisi alias tanımları ve cevap kuyruğu alias tanımları, bir remote-queue definition (uzak kuyruk tanımı) kullanılarak oluşturulur ve bu tanımlarda RNAME boş bırakılır. Bu tanımlar gerçek kuyrukları tanımlamaz; kuyruk yöneticisi, fiziksel kuyruk adlarını, kuyruk yöneticisi adlarını ve iletim kuyruklarını çözmek için kullanır.
Queue Name Resolution (Kuyruk Adı Çözümlemesi)
Kuyruk adı çözümlemesi, her kuyruk açıldığında her kuyruk yöneticisinde gerçekleşir. Amacı, hedef kuyruğu, hedef kuyruk yöneticisini (bu yerel olabilir) ve o kuyruk yöneticisine giden rotayı (bu null olabilir) belirlemektir. Çözümlenen ad üç parçadan oluşur: kuyruk yöneticisi adı, kuyruk adı ve eğer kuyruk yöneticisi uzaksa, iletim kuyruğu.
Bir uzak kuyruk tanımı mevcutsa, alias tanımları başvurulmaz. Uygulamanın sağladığı kuyruk adı, uzak kuyruk tanımında belirtilen hedef kuyruk adı, uzak kuyruk yöneticisi adı ve iletim kuyruğu adı ile çözülür. Daha fazla bilgi için Queue Name Resolution bölümüne bakabilirsiniz.
Eğer bir uzak kuyruk tanımı yoksa ve bir kuyruk yöneticisi adı belirtilmişse ya da ad servisi tarafından çözülmüşse, kuyruk yöneticisi, sağlanan kuyruk yöneticisi adıyla eşleşen bir kuyruk yöneticisi alias tanımı olup olmadığını kontrol eder. Eğer varsa, içindeki bilgi kullanılarak kuyruk yöneticisi adı hedef kuyruk yöneticisi adıyla çözülür.
Eğer çözümleme sonucu kuyruk adı yerel bir kuyruk değilse, her mesajın iletim başlığına hem kuyruk yöneticisi adı hem de kuyruk adı eklenir.
Queue Manager Alias Definitions (Kuyruk Yöneticisi Alias Tanımlamaları)
Kuyruk yöneticisi alias tanımları, bir uygulamanın bir kuyruk açarak mesaj koyarken, kuyruk adı ve kuyruk yöneticisi adını belirttiği durumlarda geçerlidir.
Kuyruk yöneticisi alias tanımlarının üç kullanımı vardır:
	1. Mesaj gönderirken, kuyruk yöneticisi adını yeniden eşleştirmek
	2. Mesaj gönderirken, iletim kuyruğunu değiştirmek veya belirtmek
	3. Mesaj alırken, yerel kuyruk yöneticisinin, bu mesajlar için hedef kuyruk yöneticisi olup olmadığını belirlemek
Outbound Messages - Remapping the Queue Manager Name (Çıkış Mesajları - Kuyruk Yöneticisi Adını Yeniden Eşleştirmek) Kuyruk yöneticisi alias tanımları, bir MQOPEN çağrısında belirtilen kuyruk yöneticisi adını yeniden eşleştirmek için kullanılabilir. Örneğin, bir MQOPEN çağrısında "THISQ" kuyruk adı ve "YOURQM" kuyruk yöneticisi adı belirtilmiştir. Yerel kuyruk yöneticisinde, aşağıdaki gibi bir alias tanımı bulunur:

scss
Copy code
DEFINE QREMOTE (YOURQM) RQMNAME(REALQM)
Bu, uygulamanın mesajlarını YOURQM kuyruk yöneticisine koymak için kullanılan gerçek kuyruk yöneticisinin REALQM olduğunu gösterir.
Outbound Messages - Altering or Specifying the Transmission Queue (Çıkış Mesajları - İletim Kuyruğunu Değiştirmek veya Belirtmek)
Yukarıdaki açıklamalarda da belirtildiği gibi, QM1'den QM3'e ulaşmak için QM2'yi geçmek gerekiyor. Kuşkusuz, iletim kuyruğu ve kanal bağlantıları doğru şekilde yapılandırıldığında, mesajlar doğru yöneticilere iletilir.
Inbound Messages - Determining the Destination (Giriş Mesajları - Hedefi Belirlemek) Bir alıcı MCA, iletim başlığında belirtilen kuyruk yöneticisi adına sahip bir alias tanımı varsa, iletim başlığındaki kuyruk yöneticisi adı, alias tanımındaki RQMNAME ile değiştirilir.
Reply-to Queue Alias Definitions (Cevap Kuyruğu Alias Tanımlamaları)
Cevap kuyruğu alias tanımlamaları, mesajın cevabı için alternatif adlar belirtir. Bunun avantajı, kuyruk veya kuyruk yöneticisinin adını değiştirebilmeniz, ancak uygulamalarınızı değiştirmek zorunda kalmamanızdır.
Bu tanımlar, cevap kuyruğu için yanıtların nerede alınacağına dair yönlendirmeleri içerir ve her zaman bir alias kullanarak bu işlem yapılabilir.

Cluster Components (Küme Bileşenleri)
Küme, kuyruk yöneticilerinden, küme depolarından, küme kanallarından ve küme kuyruklarından oluşur.
Aşağıdaki alt başlıklarda, her bir küme bileşeni hakkında daha fazla bilgi bulabilirsiniz:
Cluster Repository (Küme Deposu)
Bir depo, bir kümenin üyesi olan kuyruk yöneticileri hakkında bilgi toplayan bir koleksiyondur.
Cluster Queue Manager (Küme Kuyruk Yöneticisi)
Bir küme kuyruk yöneticisi, bir kümenin üyesi olan bir kuyruk yöneticisidir.
Cluster Queues (Küme Kuyrukları)
Bir küme kuyruğu, bir küme kuyruk yöneticisi tarafından barındırılan ve kümedeki diğer kuyruk yöneticilerine sunulan bir kuyruktur.
[z/OS] Shared Queues ve Cluster Queues Karşılaştırması
Bu bilgi, shared queues (paylaşılan kuyruklar) ve cluster queues (kümeli kuyruklar) arasındaki farkları anlamanıza yardımcı olmak için tasarlanmıştır. Hangi tür kuyrukların sisteminiz için daha uygun olabileceğini belirlemenize yardımcı olabilir.
Cluster Channels (Küme Kanalları)
Her bir tam depo için, her bir diğer tam depoya bağlanacak bir cluster-receiver (kümeye alıcı) kanalı ve bir dizi cluster-sender (kümeye gönderici) kanalı manuel olarak tanımlanır. Bir kısmi depo eklediğinizde, bir cluster-receiver kanalı ve tam depolardan birine bağlanacak tek bir cluster-sender kanalı manuel olarak tanımlanır. Diğer cluster-sender kanalları, gerekli olduğunda küme tarafından otomatik olarak tanımlanır. Otomatik olarak tanımlanan cluster-sender kanalları, alıcı kuyruk yöneticisindeki karşılık gelen cluster-receiver kanalı tanımından özelliklerini alır.
Cluster Topics (Küme Konuları)
Cluster topics (kümeli konular), küme özelliği tanımlanmış yönetimsel konulardır. Küme konuları hakkındaki bilgiler, kümedeki tüm üyelere iletilir ve yerel konularla birleşerek, birden çok kuyruk yöneticisini kapsayan bir konu alanının parçalarını oluşturur. Bu, bir kuyruk yöneticisinde bir konuda yayınlanan mesajların, kümedeki diğer kuyruk yöneticilerindeki abonelere iletilmesini sağlar.
Default Cluster Objects (Varsayılan Küme Nesneleri)
	• [UNIX, Linux, Windows, IBM i] Çoklu platformlarda, varsayılan küme nesneleri, bir kuyruk yöneticisi tanımlandığında otomatik olarak oluşturulan varsayılan nesneler setine dahil edilir.
	• [z/OS] z/OS®'te, varsayılan küme nesnesi tanımlamaları özelleştirme örneklerinde bulunabilir.

Cluster Repository (Küme Deposu)
Bir depo, bir kümenin üyesi olan kuyruk yöneticileri hakkında bilgi toplayan bir koleksiyondur.
Depo bilgisi, kuyruk yöneticisi isimlerini, bunların konumlarını, kanallarını, barındırdıkları kuyrukları ve diğer bilgileri içerir. Bu bilgiler, SYSTEM.CLUSTER.REPOSITORY.QUEUE adlı bir kuyrukta mesajlar şeklinde depolanır. Bu kuyruk, varsayılan nesnelerden biridir.
[UNIX, Linux, Windows, IBM i] Çoklu platformlarda, bir IBM® MQ kuyruk yöneticisi oluşturduğunuzda tanımlanır.
[z/OS] IBM MQ for z/OS®'te, kuyruk yöneticisi özelleştirmesinin bir parçası olarak tanımlanır.
Full Repository ve Partial Repository (Tam Depo ve Kısmi Depo)
Genellikle, bir kümedeki iki kuyruk yöneticisi tam depoya sahipken, diğer tüm kuyruk yöneticileri kısmi depolar tutar.
	• Tam depo (Full Repository): Kümedeki her bir kuyruk yöneticisi hakkında tam bilgi barındıran kuyruk yöneticisidir.
	• Kısmi depo (Partial Repository): Sadece, bu kuyruk yöneticisinin mesaj alışverişi yapması gereken kuyruk yöneticileri hakkında bilgi tutar. Bu depo, tam depo bilgileriyle güncellenmek üzere talepte bulunur.
Kısmi depo, genellikle bir kuyruk yöneticisinin kümeye katılımı için gerekli olan tüm bilgileri içerir. Ancak, daha fazla bilgi gerektiğinde, kısmi depo, tam depoya başvurur ve yeni bilgileri alır. Kümelerdeki kuyruk yöneticileri, SYSTEM.CLUSTER.COMMAND.QUEUE kuyruklarını kullanarak depo güncellemelerini talep eder ve alır.
Depo Taşınması (Migration of Repositories)
Küme üyesi kuyruk yöneticilerini taşırken, tam depoların öncelikli olarak taşınması gerekir. Çünkü eski bir depo, yeni bir sürümde tanıtılan yeni özellikleri depolayamaz. Eski depo, bu yeni özellikleri kabul edebilir ancak depolayamaz.

Cluster Queue Manager (Küme Kuyruk Yöneticisi)
Bir kümeye üye olan kuyruk yöneticisidir.
Bir kuyruk yöneticisi, birden fazla kümeye üye olabilir. Her küme kuyruk yöneticisinin, üye olduğu tüm kümelerde benzersiz bir isme sahip olması gerekir.
Bir küme kuyruk yöneticisi, diğer kuyruk yöneticilerine duyurduğu kuyrukları barındırabilir. Ancak bunu yapmak zorunda değildir. Bunun yerine, kümede başka yerlerde barındırılan kuyruklara mesaj gönderebilir ve yalnızca kendisine açıkça yönlendirilmiş yanıtları alabilir.
[z/OS] IBM® MQ for z/OS®'te bir küme kuyruk yöneticisi, bir kuyruk paylaşım grubunun üyesi olabilir. Bu durumda, kuyruk tanımlarını aynı kuyruk paylaşım grubundaki diğer kuyruk yöneticileriyle paylaşır.
Küme kuyruk yöneticileri otonomdur. Tanımladıkları kuyruklar ve kanallar üzerinde tam kontrole sahiptirler. Tanımları, diğer kuyruk yöneticileri tarafından (aynı kuyruk paylaşım grubundaki kuyruk yöneticileri dışında) değiştirilemez. Depo kuyruk yöneticileri, kümedeki diğer kuyruk yöneticilerinin tanımlarını kontrol etmez. Depolar, ihtiyaç duyulduğunda kullanılmak üzere tüm tanımların eksiksiz bir kopyasını tutar. Bir küme, kuyruk yöneticilerinin federasyonudur.
Bir küme kuyruk yöneticisinde bir tanım oluşturduğunuzda veya değiştirdiğinizde, bu bilgi tam depo kuyruk yöneticisine gönderilir. Kümedeki diğer depo yöneticileri, daha sonra güncellenir.
Full Repository Queue Manager (Tam Depo Kuyruk Yöneticisi)
Bir tam depo kuyruk yöneticisi, kümenin kaynaklarının tam bir temsilini tutan bir küme kuyruk yöneticisidir. Her kümeye, kullanılabilirliği sağlamak için iki veya daha fazla tam depo kuyruk yöneticisi kurulmalıdır. Tam depo kuyruk yöneticileri, kümedeki diğer kuyruk yöneticilerinden gelen bilgileri alır ve depolarını günceller. Yeni bilgilerin her iki depo kuyruk yöneticisinde de güncel tutulmasını sağlamak için birbirlerine mesaj gönderirler.
Queue Managers and Repositories (Kuyruk Yöneticileri ve Depolar)
Her küme, kümedeki kuyruk yöneticileri, kuyruklar ve kanallar hakkında en az bir (tercihen iki) tam depo tutan kuyruk yöneticisi içerir. Bu depolar, kümedeki diğer kuyruk yöneticilerinin bilgi güncellemeleri için talepleri de içerir.
Diğer kuyruk yöneticileri, yalnızca iletişim kurmaları gereken kuyruklar ve kuyruk yöneticileri hakkında bilgi içeren kısmi depolar tutar. Kısmi depo, bir kuyruk yöneticisi başka bir kuyruk veya kuyruk yöneticisine erişmesi gerektiğinde, bu bilgiyi almak için sorgular yapar. Bu sorgular, yeni bilgi elde edildiğinde kuyruk yöneticisinin bilgilendirilmesini sağlar.
Her kuyruk yöneticisi, depo bilgilerini SYSTEM.CLUSTER.REPOSITORY.QUEUE adlı bir kuyrukta mesajlar olarak depolar. Kuyruk yöneticileri, depo bilgilerini SYSTEM.CLUSTER.COMMAND.QUEUE adlı bir kuyruk üzerinden değiş tokuş eder.
Bir kümeye katılan her kuyruk yöneticisi, bir cluster-sender (CLUSSDR) kanalı tanımlar. Bu kanal, küme içindeki tam depolara bağlanır. Kuyruk yöneticisi, hangi diğer kuyruk yöneticilerinin tam depolara sahip olduğunu öğrenir. Bu noktadan sonra, kuyruk yöneticisi herhangi bir depodan bilgi talep edebilir. Kuyruk yöneticisi, seçilen depoya bilgi gönderdiğinde, diğer bir depoya da bilgi gönderir (varsa).
Bir tam depo, ona bağlı bir kuyruk yöneticisinden yeni bilgi aldığında güncellenir. Yeni bilgi, başka bir depoya da gönderilir, böylece bir depo kuyruk yöneticisi hizmet dışı olduğunda gecikme riski azaltılır. Tüm bilgi iki kez gönderildiği için, depoların çoğaltmaları atması gerekir. Her bilgi öğesi bir sıra numarasına sahiptir, bu numara depoların çoğaltmaları tanımlamak için kullanılır. Tüm depolar, mesajları değiş tokuş ederek birbirleriyle senkronize edilir.

Cluster Queues (Küme Kuyrukları)
Bir küme kuyruku, bir küme kuyruk yöneticisi tarafından barındırılan ve kümedeki diğer kuyruk yöneticilerine sunulan bir kuyruktur.
Bir küme kuyruk tanımı, kümedeki diğer kuyruk yöneticilerine duyurulur. Kümedeki diğer kuyruk yöneticileri, karşılık gelen bir remote-queue (uzak kuyruk) tanımına ihtiyaç duymadan bir küme kuyruğuna mesaj koyabilir. Bir küme kuyruğu, bir kümeye adlandırılmış liste (cluster namelist) kullanılarak birden fazla kümede duyurulabilir.
Bir kuyruk duyurulduğunda, kümedeki herhangi bir kuyruk yöneticisi bu kuyruğa mesaj koyabilir. Bir mesaj koymak için, kuyruk yöneticisi, tam depolardan (full repositories) kuyruğun hangi kuyruk yöneticisinde barındırıldığını öğrenmelidir. Ardından, mesajın üzerine yönlendirme bilgisi ekler ve mesajı bir küme iletim kuyruğuna (cluster transmission queue) koyar.
Bir küme kuyrugu, IBM® MQ for z/OS®'te, kuyruk paylaşım grubu (queue sharing group) üyeleri tarafından paylaşılan bir kuyruk da olabilir.

Shared Queues ve Cluster Queues Karşılaştırması
Bu bilgi, shared queues (paylaşılan kuyruklar) ve cluster queues (küme kuyrukları) arasındaki farkları anlamanıza ve sisteminiz için hangisinin daha uygun olacağına karar vermenize yardımcı olmak için hazırlanmıştır.
Channel Initiator Maliyetleri
Cluster kuyrukları mesajları kanallar aracılığıyla gönderdiği için, kanal başlatıcı (channel initiator) maliyetlerinin yanı sıra uygulama maliyetlerini de göz önünde bulundurmalısınız. Ağda, kanallar mesajları almak ve göndermek için çalışır, bu da cluster kuyrukları ile daha fazla işlem gücü kullanımına yol açar. Shared kuyruklar ise bu maliyetlere sahip değildir ve bu yüzden cluster kuyruklarına göre mesajları kuyruk yöneticileri arasında taşırken daha az işlem gücü kullanır.
Mesajların Kullanılabilirliği
Bir kuyruğa mesaj gönderildiğinde, cluster kuyrukları, mesajı aktif kanallara bağlı olan bir kuyruk yöneticisine gönderir. Uzak kuyruk yöneticisinde, mesajları işlemek için kullanılan uygulamalar çalışmıyorsa, mesajlar işlenmez ve uygulamalar başladığında işleme alınana kadar bekler. Benzer şekilde, bir kuyruk yöneticisi kapatıldığında, kuyruk yöneticisindeki mesajlar yeniden başlatılana kadar erişilebilir olmaz. Bu durumlar, shared kuyruklarla karşılaştırıldığında daha düşük mesaj kullanılabilirliği anlamına gelir.
Shared kuyruklar kullanıldığında, kuyruk paylaşım grubundaki herhangi bir uygulama gönderilen mesajları alabilir. Kuyruk paylaşım grubundaki bir kuyruk yöneticisini kapatırsanız, mesajlar diğer kuyruk yöneticilerine sunulmaya devam eder ve bu da cluster kuyruklarına göre daha yüksek mesaj kullanılabilirliği sağlar.
Kapasiteler
Bir coupling facility (bir tür özel donanım) diskten daha pahalıdır; bu nedenle, 1.000.000 mesajı yerel bir kuyrukta depolamak, aynı sayıda mesajı depolayabilecek bir coupling facility kurmaktan daha düşük maliyetlidir.
Diğer Kuyruk Yöneticilerine Mesaj Göndermek
Shared kuyruklar, yalnızca bir kuyruk paylaşım grubunda erişilebilir. Bir kuyruk yöneticisini kuyruk paylaşım grubunun dışında kullanmak isterseniz, kanallar kullanmanız gerekir. Bununla birlikte, clustering (kümelenme) ile birden fazla uzak dağıtılmış kuyruk yöneticisi arasında iş yükü dengelemesi yapabilirsiniz.
İş Yükü Dengeleme
Kümelenme (clustering), kanallar ve kuyruk yöneticilerine gönderilen mesajların bir oranını vermek için kullanılabilir. Örneğin, mesajların %60'ını bir kuyruk yöneticisine, %40'ını başka bir kuyruk yöneticisine gönderebilirsiniz. Bu durumda, ilk kuyruk yöneticisinin sistemi aşırı yüklenmiş olsa da, ikinci kuyruk yöneticisinin sistemi boşta olsa da, mesajların çoğunluğu ilk kuyruk yöneticisine gider.
Shared kuyruklarla, iki CICS® sistemi mesaj alabilir. Bir sistem aşırı yüklendiyse, diğer sistem çoğu iş yükünü devralır.

Cluster Kanalları (Cluster Channels)
Her tam depo (full repository) için, her diğer tam depo kuyruk yöneticisine bağlanacak şekilde manuel olarak bir cluster-receiver (CLUSRCVR) kanalı ve bir dizi cluster-sender (CLUSSDR) kanalı tanımlanır. Bir partial repository (kısmi depo) eklediğinizde, manuel olarak bir cluster-receiver kanalı ve yalnızca bir cluster-sender kanalı tanımlarsınız; diğer cluster-sender kanalları, gerektiğinde cluster tarafından otomatik olarak tanımlanır. Otomatik tanımlanan cluster-sender kanalları, karşılık gelen cluster-receiver kanalının tanımından özellik alır.

Cluster-Receiver Kanalı: CLUSRCVR
CLUSRCVR kanal tanımı, bir cluster queue manager'ın (küme kuyruk yöneticisi) diğer kuyruk yöneticilerinden gelen mesajları alabileceği kanalın ucunu tanımlar.
Her cluster queue manager için en az bir CLUSRCVR kanalı tanımlamanız gerekir. Bu kanalı tanımlayarak, kuyruk yöneticisi diğer cluster kuyruk yöneticilerine mesaj alabileceğini gösterir.
Bir CLUSRCVR kanal tanımı, diğer kuyruk yöneticilerinin otomatik olarak karşılık gelen cluster-sender kanalı tanımlarını oluşturmasına da olanak tanır.

Cluster-Sender Kanalı: CLUSSDR
Her full repository kuyruk yöneticisinden her diğer full repository kuyruk yöneticisine manuel olarak bir CLUSSDR kanalı tanımlanır. Full depo kuyruk yöneticileri arasındaki tüm güncellemeler yalnızca bu kanallar üzerinden akar. Bu kanalların manuel olarak tanımlanması, full repository'ler arasındaki ağı açıkça kontrol etmenizi sağlar.
Bir partial repository kuyruk yöneticisi eklediğinizde, yalnızca bir CLUSSDR kanalı tanımlarsınız ve bu kanal bir full repository'ye bağlanır. Başlangıçta hangi full repository'yi seçeceğiniz çok önemli değildir çünkü ilk bağlantı kurulduktan sonra, diğer cluster queue manager nesneleri, gerekli olduğunda otomatik olarak tanımlanır. Bu, kuyruk yöneticinizin full repository'ye cluster bilgilerini göndermesine ve cluster'daki herhangi bir kuyruk yöneticisine mesaj göndermesine olanak tanır.
Otomatik tanımlanan CLUSSDR kanalları, CLUSRCVR kanalının tanımına dayalıdır. Bu nedenle, cluster kanallarındaki tüm özellikler CLUSSDR ve cluster-receiver kanalları için aynı şekilde tanımlanmalıdır veya sadece cluster-receiver kanallarında tanımlanmalıdır.
Otomatik Tanımlanan CLUSSDR Kanalları
Tipik olarak, bir partial repository kuyruk yöneticisini bir cluster'a eklediğinizde, yalnızca iki cluster kanalı tanımlarsınız:
	• CLUSSDR kanalı (cluster-sender) bir full repository kuyruk yöneticisine.
	• CLUSRCVR kanalı (cluster-receiver).
Tanımladığınız CLUSSDR kanalı, kuyruk yöneticisinin cluster ile ilk teması kurmasına olanak tanır. İlk bağlantı kurulduktan sonra, gerekirse cluster, yeni CLUSSDR kanallarını otomatik olarak tanımlar.
Otomatik tanımlanan CLUSSDR kanalı, CLUSRCVR kanalındaki karşılık gelen tanımdan özellik alır. Örneğin, CLUSRCVR kanalını, CONNAME parametresinde bir port numarası belirtmeden tanımladığınızda ve bir CLUSSDR kanalı manuel olarak port numarasıyla tanımladığınızda, otomatik tanımlanan CLUSSDR kanalı, manuel olarak tanımlanan kanalı yerine aldığında port numarasını (CLUSRCVR kanalından alınan) boş bırakır. Bu durumda, varsayılan port numarası kullanılır ve kanal başarısız olur.
Bir CLUSSDR kanalı ile CLUSRCVR kanalı arasındaki yapılandırma farklılıkları, bazı farkların hemen etkili olmasına (örneğin, iş yükü dengeleme parametreleri) ve bazı farkların yalnızca kanal yeniden başlatıldığında etkili olmasına neden olabilir (örneğin, TLS yapılandırması).

Cluster-Sender ve Cluster-Receiver Kanallarının Manuel Tanımlanması
CLUSSDR kanallarını yalnızca full repository'lere bağlanmak için manuel olarak tanımlamalısınız. Bu kanal, partial repository'yi full repository'ye bağlamak veya iki full repository'yi birbirine bağlamak için gereklidir.
Bir CLUSSDR kanalı partial repository'ye veya küme dışındaki bir kuyruk yöneticisine bağlanacak şekilde manuel olarak yapılandırılmamalıdır, çünkü bu durum AMQ9427 ve AMQ9428 gibi hata mesajlarına yol açar. Bu durum geçici bir çözüm olarak kaçınılmaz olabilir, ancak mümkünse manuel tanım, en kısa sürede silinmelidir.

Cluster Konuları (Cluster Topics)

Cluster konuları, cluster özelliği tanımlı olan yönetimsel konulardır. Cluster konuları hakkında bilgi, tüm cluster üyelerine aktarılır ve yerel konularla birleştirilerek, birden fazla kuyruk yöneticisini kapsayan bir topic space oluşturulur. Bu, bir kuyruk yöneticisindeki bir konuya yayımlanan mesajların, cluster içindeki diğer kuyruk yöneticilerindeki abonelere iletilmesini sağlar.

Cluster Konusu Tanımlama
Bir kuyruk yöneticisinde cluster konusu tanımladığınızda, bu cluster konusu tanımı full repository kuyruk yöneticilerine gönderilir. Full repository'ler, ardından bu cluster konusu tanımını tüm cluster kuyruk yöneticilerine ileterek, aynı cluster konusunun clusterdaki herhangi bir kuyruk yöneticisindeki yayıncılara ve abone olanlara sunulmasını sağlar. Cluster konusunun tanımlandığı kuyruk yöneticisi, cluster topic host (cluster konu barındırıcı) olarak bilinir.
Bir cluster konusu, clusterdaki herhangi bir kuyruk yöneticisi tarafından kullanılabilir, ancak cluster konusu üzerindeki herhangi bir değişiklik yalnızca o konunun tanımlandığı kuyruk yöneticisinde yapılabilir (host). Bu değişiklik, ardından full repositories üzerinden clusterdaki tüm üyelere aktarılır.

Cluster Konusu Yapılandırması
Cluster konularını doğrudan yönlendirme (direct routing) veya topic host yönlendirmesi kullanacak şekilde yapılandırma, cluster topic inheritance (cluster konusu mirası) ve wildcard subscriptions (joker karakterli abonelikler) hakkında bilgi için, Cluster Konuları Tanımlama kısmına başvurabilirsiniz.
Cluster konularını görüntülemek için kullanılan komutlar hakkında daha fazla bilgi için, ilgili bilgilere göz atabilirsiniz.

Varsayılan Cluster Nesneleri (Default Cluster Objects)

Çoklu Platformlar için, varsayılan cluster nesneleri, bir kuyruk yöneticisi tanımlandığında otomatik olarak oluşturulan varsayılan nesneler kümesine dahildir. z/OS® üzerinde, varsayılan cluster nesne tanımlamaları özelleştirme örneklerinde bulunabilir.
Not: Varsayılan kanal tanımlarını, diğer kanal tanımlarına benzer şekilde, MQSC veya PCF komutları ile değiştirebilirsiniz. SYSTEM.CLUSTER.HISTORY.QUEUE dışındaki varsayılan kuyruk tanımlarını değiştirmemeniz önerilir.

SYSTEM.CLUSTER.COMMAND.QUEUE
Her cluster’daki kuyruk yöneticisinin, SYSTEM.CLUSTER.COMMAND.QUEUE adlı bir yerel kuyruğu vardır. Bu kuyruk, mesajları full repository'ye iletmek için kullanılır. Mesaj, kuyruk yöneticisi hakkındaki yeni veya değişmiş bilgileri veya diğer kuyruk yöneticileri hakkında bilgi taleplerini içerir. SYSTEM.CLUSTER.COMMAND.QUEUE genellikle boştur.
SYSTEM.CLUSTER.HISTORY.QUEUE
Her cluster’daki kuyruk yöneticisinin, SYSTEM.CLUSTER.HISTORY.QUEUE adlı bir yerel kuyruğu vardır. SYSTEM.CLUSTER.HISTORY.QUEUE, servis amaçlı cluster durumu bilgisinin geçmişini saklamak için kullanılır. Varsayılan ayarlarda, SYSTEM.CLUSTER.HISTORY.QUEUE'nun PUT (ENABLED) olarak ayarlandığı görülür. Geçmiş koleksiyonunu engellemek için ayarı PUT (DISABLED) olarak değiştirebilirsiniz.
SYSTEM.CLUSTER.REPOSITORY.QUEUE
Her cluster’daki kuyruk yöneticisinin, SYSTEM.CLUSTER.REPOSITORY.QUEUE adlı bir yerel kuyruğu vardır. Bu kuyruk, tüm full repository bilgilerini saklamak için kullanılır. Bu kuyruk genellikle bozulmaz ve her zaman doludur.
SYSTEM.CLUSTER.TRANSMIT.QUEUE
Her kuyruk yöneticisinin, SYSTEM.CLUSTER.TRANSMIT.QUEUE adlı yerel bir kuyruğu vardır. Bu kuyruk, cluster'daki tüm kuyruklara ve kuyruk yöneticilerine iletilen mesajlar için varsayılan iletim kuyruğudur. Varsayılan iletim kuyruğunu her cluster-sender kanalı için SYSTEM.CLUSTER.TRANSMIT.QUEUE yerine SYSTEM.CLUSTER.TRANSMIT.ChannelName olarak değiştirebilirsiniz, bunu DEFCLXQ kuyruk yöneticisi özelliğini değiştirerek yapabilirsiniz. SYSTEM.CLUSTER.TRANSMIT.QUEUE'yu silemezsiniz. Bu kuyruk, kullanılan varsayılan iletim kuyruğunun SYSTEM.CLUSTER.TRANSMIT.QUEUE veya SYSTEM.CLUSTER.TRANSMIT.ChannelName olup olmadığını belirlemek için yetkilendirme denetimlerini de tanımlar.
SYSTEM.DEF.CLUSRCVR
Her cluster’da, SYSTEM.DEF.CLUSRCVR adında varsayılan bir CLUSRCVR kanal tanımı vardır. SYSTEM.DEF.CLUSRCVR, cluster’daki bir kuyruk yöneticisinde bir cluster-receiver kanalı oluşturduğunuzda belirtmediğiniz herhangi bir özellik için varsayılan değerler sağlar.
SYSTEM.DEF.CLUSSDR
Her cluster’da, SYSTEM.DEF.CLUSSDR adında varsayılan bir CLUSSDR kanal tanımı vardır. SYSTEM.DEF.CLUSSDR, cluster’daki bir kuyruk yöneticisinde bir cluster-sender kanalı oluşturduğunuzda belirtmediğiniz herhangi bir özellik için varsayılan değerler sağlar.



Publish/Subscribe Messaging
Publish/subscribe messaging (yayınla/abone ol mesajlaşması), bilgi sağlayıcısını ve bu bilgiyi tüketenleri birbirinden ayırmanıza olanak tanır. Gönderen uygulama ve alıcı uygulama birbirlerinin varlıklarından haberdar olmak zorunda değildir; yalnızca bilgi gönderilip alınır.
Point-to-point Mesajlaşma ve Publish/Subscribe Mesajlaşma Arasındaki Farklar
Bir point-to-point (nokta-nokta) IBM® MQ uygulaması, mesajı başka bir uygulamaya gönderebilmek için, o uygulama hakkında bir şeyler bilmek zorundadır. Örneğin, mesajı göndereceği kuyruğun adı gibi, ayrıca kuyruk yöneticisi adı da belirtilmiş olabilir.
IBM MQ Publish/subscribe (yayınla/abone ol) sistemi, hedef uygulama hakkında herhangi bir bilgiye ihtiyaç duymadan, sadece şu adımları gerçekleştirerek iletişim sağlar:
	1. Gönderilecek bilgiyi içeren bir IBM MQ mesajı koyar.
	2. Mesajı, bilgilerin konusunu belirten bir topic (konu) ile ilişkilendirir.
	3. IBM MQ, bu bilginin dağıtımını üstlenir.
Hedef Uygulamanın Bilgisi
Benzer şekilde, hedef uygulamanın da aldığı bilginin kaynağı hakkında hiçbir bilgisi olmasına gerek yoktur.
Yayınla/Abone Ol Sisteminin Temel Yapısı
Basit bir publish/subscribe sisteminde, bir yayıncı, bir kuyruk yöneticisi ve bir abone bulunur. Abone, bir kuyruk yöneticisinde bir abonelik oluşturur, yayıncı bir mesaj gönderir ve kuyruk yöneticisi bu yayını alıcıya iletir.
Tipik Publish/Subscribe Yapısı
Tipik bir publish/subscribe sisteminde birden fazla yayıncı ve birden fazla abone bulunur, farklı konularda ve genellikle birden fazla kuyruk yöneticisi ile çalışılır. Bir uygulama, hem yayıncı hem de abone olabilir.
Publish/Subscribe ve Point-to-Point Arasındaki Farklar
	• Point-to-point mesajı sadece bir tüketici uygulaması tarafından işlenir.
	• Publish/subscribe mesajı, birden fazla abone ilgisini belirttiği sürece, tüm ilgilenen aboneler tarafından işlenir.
Publish/Subscribe Bileşenleri
Publish/subscribe sistemi, abonelerin yayıncılardan mesajlar şeklinde bilgi almasını sağlayan bir mekanizmadır. Yayıncılar ve aboneler arasındaki etkileşimler, kuyruk yöneticileri tarafından kontrol edilir ve IBM MQ standart özellikleri ile yönetilir.
Tek Kuyruk Yöneticisi ile Publish/Subscribe Yapılandırması Örneği
Her bir kuyruk yöneticisi, bir topic'e (konuya) yayımlanan mesajları, o topic'e abone olmuş yerel aboneliklerle eşleştirir. Bir kuyruk yöneticisine bağlı bir uygulamanın yayımladığı mesajlar, ağdaki diğer kuyruk yöneticilerine abone olan ilgili abonelere iletilir. Bu, basit kanalların ötesinde ek yapılandırma gerektirir.
Dağıtılmış Publish/Subscribe Ağları
Dağıtılmış bir publish/subscribe ağı, kuyruk yöneticilerinin mesajları eşleştirip abonelere ilettiği bir yapıdır. Bu sistem, daha karmaşık yapılandırmalar gerektirebilir ve birden fazla kuyruk yöneticisinin yer aldığı bir ağda çalışabilir.

Publish/Subscribe Components
Publish/subscribe, abonelerin yayıncılardan bilgi almasını sağlayan bir mekanizmadır ve bu etkileşimler kuyruk yöneticileri tarafından kontrol edilir. IBM® MQ'nin standart özelliklerini kullanarak, yayıncılar ve aboneler arasındaki etkileşimler yönetilir.
Publish/Subscribe Sistem Yapısı
Tipik bir publish/subscribe (yayınla/abone ol) sistemi birden fazla yayıncı, birden fazla abone ve birçok farklı konudan oluşur, genellikle birden fazla kuyruk yöneticisi de bulunur. Bir uygulama hem yayıncı hem de abone olabilir.
Yayıncılar (Publishers)
Bilgi sağlayıcısı yayıncı olarak adlandırılır. Yayıncılar, konu hakkında bilgi sunar ve bu bilgiyi almakla ilgilenen uygulamaları bilmek zorunda değildir. Yayıncılar, bu bilgiyi mesajlar şeklinde yayınlamak istedikleri yayınlar (publications) olarak üretir ve bu mesajların konusunu tanımlar.
Aboneler (Subscribers)
Bilgiyi tüketen uygulama abone olarak adlandırılır. Aboneler, ilgilendikleri konuyu tanımlayan abonelikler oluşturur. Abonelik, hangi yayınların aboneye iletileceğini belirler. Aboneler birden fazla abonelik oluşturabilir ve birden fazla yayıncıdan bilgi alabilir.
Mesajlar ve Konular (Topics)
Yayımlanan bilgi bir IBM MQ mesajı olarak gönderilir ve bilginin konusu topic (konu) ile tanımlanır. Yayıncı, mesajı yayınlarken konuyu belirtir ve abone, hangi konularda yayın almak istediğini belirtir. Abone yalnızca ilgilendiği konularla ilgili bilgileri alır.
Publish/Subscribe ve Point-to-Point Arasındaki Fark
Yayınla/Abone Ol mesajlaşması, point-to-point (nokta-nokta) mesajlaşmasından farklı olarak, her mesajın belirli bir hedefi içermesi gerekmez. Bu özellik, sağlayıcılar ve tüketicilerin birbirlerinden bağımsız olmasına olanak tanır.
Yayıncılar ve Yayınlar (Publishers and Publications)
IBM MQ publish/subscribe sisteminde, bir yayıncı belirli bir konu hakkında bilgiyi, bir yayın (publication) olarak bir kuyruk yöneticisine sunan bir uygulamadır. Bir yayıncı, birden fazla konu hakkında bilgi yayımlayabilir.
Aboneler ve Abonelikler (Subscribers and Subscriptions)
IBM MQ publish/subscribe sisteminde, bir abone belirli bir konu hakkında bilgi almak için kuyruk yöneticisinden istek yapan bir uygulamadır. Aboneler, aynı veya farklı konularda birden fazla yayıncıdan mesaj alabilir.
Konular (Topics)
Bir topic (konu), publish/subscribe mesajında yayımlanan bilginin konusudur.

Publishers and Publications
IBM MQ publish/subscribe (yayınla/abone ol) sisteminde, bir yayıncı (publisher), belirli bir konu hakkında bilgiyi, yayın (publication) olarak bir kuyruk yöneticisine sunan bir uygulamadır. Yayıncılar, birden fazla konu hakkında bilgi yayımlayabilir.
Yayıncılar, MQPUT komutunu kullanarak daha önce açılmış bir konuya mesaj gönderir; bu mesaj bir yayındır. Yerel kuyruk yöneticisi, yayımlanan mesajı, konuya abone olmuş olan abonelere yönlendirir. Yayınlanan bir mesaj birden fazla abone tarafından tüketilebilir.
Bunun yanı sıra, bir kuyruk yöneticisi, yayınları sadece yerel abonelere değil, aynı zamanda konuyla ilgilenen diğer kuyruk yöneticilerine de dağıtabilir. Bu, doğrudan veya kuyruk yöneticilerinin bir ağı üzerinden yapılabilir.
Bir IBM MQ publish/subscribe ağında, bir yayıncı uygulama aynı zamanda bir abone de olabilir.
Syncpoint Altında Yayınlar
Yayıncılar, MQPUT veya MQPUT1 çağrılarını syncpoint altında yaparak, tüm abonelere teslim edilen mesajları bir iş birimi (unit of work) içinde dahil edebilirler. Eğer MQPMO_RETAIN seçeneği veya topic delivery seçenekleri olan NPMSGDLV veya PMSGDLV ve değer olarak ALL veya ALLDUR belirtilirse, kuyruk yöneticisi, yayıncı MQPUT veya MQPUT1 çağrısının kapsamı içinde içsel MQPUT veya MQPUT1 çağrılarını syncpoint altında kullanır.
Durum ve Olay Bilgisi
Yayınlar, durum yayınları (örneğin, bir hisse senedinin güncel fiyatı) veya olay yayınları (örneğin, o hisse senediyle yapılan bir işlem) olarak sınıflandırılabilir.
Retained (Korunan) Yayınlar
Varsayılan olarak, bir yayın, tüm ilgilenen abonelere gönderildikten sonra atılır. Ancak bir yayıncı, bir yayın kopyasının korunmasını sağlayabilir, böylece gelecekteki abonelere, konuya ilgi gösterdiklerinde bu yayın gönderilebilir.
Syncpoint Altında Yayınlar
IBM MQ publish/subscribe sisteminde, syncpoint yayıncılar veya kuyruk yöneticisi tarafından içsel olarak kullanılabilir.

State and Event Information
Yayınlar, durum yayınları (örneğin, bir hissenin güncel fiyatı) veya olay yayınları (örneğin, bir hisse alım satımı) olarak ikiye ayrılabilir.
Durum Yayınları (State Publications)
Durum yayınları, bir şeyin mevcut durumu hakkında bilgi içerir. Örneğin, bir hisse fiyatı veya bir futbol maçının mevcut skoru gibi. Bir şey olduğunda (örneğin, hisse fiyatı değiştiğinde veya maç skoru değiştiğinde), önceki durum bilgisi artık gerekli değildir çünkü yeni bilgi onu geçersiz kılar.
Bir abone, durum bilgisi almak için, durumu alacağı zaman en güncel versiyonunu almak ister ve durum değiştikçe yeni bilgi alır.
Eğer bir yayın durum bilgisi içeriyorsa, genellikle bu yayın korunan yayın (retained publication) olarak yayımlanır. Yeni bir abone genellikle anında güncel durum bilgisini almak ister; aboneler, bilginin yeniden yayımlanması için bir olayı beklemek istemezler. Bir abone, konuya abone olduğunda, eğer MQSO_PUBLICATIONS_ON_REQUEST veya MQSO_NEW_PUBLICATIONS_ONLY seçenekleri kullanılmazsa, otomatik olarak konunun korunmuş yayını alır.
Olay Yayınları (Event Publications)
Olay yayınları, meydana gelen bireysel olaylar hakkında bilgi içerir, örneğin bir hisse senedi ticareti veya belirli bir golün atılması gibi. Her olay, diğer olaylardan bağımsızdır.
Bir abone, olaylar olduğunda o olaylar hakkında bilgi almak ister.

Korunan Yayınlar (Retained Publications)
Son Güncelleme: 2024-07-02
Varsayılan olarak, bir yayın, tüm ilgilenen abonelere gönderildikten sonra atılır. Ancak bir yayıncı, bir yayının kopyasının korunmasını sağlayabilir, böylece gelecekteki abonelere, konuya ilgi gösterdiklerinde bu yayın gönderilebilir.
Yayınlar, tüm ilgilenen abonelere gönderildikten sonra silinmesi, olay bilgileri için uygun olsa da, her zaman durum bilgisi için uygun değildir. Bir yayını koruyarak, yeni aboneler, bilginin tekrar yayımlanmasını beklemeden ilk durum bilgisini alabilir. Örneğin, bir hisse senedi fiyatına abone olmuş bir abone, hisse fiyatı değişmeden mevcut fiyatı hemen alır.
Kuyruk yöneticisi, her konu için yalnızca bir yayını koruyabilir, bu nedenle bir konuya ait mevcut korunan yayın, yeni bir korunan yayın geldiğinde silinir. Ancak mevcut yayın silinmesi, yeni yayın geldiğinde hemen gerçekleşmeyebilir. Bu nedenle, mümkünse her konu için yalnızca bir yayıncının korunan yayın göndermesi sağlanmalıdır.
Aboneler, MQSO_NEW_PUBLICATIONS_ONLY abone seçeneği kullanarak korunan yayınları almayı istemediklerini belirtebilir. Mevcut aboneler, korunan yayınların birden fazla kopyasını almak için talepte bulunabilir.
Bazı durumlarda, yayınların korunmasını istemeyebilirsiniz, hatta durum bilgileri için:
	• Bir konuya ait tüm abonelikler, herhangi bir yayın yapılmadan önce yapılmışsa ve yeni abonelik beklenmiyorsa, yayınların korunmasına gerek yoktur.
	• Yayınlar sık sık yapılıyorsa (örneğin her saniye), yeni bir abone (veya bir hatadan kurtulan bir abone) mevcut durumu hemen alır, bu yüzden bu yayınları korumaya gerek yoktur.
	• Yayınlar büyükse, her konu için korunan yayını saklamak için büyük bir depolama alanına ihtiyacınız olabilir.
Bir yayının korunmasını sağlamak için MQPMO_RETAIN put-message seçeneğini kullanın. Bu seçenek kullanıldığında ve yayın korunamazsa, mesaj yayımlanmaz ve çağrı MQRC_PUT_NOT_RETAINED hatasıyla başarısız olur.
Eğer bir mesaj korunan bir yayınsa, bu, MQIsRetained mesaj özelliğiyle belirtilir. Bir mesajın sürekliliği, ilk kez yayımlandığında nasıl ise o şekilde kalır.

Syncpoint Altında Yayınlar (Publications Under Syncpoint)
Son Güncelleme: 2024-07-02
IBM MQ publish/subscribe sisteminde, syncpoint, yayıncılar veya kuyruk yöneticisi tarafından içsel olarak kullanılabilir.
Yayıncılar, MQPUT/ MQPUT1 çağrılarını MQPMO_SYNCPOINT seçeneğiyle yaparak syncpoint kullanır. Tüm mesajlar, aboneye teslim edildikçe bir iş birimi içinde yer alır. Bu işlemde, MAXUMSGS kuyruk yöneticisi özelliği, izin verilen maksimum işlenmemiş mesaj sayısını belirtir. Bu limit aşılırsa, yayıncı 2024 (07E8) (RC2024): MQRC_SYNCPOINT_LIMIT_REACHED hata kodunu alır.
Yayıncılar MQPMO_NO_SYNCPOINT ile MQPMO_RETAIN seçeneği veya topic delivery seçenekleri NPMSGDLV/PMSGDLV ile ALL veya ALLDUR değerleriyle MQPUT/ MQPUT1 çağrılarını yaparsa, kuyruk yöneticisi içsel syncpoint'ler kullanarak mesajların belirtilen şekilde teslim edilmesini garanti eder. Eğer limit aşılırsa, yayıncı 2024 (07E8) (RC2024): MQRC_SYNCPOINT_LIMIT_REACHED hata kodunu alabilir.

Subscribers and Subscriptions
Son Güncelleme: 2024-09-05
IBM MQ publish/subscribe modelinde, bir abone (subscriber), bir konu hakkında bilgi almak için bir queue manager (kuyruk yöneticisi) ile iletişime geçen bir uygulamadır. Bir abone, aynı veya farklı konularda birden fazla yayından (publisher) mesaj alabilir.
Abonelikler, MQSC komutu kullanılarak veya uygulamalar tarafından manuel olarak oluşturulabilir. Bu abonelikler, abonenin almak istediği yayınlar hakkında bilgi içerir:
	• Abonenin ilgilendiği konu (topic); eğer joker karakterler (wildcards) kullanılıyorsa, birden fazla konuya çözülmüş olabilir.
	• Yayınlanan mesajlar üzerinde uygulanacak isteğe bağlı seçim dizesi (selection string).
	• Seçilen yayınların yerleştirileceği abone kuyruğu (subscriber queue) ve isteğe bağlı CorrelId (bağlantılı kimlik).
Yerel kuyruk yöneticisi, abonelik bilgilerini saklar ve bir yayın aldığında, aboneliğin konusu ve seçim dizesi ile uyumlu olup olmadığını belirlemek için bu bilgileri tarar. Her eşleşen abonelik için, kuyruk yöneticisi yayını abonenin abonelik kuyruğuna yönlendirir. Bir kuyruk yöneticisinin abonelikler hakkında sakladığı bilgiler, DIS SUB ve DIS SBSTATUS komutları ile görüntülenebilir.
Aboneliğin Silinmesi
Bir abonelik yalnızca aşağıdaki durumlarda silinir:
	• Abone, MQCLOSE çağrısı ile abonelikten çıkarsa (abonelik geçici olarak yapılmışsa).
	• Abonelik süresi dolarsa.
	• Sistem yöneticisi tarafından DELETE SUB komutu ile silinirse.
	• Abone uygulaması sonlanırsa (abonelik geçici olarak yapılmışsa).
	• Kuyruk yöneticisi durdurulup yeniden başlatılırsa (abonelik geçici olarak yapılmışsa).
Mesaj Alırken Kullanılacak Seçenekler
Mesajları alırken, MQGET çağrısında uygun seçenekleri kullanmalısınız. Uygulamanız yalnızca tek bir abonelik için mesajları işlerse, en azından get-by-correlid kullanılmalıdır. Kullanılacak CorrelId, MQSUB çağrısından dönen MQSD.SubCorrelId alanında yer alır.

Managed Queues ve Publish/Subscribe
Abonelik oluşturduğunuzda, managed queuing (yönetilen kuyruk kullanımı) seçeneğini kullanabilirsiniz. Eğer managed queuing kullanıyorsanız, bir abonelik kuyruğu, abonelik oluşturulduğunda otomatik olarak oluşturulur. Yönetilen kuyruklar, aboneliğin dayanıklılığı (durability) ile uyumlu olarak otomatik olarak düzenlenir. Yönetilen kuyruklar kullanmak, yayınları almak için kuyruk yaratmakla uğraşmanıza gerek kalmaması ve tüketilmeyen yayınların, dayanıksız (non-durable) bir abonelik bağlantısı kapandığında otomatik olarak abone kuyruklarından kaldırılması anlamına gelir.

Abonelik Dayanıklılığı (Subscription Durability)
Abonelikler, dayanıklı (durable) veya dayanıksız (non-durable) olarak yapılandırılabilir. Abonelik dayanıklılığı, abone uygulamaları kuyruk yöneticisinden ayrıldığında aboneliğin ne olacağını belirler:
	• Dayanıklı abonelikler: Abonelik, uygulama kuyruk yöneticisinden ayrıldığında bile geçerliliğini sürdürür. Abone tekrar bağlandığında, eski mesajları alabilir.
	• Dayanıksız abonelikler: Abone kuyruk yöneticisinden ayrıldığında abonelik silinir ve eski mesajlara erişim kaybolur.

Seçim Dizesi (Selection Strings)
Bir seçim dizesi (selection string), bir yayının, bir aboneliğe uygun olup olmadığını belirlemek için uygulanan bir ifadedir. Seçim dizesi, joker karakterler (wildcards) içerebilir. Bu joker karakterler, yayınları belirli bir paterne göre filtrelemeyi sağlar.

Topics
Son Güncelleme: 2024-07-02
Bir konu (topic), bir publish/subscribe mesajında yayımlanan bilginin konusudur.
Nokta-nokta (point-to-point) sistemlerde, mesajlar belirli bir hedef adrese gönderilir. Ancak, konuya dayalı publish/subscribe sistemlerinde, mesajlar içeriği tanımlayan bir konuya göre abonelere gönderilir. İçeriğe dayalı sistemlerde ise, mesajlar, mesajın içeriğine göre abonelere gönderilir.
IBM MQ publish/subscribe sistemi, konuya dayalı bir sistemdir. Bir yayıncı (publisher), bir mesaj oluşturur ve bu mesajı, yayın konusunu en iyi şekilde tanımlayan bir konu dizesi (topic string) ile yayımlar. Yayınları almak isteyen bir abone (subscriber), yayın konularını seçen bir abone oluşturur. Kuyruk yöneticisi, abonelikleriyle uyumlu olan yayınları, bu abonelere iletir. Topic Strings konusuna göz atarak, konu dizesinin nasıl çalıştığını daha ayrıntılı öğrenebilirsiniz.
Konuların Hiyerarşik Organizasyonu
Konu başlıkları genellikle hiyerarşik olarak düzenlenir ve '/' karakteri kullanılarak alt konular (subtopics) oluşturulur. Topic Trees başlığı altında, konu ağaçlarının örneklerine bakabilirsiniz. Konular, konu ağacındaki düğüm noktaları (nodes) olabilir. Konular, alt konulara sahip olmayan yaprak düğümleri (leaf nodes) veya alt konuları olan ara düğümleri (intermediate nodes) olabilir.
Yönetimsel Konu Nesneleri
Konular, yönetimsel konu nesneleri (administrative topic objects) ile ilişkilendirilebilir. Bu ilişkilendirme, bir konunun dağıtılıp dağıtılmayacağını, küme içinde yer alıp almayacağını belirlemek gibi özelliklerin atanmasını sağlar. Yönetimsel konu nesnesi, TOPICSTR özniteliği kullanılarak, konu nesnesiyle ilişkilendirilir. Eğer açıkça bir yönetimsel konu nesnesi atanmazsa, konu, en yakın atanan ata konusunun (ancestor topic) özniteliklerini miras alır.

Topic Strings
Yayımladığınız bilgiyi bir konu dizesi (topic string) olarak etiketlersiniz. Konu dizesi, karakter tabanlı veya konu tabanlı joker karakterler (wildcards) kullanılarak bir grup konuya abone olunmasını sağlar.

Topic String'lerinin Birleştirilmesi
Abonelikler oluştururken veya mesajları yayımlamak için konu açarken, konu dizesi iki ayrı alt-konunun birleştirilmesiyle oluşturulabilir. Bir alt konu, uygulama veya yönetimsel komut ile sağlanırken, diğer alt konu, bir konu nesnesiyle ilişkilendirilmiş konu dizesidir. Her iki alt konuyu da bağımsız bir konu dizesi olarak kullanabilir ya da birleştirerek yeni bir konu adı oluşturabilirsiniz.

Topic Trees
Tanımladığınız her konu, konu ağacında bir eleman ya da düğüm olur. Konu ağacı, başlangıçta boş olabilir veya daha önce MQSC veya PCF komutları kullanılarak tanımlanan konuları içerebilir. Yeni bir konu, ya create topic komutları ile ya da ilk kez bir yayın veya abonelikte belirterek tanımlanabilir.

Administrative Topic Objects
Bir yönetimsel konu nesnesi kullanarak, konulara belirli, varsayılan olmayan öznitelikler atayabilirsiniz.

Streams and Topics
Queued publish/subscribe sisteminde, yayın akışları (streams) kavramı vardır. Bu, entegre publish/subscribe modelinde bulunmaz. Yayın akışları, farklı konular için bilginin aktarılmasını ayrı bir şekilde sağlar. Akış, üst düzey bir konu olarak uygulanır ve yönetimsel olarak farklı bir konu tanımlayıcısına (topic identifier) bağlanabilir.

Subscription Points and Topics
Adlandırılmış abone noktaları (subscription points), konular ve konu nesneleri tarafından taklit edilir (emulate).

opic Strings
Son Güncelleme: 2024-12-06
Konu dizesi (topic string), bir publish/subscribe mesajının konusunu tanımlayan karakter dizisidir. Topic strings kullanılarak yayımlanan bilgilere etiketler eklenir. Konu dizesini oluştururken istediğiniz karakteri kullanabilirsiniz, ancak bazı karakterlerin özel anlamları vardır ve dikkatli kullanılması gerekir. Bu karakterler, konunun yapılandırılmasında ve aboneliklerde kullanılır.
Özel Anlamı Olan Karakterler
	1. Ön ek (/)
		○ Konu seviyeleri ayıran karakterdir. / karakterini, konu dizesini yapılandırarak konu ağacı oluşturmak için kullanabilirsiniz.
		○ Boş konu seviyelerinden (//) kaçının, çünkü bu, konu hiyerarşisinde boş bir düğüme karşılık gelir.
	2. Raş işareti (#)
		○ Birden fazla seviye için joker karakter olarak kullanılır ve / ile birlikte kullanılır.
		○ Aboneliklerde bu karakter, birden fazla seviyedeki tüm konuları kapsar. Ancak, yayıncı tarafında, bu karakter doğrudan konu dizesinde kullanılamaz.
	3. Artı işareti (+)
		○ Sadece bir seviye için joker karakter olarak kullanılır ve / ile birlikte kullanılır.
		○ Bir seviyedeki tüm konuları kapsar, ancak sadece tek bir seviyede geçerlidir. Ayrıca, bu karakterin yayıncı tarafından konu dizesinde kullanılması da dikkat gerektirir.
Örnek Konu Dize Örnekleri
	• IBM/Business Area#/Results
	• IBM/Diversity/%African American

Wildcard Scheme (Joker Karakter Kullanım Yöntemleri)
İki farklı wildcard şeması, çoklu konulara abone olmayı sağlar. Bu şemalardan birini seçmek, abone olma işlemi sırasında yapılır:
	1. MQSO_WILDCARD_TOPIC
		○ Topic-based wildcard şeması kullanarak konulara abone olun. Bu, varsayılan seçenektir.
	2. MQSO_WILDCARD_CHAR
		○ Character-based wildcard şeması kullanarak konulara abone olun.

Topic-based Wildcard Scheme
Topic-based wildcards (Konuya dayalı joker karakterler), abonelerin birden fazla konuya aynı anda abone olmasını sağlar. Bu şema, çoklu seviye ve tekli seviye joker karakterlerini içerir.
Joker Karakterleri
	• Çoklu Seviye Joker (#)
		○ Bu joker karakteri, birden fazla seviyeyi kapsayacak şekilde kullanılır ve yalnızca aboneliklerde geçerlidir.
	• Tekli Seviye Joker (+)
		○ Bu karakter, yalnızca tek bir seviyede geçerlidir.
Konu Dizesi Örneği
	• USA/+/Results → USA/Software/Results, USA/Services/Results, USA/Hardware/Results

Character-based Wildcard Scheme
Character-based wildcard şeması, konulara abone olmayı sağlar ancak geleneksel karakter eşleşmesi kullanır. Bu şemada joker karakterler, belirli bir karakter dizisi ile eşleşir ve farklı özelliklere sahip olabilir.

Topic Trees
Her tanımladığınız konu (topic), bir konu ağacının elemanı ya da düğümüdür. Konu ağacı, konuları hiyerarşik bir yapıya yerleştirmenize olanak tanır. Hiyerarşik yapı, konular arasında düzenli bir ilişki sağlar.
	• Konuların Yapılandırılması: Konular, kök düğümünden (root) başlayarak alt düğümlere doğru organize edilir.
	• Örnek: USA/Alabama, USA/Alaska gibi.

Administrative Topic Objects
Yönetimsel konu nesneleri, belirli konulara özel öznitelikler atamanıza olanak tanır. Bu nesnelerle, konu ağacındaki belirli düğümlere özgü yönetimsel ayarları yapabilirsiniz.
	• Inheritance (Miras Alma): Konu nesneleri, kendi özelliklerini en yakın ebeveyn konusundan miras alır.
Örnek Kullanım
	• DURSUB: Bir konu nesnesinin abone olma özellikleri gibi öznitelikler, ebeveynlerden miras alınabilir.

Wildcard Property (Joker Karakteri Özelliği)
WILDCARD özniteliği, konu nesnelerindeki joker karakterlerin nasıl işleneceğini belirler. Bu öznitelik, BLOCK veya PASSTHRU değerlerine sahip olabilir.
	• PASSTHRU: Joker karakterlerle yapılan aboneliklerde daha az özgül konularda yayınlar alınabilir.
	• BLOCK: Joker karakterlerle yapılan aboneliklerde, konuya ve alt konulara yayın gönderilmesini engeller.

Streams and Topics
Streams, IBM MQ'da yayın akışlarını temsil eder. Bir stream, adlandırılmış bir konu alanını temsil eder ve bu alanın içinde konular olabilir. Bu özellik, farklı yayın türleri için bilgilerin ayrılmasını sağlar.

Subscription Points and Topics
Subscription points (Abone noktaları), farklı topic space alanları arasında geçiş yapmaya olanak tanır ve belirli konulara abone olurken kullanılabilir. Bu noktalar, konuların birbirinden bağımsız şekilde yönetilmesini sağlar.

Tek Bir Kuyruk Yöneticisi ile Publish/Subscribe Yapılandırması Örneği
Bu yapılandırma, tek bir kuyruk yöneticisiyle çalışan temel bir publish/subscribe (yayınla/abone ol) sistemini gösterir. Bu sistemde, kuyruk yöneticisi yayınları alır ve abone olan kullanıcılara uygun olan bilgileri yönlendirir.
Yapılandırma Detayları
	1. Yayıncılar (Publishers):
		○ Yayıncı 1: Spor sonuçları hakkında bilgi yayınlıyor ve Sport (Spor) başlığını kullanıyor.
		○ Yayıncı 2: Hisse senedi fiyatları hakkında bilgi yayınlıyor ve Stock (Hisse Senedi) başlığını kullanıyor.
		○ Yayıncı 3: Film incelemeleri hakkında bilgi yayınlıyor ve Films (Filmler) başlığını kullanıyor. Ayrıca Televizyon programları hakkında bilgi yayınlıyor ve TV başlığını kullanıyor.
	2. Aboneler (Subscribers):
		○ Abone 1: Spor sonuçları ve hisse senedi fiyatları ile ilgileniyor. Bu abone, Sport ve Stock başlıklarında yayınlanan bilgileri alacak.
		○ Abone 2: Film incelemeleri ile ilgileniyor. Bu abone, Films başlığındaki yayınları alacak.
		○ Abone 3: Spor sonuçları ile ilgileniyor. Bu abone, Sport başlığındaki yayınları alacak.
Bu yapılandırmada, hiçbir abone televizyon programlarına (TV başlığı) ilgi göstermiyor, dolayısıyla bu başlık altındaki yayınlar abonelere gönderilmeyecek.
Yapılandırma Şeması
	• Yayıncılar yayınlarını kuyruk yöneticisine gönderir, her yayın bir konu başlığı ile etiketlenir.
	• Kuyruk Yöneticisi, abonelerin hangi başlıklara abone olduğunu kontrol ederek, doğru yayınları doğru abonelere iletir.

Nasıl Çalışır?
	• Kuyruk yöneticisi, yayın başlıkları ile abonelikleri karşılaştırarak yayınları doğru şekilde yönlendirir.
	• Bir abone, ilgilendiği konu başlıklarını belirterek abonelik oluşturur.
	• Bir yayıncı, bir yayın gönderdiğinde, kuyruk yöneticisi abonelik bilgilerini kontrol eder ve başlıklarıyla eşleşen abonelere yönlendirir.
	• Aboneler, sadece ilgilendikleri başlıklar altında yapılan yayınları alır.
Bu yapı, yayıncılar ile aboneler arasındaki bağımlılığı ortadan kaldırır, yani yayıncılar, verilerini kimin aldığını bilmek zorunda değildir. Benzer şekilde, aboneler de hangi yayıncıdan bilgi aldıklarını bilmek zorunda değildir.

Bu basit yapılandırma, publish/subscribe mesajlaşma sisteminin temel işleyişini gösterir. Konulara göre dinamik olarak yönlendirilmiş yayınlarla, verinin kaynağına veya alıcıya doğrudan adresleme yapılması gerekmez.

Dağıtık Publish/Subscribe Ağları

Dağıtık publish/subscribe sistemi, birden fazla kuyruk yöneticisinin birbirine bağlı olduğu bir yapıdadır. Bu yapıda, her kuyruk yöneticisi, yayınlanan mesajları abone olan istemcilere (subscriber) iletmek için yerel abonelikleri kontrol eder. Eğer birden fazla kuyruk yöneticisi varsa, bir kuyruk yöneticisi tarafından yayımlanan bir mesaj, ağdaki diğer kuyruk yöneticilerine bağlanan abonelere iletilir.
Dağıtık Publish/Subscribe Yapısının Temel Özellikleri:
	1. Yayıncılar ve Aboneler Arasındaki Bağlantı:
		○ Dağıtık publish/subscribe yapılandırmasında, her kuyruk yöneticisi bir "topic" (konu) için mesajları yayınlar.
		○ Birden fazla kuyruk yöneticisi birbirine bağlı olabilir ve bu sayede mesajlar, bir kuyruk yöneticisinden başka bir kuyruk yöneticisine aktarılabilir. Bu da, farklı sistemlerdeki kuyruk yöneticilerinin birbirleriyle haberleşmesini sağlar.
	2. Queue Manager Bağlantıları:
		○ Kuyruk yöneticileri birbirine doğrudan bağlanabilir veya publish/subscribe kümesi (cluster) oluşturulabilir. Bu küme, kuyruk yöneticilerinin birbirlerine bağlanmasını ve yayınların abonelere iletilmesini sağlar.
	3. Kuyruk Yöneticisi İlişkileri:
		○ İki kuyruk yöneticisi örneği üzerinden açıklayalım:
			§ Yayıncı 4 bir kuyruk yöneticisi üzerinden Hava Durumu ve Trafik Bilgisi yayınlar.
			§ Abone 4, trafik bilgisi konusunda abone olur.
			§ Abone 3, farklı bir kuyruk yöneticisi kullanıyor olmasına rağmen Hava Durumu bilgisi almak için abone olur.
		○ Bu bağlantılar sayesinde, farklı kuyruk yöneticilerine bağlanan aboneler bile mesaj alabilir.
Publish/Subscribe Kümesi (Cluster) Yapılandırması:
	• Cluster (kümeler) ile kuyruk yöneticileri arasındaki mesaj iletimi daha düzenli hale gelir. Küme içindeki her kuyruk yöneticisi, bir topic (konu) üzerinde yayın yapan bir yayıncı olabilir veya bu mesajları alıp işleyen bir abone olabilir.
Cluster’da Mesaj Yönlendirme:
		○ Doğrudan Yönlendirme: Bir kuyruk yöneticisinden gelen mesaj, doğrudan diğer kuyruk yöneticilerine gönderilir.
		○ Topic Host Yönlendirme: Mesajlar önce bir topic host kuyruk yöneticisi üzerinden geçer ve buradan diğer kuyruk yöneticilerine iletilir.
Dağıtık Sistemlerde Mesaj Dağıtımı:
	• Mesaj Dağıtım Yöntemleri:
		1. Mesajları yalnızca gerekli kuyruk yöneticilerine iletmek: Yalnızca ilgili abonelikleri barındıran kuyruk yöneticilerine mesaj gönderilir. Bu, daha verimli bir yöntemdir.
		2. Tüm kuyruk yöneticilerine mesaj iletmek: Mesajlar, tüm kuyruk yöneticilerine iletilir ve her kuyruk yöneticisi, yalnızca kendi abonelikleriyle eşleşenleri alır. Bu yöntem, daha az verimlidir ancak abone bilgilerini paylaşmayı gerektirmez.
Küme ve Hiyerarşi Yapılandırmaları:
	• Publish/Subscribe Hiyerarşileri: Dağıtık sistemlerde, kuyruk yöneticilerinin bir ağaç yapısı şeklinde düzenlenmesi sağlanabilir. Hiyerarşiler, her bir kuyruk yöneticisinin ana (parent) ve çocuk (child) ilişkisi kurarak mesaj iletiminin daha kontrollü olmasını sağlar.
Örnek:
		○ QM3 ve QM4 kuyruk yöneticilerine gönderilen yayınlar, QM2 üzerinden QM1'e iletilir ve en sonunda QM3 ve QM4'teki abonelere ulaşır.
	• Proxy Abonelikler: Bir kuyruk yöneticisi başka bir kuyruk yöneticisi üzerinden bir topice abone olduğunda, proxy abonelik oluşur. Bu, abone olan kuyruk yöneticisi tarafından otomatik olarak yapılır, yani proxy abonelikleri manuel olarak oluşturmazsınız.
Mesajların Dağıtımı ve Abone Yönetimi:
	• Publication Scope (Yayın Kapsamı): Yayınlar, yalnızca ilgili abonelikleri olan kuyruk yöneticilerine gönderilir. Eğer bir kuyruk yöneticisi bir abone barındırmıyorsa, o yöneticiden yayın almaz.
	• Subscription Scope (Abonelik Kapsamı): Abonelikler, yalnızca yerel kuyruk yöneticilerine mi yoksa uzaktaki kuyruk yöneticilerine de mi yayın iletilmesi gerektiğini kontrol eder.
Topic Alanları (Topic Spaces):
	• Bir topic alanı, abone olabileceğiniz ve yayın yapabileceğiniz konu başlıkları kümesidir. Her kuyruk yöneticisi, dağıtık publish/subscribe ağında, abone olduğu ve yayın yaptığı konuları içerir.

Özetle:
IBM MQ'daki dağıtık publish/subscribe sistemi, mesajların birden fazla kuyruk yöneticisi üzerinden abonelere ulaşmasını sağlayan güçlü bir yapıdır. Bu yapı, aboneliklerin yönetilmesi, mesajların yönlendirilmesi ve kuyruk yöneticileri arasındaki etkileşimin verimli şekilde yapılması için çeşitli yöntemler sunar. Küme ve hiyerarşi yapıları, mesajların daha kontrollü bir şekilde iletilmesini sağlar.
Bu yapıyı kullanarak, birden fazla kuyruk yöneticisini birbirine bağlayabilir, mesajları farklı lokasyonlarda bulunan abonelere iletebilirsiniz.

Publish/Subscribe Kümesi Son Güncelleme: 2024-07-02
Bir publish/subscribe kümesi (yayınla/abone ol kümesi), bir grup kuyruk yöneticisinin birbirine bağlandığı bir yapıdır ve bu kümede, yayımlanan mesajlar yayın yapan uygulamalardan, kümedeki herhangi bir kuyruk yöneticisinde bulunan abonelere otomatik olarak iletilir. Yayınların bir publish/subscribe kümesinde nasıl yönlendirileceği konusunda iki seçenek vardır: doğrudan yönlendirme (direct routing) ve topic host yönlendirme (topic host routing). Hangi yönlendirme türünün kullanılacağı, kümenin büyüklüğüne ve beklenen aktivite modeline bağlıdır.
Publish/Subscribe Kümesi Yapılandırması
	• Publish/subscribe kümesi, standart IBM® MQ kümesi gibi çalışır. Kümedeki kuyruk yöneticileri birbirine fiziksel olarak bağlı olabilir veya farklı fiziksel makinelerde olabilir.
	• Kuyruk yöneticileri birbiriyle cluster kanalları (küme kanalları) aracılığıyla otomatik olarak bağlantı kurar.
	• Bu küme yapılandırmasında, bir topic objesi (konu nesnesi) tanımlanır. Bu topic objesinin küme içinde paylaşılması sağlanır. Yayıncılar ve aboneler bu topic objelerini küme içindeki herhangi bir kuyruk yöneticisine bağlanarak mesajları alabilir.
Yönlendirme Seçenekleri
Yayınlar küme içinde iki farklı şekilde yönlendirilebilir:
	1. Doğrudan Yönlendirme (Direct Routing):
		○ Doğrudan yönlendirme, her kuyruk yöneticisinin, diğer kuyruk yöneticilerine doğrudan bağlanarak, yayımlanan mesajları abonelere iletmesini sağlar.
		○ Bir topic objesi yalnızca bir kuyruk yöneticisinde tanımlandığında, tüm kuyruk yöneticileri bu topic objesinden haberdar olur ve abone olan her bir kuyruk yöneticisi doğrudan birbirine bağlanır.
		○ Bu, daha doğrudan bir yol sağlar ancak küme içindeki her kuyruk yöneticisinin, diğer tüm kuyruk yöneticilerine bağlanması gerektiği için daha fazla kanal bağlantısı gerektirir.
	2. Topic Host Yönlendirme (Topic Host Routing):
		○ Bu yönlendirme yöntemi, yayınların önce topic host (konu ev sahibi) kuyruk yöneticisine yönlendirilmesini ve ardından bu yöneticinin mesajları abone olunan diğer kuyruk yöneticilerine iletmesini sağlar.
		○ Burada yalnızca topic host kuyruk yöneticileri, diğer tüm kuyruk yöneticilerinin hangi topic'lere abone olduğunu bilmektedir.
		○ Bu yöntem, doğrudan yönlendirmeye göre daha uzun bir yol sağlar, ancak avantajı, yalnızca topic host kuyruk yöneticilerinin, kümedeki diğer kuyruk yöneticileri hakkında bilgi sahibi olmasıdır.
Yayın Akışı ve Performansı
	• Doğrudan Yönlendirme:
		○ Bir topic objesi tanımlandığında, bu topic objesinin küme içindeki tüm kuyruk yöneticileri tarafından kullanılabilmesi sağlanır.
		○ Mesajlar doğrudan yayımlanan kuyruk yöneticisinden, ilgili abone kuyruk yöneticilerine iletilir.
		○ Her mesaj yalnızca, mesajı abone olarak kabul eden kuyruk yöneticilerine gönderilir.
	• Topic Host Yönlendirme:
		○ Yayınlar, bir topic host kuyruk yöneticisi aracılığıyla yönlendirilir. Topic host kuyruk yöneticileri, yalnızca kendilerine tanımlanan topic objelerinin abone bilgilerini tutar.
		○ Bu tür yönlendirme, her kuyruk yöneticisinin tüm küme üyelerine doğrudan bağlantı kurmasını engeller ve yayınların yalnızca topic host kuyruk yöneticilerine yönlendirilmesini sağlar.
Topic ve Abonelik Kapsamı (Scope)
	• Topic Kapsamı (Topic Scope): Bu, bir topic'in küme içindeki diğer kuyruk yöneticilerine iletilip iletilmeyeceğini kontrol eder.
	• Abonelik Kapsamı (Subscription Scope): Aboneliklerin, bir kuyruk yöneticisi üzerinde yapılan yayınlardan başka bir kuyruk yöneticisi üzerinde yapılan yayınlara kadar yayılan şekilde olup olmayacağını kontrol eder.
Küme Yapısındaki Diğer Konular
	• Proxy Abonelikler: Küme içinde bir kuyruk yöneticisi, başka bir kuyruk yöneticisinde yapılan bir topic aboneliği için otomatik olarak proxy abonelik oluşturur. Bu, her bir topic için aboneliklerin kuyruk yöneticileri arasında taşınmasını sağlar.
	• Yayınların Dağıtımı: Yayınların nasıl dağıtılacağı, iki yaklaşımdan biriyle yapılabilir:
		1. Yayınlar, yalnızca yayınlanan topic ile ilgili abone olan kuyruk yöneticilerine gönderilir.
		2. Yayınlar, tüm kuyruk yöneticilerine gönderilir ve her kuyruk yöneticisi, yalnızca abonelikle eşleşen yayınları alır.
Sonuç
	• Doğrudan Yönlendirme ile yayınlar daha hızlı bir şekilde doğrudan iletilir, ancak küme içindeki tüm kuyruk yöneticileri birbirine bağlanır. Bu yöntem, daha fazla kanal bağlantısı ve veri trafiği gerektirir.
	• Topic Host Yönlendirme daha az kanal bağlantısı gerektirir ve yayınları, yalnızca belirli topic'leri barındıran kuyruk yöneticileri üzerinden yönlendirir. Ancak bu yöntem, biraz daha uzun bir yol sağlar.
Hangi yöntemi seçmeniz gerektiği, kümenizin büyüklüğüne ve beklenen trafik modeline göre değişecektir.

Publish/Subscribe Hiyerarşileri

Bir publish/subscribe hiyerarşisi, kuyruk yöneticilerinin birbiriyle kanallar aracılığıyla bağlandığı ve her bir kuyruk yöneticisinin bir "ebeveyn-çocuk" ilişkisine sahip olduğu bir yapıdır. Bu yapıda, bir yayıncıdan gelen mesajlar, hiyerarşideki doğrudan ilişkiler aracılığıyla abonelere iletilir. Bazen mesajların hedef abonelere ulaşması için birkaç "atlama" (hop) yapılabilir.
	• Mesaj Dağıtımı: Bir kuyruk yöneticisi, yayınlanan mesajı abone olan diğer kuyruk yöneticilerine iletmek için yalnızca bir kez mesaj gönderir. Yani, bir mesaja birden fazla abonelik olsa bile, aynı kuyruk yöneticisinden birden fazla mesaj gönderilmez.
	• Mesajın Dağıtılması: Mesaj, bir kuyruk yöneticisinde bir veya daha fazla abonelik bulunduğunda, bu kuyruk yöneticisine ulaştığında, mesaj her bir abonelik için kopyalanarak iletilir.
Proxy Abonelikler

Bir proxy aboneliği, bir kuyruk yöneticisinin başka bir kuyruk yöneticisinde yayımlanan konulara olan abonelikleri temsil ettiği bir yapıdır. Yani, bir kuyruk yöneticisi, başka bir kuyruk yöneticisinde yayımlanan bir konuya abone olur ve bu abonelik, diğer kuyruk yöneticileriyle paylaşılır.
	• Proxy Aboneliklerin Dağıtılması: Bu abonelikler, kuyruk yöneticileri arasında otomatik olarak yayıldığı için, bir kuyruk yöneticisindeki abonelikler, başka bir kuyruk yöneticisinde yayımlanan konuya ulaşabilir. Bu, kuyruk yöneticileri arasında mesajların doğru bir şekilde dağılmasını sağlar.
	• Yayınlar ve Proxy Abonelikler: Bir kuyruk yöneticisi tarafından yayımlanan mesajlar, proxy abonelikleri aracılığıyla tüm ilgili kuyruk yöneticilerine iletilir.
	• Aboneliklerin Performansı: Proxy aboneliklerinin yayıldığı süre, performansı etkileyebilir. Aboneliklerin güncellenmesi ve yönlendirilmesi sırasında gecikmeler yaşanabilir, bu nedenle abonelik performansı göz önünde bulundurulmalıdır.
Yayın Birleştirme
	• Proxy Abonelik Birleştirme: Aynı konu için yapılan birden fazla proxy aboneliği, yalnızca bir kopya olarak iletilir. Yani, bir konuya olan proxy abonelikleri topluca birleştirilir ve gereksiz mesajlar gönderilmez.
	• Yayın Birleştirme: Eğer aynı konuya birden fazla abonelik varsa, sadece bir yayın kopyası gönderilir. Bu, mesajların fazla bir şekilde çoğaltılmasının önüne geçer ve verimli bir dağıtım sağlanır.
Yayın Kapsamı (Publication Scope)

Yayın Kapsamı, bir yayın mesajının küme içindeki diğer kuyruk yöneticilerine iletilip iletilmeyeceğini kontrol eder.
	• QMGR: Yayın yalnızca yerel abonelere gönderilir, uzak kuyruk yöneticilerine gönderilmez.
	• ALL: Yayın hem yerel hem de uzak abonelere gönderilir.
	• ASPARENT: Yayın, üst konu nesnesinin (parent topic) yayınına benzer şekilde hareket eder.
Bu özellik, küme içindeki mesajların hangi kuyruk yöneticilerine iletileceğini belirler ve bu sayede hangi kuyruk yöneticilerinin daha fazla veri trafiği yükü alacağını kontrol edebilirsiniz.
Abonelik Kapsamı (Subscription Scope)

Abonelik Kapsamı, bir kuyruk yöneticisindeki aboneliğin, sadece yerel kuyruk yöneticilerinden mi yoksa uzak kuyruk yöneticilerinden de mesaj alıp almayacağını kontrol eder.
	• QMGR: Abone, yalnızca yerel yayınları alır ve proxy abonelikler uzak kuyruk yöneticilerine iletilmez.
	• ALL: Proxy abonelikler, uzak kuyruk yöneticilerine iletilir ve abone hem yerel hem de uzak yayınları alır.
	• ASPARENT: Abonelik, üst konu nesnesinin (parent topic) abonelik kapsamını kullanır.
Bu özellik, bir aboneliğin yalnızca yerel yayınları alıp almayacağını, yoksa uzak kuyruk yöneticilerinden gelen yayınları da alıp almayacağını belirler. Küme yapısının genişliği ve aboneliklerin kapsamı, verimliliği önemli ölçüde etkileyebilir.
Topic Alanları (Topic Spaces)

Topic alanı, belirli bir kuyruk yöneticisinde abone olunabilen ve yayımlanabilen konu (topic) setini ifade eder. Publish/subscribe topolojisinde, bir kuyruk yöneticisi hem yerel hem de bağlı olduğu diğer kuyruk yöneticilerinden aldığı konuları içeren bir topic alanına sahip olabilir.
	• Cluster Konuları ve Yerel Konular: Bir publish/subscribe kümesinde yerel konular, CLUSTER özelliği olmayan konu nesneleriyle ilişkilendirilmiştir. Bu konular yalnızca yerel kuyruk yöneticilerinde kullanılabilirken, cluster konusu olan konular, küme içinde tüm kuyruk yöneticilerinde kullanılabilir.
	• Cluster Topic Objeleri ve Proxy Abonelikler: Eğer bir konu, cluster topic objesi ile ilişkilendirilmişse, bu konuya yapılan abonelikler, kümedeki tüm kuyruk yöneticilerinde proxy aboneliklerle paylaşılır. Ancak yerel konulara yapılan abonelikler yalnızca yerel kuyruk yöneticilerinde geçerlidir.
Cluster’lar ve Hiyerarşiler Arasındaki Farklar
	• Publish/subscribe Kümesi: Kümedeki tüm kuyruk yöneticileri aynı topic alanını paylaşır, ancak bir topic'in yalnızca küme içindeki diğer kuyruk yöneticileriyle paylaşılması gerekir.
	• Publish/subscribe Hiyerarşisi: Hiyerarşi yapısındaki kuyruk yöneticileri, daha geniş bir topic alanına sahip olabilirler ve bu durum bir kuyruk yöneticisinin, bağlı olduğu diğer kuyruk yöneticilerinde yayımlanan konulara abone olabilmesini sağlar.
Özet
	• Publish/subscribe kümeleri ve hiyerarşileri, kuyruk yöneticilerinin yayınları ve abonelikleri farklı yapılandırmalarla yönlendirmelerini sağlar.
	• Proxy abonelikler, abone olunan konuların diğer kuyruk yöneticilerine iletilmesini sağlar, ancak bu özellik trafik ve gecikme açısından dikkatle yönetilmelidir.
	• Yayın ve abonelik kapsamları, hangi kuyruk yöneticilerinin yayınları ve abonelikleri alacağını belirler ve sistemin verimli çalışmasını sağlamak için dikkatlice yapılandırılmalıdır.



IBM® MQ için yüksek erişilebilirlik (HA) çözümleri, platforma ve sunulan özelliklere göre farklılık gösterir. Bu çözümler, çeşitli yapılandırmalarla kullanılabilir ve aşağıdaki tablolarda her çözümün özellikleri ve avantajları/olası dezavantajları karşılaştırılmaktadır.
Yüksek Erişilebilirlik (HA) Çözümleri Karşılaştırması
Özellikler	Native HA	RDQM	IBM MQ Appliance	Multi-instance Queue Managers
Donanım Gereksinimi	Minimum iki OpenShift Compute Node (maksimum erişilebilirlik için üç node gerekli)	Üç node gerekli	M2003A/B fiziksel cihaz - 32 işlemci, 256 GB RAM	İki node gerekli
İşletim Sistemi	Linux	Linux	IBM MQ Appliance firmware	Windows veya Unix varyasyonları
Ek Yazılım Gereksinimi	Red Hat OpenShift Container Platform (OCP)	DRBD, Pacemaker	Yok	Yok
VM veya Konteyner	Konteyner tabanlı	VM veya bare metal	Queue manager'lar cihazda çalışır	VM, bare metal veya konteyner
Depolama	Kalıcı Depolama Bloğu (ReadWriteOnce)	Her node için volume group (drbdpool)	Cihazlar 4x 3.2 TB SSD RAID10 disk içerir	NFS v4 paylaşımlı dosya sistemi gerekli, dosya sistemi kilitleri kullanılır
HA Yeteneği	Evet	Evet	Evet	Evet
DR Yeteneği	Henüz değil	Evet	Evet	Hayır (Depolama replikasyonu ile DR sağlanabilir)
Diğer Ekiplerin Bağımlılığı	OpenShift / Kubernetes kümesi yöneticisi grubu	OS ekibi, ağ ekibi, depolama ekibi	Ağ ekibi (IBM MQ Appliance, MQ ekibine tamamen kontrol sağlar)	OS ekibi, ağ ekibi, depolama ekibi
Aktif / Aktif Yeteneği	Hayır	Evet	Evet	Hayır
Hem HA Hem DR Replikasyonu	Hayır	Evet	Evet	Hayır
Performans	N/A	HA yapılandırmasında hafif performans etkisi	En iyi performans (örneğin, M2002 modelinde 500.000 mesaj/sn)	N/A
Güvenlik Notları	Root erişimi gerekli bazı RDQM komutları için	-	1. Genel amaçlı OS yok	-
			2. Dijital imzalı ve şifrelenmiş firmware
			3. Uygulama kodu cihazda çalıştırılamaz
			4. Cihaz kullanıcıları ve mesajlaşma kullanıcıları ayrıdır
Lisans Denetimi	IBM License Service	ILMT	N/A	ILMT
Lisanslama	Tüm konteynerler ve pod'lar lisanslanmalı	Bir node tam IBM MQ lisansı, iki node IBM MQ High Availability Replica	Tüm 32 işlemci A modelde kullanılabilir, B modelde 8 işlemci	Bir node tam IBM MQ lisansı, bir node IBM MQ High Availability Replica
Önerilen Maksimum Latency HA için	10 ms	5 ms	10 ms	N/A
Önerilen Maksimum Latency DR için	N/A	50 ms	100 ms	N/A

Yüksek Erişilebilirlik (HA) Çözümlerinin Karşılaştırmalı Avantajları
Özellikler	Native HA	RDQM	IBM MQ Appliance	Multi-instance Queue Managers
Avantajlar	1. Üçüncü parti kütüphanelere veya harici yazılımlara bağımlılık yok	1. Split-brain durumu olasılığı düşük	1. En güvenli çözüm, çünkü uygulama kodu cihazda çalıştırılamaz	1. Split-brain durumunu yaşama olasılığı yok
	2. Split-brain durumunun yaşanması olası değil	2. Hem HA hem de DR için kullanılabilir	2. MQ ekibi, cihazda tamamen kontrol sahibi, OS yönetici ekibine bağımlı değil	2. En basit bakım ve tek bir tüketilebilir paketle yapılandırılabilir
	3. Kernel değişiklikleri veya paylaşımlı dosya sistemi gerektirmez	3. Düşük maliyetle çalışabilen yüksek erişilebilirlik replikalarında IBM MQ iş yükü çalıştırılabilir	3. Lisans sorunları yok, mevcut kapasiteyi kullanarak çok sayıda queue manager çalıştırılabilir	3. TLS sertifikası kontrolü sağlanabilir
	4. Bağlantıların yeniden kurulması için grace period yapılandırılabilir		4. Basit bakım
Olası Dezavantajlar	1. Her yazılım yığınında ayrı bakım gerektirir	1. DRBD kernel modülü, OS yamanmasını zorlaştırır	1. Split-brain durumu olasılığı var	1. En uzun kuyruk yöneticisi yeniden başlatma süresi
	2. Asenkron replikasyon şu an mevcut değil	2. Genel bakım daha karmaşıktır	2. Yüksek performanslı ağ depolaması gerekir	2. Yüksek performans ağ depolaması gerekir
	3. Yalnızca üç pod kullanılabilir	3. Root erişimi gereklidir	3. Locally bağlı uygulamalar, başarısız olan queue manager örneğiyle bağlantıyı kesmeli	3. Yalnızca VM, bare metal veya konteyner kullanılabilir
	4. Kubernetes/OpenShift bilgisi gereklidir	4. Yalnızca RHEL'de çalışır	4. Disk veya CPU güçsüzse replikalar hızlı log yazmalarını onaylamayabilir

Linkler ve Ayrıntılı Bilgiler
Özellikler	Native HA	RDQM	IBM MQ Appliance	Multi-instance Queue Managers
Dokümantasyon	Native HA	RDQM high availability	High availability on the appliance	Multi-instance queue managers

Özet:
	• Native HA, daha fazla yapılandırma gerektirirken, üçüncü parti yazılım ve kernel değişikliklerine bağımlılık olmadan çalışabilir. Yüksek güvenlik ve düşük maliyet avantajları sunar, ancak bazı bakım zorlukları vardır.
	• RDQM, yüksek erişilebilirlik ve felaket kurtarma (DR) desteği sağlar, ancak daha karmaşık bakım gereksinimlerine sahiptir ve root erişimi gerektirir.
	• IBM MQ Appliance, daha basit yönetim ve güvenlik avantajları sağlar, ancak performans ve yerel bağlamalarla ilgili bazı sınırlamalar olabilir. Ayrıca, uygulama kodu çalıştırılamaz.
	• Multi-instance Queue Managers, tüm işlem yükünü yöneten ve yüksek erişilebilirlik sağlayan bir yapı sunar, ancak en uzun yeniden başlatma sürelerine ve yüksek ağ depolama gereksinimlerine sahiptir.


IBM MQ Multicast, düşük gecikme süresi, yüksek abonelik yayılımı ve güvenilir multicast mesajlaşma sunar. Multicast, yayın/abone mesajlaşma için verimli bir yöntemdir çünkü çok sayıda aboneye yüksek performansla mesaj iletilmesini sağlar. IBM MQ, güvenilir multicast mesajlaşma sağlar ve bunun için onaylar, negatif onaylar ve sıralama numaraları gibi özellikler kullanarak düşük gecikmeli, yüksek yayılım sağlayan mesajlaşma gerçekleştirir.
Fair delivery (Adil teslimat) özelliği sayesinde mesajlar neredeyse aynı anda teslim edilir ve hiçbir alıcıya avantaj sağlanmaz. IBM MQ Multicast, ağ üzerinden mesajları ilettiği için bir yayın/abone motoruna ihtiyaç duymaz. Bir konu (topic), grup adresine eşlendiğinde, bir kuyruk yöneticisine (queue manager) ihtiyaç duyulmaz çünkü yayıncılar ve aboneler eşler arası (peer-to-peer) modda çalışabilir. Bu da kuyruk yöneticisi sunucularındaki yükü azaltır ve kuyruk yöneticisi sunucusu artık bir arıza noktası haline gelmez.
Başlangıç Multicast Kavramları
IBM MQ Multicast, mevcut sistemlere ve uygulamalara kolayca entegre edilebilir. İletişim Bilgisi (COMMINFO) nesnesi kullanılarak entegrasyon yapılır. Ayrıca iki TOPIC nesnesi alanı, mevcut TOPIC nesnelerinin multicast trafiği desteklemesi ya da bu trafiği yok sayması için hızlı yapılandırma sağlar.


IBM MQ Telemetry, uzak cihazlardan veri toplama ve bu cihazların kontrolünü sağlama hizmeti sunan bir teknolojidir. MQ Telemetry, IoT (Nesnelerin İnterneti) cihazlarını ve diğer uzak cihazları IBM MQ ile bağlar ve düşük maliyetle bu cihazlardan veri toplama ve kontrol etme işlemlerini sağlar.
MQ Telemetry'nin Temel Bileşenleri:
	1. Telemetri Kanalları: MQTT istemcilerinin IBM MQ'ya bağlanmasını yönetir. Yeni IBM MQ nesneleri, örneğin SYSTEM.MQTT.TRANSMIT.QUEUE, kullanılarak bu etkileşim sağlanır.
	2. Telemetri (MQXR) Servisi: MQTT istemcileri, telemetri kanallarına bağlanmak için SYSTEM.MQXR.SERVICE servisini kullanır.
	3. IBM MQ Explorer Desteği: IBM MQ Explorer, MQ Telemetry'nin yönetilmesini sağlar.
	4. Dokümantasyon: IBM MQ dokümantasyonu içinde yer alır ve Java ile C istemcileri için SDK dökümantasyonu sağlanır.
Temel Telemetri Kavramları:
Telemetri, uzak cihazlardan veri toplama, ölçüm yapma ve bu cihazların kontrolünü sağlama işlemidir. Uygulama geliştiricileri, cihazlardan veri alarak bu verileri merkezi bir kontrol noktasına iletebilir ve burada analiz edebilirler. Bu veri, sistemlerin karar vermesine yardımcı olur.
MQ Telemetry'nin Kullanım Alanları:
	• MQTT İstemcileri: Telemetri cihazlarından gelen verileri toplayan ve sunucuya ileten uygulamalar. Ayrıca bu istemciler, belirli konuları (topic) abone olarak dinler ve bu konulara yönelik yayınlar alabilir.
	• Mesaj Gönderimi: IBM MQ uygulamaları, MQTT istemcilerine mesaj gönderirken, bu mesajlar istemcilerin abone olduğu konulara yönelik yayınlar yapılarak iletilir.
	• Stateless ve Stateful Oturumlar: MQTT istemcileri, bağlandıkları queue manager ile stateful oturumlar oluşturabilirler. Bağlantı koparsa, queue manager, istemcinin aboneliklerini ve iletilmemiş mesajları saklar ve istemci yeniden bağlandığında mesajlar iletilir.
	• Güvenlik: Telemetri cihazlarının güvenliği önemlidir. VPN, TLS ve JAAS gibi güvenlik mekanizmaları kullanılarak bu cihazlar güvenli hale getirilebilir.
Performans ve Ölçeklenebilirlik:
MQ Telemetry, cihaz sayısının arttığı durumlarda yüksek performans sunabilmek için optimize edilmiştir. Düşük bant genişliğine sahip ağlarda bile güvenilir mesaj iletimi sağlar.
MQ Telemetry'nin Avantajları:
	• Düşük Maliyetli Veri Toplama: Cihazlardan veri toplamak için düşük maliyetli bir altyapı sağlar.
	• Esneklik: Her türlü cihazla çalışabilir, sensörlerden mobil cihazlara kadar geniş bir cihaz yelpazesini destekler.
	• Globalleşme Desteği: MQTT mesajları, UTF-8 formatında kodlanarak dünya genelinde farklı dillerle uyumlu çalışabilir.
Örnek Kullanım:
Bir örnek uygulama, deniz taşımacılığında kullanılan AIS (Automatic Identification System) verilerini toplayarak, Twitter ve SMS üzerinden yolculara geç kalkışlar hakkında bilgi verir. Bu, gerçek zamanlı veri akışı sağlayarak, yolcuların daha iyi kararlar almasına yardımcı olur.
Bu şekilde, MQ Telemetry, cihazlardan veri toplama ve bu verileri internet ve işletme sistemlerine entegre etme konusunda önemli avantajlar sağlar.


1. Yetkilendirme Servis Arayüzü
IBM MQ, erişim kontrolünü Object Authority Manager (OAM) aracılığıyla sağlar. Bu sistem, MQI çağrıları, komutlar ve nesnelere erişim için yetkilendirme işlemlerini yönetir. OAM, IBM MQ nesnelerine erişimi denetler ve yöneticilerin komut satırı arayüzü kullanarak yetkilendirmeleri vermesine veya iptal etmesine olanak tanır.
	• Yetkilendirme Yönetimi: AIX, Linux ve Windows sistemlerinde güvenlik yapılandırmalarını yapmak için yetkilendirme servis bileşenleri oluşturabilirsiniz.
2. Kullanıcı Yazılımı veya Üçüncü Taraf Kanal Çıkışları
Kanal güvenliği için kullanıcı tarafından yazılmış veya üçüncü taraf kanal çıkışları kullanılabilir. Bu çıkışlar, kanal güvenliğini artırmak için özelleştirilebilir.
	• Kanal Çıkışları: Kanal mesajlarının güvenliğini sağlamak amacıyla özel çıkış programları kullanılabilir.
3. TLS Kullanarak Kanal Güvenliği
Transport Layer Security (TLS), endüstri standardı bir kanal güvenliği sağlar. TLS, dinleme, manipülasyon ve taklit saldırılarına karşı koruma sağlar.
	• TLS Özellikleri:
		○ Mesaj Gizliliği ve Bütünlüğü: Mesajları şifreleyerek gizliliğini korur.
		○ Karşılıklı Kimlik Doğrulaması: Gönderen ve alıcı arasında kimlik doğrulama yapar.
IBM MQ'de TLS güvenliği hakkında daha ayrıntılı bilgi için Cryptographic security protocols: TLS bölümüne bakabilirsiniz.
4. Kanal Kimlik Doğrulama Kayıtları
Kanal kimlik doğrulama kayıtları, bağlı sistemlere kanal bazında verilen erişimi denetlemenizi sağlar. Bu özellik, bağlantı noktalarının kimlik doğrulamasını sağlamaya yardımcı olur.
	• Detaylı Yönetim: Bağlanan sistemlere belirli yetkiler verilebilir.
5. Mesaj Güvenliği
Advanced Message Security (AMS), IBM MQ'yu kullanarak gönderilen ve alınan mesajlara şifreleme koruması sağlar. Bu özellik, IBM MQ'nun ayrı bir bileşeni olup, özel lisans gerektirir.
	• Mesaj Şifreleme: Gönderilen mesajlar, şifreleme ve kimlik doğrulama ile korunur.
6. IBM MQ.NET Yönetilen İstemci TLS Desteği
IBM MQ'nun .NET istemcisi, Microsoft'un SSLStreams kitini temel alarak TLS desteği sunar. Bu, diğer IBM MQ istemcilerinden farklıdır çünkü diğer istemciler IBM Global Security Kit (GSKit) kullanır.
IBM MQ güvenliği, mesajların güvenli iletimini ve veri bütünlüğünü sağlamak için kapsamlı bir yaklaşım sunar. Bu yöntemler, IBM MQ'nun güvenliğini sağlamak için önemli araçlardır.


IBM MQ MQI (Message Queue Interface) istemcisi, IBM MQ ürününün bir bileşenidir ve bir sistemde çalıştığı zaman, o sistemde bir kuyruk yöneticisinin (queue manager) bulunmaz. Bu istemci, bir uygulamanın başka bir sistemdeki kuyruk yöneticisine MQI çağrıları yapmasına olanak tanır. Çıktılar, istemciye geri gönderilir ve istemci, bu çıktıyı uygulamaya iletir.
IBM MQ MQI İstemcisi ve Sunucu İletişimi
	• MQI Client: IBM MQ MQI istemcisi, istemci uygulamasının başka bir sistemdeki kuyruk yöneticisine bağlanmasını sağlar. Bu uygulama, MQI calls (Message Queue Interface çağrıları) yapabilir. Bu tür bir uygulama, IBM MQ MQI Client Application olarak adlandırılır.
	• Server Queue Manager: Bağlanılan kuyruk yöneticisine server queue manager denir. Kuyruklar ve diğer IBM MQ nesneleri, yalnızca kuyruk yöneticisinin bulunduğu makinede (IBM MQ sunucusu) mevcuttur.
Bir IBM MQ server (sunucu), bir veya daha fazla istemciye hizmet veren bir kuyruk yöneticisidir. Sunucu, her istemci ile iletişim sağlamak için özel bir iletişim bağlantısına sahiptir.
MQI Kanalı ve İletişim
	• MQI Channel: Bir MQI channel (MQI kanalı), istemci uygulaması bir MQCONN veya MQCONNX çağrısı yaparak kuyruk yöneticisine bağlandığında başlar. İstemci uygulaması MQDISC çağrısını yaparak bağlantıyı sonlandırır.
		○ MQCONN: Kuyruk yöneticisine bağlanmak için kullanılan çağrı.
		○ MQDISK: Bağlantıyı sonlandıran çağrı.
MQI İstemci Uygulamasının Bağlantısı
	• Platform Desteği: IBM MQ MQI istemcisi ve sunucusu, AIX, Linux, Windows, IBM i, ve z/OS gibi platformlarda çalışabilir.
IBM MQ MQI Client ve IBM MQ Server'ın uyumlu çalışabileceği platformlar aşağıda sıralanmıştır:
		○ IBM MQ MQI Client: AIX, Linux, Windows, IBM i
		○ IBM MQ Server: AIX, Linux, Windows, IBM i, z/OS
	• Uygulama Geliştirme: IBM MQ uygulamanızı istemci-server ortamında çalışacak şekilde geliştirmek için, ilgili istemci kitaplıklarıyla uygulamanızı bağlantılandırmanız gerekir.
		○ MQCONN çağrısı, istemciyi belirtilen kuyruk yöneticisine bağlar.
		○ İstemci daha sonra MQI calls (mesaj kuyruğu arayüzü çağrıları) yaparak kuyruk yöneticisi ile etkileşime girer.
IBM MQ İstemcileri Kullanmanın Avantajları
IBM MQ istemcileri, mesajlaşma ve kuyruk yönetimini verimli bir şekilde gerçekleştirmenizi sağlar. Bu istemciler, mesaj kuyruğunun arkasındaki altyapıya doğrudan bağlanmadan mesaj iletmek için kullanılır.
Extended Transactional Client
Bir extended transactional client (genişletilmiş işlemsel istemci), harici bir işlem yöneticisi altında, başka bir kaynak yöneticisi tarafından yönetilen kaynakları güncelleyebilir.
Bağlantı Yöntemi
Bir istemci, MQCONN veya MQCONNX çağrısı kullanarak bir kuyruk yöneticisine bağlanır ve kanal üzerinden iletişim kurar.
Önemli Terimler:
	• MQI (Message Queue Interface): IBM MQ istemci uygulamalarının kuyruk yöneticileriyle iletişim kurmasını sağlayan arabirim.
	• MQCONN: Kuyruk yöneticisine bağlanmak için kullanılan çağrı.
	• MQCONNX: Bağlantı parametreleri ile kuyruk yöneticisine bağlanmayı sağlayan çağrı.
	• MQDISC: Kuyruk yöneticisinden bağlantıyı sonlandıran çağrı.
	• Server Queue Manager: Kuyrukları ve IBM MQ nesnelerini barındıran sunucu kuyruk yöneticisi.
	• Extended Transactional Client: Genişletilmiş işlemsel istemci, harici bir işlem yöneticisi ile kaynak güncelleme yapabilir.


IBM MQ, Java uygulamaları için üç farklı uygulama programlama arabirimi (API) sağlar: IBM MQ sınıfları için Jakarta Messaging, IBM MQ sınıfları için JMS, ve IBM MQ sınıfları için Java. Bu arabirimler, Java uygulamalarının IBM MQ ile entegrasyonunu sağlar ve farklı Java platformlarında çalışan uygulamalar için iletişim özellikleri sunar.
IBM MQ için Java Arabirimleri
1. IBM MQ Sınıfları için Jakarta Messaging (Jakarta Messaging 3.0)
	• Jakarta Messaging sağlayıcısıdır ve IBM MQ, Jakarta Messaging arabirimlerini mesajlaşma sistemi olarak uygular.
	• Jakarta Connectors Architecture, Jakarta EE ortamında çalışan uygulamaları, IBM MQ gibi Kurumsal Bilgi Sistemlerine (EIS) bağlamak için standart bir yol sunar.
	• Bu API, Java 8 ve sonrasında desteklenen Jakarta Messaging 3.0 standardına uyumludur ve yeni özellikler ve basitleştirilmiş API sunar.
	• Jakarta Messaging gelecekteki gelişmeler için tercih edilen teknolojidir.
2. IBM MQ Sınıfları için JMS (JMS 2.0)
	• JMS (Java Message Service) sağlayıcısıdır ve IBM MQ, JMS arabirimlerini mesajlaşma sistemi olarak uygular.
	• Java Platform, Enterprise Edition Connector Architecture (JCA) kullanarak, Java EE ortamında çalışan uygulamaları, IBM MQ gibi Kurumsal Bilgi Sistemlerine bağlamak için bir yol sunar.
	• IBM MQ 8.0’dan itibaren JMS 2.0 standardı uygulanmaktadır. Ancak, JMS 2.0 teknolojisi yerini Jakarta Messaging’e bırakacaktır.
	• JMS 2.0 hala desteklenmektedir, ancak yeni Java mesajlaşma özellikleri Jakarta Messaging üzerinden gelişecektir.
	• IBM MQ sınıfları için JMS, yalnızca mevcut JMS 2.0 uygulamalarını desteklemek için önerilir. Yeni geliştirmeler için Jakarta Messaging tercih edilmelidir.
3. IBM MQ Sınıfları için Java
	• IBM MQ için Java sınıfları, Java ortamında IBM MQ’yu kullanmanıza olanak sağlar.
	• Java uygulamaları, IBM MQ’ya istemci olarak bağlanabilir veya doğrudan bir IBM MQ kuyruk yöneticisine bağlanabilir.
	• IBM MQ sınıfları için Java API'si IBM MQ 8.0'dan itibaren işlevsel olarak stabilize edilmiştir. Yeni özellikler eklenmeyecek ve yalnızca mevcut hatalar giderilecektir.
	• Bu API, IBM MQ 8.0 ile stabil hale gelmiştir ve gelecekte yeni özellik eklenmeyecek, mevcut özelliklere yönelik talepler reddedilecektir.
	• IBM MQ için Java sınıfları, yeni geliştirmeler için artık önerilmez; bunun yerine Jakarta Messaging API’si tercih edilmelidir.
JMS ve Jakarta Messaging
	• JMS 2.0 standardı, Jakarta Messaging tarafından aşılmıştır. Ancak, IBM MQ sınıfları için JMS, JMS 2.0 standardını desteklemeye devam etmektedir. Gelecekteki gelişmeler Jakarta Messaging API'sinde yer alacaktır.
	• IBM MQ sınıfları için Jakarta Messaging, JMS'in modernize edilmiş versiyonudur ve gelecekteki uygulamalar için tercih edilmesi gereken teknoloji olacaktır.
Desteklenen Platformlar ve Gereksinimler
	• Java 8 ve sonrasında çalışan Java çalışma ortamları, bu arabirimlerle çalışan uygulamalar için gereklidir. IBM MQ 9.3'ten itibaren, IBM MQ sınıfları için Java, JMS, ve Jakarta Messaging Java 8 ile inşa edilmiştir.
IBM MQ Mesajlaşma Sağlayıcı Modları
IBM MQ mesajlaşma sağlayıcıları üç çalışma moduna sahiptir:
	1. Normal Mod: Standart işleyiş şeklidir.
	2. Normal Mod ile Kısıtlamalar: Belirli kısıtlamalarla çalışan bir moddur.
	3. Geçiş Modu: Eski uygulamalardan yeni sürümlere geçiş yapmak için kullanılan mod.
Tercih Edilen Teknoloji
Yeni geliştirmeler için IBM MQ sınıfları için Jakarta Messaging kullanılması önerilir. Mevcut JMS 2.0 uygulamaları için ise IBM MQ sınıfları için JMS kullanılabilir.

IBM MQ, Java uygulamaları için üç farklı uygulama programlama arayüzü (API) sunar: IBM MQ sınıfları Jakarta Messaging için, IBM MQ sınıfları JMS (Java Message Service) için ve IBM MQ sınıfları Java için.
	1. IBM MQ sınıfları Jakarta Messaging: IBM MQ, Jakarta Messaging 3.0'ı desteklemeye başlamıştır. Jakarta Messaging, Java'nın mesajlaşma standardıdır ve JMS'nin yerini alacak şekilde geliştirilmiştir. IBM MQ, Jakarta Messaging API'leri ile mesajlaşma sağlayan bir sağlayıcıdır.
	2. IBM MQ sınıfları JMS: JMS 2.0, IBM MQ tarafından desteklenen eski bir sürümdür. JMS API'leri, mesajları göndermek ve almak için kullanılan standart Java API'leridir. IBM MQ, JMS 2.0 standardını, daha basit bir kullanım için bazı geliştirmelerle sağlar.
	3. IBM MQ sınıfları Java: Bu sınıflar, IBM MQ'nun Java ortamında kullanılmasını sağlar. Java uygulamaları, IBM MQ ile iletişim kurarak, bir IBM MQ kuyruğuna bağlanabilir ve mesaj gönderip alabilir.
IBM MQ sınıfları JMS ve Jakarta Messaging, IBM MQ tarafından sağlanan iki ana mesajlaşma sağlayıcısıdır. Bu sağlayıcılar, Java SE (Standard Edition) ve Java EE (Enterprise Edition) uygulamaları için kullanılabilir. Her iki sağlayıcı da aynı temel işlevleri sunar, ancak Jakarta Messaging 3.0, JMS 2.0'ı daha modern ve basitleştirilmiş bir şekilde sunar.
JMS ve Jakarta Messaging modelinin özellikleri:
	• Her iki model de, Java uygulamalarının mesajlaşma işlemlerini gerçekleştirmesi için gerekli arayüzleri tanımlar.
	• IBM MQ sınıfları JMS, IBM MQ'nun JMS arayüzlerini sağlayarak, bir mesajlaşma sistemi olarak IBM MQ'yu kullanır.
	• IBM MQ, JMS ve Jakarta Messaging için bazı ek işlevsellikler sunar, bu da daha esnek bir kullanım sağlar.
Bu arayüzlerin, özellikle yeni geliştirmeler için IBM MQ sınıfları Jakarta Messaging'in tercih edilmesi önerilmektedir, çünkü JMS 2.0'ın gelecekteki güncellemeleri yalnızca Jakarta Messaging içinde yer alacaktır.


IBM MQ Managed File Transfer (MFT) - Türkçe Açıklama
IBM MQ Managed File Transfer (MFT), dosyaların sistemler arasında yönetilen ve denetlenebilir bir şekilde transfer edilmesini sağlayan bir teknolojidir. Bu çözüm, dosya boyutlarından ve kullanılan işletim sistemlerinden bağımsız olarak, güvenli ve güvenilir dosya transferi sağlar. MFT, dosya transferlerini otomatikleştirir, güvenli hale getirir ve yönetimini basitleştirir.
MFT, aşağıdaki işlemleri gerçekleştirmenize olanak tanır:
	• Dosya transferleri oluşturma ve yönetme
	• FTP, FTPS veya SFTP sunucuları ile dosya transferi yapma
	• Dosya transferlerini zamanlama ve tetikleme (örneğin, bir dosya oluşturulduğunda transferi başlatma)
	• Dosya transferlerini izleme ve günlükleme
	• Dosyaların güvenli bir şekilde iletilmesini sağlamak için SSL bağlantıları kullanma
MFT Topolojisi
MFT, IBM MQ üzerinde çalışır ve MFT ajanları ile koordinasyon kuyruk yöneticisi arasında dosya transferlerini gerçekleştirir. Ajanlar, kendi ajan kuyruk yöneticilerine bağlanır ve dosya verilerini bu kuyruklar üzerinden iletir. Koordinasyon kuyruk yöneticisi, ajanlar ve transfer durumu hakkında bilgi yayınlar, transferlerin ilerleyişini izler.
Ana Bileşenler:
	• Ajanlar (Agents): Dosya transferlerini gerçekleştiren ve kendi kuyruk yöneticilerine bağlanan bileşenlerdir. Ajanlar, dosya transferlerini gerçekleştirmek için koordinasyon kuyruk yöneticisi ile etkileşime girer.
	• Koordinasyon Kuyruk Yöneticisi (Coordination Queue Manager): Ajanlardan gelen dosya transferi bilgilerini alır, kaydeder ve dağıtır. Ayrıca transferlerin durumu hakkında bilgi sağlar.
	• Komut Kuyruk Yöneticisi (Command Queue Manager): IBM MQ ağına bağlanan ve MFT komutlarını işleyen yöneticidir.
MFT ile IBM MQ Entegrasyonu
IBM MQ, MFT'yi daha güvenilir hale getirmek için çeşitli özellikler sunar:
	• Garanti Edilmiş Mesaj Teslimi: IBM MQ'nun mesaj teslim garantisi, dosya transferinin güvenli ve sorunsuz bir şekilde gerçekleşmesini sağlar.
	• Depolama ve İleriye Doğru Yönlendirme (Store and Forward): MFT, ağ kesintileri gibi durumlarda dosya transferini kesintisiz şekilde sürdürür.
MFT REST API
MFT, dosya transferlerini yönetmek için bir REST API sunar. Bu API, transferlerin durumunu sorgulama, ajan bilgilerini alma gibi işlemleri gerçekleştirmenizi sağlar.
MFT, IBM MQ'nun sunduğu yüksek erişilebilirlik çözümleriyle de entegre olabilir. Bu sayede, MFT konfigürasyonunun dayanıklılığını artırabilirsiniz. Örneğin, ajanlar, çoğaltılmış veri kuyruk yöneticileri (RDQM) kullanarak daha dayanıklı hale getirilebilir.
MFT ile Entegre Olabileceğiniz IBM Ürünleri:
	• IBM Integration Bus: MFT tarafından transfer edilen dosyalar, IBM Integration Bus akışlarında işlenebilir.
	• IBM Sterling Connect:Direct: MFT, mevcut Connect:Direct ağınızla dosya transferi yapabilir.
	• IBM Tivoli Composite Application Manager: Transfer bilgilerini izlemek için kullanılabilir.
MFT, IBM MQ ile entegre bir şekilde çalışarak dosya transferlerinizi yönetmenizi sağlar ve ağ altyapınızın gücünü kullanarak bu süreçleri daha verimli ve güvenli hale getirir.


IBM MQ Internet Pass-Thru (MQIPT) - Türkçe Açıklama
IBM MQ Internet Pass-Thru (MQIPT), IBM MQ'nun isteğe bağlı bir bileşenidir ve uzak konumlar arasında internet üzerinden mesajlaşma çözümleri uygulamak için kullanılır. MQIPT, IBM MQ'yu destekleyen herhangi bir sürümle çalışabilir ve ayrı bir IBM MQ bileşeni kurmanıza gerek yoktur.
MQIPT, iki IBM MQ kuyruk yöneticisi arasında veya bir IBM MQ istemcisi ile bir kuyruk yöneticisi arasındaki mesaj akışlarını alıp yönlendiren bağımsız bir hizmet olarak çalışır. Bu, istemci ve sunucunun aynı fiziksel ağda olmadığı durumlarda bağlantı kurulmasını sağlar.
MQIPT Nasıl Çalışır?
MQIPT, bir TCP/IP portu üzerinden gelen bağlantıları dinler ve bu bağlantılara karşılık verir. Bu bağlantılar, normal IBM MQ mesajları, HTTP içindeki tünellenmiş IBM MQ mesajları veya TLS/SSL ile şifrelenmiş mesajlar olabilir. MQIPT, çoklu bağlantıları aynı anda yönetebilir.
En basit yapılandırmasında, MQIPT bir IBM MQ protokol yönlendiricisi gibi çalışır. Bağlantı isteklerini kabul eder ve bu bağlantıları iletir. MQIPT'nin ağ geçidinde bulunması, doğrudan bir TCP/IP bağlantısı kurulamayan durumlarda kullanışlıdır.
MQIPT'nin Temel Özellikleri:
	• Veri Depolama: MQIPT, ilettiği verileri hafızada tutar ve disk üzerinde sadece yapılandırma dosyasını okumak veya bağlantı günlüklerini yazmak için veri okuma/yazma işlemi yapar.
	• Mesaj Güvenliği: MQIPT, IBM MQ'nun mesaj teslimat güvenliğini sağlar, ancak veri depolamaz veya senkronize kontrol (syncpoint) prosedürüne katılmaz.
	• Bağlantı Yönlendirme: MQIPT, bir IBM MQ istemcisi ve hedef kuyruk yöneticisi arasındaki iletişimi yönlendirir. IBM MQ kanalı, MQIPT aracılığıyla bağlantı kurar ve hedef kuyruk yöneticisine ulaşır.
MQIPT'nin Kullanım Senaryoları:
	• Güvenli Bağlantı Kurma: Eğer iki sistem arasındaki doğrudan TCP/IP bağlantısı engellenmişse (örneğin, bir güvenlik duvarı nedeniyle), MQIPT kullanılarak güvenli bir iletişim sağlanabilir.
	• Uzaktan Bağlantılar: Uzak konumlardaki sistemler, MQIPT ile birbirleriyle güvenli bir şekilde iletişim kurabilirler.
Desteklenen Kanal Yapılandırmaları:
MQIPT, tüm IBM MQ kanal türlerini destekler, ancak yapılandırma yalnızca TCP/IP bağlantılarıyla sınırlıdır. MQIPT, hedef kuyruk yöneticisi gibi görünür, bu nedenle kanal yapılandırması gerektiğinde, MQIPT'nin ana bilgisayar adı ve dinleyici portu belirtilir.
Yüksek Erişilebilirlik ve Multi-Instance Kuyruk Yöneticileri:
MQIPT, çoklu örnek kuyruk yöneticileri ve yüksek erişilebilirlik ortamlarıyla da kullanılabilir. Bu özellik, sistem arızaları durumunda bile kesintisiz dosya aktarımı ve iletişim sağlar.
Mesaj Güvenliği ve Dağıtık Kuyruk Yönetimi:
IBM MQ, dağılmış kuyruk yönetimi ile mesajların doğru şekilde teslim edilmesini garanti eder. MQIPT bu süreçte yalnızca mesaj iletimini sağlar ve mesaj verisini depolamaz veya teslimatın doğruluğuna müdahale etmez.
MQIPT'nin Başlıca Kullanım Alanları:
	1. İki IBM MQ kuyruğu yöneticisi arasındaki bağlantıları yönlendirme.
	2. İstemci ve kuyruk yöneticisi arasındaki bağlantı kurma.
	3. Ağ geçidi olarak çalışarak TCP/IP bağlantıları sağlayarak IBM MQ istemcileri ve kuyruk yöneticileri arasında güvenli iletişim sağlama.
MQIPT, IBM MQ'nun özelliklerinden yararlanarak bağlantıların güvenli ve verimli bir şekilde yapılmasını sağlar. Herhangi bir ağ kesintisi veya engel durumunda bile mesajların doğru ve güvenli bir şekilde iletilmesi mümkün hale gelir.
