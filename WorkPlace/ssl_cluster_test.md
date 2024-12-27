IBM MQ İleri Seviye Yapılandırma Rehberi
İçindekiler
	1. Temel Kanal ve Queue Yapılandırması
	2. Windows Bağlantı Konfigürasyonu
	3. SSL/TLS Yapılandırması
	4. Cluster Kurulumu
	5. Test ve Doğrulama
1. Temel Kanal ve Queue Yapılandırması
1.1 Listener Yapılandırması

# mqm kullanıcısı ile QMMI1 queue manager'da:
runmqsc QMMI1
# Listener oluşturma
DEFINE LISTENER(LISTENER.TCP) TRPTYPE(TCP) PORT(1414) CONTROL(QMGR)
START LISTENER(LISTENER.TCP)
# Listener durumunu kontrol
DISPLAY LSSTATUS(LISTENER.TCP)
1.2 Temel Kanallar

# Server-Connection Channel
DEFINE CHANNEL(SYSTEM.ADMIN.SVRCONN) CHLTYPE(SVRCONN) REPLACE
DEFINE CHANNEL(APP.SVRCONN) CHLTYPE(SVRCONN) MCAUSER('mqm') REPLACE
# Windows için özel kanal
DEFINE CHANNEL(WINDOWS.SVRCONN) CHLTYPE(SVRCONN) MCAUSER('mqm')
# Sender ve Receiver kanallar (Cluster için)
DEFINE CHANNEL(TO.QMMI2) CHLTYPE(SDR) CONNAME('ibmmq21.fyre.ibm.com(1414)') XMITQ(TO.QMMI2) REPLACE
DEFINE CHANNEL(FROM.QMMI1) CHLTYPE(RCVR) REPLACE
1.3 Kuyruk Yapılandırması

# Local Queue'lar
DEFINE QLOCAL(APP.QUEUE) REPLACE
DEFINE QLOCAL(WINDOWS.QUEUE) REPLACE
# Transmission Queue (Cluster için)
DEFINE QLOCAL(TO.QMMI2) USAGE(XMITQ)
# Remote Queue
DEFINE QREMOTE(REMOTE.QUEUE) RNAME(LOCAL.QUEUE) RQMNAME(QMMI2) XMITQ(TO.QMMI2)
# System Queue'ları
DEFINE QLOCAL(SYSTEM.DEAD.LETTER.QUEUE) REPLACE
DEFINE QLOCAL(SYSTEM.ADMIN.COMMAND.QUEUE) REPLACE
END
2. Windows Bağlantı Konfigürasyonu
2.1 Windows MQ Explorer için Yapılandırma

runmqsc QMMI1
# Windows bağlantısı için kanal güvenlik ayarları
ALTER QMGR CHLAUTH(DISABLED)
ALTER CHANNEL(WINDOWS.SVRCONN) CHLTYPE(SVRCONN) MCAUSER('mqm')
# Test için basit queue
DEFINE QLOCAL(WIN.QUEUE) REPLACE
END
2.2 Windows MQ Explorer Bağlantı Ayarları
	1. MQ Explorer'da sağ tık -> Add Remote Queue Manager
	2. Queue Manager Details: 
		○ Queue Manager Name: QMMI1
		○ Connection Type: Client
	3. Connection Details: 
		○ Hostname: ibmmq11.fyre.ibm.com, ibmmq21.fyre.ibm.com
		○ Port: 1414
		○ Server-connection channel: WINDOWS.SVRCONN
2.3 CCDT (Client Channel Definition Table) Oluşturma

# CCDT JSON formatında
cat > ccdt.json << EOF
{
    "channel": [
        {
            "name": "WINDOWS.SVRCONN",
            "clientConnection": {
                "connection": [
                    {
                        "host": "ibmmq11.fyre.ibm.com",
                        "port": 1414
                    },
                    {
                        "host": "ibmmq21.fyre.ibm.com",
                        "port": 1414
                    }
                ],
                "queueManager": "QMMI1"
            },
            "type": "clientConnection"
        }
    ]
}
EOF
3. SSL/TLS Yapılandırması
3.1 Sertifika Oluşturma

# Key repository oluşturma
mkdir -p /MQHA/qmgrs/QMMI1/ssl
cd /MQHA/qmgrs/QMMI1/ssl
# Key database oluşturma
runmqakm -keydb -create -db key.kdb -pw password -type cms -stash
# Self-signed sertifika oluşturma
runmqakm -cert -create -db key.kdb -label qmcert \
  -dn "CN=QMMI1,O=IBM,C=US" -size 2048 -sigalg SHA256WithRSA \
  -pw password
# Sertifika detaylarını görüntüleme
runmqakm -cert -list -db key.kdb -pw password
3.2 SSL Channel Yapılandırması

runmqsc QMMI1
# SSL kanalı oluşturma
DEFINE CHANNEL(SSL.SVRCONN) CHLTYPE(SVRCONN) +
       SSLCIPH(TLS_RSA_WITH_AES_128_CBC_SHA256) +
       SSLCAUTH(OPTIONAL) +
       MCAUSER('mqm')
# Windows kanalına SSL ekleme
ALTER CHANNEL(WINDOWS.SVRCONN) CHLTYPE(SVRCONN) +
      SSLCIPH(TLS_RSA_WITH_AES_128_CBC_SHA256) +
      SSLCAUTH(OPTIONAL)
# Queue Manager SSL yapılandırması
ALTER QMGR SSLKEYR('/MQHA/qmgrs/QMMI1/ssl/key')
ALTER QMGR CERTLABL('qmcert')
# SSL'i aktif etme
REFRESH SECURITY TYPE(SSL)
END
3.3 Windows Client için SSL Yapılandırması
	1. Sertifikaları dışa aktarma:

runmqakm -cert -extract -db key.kdb -pw password -label qmcert \
  -target qmcert.crt -format ascii
	2. qmcert.crt dosyasını Windows'a kopyalayın
	3. Windows'ta sertifikayı "Trusted Root Certification Authorities" altına import edin
4. Cluster Kurulumu
4.1 Cluster Temel Yapılandırması

runmqsc QMMI1
# Cluster repository tanımlama
ALTER QMGR REPOS(MQ.CLUSTER)
# Cluster receiver channel
DEFINE CHANNEL(TO.QMMI1) CHLTYPE(CLUSRCVR) +
       CONNAME('ibmmq11.fyre.ibm.com(1414)') +
       CLUSTER(MQ.CLUSTER)
# Cluster sender channel
DEFINE CHANNEL(TO.QMMI2) CHLTYPE(CLUSSDR) +
       CONNAME('ibmmq21.fyre.ibm.com(1414)') +
       CLUSTER(MQ.CLUSTER)
# Cluster queue tanımlama
DEFINE QLOCAL(CLUSTER.QUEUE) CLUSTER(MQ.CLUSTER)
END
4.2 Cluster Monitoring

# Cluster durumunu kontrol
DISPLAY CLUSQMGR(*)
DISPLAY CHANNEL(*) WHERE(CHLTYPE EQ CLUSRCVR)
DISPLAY QUEUE(*) WHERE(CLUSTER EQ MQ.CLUSTER)
5. Test ve Doğrulama
5.1 Windows Bağlantı Testi
Windows komut satırında:

set MQSERVER=WINDOWS.SVRCONN/TCP/ibmmq11.fyre.ibm.com(1414),ibmmq21.fyre.ibm.com(1414)
amqsputc WIN.QUEUE QMMI1
5.2 SSL Bağlantı Testi

set MQSSLKEYR=C:\MQ\ssl\key
set MQCHLLIB=C:\MQ\client
set MQCHLTAB=AMQCLCHL.TAB
amqsputc SSL.QUEUE QMMI1
5.3 Cluster Testi

# Cluster durumunu kontrol
echo "display clusqmgr(*)" | runmqsc QMMI1
# Test mesajı gönderme
/opt/mqm/samp/bin/amqsput CLUSTER.QUEUE QMMI1
Önemli Güvenlik Notları
	1. Channel Authentication:

# CHLAUTH kayıtları
SET CHLAUTH('WINDOWS.SVRCONN') TYPE(ADDRESSMAP) ADDRESS('*') USERSRC(MAP) MCAUSER('mqm')
SET CHLAUTH('SSL.SVRCONN') TYPE(ADDRESSMAP) ADDRESS('*') USERSRC(MAP) MCAUSER('mqm')
	2. Connection Authentication:

# CONNAUTH yapılandırması
DEFINE AUTHINFO(SYSTEM.DEFAULT.AUTHINFO.IDPWOS) +
       AUTHTYPE(IDPWOS) +
       ADOPTCTX(YES) +
       CHCKCLNT(OPTIONAL)
ALTER QMGR CONNAUTH(SYSTEM.DEFAULT.AUTHINFO.IDPWOS)
	3. SSL Cipher Specs:
	• TLS_RSA_WITH_AES_128_CBC_SHA256
	• TLS_RSA_WITH_AES_256_CBC_SHA256
	• ECDHE_RSA_AES_128_CBC_SHA256
	• ECDHE_RSA_AES_256_CBC_SHA384
	4. Regular Bakım İşlemleri:

# Dead letter queue kontrolü
DISPLAY QLOCAL(SYSTEM.DEAD.LETTER.QUEUE) CURDEPTH
# Channel durumları
DISPLAY CHSTATUS(*)
# Cluster sağlık kontrolü
DISPLAY CLUSQMGR(*) STATUS
