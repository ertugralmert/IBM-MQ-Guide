
IBM MQ Yükseltme Süreci
1. Yükseltmeye Başlamadan Önce:
	• Versiyon Uyumluluğu: IBM MQ’nun desteklediği Long Term Support (LTS) ve Continuous Delivery (CD) sürümleri arasındaki farkları anlayın.
	• Veri Yedekleme: Yükseltme öncesinde verilerinizi mutlaka yedekleyin:
		○ Kuyruk yöneticisi (Queue Manager) yapılandırmalarını yedekleyin.
		○ Sistem mesajlarını ve dosyalarını koruyun.

2. Yükseltme Türleri:
	• Fix Seviyesi Yükseltmeleri (F-level): Bu tip yükseltmeler yalnızca hata düzeltmeleri içerir ve kuyruk yöneticisi komut seviyesini değiştirmez.
	• VRM Yükseltmeleri (V-R-M seviyeleri): Daha büyük kod değişikliklerini temsil eder. Yükseltme sonrası kuyruk yöneticisi (Queue Manager) komut seviyesi güncellenir.

3. Yükseltme Prosedürleri:
Ortamınıza göre aşağıdaki adımları izleyin:
Linux için Genel Adımlar:
	1. Gerekli Paketlerin Hazırlanması:
		○ Yükleme dosyalarını IBM Passport Advantage ya da Fix Central'dan indirin.
		○ .tar.gz formatındaki dosyaları gunzip ve tar -xvf komutlarıyla açın.
		○ GNU tar kullanarak paketlerin doğru şekilde çıkarıldığından emin olun.
	2. Lisans Onayı:
		○ mqlicense.sh betiğini çalıştırarak lisansı kabul edin:./mqlicense.sh
	3. Uygulamaları ve Kuyruk Yöneticilerini Kapatma:
		○ MQ uygulamalarını, kuyruk yöneticilerini (endmqm) ve dinleyicileri (endmqlsr) kapatın.
		○ Kuyruk yöneticiniz bir kümenin parçasıysa, önce suspend durumuna geçirin.
	4. Yükseltmeyi Gerçekleştirme:
		○ RPM Yöntemi ile Yükseltme:rpm -Uvh MQSeries*
		○ DNF Yöntemi ile Yükseltme (Red Hat):dnf -y upgrade MQSeries*
		○ APT Yöntemi ile Yükseltme (Ubuntu):apt-get upgrade "ibmmq-*"
	5. Versiyon Doğrulama:
		○ dspmqver komutunu kullanarak yükseltmenin doğru yapıldığını kontrol edin:dspmqver
Windows için Yükseltme Adımları:
	• msiexec komutunu veya IBM MQ Launchpad’i kullanarak yükseltme yapabilirsiniz.
	• Fix seviyeleri yüklemek için yükleme medyasını kullanarak gerekli .msi dosyalarını yükleyin.

4. Yükseltme Sonrası Yapılacaklar:
	• Komut Seviyesi Güncellemesi (Command Level):
		○ Kuyruk yöneticisinin komut seviyesini güncelleyin:strmqm -e CMDLEVEL=<yeni_seviye>
	• Yeni Özelliklerin Test Edilmesi:
		○ Mevcut uygulamaların yeni versiyon ile uyumlu çalıştığından emin olun.
		○ Yeni eklenen özellikleri ve yapılandırmaları doğrulayın.

5. Sık Karşılaşılan Durumlar:
	• Kuyruk Yöneticisini Geri Almak Mümkün Mü?
		○ Eğer VRM seviyesi yükseltilmişse ve kuyruk yöneticisi başlatılmışsa, eski versiyona geri dönmek mümkün değildir.
	• IBM MQ Explorer Kaldırma:
		○ IBM MQ 9.3.0’dan itibaren IBM MQ Explorer yükleme paketinden çıkarılmıştır. Ayrı bir kurulum olarak indirilebilir.

Ek Kaynaklar:
	• IBM MQ Dokümantasyonu: IBM MQ Documentation
	• Fix Central: IBM Fix Central



*********************



IBM MQ Yükseltme Süreci (Windows)
1. Yükseltmeye Hazırlık:
Yükseltmeye başlamadan önce şu adımları uygulayın:
	• Tüm MQ Uygulamalarını Kapatın: Çalışan IBM MQ uygulamalarını durdurun.
	• Listener'ları Durdurun: endmqlsr komutunu kullanarak dinleyicileri kapatın.
	• Kuyruk Yöneticilerini (Queue Manager) Durdurun:
		○ Bir kuyruk yöneticisi kümenin parçasıysa, önce suspend duruma alın, ardından endmqm ile durdurun.
	• Verilerinizi Yedekleyin: Kuyruk yöneticisi verilerini ve yapılandırmalarını yedekleyin. Bu adım, yükseltme sırasında oluşabilecek sorunlara karşı koruma sağlar.

2. Yükseltme Seçenekleri:
A. IBM MQ Server Yükseltmesi
Yöntem 1: Launchpad ile Yükseltme
	1. Yükleme Dosyasını Bulun:
		○ Örneğin, C:\instmqs\Setup.exe dosyasını bulun.
	2. Setup.exe’yi Çalıştırın:
		○ Komut satırından çalıştırın veya Windows Explorer ile çift tıklayın.
		○ UAC etkinse, yönetici izinlerini onaylayın.
	3. Kurulum Penceresi Açıldığında:
		○ Yeni bir instance kurulumunu veya mevcut bir kurulumu yükseltme seçeneğini seçin.
		○ "Upgrade an existing named installation" seçeneğini işaretleyin.
	4. Ekrandaki Yönergeleri İzleyin: Kurulum işlemini tamamlayın.
Yöntem 2: msiexec ile Yükseltme
	1. Yükleme Dosyasını Bulun:
		○ Örneğin, C:\instmqs\MSI\IBM MQ.msi dosyasını bulun.
	2. Komut Satırından Çalıştırın:
		○ Varsayılan kurulumlar için:msiexec /i "C:\instmqs\MSI\IBM MQ.msi" /q AGREETOLICENSE=YES INSTALLATIONNAME="Installation1"
		○ Birden fazla kurulum için uygun instance ID'sini seçerek:msiexec /i "C:\instmqs\MSI\IBM MQ.msi" /q AGREETOLICENSE=YES INSTALLATIONNAME="Installation2" NEWINSTANCE=1 TRANSFORMS=":InstanceId2.mst;1033.mst"

B. IBM MQ Client Yükseltmesi
Yöntem 1: GUI Yükleyici ile Yükseltme
	1. Yükleme Dosyasını Bulun:
		○ Örneğin, C:\instmqs\Setup.exe dosyasını çalıştırın.
	2. Setup.exe’yi Çalıştırın:
		○ Yeni bir instance kurmak veya mevcut bir kurulumda güncelleme yapmak için seçenekler sunulur.
		○ "Upgrade an existing named installation" seçeneğini seçin.
	3. Ekrandaki Yönergeleri İzleyerek Kurulumu Tamamlayın.
Yöntem 2: msiexec ile Yükseltme
	1. Yükleme Dosyasını Bulun:
		○ Örneğin, C:\instmqs\MSI\IBM MQ.msi dosyasını bulun.
	2. Komut Satırından Çalıştırın:
		○ Varsayılan kurulumlar için:msiexec /i "C:\instmqs\Windows\MSI\IBM MQ.msi" /l*v install_log_path /q TRANSFORMS="1033.mst" REINSTALL=ALL REINSTALLMODE=vomus
		○ Birden fazla kurulum için uygun instance ID'sini seçerek:msiexec /i "C:\instmqs\MSI\IBM MQ.msi" /q AGREETOLICENSE=YES INSTALLATIONNAME="Installation2" NEWINSTANCE=1 TRANSFORMS=":InstanceId2.mst;1033.mst"

3. Yükseltme Sonrası Kontrol:
	• Versiyon Doğrulama: dspmqver komutuyla yükseltmenin başarılı olduğunu kontrol edin.dspmqver
	• Kuyruk Yöneticilerini Test Edin: Yeni özelliklerin uyumluluğunu kontrol edin.

4. Ek Notlar:
	• Uygun Yükleme İmajını Seçin: Yükleme dosyalarını IBM Fix Central veya Passport Advantage üzerinden indirin.
	• Lisans Kabulü: Kurulum sırasında lisans sözleşmesini onaylayın.


************************


IBM MQ Upgrade Yol Haritası
1. Ön Hazırlık Aşaması
1.1. Mevcut Ortamın Analizi ve Planlama
	• Mevcut MQ Sürümünüzü ve Yapınızı Analiz Edin:
		○ dspmqver komutunu çalıştırarak mevcut IBM MQ sürümünü doğrulayın.
		○ Queue manager'larınızın yapılandırmasını (ör. cluster, HA, RDQM) ve ilişkili queue'ları inceleyin.
	• Desteklenen Migrasyon Yollarını Doğrulayın:
		○ IBM MQ sürümünüzden hedef sürüme direkt geçiş mümkün değilse, bir ara sürüme yükseltmeniz gerekebilir.
		○ Örnek: IBM WebSphere MQ 7.5 → IBM MQ 8.0 → IBM MQ 9.4.
	• Sistem Gereksinimlerini Kontrol Edin:
		○ Donanım ve işletim sistemi gereksinimlerini karşılayıp karşılamadığını kontrol edin.
		○ Desteklenen platformları ve sürüm uyumluluklarını inceleyin.
	• Hedef Sürümün Özelliklerini ve Değişikliklerini İnceleyin:
		○ Yeni özelliklerin mevcut yapınızı nasıl etkileyebileceğini anlamak için IBM MQ sürüm notlarını okuyun.

1.2. Yükseltme Yöntemini Seçin
	• Single-Stage Migration:
		○ Mevcut MQ kurulumunu direkt olarak yeni sürümle değiştirin.
		○ Avantajları: Basit, tek bir işlemle tamamlanır.
		○ Dezavantajları: Tüm sistem bir anda yükseltilir; daha az esneklik sağlar.
	• Side-by-Side Migration:
		○ Yeni sürümü mevcut sürümle aynı sunucuda yan yana kurun.
		○ Avantajları: Yeni sürümü test etmek için fırsat sunar.
		○ Dezavantajları: Ek disk alanı gerektirir.
	• Multi-Stage Migration:
		○ Farklı queue manager'ları kademeli olarak yeni sürüme taşıyın.
		○ Avantajları: Daha az kesinti, esnek planlama.
		○ Dezavantajları: Daha fazla zaman ve kaynak gerektirir.

1.3. Yedekleme ve Geri Dönüş Planları
	• Queue Manager Yedekleme:
		○ Queue manager verilerini ve yapılandırmalarını yedekleyin (dmpmqcfg, saveqmgr komutlarını kullanabilirsiniz).
		○ Log dosyalarını, mesajları ve sistem dosyalarını kopyalayın.
	• Geri Dönüş Planı:
		○ Yükseltme sırasında bir sorun yaşanması durumunda eski sürüme dönmek için bir plan hazırlayın.
		○ Yedeklerden geri yükleme işlemini test edin.

2. Yükseltme Aşaması
2.1. Ön Kontroller
	• Yükseltilecek Queue Manager'ları Durdurun:
		○ endmqm -w veya endmqm -i komutlarıyla tüm queue manager'ları düzgün bir şekilde kapatın.
	• Listener ve Diğer Servisleri Durdurun:
		○ endmqlsr komutunu kullanarak listener'ları durdurun.
	• Aktif Bağlantıları ve Uygulamaları Kesin:
		○ IBM MQ'ya bağlı olan tüm uygulamaları geçici olarak durdurun.

2.2. Yazılımın Güncellenmesi
	• Yeni IBM MQ Sürümünü Yükleyin:
		○ Yükseltme için gerekli kurulum paketlerini indirin ve yükleme yönergelerini izleyin.
		○ Örnek:rpm -Uvh MQSeriesRuntime-*.rpm MQSeriesServer-*.rpm
		○ AIX/Linux'ta installp veya rpm, Windows'ta GUI yükleyici veya msiexec komutları kullanılabilir.
	• Gerekli Ek Yazılımları Yükleyin:
		○ TLS için sertifikaları ve CipherSpec'leri güncelleyin.
		○ Ek araçlar (MQ Explorer gibi) gerekiyorsa kurulum yapın.

2.3. Queue Manager Verilerinin Migrasyonu
	• Queue Manager'ları Başlatın ve Migrasyonu Tamamlayın:
		○ strmqm komutunu kullanarak queue manager'ları başlatın.
		○ Veritabanı ve log dosyaları otomatik olarak yeni sürüme yükseltilir.
		○ Örnek hata kontrolü:dspmq
	• Cluster ve HA Yapılandırmalarını Kontrol Edin:
		○ Cluster'larda full repository queue manager'larını önce yükseltin.
		○ Multi-instance veya HA yapılarında pasif node'ları önce güncelleyin.

2.4. Test ve Doğrulama
	• Test Senaryolarını Çalıştırın:
		○ Uygulama bağlantıları, mesaj gönderimi ve alımı gibi işlemleri test edin.
	• Log ve Performans Kontrolleri Yapın:
		○ amqerr01.log gibi log dosyalarını kontrol edin.
		○ Performansın beklentilere uygun olup olmadığını değerlendirin.

3. Son Aşama: İzleme ve İyileştirme
3.1. İzleme ve Raporlama
	• Monitoring Araçlarını Güncelleyin:
		○ MQ Explorer, Prometheus veya benzeri araçlarla yeni sürümü izlemeye başlayın.
	• Performans Karşılaştırmaları Yapın:
		○ Yükseltme öncesi ve sonrası performansı karşılaştırarak iyileştirme fırsatlarını değerlendirin.
3.2. Eğitim ve Dokümantasyon
	• Ekibinizi Yeni Özellikler Konusunda Eğitin:
		○ IBM MQ'nun yeni sürümündeki özellikler ve değişiklikler hakkında bilgi sağlayın.
	• Dokümantasyonu Güncelleyin:
		○ Sistem dokümanlarında yeni sürüme dair bilgileri ekleyin.

Detaylı Kontrol Listesi
Aşama	Yapılacak İşlem	Durum
Mevcut Durum Analizi	Queue manager konfigürasyonlarının yedeklenmesi	✅
Planlama	Uygulama bağlantılarının kesilmesi	✅
Yükseltme	Yeni sürüm yazılımının yüklenmesi	✅
Test ve Doğrulama	Mesaj iletişimlerinin kontrol edilmesi	✅
İzleme ve Optimizasyon	Monitoring araçlarının yapılandırılması	✅



**************************


