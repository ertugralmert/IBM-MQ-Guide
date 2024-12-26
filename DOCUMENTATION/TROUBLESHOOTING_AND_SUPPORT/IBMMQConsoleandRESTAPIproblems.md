IBM MQ Console ve REST API Sorun Giderme
IBM MQ Console veya REST API ile ilgili sorunlar yaşıyorsanız, aşağıdaki adımları izleyerek sorunları teşhis edebilir ve çözebilirsiniz.

1. mqweb Sunucusunun Durumu
mqweb Durumunu Kontrol Etme
	• IBM MQ Console veya REST API çalışmıyorsa, mqweb sunucusu durmuş olabilir. Durumu kontrol etmek için şu komutu çalıştırın:dspmqweb status
mqweb Sunucusunu Başlatma
	• Eğer sunucu durduysa şu komutla başlatın:bashCopy codestrmqweb
z/OS İçin Önemli Bilgiler
	• WLP_USER_DIR değişkenini ayarlayın:export WLP_USER_DIR=/var/mqm/web/installation1

2. mqweb Yapılandırma Dosyalarını Kontrol Edin
	• Yapılandırma dosyaları şunlardır:
		○ jvm.options
		○ mqwebuser.xml
		○ server.xml
	• Bu dosyaların yerini kontrol etmek için:crtmqdir -a
	• Eğer dosyalar eksikse şu komutla yeniden oluşturabilirsiniz:crtmqdir -s -f

3. Günlük Dosyalarını İnceleme
	• Günlük dosyalarının konumu:
		○ Linux, Windows, AIX: MQ_DATA_PATH/web/installations/installationName/servers/mqweb/logs
		○ z/OS: /var/mqm/web/installation1/servers/mqweb/logs
	• İnceleyin:
		○ console.log
		○ messages.log
z/OS İçin Ek Kontroller
	• STDERR ve STDOUT çıktılarını kontrol edin. STDERR yalnızca hata durumunda mesaj içerir.

4. Uzaktan Bağlantılar İçin Yapılandırma
	• Uzaktan bağlantılar için sunucu yapılandırmasını kontrol edin:dspmqweb properties -a
	• Eğer httpHost değeri localhost ise, sadece aynı sistemden erişim sağlanabilir. Uzaktan bağlantıları etkinleştirmek için:setmqweb properties -k httpHost -v "*"

5. Kuyruk Yöneticilerinin Görünürlüğünü Kontrol Etme
	• IBM MQ Console'da yerel kuyruk yöneticileri görünmüyorsa:
		○ mqweb sunucusu ile aynı kurulumdaki kuyruk yöneticilerini kontrol edin.
		○ z/OS: Kuyruk yöneticilerinin IBM MQ Console ile aynı sürümde çalıştığından emin olun.

6. Mesaj Görüntüleme ve REST API Sorunları
a. Mesajların Kısaltılması
	• Kuyrukları görüntülerken mesajlar kısaltılıyorsa, aşağıdaki yapılandırmayı artırabilirsiniz:
		○ mqConsoleMaxMsgCharsToDisplay
		○ mqConsoleMaxMsgRequestSizesetmqweb properties -k mqConsoleMaxMsgCharsToDisplay -v 10000
b. REST API Sorunları
	• Uzak Kuyruk Yöneticilerine Bağlantı
		○ Kuyruk yöneticisi adı yerine benzersiz adı kullandığınızdan emin olun.
		○ REST API’nin görebileceği kuyruk yöneticilerinde visibility parametresini kontrol edin:dspmqweb remote
		○ CCDT Dosyası:
			§ ccdtUrl parametresinin doğru konumu belirttiğinden emin olun.

7. Genel Sorun Çözme ve İzleme
a. İletişim Hatası
	• Eğer şu mesajı alıyorsanız:Lost communication with the server
		○ STEPLIB kütüphanelerinin doğru seviyede ve APF yetkili olduğundan emin olun.
		○ Yolları doğrulayın:
			§ INSTDIR, USERDIR, PATH, ve LIBPATH
b. İzleme ve Hata Ayıklama
	• IBM MQ Console ve REST API için izleme etkinleştirin. Daha fazla bilgi için:
		○ Tracing the REST API
		○ Tracing the IBM MQ Console
