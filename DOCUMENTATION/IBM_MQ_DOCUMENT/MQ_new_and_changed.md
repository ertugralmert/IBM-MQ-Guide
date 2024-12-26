IBM MQ 9.4.0 sürümü, IBM MQ 9.3.0'dan sonra gelen Long Term Support (LTS) sürümüdür ve aynı zamanda IBM MQ 9.3.5'in devamı olarak Continuous Delivery (CD) sürümüdür. Bu sürüm, önceki CD sürümlerinde yer alan özelliklerin yanı sıra yeni özellikler ve iyileştirmeler de içermektedir. İşte IBM MQ 9.4.0'daki yenilikler ve değişikliklerin ana hatları:
Yeni Özellikler ve İyileştirmeler
Multiplatforms - Base ve Advanced Entitlement
	• Yükleme ve Göç: Windows ve Linux üzerinde bakım uygulama için yeni bir yöntem eklenmiştir.
	• Güvenlik:
		○ JWT (JSON Web Token) desteği ve token tabanlı kimlik doğrulama.
		○ MQCSP şifre korumasındaki değişiklikler.
		○ TLS 1.3 desteği, yönetilen .NET istemcileri için sağlanmıştır.
	• Yönetim:
		○ IBM MQ Console'a yeni iyileştirmeler yapılmıştır.
		○ Dışa aktarma işlevselliği ve yeni bir "CAPEXPRY" özelliği eklenmiştir.
		○ OpenTelemetry izleme desteği.
		○ LZ4 sıkıştırma desteği eklenmiştir.
Uygulama Geliştirme
	• Yeni Performans İyileştirmeleri: AMQP mesaj onaylamalarındaki işlem iyileştirmeleri.
	• .NET ve XMS .NET için yeni iyileştirmeler.
	• JMS ve Jakarta Messaging için iyileştirmeler: TCP/IP bağlantılarını paylaşma ve modüler uygulamalar kullanma.
IBM MQ Advanced için Yeni Özellikler
	• Native HA (Yüksek Erişilebilirlik) için yeni haklar.
	• AWS ve Azure Marketplace üzerinden IBM MQ entegrasyonu.
z/OS - Base ve Advanced VUE Entitlement
	• Yeni Güvenlik Özellikleri: REST API için kullanıcı bağlamı ayarları.
	• Z/OS için daha fazla iyileştirme: SMF kuyruk istatistikleri ve yeni yönetim komutları.
Değişiklikler ve Kaldırılan Özellikler
	• Yeni ve Değiştirilen Mesajlar: IBM MQ 9.3.0'dan bu yana bazı yeni mesajlar eklendi ve eski mesajlar değiştirildi.
	• Eski Özellikler: Bazı özellikler IBM MQ 9.4.0'dan itibaren kullanımdan kaldırıldı veya istikrara kavuştu.
	• Lisans ve Kurulum Değişiklikleri: setmqinst komutunun nonprod (üretim dışı) lisanslama için yapılan değişiklikler.
	• Güvenlik Değişiklikleri: AMQP kanalları için desteklenen keystore türlerinde değişiklikler ve FIPS modunda RSA anahtar değişiminin kaldırılması.
Bu sürümde, kullanıcılar güvenlik, yönetim, uygulama geliştirme ve platformlar arası özelliklerde önemli iyileştirmeler ve yeni yeteneklere erişebilecek. Ayrıca, birçok eski özellik kaldırılmış veya güncellenmiş durumda.
