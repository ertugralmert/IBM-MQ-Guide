IBM MQ Teknik Genel Bakış (2024-10-24)
IBM® MQ, uygulamalarınızı birbirine bağlayarak kuruluşunuzda bilgilerin dağıtımını yönetmenizi sağlar. IBM MQ, birbirinden farklı bileşenler (işlemciler, işletim sistemleri, alt sistemler ve iletişim protokoller) üzerinden tutarlı bir uygulama programlama arayüzü (API) kullanarak programların birbirleriyle iletişim kurmasına olanak tanır. Bu arayüzü kullanan uygulamalara mesaj kuyruğu uygulamaları denir.
Aşağıdaki başlıklar, mesaj kuyruğu ve IBM MQ tarafından sunulan diğer özellikler hakkında bilgi edinmenizi sağlar.

Mesaj Kuyruğu (Message Queuing) Tanıtımı
IBM MQ ürünleri, programların birbirleriyle iletişim kurmasını sağlar. Bu, birbirinden farklı bileşenler (farklı platformlar ve iletişim protokollerini içeren sistemler) üzerinde çalışabilir. Mesaj kuyruğu sistemi, veri iletişimini güvenli ve güvenilir bir şekilde sağlar.
İngilizce Terim: Message Queuing

IBM MQ Nesneleri (Objects)
Queue Manager (kuyruk yöneticisi), IBM MQ nesnelerinin özelliklerini tanımlar. Bu özellikler, IBM MQ'nun nesneleri nasıl işleyeceğini etkiler. Nesneler, IBM MQ komutları ve arayüzleri kullanılarak oluşturulup yönetilir. Programlardan ise Message Queue Interface (MQI) kullanılarak nesneler kontrol edilir. Nesneler, programlardan erişildiğinde bir IBM MQ Object Descriptor (MQOD) ile tanımlanır.
İngilizce Terimler:
	• Queue Manager: Kuyruk Yöneticisi
	• MQI (Message Queue Interface): Mesaj Kuyruğu Arayüzü
	• MQOD (Message Queue Object Descriptor): Mesaj Kuyruğu Nesne Tanımlayıcısı

Dağıtık Kuyruğu ve Kümeleme (Distributed Queuing and Clusters)
Dağıtık Kuyruğu (Distributed Queuing), mesajların bir kuyruk yöneticisinden diğerine gönderilmesini sağlar. Bu alıcı kuyruk yöneticisi aynı makinada veya farklı bir yerde olabilir, yakın bir yer veya dünyanın öteki tarafında olabilir. Kümeler (Clusters) oluşturularak, IBM MQ bu bağlantıların çoğunu sizin yerinize otomatik olarak yapılandırabilir.
İngilizce Terimler:
	• Cluster: Küme
	• Distributed Queuing: Dağıtık Kuyruğu

Yayın/Abone Mesajlaşma (Publish/Subscribe Messaging)
Yayın/abone mesajlaşma, bilgi sağlayıcısı ile bu bilgiyi tüketenler arasındaki bağı koparmaya olanak tanır. Gönderen ve alıcı uygulamaların birbiri hakkında herhangi bir bilgiye sahip olmadan bilgi gönderilip alınabilir.
İngilizce Terim: Publish/Subscribe Messaging

Yüksek Erişilebilirlik (High Availability - HA) Çözümleri Karşılaştırması
IBM MQ, yüksek erişilebilirlik (HA) için çeşitli yapılandırmalar sunar. Bu yapılandırmalar, desteklenen platformlar ve sunulan özellikler bakımından farklılık gösterir.
İngilizce Terim: High Availability (HA) Solutions

IBM MQ Multicast
IBM MQ Multicast, düşük gecikmeli, yüksek dağılım ve güvenilir multicast mesajlaşma sunar. Bu özellik, birden fazla alıcıya mesaj göndermeyi verimli hale getirir.
İngilizce Terimler:
	• Multicast: Multicast (Çoklu yayım)
	• Low Latency: Düşük gecikme
	• High Fan-Out: Yüksek dağılım

MQ Telemetri Tanıtımı (MQ Telemetry Overview)
MQ Telemetry, uzak cihazlardan veri toplama ve bu cihazları yönetme sürecidir. MQXR (MQ Telemetry Servisi), bir kuyruk yöneticisinin parçası olarak hizmet verir. Bu özellik, cihaz verilerinin toplanması ve kontrol edilmesi ile web uygulamaları arasında entegrasyonu sağlar.
İngilizce Terimler:
	• Telemetry: Telemetri
	• MQXR: MQ Telemetry Servisi

IBM MQ'da Güvenlik (Security in IBM MQ)
IBM MQ, yetkilendirme servis arayüzü, kanal güvenliği için TLS (Transport Layer Security), kanal doğrulama kayıtları ve mesaj güvenliği gibi çeşitli güvenlik yöntemlerini destekler.
İngilizce Terimler:
	• TLS (Transport Layer Security): Taşıma Katmanı Güvenliği
	• Authorization Service Interface: Yetkilendirme Servis Arayüzü

IBM MQ MQI Müşterileri (MQI Clients)
MQI istemcisi, kuyruk yöneticisi çalıştırmayan bir sistemde IBM MQ'nun çalışmasına olanak tanır. Bu istemci, sistemlerde kuyruk yöneticisi olmadan mesaj kuyruğu özelliklerini kullanmanıza olanak sağlar.
İngilizce Terim: MQI Clients

İşlem Yönetimi ve Destek (Transaction Management and Support)
IBM MQ, işlem yönetimi ve transaction (işlem) desteği sağlar. Bu, veri tutarlılığı ve güvenilirliği sağlamak için çok önemlidir.
İngilizce Terim: Transaction Management

Kuyruk Yöneticisi İmkanlarını Genişletme (Extending Queue Manager Facilities)
User exits, API exits veya kurulum hizmetleri kullanarak kuyruk yöneticisi işlevselliğini genişletebilirsiniz.
İngilizce Terimler:
	• User Exits: Kullanıcı Çıkışları
	• API Exits: API Çıkışları

IBM MQ Java Dil Arayüzleri (Java Language Interfaces)
IBM MQ, Java uygulamalarında kullanılmak üzere üç farklı API sağlar:
	• IBM MQ classes for Jakarta Messaging
	• IBM MQ classes for JMS (Java Message Service)
	• IBM MQ classes for Java
İngilizce Terimler:
	• API (Application Programming Interface): Uygulama Programlama Arayüzü
	• JMS (Java Message Service): Java Mesaj Hizmeti
	• Jakarta Messaging: Jakarta Mesajlaşma

IBM MQ for z/OS Kavramları
IBM MQ for z/OS platformu, kayıt tutma mekanizması, depolama yönetimi teknikleri, geri dönüşüm birimi durumu ve kuyruk paylaşımı grupları gibi z/OS platformuna özgü kavramlar sunar.
İngilizce Terimler:
	• z/OS: IBM'in büyük sistem platformu
	• Queue Sharing Groups: Kuyruk Paylaşım Grupları

IBM MQ ve Diğer z/OS Ürünleri
IBM MQ, diğer z/OS ürünleriyle entegre çalışabilir, bu sayede z/OS ortamındaki diğer sistemlerle verimli iletişim sağlar.

Managed File Transfer (MFT)
Managed File Transfer, dosyaların sistemler arasında güvenli, yönetilen ve denetlenebilir bir şekilde transfer edilmesini sağlar.
İngilizce Terim: Managed File Transfer

IBM MQ Internet Pass-Thru (MQIPT)
MQIPT, uzak siteler arasında güvenli iletişim sağlamak için kullanılan isteğe bağlı bir IBM MQ bileşenidir.
İngilizce Terim: MQ Internet Pass-Thru

IBM MQ Konsolu ve REST API
IBM MQ Konsolu ve REST API, IBM MQ'nun yönetimini sağlayan ve mesajlaşma işlemleri gerçekleştirilen HTTP tabanlı arayüzlerdir.
İngilizce Terim:
	• REST API: REST API (Representational State Transfer API)
