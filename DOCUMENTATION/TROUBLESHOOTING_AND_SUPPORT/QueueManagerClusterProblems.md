Queue Manager Cluster Problemleri Giderme
IBM MQ cluster yapılarında ortaya çıkabilecek yaygın sorunları ve çözümlerini aşağıda detaylı bir şekilde açıklıyoruz. Bu rehber, cluster problemlerini etkili bir şekilde teşhis etmenize ve çözmenize yardımcı olacaktır.

Ön Hazırlık
	• Eğer sorunlarınız genel cluster yapılandırması yerine publish/subscribe (yayın/abonelik) ile ilgiliyse, "Routing for publish/subscribe clusters: Notes on behavior" başlığını inceleyin.
	• MQSC komutları ile çalışmanız gerekebilir. Platformunuza uygun olarak MQSC komutlarını nasıl kullanacağınızı öğrenmek için IBM MQ belgelerine başvurabilirsiniz.

Sorunlar ve Çözümler
1. Cluster Kanallarının Eşleşmemesi
	• Senaryo: Cluster kanalları doğru şekilde eşleşmiyor.
	• Açıklama: Her bir cluster sender kanalı, aynı ada sahip bir cluster receiver kanalına bağlanmalıdır. Eğer remote (uzak) queue manager üzerinde aynı ada sahip bir cluster receiver kanalı yoksa, kanal çalışmaz.
	• Çözüm: Kanalların doğru eşleştiğinden emin olun.

2. Kanalların RETRYING Durumunda Kalması
	• Senaryo: Kanallar sürekli RETRYING (tekrar deneme) durumunda.
	• Açıklama: Bu durum, kanal tanımında bir hata olduğunu veya uzak queue manager'ın çalışmadığını gösterebilir. Ayrıca, bu durum cluster içerisindeki nesnelerin (örneğin kuyruklar, queue manager'lar) güncel olmamasına yol açabilir.
	• Çözüm:
		○ Kanalların durumunu görüntüleyin:display chstatus(*)
		○ Sorunlu kanalların tanımlarını düzeltin veya eksik queue manager'ları çalıştırın.

3. Kanalların STOPPED Durumuna Geçmesi
	• Senaryo: Kanallar manuel olarak durdurulmuş.
	• Açıklama: Cluster auto-defined kanallar, manuel olarak durdurulduğunda otomatik olarak yeniden başlamaz.
	• Çözüm:
		○ Kanalı yeniden başlatın:start channel(kendi_kanal_adınız)
		○ Manuel olarak durdurmak yerine şu komutu kullanarak kanalı durdurun:stop channel(kendi_kanal_adınız) status(inactive)

4. Full Repositories Bilgilerinin Eksikliği
	• Senaryo: Cluster'daki queue manager'lar, tüm full repository queue manager'ların farkında değil.
	• Çözüm:
		○ Queue manager'ların full repository bilgilerini görüntüleyin:display clusqmgr(*) qmtype
		○ Eksik olan bilgileri tamamlamak için kanalların düzgün çalıştığından emin olun.

5. Dead-Letter Kuyruğunda Mesajlar
	• Senaryo: Queue manager tarafından teslim edilemeyen mesajlar dead-letter kuyruğuna gönderiliyor.
	• Çözüm:
		○ Dead-letter kuyruğunu kontrol edin ve mesajların neden teslim edilemediğini belirleyin.

6. RC2035 (NOT_AUTHORIZED) Hatası
	• Senaryo: Cluster'da bir kuyruk açmaya çalışırken yetkilendirme hatası alıyorsunuz.
	• Çözüm:
		○ Sistem kullanıcısına SYSTEM.CLUSTER.TRANSMIT.QUEUE kuyruğunda yeterli yetkiyi verin:setmqaut -m QMGR_ADI -n SYSTEM.CLUSTER.TRANSMIT.QUEUE -t q -g mqm +all

7. RC2085 (UNKNOWN_OBJECT_NAME) Hatası
	• Senaryo: Bir cluster kuyruğunu açarken MQRC_UNKNOWN_OBJECT_NAME hatası alıyorsunuz.
	• Çözüm:
		○ Kuyruğun cluster içinde doğru tanımlandığından ve uygun erişim seçeneklerinin kullanıldığından emin olun.
		○ Örnek komut:display clusqmgr(*) qmtype status

8. Cluster'daki Güncel Olmayan Bilgiler
	• Senaryo: Cluster queue manager'lar ve kuyruklarla ilgili eski bilgiler görüyorsunuz.
	• Çözüm:
		○ Cluster bilgilerini yenilemek için ilgili komutu kullanın:refresh cluster(cluster_adı)

9. RC2189 (CLUSTER_RESOLUTION_ERROR) Hatası
	• Senaryo: Bir kuyruğu açarken bu hata alınıyor.
	• Açıklama: Queue manager, tam repository'lere bağlanamıyor.
	• Çözüm:
		○ Full repository'lerle bağlantıların düzgün çalıştığını doğrulayın:display clusqmgr(*) qmtype status

10. Cluster Kuyruklarıyla Çalışma Sorunları
	• Senaryo: Cluster kuyruğu "MQPUT" için devre dışı bırakılmış.
	• Çözüm:
		○ Kuyruk tanımını şu şekilde değiştirin:alter qlocal(kuyruk_adı) defbind(notfixed)

11. Cluster Yönetim Komutlarının Etkisi
	• REFRESH CLUSTER komutu cluster yapısını geçici olarak etkileyebilir. Özellikle REFRESH CLUSTER sırasında çalıştırılan uygulamalar geçici hatalar alabilir (örneğin, MQRC_UNKNOWN_OBJECT_NAME, MQRC_CLUSTER_RESOLUTION_ERROR).
