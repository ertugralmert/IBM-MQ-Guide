IBM MQ MQI (Message Queue Interface) istemcisi, IBM MQ ürününün bir bileşenidir ve bir sistemde çalıştığı zaman, o sistemde bir kuyruk yöneticisinin (queue manager) bulunmaz. Bu istemci, bir uygulamanın başka bir sistemdeki kuyruk yöneticisine MQI çağrıları yapmasına olanak tanır. Çıktılar, istemciye geri gönderilir ve istemci, bu çıktıyı uygulamaya iletir.
IBM MQ MQI İstemcisi ve Sunucu İletişimi
	• MQI Client: IBM MQ MQI istemcisi, istemci uygulamasının başka bir sistemdeki kuyruk yöneticisine bağlanmasını sağlar. Bu uygulama, MQI calls (Message Queue Interface çağrıları) yapabilir. Bu tür bir uygulama, IBM MQ MQI Client Application olarak adlandırılır.
	• Server Queue Manager: Bağlanılan kuyruk yöneticisine server queue manager denir. Kuyruklar ve diğer IBM MQ nesneleri, yalnızca kuyruk yöneticisinin bulunduğu makinede (IBM MQ sunucusu) mevcuttur.
Bir IBM MQ server (sunucu), bir veya daha fazla istemciye hizmet veren bir kuyruk yöneticisidir. Sunucu, her istemci ile iletişim sağlamak için özel bir iletişim bağlantısına sahiptir.
MQI Kanalı ve İletişim
	• MQI Channel: Bir MQI channel (MQI kanalı), istemci uygulaması bir MQCONN veya MQCONNX çağrısı yaparak kuyruk yöneticisine bağlandığında başlar. İstemci uygulaması MQDISC çağrısını yaparak bağlantıyı sonlandırır.
		○ MQCONN: Kuyruk yöneticisine bağlanmak için kullanılan çağrı.
		○ MQDISK: Bağlantıyı sonlandıran çağrı.
MQI İstemci Uygulamasının Bağlantısı
	• Platform Desteği: IBM MQ MQI istemcisi ve sunucusu, AIX, Linux, Windows, IBM i, ve z/OS gibi platformlarda çalışabilir.IBM MQ MQI Client ve IBM MQ Server'ın uyumlu çalışabileceği platformlar aşağıda sıralanmıştır:
		○ IBM MQ MQI Client: AIX, Linux, Windows, IBM i
		○ IBM MQ Server: AIX, Linux, Windows, IBM i, z/OS
	• Uygulama Geliştirme: IBM MQ uygulamanızı istemci-server ortamında çalışacak şekilde geliştirmek için, ilgili istemci kitaplıklarıyla uygulamanızı bağlantılandırmanız gerekir.
		○ MQCONN çağrısı, istemciyi belirtilen kuyruk yöneticisine bağlar.
		○ İstemci daha sonra MQI calls (mesaj kuyruğu arayüzü çağrıları) yaparak kuyruk yöneticisi ile etkileşime girer.
IBM MQ İstemcileri Kullanmanın Avantajları
IBM MQ istemcileri, mesajlaşma ve kuyruk yönetimini verimli bir şekilde gerçekleştirmenizi sağlar. Bu istemciler, mesaj kuyruğunun arkasındaki altyapıya doğrudan bağlanmadan mesaj iletmek için kullanılır.
Extended Transactional Client
Bir extended transactional client (genişletilmiş işlemsel istemci), harici bir işlem yöneticisi altında, başka bir kaynak yöneticisi tarafından yönetilen kaynakları güncelleyebilir.
Bağlantı Yöntemi
Bir istemci, MQCONN veya MQCONNX çağrısı kullanarak bir kuyruk yöneticisine bağlanır ve kanal üzerinden iletişim kurar.
Önemli Terimler:
	• MQI (Message Queue Interface): IBM MQ istemci uygulamalarının kuyruk yöneticileriyle iletişim kurmasını sağlayan arabirim.
	• MQCONN: Kuyruk yöneticisine bağlanmak için kullanılan çağrı.
	• MQCONNX: Bağlantı parametreleri ile kuyruk yöneticisine bağlanmayı sağlayan çağrı.
	• MQDISC: Kuyruk yöneticisinden bağlantıyı sonlandıran çağrı.
	• Server Queue Manager: Kuyrukları ve IBM MQ nesnelerini barındıran sunucu kuyruk yöneticisi.
	• Extended Transactional Client: Genişletilmiş işlemsel istemci, harici bir işlem yöneticisi ile kaynak güncelleme yapabilir.
