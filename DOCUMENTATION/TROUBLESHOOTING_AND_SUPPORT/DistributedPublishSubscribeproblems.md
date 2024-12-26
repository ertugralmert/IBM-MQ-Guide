Dağıtık Publish/Subscribe Sorunlarının Giderilmesi
IBM MQ'nun dağıtık publish/subscribe (yayınlama/abone olma) özelliklerini kullanırken karşılaşılabilecek sorunları çözmek için aşağıdaki önerilerden faydalanabilirsiniz.

1. Genel Sorun Giderme
a. Sorunun Yaygın Sebepleri
	• Kümeleme ile ilgili genel bir sorun mu? Eğer sorun kümeleme ile ilgili genel bir sorun ise, queue manager cluster sorunlarının giderilmesi başlığına göz atın.
	• Yayınların korunması (retained publications) için tasarım önerilerini inceleyin.
b. Proxy Abonelikler
Bir proxy abonelik, bir yayınlamanın uzak bir kuyruk yöneticisindeki aboneye iletilmesini sağlar. Eğer aboneleriniz mesajları alamıyorsa:
	1. Proxy aboneliklerin yerlerini kontrol edin:display sub(*) subtype(proxy)
		○ Proxy abonelikler, dağıtık topolojinin türüne göre çeşitli yerlerde oluşturulabilir:
			§ Konu sahibi yönlendirme (topic host routing): Konu sahibinde proxy abonelik bulunur.
			§ Doğrudan yönlendirme (direct routing): Her küme yöneticisinde proxy abonelik bulunur.
	2. Proxy aboneliklerin doğru oluşturulduğunu doğrulayın:
		○ Yanlış yapılandırmalar, eksik veya gereksiz proxy aboneliklere neden olabilir.
		○ Eksik proxy abonelikler: Yanlış tanımlanan konu objeleri veya bozuk kanallar nedeniyle oluşabilir.
		○ Gereksiz proxy abonelikler: Yanlış "force" ayarı nedeniyle oluşabilir.
c. Proxy Aboneliklerin Yeniden Senkronize Edilmesi
Eğer bir kuyruk yöneticisi abonelikleri doğru şekilde gönderemiyor veya alamıyorsa, proxy abonelikleri manuel olarak yeniden senkronize edebilirsiniz:
	• Yeniden senkronizasyon komutu:REFRESH QMGR TYPE(PROXYSUB)
	• Dikkat: Bu işlem ağ üzerinde ani bir yük oluşturabilir. Yalnızca IBM MQ belgeleri veya hata kayıtları bu işlemi önermişse kullanın.

2. Yönlendirme Sorunları
a. CLROUTE Ayarları
	• Tüm kümelenmiş konu tanımlamaları aynı CLROUTE ayarına sahip olmalıdır.display tcluster(*) clroute
	• CLROUTE değerlerini kontrol edin ve uyumsuzlukları düzeltin.
		○ Geçersiz bir CLROUTE tanımı tespit edilirse: Hatalı tanımları kaldırın ve yeniden tanımlayın.
b. Küme Adlarının Yazımı
	• Konu nesnesi tanımlarken küme adının doğru yazıldığından emin olun. IBM MQ, var olmayan küme adlarını doğrulamaz.
c. Konu Durumu Görüntüleme
	• Tüm konu durumlarını görüntülemek için:display tpstatus('#')
	• Eğer bir konu dalı çok fazla bilgi içeriyorsa, daha küçük bir alt dalı veya tek bir konuyu görüntüleyebilirsiniz.

3. Yayın Döngüsü Algılama ve Önleme
Dağıtık bir publish/subscribe ağında, yayınların döngüye girmesi ağın aşırı yüklenmesine ve abonelerin aynı mesajı birden fazla kez almasına neden olabilir.
a. Döngü Algılama Mekanizması
	• IBM MQ, yayın hareket ederken her kuyruk yöneticisinin benzersiz bir "parmak izi" eklediği bir sistem kullanır.
	• Eğer bir kuyruk yöneticisi kendi parmak izini algılarsa, mesajı silerek döngüyü kırar ve hata günlüğüne kaydeder.
b. Parmak İzi Formatı
	• RFH2 başlık formatı şu şekilde çalışır:<ibm>  <Rfp>uuid1</Rfp>  <Rfp>uuid2</Rfp>  ...</ibm>
	• RFH2 Başlıkları:
		○ Bir kuyruk yöneticisi bir yayın aldığında, RFH2 başlığındaki mevcut parmak izlerini kontrol eder.
		○ Eğer kendi parmak izi bulunuyorsa, yayın bir döngüye girmiştir.

4. Sorun Çözüm Adımları
	1. Sorunların Sebeplerini Kontrol Edin:
		○ Proxy aboneliklerin doğru yerlerde olup olmadığını doğrulayın.
		○ CLROUTE ayarlarının uyumlu olduğundan emin olun.
		○ Küme tanımlarında yazım hatalarını kontrol edin.
	2. Komutları Kullanın:
		○ Proxy abonelikleri görüntüleyin:display sub(*) subtype(proxy)
		○ Konu yönlendirme durumlarını kontrol edin:display tcluster(*) clstate
	3. Hataları Günlüklerden İnceleyin:
		○ MQ hata günlüklerini kontrol edin.cat /var/mqm/errors/AMQERR01.LOG
	4. IBM MQ Destek Ekibiyle İletişime Geçin: Eğer sorun çözülmediyse veya karmaşık bir yapılandırma hatasıyla karşılaştıysanız, IBM destek ekibinden yardım alın.


