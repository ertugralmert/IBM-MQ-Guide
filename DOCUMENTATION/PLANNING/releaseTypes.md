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


****************

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


*****************************

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


