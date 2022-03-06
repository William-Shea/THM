# Blaster
##### Question 1: How many ports are open on our target system?
Answer
```bash
2
```

##### Question 2:Looks like there's a web server running, what is the title of the page we discover when browsing to it?
Answer
```bash
IIS Windows Server
```

##### Question 3:Interesting, let's see if there's anything else on this web server by fuzzing it. What hidden directory do we discover?
Answer
```bash
/retro
```

##### Question 4:Navigate to our discovered hidden directory, what potential username do we discover?
Answer
```bash
wade
```

##### Question 5:Crawling through the posts, it seems like our user has had some difficulties logging in recently. What possible password do we discover?
Answer
```bash
parzival
```

##### Question 6:Log into the machine via Microsoft Remote Desktop (MSRDP) and read user.txt. What are it's contents?
Answer
```bash
THM{HACK_PLAYER_ONE}
```

##### Question 7:  When enumerating a machine, it's often useful to look at what the user was last doing. Look around the machine and see if you can find the CVE which was researched on this server. What CVE was it?
Answer
```bash
CVE-2019-1388
```

##### Question 8:Looks like an executable file is necessary for exploitation of this vulnerability and the user didn't really clean up very well after testing it. What is the name of this executable?
Answer
```bash
hhupd
```

##### Question 9:Now that we've spawned a terminal, let's go ahead and run the command 'whoami'. What is the output of running this?
Answer
```bash
NT AUTHORITY\SYSTEM
```

##### Question 10:Now that we've confirmed that we have an elevated prompt, read the contents of root.txt on the Administrator's desktop. What are the contents? Keep your terminal up after exploitation so we can use it in task four!
Answer
```bash
THM{COIN_OPERATED_EXPLOITATION}
```

##### Question 11:First, let's set the target to PSH (PowerShell). Which target number is PSH?
Answer
```bash
2
```

##### Question 12:Last but certainly not least, let's look at persistence mechanisms via Metasploit. What command can we run in our meterpreter console to setup persistence which automatically starts when the system boots? Don't include anything beyond the base command and the option for boot startup.
Answer
```bash
run persistance -x
```

- - - - - - - - - - - - - - - - - -  - - - - - - - - - - - - - - - - 

Nmap Scans:
```bash

Nmap scan report for 10.10.48.231
Host is up (0.10s latency).
Not shown: 998 filtered ports
PORT     STATE SERVICE       VERSION
80/tcp   open  http          Microsoft IIS httpd 10.0
| http-methods: 
|_  Potentially risky methods: TRACE
|_http-server-header: Microsoft-IIS/10.0
|_http-title: IIS Windows Server
3389/tcp open  ms-wbt-server Microsoft Terminal Services
| rdp-ntlm-info: 
|   Target_Name: RETROWEB
|   NetBIOS_Domain_Name: RETROWEB
|   NetBIOS_Computer_Name: RETROWEB
|   DNS_Domain_Name: RetroWeb
|   DNS_Computer_Name: RetroWeb
|   Product_Version: 10.0.14393
|_  System_Time: 2022-03-06T21:53:58+00:00
| ssl-cert: Subject: commonName=RetroWeb
| Not valid before: 2022-03-05T21:52:35
|_Not valid after:  2022-09-04T21:52:35
|_ssl-date: 2022-03-06T21:54:00+00:00; 0s from scanner time.
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose


```

wordpress and RDP creds:
wade:parzival

wordpressuser567:YSPgW[%C.mQE

priv esc via CVE-2019-1388