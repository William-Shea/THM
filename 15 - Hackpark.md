# Hackpark
##### Question 1: Whats the name of the clown displayed on the homepage?
Answer
```bash
pennywise
```

##### Question 2: What request type is the Windows website login form using?
Answer
```bash
POST
```

##### Question 3: User Password for Login
Answer
```bash
1qaz2wsx
```

##### Question 4: Now you have logged into the website, are you able to identify the version of the BlogEngine?
Answer
```bash
3.3.6.0
```

##### Question 5: What is the CVE?
Answer
```bash
CVE-2019-6714
```

##### Question 6: Who is the webserver running as?
Answer
```bash
iis apppool\blog
```

##### Question 7: What is the OS version of this windows machine?
Answer
```bash
Windows 2012 R2 (6.3 Build 9600)
```

##### Question 8: What is the name of the abnormal service running?
Answer
```bash
WindowsScheduler
```

##### Question 9: What is the name of the binary you're supposed to exploit? 
Answer
```bash
message.exe
```

##### Question 10: User flag
Answer
```bash
759bd8af507517bcfaede78a21a73e39
```

##### Question 11: root flag
Answer
```bash
7e13d97f05f7ceb9881a3eb3d78d3e72
```

##### Question 12: Using winPeas, what was the Original Install time? (This is date and time)
Answer
```bash
8/3/2019, 10:43:23 AM
```

- - - - - - - - - - - - - - - - - -  - - - - - - - - - - - - - - 

Nmap Scan:
```bash
Nmap scan report for 10.10.0.112
Host is up (0.11s latency).
Not shown: 65533 filtered ports
PORT     STATE SERVICE            VERSION
80/tcp   open  http               Microsoft IIS httpd 8.5
| http-methods: 
|_  Potentially risky methods: TRACE
| http-robots.txt: 6 disallowed entries 
| /Account/*.* /search /search.aspx /error404.aspx 
|_/archive /archive.aspx
|_http-server-header: Microsoft-IIS/8.5
|_http-title: hackpark | hackpark amusements
3389/tcp open  ssl/ms-wbt-server?
| ssl-cert: Subject: commonName=hackpark
| Not valid before: 2021-12-17T00:43:44
|_Not valid after:  2022-06-18T00:43:44
|_ssl-date: 2021-12-18T00:50:14+00:00; 0s from scanner time.
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Network Distance: 4 hops
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

TRACEROUTE (using port 3389/tcp)
HOP RTT       ADDRESS
1   39.22 ms  10.6.0.1
2   ... 3
4   106.50 ms 10.10.0.112
```

Shell:
```bash
Edit The file mentioned https://www.exploit-db.com/exploits/46353

Upload it to an existing post

Have a NC listener running

navigate to http://10.10.0.112/?theme=../../App_Data/files

```

Priv Esc:
```bash
AutoLogin Creds: administrator:4q6XvFES7Fdxs

```
![[Pasted image 20211217191504.png]]