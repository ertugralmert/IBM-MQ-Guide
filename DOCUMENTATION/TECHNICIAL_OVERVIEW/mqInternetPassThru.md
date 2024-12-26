IBM MQ Internet Pass-Thru (MQIPT) - Türkçe Açıklama
IBM MQ Internet Pass-Thru (MQIPT), IBM MQ'nun isteğe bağlı bir bileşenidir ve uzak konumlar arasında internet üzerinden mesajlaşma çözümleri uygulamak için kullanılır. MQIPT, IBM MQ'yu destekleyen herhangi bir sürümle çalışabilir ve ayrı bir IBM MQ bileşeni kurmanıza gerek yoktur.
MQIPT, iki IBM MQ kuyruk yöneticisi arasında veya bir IBM MQ istemcisi ile bir kuyruk yöneticisi arasındaki mesaj akışlarını alıp yönlendiren bağımsız bir hizmet olarak çalışır. Bu, istemci ve sunucunun aynı fiziksel ağda olmadığı durumlarda bağlantı kurulmasını sağlar.
MQIPT Nasıl Çalışır?
MQIPT, bir TCP/IP portu üzerinden gelen bağlantıları dinler ve bu bağlantılara karşılık verir. Bu bağlantılar, normal IBM MQ mesajları, HTTP içindeki tünellenmiş IBM MQ mesajları veya TLS/SSL ile şifrelenmiş mesajlar olabilir. MQIPT, çoklu bağlantıları aynı anda yönetebilir.
En basit yapılandırmasında, MQIPT bir IBM MQ protokol yönlendiricisi gibi çalışır. Bağlantı isteklerini kabul eder ve bu bağlantıları iletir. MQIPT'nin ağ geçidinde bulunması, doğrudan bir TCP/IP bağlantısı kurulamayan durumlarda kullanışlıdır.
MQIPT'nin Temel Özellikleri:
	• Veri Depolama: MQIPT, ilettiği verileri hafızada tutar ve disk üzerinde sadece yapılandırma dosyasını okumak veya bağlantı günlüklerini yazmak için veri okuma/yazma işlemi yapar.
	• Mesaj Güvenliği: MQIPT, IBM MQ'nun mesaj teslimat güvenliğini sağlar, ancak veri depolamaz veya senkronize kontrol (syncpoint) prosedürüne katılmaz.
	• Bağlantı Yönlendirme: MQIPT, bir IBM MQ istemcisi ve hedef kuyruk yöneticisi arasındaki iletişimi yönlendirir. IBM MQ kanalı, MQIPT aracılığıyla bağlantı kurar ve hedef kuyruk yöneticisine ulaşır.
MQIPT'nin Kullanım Senaryoları:
	• Güvenli Bağlantı Kurma: Eğer iki sistem arasındaki doğrudan TCP/IP bağlantısı engellenmişse (örneğin, bir güvenlik duvarı nedeniyle), MQIPT kullanılarak güvenli bir iletişim sağlanabilir.
	• Uzaktan Bağlantılar: Uzak konumlardaki sistemler, MQIPT ile birbirleriyle güvenli bir şekilde iletişim kurabilirler.
Desteklenen Kanal Yapılandırmaları:
MQIPT, tüm IBM MQ kanal türlerini destekler, ancak yapılandırma yalnızca TCP/IP bağlantılarıyla sınırlıdır. MQIPT, hedef kuyruk yöneticisi gibi görünür, bu nedenle kanal yapılandırması gerektiğinde, MQIPT'nin ana bilgisayar adı ve dinleyici portu belirtilir.
Yüksek Erişilebilirlik ve Multi-Instance Kuyruk Yöneticileri:
MQIPT, çoklu örnek kuyruk yöneticileri ve yüksek erişilebilirlik ortamlarıyla da kullanılabilir. Bu özellik, sistem arızaları durumunda bile kesintisiz dosya aktarımı ve iletişim sağlar.
Mesaj Güvenliği ve Dağıtık Kuyruk Yönetimi:
IBM MQ, dağılmış kuyruk yönetimi ile mesajların doğru şekilde teslim edilmesini garanti eder. MQIPT bu süreçte yalnızca mesaj iletimini sağlar ve mesaj verisini depolamaz veya teslimatın doğruluğuna müdahale etmez.
MQIPT'nin Başlıca Kullanım Alanları:
	1. İki IBM MQ kuyruğu yöneticisi arasındaki bağlantıları yönlendirme.
	2. İstemci ve kuyruk yöneticisi arasındaki bağlantı kurma.
	3. Ağ geçidi olarak çalışarak TCP/IP bağlantıları sağlayarak IBM MQ istemcileri ve kuyruk yöneticileri arasında güvenli iletişim sağlama.
MQIPT, IBM MQ'nun özelliklerinden yararlanarak bağlantıların güvenli ve verimli bir şekilde yapılmasını sağlar. Herhangi bir ağ kesintisi veya engel durumunda bile mesajların doğru ve güvenli bir şekilde iletilmesi mümkün hale gelir.
