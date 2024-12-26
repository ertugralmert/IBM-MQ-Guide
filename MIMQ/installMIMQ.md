# MIMQ -> IBM MQ Advanced Multi-Instance Kurulumu

## Genel Bilgiler ve Gereksinimler
MIMQ kurulumu için ihtiyacımız olan 3 server. 
- server 1: NFS 
- server 2: IBM MQ
- server 3: IBM MQ

Ben burada kendi sunucu bilgilerimi paylaşıyorum siz kendi serverlarınıza göre gerekli değişiklikleri yapabilirsiniz.

### NFS Server:
• Hostname: ibm1.fyre.ibm.com (ibm1)
	• IP: 9.46.244.83
### MQ Server:
• Hostname: ibmmq11.fyre.ibm.com (ibmmq11)
	• IP: 9.46.244.57
### MQ Server:
• Hostname: ibmmq21.fyre.ibm.com (ibmmq21)
	• IP: 9.46.244.61

## Yazılım Gereksinimleri

- IBM MQ Advanced (9.4.x LTS)
- RHEL 8.x veya üzeri
- NFS Version 4.x ->>> DİKKAT!!!! MIMQ için mutlaka NFS 4 kullanmak zorundasınız.

## Network Gereksinimleri
- Minimum 1Gbps network bağlantısı
- Network latency<2ms
- Redundant network bağlantısı önerilir.

#Server Hazırlıkları ve Altyapı
 ##ortak yapılması gerekenler
 
 ``` bash
 # /etc/hosts dosyasına tüm serverlara hostname'ler eklenmeli
 vi /etc/hosts
 #Eklenecek satırlar
 9.46.244.83 ibm1.fyre.ibm.com ibm1 nfsserver
 9.46.244.57 ibmmq11.fyre.ibm.com ibmmq11 mqserver1
 9.46.244.61 ibmmq21.fyre.ibm.com ibmmq21 mqserver2
 ````
 
 #Temel sistem ayarları
 
```bash
 #zaman senkroniasyonu
 dnf install -y chrony
 systemctl enable chronyd
 systemctl start chronyd
 
 #SELinux ayaları (Gerekirse)
 vi /etc/selinux/config
 
 # Sistem limitleri ayarları
 cat >> /etc/security/limits.conf << EOF
 mqm soft nofile 10240
 mqm hard nofile 10240
 mqm soft nproc  4096
 mqm hard nproc  4096
 EOF
 ```
 
# mqm kullanıcı ve grup oluşturma
```bash
# tüm kullanıcılarda aynı UID/GID olmalı. Bu yüzden MQ kurulumu önce manual olarak oluşturuyoruz
groupadd -g 501 mqm
useradd -u 501 -g mqm -m -d /home/mqm mqm

# Parola atama (gerekirse)
passwd mqm
```


# NFS Server Kurulumu
```bash
# sistem güncellemesi
dnf update -y
# NFS paketleri
dnf install -y nfs-utils nfs4-acl-tools
```


# NFS Servislerinin Yapılandırılması
```
systemctl enable rpcbind nfs-server
systemctl start rpcbind
systemctl start nfs-server

# Servis durumlarını kontrol et
systemctl status rpcbind
systemctl status nfs-server
```

# NFS Dizin Yapısı
```bash
# Ana dizinleri oluşturma
mkdir -p /MQHA
mkdir -p /MQHA/logs
mkdir -p /MQHA/qmgrs

# İzinleri ayarlama
chown -R mqm:mqm /MQHA
chmod -R 775 /MQHA

# izin kontrol
ls -lR /MQHA
```


# NFS Paylaşım Konfigürasyonu
```bash
# /etc/exports dosyasını düzenleme
vi /etc/exports

# eklenecek satır ( güvenli konfigürasyon)
 /MQHA  ibmmq11.fyre.ibm.com(rw,sync,no_wdelay,no_root_squash,sec=sys) ibmmq21.fyre.ibm.com(rw,sync,no_wdelay,no_root_squash,sec=sys)
 
 # NFS yapılandırılmasını yenilemek
 exports -ravf
 
 # Paylaşımları kontrol edelim
 exportfs -v
 
 showmount -e localhost
 
 ```

# NFS Server Güvenlik Ayarları
```bash
	#firewall kuralları -> burada firewall açıkça bunları uygulamanız gerekir.
	firewall-cmd --permanent --add-service=nfs
	firewall-cmd --permanent --add-service=rpc-bind
	firewall-cmd --permanent --add-service=mountd
	firewall-cmd --permanent --add-port=2049/tcp
	firewall-cmd --permanent --add-port=2049/udp
	firewall-cmd --reload
	
	# SELinux ayaları 
	setsebool -P nfs_export_all_ro=1
	setsebool -P nfs_export_all_rw=1
	
	# NFS güvenlik denetimi
	rpcinfo -p localhost
	
	```
	
*******

# IBM MQ Server Kurulumu (ibmmq11 ve ibmmq21)

	# NFS Client Kurulumu
	```bash
	 # NFS client paketleri
	 dnf install -y nfs-utils
	 
	 # NFS Servisleri
	 systemctl enable rpcbind
	 systemctl start rpcbind
	 ```
	 
	 # NFS Mount Yapılandırılması
	 ```bash
	  # Mount dizini
	  mkdir -p /MQHA
	  mkdir -p /MQHAlogs 
	  chown mqm:mqm /MQHA
	  chmod 775 /MQHA
	  
	  # fstab yapılandırılması
	  vi /etc/fstab
	  
	  #eklenecek satır 
	  ibm1.fyre.ibm.com:/MQHA    /MQHA   nfs4    rw,hard,intr,bg,nofail,vers=4.1,timeo=600,retrans=2,sec=sys,actimeo=120  0 0
	  
	  # Mount işlemi ve test
	  mount -a
	  df -h | grep MQHA
	  
	  #output: df -h | grep MQHA ->>> ibm1.fyre.ibm.com:/MQHA  233G  5.2G  228G   3% /MQHA
	  
	  #output: mount | grep MQHA ->>> ibm1.fyre.ibm.com:/MQHA on /MQHA type nfs4 (rw,relatime,vers=4.1,rsize=1048576,wsize=1048576,namlen=255,acregmin=120,acregmax=120,acdirmin=120,acdirmax=120,hard,proto=tcp,timeo=600,retrans=2,sec=sys,clientaddr=9.46.244.57,local_lock=none,addr=9.46.244.83)
	  
	  # Mount testi
	  su - mqm -c "touch /MQHA/test_file"
	  su - mqm -c "rm /MQHA/tes_file"
	  ```
	  


