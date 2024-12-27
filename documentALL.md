• IBM MQ for Multiplatforms ve IBM MQ for z/OS: IBM MQ'nun çeşitli platformlar ve z/OS için uyumlu sürümleri hakkında belgeler sunuyor.
• IBM MQ Explorer: IBM MQ'yu görsel bir arayüzle yönetmeye olanak tanır. Windows ve Linux sistemlerinde çalışabilir.
• IBM MQ in Containers ve IBM Cloud Pak for Integration: IBM MQ'nun konteyner ortamlarında ve bulut tabanlı çözümlerle entegrasyonu için belgeler.
• IBM MQ on Cloud: IBM MQ'nun bulut ortamlarında yönetilen bir hizmet olarak kullanımı.
• IBM MQ Appliance: IBM MQ'yu donanım olarak sağlayan bir çözüm.

IBM MQ Nedir?
IBM MQ, uygulamalar, sistemler, servisler ve dosyalar arasında bilgi alışverişini destekleyen bir yazılımdır. Mesajlaşma kuyrukları aracılığıyla veri gönderir ve alır. Bu, iş uygulamalarının oluşturulması ve bakımını basitleştirir. IBM MQ, yerel, bulut ve hibrit bulut ortamlarında çalışabilir. Aynı zamanda, Message Queue Interface (MQI), JMS, REST, .NET, AMQP ve MQTT gibi çeşitli API'leri destekler.
IBM MQ'nun sağladığı başlıca özellikler şunlardır:
	• Çok yönlü mesajlaşma entegrasyonu: Ana bilgisayardan mobil cihazlara kadar geniş bir uygulama yelpazesinde, dinamik ve heterojen ortamlarda güçlü bir mesajlaşma altyapısı sağlar.
	• Mesaj teslimi: Mesajların güvenlik özellikleriyle teslim edilmesini sağlar ve bu, uygulama veya sistem arızalarına karşı dayanıklıdır.
	• Yüksek performans: Verilerin hızlı ve güvenilir bir şekilde iletilmesini sağlar.
	• Yüksek erişilebilirlik ve ölçeklenebilirlik: Uygulamanın ihtiyaçlarına göre ölçeklenebilir altyapılar sağlar.
	• Yönetimsel kolaylıklar: Mesajlaşma yönetimini basitleştirir ve karmaşık araçları azaltır.
	• Açık standartlar: Geliştiricilere, iş gereksinimlerine uygun çözümler geliştirebilme imkanı sunar.
Mesajlaşma ve Kuyruklama Modelleri:
	• Mesajlaşma (Messaging): Uygulamalar, verilerini mesajlar şeklinde birbirlerine gönderir ve bu mesajlar doğrudan diğer uygulamalara yönlendirilir.
	• Kuyruklama (Queuing): Mesajlar kuyruklara yerleştirilir ve bu kuyruklar üzerinden farklı uygulamalara iletilir. Mesajlar sırayla işlenir.
		○ Point-to-Point: Bir mesaj, yalnızca bir alıcıya teslim edilir. Gönderici mesajı bir kuyruğa yerleştirir, bu kuyruğa yalnızca bir alıcı erişebilir.
		○ Publish/Subscribe: Bir mesaj, birden fazla alıcıya gönderilebilir. Gönderici, mesajı bir kuyruğa yerleştirir ve alıcılar bu mesaja abone olarak alırlar.

Mesaj Kuyruklamanın Temel Özellikleri ve Faydaları
	• Programlar Arasında Doğrudan Bağlantı Olmaz:
Mesaj kuyruklama, programlar arası dolaylı bir iletişim tekniğidir. Bir program mesajı bir kuyruğa gönderir, başka bir program bu kuyruğu alır ve mesajı işler. Bu şekilde, programlar fiziksel olarak birbirine bağlı değildir. Mesajlar bir kuyruğa yerleştirilir ve bu kuyruktan alınır.
	• Zaman Bağımsız İletişim:
Mesajlar, gönderildikten sonra alıcı tarafından istenilen zaman diliminde alınabilir. Bu, bir programın mesaj gönderirken alıcının yanıtını beklemesine gerek olmadığı anlamına gelir. Gönderen program, mesajı gönderdikten sonra işlemine devam edebilir.
	• Küçük Programlar:
Mesaj kuyruklama, büyük programlar yerine küçük, bağımsız çalışabilen programların kullanılmasını sağlar. Bu, programların daha esnek olmasını ve birbirlerinden bağımsız olarak çalışabilmesini sağlar.
	• Mesaj Tetiklemesi:
Kuyruğa gelen mesajlar, ilgili uygulamaları tetikleyebilir. Bu sayede, uygulamalar kuyruğa mesaj geldiğinde otomatik olarak başlatılabilir.
	• Olay Tabanlı İşlem:
Programlar, kuyruğun durumu üzerinden kontrol edilebilir. Örneğin, kuyruğa belirli bir sayıda mesaj geldiğinde bir program başlatılabilir.
	• Mesaj Önceliği:
Gönderici, mesajlara öncelik atayabilir. Bu, kuyruğa gelen yeni mesajların hangi sırayla işleneceğini belirler.
	• Güvenlik:
Mesajların güvenliği sağlanır. Kuyruk yöneticisi, mesajın yolculuğu ve kuyruğa yerleştirilmesi sırasında mesajın şifrelenmesini sağlar.
	• Veri Bütünlüğü:
Mesajların taşınması sırasında veri bütünlüğü sağlanır. İşlem birimlerindeki başlangıç ve bitiş noktaları arasında senkronizasyon sağlanarak, veri kaybı önlenir.
	• Kurtarma Desteği:
Sistem çökmesi durumunda, tüm kalıcı mesajlar geri yüklenir. Mesajlar, işlemler sırasında güvenli bir şekilde işlenir ve sistem yeniden başlatıldığında kaldığı yerden devam edebilir.
Mesaj Kuyruklama vs. Geleneksel İletişim
Geleneksel iletişimde, bir program A, B programına doğrudan bağlanarak mesaj gönderir. Ancak mesaj kuyruklamada, A programı mesajı bir kuyruğa gönderir ve B programı bu kuyruğu dinler. Bu sayede, programlar arasındaki doğrudan bağlantı ortadan kalkar.
Bu özellikler, uygulamaların daha esnek ve bağımsız çalışmasını sağlar


IBM MQ Terminolojisi
	1. Channel (Kanal):
Kanal, bir kuyruk yöneticisinden diğerine mesajları taşıyan iletişim yoludur. Kanallar, mesajları taşıyan uygulamalardan, kullanılan iletişim protokollerinden ve mesajların geldiği yerden bağımsız olarak çalışır. Kanal, uygulamalar arasında mesaj iletimini sağlar.
	2. Cluster (Küme):
Küme, birbiriyle mantıksal olarak ilişkili olan kuyruk yöneticilerinin ağını ifade eder. Küme kullanımı, uygulamaların iletişimde olduğu kuyruk yöneticilerini daha verimli hale getirir ve yük dengelemesi sağlar.
	3. Message (Mesaj):
Mesaj, bir program tarafından diğerine gönderilen veri koleksiyonudur. Mesajlar, genellikle belirli bir formatta iletilir.
	4. Message Channel Agent (Mesaj Kanal Ajanı):
Mesaj kanal ajanı, bir kanalın bir ucunda bulunan bileşendir. Bir kanal, iki mesaj kanal ajanı tarafından yönetilir: bir gönderici ajanı ve bir alıcı ajanı. Bu ajanlar, mesajları bir kuyruk yöneticisinden diğerine taşır.
	5. Queue (Kuyruk):
Kuyruk, mesajların gönderildiği ve depolandığı hedef yerdir. Mesajlar kuyruklarda birikir ve daha sonra bu kuyrukları işleyen programlar tarafından alınır.
	6. Queue Manager (Kuyruk Yöneticisi):
Kuyruk yöneticisi, uygulamalara kuyruklama hizmeti sunan bir sistem programıdır. Kuyruk yöneticisi, kuyruklarla ilgili işlemleri yönetir, yeni kuyruklar oluşturabilir, mevcut kuyrukları değiştirebilir.
	7. Queue Sharing Group (Kuyruk Paylaşım Grubu):
Kuyruk paylaşım grubu, birden fazla kuyruk yöneticisinin aynı kuyrukları paylaşmasını sağlar. Bu özellik, IBM MQ for z/OS için geçerlidir.
	8. Publish/Subscribe Messaging (Yayınla/Abone Ol Mesajlaşması):
Yayınla/Abone ol modeli, bir yayıncı tarafından yayınlanan mesajların tüm ilgilenen alıcılara (abone olanlara) iletilmesini sağlar. Burada, alıcılar belirli konulara abone olur ve ilgili mesajlar kuyruklarda birikir.
	9. Point-to-Point Messaging (Noktadan Noktaya Mesajlaşma):
Noktadan noktaya mesajlaşmada, bir mesaj, yalnızca bir alıcıya iletilir. Gönderen program, mesajı bir kuyruğa yerleştirir ve tüketici programı bu mesajı alır.
	10. Topic (Konu):
Konu, bir mesajın içerdiği bilginin başlığıdır. Yayınla/Abone ol sisteminde, her mesaj bir konuya atanır ve kuyruk yöneticisi bu konuyu takip eden abonelere mesajı iletir.

Mesaj Nedir?
Bir mesaj, bir programdan diğerine (veya aynı programın farklı bölümleri arasında) bilgi taşıyan bir dizi bayttır. Mesaj, gönderen uygulama tarafından oluşturulur ve alıcı uygulama tarafından işlenir.
	• Mesaj Yapısı:
		1. Uygulama Verisi: Uygulamalar mesaj verisinin içeriğini belirler.
		2. Mesaj Tanımlayıcısı (Message Descriptor): Mesajın tipini, önceliğini ve diğer kontrol bilgilerini içerir.
		3. Mesaj Özellikleri (Message Properties): Uygulamalar tarafından belirlenen meta veriler içerir.
Mesaj Uzunlukları
	• Varsayılan maksimum mesaj uzunluğu 4 MB'dir, ancak bu uzunluk 100 MB'ye kadar arttırılabilir. Uygulama tarafından gönderilen her mesaj belirli bir uzunluk sınırına tabi olabilir.
Kuyruk Nedir?
Bir kuyruk, mesajların depolandığı bir veri yapısıdır. Her kuyruk bir kuyruk yöneticisi tarafından yönetilir.
	• Kuyruk Türleri:
		○ Önceden Tanımlı Kuyruklar (Predefined Queues): Yönetici tarafından MQSC veya PCF komutlarıyla oluşturulur. Bu kuyruklar kalıcıdır ve IBM MQ yeniden başlatılsa bile varlıklarını sürdürür.
		○ Dinamik Kuyruklar (Dynamic Queues): Uygulama tarafından belirli bir model kuyruk adı ile oluşturulur. Bu kuyruklar, uygulama çalışırken tanımlanır ve genellikle geçicidir.
Kuyruklardan Mesaj Alma
Uygun yetkilendirilmiş uygulamalar kuyruktan mesajları şu yöntemlerle alabilir:
	• İlk Gelen İlk Çıkar (FIFO): Kuyruğa ilk eklenen mesaj ilk alınır.
	• Mesaj Önceliği: Mesaj önceliklerine göre sıralama yapılabilir.
	• Belirli Bir Program İçin Mesaj: Belirli bir programın aldığı mesajlar.
MQI İle Mesaj Gönderme ve Alma
Uygulamalar, MQI çağrıları (MQOPEN, MQPUT, MQGET) kullanarak mesajları kuyruklara gönderir ve alır. Bu yöntem, uygulamaların birbirleriyle bağımsız olarak iletişim kurmasını sağlar.


IBM MQ Lisans Bilgileri
	• IBM MQ'yu Neler Alabilirsiniz?
IBM MQ'nun çeşitli sürümleri ve bileşenleri, farklı lisans türleriyle sunulmaktadır. Örneğin, IBM MQ'nun "Advanced" sürümü veya "High Availability Replica" gibi özelliklere sahip versiyonları bağımsız olarak satın alınabilir. Lisanslama seçenekleri, yalnızca kurulum yapılacak ortamın ihtiyaçlarına göre belirlenmelidir.
	• Lisans Satın Alma
IBM MQ lisansları, AWS Marketplace veya Azure Marketplace gibi platformlar üzerinden temin edilebilir. Aynı zamanda Passport Advantage üzerinden de IBM MQ'nun lisansları alınabilir.
	• IBM MQ için Lisans Özellikleri
Özel lisans türleri ve sunuculara bağlanan istemciler için olan "unlimited installs" gibi seçenekler mevcuttur. Lisanslar, kurulum ortamına ve ürün özelliklerine göre değişebilir.
Ürün Özellikleri ve Lisans Hakları
	• IBM MQ'nun farklı bileşenleri için lisans hakları tanımlanmış ve bu bileşenler için hangi ürünün hangi özellikleri içerdiği belirtilmiştir. Örneğin:
		○ IBM MQ Advanced: Mesaj güvenliği, dosya transferi hizmetleri gibi ekstra özellikler sunar.
		○ IBM MQ Managed File Transfer: Dosya transferi ile ilgili yönetilen bileşenler sunar.
	• Lisans hakları, IBM MQ'nun bazı özelliklerine (örneğin, dosya transferi, mesaj güvenliği) belirli bileşenler için "unlimited installs" hakları sağlar.
	• High Availability Replica (Yüksek Erişilebilirlik Yedekleme) gibi özel özellikler de belirli lisans paketlerine dahil edilebilir.
High Availability Replica Özellikleri
	• Yüksek Erişilebilirlik (HA) özellikleri, çoklu sunucu kurulumlarıyla sağlanabilir. Bu özellik, sistemde bir arıza meydana geldiğinde yedek sistemlerin devreye girmesini sağlar.
	• Bu özellik, IBM MQ Advanced lisansına sahip sistemlerde kullanılabilir.
IBM MQ'yu Nasıl Konfigüre Edebilirim?
	• Non-Production Environment (Üretim Dışı Ortam): IBM MQ Advanced for Non-Production Environment, geliştirme ve test ortamlarında kullanılmak üzere sunulmaktadır.
	• Lisans Kısıtlamaları: IBM MQ'nun bazı özellikleri, yalnızca özel lisanslara sahip kullanıcılar tarafından kullanılabilir ve bazı bileşenlerin ayrı olarak lisanslanması gerekebilir.

Dağıtılabilir Bileşenler
IBM MQ, üçüncü taraf uygulamalarıyla birlikte yeniden dağıtılabilen bileşenler sunar. Bu bileşenler, belirli lisans koşulları altında kullanılabilir ve dağıtılabilir. Dağıtılabilir bileşenler, aşağıdaki IBM MQ programlarıyla lisanslanabilir:
	• IBM MQ
	• IBM MQ Advanced
	• IBM MQ Appliance M2001, M2002 ve M2003
	• IBM MQ for z/OS®
	• IBM MQ Advanced for z/OS Value Unit Edition
Bu bileşenler, IBM MQ Client bileşenleri dahil olmak üzere üretim ortamlarında kullanılabilir ve lisansın belirlediği sistem gereksinimlerine sahip olmalıdır.
Dağıtılabilir Bileşenler:
	1. IBM MQ Client Bileşenleri:
		○ IBM MQ Client bileşenleri, IBM Fix Central veya NuGet gibi kaynaklardan indirilebilir.
		○ Java, .NET, C/C++ gibi farklı platformlarda kullanılabilecek istemci bileşenleri mevcuttur.
	2. IBM MQ Managed File Transfer Agent:
		○ IBM MQ Advanced ve IBM MQ Appliance ile birlikte dağıtılabilir.
		○ File transfer işlemleri için kullanılan bu bileşen, IBM Fix Central üzerinden indirilebilir.
	3. IBM MQ for z/OS Stub Routines:
		○ Z/OS üzerinde çalışacak olan IBM MQ için stub rutini bileşenleri de dağıtılabilir.
		○ Bu bileşenler, z/OS ortamındaki geliştirme ve derleme süreçlerinde kullanılmak üzere çeşitli dosya setlerinde mevcuttur.
Lisans Gereksinimleri ve Dağıtım
Dağıtılabilir bileşenlerin kullanılabilmesi için bağlanılan IBM MQ Queue Manager'ın doğru şekilde lisanslanmış olması gerekmektedir. Yani, uygulamanız, bağlantı kurduğu kuyruk yöneticisinin sahip olduğu lisansla uyumlu olmalıdır.
Lisanslama Koşulları
Bu bileşenlerin, yalnızca belirli programların lisanslarına sahip bir kuyruk yöneticisiyle bağlantı kurması durumunda dağıtılabileceği belirtilmiştir. Bu lisanslar, IBM'in belirlediği şartlarla uyumlu olmalıdır.

IBM MQ Sürüm Türleri
IBM MQ'nun iki ana sürüm türü bulunmaktadır:
	1. Long Term Support (LTS):
LTS sürümleri, uzun süreli destek ve istikrar gereksinimlerini karşılamak için tasarlanmıştır. Bu sürümler genellikle daha az sıklıkla güncellenir, ancak daha uzun süre desteklenir ve uzun vadeli dağıtımlar için uygundur.
	2. Continuous Delivery (CD):
CD sürümleri, IBM MQ'nun yeni özelliklerini hızlı bir şekilde sunmaya odaklanır. Bu sürümler, sık aralıklarla güncellenir ve yeni işlevsellik ekler.
LTS ve CD Sürümleri Arasındaki Farklar
	• LTS sürümleri her zaman sıfır bir modifikasyon numarasına sahiptir (örneğin, 9.3.0 ve 9.4.0).
	• CD sürümleri genellikle sıfır olmayan bir modifikasyon numarasına sahiptir (örneğin, 9.4.1, 9.4.2, vb.).
Sürüm Desteği
	• LTS sürümleri, sürümün süresi boyunca desteklenir.
	• CD sürümleri, genellikle 12 ay boyunca desteklenir veya en son iki CD sürümünden biri olduktan sonra desteklenir.
Bakım Teslimat Modeli
	• Fix Pack'ler: LTS sürümleri için güvenlik ve fonksiyonel düzeltmeleri içerir.
	• Cumulative Security Updates (CSU): Hem LTS hem de CD sürümleri için güvenlik düzeltmeleri sağlar.
	• Her iki bakım türü de birikimli olup, daha önceki fix pack veya CSU'ları içerir.
Sürüm Seçimi ve Platform Farklılıkları
	• Multiplatformlar (UNIX, Linux, Windows, IBM i): LTS fix pack'ler ve CSU'lar, interim fix olarak indirilebilir ve yeni kurulumlar veya mevcut kurulumların güncellenmesi için kullanılabilir.
	• z/OS: LTS fix pack'ler ve CSU'lar, Program Temporary Fix (PTF) numarası ile indirilebilir. CD CSU'lar genellikle bir sonraki CD sürümüyle birlikte gelir, ancak talep üzerine ayrı olarak da sağlanabilir.
IBM MQ Advanced Container ve CP4I-SC2 (Cloud Pak for Integration)
	• IBM MQ Advanced Container, IBM MQ Continuous Delivery sürümüne dayanmaktadır, ancak IBM Cloud Pak for Integration içinde kullanıldığında CP4I-SC2 (Support Cycle 2) sürümü olarak desteklenir. Bu sürüm, 2 yıl boyunca destek alır ve isteğe bağlı olarak 1 yıl daha uzatılabilir.
Sürüm Kontrolü
IBM MQ sürümünü kontrol etmek için şu yöntemler kullanılabilir:
	• dspmqver komutu veya DSPMQMVER komutu (IBM i üzerinde).
	• REST API GET metodu.
	• IBM MQ Explorer üzerinden sürüm bilgileri görüntülenebilir.


Sanal İşlemci Çekirdekleri (VPC)
	• VPC Nedir?
VPC, IBM MQ'nun lisanslanmasında kullanılan bir birimdir. Bir VPC, ya sanal bir makineye atanan sanal bir çekirdek ya da sanal makineler için ayrılmamış bir fiziksel işlemci çekirdeği olabilir. Eğer sanal çekirdek sayısı fiziksel çekirdek sayısını aşarsa, lisanslanması gereken VPC sayısı fiziksel çekirdek sayısına eşit olacaktır.
	• VPC Kullanımı
VPC'lerin kullanımı, Sanal İşlemci Çekirdek-Örnek-Saatleri (VPC Instance-Hours) cinsinden ölçülür ve bu ölçüm dakika başına yapılır. Bir "örnek" (Instance), IBM MQ'nun çalışan bir kopyasını ifade eder ve yedekleme amacıyla kullanılan kopyalar (soğuk veya sıcak yedeklemeler) dahil edilmez.
	• Lisans Gereksinimleri
IBM MQ'nun her örneği için, her VPC'nin sağlanabileceği toplam saat sayısına göre yeterli lisans hakkı alınmalıdır. Yani, her yıl için VPC başına toplam 720 saatlik lisans alınması gereklidir, her bir VPC'nin ne zaman kullanıldığına bakılmaksızın.
	• Ölçüm Aracı Kullanımı
IBM, programın kullanımını izlemek için bir ölçüm aracı sağlar. Bu aracın kullanılmaması durumunda, her VPC için ayda 720 saatlik bir kullanım için lisans almak gerekir.


IBM MQ 9.4.0 sürümü, IBM MQ 9.3.0'dan sonra gelen Long Term Support (LTS) sürümüdür ve aynı zamanda IBM MQ 9.3.5'in devamı olarak Continuous Delivery (CD) sürümüdür. Bu sürüm, önceki CD sürümlerinde yer alan özelliklerin yanı sıra yeni özellikler ve iyileştirmeler de içermektedir. İşte IBM MQ 9.4.0'daki yenilikler ve değişikliklerin ana hatları:
Yeni Özellikler ve İyileştirmeler
Multiplatforms - Base ve Advanced Entitlement
	• Yükleme ve Göç: Windows ve Linux üzerinde bakım uygulama için yeni bir yöntem eklenmiştir.
	• Güvenlik:
		○ JWT (JSON Web Token) desteği ve token tabanlı kimlik doğrulama.
		○ MQCSP şifre korumasındaki değişiklikler.
		○ TLS 1.3 desteği, yönetilen .NET istemcileri için sağlanmıştır.
	• Yönetim:
		○ IBM MQ Console'a yeni iyileştirmeler yapılmıştır.
		○ Dışa aktarma işlevselliği ve yeni bir "CAPEXPRY" özelliği eklenmiştir.
		○ OpenTelemetry izleme desteği.
		○ LZ4 sıkıştırma desteği eklenmiştir.
Uygulama Geliştirme
	• Yeni Performans İyileştirmeleri: AMQP mesaj onaylamalarındaki işlem iyileştirmeleri.
	• .NET ve XMS .NET için yeni iyileştirmeler.
	• JMS ve Jakarta Messaging için iyileştirmeler: TCP/IP bağlantılarını paylaşma ve modüler uygulamalar kullanma.
IBM MQ Advanced için Yeni Özellikler
	• Native HA (Yüksek Erişilebilirlik) için yeni haklar.
	• AWS ve Azure Marketplace üzerinden IBM MQ entegrasyonu.
z/OS - Base ve Advanced VUE Entitlement
	• Yeni Güvenlik Özellikleri: REST API için kullanıcı bağlamı ayarları.
	• Z/OS için daha fazla iyileştirme: SMF kuyruk istatistikleri ve yeni yönetim komutları.
Değişiklikler ve Kaldırılan Özellikler
	• Yeni ve Değiştirilen Mesajlar: IBM MQ 9.3.0'dan bu yana bazı yeni mesajlar eklendi ve eski mesajlar değiştirildi.
	• Eski Özellikler: Bazı özellikler IBM MQ 9.4.0'dan itibaren kullanımdan kaldırıldı veya istikrara kavuştu.
	• Lisans ve Kurulum Değişiklikleri: setmqinst komutunun nonprod (üretim dışı) lisanslama için yapılan değişiklikler.
	• Güvenlik Değişiklikleri: AMQP kanalları için desteklenen keystore türlerinde değişiklikler ve FIPS modunda RSA anahtar değişiminin kaldırılması.
Bu sürümde, kullanıcılar güvenlik, yönetim, uygulama geliştirme ve platformlar arası özelliklerde önemli iyileştirmeler ve yeni yeteneklere erişebilecek. Ayrıca, birçok eski özellik kaldırılmış veya güncellenmiş durumda.


IBM MQ 9.4 Quick Start Guide 
Abstract (Özet) Bu belge, IBM MQ 9.4.0 Long Term Support (LTS) sürümü ve bakım bilgilerini, ayrıca IBM MQ 9.4.x Continuous Delivery (CD) sürümlerini içermektedir.
Content (İçerik)
Bu belgede, ürün sınırlamaları ve bilinen problemler ana başlık olarak ele alınmaktadır.
IBM MQ ile ilgili daha fazla bilgi için:
	• IBM MQ web sitesi
	• SupportPac web sayfası
	• IBM MQ destek sayfası
	• IBM MQ ürün belgeleri
Announcement letters (Duyuru Mektupları): IBM MQ 9.4 ile ilgili duyuru mektupları ve ürün tanımlamaları:
	• IBM MQ 9.4.1; IBM MQ as a Service Reserved Instance; IBM MQ on Cloud offering name change
	• IBM MQ 9.4 for Multiplatforms and IBM MQ on Cloud
	• IBM MQ for z/OS 9.4 and IBM MQ Appliance 9.4
Update History (Güncelleme Geçmişi):
	• 24 Ekim 2024: IBM MQ 9.4.1 için güncelleme yapıldı.
	• 5 Eylül 2024: IBM MQ 9.4.0.5 Fix Pack için güncelleme yapıldı.
	• 2 Temmuz 2024: IBM MQ for z/OS 9.4 ve IBM MQ Appliance 9.4 için güncelleme yapıldı.
	• 18 Haziran 2024: IBM MQ 9.4.0 for Multiplatforms için ilk oluşturma yapıldı.
Installation Instructions (Kurulum Talimatları): IBM MQ'nun tüm desteklenen platformlarda kurulumu için talimatlar ve gerekli donanım/yazılım yapılandırmaları için:
	• IBM MQ 9.4 Kurulum Sayfası
Limitations and Known Problems (Sınırlamalar ve Bilinen Problemler)
Continuous Delivery (CD) Sürümü İçin Sınırlamalar ve Bilinen Problemler (IBM MQ 9.4.1)
	• Yeni bir sınırlama veya bilinen problem yoktur.
Long Term Support (LTS) Sürümü İçin Sınırlamalar ve Bilinen Problemler (IBM MQ 9.4.0, Fix Pack 5)
	• Linux: IBM MQ konsolunu kullanarak IBM MQ 9.4.0.5'e geçiş yapıldığında çok sayıda sistem mesajı görünmektedir. Linux sistemlerinde, rpm -U MQ* komutu kullanılarak yapılan yükseltme sırasında 6000'den fazla mesaj konsol çıktısına yazılabilir. Bu sorun, geçerli hata veya uyarı mesajlarının gözden kaçmasına neden olabilir. Bu sorun APAR IT46528 ile çözülmüştür.
Initial IBM MQ 9.4.0 Sürümü İçin Sınırlamalar ve Bilinen Problemler
	• libcurl dspmqver -a çıktısında eksik. GSKit, libcurl gerektiğinde yüklemelidir, ancak şu an libcurl çıktıda yer almamaktadır. Bu sorun gelecekteki CD güncellemeleri ve LTS bakım sürümleri ile düzeltilecektir.
	• RSA Anahtar Değişimi: IBM Java 8 JRE, FIPS modunda RSA anahtar değişimini kaldırmıştır. FIPS modunda çalışmaya devam etmek için AMQP sunucusu, Managed File Transfer (MFT), IBM MQ Console, IBM MQ Explorer, IBM MQ REST API ve IBM MQ Telemetry hizmetleri gibi IBM MQ bileşenlerinin desteklenen bir CipherSuite kullanacak şekilde değiştirilmesi gerekir.
Support (Destek) Bilgisi
	• Passport Advantage Online Destek Sayfası: https://www.ibm.com/software/howtobuy/passportadvantage/paocustomer/docs/en_US/ecare.html
IBM MQ 9.4 Ürünü İçin Teknik Destek
	• IBM MQ Ürün Ana Sayfası
	• IBM MQ Destek Portalı


IBM MQ 9.4 IBM Documentation Offline Uygulamasında
Eğer internet erişiminiz olmayan bir ortamda (airgap) çalışıyorsanız, IBM Documentation Offline uygulaması ile IBM MQ 9.4 ürün dokümantasyonunu indirebilir ve görüntüleyebilirsiniz.
IBM Documentation Offline, iki ana bileşenden oluşmaktadır:
	1. IBM Documentation Offline Uygulaması: Bu, IBM Documentation'ın çevrimdışı olarak kullanılabilen bir sürümüdür ve yerel olarak kurulum yapmanızı sağlar.
	2. Dokümantasyon Paketi: Bu paket, IBM Documentation'da çevrimiçi olarak yayımlanan dokümantasyonla aynıdır. IBM ID'nizle IBM Documentation'a giriş yaptıktan sonra, navigasyon panelinin alt kısmında "Offline docs" bağlantısı görüntülenir. Bu bağlantıya tıklayarak dokümantasyonu indirebilirsiniz.
Daha Detaylı Talimatlar İçin:
Dokümantasyon paketini ve uygulamayı nasıl indirebileceğinizle ilgili ayrıntılı talimatları şu linkten bulabilirsiniz: IBM Documentation Offline.
Önemli Notlar:
	• Birden fazla IBM dokümantasyon setini aynı uygulamaya yükleyebilirsiniz. Örneğin, IBM MQ 9.4, IBM MQ 9.3, IBM z/OS 2.4 ve IBM Cloud Pak for Integration 9.3 gibi çeşitli sürümleri aynı uygulama içinde görüntüleyebilirsiniz.
	• IBM WebSphere MQ 7.5 ve sonrasındaki sürümler için, IBM MQ sürümü artık çevrimiçi IBM Documentation'da bulunmasa bile, eski sürüm dokümantasyonlarını IBM MQ dokümantasyon indirme sitesinden indirebilirsiniz.
IBM MQ'nun eski sürümleri için dokümantasyon:
	• Eski IBM MQ sürümleri için dokümantasyon
Bu bilgilerle, internet erişiminiz olmasa bile IBM MQ 9.4 ve diğer sürümleriyle ilgili dokümantasyonu yerel ortamda erişebilirsiniz.


Erişilebilirlik Özellikleri - IBM MQ
Son Güncelleme: 2024-07-02
IBM MQ, engelli kullanıcıların bilgi teknolojisi içeriklerini başarılı bir şekilde kullanabilmesi için erişilebilirlik özellikleri sunar. Bu özellikler, sınırlı hareket kabiliyeti veya görme engeli olan kullanıcıların sistemleri etkin bir şekilde kullanmalarına yardımcı olur.
Erişilebilirlik Özellikleri
IBM MQ, şu ana erişilebilirlik özelliklerine sahiptir:
	• Yalnızca Klavye ile İşlem Yapabilme: Klavye kullanarak tam erişim sağlanabilir.
	• Ekran Okuyucu Desteği: Ekran okuyucuları kullanan kullanıcılar için erişilebilirlik desteği sağlanmıştır.
IBM MQ, W3C Standartları olan WAI-ARIA 1.0'ı kullanarak, US Section 508 ve Web İçeriği Erişilebilirlik Kılavuzları (WCAG) 2.0'a uygunluğu garanti eder. Erişilebilirlik özelliklerinden tam olarak yararlanabilmek için, ekran okuyucunuzun en son sürümünü ve bu ürün tarafından desteklenen en son web tarayıcısını kullanmanız gerekmektedir.
IBM MQ'nun çevrimiçi ürün dokümantasyonu, erişilebilirlik için optimize edilmiştir. Erişilebilirlik özellikleri hakkında daha fazla bilgiye IBM Documentation sayfasında ulaşılabilir.
Klavye Navigasyonu
Bu ürün, standart navigasyon tuşlarını kullanarak navigasyon sağlar.
Arayüz Bilgisi
IBM MQ'nun tam erişilebilir bir şekilde kullanılması için komut satırı arayüzü önerilmektedir. Komutlar hakkında daha fazla bilgi için:
	• IBM MQ'nun çoklu platformlar için yönetimi
	• IBM MQ yönetimi MQSC komutlarıyla
Windows üzerinde erişilebilir bir şekilde IBM MQ yüklemek için non-interaktif yükleme yöntemi önerilir. Daha fazla bilgi için İleri düzey yükleme msiexec kullanılarak.
IBM MQ Kullanıcı Arayüzleri ve Görsel İçerik
	• IBM MQ, ekranlarda 2-55 defa saniyede yanıp sönen içeriklere sahip değildir.
	• Web kullanıcı arayüzü, içeriği düzgün bir şekilde sunmak için CSS (Kaskadlı Stil Sayfaları) kullanmaz. Ancak, ürün dokümantasyonu için CSS kullanılmaktadır. IBM MQ, düşük görme seviyesindeki kullanıcılar için, sistem ekran ayarlarıyla uyumlu alternatif bir yol sunar. Font büyüklüğünü, cihaz veya tarayıcı ayarlarını kullanarak kontrol edebilirsiniz.
İlgili Erişilebilirlik Bilgileri
IBM'in erişilebilirlik hizmetlerine ek olarak, TTY telefon hizmeti sunulmaktadır:
	• TTY Hizmeti: 800-IBM-3383 (800-426-3383) (Kuzey Amerika içindeki kullanıcılar için)
IBM'in erişilebilirlik konusundaki taahhüdü hakkında daha fazla bilgi için IBM Accessibility sayfasını ziyaret edebilirsiniz.

IBM MQ Ürün Dokümantasyonu İçin Kullanılan Simgeler
Son Güncelleme: 2024-10-24
IBM MQ 9.4 sürümüne ait tüm dokümantasyonlar için, belirli sürüm türlerine ve platformlara ait bilgilerin ayrılması amacıyla simgeler kullanılır. Bu simgeler, ürün özelliklerinin hangi sürümlere ve platformlara uygulandığını belirtmek için kullanılır.
Sürüm Türü ve Sürüm Simgeleri
Herhangi bir ürün özelliği, belirli bir sürüm türüne uygulandığında, simgeler kullanılarak sürüm türü ve sürüm numarası belirtilir. Aşağıda yaygın kullanılan bazı simgeler:
	• Long Term Support (LTS): Koyu mavi simge, LTS sürümüne ait özellikleri belirtir.
	• Continuous Delivery (CD): Açık mavi simge, CD sürümüne ait özellikleri belirtir.
	• IBM MQ Advanced: Yeşil simge, IBM MQ Advanced ürünü ile ilgili bilgileri belirtir.
Platform Simgeleri
Platform simgeleri, yalnızca belirli platformlar veya platform grupları için geçerli olan bilgileri işaretler.
	• AIX, Linux, Windows: Bu platformlar için olan bilgiler belirtilir.
	• z/OS: z/OS platformuna özgü bilgiler belirtilir.
IBM MQ'nun çeşitli platformlardaki sürümleri için geçerli olan bilgilere ulaşılabilir. Simgeler sayesinde hangi özelliklerin hangi platformlarda ve sürümlerde mevcut olduğu hızlıca görülebilir.

https://www.ibm.com/docs/en/ibm-mq/9.4?topic=information-mq-downloads

IBM MQ'nın indirme sayfası, ürünün tam sürümünü, fix pack'leri (düzeltme paketleri), CSUs'ları (Kümülatif Güvenlik Güncellemeleri) ve ek IBM MQ kaynaklarını (resource adapter ve istemciler gibi) indirme bağlantılarını sunmaktadır. İşte bu sayfada yer alan temel bilgiler:
Herhangi bir MQ sürümü için tüm indirmeler:
Bu bölümde, IBM MQ'nun tüm sürümleri için bağlantılar yer almaktadır:
	• IBM MQ 9.4 : https://www.ibm.com/support/pages/downloading-ibm-mq-94
	• IBM MQ 9.3 : https://www.ibm.com/support/pages/downloading-ibm-mq-93
	• IBM MQ 9.2 : https://www.ibm.com/support/pages/downloading-ibm-mq-92
	• IBM MQ 9.1
	• IBM MQ 9.0
	• IBM MQ 8.0
	• IBM MQ 7.5
Yukarıdaki her bir sürüm için, en son Continuous Delivery (CD) sürümüne veya Long Term Support (LTS) sürümüne ilişkin güncellemeleri içeren bağlantılara ulaşabilirsiniz. Bu bağlantılarda ayrıca CSU ve fix pack seçeneklerine de ulaşabilirsiniz.
IBM MQ 9.4 Ücretsiz 90 Günlük Deneme Sürümü:
IBM MQ'nun LTS sürümünün 90 gün ücretsiz deneme sürümünü buradan indirebilirsiniz: IBM MQ 90 Günlük Deneme Sürümü Bu, IBM MQ’yu denemek isteyenler veya tam sürüm lisansı alana kadar geçici olarak kullanmak isteyenler için uygundur. Deneme sürümü kullanarak kurulum yapabilir ve sonrasında tam lisansa geçiş yapabilirsiniz.
IBM MQ İstemcileri ve Diğer Kaynaklar:
Aşağıda, IBM MQ için çeşitli istemciler ve bileşenler bulunmaktadır:
	• IBM MQ C ve .NET İstemcileri: IBM MQ'nun C ve .NET tabanlı istemcileri.
	• IBM MQ Java / JMS İstemcisi: IBM MQ Java istemcisi ve JMS için bileşenler.
	• IBM MQ Message Service Client (XMS): C/C++ için XMS istemcisi.
	• IBM MQ Redistributable İstemciler: Dağıtılabilir istemci bileşenleri.
	• IBM MQ Resource Adapter: Java EE veya Jakarta EE uyumlu uygulama sunucuları ile kullanılabilen adaptör.
	• IBM MQ Managed File Transfer (MFT) İstemcileri: MFT bileşenleri.
IBM MQ Bileşenleri:
Aşağıda bazı IBM MQ bileşenleri yer almaktadır:
	• IBM MQ Internet Pass-Thru (MQIPT): Güvenlik ve bağlantı yönetimi için bir bileşen.
	• IBM MQ Explorer: IBM MQ yönetimi için kullanabileceğiniz bağımsız kurulum görüntüsü.
	• IBM MQ Web Server: IBM MQ web sunucusu için bağımsız kurulum görüntüsü.
	• IBM Instana® Tracing Exit for IBM MQ: Tracing araçları ile birlikte kullanım.
IBM MQ Containers:
Konteynerler için bazı önemli özellikler:
	• Prebuilt IBM MQ Advanced Container: IBM MQ Advanced için önceden yapılmış konteyner.
	• Build Your Own: Kendi IBM MQ konteynerinizi oluşturabileceğiniz GitHub bağlantısı. MQ Konteyneri Oluşturma
	• IBM MQ Advanced Non-install Images for Linux: IBM MQ’nun Linux için yüklenmemiş (non-install) görüntüleri.
	• IBM MQ Advanced for Developers Non-install Image: Geliştiriciler için non-install paketleri (Linux, ARM64, x86-64 ve Raspberry Pi desteği).
IBM MQ Development Paketleri:
	• IBM MQ Advanced for Developers: Geliştiriciler için IBM MQ'nun geliştirme sürümü, Windows, Linux, ve Ubuntu için kullanılabilir.
	• IBM MQ Mac Toolkit for Development: MacOS üzerinde IBM MQ komutları çalıştırmanıza olanak tanır ve istemci uygulamaları geliştirmek için kullanılır.
IBM MQ SupportPacs:
IBM MQ SupportPacs; IBM MQ ürünleriyle ilgili belirli işlevsellikler veya hizmetler sunan, indirilebilir kod ve dökümantasyon paketleridir. Bu SupportPacs'lar, IBM MQ'yu desteklemek amacıyla ekstra özellikler ekler.
Daha Fazla Bilgi ve Kaynaklar:
	• IBM MQ Web Sayfası: IBM MQ ürün sayfası
	• IBM MQ Container Helm Chart: Helm Chart
	• IBM MQ Container Registry: IBM MQ Container Registry




