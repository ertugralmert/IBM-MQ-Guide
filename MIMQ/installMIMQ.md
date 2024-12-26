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




