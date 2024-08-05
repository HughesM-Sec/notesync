# Nmap

```shell-session
# Nmap 7.60 scan initiated Mon Aug  5 17:58:42 2024 as: nmap -sT -p- -oN nmap.txt -vvv 10.10.129.43
Nmap scan report for ip-10-10-129-43.eu-west-1.compute.internal (10.10.129.43)
Host is up, received arp-response (0.00053s latency).
Scanned at 2024-08-05 17:58:42 BST for 2s
Not shown: 65534 closed ports
Reason: 65534 conn-refused
PORT   STATE SERVICE    REASON
85/tcp open  mit-ml-dev syn-ack
MAC Address: 02:D9:98:8A:01:13 (Unknown)

Read data files from: /usr/bin/../share/nmap
# Nmap done at Mon Aug  5 17:58:44 2024 -- 1 IP address (1 host up) scanned in 2.79 seconds
```

Website was just a picture and text, so I decided to enumerate.

# gobuster

```shell-session
===============================================================
root@ip-10-10-128-194:~# gobuster dir -u http://10.10.129.43:85/ -w /usr/share/wordlists/dirb/big.txt 
===============================================================
Gobuster v3.0.1
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@_FireFart_)
===============================================================
[+] Url:            http://10.10.129.43:85/
[+] Threads:        10
[+] Wordlist:       /usr/share/wordlists/dirb/big.txt
[+] Status codes:   200,204,301,302,307,401,403
[+] User Agent:     gobuster/3.0.1
[+] Timeout:        10s
===============================================================
2024/08/05 18:00:33 Starting gobuster
===============================================================
/.htaccess (Status: 403)
/.htpasswd (Status: 403)
/app (Status: 301)
/server-status (Status: 403)
===============================================================
2024/08/05 18:00:35 Finished
===============================================================
```

/app brought me to a button that redirected to /app/castle/ 

Enumerating further:

```shell-session
root@ip-10-10-128-194:~# gobuster dir -u http://10.10.129.43:85/app/castle/ -w /usr/share/wordlists/dirb/big.txt 
===============================================================
Gobuster v3.0.1
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@_FireFart_)
===============================================================
[+] Url:            http://10.10.129.43:85/app/castle/
[+] Threads:        10
[+] Wordlist:       /usr/share/wordlists/dirb/big.txt
[+] Status codes:   200,204,301,302,307,401,403
[+] User Agent:     gobuster/3.0.1
[+] Timeout:        10s
===============================================================
2024/08/05 18:06:38 Starting gobuster
===============================================================
/.htaccess (Status: 403)
/.htpasswd (Status: 403)
/application (Status: 301)
/concrete (Status: 301)
/packages (Status: 301)
/robots.txt (Status: 200)
/updates (Status: 301)
===============================================================
2024/08/05 18:06:41 Finished
===============================================================
```

/concrete was a large directory, buy access is denied to the individual files held inside

/castle/ had a link to a login page at the bottom.

# Login

After failing to find a good syntax to get hydra going, I tried some common credentials

admin:admin didn't work, but admin:password did.

Found file upload, but can't upload phps. Tried changing the extension of a reverse shell but it couldn't get it to work through burp. After some tinkering with it I decided to look around. In system settings I was able to change allowed upload extensions and then upload my php shell. 

# shell

Not much I could do as the www user in the shell. Found 2 users in home folder that I couldn't access so I needed more info.

Transferred linpeas.sh over to the machine via a python http server

Got a password from the mkingdom database in /concrete/config/database.php

'password' 'toadisthebest'

I logged into toad and ran linpeas again and ididn't get much out of it. I checked the env 

```shell-session
toad@mkingdom:~$ env
env
APACHE_PID_FILE=/var/run/apache2/apache2.pid
XDG_SESSION_ID=c2
SHELL=/bin/bash
APACHE_RUN_USER=www-data
OLDPWD=/tmp
USER=toad
LS_COLORS=
PWD_token=aWthVGVOVEFOdEVTCg==
MAIL=/var/mail/toad
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
APACHE_LOG_DIR=/var/log/apache2
PWD=/home/toad
LANG=en_US.UTF-8
APACHE_RUN_GROUP=www-data
HOME=/home/toad
SHLVL=2
LOGNAME=toad
LESSOPEN=| /usr/bin/lesspipe %s
XDG_RUNTIME_DIR=/run/user/1002
APACHE_RUN_DIR=/var/run/apache2
APACHE_LOCK_DIR=/var/lock/apache2
LESSCLOSE=/usr/bin/lesspipe %s %s
_=/usr/bin/env
```
and found a password hash that translated to `ikaTeNTANtES'

I was able to use it to log into mario, I couldn't read the user.txt in mario's home folder but I remembered seeing that toad's ran with root privs on linpeas earlier.

I changed to toad and grabbed the flag.



cat /etc/hosts | sed 's/127.0.1.1\t\mkingdom.thm/10.13.57.25\t\mkingdom.thm/g' > /tmp/replace_hosts

