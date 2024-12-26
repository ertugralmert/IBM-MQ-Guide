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
