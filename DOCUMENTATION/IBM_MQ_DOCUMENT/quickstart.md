Product Overview (Ürün Özeti)
IBM MQ, çeşitli platformlar arasında farklı uygulamalar ve iş verilerini entegre etmeyi basitleştiren ve hızlandıran güçlü bir mesajlaşma ara katmanıdır. IBM MQ, uygulamalar, sistemler, hizmetler ve dosyalar arasında bilgi alışverişini güvenli, güvenilir ve garanti altına alarak iş uygulamalarının oluşturulmasını ve bakımını kolaylaştırır. Uygulama ve hizmet entegrasyonu için mesajlaşma kuyrukları aracılığıyla veri iletimi yapar. Hem yerel (on-premise) ortamlar hem de bulut ortamları ve hibrit bulut dağıtımları ile uyumlu çalışır.
IBM MQ, çeşitli Uygulama Programlama Arayüzleri (APIs) sunar:
	• Message Queue Interface (MQI)
	• Java Message Service (JMS)
	• .NET
	• AMQP
	• MQTT
	• Messaging REST API
Access the Software and Documentation (Yazılım ve Belgelere Erişim)
IBM MQ'nun Long Term Support (LTS) ve Continuous Delivery (CD) sürümleri için yazılım ve belgeler aşağıdaki bağlantılarda mevcuttur:
	• IBM MQ 9.4 yazılımını indirmek için: IBM MQ 9.4 Download
	• Quick Start Guide PDF: IBM MQ 9.4 Quick Start Guide PDF
	• IBM MQ 9.4 belgesine HTML formatında erişmek için: IBM MQ 9.4 Quick Start Guide HTML
System Requirements (Sistem Gereksinimleri)
IBM MQ'nun desteklediği platformlar için donanım ve yazılım gereksinimlerine erişmek için:
	• IBM MQ Sistem Gereksinimleri
Installation Architecture (Kurulum Mimarisi)
IBM MQ mimarileri, tek bir kuyruk yöneticisi kullanan basit yapılarla başlayıp, daha karmaşık, birbirine bağlı kuyruk yöneticilerinin oluşturduğu ağlara kadar genişler. IBM MQ mimarisini planlamak için gerekli bilgiler:
	• IBM MQ 9.4 Planlama
Installation Instructions (Kurulum Talimatları)
IBM MQ'nun tüm desteklenen platformlarda kurulumu ve gerekli donanım/yazılım yapılandırmaları için talimatlar:
	• IBM MQ 9.4 Kurulum ve Kaldırma
More Information (Daha Fazla Bilgi)
IBM MQ hakkında daha fazla bilgi ve kaynaklar:
	• IBM FAQ for Long Term Support and Continuous Delivery releases: IBM MQ FAQ
	• IBM MQ ürün okuma dosyası: IBM MQ Ürün Okuma Dosyası
	• IBM Support Site: IBM Destek Sayfası
	• IBM MQ için çoklu platformlar destek sayfası: IBM MQ Multiplatforms Support
Notlar (Notes)
	• IBM i, Long Term Support (LTS) için desteklenirken, Continuous Delivery (CD) sürümleri için desteklenmemektedir.
	• Non-install packages yalnızca konteyner imajları oluşturmak için sağlanmaktadır ve başka kullanım senaryoları için desteklenmemektedir. Bu paketler, IBM Fix Central üzerinden edinilebilir.
Trademark and Copyright Information (Ticari Marka ve Telif Hakkı Bilgisi)
IBM, IBM logosu, IBM Cloud Pak, Passport Advantage, ve z/OS gibi ticari markalarıyla dünya çapında tanınmaktadır. Java ve Java tabanlı logolar da Oracle'a ait tescilli markalardır.
****************************************
IBM MQ 9.4 Quick Start Guide 
Abstract (Özet) Bu belge, IBM MQ 9.4.0 Long Term Support (LTS) sürümü ve bakım bilgilerini, ayrıca IBM MQ 9.4.x Continuous Delivery (CD) sürümlerini içermektedir.
Content (İçerik)
Bu belgede, ürün sınırlamaları ve bilinen problemler ana başlık olarak ele alınmaktadır.
IBM MQ ile ilgili daha fazla bilgi için:
	• IBM MQ web sitesi
	• SupportPac web sayfası
	• IBM MQ destek sayfası
	• IBM MQ ürün belgeleri
Announcement letters (Duyuru Mektupları): IBM MQ 9.4 ile ilgili duyuru mektupları ve ürün tanımlamaları:
	• IBM MQ 9.4.1; IBM MQ as a Service Reserved Instance; IBM MQ on Cloud offering name change
	• IBM MQ 9.4 for Multiplatforms and IBM MQ on Cloud
	• IBM MQ for z/OS 9.4 and IBM MQ Appliance 9.4
Update History (Güncelleme Geçmişi):
	• 24 Ekim 2024: IBM MQ 9.4.1 için güncelleme yapıldı.
	• 5 Eylül 2024: IBM MQ 9.4.0.5 Fix Pack için güncelleme yapıldı.
	• 2 Temmuz 2024: IBM MQ for z/OS 9.4 ve IBM MQ Appliance 9.4 için güncelleme yapıldı.
	• 18 Haziran 2024: IBM MQ 9.4.0 for Multiplatforms için ilk oluşturma yapıldı.
Installation Instructions (Kurulum Talimatları): IBM MQ'nun tüm desteklenen platformlarda kurulumu için talimatlar ve gerekli donanım/yazılım yapılandırmaları için:
	• IBM MQ 9.4 Kurulum Sayfası
Limitations and Known Problems (Sınırlamalar ve Bilinen Problemler)
Continuous Delivery (CD) Sürümü İçin Sınırlamalar ve Bilinen Problemler (IBM MQ 9.4.1)
	• Yeni bir sınırlama veya bilinen problem yoktur.
Long Term Support (LTS) Sürümü İçin Sınırlamalar ve Bilinen Problemler (IBM MQ 9.4.0, Fix Pack 5)
	• Linux: IBM MQ konsolunu kullanarak IBM MQ 9.4.0.5'e geçiş yapıldığında çok sayıda sistem mesajı görünmektedir. Linux sistemlerinde, rpm -U MQ* komutu kullanılarak yapılan yükseltme sırasında 6000'den fazla mesaj konsol çıktısına yazılabilir. Bu sorun, geçerli hata veya uyarı mesajlarının gözden kaçmasına neden olabilir. Bu sorun APAR IT46528 ile çözülmüştür.
Initial IBM MQ 9.4.0 Sürümü İçin Sınırlamalar ve Bilinen Problemler
	• libcurl dspmqver -a çıktısında eksik. GSKit, libcurl gerektiğinde yüklemelidir, ancak şu an libcurl çıktıda yer almamaktadır. Bu sorun gelecekteki CD güncellemeleri ve LTS bakım sürümleri ile düzeltilecektir.
	• RSA Anahtar Değişimi: IBM Java 8 JRE, FIPS modunda RSA anahtar değişimini kaldırmıştır. FIPS modunda çalışmaya devam etmek için AMQP sunucusu, Managed File Transfer (MFT), IBM MQ Console, IBM MQ Explorer, IBM MQ REST API ve IBM MQ Telemetry hizmetleri gibi IBM MQ bileşenlerinin desteklenen bir CipherSuite kullanacak şekilde değiştirilmesi gerekir.
Support (Destek) Bilgisi
	• Passport Advantage Online Destek Sayfası: https://www.ibm.com/software/howtobuy/passportadvantage/paocustomer/docs/en_US/ecare.html
IBM MQ 9.4 Ürünü İçin Teknik Destek
	• IBM MQ Ürün Ana Sayfası
	• IBM MQ Destek Portalı
