
BM MQ'nin depolama ve performans gereksinimleri, platformlara ve hangi bileşenlerin kullanılacağına bağlı olarak değişir. Bu gereksinimler, uygulamanın verimli çalışabilmesi için doğru yapılandırmanın yapılmasını sağlar. İşte IBM MQ'nin Multiplatformlarda depolama ve performans gereksinimlerini ele alırken göz önünde bulundurulması gereken temel konular:
Depolama Gereksinimleri
IBM MQ, kuyruk yöneticisi verilerini dosya sisteminde saklar. Bu nedenle doğru dosya yapılarının oluşturulması ve yapılandırılması gereklidir. Ayrıca disk alanı gereksinimleri, kurulu bileşenlere, kullanılan kuyruk sayısına ve mesajların boyutlarına bağlı olarak değişir.
Disk Alanı Gereksinimleri:
IBM MQ'nin kurulumunda kullanılacak bileşenlere göre farklı disk alanı gereksinimleri olabilir. Bununla birlikte, bazı bileşenler opsiyoneldir ve ek disk alanı talep edebilir. Örneğin:
	• AIX, Linux, Windows ve IBM i sistemlerinde IBM MQ için ortalama disk alanı gereksinimleri şunlardır:
		○ AIX: 1810 MB (Tam kurulum)
		○ IBM i: 1965 MB (Tam kurulum)
		○ Linux (x86-64): 2010 MB (Tam kurulum)
		○ Windows: 2310 MB (Tam kurulum)
Log Dosyaları ve Performans:
Log dosyaları da önemli bir depolama gereksinimi oluşturur. IBM MQ, dairesel (circular) veya doğrusal (linear) loglama yöntemlerini kullanabilir. Dairesel loglama daha hızlı performans sağlar, çünkü eski loglar yeniden kullanılabilir. Ancak doğrusal loglama daha fazla hata koruması sağlar ve logların geri alımında daha fazla güvenlik sunar.
Paylaşılan Dosya Sistemleri
IBM MQ, çoklu örnek kuyruk yöneticilerini çalıştırırken, paylaşılan dosya sistemleri kullanarak kuyruk yöneticilerinin veri ve log dosyalarını paylaşabilir. Ancak paylaşılan dosya sistemlerinin, veri yazma bütünlüğünü, dosyalara garantili tekil erişim sağlamak ve başarısızlık durumunda kilitlerin serbest bırakılmasını sağlayacak özelliklere sahip olması gerekir.
	• NFS (Network File System) ve SMB (Server Message Block) gibi protokoller, paylaşılan dosya sistemlerinde IBM MQ için kritik öneme sahiptir.
	• Paylaşılan Dosya Sistemi Gereksinimleri:
		○ Veri yazma bütünlüğü: Dosyalar doğru şekilde yazılmalı, özellikle hatalı yazma veya kesilme durumlarıyla başa çıkabilmelidir.
		○ Dosyalara garantili tekil erişim: Bir kuyruk yöneticisi aktifken, başka bir kuyruk yöneticisinin aynı dosyaya erişimi engellenmeli, kilitleme sağlanmalıdır.
		○ Kilidin serbest bırakılması: Kuyruk yöneticisi çökerse veya dosya sistemine bağlantı kaybolursa, kilitlerin doğru şekilde serbest bırakılması gerekir.
Queue Manager Yapısı
IBM MQ, kuyruk yöneticisinin verilerini yerel dosya sistemlerinde saklar, ancak çoklu örnek (multi-instance) kuyruk yöneticileri için veriler paylaşılan dosya sistemlerinde saklanmalıdır. Bu yapılar, performansı ve güvenliği artıracak şekilde yapılandırılabilir.
AIX ve Linux Sistemlerinde Kuyruk Yöneticisi Dizini:
IBM MQ'de kuyruk yöneticisi dizin yapısı genellikle /var/mqm altında oluşturulur. Bu dizin yapısı, qmgrs ve log dizinleri gibi kuyruk yöneticisi verilerini içeren alt dizinleri barındırır. Ayrıca, bu dizinlerin farklı dosya sistemlerinde paylaşılması performansı artırabilir.
Dosya Sistemlerini Test Etme
Paylaşılan dosya sistemlerinin IBM MQ için uygun olup olmadığını test etmek için amqmfsck komutu kullanılabilir. Bu komut, dosya sisteminin IBM MQ gereksinimlerini karşılayıp karşılamadığını kontrol eder.
Loglama Yöntemleri
	• Dairesel Loglama (Circular Logging):
		○ Performans açısından daha iyidir, çünkü eski loglar yeniden kullanılabilir.
		○ Yönetimsel olarak daha kolaydır, çünkü ek log dosyaları oluşturulmaz.
	• Doğrusal Loglama (Linear Logging):
		○ Hata durumlarına karşı daha fazla güvenlik sağlar, çünkü hasar görmüş nesneler doğrusal loglardan geri alınabilir.
		○ Daha fazla yönetim gereksinimi ve performans kaybı vardır, çünkü her log yeni bir medya görüntüsü gerektirir.
Özet
IBM MQ'nun verimli çalışabilmesi için doğru depolama ve performans yapılandırmalarının yapılması gerekmektedir. Paylaşılan dosya sistemleri, loglama yöntemleri ve kuyruk yöneticisi dizin yapıları, sistemin güvenli ve yüksek performanslı çalışmasını sağlamak için doğru şekilde planlanmalıdır. Bu gereksinimler, işletim sistemi türüne ve IBM MQ yapılandırmasına göre değişebilir.
