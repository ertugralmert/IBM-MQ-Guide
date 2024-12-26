IBM MQ Senaryoları
IBM MQ, çok çeşitli kullanım senaryoları için yapılandırılabilir ve çeşitli görevleri gerçekleştirmek için yönlendirilmiş adımlar sunar. Her senaryo, büyük bir ürün özelliğini yapılandırmak için gerekli olan önemli adımları gösterir ve konuyla ilgili daha iyi bir anlayış kazanmanıza yardımcı olacak diğer içeriklere bağlantılar sunar. Aşağıda, IBM MQ ile ilgili bazı yaygın senaryoları bulabilirsiniz.
1. IBM MQ ile Başlarken (Windows)
Bu senaryo, IBM MQ'yu Windows platformunda kurmayı ve kullanmayı öğrenmek isteyenler için temel bir başlangıç rehberidir. IBM MQ'yu daha önce kullanmamışsanız, bu senaryo hızlıca başlamak için kullanışlıdır.
2. Point-to-Point Senaryosu
Bu senaryo, iki IBM MQ kuyruk yöneticisini bir point-to-point (nokta-noktaya) topolojisinde birbirine bağlamayı ve dağılmış kuyruklama işlemlerini nasıl etkinleştireceğinizi gösterir.
3. Streaming Kuyrukları
IBM MQ'nun streaming queues (akış kuyrukları) özelliği, her mesajın neredeyse aynı bir kopyasını ikinci bir kuyruğa koymanızı sağlar. Bu senaryo, bu özelliği nasıl yapılandıracağınızı anlatır.
4. Publish/Subscribe Senaryoları
Bu iki set senaryo, publish/subscribe (yayınla/abone ol) kümeleri ve hiyerarşileri kullanarak mesaj iletimini nasıl yapılandırabileceğinizi ve kullanabileceğinizi gösterir.
5. Transactional Destek Senaryoları
Bu senaryo, transactional support (işlem destek) kullanarak uygulamalarınızın veritabanları ile güvenilir bir şekilde nasıl çalışacağını gösterir. Bu, veritabanı işlemleri için kritik bir özelliktir.
6. Güvenlik Senaryoları
Bu set, IBM MQ yapılandırmalarınıza güvenlik uygulamayı gösteren bir dizi senaryo içerir. IBM MQ'nun çeşitli güvenlik özelliklerini nasıl uygulayabileceğiniz hakkında bilgiler sunar.
7. Windows'da Yükseltme Senaryosu
Bu senaryo, mevcut bir IBM MQ 9.3 kurulumundan IBM MQ 9.4'e geçiş yapmak için gerekli olan temel görevleri adım adım gösterir. Bu senaryoda her iki sürüm de aynı Windows ortamında yüklü olacaktır.
8. IBM MQ'nun Yeni Bir Sürümünü Kurma (Windows)
Bu senaryo, IBM MQ'nun uzun vadeli destek (LTS) sürümünü, önceki sürümüyle birlikte ("yan yana") kurmanın tüm adımlarını gösterir. Ayrıca bu sürüme bir Fix Pack yüklemeyi de içerir.
9. Managed File Transfer Senaryosu
Bu senaryo, Managed File Transfer (Yönetilen Dosya Transferi) özelliğinin nasıl yapılandırılacağını ve test mesajı gönderme sürecini gösteren yaygın topolojiler sunar. Bu, dosya aktarım işlemlerini yönetmek için kullanılan bir özellik olup, çok sayıda IBM MQ bileşeni ile entegrasyon gerektirir.
10. IBM MQ Internet Pass-Thru (MQIPT) ile Başlarken
Bu senaryo, IBM MQ Internet Pass-Thru (MQIPT) ürününü kurmak ve yapılandırmak için bazı temel görevleri gösterir. Bu senaryolar, ürünün doğru şekilde kurulduğunu doğrulamak için de kullanılabilir.
11. Kafka Connect Senaryoları
IBM MQ ve Apache Kafka, mesajlaşma alanında farklı alanlara odaklanır. MQ, bağlantı konusunda uzmanlaşırken, Kafka veri konusunda uzmanlaşır. Çoğu çözüm, bu iki sistem arasında veri akışını sağlamak için Kafka Connect kullanır. Bu senaryo, Kafka ile IBM MQ arasında veri akışını nasıl yönetebileceğinizi gösterir.

*******************
IBM MQ ile Başlarken 
IBM® MQ'yu Windows platformunda kullanmaya başlamak için gereken temel adımları anlatan bu senaryo, IBM MQ'yu daha önce kullanmamış ve hızlıca başlamak isteyenler için idealdir. Senaryo, IBM MQ'nun kurulumunu, yapılandırılmasını ve doğrulamasını basit bir şekilde yapmanıza yardımcı olacak adımları içerir.
Planlama Çözümü
IBM MQ'nun Windows'a kurulumu için aşağıdaki yöntemlerden birini seçebilirsiniz:
	• Grafiksel Kullanıcı Arayüzü (GUI) kullanarak kurulumu gerçekleştirebilirsiniz. Bu yöntem, size kurulum ve yapılandırma sürecinde yardımcı olacak sihirbazlar sunar.
	• Komut Satırı kullanarak sessiz bir kurulum yapabilirsiniz.
Çözümün Uygulanması
IBM MQ'yu Windows platformunda kurmak için aşağıdaki adımları izlersiniz:
	1. Launchpad üzerinden IBM MQ kurulumu başlatılır.
	2. IBM MQ yükleme sihirbazı ile yazılım yüklenir.
	3. Prepare IBM MQ Wizard ile gerekli hazırlıklar yapılır.
	4. IBM MQ Servisi ve IBM MQ Explorer başlatılır.
	5. IBM MQ Explorer kullanarak kuyruğa mesaj gönderilir ve alınır.
Kurulumdan Sonra Ne Yapılmalı?
Kurulum tamamlandıktan sonra IBM MQ Explorer üzerinden oluşturduğunuz kuyruğa mesaj gönderme ve alma işlemleri yapılabilir. Bu işlem, IBM MQ’nun doğru şekilde kurulduğunu ve çalıştığını doğrulamak için önemlidir.

Temel Kavramlar ve Önemli Terimler
	• Queue Managers (Kuyruk Yöneticileri): Kuyruk yöneticisi, sahip olduğu kuyrukları yönetmekten ve aldığı tüm mesajları ilgili kuyruklara depolamaktan sorumludur.
	• Messages (Mesajlar): Mesaj, bir uygulama için anlam taşıyan bayt dizisidir. Mesajlar, bir uygulama programından başka bir uygulama programına bilgi transferi yapmak için kullanılır.
	• Local Queues (Yerel Kuyruklar): Yerel kuyruk, mesajları depolamak için kullanılan veri yapılarıdır. Normal kuyruklar, mesajları uygulamanın doğrudan okuyacağı şekilde saklar. İletim kuyrukları ise bir başka kuyruk yöneticisine yönlendirilecek mesajları tutar.
Kurulum Yöntemleri
	• Grafiksel Kullanıcı Arayüzü (GUI): Kurulum sırasında size adım adım yardımcı olacak sihirbazlar kullanılır.
	• Komut Satırı Arayüzü: Komut satırını kullanarak sessiz veya etkileşimli bir kurulum yapılabilir. Bu senaryoda, sessiz kurulum üzerinden ilerlenir.
