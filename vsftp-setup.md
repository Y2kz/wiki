# FTP server setup using VSFTPD  

### Restricing the ssh login , access to specific directory only granted
--- 
<br/>

* Add new Linux User and set password <br/>
```
useradd -d <directory_for the_user_access> -s /sbin/nologin <user_name>
passwd <user_name>
<some_password> 
```

* Add new entry in the shells if not exist <br/>
```echo "/sbin/nologin" >> /etc/shells```

* Install vsftpd package and ftp package <br/>
  ```yum install vsftpd ftp -y```
  
* Confirm Below Config matches your config (Modify according to requirements) <br/>

```
[root@localhosst vsftpd]# cat /etc/vsftpd/vsftpd.conf|grep -v "^#"
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
xferlog_std_format=YES
chroot_local_user=YES
listen=YES
pam_service_name=vsftpd
userlist_enable=YES
chroot_list_enable=YES
use_localtime=YES
```
* Create config file [empty config_file] ( if not created ) <br/>
```touch /etc/vsftpd/chroot_list```

* Start the and Enable to restart when rebooted <br/>
```
systemctl start vsftpd
systemctl enable vsftpd
```




