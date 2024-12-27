# IBM MQ Yönetimi (Administering IBM MQ)

**IBM MQ Yönetimi**, sıraya alıcı yöneticileri (*queue managers*) ve ilgili kaynakları etkinleştirip yönetmek için çeşitli yöntemler sunar. Yönetim işlemleri, yerel (*local*) ya da uzak (*remote*) yönetim biçiminde yapılabilir.

---

## Görev Hakkında

IBM MQ yönetimi, yerel veya uzak sistemlerde farklı yöntemlerle yapılabilir:

### 1. Yerel Yönetim (Local Administration)

Yerel yönetim, kendi sisteminizde tanımlı kuyruk yöneticilerinde (*queue managers*) yönetim görevlerini yürütmek anlamına gelir.  
TCP/IP gibi protokollerle başka sistemlere erişip orada işlemler gerçekleştirebilirsiniz; ancak bu, IBM MQ perspektifinden yerel yönetim sayılır çünkü bu iletişim kanalları (*channels*) kullanılmadan, işletim sistemi tarafından sağlanır.  

*Daha fazla bilgi için:* **Working with Local IBM MQ objects.**

### 2. Uzak Yönetim (Remote Administration)

IBM MQ, tek bir temas noktasından uzaktaki kaynakların yönetimine olanak tanır.  
Uzak yönetimle, bir sistemden diğerine komutlar gönderebilir ve kaynakların durumunu değiştirebilirsiniz.  
Örneğin, bir uzak kuyruk yöneticisindeki bir kuyruğu değiştirmek için komut gönderebilirsiniz.  

> **Not:** Bu işlemler için doğru tanımlı kanallara ve çalışan bir kuyruk yöneticisine (*queue manager*) ihtiyaç vardır.  
Bazı işlemler (ör. kuyruk yöneticisi oluşturma veya başlatma) bu yöntemle yapılamaz.  

*Daha fazla bilgi için:* **Working with Remote IBM MQ objects.**

---

## IBM MQ Yönetim Yöntemleri

IBM MQ kaynaklarını yönetmek için aşağıdaki yöntemler kullanılabilir:

- **Komut Satırı Arayüzleri (CLI):** Sistem komut satırından kontrol komutlarını çalıştırabilirsiniz.
- **Grafiksel Arayüzler (GUI):** IBM MQ Explorer ve IBM MQ Console gibi araçlar.
- **Yönetim API'leri (Administrative APIs):** REST API ve diğer programatik araçlar.

### Her platformda farklı komut setleri bulunur:

- **IBM MQ Kontrol Komutları (Control Commands):** Komut satırı üzerinden yapılan temel işlemler.
- **IBM MQ Script Komutları (MQSC):** Kuyruk yöneticileri ve ilişkili nesneleri yönetmek için kullanılan bir komut dili.
- **Programlanabilir Komut Formatları (PCFs):** Otomasyon ve sistem yönetimi için tasarlanmış komut seti.
- **Yönetim REST API'si:** JSON formatında yönetim işlemleri.
- **IBM i için Kontrol Dili (CL):** IBM i platformunda kullanılan özel komut dili.

---

## Yerel ve Uzak IBM MQ Nesneleriyle Çalışma

### 1. Yerel Nesnelerle Çalışma

IBM MQ'da yerel nesneler, uygulama programlarının MQI (*Message Queue Interface*) kullanarak desteklenmesi için yönetilir.

### 2. Uzak Nesnelerle Çalışma

Uzak kuyruk yöneticileriyle çalışmak için önceden iletim kuyrukları (*transmission queues*) ve kanalların tanımlanması gerekir.  
Ayrıca, kuyruk yöneticisi kümesi (*queue manager cluster*) yapılandırması da yapılabilir.

---

## IBM MQ Yönetim Araçları ve Yöntemleri

1. **IBM MQ Explorer:**  
   Yerel veya uzak kuyruk yöneticilerinin yönetimi için Windows veya Linux x86-64 sistemlerinde kullanılabilir.

2. **IBM MQ Console:**  
   Web tarayıcı tabanlı bir arayüzle temel yönetim görevlerini gerçekleştirme imkanı sağlar.

3. **REST API ile Yönetim:**  
   IBM MQ nesnelerinin (ör. kuyruklar ve kuyruk yöneticileri) JSON formatında yönetimi.

4. **MQSC Komutları:**  
   Tüm platformlarda kullanılan ve kuyruk yöneticilerinin tüm nesnelerini yönetmek için tasarlanmış komut dili.

5. **PCF Komutları:**  
   Sistem yönetimi ve otomasyon görevlerinde kullanılır.

6. **Kontrol Komutları (Control Commands):**  
   Her platform için özel olarak tanımlanmış komutlarla temel işlemleri gerçekleştirme.
   
   
----------------

# MQSC Komutları ile IBM MQ Yönetimi (Administering IBM MQ using MQSC Commands)

**MQSC (Message Queue Script)** komutları, IBM MQ'daki kuyruk yöneticisi nesnelerini ve ilişkili kaynakları yönetmek için kullanılan bir komut dilidir. Bu komutlar tüm platformlarda kullanılabilir ve kuyruk yöneticilerinin (*queue managers*) yanı sıra şu nesnelerin yönetimini sağlar:

- **Kuyruklar (Queues)**
- **Süreç tanımları (Process definitions)**
- **Kanallar (Channels)**
- **İstemci bağlantı kanalları (Client connection channels)**
- **Dinleyiciler (Listeners)**
- **Hizmetler (Services)**
- **İsim listeleri (Namelists)**
- **Kümeler (Clusters)**
- **Kimlik doğrulama bilgileri nesneleri (Authentication information objects)**

---

## Görev Hakkında (About this task)
**MQSC komutlarının nasıl kullanılacağı**, kullanılan platforma bağlıdır:

### 1. AIX, Linux ve Windows Platformlarında:
- MQSC komutlarını **runmqsc** komut isteminde çalıştırabilirsiniz. Kullanım yöntemleri şunlardır:

  - **Etkileşimli Kullanım:** Klavyeden komut girerek çalıştırma *(örneğin: Running MQSC commands interactively under runmqsc)*.
  - **Metin Dosyasından Çalıştırma:** Bir ASCII metin dosyasından komut girme *(örneğin: Running MQSC commands from text files under runmqsc)*.
  - **Uzak Kuyruk Yöneticisine Komut Gönderme:** Uzak bir kuyruk yöneticisi üzerinde komut çalıştırma *(örneğin: Issuing MQSC commands on a remote queue manager)*.

### 2. IBM i Platformunda:
- Komutları bir betik dosyasına yazıp **STRMQMMQSC** komutunu kullanarak çalıştırabilirsiniz. Daha fazla bilgi için: *Administering using MQSC commands on IBM i*.

### 3. z/OS Platformunda:
- Komutlar, komutun türüne bağlı olarak çeşitli kaynaklardan çalıştırılabilir. Daha fazla bilgi için: *Sources from which you can issue MQSC and PCF commands on IBM MQ for z/OS*.

---

## MQSC Komut Sözdizimi (MQSC Command Syntax)

### Genel Sözdizimi:
- **Komut Sıralaması:** Her komut bir fiille *(örneğin, DEFINE)* başlar ve bir nesne türüyle *(örneğin, QLOCAL)* devam eder. Daha sonra, parametreler ve değerleri gelir.
- **Boşluk ve Virgüller:** Parametreler arasında boşluk veya virgül kullanılabilir. Ancak, her parametre arasında en az bir boşluk olmalıdır.
- **Tekrarlanan Parametreler:** Parametreler tekrar edilemez. Örneğin, hem **REPLACE** hem de **NOREPLACE** kullanımı geçersizdir.
- **Küçük/Büyük Harf Kullanımı:** Komutlar büyük/küçük harfe duyarsızdır. Örneğin, **ALTER** ile **alter** aynı anlama gelir.
- **Özel Karakterler:** Özel karakterler *(örneğin, , ", )* belirli kurallara göre kullanılmalıdır. Örneğin:
  ```
  DEFINE QLOCAL('Kuyruk_Adı*')
  ```

---

## Örnek Komut:
```plaintext
DEFINE QLOCAL('MY.LOCAL.QUEUE') +
DESCR('Bu bir yerel kuyruktur.') +
MAXDEPTH(5000) +
MAXMSGL(1024) +
PUT(ENABLED) +
GET(ENABLED);
```

---

## Metin Dosyalarından MQSC Komutlarının Çalıştırılması (Running MQSC Commands from Text Files)

### 1. Giriş Dosyası Sözdizimi:
- Her komut yeni bir satırda başlar.
- Satır başında `*` ile başlayan satırlar yorum satırıdır ve dikkate alınmaz.
- `+` işareti, komutun sonraki satırda devam edeceğini belirtir.
- Boş satırlar göz ardı edilir.

### 2. Örnek:
```plaintext
* Bu bir örnek MQSC komut dosyasıdır.
DEFINE QLOCAL('ORANGE.LOCAL.QUEUE') +
DESCR('Turuncu kuyruk') +
MAXDEPTH(5000) +
MAXMSGL(1024);
```

### 3. Çalıştırma:
```bash
runmqsc < QueueManagerName < KomutDosyası.txt
```

---

## MQSC Komutları ile Otomatik Yapılandırma

Bir kuyruk yöneticisinin her başlatıldığında belirli komutları otomatik olarak çalıştırmasını istiyorsanız, bir MQSC betiğini başlangıçta uygulatabilirsiniz.  
Bu yöntem, özellikle sürekli aynı komutların uygulanması gereken durumlarda kullanışlıdır.

---

## Kullanım Örnekleri ve Pratik Bilgiler

### 1. Kuyruk Oluşturma:
```plaintext
DEFINE QLOCAL('TEST.LOCAL.QUEUE') MAXDEPTH(1000) MAXMSGL(4096);
```

### 2. Kuyruk Bilgilerini Görüntüleme:
```plaintext
DISPLAY QLOCAL('TEST.LOCAL.QUEUE');
```

### 3. Dinleyici Tanımlama:
```plaintext
DEFINE LISTENER('MY.LISTENER') TRPTYPE(TCP) PORT(1414) CONTROL(QMGR);
```

----------------
# MQSC Komutları Kullanarak IBM MQ Yönetimi (Running MQSC Commands Interactively Under runmqsc)

**MQSC komutları**, IBM MQ kuyruk yöneticileri (*queue managers*) ve ilgili kaynakları yönetmek için kullanılan bir araçtır. **runmqsc** komut istemi, bu komutların etkileşimli veya dosya tabanlı olarak çalıştırılmasını sağlar.

---

## Etkileşimli Olarak MQSC Komutlarının Çalıştırılması

### Ön Koşullar
- **runmqsc** komutunu, çalışmak istediğiniz kuyruk yöneticisiyle ilişkilendirilmiş kurulumdan çalıştırmanız gerekir.
- Kuyruk yöneticisinin hangi kurulumla ilişkili olduğunu öğrenmek için şu komut kullanılabilir:

```bash
dspmq -o installation
```

- Daha iyi bir kullanıcı deneyimi için **MQPROMPT** ortam değişkenini kullanarak komut istemini özelleştirebilirsiniz. Örneğin, kuyruk yöneticisinin adını ve sistemi görüntüleyebilirsiniz.

Örnek:
```bash
export MQPROMPT="+QMNAME+> "
```

---

## Çalıştırma Yöntemi

### 1. Komut İstemini Açma:
```bash
runmqsc QMgrName
```
- **QMgrName**, çalışmak istediğiniz kuyruk yöneticisinin adıdır. Varsayılan kuyruk yöneticisiyle çalışmak için boş bırakabilirsiniz.

### 2. Komut Girme:
- Örnek bir yerel kuyruk oluşturma:
```plaintext
DEFINE QLOCAL(ORANGE.LOCAL.QUEUE)
```

- Uzun komutları birden fazla satırda yazmak için:
  - **`+` işareti:** Komutun sonraki satırın ilk boş olmayan karakterinden devam edeceğini belirtir.
  - **`-` işareti:** Komutun sonraki satırın başlangıcından devam edeceğini belirtir.

- Komutları açıkça sonlandırmak için noktalı virgül kullanabilirsiniz:
```plaintext
DEFINE QLOCAL(ORANGE.LOCAL.QUEUE) +
DESCR('Yerel bir kuyruk') +
MAXDEPTH(5000);
```

### 3. MQSC Ortamından Çıkış:
- Aşağıdaki komutlardan birini kullanarak çıkabilirsiniz:
```plaintext
end
exit
quit
```

### Çıktılar
- Başarılı işlemler için sistemden doğrulama mesajları alırsınız:
```plaintext
AMQ8006: IBM MQ queue created.
```
- Sözdizimi hataları için hata mesajları alırsınız:
```plaintext
AMQ8405: Syntax error detected at or near end of command segment.
```

---

## Örnekler ve Alternatif Kullanımlar

### Varsayılan Kuyruk Yöneticisini Kullanma

#### Tek Komut Çalıştırma
- **Windows:**
```bash
echo display chstatus(*) | runmqsc QMname
```
- **Linux:**
```bash
echo "display chstatus(*)" | runmqsc QMname
```

### Uzak Kuyruk Yöneticisi Üzerinde Komut Çalıştırma
```bash
runmqsc -w 30 -m QMLOCAL QMREMOTE
```
- **`-w`:** Bekleme süresi (30 saniye).
- **`-m`:** Yerel kuyruk yöneticisi.

### Sözdizimini Doğrulama (Komutları Çalıştırmadan)
```bash
runmqsc -f myprog.in -v QmgrName
```
- **`-f`:** Komutların bulunduğu giriş dosyası.
- **`-v`:** Doğrulama modu.

---

## MQPROMPT ile Komut İstemini Özelleştirme

**MQPROMPT** ortam değişkeni ile istem görünümünü özelleştirebilirsiniz. Örnekler:

1. **Basit bir görünüm:**
```bash
export MQPROMPT="MQSC>"
```

2. **Kullanıcı adı, kuyruk yöneticisi adı ve sistem bilgilerini gösterme:**
```bash
export MQPROMPT="+USER+ @ +QMNAME+ @ +MQ_HOST_NAME+> "
```

3. **Zaman damgası ekleme:**
```bash
export MQPROMPT="+MQ_DATE_TIME+ +USER+ @ +QMNAME+ @ +MQ_HOST_NAME+> "
```

---

## MQSC Komutlarının Otomatik Uygulanması

Kuyruk yöneticisinin her başlatıldığında belirli bir konfigürasyonu otomatik olarak yüklemesi için MQSC betiklerini kullanabilirsiniz.

### 1. Yeni Kuyruk Yöneticisi İçin:
```bash
crtmqm -ic C:\mq_configuration\uniclus.mqsc QMNAME
```

### 2. Mevcut Kuyruk Yöneticisi İçin:
- **qm.ini** dosyasına aşağıdaki gibi bir yapı eklenir:
```plaintext
AutoConfig:
  MQSCConfig=C:\mq_configuration\uniclus.mqsc
```

### 3. Otomatik Yapılandırma Çalışma Prensibi:
- Betik veya dosya ilk başlatmada doğrulama sürecinden geçer.
- Hata durumunda, önceki geçerli yapılandırma uygulanır ve hata mesajı sistem loglarına yazılır.


--------------

# PCF Komutları Kullanarak IBM MQ Yönetiminin Otomasyonu (Automating IBM MQ Administration Using PCF Commands)

**PCF (Programmable Command Format)** komutları, IBM MQ'daki yönetim görevlerini bir programlama arayüzü üzerinden otomatize etmek için kullanılır. Bu yöntem, hem yerel hem de uzak kuyruk yöneticilerinin yönetim ve izleme görevlerini kolaylaştırır.

---

## PCF Komutlarının Özellikleri ve Kullanım Alanları

### 1. PCF Komutları Nedir?
- **PCF komutları**, IBM MQ nesnelerini (*kuyruklar, süreç tanımları, isim listeleri, kanallar, dinleyiciler, hizmetler ve kimlik doğrulama bilgileri gibi*) yönetmek için bir program üzerinden kullanılabilir.
- PCF komutları, bir IBM MQ mesajının uygulama veri kısmına gömülü veri yapılarıdır ve hedef kuyruk yöneticisine **MQPUT** işleviyle gönderilir.

### 2. PCF Komutlarının Avantajları
- Merkezi bir noktadan ağdaki herhangi bir kuyruk yöneticisini yönetebilme.
- Yönetim görevlerini otomatikleştirme ve karmaşık dağıtık ağlarda yönetimi basitleştirme.
- PCF komutları metin tabanlı değildir; bu nedenle doğrudan okunamaz. Bunun yerine veri yapıları olarak işlenir.

### 3. PCF Mesajlarının Çalışma Prensibi
- **Komut Mesajı Gönderme:** Komutlar, **MQPUT** işleviyle kuyruk yöneticisine gönderilir.
- **Yanıt Alma:** Komut sunucusu (*command server*), komut mesajını işler ve yanıtı bir veya daha fazla mesaj olarak geri gönderir.
- **Yanıt İşleme:** **MQGET** işleviyle alınan yanıtlar işlenir ve sonuçlara göre aksiyon alınır.

---

## PCF Komutlarının Bileşenleri

### 1. Mesaj Başlığı (Message Descriptor)
- **MsgType:** Mesaj türü **MQMT_REQUEST** olmalıdır.
- **Format:** **MQFMT_ADMIN** olarak ayarlanmalıdır.
- **ReplyToQ:** Yanıt mesajlarının alınacağı kuyruğun adı.

### 2. PCF Mesaj Verisi
- **PCF Başlığı (PCF Header):** Komut türünü belirtir (örneğin, **MQCMD_CHANGE_Q** bir kuyruğu değiştirme komutudur).
- **Parametre Yapıları (Parameter Structures):** Komut için gerekli parametreleri içerir.

### 3. Escape PCF Komutları
- **Escape PCF komutları**, bir MQSC komutunu PCF komutları içerisinde göndermek için kullanılır. Bu yöntemle uzak kuyruk yöneticilerine MQSC komutları gönderilebilir.

---

## PCF Komutlarının Kullanım Adımları

### 1. PCF Mesaj Gönderme
**PCF Mesajının Oluşturulması:**
- Mesaj başlığı ve veri yapılarını içeren bir PCF komutu oluşturulur.
- Örnek bir PCF başlığı:
```plaintext
MQCFH - PCF Header
Command Identifier: MQCMD_CHANGE_Q
```

**MQPUT Kullanarak Mesaj Gönderme:**
- Kuyruk yöneticisine mesaj göndermek için **MQPUT** işlevi kullanılır.
- Gerekli girişler:
  - MQI bağlantı tanıtıcısı.
  - Hedef kuyruğun nesne tanıtıcısı (örneğin, **SYSTEM.ADMIN.COMMAND.QUEUE**).
  - Mesaj başlığı ve veri yapıları.

### 2. Yanıt Alma
**Yanıt Mesajının Yapısı:**
- Yanıt mesajları da PCF başlığı ve parametre yapılarını içerir.
- Yanıt türleri:
  - **OK Yanıtı:** Komut başarıyla işlenmişse.
  - **Hata Yanıtı:** Komut işlenirken bir hata oluşmuşsa.
  - **Veri Yanıtı:** İstek bir *"Inquire"* komutuysa, istenen veriyi içerir.

**MQGET Kullanarak Yanıt Alınması:**
- Yanıt mesajları **MQGET** işleviyle alınır.
- Yanıtlar bir veri çantasında (*data bag*) işlenir.

---

## IBM MQ Yönetim Arayüzü (MQAI) ile PCF Kullanımının Basitleştirilmesi

### 1. MQAI Nedir?
- IBM MQ Yönetim Arayüzü (**MQAI**), PCF mesajlarını basitleştirmek için kullanılan bir programlama arayüzüdür.
- Verileri işlemeye yönelik veri çantaları (*data bags*) kullanır ve karmaşık veri yapılarını yönetme gereksinimini ortadan kaldırır.

### 2. MQAI Kullanmanın Avantajları
- PCF mesajlarının oluşturulmasını ve yönetilmesini kolaylaştırır.
- Hata durumlarını daha basit bir şekilde yönetir.
- Mesaj verilerini farklı uygulamalar arasında dönüştürme işlemlerini kolaylaştırır.

### 3. MQAI ile Yönetim Örnekleri
- **Yerel bir kuyruğun oluşturulması:**
```plaintext
amqsaicq.c
```
- **Kuyruk durumlarının listelenmesi:**
```plaintext
amqsailq.c
```

### 4. MQAI Kullanarak Komut Gönderme:
- **mqExecute** işlevi, veri çantasını komut sunucusuna gönderir ve yanıtları bir yanıt çantasında döner.

---

## PCF Komutlarının Yetkilendirme Kontrolleri

### Kullanıcı Yetkilendirme:
- Komutu gönderen kullanıcı, hedef kuyruk yöneticisi üzerindeki gerekli yetkilere sahip olmalıdır.
- Örneğin, bir kanal komutunu çalıştırmak için kullanıcı **mqm** grubuna üye olmalıdır.

### Yetki Kontrollerinin İşleyişi:
- Hedef sistemde kullanıcı kimliği kontrol edilir.
- Hedef nesneye erişim için gereken yetkilere sahip olunmalıdır.

---

## Örnek PCF Komutları

### 1. Yerel Kuyruk Oluşturma:
- **Komut:** **MQCMD_CREATE_Q**
- **Parametreler:**
  - **QueueName:** Yeni kuyruğun adı.
  - **MaxDepth:** Kuyruğun maksimum mesaj derinliği.

### 2. Kuyruk Durumunu Sorgulama:
- **Komut:** **MQCMD_INQUIRE_Q_STATUS**
- **Yanıt:** Kuyruk derinliği ve diğer durum bilgileri.

-----------------


# IBM MQ Yönetimi için REST API Kullanımı

IBM MQ'yu yönetmek için **REST API**'yi kullanarak kuyruk yöneticileri, kuyruklar ve diğer nesneler üzerinde işlemler gerçekleştirebilirsiniz. **REST API**, **JSON** formatında bilgi alışverişi yapar ve modern **DevOps** araçlarına entegrasyonu kolaylaştırır.

---

## Genel Özellikler

### 1. REST API ile Yönetim
- IBM MQ nesneleri üzerinde işlem yapmak için **HTTP yöntemleri** (*GET, POST, PATCH, DELETE*) kullanılır.
- İşlemler **JSON tabanlı yükler** veya sorgu parametreleri aracılığıyla iletilir.
- API sonuçları **JSON formatında** döner ve **HTTP yanıt kodlarıyla** desteklenir.

### 2. Desteklenen Kaynaklar
REST API, aşağıdaki kaynakları yönetmek için kullanılır:
- **/admin/qmgr:** Kuyruk yöneticisi.
- **/admin/queue:** Kuyruk.
- **/admin/subscription:** Abonelik.
- **/admin/channel:** Kanal.
- **/action/qmgr/{qmgrName}/mqsc:** MQSC komutları çalıştırma.

### 3. Versiyonlama
- REST API sürüm numarası URL'de belirtilir. Örneğin:
```
https://localhost:9443/ibmmq/rest/v2/admin/qmgr
```

---

## REST API ile Temel İşlemler

### 1. Ön Gereksinimler
- **mqweb** sunucusunun yapılandırılmış ve çalışıyor olması gerekir.
- **dspmqweb** komutu ile API URL'si belirlenebilir:
```bash
dspmqweb status
```

### 2. Temel API Çağrıları

**Örnek 1: Kuyruk Yöneticilerini Listeleme (GET)**
Kuyruk yöneticilerini listelemek için GET yöntemi kullanılır:
```bash
curl -k https://localhost:9443/ibmmq/rest/v2/admin/qmgr -X GET -u mqadmin:mqadmin
```

**Örnek 2: Yerel Kuyruk Oluşturma (POST)**
Yeni bir kuyruk oluşturmak için:
```bash
curl -k https://localhost:9443/ibmmq/rest/v2/admin/action/qmgr/QM1/mqsc \
     -X POST \
     -u mqadmin:mqadmin \
     -H "ibm-mq-rest-csrf-token: value" \
     -H "Content-Type: application/json" \
     --data '{
         "type": "runCommandJSON",
         "command": "define",
         "qualifier": "qlocal",
         "name": "Q1"
     }'
```

**Örnek 3: Kuyruk Detaylarını Görüntüleme (POST)**
Oluşturulan kuyruğun ayrıntılarını görüntülemek için:
```bash
curl -k https://localhost:9443/ibmmq/rest/v2/admin/action/qmgr/QM1/mqsc \
     -X POST \
     -u mqadmin:mqadmin \
     -H "ibm-mq-rest-csrf-token: value" \
     -H "Content-Type: application/json" \
     --data '{
         "type": "runCommandJSON",
         "command": "display",
         "qualifier": "qlocal",
         "name": "Q1"
     }'
```

**Örnek 4: Kuyruk Güncelleme (POST)**
Kuyruğun açıklamasını değiştirmek için:
```bash
curl -k https://localhost:9443/ibmmq/rest/v2/admin/action/qmgr/QM1/mqsc \
     -X POST \
     -u mqadmin:mqadmin \
     -H "ibm-mq-rest-csrf-token: value" \
     -H "Content-Type: application/json" \
     --data '{
         "type": "runCommandJSON",
         "command": "alter",
         "qualifier": "qlocal",
         "name": "Q1",
         "parameters": {
             "descr": "new description"
         }
     }'
```

**Örnek 5: Kuyruk Silme (POST)**
Bir kuyruğu silmek için:
```bash
curl -k https://localhost:9443/ibmmq/rest/v2/admin/action/qmgr/QM1/mqsc \
     -X POST \
     -u mqadmin:mqadmin \
     -H "ibm-mq-rest-csrf-token: value" \
     -H "Content-Type: application/json" \
     --data '{
         "type": "runCommandJSON",
         "command": "delete",
         "qualifier": "qlocal",
         "name": "Q1"
     }'
```

---

## Uzaktan Yönetim

REST API, uzak kuyruk yöneticilerini yönetmek için de kullanılabilir. Bunun için:

### 1. Gateway Kuyruk Yöneticisi Ayarı
- Gateway olarak kullanılacak bir kuyruk yöneticisi tanımlanmalıdır:
```bash
setmqweb properties -k mqRestGatewayQmgr -v QM1
```

### 2. Uzaktaki Kuyruk Yöneticisine Erişim
Uzak bir kuyruk yöneticisinde işlem yapmak için URL şu şekilde düzenlenir:
```
https://localhost:9443/ibmmq/rest/v2/admin/qmgr/remoteQM
```

---

## Hata Yönetimi ve Yanıtlar

REST API, hataları **JSON formatında** döndürür ve **HTTP hata kodlarıyla** belirtir:
- **HTTP 404:** Kaynak bulunamadı.
- **HTTP 500:** Sunucu hatası.

**Örnek Yanıt:**
```json
{
  "error": [
    {
      "type": "rest",
      "messageId": "MQWB0009E",
      "message": "MQWB0009E: Could not query the queue manager 'QM1'",
      "explanation": "The MQ REST API was invoked specifying a queue manager name which cannot be located.",
      "action": "Resubmit the request with a valid queue manager name or no queue manager name, to retrieve a list of queue managers."
    }
  ]
}
```

---

# IBM MQ Console Kullanımı ile Yönetim

**IBM MQ Console**, kuyruk yöneticilerini ve ilgili IBM MQ nesnelerini yönetmek için kullanılan bir **web tabanlı arayüzdür**. Aşağıda, IBM MQ Console'u kullanmaya başlamak ve temel yönetim görevlerini gerçekleştirmek için bir kılavuz bulunmaktadır.

---

## IBM MQ Console'a Başlarken

### 1. Ön Gereksinimler
- **mqweb** sunucusunun yapılandırılmış ve çalışıyor olması gerekir.
- **dspmqweb** komutunu çalıştırabilmek için gerekli izinlere sahip bir kullanıcı olunmalıdır:
  - **[z/OS]:** *mqwebuser.xml* dosyasına yazma erişimi gereklidir.
  - **[UNIX, Linux, Windows, IBM i]:** Ayrıcalıklı bir kullanıcı olmalısınız.
  - **[IBM i]:** Komutlar **QSHELL** içinde çalıştırılmalıdır.

### 2. IBM MQ Console URI'sini Belirleme
**dspmqweb** komutuyla URI belirlenir:
```bash
dspmqweb status
```
**Örnek çıktı:**
```
MQWB1124I: Server 'mqweb' is running.
   URLS:
   https://localhost:9443/ibmmq/rest/v1/
   https://localhost:9443/ibmmq/console/
```
- **IBM MQ Console URI'si:** [https://localhost:9443/ibmmq/console/](https://localhost:9443/ibmmq/console/)

### 3. IBM MQ Console'a Erişim
1. Tarayıcınıza URI'yi girin: **https://localhost:9443/ibmmq/console/**
2. Güvenlik sertifikası için uyarı çıkarsa "İlerle" seçeneğini seçin.
3. Kullanıcı adı ve parola ile giriş yapın:
   - **Kullanıcı adı:** *mqadmin*
   - **Parola:** *mqadmin*

---

## IBM MQ Console Özellikleri

### 1. Konsol Giriş Sayfası
Giriş yaptıktan sonra şu seçeneklerden birini seçebilirsiniz:
- **Kuyruk Yöneticilerini Yönet:** Mevcut kuyruk yöneticilerini listeleyebilir veya yönetebilirsiniz.
- **Kuyruk veya Kuyruk Yöneticisi Oluştur:** Yeni nesneler oluşturabilirsiniz.
- **Eğitim Kaynaklarına Göz At:** Eğitim belgelerine ulaşabilirsiniz.
- **IBM MQ Belgeleri:** Ürün bilgilerine erişim sağlayabilirsiniz.

### 2. IBM MQ Console Ayarları
- Tema ve görünüm düzenlemeleri.
- Zaman aşımı değerlerinin yapılandırılması.

---

## IBM MQ Console ile Yönetim İşlemleri

### 1. Kuyruk Yöneticilerini Görüntüleme
1. "Kuyruk Yöneticileri" sekmesine tıklayın.
2. Mevcut kuyruk yöneticilerinin listesi görüntülenir.

### 2. Yeni Bir Kuyruk Yöneticisi Oluşturma
1. "Kuyruk Yöneticisi Oluştur" düğmesine tıklayın.
2. Gerekli bilgileri girin (örneğin, isim ve port numarası).
3. "Oluştur" düğmesine tıklayın.

### 3. Kuyruk Yöneticisi Durumunu Kontrol Etme
1. Listeden bir kuyruk yöneticisi seçin.
2. Detayları ve durum bilgilerini görüntüleyin.

### 4. Yeni Kuyruk Oluşturma
1. Bir kuyruk yöneticisini seçin.
2. "Kuyruk Oluştur" seçeneğine tıklayın.
3. Gerekli bilgileri doldurun (örneğin, kuyruk adı).
4. "Kaydet" düğmesine tıklayın.

### 5. Kanal Yönetimi
1. "Kanallar" sekmesine gidin.
2. Yeni bir kanal oluşturabilir veya mevcut bir kanalın detaylarını görüntüleyebilirsiniz.

---

## Önemli Notlar ve Kısıtlamalar

**[z/OS]:**
- Kuyruk yöneticileri oluşturulamaz veya silinemez.
- Dinleyiciler görüntülenemez veya yönetilemez.
- Sistem kaynak kullanımı izlenemez.

**[UNIX, Linux, Windows, IBM i]:**
- AMQP veya MQTT kanalları yönetilemez.

---

## IBM MQ Console ile Güvenlik

### 1. Kimlik Doğrulama
- Varsayılan olarak **token tabanlı kimlik doğrulama** kullanılır.
- Alternatif olarak **istemci sertifikası kimlik doğrulaması** kullanılabilir.

### 2. Sertifika Güvenliği
- Tarayıcının güvenlik sertifikasıyla ilgili bir uyarı göstermesi durumunda, "İlerle" seçeneği seçilebilir.

---

## Hızlı Bakış: IBM MQ Console

### Ana Sayfa
**IBM MQ Console**'un açılış sayfasında şunları yapabilirsiniz:
1. **Mevcut Kuyruk Yöneticilerini Yönetme:**
   - Kuyruk yöneticilerinin listesini görüntüleyebilir ve durumlarını kontrol edebilirsiniz.
2. **Yeni Kuyruk Yöneticisi veya Kuyruk Oluşturma:**
   - Yeni nesneler oluşturabilirsiniz.
3. **Eğitim Kaynaklarına Göz Atma:**
   - Eğitim belgelerine erişebilirsiniz.
4. **Hızlı Başlangıç Rehberi:**
   - Mesajlaşma ayarlarını yapılandırmak için rehber.

---

## IBM MQ Console ile Uzaktan Yönetim

IBM MQ Console ile uzaktaki bir kuyruk yöneticisini yönetmek için:

### 1. Kuyruk Yöneticileri Arasında İletişimi Yapılandırın
- Dinleyiciler, kanallar ve iletim kuyrukları oluşturun.

### 2. Güvenlik Ayarlarını Yapılandırın
- Gerekli yetkileri tanımlayın.

### 3. Uzaktaki Kuyruk Yöneticisine Bağlanın
- İlgili **URI**'yi kullanarak konsoldan bağlantı kurun.

---

## Kuyruk Yöneticisi Panosu

### Genel Bakış Sekmesi
- **CPU Kullanımı:** Kuyruk yöneticisinin CPU kullanım yüzdesi.
- **Bellek Kullanımı:** Bellek kullanım yüzdesi.
- **Depolama Durumu:** Diskteki boş alan yüzdesi.
- **Aktif Kuyruklar:** Mesaj bulunan kuyruk sayısı.
- **Bağlı Uygulamalar:** Aktif bağlantı sayısı.
- **Son Mesajlar:** Mesaj geçişi özet bilgileri.

### Kuyruklar Sekmesi
- **Yeni Kuyruk Oluştur:** Kuyruk yöneticisinde yeni bir kuyruk oluşturabilirsiniz.
- **Mevcut Kuyrukları Görüntüle:** Mesajları inceleyebilir ve yeni mesajlar oluşturabilirsiniz.

### Olaylar Sekmesi
- **Konular:** Yeni konular oluşturabilir veya mevcut konuları düzenleyebilirsiniz.
- **Abonelikler:** Yeni abonelikler oluşturabilir veya mevcut abonelikleri yönetebilirsiniz.

---

# IBM MQ Console: Yerel ve Uzaktaki Kuyruk Yöneticileri ile Çalışma

## Yerel Kuyruk Yöneticileri ile Çalışma
IBM MQ Console'da, aynı IBM MQ kurulumuna bağlı yerel kuyruk yöneticilerini yönetebilirsiniz. Yerel kuyruk yöneticileri üzerinde aşağıdaki işlemleri yapabilirsiniz:

### Yerel Kuyruk Yöneticisi Oluşturma
1. **"Create"** düğmesine tıklayın.
2. Kuyruk yöneticisine bir ad verin (*48 karaktere kadar, harf, rakam, '.', '/', '_' ve '%' karakterleri kullanılabilir*).
3. İsteğe bağlı olarak bir **TCP/IP portu** belirtin (*65535'i aşmamalıdır*).
4. **"Create"** butonuna tıklayın. Kuyruk yöneticisi oluşturulur ve başlatılır.

### Yerel Kuyruk Yöneticisi Başlatma
1. Listeden başlatmak istediğiniz kuyruk yöneticisini seçin.
2. **"Start"** seçeneğine tıklayın.

### Yerel Kuyruk Yöneticisi Durdurma
1. Durdurmak istediğiniz kuyruk yöneticisini seçin.
2. **"Stop"** seçeneğine tıklayın.

### Yerel Kuyruk Yöneticisini Silme
1. Kuyruk yöneticisi çalışıyorsa durdurun.
2. **"View Configuration"** menüsünden **"Delete Queue Manager"** seçeneğini seçin.
3. Silme işlemini onaylamak için kuyruk yöneticisinin adını girin.

### Yerel Kuyruk Yöneticisi Özelliklerini Görüntüleme ve Düzenleme
1. Kuyruk yöneticisinin çalıştığından emin olun ve listeden seçin.
2. **"View Configuration"** menüsünden **"Properties"** sekmesini açın.
3. Düzenlemeleri yaptıktan sonra **"Save"** butonuna tıklayın.

### Güvenlik Ayarları ile Çalışma
1. Kuyruk yöneticisini seçin ve **"View Configuration"** menüsüne tıklayın.
2. **"Security"** sekmesini seçin.
3. **Kimlik Doğrulama Nesneleri**, **Yetkilendirme Kayıtları** veya **Kanal Kimlik Doğrulama Kayıtları** üzerinde işlem yapabilirsiniz.

---

## Uzaktaki Kuyruk Yöneticilerini IBM MQ Console’a Ekleme
IBM MQ Console, uzaktaki kuyruk yöneticilerini yönetmek için de kullanılabilir. Bunun için aşağıdaki adımları izleyebilirsiniz:

### Uzaktaki Kuyruk Yöneticisini JSON CCDT ile Ekleme
1. **"Connect Remote Queue Manager"** seçeneğine tıklayın.
2. Uzaktaki kuyruk yöneticisinin adını girin.
3. **"Connect using a JSON CCDT"** seçeneğini seçin.
4. **JSON CCDT dosyasını** seçmek için **"Browse"** butonuna tıklayın.
5. İsteğe bağlı olarak kullanıcı adı ve şifre bilgilerini girin.
6. Sertifika bilgilerini ekleyin veya kontrol edin.
7. **"Connect"** butonuna tıklayın.

### Manuel Bağlantı Bilgileri ile Uzaktaki Kuyruk Yöneticisi Ekleme
1. **"Connect Remote Queue Manager"** seçeneğine tıklayın.
2. Uzaktaki kuyruk yöneticisinin adını girin.
3. **"Manual Entry"** seçeneğini seçin.
4. Kanal adını, ana bilgisayar ve port bilgilerini girin.
5. İsteğe bağlı olarak kullanıcı adı ve şifre bilgilerini girin.
6. Sertifika bilgilerini ekleyin.
7. **"Connect"** butonuna tıklayın.

---

## JSON CCDT Dosyası Örneği
Uzaktaki bir kuyruk yöneticisi için temel bir **JSON CCDT dosyası** şu şekilde olabilir:

```json
{
  "channel": [{
      "name": "QM1.SVRCONN",
      "clientConnection": {
        "connection": [{
            "host": "example.com",
            "port": 1414
          }],
        "queueManager": "QM1"
      },
      "type": "clientConnection"
    }]
}
```

---

# IBM MQ Console: Çalışma Nesneleri ile İlgili Tüm Detaylar

IBM MQ Console, bir kuyruk yöneticisi ile ilişkili çeşitli nesneler üzerinde işlem yapmanıza olanak tanır. Bu nesneler arasında **kuyruklar**, **konular**, **abonelikler**, **uygulama kanalları** ve **ağ nesneleri** bulunur.

---

## 1. Kuyruklarla Çalışma

### Kuyruk Ekleme
1. **Queues** sekmesine gidin.
2. **Create** düğmesine tıklayın.
3. Kuyruk tipini seçin:
   - **Local Queue:** Mesajları yerel kuyruk yöneticisinde depolar.
   - **Alias Queue:** Aynı kuyruk yöneticisindeki başka bir kuyruğa işaret eder.
   - **Remote Queue:** Başka bir kuyruk yöneticisindeki kuyruğa işaret eder.
   - **Model Queue:** Dinamik kuyruklar için bir şablondur.
4. Gerekli bilgileri girin ve **Create** düğmesine tıklayın.

### Mesaj Ekleme
1. Mesaj eklemek istediğiniz kuyruğu seçin.
2. **Create** butonuna tıklayın.
3. Mesajınızı yazın ve **Create** düğmesine basın.

### Mesajları Temizleme
1. Mesajlarını temizlemek istediğiniz kuyruğu seçin.
2. **Clear queue** ikonuna tıklayın ve onaylayın.

### Mesajları Görüntüleme ve Silme
1. Kuyruğu seçerek mesaj listesini görüntüleyin.
2. Silmek istediğiniz mesaj için **delete** ikonuna tıklayın ve silme işlemini onaylayın.

### Kuyruğu Silme
1. Silmek istediğiniz kuyruğu seçin.
2. **Actions** menüsünden **Delete queue** seçeneğini seçin ve onaylayın.

### Kuyruk Özelliklerini Düzenleme
1. **View Configuration** menüsünden kuyruk özelliklerini görüntüleyin.
2. **Edit** düğmesine tıklayarak değişiklik yapın ve **Save** butonuna basın.

---

## 2. Konularla Çalışma

### Konu Ekleme
1. **Events** sekmesinden **Topics** bölümüne gidin.
2. **Create** butonuna tıklayın.
3. Konu bilgilerini doldurun ve **Create** düğmesine basın.

### Mesaj Yayınlama
1. Yayın yapmak istediğiniz konuyu seçin.
2. İlgili aboneliği seçin.
3. Mesajınızı yazın ve **Put** butonuna basın.

### Konu Silme
1. Silmek istediğiniz konu için **spanner** ikonuna tıklayın.
2. **Delete topic** seçeneğini seçin ve onaylayın.

### Konu Özelliklerini Düzenleme
1. **Edit** ikonuna tıklayın.
2. Özellikleri değiştirin ve **Save** düğmesine basın.

---

## 3. Aboneliklerle Çalışma

### Abonelik Ekleme
1. **Events** sekmesinden **Subscriptions** bölümüne gidin.
2. Abonelik tipini (yönetilen veya yönetilmeyen) seçin.
3. Gerekli bilgileri girin ve **Create** düğmesine basın.

### Abonelik Silme
1. Silmek istediğiniz abonelik için **spanner** ikonuna tıklayın.
2. **Delete subscription** seçeneğini seçin ve onaylayın.

### Abonelik Özelliklerini Düzenleme
1. **Edit** ikonuna tıklayın.
2. Özellikleri düzenleyin ve **Save** butonuna tıklayın.

---

## 4. Kuyruk Yöneticisi Kanalları ile Çalışma

### Kanal Ekleme
1. **MQ Network** sekmesinden **Queue Manager Channels** bölümüne gidin.
2. **Create** butonuna tıklayın.
3. Gerekli bilgileri girin ve **Create** düğmesine basın.

### Kanalı Başlatma ve Durdurma
- **Başlatmak için:** Kanalı seçin ve **Start** seçeneğini kullanın.
- **Durdurmak için:** Kanalı seçin ve **Stop** seçeneğini kullanın.

### Kanal Özelliklerini Düzenleme
1. Kanalı seçin ve **View Configuration** menüsüne gidin.
2. Özellikleri düzenleyin ve **Save** düğmesine basın.

### Kanalı Sıfırlama ve Çözme
1. Kanalı seçin ve **Advanced** menüsünden **Reset** veya **Resolve** işlemlerini seçin.

### Kanal Silme
1. Kanalı seçin ve **Configure** menüsünden **Delete channel** seçeneğini seçin.

---

## 5. Uygulama Kanalları ile Çalışma

### Kanal Ekleme
1. **Applications** sekmesinden **App Channels** bölümüne gidin.
2. **Create** butonuna tıklayın.
3. Gerekli bilgileri girin ve **Create** düğmesine basın.

### Kanalı Yönetme
- **Başlatma ve Durdurma:** **Start** ve **Stop** seçeneklerini kullanın.
- **Sıfırlama:** Mesaj sırası numarası girerek kanalı sıfırlayın.
- **Ping:** Kanalın iletişim durumunu kontrol edin.

---

## 6. Uygulamalarla Çalışma

### Bağlı Uygulamaları Görüntüleme
1. **Applications** sekmesine gidin.
2. **Connected applications** kısmında bağlı uygulamaları listeleyin.

---

## 7. Depolama Sınıfları ve Sayfa Setleri ile Çalışma

- **Depolama Sınıfı Ekleme:** **Queues** sekmesinde **Storage classes** bölümüne giderek yeni bir sınıf oluşturabilirsiniz.
- **Sayfa Setleri Görüntüleme:** **Queues** sekmesindeki **Page Sets** bölümünden mevcut sayfa setlerini görüntüleyebilirsiniz.

---

# IBM MQ Explorer: Yönetim ve Kullanım Kılavuzu

IBM MQ Explorer, Windows ve Linux x86-64 sistemlerinde çalıştırılarak yerel veya uzaktan IBM MQ yönetimi yapmanıza olanak tanır. Bu araç, grafiksel bir kullanıcı arayüzü (GUI) sunarak IBM MQ nesneleri üzerinde işlem yapmayı kolaylaştırır.

---

## IBM MQ Explorer ile Neler Yapabilirsiniz?

### Temel Yönetim İşlemleri
1. Yerel makinenizde kuyruk yöneticileri oluşturabilir veya silebilirsiniz.
2. Kuyruk yöneticilerini başlatabilir veya durdurabilirsiniz.
3. Kuyruklar ve kanallar gibi IBM MQ nesnelerinin tanımlarını görüntüleyebilir, değiştirebilir ve oluşturabilirsiniz.
4. Kuyruklardaki mesajları görüntüleyebilir ve tarayabilirsiniz.
5. Kanalları başlatabilir, durdurabilir ve durumlarını görüntüleyebilirsiniz.
6. Küme içindeki kuyruk yöneticilerini görüntüleyebilirsiniz.
7. Bir kuyruk yöneticisinin bir kümenin üyesi olup olmadığını kontrol edebilirsiniz.

### Güvenlik ve Sertifikalar
1. **Transport Layer Security (TLS)** kullanarak kanalları güvence altına alabilirsiniz.
2. Yetkilendirme bilgileri nesnesini yönetebilirsiniz.
3. TLS etkinleştirilmiş MQI kanalları ile uzaktan bağlantılar oluşturabilirsiniz.

### Gelişmiş Yönetim
1. Komut sunucuları, kanal başlatıcıları, tetikleyici izleyiciler ve dinleyiciler oluşturabilir veya durdurabilirsiniz.
2. Hizmet izlemeyi başlatabilir veya durdurabilirsiniz.
3. Bir kuyruk yöneticisi kümesi oluşturabilir ve yeni kuyruk yöneticilerini kümeye ekleyebilirsiniz.

### Navigasyon ve Görselleştirme
1. İçerik Görünümleri ve Özellik Diyalogları ile nesneler üzerinde işlem yapabilirsiniz.
2. Eclipse tabanlı bir yapı sunduğu için, kullanıcı arabirimi genişletilebilir.

---

## IBM MQ Explorer Kullanımı

### IBM MQ Explorer'ın Kurulumu
1. IBM MQ Explorer'ı indirmek ve kurmak için **Fix Central**'ı kullanabilirsiniz.
2. Kurulumdan önce aşağıdaki gereksinimlerin karşılandığından emin olun:

```
DEFINE CHANNEL(SYSTEM.ADMIN.SVRCONN) CHLTYPE(SVRCONN)
```

- Her uzaktaki kuyruk yöneticisinde bir komut sunucusunun çalıştığından emin olun.
- TCP/IP dinleyici nesnesinin çalıştığını doğrulayın.
- **SYSTEM.MQEXPLORER.REPLY.MODEL** sistem kuyruğunun mevcut olduğundan emin olun.

### Kuyruk Yöneticilerini Gösterme ve Gizleme
1. **Queue Managers** düğümüne sağ tıklayın ve **Show/Hide Queue Managers** seçeneğini seçin.
2. **Add** düğmesine tıklayın, uzaktaki kuyruk yöneticisinin adını ve IP adresini girin.
3. **Finish** butonuna basarak uzaktaki kuyruk yöneticisini listeye ekleyin.

### Uzaktaki Kuyruk Yöneticisine Bağlanma
1. **Queue Managers** listesinde bir uzaktaki kuyruk yöneticisini seçin.
2. **Connect directly** seçeneğini belirleyin.
3. Kanal tanım tablosunu (**CCDT**) belirtin.
4. **Finish** butonuna basarak bağlantıyı tamamlayın.

---

## Güvenlik Ayarları

### Yetkilendirme Gereklilikleri
Uzaktaki bir kuyruk yöneticisine bağlanmak ve yönetmek için kullanıcı, aşağıdaki yetkilere sahip olmalıdır:
- **CONNECT**, **INQUIRE**, **DISPLAY** yetkileri.
- **SYSTEM.ADMIN.COMMAND.QUEUE** kuyruğuna yazma yetkisi.
- **SYSTEM.MQEXPLORER.REPLY.MODEL** kuyruğuna okuma ve yazma yetkisi.

### TLS Kullanarak Güvenli Bağlantı
1. **Server Connection** ve **Client Connection** kanalları tanımlayın ve **SSLCIPH** özelliğini ayarlayın.
2. CA ve kişisel TLS sertifikalarını uygun dizinlere yerleştirin.
3. IBM MQ Explorer’da **JKS** formatında bir anahtar deposu oluşturun ve bu sertifikaları anahtar deposuna ekleyin.

---

## IBM MQ Explorer'da Küme Üyeliği

1. IBM MQ Explorer, bir kümenin üyesi olan kuyruk yöneticilerini otomatik olarak algılar.
2. Küme üyeliği bilgilerinin doğru gösterilmesi için bir depo kuyruk yöneticisinin adı ve bağlantı adı sağlanmalıdır.

---

## IBM MQ Explorer ile İlgili Notlar

- IBM MQ Explorer büyük kuyruk yöneticileriyle çalışırken yavaşlayabilir.
- Linux'ta birden fazla Eclipse kurulumunuz varsa, IBM MQ Explorer’ı farklı bir kullanıcı **ID**’si ile başlatmanız gerekebilir.


------

# IBM MQ Görev Çubuğu Uygulaması (Sadece Windows)

IBM MQ Görev Çubuğu uygulaması, Windows sunucularda sistem tepsisinde bir simge gösterir ve IBM MQ’nun mevcut durumunu hızlı bir şekilde izlemek ve bazı temel yönetim görevlerini gerçekleştirmek için kullanılabilir.

---

## Sistem Tepsisi Simge Durumları

Görev çubuğundaki IBM MQ simgesi, renk kodlu sembollerle IBM MQ'nun mevcut durumunu gösterir:

- **Yeşil:** Her şey düzgün çalışıyor; herhangi bir uyarı yok.
- **Mavi:** Belirsiz durum; IBM MQ başlatılıyor veya kapatılıyor.
- **Sarı:** Uyarı; bir veya birden fazla hizmet çalışmıyor ya da başarısız olmuş.

---

## IBM MQ Görev Çubuğu Menüsüne Erişim

Menüye erişmek için:
1. Sistem tepsisindeki IBM MQ simgesine sağ tıklayın.
2. Şu seçeneklerden birini seçin:
   - **Open (Aç):** IBM MQ Uyarı İzleyicisini (Alert Monitor) açar.
   - **Exit (Çık):** IBM MQ Görev Çubuğu uygulamasını kapatır.
   - **IBM MQ Explorer:** IBM MQ Explorer'ı açar (grafiksel yönetim aracı).
   - **Stop IBM MQ (IBM MQ’yu Durdur):** IBM MQ hizmetlerini sunucuda durdurur.
   - **About IBM MQ (Hakkında):** IBM MQ Uyarı İzleyicisi ile ilgili bilgileri görüntüler.

---

# IBM MQ Uyarı İzleyicisi (Sadece Windows)

IBM MQ Uyarı İzleyicisi, yerel IBM MQ kurulumunda oluşan hataları tespit eden ve kaydeden bir hata algılama aracıdır.

## Özellikleri:

- **Durum İzleme:** Yerel IBM MQ sunucusunun mevcut durumunu görüntüler.
- **ACPI Desteği:** Windows Gelişmiş Yapılandırma ve Güç Arayüzü (ACPI) ayarlarını izler ve bu ayarların doğru bir şekilde uygulanmasını sağlar.

---

## Uygulama Erişimi:

- **IBM MQ Explorer’a doğrudan erişim sağlar.**
- **Mevcut uyarılarla ilgili bilgileri görüntüler.**
- **Yerel makinedeki IBM MQ hizmetini kapatabilir.**
- **Uyarı mesajlarını ağ üzerinden bir kullanıcı hesabına, Windows iş istasyonuna ya da bir sunucuya yönlendirebilir.**

------

# IBM MQ Yerel Nesneler ile Çalışma

IBM MQ, **Message Queue Interface (MQI)** kullanan uygulama programlarını desteklemek için yerel nesnelerin yönetimini sağlar. Bu yönetim, kuyruk yöneticilerinin başlatılması ve durdurulmasından kuyrukların ve diğer nesnelerin oluşturulması, görüntülenmesi, değiştirilmesi ve silinmesine kadar bir dizi işlemi kapsar.

---

## **Kuyruk Yöneticileri ile Çalışma**

### **Kuyruk Yöneticisini Başlatma**

#### 1. Komutla Başlatma:
- `strmqm <Kuyruk_Yöneticisi_Adı>` komutunu kullanarak kuyruk yöneticisini başlatabilirsiniz.  
- **Örnek:**
  ```bash
  strmqm QMB
  ```
  Bu komut, kuyruk yöneticisini başlatır ve bağlantı isteklerini kabul etmeye hazır hale getirir.

#### 2. IBM MQ Explorer ile Başlatma (Windows ve Linux):
1. **IBM MQ Explorer**'ı açın.  
2. **Navigator** görünümünden kuyruk yöneticisini seçin.  
3. **Başlat (Start)** seçeneğine tıklayın.

---

### **Kuyruk Yöneticisini Durdurma**

Kuyruk yöneticisini durdurmak için `endmqm` komutunu kullanabilirsiniz.  

#### 1. Kontrollü Durdurma (Quiesce):
- Tüm uygulamaların işlemlerini tamamlamasını bekler.  
- **Örnek:**
  ```bash
  endmqm QMB
  ```

#### 2. Hızlı Durdurma (Immediate):
- Mevcut işlemler tamamlanır ancak yeni çağrılar kabul edilmez.  
- **Örnek:**
  ```bash
  endmqm -i QMB
  ```

#### 3. Zorunlu Durdurma (Preemptive):
- Kuyruk yöneticisini hemen durdurur. Sadece diğer yöntemler başarısız olduğunda kullanılmalıdır.  
- **Örnek:**
  ```bash
  endmqm -p QMB
  ```

#### 4. Bekleyerek Durdurma (Wait):
- Kuyruk yöneticisi tamamen durduğunda kontrol size döner.  
- **Örnek:**
  ```bash
  endmqm -w QMB
  ```

---

### **Manuel Durdurma**

Eğer yukarıdaki yöntemler çalışmıyorsa, **manüel durdurma** gerçekleştirilir:

#### 1. Windows İçin:
- **Görev Yöneticisi** veya `taskkill` komutunu kullanarak aşağıdaki işlemleri sırayla sonlandırın:
  - **AMQZMUC0**: Kritik işlem yöneticisi  
  - **AMQZXMA0**: Uygulama çalıştırıcı  
  - **RUNMQLSR**: Kanal dinleyicisi  

#### 2. Linux/AIX İçin:
- Çalışan işlemleri bulun:
  ```bash
  ps -ef | grep <Kuyruk_Yöneticisi_Adı>
  ```
- İşlemleri sonlandırın:
  ```bash
  kill -9 <PID>
  ```
- İşlemleri şu sırayla kapatın:
  - **amqzmuc0**: Kritik işlem yöneticisi  
  - **amqzmgr0**: İşlem yöneticisi  
  - **runmqlsr**: Kanal dinleyicisi  

---

## **MQI Kanallarını Durdurma**

Bir `STOP CHANNEL` komutu verildiğinde, istemci bağlantı kanalını durdurmak için aşağıdaki modlardan birini seçebilirsiniz:

### 1. **Quiesce (Bekle ve Durdur):**
- Mevcut mesajların işlenmesi tamamlandıktan sonra kanalı durdurur.

### 2. **Force (Zorla):**
- Kanalı hemen durdurur; ancak mevcut işlemlerin tamamlanmasına izin verir.

### 3. **Terminate (Sonlandır):**
- Kanal işlemini veya iş parçacığını hemen durdurur. Bu, istemcide bağlantı hatasına neden olabilir.

> **Önemli:**  
> İstemci, `MQRC_CONNECTION_QUIESCING` veya `MQRC_CONNECTION_BROKEN` hata kodlarını alabilir.  
> - **Quiesce modunda:** İstemci mevcut işlemi tamamlamalı ve düzgün şekilde çıkmalıdır.  
> - **Terminate modunda:** Bağlantı ani olarak kesilir.

---

## **Kuyruk Yöneticisi Parametrelerini Görüntüleme ve Değiştirme**

### 1. **Parametreleri Görüntüleme:**
- `DISPLAY QMGR` komutu ile kuyruk yöneticisi parametrelerini görüntüleyin.
- **Örnek Çıktı:**
  ```bash
  DISPLAY QMGR
  QMNAME(QM1) DEADQ(SYSTEM.DEAD.LETTER.QUEUE)
  ```

### 2. **Parametreleri Değiştirme:**
- `ALTER QMGR` komutuyla parametreleri değiştirin.
- **Örnek:**
  ```bash
  ALTER QMGR DEADQ(NEW.DEAD.LETTER.QUEUE)
  ```

--------


# IBM MQ Yerel Kuyruklarla Çalışma (Working with Local Queues)

IBM MQ, mesajlaşma sisteminde kuyruklar üzerinde çeşitli işlemler yapmaya olanak tanır. Bu bölümde yerel kuyrukları tanımlama, güncelleme, temizleme, silme ve özniteliklerini görüntüleme gibi temel işlemlere yönelik detaylı açıklamalar yer almaktadır.

## Yerel Kuyruk Tanımlama: DEFINE QLOCAL
Bir uygulama için yerel kuyruk yöneticisi, uygulamanın bağlı olduğu kuyruk yöneticisidir. Yerel kuyruk yöneticisi tarafından yönetilen kuyruklar, bu kuyruk yöneticisine “yerel” olarak kabul edilir. Yerel bir kuyruk oluşturmak için `DEFINE QLOCAL` komutu kullanılır.

### Örnek Komut:
Aşağıdaki örnekte, `ORANGE.LOCAL.QUEUE` adında bir yerel kuyruk oluşturulmuştur:
```
DEFINE QLOCAL(ORANGE.LOCAL.QUEUE) + 
       DESCR('Queue for messages from other systems') + 
       PUT(ENABLED) + 
       GET(ENABLED) + 
       NOTRIGGER + 
       MSGDLVSQ(PRIORITY) + 
       MAXDEPTH(5000) + 
       MAXMSGL(4194304) + 
       USAGE(NORMAL)
```

### Önemli Noktalar:
- **PUT(ENABLED)** ve **GET(ENABLED)**: Kuyruğun mesaj alıp gönderebilmesini etkinleştirir.
- **MAXDEPTH(5000)**: Kuyrukta maksimum 5000 mesaj bulunabilir.
- **MAXMSGL(4194304)**: Mesaj başına maksimum uzunluk 4 MB olarak ayarlanır.
- **NOTRIGGER**: Bu kuyruk tetikleyici mesaj oluşturmaz.

Eğer aynı isimde bir kuyruk zaten mevcutsa, **REPLACE** özelliği kullanılarak mevcut tanımın üzerine yazılabilir:
```
DEFINE QLOCAL(ORANGE.LOCAL.QUEUE) MAXDEPTH(10000) REPLACE
```

## Varsayılan Nesne Özniteliklerini Görüntüleme: DISPLAY QUEUE
Bir IBM MQ nesnesi tanımlandığında, belirtilmeyen öznitelikler varsayılan nesneden (**SYSTEM.DEFAULT.LOCAL.QUEUE**) alınır. Varsayılan öznitelikleri görüntülemek için **DISPLAY QUEUE** komutu kullanılır.

### Örnek Komut:
```
DISPLAY QUEUE(SYSTEM.DEFAULT.LOCAL.QUEUE)
```

### Belirli Öznitelikleri Görüntüleme:
```
DISPLAY QUEUE(ORANGE.LOCAL.QUEUE) MAXDEPTH MAXMSGL CURDEPTH;
```

### Çıktı:
```
AMQ8409: Display Queue details. 
QUEUE(ORANGE.LOCAL.QUEUE) TYPE(QLOCAL)
CURDEPTH(0) MAXDEPTH(5000) MAXMSGL(4194304)
```
- **CURDEPTH**: Kuyruktaki mesaj sayısı.
- **MAXDEPTH**: Kuyruğun maksimum kapasitesi.
- **MAXMSGL**: Mesaj başına maksimum uzunluk.

## Kuyruk Tanımını Kopyalama: DEFINE QLOCAL WITH LIKE
Bir kuyruğun tanımını kopyalamak için **LIKE** özelliği kullanılabilir.

### Örnek Komut:
```
DEFINE QLOCAL(MAGENTA.QUEUE) LIKE(ORANGE.LOCAL.QUEUE)
```
Bu komut, `ORANGE.LOCAL.QUEUE` ile aynı özniteliklere sahip bir kuyruk oluşturur.

Bir kuyruğun özniteliklerini kopyalarken değiştirmek için:
```
DEFINE QLOCAL(THIRD.QUEUE) + 
LIKE(ORANGE.LOCAL.QUEUE) + 
MAXMSGL(1024)
```

## Kuyruk Özniteliklerini Değiştirme: ALTER QLOCAL ve REPLACE
Kuyruk öznitelikleri iki yolla değiştirilebilir:
1. **ALTER QLOCAL** komutu kullanarak:
```
ALTER QLOCAL(ORANGE.LOCAL.QUEUE) MAXMSGL(10000)
```
2. **DEFINE QLOCAL REPLACE** komutuyla:
```
DEFINE QLOCAL(ORANGE.LOCAL.QUEUE) MAXMSGL(10000) REPLACE
```

## Kuyruğu Temizleme: CLEAR QLOCAL
Bir yerel kuyruğu temizlemek (tüm mesajları silmek) için **CLEAR QLOCAL** komutu kullanılır. Bu işlemi yaparken dikkatli olunmalıdır, çünkü bu komut herhangi bir uyarı vermez ve tüm mesajlar kalıcı olarak silinir.

### Örnek Komut:
```
CLEAR QLOCAL(MAGENTA.QUEUE)
```

## Kuyruğu Silme: DELETE QLOCAL
Bir yerel kuyruğu silmek için **DELETE QLOCAL** komutu kullanılır.

### Örnek Komutlar:
1. Kuyruk boş ise:
```
DELETE QLOCAL(PINK.QUEUE) NOPURGE
```
2. Kuyrukta taahhüt edilmiş mesajlar olsa bile:
```
DELETE QLOCAL(PINK.QUEUE) PURGE
```

## Kuyruğun Mesajlarını Gözden Geçirme: Sample Queue Browser
IBM MQ, kuyruğunda bulunan mesajları incelemek için bir örnek program sunar.

### Komut:
```
amqsbcg SYSTEM.ADMIN.QMGREVENT.tpp01 saturn.queue.manager
```

## Büyük Kuyrukları Etkinleştirme
IBM MQ, 2 TB'ı aşan kuyrukları destekler. AIX ve Linux sistemlerinde büyük dosya desteğini etkinleştirmek için ek ayarlar yapılması gerekebilir.

### MAXFSIZE Atama:
Kuyruk dosyasının maksimum boyutunu ayarlamak için **MAXFSIZE** özelliği kullanılır:
```
DEFINE QLOCAL(LARGEQUEUE) MAXFSIZE(5242880)
```
Bu komut, 5 TB büyüklüğünde bir kuyruk tanımlar.

-----------

IBM MQ Remote Kuyruklarla Çalışma

Remote (uzak) kuyruk, yerel bir kuyruk yöneticisindeki bir tanımdır ve bu tanım başka bir kuyruk yöneticisindeki bir kuyruğa işaret eder. Remote kuyruklar, uygulamaların uzak bir kuyruğa erişim sağlamak için yerel bir ad kullanmasına olanak tanır. Bu, uygulamaların uzak kuyruk yöneticisinin kimliğini belirtmeden, yalnızca yerel bir adla kuyruğa erişmesini sağlar.

Uzaktan Kuyruk Tanımları ve Temel Kullanımlar
	1. Yerel Kuyruk Tanımından Remote Kuyruğa Erişim:
		○ Uygulama bir MQOPEN çağrısı yapar ve uzak kuyruğun yerel tanımını kullanır.
		○ Kuyruk yöneticisi, mesajı hedef kuyruğa yönlendirmek için uzak kuyruk ve kuyruk yöneticisinin adını bir iletim başlığına ekler.
	2. Remote Kuyruk Tanımı Oluşturma: Aşağıdaki komutla bir remote kuyruk tanımı yapılabilir:


DEFINE QREMOTE (CYAN.REMOTE.QUEUE) +
DESCR('Şubelerden gelen sigorta talepleri için kuyruk') +
RNAME(AUTOMOBILE.INSURANCE.QUOTE.QUEUE) +
RQMNAME(jupiter.queue.manager) +
XMITQ(INQUOTE.XMIT.QUEUE)
		○ QREMOTE: Yerel kuyruğun adı.
		○ DESCR: Kuyruğun kullanım amacını açıklayan açıklama.
		○ RNAME: Uzak kuyruğun adı.
		○ RQMNAME: Uzak kuyruk yöneticisinin adı.
		○ XMITQ: Mesajların taşınacağı iletim kuyruğunun adı (isteğe bağlıdır).
	3. Remote Kuyruğa Mesaj Gönderimi: Uygulama, MQPUT çağrısını yaparak mesajı remote kuyruğa gönderir. Bu işlem sırasında uzak kuyruk tanımını veya tam kuyruk adını kullanabilir.
	4. Diğer Komutlar:
		○ Kuyruğun özelliklerini görüntülemek için:

DISPLAY QUEUE (CYAN.REMOTE.QUEUE)
		○ Kuyruğu mesaj gönderimine açmak için:

ALTER QREMOTE (CYAN.REMOTE.QUEUE) PUT(ENABLED)
		○ Remote kuyruk tanımını silmek için:

DELETE QREMOTE (CYAN.REMOTE.QUEUE)

Remote Kuyruk Tanımları ile Alias (Takma Ad) Kullanımı
Remote kuyruk tanımları aşağıdaki durumlarda alias olarak kullanılabilir:
	• Kuyruk Yöneticisi Aliasları: Mesaj hedefini değiştirmek için remote kuyruk tanımları kullanılabilir. Bu, gönderici uygulamanın farkında olmadan hedef kuyruk yöneticisinin adını değiştirmesini sağlar.
	• Cevap Kuyruğu Aliasları: İstemci, gönderdiği bir mesaj için cevap kuyruğu olarak alias kullanabilir. Bu, cevapların gönderileceği kuyruğun ismini ve yolunu kontrol etmeyi sağlar.

IBM MQ Alias Kuyruklarla Çalışma
Alias kuyruk, dolaylı olarak başka bir kuyruğa veya konuya işaret eden bir tanımdır. Alias kuyruk gerçek bir kuyruk değildir; bir uygulama MQOPEN çağrısı yaptığında, alias kuyruk hedef kuyruğa çözülür.
	1. Alias Kuyruk Tanımı: Alias bir kuyruk tanımı şu şekilde oluşturulabilir:

DEFINE QALIAS (MY.ALIAS.QUEUE) TARGET (YELLOW.QUEUE)
		○ QALIAS: Alias kuyruğun adı.
		○ TARGET: Alias kuyruğun işaret ettiği hedef kuyruk.
Örnek olarak, alias kuyruk başka bir kuyruğa yönlendirilebilir:

ALTER QALIAS (MY.ALIAS.QUEUE) TARGET (MAGENTA.QUEUE)
	2. Farklı Uygulamalar için Farklı Aliaslar: Alias kuyruklar farklı uygulamalara özel erişim hakları tanımlamak için kullanılabilir:
		○ Uygulama A yalnızca mesaj gönderebilir:

DEFINE QALIAS (ALPHAS.ALIAS.QUEUE) TARGET(YELLOW.QUEUE) PUT(ENABLED) GET(DISABLED)
		○ Uygulama B yalnızca mesaj alabilir:

DEFINE QALIAS (BETAS.ALIAS.QUEUE) TARGET(YELLOW.QUEUE) PUT(DISABLED) GET(ENABLED)
	3. Alias Kuyruklar ile Komutlar:
		○ Alias kuyruğun özelliklerini görüntülemek için:

DISPLAY QALIAS (MY.ALIAS.QUEUE)
		○ Alias kuyruğu silmek için:

DELETE QALIAS (MY.ALIAS.QUEUE)

IBM MQ Model Kuyruklarla Çalışma

Model kuyruklar, uygulamalar tarafından dinamik kuyruklar oluşturmak için kullanılan şablonlardır. Bir uygulama bir model kuyruğa mesaj gönderdiğinde, kuyruk yöneticisi dinamik bir kuyruk oluşturur.
	1. Model Kuyruk Tanımı:

DEFINE QMODEL (GREEN.MODEL.QUEUE) +
DESCR('Uygulama X için kuyruk') +
PUT(DISABLED) GET(ENABLED) +
DEFTYPE(PERMDYN)
		○ DEFTYPE: Kuyruğun geçici mi (TEMPDYN), kalıcı mı (PERMDYN) olduğunu belirler.
	2. Model Kuyruklarla Çalışma:
		○ Model kuyruğun özelliklerini görüntülemek için:

DISPLAY QUEUE (GREEN.MODEL.QUEUE)
		○ Model kuyruğu düzenlemek için:

ALTER QMODEL (BLUE.MODEL.QUEUE) PUT(ENABLED)
		○ Model kuyruğu silmek için:

DELETE QMODEL (RED.MODEL.QUEUE)


--------

IBM MQ Dead-Letter Queues (DLQ) ile Çalışma

Dead-letter queue (DLQ), bir kuyruk yöneticisinde hedefe ulaştırılamayan mesajların saklandığı yerel bir kuyruktur. Bu kuyruk, mesajların daha sonra işlenmek üzere depolanmasını sağlar. DLQ kullanımı, mesajların teslim sırasını etkileyebilir; bu nedenle bazı durumlarda DLQ kullanımını tercih etmeyebilirsiniz.

Dead-Letter Queue Kullanımının Temelleri
	1. DLQ Tanımı:
		○ IBM MQ, her kuyruk yöneticisi için varsayılan bir DLQ sağlar: SYSTEM.DEAD.LETTER.QUEUE.
		○ DLQ, yerel bir kuyruk olmalıdır ve MAXMSGL (maksimum mesaj uzunluğu) özelliği, en büyük mesaj boyutunu ve MQDLH (dead-letter header) boyutunu karşılayacak şekilde ayarlanmalıdır.
	2. DLQ Kullanımı ve Yapılandırma:
		○ Bir DLQ tanımlamak veya değiştirmek için ALTER QMGR komutunu kullanabilirsiniz:
        ALTER QMGR DEADQ(DEAD.LETTER.QUEUE)
    	○ DLQ üzerinden işlenecek mesajların nasıl yönetileceğini belirlemek için USEDLQ özelliği yapılandırılır. Bu özellik, DLQ’nun hangi koşullarda kullanılacağını belirler.
	3. DLQ Üzerindeki Mesajları İşleme:
		○ IBM MQ, mesajları işlemek için runmqdlq adlı bir DLQ handler sağlar.
		○ Handler, DLQ üzerindeki mesajları bir kurallar tablosuyla eşleştirerek işler.
		○ Handler’ı çalıştırmak için aşağıdaki komut kullanılır:

runmqdlq DEAD.LETTER.QUEUE QUEUE.MANAGER <rules.rul

DLQ Handler ve Kurallar Tablosu
DLQ handler, kurallar tablosu kullanılarak mesajları işler. Bu tablo iki ana bölümden oluşur:
	1. Kontrol Verisi:
		○ DLQ ve kuyruk yöneticisinin adı gibi genel ayarları içerir.
		○ Örnek:

INPUTQ(DEAD.LETTER.QUEUE)
INPUTQM(QUEUE.MANAGER)
RETRYINT(60)
WAIT(YES)
	2. Kurallar:
		○ DLQ üzerindeki mesajların belirli desenlerle eşleşmesini ve işlem yapılmasını sağlar.
		○ Örnek bir kural:

REASON(MQRC_Q_FULL) ACTION(RETRY) RETRY(5)

DLQ Handler ile İşlem Adımları
	1. DLQ Handler Çalıştırma:
		○ Handler, kurallar tablosuna göre işlem yapar. İlk kuraldan başlayarak eşleşen bir desen bulur ve işlem yapar.
		○ Bir kuralın işlemi başarısız olursa RETRY değeri kadar tekrar denenir.
	2. DLQ Handler Kullanımına Örnek: Aşağıdaki kurallar tablosu örneği, DLQ üzerindeki belirli durumlar için farklı işlemler yapar:

REASON(MQRC_Q_FULL) ACTION(RETRY) RETRY(5)
REASON(MQRC_PUT_INHIBITED) ACTION(RETRY) RETRY(3)
REPLYQM(REMOTEQM) ACTION(FWD) FWDQ(DEADQ)
	3. Kuralların Genel Yapısı:
		○ Desen (Pattern): Mesajın hangi koşullarda eşleşeceğini belirtir. Örneğin, REASON ile hata kodları eşleştirilebilir.
		○ Eylem (Action): Mesaj eşleştiğinde ne yapılacağını belirler:
			§ DISCARD: Mesajı sil.
			§ IGNORE: Mesajı DLQ’da bırak.
			§ RETRY: Mesajı belirtilen sayıda tekrar dene.
			§ FWD: Mesajı başka bir kuyruğa yönlendir.

DLQ Handler Örnekleri
	1. DLQ’dan Mesajları İletme:
		○ Belirli bir DLQ'daki mesajları başka bir kuyruğa yönlendirmek:

REASON(MQRC_Q_FULL) ACTION(FWD) FWDQ(DEST.QUEUE)
	2. Manuel Müdahale için Kuyruk Oluşturma:
		○ İşlenemeyen mesajları manuel müdahale kuyruğuna yönlendirme:

ACTION(FWD) FWDQ(MANUAL.INTERVENTION.QUEUE)
	3. Mesajları Silme:
		○ Belirli bir koşula uyan mesajları DLQ’dan silme:

PERSIST(MQPER_NOT_PERSISTENT) ACTION(DISCARD)

DLQ Kullanımı için Öneriler
	• DLQ’da mümkün olduğunca az mesaj tutun. Mesajlar birikirse DLQ dolabilir ve iş yükü artar.
	• Herhangi bir mesajı işlemeyen kurallar için son bir “catch-all” kuralı ekleyin. Örneğin:

ACTION(FWD) FWDQ(REALLY.DEAD.QUEUE)


------------

IBM MQ Yönetimsel Konularla Çalışma

Yönetimsel konular (administrative topics), IBM MQ'nun yayınla/abone ol (publish/subscribe) modeli ile çalışmasını düzenleyen yapılar sağlar. MQSC komutları kullanılarak bu konuların oluşturulması, görüntülenmesi, değiştirilmesi, kopyalanması ve silinmesi yönetilebilir.

Yönetimsel Konu Tanımlama
Kullanım: DEFINE TOPIC komutunu kullanarak bir yönetimsel konu oluşturabilirsiniz. Herhangi bir özellik açıkça belirtilmediğinde, özellikler sistem varsayılan yönetimsel konusundan (SYSTEM.DEFAULT.TOPIC) devralınır.
Örnek: Aşağıdaki örnek, ORANGE.TOPIC adında bir konu tanımlar:


DEFINE TOPIC (ORANGE.TOPIC) +
TOPICSTR (ORANGE) +
DEFPRTY(ASPARENT) +
NPMSGDLV(ASPARENT)
Notlar:
	• TOPICSTR: Bu konunun yayınlama sırasında kullanılacak dize adıdır.
	• DEFPRTY(ASPARENT) ve NPMSGDLV(ASPARENT): Üst konunun varsayılan ayarlarını devralır.
	• Zaten aynı ada sahip bir konu varsa, REPLACE özniteliği ile eski tanım üzerine yazabilirsiniz.

Yönetimsel Konu Özelliklerini Görüntüleme
DISPLAY TOPIC komutu, yönetimsel bir konunun özelliklerini görüntüler.
Tüm özellikleri görüntülemek:


DISPLAY TOPIC (ORANGE.TOPIC)
Belirli özellikleri görüntülemek:


DISPLAY TOPIC (ORANGE.TOPIC) +
TOPICSTR +
DEFPRTY +
NPMSGDLV
Sonuç:


AMQ8633: Display topic details.
TOPIC(ORANGE.TOPIC)                                         TYPE(LOCAL)
TOPICSTR(ORANGE)                                            DEFPRTY(ASPARENT)
NPMSGDLV(ASPARENT)
Varsayılan ayarları görüntülemek için şu komutu kullanabilirsiniz:


DISPLAY TOPIC(SYSTEM.DEFAULT.TOPIC)

Yönetimsel Konu Özelliklerini Değiştirme
Konunun özelliklerini ALTER TOPIC veya DEFINE TOPIC ... REPLACE komutlarıyla değiştirebilirsiniz.
Örnekler:
	1. Bir özelliği değiştirme:


ALTER TOPIC(ORANGE.TOPIC) DEFPRTY(5)

Bu komut, yalnızca DEFPRTY (varsayılan öncelik) özelliğini değiştirir.
	2. Tüm özellikleri varsayılanlara döndürme ve yeni değer atama:


DEFINE TOPIC(ORANGE.TOPIC) DEFPRTY(5) REPLACE

Yönetimsel Konu Tanımını Kopyalama
Bir konu tanımını LIKE özniteliğiyle kopyalayabilirsiniz.
Örnekler:
	1. Aynı özelliklerle yeni bir konu oluşturma:


DEFINE TOPIC(MAGENTA.TOPIC) +
LIKE(ORANGE.TOPIC)
	2. Kopyalama sırasında değişiklik yapma:


DEFINE TOPIC(BLUE.TOPIC) +
TOPICSTR(BLUE) +
LIKE(ORANGE.TOPIC)
	3. Kopyalama sırasında USEDLQ özelliğini değiştirme:


DEFINE TOPIC(GREEN.TOPIC) +
TOPICSTR(GREEN) +
LIKE(BLUE.TOPIC) +
USEDLQ(NO)

Yönetimsel Konu Tanımını Silme
DELETE TOPIC komutunu kullanarak bir yönetimsel konuyu silebilirsiniz.
Örnek:


DELETE TOPIC(ORANGE.TOPIC)
Notlar:
	• Silinen bir konu artık yeni abonelikler veya yayınlar için kullanılamaz.
	• Ancak, zaten açık olan abonelikler çalışmaya devam eder ve yayıncılar mevcut yayın dizesini kullanarak yayın yapabilir.

Yönetimsel Konuların Kullanımında Öneriler
	1. Varsayılan Konuları İnceleyin: Yeni konuları tanımlarken SYSTEM.DEFAULT.TOPIC değerlerini inceleyerek gereksinimlerinizi karşılayan varsayılan ayarları kullanabilirsiniz.
	2. Düzenli Güncelleme: ALTER komutuyla konuları ihtiyaçlara göre güncelleyin.
	3. Temiz Adlandırma: Her konunun yayın dizesini (TOPICSTR) açıklayıcı ve mantıklı bir şekilde adlandırın. Bu, yöneticiler ve geliştiriciler için kolaylık sağlar.
	4. Yedekleme ve Geri Yükleme: Konu tanımlarını düzenlemeden önce mevcut ayarların yedeğini alın. Örneğin, DISPLAY komutlarını kullanarak tüm özellikleri bir dosyaya kaydedebilirsiniz.


------

IBM MQ Aboneliklerle Çalışma

IBM MQ'da abonelikler, yayınlama/abone ol (publish/subscribe) modeli ile çalışmayı kolaylaştırır. Abonelikler, belirli bir konuya yayınlanan mesajları alacak bir mekanizma sağlar. MQSC komutları kullanılarak bu abonelikler oluşturulabilir, görüntülenebilir, değiştirilebilir, kopyalanabilir ve silinebilir.

Abonelik Türleri
Abonelikler, SUBTYPE özelliği ile tanımlanan üç türden biri olabilir:
	1. ADMIN: Kullanıcı tarafından yönetimsel olarak tanımlanır.
	2. PROXY: İki kuyruk yöneticisi arasında yayın yönlendirmek için otomatik oluşturulur.
	3. API: Programatik olarak, örneğin MQI MQSUB çağrısıyla oluşturulur.

Yönetimsel Abonelik Tanımlama
DEFINE SUB komutu, yönetimsel bir abonelik tanımlamak için kullanılır. Varsayılan özellikler SYSTEM.DEFAULT.SUB adlı varsayılan abonelik nesnesinden devralınır.
Örnek:

DEFINE SUB(ORANGE) +
       TOPICSTR(ORANGE) +
       DESTCLAS(PROVIDED) +
       DEST(SUBQ) +
       EXPIRY(UNLIMITED) +
       PUBPRTY(ASPUB)
Notlar:
	• TOPICSTR(ORANGE): Bu abonelik ORANGE konusundaki yayınları alır.
	• DEST(SUBQ): Bu abonelikle eşleştirilen mesajlar SUBQ kuyruğuna iletilir. SUBQ kuyruğu önceden tanımlanmış olmalıdır.
	• EXPIRY(UNLIMITED): Abonelik süresizdir.
	• PUBPRTY(ASPUB): Mesajlar, yayıncı tarafından atanan öncelikle iletilir.
	• Aynı isimde bir abonelik varsa REPLACE özniteliği ile üzerine yazabilirsiniz.

Abonelik Özelliklerini Görüntüleme
DISPLAY SUB komutu, abonelikle ilişkili özellikleri görüntüler.
Tüm Özellikleri Görüntüleme:

DISPLAY SUB(ORANGE)
Belirli Özellikleri Görüntüleme:

DISPLAY SUB(ORANGE) +
       SUBID +
       TOPICSTR +
       DURABLE
Sonuç:

AMQ8096: IBM MQ subscription inquired.
     SUBID(414D5120414141202020202020202020EE921E4E20002A03)
     SUB(ORANGE)                                                             TOPICSTR(ORANGE)
     DURABLE(YES)
SUBID, kuyruk yöneticisi tarafından atanmış benzersiz bir abonelik kimliğidir. Bu, uzun veya karmaşık isimlere sahip aboneliklerde faydalıdır.
Abonelik Durumunu Görüntüleme:

DISPLAY SBSTATUS(ORANGE) NUMMSGS
Sonuç olarak şu değer görüntülenir:

AMQ8099: IBM MQ subscription status inquired.
   SUB(ORANGE)
   SUBID(414D5120414141202020202020202020EE921E4E20002A03)
   NUMMSGS(0)

Abonelik Özelliklerini Değiştirme
Abonelik özelliklerini ALTER SUB veya DEFINE SUB ... REPLACE komutlarıyla değiştirebilirsiniz.
Örnekler:
	1. Tek bir özelliği değiştirme:

ALTER SUB(ORANGE) PUBPRTY(5)

Bu komut, mesajların önceliğini 5 olarak değiştirir.
	2. Tüm özellikleri varsayılana döndürerek değiştirme:

DEFINE SUB(ORANGE) PUBPRTY(5) REPLACE

Abonelik Tanımını Kopyalama
Bir abonelik tanımını LIKE özniteliğiyle kopyalayabilirsiniz.
Örnek:

DEFINE SUB(BLUE) +
       LIKE(ORANGE)

Abonelik Silme
DELETE SUB komutuyla bir aboneliği silebilirsiniz.
Örnek:

DELETE SUB(ORANGE)
Abonelik Kimliğiyle Silme:

DELETE SUB SUBID(414D5120414141202020202020202020EE921E4E20002A03)

Abonelik Mesajlarını Kontrol Etme
Bir abonelik tanımlandığında, bu abonelikle eşleştirilen mesajlar bir kuyruğa iletilir.
	1. Abonelikteki mevcut mesaj sayısını kontrol edin:

DISPLAY SBSTATUS(ORANGE) NUMMSGS
	2. Mesajları kuyruğunda görüntülemek için şu komutu kullanın:

DISPLAY SUB(ORANGE) DEST
	3. Kuyruk mesajlarını incelemek için amqsbcg gibi bir örnek program kullanabilirsiniz.

Öneriler
	1. Varsayılan Abonelikleri İnceleyin: Yeni abonelikler oluştururken SYSTEM.DEFAULT.SUB varsayılan değerlerini göz önünde bulundurun.
	2. Abonelikleri Yönetimsel Olarak İzleyin: DISPLAY SBSTATUS komutuyla aboneliklerin durumunu düzenli olarak izleyin.
	3. Temiz Adlandırma: Abonelik isimlerini ve bağlı kuyruğu anlamlı şekilde adlandırarak yönetimi kolaylaştırın.


------

IBM MQ Hizmetlerle Çalışma
IBM MQ'da hizmet nesneleri, bir kuyruk yöneticisinin bir parçası olarak ek işlemleri yönetmek için kullanılır. Hizmet nesneleri, bir kuyruk yöneticisi başladığında ve durduğunda programları başlatıp durdurmak için tanımlanabilir.

Hizmet Nesnesi Türleri
	1. Server Hizmeti (SERVER):
		○ Uzun süreli çalışması beklenen programları çalıştırır. Örneğin, bir tetikleme monitörü (runmqtrm) gibi.
		○ Sadece bir örneği aynı anda çalışabilir.
		○ Durum bilgisi DISPLAY SVSTATUS komutuyla izlenebilir.
	2. Komut Hizmeti (COMMAND):
		○ Kısa süreli veya birden çok örneği aynı anda çalışabilen programları çalıştırır.
		○ Örneğin, kuyruk yöneticisi başladığında sistem günlüğüne bilgi yazan bir program.
		○ Durum bilgisi DISPLAY SVSTATUS ile izlenemez.

Hizmet Nesnesi Tanımlama
DEFINE SERVICE komutuyla bir hizmet nesnesi tanımlanabilir.
Gerekli Parametreler:
	• SERVTYPE: Hizmet türünü belirtir (SERVER veya COMMAND).
	• STARTCMD: Başlatılacak programın tam yolu.
	• STARTARG: Program için başlangıç argümanları.
	• STDOUT: Standart çıktı için yönlendirilecek dosya.
	• STDERR: Standart hata için yönlendirilecek dosya.
	• STOPCMD: Hizmeti durduracak programın tam yolu.
	• STOPARG: Durdurma programı için argümanlar.
	• CONTROL: Hizmetin nasıl başlatılıp durdurulacağını belirtir.
		○ MANUAL: Manuel başlatma/durdurma.
		○ QMGR: Kuyruk yöneticisiyle birlikte başlatılıp durdurulur.
		○ STARTONLY: Sadece kuyruk yöneticisiyle birlikte başlatılır, durdurulmaz.
Örnek Tanım:

DEFINE SERVICE(S1) +
CONTROL(QMGR) +
SERVTYPE(SERVER) +
STARTCMD('/opt/mqm/bin/runmqtrm') +
STARTARG('-m +QMNAME+ -q ACCOUNTS.INITIATION.QUEUE') +
STOPCMD('/opt/mqm/bin/amqsstop') +
STOPARG('-m +QMNAME+ -p +MQ_SERVER_PID+')

Hizmetleri Yönetme
Hizmet nesneleri otomatik veya manuel olarak başlatılabilir/durdurulabilir.
Manuel Başlatma ve Durdurma:

START SERVICE(S1)
STOP SERVICE(S1)
Durum Görüntüleme:

DISPLAY SVSTATUS(S1)

Hizmet Ortam Değişkenlerini Tanımlama
Hizmetler, kuyruk yöneticisinin ortamını devralır ancak service.env dosyası kullanılarak ek değişkenler tanımlanabilir.
Dosya Konumları:
	• Makine genelinde değişkenler:
		○ Linux: /var/mqm/service.env
		○ Windows: C:\ProgramData\IBM\MQ\service.env
	• Kuyruk yöneticisi özelinde değişkenler:
		○ Linux: /var/mqm/qmgrs/<QMNAME>/service.env
		○ Windows: C:\ProgramData\IBM\MQ\qmgrs\<QMNAME>\service.env
Örnek service.env Dosyası:

MYLOC=/opt/myloc/bin
MYTMP=/tmp
TRACEDIR=/tmp/trace
MYINITQ=ACCOUNTS.INITIATION.QUEUE

Değiştirilebilir Yer Tutucular (Replaceable Inserts)
Hizmet tanımlarında belirli yer tutucular kullanılabilir. Bu yer tutucular çalıştırma sırasında gerçek değerlere dönüştürülür.
Kullanılabilir Yer Tutucular:
	• +MQ_INSTALL_PATH+: IBM MQ'nun kurulum yolu.
	• +QMNAME+: Kuyruk yöneticisi adı.
	• +MQ_SERVER_PID+: Hizmet tarafından çalıştırılan işlemin PID'si.

Trigger Monitörü Başlatma Örneği
Bir kuyruk yöneticisi başladığında tetikleme monitörünü başlatmak için aşağıdaki tanım yapılabilir:

DEFINE SERVICE(TRIG_MON_START) +
CONTROL(QMGR) +
SERVTYPE(SERVER) +
STARTCMD('runmqtrm') +
STARTARG('-m +QMNAME+ -q ACCOUNTS.INITIATION.QUEUE')

Hizmet Örnekleri
	1. Server Hizmeti Tanımı:

DEFINE SERVICE(S1) +
CONTROL(QMGR) +
SERVTYPE(SERVER) +
STARTCMD('/usr/local/bin/my_server') +
STARTARG('-config /etc/myconfig.conf') +
STDOUT('/var/log/my_server.out') +
STDERR('/var/log/my_server.err')
	2. Komut Hizmeti Tanımı:

DEFINE SERVICE(S2) +
CONTROL(QMGR) +
SERVTYPE(COMMAND) +
STARTCMD('/usr/bin/logger') +
STARTARG('Queue manager +QMNAME+ starting') +
STOPCMD('/usr/bin/logger') +
STOPARG('Queue manager +QMNAME+ stopping')

Öneriler
	• Durum İzleme: DISPLAY SVSTATUS komutuyla uzun süreli hizmetlerin durumunu izleyin.
	• Ortam Değişkenleri: service.env dosyasını kullanarak ortam değişkenlerini yönetin.
	• Yer Tutucular: Hizmet tanımlarında esneklik sağlamak için yer tutucuları kullanın.

-------
IBM MQ'da CAPEXPRY Kullanımı
CAPEXPRY, bir kuyruğa veya konuya gönderilen mesajların son kullanma sürelerini sınırlamak için kullanılan bir özelliktir. Bu özellik, yöneticilere mesajların yaşam süresi üzerinde kontrol sağlar.

CAPEXPRY'nin Özellikleri
	1. Değer Formatı:
		○ Değer, saniyenin onda biri cinsinden ifade edilir. Örneğin, 600 değeri 1 dakikayı temsil eder.
	2. Kısıtlamalar:
		○ Uygulama tarafından belirtilen MQMD.Expiry alanındaki bir değer, CAPEXPRY değerini aşarsa, CAPEXPRY değeri ile değiştirilir.
		○ CAPEXPRY değerinden düşük bir süre belirtilmişse, bu süre kullanılır.
	3. Birden Fazla Nesne Durumu:
		○ Alias veya uzak kuyruk gibi birden fazla nesnenin kullanıldığı durumlarda, en düşük CAPEXPRY değeri geçerli olur.
	4. Değişikliklerin Etkisi:
		○ CAPEXPRY değişiklikleri hemen uygulanır. Ancak değişiklik, sadece değişiklikten sonra kuyruğa gönderilen mesajları etkiler. Kuyrukta mevcut olan mesajların süreleri etkilenmez.
	5. Kümelerde Davranış:
		○ Kümelenmiş bir kuyruğa mesaj gönderildiğinde, her hedef kuyruk yöneticisinin CAPEXPRY değeri farklı olabilir. Bu, mesajların farklı son kullanma sürelerine sahip olmasına neden olabilir.
	6. Kısıtlamalar:
		○ IBM MQ tarafından oluşturulan sistemsel mesajları tutan kuyruklarda (örneğin SYSTEM.CLUSTER.* ve SYSTEM.PROTECTION.POLICY.QUEUE) CAPEXPRY kullanılmamalıdır.

CAPEXPRY Ayarlama
	1. Kuyruklar ve Konular için CAPEXPRY Ayarı:

	2. ALTER QLOCAL(Q1) CAPEXPRY(1000)
	3. CUSTOM İçindeki CAPEXPRY Değerini Kaldırarak Yeni Değer Atama:

	4. ALTER QLOCAL(Q1) CAPEXPRY(1000) CUSTOM('')
	5. Varsayılan Değerler:
		○ Kuyruklar için varsayılan değer: NOLIMIT
		○ Konular için varsayılan değer: ASPARENT
	6. Küme Uyumluluğu:
		○ Kümelenmiş kuyruğun veya konunun tüm örnekleri aynı CAPEXPRY değerine sahip olmalıdır.

dmpmqmsg Yardımcı Programı ile Çalışma
dmpmqmsg, kuyruktaki mesajları bir dosyaya aktarmak, dosyadan geri yüklemek veya kuyruklar arasında mesaj taşımak için kullanılır.
Genel Kullanım Senaryoları:
	• Mesajları bir dosyaya kaydetmek ve daha sonra geri yüklemek.
	• Test mesajlarını yeniden oynatmak.
	• Belirli bir yaşta olan mesajları taşımak veya silmek.

dmpmqmsg Komut Örnekleri
	1. Kuyruktaki Mesajları Dosyaya Aktarma:

	2. dmpmqmsg -m QM1 -i Q1 -f c:\myfile
	3. Bir Kuyruktan Başka Bir Kuyruğa Mesaj Kopyalama:

	4. dmpmqmsg -m QM1 -i Q1 -o Q2
	5. Belirli Bir Sayıda Mesaj Kopyalama:

	6. dmpmqmsg -m QM1 -i Q1 -o Q2 -r#100
	7. Eski Mesajları Taşıma (1 Gün):

	8. dmpmqmsg -m QM1 -I Q1 -o Q2 -T1440
	9. Mesaj Yaşlarını Görüntüleme:

	10. dmpmqmsg -m QM1 -i Q1 -f stdout -dT
	11. Dosyayı Düzenleme ve Tekrar İşleme:

	12. dmpmqmsg -f c:\oldfile -f c:\newfile -dA

Notlar ve Dikkat Edilmesi Gerekenler
	• CAPEXPRY: Mesajların yaşam süresini sınırlarken uygulamanın uyumluluğunu kontrol edin.
	• dmpmqmsg: Mesaj dosyalarını düzenlerken formatı bozmamaya dikkat edin.
	• Küme Uyumluluğu: CAPEXPRY'nin kümelerde tutarlı olması sağlanmalıdır.


-----

IBM MQ Uzaktan Yönetim ve Nesne Yapılandırması
IBM MQ'da uzaktan yönetim, MQSC, PCF komutları veya REST API kullanılarak gerçekleştirilebilir. Uzaktan yönetimi etkinleştirmek için yerel ve uzak kuyruk yöneticilerinde belirli nesneleri yapılandırmanız gerekir. Aşağıda, uzaktan yönetim için gereken adımlar ve örnekler detaylı bir şekilde açıklanmıştır.

Uzaktan Yönetim için Gereken Yapılandırma
Yerel Kuyruk Yöneticisinde Yapılandırma
	1. Listener Tanımlayın: Listener, belirli bir port üzerinde gelen bağlantıları dinler.

DEFINE LISTENER ('source.queue.manager') TRPTYPE(TCP) PORT(1818)
START LISTENER ('source.queue.manager')
	2. Gönderici Kanal Tanımlayın: Gönderici kanal, uzak kuyruk yöneticisine bağlantıyı sağlar.

DEFINE CHANNEL ('source.to.target') CHLTYPE(SDR) CONNAME('remote_ip:1819') XMITQ('target.queue.manager') TRPTYPE(TCP)
	3. Alıcı Kanal Tanımlayın: Bu kanal, gelen mesajları alır.


DEFINE CHANNEL ('target.to.source') CHLTYPE(RCVR) TRPTYPE(TCP)
	4. İletim Kuyruğu Tanımlayın: Bu kuyruk, gönderilecek mesajları geçici olarak saklar.

DEFINE QLOCAL('target.queue.manager') USAGE(XMITQ)

Uzak Kuyruk Yöneticisinde Yapılandırma
	1. Listener Tanımlayın:

DEFINE LISTENER ('target.queue.manager') TRPTYPE(TCP) PORT(1819)
START LISTENER ('target.queue.manager')
	2. Gönderici Kanal Tanımlayın:

DEFINE CHANNEL ('target.to.source') CHLTYPE(SDR) CONNAME('local_ip:1818') XMITQ('source.queue.manager') TRPTYPE(TCP)
	3. Alıcı Kanal Tanımlayın:

DEFINE CHANNEL ('source.to.target') CHLTYPE(RCVR) TRPTYPE(TCP)
	4. İletim Kuyruğu Tanımlayın:

DEFINE QLOCAL('source.queue.manager') USAGE(XMITQ)

Komut Sunucusunun (Command Server) Yönetimi
Komut sunucusu, gelen MQSC ve PCF komutlarını işler. Uzaktan yönetim için etkin olması gerekir.
	1. Komut Sunucusunun Durumunu Kontrol Etme:

DISPLAY QMSTATUS CMDSERV
	2. Komut Sunucusunu Başlatma:


strmqcsv target.queue.manager
	3. Komut Sunucusunu Durdurma:

endmqcsv target.queue.manager

Uzaktan MQSC Komutları Çalıştırma
Uzaktan yönetim için runmqsc kullanılarak MQSC komutları çalıştırılır.
	1. Komutları Etkileşimli Çalıştırma:

runmqsc -w 30 -m source.queue.manager target.queue.manager
	2. Komut Dosyası Kullanarak Çalıştırma:

runmqsc -w 30 -m source.queue.manager target.queue.manager < commands.in > results.out

Kümeleme (Clustering) Alternatifi
Kümeleme, uzaktan yönetim için alternatif bir yapılandırma sunar. Küme içinde:
	• Gönderici (CLUSSDR) ve alıcı (CLUSRCVR) kanalları tanımlanır.
	• İletim kuyruğu veya uzak kuyruk tanımlamaları gerekmez.
Kümeleme için Örnek Kanal Tanımları

DEFINE CHANNEL('QM1.TO.QM2') CHLTYPE(CLUSSDR) CONNAME('host1(1414)') CLUSTER('MY.CLUSTER')
DEFINE CHANNEL('QM2.TO.QM1') CHLTYPE(CLUSRCVR) CLUSTER('MY.CLUSTER')

Kodlanmış Karakter Setleri (CCSID) ve Veri Dönüşümü
CCSID Dönüşümü için Genel Bilgiler
	• Yerel ve uzak karakter setleri (CCSID) arasındaki uyumluluk kontrol edilmelidir.
	• Desteklenmeyen dönüşümler için varsayılan dönüşüm yapılandırılabilir.
Varsayılan Dönüşüm Ayarı (ccsid.tbl veya ccsid_part2.tbl):

default 0 500 1 1 0  # EBCDIC için CCSID 500
default 0 850 1 2 0  # ASCII için CCSID 850

Test ve Sorun Giderme
	1. Kanalların Çalışır Durumda Olduğunu Kontrol Edin:

DISPLAY CHSTATUS(*) ALL
	2. İletim Kuyruğunu Kontrol Edin:

DISPLAY QLOCAL('target.queue.manager') CURDEPTH
	3. Güvenlik İzinlerini ve Komut Sunucusunu Kontrol Edin:
		○ CONNAME ve kanal izinlerini doğrulayın.
		○ Komut sunucusunun çalıştığından emin olun.
		

-----------

IBM MQ Yönetiminde Managed File Transfer (MFT) ve Telemetri İşlemleri
Managed File Transfer (MFT) ile Dosya Transferi Yönetimi
MFT, IBM MQ ile dosya transferini yönetmek için kullanılan bir özelliktir. Dosya transferleri, komut satırı veya IBM MQ Explorer üzerinden başlatılabilir, izlenebilir ve yönetilebilir.

Dosya Transferi Başlatma
	1. Komut Kuyruğuna Mesaj Yerleştirerek: Bir dosya transferi başlatmak için, kaynak aracının komut kuyruğuna bir mesaj yerleştirin.

<request>
   <source>...</source>
   <destination>...</destination>
   ...
</request>

Örnek komut kuyruğu adı: SYSTEM.FTE.COMMAND.AGENT01.
	2. Komut Satırı Kullanarak: Bir transferi doğrudan komut satırından başlatabilirsiniz:

fteCreateTransfer -sa AGENT1 -da AGENT2 -dd /destination/folder -df fileName

MFT Ajanlarını Yönetme
	• Ajan Başlatma:

fteStartAgent AGENT_NAME
	• Ajan Durdurma: Ajanın mevcut transferleri tamamlaması için:

fteStopAgent AGENT_NAME

Ajanı hemen durdurmak için:

fteStopAgent -i AGENT_NAME
	• Ajanları Listeleme:

fteListAgents -p QM_NAME

Dosya Transferi İzleme
	1. Aktif Transferler: IBM MQ Explorer’da "Current Transfer Progress" sekmesinden izlenebilir.
	2. Transfer Geçmişi: Transfer günlükleri, Explorer’da özelleştirilebilir.

Dosya Transferi Şablonları
Sık kullanılan ayarları bir şablonda saklayarak transfer işlemlerini kolaylaştırabilirsiniz:
	• Komut ile şablon oluşturma:

fteCreateTemplate -template templateName.xml
	• Explorer üzerinden "Save transfer settings as a template" seçeneğiyle şablon kaydedebilirsiniz.

Telemetri Yönetimi
IBM MQ Telemetri, MQTT istemcileri ile IBM MQ arasındaki iletişimi yönetir. IBM MQ Explorer veya MQSC komutları ile yapılandırılabilir.

Telemetriyi Yapılandırma (Windows Örneği)
	1. Telemetri İletim Kuyruğunu Oluşturma:

echo DEFINE QLOCAL('SYSTEM.MQTT.TRANSMIT.QUEUE') USAGE(XMITQ) MAXDEPTH(100000) | runmqsc QM_NAME
	2. Varsayılan İletim Kuyruğunu Ayarlama:

echo ALTER QMGR DEFXMITQ('SYSTEM.MQTT.TRANSMIT.QUEUE') | runmqsc QM_NAME
	3. MQXR Servisini Tanımlama: Örnek servis tanımı:

DEF SERVICE(SYSTEM.MQXR.SERVICE) +
    CONTROL(QMGR) +
    SERVTYPE(SERVER) +
    STARTCMD('path_to_runMQXRService.bat') +
    STARTARG('-m QM_NAME -d "path_to_data" -sf "path_to_keyFile.txt"') +
    STOPCMD('path_to_endMQXRService.bat') +
    STDOUT('path_to_mqxr.stdout') +
    STDERR('path_to_mqxr.stderr')
	4. MQXR Servisini Başlatma:

echo START SERVICE(SYSTEM.MQXR.SERVICE) | runmqsc QM_NAME

MQTT Kanal Güvenliğini Yapılandırma
	• TLS Kullanımı: MQTT istemcileri ile kanallar arasındaki iletişim TLS ile şifrelenebilir.
	• JAAS ile Kimlik Doğrulama: Kullanıcı adlarını doğrulamak için JAAS yapılandırması yapabilirsiniz.

Protokol Köprüsü (Protocol Bridge)
	• MFT ağı dışındaki dosya sunucularına erişmek için kullanılır.
	• FTP, FTPS ve SFTP protokollerini destekler.
Connect:Direct Köprüsü
	• IBM Sterling Connect:Direct ile dosya transferi yapmanızı sağlar.

Sorun Giderme ve İzleme
	1. Transfer Durumu İzleme:

fteShowTransferStatus -t transferID
	2. Transfer Hatalarını Görüntüleme: Transfer günlüklerini kontrol edin:

fteShowLog -t transferID


---------

IBM MQ'de AMQP İstemci ve Multicast Yönetimi
AMQP İstemci Yönetimi
IBM MQ, AMQP (Advanced Message Queuing Protocol) desteği ile AMQP istemcilerinin MQ altyapısına bağlanmasını ve mesajlaşmasını sağlar. AMQP istemcilerini yönetmek için IBM MQ Explorer veya komut satırı MQSC komutları kullanılabilir.

AMQP İstemci Yönetim Adımları
	1. AMQP Kanal Tanımlama:
		○ IBM MQ Explorer'da AMQP kanalları oluşturabilirsiniz.
		○ MQSC komutlarıyla bir kanal tanımlamak için:

DEFINE CHANNEL('AMQP.KANAL1') +
    CHLTYPE(AMQP) +
    TRPTYPE(TCP) +
    PORT(5672) +
    SSLCAUTH(REQUIRED) +
    SSLCIPH('TLS_RSA_WITH_AES_128_CBC_SHA256')
	2. AMQP Servisini Başlatma:
		○ MQ 9.4.0 itibarıyla, AMQP servisi varsayılan olarak otomatik başlamaz.
		○ Servisi manuel olarak başlatmak için:

START SERVICE(SYSTEM.AMQP.SERVICE)
	3. Güvenlik Yapılandırması:
		○ TLS ile veri şifrelemesi ve kuyruk yöneticisinin kimlik doğrulaması yapılabilir.
		○ Örnek TLS yapılandırması:

ALTER CHANNEL('AMQP.KANAL1') +
    SSLCAUTH(REQUIRED) +
    SSLCIPH('TLS_RSA_WITH_AES_256_CBC_SHA')
		○ JAAS kullanarak kullanıcı adı/parola doğrulaması ekleyebilirsiniz.
	4. AMQP İstemcilerini İzleme:
		○ Bağlı istemcileri IBM MQ Explorer üzerinden izleyebilirsiniz.
		○ Komut satırından bağlantıları listelemek için:

DISPLAY CONN(*) TYPE(CONN) WHERE(CHANNEL EQ 'AMQP.KANAL1')
	5. AMQP İstemcilerini Bağlantıdan Ayırma:
		○ Bir istemciyi bağlantıdan ayırmak için:

STOP CONNECTION(CONN_ID)
		○ Veya AMQP kanalını durdurabilirsiniz:

STOP CHANNEL('AMQP.KANAL1') MODE(FORCE)
	6. Mesaj Gizliliği Sağlama:
		○ Mesaj gizliliğini TLS ile sağlayın.
		○ Şifreleme ile birlikte sunucu veya karşılıklı kimlik doğrulaması eklemek daha güvenli bir yapı oluşturur.

IBM MQ Multicast Yönetimi
Multicast, IBM MQ'nun yüksek performanslı mesajlaşma için bir mesajı aynı anda birden fazla aboneye yayınlamasını sağlayan bir özelliktir. Multicast, topic tabanlıdır ve yayın (publish) ile abonelik (subscription) yapıları üzerinden çalışır.

Multicast Yönetim Adımları
	1. Multicast Topoloji Yapısını Anlamak:
		○ Multicast iletişiminde topic'ler kullanılır.
		○ Multicast topic tanımlama örneği:

DEFINE TOPIC('MULTICAST.TOPIC') +
    TOPICSTR('MULTICAST') +
    PUBSUB(MULTICAST) +
    DURABLE(YES)
	2. Multicast Mesaj Boyutunu Azaltma:
		○ Mesaj özelliklerini optimize ederek boyutu küçültün:

ALTER TOPIC('MULTICAST.TOPIC') +
    MSGDLVSQ(PRIORITY) +
    DEFPSIST(NO)
	3. Veri Dönüşümünü Etkinleştirme:
		○ Farklı karakter setleri arasında veri dönüşümü yapılmasını sağlayın:

DEFINE SUB('MULTICAST.SUB') +
    TOPICSTR('MULTICAST') +
    DEST('KUYRUK.ADI') +
    CCSID(1208)
	4. Multicast Mesajlaşmayı İzleme:
		○ Aktif bağlantıları ve mesaj durumlarını izleyin:

DISPLAY TOPIC('MULTICAST.TOPIC') ALL
	5. Mesaj Güvenilirliğini Artırma:
		○ Mesaj geri yükleme için geçmiş kaydı yapılandırın:

ALTER TOPIC('MULTICAST.TOPIC') +
    MSGHIST(YES)
	6. İleri Düzey Multicast Yapılandırmaları:
		○ Performansı optimize etmek için .ini dosyalarını düzenleyin.
		○ IBM MQ Low Latency Messaging (LLM) ile entegrasyon ihtiyacına göre yapılandırma yapabilirsiniz.

En İyi Uygulamalar
	• Güvenlik: Hem AMQP hem de Multicast mesajlaşma için şifrelemeyi (TLS) mutlaka etkinleştirin.
	• İzleme: Aktif bağlantılar, mesaj teslim durumu ve sistem kaynaklarını düzenli olarak izleyin.
	• Ölçeklenebilirlik: Yüksek verimlilik gerektiren durumlar için mesaj boyutları ve ağ ayarlarını optimize edin.

