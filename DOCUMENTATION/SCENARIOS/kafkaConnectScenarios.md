BM MQ ve Apache Kafka'nın farklı alanlarda uzmanlaşan iki mesajlaşma teknolojisi olduğu için, aralarındaki veri akışını sağlamak sıklıkla gereklidir. Bu, Kafka Connect kullanılarak yapılabilir. Kafka Connect, veri akışını sağlamak için dış bir sistemle Kafka kümesi arasında veri taşıyan bir çerçevedir ve çeşitli bağlantılar kullanır.
IBM MQ ile Kafka arasında veri akışı sağlamak için kullanılan Kafka Connect'in iki türü vardır:
	1. Source Connectors: Dış bir sistemden Kafka'ya veri aktarır.
		○ IBM MQ Source Connector: IBM MQ kuyruğundan mesajları alır ve bunları Kafka konularına (topics) aktarır.
	2. Sink Connectors: Kafka'dan dış bir sisteme veri aktarır.
		○ IBM MQ Sink Connector: Kafka konularından veri alır ve bunları IBM MQ kuyruğuna iletir.
Kafka Connect Senaryoları
	• Core Bankacılık Sistemi: IBM MQ kullanılarak, banka işlemlerinin başarıyla tamamlanmasının ardından verilerin Kafka'ya aktarılması sağlanabilir.
	• Veri Analizi için MQ'dan Kafka'ya Veri Akışı: IBM MQ üzerinden hareket eden verilerin bir kopyasının Kafka'ya aktarılması gerekebilir, özellikle analiz amaçlı.
	• z/OS Entegrasyonu: Kafka ve z/OS sistemleri arasındaki veri akışını yönetmek, örneğin IBM MQ entegrasyonuyla.
MQ ile Kafka'nın Entegrasyonu İçin Topolojiler
	1. Direct to Queue (Source):
		○ Uygulamalar verilerini doğrudan Kafka'ya göndermek için IBM MQ kullanabilir. Bu durumda, veriler zaten IBM MQ'ya gönderilmektedir, bu nedenle Kafka'ya bağlantı kurmak yerine mevcut bir IBM MQ bağlantısı kullanılabilir.
	2. Streaming Queue Copy (Source):
		○ IBM MQ'ya gelen verilerin bir kopyasını Kafka'ya iletmek için Streaming Queue özelliği kullanılabilir. Bu, verinin bir kuyruğa yazılmasını sağlar ve aynı mesaj başka bir kuyruğa kopyalanır, bu da Kafka'ya veri akışını sağlar.
	3. Direct to Queue (Sink):
		○ Kafka'dan gelen verileri doğrudan IBM MQ kuyruğuna almak için sink connector kullanılabilir. Bu, Kafka'dan gelen verilerin, örneğin bir veritabanı güncellemesi gibi işlemlerle eş zamanlı olarak IBM MQ'ya gönderilmesini sağlar.
IBM MQ Kafka Connectors
IBM MQ 9.4.0'dan itibaren, IBM MQ Advanced, IBM MQ Advanced for z/OS ve IBM MQ Advanced for Multiplatforms ile bu bağlantılar kullanılabilir. Connectors, Kafka Connect ortamına dahil edilen çeşitli dosyalarla birlikte gelir ve yapılandırmalar, JSON veya properties dosyalarıyla yapılır.
	• IBM MQ Source Connector: IBM MQ kuyruğundan Kafka'ya veri aktaran bağlantıdır.
	• IBM MQ Sink Connector: Kafka'dan IBM MQ'ya veri aktarır.
Version 2 Connector Özellikleri
Version 2 connectors, exactly-once ve at-least-once mesaj teslimatı desteği sağlar:
	• At-least-once: Bir hata durumunda, mesajlar kaybolmaz ancak Kafka'ya birden fazla kez iletilir.
	• Exactly-once: Mesajlar yalnızca bir kez iletilir, hata durumunda tekrar gönderilmez.
Kafka Connectors ve Dosya Yapısı
Kafka Connect çalıştırılmadan önce aşağıdaki dosyaların classpath'te bulunması gerekir:
	• jms.jar
	• com.ibm.mq.allclient.jar
	• org.json.jar
	• bcpkix-jdk18on.jar
	• bcprov-jdk18on.jar
	• bcutil-jdk18on.jar
	• jackson-annotations.jar
	• jackson-core.jar
	• jackson-databind.jar
	• slf4j-api.jar (Maven üzerinden temin edilebilir)
z/OS ve IBM MQ
IBM MQ Connectors, z/OS üzerinde de çalıştırılabilir. z/OS UNIX System Services (USS) kullanarak performans iyileştirmeleri sağlanabilir ve yerel bağlantılarla kuyruğa bağlanma tercih edilebilir.
Sonuç
IBM MQ ile Apache Kafka arasındaki veri akışını yönetmek için Kafka Connect kullanabilirsiniz. Source ve Sink connector’ları ile MQ’dan Kafka’ya veya Kafka’dan MQ’ya veri aktarımı sağlayabilirsiniz. Kafka Connect'in sağladığı exactly-once teslimat desteği, kritik uygulamalarda veri doğruluğunu sağlar.
