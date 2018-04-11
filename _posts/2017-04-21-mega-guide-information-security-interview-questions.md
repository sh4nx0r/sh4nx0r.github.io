---
layout: post
title: "The Mega Guide to Information Security Interview Questions."
description: Information Security Terminologies and Interview Questions for Security Enthusiasts.
headline:
modified: 2017-04-21
category: infosec
tags: [infosec, interview questions, pentesting, security analyst, infosec questions,  ]
imagefeature: blogimages/2017-04-21/cover-2017-04-21.jpg
mathjax:
chart:
comments: true
featured: true
---

Almost **<font color='red'>150</font>** questions and still counting, I've been contributing to this post on a regular basis. This is beneficial for anyone who wants to recall their knowledge on information security topics. This can also be used as a **Guide** to prepare for Information Security Openings. The Information Security topics were intentionally shuffled to achieve robustness.

> ## ***Errata & Contributions***

Even though I have taken every care to ensure the accuracy of the content, mistakes do happen. Incase if you come across any errors or typos, either you can write to me or **make changes wherever necessary in the below linked repository**. Any one of that will be highly appreciated. Contribution to this guide is welcome.
{: .notice}


> ## ***The Repository***

[![loading...](https://img.shields.io/badge/fork-repository-brightgreen.svg)](https://github.com/sh4nx0r/sh4nx0r.github.io)
{: .notice}


---

### 1. What is a ***Repudiation Attack***?

An attacker can prove a vulnerability exists in an application without actually denying the attack made by him/her. This example can be compared with _Google Hacking_. The attacker would have used Google Dork to find a weakness in the website without directly penetrating it. One more classic example would be the same website may have an information disclosure vulnerability in one of their pages if the error wasn't handled properly. Repudiation Attacks may also be termed as **_Passive Attacks_**.

### 2. What is a ***False Positive, False Negative, True Positive*** and a ***True Negative***?

Let us consider we have an automated scanner and we use that to scan a website and it generates alerts. Using this scenario let us classify the above terms as below.

**False Positive**: The scanner finds some vulnerabilities and alerts. Actual case is the website is not prone to attacks the scanner found. <font color='green'>The site is safe.</font> _This is an annoying alert as it eats away precious time of the security analyst to verify the vulnerabilities._

**False Negative**: The scanner does not find any vulnerabilities and alerts no attacks found. Actual case is the website is prone to vulnerabilities. <font color='red'>The site is unsafe.</font> This is a critical situtation as the scanner was not able to find out the vulnerabilities.

**True Positive**: The scanner finds vulnerabilities and alerts. Actual case is the website is prone to vulnerabilities. _Expected behavior of an automated scanner._

**True Negative**: The scanner does not find any vulnerabilities and alerts.

### 3. What is the key difference between ***Penetration Testing*** and ***Vulnerability Assessment***?

**Penetration Testing** is a process of breaking into the system and trying to gain the maximum privilege on the network. The ultimatum here is to get to the deepest level inside a network. This process is more like how an intruder would penetrate except there will be no damage caused. The steps must be properly documented on how the actions were performed to gain the highest privilege.
<br>**Vulnerability Assessment** is a process of listing out all weaknesses in the machine (either by using a tool/manual ways) that is being assessed and list out the vulnerabilities in the highest order of risk. This process stops with this and does not further delve as of Penetration Testing.

### 4. How to define ***CSRF*** attack in an easier way?

**Cross Site Request Forgery** or **CSRF** is a vulnerability in a website that allows an attacker to trick an end-user (victim in this case) into performing malicious operations without their knowledge in the background.

### 5. Which is more important to fix ***Threat*** or ***Vulnerability***?

Threats can be classified as _Inside Intruder, Natural Disasters, etc._ whereas Vulnerabilities can be classified as weaknesses such as _SQLi, XSS, CSRF, Non-Availability of Bunkers for protection against natural disasters, etc._ A Threat **must** make use a Vulnerability to exploit or create damage to the data. So, it is important to fix vulnerabilities first than to focus on threats. Sometimes this can also be counter-intuitive, an insider working for an organization may pass vital information (_eg: admin credentials_) to an outside intruder. The outsider can directly login to the application with the credentials and can cause damage to the data (in this case, the outsider did not make use of any vulnerability to exploit the application).
<br>Hence, there is no perfect answer that can be provided to the above question.

### 6. How do you stop ***Brute-Force Attacks***?

- Adding a **CAPTCHA** functionality to the login forms.
- Enforce **account lockout mechanism** for a maximum of three to four wrong attempts.
- Fastest fix for a temporary period would be **blocking the ip address** that is making the brute force attempts.
- **Authentication Delays**.

### 7. What's the difference between an ***Exploit*** and a ***Payload***?

An **exploit** is the medium in which the payload is contained. Both represent a _piece of code_, but a payload does contain the actual attack whereas an exploit can be termed as a _carrier_. To make the explanation more clear and precise, take a Gun for an instance. The _Gun_ is the exploit whereas the _Bullet_ is the actual payload.

### 8. Why is encryption used for confidentiality instead of encoding?

Encryption and Encoding uses _publicly available algorithms_. Encoding is not used for confidentiality purposes since the content that has been encoded using algorithms like (_Base64, UTF, etc._) can be reversed with their available algorithms and there is no secret key involved. In an encryption scheme like an (_AES, 3-DES, etc._) they have corresponding encryption and decryption algorithms which involves a common secret key.

### 9. Which type of scan is performed by NMAP through default settings?

Nmap uses a **SYN** scan by default unless we specify anything. -sS will be the default setting for Nmap. SYN scans are faster as they do not create the Three-way-handshake (SYN-><-SYN-ACK->ACK). Instead of the ACK, the SYN scan sends an RST packet, thus the connection will be closed and there won't be any chances for DoS condition. SYN scans were previously called as _Stealth Scans_ as the logging devices do not record activities since a three-way-handshake wasn't established. Nowadays, the devices do record activity of SYN scans too, so it is not fair to call it as a _Stealth Scan_ anymore.

### 10. On which port, does Nessus run?

**8834**. Nessus can be accessed through any browser by accessing https://127.0.0.1:8834.

### 11. How do you differentiate ***Bind Payloads*** and ***Reverse Payloads***?

**Bind Payloads** are a piece of code which is sent by the attacker to the target machine. The exploit then runs on the machine as a process on a certain port say 4444 passively. The attacker can connect to this target by establishing connection to this port.
<br>**Reverse Payloads** are also a piece of code that is sent by attacker and in the background the attacker runs another process that keeps listening to the port say 4444., when this exploit is executed, the target machine immediately sends a connection to the attacker machine that is passively listening on the background.

### 12. What is a ***Promiscuous Mode*** and ***Non-Promiscuous Mode*** while capturing packets with a packet sniffer?

In a **Promiscuous Mode** whichever packets that reaches the Network Interface Card is compelled to accept eventhough it was not intended for that NIC's MAC address. That's one of the reason we mostly sniff traffic using this mode. In a **Non-Promiscuous Mode**, the packets are processed only if they are intended for that NIC's MAC address, others are discarded as it is.

### 13. What is an Open Redirect?

It resides in one of the OWASP Top 10, this happens in a site which does not properly validate parameters that happens during a redirect. For instance; _Consider this URL http://www.example.com/login.aspx?redirect=profile.php. What an attacker does is that he could use this opportunity to redirect the logged in users to his/her site by crafting a URL like this. http://www.example.com/login.aspx?redirect=http://somemaliciouswebsite.com_

### 14. How would you rate or rank a vulnerability based on your findings?

This depends on how much impact the vulnerability could affect your business. An example can answer this question, _During an audit say you discover XSS and SQLi vulnerabilities. Both are equally dangerous, but in our scenario, we rank XSS as the first most since the database that has the SQLi is not a production one and it is just holds some sample data. Thus we need to rank a vulnerability based on the risk factor._

### 15. What is an Active Directory? How does LDAP differ from Active Directory?

**Active Directory** is Microsoft's implementation of directory service that provides information about the system, user's activities, policies, etc. **LDAP** (_LightWeight Directory Access Protocol_) is a protocol that is used to query the directory services (_in this case, the Actual Directory_).

### 16. Give a simple difference between Authorization and Authentication?

_Authorization_ is a process whereas an _Authentication_ is a method. Authorization takes place during Authentication. This can be made clear with an example, Consider an ATM, you use your card to **authenticate** to that machine and once you have entered the correct pin you are **authorized** to do transactions.

### 17. Can you perform a simple MiTM on a mobile phone?

Spawn a _rogue wireless access point_. Wait for the victim to connect to your AP. You can now intercept the communication.

### 18. When you deal with a stream of confidential data to be transferred across the channel, what would you do first. Encrypt or Compress?

Any compression algorithm will look for certain patterns in the data to perform compression. When the data is encrypted, the compression algorithm will find it hard to compress the data (or it may not compress the data at all). So, the better option would be. **Compress and then Encrypt**.

### 19. How do you prevent CSRF Attacks?
Use **random tokens** for each session and transaction. When an end-user logs to that application, let the application create a token for that session. That token should be included in every transaction. You can also use **CAPTCHAs** to prevent CSRF attacks.

### 20. Which is better. Closed ports or Filtered Ports?
During a scan, closed ports respond to scanners (_port scanners like nmap_) saying that the service is not running, whereas filtered ports do not respond to scanners. So, it is sometimes better to have filtered ports as they increase scanner times by not responding, but it also gives a hint to hackers that a service is running on the port but it is being blocked.

### 21. What's a Rainbow Table and a Rainbow Cracker?
Rainbow Tables are pre-computed hashes that was generated using cryptic or one-way hash algorithms. For instance, say we are subjecting a plaintext _secret_ to a one-way hash algorithm and
it generates a hash _eabecfe_. This hash and the corresponding plaintext will be stored in a table. This table is called as the Rainbow Table. It is just a repository that holds hashes that
were pre-computed and stored.
<br>
Rainbow Cracker makes use of Rainbow Tables to do the cracking process, it is a time-memory tradeoff so the process will be faster.

### 22. How do you use netcat to listen and connect through two different machines/VMs?

Say there are two machines A and B, If you want connect to A from B, then start a listener in A by running the command `nc -vvlp 2334` and execute `nc
192.168.1.2 2334` (_where 192.168.1.2 is the IP address for machine A_) on machine B.

### 23. State some differences between Netcat and Ncat.

**Netcat** is available in almost all versions of linux. Ncat will replace Netcat in future versions on linux probably. Ncat has SSL support between connections, also supports Proxies and IPv6.

### 24. Contrast Hubs. Switches and Routers

**Hubs:** Not expensive. Data collision may occur as traffic intended for one machine will reach all the machines in the network. This also results in wastage of bandwidth. This may also
result in information leak as a packet sniffer can be used to capture packets that was not intended for the machine. They operate on the Physical layer as they deal with bits.

**Switches:** They are bit expensive compared to Hubs but they are way more smarter. The switch uses a table within to make track of the MAC addresses associated with the computers on the
network. Switch acts as a hub in the beginning (transmits data to all machines when the table is empty) and learns about the addresses and during the next data transfer, the switch refers to
the table, reads the route (address) and then transfers to the target without transmitting throughout the network. They operate of the Data Link layer as they deal with MAC
addresses.

**Routers:** They are expensive than Switches. Ultimately they do Network Address Translation(NAT) which helps you connect to the Internet. They have support for DHCP and it helps in
automatically configuring ip addresses for multiple machines on the network. They operate on Network layer as they deal with IP addresses.

### 25. Which protocol does DNS use?

DNS requests make use of UDP protocol instead of TCP. UDP protocol are unreliable when compared to TCP, but they are faster when compared to TCP. The load factor is very important
when it comes to DNS, since TCP makes use of a _three-way-handshake_., it will be a little slower than UDP.

### 26. State a few steps you would use to secure a Linux machine.
- Use `faillog` command to set user account lockouts after certain failure attempts.
- Ensure the linux kernel and software are up to date.
- Never use root account to login, use sudo command whenever necessary.
- Disable unwanted services with high privileges.
- Check for world writeable files and disable it wherever necessary.

### 27. If there are a total of 65535 TCP Ports, then how many UDP Ports are available?
There are **65535** UDP ports as well.

### 28. How to check for Click-Jacking and state atleast one method to prevent it?

Write a normal html code, add an iframe something like this `<iframe src="vulnerableClickJackingSite.com">`, save it as test.html. Open this html in the browser. If vulnerableClickJackingSite.com
opens within the iframe, then the site is vulnerable to Click-Jacking.

**Prevention:** By configuring X-Frame Options Headers to `DENY` or `SAMEORIGIN` or the site using `ALLOW-FROM`. See the code below.

`X-Frame-Options: DENY` <br>
`X-Frame-Options: SAMEORIGIN` <br>
`X-Frame-Options: ALLOW-FROM https://example.com/`

### 29. List some steps in securing any Web Application.

- Make sure _Security Testing_ is part of the SDLC.
- If not, immediately _enforce VA_ on the application and find the vulnerabilities.
- Remediate the vulnerabilities and redo the VA to make sure they are gone.
- Go for PT of the web application, if required.
- Perform security checks every once in a while, depending on the application active releases.
- Install a web-application firewall if necessary.

### 30. List some steps in securing any Web Server.

- Check whether the webserver is up to date and does not contain any vulnerabilities.
- Install an application monitoring tool like New Relic to monitor the requests.
- Make sure certain services are not running with root/SYSTEM level privileges.
- Ensure PT is done on the webserver atleast once.
- Periodically check for available patches.

### 31. Compare and Contrast NIDS and HIDS.

NIDS are deployed in _strategic points_ like in DMZ and other inter connections of the network, whereas HIDS are deployed on individual hosts. NIDS are the first line of defense whereas HIDS are considered as the last line of defense. NIDS has a greater challenge to inspect encrypted packets whereas HIDS will be able to analyze those packets as well.

### 32. How do you assess security stance of a VPN?
- Scan for VPN gateways availability.
- Fingerprint it and determine the vendor and configuration information.
- Check for vulnerabilities associated with the VPN vendor.
- Capture PSK (Pre-Shared Keys).
- Perform offline PSK cracking.
- Check for the default user account information.

### 33. Why a methodology for Pen-Testing is important?

A methodology protects the assessing organization from _legal and liability_ issues since the steps have already been pre-approved by the client. It also effectively manages time and does not let the tester to miss any important engagement phases.

### 34. State some effective pen-testing methodologies of date.

- **ISSAF**: Information Systems Security Assessment Framework.
- **OSSTMM**: Open Source Security Testing Methodology Manual.
- **OWASP**: Open Web Application Security Project.
- **PTES**: Penetration Testing Execution Standard.
- **OWTF**: Offensive Web Testing Framework.

### 35. Explain OSINT

**Open Source Intelligence** (OSINT) is a type of reconnaissance of the target that is available on public sources and on the internet. This can also be considered as collection of data about the target through Google Hacking, gathering DNS and other information through websites like _Shodan, Netcraft. etc._ Mostly, this would be a passive reconnaissance.

### 36. List some pointers for a Mobile Threat Model.

- User may connect to a rogue wireless access point such that their sensitive information can be tapped.
- User may download infected/malicious app from PlayStore/iStore (if they miss some security checks) and other unsigned and non-verified apps from the internet.
- User may tap a link that was received through SMS or any IM which is malicious.
- User may visit some sites that is serving infected scripts.

### 37. State the simple Nmap command to invoke a general vulnerability assessment script on any domain.

`nmap -sV --script=vuln www.somewebsitetoscan.com`

### 38. Contrast some important DNS tools for Pentesting

- **dnsrecon** : Finds the A record, MX hosts, Nameservers, etc.
- **dnstracer** : Finds where the DNS gets its information from.
- **dnswalk** : More or like a debugger, checks the domains for consistency and precision.
- **fierce** : One of the most used DNS tools by the pentesters. Smartly attempts zone transfers and brute-force attacks to gain further DNS information.

### 39. How different is the ***tracert*** command in Windows compared to the ***traceroute*** command in Linux distributions like Kali?
Windows **tracert** uses ICMP echo requests whereas Kali **traceroute** uses UDP datagrams.

### 40. List some types of MiTM attacks.
- ARP Poisoning
- ICMP Redirection
- Port Stealing
- DHCP Spoofing

### 41. Explain Stateless and Stateful Firewalls.
**Stateless Firewalls** does not keep track of packet flow whereas **Stateful Firewalls** do, they can also tell if the packets are fragmented or changed. Stateless Firewalls are faster and they
can deal with heavy network traffic and their performance will be more effective. Stateful Firewalls will be more effective on less traffic scenario.

### 42. How do you implement security in the Software Development Life Cycle (SDLC)?
- Secure Coding Practices document must be followed by the development team. The security team should assist the development team if any queries raised.
- Security must be implemented in test cases and use cases as well.
- Make use of code scanning tools to scan the application for vulnerabilities and remediate the same.
- Security awareness trainings and latest threats should be kept informed to the development team.

### 43. Explain XPath Injection Attack.
**XPath** is a language that is very similar to SQL which is used to address XML documents. XML databases use XPath as their standard query language, Again similar to SQL Injection, there
exists XPath Injection. Even **XPath Injection** _is done by the usage of a single quote (')_. The attack is carried out in depth by knowing the errors that the XML parser throws. There also
exists Blind XPath Injection Attack, which is carried out with the help of result set returned.

### 44. What is an Incident Response Plan and a Disaster Recovery Plan? Are they same?
**No**_, they are not the same_. An _Incident Response Plan_ is a set of steps that must be followed immediately when an incident happens, for instance, A fire outbreak in a building is an
incident, an incident plan would be: usage of fire extinguishers to douse the fire, call the fire personnel, use the stairs, etc. That would be a clear example for that. _A Disaster Recovery
Plan_ comes in effect after the execution of Incident Response Plan. It also lists efficient steps that must be followed once the disaster has occurred. For instance; Restore backups from
Cloud Storage, Refurnishing the office, etc.

### 45. How to prevent website from ***Google hacking*** or getting dorked?
Use a **robots.txt** to tell the search engine which pages to crawl and what not to. Remove sensitive data from the web, if that's not possible use better authorization schemes to protect it
from getting viewed from outside world. _If site traffic does not matter to you, it's better to remove your website from Google Indexing_.

### 46. How does a Digital Signature differ from a Digital Certificate?
A **digital signature** is a mechanism that is used to verify that a digital document or a message is authentic. For eg: _If you want to send some confidential mails to other party
confirming that you are actual sender_. A **digital certificate** is a certificate issued by a trusted third party called a Certificate Authority (CA) to verify the identity of the certificate
holder. For eg: _SSL certificate for a website_.

### 47. List the type of Security Frameworks.
- ISO
- NIST
- COBIT
- COSO
- HITRUST CSF

### 48. Consider you are in the internal network of an organization, you need to find the Operating System of another machine in the same network without using any tools. What command would you use under a Windows Environment?
`systeminfo /s`.

### 49. State BYOD and its merits and demerits.
**BYOD** - _Bring Your Own Device_ is a type of policy in any organization that lets employees to bring in their own computers, laptops or other devices that would let them connect to office's network and do the official work. Employee's personal devices maybe faster than that of the gadgets their companies provide. Worst part is if the personal gadget is affected by any virus or malware it will spread through the entire network.

### 50. What are the different modules of Metasploit Architecture?
- Auxiliary
- Encoders
- Exploits
- Nops
- Payloads

### 51. Can you give a real-time example for a Threat, Risk, Vulnerability, Exploit and a Payload?
This is my own example (correct me if am wrong). _Let us consider an encounter between a Cop and a Gangster. The Cop is held by the Gangster in a Gunpoint situation and threatening him to
provide intel on the remaining cop's location_. We can relate this scenario to our question.

- Threat: The Gangster
- Vulnerability: The Unarmed Cop.
- Exploit: The Pistol the Gangster holds.
- Payload: The loaded bullet in the Gun.
- Risk: The Intel being disclosed.

### 52. Explain the three different security controls.
- **Physical Controls**: They are the first line of defense. Physical controls include Gates, Walls, Fences, Cameras, Locks, etc. This is the most critical aspect of Security Controls.
- **Logical Controls**: Otherwise termed as technical controls, they constitute authentication schemes that are used to protect unauthorized access to terminals. (eg,. Passwords). Also
Firewalls, Intrusion Detection and Prevention Systems, etc.
- **Administrative Controls**: They are more or like Policies, Procedures and Guidelines that are to be followed. (eg., A password policy stating that the password must be changed every 30 days)

### 53. Contrast ***Defense in Depth***.
**Defense in Depth** is also known as Layered Security that enables multiple security countermeasures in every level to make sure CIA (_Confidentiality, Integrity, Availability_) of data is intact. It uses multiple approach to protect the data being penetrated by attackers. For eg. Having multiple security measures at the external network, internal network, etc.

### 54. Name the attacks that affects the CIA Triad.
Just listing a single attack for each type.
- **Confidentiality**: Man in the Middle Attack
- **Integrity**: SQL Injection Attack
- **Availability**: Denial of Service Attack

### 55. Which takes place first. ***Authentication*** or ***Authorization***?
**Authentication** _takes place first and then followed by_ **Authorization**. Easiest way to remember is, you authenticate yourself to any terminal or device using authentication methods (what you are, what you have & what you know), thus the system checks whether you are authorized to use the terminal.

### 56. How Deep Packet Inspection Firewalls are better than Packet Filtering Firewalls (***Stateful & Stateless***) and depict their challenges too.
The DPI Firewalls not just inspects the traffic but the contents inside it which makes them very effective to block nefarious packets. They are _relatively slow_ compared to packet filtering firewalls and also there is a privacy at stake since it can read almost any content.

### 57. What is an ***Endpoint Security*** and how does it work?
A centralized approach to ensure protection on all endpoints like _Desktops, Laptops, Tablets, Smartphones, IoT devices_ connected to corporate network is **Endpoint Security**. Endpoint Security works on a client-server model. In the network, the EndPoint Software will be installed on a centralized device like a Server and client software will be installed on End Point devices as mentioned above. An Endpoint Security model is very useful on a BYOD scenario., When a user brings his/her personal laptop with malware infection, the centralized server gets an alert. Endpoint Security Software Solutions does come with _inbuilt Firewall, AntiVirus and AntiMalware Softwares, etc._

### 58. What does an ***SIEM*** device do?
**SIEM** is the acronym for Security Information and Event Management (SIEM). These devices basically collect logs from all of the security devices like Firewalls, IDS, etc and lets you manage from a centralized dashboard. It helps you easily correlate, search, identify and investigate events and activities that is deemed to be critical.

### 59. Does ***Active Directory Domain Services*** really neccessary for any organization?
_Definitely_ it is required for a business organization as it helps the administrators to collectively gather information about the network computers, users, policies, etc as a Centralized Desktop Management. Active Directory also provides support for Exchange and Sharepoint services.

### 60. What's an Interactive Logon and what are the types associated with it?
May sound confusing for some, an interactive logon is nothing but a method to logon to the computer or workstation. A new session can be initiated by **CTRL+ALT+DEL**. Local Logon (SAM), Domain Logon (Active Directory) & Smartcard Logon (Hardware Token) are the types associated with it.

### 61. List the attacks associated with the OSI Layer Model.
- **Physical Layer**: WarDriving, physically plugging a Keylogger Device, WireTaps
- **Data Link Layer**: MAC Address Spoofing, Sniffing, Snorting, WEP/WPA Hacking
- **Network Layer**: Fragmentation Attacks, Ping Attacks, Routing Protocol Attacks, ARP Poisoning
- **Transport Layer**: DoS Attacks, MiTM Attacks, SYN/ACK/FIN Attacks, Port Scans
- **Session Layer**: Session Hijacks, DoS Attacks, NETBIOS Attacks.
- **Presentation Layer**: HTML Code Inspection and Corrupt or Malicious Controls
- **Application Layer**: Trojans, Worms, Viruses

### 62. How does ***Port Security*** works on a Switch?
**Port Security** is a feature in which the MAC Addresses are cached. The communication takes place only if there is a match with the cached MAC table, if an attempt to connect to the port with
a different MAC is found then the administrator gets notified.

### 63. What are the layers of TCP/IP Model and how does it relate to OSI Layer?
There are four layers when it comes to the TCP/IP Model. Application, Transport, Internet and Network. This is how the layers are associated with OSI Layer.
- **Application Layer**: Application + Presentation + Session
- **Transport Layer**: Transport Layer
- **Internet Layer**: Network Layer
- **Network Layer**: Data Link + Physical

### 64. What do you mean by ***Least Privilege***?
**Least Privilege** can be a rule or policy in which a user has access to exactly what he/she needs for their current user role.

### 65. How would you employ ***Defense in Depth*** security on the OSI Model?
- **Physical Layer**: Fences, Surveillance Cameras
- **Data Link Layer**: Port Security in the Switches
- **Network Layer**: Setting Access Lists in the Border Routers, IDS/IPS
- **Transport Layer**: VA, Setting DMZs and Enabling Packet Filtering in the Firewalls, IDS/IPS
- **Session Layer**: VA, IDS/IPS
- **Presentation Layer**: VA, IDS/IPS
- **Application Layer**: VA, IDS/IPS, Virus and Malware Scanning

### 66. What is a ***Unified Threat Management*** (UTM) Device?
A **UTM** comprises of multiple software and hardware devices like _Firewalls, IPS/IDS, AntiVirus, AntiMalware, Web Filtering etc._ in a single device.

### 67. List the steps that are required to be PCI Compliant.
- Build and maintain a secure network (Proper firewall configuration and not using any default credentials)
- Protect the card holder data.
- Perform periodic VAPT assessments.
- Implementing strong access control measures. (Ensure Least Privilege properly)
- Regularly monitor and Test networks.
- Maintain an Infosec policy.

### 68. What's a ***DMZ***?
A DMZ (_Demilitarized Zone_) is otherwise referred to as a Perimeter Network, that exposes external facing servers like routers, firewalls, etc to the Internet. It can also be termed as a
segmented network whose access is secured by a Firewall.

### 69. State the six-step approach to Pentest Methodology of ***Core Impact***.
- Passive Intelligence Gathering
- Active Intelligence Gathering
- Exploitation
- Privilege Escalation
- Cleanup
- Report Generation

### 70. Does Firewall affect the time required to scan a target?
**Obviously**. In most cases, the firewalls are configured to drop the unauthorized packet **without** sending _connection refused_ message. In this case, the host which is scanning the target
must have to wait for a minimum time before it knows that the connection will not be succeeded. Hence, this will affect the scanning time of the target. There are some smart
scanners that will tell you to increase timeouts depending on outcome of the scan.

### 71. How authentic is ***Banner Grabbing***? Can you go by the results?
We _cannot totally rely_ on Banner Grabbing results. Smart administrators try to fake the banner information by representing a linux webserver look like a Windows webserver. They can also
change the version information of certain services and applications and mislead the hackers by falling into their honeypot.

### 72. What is ***Competitive CounterIntelligence***?
Competitive Intelligence is not just the process of collecting information about competitors and their intelligence, but also about customers, stake holders, etc that aids in the decision
making process of the organization. More importantly this is an ethical process and does not relates to Industrial Espionage (spying an organization) which is unethical.
When it comes to our question, **Competitive CounterIntelligence** mainly protects the organization publicly available information or data from being siphoned or tapped by its competitors.

### 73. How do you crack ***WEP***. Explain in High Level.
Assuming you have a Wireless Adapter that is capable of packet injection.
- Use `airmon-ng` to get to know your network interface cards.
- Enable the Wireless Adapter to Monitor Mode.
- Start capturing the traffic from the specific AP.
- Use `aireplay-ng` to Inject ARP Traffic (Perform ARP Spoofing) and capture the IVs
- Use `aircrack-ng` to crack the IVs. (More the IVs the faster the cracking process will be)
- The key will be displayed on the screen in a hexadecimal format.

### 74. What would you do if you need to send sensitive data over an untrusted network.?
_Encrypt the data_ using a _strong data algorithm_ and send it across over the untrusted channel.

### 75. How do you ***harden*** a server?
- Removing uneccessary softwares.
- Removing unused services.
- Perform changes on default accounts.
- Use the principle of least privilege.
- Ensure timely software updates.
- Implementing logging and auditing.

### 76. What is an ***Attack Surface***?
The entry points where an attacker could reach the legitimate application is referred to as an **Attack Surface**. Say for instance, _An organization serves FTP and Mail server that can be
accessed publicly, then the total attack surface value will be two_.

### 77. Why do you need a ***Host Based Firewall*** when you already have a ***Network Level Firewall***?
**Network perimeter firewalls** cannot provide protection for traffic generated inside a trusted network. For this reason, host-based firewalls running on individual computers are needed.
**Host-based firewalls**, of which Windows Firewall is an example, protect a host from unauthorized access and attack. In addition to blocking unwanted incoming traffic, you can configure
Windows Firewall to block specific types of outgoing traffic as well.

### 78. How to respond to a ***Malware Attack*** on a corporate network?
- Make sure the malware is quarantined by the AntiVirus/AntiMalware software.
- Check the name of the malware reported by the Software and note down their malicious activities.
- Ensure those malicious activities have not been in action.
- If suspiscious action found, try to unplug the device from the network to avoid further infection on the corporate network.
- Update the Antivirus or Install a better Endpoint security product and do a full scan on the machine.
- If the infection persists, try to back up critical data (scan it and make sure they are not infected).
- Do a fresh install of the Operating System. Restore the non-infected data.
- Install all latest security patches, end point security, host-based firewall, Antivirus and Antimalware products.
- Plug the machine back to the network.

### 79. Explain the components that come with ***Burp Suite***.
- **Target**: In this tool/interface, the information regarding the scanning target is shown. This also includes the vulnerabilities and links discovered.
- **Proxy**: This acts as a web proxy between the browser (where you configure the proxy settings) and the web application server. Acts as a MiTM interface, that intercepts requests before sending it to the web application.
- **Spider**: It crawls the web application for links and pages and lists it out in the Target section.
- **Scanner**: This comes with the professional version of the Burp Suite tool. This is basically a web vulnerability scanner that is used find web related vulnerabilities in any application.
- **Intruder**: This tool can be highly customizable and can be even used to launch a brute-force attack.
- **Repeater**: This tool can be used to manually issue a HTTP request and analyze the response.
- **Sequencer**: The tool analyzes randomness of user session tokens as well as for CSRF tokens. By determining predictable sessions, the analyst will be able to impersonate users.
- **Decoder**: This tool is mostly used for quick operations like encoding and decoding of algorithms like Base64.
- **Comparer**: This tool is to compare chunks of data and see the difference in a "git" diff like viewable format.
- **Extender**: This interface lets you import plugins for Burp Suite.

### 80. How do you use ***WebGoat*** to find vulnerabilities in a website?
_Well this was a honeypot question_, **WebGoat** is not a vulnerability scanning tool, it is a deliberately built insecure web application by OWASP such that it can be made use by security
analysts or anyone who wants to test their information security skills.

### 81. What would happen if an attacker gets hold of your website SSL's private key?
The attacker would then be _able to decrypt communications_., there are even chances that the attacker would be able to read the previous SSL sessions by decrypting it using the private key,
**unless forward secrecy** is implemented.

### 82. How to implement ***Forward Secrecy***?
**Forward Secrecy** can be implemented using the recommended Elliptic Curve Diffie Hellman Key Exchange Algorithm (ECDHE). ECDHE is faster than normal Diffie Hellman. Since the session keys are
not linked to the server's key pair, eventhough if the attacker gets hold of the private key, the SSL session cannot be decrypted.

### 83. Can you state any one method to deface a website without using any tool?
Assuming the website has a stored XSS vulnerability. An attacker can easily inject a javascript with `location.href` tag and redirect to any site of his/her choice.

### 84. Given an IP Address how will you determine the Operating System it is running?
There is no 100% effectiveness to determine the operating system of a remote machine. However certain tool like `xprobe2` is used to guess the operating system to a certain extent. It is
highly recommended over nmap.

### 85. What happens if Computer A's NIC card is interchanged to Computer B's NIC card? Will the MAC Address be the same?
**No**. Since the NICs are interchanged, Computer A will have Computer B's MAC Address and vice versa. MAC addresses are embedded in NIC cards not in the Motherboards or Microprocessors.

### 86. On which port, does ***ping*** command work and how do you ping a port?
**Ping** does not work on TCP or UDP, so obviously, it does not make use of any port. It uses ICMP. You cannot use ping command to ping a port, instead use Nmap for this purpose. To give a you
perfect illustration, ping works irrespective of port numbers. `ping sh4.in` is same as `ping sh4.in 80` or `ping sh4.in 2873687234`

### 87. Explain a simple crucial method to mitigate XSS or the Cross-Site-Scripting attack.
**Input Validation** and **Output Sanitization** are the two important methods to ward off XSS attacks.

### 88. How will you write a good penetration test report?
A penetration test report will be read not just by technical managers but also by business managers whose technical knowledge will be limited or none. The report should have detailed steps
stating how the analyst/tester made attempts in reaching the highest level of access. It is not neccessary that certain technical steps should be explained in detail, however the **executive
summary** should be drafted very well in almost _layman terms_.

### 89. Consider you are going to engage a security assessment with a client, list out some questions that you would ask them.
- Make the client understand the difference between Vulnerability Assessment and Penetration Testing, this is where most of the organizations does mistakes. So, will this be a VA or PT?
- What is the scope of the assessment, IP ranges, Timeframe, Internal and External scans etc?
- Will there be a Social Engineering assessment involved like Phishing, Fake calls, etc?
- How the assessment be like? Black Box or White Box, for instance, will a Network Topology be provided for the devices in the scope of the assessment?
- Should physical security assessments also performed? (This involves the assessing team visiting the client premises, If so the cost involved, what are the devices to be tested,
surveillance cameras, lockpicking, USB dropping, etc)

### 90. State the nmap command to scan a target and output it to an XML file without host discovery and no arp pings.
`nmap -oX out.xml -Pn --disable-arp-ping 127.0.0.1`

### 91. What's the difference between 301 and 302 HTTP Status Codes?
They both constitute redirection status codes; However, the former is permanent and the latter is temporary.

### 92. How will you generate HTML scan reports from NMap?
As of 2017, NMap does not have the feature of writing the reports to HTML format. It can output the report to XML format and from there it is possible to convert to HTML using XSLT processors.

### 93. IPTables. What are they? Set a rule to block ***google.com*** and state how effective it is.
IPTables is a Firewall Utility for Linux Operating System. You can set rules in it for the accepting, rejecting or dropping incoming, outgoing or forwarding connections. The following below rule sets the website google.com to be blocked. `iptables -A OUTPUT -p tcp -m string --string "google.com" --algo kmp -j DROP`. To be straightforward, this is not an effective way to block a website, there are better ways to do it by using certains HTTP Proxies. Any user can bypass this rule by simple typing "google.co.in" or "google.co.uk" to access the website.

### 94. What's a ***Transparent Proxy***?
**Transparent Proxy** is a type of caching proxy that is configured to sit on the gateway and intercepts the WWW requests from the client and fetches the data for the first time and the consecutive requests are cached. A Transparent Proxy can be clearly understood with these two examples.
- You come to some restaurant and you want to access their WiFi Hotspot, once you get the credentials and you connect to their WWW Gateway, You will be authorized to use the internet. Here all the data what you request and send will be routed through this proxy.
- A Content Delivery Network or a CDN can also act as a Transparent Proxy.

### 95. How do you access ***Splunk Web Interface*** by default unless specified?
Splunk Web Interface runs on port 8000 by default. It can be accessed by going to http://localhost:8000

### 96. Can you suggest an effective solution for ***encrypting data-in-rest***?
I suggest investing in SEDs. SEDs are **Self-Encrypting Drives**, they provide hardware based security by continously scrambling data using a key and descrambles the data while being retrieved with the key.

### 97. Assume a ***PKI Scenario***, You have a public and a private key, and you often perform both encryption and signing functions. Which key is used for which function?
- To perform **Signing** and send a message to the recipient, you use your **private key** to sign and send the message. The recipient will use your **public key** to verify whether the message is originally from you.
- To perform **Encryption** and send a message to the recipient, you use the recipient's **public key** to encrypt the message and the recipient will use their **private key** to decrypt the message.

### 98. How ***Meterpreter shell*** is better than normal shell on an exploited machine?
**Meterpreter** is more advanced than normal shell as you can run many commands with ease. It is _possible to dump hashes, migrate to process, easily send and receive files, take screenshots, access webcam, mouse and more_.

### 99. What's a ***Heartbeat*** and a ***HeartBleed***?
**HeartBleed** _is the vulnerability that exploits a built-in feature of OpenSSL called the **HeartBeat**_. When your browser connects to the website and requests data, the website responds back to your browser and responds with data, this is otherwise called the HeartBeat. In this vulnerability, the attacker can craft a request in such a manner that the server responds back with data from the server's memory beyond the total data of the initial request, up to 65,536 bytes. These bytes may contain more sensitive information like server config, passwords, etc.

### 100. You notice some brute-force attempts happening on your server every five minutes, as you can infer this is a near futile attempt can you guess the motive behind this attacker?
The attacker is smart, as he is playing in a _defensive way_ by not triggering the lockout mechanisms. The other crucial part here is the attacker is not just brute forcing your system, there are chances that the attacker is brute-forcing multiple targets and that's the reason for the idle time. The inference we assume from this scenario is the attacker's main motive is to build an **ultimate botnet**.

### 101. How will you find your internal IP address on your office network when your command prompt access is disabled?
Go to Control Panel -> Network & Sharing Center -> Local Area Connection -> Details...

### 102. What is ***Malware*** and ***Spyware***. Which is more of a threat?
More of a threat? _actually this is a brain teaser question_, Malware is nothing but _Malicious Software_, a software that tends to do malicious activities is termed as Malicious Software or Malware. **Spyware** (_spies on your browsing activities, webcam, etc_), Adware (_annoying popup ads that redirects to some phishing sites_), Ransomware (_Wannacry, sites that demand money to remove viruses_) etc are grouped under Malware.

### 103. How do you differentiate ***HotFix, Patch and Service Pack***?

- **Hotfix**: Say for instance, a few major clients are using a version of a software from a vendor and they feel that an important feature need is required and they can't wait for the next version of the product. In that case, the vendor releases a hotfix which is an add-on feature to that product. Make a note that this feature is not rolled out public.
- **Patch**: Unlike hotfixes, the patches are rolled out public. _A classic example would be WannaCry Patch_.
- **Service Pack**: This is a bundle that is inclusive of Hotfixes and Patches.

### 104. Explain the four-way handshake on Wireless Protocols.
- The **Access Point** sends a ANonce (_Nonce is a number used only once_) to the **Client**. (_Basically a random integer_)
- **Client** uses the ANonce and PMK (Pairwise Master Key) (_The PMK is generated from PSK_) to construct the PTK (Pairwise Transient Key). The Client then sends the PTK, Client's SNonce and MIC to the **Access Point**.
- The **Access Point** sends GTK (Group Temporal Key) (_The GTK is mostly derived from Group Master Key (GMK) which inturn is derived from Authenticator_) and MIC.
- The **Client** sends the ACK along with MIC.

### 105. What's the difference between XSS and CSRF attacks?
Both are client-side attacks, **XSS** can be more devastating as you can embed executable arbitrary code but with **CSRF** this is not possible. To exploit a **CSRF** attack in a website, the attacker must somehow forge a deceptive link and send it to the victim, the attack will take place only when the user clicks the link, in a real-world scenario this is hard to carry out. However, in an **XSS** attack (_in this case say a stored XSS vulnerability_), the attacker simply must inject a malicious script (_say a cookie stealing script or redirection script_) so any victim connects to that page will be affected.

### 106. Is it possible to leverage a CSRF attack using an XSS attack?
**Yes** it is possible. Assume there are two websites **Site A** (a social networking site) and **Site B** (a banking application). The victim logs into **Site B** with credentials and after a while the user navigates to the **Site A** which has XSS payload that loads stuff in the background and exploits the CSRF vulnerability on **Site A**. So, in this scenario, the attacker did not send any active link to the victim to exploit the CSRF vulnerability on **Site B**.

### 107. What's a GreyBox approach in Pentesting, Is it better than BlackBox?
The pentester is provided with ***not so much*** information about the target. However, that information provided is quite essential. Some of this information include network diagrams, services, credentials, etc but the target owner may not disclose business critical information during a grey-box test to the pentester. Greybox is obviously better than Blackbox testing as this can be justified with a compact example. _Let us assume a login panel that does not have a signup panel, in this case chances are quite faint to explore the internal dashboard and detect the vulnerabilities within_. Well in this case, the greybox testing gets an upper hand over the blackbox testing.

### 108. What's a Virus, Worm and a Trojan Horse? Are they all same?
***Virus, Worm and Trojan falls under the Malware set***, but they are not the same. **Virus** cannot cause damage unless it is invoked by user. Mostly it comes in the form of an executable and it can attach itself to another executable, but does not execute automatically without human intervention. This is not in the case of a Worm; they are a subset of Virus but they have the tendency to attach themselves to other files and can make copies of themselves. **Worms** can automatically infect a machine without user intervention. _A simple example for a worm scenario would be automatically sending a message to all your contacts in your address book_. **Trojans** are quite different and they are not meant to cause immediate havoc but their effects can be very devastating. Attackers make use of Trojan to place a backdoor in the exploited machine such that they can access the machine anytime or can also make the exploited machine act as a Bot in launching a DoS attack. Trojans give attackers full access over the machine and they behave as a command center. Trojans like Sub7 lets attacker to change the remote computer's windows settings, turn display upside down, open/close the DVD Drive, etc.

### 109. What's a Forward proxy and a Reverse proxy?

- A **Forward proxy** sits between the client and the server. Configuration should be done on the client side. The requests from the client are routed through the proxy and then reaches the server. For better understanding, a few examples can be listed out. _Say a user in Sweden wants to connect to a website that is accessible only for US residents, the user can make use of a Tor client and change the location to US and then access the website_. In this case, the ToR client acts a Forward Proxy. Another example would be, _An organization may allow access to their application through their specified proxy and port_, this restricts outside users to connect to the website unless they knew the proxy address and port.
- A **Reverse proxy** is quite different. Configuration must be done on the server side. Load Balancing is one of the concepts that comes under Reverse proxies. A high traffic website make uses of CDNs (Content Delivery Network) to balance the load on their servers; for example, _certain images, css, javascript files_ etc are loaded from third party sites.

### 110. Explain Buffer Overflow Attack in a simple way. How to prevent it?
Improper and insecure coding practices leads to Buffer Overflow Attacks. By ensuring proper coding standards and secure code development the buffer overflow attacks can be **totally mitigated**. Buffer overflow involves lots of details but the summary of it can be easily understood with the help of an example. _Consider a mobile phone number field in an application which is usually 10 characters of length, if an attacker sends 50 characters to that application, the application abruptly crashes by throwing excess data in the CPU memory_. By using certain techniques if the attacker can able to predict where the buffer data is getting overwritten, the attacker will be able to execute arbitrary code in the memory, else the program will result in a Denial of Service condition.

### 111. Can you list out the 18 Security Controls?
- Access Control
- Awareness and Training
- Audit and Accountability
- Security Assessment and Authorization
- Configuration Management
- Contingency Planning
- Identification and Authentication
- Incident Response
- Maintenance
- Media Protection
- Physical and Environmental Protection
- Planning
- Personnel Security
- Risk Assessment
- System and Services Acquisition
- System and Communications Protection
- System and Information Integrity
- Program Management

### 112. What are the sector specific regulations and standards that affect the information security professionals who work in organizations?
- Gramm-Leach-Bliley Act (GLBA)
- Sarbanes-Oxley Act (SOX 404 or SARBOX)
- Health Insurance Portability and Accountability Act (HIPAA)
- North American Electric Reliability Corporation Critical Infrastructure Protection Reliability Standards (NERC CIP)
- Payment Card Industry Data Security Standard (PCI DSS)

### 113. How do you create a ***Computer Security Defense Plan***?
- Make a list of the assets that ought to be protected.
- Assign a value to each asset _say on a scale of 1-5_ on how critical that asset is and also assign the value in which the asset can likely be compromised.
- Once all assets are identified, the security measures has to be implied. Critical assets with higher exposure risk must be given utmost importance and the remaining assets should be provided with baseline security measures.
- Perimeter Security should be tightened and all the internal devices must have Endpoint Security implemented.
- All the policies and procedures should be implemented properly.
- It is better to deploy an SIEM solution and get alerts and notifications about the devices on the network. If SIEM is out of scope, use good vulnerability scanning tools to make sure all the security holes are plugged.
- Ensure periodic assessments on the assets either quarterly or half-yearly.

### 114. How will you prevent ***ARP Spoofing***?
- Implementing Static ARP Tables
- Configure Port Rate Limiting
- Implementing DHCP Snooping and Dynamic ARP Inspection

The _most effective defense mechanism_ is to ***Combine Port Rate Limiting and Dynamic ARP Inspection***.

### 115. What are the four components of ***Security Documentation***?
- **Policies** (_Password Policy, Confidentiality and Privacy Policy, Incident Response Policy, etc_.)
- **Procedures**
- **Standards** (_Secure Coding Standards, NIST, COBIT, etc._)
- **Guidelines**

### 116. Explain a few security policies that would suit a ***manager***, ***technical staff*** and a ***normal user***.
- For a **Manager**, the policy should identify the expectations of senior management about roles, responsibilities and actions.
- For a **Tech Staff**, the policy should clarify which security controls should be in place for individual workstations, networks, physical locations, etc.
- For a **Normal User**, the policy should specify how they should use the computers, mobiles, and BYOD.

### 117. When you are assigned to create a policy, what are the factors you consider, can you relate your points with an existing policy?
- The ultimate **purpose** of the policy.
- To which **asset** the policy should be applied.
- The **rules** of the policy.

_Let us assume a password policy, the password should be changed as often as possible to prevent account getting compromised and should be consisting of numbers, symbols and capitalized alphabets. Again, a more complex password is quite hard to crack and this is the ultimate **purpose** of a password policy. **Asset** is the user account. **Rules** of the policy include setting a complex password, changing the password in every 90 days, etc._

### 118. Can you list the steps in Security Policy Development Life Cycle?
- Identify the project.
- Develop Policies.
- Review & Publish Policies.
- Maintain Policies.

### 119. What's a Kerberos Protocol?
Kerberos is a _ticket_ based network authentication protocol. The protocol was developed by MIT and the idea behind it is that this authentication protocol can be used under a hostile environment.

### 120. What's a ***Password*** and a ***Passphrase***? Which is secure and what do you suggest?
Well, part of the answer is available there in the question. **Password** can be an 8-10 digit long with mixed characters, symbols, capitalized text, etc. whereas a **Passphrase** is a sentence with spaces. A password is _only_ secure when it is a combination of symbols and numbers, whereas a passphrase can be stronger with a normal sentence. Passphrases are suggested when compared to passwords as they are easy to remember and obviously stronger.

### 121. What's a DLP and state the types associated with it?
**Data Loss Prevention** software detects potential data breaches and prevents them by monitoring, detecting and blocking sensitive data while in-use (_endpoint actions_), in-motion (_network traffic_), and at-rest (_data storage_). As of now, there are three types associated with DLP solutions.
- Network DLP
- Storage DLP
- EndPoint DLP

### 122. What can you say about ***Information Rights Management***?
**Information Rights Management** is a technology that is a subset of Digital Rights Management, _a technology that is used in the entertainment industry by the copyright owners to protect movies and music_. Information Rights Management helps prevent sensitive information from being printed, forwarded, saved, edited, or copied by unauthorized people. It can also limit the privileges to set of users from downloading and even copying content.

### 123. How ***Digital Rights Management*** is different from ***Information Rights Management***?
IRM mainly deals with the protection of business related information typically that involves _documents and emails_. However, a DRM relates to consumer facing rich media viz _movies and audio_.

### 124. How will you prevent packet sniffing?
**Encrypt** _the data at rest as well as in transit_ through robust encryption techniques between the channels.

### 125. How will you overcome data corruption and tampering?
- Ensure data is protected by appropriate antivirus and antimalware products.
- Utilize version control systems to keep track of data when and by whom the data is being modified.
- Ensure Role-Based Access and Least Privileges Policy/Rules are deployed.

### 126. What are the different types of backups for databases you could think of?
- **Full Backups** (_as the name states, it is supposed to take complete backup of a drive that is specified._)
- **Differential Backups** (_backs up only the specific files that was changed from the full backed up image._)
- **Incremental Backups** (_backs up only the specific files that was changed from the full backup image or differential backup image._)
- **Transaction Log Backups**

### 127. Why should you do ***OutPut Port Filtering***, is it important from a security point of view?
**Yes, it is**. Say for instance, an employee is running a vulnerable version of a webserver or some other service that opens a port to the outside world, such that the webserver can be accessed like http://localhost:8000. This may seem that it is running only in the local machine, but certain applications can be accessed by http://1.1.1.1:8000 where 1.1.1.1 being the public ip (_just for illustration purposes_) of the internal user.

### 128. How would you scan an IPv6 address using ***NPing***?
There is no such big difference when it comes to IPv6 addresses. However, it is suggested to use `-6` or `--ipv6` options whilst scanning as this makes NPing to parse faster.

### 129. What does ***2001:0db8:85a3:0000:0000:8a2e:0370:7334*** sounds like to you?
That's an IPv6 address.

### 130. How will you perform an ***ARP Spoofing Attack***?
- Using ARP Poisoning tools like Cain (_Windows_), Arpspoof (_Linux_), the attacker sets the tool’s IP address to match the IP subnet of a target.
- The IP and MAC addresses of hosts on the target’s subnet are scanned by the attacker using the tool.
- The victim's IP is noted and the attacker sends ARP packets across the network containing the attacker's MAC and victim's IP address.
- With this, all the traffic that is supposed to go to the gateway from the machine, and the other way around, will go through our machine first, and only then forwarded to the real target. A packet capturing tool like tcpdump or wireshark will be able to read the data that was intended for the victim.

### 131. What is a ***DNS Rebinding Attack***?
This attack mainly targets home users. Home users who haven't changed their router's default password fall prey to this attack. The victim may accidentally visit an attacker's website that has a javascript in the background which uses a default set of credentials for router models. Once authenticated, the attacker may create an alternate account in case the default credentials are changed to revisit and control the victim again.

### 132. Can you list the available network routing protocols?
- Distance Vector Protocol Routing. (_better suited for smaller networks_)
- Link State Protocol Routing. (_for larger networks_)

### 133. Does Linux gets affected by Viruses?
Yes. However, it is quite difficult to exploit due to some reasons.
- Virus programmers must target mutliple flavours of linux operating systems namely (fedora, kali, suse, etc.) whereas for Windows it is straight forward (Microsoft)
- They (Virus Programmers) target a huge user-base and the OS that is very easier to write viruses and access resource (_which windows wins here again hands down_)

### 134. What's an ***Information Security Charter***? What should they contain?
It's a key governance tool mainly used by the CISO. It clearly defines the objectives, process, guidelines, etc for any security leading to success. A perfect InfoSec charter should contain some of these
- Timelines.
- Approval & Authority.
- Key Players.
- Roles and Responsibilities.
- Milestones.
- Budget.

### 135. What are the ***advantages and disadvantages*** of firewalls?
- **Advantages**
  - If properly configured with rules, it can totally lockdown external malicious attacks.
  - Some firewalls come with anti-malware, anti-virus softwares. Hence, it can be a cost-effective solution.
<br>
- **Disadvantages**
  - Misconfiguring a rule may screw up the organization as it can lead external attackers to access internal servers.
  - Social Engineering attacks cannot be stopped.
  - Insider attacks cannot be averted.

### 136. Where would you place the firewall?
Typically, should sit between the internal network and external connections. Additional firewalls can also be implemented.

### 137. Can you state some pointers on writing rules for a Firewall Configuration?
- Almost all firewalls processes rules from top to bottom, hence it is recommended to write general rules on the top followed by specific rules after that. This is because some legitimate packets may get blocked.
- Ensure the firewall rule is configured to drop "impossible" or "unrouteable" packets from the internet with addresses matching the internal network (192.168.X.X or 10.1.X.X) pattern.

### 138. What's a ***Split Tunneling*** and are there any security concerns?
**Split Tunneling** falls under Remote Access VPN concepts. In this scenario, the VPN client is connected to both the corporate network as well as to the internet (not routed through the corporate network). So, there are chances the client can spread malware to the corporate network. Hence, excessive care must be emphasized under split tunneling scenario.

### 139. What do you mean by ***Client Isolation*** in a wireless network?
An organization may have both wireless and wired connection. Connecting to either of them lets you access your internal corporate network data. Client Isolation, is a feature or setting, when enabled it will prevent a device (_laptop, mobile, etc._) which is already connected to the wireless network from accessing resources that are connected to the network by a wired connection.

### 140. Explain ***Fragmentation*** and ***Reassembly*** attacks on an IDS.
The concept of MTU (_Maximum Transmission Unit_) should be discussed here. All available Routers have MTU, which is the maximum number of bytes can be allowed/sent in a single packet. A large packet (let us consider an attack in our case) can be broken down in small packets called _fragments._ An offset value in each and every fragment tells the destination IP host how to reassemble the other packets into a larger packet. If the IDS allows fragmentation and does not inspect the packet before reassembly, an attack may slip through it.

### 141. How does a ***Signature-Based*** IDS work?
The Signature based IDS works on available database of malware patterns or so-called signatures. The IDS compares the packets with the database to check for a match in the available database. If a match is found, an alert is dispatched. _It works in a similar way as of an anti-virus software._

### 142. How does an ***Anomaly-Based*** IDS work?
The Anomaly based IDS does not compares any database, but instead maintains one of its own. It profiles the normal activities of the software’s it monitors and if something unusual activities like High CPU Usage, Unexpected Escalation of the process, Unusual code changes in the memory, etc. it immediately alerts.

### 143. What are the advantages and disadvantages of Signature based IDS?
- **Advantages**
  - They can exactly detect a threat which is available on their available signature detection database/engine.
  - They can also tell you precisely which exploit was used.
<br>
- **Disadvantages**
  - They can detect malicious activities those are available only on the defined database. They are still prone to new attacks.
  - There will be a performance hit as the signatures in the database keep growing.

### 144. What are the advantages and disadvantages of Anomaly based IDS?
- **Advantages**
  - They are very effective against 0-day attacks sometimes. Say an exploit causes severe consumption of CPU resources, this IDS kicks in and preventing that from happening further as this was an intentional behavior of that program.
  - They can also detect fuzzing techniques. A field is not expected to have more than 10 characters, when a large packet is sent the IDS gets kicked in.
<br>
- **Disadvantages**
  - Throws a lot of _**false-positives**_ on a dynamic environment. (_where the activities of the assets keep changing, the profiling becomes a tough job for the IDS_).

### 145. What's a ***Smurf*** attack and how is it different from ***Ping-of-Death*** attack? Are they a serious threat?
In a **smurf attack**, the attacker sends a massive number of ICMP requests to the victim server using the spoofed addresses from the network the target is situated. A **ping-of-death** happens when attacker sends multiple ICMP packets as large as 65,535 bytes (allowable size) to the victim server, fragmentation occurs and during reassembly it exceeds the size limit leading to a buffer overflow which in turn causes the target to freeze, crash or restart. _Both the attacks are not considered a threat as of now_, since most firewalls can prevent these attacks by default.

### 146. Explain ***Event Aggregation*** and ***Event Correlation***
**Event Aggregation** is a collection of multiple similar events that are combined and put together.
**Event Correlation** is a technique that takes only important **aggregated events** into account and remaining others are skipped.

### 147. What's a ***Land Attack***?
**Land Attack** is quite similar to the SYN flood attack and is a type of Denial of Service (DoS) attack. The attacker uses the target's (victim) ip address as the spoofed address. In doing so, this creates an infinite loop between the target system and the target system itself.

### 148. How would you deploy an IDS/IPS solution on a corporate network?
- Ensure you are in par with company's security policy.
- Choose both hardware and software versions of IDS/IPS whichever necessary.
- Locate where the IDS/IPS and Sensors to be placed between assets.
- Configure the detection, logging, alerting, prevention and reporting mechanisms.
- Test the deployment using broad rules to make sure everything is working as expected.
- Encrypt communications between sensors and console.
- Analyze the results and troubleshoot.
- Keep adding the rules and refine them whenever needed.

### 149. What's a ***Teardrop*** attack?
**Teardrop** attack is a type of Denial of Service (DoS) attack that exploits fragment offset field in the IP header to produce erroneous fragments which are then delivered to the target machine. Unable to rearrange the buggy fragments, the victim keeps on accumulating the fragments until it crashes.

### 150. What's a ***PBX***? Why would an attacker try to hack it?
**PBX**, Private Branch Exchange is a private telephone network that is used within an organization that uses communication channels like VoIP, ISDN etc. The employees can make use of the PBX to communicate internally with the employees of the organization (extensions) and externally, depends on how the service is configured. An attacker once compromises the PBX, will be able to _make long distance calls with free of charge and imposing it on the organization_.

### 151. What's a ***Kernel*** and a ***Distribution***?
A kernel is a piece of software that handles interactions between hardware and end-user applications. A distribution is an operating system that is built over the kernel that includes an installation program and applications.

### 152. What's an **ARM Processor**?
**ARM** stands for Advanced RISC Machines, where RISC is the acronym for (Reduced Instruction Set Computer). ARM processor is designed to perform smaller operations and they are mainly used in wearable technology.

### 153. ***Live ISOs***. Explain.
Mostly they refer to bootable operating system that does not require any prior installations procedure. They are mostly used in forensics, pentesting where installation is not required or for installing a newer version on the drive.

### 154. How do you change a **User-Agent** in a Chrome Browser?
Go to the Developer Tools or Press `Ctrl`+`Shift`+`I` to open the Panel. To your extreme bottom left, click the three dots and choose "Network Condtions". Search for the User Agent section. You can choose existing UAs or create your custom one.

### 155. Explain **SAST** & **DAST**
SAST (_Static Application Security Testing_), otherwise referred to as White Box Pentesting of an application. Complete access to the source code will be available and it can be introduced in any SDLC models like (Agile (CICD), WaterFall) whereas in DAST (_Dynamic Application Security Testing_), otherwise called as Black Box Pentesting, can only be applied to WaterFall SDLC model, that too only after the development phase of the software. Some of these factors are analyzed from these two models.
 - SAST has high rate of success in finding the vulnerabilities as they have access to code directly.
 - Security vulnerabilities can be detected earlier in SAST, whereas in DAST the vulnerabilities can only be discovered after the end of development or the deployment phase.

### 156. How does **LDAP Injection** work?
The LDAP (_Light Weight Directory Access Protocol_) Injection works similar to that of an SQL injection. The untrusted input from the attacker can perform unauthorized queries and there are chances to execute arbitrary commands in the AD Tree.

### 157. What's an **SSL Strip** attack?
Basically, this is a MiTM attack in which the attacker sits between the client and the web server (the victim is communicating to). In this case, the attacker strips off the HTTPs communication between the victim and the web server. The attacker will be sending the HTTPs requests on the victim's behalf such that the attacker will be able access to the plain text communication of the victim. This can be illustrated by Victim -> HTTP -> Attacker -> HTTPs -> Web Server. **HSTS** (HTTP Strict Transport Security) header can be used to mitigate such an attack.

### 158. Could you state the main sections in the **PTES** (_Penetration Testing Execution Standard_) ?
- Pre-Engagement Interactions (_scope of the scan, type of assessments, when to perform the scan, etc_)
- Intelligence Gathering (_do research on the organization passively, can be netcraft, google dorking, unsuspecting social engineering, etc_)
- Threat Modeling (_know the application and analyzing the attack surface_)
- Vulnerability Analysis (_finding out all the attacks and vulnerabilities and listing out as per criticality_)
- Exploitation (_with the discovered vulnerabilities, performing the actual penetration in the network without disrupting services_)
- Post-Exploitation (_finding business critical data_)
- Reporting (_listing out all the vulnerabilities, the approach used to find them out, listing out the vulnerable machines, what threat the vulnerability can pose and detailed steps to re-mediate the vulnerability_)

### 159. Why does Nmap results vary when executed as a privileged user and a non-privileged user?
Nmap uses **raw sockets** which only an account with elevated privileges can perform.

### 160. What's a **Drive-By Attack**?
An attacker may spread malware through a compromised website or through any web location that intentionally serves malware. End-user gets affected by malware when they visit those websites. In such cases, it can termed as the machine is affected via a **drive-by attack** Most of the ransomewares make use of **drive-by** attack as a means of infecting computers.



> ## ***Books, Sources, Links and References***

- **The Basics of Information Security** - _Jason Andress_
- **IT Security Interviews Exposed** - _Chris Butler, Russ Rogers, Mason Ferratt, Greg Miles, Ed Fuller, Chris Hurley, Rob Cameron, Brian Kirouac_
{: .notice}










---
