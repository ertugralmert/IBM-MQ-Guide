IBM MQ'de Java ve JMS Problemleri Sorun Giderme
IBM MQ ile Java ve JMS uygulamalarını çalıştırırken karşılaşılan yaygın sorunlar aşağıdaki yöntemlerle çözülebilir:

1. IBM MQ JMS Sınıflarında Sorun Giderme
Kurulum Doğrulama Programları
	• IBM MQ JMS sınıfları için kurulum doğrulama programlarını çalıştırarak sorunları analiz edebilirsiniz.
	• Örnek: Point-to-Point IVT ve Publish/Subscribe IVT testleri.
Loglama
	• Varsayılan log dosyası: mqjms.log.
	• Log çıktısını özel bir dosyaya yönlendirmek için şu özelliği tanımlayın:-Dcom.ibm.msg.client.commonservices.log.outputName=/path/to/mylog.txt
	• Loglamayı kapatmak için:-Dcom.ibm.msg.client.commonservices.log.status=OFF

2. JMS Sağlayıcı Versiyon Problemleri
Yaygın Hatalar
	1. JMSCC5008: JMS 2.0 işlevi, desteklenmeyen bir bağlantıda kullanılıyor.
		○ Çözüm: JMS 2.0 API'sini kullanmayı bırakın veya IBM MQ 8 sürümü modundaki bir kuyruğa bağlanın.
	2. JMSCC5007: JMS 2.0 API, desteklenmeyen bir bağlantıda kullanılıyor.
		○ Çözüm: Normal modda çalışan bir kuyruğa bağlanın.
	3. JMSFMQ0003: Kuyruk yöneticisi komut seviyesi, istenen sağlayıcı sürümüyle uyumlu değil.
		○ Çözüm: Sağlayıcı sürümünü, kuyruk yöneticisiyle uyumlu olacak şekilde değiştirin.

3. PCF İşleme Sorunları
Sorun: Kodlama Uyumsuzluğu
	• Big-endian ve little-endian platformlarda PCF mesajları kodlama farkları nedeniyle hata verebilir.
	• Hata Mesajı: MQRCCF_STRUCTURE_TYPE_ERROR (3013)
Çözüm
	• Örnek Kod:Message receivedMessage = consumer.receive(10000);BytesMessage bytesMessage = (BytesMessage) receivedMessage;byte[] bytesReceived = new byte[(int) bytesMessage.getBodyLength()];bytesMessage.readBytes(bytesReceived);MQMessage mqMsg = new MQMessage();mqMsg.write(bytesReceived);mqMsg.encoding = receivedMessage.getIntProperty("JMS_IBM_Encoding");mqMsg.format = receivedMessage.getStringProperty("JMS_IBM_Format");mqMsg.seek(0);PCFMessage pcfMsg = new PCFMessage(mqMsg);

4. Bağlantı Havuzu Hata Yönetimi
Purge Policy
	• FailingConnectionOnly (Varsayılan): Sadece sorunlu bağlantı kapatılır.
	• EntirePool: Tüm havuzdaki bağlantılar kapatılır ve uygulamalar yeni bağlantı oluşturur.
Hangisini Seçmelisiniz?
	• EntirePool genellikle daha güvenilir bir seçenektir, çünkü aynı ağ sorunları havuzdaki diğer bağlantıları da etkileyebilir.

5. JMSCC0108 Mesajları
Nedenler ve Çözümler
	1. Mesaj Başka Bir Uygulama Tarafından Tüketildi:
		○ Çözüm: MARKINT süresini artırarak aynı mesajın farklı süreçlerce görülmesini engelleyin.
	2. Mesaj Süresi Doldu:
		○ Çözüm: Sunucu oturum havuzu boyutunu artırarak mesajların süresi dolmadan işlenmesini sağlayın.
	3. ReadAhead Özelliği Etkin:
		○ Çözüm: Bu özelliği kapatmayı düşünün.

6. 2035 MQRC_NOT_AUTHORIZED Hatası
Yaygın Nedenler
	1. Kullanıcı adı bilinmiyor veya yetkilendirilmemiş.
	2. Kullanıcı adı 12 karakterden uzun ve kesilmiş.
	3. CHLAUTH kaydı, yönetici erişimini engelliyor.
Çözüm
	• Geliştirme ortamında:
		○ MCAUSER özelliği ile uygun kullanıcı adı belirleyin.
		○ CHLAUTH kuralını düzenleyerek yönetici bağlantılarını izin verin:SET CHLAUTH('WAS.CLIENTS') TYPE(BLOCKUSER) USERLIST(ALLOWANY)
	• Üretim ortamında:
		○ SSL/TLS Güvenliği: Karşılıklı SSL/TLS doğrulama yapılandırın.
		○ Tüm yetkisiz kanalları devre dışı bırakın:ALTER CHL(SYSTEM.DEF.SVRCONN) CHLTYPE(SVRCONN) MCAUSER('NOAUTH') STOP CHL(SYSTEM.DEF.SVRCONN)

7. Kaynak Bağdaştırıcı Sorunları
Yaygın Sorunlar
	1. Kaynak Bağdaştırıcı Dağıtım Hataları:
		○ Yanlış JCA veya IBM MQ sınıf yolu.
	2. MDB Dağıtım Sorunları:
		○ Eksik kaynaklar veya yanlış ActivationSpec tanımı.
	3. Bağlantı Oluşturma Sorunları:
		○ Yanlış bağlantı parametreleri veya kullanıcı yetkilendirme hataları.
Çözüm
	• Kaynak Bağdaştırıcı İzleme: Logları ve hata raporlarını inceleyin.
	• Doğru JAR Dosyaları: IBM MQ tarafından sağlanan doğru sürümleri kullanın.
