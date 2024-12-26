1. Migration Nedir?
Migration, mevcut IBM MQ programlarının ve verilerinin yeni bir kod seviyesine uyarlanmasıdır. Bu, iki şekilde yapılabilir:
	• Zorunlu migration: Büyük sürüm değişiklikleri sonrası kuyruk yöneticisi (queue manager) veya istemci yapılandırmalarının güncellenmesi.
	• Opsiyonel migration: Bakım seviyesinde (maintenance level) yapılan küçük değişiklikler için, ek işlevsellik gerektiriyorsa.
Önemli Notlar:
	• Migration genellikle kuyruk yöneticisinin ilk başlatılmasında otomatik olarak gerçekleştirilir.
	• Bakım seviyeleri arasındaki geçişlerde kuyruk yöneticisi migration’ı gerekmeyebilir.

2. Migration Öncesi Hazırlık
A. Verilerinizi Yedekleyin
	• Kuyruk yöneticisi verilerini ve yapılandırmalarını yedekleyin.
	• dmpmqcfg komutuyla mevcut konfigürasyonu bir metin dosyasına kaydedin:dmpmqcfg -m QmgrName > config_backup.txt
B. Uyumlu Sürüm ve Yolları İnceleyin
	• Mevcut sürümden hedef sürüme olan migration yollarını kontrol edin:
		○ IBM MQ 8.0 → IBM MQ 9.4 gibi doğrudan geçişler desteklenmez. Ara sürüm (interim version) kullanılmalıdır.
	• Örnek Migration Yolları:
	Kaynak Sürüm	Hedef Sürüm	Ara Sürüm
	MQ 8.0	MQ 9.4	MQ 9.0
	MQ 9.1	MQ 9.4	Yok
C. Kuyruk Yöneticisi Cluster’ları
Cluster yapılandırmalarında önce tam depo yöneticileri (full repository managers), ardından kısmi depo yöneticileri (partial repository managers) güncellenmelidir.

3. Migration Süreci
A. Kuyruk Yöneticisi Migration
	1. Tüm Kuyruk Yöneticilerini ve Uygulamaları Kapatın:endmqm QmgrNameendmqlsrendmqweb
	2. Migration’a Başlayın:
		○ Kuyruk yöneticisini yeni seviyede başlatın:strmqm QmgrName
		○ Yeni işlevler kullanmak için COMMAND LEVEL değerini yükseltin:ALTER QMGR COMMANDLEVEL(940)
	3. Migration Tamamlandıktan Sonra Kontrol Edin:
		○ dspmqver komutuyla sürümü doğrulayın.
		○ Yeni objelerin varsayılan değerlere ayarlandığını kontrol edin.
B. İstemci Migration
	• İstemci tarafında ayar dosyalarını (mqclient.ini) güncelleyin.
	• Yeni istemci bağlantı yapılandırmalarını (CCDT) test edin ve dağıtın.

4. Migration Seçenekleri
A. Tek Aşamalı Migration (Single-Stage Migration)
	• Mevcut IBM MQ kurulumu tamamen yeni sürümle değiştirilir.
	• Kuyruk yöneticileri ve uygulamalar yeni kurulumla otomatik olarak ilişkilendirilir.
B. Yan Yana Migration (Side-by-Side Migration)
	• Aynı sunucuda eski ve yeni IBM MQ sürümleri yan yana kurulur.
	• Kuyruk yöneticileri ve uygulamalar aşamalı olarak yeni sürüme geçirilir.
C. Çok Aşamalı Migration (Multi-Stage Migration)
	• Yan yana kurulumla benzer, ancak her bir kuyruk yöneticisi veya uygulama birer birer yeni sürüme geçirilir.

5. Uyum, Uyumluluk ve Çalışabilirlik
	• Coexistence: Aynı sunucuda birden fazla IBM MQ sürümünün çalışabilmesi.
	• Compatibility: Daha eski sürümlerle çalışabilirlik.
	• Interoperability: Farklı sürümler arasında mesaj alışverişi ve bağlantı sağlama yeteneği.

6. Dikkat Edilmesi Gereken Özel Durumlar
	• AMQP Migration: IBM MQ 9.4.0’dan itibaren CMS keystore kullanımı desteklenmez. PKCS12’ye dönüştürülmesi gerekir.
	• Cluster Migration: Yeni özellikler eski cluster yöneticileri tarafından saklanamayabilir. Full repositories önce güncellenmelidir.




******************

IBM MQ'nun Windows Üzerinde Migrasyonu
IBM MQ’nun Windows ortamındaki migrasyon işlemleri, mevcut sürümden daha yeni bir sürüme geçişi ve/veya mevcut yapılandırmanın korunmasını içerir. Bu kılavuz, IBM MQ’yu Windows üzerinde nasıl migrate edeceğiniz konusunda ayrıntılı bir rehber sunar.

1. Migrasyona Başlamadan Önce
A. Ön Hazırlıklar
	1. Gereksinimleri İnceleyin:
		○ Hedef sürüm için sistem gereksinimlerini kontrol edin.System Requirements for IBM MQ
		○ Migration yollarını inceleyin:
			§ IBM MQ 7.5 veya önceki sürümlerden IBM MQ 9.4’e doğrudan geçiş mümkün değildir. İlk olarak ara bir sürüme (ör. MQ 8.0 veya MQ 9.0) geçiş yapmalısınız.
		○ Verilerinizi Yedekleyin:Kuyruk yöneticisi ve istemci verilerinin bir kopyasını alın. dmpmqcfg komutunu kullanarak mevcut konfigürasyonu yedekleyebilirsiniz:dmpmqcfg -m QueueManagerName > backup_config.mqsc
	2. Yükleme Yöntemi Seçimi:
		○ Single-Stage Migration: Mevcut IBM MQ sürümünü tamamen yenisiyle değiştirir.
		○ Side-by-Side Migration: Yeni sürüm, mevcut sürümle yan yana kurulur.
		○ Multi-Stage Migration: Uygulamalar ve kuyruk yöneticileri kademeli olarak yeni sürüme geçirilir.

2. Migrasyon Süreci
A. Kuyruk Yöneticisinin Migrasyonu
	1. Tüm İşlemleri Durdurun:Kuyruk yöneticisi ve ilişkili uygulamaları kapatın:endmqm QueueManagerNameendmqlsr
	2. IBM MQ Kurulumunu Güncelleyin:
		○ Yeni sürümü mevcut sürüm üzerine yükleyebilir veya yan yana kurulum yapabilirsiniz.
		○ Eğer yan yana kurulum yapıyorsanız, setmqinst komutuyla yeni kurulumun birincil kurulum (primary installation) olduğunu belirtin:setmqinst -i -n InstallationName
	3. Kuyruk Yöneticisini Başlatın ve Komut Seviyesini Güncelleyin:Kuyruk yöneticisini başlattıktan sonra komut seviyesini yükseltin:strmqm QueueManagerNameALTER QMGR COMMANDLEVEL(940)
	4. Log Dosyalarını Kontrol Edin:Eğer diskleriniz Advanced Format (4096 byte) diskler ise log dosyalarını migrate edin:migmqlog -m QueueManagerName

B. İstemci Migrasyonu
	1. Tüm İstemci Etkinliklerini Durdurun:endmqm -c
	2. Yeni Sürümü Kurun:
		○ Yeni istemci sürümünü yükleyin.
		○ Eğer yan yana kurulum yaptıysanız, istemci bağlantı tanım tablosunu (CCDT) kontrol edin ve gerekirse güncelleyin.

3. Özel Durumlar
A. AMQP Kullanımı
IBM MQ 9.4.0’dan itibaren AMQP kanalları CMS keystore dosyalarını desteklemez. Bu durumda:
	1. Keystore’u PKCS12 formatına dönüştürün.
	2. AMQP yapılandırmalarını uygun şekilde güncelleyin.
B. MSCS Yapılandırması
Microsoft Cluster Service (MSCS) yapılandırmalarında:
	• Her bir düğümü (node) sırayla migrate edin.
	• Pasif düğümleri güncelleme sırasında çevrimdışı (offline) tutun.

4. Migration Sonrası Kontroller
	1. Kuyruk yöneticisini ve istemcileri başlatarak işlevselliğini kontrol edin.
	2. Mevcut test senaryolarınızı kullanarak sistemin düzgün çalıştığını doğrulayın.
	3. Yeni özellikleri test edin ve kullanmaya başlayın.



*********************



AIX ve Linux'ta IBM MQ Migrasyonu
AIX ve Linux ortamlarında IBM MQ migrasyonu, genellikle daha fazla esneklik sunan bir süreçtir. Bu platformlarda, farklı sürümlerin yan yana kurulabilmesi ve çoklu kurulum desteği gibi özellikler, geçiş sürecini kolaylaştırır. İşte detaylı bir rehber:

1. Hazırlık Aşaması
Migrasyona başlamadan önce aşağıdaki adımları tamamlayın:
	1. Sistem Gereksinimlerini Doğrulayın:
		○ IBM MQ’nun yeni sürümü için donanım ve yazılım gereksinimlerini kontrol edin.
		○ Örneğin, IBM MQ 9.4 için minimum işletim sistemi sürümü gereksinimleri gibi.
	2. Mevcut Sürüm Kontrolü:
		○ dspmqver komutunu kullanarak mevcut IBM MQ sürümünüzü kontrol edin.dspmqver
	3. Yedekleme:
		○ Kuyruk yöneticisi verilerini yedekleyin:dmpmqcfg -m <QueueManagerName> -a > backup.mqsc
		○ Veritabanlarını ve log dosyalarını yedekleyin:tar -czvf mq_data_backup.tar.gz /var/mqm
	4. Yükleme Dosyalarını Hazırlayın:
		○ IBM MQ'nun yeni sürümüne ait yükleme dosyalarını indirin ve doğrulayın.

2. Migrasyon Yöntemleri
AIX ve Linux'ta aşağıdaki üç yöntem kullanılabilir:
	1. Tek Aşamalı Migrasyon (Single-stage):
		○ Eski sürüm tamamen kaldırılır ve yerine yeni sürüm yüklenir.
		○ Avantajı: Basit ve hızlıdır.
		○ Dezavantajı: Downtime gerektirir.
	2. Yan Yana Migrasyon (Side-by-side):
		○ Eski ve yeni sürüm aynı anda kurulur.
		○ Yeni sürüm test edildikten sonra eski sürüm kaldırılır.
		○ Avantajı: Kesintisiz çalışma sağlar.
		○ Dezavantajı: Daha fazla disk alanı kullanımı gerektirir.
	3. Çok Aşamalı Migrasyon (Multi-stage):
		○ Eski ve yeni sürüm birlikte çalışır.
		○ Kuyruk yöneticileri ve uygulamalar kademeli olarak yeni sürüme taşınır.
		○ Avantajı: En az riskle geçiş.
		○ Dezavantajı: Daha fazla yönetim gerektirir.

3. Adım Adım Migrasyon
A. Tek Aşamalı Migrasyon
	1. Eski Sürümü Durdurun:endmqm -i <QueueManagerName>
	2. Yedekleme Yapın:dmpmqcfg -m <QueueManagerName> -a > backup.mqsctar -czvf mq_backup.tar.gz /var/mqm
	3. Eski Sürümü Kaldırın:rpm -qa | grep MQSeries | xargs rpm -e
	4. Yeni Sürümü Yükleyin:rpm -ivh MQSeries*.rpm
	5. Yedeklemeleri Geri Yükleyin ve Kuyruk Yöneticisini Başlatın:tar -xzvf mq_backup.tar.gz -C /strmqm <QueueManagerName>
B. Yan Yana Migrasyon
	1. Yeni Sürümü Yan Yana Kurun:rpm -ivh MQSeries*.rpm --prefix=/opt/mqm_new
	2. Yeni Sürümde Test Kuyruk Yöneticisi Oluşturun ve Test Edin:crtmqm TESTQMstrmqm TESTQM
	3. Eski Kuyruk Yöneticilerini Yeni Sürüme Taşıyın:
		○ Eski sürümde dmpmqcfg ile yapılandırmaları alın ve yeni sürüme aktarın.
C. Çok Aşamalı Migrasyon
	1. Yeni Sürümü Yan Yana Kurun.
	2. Bir Kuyruk Yöneticisini Yeni Sürüme Taşıyın:bashCopy codeendmqm -i <QueueManagerName>dspmqver -m <QueueManagerName> -o all
	3. Uygulamaları Yeni Sürüme Bağlayın:
		○ setmqinst ve setmqenv komutlarını kullanarak ortam değişkenlerini ayarlayın:setmqenv -n InstallationName

4. Önemli Noktalar
	1. AMQP ve TLS Geçişi:
		○ CMS anahtar depolarını PKCS12 formatına dönüştürün.runmqckm -convert -type cms -new_format pkcs12 ...
	2. Performans Testi:
		○ Kuyruk yöneticilerini başlattıktan sonra amqsput ve amqsget komutlarıyla testler yapın.
	3. Geri Dönüş Planı:
		○ Gerekirse, yedekleme dosyalarınızı kullanarak eski sürüme dönün.




****************


1. Genel Hazırlık
Migrasyon öncesinde şu adımları tamamlayın:
	1. Tam Yedekleme Yapın:
		○ Tüm kuyruk yöneticisi yapılandırmalarını ve verilerini yedekleyin:dmpmqcfg -m <QueueManagerName> -a > cluster_backup.mqsctar -czvf cluster_data_backup.tar.gz /var/mqm
	2. Geçiş Planı Oluşturun:
		○ Kümeyi oluşturan tüm kuyruk yöneticilerinin rollerini belirleyin:
			§ Tam depo (Full Repository) Kuyruk Yöneticileri: Kümeye ait tüm yapılandırma bilgilerini depolar.
			§ Kısmi depo (Partial Repository) Kuyruk Yöneticileri: Sadece kendi ihtiyaç duyduğu bilgileri depolar.
	3. Yeni Sürüm Gereksinimlerini Kontrol Edin:
		○ Kümeye katılacak tüm kuyruk yöneticileri aynı sürümde olmalıdır.
		○ Tam depo kuyruk yöneticileri öncelikli olarak geçiş yapılmalıdır.

2. Migrasyon Yöntemleri
Kümedeki kuyruk yöneticileri için iki temel migrasyon yöntemi vardır:
	1. Toplu Migrasyon (All-at-Once):
		○ Tüm kuyruk yöneticileri aynı anda yükseltilir.
		○ Avantaj: Daha kısa sürede tamamlanır.
		○ Dezavantaj: Daha fazla kesinti riski taşır.
	2. Aşamalı Migrasyon (Staged):
		○ Kuyruk yöneticileri tek tek yükseltilir.
		○ Önce tam depo kuyruk yöneticileri yükseltilir, ardından kısmi depo kuyruk yöneticileri geçiş yapılır.
		○ Avantaj: Daha az kesinti riski.
		○ Dezavantaj: Daha uzun sürer.

3. Adım Adım Migrasyon
A. Tam Depo Kuyruk Yöneticilerini Migrasyon
	1. Tam Depo Kuyruk Yöneticisini Durdurun:endmqm -i <FullRepositoryQueueManager>
	2. Tam Depo Yöneticisinin Verilerini Yedekleyin:dmpmqcfg -m <FullRepositoryQueueManager> -a > full_repo_backup.mqsc
	3. Yeni Sürümü Yükleyin:
		○ Yeni IBM MQ sürümünü yan yana veya tek aşamalı olarak yükleyin.
	4. Tam Depo Kuyruk Yöneticisini Başlatın:strmqm <FullRepositoryQueueManager>
	5. Küme Bilgilerini Yenileyin:
		○ Küme bilgilerinin güncellenmesi için REFRESH CLUSTER komutunu çalıştırın:echo "REFRESH CLUSTER(<ClusterName>)" | runmqsc <FullRepositoryQueueManager>

B. Kısmi Depo Kuyruk Yöneticilerini Migrasyon
	1. Kısmi Depo Kuyruk Yöneticisini Migrasyon:
		○ Yukarıdaki adımları tekrar ederek kısmi depo kuyruk yöneticilerini sırayla yeni sürüme yükseltin.
	2. Kısmi Depoları Yenileyin:
		○ Her bir yükseltmeden sonra, kısmi depo kuyruk yöneticisini yenileyin:echo "REFRESH CLUSTER(<ClusterName>)" | runmqsc <PartialRepositoryQueueManager>

4. Dikkat Edilmesi Gerekenler
	1. Yeni Özelliklerin Kullanımı:
		○ Migrasyon tamamlanana kadar yeni özellikleri kullanmaktan kaçının. Yeni özellikler eski sürümde uyumsuzluklara yol açabilir.
	2. REFRESH CLUSTER Komutu:
		○ Büyük kümelerde bu komut performansı geçici olarak düşürebilir. Komut sonrası otomatik güncellemeler de sistem kaynaklarını etkileyebilir.
	3. Karışık Sürüm (Mixed Version) Yönetimi:
		○ Farklı sürümlerin aynı kümede geçici olarak çalışması mümkündür. Ancak, tam depo kuyruk yöneticileri her zaman en güncel sürümde olmalıdır.

5. Özel Durumlar
A. Yeni Bir Kuyruk Yöneticisinin Eklenmesi:
Yeni kuyruk yöneticisini kümeye eklemek için şu adımları izleyin:
	1. Kuyruk Yöneticisini Oluşturun:crtmqm <NewQueueManager>
	2. Kuyruk Yöneticisini Küme ile İlişkilendirin:DEFINE CHANNEL('TO.<ClusterName>') CHLTYPE(CLUSRCVR) CLUSTER('<ClusterName>') ...
B. Küme Yeniden Yapılandırması:
Kümedeki yapılandırma değişiklikleri sırasında dikkatli olun. Tüm kuyruk yöneticilerinin küme bilgilerini doğru şekilde aldığından emin olun.






*******************************

BM MQ Yüksek Erişilebilirlik (High Availability) Migrasyonu
Yüksek erişilebilirlik (HA) konfigurasyonları, IBM MQ kuyruk yöneticilerinin bir sunucudan diğerine kesintisiz geçiş yapmasını sağlar. Bu yapılandırmalar, uygulama kesintisini en aza indirmek için tasarlanmıştır. Migrasyon sürecinde bu yapılandırmaları düzgün bir şekilde taşımak, sistemin kararlılığını korumak açısından kritik öneme sahiptir.

1. Genel Hazırlık
Migrasyon öncesinde şu adımları tamamlayın:
	1. Tam Yedekleme Yapın:
		○ Kuyruk yöneticisi verilerini ve yapılandırmalarını yedekleyin:dmpmqcfg -m <QueueManagerName> -a > backup.mqsctar -czvf /mq/backup/<QueueManagerName>_data.tar.gz /var/mqm/qmgrs/<QueueManagerName>
	2. Yeni Sürüm Gereksinimlerini Kontrol Edin:
		○ Yeni sürümle uyumluluğu sağlamak için sistem gereksinimlerini gözden geçirin:
			§ İşletim sistemi sürümü
			§ Depolama gereksinimleri
			§ Ağ ayarları
	3. HA Grubu Konfigürasyonunu Doğrulayın:
		○ Tüm düğümlerin aynı ağda ve kümede bulunduğundan emin olun.
		○ Active-Standby veya Multi-Instance yapılandırmalarını kontrol edin.

2. Multi-Instance Kuyruk Yöneticisi Migrasyonu
Multi-instance kuyruk yöneticisi yapılandırması, birincil (active) ve yedek (standby) kuyruk yöneticilerinin aynı veritabanını paylaşmasına olanak tanır.
A. Migrasyon Süreci:
	1. Standby Kuyruk Yöneticisini Durdurun:endmqm -x <QueueManagerName>
	2. Birincil Kuyruk Yöneticisini Durdurun ve Yedek Alın:endmqm -i <QueueManagerName>tar -czvf /backup/<QueueManagerName>_data.tar.gz /var/mqm/qmgrs/<QueueManagerName>
	3. Yeni Sürümü Yükleyin:
		○ IBM MQ'yu yükseltilmiş sürüme kurun.
	4. Standby Düğümünü Yükseltin:
		○ Standby düğümde IBM MQ yazılımını güncelleyin.
		○ Yedek alınan verileri yeni düğüme geri yükleyin.
	5. Birincil Kuyruk Yöneticisini Başlatın:strmqm <QueueManagerName>
	6. Standby Kuyruk Yöneticisini Yeniden Başlatın:strmqm -x <QueueManagerName>
	7. HA Durumunu Doğrulayın:
		○ Kuyruk yöneticisi durumunu kontrol edin:dspmq -o status

3. High Availability (HA) Kümeleri Migrasyonu
HA kümeleri, aktif ve pasif sunucular arasında yük devri (failover) sağlar.
A. Migrasyon Süreci:
	1. Pasif Sunucuyu Kümeden Çıkarın:
		○ Pasif sunucuyu devre dışı bırakın:rdqmadm -s
	2. Pasif Sunucuyu Yükseltin:
		○ IBM MQ ve HA yazılımını (ör. Pacemaker, DRBD) yeni sürüme yükseltin.
	3. Aktif Sunucuda Yedek Alma ve Güncelleme:
		○ Aktif sunucuyu durdurun, yedek alın ve yeni sürüme yükseltin.
	4. Kümeyi Yeniden Etkinleştirin:
		○ Tüm düğümleri HA kümesine geri ekleyin:rdqmadm -r
	5. Failover İşlemini Test Edin:
		○ Aktif sunucuya yük devrini test edin.

4. Özel Durumlar
A. Yeni Düğümler Eklemek: Yeni bir düğümü HA kümesine eklemek için şu adımları izleyin:
	1. Düğümde IBM MQ ve HA yazılımını kurun.
	2. Kuyruk yöneticisinin yapılandırmasını aktarın.
	3. Düğümü HA grubuna ekleyin:rdqmadm -a <NodeName>
B. Disaster Recovery (DR) Migrasyonu:
	• DR konfigürasyonunda, önce ikincil (recovery) sunucuyu yükseltin.
	• Yedekleme ve geri yükleme işlemini tamamladıktan sonra, birincil sunucuyu yükseltin.

5. Dikkat Edilmesi Gerekenler
	1. Kesintisiz İşlemler İçin Öncelik:
		○ Önce standby düğümleri yükseltin.
		○ Kuyruk yöneticisi üzerinde çalışan işlemleri kesmeden aktif düğümde geçiş yapın.
	2. Yük Devri Testleri:
		○ Yük devri işlemlerini simüle ederek sistemin yeni yapılandırma ile uyumluluğunu doğrulayın.
	3. Sürüm Uyumluluğu:
		○ Tüm düğümleri aynı sürümde tutarak uyumluluk sorunlarını önleyin.


**************************

BM MQ Yüksek Erişilebilirlik (High Availability) Migrasyonu
Yüksek erişilebilirlik (HA) konfigurasyonları, IBM MQ kuyruk yöneticilerinin bir sunucudan diğerine kesintisiz geçiş yapmasını sağlar. Bu yapılandırmalar, uygulama kesintisini en aza indirmek için tasarlanmıştır. Migrasyon sürecinde bu yapılandırmaları düzgün bir şekilde taşımak, sistemin kararlılığını korumak açısından kritik öneme sahiptir.

1. Genel Hazırlık
Migrasyon öncesinde şu adımları tamamlayın:
	1. Tam Yedekleme Yapın:
		○ Kuyruk yöneticisi verilerini ve yapılandırmalarını yedekleyin:dmpmqcfg -m <QueueManagerName> -a > backup.mqsctar -czvf /mq/backup/<QueueManagerName>_data.tar.gz /var/mqm/qmgrs/<QueueManagerName>
	2. Yeni Sürüm Gereksinimlerini Kontrol Edin:
		○ Yeni sürümle uyumluluğu sağlamak için sistem gereksinimlerini gözden geçirin:
			§ İşletim sistemi sürümü
			§ Depolama gereksinimleri
			§ Ağ ayarları
	3. HA Grubu Konfigürasyonunu Doğrulayın:
		○ Tüm düğümlerin aynı ağda ve kümede bulunduğundan emin olun.
		○ Active-Standby veya Multi-Instance yapılandırmalarını kontrol edin.

2. Multi-Instance Kuyruk Yöneticisi Migrasyonu
Multi-instance kuyruk yöneticisi yapılandırması, birincil (active) ve yedek (standby) kuyruk yöneticilerinin aynı veritabanını paylaşmasına olanak tanır.
A. Migrasyon Süreci:
	1. Standby Kuyruk Yöneticisini Durdurun:endmqm -x <QueueManagerName>
	2. Birincil Kuyruk Yöneticisini Durdurun ve Yedek Alın:endmqm -i <QueueManagerName>tar -czvf /backup/<QueueManagerName>_data.tar.gz /var/mqm/qmgrs/<QueueManagerName>
	3. Yeni Sürümü Yükleyin:
		○ IBM MQ'yu yükseltilmiş sürüme kurun.
	4. Standby Düğümünü Yükseltin:
		○ Standby düğümde IBM MQ yazılımını güncelleyin.
		○ Yedek alınan verileri yeni düğüme geri yükleyin.
	5. Birincil Kuyruk Yöneticisini Başlatın:strmqm <QueueManagerName>
	6. Standby Kuyruk Yöneticisini Yeniden Başlatın:strmqm -x <QueueManagerName>
	7. HA Durumunu Doğrulayın:
		○ Kuyruk yöneticisi durumunu kontrol edin:dspmq -o status

3. High Availability (HA) Kümeleri Migrasyonu
HA kümeleri, aktif ve pasif sunucular arasında yük devri (failover) sağlar.
A. Migrasyon Süreci:
	1. Pasif Sunucuyu Kümeden Çıkarın:
		○ Pasif sunucuyu devre dışı bırakın:rdqmadm -s
	2. Pasif Sunucuyu Yükseltin:
		○ IBM MQ ve HA yazılımını (ör. Pacemaker, DRBD) yeni sürüme yükseltin.
	3. Aktif Sunucuda Yedek Alma ve Güncelleme:
		○ Aktif sunucuyu durdurun, yedek alın ve yeni sürüme yükseltin.
	4. Kümeyi Yeniden Etkinleştirin:
		○ Tüm düğümleri HA kümesine geri ekleyin:rdqmadm -r
	5. Failover İşlemini Test Edin:
		○ Aktif sunucuya yük devrini test edin.

4. Özel Durumlar
A. Yeni Düğümler Eklemek: Yeni bir düğümü HA kümesine eklemek için şu adımları izleyin:
	1. Düğümde IBM MQ ve HA yazılımını kurun.
	2. Kuyruk yöneticisinin yapılandırmasını aktarın.
	3. Düğümü HA grubuna ekleyin:rdqmadm -a <NodeName>
B. Disaster Recovery (DR) Migrasyonu:
	• DR konfigürasyonunda, önce ikincil (recovery) sunucuyu yükseltin.
	• Yedekleme ve geri yükleme işlemini tamamladıktan sonra, birincil sunucuyu yükseltin.

5. Dikkat Edilmesi Gerekenler
	1. Kesintisiz İşlemler İçin Öncelik:
		○ Önce standby düğümleri yükseltin.
		○ Kuyruk yöneticisi üzerinde çalışan işlemleri kesmeden aktif düğümde geçiş yapın.
	2. Yük Devri Testleri:
		○ Yük devri işlemlerini simüle ederek sistemin yeni yapılandırma ile uyumluluğunu     doğrulayın.
	3. Sürüm Uyumluluğu:
		○ Tüm düğümleri aynı sürümde tutarak uyumluluk sorunlarını önleyin.

************************


IBM MQ Replicated Data Queue Manager (RDQM) Migrasyonu
Replicated Data Queue Manager (RDQM), yüksek kullanılabilirlik ve veri replikasyonu sağlayan bir IBM MQ çözümüdür. Bu yapılandırma, aynı anda birden fazla düğümde veri tutar ve herhangi bir düğüm arızasında işlemleri hızlıca başka bir düğüme aktarır. Migrasyon süreci, tüm düğümlerin sıralı bir şekilde yükseltilmesini gerektirir.

1. RDQM Migrasyonuna Hazırlık
A. Genel Hazırlık Adımları
	1. Yedekleme Yapın:
		○ Kuyruk yöneticisi verilerini yedekleyin:dmpmqcfg -m <QueueManagerName> -a > /backup/<QueueManagerName>.mqsctar -czvf /backup/<QueueManagerName>_data.tar.gz /var/mqm/qmgrs/<QueueManagerName>
	2. Yeni Sürüm Gereksinimlerini Kontrol Edin:
		○ IBM MQ'nun yeni sürümünün RDQM için desteklediği işletim sistemi ve diğer gereksinimleri sağlayın:
			§ RHEL 8 veya 9 kullanmanız gerekebilir; RHEL 7 desteği yoktur.
	3. Yedekleme ve Test:
		○ Kuyruk yöneticisi verilerini ve konfigürasyonlarını yeni bir test ortamında çalıştırarak doğrulayın.

2. RDQM Migrasyon Süreci
RDQM migrasyonu sırasında, düğümleri birer birer yükseltmeniz gerekir. Her düğümde sırasıyla RDQM servisini durdurup yükseltmeyi tamamlayabilirsiniz.
A. Adım Adım RDQM Migrasyonu:
	1. İlk Düğümü (Standby) Durdurun ve Yükseltin:
		○ HA grubunu askıya alın:rdqmadm -s
		○ IBM MQ ve RDQM yazılımını kaldırın:rpm -qa | grep MQSeries | xargs dnf -y removerpm -qa | grep linbit | xargs dnf -y removerpm -qa | grep drbd | xargs dnf -y remove
		○ DRBD modülünün yüklü olmadığını doğrulayın:lsmod | grep drbd
		○ Yeni sürümü yükleyin:dnf install MQSeriesServer MQSeriesRDQM
		○ HA grubunu yeniden başlatın:rdqmadm -r
	2. İkinci Düğüm için Aynı İşlemleri Tekrarlayın:
		○ İlk düğümden sonra, ikinci düğümde aynı işlemleri uygulayın.
	3. Son Düğümü (Primary) Yükseltin:
		○ Son düğümde de yukarıdaki işlemleri uygulayın ve birincil düğümü aktif duruma getirin.
	4. Kuyruk Yöneticisini Kontrol Edin:
		○ Kuyruk yöneticisinin düzgün çalıştığını doğrulamak için şunları çalıştırın:dspmq -o status

3. Disaster Recovery (DR) RDQM Migrasyonu
A. DR Konfigürasyonu Yükseltme:
	1. Yedek (Secondary) Düğümü Yükseltin:
		○ Yedek düğümde RDQM ve IBM MQ yazılımlarını kaldırın ve yeni sürümü yükleyin.
	2. Failover Yapın:
		○ DR kuyruk yöneticisini yedek düğüme aktararak çalıştırın:rdqmadm -f
	3. Ana (Primary) Düğümü Yükseltin:
		○ Ana düğümde RDQM yazılımını kaldırıp yükseltmeyi tamamlayın.
	4. Orijinal Rolleri Geri Yükleyin:
		○ Kuyruk yöneticilerini tekrar ana düğüme aktarın:rdqmadm -m

4. Önemli Notlar ve İpuçları
	1. Aşamalı Yükseltme:
		○ Her düğümü birer birer yükseltin. Düğümler arasında farklı sürümleri çalıştırmaktan kaçının.
	2. Replikasyon Bağlantılarını Doğrulayın:
		○ Yeni sürümden sonra replikasyonun düzgün çalıştığından emin olun:rdqmadm -q
	3. Veri Kaybını Önleme:
		○ Tüm işlemleri durdurup mevcut verileri yedekleyin. Özellikle DR ortamlarında failover sırasında veri kaybını engelleyin.

5. Migrasyon Sonrası Testler
Migrasyon tamamlandıktan sonra şu testleri gerçekleştirin:
	• Bağlantı Testi: Kuyruk yöneticilerinin birbirine bağlanabildiğini doğrulayın.
	• Failover Testi: Yük devri işlemlerini test ederek sistemin yüksek erişilebilirlik vaatlerini sağladığını kontrol edin.
	• Performans Testleri: Yeni sürümün, beklenen performansı sağladığından emin olun.



