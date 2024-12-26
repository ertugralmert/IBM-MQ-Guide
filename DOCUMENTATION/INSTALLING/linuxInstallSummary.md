Başarılı Kurulum İçin Dikkat Edilmesi Gerekenler
	1. Kurulum Dizinini Doğru Seçin
		○ /opt gibi standart bir dizin kullanarak düzenli bir yapı oluşturabilirsiniz.
	2. Lisans Kabulünü Unutmayın
		○ Lisans sözleşmesini kabul etmek zorunludur. ./mqlicense.sh -text_only komutunu mutlaka çalıştırın.
	3. Kullanıcı ve Yetkiler
		○ mqm grubu ve kullanıcılarıyla çalışmak önemlidir. Yönetim işlemleri için root veya mqm grubunda bir kullanıcı kullanmalısınız.
	4. Doğru Bileşenleri Seçin
		○ Sadece ihtiyacınız olan bileşenleri yükleyin. Zorunlu olanlar:
			§ MQSeriesRuntime
			§ MQSeriesServer
			§ MQSeriesGSKit
	5. Çevre Değişkenlerini Ayarlayın
		○ setmqenv komutunu kullanarak, her oturumda IBM MQ'yu doğru bir şekilde yüklediğinizden emin olun.
	6. Kuyruk Yöneticisini ve Kuyruğu Başlatma
		○ crtmqm ve strmqm komutlarıyla kuyruk yöneticinizi oluşturup başlatmayı unutmayın.
	7. Testleri Mutlaka Yapın
		○ amqsput ve amqsget komutlarını kullanarak testler yapın. Bu testler kurulumun doğru bir şekilde tamamlandığını doğrular.
	8. Hataları Kontrol Edin
		○ Sorun yaşarsanız logları kontrol edin (/var/mqm/errors/) veya dspmq komutuyla durum bilgisi alın.
	9. Notlarınızı Güncel Tutun
		○ Her adımdaki işlemleri not alın. Özellikle yapılandırma adımlarında, kullandığınız kuyruk ve dinleyici isimlerini kaydetmek ileride kolaylık sağlar.




IBM MQ Kurulum Notları (Linux)
1. Gerekli Hazırlıklar
	1. Sistem Gereksinimlerini Kontrol Et
		○ Kernel parametrelerini kontrol et ve ayarla:sysctl -w kernel.shmmax=268435456sysctl -w kernel.shmall=2097152sysctl -w kernel.shmmni=4096
		○ Önerilen dizin: /opt.
	2. Gerekli Kullanıcı ve Grup Oluştur
		○ mqm grubunu ve kullanıcıyı kontrol et veya oluştur:-> normal şartlarda otomatik oluşur burası opsiyonelgroupadd mqmuseradd -g mqm mqm
		○ Yönetim işlemleri için root veya mqm kullanıcısına ihtiyacınız olacak.
	3. Kurulum Dosyalarını İndir
		○ IBM Passport Advantage veya Fix Central’dan doğru dosyayı indir. Örneğin:
			§ IBM-MQC-LinuxX64.tar.gz
	4. Kurulum Dosyasını Kopyala ve Çıkar
		○ tar.gz dosyasını /opt/setup dizinine kopyala ve çıkar:mkdir -p /opt/setupcp IBM-MQC-LinuxX64.tar.gz /opt/setupcd /opt/setuptar -xvf IBM-MQC-LinuxX64.tar.gz

2. IBM MQ Kurulum Adımları
	1. Lisansı Kabul Et
		○ Lisans metnini kabul etmek için:./mqlicense.sh -text_only
	2. Paketleri Yükle (rpm Kullanıyorsanız)
		○ Zorunlu bileşenler:rpm -Uvh MQSeriesRuntime-*.rpm MQSeriesServer-*.rpm MQSeriesGSKit-*.rpm
		○ Opsiyonel bileşenler (örneğin, Java destekli mesajlaşma):rpm -Uvh MQSeriesJava-*.rpm MQSeriesJRE-*.rpm
	3. Alternatif Paket Yönetimi (dnf Kullanıyorsanız)
		○ Varsayılan dizine yüklemek için:dnf -y install MQSeries*
	4. Kurulumu Doğrula
		○ IBM MQ versiyonunu kontrol et:dspmqver

3. İlk Yapılandırma Adımları
	1. Çevre Değişkenlerini Ayarla
		○ Yüklemeyi aktif hale getirmek için:. /opt/mqm/bin/setmqenv -s
	2. Kuyruk Yöneticisi Oluştur ve Başlat
		○ Örnek bir kuyruk yöneticisi oluştur ve başlat:crtmqm QMAstrmqm QMA
	3. Dinleyici ve Kuyruk Tanımla
		○ Dinleyici tanımla:runmqsc QMADEFINE LISTENER(LISTENER1) TRPTYPE(TCP) PORT(1414) CONTROL(QMGR)START LISTENER(LISTENER1)
		○ Örnek kuyruk oluştur:DEFINE QLOCAL(QUEUE1)end

4. Test ve Doğrulama
	1. Mesaj Gönder ve Oku
		○ Mesaj gönder:./amqsput QUEUE1 QMA
		○ Mesaj oku:./amqsget QUEUE1 QMA
	2. Kuyruk Yöneticisi Durumunu Kontrol Et
		○ Çalışan yöneticileri listele:dspmq

5. Kaldırma Adımları
	1. Kuyruk Yöneticilerini Durdur
		○ Çalışan kuyruk yöneticilerini durdur:endmqm QMA
	2. Paketleri Kaldır
		○ rpm ile kaldırma:rpm -qa | grep MQSeries | xargs rpm -ev
		○ dnf ile kaldırma:dnf remove MQSeries*
	3. Gereksiz Dosyaları Sil
		○ Kullanılmayan dosyaları temizle:rm -rf /var/mqm /etc/opt/mqm

Notlar
	• Kurulum sırasında root kullanıcısı veya sudo yetkileri gerekli.
	• mqm kullanıcısı, kuyruk yöneticileriyle çalışırken kullanılır.
	• Her adımda, doğru bileşenlerin seçildiğinden emin olun.
	• Kurulum ve kaldırma sonrası dizinleri temizlerken dikkatli olun; yanlış dosyalar silinirse veriler kaybolabilir.
