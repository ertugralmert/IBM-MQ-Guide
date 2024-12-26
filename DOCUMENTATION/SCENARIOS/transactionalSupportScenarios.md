1. İşlem Birimi (Unit of Work) Nedir?
İşlem birimi, bir dizi işlemi tek bir birim olarak ele alır. Bu birim, işlemlerin ya tamamen başarılı olmasını ya da tamamen başarısız olmasını garanti eder. Eğer işlem sırasında bir hata oluşursa, yapılan değişiklikler geri alınır (backout). İşlem birimi şunları içerir:
	• Commit: İşlem biriminin başarıyla tamamlanıp yapılacak değişikliklerin kalıcı hale getirilmesi.
	• Backout: Hata durumunda yapılan değişikliklerin geri alınması.
2. Yerel ve Global İşlem Birimleri
	• Yerel İşlem Birimi: Yalnızca IBM MQ kuyruğunda yapılan işlemleri içerir. Bu işlem birimi MQCMIT (commit) veya MQBACK (backout) komutları ile tamamlanır. Yerel işlem birimi yalnızca IBM MQ kuyruğunda çalışır.
	• Global İşlem Birimi: Birden fazla kaynak yöneticisini (veritabanları gibi) içerir. IBM MQ, bir işlem birimini koordinasyon için birden fazla sistemde senkronize eder. Bu işlem, iki aşamalı commit (two-phase commit) süreci ile yönetilir.
3. Global İşlem Birimi Koordinasyonu
	• Queue Manager'ın Koordinasyonu: IBM MQ, global işlem birimlerini kendi başına koordine edebilir. Bu durumda, MQBEGIN komutu ile işlem başlatılır, ardından MQCMIT veya MQBACK komutları ile işlem tamamlanır veya geri alınır.
	• Dış Yazılım Koordinasyonu: IBM MQ dışında bir yazılım (örneğin TXSeries veya Tuxedo) global işlem birimini koordine edebilir. Bu durumda, dış yazılımın API'si kullanılır ve MQBEGIN ile işlem başlatılmaz.
4. İşlem Birimi İlerleme Durumu ve Kurtarma
	• IBM MQ, işlem birimleri sırasında veritabanı ile bağlantı kaybolursa, yeniden bağlantı kurulduğunda işlem birimi otomatik olarak kurtarılır. Eğer bir işlem birimi başarıyla başlatılmış fakat tamamlanmamışsa, queue manager rsvmqtrn komutuyla bu durumları yönetebilir.
5. Veritabanı Koordinasyonu
	• XA Protokolü: IBM MQ, veritabanı güncellemelerini koordine etmek için XA protokolü kullanır. Bu protokolde, her kaynak yöneticisi (veritabanı gibi) commit veya backout kararlarını verir.
	• Veritabanı Bağlantısı: IBM MQ, işlem birimi içinde veritabanına SQL sorguları gönderdiğinde, MQCMIT komutuyla bu sorguların sonucu kalıcı hale gelir.
6. İzolasyon Seviyeleri (Isolation Levels)
	• İzolasyon Seviyesi: IBM MQ, işlem biriminde, bir mesajın kuyruğa gönderilmeden önce veritabanında yapılan güncellemelerin görülebilir olup olmayacağını belirler. İki aşamalı commit işlemi ile bu sorun çözülür. Veritabanı yapılandırmasına göre, commit işlemi önce veritabanında yapılabilir, ardından IBM MQ kuyruğunda yapılabilir.
7. Güvenlik ve Yöneticilik
	• Veritabanı Bağlantı Yönetimi: IBM MQ, işlem birimi başlatıldığında, veritabanı ile bağlantıyı kurar ve bu bağlantıyı, işlem biriminin sonunda sonlandırır. Bu süreçte kullanılan kimlik doğrulama bilgileri, XAOpenString içinde belirtilir.
	• Güvenlik Önlemleri: IBM MQ ile veritabanı arasındaki güvenlik, her iki sistemde de doğru kullanıcı yetkilendirmeleri ile sağlanır. Örneğin, Db2 veya Oracle gibi veritabanlarında, IBM MQ'nun işlemi gerçekleştirebilmesi için gerekli izinler tanımlanmalıdır.
8. Veritabanı Konfigürasyonu ve Entegrasyonu
	• Switch Load Dosyaları: Veritabanı yönetimi için IBM MQ'nun switch load dosyaları oluşturulmalıdır. Bu dosyalar, IBM MQ'nun veritabanı ile iletişim kurmasını sağlar. Uygulama tarafından kullanılan veritabanı bağlantıları bu dosyalar aracılığıyla yönetilir.
9. Dinamik Kayıt (Dynamic Registration)
	• Dinamik Kayıt: IBM MQ, veritabanlarında yapılan kalıcı güncellemeleri otomatik olarak kaydeder. Bu optimizasyon, yalnızca kalıcı veritabanı güncellemeleri içeren işlem birimlerinde gerekli olan XA işlevlerini çağırır.
Sonuç:
IBM MQ ile veritabanı koordinasyonu, iki aşamalı commit protokolü kullanarak verilerin tutarlılığını sağlar. Yerel ve global işlem birimleri, farklı senaryolara göre özelleştirilebilir ve IBM MQ'nun sağladığı güçlü yönetim araçları ile güvenli ve verimli bir işlem birimi yönetimi sağlanabilir. Bu süreçlerin doğru çalışabilmesi için sistemin doğru yapılandırılması ve her bileşenin uygun şekilde senkronize olması gerekmektedir.

*****************


enaryo 2: Diğer Yazılımın Koordinasyonu Sağladığı Durum
Bu senaryoda, IBM MQ, global işlem birimlerini koordine etmek için dış bir işlem yöneticisi kullanır. IBM MQ burada işlem birimini koordine etmez; sadece işlemlere katılır. MQBEGIN, MQCMIT, ve MQBACK komutları kullanılamaz.
1. Dış Senkronizasyon Koordinasyonu
Dış bir X/Open XA uyumlu işlem yöneticisi, global işlem birimlerini koordine eder. IBM MQ, bu işlem biriminde bir kaynak yöneticisi olarak yer alır. İşlem yöneticisi (örneğin, TXSeries veya CICS), işlemi başlatır, ilgili kaynak yöneticilerine haber verir ve işlemi iki aşamalı commit süreciyle tamamlar.
İşlem Akışı:
	• Uygulama, dış senkronizasyon yöneticisine bir işlem başlatmak istediğini bildirir.
	• Senkronizasyon yöneticisi, IBM MQ gibi kaynak yöneticilerine bu işlem hakkında bilgi verir.
	• Uygulama, işlemle ilgili kaynak yöneticilerine (örneğin, MQGET komutlarıyla IBM MQ) çağrılar yapar.
	• Uygulama, commit veya backout talebini senkronizasyon yöneticisine iletir.
	• Senkronizasyon yöneticisi, işlem birimini tamamlamak için her kaynak yöneticisine uygun komutları gönderir, genellikle iki aşamalı commit protokolü ile.
2. IBM MQ XA Anahtarı Yapısı
IBM MQ'nun her kaynak yöneticisi için bir XA switch yapısı gereklidir. Bu yapı, kaynak yöneticisinin yeteneklerini ve senkronizasyon yöneticisi tarafından çağrılacak fonksiyonları tanımlar.
	• MQRMIXASwitch: Statik XA kaynak yönetimi için kullanılan yapıdır.
	• MQRMIXASwitchDynamic: Dinamik XA kaynak yönetimi için kullanılan yapıdır.
Çoğu işlem yöneticisi, dinamik XA kaynak yönetimini tercih eder. Bu, daha verimli bir işlem yönetimi sağlar.
3. Dış Senkronizasyon Yöneticisi ve IBM MQ Bağlantısı
Dış senkronizasyon yöneticisinin (örneğin, CICS veya Tuxedo) IBM MQ ile bağlantısı aşağıdaki gibi yapılır:
	• xa_open çağrısı, işlem yöneticisi tarafından yapılır ve bu çağrı, IBM MQ'nun bağlanacağı doğru kuyruğa yönlendirilir.
	• MQCONN çağrısı, işlem yöneticisi ve IBM MQ arasındaki bağlantıyı kurar.
4. CICS Kullanımı
CICS (Customer Information Control System), TXSeries'in bir parçasıdır ve IBM MQ ile iki aşamalı commit protokolüyle çalışır. CICS, IBM MQ'yu bir kaynak yöneticisi olarak kullanabilir, ancak işlemler CICS tarafından koordine edilir. Bu, işlem yöneticisinin IBM MQ işlemlerini yönetmesini sağlar.
CICS Gereksinimleri:
	• CICS ve IBM MQ aynı fiziksel makinede olmalıdır.
	• CICS, yalnızca tek bir IBM MQ kuyruğuna bağlanabilir.
	• CICS, IBM MQ ile etkileşime girmeden önce MQCONN çağrısı yapmalıdır.
5. Microsoft Transaction Server (COM+) Kullanımı
COM+ (Microsoft Transaction Server), iş mantığı uygulamalarını yönetmek için kullanılan bir teknolojidir. COM+ üzerinden yapılan işlemler, IBM MQ ve veritabanı sistemleri gibi arka uç hizmetleriyle entegrasyonu sağlar. IBM MQ, COM+ ile köprü işlevi görür.
6. Global İşlem Birimlerinin Süre Sonu
Queue Manager, işlem yöneticisinin çalışmaya başlaması ve işlemin tamamlanmaması durumunda işlemi sonlandırabilir. AMQ_XA_TRANSACTION_EXPIRY ve AMQ_TRANSACTION_EXPIRY_RESCAN gibi çevresel değişkenlerle, işlem birimlerinin sonlanma sürelerini kontrol edebilirsiniz. Bu özellik, dış işlem yöneticisinin çökmeleri durumunda önemlidir.
7. İyileştirilmiş Dış Senkronizasyon Koordinatörleri
Bazı dış işlem yöneticileri, işlem birimlerinin başarılı bir şekilde tamamlanmasını sağlamak için farklı bağlantı stratejileri kullanır. IBM MQ, genellikle yalnızca tek bir queue manager'a bağlanabilir ve yalnızca bir işlem yöneticisiyle işlem yapabilir. Ancak, CICS veya Tuxedo gibi sistemlerle bu sınırlar aşılabilir.
8. Z/OS ve Recovery Düzeyi
IBM MQ, recovery (kurtarma) süreçlerinde Unit of Recovery özelliği kullanır. Bu özellik, işlemlerin kurtarılmasını ve yeniden başlatılmasını sağlar. CICS veya diğer dış işlem yöneticileri ile yapılan işlemler, kuyruğa bağlı birden fazla sistemde yönetilebilir ve kurtarılabilir.



