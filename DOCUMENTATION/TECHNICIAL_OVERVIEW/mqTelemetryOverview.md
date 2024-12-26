IBM MQ Telemetry, uzak cihazlardan veri toplama ve bu cihazların kontrolünü sağlama hizmeti sunan bir teknolojidir. MQ Telemetry, IoT (Nesnelerin İnterneti) cihazlarını ve diğer uzak cihazları IBM MQ ile bağlar ve düşük maliyetle bu cihazlardan veri toplama ve kontrol etme işlemlerini sağlar.
MQ Telemetry'nin Temel Bileşenleri:
	1. Telemetri Kanalları: MQTT istemcilerinin IBM MQ'ya bağlanmasını yönetir. Yeni IBM MQ nesneleri, örneğin SYSTEM.MQTT.TRANSMIT.QUEUE, kullanılarak bu etkileşim sağlanır.
	2. Telemetri (MQXR) Servisi: MQTT istemcileri, telemetri kanallarına bağlanmak için SYSTEM.MQXR.SERVICE servisini kullanır.
	3. IBM MQ Explorer Desteği: IBM MQ Explorer, MQ Telemetry'nin yönetilmesini sağlar.
	4. Dokümantasyon: IBM MQ dokümantasyonu içinde yer alır ve Java ile C istemcileri için SDK dökümantasyonu sağlanır.
Temel Telemetri Kavramları:
Telemetri, uzak cihazlardan veri toplama, ölçüm yapma ve bu cihazların kontrolünü sağlama işlemidir. Uygulama geliştiricileri, cihazlardan veri alarak bu verileri merkezi bir kontrol noktasına iletebilir ve burada analiz edebilirler. Bu veri, sistemlerin karar vermesine yardımcı olur.
MQ Telemetry'nin Kullanım Alanları:
	• MQTT İstemcileri: Telemetri cihazlarından gelen verileri toplayan ve sunucuya ileten uygulamalar. Ayrıca bu istemciler, belirli konuları (topic) abone olarak dinler ve bu konulara yönelik yayınlar alabilir.
	• Mesaj Gönderimi: IBM MQ uygulamaları, MQTT istemcilerine mesaj gönderirken, bu mesajlar istemcilerin abone olduğu konulara yönelik yayınlar yapılarak iletilir.
	• Stateless ve Stateful Oturumlar: MQTT istemcileri, bağlandıkları queue manager ile stateful oturumlar oluşturabilirler. Bağlantı koparsa, queue manager, istemcinin aboneliklerini ve iletilmemiş mesajları saklar ve istemci yeniden bağlandığında mesajlar iletilir.
	• Güvenlik: Telemetri cihazlarının güvenliği önemlidir. VPN, TLS ve JAAS gibi güvenlik mekanizmaları kullanılarak bu cihazlar güvenli hale getirilebilir.
Performans ve Ölçeklenebilirlik:
MQ Telemetry, cihaz sayısının arttığı durumlarda yüksek performans sunabilmek için optimize edilmiştir. Düşük bant genişliğine sahip ağlarda bile güvenilir mesaj iletimi sağlar.
MQ Telemetry'nin Avantajları:
	• Düşük Maliyetli Veri Toplama: Cihazlardan veri toplamak için düşük maliyetli bir altyapı sağlar.
	• Esneklik: Her türlü cihazla çalışabilir, sensörlerden mobil cihazlara kadar geniş bir cihaz yelpazesini destekler.
	• Globalleşme Desteği: MQTT mesajları, UTF-8 formatında kodlanarak dünya genelinde farklı dillerle uyumlu çalışabilir.
Örnek Kullanım:
Bir örnek uygulama, deniz taşımacılığında kullanılan AIS (Automatic Identification System) verilerini toplayarak, Twitter ve SMS üzerinden yolculara geç kalkışlar hakkında bilgi verir. Bu, gerçek zamanlı veri akışı sağlayarak, yolcuların daha iyi kararlar almasına yardımcı olur.
Bu şekilde, MQ Telemetry, cihazlardan veri toplama ve bu verileri internet ve işletme sistemlerine entegre etme konusunda önemli avantajlar sağlar.
