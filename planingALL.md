IBM MQ Mimari Planlaması

IBM® MQ ortamınızı planlarken, IBM MQ'nun tekli ve çoklu kuyruk yöneticisi (queue manager) mimarileri için sağladığı desteği ve nokta-nokta (point-to-point) ile yayın/abone (publish/subscribe) mesajlaşma stillerini göz önünde bulundurmalısınız. Ayrıca, kaynak gereksinimlerinizi, günlükleme (logging) ve yedekleme (backup) tesislerinizi planlamalısınız.
Bu Görev Hakkında
IBM MQ mimarinizi planlamadan önce, temel IBM MQ kavramları hakkında bilgi sahibi olmalısınız. IBM MQ Teknik Genel Bakış başlığına göz atabilirsiniz.
IBM MQ mimarileri, tek bir kuyruk yöneticisi kullanarak basit mimarilerden, birbirine bağlı çoklu kuyruk yöneticisi ağlarına kadar genişler. Birden fazla kuyruk yöneticisi, dağılmış kuyruklama (distributed queuing) teknikleri kullanılarak birbirine bağlanır. Tekli kuyruk yöneticisi ve çoklu kuyruk yöneticisi mimarileriyle ilgili daha fazla bilgi için aşağıdaki başlıklara bakabilirsiniz:
	• Tekli kuyruk yöneticisi tabanlı mimariler
	• Çoklu kuyruk yöneticisi tabanlı mimariler
	• Dağılmış kuyruklar ve kümeler (clusters) için planlama
	• Dağılmış yayın/abone (publish/subscribe) ağı planlaması
[z/OS] IBM MQ için z/OS Mimari Planlaması
IBM MQ için z/OS®'ta, yük dengeleme (workload balancing) sağlamak ve IBM MQ uygulamalarınızın ölçeklenebilir ve yüksek kullanılabilir olmasını sağlamak için paylaşılan kuyruklar ve kuyruk paylaşım grupları kullanılabilir. Paylaşılan kuyruklar ve kuyruk paylaşım grupları hakkında bilgi için Paylaşılan Kuyruklar ve Kuyruk Paylaşım Grupları başlığına bakabilirsiniz.
IBM MQ Sürümleri
IBM MQ, iki farklı sürüm modeli sunar:
	1. Long Term Support (LTS) sürümü, uzun vadeli dağıtım ve maksimum kararlılık gerektiren sistemler için en uygun olandır.
	2. Continuous Delivery (CD) sürümü, IBM MQ'nun en son işlevsel iyileştirmelerinden hızla yararlanması gereken sistemler için uygundur.
Her iki sürüm de aynı şekilde yüklenir, ancak destek ve göç (migration) ile ilgili anlamanız gereken bazı farklar vardır. Daha fazla bilgi için IBM MQ sürüm türleri ve sürümleme başlığına bakabilirsiniz.
IBM MQ için Planlama Konuları
	• IBM MQ ve IBM MQ Appliance yerel olarak GDPR uyumluluğu açısından gereksinimleri göz önünde bulundurmak.
	• Tekli Kuyruk Yöneticisi Tabancalı Mimariler ve Çoklu Kuyruk Yöneticisi Tabancalı Mimariler ile ilgili ayrıntılı bilgiler.
Tekli Kuyruk Yöneticisi Tabanlı Mimariler
En basit IBM MQ mimarileri, tek bir kuyruk yöneticisinin yapılandırılması ve kullanılmasını içerir. Bu tür mimariler, küçük ve yerel sistemlerde tercih edilebilir.
Çoklu Kuyruk Yöneticisi Tabanlı Mimariler
Dağıtılmış mesaj kuyruklama (distributed message queuing) teknikleri kullanarak, IBM MQ mimarisi oluşturmak için birden fazla kuyruk yöneticisinin yapılandırılması ve kullanılması mümkündür. Bu tür mimariler daha büyük, daha karmaşık sistemler için uygundur.
[UNIX, Linux, Windows, IBM i] Çoklu Platformlarda Depolama ve Performans Gereksinimleri
IBM MQ sisteminiz için gerçekçi ve ulaşılabilir depolama ve performans hedefleri belirlemelisiniz. Depolama ve performansı etkileyen faktörler hakkında bilgi edinmek için bağlantıları kullanabilirsiniz.
[z/OS] IBM MQ için z/OS Ortamı Planlaması
IBM MQ ortamınızı planlarken, veri setleri, sayfa setleri, Db2®, Coupling Facilities ve günlükleme (logging) ile yedekleme (backup) tesislerinin gereksinimlerini göz önünde bulundurmalısınız. IBM MQ'nun çalışacağı ortamı planlamak için bu başlıkları inceleyebilirsiniz.

IBM MQ'nun mimarisi planlanırken her bir gereksinim ve gereksinimlerinizi en iyi şekilde karşılayacak yapılandırmalar dikkate alınmalıdır. Bu süreci doğru yönetmek, sistemin uzun ömürlü ve verimli çalışmasını sağlar.


IBM MQ Sürüm Türleri: Planlama Konuları
Son Güncelleme: 2024-12-06
IBM® MQ için iki ana sürüm türü bulunmaktadır: Long Term Support (LTS) ve Continuous Delivery (CD). Seçtiğiniz sürüm türü, sipariş, kurulum, bakım ve geçiş (migration) işlemlerini etkiler.
Detaylı Bilgi
IBM MQ'nun sürüm türleri ve sürümleme hakkında daha fazla bilgi için IBM MQ sürüm türleri ve sürümleme başlığını inceleyebilirsiniz.

[UNIX, Linux, Windows, IBM i] IBM MQ için Çoklu Platformlar
Sipariş
Passport Advantage® üzerinden IBM MQ 9.4 için iki ayrı eAssembly bulunmaktadır. Bunlardan biri IBM MQ 9.4.0 LTS sürümünü, diğeri ise IBM MQ 9.4.x CD sürümünü içeren kurulum görüntülerini sunar. Hangi sürüm türünü tercih ettiğinize göre kurulum görüntülerini ilgili eAssembly'den indirin.
Tüm IBM MQ sürümleri ve özellikle IBM MQ 9.4, hem LTS sürümleri hem de CD sürümleri aynı Ürün Kimliği (PID) altında yer almaktadır. Bu, lisanslanmış bileşenlerin ve fiyatlandırma metriklerinin kısıtlamalarına tabi olarak, LTS ve CD sürümleri arasında seçim yapabileceğiniz anlamına gelir.
Kurulum
Passport Advantage üzerinden bir kurulum görüntüsü indirdikten sonra, yalnızca lisans satın aldığınız bileşenleri seçerek kurulum yapmalısınız. Hangi bileşenlerin kurulumda yer alacağını öğrenmek için IBM MQ lisans bilgileri sayfasına bakabilirsiniz.
IBM MQ 9.4.0 LTS sürümünü ve IBM MQ 9.4.x CD sürümünü aynı işletim sistemi görüntüsünde kurabilirsiniz. Bu durumda, her sürüm ayrı kurulumlar olarak görünür ve IBM MQ'nun çoklu sürüm desteği sayesinde her sürüm için farklı kuyruk yöneticileri (queue managers) kullanılabilir.
Her yeni CD sürümü, bir kurulum görüntüsü olarak sağlanır. Yeni CD sürümü mevcut bir sürümle birlikte kurulabilir veya eski bir CD sürümü, kurulum aracılığıyla yeni sürüme yükseltilebilir.
CD sürümleri, işlevsel iyileştirmeler ve en son hata düzeltmeleri ile güvenlik güncellemelerini içerir. Her CD sürümü, önceki tüm sürümleri kapsar ve tamamen yerine geçer. Bu nedenle, belirli bir CD sürümü, şirketiniz için gereksizse geçilebilir.
Bakım
LTS sürümü, hata düzeltmeleri ve güvenlik güncellemeleri (CSU'lar) sağlayan düzeltme paketleri (fix packs) ile servis edilir. Düzeltme paketleri ve CSU'lar periyodik olarak sunulur ve birikmeli (cumulative) olarak uygulanır.
CD için, CSU'lar yalnızca en son CD sürümü için üretilir. Bir sonraki sürüme geçişte, IBM Destek tarafından geçici bir düzeltme (interim fix) uygulanması istenebilir.
LTS ve CD Arasında Geçiş
LTS ve CD sürümleri arasında geçiş yapmak mümkündür, ancak bazı kısıtlamalar ve sınırlamalar vardır. Genel olarak, bir kuyruk yöneticisi LTS sürümü kodundan CD sürümü koduna veya tam tersine geçiş yapabilir, ancak hedef sürüm, kullanılan sürümden daha yüksek olmalıdır.
İki geçiş yöntemi mevcuttur:
	1. Yeni sürüm kodunu mevcut kurulum üzerine yükleyerek güncelleme yapmak. Bu durumda, kuyruk yöneticileri yeni sürümde başlatıldığında, yeni sürüm kodu kullanılır.
	2. Yeni sürümü yeni bir kurulum olarak yükleyip, sonra setmqm komutuyla kuyruk yöneticisi örneklerini yeni kuruluşa taşıyabilirsiniz.
Bir kuyruk yöneticisi CD sürümünde çalışmaya başladığında, kuyruk yöneticisinin komut seviyesi güncellenir ve bu, yeni sürümdeki tüm işlevlerin etkinleştirildiği anlamına gelir. Artık daha düşük bir sürümle başlatılamaz.

[z/OS] IBM MQ için z/OS
Sipariş
IBM MQ for z/OS® 9.4 için sipariş verirken, LTS sürümü ve CD sürümü için iki ayrı özellik bulunmaktadır. Her iki özellik de aynı ürün kimliğine (PID) karşılık gelir. Bu nedenle, bir özellik için lisans alındığında, gerekirse diğer özelliği de kullanma hakkınız olur.
Kurulum
LTS ve CD sürümleri ayrı FMID setleriyle sağlanır. Bu FMID'ler aynı SMP/E hedef bölgesine (target zone) yüklenemez. LTS ve CD sürümlerini kurmak için:
	• LTS ve CD sürümlerini ayrı hedef bölgelerine kurmalısınız.
	• Her iki sürüm için ayrı hedef ve dağıtım (distribution) kitaplıkları (libraries) kullanmalısınız.
Eğer kuyruk yöneticiniz bir kuyruk paylaşım grubunda (queue sharing group) yer alıyorsa, en son CD sürümüne yükseltme yaparken, grubun tüm kuyruk yöneticilerinin de yükseltilmesi gerekir.
Bakım
IBM MQ for z/OS, bakım için PTF'ler (Program Temporary Fixes) kullanır.
	• LTS sürümleri için PTF'ler belirli bir sürümle uyumludur ve JMS, Web UI, Connector Pack ve Managed File Transfer gibi özellikler, çoklu platform düzeltme paketleriyle aynı zamanda sunulur.
	• CD sürümleri için, CSUs genellikle CD sürümleri arasında yayınlanmaz, ancak bir sonraki CD sürümüne dahil edilir. CD sürümleri için ayrıca ++USERMOD talep edilebilir.
LTS ve CD Arasında Geçiş
LTS ve CD sürümleri arasında geçiş yapmak mümkündür, ancak bazı kısıtlamalar vardır. Örneğin, bir kuyruk yöneticisi LTS sürümünden CD sürümüne veya CD sürümünden LTS sürümüne geçiş yapabilir, ancak hedef sürüm önceden kullanılan sürümden daha yüksek olmalıdır.
	• 9.1.0 LTS → 9.4.0 LTS veya 9.4.0 CD: Geriye dönüş (backwards migration) desteklenmez çünkü 9.1.0 LTS standard destekten çıkmıştır.
	• 9.2.0 LTS → 9.4.0 LTS veya 9.4.0 CD: Geriye dönüş desteklenir.
	• 9.3.5 CD → 9.4.0 LTS veya 9.4.0 CD: Geriye dönüş desteklenmez.

Sonuç olarak, IBM MQ'nun LTS ve CD sürümleri arasındaki geçişler dikkatlice planlanmalı ve her iki sürümdeki farklılıklar göz önünde bulundurulmalıdır. Geçiş yaparken, kuyruk yöneticisi işlevselliği ve kullanılabilirliği için doğru sürüm seçilmelidir.

IBM MQ ve IBM MQ Appliance için GDPR Hazırlığına Yönelik Düşünceler
Son Güncelleme: 2024-12-06
Bu belge, IBM® MQ'nun GDPR uyumluluğuna hazırlık için yapılandırabileceğiniz özellikler ve ürünün kullanımıyla ilgili konuları ele alır. Bu bilgiler, ürünün nasıl yapılandırılacağı ve kullanıldığına bağlı olarak farklılık gösterebilir. IBM, yasal tavsiye verme veya ürünlerinin GDPR uyumluluğunu garanti etme konusunda sorumluluk taşımaz.
GDPR Nedir?
Genel Veri Koruma Yönetmeliği (GDPR), 25 Mayıs 2018'de Avrupa Birliği tarafından kabul edilmiştir ve kişisel verilerin işlenmesine yönelik güçlü bir düzenleyici çerçeve sunar. GDPR, aşağıdaki konularda yenilikler getirir:
	• Bireyler için yeni ve güçlendirilmiş haklar.
	• Kişisel verinin tanımının genişletilmesi.
	• Veri işleyenler için yeni yükümlülükler.
	• Uyumsuzluk durumunda önemli finansal cezalar.
	• Zorunlu veri ihlali bildirimleri.
IBM MQ’nun GDPR Hazırlığı İçin Yapılandırma Düşünceleri
IBM MQ, uygulamaların verileri asenkron olarak değiş tokuş etmelerini sağlayan bir mesaj odaklı ara katman yazılımıdır. Bu yazılım, çeşitli mesajlaşma API’leri, protokoller ve köprüler aracılığıyla uygulamaları birbirine bağlar. IBM MQ, üzerinden kişisel verilerin geçtiği çeşitli uygulamalara bağlanabilir. Bu, GDPR ile ilgili bazı ek düzenlemeleri göz önünde bulundurmayı gerektirir.
Veri Yaşam Döngüsü
IBM MQ, verilerin kuyruğa alındığı, işlendiği ve saklandığı süreçleri yönetir. Bu süreçler, veri güvenliği ve GDPR uyumluluğu için kritik öneme sahiptir. Aşağıdaki veri türlerinin IBM MQ ile geçişi sırasında GDPR uyumluluğu sağlanmalıdır:
	• Kişisel veriler: Çalışan bilgileri, müşteri verileri, hassas kişisel veriler (örneğin sağlık kayıtları).
	• Kimlik bilgileri: Kullanıcı adları, şifreler, API anahtarları gibi kimlik doğrulama verileri.
	• Mesaj verileri: Uygulamalar arası mesajlaşmalar, hata günlükleri, izleme dosyaları gibi veriler.
Veri Toplama ve Saklama
IBM MQ, kişisel verilerin toplanmasında rol oynayabilir. GDPR ile uyumluluk sağlamak için verilerin hangi protokollerle geldiğini, şifrelenip şifrelenmediğini ve verilerin ne şekilde saklandığını göz önünde bulundurmalısınız:
	• Veri iletimi: Veriler şifrelenmiş mi? İletim sırasında imzalanmış mı?
	• Veri saklama: IBM MQ, verileri kuyruklarda, geçici dosyalarda ve diğer medya alanlarında saklar. Bu verilerin korunması gerekir.
Veri Erişimi ve Yönetimi
IBM MQ, farklı kullanıcıların ve uygulamaların veri kaynaklarına erişmesini yönetir. Bu erişim kontrolü, güvenli bir şekilde kimlik doğrulama, rol eşlemesi ve yetkilendirme aşamalarını içerir:
	• Kimlik doğrulama: Yerel veya uzak bağlantılarda kullanıcı adı, şifre veya dijital sertifikalarla kimlik doğrulaması yapılır.
	• Yetkilendirme: Kullanıcılara, kuyruklar, konular gibi IBM MQ kaynaklarına belirli yetkiler atanabilir.
Veri Silme
GDPR'e uygunluk için, verilerin silinmesi gerektiğinde IBM MQ, ilgili verileri silebilir. Bu işlem, kişisel verilerin içeren mesajları kuyruktan kaldırmak veya tüm kuyruk yöneticisini silmek gibi yöntemlerle yapılabilir:
	• Mesaj silme: Mesajlar API veya araçlar ile silinebilir.
	• Geride kalan verilerin silinmesi: Retained Publication verisi veya diğer geçici veriler silinebilir.
Veri İşleme ve Şifreleme
Veri işleme sırasında IBM MQ, TLS (Transport Layer Security) kullanarak ağ bağlantılarını şifreleyebilir. Ayrıca, IBM MQ Advanced Message Security (AMS) özelliği, mesaj verilerini dijital imzalama ve/veya şifreleme işlemleriyle güvence altına alır.
Veri İzleme
IBM MQ, sistemin ve uygulamaların nasıl çalıştığını izlemek için çeşitli izleme özellikleri sunar. Ayrıca, veri erişimi ve yönetimi hakkında denetim günlükleri oluşturulabilir:
	• İzleme: Bağlantı ve veri aktarımı izlenebilir.
	• Denetim günlükleri: Kullanıcı erişimlerini, yetkilendirme hatalarını ve yapılandırma değişikliklerini kaydedebilirsiniz.
IBM MQ ve GDPR Uyumluluğu İçin Yapılandırma
IBM MQ'nun GDPR uyumluluğuna yardımcı olmak için aşağıdaki özellikleri yapılandırabilirsiniz:
	• Veri şifreleme: Verinin aktarım ve depolama sırasında şifrelenmesini sağlayın.
	• Erişim kontrolü: Kullanıcıların verilere erişimini kısıtlayarak, yalnızca yetkili kişilerin verilere erişmesini sağlayın.
	• Veri silme: Kişisel verileri yasal gerekliliklere uygun şekilde silin.
	• Denetim günlükleri: Erişim ve işlem kayıtlarını tutarak, gerektiğinde denetim yapabilme yeteneğine sahip olun.
IBM MQ, doğru yapılandırma ile GDPR gereksinimlerini karşılamaya yardımcı olabilir. Ancak, nihayetinde her kuruluş kendi yasal yükümlülüklerini yerine getirmekle sorumludur ve uygun hukuki danışmanlık alması gerekmektedir.

Özetle, IBM MQ'nun GDPR uyumluluğunu sağlamak için veri güvenliği, veri saklama ve silme süreçlerini yönetmek, erişim kontrolünü uygulamak, şifreleme kullanmak ve denetim kayıtları tutmak önemlidir.


Tek Bir Kuyruk Yöneticisi Tabanlı Mimari

En basit IBM® MQ mimarileri, tek bir kuyruk yöneticisinin yapılandırılması ve kullanılmasıyla ilgilidir. IBM MQ'nun temel kavramlarına aşina olmak, doğru bir planlama yapabilmek için önemlidir. Bu kavramlara IBM MQ Teknik Genel Bakış dokümanında göz atabilirsiniz.
Tek bir kuyruk yöneticisi kullanan bir dizi mimari bulunmaktadır. Aşağıda, bunlardan bazıları detaylandırılacaktır:
1. Yerel Uygulamalara Hizmet Erişimi Olan Tek Kuyruk Yöneticisi
İlk mimari, uygulamaların, hizmet sağlayıcı uygulamalarıyla aynı sistem üzerinde çalıştığı bir senaryodur. Bu mimaride, bir IBM MQ kuyruk yöneticisi, hizmet isteyen uygulamalar ile hizmet sağlayıcı uygulamalar arasında asenkron iletişim sağlar. Bu, bir uygulama çevrimdışı olsa bile diğerinin iletişimde kalmasına olanak tanır. Yerel uygulamalar arasında veri transferi, uzun süreli kesintilerde bile devam edebilir.
2. Uzaktan Uygulamalara Hizmet Erişimi Olan Tek Kuyruk Yöneticisi
İkinci mimari, hizmet sağlayıcı uygulamalardan uzak bir sistemde çalışan uygulamaların olduğu bir yapılandırmadır. Uzaktaki uygulamalar, tek bir kuyruk yöneticisine istemci olarak bağlanır. Bu mimari, bir kuyruk yöneticisi üzerinden birçok sisteme hizmet erişimi sağlar.
Ancak bu mimarinin sınırlaması, uygulamaların çalışabilmesi için ağ bağlantısının gerekli olmasıdır. Uygulama ile kuyruk yöneticisi arasındaki etkileşim ağ üzerinden gerçekleşir ve senkronize bir şekilde çalışır.
3. Yayın/Abone Yapılandırması Olan Tek Kuyruk Yöneticisi
Alternatif bir mimari, tek bir kuyruk yöneticisi ile yayın/abone (publish/subscribe) yapılandırmasını kullanmaktır. Yayın/abone mesajlaşma modelinde, bilgi sağlayıcıyı, bu bilgiyi tüketenlerden ayırırsınız. Bu, daha önceki noktadan noktaya mesajlaşma modellerinden farklıdır, çünkü burada bir uygulama hedef uygulama hakkında (örneğin, mesajları koyacak kuyruk adı) bilgi sahibi olmak zorunda değildir. IBM MQ publish/subscribe modelinde, gönderen uygulama, bilgilerin konusu doğrultusunda belirli bir konu (topic) ile mesaj yayınlar. IBM MQ, bu mesajı, bu konuya ilgi gösteren abonelere iletir. Alıcı uygulamalar, mesajları aldıkları kaynağı bilmek zorunda değildir.
Özet
Tek bir kuyruk yöneticisi kullanarak farklı uygulama mimarileri oluşturulabilir. Bu mimariler arasında yerel ve uzaktan uygulamalarla hizmet sağlama, ya da publish/subscribe (yayın/abone) modeli kullanma seçenekleri bulunur. Bu yapılar, uygulama kesintilerinin daha uzun sürede etkisini azaltır ve veri iletişimini daha esnek hale getirir.


Birden Çok Kuyruk Yöneticisi Tabanlı Mimariler

Bir IBM® MQ mimarisi, birden fazla kuyruk yöneticisinin yapılandırılması ve kullanılması ile daha karmaşık hale getirilebilir. Bu tür mimariler, mesaj kuyruğu yönetimini ve veri aktarımını daha verimli hale getirebilir. Aşağıda, birden çok kuyruk yöneticisi kullanan mimarilerin nasıl yapılandırılacağına dair detaylı bir açıklama bulunmaktadır.
Temel Kavramlar:
Birden fazla kuyruk yöneticisi ile yapılan dağıtık mesaj kuyruğu mimarileri, her kuyruk yöneticisinin diğerleriyle iletişim kurarak mesajları taşımasına olanak tanır. Bu mimaride, kuyruk yöneticileri arasındaki bağlantılar kanallar kullanılarak yapılır. Kanallar, bir kuyruk yöneticisinden diğerine mesajları otomatik olarak taşır ve her bir kanal, yapılandırmaya bağlı olarak belirli bir yön üzerinden çalışır.
Dağıtık Kuyruk Yöneticisi Yapılandırması
Dağıtık mesaj kuyruğu yönetimi ile, uygulamalar bir kuyruk yöneticisinin bulunduğu sistemde çalışırken, bu uygulamalar başka bir sistemdeki başka bir kuyruk yöneticisine erişebilir. Aşağıda, birden fazla kuyruk yöneticisinin kullanıldığı bazı temel mimariler açıklanmıştır:
	1. Manuel Bağlantılar Kullanma:
Dağıtık kuyruk yöneticileri arasında kanallar manuel olarak yapılandırılabilir. Ancak, bu yöntem daha küçük ağlar ve az sayıda bağlantı için uygundur. Her bağlantının çok hassas bir şekilde tanımlanması gerektiğinde tercih edilir.
	2. Kuyruk Yöneticisi Kümesi (Cluster) Kullanma:
Eğer ağda birden fazla kuyruk yöneticisi ile ilişkili ve veri paylaşan bir yapı kurulması gerekiyorsa, kuyruk yöneticileri bir kümeye (cluster) dahil edilebilir. Küme kullanımı, kuyruk yöneticilerinin birbirleriyle iletişim kurmasını kolaylaştırır ve ek kanal tanımlamalarına gerek kalmaz.
Dağıtık Kuyruklar ve Küme Planlaması
Birden fazla kuyruk yöneticisini birbirine bağlamak için iki yöntem kullanabilirsiniz:
	1. Manuel Bağlantılar:
Bu yöntemle, her bir kuyruk yöneticisi için kanal ve uzak kuyruk tanımlamaları manuel olarak yapılır. Bu yöntem, ağın küçük olduğu veya özel bağlantı gereksinimlerinin bulunduğu durumlar için uygundur.
	2. Kuyruk Yöneticisi Kümesi (Cluster):
Küme yapısı, kuyruk yöneticilerinin birbirine bağlanmasını basitleştirir. Küme içinde yer alan her kuyruk yöneticisi, kendisine ait bir cluster-receiver kanalına ve bir cluster-sender kanalına sahiptir. Bu sayede, her kuyruk yöneticisi küme içindeki diğer kuyruk yöneticilerine kolayca mesaj gönderebilir.
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
		○ MQSC komutunu kullanarak yapılandırabilirsiniz:

ALTER QMGR DEFCLXQ(CHANNEL)
	2. Mesaj Akışlarını İzole Etme:
		○ Belirli mesaj akışlarını, diğer akışlarla aynı iletim kuyruğunu paylaşmayacak şekilde yapılandırabilirsiniz.
		○ Örneğin, SALES kuyruğuna yönlendirilmiş mesajları izole etmek için Q.SALES adlı yeni bir küme oluşturulabilir ve bu küme iletim kuyruğu yalnızca SALES kanalına bağlı olan mesajlarla kullanılabilir.
	3. Gözetim ve Yönetim Gereksinimleri İçin Küme İletim Kuyrukları Oluşturma:
		○ Bazı durumlarda, farklı küme hedeflerine yönelik mesajları izlemek ve yönetmek için ek iletim kuyrukları tanımlanabilir. Bu, örneğin gözetim veya yönetim gereksinimlerini karşılamak için yapılabilir.
Örnek Yapılandırma Adımları:
Örneğin, SALES, FINANCE, ve DEVELOP adında üç bölümlü bir küme yapısı oluşturulmuştur ve mesaj akışlarının her birini izole etmek için ayrı küme iletim kuyrukları tanımlanabilir.
	1. SALES Kuyruğunu İzole Etme:
		○ Yeni bir küme olan Q.SALES oluşturulabilir ve SALES kuyrukları bu kümeye dahil edilir.
		○ Yeni kanal tanımlamaları yapılır:

DEFINE CHANNEL(Q.SALES.SALER1) CHLTYPE(CLUSSDR) CONNAME('localhost(1416)') CLUSTER(Q.SALES) REPLACE
DEFINE CHANNEL(Q.SALES.SALER2) CHLTYPE(CLUSRCVR) CONNAME('localhost(1417)') CLUSTER(Q.SALES) REPLACE
	2. Küme İletim Kuyruğu Tanımlamaları:
		○ Q.SALES kümesi için iletim kuyruğu tanımlanır:

DEFINE QLOCAL(XMITQ.Q.SALES.SALESRV) USAGE(XMITQ) CLCHNAME(Q.SALES.SALESRV) REPLACE
	3. Gözetim için Küme İletim Kuyruğu Tanımlama:
		○ Finansal mesajlar için ayrı iletim kuyrukları:

DEFINE QLOCAL(XMITQ.SALES)  USAGE(XMITQ) CLCHNAME(SALES.*)  REPLACE
DEFINE QLOCAL(XMITQ.FINANCE)    USAGE(XMITQ) CLCHNAME(FINANCE.*) REPLACE
Sonraki Adımlar:
	• Yeni yapılandırmayı aktive etmek için, geçiş yöneticisindeki tüm kanallar durdurulup yeniden başlatılabilir:
endmqm -i GATE
strmqm GATE
	• Sonrasında, yapılandırmanın doğruluğu test edilmelidir. Testler için, örneğin amqsmon komutuyla iletim kuyruklarındaki mesajları izleyebilirsiniz:

amqsmon -m GATE -t statistics
Bu adımlarla, kümelenmiş IBM MQ ortamlarında mesaj akışlarını daha verimli bir şekilde yönetebilir ve izole edebilirsiniz.



Küme İletim Kuyruklarını Değiştirme (Switching)
Son Güncelleme: 2024-12-06
Bu işlem, mevcut bir üretim kuyruğu yöneticisinde küme iletim kuyruklarını değiştirmek için nasıl bir plan yapılacağına dair yönergeler sağlar. Küme iletim kuyruğunda yapılacak değişiklikler, çalışan sistemin kesintiye uğramaması için dikkatlice yapılmalıdır. Bu işlemde, değişikliklerin etkili hale getirilmesi için iki ana seçenek bulunmaktadır.
Başlamadan Önce
Küme iletim kuyruğunda yapılacak değişikliklerin zamanını minimize etmek, geçiş sürecini hızlandırabilir. Küme-sender kanalı geçiş süreci hakkında bilgi edinmek ve kuyruğun boşaltılması gerektiği konusunda hazırlıklı olmak faydalıdır.
İki Seçenekle Değişiklik Yapma
	1. Otomatik Değişim (Queue Manager tarafından yönetilen)
Bu seçenek, kuyruğu yönetici tarafından otomatik olarak değiştirilmesine izin verir. Küme-sender kanalı bir sonraki başlatıldığında, geçiş işlemi başlatılır ve aktif hale gelir.
		○ Avantaj: Bu yöntem otomatik olup, kanal yeniden başlatıldığında geçiş işlemi otomatik olarak yapılır.
		○ Dezavantaj: Zaman sınırlıysa, bu geçişin tamamlanıp tamamlanamayacağı garanti edilemez. Zamanlamayı kontrol edemiyorsanız, ikinci seçenek daha uygun olabilir.
	2. Manuel Değişim (El ile kontrol edilen geçiş)
Bu seçenek, kuyruğun manuel olarak değiştirilmesini sağlar. Kanal durdurulur ve bu işlemi yaparken belirli bir zaman diliminde kontrol sağlanabilir.
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
	• Adım 1: Kanalı durdurun:

STOP CHANNEL(ChannelName) MODE(QUIESCSE) STATUS(STOPPED)
	• Adım 2: Küme iletim kuyruğunun geçişini başlatın:

runswchl -m QmgrName -c ChannelName
	• Adım 3: Kanalı yeniden başlatın:

START CHANNEL(ChannelName)
Kanal Durumunu İzleme
Geçiş sırasında, kanal durumunu ve iletim kuyruğunun derinliğini izlemek önemlidir. Bu, geçişin nasıl gerçekleştiğini anlamanızı sağlar:
	• Kanal durumu kontrolü:

DISPLAY CHSTATUS(*) WHERE(XMITQ LK 'SYSTEM.CLUSTER.TRANSMIT.*')
	• İletim kuyruğu derinliği izleme:

DISPLAY QUEUE('SYSTEM.CLUSTER.TRANSMIT.*') CURDEPTH
Sonuç:
	• Otomatik Geçiş: Bu yöntem, geçişin kanal yeniden başlatıldığında otomatik olarak yapılmasını sağlar.
	• Manuel Geçiş: Bu seçenek, kanal durdurulup değişiklik yapılmasını sağlar ve geçişin kesin olarak zamanlanması için daha fazla kontrol sunar.

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
	1. Doğrudan Yönlendirilmiş Küme:
Bu, bir küme zaten mevcut olduğunda yapılandırılması en basit topolojidir. Küme içinde herhangi bir kuyruk yöneticisinde tanımlanan herhangi bir konu, kümedeki her kuyruk yöneticisinde otomatik olarak kullanılabilir hale gelir. Yayınlar, bir yayın uygulamasının bağlandığı her bir kuyruk yöneticisinden doğrudan, eşleşen aboneliklerin bulunduğu kuyruk yöneticilerine yönlendirilir. Küçük ve basit ağlar için bu topoloji kabul edilebilirken, daha büyük veya dinamik ortamlarda bu yaklaşımın aşırı yük oluşturması muhtemeldir.
	2. Konu Ana Bilgisayarı Yönlendirilmiş Küme:
Bu topoloji, herhangi bir kuyruk yöneticisinde tanımlanan bir konunun kümedeki her kuyruk yöneticisinde otomatik olarak kullanılabilir hale gelmesini sağlar, ancak konuların hangi kuyruk yöneticilerinde barındırılacağı dikkatlice seçilmelidir. Tüm bilgi ve yayınlar, bu konu ana bilgisayarı kuyruk yöneticileri üzerinden geçer. Bu, sistemin tüm kuyruk yöneticileri arasında kanal bağlantıları ve bilgi akışları bakımını gerektirmediği anlamına gelir. Ancak, bu da yükü artırabilir, özellikle konu barındıran kuyruk yöneticilerinde.
	3. Hiyerarşi:
Bu, en fazla manuel yapılandırma gerektiren topolojidir. Her bir kuyruk yöneticisinin hiyerarşideki doğrudan ilişkileri elle yapılandırılmalıdır. Bu topoloji, belirli gereksinimlere göre çok özelleştirilebilir, ancak bir yayının, aboneliklere ulaşabilmek için birçok kuyruk yöneticisi üzerinden "atlaması" gerekebilir.
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



BM MQ'nin depolama ve performans gereksinimleri, platformlara ve hangi bileşenlerin kullanılacağına bağlı olarak değişir. Bu gereksinimler, uygulamanın verimli çalışabilmesi için doğru yapılandırmanın yapılmasını sağlar. İşte IBM MQ'nin Multiplatformlarda depolama ve performans gereksinimlerini ele alırken göz önünde bulundurulması gereken temel konular:
Depolama Gereksinimleri
IBM MQ, kuyruk yöneticisi verilerini dosya sisteminde saklar. Bu nedenle doğru dosya yapılarının oluşturulması ve yapılandırılması gereklidir. Ayrıca disk alanı gereksinimleri, kurulu bileşenlere, kullanılan kuyruk sayısına ve mesajların boyutlarına bağlı olarak değişir.
Disk Alanı Gereksinimleri:
IBM MQ'nin kurulumunda kullanılacak bileşenlere göre farklı disk alanı gereksinimleri olabilir. Bununla birlikte, bazı bileşenler opsiyoneldir ve ek disk alanı talep edebilir. Örneğin:
	• AIX, Linux, Windows ve IBM i sistemlerinde IBM MQ için ortalama disk alanı gereksinimleri şunlardır:
		○ AIX: 1810 MB (Tam kurulum)
		○ IBM i: 1965 MB (Tam kurulum)
		○ Linux (x86-64): 2010 MB (Tam kurulum)
		○ Windows: 2310 MB (Tam kurulum)
Log Dosyaları ve Performans:
Log dosyaları da önemli bir depolama gereksinimi oluşturur. IBM MQ, dairesel (circular) veya doğrusal (linear) loglama yöntemlerini kullanabilir. Dairesel loglama daha hızlı performans sağlar, çünkü eski loglar yeniden kullanılabilir. Ancak doğrusal loglama daha fazla hata koruması sağlar ve logların geri alımında daha fazla güvenlik sunar.
Paylaşılan Dosya Sistemleri
IBM MQ, çoklu örnek kuyruk yöneticilerini çalıştırırken, paylaşılan dosya sistemleri kullanarak kuyruk yöneticilerinin veri ve log dosyalarını paylaşabilir. Ancak paylaşılan dosya sistemlerinin, veri yazma bütünlüğünü, dosyalara garantili tekil erişim sağlamak ve başarısızlık durumunda kilitlerin serbest bırakılmasını sağlayacak özelliklere sahip olması gerekir.
	• NFS (Network File System) ve SMB (Server Message Block) gibi protokoller, paylaşılan dosya sistemlerinde IBM MQ için kritik öneme sahiptir.
	• Paylaşılan Dosya Sistemi Gereksinimleri:
		○ Veri yazma bütünlüğü: Dosyalar doğru şekilde yazılmalı, özellikle hatalı yazma veya kesilme durumlarıyla başa çıkabilmelidir.
		○ Dosyalara garantili tekil erişim: Bir kuyruk yöneticisi aktifken, başka bir kuyruk yöneticisinin aynı dosyaya erişimi engellenmeli, kilitleme sağlanmalıdır.
		○ Kilidin serbest bırakılması: Kuyruk yöneticisi çökerse veya dosya sistemine bağlantı kaybolursa, kilitlerin doğru şekilde serbest bırakılması gerekir.
Queue Manager Yapısı
IBM MQ, kuyruk yöneticisinin verilerini yerel dosya sistemlerinde saklar, ancak çoklu örnek (multi-instance) kuyruk yöneticileri için veriler paylaşılan dosya sistemlerinde saklanmalıdır. Bu yapılar, performansı ve güvenliği artıracak şekilde yapılandırılabilir.
AIX ve Linux Sistemlerinde Kuyruk Yöneticisi Dizini:
IBM MQ'de kuyruk yöneticisi dizin yapısı genellikle /var/mqm altında oluşturulur. Bu dizin yapısı, qmgrs ve log dizinleri gibi kuyruk yöneticisi verilerini içeren alt dizinleri barındırır. Ayrıca, bu dizinlerin farklı dosya sistemlerinde paylaşılması performansı artırabilir.
Dosya Sistemlerini Test Etme
Paylaşılan dosya sistemlerinin IBM MQ için uygun olup olmadığını test etmek için amqmfsck komutu kullanılabilir. Bu komut, dosya sisteminin IBM MQ gereksinimlerini karşılayıp karşılamadığını kontrol eder.
Loglama Yöntemleri
	• Dairesel Loglama (Circular Logging):
		○ Performans açısından daha iyidir, çünkü eski loglar yeniden kullanılabilir.
		○ Yönetimsel olarak daha kolaydır, çünkü ek log dosyaları oluşturulmaz.
	• Doğrusal Loglama (Linear Logging):
		○ Hata durumlarına karşı daha fazla güvenlik sağlar, çünkü hasar görmüş nesneler doğrusal loglardan geri alınabilir.
		○ Daha fazla yönetim gereksinimi ve performans kaybı vardır, çünkü her log yeni bir medya görüntüsü gerektirir.
Özet
IBM MQ'nun verimli çalışabilmesi için doğru depolama ve performans yapılandırmalarının yapılması gerekmektedir. Paylaşılan dosya sistemleri, loglama yöntemleri ve kuyruk yöneticisi dizin yapıları, sistemin güvenli ve yüksek performanslı çalışmasını sağlamak için doğru şekilde planlanmalıdır. Bu gereksinimler, işletim sistemi türüne ve IBM MQ yapılandırmasına göre değişebilir.

