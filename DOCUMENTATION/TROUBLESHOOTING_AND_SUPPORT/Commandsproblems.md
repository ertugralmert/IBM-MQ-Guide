IBM MQ Advanced Message Security (AMS) Sorun Giderme
IBM MQ Advanced Message Security (AMS) ile ilgili sorunları tanımlayıp çözmek için aşağıdaki bilgileri ve adımları kullanabilirsiniz.

1. Genel Yaklaşım
	1. Hata Loglarını Kontrol Edin:
		○ Queue manager hata loglarını inceleyin:cat {MQ_DATA_PATH}/errors/AMQERR01.LOG
		○ Daha fazla bilgi için Error logs on AIX, Linux, and Windows bağlantısını takip edin.
	2. Kriptografik Algoritma Sorunları:
		○ Eğer aşağıdaki gibi bir hata alıyorsanız:com.ibm.security.pkcsutil.PKCSException: Error encrypting contentsjava.security.InvalidKeyException: Illegal key size or default parameters
			§ JCE güvenlik politikalarını kontrol edin:
				□ JAVA_HOME/lib/security/local_policy.jar/*.policy dosyasını kontrol ederek kullanılan imzalama algoritmalarına izin verildiğinden emin olun.
			§ İlgili Java politikası dosyasını IBM Developer Kits'ten indirin.

2. OSGi ile AMS Kullanımı
Eğer AMS'yi bir OSGi Bundle içinde kullanıyorsanız, ek yapılandırma gerekebilir:
	1. Başlangıç Parametresi:-Dorg.osgi.framework.system.packages.extra=com.ibm.security.pkcs7
	2. Şifrelenmiş Parola Desteği:
		○ Keystore.conf dosyasındaki şifreli parolalar için aşağıdaki parametreyi ekleyin:-Dorg.osgi.framework.system.packages.extra=com.ibm.security.pkcs7,com.ibm.misc
	Kısıtlama: OSGi Bundle içinde korunan sıralar için yalnızca MQ Base Java Sınıfları desteklenir.

3. Korunan Kuyrukları Açarken Yaşanan Sorunlar
Hata Durumu
	• JMS uygulaması çalıştırılırken şu hataları alabilirsiniz:
		○ 2085 (MQRC_UNKNOWN_OBJECT_NAME)
		○ JMSMQ2008
Çözüm Yöntemleri
	1. Desteklenen IBM JRE Kullanımı:
		○ Uygulamanızı desteklenen bir IBM Java Çalışma Ortamında (JRE) çalıştırmayı deneyin.
	2. Bindings Mode Kullanımı:
		○ Uygulamayı, queue manager'ın çalıştığı makinede çalıştırarak bindings mode bağlantısı kullanın.
			§ Bindings Mode, platformun doğal kütüphanelerini kullanır ve AMS işlemleri için JRE'ye bağımlılığı ortadan kaldırır.
	3. MCA Interceptor Kullanımı:
		○ Message Channel Agent (MCA) Interceptor kullanarak mesajların kuyruk yöneticisine ulaştığında imzalanmasını ve şifrelenmesini sağlayabilirsiniz.
		○ TLS Şifreleme: MCA Interceptor, istemci ve queue manager arasında veri koruması sağlamak için TLS şifreleme gerektirir.
			§ Server bağlantı kanalı üzerinde TLS yapılandırmasını kontrol edin:DISPLAY CHANNEL(SYSTEM.DEF.SVRCONN) SSLCIPH
	4. AMS’yi Devre Dışı Bırakma:
		○ Eğer AMS'yi istemiyorsanız aşağıdaki ortam değişkenini ayarlayın:export AMQ_DISABLE_CLIENT_AMS=1
Not:
	• Her kuyruk için bir güvenlik politikası tanımlanmalıdır.
	• MCA Interceptor'un kullandığı sertifikanın DN (Distinguished Name) değeri, hedef kuyruk politikası ile eşleşmelidir:
		○ cms.certificate.channel.SYSTEM.DEF.SVRCONN parametresi, keystore.conf dosyasındaki sertifikaya işaret etmelidir.

Önemli Notlar
	• Eğer sorunlar devam ediyorsa veya daha karmaşık bir problemle karşılaşıyorsanız, logları detaylı bir şekilde inceleyerek IBM Support ile iletişime geçebilirsiniz.
	• Güvenlik politikalarını doğru yapılandırdığınızdan ve sertifikaların geçerli olduğundan emin olun.
