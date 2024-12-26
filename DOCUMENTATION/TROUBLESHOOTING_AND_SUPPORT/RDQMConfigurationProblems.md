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
		○ Hata veren düğümdeki bağlantıların yeniden başlatılması gerekebilir:drbdadm disconnect <kaynak_adı>drbdadm connect <kaynak_adı>
c. Senkronizasyonun Takılması:
	• Belirti: drbdadm status çıktısında "replication: SyncSource" ve "done" değeri artmıyor.
	• Çözüm:
		○ Problemli düğümde bağlantılar yeniden başlatılır:drbdadm disconnect <kaynak_adı>drbdadm connect <kaynak_adı>

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
		○ rdqmclean komutuyla hatalı eylemler temizlenir:rdqmclean -m <kuyruk_yöneticisi_adı>

2.3. Yükseltme Sonrası Problemler
a. DRBD Çekirdek Modülü Uyuşmazlığı:
	• Belirti: Kuyruk yöneticisi başlatılamaz veya DRBD modülü "Partially loaded" durumundadır.
	• Çözüm:
		○ Çekirdek sürümüne uygun DRBD modülü yüklenir:yum install drbd-<uyumlu_sürüm>
b. Hafif Uyumsuzluk:
	• Belirti: DRBD modülü çalışıyor ancak uyumsuz bir sürüm kullanılıyor.
	• Çözüm:
		○ Uygun DRBD sürümü yüklenerek sistem tam uyumlu hale getirilir.

3. RDQM Durum Kontrol Komutları
	1. Durum Görüntüleme:rdqmstatus -m <kuyruk_yöneticisi_adı>
	2. Hatalı Kaynak Eylemleri Görüntüleme:rdqmstatus -m <kuyruk_yöneticisi_adı> -a
	3. DRBD Durumu Görüntüleme:drbdadm status
	4. Bağlantı Yenileme:drbdadm disconnect <kaynak_adı>drbdadm connect <kaynak_adı>

Sonuç
RDQM yapılandırma sorunlarının çözümü için doğru teşhis ve sistematik bir yaklaşım gereklidir. Bu rehberde belirtilen adımları takip ederek IBM MQ RDQM yapılandırmalarınızda yüksek erişilebilirlik ve felaket kurtarma işlevlerini sorunsuz bir şekilde sürdürebilirsiniz.
