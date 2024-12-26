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
		○ Abone 3: Spor sonuçları ile ilgileniyor. Bu abone, Sport başlığındaki yayınları alacak.Bu yapılandırmada, hiçbir abone televizyon programlarına (TV başlığı) ilgi göstermiyor, dolayısıyla bu başlık altındaki yayınlar abonelere gönderilmeyecek.
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
	• Cluster (kümeler) ile kuyruk yöneticileri arasındaki mesaj iletimi daha düzenli hale gelir. Küme içindeki her kuyruk yöneticisi, bir topic (konu) üzerinde yayın yapan bir yayıncı olabilir veya bu mesajları alıp işleyen bir abone olabilir.Cluster’da Mesaj Yönlendirme:
		○ Doğrudan Yönlendirme: Bir kuyruk yöneticisinden gelen mesaj, doğrudan diğer kuyruk yöneticilerine gönderilir.
		○ Topic Host Yönlendirme: Mesajlar önce bir topic host kuyruk yöneticisi üzerinden geçer ve buradan diğer kuyruk yöneticilerine iletilir.
Dağıtık Sistemlerde Mesaj Dağıtımı:
	• Mesaj Dağıtım Yöntemleri:
		1. Mesajları yalnızca gerekli kuyruk yöneticilerine iletmek: Yalnızca ilgili abonelikleri barındıran kuyruk yöneticilerine mesaj gönderilir. Bu, daha verimli bir yöntemdir.
		2. Tüm kuyruk yöneticilerine mesaj iletmek: Mesajlar, tüm kuyruk yöneticilerine iletilir ve her kuyruk yöneticisi, yalnızca kendi abonelikleriyle eşleşenleri alır. Bu yöntem, daha az verimlidir ancak abone bilgilerini paylaşmayı gerektirmez.
Küme ve Hiyerarşi Yapılandırmaları:
	• Publish/Subscribe Hiyerarşileri: Dağıtık sistemlerde, kuyruk yöneticilerinin bir ağaç yapısı şeklinde düzenlenmesi sağlanabilir. Hiyerarşiler, her bir kuyruk yöneticisinin ana (parent) ve çocuk (child) ilişkisi kurarak mesaj iletiminin daha kontrollü olmasını sağlar.Örnek:
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
