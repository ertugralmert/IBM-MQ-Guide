WCF için IBM MQ Özelleştirilmiş Kanal Sorunlarını Giderme Rehberi
IBM MQ'yu Microsoft Windows Communication Foundation (WCF) uygulamalarıyla entegre etmek için kullanılan özelleştirilmiş kanal yapılandırmalarında karşılaşılabilecek sorunları tanımlamak ve çözmek için detaylı bir rehber.

1. WCF Özelleştirilmiş Kanal İstisna Hiyerarşisi
Genel İstisna Türleri
	• TimeoutException: Zaman aşımı nedeniyle oluşur.
	• CommunicationException: İletişim sırasında meydana gelen hataları temsil eder. Alt sınıfları şunları içerebilir:
		○ IBM.XMS.XMSException
		○ IBM.WMQ.MQException
SOAP/JMS Arayüzünde İstisnalar
	• İlgili İstisnalar:
		○ System.ServiceModel.CommunicationsException
		○ IBM.XMS.XMSException
		○ IBM.WMQ.MQException
	• Eklenen Bilgiler:
		○ IBM.XMS.WCF.ErrorCode: Özel kanal istisnasının hata mesajı kodu.
		○ IBM.XMS.ErrorCode: İlk XMS istisnasının hata mesajı.
		○ IBM.WMQ.ReasonCode: Temel IBM MQ neden kodu.
		○ IBM.WMQ.CompletionCode: Temel IBM MQ tamamlanma kodu.
SOAP Olmayan/Non-JMS Arayüzünde İstisnalar
	• İlgili İstisnalar:
		○ System.ServiceModel.CommunicationsException
		○ IBM.WMQ.MQException
	• Eklenen Bilgiler:
		○ IBM.WMQ.WCF.ErrorCode: Özel kanal istisnasının hata mesajı kodu.
		○ IBM.WMQ.ReasonCode: Temel IBM MQ neden kodu.
		○ IBM.WMQ.CompletionCode: Temel IBM MQ tamamlanma kodu.

2. WCF Versiyon Bilgisi
Versiyon Bilgisine Erişim Yöntemleri
	1. IBM MQ Komutu (dspmqver):
		○ dspmqver komutu kullanılarak versiyon bilgisi alınabilir.
	2. Windows Explorer Özellikler Menüsü:
		○ IBM.XMS.WCF.dll dosyasına sağ tıklayıp, Properties > Version sekmesine gidin.
	3. FFST veya İzleme Dosyaları Başlık Bilgisi:
		○ FFST dosyaları üzerinden versiyon bilgisi alınabilir.

3. WCF İpuçları ve Öneriler
Hata Yönetiminin Dışa Aktarılması
	• WCF servis hostu kullanılırken, hizmet tarafından atılan işlenmemiş istisnalar varsayılan olarak dışa aktarılmaz.
	• Bu istisnalardan haberdar olmak için bir hata işleyici (error handler) kaydedilmelidir.
Kod Örneği: Hata İşleyici Davranışı Aşağıdaki kod, bir hata işleyici hizmet davranışını tanımlamak ve bu davranışı bir hizmete uygulamak için kullanılabilir:

using System.ServiceModel.Dispatcher;using System.Collections.ObjectModel;
public class ErrorHandlerBehaviorAttribute : Attribute, IServiceBehavior, IErrorHandler{    // IServiceBehavior Arayüzü    public void AddBindingParameters(ServiceDescription serviceDescription,       ServiceHostBase serviceHostBase, Collection<ServiceEndpoint> endpoints,       BindingParameterCollection bindingParameters)    {    }
public void ApplyDispatchBehavior(ServiceDescription serviceDescription,        ServiceHostBase serviceHostBase)    {        foreach (ChannelDispatcher channelDispatcher in serviceHostBase.ChannelDispatchers) {            channelDispatcher.ErrorHandlers.Add(this);        }    }
public void Validate(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)    {    }
// IErrorHandler Arayüzü    public bool HandleError(Exception e)    {        // Hatanın istenilen şekilde işlenmesi (örneğin, konsola yazdırma)        Console.Out.WriteLine(e);
// Diğer hata işleyicilerinin çalışmasına izin vermek için false döndürülür        return false;    }
public void ProvideFault(Exception error, MessageVersion version, ref Message fault)    {    }}

4. Genel Sorunlar ve Çözümleri
İstisna İletişimi
	• CommunicationException: Alt katmanlardan alınan ek istisnalarla bağlanır ve daha ayrıntılı bilgiler sağlar.
	• Çözüm: En üst düzeydeki istisnayı inceleyerek kök nedenleri belirleyin.
DLL ve Konfigürasyon Sorunları
	• Çözüm: DLL versiyonlarının doğru olduğundan ve yapılandırmaların güncel olduğundan emin olun.
