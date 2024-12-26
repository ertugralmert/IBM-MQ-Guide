Birden Çok Kuyruk Yöneticisi Tabanlı Mimariler

Bir IBM® MQ mimarisi, birden fazla kuyruk yöneticisinin yapılandırılması ve kullanılması ile daha karmaşık hale getirilebilir. Bu tür mimariler, mesaj kuyruğu yönetimini ve veri aktarımını daha verimli hale getirebilir. Aşağıda, birden çok kuyruk yöneticisi kullanan mimarilerin nasıl yapılandırılacağına dair detaylı bir açıklama bulunmaktadır.
Temel Kavramlar:
Birden fazla kuyruk yöneticisi ile yapılan dağıtık mesaj kuyruğu mimarileri, her kuyruk yöneticisinin diğerleriyle iletişim kurarak mesajları taşımasına olanak tanır. Bu mimaride, kuyruk yöneticileri arasındaki bağlantılar kanallar kullanılarak yapılır. Kanallar, bir kuyruk yöneticisinden diğerine mesajları otomatik olarak taşır ve her bir kanal, yapılandırmaya bağlı olarak belirli bir yön üzerinden çalışır.
Dağıtık Kuyruk Yöneticisi Yapılandırması
Dağıtık mesaj kuyruğu yönetimi ile, uygulamalar bir kuyruk yöneticisinin bulunduğu sistemde çalışırken, bu uygulamalar başka bir sistemdeki başka bir kuyruk yöneticisine erişebilir. Aşağıda, birden fazla kuyruk yöneticisinin kullanıldığı bazı temel mimariler açıklanmıştır:
	1. Manuel Bağlantılar Kullanma:Dağıtık kuyruk yöneticileri arasında kanallar manuel olarak yapılandırılabilir. Ancak, bu yöntem daha küçük ağlar ve az sayıda bağlantı için uygundur. Her bağlantının çok hassas bir şekilde tanımlanması gerektiğinde tercih edilir.
	2. Kuyruk Yöneticisi Kümesi (Cluster) Kullanma:Eğer ağda birden fazla kuyruk yöneticisi ile ilişkili ve veri paylaşan bir yapı kurulması gerekiyorsa, kuyruk yöneticileri bir kümeye (cluster) dahil edilebilir. Küme kullanımı, kuyruk yöneticilerinin birbirleriyle iletişim kurmasını kolaylaştırır ve ek kanal tanımlamalarına gerek kalmaz.
Dağıtık Kuyruklar ve Küme Planlaması
Birden fazla kuyruk yöneticisini birbirine bağlamak için iki yöntem kullanabilirsiniz:
	1. Manuel Bağlantılar:Bu yöntemle, her bir kuyruk yöneticisi için kanal ve uzak kuyruk tanımlamaları manuel olarak yapılır. Bu yöntem, ağın küçük olduğu veya özel bağlantı gereksinimlerinin bulunduğu durumlar için uygundur.
	2. Kuyruk Yöneticisi Kümesi (Cluster):Küme yapısı, kuyruk yöneticilerinin birbirine bağlanmasını basitleştirir. Küme içinde yer alan her kuyruk yöneticisi, kendisine ait bir cluster-receiver kanalına ve bir cluster-sender kanalına sahiptir. Bu sayede, her kuyruk yöneticisi küme içindeki diğer kuyruk yöneticilerine kolayca mesaj gönderebilir.
Küme Yapısının Avantajları:
	• Kolay Yönetim: Küme yapılandırıldığında, yeni kuyruk yöneticileri eklemek oldukça kolaydır ve mevcut yapı üzerinde değişiklik yapmadan ekleme işlemi yapılabilir.
	• Veri Paylaşımı: Küme içinde yer alan kuyruklar birbirlerine erişilebilir hale gelir, bu da her bir kuyruk yöneticisinin, diğerlerine mesaj gönderebilmesi anlamına gelir.
	• Düşük Yapılandırma Hatası Riski: Küme yapılandırması, gereksiz manuel kanal, uzak kuyruk ve iletim kuyruğu tanımlamalarını ortadan kaldırır.
Küme Yapısı Seçerken Dikkat Edilmesi Gerekenler:
	• Manuel Kontrol İhtiyacı: Eğer belirli bir kontrol istiyorsanız, manuel yapılandırmalar kullanmanız gerekebilir. Küme kullanımı, özellikle büyük ağlar için önerilir.
	• Ağ Boyutu ve Dinamiklik: Küme yapısı, büyük ağlar ve sık değişen yapılandırmalar için uygundur. Küme, yeni kuyruk yöneticilerini otomatik olarak keşfeder.
	• Yüksek Erişilebilirlik ve Ölçeklenebilirlik: Küme yapıları, yüksek erişilebilirlik ve ölçeklenebilirlik gereksinimlerini karşılamak için daha uygundur.
Dağıtık Yayın/Abone Yapılandırması (Publish/Subscribe)
Dağıtık kuyruk yöneticisi yapısında, bir yayın/abone yapısı da kullanılabilir. Bu yapı, mesajları yalnızca bir konuya abone olan uygulamalara yönlendirir. Yayıncı, mesajları bir konu ile yayınlar, abone olan uygulamalar bu mesajları alır. Yayıncı ve alıcı arasında doğrudan bir bağlantı kurmaya gerek yoktur. Yayıncı, sadece bir konu belirler ve mesajını bu konuda abone olanlara gönderir.
Bu yapı, özellikle büyük ağlarda veya çok sayıda uygulama arasında veri paylaşımında önemli avantajlar sağlar. Her uygulama, yalnızca ilgilendiği konuya abone olur ve sadece bu konuyla ilgili mesajları alır.
Yüksek Erişilebilirlik ve İki Tam Depo (Full Repository)
Bir kuyruk yöneticisi kümesinin sağlıklı çalışabilmesi için, iki tam depo (full repository) tanımlanmalıdır. Bu iki depo, küme durumunu senkronize tutar. Bir depo devre dışı kalırsa, diğeri aktif olarak küme bilgilerini güncel tutmaya devam eder. Bu sayede, yüksek erişilebilirlik sağlanır.
Küme İsimlendirme ve Yapılandırma İpuçları
	• Küme ve Kanal İsimlendirme: Küme yapısı için kısa ama anlamlı isimler seçilmelidir. Kanal isimleri de benzer şekilde açık ve anlamlı olmalıdır.
	• Daha Fazla Full Repository Kullanımı: Çok büyük küme yapılarında, birden fazla full repository kullanılabilir ancak bu genellikle önerilmez çünkü iki tam depo yeterlidir. Daha fazla depo eklemek, bazı durumlarda veri güncellemelerini karmaşıklaştırabilir.
Sonuç
Birden çok kuyruk yöneticisi tabanlı yapı, özellikle büyük ve dinamik ağlarda verimli ve ölçeklenebilir bir çözüm sunar. Küme yapıları, yönetim açısından kolaylık sağlar ve yüksek erişilebilirlik sunar. İyi bir küme yapılandırması, doğru sayıda tam depo ve etkili kanal isimlendirme ile desteklenmelidir.


*********************


Örnek Küme Yapıları
Son Güncelleme: 2024-07-02
Bu örnekler, iki ve üç kuyruk yöneticisi içeren IBM® MQ kümelerinin nasıl yapılandırılabileceğini göstermektedir. Küme yapıları, birden çok kuyruk yöneticisi arasındaki bağlantıları ve veri paylaşımını kolaylaştırmak için kullanılır.
En Küçük Küme: İki Kuyruk Yöneticisi
İlk örnekte, en küçük küme yapısı olan iki kuyruk yöneticisi kullanılıyor. Bu durumda her iki kuyruk yöneticisi de tam depo (full repository) olarak yapılandırılmıştır. Küme yapılandırması için sadece birkaç tanım gerekir ve her bir kuyruk yöneticisinin yüksek derecede otonomisi vardır.
Küme Yapısı:
	• Küme Adı: DEMOCLSTR
	• Kuyruk Yöneticileri: QM1 ve QM2
	• QM1, bir küme kuyruğuna (Q1) sahiptir.
	• Her kuyruk yöneticisi kendi sisteminde çalışır, ancak aynı makine üzerinde birden fazla kuyruk yöneticisi de olabilir.
Küme Yapılandırması için Adımlar:
	1. Kuyruk Yöneticisi Tanımlamaları: Her kuyruk yöneticisi için tam depo (full repository) tanımlamaları yapılır.
	2. Kanal Tanımlamaları: Her kuyruk yöneticisi, küme bilgilerini almak için bir cluster-receiver kanalı ve mesaj göndermek için bir cluster-sender kanalı tanımlar.
Üç Kuyruk Yöneticili Küme Yapısı
İkinci örnek, üç kuyruk yöneticisinden oluşan bir küme yapısını göstermektedir. Bu yapıda QM1 ve QM2, tam depo kuyruk yöneticileri olarak işlev görür. QM2 ve QM3, küme içindeki diğer kuyruk yöneticilerine erişim sağlayan kümeler arası kuyruklar (cluster queues) barındırır.
Küme Yapısı:
	• Küme Adı: CLSTR1
	• Kuyruk Yöneticileri: QM1, QM2, QM3
	• Tam Depo Kuyruk Yöneticileri: QM1 ve QM2
	• Küme Kuyrukları: QM2 ve QM3'teki kuyruklar, kümedeki diğer kuyruk yöneticilerinden erişilebilir.
Kanal Yapılandırması:
	1. Cluster-Receiver Kanalları: Her kuyruk yöneticisi, cluster-receiver kanalı tanımlar. Bu kanal, kuyruk yöneticisini küme hakkında bilgilendirir ve mesajları alır.
		○ Örneğin: QM1'in cluster-receiver kanalı, CLSTR1.QM1 olarak adlandırılır.
	2. Cluster-Sender Kanalları: Küme içinde bir kuyruk yöneticisinden diğerine mesaj göndermek için cluster-sender kanalları kullanılır.
		○ Örneğin: QM1 ve QM3, CLSTR1.QM2'ye bağlanmak için cluster-sender kanalları tanımlar.
İlk Erişim ve Keşif:
	• Kuyruk Yöneticisi QM3'ten QM2'ye Mesaj Gönderme: QM3'teki bir uygulama, ilk kez QM2'deki kuyruklara mesaj göndereceğinde, bu kuyrukları keşfetmek için tam depo (full repository) olan QM2'yi kullanır. Bu süreçte, QM2, küme hakkında bilgi tutan tam depo olarak görev yapar.
Otomatik Tanımlama:
	• Cluster-Sender ve Cluster-Receiver Kanalları: Bir kuyruk yöneticisi, cluster-sender kanalı tanımlayarak, küme hakkında bilgi almak için tam depo kuyruk yöneticisine bağlanır. Bu işlem otomatik olarak yapılır ve kanallar, kuyruk yöneticileri arasında iletişim sağlamak için kullanılır.
Otomatik Tanımlanan Kanallar ve Küme Kuyrukları
	• Cluster Transmission Queue (SYSTEM.CLUSTER.TRANSMIT.QUEUE): Tüm kuyruk yöneticilerinde bulunan bu iletim kuyruğu, kümedeki diğer kuyruk yöneticilerine mesaj göndermek için kullanılır. Her bir kuyruk yöneticisi, bu iletim kuyruğu üzerinden mesajlarını iletir.
Görüntüleme:
	• Kanal Yapılandırmaları: Küme içindeki tüm kuyruk yöneticileri, cluster-receiver ve cluster-sender kanallarını otomatik olarak tanımlar. Bu kanalların her biri, küme yönetimini ve veri akışını sağlamak için kullanılır.
Sonuç
Bu örnekler, IBM MQ kümeleri ile birden fazla kuyruk yöneticisinin nasıl yapılandırılacağını ve birbirleriyle nasıl iletişim kuracağını göstermektedir. Küme yapıları, mesajların merkezi bir yapı üzerinden iletilmesini sağlar ve her bir kuyruk yöneticisi, sadece gerekli olan bilgileri alarak verimli bir şekilde çalışır. Bu yapı, yüksek verimlilik ve esneklik sağlar, çünkü her bir kuyruk yöneticisi küme bilgilerini otomatik olarak günceller.








**************************

Kümelenme: En İyi Uygulamalar
IBM MQ kümeleri, kuyruk yöneticilerini birbirine bağlamak için kullanılan bir mekanizmadır. Bu bölümde, kümelerin nasıl başarılı bir şekilde yapılandırılacağı ve yönetileceği konusunda testlere ve kullanıcı geri bildirimlerine dayalı en iyi uygulamalar yer almaktadır. Başarılı bir küme kurulumu, iyi bir planlama ve IBM MQ temellerine dair derin bir anlayışa dayanır. Bu nedenle, bu konuyu ele almadan önce ilgili konuları gözden geçirmek önemlidir.
Kümelenme: Örtüşen Kümeler İçin Özel Düşünceler
Bu başlık, IBM MQ kümelerinin planlanması ve yönetilmesi hakkında rehberlik sağlar. Kullanıcı geri bildirimleri ve testlere dayalı bilgiler içerir.
Küme Sahipliği
Örtüşen kümelerle çalışan bir sistemi yapılandırırken, aşağıdaki konularda dikkatli olmak faydalıdır:
	• Kümeler gevşek bağlı olmakla birlikte, her bir kümeyi tek bir yönetim birimi olarak ele almak, kümeler arasındaki etkileşimi yönetmek için faydalıdır. Örneğin, yük dengelemesi yapan küme kuyrukları kullanırken, mesajların hedeflerine doğru yönlendirilmesi için tek bir yönetici ya da takım tarafından kümelerin tamamının anlaşılması gerekir.
	• Birden fazla kümeyi yöneten farklı takımlar arasındaki işbirliği önemlidir. Birden fazla kümeyi yönetirken, özellikle geçiş yöneticisi (gateway queue manager) olan kuyruk yöneticilerinin yönetimi konusunda net kurallar ve politikalar belirlemek faydalıdır.
Örtüşen Kümeler: Geçiş Yöneticileri
	• Geçiş Yöneticisi (Gateway Queue Manager): Birden fazla kümeyi birbirine bağlamak için kullanılan geçiş yöneticisi, kümeler arasında mesaj iletmek için kritik rol oynar. Bu yapı, yönetilmesi zor bir point-to-point kanal ağının önüne geçer.
	• Kanal Yönetimi: Bir geçiş yöneticisi, farklı kümelere ait kuyruğa ulaşmak için kuyruk yöneticisi takma adları (aliases) ve uzak kuyruk tanımları kullanabilir. Bu, kümeler arasındaki mesajların doğru şekilde yönlendirilmesini sağlar.
Kümelenme: Topoloji Tasarımı
Küme tasarımı, performansı iyileştirmek ve bakım süreçlerini kolaylaştırmak için önemlidir. Özellikle tam depo kuyruk yöneticileri (full repositories) ve kanal tanımlamalarının yönetimi, doğru tasarım kararları ile verimli bir şekilde yapılabilir.
	• Tam Depo Kuyruk Yöneticileri: Tam depo kuyruk yöneticileri, tüm küme bilgilerini tutar. Bu nedenle, tam depo kuyruk yöneticilerinin her zaman yüksek erişilebilirliğe sahip olması önemlidir. Bu, küme yönetiminin sürekliliği için kritik rol oynar.
	• Performans Düşünceleri: Küme içindeki kuyruklar üzerindeki ilgiyi kaydeden ve yöneten sistemler, yüksek yoğunluklu mesaj trafiği ile aşırı yüklenebilir. Bu yükü minimize etmek için, benzer uygulamaları az sayıda kuyruk yöneticisine bağlamak daha verimli olabilir.
Kümelenme: Uygulama İzolasyonu
Birden fazla küme ile çalışan uygulamaları izole etmek için çeşitli yollar vardır. Uygulamalar, kümeler arasında izole edilmiş mesaj akışları sağlamak için ayrı kuyruklar, kanallar ve kuyruk yöneticileri kullanabilir.
	• Çoklu Küme İletim Kuyrukları: Mesajları farklı cluster-sender kanalları aracılığıyla farklı iletim kuyruklarına yönlendirmek, mesaj trafiğini izole etmenin bir yoludur. Bu yöntem, yalnızca tek bir küme içinde değil, aynı zamanda örtüşen kümelerde de kullanılabilir.
Kümelenme: Kanalların Yönetimi
Bir küme içindeki birden fazla kanal tanımı, iki kuyruk yöneticisi arasındaki farklı yolları sağlayabilir. Ancak bu tasarım, daha fazla karmaşıklığa yol açabilir ve kanal kullanımını azaltarak performansı düşürebilir.
	• Yük Dengeleme: Kümelerde, kanal sayısının artırılması, yük dengeleme algoritmasında bazen karmaşıklık yaratabilir. İki kuyruk yöneticisi arasında birden fazla kanal varsa, yük dengeleme algoritması bu kanalları farklı kuyruk yöneticilerine yönlendirebilir. Bu, performansın düşmesine neden olabilir.
Kümelenme: Tam Depo Kuyruk Yöneticilerinin Kullanımı
Tam depo kuyruk yöneticileri, genellikle uygulama kuyrukları için kullanılmaz. Bunun yerine, bu kuyruk yöneticileri, küme bilgilerini güncel tutmak için ayrılır.
	• Kullanım Durumları: Tam depo kuyruk yöneticilerini, sistem bakımında ya da yeni küme özelliklerini kullanmak için güncelleme işlemlerinde izole tutmak daha verimli olabilir. Bu, uygulama performansını etkilemeden bakım yapmayı kolaylaştırır.
Sonuç
IBM MQ kümeleri, çok sayıda kuyruk yöneticisinin ve uygulamanın birbirine bağlanmasını sağlayan güçlü bir mekanizmadır. Ancak, kümelerin yönetimi karmaşık olabilir, özellikle de öğeler (geçiş yöneticileri, tam depo yöneticileri) ve bağlantı yapılandırmaları dikkatlice tasarlanmalıdır. Küme yönetimini basitleştirmek ve yüksek verimliliği sağlamak için iyi bir planlama ve uygulama yönetimi gereklidir.


************************


Kümelenme: Küme İletim Kuyruklarını Yapılandırma Planı
IBM MQ küme yapılandırmalarında, kümeler arası mesaj iletimi için kullanılacak iletim kuyruklarının nasıl yapılandırılacağına dair birkaç seçenek bulunmaktadır. Bu yazıda, farklı küme iletim kuyruğu yapılandırma seçenekleri ile ilgili bilgiler yer almaktadır.
Başlamadan Önce
İlk olarak, hangi tür küme iletim kuyruğunun kullanılacağına karar vermek önemlidir. Bu, küme kanal iletim kuyruğu yapılandırmasını planlamadan önce gözden geçirilmesi gereken bir adımdır.
Küme İletim Kuyruğu Seçenekleri
	• Varsayılan Küme İletim Kuyruğu: Küme mesaj iletimleri için kullanılan COMMON (genel) bir iletim kuyruğu, yani SYSTEM.CLUSTER.TRANSMIT.QUEUE varsayılan olarak belirlenmiştir.
	• Ayrı Küme İletim Kuyrukları: Küme yöneticisi, her bir küme-sender kanalı için ayrı iletim kuyrukları oluşturabilir. Bu kuyruklar, SYSTEM.CLUSTER.TRANSMIT.MODEL.QUEUE model kuyruğundan kalıcı-dinamik kuyruklar olarak yaratılır. Her bir küme-sender kanalı için bir küme iletim kuyruğu oluşturulur.
Manuel Tanımlanan İletim Kuyrukları Seçenekleri:
	1. Her Küme-Sender Kanalı İçin Ayrı Kuyruk Tanımlama:
		○ Her bir kanal için ayrı iletim kuyruğu oluşturulabilir ve CLCHNAME (kanal adı) özelliği ile kanal adını ilişkilendirerek, belirli bir kanal için yönlendirme yapılabilir.
	2. Birden Fazla Küme-Sender Kanalı İçin Ortak İletim Kuyruğu Kullanma:
		○ Bu durumda, birden fazla küme-sender kanalını tek bir iletim kuyruğunda toplayabilirsiniz. Bu amaçla CLCHNAME özelliği için bir wildcard (joker karakter) kullanılır. Örneğin, SALES.* ifadesi, adı SALES ile başlayan tüm kanalları kapsayacak şekilde yapılandırılabilir.
Adımlar:
	1. Varsayılan Küme İletim Kuyruğu Türünü Seçme:
		○ Küme yöneticisini tek bir iletim kuyruğu kullanacak şekilde ayarlayabilir veya her kanal için ayrı iletim kuyruğu seçebilirsiniz.
		○ MQSC komutunu kullanarak yapılandırabilirsiniz:ALTER QMGR DEFCLXQ(CHANNEL)
	2. Mesaj Akışlarını İzole Etme:
		○ Belirli mesaj akışlarını, diğer akışlarla aynı iletim kuyruğunu paylaşmayacak şekilde yapılandırabilirsiniz.
		○ Örneğin, SALES kuyruğuna yönlendirilmiş mesajları izole etmek için Q.SALES adlı yeni bir küme oluşturulabilir ve bu küme iletim kuyruğu yalnızca SALES kanalına bağlı olan mesajlarla kullanılabilir.
	3. Gözetim ve Yönetim Gereksinimleri İçin Küme İletim Kuyrukları Oluşturma:
		○ Bazı durumlarda, farklı küme hedeflerine yönelik mesajları izlemek ve yönetmek için ek iletim kuyrukları tanımlanabilir. Bu, örneğin gözetim veya yönetim gereksinimlerini karşılamak için yapılabilir.
Örnek Yapılandırma Adımları:
Örneğin, SALES, FINANCE, ve DEVELOP adında üç bölümlü bir küme yapısı oluşturulmuştur ve mesaj akışlarının her birini izole etmek için ayrı küme iletim kuyrukları tanımlanabilir.
	1. SALES Kuyruğunu İzole Etme:
		○ Yeni bir küme olan Q.SALES oluşturulabilir ve SALES kuyrukları bu kümeye dahil edilir.
		○ Yeni kanal tanımlamaları yapılır:DEFINE CHANNEL(Q.SALES.SALER1) CHLTYPE(CLUSSDR) CONNAME('localhost(1416)') CLUSTER(Q.SALES) REPLACEDEFINE CHANNEL(Q.SALES.SALER2) CHLTYPE(CLUSRCVR) CONNAME('localhost(1417)') CLUSTER(Q.SALES) REPLACE
	2. Küme İletim Kuyruğu Tanımlamaları:
		○ Q.SALES kümesi için iletim kuyruğu tanımlanır:DEFINE QLOCAL(XMITQ.Q.SALES.SALESRV) USAGE(XMITQ) CLCHNAME(Q.SALES.SALESRV) REPLACE
	3. Gözetim için Küme İletim Kuyruğu Tanımlama:
		○ Finansal mesajlar için ayrı iletim kuyrukları:DEFINE QLOCAL(XMITQ.SALES)  USAGE(XMITQ) CLCHNAME(SALES.*)  REPLACEDEFINE QLOCAL(XMITQ.FINANCE)    USAGE(XMITQ) CLCHNAME(FINANCE.*) REPLACE
Sonraki Adımlar:
	• Yeni yapılandırmayı aktive etmek için, geçiş yöneticisindeki tüm kanallar durdurulup yeniden başlatılabilir:endmqm -i GATEstrmqm GATE
	• Sonrasında, yapılandırmanın doğruluğu test edilmelidir. Testler için, örneğin amqsmon komutuyla iletim kuyruklarındaki mesajları izleyebilirsiniz:amqsmon -m GATE -t statistics
Bu adımlarla, kümelenmiş IBM MQ ortamlarında mesaj akışlarını daha verimli bir şekilde yönetebilir ve izole edebilirsiniz.




****************************

Küme İletim Kuyruklarını Değiştirme (Switching)
Son Güncelleme: 2024-12-06
Bu işlem, mevcut bir üretim kuyruğu yöneticisinde küme iletim kuyruklarını değiştirmek için nasıl bir plan yapılacağına dair yönergeler sağlar. Küme iletim kuyruğunda yapılacak değişiklikler, çalışan sistemin kesintiye uğramaması için dikkatlice yapılmalıdır. Bu işlemde, değişikliklerin etkili hale getirilmesi için iki ana seçenek bulunmaktadır.
Başlamadan Önce
Küme iletim kuyruğunda yapılacak değişikliklerin zamanını minimize etmek, geçiş sürecini hızlandırabilir. Küme-sender kanalı geçiş süreci hakkında bilgi edinmek ve kuyruğun boşaltılması gerektiği konusunda hazırlıklı olmak faydalıdır.
İki Seçenekle Değişiklik Yapma
	1. Otomatik Değişim (Queue Manager tarafından yönetilen)Bu seçenek, kuyruğu yönetici tarafından otomatik olarak değiştirilmesine izin verir. Küme-sender kanalı bir sonraki başlatıldığında, geçiş işlemi başlatılır ve aktif hale gelir.
		○ Avantaj: Bu yöntem otomatik olup, kanal yeniden başlatıldığında geçiş işlemi otomatik olarak yapılır.
		○ Dezavantaj: Zaman sınırlıysa, bu geçişin tamamlanıp tamamlanamayacağı garanti edilemez. Zamanlamayı kontrol edemiyorsanız, ikinci seçenek daha uygun olabilir.
	2. Manuel Değişim (El ile kontrol edilen geçiş)Bu seçenek, kuyruğun manuel olarak değiştirilmesini sağlar. Kanal durdurulur ve bu işlemi yaparken belirli bir zaman diliminde kontrol sağlanabilir.
		○ Avantaj: Bu yöntemde, kanal geçişi tamamen kontrol edilebilir ve bakım penceresi içinde kesin bir süre içinde tamamlanabilir.
		○ Dezavantaj: El ile yapılan işlemler, kanal durdurulup tekrar başlatılmak zorunda olduğundan yönetimi biraz daha karmaşık hale getirebilir.
Geçişin Otomatik Yapılması (Seçenek 1)
Otomatik geçiş yapmak için, kuyruğu yönetici kanal yeniden başlatıldığında değiştirir. Kanal aktif olmadığında, eski iletim kuyruğunda bekleyen mesajlar tamamen bitene kadar yeni iletim kuyruğuna geçiş yapılmaz. Eğer zaman sınırlıysa, geçiş süreci tamamlanmayabilir.
	• Adım 1: Kuyruğun durması beklenir.
	• Adım 2: Yeni iletim kuyruğuna gelen mesajlar aktarılmaya başlanır.
	• Adım 3: Eski kuyruğa gelen mesajlar, yeni kuyruğa aktarılır.
Geçişin Manuel Yapılması (Seçenek 2)
Manuel geçişte, kuyruğu manuel olarak değiştirebilirsiniz ve bu geçiş sürecini tam olarak ne zaman yapacağınızı kontrol edebilirsiniz. Eğer geçişin tamamlanacağı zaman dilimi kısıtlıysa, manuel geçişle daha iyi sonuç alabilirsiniz.
	• Adım 1: İlgili kanal durdurulur.
	• Adım 2: Yapılacak olan değişiklikler yapılır.
	• Adım 3: Kanal yeni iletim kuyruğu ile yeniden başlatılır.
Küme İletim Kuyruğuna Geçiş (Manuel Geçiş)
Eğer kanal durduysa ve mevcut iletim kuyruğu değiştirilmek isteniyorsa, kanal durdurulup yeni iletim kuyruğu atandıktan sonra yeniden başlatılabilir. Bu işlem için aşağıdaki komutlar kullanılabilir:
	• Adım 1: Kanalı durdurun:STOP CHANNEL(ChannelName) MODE(QUIESCSE) STATUS(STOPPED)
	• Adım 2: Küme iletim kuyruğunun geçişini başlatın:runswchl -m QmgrName -c ChannelName
	• Adım 3: Kanalı yeniden başlatın:START CHANNEL(ChannelName)
Kanal Durumunu İzleme
Geçiş sırasında, kanal durumunu ve iletim kuyruğunun derinliğini izlemek önemlidir. Bu, geçişin nasıl gerçekleştiğini anlamanızı sağlar:
	• Kanal durumu kontrolü:DISPLAY CHSTATUS(*) WHERE(XMITQ LK 'SYSTEM.CLUSTER.TRANSMIT.*')
	• İletim kuyruğu derinliği izleme:DISPLAY QUEUE('SYSTEM.CLUSTER.TRANSMIT.*') CURDEPTH
Sonuç:
	• Otomatik Geçiş: Bu yöntem, geçişin kanal yeniden başlatıldığında otomatik olarak yapılmasını sağlar.
	• Manuel Geçiş: Bu seçenek, kanal durdurulup değişiklik yapılmasını sağlar ve geçişin kesin olarak zamanlanması için daha fazla kontrol sunar.


************************


Küme Migrasyonu ve Değişiklik Best Practices
Bu bölüm, IBM® MQ kümelerinin planlanması ve yönetilmesine dair en iyi uygulamalarla ilgili rehberlik sağlar. Müşterilerden alınan geri bildirimler ve testler, bu uygulamaların temelini oluşturur.
Küme İçerisinde Nesneleri Taşımak
Uygulamalar ve Kuyruklar
Bir kuyruğun bir küme yöneticisinden diğerine taşınması gerektiğinde, geçişi sorunsuz bir şekilde gerçekleştirmek için yük dengeleme parametrelerini kullanabilirsiniz. Bu işlem adımları ile yapılabilir:
	1. Mevcut kuyruğun CLWLRANK parametresini yüksek bir değere (örneğin 5) ayarlayın.
	2. Kuyruğun yeni bir örneğini oluşturun ve CLWLRANK parametresini sıfır olarak ayarlayın.
	3. Yeni sistemi yapılandırın ve uygulamaları yeni kuyruk örneği üzerinde çalışacak şekilde yapılandırın.
	4. Yeni kuyruk örneğinin CLWLRANK parametresini mevcut kuyruğun üstüne çıkarın (örneğin 9).
	5. Mevcut kuyruğun işlemdeki mesajlarını tamamlamasına izin verin ve ardından bu kuyruğu silin.
Küme Yöneticilerini Taşımak
Bir küme yöneticisinin aynı sunucuda kalsa da IP adresi değiştirilecekse, aşağıdaki adımlar izlenebilir:
	1. DNS kullanarak bu işlemi basitleştirebilirsiniz. CONNAME kanal özelliğini kullanarak DNS üzerinden bağlantı adresini ayarlayın.
	2. Eğer bir tam depo taşıyorsanız, değişiklik yapmadan önce diğer tam depoların düzgün çalıştığından emin olun.
	3. SUSPEND QMGR komutunu kullanarak kuyruk yöneticisini askıya alın, böylece trafik birikimini önleyin.
	4. Sunucunun IP adresini değiştirin. CLUSRCVR kanal tanımında kullanılan IP adresini güncelleyin.
	5. Kuyruk yöneticisi, tam depolar ile yeniden bağlandığında, kanal tanımları otomatik olarak çözülecektir.
	6. Küme yöneticisi bir IP adresi değişikliğinden etkileniyorsa, partial depolar mümkün olan en kısa sürede yönlendirilmelidir.
	7. SUSPEND QMGR komutunu kullanarak yöneticiyi askıya alın ve değişiklikleri yaptıktan sonra RESUME QMGR komutunu çalıştırarak yöneticiyi yeniden başlatın.
Küme Yöneticisini Yeni Bir Sunucuya Taşımak
Bir küme yöneticisini yeni bir sunucuya taşımak için, verilerin kopyalanması ve yedekten geri yüklenmesi gerekir. Ancak bu işlem, ideal bir seçenek değildir. Yeni bir küme yöneticisi oluşturmak ve kuyrukları ile uygulamaları çoğaltmak, daha düzgün bir geçiş sağlar.
Eğer küme yöneticisini yedeklemeden taşımak istiyorsanız, aşağıdaki en iyi uygulamaları takip etmelisiniz:
	• Yedekleme işlemlerinde ve kurtarma süreçlerinde kullanılan işlemleri, işletim sisteminize göre uygulayın.
	• REFRESH CLUSTER komutunu kullanarak, tüm yerel küme bilgilerini silin ve yeniden oluşturulmasını sağlayın.
Önemli Not: Küme büyükse, REFRESH CLUSTER komutunun kullanımı, performansı ve kullanılabilirliği etkileyebilir.
Yükseltmeler ve Bakım Kurulumları
Küme yönetimi sırasında, "big bang" senaryosundan (tüm küme yöneticilerini durdurup, yükseltme yapıp tekrar başlatmak) kaçının. Küme, farklı sürümlere sahip birden fazla küme yöneticisinin birlikte çalışmasını destekler, bu nedenle planlı ve aşamalı bir bakım yaklaşımı tercih edilmelidir.
Yükseltme öncesinde aşağıdaki adımları takip edin:
	1. Yedeklemelerinizi alın.
	2. Tüm küme yöneticileri yükseltilene kadar yeni küme fonksiyonlarını kullanmayın.
	3. Tam depo yöneticileri ilk olarak yükseltilmelidir. Bu, yeni sürümde olmayan bilgilerin kaybolmaması için gereklidir.
REFRESH CLUSTER Komutu için En İyi Uygulamalar
REFRESH CLUSTER komutu, küme hakkında yerel olarak tutulan bilgileri siler ve bu bilgileri tam depolardan yeniden alır. Bu komut yalnızca özel durumlarda kullanılmalıdır. Herhangi bir küme uyumsuzluğu veya yapılandırma hatasında, REFRESH CLUSTER komutunun kullanılmasından önce alternatif çözümler araştırılmalıdır.
Dikkat Edilmesi Gerekenler:
	• Büyük kümeler üzerinde REFRESH CLUSTER komutunun çalıştırılması, tam depoların üzerindeki yükü artırabilir. Bu nedenle, geçiş işlemi düşük yoğunluklu saatlerde yapılmalıdır.
	• Küme geçmişi kuyruğu (SYSTEM.CLUSTER.HISTORY.QUEUE), komut çalıştırıldığında bir anlık görüntü alır ve 3 ay sonra mesajlar sona erer.
Küme Kullanılabilirliği, Çoklu Örnek ve Felaket Kurtarma
Küme mimarisi, doğrudan bir Yüksek Kullanılabilirlik (HA) çözümü olmasa da, bazı durumlarda bu hizmetlerin erişilebilirliğini iyileştirmek için kullanılabilir. Örneğin, bir kuyruğun farklı yöneticilerdeki birden fazla örneği, hizmetlerin yüksek kullanılabilirliğini artırabilir.
Çoklu Örnek Kuyruk Yöneticileri
IBM MQ, çoklu örnek kuyruk yöneticisi teknolojisi ile yüksek kullanılabilirlik sunar. Bu, bir kuyruğun örneklerinin birden fazla kuyruk yöneticisinde bulunmasını sağlar.
	• Eğer iki tam depo yöneticisi varsa, bunlar doğal olarak yüksek kullanılabilirliğe sahip olacaktır.
	• Çoklu örnek kuyruk yöneticileri kullanmak, büyük küme yöneticilerinde veya belirli durumlarda, yedeklilik sağlamada faydalıdır.
Felaket Kurtarma
Felaket kurtarma için IBM MQ, doğrudan kurtarma sunmaz; ancak, yedeklemeler ve yeniden yapılandırmalarla yardımcı olabilir. Eğer bir kuyruk yöneticisinin verisi bozulursa, yedekten geri yükleme en doğru yöntem olacaktır.
Felaket Kurtarma Testi:
	• Canlı küme üzerinde herhangi bir kesintiye yol açmamak için dikkatli olunmalıdır.
	• Testlerin ağ izolasyonu veya güvenlik duvarı seviyesinde yapılması gerekir.
Önemli Not: Yedekten geri yükleme sırasında, REFRESH CLUSTER komutunu kullanarak küme senkronizasyonunu sağlamak gerekebilir.


*************************



Dağıtılmış Yayın/Abone Ağı Planlaması
Son Güncelleme: 2024-07-02
Dağıtılmış yayın/abone ağı, bir kuyruk yöneticisinde oluşturulan aboneliklerin, başka bir kuyruk yöneticisine bağlı bir uygulama tarafından yayınlanan mesajları almasını sağlar. Uygun bir topolojiyi seçerken, manuel kontrol, ağ boyutu, değişim sıklığı, kullanılabilirlik ve ölçeklenebilirlik gibi gereksinimlerinizi göz önünde bulundurmanız gerekir.
Bu Görev Hakkında
Bu görev, dağıtılmış yayın/abone ağları hakkında temel bilgilere sahip olduğunuzu varsayar. Dağıtılmış yayın/abone ağlarıyla ilgili teknik bir genel bakış için Dağıtılmış yayın/abone ağları başlığına göz atın.
Dağıtılmış Yayın/Abone Ağı İçin Üç Temel Topoloji
	1. Doğrudan Yönlendirilmiş Küme (Direct Routed Cluster)
	2. Konu Ana Bilgisayarı Yönlendirilmiş Küme (Topic Host Routed Cluster)
	3. Hiyerarşi (Hierarchy)
İlk iki topoloji, bir IBM® MQ küme yapılandırması kullanılarak başlatılır. Üçüncü topoloji ise bir küme ile veya bir küme olmadan oluşturulabilir. Altyapı için kuyruk yöneticisi ağı planlaması hakkında daha fazla bilgi için Dağıtılmış Kuyruklar ve Küme Planlaması başlığına göz atın.
	1. Doğrudan Yönlendirilmiş Küme:Bu, bir küme zaten mevcut olduğunda yapılandırılması en basit topolojidir. Küme içinde herhangi bir kuyruk yöneticisinde tanımlanan herhangi bir konu, kümedeki her kuyruk yöneticisinde otomatik olarak kullanılabilir hale gelir. Yayınlar, bir yayın uygulamasının bağlandığı her bir kuyruk yöneticisinden doğrudan, eşleşen aboneliklerin bulunduğu kuyruk yöneticilerine yönlendirilir. Küçük ve basit ağlar için bu topoloji kabul edilebilirken, daha büyük veya dinamik ortamlarda bu yaklaşımın aşırı yük oluşturması muhtemeldir.
	2. Konu Ana Bilgisayarı Yönlendirilmiş Küme:Bu topoloji, herhangi bir kuyruk yöneticisinde tanımlanan bir konunun kümedeki her kuyruk yöneticisinde otomatik olarak kullanılabilir hale gelmesini sağlar, ancak konuların hangi kuyruk yöneticilerinde barındırılacağı dikkatlice seçilmelidir. Tüm bilgi ve yayınlar, bu konu ana bilgisayarı kuyruk yöneticileri üzerinden geçer. Bu, sistemin tüm kuyruk yöneticileri arasında kanal bağlantıları ve bilgi akışları bakımını gerektirmediği anlamına gelir. Ancak, bu da yükü artırabilir, özellikle konu barındıran kuyruk yöneticilerinde.
	3. Hiyerarşi:Bu, en fazla manuel yapılandırma gerektiren topolojidir. Her bir kuyruk yöneticisinin hiyerarşideki doğrudan ilişkileri elle yapılandırılmalıdır. Bu topoloji, belirli gereksinimlere göre çok özelleştirilebilir, ancak bir yayının, aboneliklere ulaşabilmek için birçok kuyruk yöneticisi üzerinden "atlaması" gerekebilir.
Uygun Bir Topoloji Seçmek İçin Sorulması Gereken Sorular
	1. Ağınızın büyüklüğü ne kadar olacak?
		○ Tahmini olarak, ağınızda kaç kuyruk yöneticisi olacak?
		○ Tahmini olarak, kaç konu ve abone olacak?
	2. Konfigürasyon üzerinde ne kadar manuel kontrol ihtiyacınız var?
		○ Kuyruk yöneticilerinizin bazıları daha mı az yetenekli?
		○ Bazı kuyruk yöneticilerinize bağlantılar daha mı kırılgan?
	3. Ağın dinamikliği nasıl olacak?
		○ Abonelikler ne kadar sıklıkla eklenip çıkarılacak?
		○ Konu dizileri ne kadar sık değişecek?
	4. Kullanılabilirlik ve ölçeklenebilirlik gereksinimleriniz nelerdir?
		○ Yayıncıdan aboneye her zaman bir bağlantı yolu mevcut olmalı mı?
		○ Yayın trafiğinin ölçeklenmesi gerekecek mi?
Topoloji Seçimi İçin Prosedür
	1. Ağınızın büyüklüğünü tahmin edin:
		○ Yayıncılar ve aboneler dahil olmak üzere kaç kuyruk yöneticisinin yayın/abone etkinliklerinde yer alacağını tahmin edin.
	2. Manuel kontrol ihtiyacını göz önünde bulundurun:
		○ Konuların ve yayıncıların hangi kuyruk yöneticilerinde barındırılacağını belirleme ihtiyacı var mı?
		○ Kuyruk yöneticilerinin bir kısmı daha az güçlü mü veya iletişim bağlantıları daha mı kırılgan?
	3. Ağ dinamikliğini tahmin edin:
		○ Abonelikler ne kadar sıklıkla eklenip çıkarılacak?
		○ Konular ne kadar dinamik olacak?
	4. Yol kullanılabilirliği ve yayın trafiği ölçeklenebilirliğini göz önünde bulundurun:
		○ Yayıncı kuyruk yöneticisinden abone kuyruk yöneticisine her zaman bir yol var mı?
		○ Yayın trafiği tek bir kuyruk yöneticisinden ya da kanal üzerinden yönlendirilmemeli mi?
En İyi Uygulamalar ve Kısıtlamalar
	• Doğrudan Yönlendirilmiş Küme: Küçük ağlar için uygun olsa da, daha büyük ağlar için performans sorunları yaratabilir.
	• Konu Ana Bilgisayarı Yönlendirilmiş Küme: Konu barındıran kuyruk yöneticileri üzerinde ekstra yük oluşturabilir. Ancak, daha büyük ağlar ve dinamik yayın/abone ilişkileri için uygundur.
	• Hiyerarşi: Daha fazla manuel yapılandırma gerektirir ve daha karmaşıktır. Ancak, çok özel yapılandırmalar için gereklidir ve çok fazla "atlama" gerektirebilir.
Özet
Ağınızın büyüklüğüne, dinamikliğine, kontrol ihtiyacınıza ve ölçeklenebilirlik gereksinimlerinize bağlı olarak uygun bir topoloji seçmek, başarılı bir dağıtılmış yayın/abone ağı oluşturmanın temelini atar. Küme ve konu barındırma seçeneklerinin her birinin avantajları ve sınırlamaları vardır, bu nedenle her gereksinim için doğru topolojiyi seçmek önemlidir.
