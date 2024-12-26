1. IBM MQ MQI Client Bağlantı Problemleri
Bağlantı Hataları
MQCONN veya MQCONNX çağrıları sırasında aşağıdaki nedenlerle hata alabilirsiniz:
	• Listener Eksikliği: Sunucuda bir "listener" programı yoksa veya yanlış yapılandırılmışsa.
	• Protokol Kontrol Hatası: IBM MQ protokol kontrolleri sırasında bağlantı başarısız olabilir.
Hata Kodu: MQRC_Q_MQR_NOT_AVAILABLE
	• Bu hata kodu, bağlantı yapılamadığını gösterir. Aşağıdaki adımları kontrol edin:
		1. Listener Çalışıyor mu?
			§ Listener programının çalıştığından emin olun. Sunucuda runmqlsr komutunu kullanarak listener başlatabilirsiniz.
		2. Port ve IP Adresi Doğruluğu:
			§ İstemci konfigürasyonunda sunucunun IP adresi ve port numarasının doğru olduğundan emin olun.
		3. İstemci Hata Günlüğü:
			§ Hata günlüğünü kontrol edin:
				□ Windows: C:\Program Files\IBM\MQ\errors
				□ Linux: /var/mqm/errors
Bağlantı Sorunlarının Nedenleri
	• Sunucu programı veya listener yok.
	• Yanlış port veya IP adresi belirtilmiş.
	• İstemci ile sunucu arasındaki TCP/IP bağlantısı başarısız.

2. ECONNRESET Hatası
ECONNRESET: Bağlantının Kesilmesi
Bu hata, bağlantının karşı uçtan kapatıldığını gösterir. Aşağıdaki durumlarda oluşabilir:
	• Bağlantının Düzensiz Kapanması: İstemci sistem yeniden başlatılmış olabilir.
	• Yanlış Port veya IP: Uygulama, herhangi bir sunucunun dinlemediği bir port veya IP adresine bağlanmaya çalışıyor.
	• Beklenmeyen Veri: Kapalı bir bağlantıya veri gönderilmeye çalışılıyor.
	• Linger Seçeneği: Uygulama, linger seçeneğini sıfırlayarak bağlantıyı ani şekilde kapatmış olabilir.
Hata Mesajları
	• AMQ9208I: "Error on receive from host <hostname>."
	• AMQ9209I: "Connection to host <hostname> for channel <channelname> closed."
Çözüm Önerileri
	• Ağ Yöneticisine Başvurun: Ağ yöneticinizden TCP/IP paket izleme veya "sniffer" araçları kullanarak bağlantı sıfırlanma nedenlerini kontrol etmesini isteyin.
	• Güvenlik Duvarı Kontrolü: Gelen ve giden trafiğin güvenlik duvarı kurallarına uygun olduğundan emin olun.
	• Otomatik İstemci Yeniden Bağlanma:
		○ IBM MQ'nun Automatic Client Reconnection özelliğini uygulamanıza ekleyerek bağlantı kesintilerinde otomatik olarak yeniden bağlanmayı etkinleştirebilirsiniz.

3. Hata Günlüklerini İnceleme
Hata Günlüğü Dosyaları
	• Windows: C:\Program Files\IBM\MQ\errors
	• Linux: /var/mqm/errors
	• IBM i: /QIBM/UserData/mqm/errors
Ek Hata Mesajları
Bazı istemci hataları, sunucu hata günlüklerinde de kaydedilir. Bu nedenle, istemci ve sunucu hata günlüklerini birlikte incelemek önemlidir.

4. İstemci Kapatıldığında Kuyrukların Açık Kalması
Bir istemci kapatıldığında bile, sunucu tarafındaki süreçlerin kuyrukları açık tutabileceğini unutmayın. Bu, iletişim katmanının istemcinin kapatıldığını algılamasına kadar sürebilir.

5. Diagnostik İpuçları ve Çözüm Önerileri
Diagnostik Araçlar
	• TCP/IP Paket İzleme: Ağ yöneticinizden paket izleme araçlarını kullanmasını isteyin.
	• Sunucu Hata Kodları:
		○ Hata kodlarını anlamak için IBM MQ dokümantasyonundaki API Tamamlama ve Hata Kodları bölümüne bakabilirsiniz.
İzleme ve Test
	• Ping Kullanımı:
		○ Sunucu ve istemci arasındaki bağlantıyı test etmek için PING CHANNEL komutunu kullanabilirsiniz:runmqsc <QMGR>PING CHANNEL(<channel_name>)
