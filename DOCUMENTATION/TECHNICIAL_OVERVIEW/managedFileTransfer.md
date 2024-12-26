IBM MQ Managed File Transfer (MFT) - Türkçe Açıklama
IBM MQ Managed File Transfer (MFT), dosyaların sistemler arasında yönetilen ve denetlenebilir bir şekilde transfer edilmesini sağlayan bir teknolojidir. Bu çözüm, dosya boyutlarından ve kullanılan işletim sistemlerinden bağımsız olarak, güvenli ve güvenilir dosya transferi sağlar. MFT, dosya transferlerini otomatikleştirir, güvenli hale getirir ve yönetimini basitleştirir.
MFT, aşağıdaki işlemleri gerçekleştirmenize olanak tanır:
	• Dosya transferleri oluşturma ve yönetme
	• FTP, FTPS veya SFTP sunucuları ile dosya transferi yapma
	• Dosya transferlerini zamanlama ve tetikleme (örneğin, bir dosya oluşturulduğunda transferi başlatma)
	• Dosya transferlerini izleme ve günlükleme
	• Dosyaların güvenli bir şekilde iletilmesini sağlamak için SSL bağlantıları kullanma
MFT Topolojisi
MFT, IBM MQ üzerinde çalışır ve MFT ajanları ile koordinasyon kuyruk yöneticisi arasında dosya transferlerini gerçekleştirir. Ajanlar, kendi ajan kuyruk yöneticilerine bağlanır ve dosya verilerini bu kuyruklar üzerinden iletir. Koordinasyon kuyruk yöneticisi, ajanlar ve transfer durumu hakkında bilgi yayınlar, transferlerin ilerleyişini izler.
Ana Bileşenler:
	• Ajanlar (Agents): Dosya transferlerini gerçekleştiren ve kendi kuyruk yöneticilerine bağlanan bileşenlerdir. Ajanlar, dosya transferlerini gerçekleştirmek için koordinasyon kuyruk yöneticisi ile etkileşime girer.
	• Koordinasyon Kuyruk Yöneticisi (Coordination Queue Manager): Ajanlardan gelen dosya transferi bilgilerini alır, kaydeder ve dağıtır. Ayrıca transferlerin durumu hakkında bilgi sağlar.
	• Komut Kuyruk Yöneticisi (Command Queue Manager): IBM MQ ağına bağlanan ve MFT komutlarını işleyen yöneticidir.
MFT ile IBM MQ Entegrasyonu
IBM MQ, MFT'yi daha güvenilir hale getirmek için çeşitli özellikler sunar:
	• Garanti Edilmiş Mesaj Teslimi: IBM MQ'nun mesaj teslim garantisi, dosya transferinin güvenli ve sorunsuz bir şekilde gerçekleşmesini sağlar.
	• Depolama ve İleriye Doğru Yönlendirme (Store and Forward): MFT, ağ kesintileri gibi durumlarda dosya transferini kesintisiz şekilde sürdürür.
MFT REST API
MFT, dosya transferlerini yönetmek için bir REST API sunar. Bu API, transferlerin durumunu sorgulama, ajan bilgilerini alma gibi işlemleri gerçekleştirmenizi sağlar.
MFT, IBM MQ'nun sunduğu yüksek erişilebilirlik çözümleriyle de entegre olabilir. Bu sayede, MFT konfigürasyonunun dayanıklılığını artırabilirsiniz. Örneğin, ajanlar, çoğaltılmış veri kuyruk yöneticileri (RDQM) kullanarak daha dayanıklı hale getirilebilir.
MFT ile Entegre Olabileceğiniz IBM Ürünleri:
	• IBM Integration Bus: MFT tarafından transfer edilen dosyalar, IBM Integration Bus akışlarında işlenebilir.
	• IBM Sterling Connect:Direct: MFT, mevcut Connect:Direct ağınızla dosya transferi yapabilir.
	• IBM Tivoli Composite Application Manager: Transfer bilgilerini izlemek için kullanılabilir.
MFT, IBM MQ ile entegre bir şekilde çalışarak dosya transferlerinizi yönetmenizi sağlar ve ağ altyapınızın gücünü kullanarak bu süreçleri daha verimli ve güvenli hale getirir.
