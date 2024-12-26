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
*******************
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

*******
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

************
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

*******
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

**********
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

DEFINE QREMOTE (YOURQM) RQMNAME(REALQM)
Bu, uygulamanın mesajlarını YOURQM kuyruk yöneticisine koymak için kullanılan gerçek kuyruk yöneticisinin REALQM olduğunu gösterir.
Outbound Messages - Altering or Specifying the Transmission Queue (Çıkış Mesajları - İletim Kuyruğunu Değiştirmek veya Belirtmek)
Yukarıdaki açıklamalarda da belirtildiği gibi, QM1'den QM3'e ulaşmak için QM2'yi geçmek gerekiyor. Kuşkusuz, iletim kuyruğu ve kanal bağlantıları doğru şekilde yapılandırıldığında, mesajlar doğru yöneticilere iletilir.
Inbound Messages - Determining the Destination (Giriş Mesajları - Hedefi Belirlemek) Bir alıcı MCA, iletim başlığında belirtilen kuyruk yöneticisi adına sahip bir alias tanımı varsa, iletim başlığındaki kuyruk yöneticisi adı, alias tanımındaki RQMNAME ile değiştirilir.
Reply-to Queue Alias Definitions (Cevap Kuyruğu Alias Tanımlamaları)
Cevap kuyruğu alias tanımlamaları, mesajın cevabı için alternatif adlar belirtir. Bunun avantajı, kuyruk veya kuyruk yöneticisinin adını değiştirebilmeniz, ancak uygulamalarınızı değiştirmek zorunda kalmamanızdır.
Bu tanımlar, cevap kuyruğu için yanıtların nerede alınacağına dair yönlendirmeleri içerir ve her zaman bir alias kullanarak bu işlem yapılabilir.

*****

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
	********
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
	*************
	
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
	
	

*******************
Cluster Queues (Küme Kuyrukları)
Bir küme kuyruku, bir küme kuyruk yöneticisi tarafından barındırılan ve kümedeki diğer kuyruk yöneticilerine sunulan bir kuyruktur.
Bir küme kuyruk tanımı, kümedeki diğer kuyruk yöneticilerine duyurulur. Kümedeki diğer kuyruk yöneticileri, karşılık gelen bir remote-queue (uzak kuyruk) tanımına ihtiyaç duymadan bir küme kuyruğuna mesaj koyabilir. Bir küme kuyruğu, bir kümeye adlandırılmış liste (cluster namelist) kullanılarak birden fazla kümede duyurulabilir.
Bir kuyruk duyurulduğunda, kümedeki herhangi bir kuyruk yöneticisi bu kuyruğa mesaj koyabilir. Bir mesaj koymak için, kuyruk yöneticisi, tam depolardan (full repositories) kuyruğun hangi kuyruk yöneticisinde barındırıldığını öğrenmelidir. Ardından, mesajın üzerine yönlendirme bilgisi ekler ve mesajı bir küme iletim kuyruğuna (cluster transmission queue) koyar.
Bir küme kuyrugu, IBM® MQ for z/OS®'te, kuyruk paylaşım grubu (queue sharing group) üyeleri tarafından paylaşılan bir kuyruk da olabilir.


****************
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

************
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

**********
Cluster Konuları (Cluster Topics)

Cluster konuları, cluster özelliği tanımlı olan yönetimsel konulardır. Cluster konuları hakkında bilgi, tüm cluster üyelerine aktarılır ve yerel konularla birleştirilerek, birden fazla kuyruk yöneticisini kapsayan bir topic space oluşturulur. Bu, bir kuyruk yöneticisindeki bir konuya yayımlanan mesajların, cluster içindeki diğer kuyruk yöneticilerindeki abonelere iletilmesini sağlar.

Cluster Konusu Tanımlama
Bir kuyruk yöneticisinde cluster konusu tanımladığınızda, bu cluster konusu tanımı full repository kuyruk yöneticilerine gönderilir. Full repository'ler, ardından bu cluster konusu tanımını tüm cluster kuyruk yöneticilerine ileterek, aynı cluster konusunun clusterdaki herhangi bir kuyruk yöneticisindeki yayıncılara ve abone olanlara sunulmasını sağlar. Cluster konusunun tanımlandığı kuyruk yöneticisi, cluster topic host (cluster konu barındırıcı) olarak bilinir.
Bir cluster konusu, clusterdaki herhangi bir kuyruk yöneticisi tarafından kullanılabilir, ancak cluster konusu üzerindeki herhangi bir değişiklik yalnızca o konunun tanımlandığı kuyruk yöneticisinde yapılabilir (host). Bu değişiklik, ardından full repositories üzerinden clusterdaki tüm üyelere aktarılır.

Cluster Konusu Yapılandırması
Cluster konularını doğrudan yönlendirme (direct routing) veya topic host yönlendirmesi kullanacak şekilde yapılandırma, cluster topic inheritance (cluster konusu mirası) ve wildcard subscriptions (joker karakterli abonelikler) hakkında bilgi için, Cluster Konuları Tanımlama kısmına başvurabilirsiniz.
Cluster konularını görüntülemek için kullanılan komutlar hakkında daha fazla bilgi için, ilgili bilgilere göz atabilirsiniz.

**************
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

