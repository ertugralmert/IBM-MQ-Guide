Konteynerlerde IBM MQ'yu Planlama
Son Güncelleme: 29 Ekim 2024
IBM MQ'yu konteynerlerde kullanmadan önce, IBM MQ'nun temel kavramlarına (IBM MQ Teknik Genel Bakış) ve Kubernetes/Red Hat OpenShift gibi konteyner platformlarının temel mimarisine (OpenShift Container Platform Mimari) aşina olmanız önerilir.

IBM MQ'yu Konteynerlerde Kullanım Seçenekleri
IBM MQ'yu konteyner ortamında kullanmak için üç temel yöntem vardır:
	1. IBM MQ Operatörü Kullanımı
		○ IBM MQ Operatörü, OpenShift API'sini genişleterek QueueManager (Kuyruk Yöneticisi) için özel bir kaynak ekler. Bu operatör, kuyruğun tanımlarını algılar ve gerekli Kubernetes kaynaklarına (StatefulSet, Service) dönüştürür.
		○ Native High Availability (HA) gibi karmaşık güncelleme işlemlerini otomatikleştirir.
	2. Önceden Hazırlanmış IBM MQ Advanced Görsellerini Kullanma
		○ IBM Container Registry'den temin edilebilen önceden hazırlanmış görseller kullanılabilir. Bu görseller, IBM MQ Advanced özelliklerini içerir.
	3. Kendi Görsellerinizi ve Dağıtım Kodunuzu Oluşturma
		○ Daha esnek bir çözüm isteyenler için kendi konteyner görüntülerinizi oluşturabilirsiniz. Ancak, bu yaklaşım güçlü bir konteyner yapılandırma bilgisi gerektirir ve oluşturulan konteynerin tüm sorumluluğunu almayı içerir.

IBM MQ Konteynerleri için Lisanslama Planlaması
Konteyner lisanslama, IBM License Service kullanılarak konteynerlerin kapasitelerine dayalı bir lisans modeli sunar. Tüm sunucuyu lisanslamak yerine, yalnızca kullanılan konteynerlerin kapasitesi lisanslanır.

Depolama Seçenekleri
	1. Ephemeral (Geçici) Depolama
		○ Konteyner yeniden başlatıldığında tüm veriler kaybolur.
		○ Demo ortamları veya bağımsız geliştirme için uygundur.
		○ Eksiler: Tüm mesajlar, işlem durumları ve yapılandırmalar sıfırlanır.
	2. Kalıcı Depolama
		○ Varsayılan olarak kullanılan bu yöntem, kuyruğun yeniden başlatıldığında mevcut mesajlarını ve yapılandırmalarını korumasını sağlar.
		○ Depolama sınıfına bağlı olarak özelleştirilebilir.

Yüksek Erişilebilirlik (HA) Seçenekleri
IBM MQ için üç ana yüksek erişilebilirlik seçeneği bulunur:
	1. Native HA Kuyruk Yöneticisi
		○ Aktif bir kopya ve iki yedekleme podu içerir. Blok depolama kullanır.
		○ Daha hızlı kurtarma süreleri sağlar.
	2. Çoklu Örnekli Kuyruk Yöneticisi
		○ Paylaşılan dosya sistemi üzerinde çalışan aktif ve yedek bir pod içerir.
		○ File locking (dosya kilitleme) ile geçiş sağlanır.
	3. Tek Dayanıklı Kuyruk Yöneticisi
		○ Bir podda çalışır ve Kubernetes tarafından izlenir. Pod başarısız olduğunda, Kubernetes yeni bir pod başlatır.

Konteynerlerde Güvenlik Planlaması
	1. Kimlik Doğrulama ve Yetkilendirme
		○ LDAP, Mutual TLS veya özel bir MQ eklentisi aracılığıyla kullanıcı kimlik doğrulaması yapılabilir.
	2. Ağ Trafiğinin Sınırlandırılması
		○ IBM MQ için ağ politikaları uygulanabilir.
	3. FIPS Uyumluluğu
		○ Çalışma sırasında, konteynerin FIPS uyumlu bir işletim sisteminde başlatılıp başlatılmadığını tespit eder ve buna göre FIPS desteği yapılandırır.

Performans ve Ölçeklenebilirlik Planlaması
	1. İşlem ve İş Parçacığı Sınırları
		○ Linux platformlarında iş parçacığı sınırları konteyner platformu tarafından sınırlandırılabilir. Örneğin, OpenShift'te varsayılan sınır konteyner başına 4096 işlemdir.
	2. Depolama Hacmi Sınırları
		○ Konteyner platformları, bir node'a bağlanabilecek maksimum hacim sayısını sınırlandırabilir (ör. AWS EC2 için maksimum 30 hacim).
	3. IBM MQ Ölçekleme Teknikleri
		○ Tek bir büyük kuyruk yöneticisi yerine, birden fazla kuyruk yöneticisi çalıştırmak avantajlı olabilir.
