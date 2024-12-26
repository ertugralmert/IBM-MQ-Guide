
Publish/Subscribe Senaryoları ve Yapılandırmaları
IBM MQ'da publish/subscribe (yayınla/abone ol) modeli, uygulamaların mesajları yayınlamasına (publish) ve bu mesajlara abone olan diğer uygulamalara iletmesine olanak tanır. Bu senaryolarda, farklı publish/subscribe kümeleri ve hierarşiler oluşturularak farklı yapılandırma yöntemleri kullanılır. Aşağıda, üç farklı publish/subscribe senaryosu ve her biri için nasıl yapılandırılacağını açıklamaktadır:

Senaryo: Publish/Subscribe Kümesi Oluşturma
Bu senaryoda, publish/subscribe (yayınla/abone ol) kümesi oluşturulur. Küme, üç farklı queue manager içerir ve bu kümeyi, bir queue manager üzerinden abone olanların, başka bir queue manager üzerinden yayınlanan mesajları alabilmesini sağlayacak şekilde yapılandırır.
Başlangıç İçin Gereksinimler
	• IBM MQ'nun kurulu olması gerekir. Eğer kurulum yapılmadıysa, IBM MQ kurulumu için IBM MQ Server kurulum yönergelerine bakılabilir.
Yapılandırma Adımları
	1. Queue Manager'ları Oluşturun ve Başlatın:
		○ Üç farklı queue manager oluşturulacaktır: PS1, PS2, ve PS3.Komutlar:crtmqm PS1strmqm PS1crtmqm PS2strmqm PS2crtmqm PS3strmqm PS3
	2. İlk Queue Manager'ın Yapılandırılması (PS1):
		○ PS1, küme için tam bir depo (full repository) olarak yapılandırılacaktır.
		○ Listener ve receiver channel tanımlanacak ve PS1, PS2 ile bilgi alışverişi yapmak için sender channel kurulacaktır.Komutlar:
		○ DEFINE LISTENER(PS1_LS) TRPTYPE(TCP) CONTROL(QMGR) PORT(5000)START LISTENER(PS1_LS)ALTER QMGR REPOS(DEMO)DEFINE CHANNEL(DEMO.PS1) CHLTYPE(CLUSRCVR) TRPTYPE(TCP) CONNAME('localhost(5000)') CLUSTER(DEMO)DEFINE CHANNEL(DEMO.PS2) CHLTYPE(CLUSSDR) TRPTYPE(TCP) CONNAME('localhost(5001)') CLUSTER(DEMO)
	3. İkinci Queue Manager'ın Yapılandırılması (PS2):
		○ PS2, küme için başka bir tam depo olarak yapılandırılır.
		○ Listener ve receiver channel tanımlanır. Ayrıca, PS1 ile bilgi alışverişi yapabilmesi için sender channel oluşturulur.Komutlar:DEFINE LISTENER(PS2_LS) TRPTYPE(TCP) CONTROL(QMGR) PORT(5001)START LISTENER(PS2_LS)ALTER QMGR REPOS(DEMO)DEFINE CHANNEL(DEMO.PS2) CHLTYPE(CLUSRCVR) TRPTYPE(TCP) CONNAME('localhost(5001)') CLUSTER(DEMO)DEFINE CHANNEL(DEMO.PS1) CHLTYPE(CLUSSDR) TRPTYPE(TCP) CONNAME('localhost(5000)') CLUSTER(DEMO)
	4. Üçüncü Queue Manager'ın Yapılandırılması (PS3):
		○ PS3, bir kısmi depo (partial repository) olarak yapılandırılır ve diğer full repository queue manager'lar ile iletişim kurar.
		○ Listener ve receiver channel tanımlanır. PS1 veya PS2 ile iletişim kurabilmesi için sender channel oluşturulur.Komutlar:DEFINE LISTENER(PS3_LS) TRPTYPE(TCP) CONTROL(QMGR) PORT(5002)START LISTENER(PS3_LS)DEFINE CHANNEL(DEMO.PS3) CHLTYPE(CLUSRCVR) TRPTYPE(TCP) CONNAME('localhost(5002)') CLUSTER(DEMO)DEFINE CHANNEL(DEMO.PS1) CHLTYPE(CLUSSDR) TRPTYPE(TCP) CONNAME('localhost(5000)') CLUSTER(DEMO)
	5. Cluster Konfigürasyonu:
		○ PS1, PS2, ve PS3 queue manager'lar küme (cluster) üyeleri olarak tanımlanacak.
		○ Küme konusu (cluster topic) oluşturulacak ve küme, bir publish/subscribe kümesine dönüştürülecek.Komutlar:DEFINE TOPIC(SCORES) TOPICSTR('/Sport/Scores') CLUSTER(DEMO) CLROUTE(DIRECT)
	6. Yayınlama ve Abonelik Testi:
		○ amqspub ve amqssub komutlarını kullanarak farklı queue manager'lar üzerinden bir konuya (topic) yayın yapılacak ve abonelik test edilecektir.Komutlar:amqspub /Sport/Scores/Football PS1amqssub /Sport/Scores/Football PS2amqssub /Sport/Scores/Football PS3

Publish/Subscribe Hierarşisi Senaryoları
Publish/subscribe hierarşisi, mesajların farklı queue manager'lar arasında daha organize ve hiyerarşik bir yapıyla dağıtılmasını sağlar. Bu senaryolarda, üç farklı yaklaşım kullanarak queue manager'lar arası bağlantılar kurulmaktadır.
Senaryo 1: Queue Manager Adı Alias'ı ile Point-to-Point Kanallar Kullanarak
Bu senaryoda, QM1 ana queue manager'ı, QM2 ve QM3 ise alt queue manager'lardır. Bağlantılar point-to-point kanallar üzerinden yapılır ve queue manager adı alias kullanılarak bağlanır.
Adımlar:
	1. Queue Manager'ları Oluşturun ve Başlatın:
		○ QM1, QM2 ve QM3 için aşağıdaki komutlar kullanılacaktır.crtmqm QM1strmqm QM1crtmqm QM2strmqm QM2crtmqm QM3strmqm QM3
	2. Queue Manager'ların Yapılandırılması:
		○ Her bir queue manager için listener ve channel'lar oluşturulacak.
	3. Bağlantıların Kurulması:
		○ Point-to-point kanalları ile QM1 ile QM2, QM3 arasındaki bağlantılar kurularak iletişim sağlanacak.
	4. Topic Oluşturulması ve Test:
		○ QM2 ve QM3 abone olacak, ve QM1'den yayınlanan mesajlar her iki queue manager'da da alınıp test edilecek.

Bu şekilde, publish/subscribe yapısını kurarak mesajlar arasında iletişim sağlanabilir ve kümeler arasında veri iletimi düzenli bir şekilde yapılabilir.
