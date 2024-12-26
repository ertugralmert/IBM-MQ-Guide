IBM MQ Sürüm Türleri
IBM MQ'nun iki ana sürüm türü bulunmaktadır:
	1. Long Term Support (LTS):LTS sürümleri, uzun süreli destek ve istikrar gereksinimlerini karşılamak için tasarlanmıştır. Bu sürümler genellikle daha az sıklıkla güncellenir, ancak daha uzun süre desteklenir ve uzun vadeli dağıtımlar için uygundur.
	2. Continuous Delivery (CD):CD sürümleri, IBM MQ'nun yeni özelliklerini hızlı bir şekilde sunmaya odaklanır. Bu sürümler, sık aralıklarla güncellenir ve yeni işlevsellik ekler.
LTS ve CD Sürümleri Arasındaki Farklar
	• LTS sürümleri her zaman sıfır bir modifikasyon numarasına sahiptir (örneğin, 9.3.0 ve 9.4.0).
	• CD sürümleri genellikle sıfır olmayan bir modifikasyon numarasına sahiptir (örneğin, 9.4.1, 9.4.2, vb.).
Sürüm Desteği
	• LTS sürümleri, sürümün süresi boyunca desteklenir.
	• CD sürümleri, genellikle 12 ay boyunca desteklenir veya en son iki CD sürümünden biri olduktan sonra desteklenir.
Bakım Teslimat Modeli
	• Fix Pack'ler: LTS sürümleri için güvenlik ve fonksiyonel düzeltmeleri içerir.
	• Cumulative Security Updates (CSU): Hem LTS hem de CD sürümleri için güvenlik düzeltmeleri sağlar.
	• Her iki bakım türü de birikimli olup, daha önceki fix pack veya CSU'ları içerir.
Sürüm Seçimi ve Platform Farklılıkları
	• Multiplatformlar (UNIX, Linux, Windows, IBM i): LTS fix pack'ler ve CSU'lar, interim fix olarak indirilebilir ve yeni kurulumlar veya mevcut kurulumların güncellenmesi için kullanılabilir.
	• z/OS: LTS fix pack'ler ve CSU'lar, Program Temporary Fix (PTF) numarası ile indirilebilir. CD CSU'lar genellikle bir sonraki CD sürümüyle birlikte gelir, ancak talep üzerine ayrı olarak da sağlanabilir.
IBM MQ Advanced Container ve CP4I-SC2 (Cloud Pak for Integration)
	• IBM MQ Advanced Container, IBM MQ Continuous Delivery sürümüne dayanmaktadır, ancak IBM Cloud Pak for Integration içinde kullanıldığında CP4I-SC2 (Support Cycle 2) sürümü olarak desteklenir. Bu sürüm, 2 yıl boyunca destek alır ve isteğe bağlı olarak 1 yıl daha uzatılabilir.
Sürüm Kontrolü
IBM MQ sürümünü kontrol etmek için şu yöntemler kullanılabilir:
	• dspmqver komutu veya DSPMQMVER komutu (IBM i üzerinde).
	• REST API GET metodu.
	• IBM MQ Explorer üzerinden sürüm bilgileri görüntülenebilir.
