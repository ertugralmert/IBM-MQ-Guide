1. Yetkilendirme Servis Arayüzü
IBM MQ, erişim kontrolünü Object Authority Manager (OAM) aracılığıyla sağlar. Bu sistem, MQI çağrıları, komutlar ve nesnelere erişim için yetkilendirme işlemlerini yönetir. OAM, IBM MQ nesnelerine erişimi denetler ve yöneticilerin komut satırı arayüzü kullanarak yetkilendirmeleri vermesine veya iptal etmesine olanak tanır.
	• Yetkilendirme Yönetimi: AIX, Linux ve Windows sistemlerinde güvenlik yapılandırmalarını yapmak için yetkilendirme servis bileşenleri oluşturabilirsiniz.
2. Kullanıcı Yazılımı veya Üçüncü Taraf Kanal Çıkışları
Kanal güvenliği için kullanıcı tarafından yazılmış veya üçüncü taraf kanal çıkışları kullanılabilir. Bu çıkışlar, kanal güvenliğini artırmak için özelleştirilebilir.
	• Kanal Çıkışları: Kanal mesajlarının güvenliğini sağlamak amacıyla özel çıkış programları kullanılabilir.
3. TLS Kullanarak Kanal Güvenliği
Transport Layer Security (TLS), endüstri standardı bir kanal güvenliği sağlar. TLS, dinleme, manipülasyon ve taklit saldırılarına karşı koruma sağlar.
	• TLS Özellikleri:
		○ Mesaj Gizliliği ve Bütünlüğü: Mesajları şifreleyerek gizliliğini korur.
		○ Karşılıklı Kimlik Doğrulaması: Gönderen ve alıcı arasında kimlik doğrulama yapar.
IBM MQ'de TLS güvenliği hakkında daha ayrıntılı bilgi için Cryptographic security protocols: TLS bölümüne bakabilirsiniz.
4. Kanal Kimlik Doğrulama Kayıtları
Kanal kimlik doğrulama kayıtları, bağlı sistemlere kanal bazında verilen erişimi denetlemenizi sağlar. Bu özellik, bağlantı noktalarının kimlik doğrulamasını sağlamaya yardımcı olur.
	• Detaylı Yönetim: Bağlanan sistemlere belirli yetkiler verilebilir.
5. Mesaj Güvenliği
Advanced Message Security (AMS), IBM MQ'yu kullanarak gönderilen ve alınan mesajlara şifreleme koruması sağlar. Bu özellik, IBM MQ'nun ayrı bir bileşeni olup, özel lisans gerektirir.
	• Mesaj Şifreleme: Gönderilen mesajlar, şifreleme ve kimlik doğrulama ile korunur.
6. IBM MQ.NET Yönetilen İstemci TLS Desteği
IBM MQ'nun .NET istemcisi, Microsoft'un SSLStreams kitini temel alarak TLS desteği sunar. Bu, diğer IBM MQ istemcilerinden farklıdır çünkü diğer istemciler IBM Global Security Kit (GSKit) kullanır.
IBM MQ güvenliği, mesajların güvenli iletimini ve veri bütünlüğünü sağlamak için kapsamlı bir yaklaşım sunar. Bu yöntemler, IBM MQ'nun güvenliğini sağlamak için önemli araçlardır.
