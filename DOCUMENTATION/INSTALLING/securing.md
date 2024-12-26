IBM MQ Güvenliği Nedir?
IBM MQ güvenliği, mesajların gizliliğini, bütünlüğünü ve erişim yetkilendirmesini koruyarak sistemler arası güvenli iletişim sağlamayı amaçlar. IBM MQ güvenlik mekanizmaları; kimlik doğrulama, yetkilendirme, mesaj şifreleme, veri bütünlüğü ve denetleme gibi farklı alanlarda kapsamlı çözümler sunar.

IBM MQ Güvenlik Bileşenleri
1. Kimlik Doğrulama (Identification and Authentication)
Kimlik doğrulama, bir kullanıcı veya uygulamanın gerçekten iddia ettiği kişi veya uygulama olduğunu kanıtlama sürecidir.
	• X.509 Sertifikaları: Kullanıcı veya uygulamalar, X.509 dijital sertifikaları kullanarak tanımlanabilir ve doğrulanabilir. Bu sertifikalar, SSL/TLS kanallarında güvenli bir bağlantı kurmak için kullanılabilir.
	• MQCSP Yapısı: Kullanıcı adı ve şifre bilgilerini içeren MQCSP (Connection Security Parameters) yapısı, uygulamaların güvenli bir şekilde bağlanması için kullanılır. Ancak bu bilgilerin güvenli bir ağ bağlantısı üzerinden gönderilmesi önemlidir.
	• PAM Desteği: Linux ve AIX platformlarında, Pluggable Authentication Module (PAM) kimlik doğrulama mekanizması desteklenir.

2. Yetkilendirme (Authorization)
Yetkilendirme, sistemdeki kaynaklara yalnızca yetkili kullanıcıların erişmesini sağlamak için kullanılır.
	• Object Authority Manager (OAM): IBM MQ nesnelerine erişim yetkileri, OAM üzerinden yönetilir. Kullanıcılara veya gruplara, kuyruğa mesaj yazma veya okuma gibi belirli işlemleri gerçekleştirme yetkisi verilebilir.
	• Kanallar İçin Yetkilendirme: Kanalların yalnızca yetkilendirilmiş kullanıcılar tarafından yönetilmesi sağlanabilir. MCAUSER özelliği, belirli bir kanal üzerinden bağlantı yapan kullanıcıların yetkilendirilmesini sağlar.
	• LDAP Yetkilendirmesi: Yerel kullanıcı kimliklerini kullanmak yerine, LDAP sunucuları üzerinden yetkilendirme yapılabilir. Bu, özellikle büyük ve dağınık sistemlerde yönetim kolaylığı sağlar.

3. Mesaj Gizliliği (Message Confidentiality)
Mesaj gizliliği, mesajların yalnızca yetkili taraflarca görülebilmesini sağlar.
	• TLS Şifreleme: TLS protokolü, mesajların ağ üzerinden taşınırken şifrelenmesini sağlar. CipherSpec tanımlarıyla TLS bağlantıları için şifreleme algoritmaları belirlenebilir.
	• Advanced Message Security (AMS): AMS, mesajların uygulama düzeyinde şifrelenmesini ve imzalanmasını sağlar. Bu, mesajların güvenliğini yalnızca taşıma sırasında değil, aynı zamanda kuyrukta depolanırken de sağlar.
	• Z/OS Veri Şifreleme: Z/OS platformunda, veriler aktif günlük dosyaları veya paylaşılan mesaj veri setleri (SMDS) üzerinde şifrelenebilir.

4. Veri Bütünlüğü (Message Integrity)
Veri bütünlüğü, mesajların herhangi bir değişikliğe uğramadığını doğrulamak için kullanılır.
	• TLS İle Veri Bütünlüğü: TLS kullanıldığında, kullanılan CipherSpec'e bağlı olarak veri bütünlüğü sağlanır.
	• Dijital İmzalar: Mesajlara dijital imza eklenerek, mesajın gönderildiği andan itibaren değiştirilmediği kanıtlanabilir.

5. Denetleme (Auditing)
Denetleme, sistemde gerçekleşen güvenlik ihlallerini veya yetkisiz erişim girişimlerini izleme ve raporlama sürecidir.
	• Olay Mesajları: Yetki ihlalleri gibi olaylar, olay mesajları aracılığıyla raporlanabilir.
	• IBM MQ Explorer: IBM MQ Explorer, sistemin güvenlik durumunu kontrol etmek için kullanılabilir.

6. Gelişmiş Mesaj Güvenliği (Advanced Message Security - AMS)
AMS, mesajların şifrelenmesini ve imzalanmasını sağlayan ek bir güvenlik katmanıdır.
	• Mesaj Politikaları: Mesajların şifreleme ve imzalama algoritmaları, AMS güvenlik politikaları aracılığıyla belirlenir.
	• Keystore ve Sertifikalar: AMS, şifreleme için keystore ve dijital sertifikaları kullanır.

7. IBM MQ Konsol ve REST API Güvenliği
	• Kullanıcı Doğrulama: IBM MQ Konsolu ve REST API kullanıcıları, yerel işletim sistemi, LDAP veya SAF gibi farklı kayıt sistemleri aracılığıyla doğrulanabilir.
	• Yetki Seviyeleri: Kullanıcılar, yalnızca atanmış rollerine uygun işlemleri gerçekleştirebilir. Örneğin, mesajlaşma işlemleri için MQWebUser rolü atanmalıdır.
	• Token ve Sertifika Doğrulama: Kullanıcılar, LTPA token veya istemci sertifikaları ile doğrulanabilir.

8. Şifreleme Anahtarları ve Sertifika Yönetimi
IBM MQ, şifreleme anahtarları ve sertifikaların yönetimi için runmqakm ve runmqktool komutlarını sağlar.
	• Keystore Yönetimi: Şifreleme anahtarları, sertifikalar ve sertifika istekleri için CMS veya PKCS #12 formatında keystore oluşturulabilir.
	• FIPS Uyumluluğu: runmqakm komutu, FIPS uyumlu şifreleme algoritmaları sunar.

9. Kanal Güvenliği
Kanallar, iletişimde güvenlik sağlamak için aşağıdaki yöntemlerle korunabilir:
	• Kanal Yetkilendirme Kuralları (CHLAUTH): Kanallar üzerinden bağlanan kullanıcıların yetkilendirilmesi.
	• SSL/TLS Desteği: Kanallarda şifreleme ve sertifika doğrulama kullanımı.

10. Parola Koruma
IBM MQ, konfigürasyon dosyalarındaki şifreleri korumak için AES-128 şifreleme mekanizması kullanır.
	• runmqicred Komutu: Şifrelerin şifrelenmesi ve güvenli bir şekilde saklanması.
