[jedi@192 sharedwin]$ ls /mnt/hgfs
sharedwin
[jedi@192 sharedwin]$ ls /mnt/hgfs/sharedwin/
9.4.0.0-IBM-MQ-LinuxX64.tar.gz  9.4.0.0-IBM-MQ-Win64.zip
[jedi@192 sharedwin]$ sudo mkdir -p /opt/setup

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for jedi: 
[jedi@192 sharedwin]$ sudo cp -r /mnt/hgfs/sharedwin/9.4.0.0-IBM-MQ-LinuxX64.tar.gz /opt/setup/
[jedi@192 sharedwin]$ ls /opt/setup/
9.4.0.0-IBM-MQ-LinuxX64.tar.gz
[jedi@192 sharedwin]$ 


[jedi@192 MQServer]$ sudo rpm -ivh MQSeries*.rpm
warning: MQSeriesAMQP-9.4.0-0.x86_64.rpm: Header V4 RSA/SHA256 Signature, key ID 07b22880: NOKEY
Verifying...                          ################################# [100%]
Preparing...                          ################################# [100%]
Creating group mqm
Creating user mqm
Updating / installing...
   1:MQSeriesRuntime-9.4.0-0          ################################# [  3%]
Warning : package "MQSeriesRuntime" is signed but key is not installed on this system.
          rpm verify shows "Header V4 RSA/SHA256 Signature, key ID 07b22880: NOKEY"
          rpm warning message may have been issued at install time.
          See topic "IBM MQ code signatures" in the IBM MQ documentation for more information.
   2:MQSeriesJava-9.4.0-0             ################################# [  6%]
   3:MQSeriesJRE-9.4.0-0              ################################# [ 10%]
   4:MQSeriesFTBase-9.4.0-0           ################################# [ 13%]
   5:MQSeriesGSKit-9.4.0-0            ################################# [ 16%]
   6:MQSeriesServer-9.4.0-0           ################################# [ 19%]
Updated PAM configuration in /etc/pam.d/ibmmq

WARNING: System settings for this system do not meet recommendations for this product 
         See the log file at "/tmp/mqconfig.3879.log" for more information

   7:MQSeriesFTAgent-9.4.0-0          ################################# [ 23%]
   8:MQSeriesFTService-9.4.0-0        ################################# [ 26%]
Licensed entitlement 'advanced' set for installation at '/opt/mqm'.
   9:MQSeriesAMQP-9.4.0-0             ################################# [ 29%]
  10:MQSeriesAMS-9.4.0-0              ################################# [ 32%]
Licensed entitlement 'advanced' set for installation at '/opt/mqm'.
  11:MQSeriesFTLogger-9.4.0-0         ################################# [ 35%]
  12:MQSeriesWeb-9.4.0-0              ################################# [ 39%]
  13:MQSeriesXRService-9.4.0-0        ################################# [ 42%]
Licensed entitlement 'advanced' set for installation at '/opt/mqm'.
  14:MQSeriesClient-9.4.0-0           ################################# [ 45%]
  15:MQSeriesFTTools-9.4.0-0          ################################# [ 48%]
  16:MQSeriesMan-9.4.0-0              ################################# [ 52%]
  17:MQSeriesMsg_cs-9.4.0-0           ################################# [ 55%]
  18:MQSeriesMsg_de-9.4.0-0           ################################# [ 58%]
  19:MQSeriesMsg_es-9.4.0-0           ################################# [ 61%]
  20:MQSeriesMsg_fr-9.4.0-0           ################################# [ 65%]
  21:MQSeriesMsg_hu-9.4.0-0           ################################# [ 68%]
  22:MQSeriesMsg_it-9.4.0-0           ################################# [ 71%]
  23:MQSeriesMsg_ja-9.4.0-0           ################################# [ 74%]
  24:MQSeriesMsg_ko-9.4.0-0           ################################# [ 77%]
  25:MQSeriesMsg_pl-9.4.0-0           ################################# [ 81%]
  26:MQSeriesMsg_pt-9.4.0-0           ################################# [ 84%]
  27:MQSeriesMsg_ru-9.4.0-0           ################################# [ 87%]
  28:MQSeriesMsg_Zh_CN-9.4.0-0        ################################# [ 90%]
  29:MQSeriesMsg_Zh_TW-9.4.0-0        ################################# [ 94%]
  30:MQSeriesSamples-9.4.0-0          ################################# [ 97%]
  31:MQSeriesSDK-9.4.0-0              ################################# [100%]
[jedi@192 MQServer]$ 



1. Advanced ve Server Kurulum Modları
IBM MQ, iki farklı modda çalıştırılabilir:
	1. Advanced: Ek özellikler içerir, örneğin:
		○ File Transfer Service (FTS)
		○ Advanced Message Security (AMS)
		○ XR Service gibi gelişmiş bileşenler.
	2. Server: Daha hafif ve temel işlevsellik içerir. Advanced bileşenleri olmadan çalışır.
Eğer yalnızca "server" modunu kullanmak istiyorsanız, yukarıda belirttiğiniz RPM paketlerini kaldırmamız gerekiyor.

2. Advanced Bileşenlerini Kaldırma
Advanced bileşenlerini kaldırmak için, aşağıdaki komutları çalıştırabilirsiniz:

sudo rpm -ev MQSeriesFTLogger-9.4.0-0.x86_64
sudo rpm -ev MQSeriesFTTools-9.4.0-0.x86_64
sudo rpm -ev MQSeriesFTService-9.4.0-0.x86_64
sudo rpm -ev MQSeriesFTAgent-9.4.0-0.x86_64
sudo rpm -ev MQSeriesFTBase-9.4.0-0.x86_64
sudo rpm -ev MQSeriesXRService-9.4.0-0.x86_64
sudo rpm -ev MQSeriesAMS-9.4.0-0.x86_64
	• rpm -ev: Paketleri sistemden kaldırır.
	• Yukarıdaki komutları tek tek çalıştırarak, bu bileşenleri kaldırabilirsiniz.

3. MQ Kurulum Modunu Server Olarak Ayarlama
Advanced bileşenleri kaldırıldıktan sonra, MQ kurulumunu server modunda ayarlamak için şu komutları çalıştırın:
Adım 1: Kurulum Modunu Belirtin

sudo ./setmqinst -i -p /opt/mqm
	• -i: Varsayılan kurulum modunu ayarlamak için kullanılır.
	• -p: IBM MQ kurulum dizinini belirtir (varsayılan: /opt/mqm).
Adım 2: Ortam Değişkenlerini Ayarlayın

. /opt/mqm/bin/setmqenv -s -k
	• setmqenv: IBM MQ için ortam değişkenlerini ayarlar.
	• -s: Server modunu etkinleştirir.
	• -k: Kernel ortamını kullanır.
	• 
	
[jedi@192 MQServer]$ cd /opt/mqm/bin/
[jedi@192 bin]$ sudo ./setmqinst -i -p /opt/mqm/
147 of 147 tasks have been completed successfully.
'Installation1' (/opt/mqm) set as the primary installation.
[jedi@192 bin]$ 


Komutun Amacı
	• setmqinst: IBM MQ'nun kurulum örneğini (instance) sistemde varsayılan olarak tanımlar.
	• -i: Kurulumu etkinleştirir ve bu IBM MQ sürümünü varsayılan yapar.
	• -p /opt/mqm: IBM MQ'nun kurulu olduğu dizini belirtir.

4. Kurulumun Doğruluğunu Kontrol Etme
Server moduna geçtikten sonra, kurulumun doğru çalıştığını doğrulamak için şu komutları çalıştırabilirsiniz:
	1. Kurulum Bilgisini Doğrulama

/opt/mqm/bin/dspmqver


	[jedi@192 bin]$ dspmqver
	Name:        IBM MQ
	Version:     9.4.0.0
	Level:       p940-L240605.1
	BuildType:   IKAP - (Production)
	Platform:    IBM MQ for Linux (x86-64 platform)
	Mode:        64-bit
	O/S:         Linux 5.14.0-503.15.1.el9_5.x86_64
	O/S Details: Red Hat Enterprise Linux 9.5 (Plow)
	InstName:    Installation1
	InstDesc:    
	Primary:     Yes
	InstPath:    /opt/mqm
	DataPath:    /var/mqm
	MaxCmdLevel: 940
	LicenseType: Production
	ReleaseType: Long Term Support (LTS) and Continuous Delivery (CD)
	[jedi@192 bin]$ 
	2. 

Çıktıda "server" modu belirtilmelidir.


	[jedi@192 bin]$ sudo -i
	[sudo] password for jedi: 
	[root@192 ~]# su - mqm
	[mqm@192 ~]$ crtmqm QM1
	IBM MQ queue manager 'QM1' created.
	Directory '/var/mqm/qmgrs/QM1' created.
	The queue manager is associated with installation 'Installation1'.
	Creating or replacing default objects for queue manager 'QM1'.
	Default objects statistics : 83 created. 0 replaced. 0 failed.
	Completing setup.
	Setup completed.
	[mqm@192 ~]$ strmqm QM1
	The system resource RLIMIT_NOFILE is set at an unusually low level for IBM MQ.
	IBM MQ queue manager 'QM1' starting.
	The queue manager is associated with installation 'Installation1'.
	6 log records accessed on queue manager 'QM1' during the log replay phase.
	Log replay for queue manager 'QM1' complete.
	Transaction manager state recovered for queue manager 'QM1'.
	Plain text communication is enabled.
	IBM MQ queue manager 'QM1' started using V9.4.0.0.
	[mqm@192 ~]$ runmqsc QM1
	5724-H72 (C) Copyright IBM Corp. 1994, 2024.
	Starting MQSC for queue manager QM1.
	
	
	DEFINE LISTENER('REDHAT.LISTENER') TRPTYPE(TCP) PORT(1414) CONTROL(QMGR)
	     1 : DEFINE LISTENER('REDHAT.LISTENER') TRPTYPE(TCP) PORT(1414) CONTROL(QMGR)
	AMQ8626I: IBM MQ listener created.
	START  LISTENER('REDHAT.LISTENER')
	     2 : START  LISTENER('REDHAT.LISTENER')
	AMQ8021I: Request to staO.WINDOWS') CHLTYPE(SDR) TRPTYPE(TCP) CONNAME('192.13 MQSC commands read.
	No commands have a syntax error.
	All valid MQSC commands were processed.
	[mqm@192 ~]$ runmqsc QM1
	5724-H72 (C) Copyright IBM Corp. 1994, 2024.
	Starting MQSC for queue manager QM1.
	
	
	DEFINE CHANNEL('REDHAT.TO.WINDOWS') CHLTYPE(SDR) TRPTYPE(TCP) CONNAME('192.168.142.129(1414)') XMITQ('WINDOWS.TRANSMIT.QUEUE') 
	     1 : DEFINE CHANNEL('REDHAT.TO.WINDOWS') CHLTYPE(SDR) TRPTYPE(TCP) CONNAME('192.168.142.129(1414)') XMITQ('WINDOWS.TRANSMIT.QUEUE')
	AMQ8014I: IBM MQ channel created.

Windows:
	• IPv4 Adresi: 192.168.142.129
	• Port: 1414
Red Hat:
	• IPv4 Adresi: 192.168.142.128
	• Port: 1414

netsh advfirewall firewall add rule name="MQ Port 1414" protocol=TCP dir=in localport=1414 action=allow
