IBM MQ'nun daha yeni bir sürümünü, daha önceki bir sürümle aynı sistemde "yan yana" kurmak (side-by-side installation) için takip edilmesi gereken adımlar şunlardır:
1. Çoklu Kurulum Genel Bakış
IBM MQ'nun farklı sürümlerinin aynı sistemde yan yana çalışabilmesi, özellikle geçiş süreçlerini yönetmek açısından faydalıdır. Bu tür bir kurulumda, eski sürümdeki uygulamalar ve kuyruk yöneticileri durdurulmadan yeni sürüm kurulabilir.
Sistem Gereksinimleri ve Donanım
	• İşletim Sistemi: Windows 10
	• Örnek Kuyruk Yöneticileri:
		○ QM80: IBM MQ 8.0.0 ile kurulu kalacak.
		○ QMMIG: IBM MQ 8.0.0 ile oluşturulmuş, IBM MQ 9.1'e geçiş yapılacak.
		○ QM910: IBM MQ 9.1.0 ile kurulu ve değiştirilmeyecek.
2. IBM MQ 9.4'ü Yan Yana Kurma
IBM MQ 9.4 sürümünü daha eski bir sürümle aynı makinede yan yana kurmak için şu adımları takip edin:
Başlamadan Önce
IBM MQ 9.1 sürümünün kurulu olduğundan emin olun. Eğer kurulu değilse, IBM MQ 9.1'i önce kurmalısınız.
Kurulum Adımları:
	1. Yönetici Olarak Giriş Yapın: Yönetici haklarıyla giriş yapın.
	2. IBM MQ 9.4'ü İndirin ve Kurun:
		○ IBM MQ 9.4'ün kurulum dosyasını indirin ve çıkarın.
		○ setup.exe komutunu çalıştırarak kurulum başlatın.
		○ Yazılım Gereksinimlerini Kontrol Edin: Gerekli yazılımın kurulu olduğundan emin olun.
		○ Ağ Konfigürasyonunu Kontrol Edin: Bu örnekte, sistem bir alan (domain) parçası olmadığı için "Hayır" seçeneğini seçin.
		○ Kurulum Yöntemi Seçimi: "Mevcut kurulumu etkilemeden kurulum" seçeneğini seçin.
		○ Özel Kurulum: Gerekli bileşenleri seçin (örneğin, MQI istemcisi).
		○ Kurulum tamamlandığında, IBM MQ Explorer'ı başlatın.
3. setmqenv Komutunu Kullanarak İki Sürümle Çalışma
Kurulum tamamlandığında, iki sürümle de çalışmak için setmqenv komutunu kullanarak ortamı yapılandırabilirsiniz.
Komutlar:
	• dspmqinst komutunu kullanarak kurulu sürümlerin bilgilerini görüntüleyebilirsiniz.
	• dspmqver komutuyla her iki kurulumun sürüm bilgisini kontrol edin.
Örnek:

dspmqinst
Bu komut, kurulu olan her iki IBM MQ sürümünü ve kurulum yollarını gösterir.
4. Kuyruk Yöneticisi Oluşturma
Yeni sürümü kullanarak bir kuyruk yöneticisi oluşturmak için crtmqm komutunu kullanabilirsiniz. Örneğin, QM930 adında bir kuyruk yöneticisi oluşturabilirsiniz.
Komut:

crtmqm QM930
Bu komut, QM930 adlı kuyruk yöneticisini oluşturur ve ilgili dizini oluşturur.
5. Kuyruk Yöneticisini Yeni Sürüme Geçirme
IBM MQ 9.4'te yeni bir kuyruk yöneticisini kullanmaya başlamak için, önce eski sürümdeki kuyruğu yeni sürüme taşımak gerekecektir.
Geçiş Adımları:
	1. Kuyruk Yöneticisinin Yedeğini Alın:dmpmqcfg -m QMMIG -a > QMMIG.dmpmqcfg.out.all.mqsc
	2. Kuyruk Yöneticisini Eski Sürümden Yeni Sürüme Geçirin: setmqm komutunu kullanarak kuyruk yöneticisini yeni IBM MQ sürümüne ilişkilendirin:setmqm -m QMMIG -n Installation2
	3. Kuyruk Yöneticisini Başlatın:strmqm QMMIG
6. Fix Pack Yükleme
IBM MQ 9.4 için bir Fix Pack yüklemek, ürününüzü güncel tutmak için önemlidir. Yükleme şu adımları içerir:
	1. IBM MQ 9.4 için en son Fix Pack’i indirin.
	2. Fix Pack yüklemek için dosyayı çalıştırın ve yükleme sihirbazını takip edin.
Sonuç:
	• IBM MQ 9.4'ü eski sürümle aynı sistemde başarıyla kurdunuz ve yeni sürüme geçiş yaptınız.
	• Kuyruk Yöneticisi Migrasyonu başarıyla tamamladınız ve yeni sürüme geçiş için hazırlık yaptınız.
	• Fix Pack yükleme işlemini başarıyla gerçekleştirdiniz.
Bu adımlar sayesinde IBM MQ'nun farklı sürümleri arasında geçiş yapabilir ve yan yana kurulumlar ile yönetim kolaylıkları sağlayabilirsiniz.
