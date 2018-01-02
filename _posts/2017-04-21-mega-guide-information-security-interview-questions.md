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

Almost **<font color='red'>100</font>** questions and still counting, I've been contributing to this post on a regular basis. This is beneficial for anyone who wants to recall their knowledge on information security topics. This can also be used as a **Guide** to prepare for Information Security Openings. The Information Security topics were intentionally shuffled to achieve robustness.

> ## **Errata**

Eventhough I have taken every care to ensure the accuracy of the content, mistakes do happen. Incase if you come across any mistake or typos, either you can write to me or **you can pull the repository and make changes wherever neccessary**. Any one of that will be highly appreciated.
{: .notice}

> ## **Contribution**

Contribution to this guide is welcome. You can either write to me or **you can pull this repository**. Credits will definitely be given to your name aside the question.
{: .notice}

---

### 1. What is a Repudiation Attack?

An attacker can prove a vulnerability exists in an application without actually denying the attack made by him/her. This example can be compared with "Google Hacking". The attacker would have used Google Dork to find a weakness in the website without directly penetrating it. One more classic example would be the same website may have an information disclosure vulnerability in one of their pages if the error wasn't handled properly. Repudiation Attacks may also be termed as **"Passive Attacks"**.

### 2. What is a False Positive and a False Negative?

**False Positive**: An automated scanner scans a website and it shows the website is prone to some attack (say, SQLi, CSRF, etc), which actually isn't. <font color='green'>The site is safe.</font>
<br>**False Negative**: An automated scanner scans a website and it shows the website is safe from attacks (say, SQLi, CSRF, etc), which actually isn't. <font color='red'>The site isn't safe.</font>

### 3. What is the key difference between Penetration Testing and Vulnerability Assessment?

**Penetration Testing** is a process of breaking into the system and trying to gain the maximum privilege on the network. The ultimatum here is to get to the deepest level inside a network. This process is more similar to how an intruder would penetrate except there will be no damage caused. The steps has to be properly documented on how the actions were performed to gain the highest privilege.
<br>**Vulnerability Assessment** is a process of listing out all weaknesses in the machine (either by using a tool/manual ways) that is being assessed and list out the vulnerabilities in the highest order of risk. This process stops with this and does not further delve as of Penetration Testing.

### 4. How to define CSRF attack in an easier way?

**Cross Site Request Forgery** or **CSRF** is a vulnerability in a website that allows an attacker to trick an end-user(victim in this case) into performing malicious operations without their knowledge in the background.

### 5. Which is more important to fix "Threat" or "Vulnerability"?

Threats can be classified as "Inside Intruder", "Natural Disasters", etc whereas Vulnerabilities can be classified as weaknesses such as "SQLi", "XSS", "CSRF", "Non Availability of Bunkers for protection against natural disasters", etc. A Threat **must** make use a Vulnerability to exploit or create damage to the data. So it is important to fix vulnerabilities first than to focus on threats. Sometimes this can also be counter-intuitive, an insider working for an organization may pass vital information (eg: admin credentials) to an outside intruder. The outsider can directly login to the application with the credentials and can cause damage to the data (in this case, the outsider did not make use of any vulnerability to exploit the application).
<br>Hence, there is no perfect answer that can be provided to the above question.

### 6. How do you stop Brute-Force Attacks?

- Adding a **CAPTCHA** functionality to the login forms.
- Enforce account lockout mechanism for a maximum of three to four wrong attempts.
- Fastest fix for a temporary period would be blocking the particular ip address that is making the brute force attempts.
- Authentication Delays.

### 7. What's the difference between an "Exploit" and a "Payload"?

An exploit is the medium in which the payload is contained. Both represent a _piece of code_, but a payload does contain the actual attack whereas an exploit can be termed as a _carrier_. To make the explanation more clear and precise, take a Gun for an instance. The "Gun" is the exploit whereas the "Bullet" is the actual payload.

### 8. Why is encryption used for confidentiality instead of encoding?

Encryption and Encoding uses publicly available algorithms. Encoding is not used for confidentiality purposes since the content that has been encoded using algorithms like (Base64, UTF, etc) can be reversed with their available algorithms and there is no secret key involved. In an encryption scheme like an (AES, 3-DES, etc) they have corresponding encryption and decryption algorithms which involves a common secret key.

### 9. Which type of scan is performed by NMAP through default settings?

Nmap uses a "SYN" scan by default unless we specify anything. -sS will be the default setting for Nmap. SYN scans are faster as they do not create the Three-way-handshake (SYN-><-SYN-ACK->ACK). Instead of the ACK, the SYN scan sends an RST packet, thus the connection will be closed and there won't be any chances for DoS condition. SYN scans were previously called as "Stealth Scans" as the logging devices do not record activities since a three-way-handshake wasn't established. Nowadays, the devices do record activity of SYN scans too, so it is not fair to call it as a "Stealth Scan" anymore.

### 10. On which port does Nessus run?

**8834**. Nessus can be accessed through any browser by accessing https://127.0.0.1:8834.

### 11.How do you differentiate "Bind Payloads" and "Reverse Payloads"?

Bind Payloads are a piece of code which is sent by the attacker to the target machine. The exploit then runs on the machine as a process on a certain port say 4444 passively. The attacker can connect to this target by establishing connection to this particular port.
<br>Reverse Payloads are also a piece of code that is sent by attacker and in the background the attacker runs another process that keeps listening to the port say 4444., when this exploit is executed, the target machine immediately sends a connection to the attacker machine that is passively listening on the background.

### 12. What is a "Promiscuous Mode and Non-Promiscuous Mode" while capturing packets with a packet sniffer?

In a "Promiscuous Mode" whichever packets that reaches the Network Interface Card is compelled to accept eventhough it was not intended for that NIC's particular MAC address. That's one of the reason we mostly sniff traffic using this mode. In a "Non-Promiscuous Mode", the packets are processed only if they are intended for that NIC's MAC address, others are discarded as it is.

### 13. What is an Open Redirect?

It resides in one of the OWASP Top 10, this happens in a site which does not properly validate parameters that happens during a redirect. For instance; Consider this URL http://www.example.com/login.aspx?redirect=profile.php. What an attacker does is that he could use this opportunity to redirect the logged in users to his/her site by crafting a URL like this. http://www.example.com/login.aspx?redirect=http://somemaliciouswebsite.com

### 14. How would you rate or rank a vulnerability based on your findings?

This depends on how much impact the vulnerability could affect your business. An example can answer this question, During an audit say you discover XSS and SQLi vulnerabilities. Both are equally dangerous, but in our scenario we rank XSS as the first most since the database that has the SQLi is not a production one and it is just holds some sample data. Thus we need to rank a vulnerability based on the risk factor.

### 15. What is an Active Directory? How does LDAP differs from Active Directory?

Active Directory is Microsoft's implementation of directory service that provides information about the system, user's activities, policies, etc. LDAP (LightWeight Directory Access Protocol) is a protocol that is used to query the directory services (in this case, the Actual Directory).

### 16. Give a simple difference between Authorization and Authentication?

Authorization is a process whereas an Authentication is a method. Authorization takes place during Authentication. This can be made clear with an example, Consider an ATM, You use your card to "authenticate" to that machine and once you have entered the correct pin you are "authorized" to do transactions.

### 17. Can you perform a simple MiTM on a mobile phone?

Spawn a rogue wireless access point. Wait for the victim to connect to your AP. You can now intercept the communication.

### 18. When you deal with a stream of confidential data to be transferred across the channel, what would you do first. Encrypt or Compress?

Any compression algorithm will look for certain patterns in the data to perform compression. When the data is encrypted, the compression algorithm will find it hard to compress the data (or it may not compress the data at all). So the good option would be. Compress and then Encrypt.

### 19. How do you prevent CSRF Attacks?
Use random tokens for each session and transaction. When an end-user logs to that application, let the application create a token for that particular session. That token should be included in every transaction. You can also use CAPTCHAs to prevent CSRF attacks.

### 20. Which is better. Closed ports or Filtered Ports?
During a scan, closed ports respond to scanners (port scanners like nmap) saying that the service is not running, whereas filtered ports do not respond to scanners. So it is sometimes better to have filtered ports as they increase scanner times by not responding, but it also gives a hint to hackers that a particular service is running on the port but it is being blocked.

### 21. What's a Rainbow Table and a Rainbow Cracker?
Rainbow Tables are pre-computed hashes that was generated using cryptic or one-way hash algorithms. For instance, say we are subjecting a plaintext "secret" to a one-way hash algorithm and 
it generates a hash "eabecfe". This hash and the corresponding plaintext will be stored in a table. This table is called as the Rainbow Table. It is just a repository that holds hashes that 
were pre-computed and stored.
<br>
Rainbow Cracker makes use of Rainbow Tables to do the cracking process, it is a time-memory tradeoff so the process will be faster.

### 22. How do you use netcat to listen and connect through two different machines/VMs?

Say there are two machines A and B, If you want connect to A from B, then start a listener in A by running the command `nc -l -p 2334` . Inorder to connect to A from B., execute `nc 
192.168.1.2 2334` (where 192.168.1.2 is the IP address for machine A) on machine B.

### 23. State some differences between Netcat and Ncat.

Netcat is available in almost all versions of linux. Ncat will replace Netcat in future versions on linux probably. Ncat has SSL support between connections, also supports Proxies and IPv6.

### 24. Contrast Hubs. Switches and Routers

**Hubs:** Not expensive. Data collision may occur as traffic intended for one machine will reach all the machines in the network. This also results in wastage of bandwidth. This may also 
result in information leak as a packet sniffer can be used to capture packets that was not intended for the particular machine. They operate on the Physical layer as they deal with bits.

**Switches:** They are bit expensive compared to Hubs but they are way more smarter. The switch uses a table within to make track of the MAC addresses associated with the computers on the 
network. Switch acts as a hub in the begining (transmits data to all machines when the table is empty) and learns about the addresses and during the next data transfer, the switch refers to 
the table, reads the route (address) and then transfers to the particular target without transmitting throughout the network. They operate of the Data Link layer as they deal with MAC 
addresses.

**Routers:** They are expensive than Switches. Ultimately they do Network Address Translation(NAT) which helps you connect to the Internet. They have support for DHCP and it helps in 
automatically configuring ip addresses for multiple machines on the network. They operate on Network layer as they deal with IP addresses.

### 25. Which protocol does DNS use?

DNS requests make use of UDP protocol instead of TCP. UDP protocol are unreliable when compared to TCP, but they are faster when compared to TCP. The load factor is very important 
when it comes to DNS, since TCP makes use of a three-way-handshake., it will be a little slower than UDP.

### 26. State a few steps you would use to secure a Linux machine.
- Use `faillog` command to set user account lockouts after certain failure attempts.
- Ensure the linux kernel and software are up to date.
- Never use root account to login, use sudo command whenever necessary.
- Disable unwanted services with high privileges. 
- Check for world writeable files and disable it wherever necessary.

### 27. If there are a total of 65535 TCP Ports, then how many UDP Ports are available?
There are 65535 UDP ports as well.

### 28. How to check for Click-Jacking and state atleast one method to prevent it?

Write a normal html code, add an iframe something like this `<iframe src="vulnerableClickJackingSite.com">`, save it as test.html. Open this html in the browser. If vulnerableClickJackingSite.com 
opens up within the iframe, then the site is vulnerable to Click-Jacking.

**Prevention:** By configuring X-Frame Options Headers to `DENY` or `SAMEORIGIN` or the site using `ALLOW-FROM`. See the code below.

`X-Frame-Options: DENY` <br>
`X-Frame-Options: SAMEORIGIN` <br>
`X-Frame-Options: ALLOW-FROM https://example.com/`

### 29. List some steps in securing any Web Application.

- Make sure "Security Testing" is part of the SDLC.
- If not, immediately enforce VA on the application and find the vulnerabilities.
- Remediate the vulnerabilities and redo the VA to make sure they are gone.
- Go for PT of the web application, if required.
- Perform security checks every once in a while depending on the application active releases.
- Install a web-application firewall if necessary.

### 30. List some steps in securing any Web Server.

- Check whether the webserver is up to date and does not contain any vulnerabilities.
- Install an application monitoring tool like New Relic to monitor the requests.
- Make sure certain services are not running with root/SYSTEM level privileges.
- Ensure PT is done on the webserver atleast once.
- Periodically check for available patches.

### 31. Compare and Contrast NIDS and HIDS.

NIDS are deployed in "strategic points" like in DMZ and other inter connections of the network, whereas HIDS are deployed on individual hosts. NIDS are the first line of defense whereas HIDS are considered as the last line of defense. NIDS has a greater challenge to inspect encrypted packets whereas HIDS will be able to analyze those packets as well.

### 32. How do you assess security stance of a VPN?
- Scan for VPN gateways availability.
- Fingerprint it and determine the vendor and configuration information.
- Check for vulnerabilities associated with the VPN vendor.
- Capture PSK (Pre-Shared Keys).
- Perform offline PSK cracking.
- Check for the default user account information.

### 33. Why a methodology for Pen-Testing is important?

- A methodology protects the assessing organization from legal and liability issues since the steps have already been preapproved by the client. It also effectively manage time and does not let the tester to miss any important engagement phases.

### 34. State some effective pen-testing methodologies of date.

- ISSAF: Information Systems Security Assessment Framework.
- OSSTMM: Open Source Security Testing Methodology Manual.
- OWASP: Open Web Application Security Project.
- PTES: Penetration Testing Execution Standard.
- OWTF: Offensive Web Testing Framework.

### 35. Explain OSINT

**Open Source Intelligence** (OSINT) is a type of reconnaissance of the target that is available on public sources and on the internet. This can also be considered as collection of data about the target through Google Hacking, gathering DNS and other information through websites like Shodan, Netcraft. etc.

### 36. List some pointers for a Mobile Threat Model.

- User may connect to a rogue wireless access point such that their sensitive information can be tapped.
- User may download infected/malicious app from PlayStore/iStore (if they miss some security checks) and other unsigned and non-verified apps from the internet.
- User may tap a link that was received through SMS or any IM which is considered to be malicious.
- User may visit some sites that is serving infected scripts.

### 37. Write the simple Nmap command to invoke a general vulnerability assessment script on any domain.

`nmap -sV --script=vuln www.somewebsitetoscan.com`

### 38. Contrast some important DNS tools for Pentesting

- **dnsrecon** : Finds the A record, MX hosts, Nameservers, etc.
- **dnstracer** : Finds where the DNS gets its information from.
- **dnswalk** : More or like a debugger, checks the domains for consistency and precision.
- **fierce** : One of the most used DNS tools by the pentesters. Smartly attempts zone transfers and brute-force attacks to gain further DNS information.

### 39. How different is the `tracert` command in Windows compared to the `traceroute` command in Linux distributions like Kali?
Windows `tracert` uses ICMP echo requests whereas Kali `traceroute` uses UDP datagrams.

### 40. List some types of MiTM attacks.
- ARP Poisoning
- ICMP Redirection
- Port Stealing
- DHCP Spoofing

### 41. Explain Stateless and Stateful Firewalls.
Stateless Firewalls does not keep track of packet flow whereas Stateful Firewalls do, they can also tell if the packets are fragmented or changed. Stateless Firewalls are faster and they 
can deal with heavy network traffic and their performance will be more effective. Stateful Firewalls will be more effective on less traffic scenario.

### 42. How do you implement security in the Software Development Life Cycle (SDLC)?
- Secure Coding Practices document has to be followed by the development team. The security team should assist the development team if any queries raised.
- Security has to be implemented in test cases and use cases as well.
- Make use of code scanning tools to scan the application for vulnerabilities and remediate the same.
- Security awareness trainings and latest threats has to be kept informed to the development team.

### 43. Explain XPath Injection Attack.
XPath is a language that is very similar to SQL which is used to address XML documents. XML databases use XPath as their standard query language, Again similar to SQL Injection, there 
exists XPath Injection. Even XPath Injection is done by the usage of a single quote ('). The attack is carried out in depth by knowing the errors that the XML parser throws. There also 
exists Blind XPath Injection Attack, which is carried out with the help of result set returned.

### 44. What is an Incident Response Plan and a Disaster Recovery Plan. Are they same?
No they are not the same. An Incident Response Plan is a set of steps that has to be followed immediately when an incident happens, For instance, A fire outbreak in a building is an 
incident, an incident plan would be: usage of fire extinguishers to douse the fire, call the fire personnel, use the stairs, etc. That would be a clear example for that. A Disaster Recovery 
Plan comes in effect after the execution of Incident Response Plan. It also lists efficient steps that has to be followed after the Disaster has occurred. For instance; Restore backups from 
Cloud Storage, Refurnishing the office, etc.

### 45. How to prevent website from Google hacking or getting dorked?
Use a robots.txt to tell the search engine which pages to crawl and what not to. Remove sensitive data from the web, if that's not possible use better authorization schemes to protect it 
from getting viewed from outside world. If site traffic does not matter to you, it's better to remove your website from Google Indexing.

### 46. How does a Digital Signature differ from a Digital Certificate?
A digital signature is a mechanism that is used to verify that a particular digital document or a message is authentic. For eg: If you want to send some confidential mails to other party 
confirming that you are actual sender. A digital certificate is a certificate issued by a trusted third party called a Certificate Authority (CA) to verify the identity of the certificate 
holder. For eg: SSL certificate for a website.

### 47. List the type of Security Frameworks.
- ISO
- NIST
- COBIT
- COSO
- HITRUST CSF

### 48. Consider you are in the internal network of a organization, you need to find the Operating System of another machine in the same network without using any tools. What command would you use under a Windows Environment?
`systeminfo /s`.

### 49. State BYOD and its merits and demerits.
BYOD - Bring Your Own Device is a type of policy in any organization that lets employees to bring in their own computers, laptops or other devices that would let them connect to office's network and do the official work. Employee's personal devices maybe faster than that of the gadgets their companies provide. Worst part is if the personal gadget is affected by any virus or malware if will spread through the entire network.

### 50. What are the different modules of Metasploit Architecture?
- Auxiliary
- Encoders
- Exploits
- Nops
- Payloads

### 51. Can you give a real-time example for a Threat, Risk, Vulnerability, Exploit and a Payload?
This is my own example (correct me if am wrong). Let us consider an encounter between a Cop and a Gangster. The Cop is held by the Gangster in a Gunpoint situation and threatening him to 
provide intel on the remaining cop's location. We can relate this scenario to our question.

- Threat: The Gangster
- Vulnerability: The Unarmed Cop.
- Exploit: The Pistol the Gangster holds.
- Payload: The loaded bullet in the Gun.
- Risk: The Intel being disclosed.

### 52. Explain the three different security controls.
- Physical Controls: They are the first line of defense. Physical controls include Gates, Walls, Fences, Cameras, Locks, etc. This is the most critical aspect of Security Controls.
- Logical Controls: Otherwise termed as technical controls, they constitute authentication schemes that are used to protect unauthorized access to terminals. (eg,. Passwords). Also 
Firewalls, Intrusion Detection and Prevention Systems, etc.
- Administrative Controls: They are more or like Policies, Procedures and Guidelines that are to be followed. (eg., A password policy stating that the password must be changed every 30 days)

### 53. Contrast Defense in Depth.
Defense in Depth is also known as Layered Security that enables multiple security countermeasures in each and every level to make sure CIA (Confidentiality, Integrity, Availability) of data is intact. It uses multiple approach to protect the data being penetrated by attackers. For eg. Having multiple security measures at the external network, internal network, etc.

### 54. Name the attacks that affects the CIA Triad.
Just listing a single attack for each type.
- Confidentiality: Man in the Middle Attack
- Integrity: SQL Injection Attack
- Availability: Denial of Service Attack

### 55. Which takes place first. Authentication or Authorization?
Authentication takes place first and then followed by Authorization. Easiest way to remember is, you authenticate yourself to any terminal or device using authentication methods (what you are, what you have & what you know), thus the system checks whether you are authorized to use the terminal.

### 56. How Deep Packet Inspection Firewalls are better than Packet Filtering Firewalls (Stateful & Stateless) and depict their challenges too.
The DPI Firewalls not just inspects the traffic but the contents inside it which makes them very effective to block nefarious packets. They are relatively slow compared to packet filtering firewalls and also there is a privacy at stake since it can read almost any content. 

### 57. What is an Endpoint Security and how does it work?
A centralized approach to ensure protection on all endpoints like Desktops, Laptops, Tablets, Smartphones, IoT devices connected to corporate network is Endpoint Security. Endpoint Security works on a client-server model. In the network, the EndPoint Software will be installed on a centralized device like a Server and client software will be installed on End Point devices as mentioned above. An Endpoint Security model is very useful on a BYOD scenario., When a user brings his/her personal laptop with malware infection, the centralized server gets an alert. Endpoint Security Software Solutions does come with inbuilt Firewall, AntiVirus and AntiMalware Softwares, etc.,

### 58. What does an SIEM device do?
SIEM is the acronym for Security Information and Event Management (SIEM). These devices basically collect logs from all of the security devices like Firewalls, IDS, etc and lets you manage from a centralized dashboard. It helps you easily correlate, search, identify and investigate events and activities that is deemed to be critical.

### 59. Does Active Directory Domain Services really neccessary for any organization?
Definitely it is required for a business organization as it helps the administrators to collectively gather information about the network computers, users, policies, etc as a Centralized Desktop Management. Active Directory also provides support for Exchange and Sharepoint services.

### 60. What's an Interactive Logon and what are the types associated with it?
May sound confusing for some, An interactive logon is nothing but a method to logon to the computer or workstation. A new session can be initiated by CTRL+ALT+DEL. Local Logon (SAM), Domain Logon (Active Directory) & Smartcard Logon (Hardware Token) are the types associated with it.

### 61. List the attacks associated with the OSI Layer Model.
- Physical Layer: WarDriving, Physically plugging a Keylogger Device, WireTaps
- Data Link Layer: MAC Address Spoofing, Sniffing, Snorting, WEP/WPA Hacking
- Network Layer: Fragmentation Attacks, Ping Attacks, Routing Protocol Attacks, ARP Poisoning
- Transport Layer: DoS Attacks, MiTM Attacks, SYN/ACK/FIN Attacks, Port Scans
- Session Layer: Session Hijacks, DoS Attacks, NETBIOS Attacks.
- Presentation Layer: HTML Code Inspection and Corrupt or Malicious Controls
- Application Layer: Trojans, Worms, Viruses

### 62. How does Port Security works on a Switch?
Port Security is a feature in which the MAC Addresses are cached. The communication takes place only if there is a match with the cached MAC table, if an attempt to connect to the port with 
a different MAC is found then the administrator gets notified.

### 63. What are the layers of TCP/IP Model and how does it relate to OSI Layer?
There are four layers when it comes to the TCP/IP Model. Application, Transport, Internet and Network. This is how the layers are associated with OSI Layer.
- Application Layer: Application + Presentation + Session
- Transport Layer: Transport Layer
- Internet Layer: Network Layer
- Network Layer: Data Link + Physical

### 64. What do you mean by Least Privilege?
Least Privilege can be a rule or policy in which a user has access to exactly what he/she needs for their current user role.

### 65. How would you employ "Defense in Depth" security on the OSI Model?
- Physical Layer: Fences, Surveillance Cameras
- Data Link Layer: Port Security in the Switches
- Network Layer: Setting Access Lists in the Border Routers, IDS/IPS
- Transport Layer: VA, Setting DMZs and Enabling Packet Filtering in the Firewalls, IDS/IPS
- Session Layer: VA, IDS/IPS
- Presentation Layer: VA, IDS/IPS
- Application Layer: VA, IDS/IPS, Virus and Malware Scanning

### 66. What is a Unified Threat Management (UTM) Device?
A UTM comprises of multiple software and hardware devices like Firewalls, IPS/IDS, AntiVirus, AntiMalware, Web Filtering etc in a single device. 

### 67. List the steps that are required to be PCI Compliant.
- Build and maintain a secure network (Proper firewall configuration and not using any default credentials)
- Protect the card holder data.
- Perform periodic VAPT assessments.
- Implementing strong access control measures. (Ensure Least Privilege properly)
- Regularly monitor and Test networks.
- Maintain an Infosec policy.

### 68. What's a DMZ?
A DMZ (Demilitarized Zone) is otherwise referred to as a Perimeter Network, that exposes external facing servers like routers, firewalls, etc to the Internet. It can also be termed as a 
segmented network whose access is secured by a Firewall.

### 69. State the six step approach to Pentest Methodology of Core Impact.
- Passive Intelligence Gathering
- Active Intelligence Gathering
- Exploitation
- Privilege Escalation
- Cleanup
- Report Generation

### 70. Does Firewall affects the time required to scan a target?
Obviously. In most cases, the firewalls are configured to drop the unauthorized packet **without** sending "connection refused" message. In this case, the host which is scanning the target 
must have to wait for a minimum time before it knows that the connection will not be succeeded. Hence, this will affect the scanning time of that particular target. There are some smart 
scanners that will tell you to increase timeouts depending on outcome of the scan.

### 71. How authentic is Banner Grabbing? Can you go by the results?
We cannot totally rely on Banner Grabbing results. Smart administrators try to fake the banner information by representing a linux webserver look like a Windows webserver. They can also 
change the version information of certain services and applications and mislead the hackers by falling into their honeypot.

### 72. What is Competitive CounterIntelligence?
Competitive Intelligence is not just the process of collecting information about competitors and their intelligence, but also about customers, stake holders, etc that aids in the decision 
making process of the organization. More importantly this is an ethical process and does not relates to Industrial Espionage (spying an organization) which is considered to be unethical. 
When it comes to our question, **Competitive CounterIntelligence** mainly protects the organization publicly available information or data from being siphoned or tapped by its competitors. 

### 73. How do you crack WEP. Explain in High Level.
Assuming you have a Wireless Adapter that is capable of packet injection.
- Use `airmon-ng` to get to know your network interface cards.
- Enable the Wireless Adapter to Monitor Mode.
- Start capturing the traffic from the specific AP.
- Use `aireplay-ng` to Inject ARP Traffic (Perform ARP Spoofing) and capture the IVs
- Use `aircrack-ng` to crack the IVs. (More the IVs the faster the cracking process will be)
- The key will be displayed on the screen in a hexadecimal format.

### 74. What would you do if you need to send sensitive data over an untrusted network.?
Encrypt the data using a strong data algorithm and send it across over the untrusted channel.

### 75. How do you harden a server?
- Removing uneccessary softwares.
- Removing unused services.
- Perform changes on default accounts.
- Use the principle of least privilege.
- Ensure timely software updates.
- Implementing logging and auditing.

### 76. What is an Attack Surface?
The entry points where an attacker could reach the legitimate application is referred to as an "Attack Surface". Say for instance, an organization serves FTP and Mail server that can be 
accessed publicly, then the total attack surface value will be two.

### 77. Why do you need a Host Based Firewall when you already have a Network Level Firewall?
Network perimeter firewalls cannot provide protection for traffic generated inside a trusted network. For this reason, host-based firewalls running on individual computers are needed. 
Host-based firewalls, of which Windows Firewall is an example, protect a host from unauthorized access and attack. In addition to blocking unwanted incoming traffic, you can configure 
Windows Firewall to block specific types of outgoing traffic as well.

### 78. How to respond to a Malware Attack on a corporate network?
- Make sure the malware is quarantined by the AntiVirus/AntiMalware software.
- Check the name of the malware reported by the Software and note down their malicious activities.
- Ensure those malicious activities have not been in action.
- If suspiscious action found, try to unplug the device from the network to avoid further infection on the corporate network.
- Update the Antivirus or Install a better Endpoint security product and do a full scan on the machine.
- If the infection still persists, try to back up critical data (scan it and make sure they are not infected).
- Do a fresh install of the Operating System. Restore the non-infected data.
- Install all latest security patches, end point security, host-based firewall, Antivirus and Antimalware products.
- Plug the machine back to the network.

### 79. Explain the components that come with Burp Suite.
- Target: In this tool/interface, the information regarding the scanning target is shown. This also includes the vulnerabilities and links discovered.
- Proxy: This acts as a web proxy between the browser (where you configure the proxy settings) and the web application server. Acts as a MiTM interface, that intercepts requests before sending it to the web application.
- Spider: It crawls the web application for links and pages and lists it out in the Target section.
- Scanner: This comes with the professional version of the Burp Suite tool. This is basically a web vulnerability scanner that is used find web related vulnerabilities in any application.
- Intruder: This tool can be highly customizable and can be even used to launch a brute-force attack.
- Repeater: This tool can be used to manually issue a HTTP request and analyze the response.
- Sequencer: The tool analyzes randomness of user session tokens as well as for CSRF tokens. By determining predictable sessions, the analyst will be able to impersonate users.
- Decoder: This tool is mostly used for quick operations like encoding and decoding of algorithms like Base64.
- Comparer: This tool is to compare chunks of data and see the difference in a "git" diff like viewable format.
- Extender: This interface lets you import plugins for Burp Suite.

### 80. How do you use WebGoat to find vulnerabilities in a website?
Well this was a honeypot question, WebGoat is not a vulnerability scanning tool., it is a deliberately built insecure web application by OWASP such that it can be made use by security 
analysts or anyone who wants to test their information security skills.

### 81. What would happen if an attacker gets hold of your website SSL's private key?
The attacker would then be able to decrypt communications., there are even chances that the attacker would be able to read the previous SSL sessions by decrypting it using the private key, 
unless forward secrecy is implemented.

### 82. How to implement Forward Secrecy?
Forward Secrecy can be implemented using the recommended Elliptic Curve Diffie Hellman Key Exchange Algorithm (ECDHE). ECDHE is faster than normal Diffie Hellman. Since the session keys are 
not linked to the server's key pair, eventhough if the attacker gets hold of the private key, the SSL session cannot be decrypted.

### 83. Can you state any one method to deface a website without using any tool?
Assuming the website has a stored XSS vulnerability. An attacker can easily inject a javascript with `location.href` tag and redirect to any site of his/her choice.

### 84. Given an IP Address how will you determine the Operating System it is running?
There is no 100% effectiveness to determine the operating system of a remote machine. However certain tool like `xprobe2` is used to guess the operating system to a certain extent. It is 
highly recommended over nmap.

### 85. What happens if Computer A's NIC card is interchanged to Computer B's NIC card? Will the MAC Address be the same?
No. Since the NICs are interchanged, Computer A will have Computer B's MAC Address and vice versa. MAC addresses are embedded in NIC cards not in the Motherboards or Microprocessors.

### 86. On which port does ping command work and how do you ping a port?
**Ping** does not work on TCP or UDP, so obviously it does not make use of any port. It uses ICMP. You cannot use ping command to ping a port, instead use Nmap for this purpose. To give a you 
perfect illustration, ping works irrespective of port numbers. `ping sh4.in` is same as `ping sh4.in 80` or `ping sh4.in 2873687234`

### 87. Explain a simple crucial method to mitigate XSS or the Cross-Site-Scripting attack.
Input Validation and Output Sanitization are the two important methods to ward off XSS attacks.

### 88. How will you write a good penetration test report?
A penetration test report will be read not just by technical managers but also by business managers whose technical knowledge will be limited or none. The report should have detailed steps 
stating how the analyst/tester made attempts in reaching the highest level of access. It is not neccessary that certain technical steps have to be explained in detail, however the **executive 
summary** should be drafted very well in almost "layman terms".

### 89. Consider you are going to engage a security assessment with a client, list out some questions that you would ask them.
- Make the client understand the difference between Vulnerability Assessment and Penetration Testing, this is where most of the organizations does mistakes. So will this be a VA or PT?
- What is the scope of the assessment, IP ranges, Timeframe, Internal and External scans etc?
- Will there be a Social Engineering assessment involved like Phishing, Fake calls, etc?
- How the assessment be like? Black Box or White Box, For instance, Will a Network Topology be provided for the devices in the scope of the assessment?
- Should physical security assessments also performed? (This involves the assessing team visiting the client premises, If so the cost involved, what are the devices to be tested, 
surveillance cameras, lockpicking, USB dropping, etc)

### 90. State the nmap command to scan a target and output it to an XML file without host discovery and no arp pings. (You have 10 seconds)
`nmap -oX out.xml -Pn --disable-arp-ping 127.0.0.1`

### 91. What's the difference between 301 and 302 HTTP Status Codes?
They both constitute redirection status codes, However the former is permanent and the latter is temporary.

### 92. How will you generate HTML scan reports from NMap?
As of 2017, NMap does not have the feature of writing the reports to HTML format. It can output the report to XML format and from there it is possible to convert to HTML using XSLT processors.

### 93. IPTables. What are they? Set a rule to block google.com and state how effective it is.
IPTables is a Firewall Utility for Linux Operating System. You can set rules in it for the accepting, rejecting or dropping incoming, outgoing or forwarding connections. The following below rule sets the website google.com to be blocked. `iptables -A OUTPUT -p tcp -m string --string "google.com" --algo kmp -j DROP`. To be straightforward, this is not an effective way to block a website, there are better ways to do it by using certains HTTP Proxies. Any user can bypass this rule by simple typing "google.co.in" or "google.co.uk" to access the website.

### 94. What's a Transparent Proxy?
Transparent Proxy is a type of caching proxy that is configured to sit on the gateway and intercepts the WWW requests from the client and fetches the data for the first time and the consecutive requests are cached. A Transparent Proxy can be clearly understood with these two examples.
- You come to some restaurant and you want to access their WiFi Hotspot, Once you get the credentials and you connect to their WWW Gateway, You will be authorized to use the internet. Here all the data what you request and send will be routed through this proxy.
- A Content Delivery Network or a CDN can also act as a Transparent Proxy.

### 95. How do you access Splunk Web Interface by default unless specified?
Splunk Web Interface runs on port 8000 by default. It can be accessed by going to http://localhost:8000

### 96. Can you suggest an effective solution for encrypting data-in-rest?
I suggest investing in SEDs. SEDs are **Self-Encrypting Drives**, they provide hardware based security by continously scrambling data using a key and descrambles the data while being retrieved with the key.

### 97. Assume a PKI Scenario, You have a public and a private key, and you often perform both encryption and signing functions. Which key is used for which function? 
- To perform **Signing** and send a message to the recipient, You use your **private key** to sign and send the message. The recipient will use your **public key** to verify whether the message is originally from you.
- To perform **Encryption** and send a message to the recipient, You use the recipient's **public key** to encrypt the message and the recipient will use their **private key** to decrypt the message.

### 98. How Meterpreter shell is better than normal shell on an exploited machine?
Meterpreter is more advanced than normal shell as you can run many commands with ease. It is possible to dump hashes, migrate to process, easily send and receive files, take screenshots, access webcam, mouse and more.

### 99. What's a Heartbeat and a HeartBleed?
HeartBleed is the vulnerability that exploits a built-in feature of OpenSSL called the HeartBeat. When your browser connects to the website and requests data, the website responds back to your browser and responds with data, this is otherwise called the HeartBeat. In this particular vulnerability, the attacker is able to craft a request in such a manner that the server responds back with data from the server's memory beyond the total data of the initial request, up to 65,536 bytes. These bytes may contain more sensitive information like server config, passwords, etc.

### 100. You notice some brute-force attempts happening on your server every five minutes, as you can infer this is a near futile attempt can you guess the motive behind this attacker?
The attacker is pretty smart, as he is playing in a defensive way by not triggering the lockout mechanisms. The other crucial part here is the attacker is not just brute forcing your system, there are chances that the attacker is brute-forcing multiple targets and that's the reason for the idle time. The inference we assume from this scenario is the attacker's main motive is to build an ultimate botnet.

---
