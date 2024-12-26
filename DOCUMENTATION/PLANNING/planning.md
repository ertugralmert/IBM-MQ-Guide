IBM MQ Mimari Planlaması
Son Güncelleme: 2024-07-11
IBM® MQ ortamınızı planlarken, IBM MQ'nun tekli ve çoklu kuyruk yöneticisi (queue manager) mimarileri için sağladığı desteği ve nokta-nokta (point-to-point) ile yayın/abone (publish/subscribe) mesajlaşma stillerini göz önünde bulundurmalısınız. Ayrıca, kaynak gereksinimlerinizi, günlükleme (logging) ve yedekleme (backup) tesislerinizi planlamalısınız.
Bu Görev Hakkında
IBM MQ mimarinizi planlamadan önce, temel IBM MQ kavramları hakkında bilgi sahibi olmalısınız. IBM MQ Teknik Genel Bakış başlığına göz atabilirsiniz.
IBM MQ mimarileri, tek bir kuyruk yöneticisi kullanarak basit mimarilerden, birbirine bağlı çoklu kuyruk yöneticisi ağlarına kadar genişler. Birden fazla kuyruk yöneticisi, dağılmış kuyruklama (distributed queuing) teknikleri kullanılarak birbirine bağlanır. Tekli kuyruk yöneticisi ve çoklu kuyruk yöneticisi mimarileriyle ilgili daha fazla bilgi için aşağıdaki başlıklara bakabilirsiniz:
	• Tekli kuyruk yöneticisi tabanlı mimariler
	• Çoklu kuyruk yöneticisi tabanlı mimariler
	• Dağılmış kuyruklar ve kümeler (clusters) için planlama
	• Dağılmış yayın/abone (publish/subscribe) ağı planlaması
[z/OS] IBM MQ için z/OS Mimari Planlaması
IBM MQ için z/OS®'ta, yük dengeleme (workload balancing) sağlamak ve IBM MQ uygulamalarınızın ölçeklenebilir ve yüksek kullanılabilir olmasını sağlamak için paylaşılan kuyruklar ve kuyruk paylaşım grupları kullanılabilir. Paylaşılan kuyruklar ve kuyruk paylaşım grupları hakkında bilgi için Paylaşılan Kuyruklar ve Kuyruk Paylaşım Grupları başlığına bakabilirsiniz.
IBM MQ Sürümleri
IBM MQ, iki farklı sürüm modeli sunar:
	1. Long Term Support (LTS) sürümü, uzun vadeli dağıtım ve maksimum kararlılık gerektiren sistemler için en uygun olandır.
	2. Continuous Delivery (CD) sürümü, IBM MQ'nun en son işlevsel iyileştirmelerinden hızla yararlanması gereken sistemler için uygundur.
Her iki sürüm de aynı şekilde yüklenir, ancak destek ve göç (migration) ile ilgili anlamanız gereken bazı farklar vardır. Daha fazla bilgi için IBM MQ sürüm türleri ve sürümleme başlığına bakabilirsiniz.
IBM MQ için Planlama Konuları
	• IBM MQ ve IBM MQ Appliance yerel olarak GDPR uyumluluğu açısından gereksinimleri göz önünde bulundurmak.
	• Tekli Kuyruk Yöneticisi Tabancalı Mimariler ve Çoklu Kuyruk Yöneticisi Tabancalı Mimariler ile ilgili ayrıntılı bilgiler.
Tekli Kuyruk Yöneticisi Tabanlı Mimariler
En basit IBM MQ mimarileri, tek bir kuyruk yöneticisinin yapılandırılması ve kullanılmasını içerir. Bu tür mimariler, küçük ve yerel sistemlerde tercih edilebilir.
Çoklu Kuyruk Yöneticisi Tabanlı Mimariler
Dağıtılmış mesaj kuyruklama (distributed message queuing) teknikleri kullanarak, IBM MQ mimarisi oluşturmak için birden fazla kuyruk yöneticisinin yapılandırılması ve kullanılması mümkündür. Bu tür mimariler daha büyük, daha karmaşık sistemler için uygundur.
[UNIX, Linux, Windows, IBM i] Çoklu Platformlarda Depolama ve Performans Gereksinimleri
IBM MQ sisteminiz için gerçekçi ve ulaşılabilir depolama ve performans hedefleri belirlemelisiniz. Depolama ve performansı etkileyen faktörler hakkında bilgi edinmek için bağlantıları kullanabilirsiniz.
[z/OS] IBM MQ için z/OS Ortamı Planlaması
IBM MQ ortamınızı planlarken, veri setleri, sayfa setleri, Db2®, Coupling Facilities ve günlükleme (logging) ile yedekleme (backup) tesislerinin gereksinimlerini göz önünde bulundurmalısınız. IBM MQ'nun çalışacağı ortamı planlamak için bu başlıkları inceleyebilirsiniz.

IBM MQ'nun mimarisi planlanırken her bir gereksinim ve gereksinimlerinizi en iyi şekilde karşılayacak yapılandırmalar dikkate alınmalıdır. Bu süreci doğru yönetmek, sistemin uzun ömürlü ve verimli çalışmasını sağlar.
