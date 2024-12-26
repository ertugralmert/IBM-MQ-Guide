
IBM MQ Streaming Queues Özelliği
Genel Bakış: IBM® MQ'nun streaming queues (akış kuyruğu) özelliği, bir kuyruğa gönderilen her mesajın hemen hemen aynı kopyasının başka bir kuyruğa iletilmesini sağlar. Bu özellik, bazı senaryolarda mesajların bir kopyasını oluşturmanız gerektiğinde faydalıdır. Örneğin:
	• Apache Kafka'ya mesaj akışı sağlamak için Kafka Connect source connector kullanarak IBM MQ'ya bağlanmak.
	• Sistemdeki verilerin analizini yapmak.
	• Mesajları gelecekteki bir zaman için kurtarma amacıyla depolamak.
	• Geliştirme ve test sistemlerinde kullanılmak üzere mesajları yakalamak.
	• IBM MQ olay mesajlarını sistem olay kuyruklarından tüketmek ve ek kopyalarını diğer kuyruklara veya konulara göndermek.
Bu senaryolarda, streaming queues yapılandırılması, orijinal mesajların akış işleminden etkilenmemesini sağlar. Bu, iş uygulamalarının akıştan etkilenmemesini garanti eder.
Streaming Queues Konfigürasyonu
Konfigürasyon:
Streaming queues, IBM MQ yöneticisi tarafından her bir kuyruk için yapılandırılır ve mesajlar, uygulama tarafından değil, queue manager (kuyruk yöneticisi) tarafından akışa alınır.
Örnek Konfigürasyon: Bir kuyruk, STREAMQ(MY.REMOTE.Q) şeklinde yapılandırılabilir; burada MY.REMOTE.Q bir uzak kuyruk tanımıdır.
Streaming Queues ile İlgili Kısıtlamalar
	• Transaction (İşlem) ile Streaming:Streaming queues özelliği, bir kuyruktan bir mesaja kopya eklerken, iki mesajın da aynı işlem (unit of work) altında kuyruğa eklenmesini sağlar. Bu, genellikle işlemlerin tutarlılığını sağlamaya yardımcı olur.
	• Cluster Queues (Küme Kuyrukları) ile Streaming:Mesajlar, yerel kuyruktan bir cluster kuyruğuna ve cluster kuyruk örneklerinden birine yerel kuyruğa aktarılabilir. Bu işlem, kümeleme yapılandırmalarında da çalışır.
Streaming Queues Özelliğinin Kullanım Alanları
	1. Veri Analizi:Sistemdeki veriler üzerinden analiz yapabilmek için mesajların bir kopyasını farklı kuyruklarda saklayabilirsiniz.
	2. Mesajları Kurtarma İçin Depolama:Mesajlar, ilerleyen zamanlarda kurtarma amacıyla saklanabilir. Bu, özellikle kritik işlemlerin kayıt altına alınması için kullanışlıdır.
	3. Geliştirme ve Test Sistemlerinde Kullanma:Geliştirme ve test aşamalarında kullanılacak veri setlerinin oluşturulması amacıyla mesajlar kopyalanabilir.
	4. Sistem Olay Mesajları ve Ekstra Kopyalar:IBM MQ sisteminin olay mesajlarını kullanarak, mesajlar ek kuyruklara veya konu başlıklarına yönlendirilebilir.
	5. Cluster Kuyruklarında Mesaj Akışı:Mesajlar, küme kuyruklarına ve küme kuyruklarından yerel kuyruklara aktarılabilir. Bu, dağıtık sistemlerde etkin veri aktarımı sağlar.

Mesaj Geçmişi Saklama
CAPEXPRY (Geçerlilik Süresi) Özelliği: Streaming queues özelliği, mesajların bir geçmişinin tutulmasını sağlar. Bu özellik, mesajların belli bir süre boyunca saklanmasını sağlamak için CAPEXPRY (geçerlilik süresi) özelliği ile yapılandırılabilir. Bu sayede mesajların belirli bir süre sonra otomatik olarak silinmesi sağlanabilir.

Bu özellik, IBM MQ'yu veri akışları, veri analizi ve mesajların korunması gibi çeşitli kritik senaryolarda etkili şekilde kullanabilmenizi sağlar. Bu özellik, özellikle veri güvenliği ve sistem performansının kritik olduğu üretim ortamlarında büyük önem taşır.


**************

Streaming Queues Configuration in IBM MQ
Genel Bakış: IBM® MQ'nun streaming queues (akış kuyruğu) özelliği, yöneticilerin her bir kuyruk için yapılandırabileceği bir özelliktir. Bu özellik sayesinde, mesajlar, kuyruk yöneticisi tarafından akışa alınır ve uygulama tarafından değil. Bu, uygulamanın orijinal kuyruğa mesaj gönderirken, akışın gerçekleştiğinden haberdar olmaması anlamına gelir. Benzer şekilde, orijinal kuyruğa mesajları tüketen uygulama da mesaj akışından haberdar değildir.
Not: IBM MQ istemci kütüphanesinin sürümünü güncellemek gerekmez ve orijinal mesajlar akış sürecinden tamamen etkilenmez.
İki Modda Yapılandırma
	1. Best Effort (En İyi Çaba)Bu modda, kuyruk yöneticisi, orijinal mesajın teslimatının, akış mesajının teslimatından daha önemli olduğunu varsayar.Eğer orijinal mesaj teslim edilebiliyorsa ancak akış mesajı teslim edilemiyorsa, orijinal mesaj yine de kuyruğa teslim edilir. Bu mod, iş uygulamalarının akış işleminden etkilenmemesinin önemli olduğu durumlar için uygundur.
	2. Must Duplicate (Zorunlu Kopya)Bu modda, kuyruk yöneticisi her iki mesajın da başarılı bir şekilde teslim edilmesini sağlar.Eğer akış mesajı teslim edilemiyorsa (örneğin, ikinci kuyruk doluysa), orijinal mesaj da teslim edilmez. Uygulama, bir hata nedeni kodu alır ve mesajı tekrar göndermeyi denemelidir. Bu mod, her iki mesajın da teslim edilmesi gerektiği senaryolar için kullanılır.
Akış Mesajları
Çoğu durumda, ikinci kuyruğa teslim edilen mesaj, orijinal mesajın bir kopyasıdır. Bu, mesajın tüm açıklama alanlarını (mesaj ID ve korelasyon ID dahil) içerir. Akış mesajları, orijinal mesajlara oldukça yakın kopyalar olarak tasarlanır, böylece daha kolay bulunabilir ve gerekirse başka bir IBM MQ sistemine tekrar aktarılabilir.
Akış Mesajlarında Yapılan Değişiklikler:
	• Mesajın son kullanma tarihi (expiry):Akış mesajının son kullanma tarihi, orijinal mesajın son kullanma tarihinden bağımsız olarak MQEI_UNLIMITED olarak ayarlanır. Eğer ikinci kuyrukta CAPEXPRY özelliği ayarlanmışsa, bu değeri kullanarak akış mesajının son kullanma tarihi belirlenir.
	• Rapor Seçenekleri:Orijinal mesajda belirtilen şu raporlama seçenekleri, akış mesajlarında etkinleştirilmez:
		○ Aktivite raporları
		○ Süre sonu raporları
		○ İstisna raporları
		○ Varış onayı (COA)
		○ Teslimat onayı (COD)Bu, akış mesajlarının, beklenmedik rapor mesajlarını, bu tür raporları almak için tasarlanmamış uygulamalara iletmeyecek şekilde yapılandırılmasını sağlar.
Diğer Özellikler:
	• Akış mesajları, genellikle ikinci kuyrukla ilgili hiçbir özelliği taşımaz. Örneğin, ikinci kuyruğun DEFPSIST ve DEFPRTY gibi özellikleri, akış mesajını etkilemez.
Özel Durumlar:
	• CAPEXPRY Özelliği:Eğer ikinci kuyruk CAPEXPRY özelliği ile yapılandırılmışsa, bu özellik akış mesajına da uygulanır.
	• Cluster Kuyruklarında DEFBIND:Eğer ikinci kuyruk bir cluster kuyruğuysa, akış mesajı, DEFBIND özelliğinde belirtilen bağlama seçeneği kullanılarak kuyruğa iletilir.
Kullanım Senaryoları
	• Veri Depolama ve Kurtarma:Mesajların geçmişini saklamak için akış kuyrukları kullanılabilir, bu da verilerin belirli bir süre boyunca korunmasını sağlar.
	• Veri Akışı ve Analiz:Sistem içindeki verilerin analiz edilmesi veya başka sistemlere veri akışı yapılması için kullanılabilir.
Akış kuyrukları özelliği, IBM MQ sistemlerinde mesajların güvenli ve tutarlı bir şekilde kopyalanmasını sağlayarak, birden fazla uygulamanın aynı mesaj verisi üzerinde işlem yapmasına imkan verir.


****************


Streaming to Remote and Alias Queues in IBM MQ
Genel Bakış: IBM® MQ'da, mesajların yerel kuyruklardan uzak kuyruklara (remote queues) veya takma ad kuyruklarına (alias queues) akışının yapılması mümkündür. Bu özellik, bir kuyruktaki mesajları başka bir kuyruktan bağımsız olarak çoğaltmanıza ve farklı sistemlere iletmenize olanak tanır.
Streaming to Remote Queues (Uzak Kuyruğa Akış)
	• Tanım:Yerel bir kuyruktan uzak bir kuyruğa mesaj akışı yapıldığında, kopyalanmış mesajlar başka bir kuyruk yöneticisine ait bir kuyruğa gönderilebilir. Bu, mesajların birden fazla IBM MQ ağındaki kuyruğa kopyalanmasını sağlar.
	• Örnek Senaryo:Örneğin, Q1 kuyruğu STREAMQ(MY.REMOTE.Q) şeklinde yapılandırılabilir. Burada, MY.REMOTE.Q bir uzak kuyruk tanımıdır ve mesajlar bu kuyruk üzerinden yönlendirilir.
Avantaj:
Bu özellik, mesajların merkezi bir noktada saklanmasının yanı sıra, farklı konumlar arasında veri yedekleme ve yeniden iletim sağlar.
Streaming to Alias Queues (Takma Ad Kuyruğuna Akış)
	• Tanım:Mesajları bir alias kuyruğuna akış yapmak, çoğaltılmış mesajları alias kuyruğunun hedef kuyruğuna yönlendirmeyi sağlar. Takma ad kuyrukları, hedef olarak bir başka kuyruk ya da bir topic (yayın/abone) de olabilir. Bu durumda, çoğaltılmış mesajlar, topic'e abone olan tüm alıcılara gönderilebilir.
	• Publish/Subscribe ile Entegrasyon:Bir alias kuyruğu hedef olarak bir topic'e işaret ediyorsa, bu durumda çoğaltılmış mesajlar, topic'e abone olan her kullanıcılara gönderilecektir. Ancak, mesajlar orijinal mesajla tamamen aynı olmayacaktır. Yayın/abone kurallarına göre şu değişiklikler olabilir:
		○ Yeni bir mesaj ID'si oluşturulur.
		○ Korelasyon ID'si, abonelik yapılandırmasına bağlı olarak oluşturulur.
		○ UserIdentifier alanı, mesajı gönderen uygulamanın kimliğinden ziyade, kuyruk yöneticisinin çalıştığı kullanıcıyı gösterir.
		○ PutApplName, mesajı koyan uygulamanın adı yerine kuyruk yöneticisinin adı olur.
Önemli Notlar:
	• STREAMQ Özelliği:Uzak kuyruklar veya alias kuyrukları üzerinde doğrudan STREAMQ özelliği yapılandırılamaz. Yalnızca mesajlar bu kuyruklara akış yapılabilir, bu kuyruklardan mesaj akışı yapılamaz.
	• Alias Kuyruğu ve STREAMQ:Eğer mesajlar bir alias kuyruğuna akış yapılacaksa, alias kuyruğunun hedef kuyruk üzerinde STREAMQ özelliği ayarlanmış olamaz.
Özetle:
	1. Uzak Kuyruklara Akış:Mesajlar, orijinal kuyruktan bir uzak kuyruğa çoğaltılır ve başka bir IBM MQ sisteminde bulunan kuyruğa iletilir. Bu, çoklu sistemler arasında veri iletimi için faydalıdır.
	2. Takma Ad Kuyruklarına Akış:Takma ad kuyrukları, topic gibi başka hedeflere yönlendirilerek çoğaltılmış mesajların daha fazla alıcıya iletilmesine olanak sağlar. Ancak, mesajlar, orijinal mesajlardan farklı olacak şekilde bazı meta verilerinde değişikliklere uğrar.
Bu özellikler, özellikle mesajların güvenli bir şekilde çoğaltılmasına, arşivlenmesine veya analiz edilmesine olanak tanır.


****************

Streaming Queue Restrictions in IBM MQ
IBM® MQ'da streaming kuyrukları kullanırken, bazı yapılandırmalar desteklenmemektedir. Bu sınırlamalar, mesajların çoğaltılması sırasında karşılaşılabilecek çeşitli senaryoları engeller veya kısıtlar. Aşağıda, streaming kuyruğu özelliğini kullanırken karşılaşılan bazı yapılandırma kısıtlamaları bulunmaktadır:
1. Kuyruk Zinciri Tanımlaması:
	• Desteklenmeyen yapılandırma: Kuyruklar arasında bir zincir oluşturarak mesajları birbirine aktarmak, örneğin: Q1 -> Q2 -> Q3 -> Q4 şeklinde.
	• Açıklama: Bir kuyruktan diğerine sürekli akış sağlamak, her kuyruğun mesajları bir sonraki kuyruğa iletmesini sağlamak mümkün değildir. Bu tür bir yapılandırma, kaynak kuyruğa akışta bir döngü oluşturur ve bu, desteklenmez.
2. Kuyruk Döngüsü Tanımlaması:
	• Desteklenmeyen yapılandırma: Kuyruklar arasında bir döngü oluşturarak mesajların sürekli birbirine akmasını sağlamak, örneğin: Q1 -> Q2 -> Q1 şeklinde.
	• Açıklama: Aynı mesajın sürekli olarak birbirine aktarılacağı bir döngü oluşturmak, mesajın doğru bir şekilde işlenmesini engeller ve bu tür döngüler desteklenmez.
3. Abonelik Tanımlaması ile STREAMQ Özelliği:
	• Desteklenmeyen yapılandırma: Bir abonelik tanımlandığında ve hedef kuyrukta STREAMQ özelliği tanımlı olduğunda.
	• Açıklama: Eğer bir kuyruk bir topic (konu) için abone olarak yapılandırılmışsa ve bu kuyruğa STREAMQ eklenmişse, bu yapılandırma mümkün değildir.
4. XMITQ ile Yapılandırılmış Kuyruklar:
	• Desteklenmeyen yapılandırma: USAGE(XMITQ) olarak yapılandırılmış bir kuyrukta STREAMQ özelliğinin tanımlanması.
	• Açıklama: XMITQ (Transmission Queue) olarak kullanılan kuyruğa STREAMQ eklenemez. XMITQ özelliği, mesajların iletimi için özel bir yapılandırma gerektirdiğinden, STREAMQ özelliğiyle çakışır.
5. Dinamik Kuyrukların STREAMQ Özelliği:
	• Desteklenmeyen yapılandırma: Dinamik kuyruklar için STREAMQ özelliği değiştirilmesi.
	• Açıklama: Dinamik olarak oluşturulan kuyruğun STREAMQ özelliği değiştirilmek istense de, bu mümkün değildir.
6. SYSTEM Kuyrukları ile STREAMQ:
	• Desteklenmeyen yapılandırma: SYSTEM.* adıyla başlayan herhangi bir kuyruk için STREAMQ tanımlanması, ancak aşağıdaki istisnalar dışında:
		○ SYSTEM.DEFAULT.LOCAL.QUEUE
		○ SYSTEM.ADMIN.ACCOUNTING.QUEUE
		○ SYSTEM.ADMIN.ACTIVITY.QUEUE
		○ SYSTEM.ADMIN.CHANNEL.EVENT
		○ SYSTEM.ADMIN.COMMAND.EVENT
		○ SYSTEM.ADMIN.CONFIG.EVENT
		○ SYSTEM.ADMIN.LOGGER.EVENT
		○ SYSTEM.ADMIN.PERFM.EVENT
		○ SYSTEM.ADMIN.PUBSUB.EVENT
		○ SYSTEM.ADMIN.QMGR.EVENT
		○ SYSTEM.ADMIN.STATISTICS.QUEUE
		○ SYSTEM.DEFAULT.MODEL.QUEUE
		○ SYSTEM.JMS.TEMPQ.MODEL
	• Açıklama: SYSTEM.* adıyla başlayan sistem kuyruğunda STREAMQ özelliği yapılandırılamaz. Ancak, belirli sistem kuyruğu isimlerinde, bu kısıtlama geçerli değildir ve bu kuyruğa STREAMQ tanımlanabilir.
7. Model Kuyruğu Adı ile STREAMQ Tanımlanması:
	• Desteklenmeyen yapılandırma: Bir model kuyruğunun adıyla STREAMQ özelliği tanımlanması.
	• Açıklama: Model kuyrukları, mesajların şablon olarak oluşturulmasına yarar ve bu tür kuyruklarda STREAMQ özelliği tanımlanamaz.

Özet:
Bu kısıtlamalar, IBM MQ'da streaming kuyruğu özelliğini kullanırken karşılaşılan bazı yapılandırma engelleridir. Uygulamanın doğru ve verimli bir şekilde çalışabilmesi için bu sınırlamalar göz önünde bulundurulmalıdır. Özellikle kuyruklar arasında döngüler ve zincirler oluşturmak, sistem kuyruğu tanımlamaları ve dinamik kuyruklar gibi belirli durumlar, streaming kuyruğu özelliklerini kullanırken kaçınılması gereken senaryolardır.



**************

IBM MQ Streaming Kuyrukları ve İşlemler
Streaming Kuyrukları ve İşlemler
IBM MQ’nun streaming kuyrukları özelliği, bir kuyruğa gönderilen mesajın, ikinci bir kuyruğa kopyalanmasını sağlar. Bu kopyalama işlemi, genellikle bir işlem birimi (unit of work) içerisinde yapılır. Stream edilen mesajların durumu, orijinal mesajın nasıl gönderildiğine göre farklılık gösterir:
	1. Orijinal mesaj MQPMO_SYNCPOINT ile gönderildiyse:
		○ Kopyalanan mesaj, aynı işlem birimi içerisinde stream kuyruğuna gönderilir. Bu durumda, hem orijinal mesaj hem de kopyalanan mesajın başarılı bir şekilde teslim edilmesi beklenir; aksi takdirde her iki mesaj da teslim edilmez.
	2. Orijinal mesaj MQPMO_NO_SYNCPOINT ile gönderildiyse:
		○ Bu durumda, bir işlem birimi başlatılır, ancak orijinal mesaj işlem birimi talep etmemiş olsa bile, hem orijinal mesaj hem de kopyalanan mesaj aynı işlem birimi içinde işlenir. Bu:
			§ Kopyalanan mesajın teslim edilmediği durumda orijinal mesajın da teslim edilmemesini garanti eder.
			§ Performans artışı sağlar çünkü her iki mesaj aynı işlem birimi içinde yer alır.İstisnalar:
		○ Eğer orijinal mesaj, MQPMO_NO_SYNCPOINT ile ve STRMQOS özelliği BESTEF (best effort) olarak ayarlanmışsa, mesajlar işlem birimi içinde teslim edilmez. Bu durumda, kopyalanan mesajın teslim edilmemesi orijinal mesajı etkilemez.
Cluster Kuyruklarına Mesaj Stream Etme ve Cluster Kuyruklarından Mesaj Stream Etme
	1. Cluster Kuyruğuna Mesaj Stream Etme:
		○ Bir yerel kuyruğa gelen orijinal mesajların bir kopyasının bir veya birden fazla cluster kuyruk instance'ına gönderilmesini sağlar. Bu, iş yükü dengelemesi yapmak ya da sadece cluster'da başka bir kuyrukta kopyaların yer almasını sağlamak için kullanılabilir.
		○ Cluster Kuyruğu Çalışma Yükü Dengeleme: Mesajlar, DEFBIND özelliğine göre dağıtılır:
			§ Eğer DEFBIND(OPEN) olarak ayarlanmışsa, orijinal kuyruk açıldığında bir cluster kuyruk instance'ı seçilir ve tüm kopyalanan mesajlar bu instance'a yönlendirilir.
			§ Eğer DEFBIND(NOTFIXED) olarak ayarlanmışsa, her MQPUT işlemi için bir cluster kuyruk instance'ı seçilir.Not: Cluster kuyrukları için tüm instance’lar aynı DEFBIND değerine sahip olmalıdır.
	2. Cluster Kuyruğundan Mesaj Stream Etme:
		○ Eğer bir cluster kuyruğunun birden fazla instance'ına mesaj gönderiyorsanız, her bir mesajın bir kopyasının aynı queue manager üzerinde bir stream kuyruğuna teslim edilmesini sağlamak için kullanılabilir.
Mesajların Tarihini Saklamak İçin Streaming Kuyruklarını Kullanma
Mesajların bir kopyasını belirli bir süre saklamak için streaming kuyrukları kullanılabilir. Bu, örneğin, orijinal mesaj bir uygulama tarafından yanlışlıkla silindiğinde, mesajları geri alabilmek için faydalıdır.
CAPEXPRY Özelliği ile Streaming Kuyruğuna Mesaj Saklama:
	• CAPEXPRY (Mesajın Süre Sonu) özelliği, stream edilen mesajların ne kadar süreyle saklanacağını belirler.
	• Adımlar:
		1. CAPEXPRY özelliğini, mesajların stream edileceği kuyruğa ayarlayın.
		2. Orijinal kuyruğun CAPEXPRY değerini değiştirmenize gerek yoktur.
		3. Şu faktörleri göz önünde bulundurun:
			§ Mesajlara ne kadar süreyle erişmeniz gerektiği.
			§ Orijinal kuyruktan gelen mesaj hızına bağlı olarak, hedef kuyruğun MAXDEPTH ve MAXFSIZE özelliklerinin nasıl ayarlanması gerektiği.
Stream Edilen Mesajlara Erişim:
Eğer bir problem meydana gelir ve bazı veya tüm stream edilen mesajlara erişmeniz gerekirse, dmpmqmsg komutunu kullanarak bu mesajlara erişebilirsiniz:
	• Kuyruktan mesajları okuyup, bir dosyaya kaydedebilirsiniz.
	• Dosyadan mesajları okuyup, tekrar kuyruğa yazabilirsiniz.
dmpmqmsg komutu ile mesaj başlıklarını düzenleyebilir ve örneğin, expiry değerini değiştirebilirsiniz.
Performans Düşünceleri:
Stream edilen mesajların bir kuyruğa kopyalanması ve daha sonra süre bitmiş mesajların silinmesi işlemi küçük bir performans maliyeti yaratır. Ancak, bu maliyet, mesajları manuel olarak başka bir kuyruğa koymak ve sonra uygulamanın bu mesajları silmesi için gereken işlem maliyetinden çok daha düşüktür. Bu konu ile ilgili daha fazla bilgi, Streaming Queues Performance Report'unda bulunmaktadır.
