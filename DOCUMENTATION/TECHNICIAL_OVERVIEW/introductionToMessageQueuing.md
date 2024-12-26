Mesaj Kuyruğu'na Giriş (Introduction to Message Queuing)
Son Güncelleme: 2024-07-02
IBM® MQ ürünleri, programların birbirleriyle iletişim kurmasını sağlar. Bu iletişim, birbirinden farklı bileşenlerden (işlemciler, işletim sistemleri, alt sistemler ve iletişim protokolleri) oluşan bir ağda tutarlı bir uygulama programlama arayüzü (API) kullanılarak yapılır. Bu API'yi kullanarak tasarlanan ve yazılan uygulamalar mesaj kuyruğu uygulamaları olarak bilinir, çünkü bu uygulamalar mesajlaşma ve kuyruğa koyma tarzını kullanır.
	• Mesajlaşma (Messaging), programların doğrudan birbirlerini çağırmak yerine, verileri mesajlar aracılığıyla göndererek iletişim kurması anlamına gelir.
	• Kuyruğa koyma (Queuing), mesajların depolarda kuyruğa yerleştirilmesi anlamına gelir. Bu sayede programlar birbirlerinden bağımsız olarak, farklı hızlarda ve farklı zamanlarda çalışabilirler ve birbirlerine mantıksal bir bağlantıya gerek duymazlar.
Mesaj kuyruğu, veri işleme dünyasında uzun yıllardır kullanılmaktadır. Bugün en yaygın kullanım alanlarından biri elektronik posta (e-mail) sistemidir. Kuyruğa koyma sistemi kullanılmazsa, uzak mesafelere elektronik bir mesaj göndermek, iletimdeki her düğümün mesajları iletebilmesi için her birinin kullanılabilir olması gereklidir. Ancak bir kuyruğa koyma sistemi ile mesajlar, sistem iletmeye hazır olana kadar ara düğümlerde depolanır ve nihai hedeflerine ulaştığında alıcılar tarafından okunana kadar beklerler.

Mesaj Kuyruğu Nedir?
Bir mesaj kuyruğu, ya da sadece kuyruk, mesajların gönderilebileceği adlandırılmış bir hedeftir. Mesajlar kuyruğa birikir ve kuyruğa hizmet eden programlar tarafından alınana kadar burada beklerler.
İngilizce Terimler:
	• Message Queue: Mesaj Kuyruğu
	• Queue Manager: Kuyruk Yöneticisi
Kuyruklar, bir queue manager (kuyruk yöneticisi) tarafından yönetilir. Kuyruğun fiziksel yapısı, kuyruk yöneticisinin çalıştığı işletim sistemine bağlıdır. Kuyruk, bir bilgisayarın belleğinde geçici bir tampon alanı ya da bir depolama cihazında (disk gibi) kalıcı bir veri kümesi olabilir. Kuyrukların fiziksel yönetimi kuyruk yöneticisinin sorumluluğundadır ve uygulama programlarına görünür değildir.

Mesaj Kuyruğu Türleri (Message Queuing Styles)
	1. Point-to-Point (Nokta-Noktaya) Mesajlaşma
		○ Bir mesaj kuyruğa yerleştirilir ve bir uygulama bu mesajı alır.
		○ Gönderen uygulama, alıcı uygulamanın bilgilerini (örneğin, mesajın gönderileceği kuyruğun adı) bilmelidir.İngilizce Terim: Point-to-Point Messaging
	2. Yayın/Abone (Publish/Subscribe) Mesajlaşma
		○ Yayın yapan bir uygulama tarafından yayınlanan her mesaj, her ilgili uygulamaya gönderilir. İlgili uygulamalar aboneler olarak bilinir.
		○ Bu modelde, mesajların gönderilmesi için gönderen ve alıcı uygulamaların birbirini tanımasına gerek yoktur.İngilizce Terimler:
		○ Publish/Subscribe: Yayın/Abone
		○ Subscriber: Abone

Mesaj Kuyruğunun Uygulama Tasarımcısına ve Geliştiricisine Faydaları
IBM MQ, uygulama programlarının mesajla yönlendirilen işleme katılmalarını sağlar. Uygulama programları, uygun mesaj kuyruğu yazılım ürünlerini kullanarak farklı platformlar arasında iletişim kurabilir. Örneğin, z/OS® uygulamaları IBM MQ for z/OS üzerinden iletişim kurabilir. Bu, uygulamaların alt yapıyı bilmeden iletişim kurmalarını sağlar.
Mesaj Kuyruğunun Faydaları:
	• Küçük programlar tasarlayarak birden fazla uygulama arasında paylaşılabilir.
	• Yeniden kullanılabilir yapı taşları ile hızlıca yeni uygulamalar inşa edilebilir.
	• Mesaj kuyruğu teknikleriyle yazılmış uygulamalar, kuyruk yöneticisinin çalışma şeklinin değişmesi durumunda etkilenmez.
	• İletişim protokollerini yazmaya gerek yoktur, kuyruk yöneticisi tüm iletişim süreçlerini yönetir.
	• Mesajları alan programlar, mesajlar gönderilmeden önce çalışmak zorunda değildir, mesajlar kuyruklarda bekletilebilir.
İngilizce Terimler:
	• Message Queue Interface (MQI): Mesaj Kuyruğu Arayüzü

Mesaj Kuyruğunun Ana Özellikleri ve Faydaları
Mesaj kuyruğunun temel özelliklerinden bazıları şunlardır:
	• Güvenlik (Security): Mesajların güvenliğini sağlamak için çeşitli yöntemler kullanılır.
	• Veri Bütünlüğü (Data Integrity): Mesajların doğru bir şekilde iletilmesi sağlanır.

Mesaj Kuyruğu Terminolojisi
Mesaj kuyruğu terminolojisi, kullanılan temel terimleri ve kavramları içerir. Mesajlar ve kuyruklar, bir mesaj kuyruğu sisteminin temel bileşenleridir.
İngilizce Terimler:
	• Message: Mesaj
	• Queue: Kuyruk

************************************
Temel Avantajlar:
	1. Zaman Bağımsız İletişim (Time-independent communication): Gönderici program, alıcı programın mesajı almak için hazır olup olmadığını beklemeden mesajı kuyruğa ekler. Mesaj kuyrukta tutulur ve alıcı program hazır olduğunda mesajı alır. Bu sayede, iletişim zaman bağımsız olur ve her iki program farklı hızlarda çalışabilir.
	2. Küçük Programlar Kullanma (Small programs): IBM MQ, küçük ve bağımsız programlar kullanarak büyük işler yapılmasına imkan tanır. Bu programlar daha küçük işlevsel parçalar olarak tasarlanabilir ve bir işin tamamlanması için birden fazla bağımsız program çalıştırılabilir.
	3. Mesaj Tetikleme (Message-driven processing): Kuyruğa bir mesaj geldiğinde, bu mesaj otomatik olarak bir programı tetikleyebilir. Yani, belirli bir mesaj geldiğinde ilgili program devreye girer ve işlem başlatılır.
	4. Olay Tabanlı İşlem (Event-driven processing): Programlar, kuyruktaki mesaj sayısına göre tetiklenebilir. Örneğin, bir program yalnızca belirli bir sayıda mesaj kuyruğa geldikçe çalışmaya başlayabilir.
	5. Mesaj Önceliği (Message priority): Gönderilen mesajlar kuyruğa eklenirken, her bir mesaja bir öncelik verilebilir. Bu, mesajların kuyruğa eklenme sırasını belirler.
	6. Güvenlik (Security): IBM MQ, mesajların güvenliğini sağlamak için çeşitli güvenlik önlemleri sunar. Mesajlar, iletim sırasında şifrelenebilir ve kuyruklar üzerinde kimlik doğrulaması yapılabilir.
	7. Veri Bütünlüğü (Data integrity): IBM MQ, verilerin doğruluğunu sağlamak için işlem birimlerini destekler. Bu, bir işlem sırasında yapılan değişikliklerin tutarlı olmasını garanti eder.
	8. Kurtarma Desteği (Recovery support): Mesajların güvenli bir şekilde iletilmesi sağlanırken, herhangi bir bağlantı kesintisi durumunda mesajlar yeniden iletilir. Ayrıca, tüm işlemler, sistemde bir hata durumunda geri alınabilir.
IBM MQ'yu Kullanmanın Avantajları:
	• Farklı Sistemler Arasında İletişim: IBM MQ, farklı platformlardaki programların birbirleriyle güvenli bir şekilde iletişim kurmasını sağlar. Mesajlar, alıcı programın hazır olduğu zaman alınır.
	• Daha Az Bağımlılık: Programlar, birbirleriyle doğrudan bağlantı kurmak zorunda kalmadan, yalnızca belirli bir kuyruğa mesaj gönderir ve alır.
	• Gelişmiş Yük Dengeleme ve Ölçeklenebilirlik: Kuyruklar üzerinden mesajlar dağıtılabilir ve birden fazla program kuyruğa hizmet verebilir. Bu, sistemdeki yükü dengeler.
	• Hızlı Uygulama Geliştirme: Mesaj kuyruklama, uygulamaların daha hızlı geliştirilmesini sağlar çünkü uygulama bileşenleri birbirinden bağımsız olarak çalışır.
Mesaj Kuyruğu Nedir?
Mesaj kuyruğu, mesajların gönderileceği adlandırılmış bir hedef noktadır. Mesajlar, kuyrukta birikir ve işleme alınana kadar bekletilir. Kuyruklar, bir kuyruk yöneticisi tarafından yönetilir. Kuyruklar, bellekte geçici olarak veya kalıcı depolama alanlarında (örneğin disk) fiziksel olarak tutulabilir.
İletişim Modelleri
	• Point-to-Point (Nokta-Nokta) İletişimi: Bir mesaj, bir kuyrukta bulunur ve yalnızca bir alıcı program tarafından alınır.
	• Publish/Subscribe (Yayınla/Abone Ol) İletişimi: Bir mesaj, birden fazla alıcıya gönderilebilir. Bu modelde, bir yayıncı mesajı yayınlar ve abone olan programlar bu mesajı alır.


*************************
Mesaj Kuyruklama Terminolojisi
	1. Kanallar (Channels):Kanallar, mesajları bir kuyruk yöneticisinden diğerine taşımak için kullanılır ve uygulamaları temel iletişim protokollerinden gizler. Kuyruk yöneticileri aynı sistemde veya farklı sistemlerde, farklı platformlarda bulunabilir. Mesajlar, birden fazla kaynaktan gelebilir, örneğin kullanıcı yazılımı uygulamaları, IBM MQ Explorer veya uzak yönetim komutları gibi.
	2. Küme (Cluster):Küme, birbiriyle mantıksal olarak ilişkilendirilmiş kuyruk yöneticilerinin ağını ifade eder. Küme kullanmanın iki ana nedeni vardır: sistem yönetimini basitleştirmek ve yük dengelemesi ile yüksek erişilebilirlik sağlamak. Küme oluşturulduğunda, yönetim daha basit hale gelir ve daha az tanımlama yapılması gerekir.
	3. IBM MQ MQI İstemcisi (IBM MQ MQI client):IBM MQ MQI istemcisi, IBM MQ'nun bağımsız olarak kurulabilen bileşenleridir. MQI istemcisi, birden fazla platformda çalışan ve bir kuyruk yöneticisine bağlanan IBM MQ uygulamaları ile iletişim kurmak için kullanılan bir bileşendir.
	4. İç Gruplama Kuyruğu (Intra-group queuing):Kuyruk paylaşım grubundaki kuyruk yöneticileri, normal kanallar kullanarak iletişim kurabilir veya iç gruplama kuyruğu (IGQ) tekniğini kullanarak hızlı mesaj iletimi yapabilir. Bu özellik sadece IBM MQ for z/OS için geçerlidir.
	5. Mesaj (Message):Mesaj, bir program tarafından gönderilen ve başka bir program için amaçlanan veri kümesidir. Mesajlar, genellikle uygulama verisi ve kontrol bilgisi içerir.
	6. Mesaj Kanalı Aracısı (Message Channel Agent):Mesaj kanal aracısı, bir kanalın bir ucudur. Bir çift mesaj kanal aracı, bir gönderici ve bir alıcı olmak üzere, mesajları bir kuyruk yöneticisinden diğerine taşır.
	7. Mesaj Tanımlayıcısı (Message Descriptor):IBM MQ mesajı, kontrol bilgileri ve uygulama verilerinden oluşur. Kontrol bilgileri, mesajın türünü, kimliğini, teslimat önceliğini içerir. Uygulama verilerinin yapısı, katılımcı programlar tarafından belirlenir.
	8. Nokta-Nokta İletişimi (Point-to-point messaging):Nokta-nokta iletişimi, her mesajın bir üretici uygulamadan bir tüketici uygulamaya doğru gitmesidir. Gönderici uygulama mesajı bir kuyruğa ekler ve alıcı uygulama bu mesajı kuyruğundan alır.
	9. Yayınla/Abone Ol İletişimi (Publish/subscribe messaging):Yayıncı uygulama tarafından yayımlanan her mesaj, ilgilenen her uygulamaya teslim edilir. Bu modelde ilgilenen uygulama "abonelik" olarak bilinir. Yayıncı, her mesaj için bir konu (topic) atar ve kuyruk yöneticisi bu konuya abone olanlara mesajı iletir.
	10. Kuyruk (Queue):Kuyruk, mesajların gönderilebileceği adlandırılmış bir hedef noktadır. Mesajlar kuyruklarda birikir ve bir program tarafından alınıncaya kadar bekler.
	11. Kuyruk Yöneticisi (Queue Manager):Kuyruk yöneticisi, uygulamalara kuyruk hizmetleri sunan bir sistem programıdır. Uygulamalar, kuyruklara mesaj eklemek ve almak için kuyruk yöneticisinin programlama arabirimini kullanır. Kuyruk yöneticisi ayrıca yeni kuyruklar oluşturma, mevcut kuyrukların özelliklerini değiştirme ve kuyruk yöneticisinin çalışmasını kontrol etme gibi işlevler sunar.
	12. Kuyruk Paylaşım Grubu (Queue Sharing Group):Kuyruk yöneticileri, paylaşılan kuyruğa erişebildiklerinde, bu yöneticiler bir kuyruk paylaşım grubu (QSG) oluştururlar. IBM MQ for z/OS üzerinde kullanılan bu özellik, kuyrukları paylaşarak yüksek erişilebilirlik sağlar.
	13. Paylaşılan Kuyruk (Shared Queue):Paylaşılan kuyruk, birden fazla kuyruk yöneticisinin erişebildiği ve aynı sysplex içinde bulunan bir kuyruk türüdür. Bu özellik yalnızca IBM MQ for z/OS için geçerlidir.
	14. Abonelik (Subscription):Yayınla/Abone ol uygulamaları, belirli konulardaki mesajlara ilgi gösterebilir. Bir uygulama, bir konuya abone olduğunda "abonelik" terimi kullanılır ve bu abone, kuyruklara iletilecek mesajların nasıl yerleştirileceğini belirler.
	15. Konu (Topic):Konu, bir yayın/abone mesajında yayınlanan bilginin konusunu tanımlar. Konular, yayın/abone sistemlerinde mesajların başarılı bir şekilde teslim edilmesini sağlamak için gereklidir. Yayıncı, her mesaja bir konu atar ve kuyruk yöneticisi bu konuyu, abone olanlar ile eşleştirir.

***************************
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
