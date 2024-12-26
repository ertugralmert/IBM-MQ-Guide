IBM MQ, Java uygulamaları için üç farklı uygulama programlama arabirimi (API) sağlar: IBM MQ sınıfları için Jakarta Messaging, IBM MQ sınıfları için JMS, ve IBM MQ sınıfları için Java. Bu arabirimler, Java uygulamalarının IBM MQ ile entegrasyonunu sağlar ve farklı Java platformlarında çalışan uygulamalar için iletişim özellikleri sunar.
IBM MQ için Java Arabirimleri
1. IBM MQ Sınıfları için Jakarta Messaging (Jakarta Messaging 3.0)
	• Jakarta Messaging sağlayıcısıdır ve IBM MQ, Jakarta Messaging arabirimlerini mesajlaşma sistemi olarak uygular.
	• Jakarta Connectors Architecture, Jakarta EE ortamında çalışan uygulamaları, IBM MQ gibi Kurumsal Bilgi Sistemlerine (EIS) bağlamak için standart bir yol sunar.
	• Bu API, Java 8 ve sonrasında desteklenen Jakarta Messaging 3.0 standardına uyumludur ve yeni özellikler ve basitleştirilmiş API sunar.
	• Jakarta Messaging gelecekteki gelişmeler için tercih edilen teknolojidir.
2. IBM MQ Sınıfları için JMS (JMS 2.0)
	• JMS (Java Message Service) sağlayıcısıdır ve IBM MQ, JMS arabirimlerini mesajlaşma sistemi olarak uygular.
	• Java Platform, Enterprise Edition Connector Architecture (JCA) kullanarak, Java EE ortamında çalışan uygulamaları, IBM MQ gibi Kurumsal Bilgi Sistemlerine bağlamak için bir yol sunar.
	• IBM MQ 8.0’dan itibaren JMS 2.0 standardı uygulanmaktadır. Ancak, JMS 2.0 teknolojisi yerini Jakarta Messaging’e bırakacaktır.
	• JMS 2.0 hala desteklenmektedir, ancak yeni Java mesajlaşma özellikleri Jakarta Messaging üzerinden gelişecektir.
	• IBM MQ sınıfları için JMS, yalnızca mevcut JMS 2.0 uygulamalarını desteklemek için önerilir. Yeni geliştirmeler için Jakarta Messaging tercih edilmelidir.
3. IBM MQ Sınıfları için Java
	• IBM MQ için Java sınıfları, Java ortamında IBM MQ’yu kullanmanıza olanak sağlar.
	• Java uygulamaları, IBM MQ’ya istemci olarak bağlanabilir veya doğrudan bir IBM MQ kuyruk yöneticisine bağlanabilir.
	• IBM MQ sınıfları için Java API'si IBM MQ 8.0'dan itibaren işlevsel olarak stabilize edilmiştir. Yeni özellikler eklenmeyecek ve yalnızca mevcut hatalar giderilecektir.
	• Bu API, IBM MQ 8.0 ile stabil hale gelmiştir ve gelecekte yeni özellik eklenmeyecek, mevcut özelliklere yönelik talepler reddedilecektir.
	• IBM MQ için Java sınıfları, yeni geliştirmeler için artık önerilmez; bunun yerine Jakarta Messaging API’si tercih edilmelidir.
JMS ve Jakarta Messaging
	• JMS 2.0 standardı, Jakarta Messaging tarafından aşılmıştır. Ancak, IBM MQ sınıfları için JMS, JMS 2.0 standardını desteklemeye devam etmektedir. Gelecekteki gelişmeler Jakarta Messaging API'sinde yer alacaktır.
	• IBM MQ sınıfları için Jakarta Messaging, JMS'in modernize edilmiş versiyonudur ve gelecekteki uygulamalar için tercih edilmesi gereken teknoloji olacaktır.
Desteklenen Platformlar ve Gereksinimler
	• Java 8 ve sonrasında çalışan Java çalışma ortamları, bu arabirimlerle çalışan uygulamalar için gereklidir. IBM MQ 9.3'ten itibaren, IBM MQ sınıfları için Java, JMS, ve Jakarta Messaging Java 8 ile inşa edilmiştir.
IBM MQ Mesajlaşma Sağlayıcı Modları
IBM MQ mesajlaşma sağlayıcıları üç çalışma moduna sahiptir:
	1. Normal Mod: Standart işleyiş şeklidir.
	2. Normal Mod ile Kısıtlamalar: Belirli kısıtlamalarla çalışan bir moddur.
	3. Geçiş Modu: Eski uygulamalardan yeni sürümlere geçiş yapmak için kullanılan mod.
Tercih Edilen Teknoloji
Yeni geliştirmeler için IBM MQ sınıfları için Jakarta Messaging kullanılması önerilir. Mevcut JMS 2.0 uygulamaları için ise IBM MQ sınıfları için JMS kullanılabilir.

****************


IBM MQ, Java uygulamaları için üç farklı uygulama programlama arayüzü (API) sunar: IBM MQ sınıfları Jakarta Messaging için, IBM MQ sınıfları JMS (Java Message Service) için ve IBM MQ sınıfları Java için.
	1. IBM MQ sınıfları Jakarta Messaging: IBM MQ, Jakarta Messaging 3.0'ı desteklemeye başlamıştır. Jakarta Messaging, Java'nın mesajlaşma standardıdır ve JMS'nin yerini alacak şekilde geliştirilmiştir. IBM MQ, Jakarta Messaging API'leri ile mesajlaşma sağlayan bir sağlayıcıdır.
	2. IBM MQ sınıfları JMS: JMS 2.0, IBM MQ tarafından desteklenen eski bir sürümdür. JMS API'leri, mesajları göndermek ve almak için kullanılan standart Java API'leridir. IBM MQ, JMS 2.0 standardını, daha basit bir kullanım için bazı geliştirmelerle sağlar.
	3. IBM MQ sınıfları Java: Bu sınıflar, IBM MQ'nun Java ortamında kullanılmasını sağlar. Java uygulamaları, IBM MQ ile iletişim kurarak, bir IBM MQ kuyruğuna bağlanabilir ve mesaj gönderip alabilir.
IBM MQ sınıfları JMS ve Jakarta Messaging, IBM MQ tarafından sağlanan iki ana mesajlaşma sağlayıcısıdır. Bu sağlayıcılar, Java SE (Standard Edition) ve Java EE (Enterprise Edition) uygulamaları için kullanılabilir. Her iki sağlayıcı da aynı temel işlevleri sunar, ancak Jakarta Messaging 3.0, JMS 2.0'ı daha modern ve basitleştirilmiş bir şekilde sunar.
JMS ve Jakarta Messaging modelinin özellikleri:
	• Her iki model de, Java uygulamalarının mesajlaşma işlemlerini gerçekleştirmesi için gerekli arayüzleri tanımlar.
	• IBM MQ sınıfları JMS, IBM MQ'nun JMS arayüzlerini sağlayarak, bir mesajlaşma sistemi olarak IBM MQ'yu kullanır.
	• IBM MQ, JMS ve Jakarta Messaging için bazı ek işlevsellikler sunar, bu da daha esnek bir kullanım sağlar.
Bu arayüzlerin, özellikle yeni geliştirmeler için IBM MQ sınıfları Jakarta Messaging'in tercih edilmesi önerilmektedir, çünkü JMS 2.0'ın gelecekteki güncellemeleri yalnızca Jakarta Messaging içinde yer alacaktır.
