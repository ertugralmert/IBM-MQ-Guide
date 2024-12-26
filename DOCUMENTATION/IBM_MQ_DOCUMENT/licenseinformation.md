IBM MQ Lisans Bilgileri
	• IBM MQ'yu Neler Alabilirsiniz?IBM MQ'nun çeşitli sürümleri ve bileşenleri, farklı lisans türleriyle sunulmaktadır. Örneğin, IBM MQ'nun "Advanced" sürümü veya "High Availability Replica" gibi özelliklere sahip versiyonları bağımsız olarak satın alınabilir. Lisanslama seçenekleri, yalnızca kurulum yapılacak ortamın ihtiyaçlarına göre belirlenmelidir.
	• Lisans Satın AlmaIBM MQ lisansları, AWS Marketplace veya Azure Marketplace gibi platformlar üzerinden temin edilebilir. Aynı zamanda Passport Advantage üzerinden de IBM MQ'nun lisansları alınabilir.
	• IBM MQ için Lisans ÖzellikleriÖzel lisans türleri ve sunuculara bağlanan istemciler için olan "unlimited installs" gibi seçenekler mevcuttur. Lisanslar, kurulum ortamına ve ürün özelliklerine göre değişebilir.
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

*********************************

IBM MQ Redistributable Components
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

************
IBM MQ Client for .NET Lisans Bilgileri
	• Ücretsiz İndirme: IBM MQ Client for .NET, ücretsiz olarak indirilebilen bir bileşendir. Bu bileşen, üçüncü taraf .NET uygulamalarının IBM MQ mesajlaşma altyapısına entegre edilmesini sağlar.
	• Lisans Koşulları: IBM MQ Client bileşenleri, IBM MQ ürün lisansına bağlı olarak IBM MQ Client lisans koşulları altında lisanslanır. Bu, yazılımın kullanımı ve dağıtımı ile ilgili kuralları belirler.
	• Dağıtılabilir Bileşenler: IBM MQ Client for .NET, belirli dağıtım hakları ile birlikte gelir. Bu, üçüncü tarafların IBM MQ uygulamalarını kolayca geliştirmesini ve dağıtmasını sağlar. Ancak, teknik destek ve hata düzeltmeleri için IBM ile bir destek sözleşmesi gereklidir.
	• Destek ve Hata Düzeltmeleri: IBM MQ Client bileşenleri "olduğu gibi" sağlanır ve bu bileşenler için teknik destek almak isteyen kullanıcılar, IBM ile bir destek sözleşmesi yapmak zorundadır.
***********
IBM MQ Ürün Tanımlayıcıları ve İhracat Bilgileri
	• IBM MQ Ürünleri ve PID Değerleri: IBM MQ ürünlerinin tanımlayıcılarını (PID) ve ihracat sınıflandırmalarını (ECCN) içeriyor. Örneğin:
		○ IBM MQ için PID: 5724-H72, ECCN: 5D992
		○ IBM MQ for z/OS için PID: 5655-MQ9, ECCN: 5D002.c.1
		○ IBM MQ Advanced için PID: 5655-AV1, ECCN: 5D002.c.1
	• IBM MQ Appliance Ürünleri:
		○ IBM MQ Appliance M2000: PID: 5725-S14, MTM: 8436-54X, ECCN: 5D992
		○ IBM MQ Appliance M2001: PID: 5725-20S, MTM: 8436-55X, ECCN: 5D992
		○ IBM MQ Appliance M2002: PID: 5737-14Y, MTM: 8441-54X, ECCN: 5D992
Ürün Lisansları ve Dağıtılabilirlik
	• IBM MQ için Lisanslama: IBM MQ ürünleri, belirli lisans koşulları ve dağıtım hakları altında sunulmaktadır. Her ürünün kendine ait bir PID değeri ve ihracat sınıflandırması vardır.
	• IBM MQ Appliances: IBM MQ Appliance ürünleri, donanım tabanlı çözümler olup, belirli ihracat sınıflandırmalarıyla listelenmiştir.
Önemli Notlar
	• IBM MQ for z/OS ve IBM MQ Advanced ürünleri, yüksek erişilebilirlik ve gelişmiş mesaj güvenliği gibi ek özellikler sunan lisanslara sahip olabilir.
	• IBM MQ Managed File Transfer ve IBM MQ Telemetry gibi bileşenler de lisansla birlikte sunulmaktadır.
