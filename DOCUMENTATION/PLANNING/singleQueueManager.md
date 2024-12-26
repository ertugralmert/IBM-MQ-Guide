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
