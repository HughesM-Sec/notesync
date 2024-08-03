Metasploit allows you to quickly identify some critical vulnerabilities that could be considered as “low hanging fruit”.  The term “low hanging fruit” usually refers to easily identifiable and exploitable vulnerabilities that could potentially allow you to gain a foothold on a system and, in some cases, gain high-level privileges such as root or administrator.

Finding vulnerabilities using Metasploit will rely heavily on your ability to scan and fingerprint the target. The better you are at these stages, the more options Metasploit may provide you. For example, if you identify a VNC service running on the target, you may use the `search` function on Metasploit to list useful modules. The results will contain payload and post modules. At this stage, these results are not very useful as we have not discovered a potential exploit to use just yet. However, in the case of VNC, there are several scanner modules that we can use.

Example: VNC scanning modules

`msf6 > use auxiliary/scanner/vnc/`

`use auxiliary/scanner/vnc/ard_root_pw use auxiliary/scanner/vnc/vnc_login use auxiliary/scanner/vnc/vnc_none_auth`

`msf6 > use auxiliary/scanner/vnc/`

You can use the `info` command for any module to have a better understanding of its use and purpose.

VNC login scanner

`msf6 auxiliary(scanner/vnc/vnc_login) > info`

`Name: VNC Authentication Scanner`

`Module: auxiliary/scanner/vnc/vnc_login`

`License: Metasploit Framework License (BSD)`

`Rank: Normal`

`Provided by:`

`carstein`

`jduck`

`Check supported:`

`No`

`Basic options:`

`Name Current Setting Required Description`

`---- --------------- -------- -----------`

`BLANK_PASSWORDS false no Try blank passwords for all users`

`BRUTEFORCE_SPEED 5 yes How fast to bruteforce, from 0 to 5`

`DB_ALL_CREDS false no Try each user/password couple stored in the current database`

`DB_ALL_PASS false no Add all passwords in the current database to the list`

`DB_ALL_USERS false no Add all users in the current database to the list`

`PASSWORD no The password to test`

`PASS_FILE /opt/metasploit-framework-5101/data/wordlists/vnc_passwords.txt no File containing passwords, one per line`

`Proxies no A proxy chain of format type:host:port[,type:host:port][...]`

`RHOSTS yes The target host(s), range CIDR identifier, or hosts file with syntax 'file:'`

`RPORT 5900 yes The target port (TCP)`

`STOP_ON_SUCCESS false yes Stop guessing when a credential works for a host`

`THREADS 1 yes The number of concurrent threads (max one per host)`

`USERNAME no A specific username to authenticate as`

`USERPASS_FILE no File containing users and passwords separated by space, one pair per line`

`USER_AS_PASS false no Try the username as the password for all users`

`USER_FILE no File containing usernames, one per line`

`VERBOSE true yes Whether to print output for all attempts`

`Description:`

`This module will test a VNC server on a range of machines and report`

`successful logins. Currently it supports RFB protocol version 3.3,`

`3.7, 3.8 and 4.001 using the VNC challenge response authentication`

`method.`

`References:`

`https://cvedetails.com/cve/CVE-1999-0506/`

`msf6 auxiliary(scanner/vnc/vnc_login) >`

As you can see, the `vnc_login` module can help us find login details for the VNC service.