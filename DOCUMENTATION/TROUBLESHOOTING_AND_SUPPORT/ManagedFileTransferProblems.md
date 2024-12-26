Genel MFT Sorun Giderme Adımları:
	1. Agent Durum Sorunları:
		○ Agent'ın fteListAgents komutunda listelenmediği veya "UNKNOWN" durumda olduğu sorunlar.
		○ ftePingAgent komutunun yanıt alamadığı durumlar.
	2. Aktarım Sorunları:
		○ Tamamlanmayan transferler, sıkışmış transferler ve küme kuyruğuna yapılan hatalı transferler.
		○ Zamanlanmış transferlerin çalışmaması veya gecikmesi.
	3. Kaynak Monitör Sorunları:
		○ Klasör veya kuyruk monitörlerinde dosyaların yanlış tetiklenmesi veya birden fazla kez tetiklenmesi.
		○ Monitör ayarlarının optimize edilmesiyle agent üzerindeki yükün azaltılması.
	4. Hafıza Sorunları (OutOfMemoryError):
		○ Java Heap veya Native Heap tükenmesi.
		○ JVM özelliklerini ve agent yapılandırmasını ayarlayarak bellek kullanımının optimize edilmesi.

Sık Görülen Hata Kodları ve Çözümleri:
	• Return Code 0: Başarılı.
	• Return Code 1: Komut başarısız oldu.
	• Return Code 40: Transfer tamamen başarısız oldu.
	• Return Code 49: Hedefe ulaşılamadı (queue manager bağlantısı sorunu).
	• Return Code 53: Yetkilendirme hatası.
Her kodun detaylı açıklaması ve çözüm adımları ilgili tabloda yer almakta.

Önemli Öneriler:
	• Agent yapılandırması değiştirilirse yeniden başlatılmalıdır.
	• Ağ gecikmesi durumlarında -w parametresi ile komut bekleme süresi uzatılabilir.
	• BFG_JVM_PROPERTIES kullanılarak JVM bellek limitleri ayarlanabilir:set BFG_JVM_PROPERTIES="-Xmx1024M"
	• Temp Output Files kullanımı gerekiyorsa bu dosyaların taşınmaması sağlanmalıdır.

Örnek Senaryolar ve Çözümler:
	• Aktarım Gecikmesi: Agent'ın maxSourceTransfers veya monitorMaxResourcesInPoll gibi özellikleri optimize edilmelidir.
	• Bellek Sorunları:
		○ Java heap artırılabilir veya workload azaltılabilir.
		○ Native heap sorunları için BINDINGS yerine CLIENT transport seçeneği kullanılabilir.

****

1. IBM MQ JMS Sınıflarında Sorun Giderme
a. Kurulum Doğrulama Programları
	• IBM MQ JMS sınıfları için kurulum doğrulama programlarını kullanarak test yapabilirsiniz.
		○ Örnek Testler:
			§ Point-to-Point IVT
			§ Publish/Subscribe IVT
	• Bu testler, temel bağlantı ve mesaj alışverişi yapılandırmalarının doğruluğunu kontrol eder.
b. Loglama
	• Varsayılan log dosyası: mqjms.log
	• Log çıktısını özel bir dosyaya yönlendirmek için şu komutu kullanabilirsiniz:-Dcom.ibm.msg.client.commonservices.log.outputName=/path/to/mylog.txt
	• Loglamayı kapatmak için:-Dcom.ibm.msg.client.commonservices.log.status=OFF

2. JMS Sağlayıcı Versiyon Problemleri
a. Yaygın Hatalar ve Çözümleri
	• JMSCC5008: JMS 2.0 işlevi, desteklenmeyen bir bağlantıda kullanılıyor.
		○ Çözüm: JMS 2.0 API'sini kullanmayı bırakın veya IBM MQ 8 sürümündeki bir kuyruğa bağlanın.
	• JMSFMQ0003: Kuyruk yöneticisi komut seviyesi, sağlayıcı sürümüyle uyumlu değil.
		○ Çözüm: Sağlayıcı sürümünü kuyruk yöneticisi ile uyumlu olacak şekilde değiştirin.

3. PCF İşleme Sorunları
a. Kodlama Uyumsuzluğu
	• Big-endian ve little-endian platformlar arasındaki farklılıklar sorunlara neden olabilir.
	• Hata Mesajı: MQRCCF_STRUCTURE_TYPE_ERROR (3013)
b. Çözüm Örneği

java
Copy code
Message receivedMessage = consumer.receive(10000);BytesMessage bytesMessage = (BytesMessage) receivedMessage;byte[] bytesReceived = new byte[(int) bytesMessage.getBodyLength()];bytesMessage.readBytes(bytesReceived);
MQMessage mqMsg = new MQMessage();mqMsg.write(bytesReceived);mqMsg.encoding = receivedMessage.getIntProperty("JMS_IBM_Encoding");mqMsg.format = receivedMessage.getStringProperty("JMS_IBM_Format");mqMsg.seek(0);
PCFMessage pcfMsg = new PCFMessage(mqMsg);

4. Bağlantı Havuzu Hataları
a. Purge Policy Ayarları
	• FailingConnectionOnly: Sadece sorunlu bağlantı kapatılır (varsayılan).
	• EntirePool: Tüm bağlantılar kapatılır, güvenilir bir çözüm olabilir.

5. 2035 MQRC_NOT_AUTHORIZED Hatası
a. Nedenler
	• Kullanıcı adı bilinmiyor veya yetkilendirilmemiş.
	• CHLAUTH kaydı yönetici erişimini engelliyor.
b. Çözümler
	• Geliştirme ortamında:SET CHLAUTH('WAS.CLIENTS') TYPE(BLOCKUSER) USERLIST(ALLOWANY)
	• Üretim ortamında:
		○ SSL/TLS Güvenliği: Karşılıklı SSL doğrulama yapılandırın.
		○ Yetkilendirme hatalarını analiz edin ve çözümleyin.

6. Managed File Transfer (MFT) Problemleri
a. Mesaj Reddetme ve Yeniden İşleme
	• Reddedilen Mesajların İncelenmesi:
		○ Reject Queue'deki mesajları inceleyin.
		○ usr.WMQFTE_ReasonForRejection adlı bir özellik, reddedilme nedenini açıklar.
	• Mesajların Yeniden İşlenmesi:
		○ Mesajları Reject Queue'dan alıp, Input Queue'ya taşıyabilirsiniz.DISPLAY SUB(SYSTEM.FTE.DATABASELogger.AUTO) DEST
b. Logger Hataları
	• SQLSTATE=42704 hatası: Veritabanı tablo boyutları küçük.
		○ Çözüm: Veritabanı sayfa boyutunu 8 KB veya daha büyük olacak şekilde ayarlayın.

7. Connect:Direct Köprüsü ile Sorun Giderme
a. Dosya Yolu Hataları
	• Çift eğik çizgi (//) ile başlayan yollar, yanlışlıkla veri seti olarak yorumlanabilir.
		○ Çözüm: Dosya yollarını doğru formatta belirtin.
b. İzin Hataları
	• Hata Mesajı:BFGCD0001E: LCCA000I Kullanıcı, SNODEID geçersiz kılma iznine sahip değil.
		○ Çözüm: İlgili kullanıcıya gerekli yetkileri verin.
c. Eş Zamanlı Transferleri Artırma
	• Agent Properties Ayarları:maxSourceTransfers=25maxDestinationTransfers=25ioThreadPoolSize=50
	• Connect:Direct düğümündeki api.max.connects parametresini artırın.

8. Genel Sorun Giderme Adımları
	• Koordinasyon Kuyruk Yöneticisi Bağlantısı:
		○ Bağlantı hataları için 2058 hata kodunu analiz edin.
	• JVM DNS Cache Sorunları:
		○ Cache süresini düzenlemek için şu değişkeni ayarlayın:-Dsun.net.inetaddr.ttl=value
