XMS .NET Sorunlarını Giderme Rehberi
IBM MQ ve XMS .NET entegrasyonu sırasında karşılaşılabilecek sorunları çözmek için bir rehber.

1. Genel Sorunlar ve Çözümler
1.1 XMS Uygulaması Kuyruk Yöneticisine Bağlanamıyor
	• Hata Kodu: MQRC_NOT_AUTHORIZED
	• Sebep:
		○ XMS .NET istemcisi, IBM MQ JMS istemcisinden farklı davranışlar sergileyebilir. Bu durum, JMS istemcisinin bağlanabildiği bir kuyruk yöneticisine XMS istemcisinin bağlanamamasıyla sonuçlanabilir.
	• Çözüm:
		○ 12 karakterden kısa bir kullanıcı kimliği kullanmayı deneyin.
		○ Kullanıcı kimliğinizin kuyruk yöneticisinde tam yetkiye sahip olduğundan emin olun.
		○ Gerekirse güvenlik çıkışlarını (security exits) kullanmayı değerlendirin.
1.2 Kullanıcı Kimliği ve Parola
	• Not: XMSC_USERID özelliği ayarlandığında, bu kimlik giriş yapmış kullanıcı ile eşleşmelidir.
	• Çözüm:
		○ Kullanıcı kimliği ve parolayı XMSC_USERID ve XMSC.PASSWORD alanlarında doğru şekilde yapılandırın.
		○ Varsayılan olarak kuyruk yöneticisi, oturum açmış kullanıcının kimliğini kullanır.
1.3 WebSphere Application Server'a Bağlanma Sorunları
	• Sorun:
		○ Servis Entegrasyon Yolu (Service Integration Bus) bağlantıları, IP adresi yerine bir ana bilgisayar adına yönlendirilebilir.
	• Çözüm:
		○ İstemci makinenizin yerel ana bilgisayarlar (hosts) tablosunda ana bilgisayar adlarını ve IP adreslerini eşleyin.
1.4 SetDoubleProperty ve GetDoubleProperty Yöntemlerinde Hatalar
	• Sorun:
		○ 64-bit Windows platformlarında Double.Epsilon değerinden küçük çift (double) türleri doğru şekilde işlenmeyebilir.
	• Çözüm:
		○ Bu bilinen bir .NET Framework 2.0 sorunudur. Farklı bir platformda değerleri doğrulayarak çalışmayı deneyin.

2. SSL Hataları ve Çözümleri
2.1 IBM MQ 9.4.0'dan Önceki ve Sonraki Hata Mesajları
IBM MQ 9.4.0 itibarıyla, XMS .NET istemcisi SSL ile ilgili hatalar için daha açıklayıcı hata mesajları sağlamaktadır.
Senaryo	IBM MQ 9.4.0 Öncesi Hata Mesajı	IBM MQ 9.4.0 Hata Mesajı
Yanlış SSL anahtar deposu parametresi	2059 - MQRC_Q_MGR_NOT_AVAILABLE	2381 - MQRC_KEY_REPOSITORY_ERROR
Geçersiz şifreleme algoritması	2538 - MQRC_HOST_NOT_AVAILABLE	2393 - MQRC_KEY_REPOSITORY_ERROR
Geçersiz eş adı ayarı	2059 - MQRC_Q_MGR_NOT_AVAILABLE	2399 - MQRC_SSL_PEER_NAME_ERROR
Eş adlarının uyuşmaması	2059 - MQRC_Q_MGR_NOT_AVAILABLE	2398 - MQRC_SSL_PEER_NAME_ERROR
Geçersiz sertifika kullanımı	2059 - MQRC_Q_MGR_NOT_AVAILABLE	2393 - MQRC_KEY_REPOSITORY_ERROR
SSL için şifreleme algoritması belirtilmemesi	2059 - MQRC_Q_MGR_NOT_AVAILABLE	2393 - MQRC_KEY_REPOSITORY_ERROR
Şifreleme algoritması uyuşmazlığı	2059 - MQRC_Q_MGR_NOT_AVAILABLE	2393 - MQRC_KEY_REPOSITORY_ERROR
Anahtar deposu klasörü için izin eksikliği	2059 - MQRC_Q_MGR_NOT_AVAILABLE	2393 - MQRC_KEY_REPOSITORY_ERROR
2.2 Detaylı Çözümler
	• Anahtar Deposu Sorunları:
		○ SSL anahtar deposunun doğru şekilde yapılandırıldığından emin olun.
		○ Depo dosyasının IBM MQ süreçleri tarafından erişilebilir olduğundan emin olun.
	• Şifreleme Uyuşmazlıkları:
		○ İstemci ve sunucu tarafındaki şifreleme algoritmalarını uyumlu hale getirin.
	• Eş Adı Sorunları:
		○ Eş adı ayarlarının doğru ve uyumlu olduğundan emin olun.

3. Sorun Giderme İpuçları
3.1 SSL Hatalarını Anlamak
	• Hata mesajlarını ve kuyruk yöneticisi günlüklerini analiz edin:
		○ Günlük dosyalarını şu konumda bulabilirsiniz: MQ_DATA_DIRECTORY/qmgrs/errors/AMQERR*.log.
3.2 Bağlantı Yetkilendirme
	• IBM MQ'da bağlantı yetkilendirme kurallarını inceleyin.
	• Gerekirse yetkilendirme yapılandırmasını güncelleyin.
3.3 Platform Uyumluluğu
	• Çalışma ortamınızdaki platformlar (AIX, Linux, Windows) arasında veri tiplerinin uyumluluğunu doğrulayın.
