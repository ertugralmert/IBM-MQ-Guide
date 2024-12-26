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
	• Programlar Arasında Doğrudan Bağlantı Olmaz:Mesaj kuyruklama, programlar arası dolaylı bir iletişim tekniğidir. Bir program mesajı bir kuyruğa gönderir, başka bir program bu kuyruğu alır ve mesajı işler. Bu şekilde, programlar fiziksel olarak birbirine bağlı değildir. Mesajlar bir kuyruğa yerleştirilir ve bu kuyruktan alınır.
	• Zaman Bağımsız İletişim:Mesajlar, gönderildikten sonra alıcı tarafından istenilen zaman diliminde alınabilir. Bu, bir programın mesaj gönderirken alıcının yanıtını beklemesine gerek olmadığı anlamına gelir. Gönderen program, mesajı gönderdikten sonra işlemine devam edebilir.
	• Küçük Programlar:Mesaj kuyruklama, büyük programlar yerine küçük, bağımsız çalışabilen programların kullanılmasını sağlar. Bu, programların daha esnek olmasını ve birbirlerinden bağımsız olarak çalışabilmesini sağlar.
	• Mesaj Tetiklemesi:Kuyruğa gelen mesajlar, ilgili uygulamaları tetikleyebilir. Bu sayede, uygulamalar kuyruğa mesaj geldiğinde otomatik olarak başlatılabilir.
	• Olay Tabanlı İşlem:Programlar, kuyruğun durumu üzerinden kontrol edilebilir. Örneğin, kuyruğa belirli bir sayıda mesaj geldiğinde bir program başlatılabilir.
	• Mesaj Önceliği:Gönderici, mesajlara öncelik atayabilir. Bu, kuyruğa gelen yeni mesajların hangi sırayla işleneceğini belirler.
	• Güvenlik:Mesajların güvenliği sağlanır. Kuyruk yöneticisi, mesajın yolculuğu ve kuyruğa yerleştirilmesi sırasında mesajın şifrelenmesini sağlar.
	• Veri Bütünlüğü:Mesajların taşınması sırasında veri bütünlüğü sağlanır. İşlem birimlerindeki başlangıç ve bitiş noktaları arasında senkronizasyon sağlanarak, veri kaybı önlenir.
	• Kurtarma Desteği:Sistem çökmesi durumunda, tüm kalıcı mesajlar geri yüklenir. Mesajlar, işlemler sırasında güvenli bir şekilde işlenir ve sistem yeniden başlatıldığında kaldığı yerden devam edebilir.
Mesaj Kuyruklama vs. Geleneksel İletişim
Geleneksel iletişimde, bir program A, B programına doğrudan bağlanarak mesaj gönderir. Ancak mesaj kuyruklamada, A programı mesajı bir kuyruğa gönderir ve B programı bu kuyruğu dinler. Bu sayede, programlar arasındaki doğrudan bağlantı ortadan kalkar.
Bu özellikler, uygulamaların daha esnek ve bağımsız çalışmasını sağlar


IBM MQ Terminolojisi
	1. Channel (Kanal):Kanal, bir kuyruk yöneticisinden diğerine mesajları taşıyan iletişim yoludur. Kanallar, mesajları taşıyan uygulamalardan, kullanılan iletişim protokollerinden ve mesajların geldiği yerden bağımsız olarak çalışır. Kanal, uygulamalar arasında mesaj iletimini sağlar.
	2. Cluster (Küme):Küme, birbiriyle mantıksal olarak ilişkili olan kuyruk yöneticilerinin ağını ifade eder. Küme kullanımı, uygulamaların iletişimde olduğu kuyruk yöneticilerini daha verimli hale getirir ve yük dengelemesi sağlar.
	3. Message (Mesaj):Mesaj, bir program tarafından diğerine gönderilen veri koleksiyonudur. Mesajlar, genellikle belirli bir formatta iletilir.
	4. Message Channel Agent (Mesaj Kanal Ajanı):Mesaj kanal ajanı, bir kanalın bir ucunda bulunan bileşendir. Bir kanal, iki mesaj kanal ajanı tarafından yönetilir: bir gönderici ajanı ve bir alıcı ajanı. Bu ajanlar, mesajları bir kuyruk yöneticisinden diğerine taşır.
	5. Queue (Kuyruk):Kuyruk, mesajların gönderildiği ve depolandığı hedef yerdir. Mesajlar kuyruklarda birikir ve daha sonra bu kuyrukları işleyen programlar tarafından alınır.
	6. Queue Manager (Kuyruk Yöneticisi):Kuyruk yöneticisi, uygulamalara kuyruklama hizmeti sunan bir sistem programıdır. Kuyruk yöneticisi, kuyruklarla ilgili işlemleri yönetir, yeni kuyruklar oluşturabilir, mevcut kuyrukları değiştirebilir.
	7. Queue Sharing Group (Kuyruk Paylaşım Grubu):Kuyruk paylaşım grubu, birden fazla kuyruk yöneticisinin aynı kuyrukları paylaşmasını sağlar. Bu özellik, IBM MQ for z/OS için geçerlidir.
	8. Publish/Subscribe Messaging (Yayınla/Abone Ol Mesajlaşması):Yayınla/Abone ol modeli, bir yayıncı tarafından yayınlanan mesajların tüm ilgilenen alıcılara (abone olanlara) iletilmesini sağlar. Burada, alıcılar belirli konulara abone olur ve ilgili mesajlar kuyruklarda birikir.
	9. Point-to-Point Messaging (Noktadan Noktaya Mesajlaşma):Noktadan noktaya mesajlaşmada, bir mesaj, yalnızca bir alıcıya iletilir. Gönderen program, mesajı bir kuyruğa yerleştirir ve tüketici programı bu mesajı alır.
	10. Topic (Konu):Konu, bir mesajın içerdiği bilginin başlığıdır. Yayınla/Abone ol sisteminde, her mesaj bir konuya atanır ve kuyruk yöneticisi bu konuyu takip eden abonelere mesajı iletir.

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






