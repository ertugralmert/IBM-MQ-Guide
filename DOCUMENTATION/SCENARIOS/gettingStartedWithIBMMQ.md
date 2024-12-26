1. IBM MQ Kurulumu (Grafiksel Kullanıcı Arayüzü ile)
Kurulum Adımları:
	1. IBM MQ'yu İndirin ve Kurulum Başlatın:
		○ IBM MQ'yu indirip kurulum başlatıcısını (Launchpad) çalıştırın.
		○ Kurulum sırasında, gerekli yazılım gereksinimlerini kontrol edin ve ağ bilgilerini girin.
		○ Kurulum sihirbazını izleyin ve IBM MQ yazılımını yükleyin.
	2. Queue Manager (Kuyruk Yöneticisi) Oluşturun:
		○ IBM MQ Explorer'ı açın ve yeni bir queue manager oluşturun. Burada "QM1" adında bir kuyruk yöneticisi yaratabilirsiniz.
		○ Queue manager, mesajlaşma işlemlerini yöneten ana bileşendir.
	3. Queue (Kuyruk) Oluşturun:
		○ LQ1 adında bir yerel kuyruk oluşturun. Bu kuyruk, mesajları depolayan bir veri yapısıdır.
	4. Mesaj Gönderme (Put Message):
		○ IBM MQ Explorer üzerinden LQ1 kuyruğuna bir mesaj gönderin. Örneğin, "Hello World" gibi basit bir mesaj gönderebilirsiniz.
	5. Mesaj Alma (Get Message):
		○ LQ1 kuyruğundaki mesajı almak için IBM MQ Explorer üzerinden mesajı alın. Bu, kuyruğa eklenen mesajın doğru bir şekilde işlendiğini doğrulamak içindir.


*****************


2. IBM MQ Kurulumu (Komut Satırı ile)
Kurulum Adımları:
	1. Silent (Sessiz) Kurulum Başlatın:
		○ IBM MQ'yu sessiz kurulumla komut satırından kurabilirsiniz. Bunun için aşağıdaki komutu kullanırsınız:msiexec /i "MQ_INSTALLATION_MEDIA\MSI\IBM MQ.msi" /l*v c:\wmqinslogs\install.log /q USEINI="MQ_INSTALLATION_MEDIA\Response.ini" TRANSFORMS="1033.mst" AGREETOLICENSE="yes" ADDLOCAL="Server"
		○ Bu komut, IBM MQ'yu sessiz bir şekilde yükler ve log dosyasına kurulum çıktısını kaydeder.
	2. Ortam Değişkenlerini Yapılandırın:
		○ IBM MQ’nun doğru çalışabilmesi için ortam değişkenlerini ayarlamanız gerekecek. Bu, setmqenv komutuyla yapılır:"MQ_INSTALLATION_PATH/bin/setmqenv" -s
	3. Queue Manager (Kuyruk Yöneticisi) Oluşturun:
		○ Aşağıdaki komutla QM1 adında bir kuyruk yöneticisi oluşturun:crtmqm QM1
		○ Sonrasında kuyruk yöneticisini başlatmak için şu komutu kullanın:strmqm QM1
	4. Queue (Kuyruk) Oluşturun:
		○ Komut satırında runmqsc komutuyla kuyrukları ve diğer MQ objelerini oluşturabilirsiniz. LQ1 adında bir kuyruk oluşturmak için:
		○ runmqsc QM1define qlocal(LQ1)end
	5. Mesaj Gönderme (Put Message):
		○ IBM MQ'nun sağladığı amqsput örnek uygulamasıyla kuyruğa mesaj gönderin:amqsput LQ1 QM1
		○ Bu komut ile kuyruğa "Hello World" mesajını gönderirsiniz.
	6. Mesaj Alma (Get Message):
		○ amqsget komutuyla kuyruğa eklediğiniz mesajı alabilirsiniz:amqsget LQ1 QM1
		
		
		
		
******************
3. IBM MQ'nun Uninstall Edilmesi
Eğer IBM MQ'yu kaldırmak isterseniz, aşağıdaki adımları izleyebilirsiniz:
	1. IBM MQ servisini durdurun.
	2. MQ'yu kaldırın ve kuyruk yöneticilerini de silin. Bu işlemle birlikte tüm IBM MQ nesneleri de silinir.




***************

4. Özet
Bu senaryonun amacı, IBM MQ'yu Windows üzerinde kurmak ve temel yapılandırmaları (queue manager ve queue oluşturma, mesaj gönderme ve alma) yapmaktır. Kurulumun ardından:
	• IBM MQ Explorer veya komut satırı üzerinden kuyruk yöneticisini ve kuyrukları yönetebilirsiniz.
	• Mesajlaşma işlemleri gerçekleştirebilir ve verilerin doğru bir şekilde iletilip alındığını doğrulayabilirsiniz.

