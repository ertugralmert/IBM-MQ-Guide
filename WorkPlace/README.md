1. Mevcut Yapımız Nasıl Çalışıyor?
	• Red Hat (Gönderici):
		○ TEST.REMOTE adlı bir Remote Queue üzerinden mesaj gönderiyor.
		○ Mesajlar önce WINDOWS.TRANSMIT.QUEUE adlı bir Transmission Queue'ya düşüyor.
		○ Bu mesajlar, REDHAT.TO.WINDOWS adlı bir Sender Channel kullanılarak Windows’a iletiliyor.
		○ Listener (REDHAT.LISTENER), gelen bağlantıları dinliyor.
	• Windows (Alıcı):
		○ REDHAT.TO.WINDOWS adlı bir Receiver Channel aracılığıyla Red Hat'ten gelen mesajları alıyor.
		○ Gelen mesajlar, TEST.QUEUE adlı bir Local Queue'ya düşüyor.
		○ Mesajlar burada işlemeye hazır hale geliyor.
Bu yapı, tek yönlü bir mesajlaşma sistemi: Red Hat mesaj gönderiyor, Windows bu mesajları alıyor.

2. İki Taraflı Mesajlaşma Mümkün mü?
Evet.
Nasıl Kurulur?
	1. Windows'tan Red Hat’e Mesaj Göndermek için:
		○ Windows tarafında:
			§ Remote Queue: Red Hat'teki bir Local Queue'yu işaret eden bir Remote Queue oluşturulur (ör. REDHAT.REMOTE).
			§ Transmission Queue: Mesajların Red Hat’e gönderilmesi için kullanılır (ör. REDHAT.TRANSMIT.QUEUE).
			§ Sender Channel: Windows’tan Red Hat’e mesaj göndermek için bir Sender Channel oluşturulur (ör. WINDOWS.TO.REDHAT).
		○ Red Hat tarafında:
			§ Receiver Channel: Windows’tan gelen mesajları almak için bir Receiver Channel oluşturulur (ör. WINDOWS.TO.REDHAT).
			§ Local Queue: Windows’tan gelen mesajların düşeceği bir Local Queue oluşturulur (ör. REDHAT.QUEUE).
	2. İki Taraflı Mesajlaşma Yapısı:
		○ Red Hat'ten Windows’a: Zaten kurulu olan yapı kullanılabilir.
		○ Windows’tan Red Hat’e: Yukarıdaki yeni yapı eklenir.
Önerilir mi?
	• Evet, ancak karmaşıklığı artırdığı için dikkatli yönetilmelidir.
	• İki taraflı mesajlaşmada, her iki Queue Manager’ın da düzgün yapılandırılmış olması gerekir.
	• Güvenlik, izleme ve hata yönetimi gibi konular öncelikli olmalıdır.

3. Ubuntu’da MQ Kurulursa Yapı Nasıl Olur?
Eğer Ubuntu'ya MQ kurulursa, üç farklı makine arasında mesajlaşmayı sağlayan bir yapı oluşturulabilir. Örnek yapı şu şekilde olabilir:
A. Ubuntu Gönderici, Windows Alıcı
	• Ubuntu üzerinde:
		○ Queue Manager (ör. QM3).
		○ Transmission Queue (WINDOWS.TRANSMIT.QUEUE).
		○ Remote Queue (TEST.REMOTE), Windows'taki TEST.QUEUE'yi işaret eder.
		○ Sender Channel (UBUNTU.TO.WINDOWS).
		○ Listener (UBUNTU.LISTENER).
	• Windows üzerinde:
		○ Receiver Channel (UBUNTU.TO.WINDOWS).
B. Windows Gönderici, Ubuntu Alıcı
	• Windows üzerinde:
		○ Transmission Queue (UBUNTU.TRANSMIT.QUEUE).
		○ Remote Queue (UBUNTU.REMOTE), Ubuntu'daki bir Local Queue’yu işaret eder.
		○ Sender Channel (WINDOWS.TO.UBUNTU).
	• Ubuntu üzerinde:
		○ Receiver Channel (WINDOWS.TO.UBUNTU).
		○ Local Queue (UBUNTU.QUEUE).
C. Red Hat ve Ubuntu Birbirine Bağlanır mı?
	• Evet, bu durumda Red Hat ve Ubuntu arasında da aynı şekilde Sender/Receiver Channels, Transmission/Remote Queues yapılandırılabilir. Örneğin:
		○ Red Hat: REDHAT.TO.UBUNTU ve REDHAT.TRANSMIT.QUEUE.
		○ Ubuntu: REDHAT.TO.UBUNTU ve UBUNTU.QUEUE.
Üç Sistemli Mesajlaşma:
	• Red Hat, Windows ve Ubuntu üçgeninde, her sistem arasında kanallar kurulur.
	• Her Queue Manager birbirine bağlanabilir, ancak tasarım karmaşıklaşır.

4. IBM MQ Explorer ile İzleme
IBM MQ Explorer’ı kullanarak tüm Queue Manager’ları tek bir yerden izleyebilirsiniz:
Red Hat ve Ubuntu'yu Eklemek için:
	1. IBM MQ Explorer’da "Queue Manager ekleme" seçeneğini kullanın.
	2. Red Hat (veya Ubuntu) Queue Manager’ının:
		○ Host IP adresi (ör. 192.168.142.128).
		○ Port numarası (ör. 1414).
		○ Queue Manager adı (ör. QM2 veya QM3).
	3. Bağlantıyı test edin ve izlemeye başlayın.
Explorer ile Yapılabilecekler:
	• Queue Manager’ları durdurup başlatabilirsiniz.
	• Kanal durumlarını görüntüleyip sorun giderebilirsiniz.
	• Kuyruklardaki mesajları görebilir ve yönetebilirsiniz.

5. Oluşturulan Yapıda Neler Yaptık?
Red Hat Üzerinde:
	• Queue Manager (QM2).
	• Transmission Queue (WINDOWS.TRANSMIT.QUEUE).
	• Remote Queue (TEST.REMOTE).
	• Sender Channel (REDHAT.TO.WINDOWS).
	• Listener (REDHAT.LISTENER).
Windows Üzerinde:
	• Queue Manager (QM1).
	• Local Queue (TEST.QUEUE).
	• Receiver Channel (REDHAT.TO.WINDOWS).
	• Listener (WIN.LISTENER).

6. Kaç Listener ve Channel Olacak?
	1. Her Queue Manager için en az 1 Listener gerekir. Her Queue Manager gelen bağlantıları dinlemek için bir Listener’a ihtiyaç duyar.
	2. Kanallar (Channels):
		○ Her iki yönlü iletişim için bir Sender Channel ve bir Receiver Channel çifti gerekir.
		○ Örneğin:
			§ Red Hat’ten Windows’a: 1 Sender + 1 Receiver Channel.
			§ Windows’tan Red Hat’e: 1 Sender + 1 Receiver Channel.

7. Önerilerim
	1. Karmaşıklığı Azaltın:
		○ İlk aşamada tek yönlü iletişim kullanın.
		○ Çok yönlü iletişime geçtiğinizde güvenlik ve hata yönetimi için dikkatli olun.
	2. Queue İsimlendirme Standartları Kullanın:
		○ Ör. APP.REQUEST.QUEUE, APP.RESPONSE.QUEUE gibi anlamlı isimler kullanın.
	3. Güvenliği İhmal Etmeyin:
		○ SSL/TLS yapılandırmaları ekleyin.
		○ Kullanıcı erişim kontrollerini (MCAUSER ve CHLAUTH) uygulayın.
	4. İzleme Araçlarını Kullanın:
		○ IBM MQ Explorer üzerinden tüm sistemleri izleyin.
		○ Alternatif olarak Prometheus/Grafana gibi araçlarla metrikleri görselleştirin.
	5. Hata Yönetimi Ekleyin:
		○ Dead Letter Queue (DLQ) oluşturun. Gönderilemeyen mesajlar burada toplanır.

