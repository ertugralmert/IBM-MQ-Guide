MFT Yaygın Topolojileri
	• Tek bir kuyruk yöneticisi ile temel topoloji: Bu yapı, sadece bir kuyruk yöneticisi ile dosya transferi yapılandırması yapmanızı sağlar. Genellikle geliştirme aşamasında ya da sadece aynı sunucu üzerinde dosya taşımak için kullanılır.
	• Bir partner ajanı ile temel topoloji: Bu yapı, temel sunucu ve uzak bir partner sunucu arasındaki dosya transferini mümkün kılar.
	• Koordinasyon kuyruk yöneticisi ve bir partner ajanı ile temel topoloji: Bu yapıda, koordinasyon için ayrı bir kuyruk yöneticisi (örneğin MFT5) kullanılır ve temel sunucudaki başka bir kuyruk yöneticisi, ajan ve komut rolleri için kullanılır.
	• Bir MFT Ajanı partneri ile temel topoloji: Partner sunucu, IBM MQ sunucu yerine IBM MQ istemci bağlantısı kullanarak çalışır. Bu yapı, partnerin IBM MQ sunucusu olmadığında tercih edilir.
2. Temel Sunucunun Yapılandırılması
	• Koordinasyon Kuyruk Yöneticisi: Koordinasyon kuyruk yöneticisi (örneğin MFT5), dosya transferlerini yönetir.
		○ fteSetupCoordination komutunu çalıştırarak koordinasyon kuyruk yöneticisini yapılandırın.
		○ Koordinasyon kuyruk yöneticisinde gerekli IBM MQ tanımlarını oluşturmak için MQSC komut dosyasını çalıştırın.
	• Komut Kuyruk Yöneticisi: Komut kuyruk yöneticisi (örneğin MFT4), dosya transferlerine ilişkin komutları yönetir.
		○ fteSetupCommands komutunu çalıştırarak komut kuyruk yöneticisini yapılandırın.
	• Ajanın Yapılandırılması: Ajanlar, dosya transferlerini gerçekleştiren bileşenlerdir.
		○ fteCreateAgent komutunu kullanarak bir ajan oluşturun ve gerekli IBM MQ tanımlarını oluşturun.
		○ Ajanı fteStartAgent komutuyla başlatın ve fteListAgents komutuyla durumunu kontrol edin.
3. Logger (Kayıt Tutucu) Yapılandırması
	• Dosya transfer aktivitelerinin izlenmesi ve denetimi için bir logger (kayıt tutucu) gereklidir.
	• fteCreateLogger komutunu kullanarak dosya tabanlı bir logger oluşturun, dosya boyutu ve dosya sayısı parametrelerini belirleyin.
	• Logger'ı fteStartLogger komutuyla başlatın ve output0.log dosyasını kontrol ederek kayıtların yazıldığını doğrulayın.
4. Partner Sunucusunun Yapılandırılması
	• Partner Sunucu: Temel sunucunun koordinasyon kuyruk yöneticisi ayrı bir sunucuda ise, partner sunucu yapılandırılmalıdır.
	• Koordinasyon Kuyruk Yöneticisi Bağlantısı: Partner sunucusunun koordinasyon kuyruk yöneticisine bağlanması için fteSetupCoordination komutunu kullanın.
	• Komut Kuyruk Yöneticisi Bağlantısı: Partner sunucusundaki komut kuyruk yöneticisini fteSetupCommands komutuyla yapılandırın.
	• Partner Ajanının Yapılandırılması: Partner sunucusunda bir ajan oluşturun ve fteCreateAgent komutunu kullanarak IBM MQ tanımlarını oluşturun.
	• Ajanı fteStartAgent komutuyla başlatın ve fteListAgents komutuyla durumunu kontrol edin.
5. IBM MQ Explorer ile Test Yapılması
	• IBM MQ Explorer'ı Başlatma: IBM MQ Explorer'ı başlatın ve sol pencerede "Managed File Transfer" bölümüne gidin.
	• Koordinasyon Kuyruk Yöneticisine Bağlanma: Koordinasyon kuyruk yöneticisi MFT5’e sağ tıklayın ve "Connect" seçeneğini tıklayın.
	• Dosya Transferi Testi: Sağ tıklayıp "New Transfer" seçeneği ile dosya transferi başlatın. Kaynak ajanı (örneğin MFT4AGT1) ve hedef ajanı (örneğin CSMAGT1) seçin.
	• Transferin başarılı olup olmadığını kontrol edin. Eğer yeşil renkte başarı mesajı alırsanız, transfer başarılı olmuştur. Hata alırsanız, Transfer Log kısmından hata mesajlarını inceleyerek çözüm sağlayabilirsiniz.
