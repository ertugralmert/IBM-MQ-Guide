IBM® MQ için yüksek erişilebilirlik (HA) çözümleri, platforma ve sunulan özelliklere göre farklılık gösterir. Bu çözümler, çeşitli yapılandırmalarla kullanılabilir ve aşağıdaki tablolarda her çözümün özellikleri ve avantajları/olası dezavantajları karşılaştırılmaktadır.

Yüksek Erişilebilirlik (HA) Çözümleri Karşılaştırması

Özellikler	Native HA	RDQM	IBM MQ Appliance	Multi-instance Queue Managers
Donanım Gereksinimi	Minimum iki OpenShift Compute Node (maksimum erişilebilirlik için üç node gerekli)	Üç node gerekli	M2003A/B fiziksel cihaz - 32 işlemci, 256 GB RAM	İki node gerekli
İşletim Sistemi	Linux	Linux	IBM MQ Appliance firmware	Windows veya Unix varyasyonları
Ek Yazılım Gereksinimi	Red Hat OpenShift Container Platform (OCP)	DRBD, Pacemaker	Yok	Yok
VM veya Konteyner	Konteyner tabanlı	VM veya bare metal	Queue manager'lar cihazda çalışır	VM, bare metal veya konteyner
Depolama	Kalıcı Depolama Bloğu (ReadWriteOnce)	Her node için volume group (drbdpool)	Cihazlar 4x 3.2 TB SSD RAID10 disk içerir	NFS v4 paylaşımlı dosya sistemi gerekli, dosya sistemi kilitleri kullanılır
HA Yeteneği	Evet	Evet	Evet	Evet
DR Yeteneği	Henüz değil	Evet	Evet	Hayır (Depolama replikasyonu ile DR sağlanabilir)
Diğer Ekiplerin Bağımlılığı	OpenShift / Kubernetes kümesi yöneticisi grubu	OS ekibi, ağ ekibi, depolama ekibi	Ağ ekibi (IBM MQ Appliance, MQ ekibine tamamen kontrol sağlar)	OS ekibi, ağ ekibi, depolama ekibi
Aktif / Aktif Yeteneği	Hayır	Evet	Evet	Hayır
Hem HA Hem DR Replikasyonu	Hayır	Evet	Evet	Hayır
Performans	N/A	HA yapılandırmasında hafif performans etkisi	En iyi performans (örneğin, M2002 modelinde 500.000 mesaj/sn)	N/A
Güvenlik Notları	Root erişimi gerekli bazı RDQM komutları için	-	1. Genel amaçlı OS yok	-
			2. Dijital imzalı ve şifrelenmiş firmware
			3. Uygulama kodu cihazda çalıştırılamaz
			4. Cihaz kullanıcıları ve mesajlaşma kullanıcıları ayrıdır
Lisans Denetimi	IBM License Service	ILMT	N/A	ILMT
Lisanslama	Tüm konteynerler ve pod'lar lisanslanmalı	Bir node tam IBM MQ lisansı, iki node IBM MQ High Availability Replica	Tüm 32 işlemci A modelde kullanılabilir, B modelde 8 işlemci	Bir node tam IBM MQ lisansı, bir node IBM MQ High Availability Replica
Önerilen Maksimum Latency HA için	10 ms	5 ms	10 ms	N/A
Önerilen Maksimum Latency DR için	N/A	50 ms	100 ms	N/A

Yüksek Erişilebilirlik (HA) Çözümlerinin Karşılaştırmalı Avantajları
Özellikler	Native HA	RDQM	IBM MQ Appliance	Multi-instance Queue Managers
Avantajlar	1. Üçüncü parti kütüphanelere veya harici yazılımlara bağımlılık yok	1. Split-brain durumu olasılığı düşük	1. En güvenli çözüm, çünkü uygulama kodu cihazda çalıştırılamaz	1. Split-brain durumunu yaşama olasılığı yok
	2. Split-brain durumunun yaşanması olası değil	2. Hem HA hem de DR için kullanılabilir	2. MQ ekibi, cihazda tamamen kontrol sahibi, OS yönetici ekibine bağımlı değil	2. En basit bakım ve tek bir tüketilebilir paketle yapılandırılabilir
	3. Kernel değişiklikleri veya paylaşımlı dosya sistemi gerektirmez	3. Düşük maliyetle çalışabilen yüksek erişilebilirlik replikalarında IBM MQ iş yükü çalıştırılabilir	3. Lisans sorunları yok, mevcut kapasiteyi kullanarak çok sayıda queue manager çalıştırılabilir	3. TLS sertifikası kontrolü sağlanabilir
	4. Bağlantıların yeniden kurulması için grace period yapılandırılabilir		4. Basit bakım
Olası Dezavantajlar	1. Her yazılım yığınında ayrı bakım gerektirir	1. DRBD kernel modülü, OS yamanmasını zorlaştırır	1. Split-brain durumu olasılığı var	1. En uzun kuyruk yöneticisi yeniden başlatma süresi
	2. Asenkron replikasyon şu an mevcut değil	2. Genel bakım daha karmaşıktır	2. Yüksek performanslı ağ depolaması gerekir	2. Yüksek performans ağ depolaması gerekir
	3. Yalnızca üç pod kullanılabilir	3. Root erişimi gereklidir	3. Locally bağlı uygulamalar, başarısız olan queue manager örneğiyle bağlantıyı kesmeli	3. Yalnızca VM, bare metal veya konteyner kullanılabilir
	4. Kubernetes/OpenShift bilgisi gereklidir	4. Yalnızca RHEL'de çalışır	4. Disk veya CPU güçsüzse replikalar hızlı log yazmalarını onaylamayabilir

Linkler ve Ayrıntılı Bilgiler
Özellikler	Native HA	RDQM	IBM MQ Appliance	Multi-instance Queue Managers
Dokümantasyon	Native HA	RDQM high availability	High availability on the appliance	Multi-instance queue managers

Özet:
	• Native HA, daha fazla yapılandırma gerektirirken, üçüncü parti yazılım ve kernel değişikliklerine bağımlılık olmadan çalışabilir. Yüksek güvenlik ve düşük maliyet avantajları sunar, ancak bazı bakım zorlukları vardır.
	• RDQM, yüksek erişilebilirlik ve felaket kurtarma (DR) desteği sağlar, ancak daha karmaşık bakım gereksinimlerine sahiptir ve root erişimi gerektirir.
	• IBM MQ Appliance, daha basit yönetim ve güvenlik avantajları sağlar, ancak performans ve yerel bağlamalarla ilgili bazı sınırlamalar olabilir. Ayrıca, uygulama kodu çalıştırılamaz.
	• Multi-instance Queue Managers, tüm işlem yükünü yöneten ve yüksek erişilebilirlik sağlayan bir yapı sunar, ancak en uzun yeniden başlatma sürelerine ve yüksek ağ depolama gereksinimlerine sahiptir.
