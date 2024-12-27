IBM MQ Windows Üzerinde Sorun Giderme Rehberi
IBM MQ kullanırken Windows platformunda karşılaşılabilecek sorunların belirlenmesi ve çözülmesi için aşağıdaki adımları takip edebilirsiniz. Bu rehber, olası nedenleri daraltmanıza ve sorunu hızlı bir şekilde çözmenize yardımcı olacaktır.

Başlangıç Kontrolleri
1. IBM MQ Daha Önce Başarıyla Çalıştı mı?
	• Eğer çalışmadıysa, kurulum ve yapılandırmanın doğru yapıldığından emin olun:
		○ IBM MQ Kurulum Kontrolü:
			§ Komut:

dspmq

Kuyruk yöneticilerini listeler.
			§ IBM MQ'nun düzgün kurulduğunu doğrulayın. Gerekirse IBM MQ Kurulum Doğrulama talimatlarına bakın.
2. Son Başarılı Çalışmadan Bu Yana Değişiklikler Yapıldı mı?
	• Kuyruk veya kanal tanımları değiştirildi mi?
	• Sisteme yeni yazılım veya donanım bileşenleri eklendi mi?
	• Windows Registry üzerinde IBM MQ'yu etkileyebilecek değişiklikler yapıldı mı?
3. Bakım Güncellemeleri Uygulandı mı?
	• Güncellemeler sırasında hata mesajları oluştu mu?
	• Güncellemelerin doğru uygulandığını test ettiniz mi?
4. Uygulama Daha Önce Başarıyla Çalıştı mı?
	• Uygulamada değişiklikler yapıldıysa, hatanın bu değişikliklerle ilişkili olup olmadığını kontrol edin.
	• Uygulama tüm fonksiyonlarını daha önce kullandı mı? Daha önce hiç çağrılmamış bir bölüm mü sorun çıkarıyor?
5. Sorun Tekrarlanabiliyor mu?
	• Sorunun oluşma koşullarını analiz edin:
		○ Belirli bir komut veya işlem mi soruna neden oluyor?
		○ Aynı işlem farklı yöntemlerle çalıştırıldığında sorun yaşanıyor mu?
		○ Belirli bir program çalışırken mi sorun oluşuyor?

Uygulama ve Mesaj Sorunları
Mesajlar Kuyruğa Ulaşmıyor
	• Kuyruk Ayarlarını Kontrol Edin:
		○ Komut:

DISPLAY QUEUE(queue_name) ALL

Kuyruğun PUT ve GET işlemlerine açık olup olmadığını kontrol edin.
		○ Kuyruk dolu mu? (MAXDEPTH sınırı kontrol edin.)
		○ Kuyruğa başka bir uygulama tarafından münhasır erişim sağlanmış olabilir mi?
	• Uygulama Kontrolleri:
		○ Uygulama başlatıldı mı? Tetikleme (triggering) ayarları doğru mu?
		○ Uygulama değişiklikleri commit etti mi, yoksa geri mi aldı?
Beklenmeyen veya Bozuk Mesajlar
	• Mesaj Verileri Beklendiği Gibi mi?
		○ Gönderici ve alıcı uygulamaların aynı mesaj formatını kullandığından emin olun.
		○ Mesajın yanlış bir kuyrukta olabileceğini kontrol edin. Gerekirse güvenlik ayarlarını gözden geçirin.
Dağıtık Kuyruklarda Beklenmeyen Mesajlar
	• Gönderici ve alıcı sistemlerin IBM MQ yapılandırmaları doğru mu?
	• Bağlantı Durumu Kontrolleri:
		○ Komut:

PING QMGR
PING CHANNEL(channel_name)

Hata Mesajları ve Geri Dönüş Kodları
Hata Günlüklerini Kontrol Edin
	• Windows Olay Günlükleri:
		○ Yol: "Bilgisayar Yönetimi > Olay Görüntüleyici > Uygulama."
		○ IBM MQ ile ilgili hata mesajlarını kontrol edin.
API Tamamlama ve Neden Kodları
	• Kod Listesi: Tamamlama ve Neden Kodları.

Uzaktan Kuyruk Sorunları
	• Kanal Durumları:
		○ Gerekli kanallar başlatılmış mı? Tetikleme ve başlatıcı ayarları doğru mu?
		○ Kanallarda herhangi bir uyumsuzluk var mı? (Örneğin, sekans numarası.)

Performans Sorunları
	• Donanım Kapasitesi:
		○ Sistem yükünün yüksek olduğu zamanlarda sorunlar oluşuyor mu?
		○ Sistem kaynak sınırlarını kontrol edin.
	• Uygulama Performansı:
		○ Sürekli yazma işlemleri birikmelere neden olabilir. Kalıcı mesajların işlenme biçimini kontrol edin.

IBM Destek ile Çalışma
Sorunları çözemezseniz, aşağıdaki bilgileri IBM'e iletin:
	1. Sorun Yeniden Yaratma Adımları.
	2. Günlük Dosyaları ve Hata Mesajları.
	3. Konfigürasyon Dosyaları ve Sistem Bilgileri.



IBM MQ kullanırken Linux üzerinde sorun giderme adımlarını açıklayan kapsamlı bir rehber paylaşıldı. Bu bilgileri, IBM MQ ile ilgili karşılaşabileceğiniz sorunları çözmek ve potansiyel nedenleri araştırmak için kullanabilirsiniz. Aşağıda, ana başlıklar ve detaylı kontrol yöntemleri yer alıyor:

Linux'ta Başlangıç Kontrolleri
IBM MQ veya bağlantılı uygulamalarda sorun yaşandığında, sorun gidermeye başlamadan önce aşağıdaki soruları göz önünde bulundurun:
	1. IBM MQ Daha Önce Başarıyla Çalıştı mı?
		○ Eğer hiç çalışmadıysa, kurulum ve yapılandırma adımlarını kontrol edin:
			§ Komut:

dspmq

Tüm kuyruk yöneticilerini listeler ve durumlarını kontrol eder.
		○ Doğrulama prosedürünü uygulayın: IBM MQ Doğrulama.
	2. Son Başarılı Çalıştırmadan Bu Yana Yapılan Değişiklikler Neler?
		○ Kuyruk veya kanal tanımları değişti mi?
		○ Temel sistem yapılandırması veya uygulamalar güncellendi mi?
	3. Bakım Güncellemeleri Uygulandı mı?
		○ Güncellemeler sırasında hata mesajı oluştu mu?
		○ Güncellemeler sonrasında doğrulama testleri yapıldı mı?
	4. Uygulama Daha Önce Başarıyla Çalıştı mı?
		○ Kodda yapılan yeni değişiklikler sonucu hatalar oluşmuş olabilir.
		○ Sorunlu bölümün yalnızca yeni çağrılan bir fonksiyon olup olmadığını kontrol edin.

Tipik Sorunlar ve Çözüm Yolları
1. Mesajlar Kuyruğa Ulaşmıyor
	• Kuyruğun doğru tanımlandığından emin olun:
		○ Komut:

DISPLAY QUEUE(queue_name) ALL

Kuyruk özelliklerini görüntüler.
	• Kuyruk GET ve PUT işlemlerine açık mı?
	• Kuyruk dolu mu? (MAXDEPTH kontrol edin.)
Mesaj Kuyruğa Konulamadıysa:
	• Gönderim uygulaması tetiklendi mi? (Trigger özelliklerini kontrol edin.)
	• Uygulama işlem değişikliklerini commit etti mi yoksa geri mi aldı?
Mesajlar Geliyorsa Ancak İşlenemiyorsa:
	• Mesaj formatı beklenenle uyumlu mu?
	• Mesaj persistent (kalıcı) olarak tanımlandı mı?

2. Dağıtık Kuyruklarla Çalışırken Beklenmeyen Mesajlar
	• Gönderici ve alıcı sistemlerin IBM MQ yapılandırması doğru mu?
	• İlgili bağlantılar aktif mi?
		○ Ping Komutları:

PING QMGR
PING CHANNEL(channel_name)
Önemli Kontroller:
	• Kanal tanımları uyumlu mu? (Örn. sekans numarası uyumsuzluğu.)
	• Veri dönüşümü yapılıyor mu? (Formatlar farklıysa otomatik dönüşüm gerekebilir.)

3. Uygulamalar veya Komutlardan Yanıt Gelmiyor
	• Komut sunucusu çalışıyor mu?
		○ Komut:

dspmqcsv

Komut sunucusunun durumunu kontrol eder.
	• Sistem hata günlüklerinde mesajlar var mı?
		○ Günlük dizini:

/var/mqm/errors/

Kaynak Problemleri ve Performans Sorunları
Kaynak Sınırlamaları Kontrolleri
	• Kullanıcı limitlerini kontrol edin:
		○ Komut:

ulimit -a

Tüm kullanıcı limitlerini listeler.
	• IBM MQ işlemlerini görüntüleyin:

ps -eLf | grep "amq" | wc -l
Gerekirse Ayarları Güncelleyin:
	• Kalıcı Değişiklikler İçin Dosyalar:

/etc/security/limits.conf
Shared Memory Kullanımı:
	• Shared memory sınırlarını kontrol edin:

ipcs -ma
Performans Sorunları:
	• Yüksek bellek veya CPU kullanımı olup olmadığını kontrol edin.
	• Tüm işlemler için thread limitlerini ayarlayın:

cat /proc/sys/kernel/threads-max

Hata Çözümünde IBM Desteği
IBM MQ hata mesajlarını ve neden kodlarını analiz ederek sorununuzu çözemiyorsanız, aşağıdaki bilgileri IBM Destek'e iletin:
	1. Sistem bilgileri ve MQ yapılandırma dosyaları.
	2. Sorunu Yineleme Adımları.
	3. Günlük dosyalarından ilgili kayıtlar.


IBM MQ Windows Üzerinde Sorun Giderme Rehberi
IBM MQ kullanırken Windows platformunda karşılaşılabilecek sorunların belirlenmesi ve çözülmesi için aşağıdaki adımları takip edebilirsiniz. Bu rehber, olası nedenleri daraltmanıza ve sorunu hızlı bir şekilde çözmenize yardımcı olacaktır.

Başlangıç Kontrolleri
1. IBM MQ Daha Önce Başarıyla Çalıştı mı?
	• Eğer çalışmadıysa, kurulum ve yapılandırmanın doğru yapıldığından emin olun:
		○ IBM MQ Kurulum Kontrolü:
			§ Komut:

dspmq

Kuyruk yöneticilerini listeler.
			§ IBM MQ'nun düzgün kurulduğunu doğrulayın. Gerekirse IBM MQ Kurulum Doğrulama talimatlarına bakın.
2. Son Başarılı Çalışmadan Bu Yana Değişiklikler Yapıldı mı?
	• Kuyruk veya kanal tanımları değiştirildi mi?
	• Sisteme yeni yazılım veya donanım bileşenleri eklendi mi?
	• Windows Registry üzerinde IBM MQ'yu etkileyebilecek değişiklikler yapıldı mı?
3. Bakım Güncellemeleri Uygulandı mı?
	• Güncellemeler sırasında hata mesajları oluştu mu?
	• Güncellemelerin doğru uygulandığını test ettiniz mi?
4. Uygulama Daha Önce Başarıyla Çalıştı mı?
	• Uygulamada değişiklikler yapıldıysa, hatanın bu değişikliklerle ilişkili olup olmadığını kontrol edin.
	• Uygulama tüm fonksiyonlarını daha önce kullandı mı? Daha önce hiç çağrılmamış bir bölüm mü sorun çıkarıyor?
5. Sorun Tekrarlanabiliyor mu?
	• Sorunun oluşma koşullarını analiz edin:
		○ Belirli bir komut veya işlem mi soruna neden oluyor?
		○ Aynı işlem farklı yöntemlerle çalıştırıldığında sorun yaşanıyor mu?
		○ Belirli bir program çalışırken mi sorun oluşuyor?

Uygulama ve Mesaj Sorunları
Mesajlar Kuyruğa Ulaşmıyor
	• Kuyruk Ayarlarını Kontrol Edin:
		○ Komut:

DISPLAY QUEUE(queue_name) ALL

Kuyruğun PUT ve GET işlemlerine açık olup olmadığını kontrol edin.
		○ Kuyruk dolu mu? (MAXDEPTH sınırı kontrol edin.)
		○ Kuyruğa başka bir uygulama tarafından münhasır erişim sağlanmış olabilir mi?
	• Uygulama Kontrolleri:
		○ Uygulama başlatıldı mı? Tetikleme (triggering) ayarları doğru mu?
		○ Uygulama değişiklikleri commit etti mi, yoksa geri mi aldı?
Beklenmeyen veya Bozuk Mesajlar
	• Mesaj Verileri Beklendiği Gibi mi?
		○ Gönderici ve alıcı uygulamaların aynı mesaj formatını kullandığından emin olun.
		○ Mesajın yanlış bir kuyrukta olabileceğini kontrol edin. Gerekirse güvenlik ayarlarını gözden geçirin.
Dağıtık Kuyruklarda Beklenmeyen Mesajlar
	• Gönderici ve alıcı sistemlerin IBM MQ yapılandırmaları doğru mu?
	• Bağlantı Durumu Kontrolleri:
		○ Komut:

PING QMGR
PING CHANNEL(channel_name)

Hata Mesajları ve Geri Dönüş Kodları
Hata Günlüklerini Kontrol Edin
	• Windows Olay Günlükleri:
		○ Yol: "Bilgisayar Yönetimi > Olay Görüntüleyici > Uygulama."
		○ IBM MQ ile ilgili hata mesajlarını kontrol edin.
API Tamamlama ve Neden Kodları
	• Kod Listesi: Tamamlama ve Neden Kodları.

Uzaktan Kuyruk Sorunları
	• Kanal Durumları:
		○ Gerekli kanallar başlatılmış mı? Tetikleme ve başlatıcı ayarları doğru mu?
		○ Kanallarda herhangi bir uyumsuzluk var mı? (Örneğin, sekans numarası.)

Performans Sorunları
	• Donanım Kapasitesi:
		○ Sistem yükünün yüksek olduğu zamanlarda sorunlar oluşuyor mu?
		○ Sistem kaynak sınırlarını kontrol edin.
	• Uygulama Performansı:
		○ Sürekli yazma işlemleri birikmelere neden olabilir. Kalıcı mesajların işlenme biçimini kontrol edin.

IBM Destek ile Çalışma
Sorunları çözemezseniz, aşağıdaki bilgileri IBM'e iletin:
	1. Sorun Yeniden Yaratma Adımları.
	2. Günlük Dosyaları ve Hata Mesajları.
	3. Konfigürasyon Dosyaları ve Sistem Bilgileri.



AMQP Sorunlarını Giderme
Log ve Konfigürasyon Dosyalarının Bulunması
	• AMQP ile ilgili hata loglarını ve yapılandırma dosyalarını kontrol edin:
		○ Varsayılan yollar:
			§ Loglar: {MQ_DATA_PATH}/errors
			§ Konfigürasyon dosyaları: amqptraceOn.properties, amqptraceOff.properties, amqp_java.properties.
JSON Loglama Aktifleştirme
	1. amqptraceOn.properties ve amqptraceOff.properties dosyalarını açın.
	2. Aşağıdaki gibi handlers ayarını değiştirin:
		○ Sadece JSON Loglama:

handlers= com.ibm.mq.util.logging.MQJSONErrorLogFileHandler
		○ Hem JSON hem metin tabanlı loglama:

handlers= com.ibm.mq.util.logging.MQErrorLogFileHandler, com.ibm.mq.util.logging.MQJSONErrorLogFileHandler
	3. AMQP servisini yeniden başlatın:

start SERVICE(SYSTEM.AMQP.SERVICE)
Düşük Bellek Hataları için Java Heap Dump Aktifleştirme
	1. amqp_java.properties dosyasını düzenleyin:

-Dcom.ibm.mq.MQXR.GenerateHeapDump=true
	2. AMQP servisini yeniden başlatın.
	3. Oluşan heap dump dosyasını {WMQ_DATA_PATH}/errors dizininde bulabilirsiniz.

Dağıtık Sıra Yönetimi Sorunlarını Giderme
Yaygın Sorunlar
	• Mesajların Kuyruğa Ulaşmaması:
		○ Kanal durumunu kontrol edin:

DISPLAY CHSTATUS(*)
		○ İletim kuyruğunun dolu olmadığından emin olun.
	• Dead-letter Queue Kullanımı:
		○ Teslim edilemeyen mesajlar için dead-letter kuyruğunu inceleyin:

DISPLAY QL(SYSTEM.DEAD.LETTER.QUEUE) ALL
	• Sıra Yöneticisi Bağlantı Sorunları:
		○ İki sistem arasındaki bağlantıyı doğrulamak için:

PING CHANNEL(channel_name)
Önemli MQSC Komutları
	• Kanalları başlatma veya durdurma:

START CHANNEL(channel_name)
STOP CHANNEL(channel_name)

Java ve JMS Sorunlarını Giderme
Yaygın Sorunlar
	• Bağlantı Hataları:
		○ CONNECTION_FACTORY ve QUEUE_CONNECTION_FACTORY ayarlarını doğrulayın.
		○ JMS dinleyici portlarının doğru yapılandırıldığından emin olun.
	• ClassNotFound veya NoClassDefFoundError:
		○ Gerekli tüm IBM MQ istemci kütüphanelerinin (örn. com.ibm.mqjms) classpath'te yer aldığından emin olun.
	• İşlem Geri Alım Sorunları:
		○ Uygulama kodunda işlemlerin doğru şekilde commit edildiğini kontrol edin.

Güvenlik Sorunlarını Giderme
Sertifika veya Kimlik Doğrulama Problemleri
	• SSL ayarlarını kontrol edin:

DISPLAY CHANNEL(channel_name) SSLCIPH
	• Kullanıcı yetkilerini inceleyin:

DISPLAY AUTHREC
Hata Logları
	• Güvenlikle ilgili logları kontrol edin:

{MQ_DATA_PATH}/errors/AMQERR01.LOG

Sıra Yöneticisi Sorunlarını Giderme
Sıra Yöneticisi Başlatılamıyor
	1. Hata loglarını kontrol edin:

cat {MQ_DATA_PATH}/errors/AMQERR01.LOG
	2. Sistem kaynaklarını doğrulayın:
		○ CPU ve bellek kullanımını kontrol edin.
		○ Uygulamalar arasındaki kaynak çatışmalarını analiz edin.


IBM MQ Advanced Message Security (AMS) Sorun Giderme
IBM MQ Advanced Message Security (AMS) ile ilgili sorunları tanımlayıp çözmek için aşağıdaki bilgileri ve adımları kullanabilirsiniz.

1. Genel Yaklaşım
	1. Hata Loglarını Kontrol Edin:
		○ Queue manager hata loglarını inceleyin:

cat {MQ_DATA_PATH}/errors/AMQERR01.LOG
		○ Daha fazla bilgi için Error logs on AIX, Linux, and Windows bağlantısını takip edin.
	2. Kriptografik Algoritma Sorunları:
		○ Eğer aşağıdaki gibi bir hata alıyorsanız:


com.ibm.security.pkcsutil.PKCSException: Error encrypting contents
java.security.InvalidKeyException: Illegal key size or default parameters
			§ JCE güvenlik politikalarını kontrol edin:
				□ JAVA_HOME/lib/security/local_policy.jar/*.policy dosyasını kontrol ederek kullanılan imzalama algoritmalarına izin verildiğinden emin olun.
			§ İlgili Java politikası dosyasını IBM Developer Kits'ten indirin.

2. OSGi ile AMS Kullanımı
Eğer AMS'yi bir OSGi Bundle içinde kullanıyorsanız, ek yapılandırma gerekebilir:
	1. Başlangıç Parametresi:

-Dorg.osgi.framework.system.packages.extra=com.ibm.security.pkcs7
	2. Şifrelenmiş Parola Desteği:
		○ Keystore.conf dosyasındaki şifreli parolalar için aşağıdaki parametreyi ekleyin:

-Dorg.osgi.framework.system.packages.extra=com.ibm.security.pkcs7,com.ibm.misc
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
			§ Server bağlantı kanalı üzerinde TLS yapılandırmasını kontrol edin:

DISPLAY CHANNEL(SYSTEM.DEF.SVRCONN) SSLCIPH
	4. AMS’yi Devre Dışı Bırakma:
		○ Eğer AMS'yi istemiyorsanız aşağıdaki ortam değişkenini ayarlayın:

export AMQ_DISABLE_CLIENT_AMS=1
Not:
	• Her kuyruk için bir güvenlik politikası tanımlanmalıdır.
	• MCA Interceptor'un kullandığı sertifikanın DN (Distinguished Name) değeri, hedef kuyruk politikası ile eşleşmelidir:
		○ cms.certificate.channel.SYSTEM.DEF.SVRCONN parametresi, keystore.conf dosyasındaki sertifikaya işaret etmelidir.

Önemli Notlar
	• Eğer sorunlar devam ediyorsa veya daha karmaşık bir problemle karşılaşıyorsanız, logları detaylı bir şekilde inceleyerek IBM Support ile iletişime geçebilirsiniz.
	• Güvenlik politikalarını doğru yapılandırdığınızdan ve sertifikaların geçerli olduğundan emin olun.


IBM MQ Komut Sorunları Giderme
IBM MQ komutlarını çalıştırırken karşılaşabileceğiniz yaygın sorunlar ve bu sorunların çözüm yöntemleri aşağıda açıklanmıştır.

1. Özel Karakterlerle İlgili Sorunlar
Bazı karakterlerin, özellikle \ (ters eğik çizgi) ve " (çift tırnak), komutlarda özel anlamları olabilir. Özel karakterlerin kullanımı sırasında hata alıyorsanız:
	• Karakterleri doğru kullandığınızdan emin olun.
	• Özel karakterler için kaçış karakterlerini (\) kullanmayı deneyin:
		○ Örneğin, bir tırnak işaretini metin içinde kullanmak için \" yazın.
	• Daha fazla bilgi için Special Characters in MQ Commands bölümüne göz atabilirsiniz.

2. MQSC Komut Sorunları
Eğer MQSC komutlarını çalıştıramıyorsanız aşağıdaki adımları izleyin:
a. Yönlendirme Operatörlerini Doğru Kullanma
	• Dosyadan giriş yönlendirmesi yapıyorsanız < operatörünü kullanın:

runmqsc < input_file.mqsc
		○ Eğer bu operatörü unutursanız, hata mesajı alabilirsiniz:

AMQ8118E: IBM MQ queue manager does not exist.
	• Çıktıyı bir dosyaya yönlendirme yapmak için > operatörünü kullanın:

runmqsc > output_file.txt
		○ Çıkış dosyası varsayılan olarak mevcut çalışma dizinine kaydedilir. Özel bir dizin belirtmek için tam dosya yolunu kullanın:

runmqsc > /path/to/output_file.txt

b. Kuyruk Yöneticisinin Çalıştığından Emin Olun
	• Tüm kuyruk yöneticilerini listelemek için şu komutu çalıştırın:

dspmq
	• Kuyruk yöneticisi çalışmıyorsa başlatın:

strmqm QMNAME

c. Varsayılan Kuyruk Yöneticisi Tanımlı mı?
	• Eğer varsayılan bir kuyruk yöneticisi tanımlı değilse veya aşağıdaki hatayı alıyorsanız:

AMQ8146E: IBM MQ queue manager not available.
		○ runmqsc komutunda bir kuyruk yöneticisi belirtin:

runmqsc QMNAME

d. Komutun Doğru Yerde Verildiğinden Emin Olun
	1. MQSC Komutları yalnızca runmqsc ortamında çalıştırılabilir. Örnek:
		○ Geçersiz Komut:

runmqsc DEFINE QLOCAL(FRED)

Bu tür bir kullanım geçerli değildir.
		○ Geçerli Komut:

runmqsc QMNAME
DEFINE QLOCAL(FRED)
	2. Kontrol Komutları ile MQSC Komutlarını Karıştırmayın:
		○ MQSC içinde kontrol komutları çalıştırılamaz. Örneğin:
			§ Yanlış: strmqm QMNAME komutu runmqsc ortamında çalıştırılamaz.
		○ MQSC'de yalnızca şu komutlar geçerlidir:
			§ ALTER
			§ CLEAR
			§ DEFINE
			§ DELETE
			§ DISPLAY
			§ END
			§ PING
			§ REFRESH
			§ RESET
			§ RESOLVE
			§ RESUME
			§ START
			§ STOP
			§ SUSPEND

3. setmqenv ile Çevre Değişkenlerini Ayarlama
Eğer komutun tanınmadığına dair bir hata alıyorsanız:
	• setmqenv komutunu kullanarak çevre değişkenlerini doğru şekilde ayarlayın:

setmqenv -s -m QMNAME
Bu komut, işletim sistemine uygun IBM MQ komutlarını bulması için gerekli ortam değişkenlerini yükler.

4. Örnek Komut Kullanımları
	• Kuyruk yöneticisini başlatma ve komut ortamına giriş:

strmqm QMNAME
runmqsc QMNAME
	• Bir kuyruk oluşturma:

DEFINE QLOCAL(MY.QUEUE)
	• Kuyruk özelliklerini görüntüleme:

DISPLAY QLOCAL(MY.QUEUE)

Sorun Hala Devam Ediyor mu?
Eğer yukarıdaki adımlarla sorun çözülmediyse:
	1. Hata mesajlarını inceleyin ve kaydedin.
	2. IBM MQ hata loglarını kontrol edin:

cat /var/mqm/errors/AMQERR01.LOG
	3. IBM Destek Ekibiyle İletişime Geçin.



Dağıtık Publish/Subscribe Sorunlarının Giderilmesi
IBM MQ'nun dağıtık publish/subscribe (yayınlama/abone olma) özelliklerini kullanırken karşılaşılabilecek sorunları çözmek için aşağıdaki önerilerden faydalanabilirsiniz.

1. Genel Sorun Giderme
a. Sorunun Yaygın Sebepleri
	• Kümeleme ile ilgili genel bir sorun mu? Eğer sorun kümeleme ile ilgili genel bir sorun ise, queue manager cluster sorunlarının giderilmesi başlığına göz atın.
	• Yayınların korunması (retained publications) için tasarım önerilerini inceleyin.
b. Proxy Abonelikler
Bir proxy abonelik, bir yayınlamanın uzak bir kuyruk yöneticisindeki aboneye iletilmesini sağlar. Eğer aboneleriniz mesajları alamıyorsa:
	1. Proxy aboneliklerin yerlerini kontrol edin:

display sub(*) subtype(proxy)
		○ Proxy abonelikler, dağıtık topolojinin türüne göre çeşitli yerlerde oluşturulabilir:
			§ Konu sahibi yönlendirme (topic host routing): Konu sahibinde proxy abonelik bulunur.
			§ Doğrudan yönlendirme (direct routing): Her küme yöneticisinde proxy abonelik bulunur.
	2. Proxy aboneliklerin doğru oluşturulduğunu doğrulayın:
		○ Yanlış yapılandırmalar, eksik veya gereksiz proxy aboneliklere neden olabilir.
		○ Eksik proxy abonelikler: Yanlış tanımlanan konu objeleri veya bozuk kanallar nedeniyle oluşabilir.
		○ Gereksiz proxy abonelikler: Yanlış "force" ayarı nedeniyle oluşabilir.
c. Proxy Aboneliklerin Yeniden Senkronize Edilmesi
Eğer bir kuyruk yöneticisi abonelikleri doğru şekilde gönderemiyor veya alamıyorsa, proxy abonelikleri manuel olarak yeniden senkronize edebilirsiniz:
	• Yeniden senkronizasyon komutu:

REFRESH QMGR TYPE(PROXYSUB)
	• Dikkat: Bu işlem ağ üzerinde ani bir yük oluşturabilir. Yalnızca IBM MQ belgeleri veya hata kayıtları bu işlemi önermişse kullanın.

2. Yönlendirme Sorunları
a. CLROUTE Ayarları
	• Tüm kümelenmiş konu tanımlamaları aynı CLROUTE ayarına sahip olmalıdır.

display tcluster(*) clroute
	• CLROUTE değerlerini kontrol edin ve uyumsuzlukları düzeltin.
		○ Geçersiz bir CLROUTE tanımı tespit edilirse: Hatalı tanımları kaldırın ve yeniden tanımlayın.
b. Küme Adlarının Yazımı
	• Konu nesnesi tanımlarken küme adının doğru yazıldığından emin olun. IBM MQ, var olmayan küme adlarını doğrulamaz.
c. Konu Durumu Görüntüleme
	• Tüm konu durumlarını görüntülemek için:

display tpstatus('#')
	• Eğer bir konu dalı çok fazla bilgi içeriyorsa, daha küçük bir alt dalı veya tek bir konuyu görüntüleyebilirsiniz.

3. Yayın Döngüsü Algılama ve Önleme
Dağıtık bir publish/subscribe ağında, yayınların döngüye girmesi ağın aşırı yüklenmesine ve abonelerin aynı mesajı birden fazla kez almasına neden olabilir.
a. Döngü Algılama Mekanizması
	• IBM MQ, yayın hareket ederken her kuyruk yöneticisinin benzersiz bir "parmak izi" eklediği bir sistem kullanır.
	• Eğer bir kuyruk yöneticisi kendi parmak izini algılarsa, mesajı silerek döngüyü kırar ve hata günlüğüne kaydeder.
b. Parmak İzi Formatı
	• RFH2 başlık formatı şu şekilde çalışır:

<ibm>
  <Rfp>uuid1</Rfp>
  <Rfp>uuid2</Rfp>
  ...
</ibm>
	• RFH2 Başlıkları:
		○ Bir kuyruk yöneticisi bir yayın aldığında, RFH2 başlığındaki mevcut parmak izlerini kontrol eder.
		○ Eğer kendi parmak izi bulunuyorsa, yayın bir döngüye girmiştir.

4. Sorun Çözüm Adımları
	1. Sorunların Sebeplerini Kontrol Edin:
		○ Proxy aboneliklerin doğru yerlerde olup olmadığını doğrulayın.
		○ CLROUTE ayarlarının uyumlu olduğundan emin olun.
		○ Küme tanımlarında yazım hatalarını kontrol edin.
	2. Komutları Kullanın:
		○ Proxy abonelikleri görüntüleyin:

display sub(*) subtype(proxy)
		○ Konu yönlendirme durumlarını kontrol edin:

display tcluster(*) clstate
	3. Hataları Günlüklerden İnceleyin:
		○ MQ hata günlüklerini kontrol edin.

cat /var/mqm/errors/AMQERR01.LOG
	4. IBM MQ Destek Ekibiyle İletişime Geçin: Eğer sorun çözülmediyse veya karmaşık bir yapılandırma hatasıyla karşılaştıysanız, IBM destek ekibinden yardım alın.


Dağıtık Kuyruk Yönetimi (DQM) Sorunlarının Giderilmesi
IBM MQ'nun Dağıtık Kuyruk Yönetimi (DQM) özelliklerini kullanırken karşılaşılabilecek sorunların nasıl çözüleceği hakkında kapsamlı bilgi aşağıda verilmiştir.

1. Sorun Belirleme ve Genel Bilgiler
a. Platform ve Kurulum Özgü Sorunlar
	• Bazı sorunlar platform ve kurulumlara özel olabilir. Bu durumda, IBM MQ'nun dokümantasyonunda ilgili açıklamaları kontrol edin.
b. Sorun Tanılama Aracı (amqldmpa)
	• amqldmpa aracı, IBM MQ sorunlarının belirlenmesi için kullanılabilir.
	• IBM hizmet temsilcisi, bu araçtan alınan çıktıyı isteyebilir.

2. Sorun Çözümüne Yönelik Genel Kaynaklar
a. Komut Doğrulama Sorunları
	• Kanal tanımlarken aşağıdaki hatalar olabilir:
		○ Çift kanal adı kullanımı
		○ Geçersiz parametre değerleri
		○ Mevcut olmayan veya şüpheli bir kanalın değiştirilmesi
b. Normal Kanal İşlemindeki Sorunlar
	• Sorunlar sistem konsolunda veya kanal günlüklerinde bildirilir.
	• Sorun tanılama adımları:
		1. Hata mesajlarını analiz edin.
		2. Kanalın durumu hakkında detaylı bilgi toplayın.
c. Kanal Başlatma ve Müzakere Hataları
	• Kanal başlatıldığında, her iki uç tarafın parametreler üzerinde uzlaşması gerekir. Eğer bu gerçekleşmezse, kanal kapanır ve hata günlüğüne mesaj yazılır.
d. İstemci Uygulama Sorunları
	• Yaygın istemci hata kodları:
		○ MQRC_Q_MGR_NOT_AVAILABLE: Kuyruk yöneticisine erişim yok.
		○ MQRC_CONNECTION_BROKEN: Bağlantı kesilmiş.
e. Ölümcül Mesaj Kuyruğu (DLQ)
	• Bir kanal çalışmayı durdurursa, taşınamayan mesajlar ölümcül mesaj kuyruğuna (DLQ) yönlendirilir.
	• Eğer DLQ mevcut değilse veya doluysa, kanal durur ve mesajlar aktarım kuyruğunda kalır.

3. Sorun Çözüm Adımları
a. Hata Durumunda Yapılacaklar
	1. Kanal Durumu Kontrolü:

DISPLAY CHSTATUS(channel_name) ALL

Bu komut, kanalın mevcut durumu hakkında bilgi sağlar.
	2. Kanalın Çalışmadığı Durumlarda:
		○ Kanalların doğru şekilde yapılandırıldığını doğrulayın.
		○ Gerekirse aşağıdaki komutları kullanarak sorunlu kanalı yeniden senkronize edin:

RESOLVE CHANNEL(channel_name) ACTION(COMMIT)
	3. Erişim ve Ağ Sorunları:
		○ PING CHANNEL komutuyla iletişim bağlantısını test edin:

PING CHANNEL(channel_name)
b. İletişim ve Ağ Sorunları
	1. KEEPALIVE Ayarları:
		○ Kanallar için sistem genelinde SO_KEEPALIVE seçeneğini etkinleştirin.
		○ Z/OS gibi sistemlerde KAINT ve RCVTIME ayarlarını kullanın.
	2. Kanalın Yeniden Başlatılması: Eğer kanal durumu STOPPED ise, aşağıdaki komutla yeniden başlatın:

START CHANNEL(channel_name)
c. Mesaj Takibi
	• Bir mesajın hedef kuyruğa ulaşıp ulaşmadığını belirlemek için dspmqrte komutunu kullanın:

dspmqrte -m QMgrName -q DestinationQueueName

4. Sık Karşılaşılan Sorunlar
a. Kanalın Çalışmayı Durdurması
	• Sebep: Örneğin, DLQ’nün dolu olması veya hatalı tanımlama.
	• Çözüm:
		1. DLQ’nün mevcut ve yeterli boyutta olduğundan emin olun.
		2. Sorun giderildikten sonra kanalı manuel olarak yeniden başlatın.
b. Ağ Bağlantı Kesintisi
	• Sebep: TCP/IP bağlantı sorunları veya IP adresi çözülememesi.
	• Çözüm:
		○ DNS veya ağ konfigürasyonlarını kontrol edin.
		○ SUBSTATE alanını analiz ederek detaylı bilgi alın.
c. Hatalı Kanal Eşleşmeleri
	• Sebep: Kanal adlarının eşleşmemesi veya farklı türlerin kullanılması.
	• Çözüm:
		○ Kanal tanımlarını yeniden gözden geçirin.
d. Mesajların Kaybolması
	• Sebep: DLQ’nün yokluğu veya hatalı yapılandırma.
	• Çözüm:
		1. DLQ’yi oluşturun ve tanımlayın.
		2. Sistem hatalarını analiz edin ve çözümleyin.

5. Afet Kurtarma
	• Düzenli sistem yedekleri alın ve bunları güvenli bir yerde saklayın.
	• Bir felaket durumunda, sistem yedeklerini kullanarak kuyruk yöneticilerini yeniden oluşturun.



IBM MQ Console ve REST API Sorun Giderme
IBM MQ Console veya REST API ile ilgili sorunlar yaşıyorsanız, aşağıdaki adımları izleyerek sorunları teşhis edebilir ve çözebilirsiniz.

1. mqweb Sunucusunun Durumu
mqweb Durumunu Kontrol Etme
	• IBM MQ Console veya REST API çalışmıyorsa, mqweb sunucusu durmuş olabilir. Durumu kontrol etmek için şu komutu çalıştırın:

dspmqweb status
mqweb Sunucusunu Başlatma
	• Eğer sunucu durduysa şu komutla başlatın:

bash
Copy code
strmqweb
z/OS İçin Önemli Bilgiler
	• WLP_USER_DIR değişkenini ayarlayın:

export WLP_USER_DIR=/var/mqm/web/installation1

2. mqweb Yapılandırma Dosyalarını Kontrol Edin
	• Yapılandırma dosyaları şunlardır:
		○ jvm.options
		○ mqwebuser.xml
		○ server.xml
	• Bu dosyaların yerini kontrol etmek için:

crtmqdir -a
	• Eğer dosyalar eksikse şu komutla yeniden oluşturabilirsiniz:

crtmqdir -s -f

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
	• Uzaktan bağlantılar için sunucu yapılandırmasını kontrol edin:

dspmqweb properties -a
	• Eğer httpHost değeri localhost ise, sadece aynı sistemden erişim sağlanabilir. Uzaktan bağlantıları etkinleştirmek için:

setmqweb properties -k httpHost -v "*"

5. Kuyruk Yöneticilerinin Görünürlüğünü Kontrol Etme
	• IBM MQ Console'da yerel kuyruk yöneticileri görünmüyorsa:
		○ mqweb sunucusu ile aynı kurulumdaki kuyruk yöneticilerini kontrol edin.
		○ z/OS: Kuyruk yöneticilerinin IBM MQ Console ile aynı sürümde çalıştığından emin olun.

6. Mesaj Görüntüleme ve REST API Sorunları
a. Mesajların Kısaltılması
	• Kuyrukları görüntülerken mesajlar kısaltılıyorsa, aşağıdaki yapılandırmayı artırabilirsiniz:
		○ mqConsoleMaxMsgCharsToDisplay
		○ mqConsoleMaxMsgRequestSize

setmqweb properties -k mqConsoleMaxMsgCharsToDisplay -v 10000
b. REST API Sorunları
	• Uzak Kuyruk Yöneticilerine Bağlantı
		○ Kuyruk yöneticisi adı yerine benzersiz adı kullandığınızdan emin olun.
		○ REST API’nin görebileceği kuyruk yöneticilerinde visibility parametresini kontrol edin:

dspmqweb remote
		○ CCDT Dosyası:
			§ ccdtUrl parametresinin doğru konumu belirttiğinden emin olun.

7. Genel Sorun Çözme ve İzleme
a. İletişim Hatası
	• Eğer şu mesajı alıyorsanız:

Lost communication with the server
		○ STEPLIB kütüphanelerinin doğru seviyede ve APF yetkili olduğundan emin olun.
		○ Yolları doğrulayın:
			§ INSTDIR, USERDIR, PATH, ve LIBPATH
b. İzleme ve Hata Ayıklama
	• IBM MQ Console ve REST API için izleme etkinleştirin. Daha fazla bilgi için:
		○ Tracing the REST API
		○ Tracing the IBM MQ Console



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
	• Kurulumun doğru olup olmadığını test etmek için:

mqipt xxx
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
	• Windows Registry Editor’da şu anahtarı kontrol edin:

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\MQInternetPassThru
		○ ConfigFilePath ayarının doğru mqipt.conf yolunu gösterdiğinden emin olun.
		○ ImagePath ayarının doğru mqiptService.exe yolunu gösterdiğinden emin olun.
Hata Teşhisi İçin Debug Modunu Etkinleştirme
	• Şu komutu çalıştırarak Windows Olay Günlüğüne detaylı bilgiler yazdırabilirsiniz:

mqiptService -debugevent
UTF-8 Kodlama Sorunu
	• mqipt.conf dosyasını Notepad ile düzenliyorsanız, dosyayı ANSI olarak kaydedin:
		○ File > Save As > Encoding: ANSI

4. İzleme ve Hata Ayıklama
İzleme Seviyesini Artırma
	• Trace Property: İzleme seviyesini artırmak için Trace=5 olarak ayarlayın. Örnek yapılandırma:

[global]
Trace=5
	• İzleme dosyası, errors dizininde oluşturulur.
JRE Teşhis Seçenekleri
	• SSL/TLS hatalarını teşhis etmek için:

-Djavax.net.debug=all
	• Güvenlik politikası sorunlarını teşhis etmek için:

-Djava.security.debug=access,failure
JRE Teşhis Komutları
	• Linux ve AIX:

MQIPT_JVM_OPTIONS="-Djavax.net.debug=all -Djava.security.debug=access,failure"
export MQIPT_JVM_OPTIONS
	• Windows:

set MQIPT_JVM_OPTIONS=-Djavax.net.debug=all -Djava.security.debug=access,failure
	• Bu ayarların etkili olması için MQIPT’yi yeniden başlatmanız gerekir.

5. Bağlantıyı Otomatik Başlatma
	• Windows Hizmeti: MQIPT’yi bir Windows hizmeti olarak kurduysanız, sistemle birlikte başlaması gerekir.
	• Hizmet başlamıyorsa:
		1. mqipt.conf ve mqiptService.exe yollarını kontrol edin.
		2. İlgili hata günlüklerini ve FFST kayıtlarını inceleyin.
		3. Gerekirse izleme modunu etkinleştirin ve destek için IBM’e başvurun.



1. IBM MQ MQI Client Bağlantı Problemleri
Bağlantı Hataları
MQCONN veya MQCONNX çağrıları sırasında aşağıdaki nedenlerle hata alabilirsiniz:
	• Listener Eksikliği: Sunucuda bir "listener" programı yoksa veya yanlış yapılandırılmışsa.
	• Protokol Kontrol Hatası: IBM MQ protokol kontrolleri sırasında bağlantı başarısız olabilir.
Hata Kodu: MQRC_Q_MQR_NOT_AVAILABLE
	• Bu hata kodu, bağlantı yapılamadığını gösterir. Aşağıdaki adımları kontrol edin:
		1. Listener Çalışıyor mu?
			§ Listener programının çalıştığından emin olun. Sunucuda runmqlsr komutunu kullanarak listener başlatabilirsiniz.
		2. Port ve IP Adresi Doğruluğu:
			§ İstemci konfigürasyonunda sunucunun IP adresi ve port numarasının doğru olduğundan emin olun.
		3. İstemci Hata Günlüğü:
			§ Hata günlüğünü kontrol edin:
				□ Windows: C:\Program Files\IBM\MQ\errors
				□ Linux: /var/mqm/errors
Bağlantı Sorunlarının Nedenleri
	• Sunucu programı veya listener yok.
	• Yanlış port veya IP adresi belirtilmiş.
	• İstemci ile sunucu arasındaki TCP/IP bağlantısı başarısız.

2. ECONNRESET Hatası
ECONNRESET: Bağlantının Kesilmesi
Bu hata, bağlantının karşı uçtan kapatıldığını gösterir. Aşağıdaki durumlarda oluşabilir:
	• Bağlantının Düzensiz Kapanması: İstemci sistem yeniden başlatılmış olabilir.
	• Yanlış Port veya IP: Uygulama, herhangi bir sunucunun dinlemediği bir port veya IP adresine bağlanmaya çalışıyor.
	• Beklenmeyen Veri: Kapalı bir bağlantıya veri gönderilmeye çalışılıyor.
	• Linger Seçeneği: Uygulama, linger seçeneğini sıfırlayarak bağlantıyı ani şekilde kapatmış olabilir.
Hata Mesajları
	• AMQ9208I: "Error on receive from host <hostname>."
	• AMQ9209I: "Connection to host <hostname> for channel <channelname> closed."
Çözüm Önerileri
	• Ağ Yöneticisine Başvurun: Ağ yöneticinizden TCP/IP paket izleme veya "sniffer" araçları kullanarak bağlantı sıfırlanma nedenlerini kontrol etmesini isteyin.
	• Güvenlik Duvarı Kontrolü: Gelen ve giden trafiğin güvenlik duvarı kurallarına uygun olduğundan emin olun.
	• Otomatik İstemci Yeniden Bağlanma:
		○ IBM MQ'nun Automatic Client Reconnection özelliğini uygulamanıza ekleyerek bağlantı kesintilerinde otomatik olarak yeniden bağlanmayı etkinleştirebilirsiniz.

3. Hata Günlüklerini İnceleme
Hata Günlüğü Dosyaları
	• Windows: C:\Program Files\IBM\MQ\errors
	• Linux: /var/mqm/errors
	• IBM i: /QIBM/UserData/mqm/errors
Ek Hata Mesajları
Bazı istemci hataları, sunucu hata günlüklerinde de kaydedilir. Bu nedenle, istemci ve sunucu hata günlüklerini birlikte incelemek önemlidir.

4. İstemci Kapatıldığında Kuyrukların Açık Kalması
Bir istemci kapatıldığında bile, sunucu tarafındaki süreçlerin kuyrukları açık tutabileceğini unutmayın. Bu, iletişim katmanının istemcinin kapatıldığını algılamasına kadar sürebilir.

5. Diagnostik İpuçları ve Çözüm Önerileri
Diagnostik Araçlar
	• TCP/IP Paket İzleme: Ağ yöneticinizden paket izleme araçlarını kullanmasını isteyin.
	• Sunucu Hata Kodları:
		○ Hata kodlarını anlamak için IBM MQ dokümantasyonundaki API Tamamlama ve Hata Kodları bölümüne bakabilirsiniz.
İzleme ve Test
	• Ping Kullanımı:
		○ Sunucu ve istemci arasındaki bağlantıyı test etmek için PING CHANNEL komutunu kullanabilirsiniz:

runmqsc <QMGR>
PING CHANNEL(<channel_name>)



IBM MQ .NET Uygulama Problemleri Sorun Giderme
IBM MQ .NET uygulamaları çalıştırılırken karşılaşılan sorunlar, genellikle yapılandırma, SSL bağlantıları veya global assembly cache (GAC) ile ilgilidir. Bu sorunları çözmek için aşağıdaki yöntemleri izleyebilirsiniz:

1. Sorun Giderme için .NET Örnek Uygulamaları ve Hata Mesajları
Örnek Uygulamalarla Sorun Giderme
	1. Örnek Uygulama Çalıştırma:
		○ IBM MQ ile birlikte gelen .NET örnek uygulamalarını çalıştırarak sorunları tanımlayabilirsiniz.
		○ Bu örnek uygulamalar hakkında bilgi için Sample applications for .NET dokümantasyonuna bakın.
	2. Hata Mesajlarını İnceleme:
		○ Hata mesajlarını dikkatlice okuyarak önerilen adımları uygulayın.
Unhandled Exception: System.IO.FileNotFoundException
Bu hata genellikle şu dosyalara erişimle ilgili problemleri işaret eder:
	• amqmdnet.dll
	• amqmdxcs.dll
Çözüm Yöntemleri
	• Global Assembly Cache (GAC) Kaydı:
		○ Dosyaların global assembly cache’e (GAC) kayıtlı olduğundan emin olun.
	• Konfigürasyon Dosyası Oluşturma:
		○ amqmdnet.dll ve amqmdxcs.dll dosyalarını işaret eden bir konfigürasyon dosyası oluşturun.
	• Elle Kayıt:
		○ Eğer .NET Framework IBM MQ kurulumu sırasında yoksa, sınıflar GAC'e otomatik olarak kaydedilmeyebilir. Aşağıdaki komutu kullanarak kaydı manuel olarak tekrar yapabilirsiniz:

amqidnet -c MQ_INSTALLATION_PATH\bin\amqidotn.txt -l logfile.txt
			§ MQ_INSTALLATION_PATH, IBM MQ'nun kurulu olduğu üst dizini temsil eder.
			§ logfile.txt, kurulum detaylarının kaydedileceği log dosyasıdır.

2. Ortak SSL Hata Kodları
IBM MQ 9.4.0'dan itibaren, .NET istemci kütüphaneleri (amqmdnetstd.dll), SSL ile ilgili sorunlar için daha spesifik hata mesajları sunar.
Senaryo	Önceki Hata Mesajı	IBM MQ 9.4.0 Sonrası Hata Mesajı
SSL anahtar deposu yanlış ayarlandığında	2059 – MQRC_Q_MGR_NOT_AVAILABLE	2381 – MQRC_KEY_REPOSITORY_ERROR
Geçersiz bir şifreleme algoritması ayarlandığında	2538 – MQRC_HOST_NOT_AVAILABLE	2393 – MQRC_SSL_INITIALIZATION_ERROR
Geçersiz bir eş adı ayarlandığında	2059 – MQRC_Q_MGR_NOT_AVAILABLE	2399 – MQRC_SSL_PEER_NAME_ERROR
Eş adları eşleşmediğinde	2059 – MQRC_Q_MGR_NOT_AVAILABLE	2398 – MQRC_SSL_PEER_NAME_MISMATCH
Geçersiz bir sertifika kullanıldığında	2059 – MQRC_Q_MGR_NOT_AVAILABLE	2393 – MQRC_SSL_INITIALIZATION_ERROR
Şifreleme algoritmaları arasında uyumsuzluk olduğunda	2059 – MQRC_Q_MGR_NOT_AVAILABLE	2393 – MQRC_SSL_INITIALIZATION_ERROR
IBM MQ anahtar deposuna erişim izni olmadığında	2059 – MQRC_Q_MGR_NOT_AVAILABLE	2393 – MQRC_SSL_INITIALIZATION_ERROR
Sorunun Tespiti
	• Kuyruk Yöneticisi Günlüklerini İnceleyin:
		○ Hataların detaylı açıklamalarını görmek için MQ_DATA_DIRECTORY/qmgrs/errors/AMQERR.log* dosyalarını kontrol edin.

3. IBM MQ .NET İstemci Bağlantı Problemleri
MQCONN veya MQCONNX Çağrısı Başarısız
Bu sorun genellikle şu nedenlerle ortaya çıkar:
	• Listener Yok:
		○ Sunucuda bir "listener" programı çalışmıyor olabilir.
	• Yanlış SSL Konfigürasyonu:
		○ Geçersiz bir şifreleme algoritması veya sertifika ayarları yapılmış olabilir.
Hata Günlüğü Dosyaları
	• Windows: C:\Program Files\IBM\MQ\errors
	• Linux: /var/mqm/errors
ECONNRESET Hatası
	• Nedenler:
		○ TCP/IP bağlantısının karşı uçtan aniden kesilmesi.
		○ Geçersiz bağlantı adresi veya port.
		○ Ağ bağlantısındaki sorunlar.
	• Çözüm:
		○ Ağ yöneticinizle iletişime geçerek TCP/IP paket izleme araçları kullanmasını isteyin.

4. İzleme ve Diagnostik
İzleme Aktifleştirme
	• İzleme özelliğini aktifleştirmek için .NET istemci uygulamalarınızda Tracing IBM MQ .NET applications dokümantasyonuna bakarak gerekli adımları izleyin.
SSL Sorunları İçin Diagnostik
	1. SSL/TLS Tanılama:

set MQIPT_JVM_OPTIONS=-Djavax.net.debug=all
	2. Java Güvenlik Tanılama:

set MQIPT_JVM_OPTIONS=-Djava.security.debug=access,failure
İzleme Sonuçlarını Analiz Etme
	• İzleme sonuçlarını inceleyerek sorun kaynağını belirleyin.
	• Hata dosyaları ve logları IBM Destek Ekibine sağlayarak daha fazla yardım alabilirsiniz.

Sonraki Adımlar
	• SSL ile ilgili sorunlarda, sertifikaların doğru yapılandırıldığından ve eş adlarının uyumlu olduğundan emin olun.
	• Ağ bağlantı sorunlarında, ağ ekipleri ile birlikte çalışarak altyapı sorunlarını giderin.
	• IBM MQ 9.4.0 sonrası gelen geliştirilmiş hata mesajlarını inceleyerek sorunları daha hızlı çözebilirsiniz.



IBM MQ'de Java ve JMS Problemleri Sorun Giderme
IBM MQ ile Java ve JMS uygulamalarını çalıştırırken karşılaşılan yaygın sorunlar aşağıdaki yöntemlerle çözülebilir:

1. IBM MQ JMS Sınıflarında Sorun Giderme
Kurulum Doğrulama Programları
	• IBM MQ JMS sınıfları için kurulum doğrulama programlarını çalıştırarak sorunları analiz edebilirsiniz.
	• Örnek: Point-to-Point IVT ve Publish/Subscribe IVT testleri.
Loglama
	• Varsayılan log dosyası: mqjms.log.
	• Log çıktısını özel bir dosyaya yönlendirmek için şu özelliği tanımlayın:

-Dcom.ibm.msg.client.commonservices.log.outputName=/path/to/mylog.txt
	• Loglamayı kapatmak için:

-Dcom.ibm.msg.client.commonservices.log.status=OFF

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
	• Örnek Kod:

Message receivedMessage = consumer.receive(10000);
BytesMessage bytesMessage = (BytesMessage) receivedMessage;
byte[] bytesReceived = new byte[(int) bytesMessage.getBodyLength()];
bytesMessage.readBytes(bytesReceived);

MQMessage mqMsg = new MQMessage();
mqMsg.write(bytesReceived);
mqMsg.encoding = receivedMessage.getIntProperty("JMS_IBM_Encoding");
mqMsg.format = receivedMessage.getStringProperty("JMS_IBM_Format");
mqMsg.seek(0);

PCFMessage pcfMsg = new PCFMessage(mqMsg);

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
		○ CHLAUTH kuralını düzenleyerek yönetici bağlantılarını izin verin:

SET CHLAUTH('WAS.CLIENTS') TYPE(BLOCKUSER) USERLIST(ALLOWANY)
	• Üretim ortamında:
		○ SSL/TLS Güvenliği: Karşılıklı SSL/TLS doğrulama yapılandırın.
		○ Tüm yetkisiz kanalları devre dışı bırakın:

ALTER CHL(SYSTEM.DEF.SVRCONN) CHLTYPE(SVRCONN) MCAUSER('NOAUTH') STOP CHL(SYSTEM.DEF.SVRCONN)

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


1. IBM MQ JMS Sınıflarında Sorun Giderme
a. Kurulum Doğrulama Programları
	• IBM MQ JMS sınıfları için kurulum doğrulama programlarını kullanarak test yapabilirsiniz.
		○ Örnek Testler:
			§ Point-to-Point IVT
			§ Publish/Subscribe IVT
	• Bu testler, temel bağlantı ve mesaj alışverişi yapılandırmalarının doğruluğunu kontrol eder.
b. Loglama
	• Varsayılan log dosyası: mqjms.log
	• Log çıktısını özel bir dosyaya yönlendirmek için şu komutu kullanabilirsiniz:

-Dcom.ibm.msg.client.commonservices.log.outputName=/path/to/mylog.txt
	• Loglamayı kapatmak için:

-Dcom.ibm.msg.client.commonservices.log.status=OFF

2. JMS Sağlayıcı Versiyon Problemleri
a. Yaygın Hatalar ve Çözümleri
	• JMSCC5008: JMS 2.0 işlevi, desteklenmeyen bir bağlantıda kullanılıyor.
		○ Çözüm: JMS 2.0 API'sini kullanmayı bırakın veya IBM MQ 8 sürümündeki bir kuyruğa bağlanın.
	• JMSFMQ0003: Kuyruk yöneticisi komut seviyesi, sağlayıcı sürümüyle uyumlu değil.
		○ Çözüm: Sağlayıcı sürümünü kuyruk yöneticisi ile uyumlu olacak şekilde değiştirin.

3. PCF İşleme Sorunları
a. Kodlama Uyumsuzluğu
	• Big-endian ve little-endian platformlar arasındaki farklılıklar sorunlara neden olabilir.
	• Hata Mesajı: MQRCCF_STRUCTURE_TYPE_ERROR (3013)
b. Çözüm Örneği

java
Copy code
Message receivedMessage = consumer.receive(10000);
BytesMessage bytesMessage = (BytesMessage) receivedMessage;
byte[] bytesReceived = new byte[(int) bytesMessage.getBodyLength()];
bytesMessage.readBytes(bytesReceived);
MQMessage mqMsg = new MQMessage();
mqMsg.write(bytesReceived);
mqMsg.encoding = receivedMessage.getIntProperty("JMS_IBM_Encoding");
mqMsg.format = receivedMessage.getStringProperty("JMS_IBM_Format");
mqMsg.seek(0);
PCFMessage pcfMsg = new PCFMessage(mqMsg);

4. Bağlantı Havuzu Hataları
a. Purge Policy Ayarları
	• FailingConnectionOnly: Sadece sorunlu bağlantı kapatılır (varsayılan).
	• EntirePool: Tüm bağlantılar kapatılır, güvenilir bir çözüm olabilir.

5. 2035 MQRC_NOT_AUTHORIZED Hatası
a. Nedenler
	• Kullanıcı adı bilinmiyor veya yetkilendirilmemiş.
	• CHLAUTH kaydı yönetici erişimini engelliyor.
b. Çözümler
	• Geliştirme ortamında:

SET CHLAUTH('WAS.CLIENTS') TYPE(BLOCKUSER) USERLIST(ALLOWANY)
	• Üretim ortamında:
		○ SSL/TLS Güvenliği: Karşılıklı SSL doğrulama yapılandırın.
		○ Yetkilendirme hatalarını analiz edin ve çözümleyin.

6. Managed File Transfer (MFT) Problemleri
a. Mesaj Reddetme ve Yeniden İşleme
	• Reddedilen Mesajların İncelenmesi:
		○ Reject Queue'deki mesajları inceleyin.
		○ usr.WMQFTE_ReasonForRejection adlı bir özellik, reddedilme nedenini açıklar.
	• Mesajların Yeniden İşlenmesi:
		○ Mesajları Reject Queue'dan alıp, Input Queue'ya taşıyabilirsiniz.

DISPLAY SUB(SYSTEM.FTE.DATABASELogger.AUTO) DEST
b. Logger Hataları
	• SQLSTATE=42704 hatası: Veritabanı tablo boyutları küçük.
		○ Çözüm: Veritabanı sayfa boyutunu 8 KB veya daha büyük olacak şekilde ayarlayın.

7. Connect:Direct Köprüsü ile Sorun Giderme
a. Dosya Yolu Hataları
	• Çift eğik çizgi (//) ile başlayan yollar, yanlışlıkla veri seti olarak yorumlanabilir.
		○ Çözüm: Dosya yollarını doğru formatta belirtin.
b. İzin Hataları
	• Hata Mesajı:

BFGCD0001E: LCCA000I Kullanıcı, SNODEID geçersiz kılma iznine sahip değil.
		○ Çözüm: İlgili kullanıcıya gerekli yetkileri verin.
c. Eş Zamanlı Transferleri Artırma
	• Agent Properties Ayarları:

maxSourceTransfers=25
maxDestinationTransfers=25
ioThreadPoolSize=50
	• Connect:Direct düğümündeki api.max.connects parametresini artırın.

8. Genel Sorun Giderme Adımları
	• Koordinasyon Kuyruk Yöneticisi Bağlantısı:
		○ Bağlantı hataları için 2058 hata kodunu analiz edin.
	• JVM DNS Cache Sorunları:
		○ Cache süresini düzenlemek için şu değişkeni ayarlayın:

-Dsun.net.inetaddr.ttl=value


IBM MQ'da Mesaj Sorunlarının Giderilmesi: Teslim Edilemeyen Mesajlar
IBM MQ, mesajların hedeflerine ulaşamadığı durumlarda bu mesajları "dead-letter queue" (DLQ) adı verilen bir kuyrukta saklar. Teslim edilemeyen mesajlarla ilgili sorunları çözmek için aşağıdaki adımları izleyebilirsiniz.

1. Teslim Edilemeyen Mesajları Tespit Etme
Teslim edilemeyen mesajların nedenlerini belirlemek için "dead-letter queue" üzerinde inceleme yapmanız gerekir. Her bir kuyruk yöneticisi genellikle mesajları saklamak için bir yerel "dead-letter queue" tanımlar.

2. Adım Adım Sorun Giderme
	1. Kuyrukta Mesaj Olup Olmadığını Kontrol Edin
Aşağıdaki MQSC komutunu kullanarak ilgili kuyrukta mesaj bulunup bulunmadığını doğrulayabilirsiniz:

scss
Copy code
DISPLAY QUEUE('DEAD.LETTER.QUEUE.NAME') CURDEPTH

Bu komut, kuyruktaki mevcut mesaj sayısını (CURDEPTH) gösterir.
	2. Mesajları İnceleyin
IBM MQ, mesajları taramak için bir örnek uygulama sağlar: amqsbcg. Bu uygulama, kuyruktaki mesajları MQGET çağrısıyla okur ve mesaj tanımlayıcı (MQMD) ile bağlam alanlarını gösterir.
Kullanım:


amqsbcg DEAD.LETTER.QUEUE.NAME QUEUE_MANAGER_NAME
	3. Mesajların Durumuna Göre İşlem Yapın
		○ Nedenlerini Belirleyin: Mesajların "dead-letter queue"ya gönderilme nedenini tespit edin.
			§ Yanlış hedef kuyruk adı
			§ Yetkilendirme hatası
			§ Hedef kuyruk dolu
			§ Mesajın yaşam süresi (TTL) dolmuş olabilir.
		○ İşlem Kararı Alın: Mesajları yeniden yönlendirin, yok edin veya başka bir şekilde işleyin.

3. Ölü Mektup Kuyruğu (DLQ) Yoksa Ne Olur?
Eğer her kuyruk yöneticisi için bir "dead-letter queue" tanımlamazsanız, mesajlar kaybolabilir veya işlenemez duruma gelir. Bu tür durumları önlemek için:
	• DLQ Tanımlayın: Her kuyruk yöneticisi için bir "dead-letter queue" oluşturun ve tanımlayın.

ALTER QMGR DEADQ('DEAD.LETTER.QUEUE.NAME')

4. Ölü Mektup Kuyruğu İşleyici Kullanımı
IBM MQ, "dead-letter queue"deki mesajları işlemek için bir "Dead-Letter Queue Handler" (DLQ Handler) sağlar. Bu işlemci sayesinde:
	• Mesajları otomatik olarak silebilir,
	• Yeniden yönlendirebilir,
	• İşlenmesi gereken mesajları belirli bir kurala göre filtreleyebilirsiniz.
DLQ işleyici ile ilgili daha fazla bilgi için IBM MQ dokümantasyonundaki "Working with dead-letter queues" bölümünü inceleyebilirsiniz.


IBM MQ Telemetri Problemleri Giderme
IBM MQ Telemetry (MQXR) hizmeti, telemetri kanallarını ve MQTT istemcilerini destekler. Ancak bu hizmetle ilgili çeşitli problemler ortaya çıkabilir. Aşağıda, belirli problemleri tanımlama ve çözme yöntemlerini içeren kapsamlı bir açıklama bulunmaktadır.

Telemetri Günlükleri, Hata Kayıtları ve Yapılandırma Dosyalarının Konumu
Sunucu Tarafı Günlükleri ve Hataları:
	• MQXR hizmeti, hata bilgilerini IBM MQ hata dizinine yazar. FDC dosyaları aşağıdaki yolda bulunabilir:

WMQ data directory\errors\AMQ nnn.n.FDC
	• MQXR hizmeti ayrıca kendi günlük dosyasını oluşturur:

WMQ data directory\Qmgrs\qMgrName\errors\mqxr.log

JSON formatında hata günlüğü etkinleştirilirse:

WMQ data directory\Qmgrs\qMgrName\errors\mqxr.json
Sunucu Tarafı Yapılandırma Dosyaları:
	• Telemetri kanalları ve hizmeti için yapılandırmalar şu dosyalarda saklanır:

bash
Copy code
WMQ data directory\Qmgrs\qMgrName\mqxr\mqxr_win.properties (Windows)
/var/mqm/qmgrs/qMgrName/mqxr/mqxr_unix.properties (AIX veya Linux)
	• JVM yapılandırma dosyası:

WMQ data directory\Qmgrs\qMgrName\mqxr\java.properties
Trace Yapılandırması:
	• İzleme yapılandırma dosyaları:

WMQ data directory\Qmgrs\qMgrName\mqxr\trace.config
mqxrtraceOn.properties
mqxrtraceOff.properties

JSON Formatında Günlükleri Etkinleştirme
	1. Dosyaları Güncelleyin:
		○ mqxrtraceOn.properties ve mqxrtraceOff.properties dosyalarını düzenleyin.
		○ Sadece JSON formatında günlükler için:

Copy codehandlers=com.ibm.mq.util.logging.MQJSONErrorLogFileHandler
		○ Metin tabanlı günlüklerle birlikte JSON formatını kullanmak için:

handlers=com.ibm.mq.util.logging.MQErrorLogFileHandler,com.ibm.mq.util.logging.MQJSONErrorLogFileHandler
	2. Hizmeti Yeniden Başlatın:
		○ Değişikliklerin etkili olması için MQTT hizmetini yeniden başlatın.

Düşük Bellek Hataları için Java Heap Dump Üretimi
	1. JVM Yapılandırma Dosyasını Düzenleyin:
		○ java.properties dosyasına şu satırı ekleyin:

-Dcom.ibm.mq.MQXR.GenerateHeapDump=true
	2. Hizmeti Yeniden Başlatın:
		○ Değişikliklerin uygulanması için hizmeti yeniden başlatın.
	3. Sonuçlar:
		○ Düşük bellek hatası oluştuğunda, bir Java heap dump dosyası oluşturulur. Dosya şu dizinde bulunur:

WMQ data directory\errors

MQTT İstemcisi Bağlantı Sorunlarını Çözme
	1. Hata Kodlarını Kontrol Edin:
		○ REASON_CODE_INVALID_PROTOCOL_VERSION: Protokol sürümünü doğrulayın.
		○ REASON_CODE_INVALID_CLIENT_ID: İstemci kimliği 23 bayttan uzun olmamalıdır.
		○ REASON_CODE_SERVER_CONNECT_ERROR: MQXR hizmetinin ve kuyruk yöneticisinin düzgün çalıştığını kontrol edin.
	2. Bağlantı Sorunlarını İzole Edin:
		○ netstat kullanarak soket adreslerini doğrulayın.
		○ ping komutuyla sunucu adresine erişimi kontrol edin.

MQTT Mesaj Kaybı Sorunlarını Giderme
	1. Kalite Servisini Ayarlayın:
		○ Mesajları At least once veya At most once kalite servisleri ile gönderin.
		○ CleanSession=false ayarını yaparak oturumun korunmasını sağlayın.
	2. Abonelikleri Kontrol Edin:
		○ MQTT istemci aboneliklerini IBM MQ Explorer veya runmqsc ile kontrol edin.
	3. Yetkilendirmeyi Doğrulayın:
		○ Yayıncı ve abonenin gerekli izinlere sahip olduğunu doğrulamak için dspmqaut komutunu kullanın.

MQXR Hizmeti Başlatma Sorunları
	1. Başlangıç Hataları:
		○ Sistem nesnelerini göstermek için IBM MQ Explorer'da sistem nesnelerini görünür hale getirin.
		○ Eksik dosyalar veya yanlış izinler olup olmadığını kontrol edin.
	2. Hata Kayıtlarını Kontrol Edin:
		○ Hataları mqxr.log ve AMQERR01.LOG dosyalarından inceleyin.

JAAS Oturum Açma Modülü Sorunları
	1. Konfigürasyonu Kontrol Edin:
		○ jaas.config dosyasında doğru sınıf adını belirttiğinizden emin olun.
	2. Günlükleri Kontrol Edin:
		○ mqxr.log dosyasında javax.security.auth.login.LoginException hatasını arayın.

Bu prosedürler ve çözümler, IBM MQ Telemetry hizmetiyle ilişkili yaygın sorunları tanımlamak ve çözmek için size rehberlik edecektir. Daha karmaşık durumlar için IBM Support ile iletişime geçebilirsiniz.



IBM MQ Multicast Problemleri Giderme
IBM MQ Multicast, dağıtılmış mesajlaşma için multicast yöntemini kullanarak yüksek performans sağlar. Ancak multicast yapılandırmaları ve uygulamaları sırasında bazı yaygın sorunlarla karşılaşılabilir. Bu belgede, IBM MQ Multicast ile ilgili yaygın sorunların tanımlanması ve çözülmesi için kapsamlı açıklamalar yer almaktadır.

Multicast Uygulamalarını Multicast Olmayan Bir Ağda Test Etme
Multicast destekli bir ağa erişiminiz yoksa, multicast uygulamalarını yerel olarak test etmek mümkündür:
	1. mqclient.ini Dosyasını Düzenleyin:
		○ Interface parametresini şu şekilde ayarlayın:

Multicast:
Interface = 127.0.0.1
		○ Bu yapılandırma, multicast iletilerinin yalnızca yerel döngü adaptörünü kullanmasını sağlar.
	2. Dosya Konumu:
		○ MQ_DATA_PATH/mqclient.ini dizininde bulunur.

Multicast Trafiği için Doğru Ağı Ayarlama
Multicast uygulamalarını test etmek için bir multicast destekli ağa geçiş yapıldığında:
	1. mqclient.ini Dosyasını Güncelleyin:
		○ Birden fazla ağ adaptörü veya VPN kullanıyorsanız, doğru adaptörü belirtin.
		○ Örnek:

Multicast:
Interface = IPAddress
		○ IPAddress, multicast trafiğinin akacağı ağ adaptörünün IP adresidir.
	2. Multicast Stanza'sı Yoksa:
		○ Aşağıdaki yapılandırmayı ekleyin:

Multicast:
Interface = IPAddress

Multicast Konu Dizesi Çok Uzun
IBM MQ Multicast'ta konu dizesi uzunluğu 255 karakterle sınırlıdır. Aşırı uzun konu dizeleri aşağıdaki hata koduyla sonuçlanabilir:
	• Hata Kodu: MQRC_TOPIC_STRING_ERROR (RC2425)
Çözüm:
	• Konu dizesi uzunluğunu kısaltarak performans sorunlarını azaltın.
	• Ağaç yapısındaki düğüm adlarını mümkün olduğunca kısa tutun.

Multicast Konu Topolojisi Sorunları
IBM MQ Multicast, her alt ağacın kendi multicast grubu ve veri akışına sahip olmasını gerektirir. Ancak, belirli topolojiler önerilmez:
Önerilen Multicast Topoloji
	1. COMMINFO Nesneleri Tanımlayın:

DEF COMMINFO(MC1) GRPADDR(227.20.133.1)
DEF COMMINFO(MC2) GRPADDR(227.20.133.2)
	2. Konu Tanımları:

DEFINE TOPIC(FRUIT) TOPICSTRING('Price/FRUIT') MCAST(ENABLED) COMMINFO(MC1)
DEFINE TOPIC(FISH) TOPICSTRING('Price/FISH') MCAST(ENABLED) COMMINFO(MC2)
	3. Ağaç Yapısı:
		○ FRUIT konusu MC1 adresini, FISH konusu ise MC2 adresini kullanır.
		○ Bu yapı, her konu için ayrı bir veri akışı sağlar.
Önerilmeyen Multicast Topoloji
	1. Ek COMMINFO Tanımları:

DEF COMMINFO(MC3) GRPADDR(227.20.133.3)
	2. Konu Tanımları:

DEFINE TOPIC(ORANGES) TOPICSTRING('Price/FRUIT/ORANGES') MCAST(ENABLED) COMMINFO(MC3)
	3. Sorun:
		○ Price/FRUIT/# konusuna abone olan bir uygulama, yalnızca MC1 adresinden veri alır.
		○ Ancak, Price/FRUIT/ORANGES/Small konusuna yayın yapan bir uygulama, MC3 adresine veri gönderir ve bu, abonenin beklentisiyle uyumlu değildir.

Genel Multicast Sorunlarının Çözümü
	1. Multicast Adreslerini Doğru Ayarlayın:
		○ Yerel multicast adresleri kullanın: 239.0.0.0 - 239.255.255.255
	2. Hataları İzleyin:
		○ Hata günlüklerini kontrol edin: mqxr.log ve AMQERR01.LOG
	3. Yapılandırmaları Gözden Geçirin:
		○ COMMINFO ve TOPIC tanımlarının doğru yapılandırıldığından emin olun.

Bu kılavuz, IBM MQ Multicast ile ilgili yaygın sorunların çözülmesine yönelik öneriler sunar. Daha karmaşık durumlar için IBM Support ile iletişime geçilmesi önerilir.


Queue Manager Cluster Problemleri Giderme
IBM MQ cluster yapılarında ortaya çıkabilecek yaygın sorunları ve çözümlerini aşağıda detaylı bir şekilde açıklıyoruz. Bu rehber, cluster problemlerini etkili bir şekilde teşhis etmenize ve çözmenize yardımcı olacaktır.

Ön Hazırlık
	• Eğer sorunlarınız genel cluster yapılandırması yerine publish/subscribe (yayın/abonelik) ile ilgiliyse, "Routing for publish/subscribe clusters: Notes on behavior" başlığını inceleyin.
	• MQSC komutları ile çalışmanız gerekebilir. Platformunuza uygun olarak MQSC komutlarını nasıl kullanacağınızı öğrenmek için IBM MQ belgelerine başvurabilirsiniz.

Sorunlar ve Çözümler
1. Cluster Kanallarının Eşleşmemesi
	• Senaryo: Cluster kanalları doğru şekilde eşleşmiyor.
	• Açıklama: Her bir cluster sender kanalı, aynı ada sahip bir cluster receiver kanalına bağlanmalıdır. Eğer remote (uzak) queue manager üzerinde aynı ada sahip bir cluster receiver kanalı yoksa, kanal çalışmaz.
	• Çözüm: Kanalların doğru eşleştiğinden emin olun.

2. Kanalların RETRYING Durumunda Kalması
	• Senaryo: Kanallar sürekli RETRYING (tekrar deneme) durumunda.
	• Açıklama: Bu durum, kanal tanımında bir hata olduğunu veya uzak queue manager'ın çalışmadığını gösterebilir. Ayrıca, bu durum cluster içerisindeki nesnelerin (örneğin kuyruklar, queue manager'lar) güncel olmamasına yol açabilir.
	• Çözüm:
		○ Kanalların durumunu görüntüleyin:

display chstatus(*)
		○ Sorunlu kanalların tanımlarını düzeltin veya eksik queue manager'ları çalıştırın.

3. Kanalların STOPPED Durumuna Geçmesi
	• Senaryo: Kanallar manuel olarak durdurulmuş.
	• Açıklama: Cluster auto-defined kanallar, manuel olarak durdurulduğunda otomatik olarak yeniden başlamaz.
	• Çözüm:
		○ Kanalı yeniden başlatın:

start channel(kendi_kanal_adınız)
		○ Manuel olarak durdurmak yerine şu komutu kullanarak kanalı durdurun:

stop channel(kendi_kanal_adınız) status(inactive)

4. Full Repositories Bilgilerinin Eksikliği
	• Senaryo: Cluster'daki queue manager'lar, tüm full repository queue manager'ların farkında değil.
	• Çözüm:
		○ Queue manager'ların full repository bilgilerini görüntüleyin:

display clusqmgr(*) qmtype
		○ Eksik olan bilgileri tamamlamak için kanalların düzgün çalıştığından emin olun.

5. Dead-Letter Kuyruğunda Mesajlar
	• Senaryo: Queue manager tarafından teslim edilemeyen mesajlar dead-letter kuyruğuna gönderiliyor.
	• Çözüm:
		○ Dead-letter kuyruğunu kontrol edin ve mesajların neden teslim edilemediğini belirleyin.

6. RC2035 (NOT_AUTHORIZED) Hatası
	• Senaryo: Cluster'da bir kuyruk açmaya çalışırken yetkilendirme hatası alıyorsunuz.
	• Çözüm:
		○ Sistem kullanıcısına SYSTEM.CLUSTER.TRANSMIT.QUEUE kuyruğunda yeterli yetkiyi verin:

setmqaut -m QMGR_ADI -n SYSTEM.CLUSTER.TRANSMIT.QUEUE -t q -g mqm +all

7. RC2085 (UNKNOWN_OBJECT_NAME) Hatası
	• Senaryo: Bir cluster kuyruğunu açarken MQRC_UNKNOWN_OBJECT_NAME hatası alıyorsunuz.
	• Çözüm:
		○ Kuyruğun cluster içinde doğru tanımlandığından ve uygun erişim seçeneklerinin kullanıldığından emin olun.
		○ Örnek komut:

display clusqmgr(*) qmtype status

8. Cluster'daki Güncel Olmayan Bilgiler
	• Senaryo: Cluster queue manager'lar ve kuyruklarla ilgili eski bilgiler görüyorsunuz.
	• Çözüm:
		○ Cluster bilgilerini yenilemek için ilgili komutu kullanın:

refresh cluster(cluster_adı)

9. RC2189 (CLUSTER_RESOLUTION_ERROR) Hatası
	• Senaryo: Bir kuyruğu açarken bu hata alınıyor.
	• Açıklama: Queue manager, tam repository'lere bağlanamıyor.
	• Çözüm:
		○ Full repository'lerle bağlantıların düzgün çalıştığını doğrulayın:

display clusqmgr(*) qmtype status

10. Cluster Kuyruklarıyla Çalışma Sorunları
	• Senaryo: Cluster kuyruğu "MQPUT" için devre dışı bırakılmış.
	• Çözüm:
		○ Kuyruk tanımını şu şekilde değiştirin:

alter qlocal(kuyruk_adı) defbind(notfixed)

11. Cluster Yönetim Komutlarının Etkisi
	• REFRESH CLUSTER komutu cluster yapısını geçici olarak etkileyebilir. Özellikle REFRESH CLUSTER sırasında çalıştırılan uygulamalar geçici hatalar alabilir (örneğin, MQRC_UNKNOWN_OBJECT_NAME, MQRC_CLUSTER_RESOLUTION_ERROR).


Queue Manager Problemleri Giderme
IBM MQ kullanırken queue manager'lar (kuyruk yöneticileri) ile ilgili yaygın sorunlar ortaya çıkabilir. Aşağıda bu sorunlar ve çözüm yolları detaylı olarak açıklanmıştır:

Queue Manager Ulaşılamıyor Hatası
Senaryo:
	• Queue manager'a erişmeye çalıştığınızda "Queue Manager Unavailable" hatası alıyorsunuz.
Açıklama:
	• Konfigürasyon dosyasındaki hatalar, queue manager'ların bulunmasını engelleyebilir.
	• Özellikle Windows'ta, qm.ini dosyasındaki problemler bu hataya yol açabilir.
Çözüm:
	1. Konfigürasyon Dosyalarını Kontrol Edin:
		○ Queue manager ve log dizinlerini doğru şekilde referans gösterdiğinden emin olun.
	2. Windows için Özel Kontrol:
		○ qm.ini dosyasında bir hata olup olmadığını kontrol edin.

Log I/O İşlemi Eşik Değerini Aştı Hatası
Senaryo:
	• Queue manager hata günlüğünde şu mesajı alıyorsunuz:
AMQ6729W: Log I/O operation exceeded threshold.
Açıklama:
	• IBM MQ, log okuma, yazma veya I/O işlemlerinin beklenenden uzun sürdüğünü tespit etmiştir.
	• Bu sorun, işletim sistemi veya depolama sistemi ile ilgili performans problemlerinden kaynaklanabilir.
	• Queue manager performansını olumsuz etkileyebilir.
Çözüm:
	1. Çevresel Değişkenleri Ayarlayın:
		○ Depolama performansı sorunlarını teşhis etmek veya bu gecikmelere karşı toleransı artırmak için şu değişkenleri kullanabilirsiniz:
			§ AMQ_IODELAY
			§ AMQ_IODELAY_INMS
			§ AMQ_IODELAY_FFST
	2. Daha Fazla Bilgi:
		○ Bu değişkenler hakkında detaylı bilgi için IBM MQ dokümantasyonuna başvurun.

IBM MQ'nun Db2 ile Koordinasyonu Sorunu
Senaryo:
	• IBM MQ Explorer üzerinden queue manager'ları başlatıyorsunuz, ancak Db2 ile koordinasyonda sorun yaşıyorsunuz.
	• Queue manager hata günlüğünde şu hatayı görüyorsunuz:

AMQ7604: The XA resource manager 'DB2 MQBankDB database' was not available when called for xa_open. The queue manager is continuing without this resource manager.
Açıklama:
	• IBM MQ servis işlemini çalıştıran kullanıcı kimliği (genellikle MUSR_MQADMIN), DB2USERS grubunun üyesi olmayabilir.
	• Bu durum, grup üyeliği bilgilerini içermeyen bir erişim belirteciyle çalıştığından hata oluşmasına neden olur.
Çözüm:
	1. Kullanıcı Grubu Üyeliğini Doğrulayın:
		○ MUSR_MQADMIN kullanıcı kimliğinin DB2USERS grubunun bir üyesi olduğundan emin olun.
	2. Komutları Sırasıyla Çalıştırın:
		○ Servisi durdurun:

net stop MQSeries
		○ Aynı kullanıcı kimliği altında çalışan diğer işlemleri durdurun.
		○ Bu işlemleri yeniden başlatın:

net start MQSeries
		○ Not: Sistemi yeniden başlatmak bu adımları doğrulamanın kesin bir yoludur, ancak genellikle gerekli değildir.



RDQM (Replicated Data Queue Manager) Yapılandırma Sorunlarını Giderme
IBM MQ RDQM yapılandırmasında karşılaşılabilecek yüksek erişilebilirlik (HA) ve felaket kurtarma (DR) sorunlarını teşhis etmek ve çözmek için ayrıntılı bir rehber sunuyoruz.

1. RDQM Mimarisi
RDQM HA ve DR Mimarisi:
	• HA (High Availability): Verilerin çoğaltılması için DRBD kullanır ve RDQM HA kuyruğu için Pacemaker yöneticisi devreye girer.
	• DR (Disaster Recovery): Daha basit bir yapıdadır; yalnızca DRBD ile veri çoğaltması yapılır.
Ana Bileşenler:
	1. DRBD: Verilerin çoğaltılması için kullanılan araç.
		○ Her bir kuyruk yöneticisi için /etc/drbd.d/<kuyruk_adı>.res dosyası oluşturulur.
		○ minor numarası üzerinden DRBD hatalarını takip edebilirsiniz.
	2. Pacemaker:
		○ Kuyruk yöneticisinin hangi düğümde çalışacağını belirler.
		○ p_fs_qm, p_ip_qm, ms_drbd_qm gibi kaynaklar oluşturur.
	3. RDQM Komutları:
		○ rdqmstatus: RDQM durumunu kontrol eder.
		○ drbdadm: DRBD işlemleri için kullanılır.

2. Yaygın Sorunlar ve Çözümler
2.1. DRBD Sorunları
a. DRBD Quorum Kaybı:
	• Belirti: Kuyruk yöneticisi çalışmayı durdurur ve hata günlüklerine "quorum(yes -> no)" kaydı düşer.
	• Çözüm:
		○ rdqmstatus komutuyla durum kontrol edilir.
		○ Bağlantılar geri geldiğinde DRBD quorum otomatik olarak düzelir.
b. Tek DRBD Bağlantısının Kaybı:
	• Belirti: Kuyruk yöneticisi çalışmaya devam eder ancak bir düğümde "Remote unavailable" durumu görülür.
	• Çözüm:
		○ Hata veren düğümdeki bağlantıların yeniden başlatılması gerekebilir:

drbdadm disconnect <kaynak_adı>
drbdadm connect <kaynak_adı>
c. Senkronizasyonun Takılması:
	• Belirti: drbdadm status çıktısında "replication: SyncSource" ve "done" değeri artmıyor.
	• Çözüm:
		○ Problemli düğümde bağlantılar yeniden başlatılır:

drbdadm disconnect <kaynak_adı>
drbdadm connect <kaynak_adı>

2.2. Pacemaker Sorunları
a. Corosync Zamanlama Problemi:
	• Belirti: Sistem günlüğünde "Corosync main process was not scheduled" hatası görülür.
	• Sebep: Sanal makinede (VM) yeterli CPU zamanı atanamıyor.
	• Çözüm:
		○ VM için CPU ve kaynak kullanımı optimize edilir.
		○ Corosync zaman aşımı değerleri artırılabilir.
b. Kuyruk Yöneticisi Yanlış Düğümde Çalışıyor:
	• Belirti: RDQM HA preferred location değeri düzeltilmesine rağmen kuyruk yöneticisi hareket etmiyor.
	• Çözüm:
		○ rdqmclean komutuyla hatalı eylemler temizlenir:

rdqmclean -m <kuyruk_yöneticisi_adı>

2.3. Yükseltme Sonrası Problemler
a. DRBD Çekirdek Modülü Uyuşmazlığı:
	• Belirti: Kuyruk yöneticisi başlatılamaz veya DRBD modülü "Partially loaded" durumundadır.
	• Çözüm:
		○ Çekirdek sürümüne uygun DRBD modülü yüklenir:

yum install drbd-<uyumlu_sürüm>
b. Hafif Uyumsuzluk:
	• Belirti: DRBD modülü çalışıyor ancak uyumsuz bir sürüm kullanılıyor.
	• Çözüm:
		○ Uygun DRBD sürümü yüklenerek sistem tam uyumlu hale getirilir.

3. RDQM Durum Kontrol Komutları
	1. Durum Görüntüleme:

rdqmstatus -m <kuyruk_yöneticisi_adı>
	2. Hatalı Kaynak Eylemleri Görüntüleme:

rdqmstatus -m <kuyruk_yöneticisi_adı> -a
	3. DRBD Durumu Görüntüleme:

drbdadm status
	4. Bağlantı Yenileme:

drbdadm disconnect <kaynak_adı>
drbdadm connect <kaynak_adı>

Sonuç
RDQM yapılandırma sorunlarının çözümü için doğru teşhis ve sistematik bir yaklaşım gereklidir. Bu rehberde belirtilen adımları takip ederek IBM MQ RDQM yapılandırmalarınızda yüksek erişilebilirlik ve felaket kurtarma işlevlerini sorunsuz bir şekilde sürdürebilirsiniz.


IBM MQ Güvenlik Sorunlarını Giderme Rehberi
IBM MQ'da karşılaşılabilecek güvenlik sorunlarını teşhis etmek ve çözmek için kapsamlı bir rehber sunuyoruz.

1. Kanal Kimlik Doğrulama Kayıtları Sorunları
Kanalın Kuyruk Yöneticisine Gösterdiği Adres
	• Kanalın kullandığı CONNAME değeri (ör. localhost veya gerçek IP adresi), kuyruk yöneticisinin farklı kimlik doğrulama kurallarını tetikleyebilir.
BLOCKADDR ile Kanal Adları Kullanımı
	• SET CHLAUTH TYPE(BLOCKADDR) komutu yalnızca CHLAUTH(*) için geçerlidir.
Z/OS Sistemlerinde CHLAUTH Kullanımı
	• Z/OS sistemlerinde kanal adı içeren yıldız işareti (*), tırnak içinde belirtilmelidir. Örnek: CHLAUTH('*').
SET CHLAUTH Komutunun Kuyruk Yöneticisi Yeniden Başlatıldığında Davranışı
	• SYSTEM.CHLAUTH.DATA.QUEUE kuyruğunun erişilemez (PUT(DISABLED)) olması durumunda, SET CHLAUTH komutu yalnızca bellek üzerinde çalışır. Kalıcı hale getirmek için:

SET CHLAUTH ... ACTION(REPLACE)
IPv6 Adres Deseni Sınırları
	• Z/OS için ADDRESS veya ADDRLIST alanlarının maksimum uzunluğu 48 karakterdir. Daha uzun adresler için yıldız (*) kullanılabilir.

2. CipherSpec Uyuşmazlıkları
TLS El Sıkışma ve Kanal Başlatma Hataları
	• El Sıkışma Hataları: TLS istemcisi ve sunucusu arasında CipherSpec uyumsuzluğu.
	• Kanal Başlatma Hataları: Her iki uçta tanımlanan CipherSpec uyumsuzluğu veya eksikliği.
Çözüm:
	• Her iki uçta da uyumlu CipherSpec tanımlayın. Örneğin:

DEFINE CHANNEL(...) SSLCIPH(...)
Global Sunucu Sertifikası Kullanımı
	• Global Sunucu Sertifikaları daha yüksek şifreleme gerektirir. Uyumlu bir CipherSpec tanımlayın.

3. TLS El Sıkışma Sorunları
Yaygın Sorunlar ve Çözümleri
	1. Sertifika İptali:
		○ Çözüm: Sertifikayı iptal listelerine (CRL/ARL) karşı kontrol edin.
	2. OCSP Yanıtlayıcı Sorunları:
		○ Çözüm: OCSP ile sertifikayı doğrulayın.
	3. Geçersiz veya Etkin Olmayan Sertifika:
		○ Çözüm: Sertifikanın geçerlilik tarihlerini kontrol edin.
	4. Eksik veya Zarar Görmüş Sertifika:
		○ Çözüm: Sertifikayı yenileyin veya tamamlayın.
	5. Eksik Kök Sertifika veya Zincir:
		○ Çözüm: Tam bir güven zincirini sağlayın ve gerekli tüm CA sertifikalarını ekleyin.

4. Doğrulama Belirteçleri (Authentication Token) Sorunları
Yöneticiye Özel Öneriler
	• Kuyruk Yöneticisi Yapılandırması:
		○ Kuyruk yöneticisinin belirteçleri kabul ettiğinden emin olun:

REFRESH SECURITY TYPE(CONNAUTH)
	• Belirteç Deposu:
		○ AuthToken yapılandırmasındaki KeyStore ve KeyStorePwdFile yollarını kontrol edin.
	• Kök Sertifika:
		○ Belirteç verenin kök sertifikasını doğru anahtar deposuna ekleyin.
Geliştiriciye Özel Öneriler
	• Hata Kodları:
		○ Bağlantı sorunlarında, aşağıdaki hata kodlarını inceleyin:
			§ 2035 MQRC_NOT_AUTHORIZED
			§ 2063 MQRC_SECURITY_ERROR
			§ 2064 MQRC_TOKEN_TIMESTAMP_NOT_VALID
	• Belirteç Formatı:
		○ Belirteç yapısı ve içeriklerinin doğru olduğunu kontrol edin (başlık, yük, imza).

5. TLS Sistemindeki Diğer Sorunlar
Eksik Sertifika veya İmzacı
	• İstemci veya Sunucuda Eksik Sertifika:
		○ Çözüm: Sertifikaları karşılıklı güven depolarına ekleyin.
SSLPEER Uyuşmazlıkları
	• Çözüm: SSLPEER değerinin sertifika ile eşleştiğinden emin olun.
FIPS Modu Uyuşmazlığı
	• Çözüm: FIPS uyumlu bir şifreleme kullanın veya FIPS modunu devre dışı bırakın.

6. Anahtar Deposu ve Şifreleme Sorunları
Anahtar Deposu Erişim Sorunları
	• Çözüm: Anahtar deposu dosyalarının doğru yerleştirildiğinden ve erişim izinlerinin uygun olduğundan emin olun.
Şifreleme Sorunları
	• JVM özelliklerini doğru tanımlayın:

javax.net.ssl.keyStore=/path/to/keystore
javax.net.ssl.keyStorePassword=password



WCF için IBM MQ Özelleştirilmiş Kanal Sorunlarını Giderme Rehberi
IBM MQ'yu Microsoft Windows Communication Foundation (WCF) uygulamalarıyla entegre etmek için kullanılan özelleştirilmiş kanal yapılandırmalarında karşılaşılabilecek sorunları tanımlamak ve çözmek için detaylı bir rehber.

1. WCF Özelleştirilmiş Kanal İstisna Hiyerarşisi
Genel İstisna Türleri
	• TimeoutException: Zaman aşımı nedeniyle oluşur.
	• CommunicationException: İletişim sırasında meydana gelen hataları temsil eder. Alt sınıfları şunları içerebilir:
		○ IBM.XMS.XMSException
		○ IBM.WMQ.MQException
SOAP/JMS Arayüzünde İstisnalar
	• İlgili İstisnalar:
		○ System.ServiceModel.CommunicationsException
		○ IBM.XMS.XMSException
		○ IBM.WMQ.MQException
	• Eklenen Bilgiler:
		○ IBM.XMS.WCF.ErrorCode: Özel kanal istisnasının hata mesajı kodu.
		○ IBM.XMS.ErrorCode: İlk XMS istisnasının hata mesajı.
		○ IBM.WMQ.ReasonCode: Temel IBM MQ neden kodu.
		○ IBM.WMQ.CompletionCode: Temel IBM MQ tamamlanma kodu.
SOAP Olmayan/Non-JMS Arayüzünde İstisnalar
	• İlgili İstisnalar:
		○ System.ServiceModel.CommunicationsException
		○ IBM.WMQ.MQException
	• Eklenen Bilgiler:
		○ IBM.WMQ.WCF.ErrorCode: Özel kanal istisnasının hata mesajı kodu.
		○ IBM.WMQ.ReasonCode: Temel IBM MQ neden kodu.
		○ IBM.WMQ.CompletionCode: Temel IBM MQ tamamlanma kodu.

2. WCF Versiyon Bilgisi
Versiyon Bilgisine Erişim Yöntemleri
	1. IBM MQ Komutu (dspmqver):
		○ dspmqver komutu kullanılarak versiyon bilgisi alınabilir.
	2. Windows Explorer Özellikler Menüsü:
		○ IBM.XMS.WCF.dll dosyasına sağ tıklayıp, Properties > Version sekmesine gidin.
	3. FFST veya İzleme Dosyaları Başlık Bilgisi:
		○ FFST dosyaları üzerinden versiyon bilgisi alınabilir.

3. WCF İpuçları ve Öneriler
Hata Yönetiminin Dışa Aktarılması
	• WCF servis hostu kullanılırken, hizmet tarafından atılan işlenmemiş istisnalar varsayılan olarak dışa aktarılmaz.
	• Bu istisnalardan haberdar olmak için bir hata işleyici (error handler) kaydedilmelidir.
Kod Örneği: Hata İşleyici Davranışı Aşağıdaki kod, bir hata işleyici hizmet davranışını tanımlamak ve bu davranışı bir hizmete uygulamak için kullanılabilir:

using System.ServiceModel.Dispatcher;
using System.Collections.ObjectModel;
public class ErrorHandlerBehaviorAttribute : Attribute, IServiceBehavior, IErrorHandler
{
    // IServiceBehavior Arayüzü
    public void AddBindingParameters(ServiceDescription serviceDescription,
       ServiceHostBase serviceHostBase, Collection<ServiceEndpoint> endpoints,
       BindingParameterCollection bindingParameters)
    {
    }
public void ApplyDispatchBehavior(ServiceDescription serviceDescription,
        ServiceHostBase serviceHostBase)
    {
        foreach (ChannelDispatcher channelDispatcher in serviceHostBase.ChannelDispatchers) {
            channelDispatcher.ErrorHandlers.Add(this);
        }
    }
public void Validate(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)
    {
    }
// IErrorHandler Arayüzü
    public bool HandleError(Exception e)
    {
        // Hatanın istenilen şekilde işlenmesi (örneğin, konsola yazdırma)
        Console.Out.WriteLine(e);
// Diğer hata işleyicilerinin çalışmasına izin vermek için false döndürülür
        return false;
    }
public void ProvideFault(Exception error, MessageVersion version, ref Message fault)
    {
    }
}

4. Genel Sorunlar ve Çözümleri
İstisna İletişimi
	• CommunicationException: Alt katmanlardan alınan ek istisnalarla bağlanır ve daha ayrıntılı bilgiler sağlar.
	• Çözüm: En üst düzeydeki istisnayı inceleyerek kök nedenleri belirleyin.
DLL ve Konfigürasyon Sorunları
	• Çözüm: DLL versiyonlarının doğru olduğundan ve yapılandırmaların güncel olduğundan emin olun.



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


IBM MQ İçin IBM Destek ile İletişim ve Sorun Giderme Bilgilerinin Toplanması
1. IBM Destek ile İletişim
IBM MQ ile ilgili sorunlarınızda IBM Destek ile iletişim kurabilirsiniz. Aşağıdaki adımlar, destek talebi oluşturma ve sorun giderme bilgilerini IBM'e gönderme süreçlerini açıklar.

2. IBM Destek Web Sayfaları
	• Multiplatformlar İçin IBM MQ Destek Web Sayfası
	• z/OS İçin IBM MQ Destek Web Sayfası

3. Sorun Giderme Verilerini Toplama
Sorun yaşadığınızda, IBM'e destek talebi açarken aşağıdaki yöntemlerle detaylı sorun giderme bilgilerini toplayabilirsiniz.
3.1 Otomatik Verilerin Toplanması (runmqras)
	• Komut: runmqras
	• Amacı: Tüm hata günlüklerini, yapılandırma dosyalarını, işlem bilgilerini ve daha fazlasını toplar ve sıkıştırılmış bir arşiv oluşturur.
	• Hazırlık:
		○ IBM MQ'nun Java bileşenini yükleyin veya sistemde geçerli bir JRE bulunmasını sağlayın.
		○ Çevresel değişkenleri IBM MQ kurulum dizinine göre ayarlayın:

# Linux/UNIX
. /opt/mqm/bin/setmqenv -n Installation1

# Windows
C:\Program Files\IBM\MQ\bin\setmqenv -n Installation2
3.2 Kullanım Adımları
	1. IBM Vaka Numarasıyla Dosya Oluşturma:

# Linux/UNIX
runmqras -caseno TS123456789

# Windows
runmqras -caseno TS123456789
	2. Belirli Bölümlerin Verilerini Toplama: Örneğin, kuyruk yöneticisi tanımları ve küme yapılandırmaları:

runmqras -caseno TS123456789 -section defs,cluster,trace
	3. Hedef Kuyruk Yöneticilerini Belirleme:

runmqras -caseno TS123456789 -section defs,cluster,trace -qmlist QMA,QMB
	4. Büyük Dosyalar İçin Çalışma Dizini Ayarlama:

runmqras -caseno TS123456789 -workdirectory /tmp/mq_logs
	5. Dosyayı IBM'e Gönderme: Oluşturulan dosyayı (TS123456789-runmqras.zip) IBM Destek'e yükleyin.
3.3 Manuel Verilerin Toplanması
Otomatik araçlar kullanılamıyorsa, verileri manuel olarak toplayabilirsiniz.
	1. IBM MQ Sürümü ve İşletim Sistemi Bilgisi:
		○ IBM MQ: dspmqver
		○ İşletim Sistemi:

uname -a # Linux/UNIX
systeminfo # Windows
	2. Hata ve Yapılandırma Dosyalarını Toplama:
		○ Hata Günlükleri:

ls -ltR /var/mqm/errors
		○ Kuyruk Yöneticisi LogPath:

ls -ltR /var/mqm/log/QMA
	3. Kuyruk Yöneticisi Durumunu Kaydetme:

dspmq -a
	4. Ağ Bağlantılarını İnceleme:
		○ Linux/UNIX: netstat -an
		○ Windows: NETSTAT -AN
	5. Toplanan Verileri Paketleme:
		○ Linux/UNIX:

tar -cvzf TS123456789-mqdata.tar.gz /var/mqm/errors /var/mqm/qmgrs
		○ Windows: Windows Gezgini ile sıkıştırılmış dosya oluşturun.
		
		
		
		
		
		
		

Genel Veri Toplama Adımları
	1. Sorununuzu Netleştirin:
		○ Hangi sorunla karşılaşıyorsunuz?
		○ Sorun ne zaman başladı ve ne zaman sona erdi?
		○ Hangi uygulamalar, kullanıcılar veya IBM MQ objeleri etkileniyor?
	2. runmqras Komutu ile Otomatik Veri Toplama:
		○ Komut:

runmqras -section defs,trace -qmlist QMA -caseno TS123456789
		○ Açıklama: defs yapılandırma bilgilerini, trace ise hata ayıklama bilgilerini toplar.
	3. Manuel Veri Toplama:
		○ Kuyruk yöneticisi yapılandırma dosyalarını ve hata günlüklerini kaydedin.
		○ mqconfig, dmpmqlog, amqsbcg gibi komutları kullanarak ek bilgiler toplayın.
		○ Sorunla ilgili ekran görüntüleri veya komut çıktıları ekleyin.
	4. Soruna Özel Ek Bilgiler Toplayın:
		○ AMS Problemleri: keystore.conf dosyaları ve sertifika detaylarını ekleyin.
		○ Kanal Problemleri: Hem yerel hem de uzak kuyruğu yöneticisinden eşzamanlı izleme verilerini alın.
		○ Java ve JMS Uygulamaları: mqjms.log, native_stdout.log, native_stderr.log gibi dosyaları ekleyin.
		○ TLS Problemleri: TLS sertifikalarının geçerlilik tarihlerini ve yapılandırma detaylarını sağlayın.
		○ Tetikleme Problemleri: Tetikleme sırasındaki izleme dosyalarını toplayın.
	5. Toplanan Verileri IBM'e Gönderin:
		○ FTP ve E-posta İle: IBM Software Support sayfasındaki talimatları takip edin.
		○ IBM My Support Site: Sorununuzu açıklayan bir vaka oluşturun ve topladığınız verileri buradan yükleyin.

IBM MQ Hata Günlüklerinin Kullanımı
IBM MQ, problem tanımlama ve giderme için farklı hata günlükleri sağlar. Hata günlüklerinin doğru kullanımı, sorunları hızlı bir şekilde çözmenize yardımcı olabilir. Bu belge, hata günlüklerinin nasıl kullanılacağını ve özelleştirileceğini açıklar.

Hata Günlükleri Türleri ve Konumları
	1. Genel Sistem Hata Günlükleri:
		○ Linux ve AIX: /var/mqm/errors
		○ Windows: MQ_INSTALLATION_PATH\errors
	2. Kuyruk Yöneticisi Hata Günlükleri:
		○ Kuyruk yöneticisinin adı biliniyorsa:
			§ Linux ve AIX: /var/mqm/qmgrs/qmname/errors
			§ Windows: MQ_INSTALLATION_PATH\qmgrs\qmname\errors
	3. İstemci Hata Günlükleri:
		○ İstemci uygulamaları için:
			§ Linux ve AIX: /var/mqm/errors
			§ Windows: MQ_DATA_PATH\errors
	4. Ön Yükleme Hataları:
		○ Sistem yapılandırması doğru şekilde yüklenemediğinde:
			§ Linux ve AIX: /var/mqm
			§ Windows: C:\Program Files\IBM\MQ

Hata Günlüğü Formatı
	• Hata mesajlarının detayları ISO 8601 formatında zaman damgaları ile kayıt edilir.
	• Mesajlar aşağıdaki önem seviyelerine göre sınıflandırılır:
		○ I (Informational): Bilgilendirme
		○ W (Warning): Uyarı
		○ E (Error): Hata
		○ S (Severe): Kritik Hata
		○ T (Termination): Sonlandırma
Örnek Mesaj:

AMQ7075W: Unknown attribute foo at /var/mqm/qmgrs/QM1/qm.ini in configuration data.
Time(2023-12-06T10:15:30.456Z)

Günlük Yönetimi ve Özelleştirme
	1. Boyut ve Döngü Ayarları:
		○ Günlük dosyalarının varsayılan boyutu 32 MB’tır.
		○ QMErrorLog bölümünde LogSize parametresi ile değiştirilebilir.
	2. Mesajların Bastırılması:
		○ QMErrorLog Stanza:

SuppressMessage=9999,9002,9209
SuppressInterval=30
		○ Ortam Değişkenleri:

export MQ_CHANNEL_SUPPRESS_MSGS=9999,9002,9209
export MQ_CHANNEL_SUPPRESS_INTERVAL=60,5
	3. Yönlendirme ve Yetki:
		○ Hata mesajları uygun erişim izni olmayan kullanıcılar tarafından yazılamaz. Bu durumda, sistem hata günlüğüne yönlendirilir.
		○ MQ Explorer kullanarak hata mesajlarını özelleştirebilirsiniz.

Örnek Kullanım ve İnceleme
Hata Günlüğü Örneği:

plaintext
Copy code
17/11/2024 10:32:29 - Process(2132.1) User(USER_1) Program(runmqchi.exe)
Host(HOST_1) Installation(Installation1)
VRMF(8.0.0.0) QMgr (QM1)
AMQ9542: Queue manager is ending.
EXPLANATION:
The program will end because the queue manager is quiescing.
ACTION:
None.
Hata Günlüğü İnceleme:
	• Sistem düzenleyicisi kullanarak hata günlüklerini inceleyebilirsiniz:

less /var/mqm/qmgrs/QM1/errors/AMQERR01.LOG
