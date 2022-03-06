# Anthem
##### Question 1: What port is for the web server?
Answer
```bash
80
```

##### Question 2: What port is for remote desktop service?
Answer
```bash
3389
```

##### Question 3: What is a possible password in one of the pages web crawlers check for?
Answer
```bash
UmbracoIsTheBest!
```

##### Question 4: What CMS is the website using?
Answer
```bash
Umbraco
```

##### Question 5: What is the domain of the website?
Answer
```bash
anthem.com
```

##### Question 6: What's the name of the Administrator
Answer
```bash
Solomon Grundy
```

##### Question 7: Can we find find the email address of the administrator?
Answer
```bash
sg@anthem.com
```

##### Question 8: What is flag 1?
Answer
```bash
THM{L0L_WH0_US3S_M3T4}
```

##### Question 9: What is flag 2?
Answer
```bash
THM{G!T_G00D}
```

##### Question 10: What is flag 3?
Answer
```bash
THM{L0L_WH0_D15}
```

##### Question 11: What is flag 4?
Answer
```bash
THM{AN0TH3R_M3TA}
```

##### Question 12: Gain initial access to the machine, what is the contents of user.txt?
Answer
```bash
THM{N00t_NO0t}
```

##### Question 13: Can we spot the admin password?
Answer
```bash
ChangeMeBaby1MoreTime
```

##### Question 14: Escalate your privileges to root, what is the contents of root.txt?
Answer
```bash
THM{Y0U_4R3_1337}
```

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 

Nmap Scans:
```bash

Nmap scan report for 10.10.176.58
Host is up (0.10s latency).
Not shown: 998 filtered ports
PORT     STATE SERVICE       VERSION
80/tcp   open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
3389/tcp open  ms-wbt-server Microsoft Terminal Services
| rdp-ntlm-info: 
|   Target_Name: WIN-LU09299160F
|   NetBIOS_Domain_Name: WIN-LU09299160F
|   NetBIOS_Computer_Name: WIN-LU09299160F
|   DNS_Domain_Name: WIN-LU09299160F
|   DNS_Computer_Name: WIN-LU09299160F
|   Product_Version: 10.0.17763
|_  System_Time: 2022-03-06T22:27:06+00:00
| ssl-cert: Subject: commonName=WIN-LU09299160F
| Not valid before: 2022-03-05T22:24:40
|_Not valid after:  2022-09-04T22:24:40
|_ssl-date: 2022-03-06T22:27:34+00:00; 0s from scanner time.
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: specialized|general purpose
Running (JUST GUESSING): AVtech embedded (87%), Microsoft Windows XP (85%)
OS CPE: cpe:/o:microsoft:windows_xp::sp3
Aggressive OS guesses: AVtech Room Alert 26W environmental monitor (87%), Microsoft Windows XP SP3 (85%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 4 hops
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows


```

umbraco login:
sg@anthem.com:UmbracoIsTheBest!

rdp login:
sg:UmbracoIsTheBest!

```bash

privesc - edit file

add yourself read permissions on the c:\backup\restore.txt file

administrator:ChangeMeBaby1MoreTime

```