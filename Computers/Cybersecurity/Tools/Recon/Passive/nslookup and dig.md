# nslookup

Find the IP address of a domain name using `nslookup`, which stands for Name Server Look Up. You need to issue the command `nslookup DOMAIN_NAME`, for example, `nslookup tryhackme.com`. Or, more generally, you can use `nslookup OPTIONS DOMAIN_NAME SERVER`. These three main parameters are:

- OPTIONS contains the query type as shown in the table below. For instance, you can use `A` for IPv4 addresses and `AAAA` for IPv6 addresses.
- DOMAIN_NAME is the domain name you are looking up.
- SERVER is the DNS server that you want to query. You can choose any local or public DNS server to query. Cloudflare offers `1.1.1.1` and `1.0.0.1`, Google offers `8.8.8.8` and `8.8.4.4`, and Quad9 offers `9.9.9.9` and `149.112.112.112`. There are many [more public DNS servers](https://duckduckgo.com/?q=public+dns) that you can choose from if you want alternatives to your ISP’s DNS servers.

| Query type | Result             |
| ---------- | ------------------ |
| A          | IPv4 Addresses     |
| AAAA       | IPv6 Addresses     |
| CNAME      | Canonical Name     |
| MX         | Mail Servers       |
| SOA        | Start of Authority |
| TXT        | TXT Records        |

`nslookup -type=a tryhackme.com 1.1.1.1` can be used to return all the IPv4 addresses used by tryhackme.com.
```sh-session
┌──(kali㉿kali)-[~]
└─$ nslookup -type=a tryhackme.com 1.1.1.1
Server:         1.1.1.1
Address:        1.1.1.1#53

Non-authoritative answer:
Name:   tryhackme.com
Address: 104.22.54.228
Name:   tryhackme.com
Address: 104.22.55.228
Name:   tryhackme.com
Address: 172.67.27.10
```

The A and AAAA records are used to return IPv4 and IPv6 addresses, respectively. In a penetration test, each of these IP addresses can be further investigated for vulnerabilities, assuming they lie within the scope of the penetration test.

If you want to learn about email servers and configurations for a domain, you can issue `nslookup -type=mx tryhackme.com`.
###### EXAMPLE:
```sh-session
┌──(kali㉿kali)-[~]
└─$ nslookup -type=mx tryhackme.com       
Server:         68.105.28.11
Address:        68.105.28.11#53

Non-authoritative answer:
tryhackme.com   mail exchanger = 1 aspmx.l.google.com.
tryhackme.com   mail exchanger = 10 alt3.aspmx.l.google.com.
tryhackme.com   mail exchanger = 10 alt4.aspmx.l.google.com.
tryhackme.com   mail exchanger = 5 alt1.aspmx.l.google.com.
tryhackme.com   mail exchanger = 5 alt2.aspmx.l.google.com.

Authoritative answers can be found from:
aspmx.l.google.com      internet address = 142.251.2.26
aspmx.l.google.com      has AAAA address 2607:f8b0:4023:c0d::1a
alt3.aspmx.l.google.com internet address = 172.253.113.27
alt1.aspmx.l.google.com internet address = 108.177.104.27
alt1.aspmx.l.google.com has AAAA address 2607:f8b0:4003:c04::1b
alt2.aspmx.l.google.com internet address = 142.250.152.27
alt2.aspmx.l.google.com has AAAA address 2607:f8b0:4001:c56::1a
```

This shows that tryhackme.com's current email config uses Google. Since **MX** is looking up the **Mail Exchange** servers, we see that when a mail server tries to deliver an email to `@tryhackme.com`, it will try to connect to the `aspmx.l.google.com`, which has order  1. If it is unavailable, the mail server will attempt to connect to the next mail exchange servers in the order: `alt1.aspmx.l.google.com` or `alt2.aspmx.l.google.com`.

In this case, Google is providing the listed mail servers, so it is not expected that the mail servers will be running a vulnerable server version. In other cases we might find mail servers that are not adequately secured or patched.

This can prove to be valuable information as you continue passive reconnaissance of your target. You can repeat similar queries for other domain names using different options, such as `-type=txt`.

# Dig

For more advanced DNS queries and additional functionality you can use `dig`, which is the acronym for "Domain Information Groper". Let's use `dig` to look up the MX records and compare them with `nslookup`. We can use `dig DOMAIN_NAME`, but to specify the record type, we use `dig DOMAIN_NAME TYPE`. Optionally, we can select the server we want to query using `dig @SERVER DOMAIN_NAME TYPE`.

- SERVER is the DNS server you want to query.
- DOMAIN_NAME is the domain name you are looking up.
- TYPE contains the DNS record type, as shown in the table provided earlier.

###### EXAMPLE:
```sh-session
┌──(kali㉿kali)-[~]
└─$ dig tryhackme.com mx

; <<>> DiG 9.19.25-185-g392e7199df2-1-Debian <<>> tryhackme.com mx
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 34315
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 8

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;tryhackme.com.                 IN      MX

;; ANSWER SECTION:
tryhackme.com.          300     IN      MX      5 alt2.aspmx.l.google.com.
tryhackme.com.          300     IN      MX      1 aspmx.l.google.com.
tryhackme.com.          300     IN      MX      10 alt3.aspmx.l.google.com.
tryhackme.com.          300     IN      MX      10 alt4.aspmx.l.google.com.
tryhackme.com.          300     IN      MX      5 alt1.aspmx.l.google.com.

;; ADDITIONAL SECTION:
aspmx.l.google.com.     60      IN      A       142.250.141.26
aspmx.l.google.com.     275     IN      AAAA    2607:f8b0:4023:c03::1b
alt3.aspmx.l.google.com. 68     IN      AAAA    2607:f8b0:4023:1::1a
alt1.aspmx.l.google.com. 34     IN      A       108.177.104.27
alt1.aspmx.l.google.com. 107    IN      AAAA    2607:f8b0:4003:c04::1a
alt2.aspmx.l.google.com. 34     IN      A       142.250.152.26
alt2.aspmx.l.google.com. 2      IN      AAAA    2607:f8b0:4001:c56::1b

;; Query time: 16 msec
;; SERVER: 68.105.28.11#53(68.105.28.11) (UDP)
;; WHEN: Thu Jul 04 10:28:39 EDT 2024
;; MSG SIZE  rcvd: 317
```

A quick comparison between the output of `nslookup` and `dig` shows that `dig` returned more information, such as the **Time To Live** by default. If you want to query a 1.1.1.1 DNS server, you can execute `dig @1.1.1.1 tryhackme.com MX`.

