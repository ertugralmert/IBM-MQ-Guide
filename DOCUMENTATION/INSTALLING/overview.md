IBM MQ Kurulumuna Genel Bakış
IBM MQ'nun kurulumu, hangi platformda kullanıldığına ve hangi bileşenlerin yükleneceğine bağlı olarak farklılıklar gösterebilir. IBM MQ'nun kurulumu aşağıdaki adımlarla gerçekleştirilir:
	1. Bileşenler ve Özellikler:
		○ IBM MQ'yu kurarken ihtiyacınız olan bileşenleri seçebilirsiniz. Sunucu ve istemci kurulumları farklıdır.
		○ Sunucu kurulumu: Bir veya birden fazla kuyruk yöneticisi içerir.
		○ İstemci kurulumu: Bir uygulamanın, başka bir sistemdeki kuyruk yöneticisiyle iletişim kurmasını sağlar.
	2. Lisans Gereksinimleri:
		○ IBM MQ'nun doğru şekilde çalışabilmesi için gerekli lisansların alınmış olması gerekir. Kurulum sırasında lisans anlaşması bilgileri sisteme kaydedilir.
	3. Yazılım Gereksinimleri:
		○ IBM MQ'nun desteklediği işletim sistemleri ve yazılım gereksinimleri için IBM MQ Sistem Gereksinimleri web sitesini kontrol etmelisiniz.
	4. Kurulum Resimleri:
		○ IBM MQ'nun kurulumu için gerekli dosyalar, Passport Advantage veya Fix Central gibi kaynaklardan indirilebilir.
Kurulum Adımları
IBM MQ kurulumunun her platformda nasıl yapılacağına dair detaylar aşağıda verilmiştir:
	1. Sunucu Kurulumu:
		○ AIX, Linux, Windows ve IBM i platformlarında sunucu kurulumu için özel talimatlar bulunur. Her platformda IBM MQ'nun sunucu ve istemci bileşenleri ayrı olarak yüklenebilir.
	2. İstemci Kurulumu:
		○ IBM MQ istemcisi, ayrı bir makinede kurulu bir kuyruk yöneticisiyle iletişim kuran bir bileşendir. Sunucu ve istemcinin aynı sistemde kurulu olması mümkündür, ancak her iki bileşen arasında bir MQI kanalı tanımlanmalıdır.
	3. Bileşen Seçimi:
		○ IBM MQ'nun kurulumunda Advanced Message Security, Managed File Transfer, MQ Telemetry ve RDQM gibi bileşenler de ayrıca kurulabilir. Bu bileşenlerin kurulumunda uygun lisansların alındığından emin olmalısınız.
	4. Z/OS Kurulumu:
		○ IBM MQ'nun z/OS sistemlerinde kurulumu, ShopZ web sitesinden yapılabilir.
Lisans Gereksinimleri
IBM MQ'nun kurulumunda IBM License Metric Tool (ILMT) kullanılabilir. Bu araç, IBM MQ'yu kurduğunuzda otomatik olarak lisansları izler ve her kuyruk yöneticisi başlatıldığında lisans uyumunu kontrol eder.
	• Lisans bilgileri, /licenses dizininde saklanır ve her zaman okunabilir.
	• Deneme lisansı kullanıyorsanız, belirli talimatlara uyarak bu lisansı tam bir lisansa dönüştürebilirsiniz.
Kurulum Sonrası
IBM MQ'nun başarılı bir şekilde kurulup kurulmadığını doğrulamak için aşağıdaki adımları izleyebilirsiniz:
	1. Kurulum Doğrulaması:
		○ IBM MQ kurulumunun doğru yapıldığını doğrulamak için dspmqver komutunu kullanarak kurulum bilgilerini görüntüleyebilirsiniz.
	2. Kurulum Resmi Web Siteleri:
		○ IBM MQ'nun kurulum dosyalarını ve güncellemelerini Fix Central ve Passport Advantage gibi platformlardan indirebilirsiniz.
IBM MQ Kaldırılması
IBM MQ'nun kaldırılması için, kurulum işleminin tersine yapılacak işlemler gereklidir. IBM MQ, platforma özel komutlar ile kaldırılabilir. Örneğin, Windows platformunda bir "uninstall" komutu kullanılabilir.


************


IBM MQ Kurulumu İçin Ön Hazırlık
İlk olarak IBM MQ'yu kullanmayı planladığınız platformun gereksinimlerini ve kurulum yapacağınız ortamı iyi bir şekilde belirlemelisiniz. IBM MQ’nun aşağıdaki bileşenleri olabilir:
	1. Sunucu ve İstemci Bileşenleri: IBM MQ, bir sunucu ya da istemci olarak kurulabilir. Sunucu, kuyruk yöneticilerini ve kuyrukları barındıran bir bileşendir. İstemci ise bir sunucudaki kuyruk yöneticisiyle iletişim kuran bir uygulamadır.
	2. Yazılım ve Donanım Gereksinimleri: Kurulum öncesinde, IBM MQ’nun çalışacağı işletim sistemi ve donanım gereksinimlerinin karşılandığından emin olmalısınız. Bu gereksinimleri IBM MQ Sistem Gereksinimleri bölümünden kontrol edebilirsiniz.
Kurulum İçin Konfigürasyon Seçenekleri
IBM MQ’nun kurulumuna başlamadan önce, aşağıdaki konuları değerlendirmeniz gerekir:
	1. Kurulum Yeri ve Adı:
		○ IBM MQ kurulumlarının her birinin benzersiz bir kurulum adı vardır. İlk kurulumda bu isim Installation1 olarak atanır. Daha fazla kurulum yapıldıkça bu isim sırasıyla artar. AIX, Linux ve Windows sistemlerinde her kurulum için bu isim belirlenebilir.
		○ Aşağıdaki kurulum yollarını inceleyebilirsiniz:
			§ Varsayılan Kurulum Yeri:
				□ AIX: /usr/mqm
				□ Linux: /opt/mqm
				□ Windows: C:\Program Files\IBM\MQ
			§ Özel Kurulum Yeri: İsterseniz IBM MQ’yu özel bir yere kurabilirsiniz. Bu yolu belirtmeniz gerekecek.
	2. Birincil Kurulum (Primary Installation):
		○ IBM MQ’nun birincil kurulumu, sistem genelinde kullanılan kütüphane ve komutlara yönlendirme yapan kurulumdur. Birincil kurulum, IBM MQ ile etkileşimde bulunan uygulamalar için önemlidir çünkü bu kurulum tüm sistem genelindeki işlevlere erişimi sağlar.
		○ Eğer birden fazla IBM MQ kurulumunuz olacaksa, birini birincil kurulum olarak belirlemeniz gerekecek. Bu, sistemdeki çeşitli komut ve kütüphanelerin doğru kurulumla ilişkilendirilmesini sağlar.
	3. Birincil Kurulum Seçenekleri:
		○ AIX/Linux/Windows: İlk kurulum otomatik olarak birincil kurulum olarak ayarlanabilir. Eğer birden fazla kurulum yapıyorsanız, birincil kurulum belirlemek için setmqinst komutunu kullanabilirsiniz.
	4. Birden Fazla IBM MQ Kurulumu:
		○ IBM MQ, AIX, Linux ve Windows üzerinde birden fazla kurulum yapmayı destekler. Birden fazla kurulum, sistemin farklı versiyonlarını veya yapılandırmalarını aynı anda çalıştırmanıza olanak tanır. Fakat her kurulumun farklı bir kurulum yolunda olması gerekir. Bu sayede birden fazla versiyon veya yapılandırma üzerinde çalışabilirsiniz.
Kurulum Gereksinimleri ve Yönlendirme
	1. Kütüphaneler ve Kontrol Komutları:
		○ IBM MQ’nun kütüphaneleri, belirli komutlar ve çıkışlar için /usr/lib, /usr/bin gibi sistem dizinlerine sembolik bağlantılar yapılır. Bu, uygulamaların ve komutların doğru şekilde çalışmasını sağlar.
		○ AIX ve Linux: Kurulumda, birincil kurulum olarak belirlediğiniz versiyonun kütüphanelerine ve komutlarına sembolik bağlantılar oluşturulur.
		○ Windows: Windows sistemlerinde, birincil kurulumun yeri tüm sistem için referans alınır ve bu referans, uygulamalar ve sistem işlevleri için önemlidir.
	2. Yapılandırmalar ve Çevresel Değişkenler:
		○ Uygulamalarınızın doğru kurulumla iletişim kurabilmesi için setmqenv ve crtmqenv komutlarıyla çevresel değişkenleri yapılandırabilirsiniz.
		○ AIX ve Linux: Çevresel değişkenleri doğru ayarlamak için, setmqenv komutunu kullanarak, kütüphanelerin ve komutların doğru bir şekilde bulunmasını sağlayabilirsiniz.
	3. Uygulama Bağlantıları:
		○ Uygulamalarınızın doğru IBM MQ kütüphanelerini bulabilmesi için sistemdeki doğru kurulum adıyla bağlantı kurması gereklidir. Bu, uygulamaların doğru kuyruk yöneticisiyle iletişim kurmasını sağlar.
	4. Uygulama Çıkışları:
		○ Birincil kurulum gerektiğinde, özel çıkışlar ve kurulum hizmetlerinin de uygun şekilde yapılandırılması gerekir. Çıkışlar doğru kurulumu işaret etmek için sistemdeki belirli dizinlere yerleştirilir.
Kurulum Sonrası Yapılacaklar
	1. Kurulumun Doğrulanması:
		○ IBM MQ’nun doğru kurulduğunu doğrulamak için dspmqver komutunu kullanarak kurulum bilgilerini kontrol edebilirsiniz.
		○ Ayrıca: IBM MQ’nun kurulumunun ve çalışan bileşenlerinin düzgün bir şekilde yapılandırıldığını kontrol etmek önemlidir.
	2. Yedekleme ve Bakım:
		○ Kurulumdan sonra, IBM MQ’nun düzgün çalışması için düzenli bakım yapmanız önemlidir. Ayrıca, IBM MQ’nun çeşitli özelliklerini kullanırken, uygulama ve veri güvenliği için yedekleme yapmak gerekir.
	3. Sistem İletişimi ve Bağlantılar:
		○ Sunucu-iletişim bağlantılarının doğruluğunu kontrol etmelisiniz. AIX, Linux ve Windows platformlarında TCP/IP veya başka iletişim protokollerini kullanarak doğru bağlantıları kurmalısınız.
