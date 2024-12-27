cd "C:\Program Files\IBM\MQ\bin"

Queue Manager Oluşturma Komutu:
crtmqm QM1

1. Queue Manager (QM1) Nedir?
	• Queue Manager, mesajların gönderilip alınmasını yöneten IBM MQ'nun temel bileşenidir. Tüm kuyruklar, kanallar ve diğer yapılandırmalar bu Queue Manager içinde tanımlanır.
	• Biz burada QM1 adında bir Queue Manager oluşturduk.
Ne Oldu?
	• crtmqm QM1 komutuyla QM1 adlı bir Queue Manager:
		○ C:\ProgramData\IBM\MQ\qmgrs\QM1 dizininde oluşturuldu.
		○ Varsayılan ayarlarıyla birlikte 86 tane default obje (örneğin varsayılan kuyruklar ve kanallar) tanımlandı.
		○ Bu Queue Manager, Installation1 adlı IBM MQ kurulumu ile ilişkilendirildi.
Queue Manager'ın Görevleri:
	• Mesajları yönlendirir, depolar ve teslim eder.
	• Kuyrukları, kanalları ve diğer MQ bileşenlerini barındırır.

2. Bir Sonraki Adım: Queue Manager'ı Başlatma
Queue Manager'ı Neden Başlatıyoruz?
	• Oluşturulan Queue Manager, şu an için duruyor (inactive durumda). Onun çalışır hale gelmesi gerekiyor ki içinde kuyruk oluşturabilelim, mesaj gönderebilelim ve alabilelim.
Komut:
strmqm QM1
Ne Yapacak?
	• Bu komut, QM1 adlı Queue Manager’ı çalıştırır.
	• Başlatıldığında şu işlemler gerçekleşir:
		○ Listener’lar (varsa) otomatik olarak çalışır.
		○ Kuyruklar ve diğer bileşenler erişilebilir hale gelir.
Not: Komut çalıştırıldığında, başarılı bir şekilde başlatıldığına dair bir mesaj göreceksiniz.



PS C:\Program Files\IBM\MQ\bin> strmqm QM1
IBM MQ queue manager 'QM1' starting.
The queue manager is associated with installation 'Installation1'.
6 log records accessed on queue manager 'QM1' during the log replay phase.
Log replay for queue manager 'QM1' complete.
Transaction manager state recovered for queue manager 'QM1'.
Plain text communication is enabled.
IBM MQ queue manager 'QM1' started using V9.4.0.0.
PS C:\Program Files\IBM\MQ\bin>
********************************************************

3. Queue Manager'ın Durumunu Kontrol Etme
Queue Manager'ın Durumunu Neden Kontrol Ederiz?
	• Queue Manager’ın "Running" durumda olduğundan emin olmamız gerekir.
Komut:

dspmq
Ne Göreceksiniz?
	• Sistemdeki tüm Queue Manager’ların durumlarını listeler.
	• Çıktı şu şekilde olmalı:



PS C:\Program Files\IBM\MQ\bin> dspmq
QMNAME(QM1)                                               STATUS(Running)
PS C:\Program Files\IBM\MQ\bin>


************************************************************

4. Bir Local Queue Tanımlama
Local Queue Nedir?
	• Local Queue, mesajları göndermek veya almak için kullanılan bir depolama alanıdır.
	• Örneğin: Mesaj gönderdiğinizde, bu mesaj Local Queue’da saklanır ve alıcı (consumer) bu kuyruğa bağlanarak mesajı alır.
Komut:
Queue Manager içinde bir Local Queue oluşturacağız. Bunun için runmqsc komutunu kullanıyoruz:
	1. Queue Manager’a Bağlan:
-->> runmqsc QM1

Bu komut, QM1 Queue Manager’ı üzerinde yapılandırma yapmak için interaktif bir moda geçmenizi sağlar.

PS C:\Program Files\IBM\MQ\bin> runmqsc QM1
5724-H72 (C) Copyright IBM Corp. 1994, 2024.
Starting MQSC for queue manager QM1.

	1. Local Queue Tanımla:

DEFINE QLOCAL('TEST.QUEUE') REPLACE
		○ DEFINE QLOCAL: Yeni bir Local Queue oluşturur.
		○ 'TEST.QUEUE': Kuyruğun adıdır. Burada istediğiniz bir ad kullanabilirsiniz.
		○ REPLACE: Eğer aynı adla bir kuyruk varsa üzerine yazmasını sağlar.

DEFINE QLOCAL('TEST.QUEUE') REPLACE
     1 : DEFINE QLOCAL('TEST.QUEUE') REPLACE
AMQ8006I: IBM MQ queue created.
end


	1. Konfigürasyon Modundan Çık:

end




5. Listener Tanımlama ve Başlatma
Listener Nedir?
	• Listener, Queue Manager’ın belirli bir port üzerinden gelen bağlantıları dinlemesini sağlar.
	• Varsayılan port 1414’tür. Bu port üzerinden mesaj alışverişi yapılır.
Komut:
	1. Listener’ı Tanımla:

DEFINE LISTENER('WIN.LISTENER') TRPTYPE(TCP) PORT(1414) CONTROL(QMGR)
	
		○ LISTENER('WIN.LISTENER'): Listener’ın adı.
		○ TRPTYPE(TCP): TCP protokolünü kullanır.
		○ PORT(1414): Listener’ın hangi porttan dinleyeceğini belirtir.
		○ CONTROL(QMGR): Listener’ın Queue Manager tarafından kontrol edilmesini sağlar.


	2. Listener’ı Başlat:

START LISTENER('WIN.LISTENER')


	DEFINE LISTENER('WIN.LISTENER') TRPTYPE(TCP) PORT(1414) CONTROL(QMGR)
	     1 : DEFINE LISTENER('WIN.LISTENER') TRPTYPE(TCP) PORT(1414) CONTROL(QMGR)
	AMQ8626I: IBM MQ listener created.
	START LISTENER('WIN.LISTENER')
	     2 : START LISTENER('WIN.LISTENER')
	AMQ8021I: Request to start IBM MQ listener accepted.
	
	3. Konfigürasyon Modundan Çık:

end

6. Mesaj Göndermek ve Almak için Channel Tanımlama
Channel Nedir?
	• Channel, Queue Manager’lar arasında iletişim sağlayan bir bağlantıdır.
	• Demo ortamımızda:
		○ Sender Channel: Windows’tan mesaj göndermek için.
		○ Receiver Channel: Ubuntu veya Red Hat’ten mesaj almak için.
Komut:
	1. Sender Channel Tanımlama:

DEFINE CHANNEL('WIN.TO.UBU') CHLTYPE(SDR) TRPTYPE(TCP) CONNAME('Ubuntu_IP(1414)')
		○ CHLTYPE(SDR): Sender Channel olduğunu belirtir.
		○ CONNAME: Ubuntu Queue Manager’ın IP adresi ve portu.
	2. Receiver Channel Tanımlama:

DEFINE CHANNEL('UBU.TO.WIN') CHLTYPE(RCVR) TRPTYPE(TCP)
		○ CHLTYPE(RCVR): Receiver Channel olduğunu belirtir.
	3. Konfigürasyon Modundan Çık:

end

7. MQ Explorer ile Kontrol
MQ Explorer Nedir?
	• IBM MQ’nun GUI (grafiksel) yönetim aracıdır.
	• Tüm bileşenlerinizi (Queue Manager, Queue, Channel, Listener vb.) görsel olarak kontrol edebilirsiniz.
Nasıl Kullanılır?
	1. MQ Explorer’ı Açın:
		○ Başlat Menüsü > IBM MQ > IBM MQ Explorer yolunu izleyin.
	2. Queue Manager’ı Ekleyin:
		○ Sol menüde sağ tıklayın ve "Add Queue Manager" seçeneğini seçin.
		○ Queue Manager Name kısmına QM1 yazın ve ekleyin.
	3. Queue ve Listener’ları Kontrol Edin:
		○ Queues sekmesinden TEST.QUEUE adlı kuyruğunuzu görebilirsiniz.
		○ Listener’ların ve kanalların çalıştığını kontrol edin


