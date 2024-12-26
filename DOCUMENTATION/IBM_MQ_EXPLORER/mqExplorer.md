IBM MQ Explorer Nedir?
IBM MQ Explorer, IBM MQ nesnelerini yönetmek ve izlemek için kullanılan grafiksel bir kullanıcı arayüzüdür (GUI). IBM MQ Explorer:
	• Yerel bilgisayarınızdaki veya uzak bir sistemdeki kuyruk yöneticilerini (queue manager) yönetmenize olanak tanır.
	• Windows ve Linux x86-64 sistemlerinde çalışır.
	• z/OS dahil olmak üzere tüm desteklenen platformlardaki kuyruk yöneticilerine uzaktan bağlanabilir.
	• Eclipse tabanlıdır ve özelleştirilebilir, genişletilebilir bir yapıya sahiptir.
Not: IBM MQ 9.3.0'dan itibaren, IBM MQ Explorer artık IBM MQ kurulum paketiyle birlikte gelmemektedir. Ancak, Fix Central'dan bağımsız bir indirme olarak edinilebilir.

Kurulum Gereksinimleri
IBM MQ Explorer'ı kurmadan önce aşağıdaki minimum gereksinimleri kontrol edin:
	• RAM: 512 MB
	• İşlemci: 1 GHz
	• Disk Alanı: En az 300 MB
	• Ekran: En az 1024x768 çözünürlük
	• Linux için:
		○ GTK2 ve ilgili temalar (GTK2-engines)
		○ Bitstream-vera-fonts
		○ GTK3 varsa, SWT_GTK3=0 çevre değişkenini ayarlayarak devre dışı bırakılmalı.
Desteklenen Platformlar:
	• IBM MQ Explorer, yalnızca desteklenen Eclipse sürümleri ile uyumludur.

IBM MQ Explorer'ın Yüklenmesi
Fix Central'dan İndirme ve Yükleme
	1. Fix Central'a Git:
		○ Fix Central adresinden IBM MQ Explorer'ı indirin.
	2. Kurulum Dosyasını Çalıştırın:
		○ İndirilen dosyayı çalıştırarak kurulum işlemini tamamlayın.
Eclipse Ortamına Yükleme
IBM MQ Explorer, kendi Eclipse ortamınıza veya Eclipse tabanlı bir ürüne eklenti olarak yüklenebilir.
	1. Eclipse’te "New Software" Seçeneğini Açın:
		○ Eclipse’de Help > Install New Software seçeneğine tıklayın.
	2. MQExplorerSDK.zip Dosyasını Seçin:
		○ IBM MQ kurulum dizinindeki mqexplorer/eclipse klasöründe bulunan MQExplorerSDK.zip dosyasını seçin.
	3. MQ Explorer Kategorisini Seçin:
		○ MQ Explorer kategorisini genişletin ve gerekli bileşenleri seçin.
	4. Kurulumu Tamamlayın ve Eclipse'i Yeniden Başlatın:
		○ Kurulum talimatlarını izleyerek işlemi tamamlayın.

IBM MQ Explorer’ın Başlatılması
Linux’ta Başlatma
	1. Sistem Menüsünden Açın:
		○ SUSE için: Computer > More Applications... > Development yolunu takip edin.
		○ Red Hat için: Applications > Programming altında bulunabilir.
	2. Komut Satırından Başlatma:bashCopy code/opt/mqexplorer/MQExplorer
Windows’ta Başlatma
	1. Başlat Menüsünden Açın:
		○ IBM MQ Explorer seçeneğini IBM MQ grubundan seçin.
	2. Komut Satırından Başlatma:cmdCopy code"C:\Program Files\IBM\MQ Explorer\MQExplorer.exe"

IBM MQ Explorer ile Yapılabilecekler
1. Kuyruk Yöneticilerini Yönetme
	• Kuyruk Yöneticisi Ekleme:
		○ Navigator görünümünde sağ tıklayın ve New > Queue Manager seçeneğini seçin.
	• Kuyruk Oluşturma ve Yapılandırma:
		○ Bir kuyruk yöneticisini seçtikten sonra sağ tıklayarak yeni bir kuyruk oluşturabilirsiniz.
	• Kanalları Yönetme:
		○ Channels sekmesinden mevcut kanalları görebilir ve yeni kanal oluşturabilirsiniz.
2. JMS Yönetilen Nesneleri Yapılandırma
	• IBM MQ Explorer, Java uygulamaları ile iletişim kurmak için gerekli JMS nesnelerini yapılandırmanıza olanak tanır.
	• Navigator görünümünde JMS Administered Objects kısmını kullanarak işlemleri gerçekleştirebilirsiniz.
3. İzleme ve Sorun Giderme
	• IBM MQ Explorer üzerinden izleme yapmak ve günlükleri incelemek mümkündür.
	• Runwithtrace Komutu:
		○ Linux: runwithtrace
		○ Windows: runwithtrace.cmd

Görsel Yardım ve Ayarlar
Bağlamsal Yardım (Pop-up Help)
	• Yardım Almak İçin:
		○ Windows: F1 tuşuna basın.
		○ Linux: Ctrl+F1 tuşlarına basın.
	• Yardım ayarlarını değiştirmek için: Window > Preferences > Help.

Notlar ve Öneriler
	• Yerel kuyruk yöneticilerini yönetmek için ek yapılandırma gerekebilir:
		○ Linux: LD_LIBRARY_PATH ve setmqenv ayarlanmalı.
		○ Windows: setmqenv komutu kullanılarak PATH ayarları yapılmalı.
	• Sık kullanılan işlemler için bir toplu işlem dosyası (batch file) oluşturabilirsiniz.
	
	
	
	
	
	
	
	

****


IBM MQ Explorer Kullanarak IBM MQ’yu Yapılandırma
Navigator Görünümünden Yapılandırma
IBM MQ Explorer’da Navigator Görünümü üzerinden IBM MQ'nun tüm kurulumuna veya belirli kuyruk yöneticilerine yönelik ayarları yapılandırabilirsiniz. Bu işlemleri aşağıdaki adımları izleyerek gerçekleştirebilirsiniz:
	1. Navigator Görünümünde IBM MQ’yu Seçin:
		○ Sağ tıklayın ve Properties... seçeneğine tıklayın.
		○ Properties (Özellikler) penceresi açılacaktır.
	2. Aşağıdaki Özellikleri Yapılandırın:
		○ General (Genel): Kuyruk yöneticilerinin varsayılan konumu gibi temel özellikleri ayarlayın.
		○ Extended (Gelişmiş): EBCDIC ile ASCII arasında dönüşüm gibi ileri düzey özellikleri yapılandırın.
		○ Exits: IBM MQ ile entegre çalışacak kendi yazdığınız kod modüllerini tanımlayın.
		○ Default Log Settings (Varsayılan Günlük Ayarları): IBM MQ günlüklerinin türünü ve konumunu değiştirin.
		○ ACPI: Bilgisayarın uyku moduna geçmesi sırasında IBM MQ'nun nasıl davranacağını belirleyin.
		○ Alert Monitor: Önemli bir kuyruk eksikliği gibi sorunlarda uyarı almak için yapılandırma yapın.
	3. Sonuç:
		○ Yapılan değişiklikler, belirli kuyruk yöneticileri farklı ayarlara sahipse bunlar hariç tüm kurulum için geçerli olur.

Kuyruk Yöneticileri ve Nesneler Oluşturma ve Yapılandırma
Kuyruk Yöneticileri ve Nesneler
IBM MQ Explorer’da kuyruk yöneticileri ve diğer nesneler, Navigator Görünümü altında klasörler halinde düzenlenmiştir. Örnekler:
	• Queue Managers (Kuyruk Yöneticileri): Tüm kuyruk yöneticilerini içerir.
	• Channels (Kanallar): Belirli bir kuyruk yöneticisinin kanallarını gösterir.
Her klasörde sağ tıklayarak aşağıdaki işlemleri yapabilirsiniz:
	• Yeni Nesne Oluşturma: Yeni bir kuyruk, kanal veya abone gibi nesneler ekleyin.
	• Nesneyi Yapılandırma: Mevcut bir nesneyi düzenlemek için nesneye sağ tıklayın ve Properties seçeneğini seçin.
	• Nesneyi Silme: Seçilen nesneyi sistemden kaldırın.
Yaygın Kullanılan Kuyruk Türleri
	• Local Queue (Yerel Kuyruk): Mesajları yerel olarak tutar.
	• Transmission Queue (Aktarım Kuyruğu): Uzak kuyruklara mesaj iletiminde kullanılır.
	• Alias Queue (Takma Ad Kuyruk): Mevcut bir kuyruğun alternatif adıdır.
	• Model Queue (Model Kuyruk): Dinamik olarak kuyruk oluşturmak için bir şablon sağlar.

Yayın/Abone Mesajlaşma Modeli
IBM MQ, yayıncı (publisher) ve abone (subscriber) modelini destekler. Bu modelde:
	• Yayıncılar: Mesajlarını belirli bir konu (topic) üzerinden gönderir.
	• Aboneler: İlgi duydukları konulara abone olarak ilgili mesajları alır.
Konu ve Abonelikler
	• Konu Tanımı: Mesajın içeriğini tanımlayan bir karakter dizisidir. Örneğin, “/hissem/satislar”.
	• Abonelikler: Bir abonenin hangi konuları takip ettiğini belirler.
	• Wildcard (Joker Karakterler):
		○ # (Multilevel): Birden fazla alt seviyeyi kapsar.
		○ + (Single Level): Yalnızca bir alt seviyeyi kapsar.

Kanal Türleri ve Dinleyiciler
Kanal Türleri
IBM MQ, üç ana kanal türünü destekler:
	1. Mesaj Kanalları: Kuyruk yöneticileri arasında mesajları taşır.
		○ Örneğin: Sender-Receiver (Gönderen-Alıcı) kanalları.
	2. MQI Kanalları: Uygulamalar ve kuyruk yöneticileri arasında çift yönlü bağlantı sağlar.
		○ Örneğin: Server Connection (Sunucu Bağlantısı).
	3. AMQP Kanalları: AMQP istemcileri ve kuyruk yöneticileri arasında bağlantı kurar.
Dinleyiciler (Listeners)
	• Kuyruk yöneticisine gelen bağlantıları dinleyen bir süreçtir.
	• Navigator Görünümünde Dinleyici Oluşturma:
		○ Kuyruk yöneticisine sağ tıklayın, New > Listener seçeneğini seçin.

Kümeler (Clusters)
Küme Nedir?
Bir küme, mantıksal olarak ilişkili iki veya daha fazla kuyruk yöneticisinin grup halinde düzenlenmesidir. Kümeler sayesinde:
	• Herhangi bir kuyruk yöneticisi, küme içindeki diğerlerine mesaj gönderebilir.
	• İş yükü paylaştırması yapılabilir.
Küme Kuyrukları
	• Küme içindeki diğer kuyruk yöneticileri tarafından erişilebilir.
	• Örneğin: İş yükü paylaşımı için aynı isimde birden fazla kuyruk oluşturabilirsiniz.

IBM MQ Explorer Kullanımı İçin İpuçları
	• Bağlantı Testi: Kanalların doğru çalıştığını kontrol etmek için kanal “ping” testi yapabilirsiniz.
	• Test Mesajları Gönderme: Kuyruklara test mesajları göndererek bağlantıları kontrol edin.
	• Nesnelerin Durumunu İzleme: Mevcut nesnelerin durumlarını görüntüleyin ve gerektiğinde müdahale edin.
	• Sorun Giderme: Günlük ve izleme özelliklerini kullanarak sorunları hızlıca çözün.


*****

JMS Nesnelerinden IBM MQ Nesneleri Oluşturma
IBM MQ Explorer ile mevcut bir JMS kuyruğundan veya konusundan yeni bir IBM MQ nesnesi oluşturabilirsiniz. Bu işlem sırasında JMS nesnesinin ilgili özellikleri yeni oluşturulan IBM MQ nesnesine kopyalanır.
Adım Adım JMS Nesnesinden IBM MQ Nesnesi Oluşturma
	1. JMS Nesnesini İçeren Bağlamı Açın:
		○ Navigator Görünümü içinde, JMS nesnesini içeren başlangıç bağlamını genişletin.
		○ Destinations (Hedefler) klasörüne tıklayın.
	2. Nesneyi Seçin ve IBM MQ Nesnesi Oluşturun:
		○ Content Görünümü içinde, nesneye sağ tıklayın.
		○ Create MQ Queue veya Create MQ Topic seçeneğini seçin (uygun olanı).
	3. Wizard’ı Kullanarak IBM MQ Nesnesini Tanımlayın:
		○ New Queue veya New Topic wizard’ını açın.
		○ Kuyruk yöneticisini seçin.
		○ Wizard içindeki adımları tamamlayarak yeni IBM MQ nesnesini tanımlayın.
	4. Sonuç:
		○ Yeni IBM MQ nesnesi oluşturulur ve ilgili kuyruk yöneticisinin altında görünür.

IBM MQ ve JMS Nesnelerini Aynı Anda Oluşturma
IBM MQ Explorer, aynı türden bir JMS nesnesi ile eşzamanlı olarak bir IBM MQ nesnesi oluşturmanıza olanak tanır.
Örnekler
	1. IBM MQ Kuyruğu ve JMS Kuyruğu Eşzamanlı Oluşturma:
		○ Navigator Görünümü içinde kuyruk yöneticisine sağ tıklayın.
		○ New > Local Queue seçeneğini seçin.
		○ Wizard’da bir kuyruk adı girin ve Start wizard to create a matching JMS Queue seçeneğini işaretleyin.
		○ IBM MQ kuyruğu oluşturma işlemi tamamlandığında, JMS Kuyruğu Wizard’ı açılır ve gerekli detaylar otomatik olarak aktarılır.
	2. IBM MQ Konusu ve JMS Konusu Eşzamanlı Oluşturma:
		○ Aynı adımları takip ederek bir konu oluşturabilirsiniz. Sadece Topic seçeneğini kullanın.

Kuyruk Yöneticilerini ve Nesneleri Yapılandırma
IBM MQ Explorer, kuyruk yöneticileri ve nesneler için yapılandırma özelliklerini düzenlemek için kapsamlı bir özellikler (Properties) penceresi sağlar.
Yapılandırma Adımları
	1. Nesneyi veya Kuyruk Yöneticisini Seçin:
		○ Navigator Görünümü içinde ilgili klasöre tıklayarak nesneyi seçin.
		○ Örneğin, bir kuyruğu yapılandırmak için Queues klasörünü seçin.
	2. Özellikleri Düzenleyin:
		○ Nesneye sağ tıklayın ve Properties seçeneğini seçin.
		○ Gerekli ayarları düzenleyin ve Apply veya OK butonuna tıklayarak kaydedin.
	3. Sonuç:
		○ Çoğu değişiklik hemen uygulanır. Ancak, örneğin TLS anahtar deposunun konumu gibi bazı değişiklikler için kuyruk yöneticisinin yeniden başlatılması gerekebilir.

Nesne Özelliklerini Karşılaştırma
IBM MQ Explorer, aynı türden iki nesnenin özelliklerini karşılaştırmanıza olanak tanır.
Karşılaştırma Adımları
	1. Nesneye Sağ Tıklayın ve Karşılaştırın:
		○ Compare With... seçeneğini seçin.
	2. İkinci Nesneyi Seçin:
		○ Aynı kuyruk yöneticisinden veya farklı bir kuyruk yöneticisinden nesne seçebilirsiniz.
	3. Farkları Görüntüleme:
		○ Varsayılan olarak, yalnızca farklı özellikler görüntülenir. Tüm özellikleri görmek için Show differences only seçeneğini devre dışı bırakın.

Kanalları Test Etme ve Yönetme
Bir Kanalı Pinglemek
Kanalların doğru tanımlandığından emin olmak için bir kanal ping testi gerçekleştirebilirsiniz.
	1. Kanala Sağ Tıklayın:
		○ Ping seçeneğini seçin.
	2. Sonuçları Değerlendirin:
		○ Başarılı bir ping işlemi için: IBM MQ successfully sent data to the remote queue manager mesajı görünür.
Bir Kanalı Elle Başlatma
	1. Kanala Sağ Tıklayın ve Başlatın:
		○ Start seçeneğini seçin.
	2. Dinleyiciyi Başlatma:
		○ Yanıtlayıcı kanalları başlatırken dinleyicinin çalışıyor olması gerekir.

Kuyruk Yöneticisi veya Nesne Silme
Bir kuyruk yöneticisini veya nesneyi silmeden önce bu nesnenin başka bir uygulama tarafından kullanılmadığından emin olun.
Adımlar
	1. Nesneyi Seçin ve Sağ Tıklayın:
		○ Delete seçeneğini seçin.
	2. Mesajları Temizleyin (Gerekirse):
		○ Kuyrukta mesajlar varsa, silme işlemi için önce bu mesajları temizlemeniz istenir.
	3. Silme İşlemini Onaylayın:
		○ Delete butonuna tıklayın.


***

Nesne Tanımlamalarını Test Etme
IBM MQ Explorer, nesne tanımlamalarını doğrulamak için testler sunar. Bu testler, hem hataları hem de olası sorunları belirlemek için tasarlanmıştır.
Testleri Çalıştırma
Varsayılan Testleri Çalıştırma
	1. Navigator Görünümü’nde bir nesneye veya klasöre sağ tıklayın.
	2. Tests > Run Default Tests seçeneğini seçin.
	3. Testler çalışırken, işlemi arka planda sürdürmek için Run in Background butonuna tıklayın.
	4. Testler tamamlandığında sonuçlar Test Results görünümünde gösterilir.
Kendi Test Yapılandırmanızı Oluşturma
	1. Navigator Görünümü’nde, bir nesneye veya klasöre sağ tıklayın.
	2. Tests > Run Custom Test Configuration seçeneğini seçin.
	3. Run Tests Configurations dialog penceresi açılır.
	4. New butonuna tıklayarak yeni bir test yapılandırması oluşturun.
	5. Testleri ve nesneleri seçin:
		○ Testlerin otomatik güncellenmesi için Automatically include any new tests seçeneğini işaretleyin.
		○ Yeni nesnelerin dahil edilmesi için Automatically include any new objects seçeneğini işaretleyin.
	6. Run butonuna tıklayarak yapılandırmayı çalıştırın.
Bireysel Bir Testi Yeniden Çalıştırma
	1. Test Results görünümünde, bir test sonucuna sağ tıklayın.
	2. Run This Test Again seçeneğini seçin.
	3. Test yeniden çalıştırılır ve sonuçlar güncellenir.

Test Sonuçlarını Görüntüleme ve Yönetme
Sonuçları Görüntüleme
	• Test sonuçları Test Results görünümünde gösterilir.
	• Bir sonuca çift tıklayarak detaylarını inceleyebilirsiniz.
Sonuçları Filtreleme
	1. Test Results görünümünde filtre ikonuna tıklayın.
	2. Filters dialog penceresini açarak kriterleri belirleyin (örneğin, yalnızca hataları göstermek).
	3. OK butonuna tıklayarak filtreyi uygulayın.
Sonuçları Sıralama
	• Test Results görünümünde bir sütun başlığına tıklayarak sonuçları artan veya azalan şekilde sıralayın.

Test Mesajları Gönderme ve Kuyruk Yönetimi
IBM MQ Explorer ile kuyruklara test mesajları gönderebilir, mevcut mesajları gözden geçirebilir ve kuyruktaki mesajları temizleyebilirsiniz.
Test Mesajı Gönderme
	1. Navigator Görünümü’nde, Queues klasörüne tıklayın.
	2. İlgili kuyruk Content Görünümü’nde listelenir.
	3. Kuyruğa sağ tıklayın ve Put Test Message... seçeneğini seçin.
	4. Açılan dialog penceresinde Message data alanına bir mesaj yazın (örneğin, "This is a test message").
	5. Put Message butonuna tıklayın.
	6. Close ile dialog penceresini kapatın.
Sonuç: Kuyruğun Current queue depth sütunundaki değer bir artar.

Kuyruktaki Mesajları Gözden Geçirme
	1. Kuyruğa sağ tıklayın ve Browse Messages... seçeneğini seçin.
	2. Açılan Message Browser penceresinde mesajları inceleyebilirsiniz.
	3. Bir mesaja çift tıklayarak özelliklerini ve verilerini görüntüleyin.

Kuyruktaki Mesajları Temizleme
	1. Kuyruğa sağ tıklayın ve Clear Messages... seçeneğini seçin.
	2. Clear Queue dialog penceresi açılır.
	3. Kullanmak istediğiniz temizleme yöntemini seçin:
		○ CLEAR komutu: Kuyruktaki tüm mesajları temizler, ancak uncommitted mesajlar kalabilir.
		○ MQGET API çağrısı: Kuyruktaki mesajları işler ancak uncommitted mesajları göz ardı eder.
	4. Clear butonuna tıklayın.
	5. İşlem tamamlandığında bir mesaj görüntülenir.

IBM MQ Explorer Tarafından Sağlanan Testler
IBM MQ Explorer aşağıdaki kategorilerde testler sağlar:
	• Genel Testler: Kuyruk yöneticisi adlarını ve ölü mektup kuyruklarını doğrular.
	• Küme Testleri: Küme tanımlarını kontrol eder.
	• Kuyruk Testleri: Kuyruk tanımlarını ve özelliklerini doğrular.
	• Kanal Testleri: Kanal çiftlerini ve bağlantı adlarını test eder.
	• Dinleyici Testleri: TCP portlarının kullanımını kontrol eder.
	• Tetikleme Testleri: Kuyruk tetikleme tanımlarını doğrular.
	• SSL/TLS Testleri: SSL/TLS yapılandırmalarını test eder.
Her test kategorisi, IBM MQ yapılandırmanızı optimize etmek ve sorunları belirlemek için önemlidir.


****

Kuyruk Yöneticilerinin Başlatılması ve Durdurulması
Bireysel Kuyruk Yöneticisini Başlatma veya Durdurma
	1. Navigator Görünümü’nde, Queue Managers klasörünü genişletin.
	2. İlgili kuyruk yöneticisine sağ tıklayın ve Start veya Stop seçeneğini seçin.
	3. Kuyruk yöneticisini durdururken:
		○ Controlled: Mevcut işlemlerin tamamlanmasını bekler.
		○ Immediate: Kuyruk yöneticisini hemen durdurur.
	4. OK butonuna tıklayın.
Sonuç: Kuyruk yöneticisinin simgesi, durumunu gösterecek şekilde değişir.
Tüm Kuyruk Yöneticilerini Başlatma veya Durdurma
	1. Kuyruk yöneticilerini bir sette göstermek için bir set tanımlayın.
	2. Navigator Görünümü’nde, Queue Managers klasörünü genişletin.
	3. Sete sağ tıklayın ve Start Local Queue Managers veya Stop Local Queue Managers seçeneğini seçin.

Kanalların Başlatılması ve Durdurulması
Kanalları Başlatma
	1. Navigator Görünümü’nde, Channels klasörüne tıklayın.
	2. Content Görünümü’nde, başlatmak istediğiniz kanala sağ tıklayın ve Start seçeneğini seçin.
Sonuç: Kanal başlatılır ve simgesi aktif olduğunu gösterecek şekilde değişir.
Kanalları Durdurma
	1. Navigator Görünümü’nde, Channels klasörüne tıklayın.
	2. Content Görünümü’nde, durdurmak istediğiniz kanala sağ tıklayın ve Stop seçeneğini seçin.
	3. Stop Channel dialog penceresinde bir durdurma yöntemi seçin:
		○ Varsayılan Durum: Mevcut mesajların işlenmesini tamamladıktan sonra durur.
		○ Force interruption of current message batch: Mevcut mesaj grubunu keser.
		○ Allow process/thread termination: Kanal iş parçacığını veya sürecini sonlandırır.
		○ Stopped: Kanal durur ancak kaynak kullanmaya devam eder.
		○ Inactive: Kanal tamamen durur ve kaynak kullanmayı bırakır.

Listener’ların Başlatılması ve Durdurulması
	1. Navigator Görünümü’nde, Listeners klasörüne tıklayın.
	2. Content Görünümü’nde, başlatmak veya durdurmak istediğiniz listener’a sağ tıklayın.
	3. Start veya Stop seçeneğini seçin.
Sonuç: Listener başlar veya durur.

Komut Sunucularının Başlatılması ve Durdurulması
	1. Navigator Görünümü’nde, ilgili kuyruk yöneticisine sağ tıklayın.
	2. Start Command Server veya Stop Command Server seçeneğini seçin.
Sonuç: Komut sunucusu başlar veya durur.

Özel Servislerin Başlatılması ve Durdurulması
Manuel Başlatma veya Durdurma
	1. Navigator Görünümü’nde, Services klasörüne tıklayın.
	2. Content Görünümü’nde, başlatmak veya durdurmak istediğiniz servise sağ tıklayın.
	3. Start veya Stop seçeneğini seçin.
Sonuç: Servis başlar veya durur.
Otomatik Başlatma Ayarları
	• Servis özelliklerindeki Service control alanında Queue Manager veya Queue Manager Start seçeneklerini belirleyerek servislerin otomatik başlatılmasını sağlayabilirsiniz.

Trigger Monitörünü Başlatma
	1. Trigger monitörü başlatmak için bir servis oluşturun:
		○ Navigator Görünümü’nde, kuyruk yöneticisine sağ tıklayın ve New > Service seçeneğini seçin.
		○ Start Command alanına MQ_INSTALLATION_PATH\bin\runmqtrm komutunu yazın.
		○ Başlatılacak kuyruk adını belirtmek için Start args alanına -q initq_name yazın.
	2. Servisi başlatın:
		○ Content Görünümü’nde, oluşturulan servise sağ tıklayın ve Start seçeneğini seçin.

Kanal İnisiyatörünü Başlatma
	1. Kanal inisiyatörü için bir servis oluşturun:
		○ Navigator Görünümü’nde, kuyruk yöneticisine sağ tıklayın ve New > Service seçeneğini seçin.
		○ Start Command alanına MQ_INSTALLATION_PATH\bin\runmqchi komutunu yazın.
	2. Servisi başlatın:
		○ Content Görünümü’nde, oluşturulan servise sağ tıklayın ve Start seçeneğini seçin.

Kuyruk Yöneticilerini Gösterme veya Gizleme
	• Bir kuyruk yöneticisini göstermek için:
		○ Queue Managers klasöründe Show Queue Manager seçeneğini kullanın.
	• Gizlemek için:
		○ Queue Managers klasöründe kuyruk yöneticisine sağ tıklayın ve Hide Queue Manager seçeneğini seçin.


****

IBM MQ ile çalışırken bağlantı kurma, uzaktan yönetim ve güvenlik ayarları gibi işlemleri nasıl gerçekleştirebileceğinize dair kapsamlı bir rehber hazırladım. İşte IBM MQ'nun ilgili konularındaki temel detaylar:

Kuyruk Yöneticisine Bağlanma veya Bağlantıyı Kesme
IBM MQ Explorer üzerinden bir kuyruk yöneticisini yönetmek için önce bu yöneticiyi bağlamanız gerekir.
Ön Koşullar
	• Kuyruk yöneticisi IBM MQ Explorer'da Queue Managers klasöründe görüntülenmelidir.
	• Uzaktan bir kuyruk yöneticisi bağlanacaksa, kuyruk yöneticisinin çalıştığından emin olun.
Adımlar
	1. Navigator Görünümü’nde, kuyruk yöneticisine sağ tıklayın.
	2. Connect veya Disconnect seçeneğini seçin.
Sonuç: Bağlı bir kuyruk yöneticisinin simgesi sarı renkte, bağlantısı kesilmiş bir yöneticinin simgesi ise gri renkte görünür.

Uzaktan Kuyruk Yöneticilerinin Yönetimi
Uzaktan Yönetim İçin Gereksinimler
	• Kuyruk yöneticisi uzaktan yönetim için TCP/IP ile bağlantılı olmalıdır.
	• Uzaktan yönetim için SYSTEM.ADMIN.SVRCONN kanalının etkinleştirilmesi gerekir.
Uzaktan Kuyruk Yöneticisi Yönetimi
	1. Bilgisayar A’da (uzaktaki kuyruk yöneticisinin bulunduğu bilgisayar):
		○ Kuyruk yöneticisini IBM MQ Explorer’da görüntüleyin.
		○ Kuyruk yöneticisini başlatın.
		○ Uzaktan yönetim için gerekli ayarları yapın.
	2. Bilgisayar B’de (IBM MQ Explorer’ın bulunduğu bilgisayar):
		○ Uzaktaki kuyruk yöneticisini IBM MQ Explorer’da gösterin.

Kanal Senkronizasyonunun ve İn-Doubt Durumlarının Çözülmesi
Kanalların senkronizasyon sorunlarını çözmek veya in-doubt durumundaki kanalları yönetmek için aşağıdaki yöntemleri kullanabilirsiniz.
Kanal Senkronizasyonunun Sıfırlanması
	• Kanal uçlarındaki mesaj sayımları senkronize değilse, senkronizasyonu sıfırlamak gerekebilir.
In-Doubt Kanal Sorunlarının Çözülmesi
	• Mesajları geri çekme (backout) veya onaylama (commit) işlemlerini kullanarak sorunları çözebilirsiniz.
Kanalların İn-Doubt Olma İhtimalini Azaltma
	• Batch heartbeat interval özelliğini kullanarak kanalların in-doubt duruma düşme olasılığını azaltabilirsiniz.

Yayın/Abonelik Mesajlaşmasının Yapılandırılması
Yayın/Abonelik yöntemiyle bir gönderici (yayıncı) mesajları doğrudan alıcıları bilmeden bir konuya (topic) yayınlar.
Yapılandırma Adımları
	1. Konu (Topic) Oluşturma: Yayınlanacak bilginin konusunu tanımlayın.
	2. Yeni Bir Abonelik Oluşturma: Abone olacak bir uygulama için abonelik oluşturun.
	3. Test Yayınları Gönderme ve Alma: Ağınızı test etmek için mesaj yayınlayın ve alın.

Çoklu Örnek Kuyruk Yöneticilerinin Yönetimi
Bağlantı Yönetimi
	• IBM MQ Explorer’da, birden fazla örneği olan kuyruk yöneticileri için bağlantılar oluşturabilirsiniz.
	• Aktif ve yedek durumdaki örneklerin bağlantılarını test ettiğinizden emin olun.
Dinleyiciler ve Servisler
	• Her örnek için dinleyicilerin çalıştığından emin olun.
	• Dinleyiciler, kuyruk yöneticisi ile birlikte başlatılıyorsa, elle başlatmamaya dikkat edin.

Kümelerin (Cluster) Yapılandırılması
Küme Tanımları
	• Kümeler, kuyruk yöneticilerinin mantıksal olarak ilişkilendirildiği ve bilgiyi paylaştığı gruplardır.
	• Mesajlar, bir kuyruk yöneticisinden kümeye tanımlı başka bir kuyruk yöneticisine otomatik olarak yönlendirilir.
Küme İşlemleri
	1. Yeni Bir Küme Oluşturma: Yeni bir küme tanımlayın.
	2. Kuyruk Yöneticisini Küme’ye Ekleme: Bir kuyruk yöneticisini tam veya kısmi bir depo olarak kümeye ekleyin.
	3. Kümeden Çıkarma veya Askıya Alma: Geçici olarak kuyruk yöneticisinin küme paylaşımını durdurabilirsiniz.

Güvenlik ve Yetkilendirme Yönetimi
TLS Kullanarak Güvenli Kanallar
	• Transport Layer Security (TLS) kullanarak güvenli iletişim sağlayabilirsiniz.
	• Sertifikalarla kimlik doğrulama ve mesaj şifreleme yapabilirsiniz.
Yetki Yönetimi
	• IBM MQ nesnelerine erişim yetkilerini yönetmek için yetkilendirme servisini kullanabilirsiniz.

Bağlantıların Görüntülenmesi ve Kapatılması
	• Bir kuyruk yöneticisine bağlı uygulamaları ve bu uygulamaların eriştiği nesneleri görüntüleyebilirsiniz.
	• Bir bağlantıyı kapatmak için:
		1. Kuyruk yöneticisine sağ tıklayın ve Application Connections seçeneğini seçin.
		2. Kapatmak istediğiniz bağlantıyı seçin ve Close Connection butonuna tıklayın.
Sonuç: Bağlantı kesilir ve uygulama artık kuyruk yöneticisinin nesnelerine erişemez.



****


Troubleshooting Problems with IBM MQ Explorer
IBM MQ Explorer sorunları ile karşılaştığınızda, bu sorunları çözmek için çeşitli tanılama ve çözüm tekniklerini kullanabilirsiniz. İşte sorun giderme işlemleri için kapsamlı bir rehber:

1. Sorun Giderme Yaklaşımları
	• Hata Mesajları:
		○ IBM MQ Explorer’da bir hata mesajı alırsanız, More Details butonuna tıklayarak daha fazla bilgi alabilirsiniz.
		○ Hata mesajı genellikle sorunun nedenini ve çözüm yollarını içerir.
	• Test Etme:
		○ Object Definitions (Nesne Tanımları): Sorunların kaynağı genellikle yanlış nesne tanımlamalarıdır. Nesne tanımlarını test ederek potansiyel problemleri tespit edebilirsiniz.
		○ Daha fazla bilgi için: Testing your object definitions for problems.

2. IBM MQ Explorer İzleme (Trace) Toplama
IBM MQ Explorer’da izleme (trace) aktifleştirilerek sistemin detaylı davranışları incelenebilir.
Windows İçin İzleme Toplama
	1. IBM MQ Explorer’ı Kapatın:
		○ İzleme oturumu başlatılmadan önce açık olan tüm IBM MQ Explorer pencerelerini kapatın.
	2. runwithtrace.cmd Komutunu Kullanma:
		○ Komut Satırını açın.
		○ runwithtrace.cmd komutunu çalıştırarak IBM MQ Explorer’ı izleme aktif halde başlatın.
		○ Komut:cmdCopy codecd MQ_INSTALLATION_PATH/binrunwithtrace.cmd
		○ İzleme dosyasının çıkış yeri, komut satırında görüntülenir.
Linux İçin İzleme Toplama
	1. IBM MQ Explorer’ı Kapatın:
		○ İzleme oturumu başlamadan önce IBM MQ Explorer’ı kapatın.
	2. runwithtrace Komutunu Kullanma:
		○ Terminali açın.
		○ runwithtrace komutunu çalıştırarak izlemeyi aktif hale getirin.
		○ Komut:bashCopy codecd MQ_INSTALLATION_PATH/bin./runwithtrace

3. IBM MQ İzleme (Trace) Kullanımı
IBM MQ Trace, sistemin nasıl çalıştığına dair detaylı bilgiler sağlar. Bu araç, özellikle karmaşık sorunların çözümünde kullanışlıdır.
İzleme Dosyası Adlandırması
	• İzleme dosyası formatı: AMQYYYYMMDDHHmmssmmm.TRC.n
		○ YYYYMMDD: Tarih
		○ HHmmssmmm: Saat, dakika ve milisaniye
		○ .n: Dosya numarası (dosya boyutu maksimuma ulaştığında artar).

4. Javacore Dosyası Toplama
Bazı sorunlarda, kullanıcı arayüzündeki içsel süreçleri incelemek için Javacore dosyası toplanması gerekebilir.
Javacore Dosyasını Toplama
	1. IBM MQ Explorer’ı Açık Tutun:
		○ Sorunun yaşandığı anda IBM MQ Explorer açık olmalıdır.
	2. Javacore Toplama Komutu:
		○ Komut satırında, aşağıdaki komutları çalıştırarak Javacore oluşturun:bashCopy codekill -3 <process_id>
		○ <process_id>: IBM MQ Explorer'ın işlem kimliği.

5. Yaygın Sorunlar ve Çözümleri
Bağlantı Sorunları
	• Kuyruk yöneticisi bağlanamıyor:
		○ Kuyruk yöneticisinin çalıştığından emin olun.
		○ TCP/IP bağlantı ayarlarını kontrol edin.
Nesne Erişim Sorunları
	• Hatalı nesne tanımları:
		○ Nesne tanımlarını ve izinlerini kontrol edin.
		○ Gerekirse nesneleri yeniden yapılandırın.
Performans Sorunları
	• İzleme (Trace) aktif halde bırakılmış olabilir. İzleme işlemi bittikten sonra izlemeyi devre dışı bırakın.


****

IBM MQ İzleme (Trace) ve Javacore Toplama

1. IBM MQ İzleme (Trace) Kullanımı
IBM MQ izleme, sistemin yaptığı işlemleri detaylı bir şekilde kaydeder ve sorunları teşhis etmek için kullanılır. İzleme genellikle yalnızca IBM Destek ekibinin talebi üzerine etkinleştirilir, çünkü sistem performansını yavaşlatabilir ve dosya boyutları hızla büyüyebilir.

İzlemeyi Başlatma
	1. IBM MQ Explorer ile:
		○ IBM MQ Explorer'ı açın.
		○ Navigator Görünümü'nde IBM MQ'ya sağ tıklayın ve Trace... seçeneğine tıklayın.
		○ Açılan Trace Dialog penceresinde:
			§ All seçeneğiyle tüm izleme noktalarını etkinleştirin.
			§ Detail seçeneğiyle daha detaylı bir izleme düzeyini etkinleştirin.
		○ Start düğmesine tıklayın.
	2. Komut Satırı ile:
		○ Aşağıdaki komutu kullanarak bir kuyruk yöneticisi için izlemeyi başlatabilirsiniz:strmqtrc -e -m <KuyrukYöneticisiAdı>
			§ <KuyrukYöneticisiAdı> kısmına ilgili kuyruk yöneticisinin adını yazın.
		○ Tüm kuyruk yöneticileri için izleme başlatmak isterseniz:strmqtrc -e

İzlemeyi Durdurma
	1. IBM MQ Explorer ile:
		○ IBM MQ'ya sağ tıklayın ve Trace... seçeneğini seçin.
		○ Stop düğmesine tıklayın.
	2. Komut Satırı ile:
		○ İzlemeyi durdurmak için şu komutu kullanabilirsiniz:endmqtrc -e -m <KuyrukYöneticisiAdı>
		○ Tüm kuyruk yöneticileri için izlemeyi durdurmak isterseniz:endmqtrc -e

İzleme Dosyalarını Görüntüleme
	• İzleme dosyaları genellikle IBM MQ kurulum dizininde, trace alt klasöründe bulunur.
	• İzleme dosyalarının adları şu formattadır: AMQ123.TRC. Bu dosyalar, basit bir metin görüntüleyiciyle açılabilir.

2. IBM MQ Explorer İçin Javacore Toplama
Javacore, IBM MQ Explorer'ın dahili iş parçacıklarının durumunu analiz etmek için kullanılır ve genellikle IBM Destek ekibinin talebi üzerine toplanır.

Javacore Toplama Adımları
	1. Linux Sistemlerinde:
		○ IBM MQ Explorer'ı çalıştırmak için şu komutu kullanın:MQExplorer
		○ Explorer çalışırken, sürecin işlem kimliğini (PID) öğrenmek için şu komutu çalıştırın:ps -u `whoami` | grep MQExplorer | awk '{ print $1 }'
		○ Aşağıdaki komutla Javacore dosyasını oluşturun:kill -3 <MQExplorerPID>
	2. Windows Sistemlerinde:
		○ IBM MQ Explorer'ı şu komutla başlatın:MQExplorer -debug
		○ Komut satırı penceresinde odaklanın ve Ctrl + Break tuşlarına basarak Javacore oluşturun.

Javacore Dosyalarının Konumu
	• Linux: Genellikle kullanıcının ev dizininde oluşturulur (ör. /home/mquser/).
	• Windows: Kullanıcının ev dizininde oluşturulur (ör. C:\Users\MQUser\).
Javacore dosyalarının isimleri şu şekildedir: javacore.YYYYMMDD.HHmmss.PID.XXXX.txt.


****

IBM MQ Explorer İzleme (Trace) ve Kendi Eclipse Ortamında Çalıştırma
IBM MQ Explorer, başka bir Eclipse tabanlı ürün veya kendi Eclipse ortamınıza entegre edildiğinde, standart izleme komutları kullanılamaz. Bu durumda, özel bir runwithtrace komut varyantı kullanılarak izleme etkinleştirilebilir.

IBM MQ Explorer İzlemesini Kendi Eclipse Ortamında Etkinleştirme
1. Gerekli Eklentilerin Yüklenmesi
IBM MQ Explorer izleme mekanizması, AspectJ ve Equinox Weaving eklentilerinin yüklenmiş olmasını gerektirir. Bu eklentilerin yüklü olduğundan emin olun:
	1. Eklenti Kontrolü:
		○ Eclipse içinde Help > About... > Installation Details > Plug-ins sekmesine gidin.
		○ Şu eklentilerin yüklü olduğundan emin olun:
			§ org.aspectj.runtime
			§ org.aspectj.weaver
			§ org.eclipse.equinox.weaving.aspectj
			§ org.eclipse.equinox.weaving.caching
			§ org.eclipse.equinox.weaving.hook
	2. Eksikse Yükleme:
		○ Eclipse için doğru sürümden eklenti yüklemek için:
			§ Help > Install New Software... seçeneğine tıklayın.
			§ Gerekli indirme adresini ekleyin (ör. https://download.eclipse.org/tools/ajdt/44/dev/update).
			§ AspectJ Compiler ve Equinox Weaving SDK seçeneklerini işaretleyin ve yükleyin.

2. İzleme Komutunun Çalıştırılması
	• IBM MQ Explorer izleme, aşağıdaki adımlarla başlatılabilir:
		○ Windows için:
			§ Aşağıdaki komut dosyasını runwithtrace.cmd adıyla kaydedin ve aynı dizinde çalıştırın.
		○ Linux için:
			§ Komut dosyasını runwithtrace adıyla kaydedin ve çalıştırın.
Komut Dosyasını Çalıştırmak:
	• Komut dosyasını Eclipse’in çalıştırılabilir dosyasının bulunduğu dizinde çalıştırın.
	• İzleme dosyalarının yolu, komut çalıştırıldığında komut satırında görüntülenir.
Dosya İsim Formatı:
	• İzleme dosyaları şu formatta kaydedilir: AMQYYYYMMDDHHmmssmmm.TRC.n.

3. İzleme Tamamlandıktan Sonra Eklentilerin Kaldırılması
İzleme işlemi tamamlandıktan sonra, yüklenen AspectJ ve Equinox Weaving eklentilerini kaldırabilirsiniz:
	1. Help > About... > Installation Details > Installed Software sekmesine gidin.
	2. AspectJ Compiler ve Equinox Weaving SDK öğelerini seçin ve Uninstall... düğmesine tıklayın.

Windows ve Linux için Komut Dosyaları
	1. Windows için: runwithtrace.cmd dosyası, izleme başlatmak için yukarıda verilen açıklamaları içerir. Dosya, Eclipse çalıştırılabilir dosyasını izleme özellikleriyle başlatır.
	2. Linux için: runwithtrace dosyası benzer şekilde izleme başlatır. Dosya, /var/mqm/trace dizinini veya izinlere bağlı olarak /tmp dizinini kullanır.

Önemli Notlar
	• İzleme genellikle sadece IBM Destek tarafından talep edildiğinde etkinleştirilmelidir.
	• İzleme, sistem performansını yavaşlatabilir ve büyük boyutlu dosyalar oluşturabilir.
	• İzleme işlemini tamamladıktan sonra, gereksiz dosyaları ve eklentileri kaldırmanız önerilir.


****

IBM MQ Telemetry (MQTT) Kullanımı
IBM MQ Telemetry, MQTT protokolünü kullanarak IBM MQ mesaj sunucusunu çeşitli telemetri cihazları (ör. sensörler, aktüatörler, mobil cihazlar, akıllı sayaçlar, tıbbi cihazlar) ile bağlamayı destekler. MQTT, düşük bellek ve işlem kapasitesine sahip cihazlarda ve sınırlı bant genişliği gibi zorlu ağ koşullarında çalışabilir. Telemetry, enerji, sağlık, perakende gibi sektörlerde yaygın olarak kullanılır.

MQ Telemetry ile İlgili Temel Kavramlar
1. MQ Telemetry Nesneleri
	• Telemetry (MQXR) Hizmeti: IBM MQ'ya telemetri bağlantıları sağlamak için kullanılan TCP/IP dinleyici.
	• Telemetry Kanalları: MQTT istemcileri ile IBM MQ arasında iletişim sağlar.
	• Telemetry Kanal Durum Nesneleri: MQTT istemcilerinden gelen bilgileri toplayarak IBM MQ'ya iletir.
2. MQTT İstemci Yardımcı Programı
	• Amaç: MQTT özelliklerini keşfetmek, mesaj gönderip almak, telemetri kurulumunu test etmek.
	• Temel Kavramlar:
		○ Topic (Konu): Mesajların yayınlandığı anahtar.
		○ Quality of Service (QoS): Mesaj teslimi garantisinin seviyesi.
		○ Retained Mesajlar: Mesajın aboneye hemen iletilmesi için MQTT sunucusunda tutulması.
		○ Last Will and Testament: MQTT istemcisinin bağlantısının kesilmesi durumunda gönderilecek mesaj.
		○ Wildcard (Joker Karakterler):
			§ #: Çok seviyeli joker. (ör. ibm/qmgr/#)
			§ +: Tek seviyeli joker. (ör. ibm/qmgr/+)

MQ Telemetry Yapılandırması
1. IBM MQ Explorer ile Telemetry Yapılandırma
	• Telemetry kanal özelliklerini ve durumlarını ayarlayarak kurulum yapılabilir.
	• Adımlar:
		○ Yeni bir Telemetry Kanalı oluşturun.
		○ Örnek yapılandırma sihirbazını kullanarak temel bir Telemetry kurulumunu test edin.
2. MQXR Hizmetinin Yönetimi
	• Queue manager başlatıldığında MQXR servisi otomatik çalışır.
	• Hizmet elle de başlatılıp durdurulabilir.
3. Telemetry Kanalları
	• MQTT istemcilerini IBM MQ’ya bağlamak için kullanılır.
	• Kanal özelliklerini (örn. port numarası) ayarlayarak istemci bağlantıları yönetilir.

MQ Telemetry'nin Yönetimi
1. Durum İzleme
	• Telemetry kanalının durumu IBM MQ Explorer üzerinden izlenebilir.
	• MQTT istemcileri ve bunların bağlantıları görüntülenebilir.
2. Kanalların Başlatılması ve Durdurulması
	• Telemetry kanalları elle veya otomatik olarak başlatılabilir/durdurulabilir.
3. Filtreleme
	• Çok sayıda tanımlı Telemetry nesnesi varsa, filtreler kullanılarak belirli nesnelere odaklanılabilir.

MQ Telemetry Sorun Giderme
1. MQTT İstemci Bağlantı Sorunları
	• Bağlanamama: Yanlış port numarası veya sunucu adresi kontrol edilmeli.
	• Bağlantının Kesilmesi: MQXR hizmeti ve Telemetry kanalı durumu kontrol edilmeli.
2. Telemetry Kanal Sorunları
	• Kanal Başlamıyor: Port numarasının başka bir uygulama tarafından kullanılmadığından emin olun.
	• Kanal Beklenmedik Şekilde Duruyor: MQXR hizmetinin çalıştığından emin olun.
	• Kanal İstemci Bağlantılarını Düşürüyor: MQTT istemcilerinin doğru kanala bağlandığını kontrol edin.

MQ Telemetry ile Test ve Doğrulama
	• MQTT İstemci Yardımcı Programı: Mesajları yayınlamak ve abone olmak için kullanılır.
	• Örnek Yapılandırma: Sihirbaz yardımıyla temel ayarlar test edilir.

MQTT'nin Öne Çıkan Özellikleri
	1. Düşük Bant Genişliği Kullanımı: Zayıf ağlarda dahi iletişim sağlar.
	2. Esnek Konu Yönetimi: Hiyerarşik konu yapısı ve joker karakterlerle esnek abonelikler.
	3. Mesaj Kalite Seviyesi (QoS): Teslim garantisi seviyeleri sunar (QoS 0, 1, 2).
	4. Gerçek Zamanlı İzleme: MQTT istemcilerinin ve kanalların durumu izlenebilir.
IBM MQ Telemetry, MQTT protokolünü kullanarak IoT ve telemetri çözümleri için güçlü bir entegrasyon sunar.


***

IBM MQ Eğitim Rehberleri
IBM MQ için sunulan eğitim rehberleri, temel görevleri yerine getirmeyi öğrenmek için tasarlanmıştır. Bu rehberlerde, kuyruk yöneticisi oluşturma, kuyruk oluşturma, bir mesaja işlem yapma ve mesajları kuyruklar arasında gönderme gibi işlemler ele alınmaktadır. Bu eğitimler yalnızca Multiplatform ortamlar için geçerlidir ve IBM MQ Explorer grafik arayüzü veya MQSC (IBM MQ Script Commands) komut satırı arayüzü kullanılarak tamamlanabilir.
Her bir rehber, IBM MQ'yu anlamak için temel adımları kapsar ve daha karmaşık mesajlaşma senaryolarını içermez.

Eğitim Rehberlerinin Genel Özeti
1. Eğitim: Mesajı Yerel Kuyruğa Gönderme
Bu eğitimde şunları yapmayı öğreneceksiniz:
	• Kuyruk yöneticisi (Queue Manager) oluşturma: "QM_APPLE" adında bir kuyruk yöneticisi.
	• Yerel kuyruk (Queue) oluşturma: "Q1" adında bir kuyruk.
	• Mesaj gönderme: "Q1" kuyruğuna bir test mesajı gönderme.
	• Mesajın alındığını doğrulama: Mesajın kuyruğa başarıyla eklendiğinden emin olun.
2. Eğitim: Mesajı Uzak Kuyruğa Gönderme
Birden fazla kuyruk yöneticisi arasında mesaj gönderme işlemlerini öğrenirsiniz:
	• Gönderici kuyruk yöneticisi: "QM_ORANGE".
	• Alıcı kuyruk yöneticisi: "QM_APPLE".
	• Mesaj kanalı oluşturma: İki kuyruk yöneticisi arasında iletişim kurmak için bir kanal tanımlama.
	• Test mesajı gönderme: Mesajın uzak kuyruk üzerinden başarıyla ulaştığını doğrulama.
3. Eğitim: İstemci-Sunucu Yapılandırmasında Mesaj Gönderme
Bu eğitimde istemci ve sunucu makineleri arasında mesajlaşmayı öğrenirsiniz:
	• Sunucu Yapılandırması: "QM_ORANGE" kuyruk yöneticisinde bir sunucu-bağlantı kanalı tanımlayın.
	• İstemci Yapılandırması: "MQSERVER" ortam değişkeni ile istemciyi yapılandırın.
	• Mesaj Gönderme: İstemciden "QM_ORANGE" yöneticisine bir mesaj gönderin; mesaj "QM_APPLE" kuyruğuna iletilir.
	• Doğrulama: Mesajın başarılı bir şekilde gönderilip gönderilmediğini kontrol edin.

1. Eğitim: Mesajı Yerel Kuyruğa Gönderme
Adımlar
	1. Kuyruk Yöneticisi Oluşturma:
		○ IBM MQ Explorer veya MQSC komutlarını kullanarak "QM_APPLE" adında bir kuyruk yöneticisi oluşturun.
	2. Yerel Kuyruk Oluşturma:
		○ "Q1" adlı bir yerel kuyruk oluşturun.
	3. Mesaj Gönderme:
		○ IBM MQ Explorer veya amqsput programını kullanarak test mesajını kuyruğa ekleyin.
	4. Mesaj Doğrulama:
		○ IBM MQ Explorer veya amqsget programı ile mesajın kuyruğa ulaştığını doğrulayın.

2. Eğitim: Mesajı Uzak Kuyruğa Gönderme
Adımlar
	1. Gönderici Kuyruk Yöneticisi Oluşturma:
		○ IBM MQ Explorer veya MQSC ile "QM_ORANGE" yöneticisini oluşturun.
	2. Kuyrukları Tanımlama:
		○ Gönderici yöneticide bir uzak kuyruk tanımı ve iletim kuyruğu oluşturun.
	3. Mesaj Kanalı Oluşturma:
		○ "QM_ORANGE" ve "QM_APPLE" arasında bir mesaj kanalı tanımlayın.
	4. Mesaj Gönderme:
		○ "QM_ORANGE" üzerinden bir test mesajı gönderin.
	5. Doğrulama:
		○ Mesajın "Q1" kuyruğuna başarıyla ulaştığını kontrol edin.

3. Eğitim: İstemci-Sunucu Yapılandırmasında Mesaj Gönderme
Adımlar
	1. Sunucuyu Yapılandırma:
		○ "QM_ORANGE" yöneticisi üzerinde bir sunucu-bağlantı kanalı oluşturun.
	2. İstemciyi Yapılandırma:
		○ İstemci makinede "MQSERVER" ortam değişkenini yapılandırın.
	3. Mesaj Gönderme:
		○ İstemciden "QM_ORANGE" yöneticisine bir mesaj gönderin; bu mesaj "Q1" kuyruğuna iletilir.
	4. Mesaj Doğrulama:
		○ Mesajın hedef kuyruğa ulaştığını kontrol edin.


****

IBM MQ Explorer Referans Rehberi
IBM MQ Explorer kullanımı için hazırlanmış olan bu rehber, erişilebilirlik, ikonlar, görünümler, tercih ayarları ve nesne özellikleri gibi konuları kapsamaktadır. IBM MQ Explorer, IBM MQ nesnelerini yönetmek ve izlemek için bir grafik arayüz sunar.

Ana Başlıklar
	1. Erişilebilirlik (Accessibility):
		○ Fiziksel engelli kullanıcıların IBM MQ Explorer'ı daha verimli kullanmasını sağlamak için çeşitli erişilebilirlik özellikleri mevcuttur.
		○ Renkler değiştirilebilir, nesne ikonları yerine metin açıklamaları gösterilebilir.
		○ Klavye kısayolları ve ekran okuyucu desteği sunulur.
	2. İkonlar (Icons):
		○ IBM MQ Explorer, farklı nesneleri temsil etmek için ikonlar kullanır.
		○ İkonlar, nesnelerin durumunu (çalışıyor, durmuş, uyarı veya hata) belirtmek için değiştirilir.
		○ Yerel ve uzak kuyruk yöneticileri, kuyruklar, kanallar ve diğer nesneler için ikonlar farklıdır.
	3. Görünümler (Views):
		○ IBM MQ Explorer, Eclipse platformuna dayalı bir perspektif sağlar.
		○ Navigator View: Kuyruk yöneticileri ve diğer nesneler hiyerarşik bir yapıda gösterilir.
		○ Content View: Seçilen nesnelerin detaylı özellikleri ve durum bilgileri görüntülenir.
	4. Tercihler (Preferences):
		○ IBM MQ Explorer'ın arayüzü, kullanıcı ihtiyaçlarına göre özelleştirilebilir.
		○ Renkler, sütun sıralamaları, yenileme sıklığı gibi ayarlar değiştirilebilir.
		○ TLS sertifikaları, güvenlik ayarları ve istemci bağlantıları için varsayılan değerler ayarlanabilir.
	5. Özellikler (Properties):
		○ IBM MQ nesnelerinin özellikleri düzenlenebilir veya görüntülenebilir.
		○ Kuyruk yöneticileri, kuyruklar, kanallar ve dinleyiciler gibi nesnelerin farklı özellik setleri bulunmaktadır.
		○ Özellikler, IBM MQ SC komutları ve API çağrıları ile eşleştirilebilir.
	6. Durum Nitelikleri (Status Attributes):
		○ Kuyruk yöneticileri, kuyruklar, konular ve kanallar gibi nesnelerin mevcut durum bilgileri görüntülenebilir.
		○ Örneğin, bir kanalın çalışıp çalışmadığı veya bir kuyruğa en son ne zaman mesaj gönderildiği öğrenilebilir.
	7. Bayt Dizisi Diyaloğu (Byte Array Dialog):
		○ IBM MQ nesnelerinin bayt dizisi özelliklerini tanımlamak veya düzenlemek için kullanılır.
		○ Örneğin, bir abonelik nesnesi için Correl ID (24 bayt) veya Accounting Token (32 bayt) tanımlanabilir.

Detaylı Açıklamalar
1. Erişilebilirlik
	• Metinle Durum Gösterimi: Nesne durumlarını ekran okuyucularla uyumlu hale getirmek için ikon yerine metin gösterebilirsiniz.
	• Renk Değiştirme: Varsayılan renkleri değiştirebilirsiniz. Bu, görme zorluğu çeken kullanıcılar için faydalıdır.
	• İzin Ayarları: Yönetim izinlerini ikon yerine metinle gösterebilirsiniz.
2. İkonlar
	• Durum İkonları:
		○ Çalışıyor: Nesne aktif durumda.
		○ Durmuş: Nesne pasif.
		○ Uyarı: Nesne bağlantı sorunları yaşıyor.
		○ Hata: Nesneye erişim mümkün değil.
	• Kuyruk Yöneticisi İkonları:
		○ Yerel yöneticiler sarı, uzak yöneticiler gri tonlarında gösterilir.
		○ Bağlantı durumu ikonlarla belirtilir (bağlı, bağlantısız).
	• Kuyruk İkonları:
		○ Yerel Kuyruk: Lokal olarak tanımlı bir kuyruk.
		○ Model Kuyruk: Kuyruk şablonu.
		○ İletim Kuyruğu: Mesajların iletildiği kuyruk.
3. Görünümler
	• Navigator View: IBM MQ nesneleri hiyerarşik olarak görüntülenir.
		○ Kuyruk yöneticileri, kuyruklar, kanallar gibi nesneler bir klasör yapısında düzenlenir.
		○ Her klasör, içerdiği nesnelerle ilgili işlemler için sağ tıklama menüsü sunar.
	• Content View:
		○ Seçilen nesnelerin detaylı özellikleri listelenir.
		○ Özelleştirme seçenekleriyle görünüm daha kullanıcı dostu hale getirilebilir.
4. Tercihler
	• Görsel Özelleştirme:
		○ Tablo sütun sıralamaları değiştirilebilir.
		○ Arayüz yenileme sıklığı ayarlanabilir.
	• Güvenlik Ayarları:
		○ TLS sertifika deposu varsayılan konumları ayarlanabilir.
		○ İstemci bağlantıları için varsayılan değerler belirlenebilir.
5. Özellikler
	• Genel Özellikler:
		○ Varsayılan kuyruk yöneticisi adı ve veri yolu gibi genel ayarlar düzenlenebilir.
	• Kanal Özellikleri:
		○ Kanal türüne göre (alıcı, gönderici vb.) farklı özellikler ayarlanabilir.
	• Kuyruk Özellikleri:
		○ Kuyruğun tipi (model, uzak, yerel) özellik setini belirler.
6. Durum Nitelikleri
	• Kuyruk Yöneticisi Durumu:
		○ Kuyruk yöneticisinin aktif mi pasif mi olduğu bilgisi alınabilir.
	• Kuyruk Durumu:
		○ Kuyruğa en son ne zaman mesaj gönderildiği görülebilir.
	• Kanal Durumu:
		○ Kanalın mevcut ve kaydedilmiş durum bilgileri incelenebilir.
7. Bayt Dizisi Diyaloğu
	• Metin veya Bayt Girişi:
		○ Bayt dizileri metin veya ham bayt olarak düzenlenebilir.


****
IBM MQ Explorer'ı Genişletme Yolları
	1. Mevcut Menü Seçeneklerini Genişletmek:
		○ Var olan menülere yeni seçenekler ekleyebilir ve bu seçeneklere özel işlemler atayabilirsiniz.
	2. Ağaç Düğümleri Eklemek:
		○ Gezinti görünümüne yeni ağaç düğümleri ekleyebilir ve bunlara içerik sayfaları bağlayabilirsiniz.
	3. Özellik Sekmeleri Eklemek:
		○ Özellik diyaloglarına yeni sekmeler ve sayfalar ekleyerek özelleştirme yapabilirsiniz.

Eklenti Yazımı İçin Gerekenler
	1. plugin.xml Dosyası:
		○ Eklentinizin işlevselliğini tanımlayan genişletme noktalarını belirtir.
		○ IBM MQ Explorer ve Eclipse, genişletme noktaları için farklı türler sunar.
		○ Daha fazla bilgi için Eclipse Yardımı: Eclipse Extension Points.
	2. Java Archive (JAR) Dosyaları:
		○ Genişletme noktalarını destekleyen sınıfları içeren JAR dosyaları oluşturmanız gereklidir.
	3. Örnek Eklentiler:
		○ IBM MQ, "simple" ve "menu" adlı örnek eklentiler sunar. Bu eklentiler, IBM MQ Explorer genişletme noktalarını anlamanız için bir temel oluşturabilir.

Örnek Eklentileri İçe Aktarma
IBM MQ Explorer için örnek Eclipse eklentilerini içe aktarmak için şu adımları takip edin:
	1. IBM MQ Explorer’ı bir Eclipse ortamına kurun.
	2. Plug-in Development perspektifini açın.
	3. File > Import seçeneğine tıklayın ve aşağıdaki adımları tamamlayın:
		○ Plug-in Development > Plug-ins and Fragments yolunu izleyin.
		○ "Projects with source folders" seçeneğini işaretleyin ve devam edin.
		○ Şu projelerden bir veya daha fazlasını seçin:
			§ com.ibm.mq.explorer.sample.simple
			§ com.ibm.mq.explorer.sample.menus
	4. İçe aktarma işlemini tamamladıktan sonra projeler hazır olacaktır.

IBM MQ Explorer İçin Eclipse Eklentisi Yazma
	1. Genişletme Noktalarını Kullanma:
		○ Genişletme noktaları, IBM MQ Explorer'ın işlevselliğini artırmak için kullanılır. Örneğin:
			§ Yeni menü seçenekleri ekleme.
			§ Gezinti görünümüne yeni ağaç düğümleri ekleme.
			§ İçerik sayfaları oluşturma.
	2. Register Extension Point:
		○ Her eklenti, IBM MQ Explorer ile entegre olmak için bir "register" genişletme noktası kullanmalıdır.
	3. Kodlama ve Test Etme:
		○ Genişletme noktalarını destekleyen Java sınıfları oluşturun ve test edin.

Eklentileri Uygulama
	1. Eclipse Workbench’te Çalıştırma:
		○ Run > Run As > Eclipse Application seçeneğini kullanarak eklentinizi test edebilirsiniz.
	2. Kalıcı Uygulama:
		○ Eklenti dosyasını IBM MQ Explorer kurulum dizinindeki eclipse\dropins klasörüne kopyalayın.
		○ IBM MQ Explorer’ı yeniden başlatarak güncellemeleri uygulayın.

API Referansı ve Ek Kaynaklar
IBM MQ Explorer API dökümantasyonuna erişmek için:
	1. IBM MQ Explorer'ı başlatın.
	2. Ürün yardımı dokümantasyonunda "API Reference" konusunu açın.
Daha fazla bilgi için Eclipse Platform Plug-in Developers Guide kaynağını inceleyebilirsiniz.
Bu rehber ile IBM MQ Explorer'ı genişleterek daha işlevsel ve özelleştirilmiş bir yönetim aracı oluşturabilirsiniz.
