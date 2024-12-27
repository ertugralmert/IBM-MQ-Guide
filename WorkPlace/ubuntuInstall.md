cd /opt/setup
tar -xvf 9.4.0.0-IBM-MQ-UbuntuLinuxX64.tar

jedi@jedi:/opt/setup/MQServer$ sudo ./mqlicense.sh -accept
Licensed Materials - Property of IBM
 5724-H72
 (C) Copyright IBM Corporation 1993, 2024
US Government Users Restricted Rights - Use, duplication or disclosure
restricted by GSA ADP Schedule Contract with IBM Corp.
License has already been accepted:  Proceed with install.

*****
sudo dpkg -i ibmmq-*.deb
Sudo su - mqm

mqm@jedi:~$ ls /opt/mqm
bin	inc	      java  lib    licenses	msg	 samp
gskit8	instinfo.tsk  lap   lib64  mqpatch.dat	READMES  swidtag
mqm@jedi:~$ export PATH=$PATH:/opt/mqm/bin/:/opt/mqm/samp/bin
mqm@jedi:~$ dspmqver
Name:        IBM MQ
Version:     9.4.0.0
Level:       p940-L240605.1
BuildType:   IKAP - (Production)
Platform:    IBM MQ for Linux (x86-64 platform)
Mode:        64-bit
O/S:         Linux 6.8.0-49-generic
O/S Details: Ubuntu 24.04.1 LTS (Noble Numbat)
InstName:    Installation1
InstDesc:    
Primary:     No
InstPath:    /opt/mqm
DataPath:    /var/mqm
MaxCmdLevel: 940
LicenseType: Production
ReleaseType: Long Term Support (LTS) and Continuous Delivery (CD)
mqm@jedi:~$ 
mqm@jedi:~$ nano ~/.bashrc.   ->>>> export PATH=$PATH:/opt/mqm/bin:/opt/mqm/samp/bin
mqm@jedi:~$ source ~/.bashrc
mqm@jedi:~$ 


mqm@jedi:~$ crtmqm QM3
IBM MQ queue manager 'QM3' created.
Directory '/var/mqm/qmgrs/QM3' created.
The queue manager is associated with installation 'Installation1'.
Creating or replacing default objects for queue manager 'QM3'.
Default objects statistics : 83 created. 0 replaced. 0 failed.
Completing setup.
Setup completed.


mqm@jedi:~$ strmqm QM3
The system resource RLIMIT_NOFILE is set at an unusually low level for IBM MQ.
IBM MQ queue manager 'QM3' starting.
The queue manager is associated with installation 'Installation1'.
6 log records accessed on queue manager 'QM3' during the log replay phase.
Log replay for queue manager 'QM3' complete.
Transaction manager state recovered for queue manager 'QM3'.
Plain text communication is enabled.
IBM MQ queue manager 'QM3' started using V9.4.0.0.


mqm@jedi:~$ dspmq
QMNAME(QM3)                                               STATUS(Running)
mqm@jedi:~$ 

