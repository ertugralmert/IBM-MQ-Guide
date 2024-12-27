IBM MQ Yapılandırma ve Kullanımına Dair Detaylı Doküman
Bu doküman, IBM MQ'nun yapılandırma, özellikler ve detaylı kullanımı ile ilgili kapsamılı bir rehber sunar. IBM MQ'da kuyruğuzdan kanal tanımlarına kadar her adımı öğrenmek isteyenler için çok önemli bilgiler içermektedir.

Queue Manager Yapılandırma Dosyası (qm.ini)
Genel Bilgi
	• qm.ini dosyası, bir kuyruk yöneticisinin (“queue manager”) davranışını tanımlar.
	• Kuyruk yöneticisinin kurulumuyla birlikte otomatik olarak oluşturulur.
	• Özel parametreleri değiştirerek IBM MQ'nun çalışma biçimini değiştirebilirsiniz.
Dosya Konumları
	• Linux ve AIX: /var/mqm/qmgrs/<QueueManagerAdı>/qm.ini
	• Windows: C:\ProgramData\IBM\MQ\qmgrs\<QueueManagerAdı>\qm.ini
	• IBM i: /QIBM/UserData/mqm/qmgrs/<QueueManagerAdı>/qm.ini
Önemli Stanzalar ve Parametreler
1. Log Stanza
Kuyruk yöneticisinin loglama ayarlarını belirler.
Log:
  LogPrimaryFiles=3
  LogSecondaryFiles=2
  LogFilePages=4096
  LogType=CIRCULAR
  LogBufferPages=0
	• LogPrimaryFiles: Birincil log dosyası sayısı.
	• LogSecondaryFiles: Yedek log dosyası sayısı.
	• LogType: Loglama tipi (CIRCULAR veya LINEAR).
	• LogBufferPages: Log için ayrılan tampon boyutu.
2. Channels Stanza
Kanal (“channel”) yapılandırmasını tanımlar.
Channels:
  MaxChannels=100
  MaxActiveChannels=50
	• MaxChannels: Tanımlanabilecek maksimum kanal sayısı.
	• MaxActiveChannels: Aynı anda çalışabilecek maksimum kanal sayısı.
3. SSL Stanza
SSL/TLS protokolü ile ilgili ayarları belirler.
SSL:
  KeyRepository=/var/mqm/ssl
  SSLProtocol=TLSV12
	• KeyRepository: Anahtar deposunun bulunduğu dizin.
	• SSLProtocol: Kullanılacak SSL/TLS protokolü versiyonu.
4. ExitPath Stanza
Kullanıcı tanımlı program (“exit program”) yollarını tanımlar.
ExitPath:
  ExitsDefaultPath=/var/mqm/exits
  ExitsDefaultPath64=/var/mqm/exits64
5. TuningParameters Stanza
Performans optimizasyonu için kullanılır.
TuningParameters:
  MaxUncommittedMsgs=10000
	• MaxUncommittedMsgs: Bir işlemde işlenebilecek maksimum mesaj sayısı.
6. Security Stanza
Güvenlik ayarlarını yapılandırır.
Security:
  PermitStandby=YES
	• PermitStandby: Yedek kuyruk yöneticisinin izin verilip verilmediğini belirler.

Streaming Queues (Akış Kuyrukları) Yapılandırması
Streaming queue, bir kuyruğun mesajlarının kopyasını başka bir kuyruğa çoğaltmanıza olanak tanır. Bu, genellikle analiz veya yedekleme için kullanılır.
Parametreler
	1. STREAMQ
		○ Mesajların kopyalanacağı hedef kuyruğun adı.
	2. STRMQOS
		○ Hizmet kalitesini belirler.
		○ BESTEF: Mesajın kopyası başarısız olursa orijinal mesaj etkilenmez.
		○ MUSTDUP: Kopya oluşturulamazsa orijinal mesaj da işlenmez.
Örnek Tanımlar
Best Effort (BESTEF):
Orijinal mesaj işlenmeye devam eder.
DEFINE QLOCAL(ANALYTICS.QUEUE)
ALTER QLOCAL(ORDERS.QUEUE) STRMQOS(BESTEF) STREAMQ(ANALYTICS.QUEUE)
Must Duplicate (MUSTDUP):
Orijinal mesaj kopya oluşturulana kadar işlenmez.
DEFINE QLOCAL(AUDIT.QUEUE)
ALTER QLOCAL(PAYMENTS.QUEUE) STRMQOS(MUSTDUP) STREAMQ(AUDIT.QUEUE)
Dikkat Edilecek Noktalar
	• Streaming kuyruğunun maksimum derinliği (“max depth”), orijinal kuyruğun maksimum derinliğinden daha küçük olmamalıdır.
	• MUSTDUP ayarı yapılmış bir kuyruğta, hedef kuyruk oluşturulmamışsa işlem başarısız olur.

Distributed Queue Management (Dağıtılmış Kuyruk Yönetimi)
Birden fazla kuyruk yöneticisi arasında mesaj alışverişini sağlayan mekanizmadır.
Temel Kavramlar
1. Channels (Kanallar)
Kuyruk yöneticileri arasındaki bir yönlü (“one-way”) iletişim hattı.
	• SENDER: Mesaj gönderen kanal.
	• RECEIVER: Mesaj alan kanal.
2. Transmission Queue
Mesajların başka bir kuyruk yöneticisine gönderilmeden önce depolandığı kuyruktur.
3. Message Channel Agent (MCA)
Kanalın iki ucundaki mesaj gönderim ve alım programları.
Örnek Tanımlar
Sender Kanalı
DEFINE CHANNEL(SENDER.CHANNEL) CHLTYPE(SDR) TRPTYPE(TCP) CONNAME('192.168.1.10(1414)')
Receiver Kanalı
DEFINE CHANNEL(RECEIVER.CHANNEL) CHLTYPE(RCVR)
Transmission Queue
DEFINE QLOCAL('TRANSMISSION.QUEUE') USAGE(XMITQ)

Kanallar İçin Kimlik Doğrulama ve Yetkilendirme
Channel Authentication Records (CHLAUTH)
IBM MQ, kanal bağlantılarını kontrol etmek için CHLAUTH kayıtlarını kullanır.
Örnek Tanımlar
Belirli Bir IP Adresine İzin Verme
SET CHLAUTH('MY.CHANNEL') TYPE(ADDRESSMAP) ADDRESS('192.168.1.10') USERSRC(NOACCESS)
TLS Kullanarak Kimlik Doğrulama
SET CHLAUTH('TLS.CHANNEL') TYPE(SSLPEERMAP) SSLPEER('CN=mycert') USERSRC(MCAUSER) MCAUSER('appuser')

SSL/TLS Yapılandırması
Sertifika Yönetimi
Sertifikaları oluşturmak ve yönetmek için runmqakm komutu kullanılır.
Örnek Adımlar:
	1. Sertifika deposu oluşturun:
runmqakm -keydb -create -db key.kdb -pw password -type cms -stash
	2. Sertifika isteği oluşturun:
runmqakm -certreq -create -db key.kdb -pw password -label ibmmqcert -dn "CN=example.com" -file certreq.arm
	3. Sertifikayı içe aktarın:
runmqakm -cert -add -db key.kdb -pw password -label ibmmqcert -file cert.arm
	4. Kanala SSL yapılandırmasını ekleyin:
DEFINE CHANNEL(SSL.CHANNEL) CHLTYPE(SVRCONN) SSLCIPH(TLS_RSA_WITH_AES_128_CBC_SHA256) SSLPEER('CN=example.com')

