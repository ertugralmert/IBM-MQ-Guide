IBM MQ Internet Pass-Thru (MQIPT) Sorun Giderme
MQIPT kullanırken karşılaşabileceğiniz sorunları teşhis etmek ve çözmek için aşağıdaki adımları izleyin.

1. Genel Hataları Kontrol Etme
Sık Karşılaşılan Hatalar
	• HTTP Property Ayarı: HTTP=true olarak ayarlanmışsa, bu ayar doğrudan bir kuyruk yöneticisine bağlanılan bir rotada kullanılamaz.
	• SSLClient Property Ayarı: SSLClient=true olarak ayarlanmışsa, ancak kuyruk yöneticisi SSL/TLS kullanacak şekilde yapılandırılmamışsa sorun oluşur.
	• Anahtar Yüzüğü Şifreleri: Anahtar yüzüğü (key ring) dosyalarının şifreleri büyük/küçük harfe duyarlıdır.
FFST Raporlarını Kontrol Edin
	• Hatalar Alt Dizini: errors alt dizininde FFST raporlarını kontrol edin.
	• FFST raporları varsa, MQIPT doğru kurulmuş, ancak yapılandırmada bir sorun olabilir.
		○ Sorunu düzeltin, eski FFST’yi silin ve MQIPT’yi yeniden başlatın.
MQIPT’yi Manuel Başlatma
	• Kurulumun doğru olup olmadığını test etmek için:mqipt xxx
		○ xxx, MQIPT ana dizinini belirtir.
		○ Çıktıdaki hata mesajlarını ve FFST örneklerini inceleyin.

2. Bağlantı Sorunları
Bağlantı Günlüğü
	• ConnectionLog Property: ConnectionLog=true olarak ayarlayın ve MQIPT’yi yeniden başlatın.
		○ Günlük Yoksa: MQIPT doğru kurulmamış olabilir.
		○ Bağlantı Kayıtlı Değilse: Gönderen doğru yapılandırılmamış olabilir.
		○ Bağlantı Kayıtlıysa: MQIPT’nin mesajları doğru adres ve porta yönlendirdiğini doğrulayın.

3. Windows Sunucusunda MQIPT’nin Başlatılamaması
Registry Ayarlarını Kontrol Edin
	• Windows Registry Editor’da şu anahtarı kontrol edin:HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\MQInternetPassThru
		○ ConfigFilePath ayarının doğru mqipt.conf yolunu gösterdiğinden emin olun.
		○ ImagePath ayarının doğru mqiptService.exe yolunu gösterdiğinden emin olun.
Hata Teşhisi İçin Debug Modunu Etkinleştirme
	• Şu komutu çalıştırarak Windows Olay Günlüğüne detaylı bilgiler yazdırabilirsiniz:mqiptService -debugevent
UTF-8 Kodlama Sorunu
	• mqipt.conf dosyasını Notepad ile düzenliyorsanız, dosyayı ANSI olarak kaydedin:
		○ File > Save As > Encoding: ANSI

4. İzleme ve Hata Ayıklama
İzleme Seviyesini Artırma
	• Trace Property: İzleme seviyesini artırmak için Trace=5 olarak ayarlayın. Örnek yapılandırma:[global]Trace=5
	• İzleme dosyası, errors dizininde oluşturulur.
JRE Teşhis Seçenekleri
	• SSL/TLS hatalarını teşhis etmek için:-Djavax.net.debug=all
	• Güvenlik politikası sorunlarını teşhis etmek için:-Djava.security.debug=access,failure
JRE Teşhis Komutları
	• Linux ve AIX:MQIPT_JVM_OPTIONS="-Djavax.net.debug=all -Djava.security.debug=access,failure"export MQIPT_JVM_OPTIONS
	• Windows:set MQIPT_JVM_OPTIONS=-Djavax.net.debug=all -Djava.security.debug=access,failure
	• Bu ayarların etkili olması için MQIPT’yi yeniden başlatmanız gerekir.

5. Bağlantıyı Otomatik Başlatma
	• Windows Hizmeti: MQIPT’yi bir Windows hizmeti olarak kurduysanız, sistemle birlikte başlaması gerekir.
	• Hizmet başlamıyorsa:
		1. mqipt.conf ve mqiptService.exe yollarını kontrol edin.
		2. İlgili hata günlüklerini ve FFST kayıtlarını inceleyin.
		3. Gerekirse izleme modunu etkinleştirin ve destek için IBM’e başvurun.
