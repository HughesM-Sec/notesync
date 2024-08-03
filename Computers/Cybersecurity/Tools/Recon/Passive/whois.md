WHOIS is a request and response protocol that follows the RFC 3912 spec. A WHOIS server listens on TCP port 43 for incoming requests. The domain registrar is responsible for maintaining the WHOIS records for he domain names it is leasing. The WHOIS server replies with various information related to the domain requested. OF particular interest, we can learn:

- Registrar: Via which registrar was the domain name registered?
- Contact info of registrant: Name, org, address, phone, among other things. (unless made hidden by a privacy service)
- Creation, update, and expiration dates: When was the domain name first registered? When was it last updated? And when does it need to be renewed?
- Name Server: Which server to ask to resolve the domain name?

To get this information, we use a `whois` client or an online service. Many online services provide `whois` info; however, it is generally faster and more convenient to use your local whois client. Using a local Linux machine, you can access your whois client through the terminal. The syntax is `whois DOMAIN_NAME`, where `DOMAIN_NAME` is the domain about which you are trying to get more information.
###### Example:
```sh-session
┌──(kali㉿kali)-[~]
└─$ whois tryhackme.com
   Domain Name: TRYHACKME.COM
   Registry Domain ID: 2282723194_DOMAIN_COM-VRSN
   Registrar WHOIS Server: whois.namecheap.com
   Registrar URL: http://www.namecheap.com
   Updated Date: 2021-05-01T19:43:23Z
   Creation Date: 2018-07-05T19:46:15Z
   Registry Expiry Date: 2027-07-05T19:46:15Z
   Registrar: NameCheap, Inc.
   Registrar IANA ID: 1068
   Registrar Abuse Contact Email: abuse@namecheap.com
   Registrar Abuse Contact Phone: +1.6613102107
   Domain Status: clientTransferProhibited https://icann.org/epp#clientTransferProhibited
   Name Server: KIP.NS.CLOUDFLARE.COM
   Name Server: UMA.NS.CLOUDFLARE.COM
   DNSSEC: unsigned
   URL of the ICANN Whois Inaccuracy Complaint Form: https://www.icann.org/wicf/
>>> Last update of whois database: 2024-07-04T14:36:15Z <<<

For more information on Whois status codes, please visit https://icann.org/epp

NOTICE: The expiration date displayed in this record is the date the
registrar's sponsorship of the domain name registration in the registry is
currently set to expire. This date does not necessarily reflect the expiration
date of the domain name registrant's agreement with the sponsoring
registrar.  Users may consult the sponsoring registrar's Whois database to
view the registrar's reported date of expiration for this registration.

TERMS OF USE: You are not authorized to access or query our Whois
database through the use of electronic processes that are high-volume and
automated except as reasonably necessary to register domain names or
modify existing registrations; the Data in VeriSign Global Registry
Services' ("VeriSign") Whois database is provided by VeriSign for
information purposes only, and to assist persons in obtaining information
about or related to a domain name registration record. VeriSign does not
guarantee its accuracy. By submitting a Whois query, you agree to abide
by the following terms of use: You agree that you may use this Data only
for lawful purposes and that under no circumstances will you use this Data
to: (1) allow, enable, or otherwise support the transmission of mass
unsolicited, commercial advertising or solicitations via e-mail, telephone,
or facsimile; or (2) enable high volume, automated, electronic processes
that apply to VeriSign (or its computer systems). The compilation,
repackaging, dissemination or other use of this Data is expressly
prohibited without the prior written consent of VeriSign. You agree not to
use electronic processes that are automated and high-volume to access or
query the Whois database except as reasonably necessary to register
domain names or modify existing registrations. VeriSign reserves the right
to restrict your access to the Whois database in its sole discretion to ensure
operational stability.  VeriSign may restrict or terminate your access to the
Whois database for failure to abide by these terms of use. VeriSign
reserves the right to modify these terms at any time.

The Registry database contains ONLY .COM, .NET, .EDU domains and
Registrars.
Domain name: tryhackme.com
Registry Domain ID: 2282723194_DOMAIN_COM-VRSN                                                                                                                                                   
Registrar WHOIS Server: whois.namecheap.com                                                                                                                                                      
Registrar URL: http://www.namecheap.com                                                                                                                                                          
Updated Date: 2021-05-01T19:43:23.31Z                                                                                                                                                            
Creation Date: 2018-07-05T19:46:15.00Z                                                                                                                                                           
Registrar Registration Expiration Date: 2027-07-05T19:46:15.00Z                                                                                                                                  
Registrar: NAMECHEAP INC                                                                                                                                                                         
Registrar IANA ID: 1068                                                                                                                                                                          
Registrar Abuse Contact Email: abuse@namecheap.com                                                                                                                                               
Registrar Abuse Contact Phone: +1.9854014545                                                                                                                                                     
Reseller: NAMECHEAP INC                                                                                                                                                                          
Domain Status: clientTransferProhibited https://icann.org/epp#clientTransferProhibited                                                                                                           
Registry Registrant ID:                                                                                                                                                                          
Registrant Name: Redacted for Privacy                                                                                                                                                            
Registrant Organization: Privacy service provided by Withheld for Privacy ehf                                                                                                                    
Registrant Street: Kalkofnsvegur 2                                                                                                                                                               
Registrant City: Reykjavik                                                                                                                                                                       
Registrant State/Province: Capital Region                                                                                                                                                        
Registrant Postal Code: 101                                                                                                                                                                      
Registrant Country: IS                                                                                                                                                                           
Registrant Phone: +354.4212434                                                                                                                                                                   
Registrant Phone Ext: 
Registrant Fax: 
Registrant Fax Ext: 
Registrant Email: a70a4ff6d25041a48378997194f9e834.protect@withheldforprivacy.com
Registry Admin ID: 
Admin Name: Redacted for Privacy
Admin Organization: Privacy service provided by Withheld for Privacy ehf
Admin Street: Kalkofnsvegur 2 
Admin City: Reykjavik
Admin State/Province: Capital Region
Admin Postal Code: 101
Admin Country: IS
Admin Phone: +354.4212434
Admin Phone Ext: 
Admin Fax: 
Admin Fax Ext: 
Admin Email: a70a4ff6d25041a48378997194f9e834.protect@withheldforprivacy.com
Registry Tech ID: 
Tech Name: Redacted for Privacy
Tech Organization: Privacy service provided by Withheld for Privacy ehf
Tech Street: Kalkofnsvegur 2 
Tech City: Reykjavik
Tech State/Province: Capital Region
Tech Postal Code: 101
Tech Country: IS
Tech Phone: +354.4212434
Tech Phone Ext: 
Tech Fax: 
Tech Fax Ext: 
Tech Email: a70a4ff6d25041a48378997194f9e834.protect@withheldforprivacy.com
Name Server: kip.ns.cloudflare.com
Name Server: uma.ns.cloudflare.com
DNSSEC: unsigned
URL of the ICANN WHOIS Data Problem Reporting System: http://wdprs.internic.net/
>>> Last update of WHOIS database: 2024-07-04T12:35:27.43Z <<<
For more information on Whois status codes, please visit https://icann.org/epp
```
As you can see, it returns with a lot of information. Notice that we were redirected to `whois.namecheap.com` to get our info. In this case, `namecheap.com` is maintaining the WHOIS record for this domain name. We can also see the creation date, last-update date, and expiration date.

Other information obtained is info about the registrar and registrant. We can find the registrant's name and contact info unless they are using some privacy service. We can get admin and tech contacts and domain name servers also.

The information collected can then be inspected to find additional attack surfaces, such as social engineering or technical attacks.

It is important to note that due to automated tools abusing WHOIS queries to harvest email addresses, many WHOIS services take measures against this. They might redact email addresses, for instance. Moreover, many registrants subscribe to privacy services to avoid their email addresses being harvested by spammers and keep their information private.