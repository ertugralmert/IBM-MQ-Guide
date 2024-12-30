IBM MQ Ubuntu Kurulum Dokümantasyonu
Bu doküman, IBM MQ'yu Ubuntu üzerinde konfigüre etmek ve bir Windows sunucu kuyruk yöneticisi ile iletişim kurmak için yapılanı açıklamaktadır.

Başlangıç Kurulumu ve Yükleme
	1. Gerekli Paketlerin Yüklenmesi:
		○ IBM MQ için gerekli .deb dosyalarını yükleyin:
sudo dpkg -i ibmmq-runtime_9.4.0.0_amd64.deb ibmmq-server_9.4.0.0_amd64.deb ibmmq-samples_9.4.0.0_amd64.deb ibmmq-java_9.4.0.0_amd64.deb
			§ ibmmq-runtime: MQ'nun temel çalışma ortamı.
			§ ibmmq-server: Sunucu tarafı bileşenler.
			§ ibmmq-samples: Test için örnek uygulamalar.
			§ ibmmq-java: Java tabanlı MQ bileşenleri.
	2. Kurulumu Doğrulama:
		○ MQ'nun doğru yüklenip yüklenmediğini kontrol edin:
dspmqver
	3. IBM MQ Dizininin PATH'e Eklenmesi:
		○ MQ binary'lerini çalıştırabilmek için PATH değişkenini güncelleyin:
export PATH=$PATH:/opt/mqm/bin:/opt/mqm/samp/bin
	4. Kullanıcı Ortamını Ayarlama:
		○ mqm kullanıcısına geçiş yapın:
sudo su - mqm
		○ (Opsiyonel) PATH'i otomatik ayarlamak için mqm için bir .bashrc dosyası ekleyin:
echo 'export PATH=$PATH:/opt/mqm/bin:/opt/mqm/samp/bin' >> ~/.bashrc
source ~/.bashrc

Kuyruk Yöneticisi ve Yapılandırma
	1. Kuyruk Yöneticisi Oluşturma:
		○ QM3 adında bir kuyruk yöneticisi oluşturun:
crtmqm QM3
		○ Kuyruk yöneticisini başlatın:
strmqm QM3
	2. Dinleyici Tanımlama:
		○ Port 1415 üzerinden iletişimi etkinleştirmek için bir dinleyici oluşturun ve başlatın:
runmqsc QM3
DEFINE LISTENER('UBUNTU.LISTENER') TRPTYPE(TCP) PORT(1415)
START LISTENER('UBUNTU.LISTENER')
	3. İleti Kuyruğu Tanımlama:
		○ Mesajları Windows'a iletmek için bir iletim kuyruğu tanımlayın:
DEFINE QLOCAL('WINDOWS.TRANSMIT.QUEUE') USAGE(XMITQ)
	4. Sender Kanalı Oluşturma:
		○ Mesajları Windows'a göndermek için bir gönderici kanal tanımlayın:
DEFINE CHANNEL('UBUNTU.TO.WINDOWS') CHLTYPE(SDR) TRPTYPE(TCP) CONNAME('192.168.142.129(1414)') XMITQ('WINDOWS.TRANSMIT.QUEUE')
		○ Sender kanalını başlatın:
START CHANNEL('UBUNTU.TO.WINDOWS')
	5. Uzak Kuyruk Tanımlama:
		○ Windows kuyruk yöneticisine işaret eden bir uzak kuyruk tanımlayın:
DEFINE QREMOTE('TEST.REMOTE') RNAME('WINDOWS.TEST.LOCAL') RQMNAME('QM1') XMITQ('WINDOWS.TRANSMIT.QUEUE')

Windows Kuyruk Yöneticisi Konfigürasyonu
	1. Windows Kuyruk Yöneticisi (QM1) Ayarı:
		○ Ubuntu'dan mesaj almak için bir alıcı kanal tanımlayın:
DEFINE CHANNEL('UBUNTU.TO.WINDOWS') CHLTYPE(RCVR) TRPTYPE(TCP)
	2. Ubuntu Mesajları İçin Yerel Kuyruk Tanımlama:
		○ Ubuntu'dan gelen mesajları saklamak için WINDOWS.TEST.LOCAL kuyruğunu oluşturun:
DEFINE QLOCAL('WINDOWS.TEST.LOCAL') DEFPSIST(YES)
	3. Kanal Kimlik Doğrulama Güncellemesi:
		○ Ubuntu'nun IP adresinden iletişime izin verin:
SET CHLAUTH('UBUNTU.TO.WINDOWS') TYPE(ADDRESSMAP) ADDRESS('192.168.142.130') MCAUSER('mqm') ACTION(ADD)
	4. Firewall Ayarı:
		○ Hem Windows hem de Ubuntu'da 1415 portunun inbound ve outbound trafiğe izin verdiğinden emin olun:
netsh advfirewall firewall add rule name="MQ 1415" dir=in action=allow protocol=TCP localport=1415

İletişimi Test Etme
	1. Ubuntu'dan Test Mesajı Gönderme:
		○ Bir mesaj göndermek için amqsput örnek uygulamasını kullanın:
amqsput TEST.REMOTE QM3
		○ Test mesajı girin, örneğin, Hello from Ubuntu.
	2. Windows'da Mesajı Doğrulama:
		○ Mesajı almak için amqsget örnek uygulamasını kullanın:
amqsget WINDOWS.TEST.LOCAL QM1
		○ Alternatif olarak, MQSC komutlarıyla kuyruk derinliğini kontrol edin:
DISPLAY QLOCAL('WINDOWS.TEST.LOCAL') CURDEPTH

Neden CHLAUTH'da MAP Kullandık?
	• MAP (Kanal Kimlik Doğrulama): Belirtilen IP adresinin (192.168.142.130) alıcı kanala (UBUNTU.TO.WINDOWS) erişmesine izin verir.
	• MCAUSER: Doğrulanan bağlantıyı uygun izinlere sahip mqm kullanıcısına atar.
Sebep: Kanal kimlik doğrulama, yalnızca geçerli istemcilerin kuyruk yöneticisine bağlanmasını sağlamak için ek bir güvenlik katmanı sağlar.

Oluşturulan Nesnelerin Özeti
Ubuntu (QM3):
	1. Dinleyici: 1415 portunda UBUNTU.LISTENER.
	2. İleti Kuyruğu: WINDOWS.TRANSMIT.QUEUE.
	3. Sender Kanalı: UBUNTU.TO.WINDOWS.
	4. Uzak Kuyruk: TEST.REMOTE, WINDOWS.TEST.LOCAL'e işaret eder.
Windows (QM1):
	1. Alıcı Kanal: UBUNTU.TO.WINDOWS.
	2. Yerel Kuyruk: WINDOWS.TEST.LOCAL.
	3. Kanal Kimlik Doğrulama Kuralı: Ubuntu'nun IP adresi (192.168.142.130) kanala erişim sağlar.



IBM MQ Ubuntu Kurulum ve Kullanım Kılavuzu
Bu doküman, IBM MQ'nun Ubuntu üzerinde nasıl kurulacağını ve Windows sunucusu ile iletişim kuracak şekilde nasıl yapılandırılacağını açıklamaktadır. 
Başlangıç Kurulumu ve Yapılandırma
	1. Gerekli Paketlerin Yüklenmesi:
		○ IBM MQ için gerekli .deb dosyalarını yükleyin:
sudo dpkg -i ibmmq-runtime_9.4.0.0_amd64.deb ibmmq-server_9.4.0.0_amd64.deb ibmmq-samples_9.4.0.0_amd64.deb ibmmq-java_9.4.0.0_amd64.deb
			§ ibmmq-runtime: MQ'nun temel çalışma zamanı bileşenleri.
			§ ibmmq-server: Sunucu tarafı bileşenler.
			§ ibmmq-samples: Test için örnek uygulamalar.
			§ ibmmq-java: Java tabanlı MQ bileşenleri.
	2. Kurulumu Doğrulama:
		○ MQ'nun doğru yüklendiğini kontrol etmek için sürüm bilgisini görüntüleyin:
dspmqver
	3. IBM MQ Dizinlerini PATH'e Ekleme:
		○ MQ komutlarını her seferinde tam yol yazmadan çalıştırabilmek için PATH değişkenine MQ dizinlerini ekleyin:
export PATH=$PATH:/opt/mqm/bin:/opt/mqm/samp/bin
	4. Kullanıcı Ortamını Yapılandırma:
		○ mqm kullanıcısına geçiş yapın:
sudo su - mqm
		○ (Opsiyonel) mqm için .bashrc dosyasına PATH ayarlarını ekleyin:
echo 'export PATH=$PATH:/opt/mqm/bin:/opt/mqm/samp/bin' >> ~/.bashrc
source ~/.bashrc

Queue Manager ve Yapılandırmaların Oluşturulması
	1. Queue Manager Oluşturma:
		○ QM3 adlı bir Queue Manager oluşturun:
crtmqm QM3
		○ Queue Manager'ı başlatın:
strmqm QM3
	2. Listener Tanımlama:
		○ QM3 için bir listener oluşturun ve 1415 portunda iletişim sağlayacak şekilde başlatın:
runmqsc QM3
DEFINE LISTENER('UBUNTU.LISTENER') TRPTYPE(TCP) PORT(1415)
START LISTENER('UBUNTU.LISTENER')
	3. Transmission Queue Tanımlama:
		○ Mesajları Windows'a iletmek için bir transmission queue oluşturun:
DEFINE QLOCAL('WINDOWS.TRANSMIT.QUEUE') USAGE(XMITQ)
	4. Sender Kanalı Oluşturma:
		○ Mesajları Windows'a göndermek için bir sender kanalı tanımlayın:
DEFINE CHANNEL('UBUNTU.TO.WINDOWS') CHLTYPE(SDR) TRPTYPE(TCP) CONNAME('192.168.142.129(1414)') XMITQ('WINDOWS.TRANSMIT.QUEUE')
		○ Sender kanalını başlatın:
START CHANNEL('UBUNTU.TO.WINDOWS')
	5. Remote Queue Tanımlama:
		○ Windows queue manager'ına yönlendirme yapmak için bir remote queue oluşturun:
DEFINE QREMOTE('TEST.REMOTE') RNAME('WINDOWS.TEST.LOCAL') RQMNAME('QM1') XMITQ('WINDOWS.TRANSMIT.QUEUE')

Windows Queue Manager Yapılandırması
	1. Queue Manager Yapılandırması (QM1):
		○ Ubuntu'dan gelen mesajları almak için bir receiver kanalı tanımlayın:
DEFINE CHANNEL('UBUNTU.TO.WINDOWS') CHLTYPE(RCVR) TRPTYPE(TCP)
	2. Local Queue Tanımlama:
		○ Ubuntu'dan gelen mesajların kaydedileceği WINDOWS.TEST.LOCAL kuyruğunu oluşturun:
DEFINE QLOCAL('WINDOWS.TEST.LOCAL') DEFPSIST(YES)
	3. Channel Authentication Güncellemesi:
		○ Ubuntu'nun IP adresini izinli hale getirin:
SET CHLAUTH('UBUNTU.TO.WINDOWS') TYPE(ADDRESSMAP) ADDRESS('192.168.142.130') MCAUSER('mqm') ACTION(ADD)
	4. Firewall Ayarları:
		○ Hem Ubuntu hem de Windows üzerinde ilgili portları (1414 ve 1415) açın:
netsh advfirewall firewall add rule name="MQ 1415" dir=in action=allow protocol=TCP localport=1415

Yapılan İşlemlerin Mantığı
Queue ve Kanal Yapıları
	1. Transmission Queue:
		○ Mesajların başka bir queue manager'a iletilmesi için kullanılır.
		○ Örneğin, Ubuntu'dan Windows'a mesaj iletimi için WINDOWS.TRANSMIT.QUEUE tanımlandı.
	2. Remote Queue:
		○ Mesajın hangi queue'ya ve queue manager'a yönlendirileceğini belirler.
		○ Örneğin, TEST.REMOTE kuyruğu, mesajları WINDOWS.TEST.LOCAL kuyruğuna iletir.
	3. Sender ve Receiver Kanalları:
		○ Sender Kanalı (SDR): Mesajları karşı tarafa göndermek için kullanılır.
		○ Receiver Kanalı (RCVR): Gelen mesajları almak için kullanılır.
Komutların Mantığı
	• DEFINE: Yeni bir obje (queue, channel, vb.) tanımlamak için kullanılır.
	• DISPLAY: Mevcut objelerin durumunu görmek için kullanılır.
	• ALTER: Mevcut bir objenin yapılandırmasını değiştirmek için kullanılır.
	• DELETE: Bir objeyi silmek için kullanılır.
	• START/STOP: Kanalları veya listener'ları başlatmak/durdurmak için kullanılır.
Logları Analiz Etme
	• Queue Depth (CURDEPTH): Bir kuyruğun derinliğini kontrol ederek mesajların işlenip işlenmediğini anlayabilirsiniz.
	• Channel Status: Kanalların durumu (RUNNING, RETRYING, vb.) ile bağlantı problemleri tespit edilir.
	• Error Logs: /var/mqm/errors veya /opt/mqm/errors dizinlerinde hata kayıtları bulunur.

Gelişmiş ve Alternatif Yükleme Seçenekleri
	• Advanced Server:
		○ Tüm bileşenleri içerir, örneğin MFT veya AMS gibi.
		○ Daha büyük yapılar için uygundur.
	• Basic Server:
		○ Sadece temel mesajlaşma özelliklerini içerir.
		○ Küçük ölçekli kurulumlar için idealdir.



1. Komutların Mantığı ve Kullanımı
Temel Mantık:
IBM MQ'da tüm konfigürasyonlar Queue Manager, Queue, Channel, ve Listener gibi nesneler üzerinden gerçekleştirilir. Her bir komut bu nesnelerin oluşturulması, değiştirilmesi veya yönetilmesi için kullanılır. Komutların temel mantığını anlamak için şu yapıyı bilmeliyiz:
	1. Queue Manager (QMGR):
		○ MQ ekosisteminin temel yapı taşıdır. Tüm işlemler QMGR üzerinden yönetilir.
		○ Örnek:

crtmqm QM1
strmqm QM1
	2. Listener:
		○ Queue Manager’ın dış dünyadan gelen bağlantıları dinlediği bir ağ noktasıdır. Örneğin, PORT değiştirildiğinde şu şekilde tanımlanır:

DEFINE LISTENER('MY.LISTENER') TRPTYPE(TCP) PORT(1415)
ALTER LISTENER('MY.LISTENER') PORT(1416)
START LISTENER('MY.LISTENER')
	3. Channel:
		○ Queue Manager’lar arasında mesajların iletilmesini sağlar.
		○ Sender Channel (SDR): Mesajları gönderir.
		○ Receiver Channel (RCVR): Mesajları alır.
		○ Örnek:

DEFINE CHANNEL('MY.SENDER') CHLTYPE(SDR) TRPTYPE(TCP) CONNAME('192.168.0.1(1414)')
ALTER CHANNEL('MY.SENDER') CONNAME('192.168.0.2(1415)')
	4. Queue:
		○ Mesajların tutulduğu veri yapılandırmalarıdır.
		○ Local Queue: Mesajları depolar.
		○ Remote Queue: Mesajları başka bir Queue Manager’a iletir.
		○ Alias Queue: Queue için bir takma isim oluşturur.
		○ Transmission Queue: Remote Queue için mesajları iletir.
		○ Örnek:

DEFINE QLOCAL('MY.QUEUE') MAXDEPTH(5000)
DEFINE QREMOTE('REMOTE.QUEUE') RNAME('MY.REMOTE') RQMNAME('QM2') XMITQ('MY.TRANSMIT')

2. Değişiklik veya Ayar Yapma
Channel Adını Değiştirme:
MQSC komutlarıyla kanal adı doğrudan değiştirilemez. Ancak yeni bir kanal tanımlayıp eskisini silebilirsiniz:

DEFINE CHANNEL('NEW.CHANNEL') CHLTYPE(SDR) TRPTYPE(TCP) CONNAME('192.168.0.1(1414)') XMITQ('MY.TRANSMIT')
DELETE CHANNEL('OLD.CHANNEL')
Listener Portunu Değiştirme:

ALTER LISTENER('MY.LISTENER') PORT(1416)
STOP LISTENER('MY.LISTENER')
START LISTENER('MY.LISTENER')

3. Queue Türleri ve Kullanımları
Local Queue:
	• Mesajların depolandığı ve alındığı temel yapı.
	• Örnek:

DEFINE QLOCAL('LOCAL.QUEUE') MAXDEPTH(5000)
Remote Queue:
	• Mesajları başka bir Queue Manager’a iletir.
	• Örnek:

DEFINE QREMOTE('REMOTE.QUEUE') RNAME('WINDOWS.TEST.LOCAL') RQMNAME('QM1') XMITQ('WINDOWS.TRANSMIT.QUEUE')
Transmission Queue:
	• Remote Queue için mesajları taşır.
	• Örnek:

DEFINE QLOCAL('TRANSMIT.QUEUE') USAGE(XMITQ)

4. Log Analizi ve Hata Çözümleri
Loglar Nerede Bulunur?
	• Ubuntu: /var/mqm/errors/
	• Windows: C:\Program Files\IBM\MQ\errors\
Örnek Hata ve Çözüm:
	1. AMQ9208E: Connection Error:
		○ Nedeni: Listener çalışmıyor veya port engellenmiş.
		○ Çözüm:

DISPLAY LISTENER('MY.LISTENER') ALL
START LISTENER('MY.LISTENER')
	2. AMQ4036E: Authorization Error:
		○ Nedeni: CHLAUTH eksik veya MCAUSER doğru yapılandırılmamış.
		○ Çözüm:

SET CHLAUTH('MY.CHANNEL') TYPE(ADDRESSMAP) ADDRESS('192.168.0.1') MCAUSER('mqm') ACTION(ADD)

5. Advanced ve Server Yükleme Farkı
Advanced:
	• Ek olarak yüksek güvenlik özellikleri (MQ AMS), telemetri ve büyük sistem entegrasyonları içerir.
Gereksiz Paketleri Kaldırma:

sudo apt remove ibmmq-ams ibmmq-ftbase

6. Update ve Bakım
Update İşlemleri:

sudo dpkg -i ibmmq-runtime_9.4.0.1_amd64.deb
sudo systemctl restart mq

7. Grafana ile İzleme
IBM MQ Grafana entegrasyonu için Prometheus Exporter kullanılır. Veriler MQ’dan çekilir ve görselleştirilir.
Adımlar:
	1. Prometheus Exporter kurun.
	2. Grafana’da Prometheus veri kaynağını ekleyin.
	3. MQ metriklerini görüntülemek için hazır panelleri kullanın.

Özet
	1. Gönderici Tarafı:
		○ Queue Manager, Sender Channel, Transmission Queue, ve Remote Queue oluşturulur.
	2. Alıcı Tarafı:
		○ Receiver Channel ve Local Queue oluşturulur.


1. Temel Terimlerin Açıklamaları
MAXDEPTH (Maximum Depth)
	• Tanım: Bir kuyrukta aynı anda tutulabilecek maksimum mesaj sayısını belirler.
	• Örnek Kullanım:

DEFINE QLOCAL('MY.QUEUE') MAXDEPTH(5000)
	• Anlamı: MY.QUEUE adlı kuyruğun maksimum 5000 mesaj tutmasına izin verilir.
	• Not: Eğer CURDEPTH (current depth) MAXDEPTH’i aşarsa, kuyruk dolu hatası (MQRC_Q_FULL) alınır.

RQMNAME (Remote Queue Manager Name)
	• Tanım: Bir Remote Queue (uzak kuyruk) tanımlarken, mesajların gönderileceği hedef Queue Manager’ın adını belirtir.
	• Örnek Kullanım:

DEFINE QREMOTE('REMOTE.QUEUE') RNAME('TARGET.QUEUE') RQMNAME('QM2') XMITQ('TRANSMIT.QUEUE')
	• Anlamı: Mesajlar TRANSMIT.QUEUE üzerinden QM2 adlı Queue Manager’a gönderilir ve TARGET.QUEUE'ya iletilir.

XMITQ (Transmission Queue)
	• Tanım: Remote Queue aracılığıyla gönderilen mesajları taşıyan özel bir Local Queue türüdür.
	• Örnek Kullanım:

DEFINE QLOCAL('TRANSMIT.QUEUE') USAGE(XMITQ)
	• Anlamı: TRANSMIT.QUEUE, başka bir Queue Manager’a iletilecek mesajları geçici olarak depolar.

CHLAUTH (Channel Authentication Records)
	• Tanım: Güvenlik politikaları tanımlamak için kullanılan bir mekanizmadır. Hangi IP adreslerinin, kullanıcıların veya sertifikaların bir kanala bağlanabileceğini belirler.
	• Örnek Kullanım:

SET CHLAUTH('MY.CHANNEL') TYPE(ADDRESSMAP) ADDRESS('192.168.1.1') MCAUSER('mqm') ACTION(ADD)
	• Anlamı: MY.CHANNEL adlı kanala yalnızca 192.168.1.1 IP adresinden bağlanmaya izin verir ve bu bağlantıyı mqm kullanıcısına eşler.

MCAUSER (Message Channel Agent User ID)
	• Tanım: Kanal üzerinden bağlanan istemcinin (client) yetkilerini tanımlayan kullanıcı kimliğidir.
	• Örnek Kullanım:

DEFINE CHANNEL('MY.SENDER') CHLTYPE(SDR) MCAUSER('mqm')
	• Anlamı: Kanalı kullanan istemcinin, mqm kullanıcısının yetkilerine sahip olmasını sağlar.

RDQM (Replicated Data Queue Manager)
	• Tanım: IBM MQ’nun yüksek kullanılabilirlik (High Availability) ve felaket kurtarma (Disaster Recovery) özellikleri sağlayan bir bileşenidir. Mesajlar ve Queue Manager’lar birden fazla sunucuda eşzamanlı olarak çoğaltılır.
	• Kullanım Alanı: Kritik iş uygulamalarında mesaj kaybını önlemek için kullanılır. Örneğin:
		○ Akbank veya İş Bankası gibi finans kurumları, müşteri işlemlerinde kesintisiz hizmet sağlamak için RDQM kullanabilir.

2. IBM MQ ile Şirketlerin Ne Yaptığı?
IBM MQ'nun Şirketlerdeki Rolü
	• Finans (Akbank, İş Bankası): Ödeme işlemleri, para transferleri, kredi kartı işlemleri gibi yüksek hacimli mesajların güvenilir ve tutarlı bir şekilde iletilmesi.
		○ Örnek: Bir müşterinin havale işlemi, farklı sistemler arasında mesaj olarak taşınır. IBM MQ, bu mesajların kaybolmadan iletilmesini sağlar.
	• Ulaştırma (TCDD): Tren biletleme, rezervasyon sistemleri ve lojistik süreçlerinde mesaj tabanlı iletişim.
		○ Örnek: Tren hareket bilgilerinin gerçek zamanlı olarak iletilmesi.
	• Telekomünikasyon: Faturalandırma, müşteri hizmetleri sistemleri ve veri entegrasyonu.
	• Sağlık: Hasta kayıtları, laboratuvar sonuçları ve diğer kritik verilerin güvenli iletimi.

3. Dünya Genelinde Karşılaşılan Sorunlar
	1. Queue Doluluk Sorunu (MQRC_Q_FULL):
		○ Nedeni: MAXDEPTH sınırına ulaşılması.
		○ Çözüm: Kuyruğun derinliğini artırmak veya mesaj tüketim hızını optimize etmek.

ALTER QLOCAL('MY.QUEUE') MAXDEPTH(10000)
	2. Kanal Bağlantı Hataları (AMQ9208E):
		○ Nedeni: Kanal kimlik doğrulama (CHLAUTH) hatası veya network problemi.
		○ Çözüm: CHLAUTH kayıtlarını kontrol etmek ve izin verilen IP adreslerini eklemek.
	3. Yetkilendirme Sorunları (AMQ4036E):
		○ Nedeni: Yanlış veya eksik MCAUSER ayarı.
		○ Çözüm: Doğru kullanıcı yetkilerini eklemek.

SET AUTHREC PROFILE('MY.QUEUE') OBJTYPE(QUEUE) AUTHADD(PUT,GET)
	4. Performans Sorunları:
		○ Nedeni: Yanlış konfigürasyon veya aşırı yük.
		○ Çözüm: Kanal sıkışmalarını önlemek için BATCHSZ, DISCINT gibi parametreleri optimize etmek.

4. Advanced ve Server Yüklemesi Farkı
Advanced:
	• Ek olarak:
		○ MQ AMS (Advanced Message Security): Mesajların şifrelenmesi.
		○ Telemetry (MQTT): IoT cihazlarıyla iletişim.
	• Advanced kullanımı, güvenlik ve IoT entegrasyonu gibi ileri seviye ihtiyaçlar için uygundur.
Server:
	• Standart mesajlaşma ihtiyaçları için yeterlidir.

5. Güncelleme Süreci
Update İşlemi:
	1. Yeni .deb veya .rpm dosyalarını indirin.
	2. Şu komutla güncelleyin:

sudo dpkg -i ibmmq-runtime_9.4.0.1_amd64.deb

6. Grafana ile İzleme
MQ'yu İzlemek için Grafana Kullanımı:
	• Grafana’ya Prometheus Exporter entegre edilerek MQ metriklerini görselleştirebilirsiniz.
	• Örnek metrikler:
		○ Kanal durumu.
		○ Kuyruk derinliği.
		○ Mesaj işleme süreleri.

7. Gönderici ve Alıcı Yapılandırmaları
Gönderici Taraf (Ubuntu):
	1. Transmission Queue: WINDOWS.TRANSMIT.QUEUE
	2. Remote Queue: TEST.REMOTE
	3. Sender Channel: UBUNTU.TO.WINDOWS
Alıcı Taraf (Windows):
	1. Receiver Channel: UBUNTU.TO.WINDOWS
	2. Local Queue: WINDOWS.TEST.LOCAL



1. IBM MQ'da Mesaj Gönderme ve Alma Süreci
Mesaj Gönderme ve Alma Mantığı
	• IBM MQ, uygulamalar arasında asenkron (eş zamanlı olmayan) mesajlaşmayı sağlayan bir ara katman yazılımıdır.
	• Gönderici Uygulama (Producer): Mesajları bir kuyruğa gönderir.
	• Alıcı Uygulama (Consumer): Mesajları kuyruğun diğer ucundan alır.

Mesaj Gönderme ve Alma için Kullanılan Araçlar
1. MQSC Komutları ile Test
	• Gönderme: amqsput komutunu kullanarak bir mesaj gönderebilirsiniz:

amqsput QUEUE_NAME QUEUE_MANAGER
		○ Mesajınızı yazdıktan sonra Enter’a basmanız yeterlidir.
	• Alma: amqsget komutunu kullanarak kuyruğu okuyabilirsiniz:

amqsget QUEUE_NAME QUEUE_MANAGER
2. Uygulama Seviyesinde Kullanım
	• IBM MQ’yu genellikle uygulamalar aşağıdaki yollarla kullanır:
		○ Java JMS (Java Message Service): Java tabanlı uygulamalar için.
		○ C/C++ API: Performans odaklı uygulamalar için.
		○ Node.js, Python gibi modern dillerde MQ SDK kullanarak entegrasyon yapılabilir.
3. IBM MQ Explorer ile İzleme ve Yönetim
	• IBM MQ Explorer, görsel bir araçtır. Kuyruk derinliklerini, mesaj trafiğini ve kanal durumlarını kontrol edebilirsiniz.

Şirketler Mesajları Nasıl Takip Ediyor?
	• Log Dosyaları: /var/mqm/errors veya Windows tarafında C:\Program Files\IBM\MQ\log altındaki loglar analiz edilir.
	• Monitoring Araçları:
		○ Grafana/Prometheus: Kuyrukların ve kanalların durumunu görselleştirir.
		○ IBM Tivoli Monitoring (ITM): Daha gelişmiş bir çözüm sunar.

2. Tek Yönlü ve Çift Yönlü Mesajlaşma
IBM MQ genelde iki bağlantı türünü destekler:
	• Tek Yönlü Mesajlaşma (One-Way Communication): Bir sistem, diğerine mesaj gönderir. Alıcı sadece bu mesajı okur.
	• Çift Yönlü Mesajlaşma (Two-Way Communication): İki sistem mesajları hem gönderir hem alır. Örneğin, bir bankacılık uygulamasında sorgu ve yanıt işlemleri.

Tek Yönlü Mesajlaşma
Gereken Bileşenler:
	1. Gönderici Taraf:
		○ Queue Manager: Mesajları yöneten bileşen.
		○ Transmission Queue (XMITQ): Mesajları iletmek için kullanılan ara kuyruk.
		○ Sender Channel: Mesajları bir başka Queue Manager’a taşır.
		○ Listener: Gelen bağlantıları dinleyen TCP/IP portu.
	2. Alıcı Taraf:
		○ Queue Manager
		○ Receiver Channel: Gönderici tarafındaki Sender Channel ile eşleşir.
		○ Local Queue: Mesajların sonlandığı kuyruk.
Kısaca Süreç:
	1. Gönderici, mesajı Remote Queue'ya gönderir.
	2. Remote Queue, mesajı XMITQ üzerinden iletir.
	3. Sender Channel, mesajı Receiver Channel üzerinden diğer Queue Manager’a taşır.
	4. Mesaj, Local Queue’ya ulaşır ve oradan alınır.

Çift Yönlü Mesajlaşma
	• Ek Gerekenler:
		○ Her iki taraf için Sender ve Receiver Channel tanımlanır.
		○ Gönderici ve alıcı için hem Transmission Queue hem de Local Queue oluşturulur.
Örnek Konfigürasyon:
	• Ubuntu -> Windows (Mesaj Gönderme)
		○ Sender Channel: UBUNTU.TO.WINDOWS
		○ Transmission Queue: WINDOWS.TRANSMIT.QUEUE
	• Windows -> Ubuntu (Yanıt Gönderme)
		○ Sender Channel: WINDOWS.TO.UBUNTU
		○ Transmission Queue: UBUNTU.TRANSMIT.QUEUE
Süreç:
	1. Ubuntu’dan Windows’a mesaj gönderilir.
	2. Windows mesajı işler ve yanıtını UBUNTU.TRANSMIT.QUEUE üzerinden geri gönderir.

3. Cluster Yapılandırması
Cluster Nedir?
	• Cluster, birden fazla Queue Manager’ın birlikte çalıştığı bir yapı sağlar.
	• Amaç:
		○ Yük dengeleme (Load Balancing).
		○ Yedeklilik (Redundancy).
		○ Merkezi bir yapı üzerinden mesaj yönetimi.

Cluster Nasıl Kurulur?
	1. Cluster Repositories Tanımlanır:
		○ İki Queue Manager, cluster’ın koordinasyonunu yapar.
		○ Örnek:

DEFINE QLOCAL('CLUSTER.QUEUE') CLUSTER('MYCLUSTER')
	2. Cluster’a Diğer Queue Manager’lar Eklenir:

ALTER QMGR REPOS('MYCLUSTER')
	3. Cluster Kanalları Tanımlanır:
		○ Gönderici ve alıcı taraflar için tanımlama yapılır:

DEFINE CHANNEL('MYCLUSTER.SDR') CHLTYPE(CLUSSDR) TRPTYPE(TCP) CONNAME('192.168.1.2(1414)') CLUSTER('MYCLUSTER')
DEFINE CHANNEL('MYCLUSTER.RCVR') CHLTYPE(CLUSRCVR) TRPTYPE(TCP) CLUSTER('MYCLUSTER')

4. Gerçek Hayatta IBM MQ ile Karşılaşılan Sorunlar
1. Kuyruk Tıkanıklığı:
	• Sorun: Mesajlar işlenmediği için kuyruk doluyor.
	• Çözüm:
		○ Tüketici uygulamayı ölçeklendirin.
		○ Kuyruk kapasitesini artırın:

ALTER QLOCAL('MY.QUEUE') MAXDEPTH(10000)
2. Kanal Kopmaları:
	• Sorun: Ağ sorunları veya timeout nedeniyle kanallar kopar.
	• Çözüm:
		○ Kanal parametrelerini ayarlayın:

ALTER CHANNEL('MY.CHANNEL') HBINT(60)
3. Güvenlik Hataları:
	• Sorun: CHLAUTH kuralları nedeniyle bağlantı reddedilir.
	• Çözüm: İzin verilen IP’leri ve kullanıcıları güncelleyin:

SET CHLAUTH('MY.CHANNEL') TYPE(ADDRESSMAP) ADDRESS('192.168.1.1') MCAUSER('mqm') ACTION(ADD)

5. Özet
	1. Tek Yönlü Mesajlaşma:
		○ Gönderici taraf: Sender Channel, Remote Queue, XMITQ.
		○ Alıcı taraf: Receiver Channel, Local Queue.
	2. Çift Yönlü Mesajlaşma:
		○ İki taraf için hem Sender hem Receiver Channel tanımlanır.
	3. Cluster:
		○ Yük dengeleme ve yedeklilik için kullanılır.
	4. Log ve Monitoring:
		○ Log dosyalarını inceleyerek sorunları anlayabilirsiniz.
		○ Monitoring araçları (Grafana, Prometheus) ile izleme yapılabilir.
	5. Mesajların Yönetimi:
		○ IBM MQ Explorer veya komut satırı araçlarıyla yönetim sağlanır.

IBM MQ Mesaj Gönderme, Alma ve Yapılandırma 


1. Mevcut Yapının Durumu
	• Windows (QM1): Alıcı olarak konfigüre edilmiştir.
		○ Üzerinde bir local queue WINDOWS.TEST.LOCAL mevcut.
		○ UBUNTU.TO.WINDOWS ve REDHAT.TO.WINDOWS adında iki çalma kanalları (receiver channels) bulunur.
	• Ubuntu (QM3):
		○ Windows'a mesaj göndermek için TEST.REMOTE adında bir remote queue tanımlı.
		○ Bu remote queue mesajları WINDOWS.TRANSMIT.QUEUE adlı transmission queue üzerinden gönderir.
	• RedHat (QM2): Benzer şekilde Ubuntu ile aynı mantıkta bir yapıya sahiptir.
Amaç: Ubuntu ve RedHat üzerinden mesajları Windows tarafındaki WINDOWS.TEST.LOCAL kuyruğuna iletmek.

2. Mesaj Gönderme Öncesi Kontroller
Mesaj göndermeden önce aşağıdaki adımlar kontrol edilmelidir:
a) Listener Durumu
Her bir queue manager üzerindeki listener portlarının çalıştığından emin olun.
	• Listener'ları kontrol etmek için:
DISPLAY LSSTATUS('LISTENER_NAME') ALL
		○ Durum: RUNNING olmalıdır.
b) Channel Durumu
	• Gönderici kanalın çalışıp çalışmadığını kontrol edin:
DISPLAY CHSTATUS('CHANNEL_NAME') ALL
		○ Durum: RUNNING olmalı.
		○ Bağlı:ş: Receiver kanalın doğru adreste ve portta dinlediğinden emin olun.
c) Queue Durumu
	• Gönderici tarafındaki Remote Queue ve Transmission Queue’nun aşağıdaki gibi tanımlı olduğundan emin olun:
		○ Transmission Queue (XMITQ):
DISPLAY QLOCAL('WINDOWS.TRANSMIT.QUEUE') ALL
		○ Remote Queue:
DISPLAY QREMOTE('TEST.REMOTE') ALL
	• CURDEPTH: Transmission kuyruğu boşal olmalıdır (CURDEPTH=0).

3. Mesaj Gönderme Adımları
Mesaj göndermek için aşağıdaki adımlar izlenir:
a) Komut Satırından Mesaj Gönderme
	1. amqsput komutunu kullanarak mesaj gönderin:
amqsput TEST.REMOTE QM3
		○ TEST.REMOTE: Remote queue.
		○ QM3: Ubuntu üzerindeki queue manager.
	2. Windows tarafından mesajı almak için:
amqsget WINDOWS.TEST.LOCAL QM1
		○ Bu komut ile mesajı WINDOWS.TEST.LOCAL kuyruğundan okuyabilirsiniz.
b) Profesyonel Yöntem: Uygulama ile Gönderim
	• IBM MQ, birçok programlama dili ile entegre olabilir. Java ile bir uygulama geliştirerek mesaj gönderim/alım sürecini otomatize edebilirsiniz.
	• Aşağıda örnek bir Java kodu verilmiştir:
Java Örneği:
import com.ibm.mq.*;
import com.ibm.mq.constants.*;
public class MQMessageSender {
    public static void main(String[] args) {
        MQQueueManager qMgr = null;
        try {
            MQEnvironment.hostname = "192.168.142.130"; // Ubuntu IP
            MQEnvironment.channel = "UBUNTU.TO.WINDOWS";
            MQEnvironment.port = 1415;
qMgr = new MQQueueManager("QM3");
            MQQueue queue = qMgr.accessQueue("TEST.REMOTE", CMQC.MQOO_OUTPUT);
MQMessage message = new MQMessage();
            message.writeString("Hello from Java MQ!");
MQPutMessageOptions pmo = new MQPutMessageOptions();
            queue.put(message, pmo);
System.out.println("Message sent successfully!");
            queue.close();
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            if (qMgr != null) try { qMgr.disconnect(); } catch (Exception ignored) {}
        }
    }
}
	• Bu kod, bir mesajı TEST.REMOTE kuyruğuna gönderir.

4. IBM MQ Genel Komutları
IBM MQ'yu kullanırken en sık kullanılan komutlar ve açıklamaları aşağıdadir:
Komut	Amaç
dspmqver	IBM MQ versiyon bilgisini görüntüler.
crtmqm QM_NAME	Yeni bir queue manager oluşturur.
strmqm QM_NAME	Belirtilen queue manager'ı başlatır.
endmqm QM_NAME	Queue manager'ı kapatır.
runmqsc QM_NAME	Queue manager komut ortamına giriş yapar.
DEFINE QLOCAL(QUEUE_NAME)	Yeni bir local queue oluşturur.
DEFINE QREMOTE(QUEUE_NAME)	Remote queue tanımlar.
DEFINE CHANNEL(CHANNEL_NAME)	Yeni bir kanal tanımlar.
START CHANNEL(CHANNEL_NAME)	Belirtilen kanalları başlatır.
DISPLAY QLOCAL(QUEUE_NAME)	Local queue detaylarını görüntüler.
DISPLAY CHSTATUS(CHANNEL_NAME)	Kanal durumunu görüntüler.
SET CHLAUTH(CHANNEL_NAME)	Kanal yetkilendirme ayarı yapar.
ALTER QMGR	Queue manager ayarını değiştirir.
DELETE QLOCAL(QUEUE_NAME)	Local queue’yu siler.
DELETE CHANNEL(CHANNEL_NAME)	Kanalı siler.

5. SSL Kanalları ve Güvenlik
	• Bizim yaptığımız çalışma SSL kullanmadan TCP/IP protokolü üzerinden bağlantı sağlamıştır.
SSL Kanalı Nedir?
	• SSL (Secure Sockets Layer), MQ kanalları arasında şifreli veri aktarımı sağlar.
	• Bir kanalı SSL ile kullanmak için:
		1. Sertifikalar oluşturulur.
		2. Kanala SSL Cipher Spec eklenir:
ALTER CHANNEL('MY.CHANNEL') SSLCIPH('TLS_RSA_WITH_AES_256_CBC_SHA')
		3. Sertifika deposu (key repository) tanımlanır.

6. Grafana ile Monitoring
	• Grafana, IBM MQ’daki kuyruğun ve kanalların durumunu izlemek için harika bir araçtır.
	• Kurulum: Grafana Ubuntu veya RedHat üzerine kurulabilir.
	• MQ Prometheus Exporter: IBM MQ’dan verileri Prometheus protokolüne uygun olarak Grafana’ya aktarır.
Adımlar:
	1. Prometheus Exporter Kurulumu:
docker run -d -p 8080:8080 prom/mq_exporter
	2. Grafana Datasource Ekleme: Prometheus’u kaynak olarak ekleyin.
	3. MQ Dashboard: Grafana’daki hazır şablonlarla kuyruğunuzun durumunu izleyin.



IBM MQ - SSL Channel Yapılandırma Rehberi

1. SSL Channel Nedir ve Nasıl Oluşturulur?
SSL Channel Nedir?
SSL (Secure Sockets Layer) veya TLS (Transport Layer Security), IBM MQ üzerinden iletilen mesajların şifrelenmesini sağlayan bir protokoldür. Bu, mesajların güvenliğini artırmak ve kimlik doğrulama için kullanılır.


SSL Channel Oluşturma Adımları
	1. SSL Sertifikası Oluşturma:
		○ IBM MQ, GSKit'i kullanarak kendi kendine imzalanmış sertifikalar oluşturabilir. Sertifika otoritesinden (CA) alınan sertifikalar da kullanılabilir.
		○ Sertifika depoları oluşturulur:
runmqckm -keydb -create -db QM1Key.kdb -pw password -type cms -stash
			§ QM1Key.kdb: Sertifika deposu dosyası.
			§ -pw: Parola.
	2. Sertifika Talebi Oluşturma:
runmqckm -certreq -create -db QM1Key.kdb -pw password -label ibmwebspheremqqm1 -dn "CN=qm1.example.com, O=YourOrganization, C=TR" -size 2048 -sig_alg SHA256WithRSA
	3. CA Sertifikasını Alma ve İçeri Aktarma:
		○ Sertifika talebinizi CA'ya gönderip bir sertifika alın.
		○ Aldığınız sertifikayı deponuza ekleyin:
runmqckm -cert -add -db QM1Key.kdb -pw password -label ibmwebspheremqqm1 -file mycert.crt
	4. SSL Channel Tanımlama:
		○ IBM MQ üzerinde bir channel için SSL özelliklerini etkinleştirin:
DEFINE CHANNEL('SECURE.SDR') CHLTYPE(SDR) TRPTYPE(TCP) SSLCIPH('TLS_RSA_WITH_AES_128_CBC_SHA256') CONNAME('192.168.1.10(1414)') XMITQ('SECURE.TRANSMIT.QUEUE')
		○ Önemli Parametreler:
			§ SSLCIPH: Kullandığınız şifreleme algoritması.
			§ CONNAME: Hedef IP ve port.
	5. SSL Ayarlarını Doğrulama:
		○ Çalışan bir channel'da SSL özelliklerini kontrol edin:
DISPLAY CHANNEL('SECURE.SDR') SSLCIPH SSLPEER

3. IBM MQ Komutları Listesi
IBM MQ'da kullanılan en sık komutlar ve açıklamaları:
Queue Manager Komutları
	• crtmqm [Queue Manager Adı]: Yeni bir queue manager oluşturur.
	• strmqm [Queue Manager Adı]: Belirtilen queue manager'ı başlatır.
	• endmqm [Queue Manager Adı]: Queue manager'ı durdurur.
	• dspmq: Sistemdeki tüm queue manager'ı listeler ve durumlarını gösterir.
Channel Komutları
	• DEFINE CHANNEL: Yeni bir channel oluşturur.
DEFINE CHANNEL('MY.SENDER') CHLTYPE(SDR) TRPTYPE(TCP) CONNAME('192.168.1.20(1414)') XMITQ('MY.TRANSMIT.QUEUE')
	• START CHANNEL('Channel Adı'): Channel'ı başlatır.
	• STOP CHANNEL('Channel Adı'): Channel'ı durdurur.
	• DISPLAY CHANNEL: Channel detaylarını gösterir.
Queue Komutları
	• DEFINE QLOCAL: Yerel bir kuyruk oluşturur.
DEFINE QLOCAL('MY.LOCAL.QUEUE') MAXDEPTH(5000) DEFPSIST(YES)
	• DEFINE QREMOTE: Uzak bir kuyruk tanımlar.
DEFINE QREMOTE('MY.REMOTE.QUEUE') RNAME('REMOTE.QUEUE') RQMNAME('REMOTEQM') XMITQ('MY.TRANSMIT.QUEUE')
	• DISPLAY QLOCAL/QREMOTE: Kuyruk detaylarını gösterir.
	• DELETE QLOCAL/QREMOTE: Belirtilen kuyruğu siler.

4. VMware İçinde IBM MQ Yapısı ve Gözlemleme
IBM MQ Explorer
	• IBM MQ Explorer, IBM MQ queue manager'larını ve kuyruğlarını grafiksel bir arayüzden izlemek için kullanılır.
	• VMware üzerinde kurulu Windows sisteminizdeki Explorer'a, Ubuntu ve RedHat queue manager'ını eklemek için:
		1. Queue manager'ın listener portunu kontrol edin (Ubuntu ve RedHat).
		2. IBM MQ Explorer'da "Add Remote Queue Manager" özelliğini kullanın.
Grafana ile Gözlemleme
	• Grafana, IBM MQ metriklerini Prometheus gibi bir aracı kullanarak izlemek için mükemmel bir çözümdür.
	• Kurulum:
		1. Prometheus’u Windows veya Ubuntu’da kurun.
		2. IBM MQ’dan metrikleri toplamak için Prometheus MQ Exporterı ekleyin.
		3. Grafana'da Prometheus veri kaynağını ekleyin.
Grafana, hem üretici hem de tüketici kuyrukların derinliklerini, mesaj gecikmelerini ve sistem performansını gözlemlemek için çok faydalıdır.

5. Java Uygulaması ile IBM MQ Kullanımı
MacBook üzerinde IntelliJ veya Eclipse kullanarak bir Java uygulaması geliştirerek, IBM MQ'ya mesaj gönderme ve alma işlemlerini yapabilirsiniz.
Bağlantı İçin Gerekenler:
	1. IBM MQ Client Kütüphanesi:
		○ Uygulamanızda com.ibm.mq.allclient Maven bağımlılığını ekleyin.
<dependency>
    <groupId>com.ibm.mq</groupId>
    <artifactId>com.ibm.mq.allclient</artifactId>
    <version>9.4.0</version>
</dependency>
	2. Java Kodörneği:
		○ Mesaj Gönderme:
MQQueueManager queueManager = new MQQueueManager("QM1");
MQQueue queue = queueManager.accessQueue("TEST.QUEUE", MQC.MQOO_OUTPUT);
MQMessage message = new MQMessage();
message.writeUTF("Hello, IBM MQ!");
MQPutMessageOptions pmo = new MQPutMessageOptions();
queue.put(message, pmo);
queue.close();
queueManager.disconnect();
	3. Grafana ile Bağlantı:
		○ Java uygulamanızın Prometheus’tan metrik toplamasını sağlamak için Prometheus Java Clientı kullanabilirsiniz.
---

1. IBM MQ Komutlarının Açıklaması ve Kullanımı
IBM MQ'da komutların mantığı ve parametreleri şöyledir:
Örnek Komut:

DEFINE QLOCAL('MY.LOCAL.QUEUE') MAXDEPTH(5000) DEFPSIST(YES)
Açıklama:
	1. DEFINE QLOCAL: Bu komut yerel (local) bir kuyruk oluşturur.
		○ Yerel Kuyruk (Local Queue): Mesajların fiziksel olarak saklandığı yerdir.
	2. Parametreler:
		○ MAXDEPTH(5000): Kuyruğun maksimum mesaj kapasitesini belirtir.
			§ 5000 nedir?: Kuyruğun aynı anda en fazla 5000 mesaj saklayabileceğini ifade eder.
			§ Ne olmalı?: İhtiyacınıza bağlıdır. Daha fazla mesaj taşınması gerekiyorsa 10000 veya daha yüksek bir değer ayarlanabilir. Ancak çok yüksek bir değer, performans sorunlarına yol açabilir.
		○ DEFPSIST(YES): Mesajların kalıcı (persistent) olmasını sağlar.
			§ Kalıcı Mesajlar: Sistem kapansa bile mesajlar saklanır.
			§ Kalıcı olmayan mesajlar (NO): Sistem kapandığında mesajlar kaybolur.
Diğer Parametreler:
	• DESCR('Açıklama'): Kuyruğa bir açıklama ekler.
	• USAGE(XMITQ): Eğer bu kuyruk bir iletim (transmit) kuyruğu olarak kullanılacaksa bu parametre eklenir.
	• PUT(DISABLED): Kuyruğa mesaj koyma (PUT) işlemini devre dışı bırakır.
	• GET(DISABLED): Kuyruktan mesaj alma (GET) işlemini devre dışı bırakır.

2. SSL Channel ile TCP Channel Arasındaki Fark
	• TCP Channel (Normal):
		○ Mesajlar şifrelenmeden gönderilir.
		○ Daha az güvenlidir, ancak daha basittir ve konfigürasyonu kolaydır.
	• SSL Channel:
		○ Secure Sockets Layer (SSL) kullanılarak mesajlar şifrelenir.
		○ Veri gizliliği ve güvenliği sağlar.
		○ Konfigürasyon gerektirir: Sertifikaların oluşturulması ve yüklenmesi gerekir.
SSL Channel Nasıl Oluşturulur?
	1. Sertifika Oluşturun:
		○ IBM MQ’nun kendi sertifika yönetim aracı olan runmqckm veya OpenSSL kullanılır.

runmqckm -keydb -create -db key.kdb -pw password -type cms -stash
	2. Channel Oluşturun:

DEFINE CHANNEL('SSL.CHANNEL') CHLTYPE(SVRCONN) SSLCIPH('TLS_RSA_WITH_AES_128_CBC_SHA256')
	3. Listener Güncellemesi:
		○ Listener'ı SSL desteği için konfigüre edin:

ALTER LISTENER('SSL.LISTENER') TRPTYPE(TCP) PORT(1415) CERTLABL('mycert')

3. Mesaj Gönderme ve Alma Süreci
Mesaj gönderme ve alma süreçlerini adım adım açıklayalım:
Mesaj Gönderme:
	1. Gönderici Kanal (Sender Channel) Tanımlayın:

DEFINE CHANNEL('SENDER.CHANNEL') CHLTYPE(SDR) TRPTYPE(TCP) CONNAME('192.168.1.2(1414)') XMITQ('TRANSMIT.QUEUE')
		○ XMITQ: Mesajların taşındığı kuyruk.
	2. Mesaj Gönderme Komutları:

amqsput TEST.REMOTE QM3
Mesaj Alma:
	1. Alıcı Kuyruğa Bağlanın:

amqsget WINDOWS.TEST.LOCAL QM1

4. Komutların Genel Listesi
Komut	Açıklama
DEFINE QLOCAL	Yerel bir kuyruk oluşturur.
DEFINE CHANNEL	Bir channel (kanal) oluşturur.
ALTER QLOCAL	Var olan bir kuyruğu değiştirir.
DISPLAY QLOCAL	Kuyruk bilgilerini gösterir.
START CHANNEL	Belirli bir kanalı başlatır.
STOP CHANNEL	Belirli bir kanalı durdurur.
DEFINE LISTENER	Listener tanımlar (port dinler).
DISPLAY CHSTATUS	Kanal durumlarını gösterir.
SET CHLAUTH	Channel Authentication ayarları yapar.
DISPLAY CHLAUTH	Channel Authentication kurallarını gösterir.

5. Grafana ile İzleme
	• Grafana Nedir?
		○ IBM MQ'nun performansını izlemek için kullanılabilecek açık kaynak bir araçtır.
		○ MQ’dan alınan metrikleri gösterir (örneğin, queue depth, channel status).
	• Grafana’yı Kurmak:
		1. Grafana’yı VM içerisindeki Windows sunucusuna kurabilirsiniz.
		2. Grafana’ya IBM MQ metriklerini entegre etmek için bir MQ exporter kurulur (örneğin, Prometheus).

6. Java ile IBM MQ Uygulaması
	• Java Uygulaması ile Mesaj Gönderme ve Alma:
		○ IBM MQ’ya Java kullanarak bağlanabilir ve mesaj alıp gönderebilirsiniz.
		○ Maven Dependency:

<dependency>
  <groupId>com.ibm.mq</groupId>
  <artifactId>mq-jms-spring-boot-starter</artifactId>
  <version>2.6.0</version>
</dependency>
		○ Kod Örneği:

MQQueueConnectionFactory factory = new MQQueueConnectionFactory();
factory.setHostName("192.168.1.2");
factory.setPort(1414);
factory.setQueueManager("QM1");
factory.setChannel("SENDER.CHANNEL");

Connection connection = factory.createConnection();
Session session = connection.createSession(false, Session.AUTO_ACKNOWLEDGE);
Queue queue = session.createQueue("TEST.QUEUE");
MessageProducer producer = session.createProducer(queue);
TextMessage message = session.createTextMessage("Hello from Java!");
producer.send(message);

7. Test Ortamının Profesyonelliği
	• Test Ortamı Yeterli mi?
		○ Şu an kurduğumuz yapı profesyonel bir test ortamıdır.
		○ SSL kanal ve monitoring araçları (Grafana gibi) eklerseniz kurumsal düzeyde bir ortam olur.

1. Java ile IBM MQ'ya Bağlanmak
Java ile IBM MQ'ya bağlanabilir ve tüm mesajlaşma işlemlerini yapabilirsiniz. Bunun için gerekli olan adımları ve bileşenleri açıklıyorum:
Java'da Gerekenler:
	1. IBM MQ JAR Dosyaları:
		○ IBM MQ'ya Java üzerinden bağlanmak için gerekli olan JAR dosyaları:
			§ com.ibm.mq.allclient.jar
				□ IBM MQ'yu Java istemcisi olarak kullanmanıza olanak sağlar.
			§ com.ibm.mqjms.jar
				□ JMS (Java Messaging Service) protokolü ile bağlanmayı sağlar.
Bu JAR dosyaları IBM MQ yüklemesiyle birlikte gelir. Eğer kurulu değilse, IBM MQ Client indirilip kullanılabilir.
	2. Maven Projesi (Önerilen Yaklaşım): Eğer Maven kullanıyorsanız, bağımlılığı ekleyebilirsiniz:


<dependency>
    <groupId>com.ibm.mq</groupId>
    <artifactId>com.ibm.mq.allclient</artifactId>
    <version>9.3.0.0</version>
</dependency>
	3. IDE Seçimi:
		○ IntelliJ IDEA veya Eclipse, projeyi geliştirmek için kullanılabilir.
		○ Maven veya Gradle yapılandırmasıyla gerekli bağımlılıkları kolayca ekleyebilirsiniz.

Java ile IBM MQ Bağlantısı için Örnek Kod
Aşağıda, Java ile IBM MQ'ya bağlanıp bir mesaj gönderme örneği yer alıyor:
Kod:
import com.ibm.mq.jms.MQQueueConnectionFactory;
import com.ibm.msg.client.jms.JmsConstants;
import javax.jms.*;
public class MQTest {
    public static void main(String[] args) {
        try {
            // Connection Factory oluştur
            MQQueueConnectionFactory factory = new MQQueueConnectionFactory();
            factory.setHostName("192.168.1.2"); // MQ Server IP
            factory.setPort(1414);             // MQ Server Port
            factory.setQueueManager("QM1");   // Queue Manager
            factory.setChannel("SENDER.CHANNEL"); // Channel Name
            factory.setTransportType(JmsConstants.WMQ_CM_CLIENT); // Client Mode
            
            // Bağlantı oluştur
            Connection connection = factory.createConnection();
            connection.start();
            
            // Session oluştur
            Session session = connection.createSession(false, Session.AUTO_ACKNOWLEDGE);
            Queue queue = session.createQueue("TEST.QUEUE");
// Mesaj gönderici (Producer)
            MessageProducer producer = session.createProducer(queue);
            TextMessage message = session.createTextMessage("Hello from Java!");
            producer.send(message);
System.out.println("Message sent successfully!");
// Bağlantıyı kapat
            producer.close();
            session.close();
            connection.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
Yapmanız Gerekenler:
	1. IBM MQ'ya uygun bağlantı bilgilerini girin:
		○ HostName: MQ sunucusunun IP adresi veya hostname'i.
		○ Port: IBM MQ Listener'ın dinlediği port (örneğin, 1414).
		○ QueueManager: Mesajların yönetildiği Queue Manager (örneğin, QM1).
		○ Channel: Bağlantı için kullanılan kanal (örneğin, SENDER.CHANNEL).
	2. JAR Dosyalarını Projeye Dahil Edin:
		○ Eğer Maven kullanmıyorsanız, JAR dosyalarını manuel olarak projeye ekleyin.
	3. IntelliJ veya Eclipse üzerinden bu kodu çalıştırabilirsiniz.

2. Grafana ile İzleme
IBM MQ'yu Grafana ile izlemek için şu adımları izleyebilirsiniz:
Grafana Nasıl Kurulur?
Grafana, hem fiziksel bir makineye hem de bir sanal makineye kurulabilir. Windows veya MacBook üzerine kurmanızda bir sakınca yoktur. Ancak, genelde izleme araçları için merkezi bir Linux sunucusu önerilir.
Ubuntu'da Grafana Kurulumu:
	1. Grafana'yı Yükleyin:

sudo apt-get update
sudo apt-get install -y grafana
	2. Grafana'yı Başlatın:


sudo systemctl start grafana-server
sudo systemctl enable grafana-server
	3. Web Arayüzüne Erişim:
		○ Web tarayıcınızda http://localhost:3000 adresine gidin.
		○ Varsayılan kullanıcı adı: admin
		○ Varsayılan parola: admin
	4. IBM MQ Exporter Ayarı:
		○ IBM MQ'yu Grafana ile izlemek için bir Prometheus Exporter kurmanız gerekir.
		○ Örnek IBM MQ Exporter: IBM MQ Exporter GitHub

3. SSL Channel Yapılandırması
SSL Channel yapılandırması, güvenli iletişim sağlamak için yapılır. Adımları detaylıca açıklıyorum:
Adımlar:
	1. Sertifika Oluşturma:
		○ IBM MQ için bir key database (sertifika deposu) oluşturun:


runmqckm -keydb -create -db mq.kdb -pw mypassword -type cms -stash
	2. Sertifika Talebi (CSR) Oluşturun:


runmqckm -certreq -create -db mq.kdb -pw mypassword -label ibmmqcert -dn "CN=MyQueueManager,O=MyOrganization" -size 2048 -sig_alg SHA256WithRSA
	3. Sertifikayı İçe Aktarın:
		○ Sertifikayı bir sertifika otoritesine (CA) gönderin ve alınan sertifikayı içe aktarın:


runmqckm -cert -receive -file mqcert.arm -db mq.kdb -pw mypassword -format ascii
	4. SSL Channel Tanımlayın:


DEFINE CHANNEL('SSL.CHANNEL') CHLTYPE(SVRCONN) SSLCIPH('TLS_RSA_WITH_AES_128_CBC_SHA256')
	5. Listener için Sertifika Etiketi (Label) Ekleyin:


ALTER LISTENER('SSL.LISTENER') TRPTYPE(TCP) PORT(1415) CERTLABL('ibmmqcert')

4. Genel IBM MQ Komutları
Komut	Açıklama
DEFINE QLOCAL	Yerel kuyruk oluşturur.
DEFINE CHANNEL	Bir channel oluşturur.
DISPLAY QLOCAL	Yerel kuyruk bilgilerini gösterir.
DISPLAY CHANNEL	Kanal bilgilerini gösterir.
DEFINE LISTENER	Listener tanımlar.
ALTER LISTENER	Listener ayarlarını değiştirir.
SET CHLAUTH	Kanal doğrulama kuralları oluşturur.
START CHANNEL	Bir kanalı başlatır.
STOP CHANNEL	Bir kanalı durdurur.
DISPLAY CHSTATUS	Kanal durumlarını gösterir.

5. Test Ortamınız Profesyonel mi?
Yaptığınız ortam profesyonel bir test ortamıdır. Ancak, tam profesyonellik için:
	• SSL Channel kurulumu.
	• Grafana ile performans izleme.
	• Yük testi ve senaryolar oluşturmanız gerekir.
