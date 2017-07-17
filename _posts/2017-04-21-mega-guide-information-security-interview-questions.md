---
layout: post
title: "The Mega Guide to Information Security Interview Questions."
description: Information Security Terminologies and Interview Questions for Security Enthusiasts.
headline: 
modified: 2017-04-21
category: infosec
tags: [infosec, interview questions, pentesting, security analyst ]
imagefeature: blogimages/2017-04-21/cover-2017-04-21.jpg
mathjax: 
chart: 
comments: true
featured: false
---

Almost **47** questions and still counting, I've been contributing to this post on a regular basis. This is beneficial for anyone who wants to recall their knowledge on information security topics. This can also be used as a **Guide** to prepare for Information Security Openings. The Information Security topics were intentionally shuffled to achieve robustness to the reader.


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

- Adding a CAPTCHA functionality to the login forms.
- Enforce account lockout mechanism for a maximum of three to four wrong attempts.
- Fastest fix for a temporary period would be blocking the particular ip address that is making the brute force attempts.
- Authentication Delays.

### 7. What's the difference between an "Exploit" and a "Payload"?

An exploit is the medium in the which the payload is contained.Both represent a "piece of code", but a payload does contain the actual attack whereas an exploit can be termed as a "carrier". To make the explanation more clear and precise, take a rifle/gun for an instance. The "Gun" is the exploit whereas the "bullet" is the actual payload.

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

It resides in one of the OWASP Top 10, This happens in a site which does not properly validate parameters that happens during a redirect. For instance; Consider this URL http://www.example.com/login.aspx?redirect=profile.php. What an attacker does is that he could use this opportunity to redirect the logged in users to his/her site by crafting a URL like this. http://www.example.com/login.aspx?redirect=http://somemaliciouswebsite.com

### 14. How would you rate or rank a vulnerability based on your findings?

This depends on how much impact the vulnerability could affect your business. An example can answer this question., During your audit say you discover XSS and SQLi vulnerabilities. Both are equally dangerous, but in our scenario we rank XSS as the first most since the database that has the SQLi is not a production one and it is just holds some sample data. Thus we need to rank a vulnerability based on the risk factor.

### 15. What is an Active Directory? How does LDAP differs from Active Directory?

Active Directory is Microsoft's implementation of directory service that provides information about the system, user's activities, policies, etc. LDAP (LightWeight Directory Access Protocol) is a protocol that is used to query the directory services (in this case, the Actual Directory).

### 16. Give a simple difference between Authorization and Authentication?

Authorization is a process whereas an Authentication is a method. Authorization takes place during Authentication. This can be made clear with an example, Consider an ATM, You use your card to "authenticate" to that machine and once you have entered the correct pin you are "authorized" to do transacations.

### 17. Can you perform a simple MiTM on a mobile phone?

Spawn a rogue wireless access point. Wait for the victim to connect to your AP. You can now intercept the communication.

### 18. When you deal with a stream of confidential data to be transferred across the channel, What would you do first. Encrypt or Compress?

Any compression algorithm will look for certain patterns in the data to perform compression. When the data is encrypted, the compression algorithm will find it hard to compress the data (or it may not compress the data at all). So the good option would be. Compress and then Encrypt.

### 19. How do you prevent CSRF Attacks?
Use random tokens for each session and transaction. When a end-user logs to that application, let the application create a token for that particular session. That token should be included in every transaction.

### 20. Which is better. Closed ports or Filtered Ports?
During a scan, closed ports respond to scanners (port scanners like nmap) saying that the service is not running, whereas filtered ports do not respond to scanners. So it is sometimes better to have filtered ports as they increase scanner times by not responding., But it also gives a hint to hackers that a particular service is running on the port but it is being blocked.

### 21. What's a Rainbow Table and a Rainbow Cracker?
Rainbow Tables are pre-computed hashes that was generated using cryptic or one-way hash algorithms. For instance., say we are subjecting a plaintext "secret" to a one-way hash algorithm and 
it generates a hash "eabecfe". This hash and the corresponding plaintext will be stored in a table. This table is called as the Rainbow Table. It is just a repository that holds hashes that 
were pre-computed and stored.
<br>
Rainbow Cracker makes use of Rainbow Tables to do the cracking process, it is a  time-memory tradeoff so the process will be faster.

### 22. How do you use netcat to listen and connect through two different machines/VMs?

Say there are two machines A and B, If you want connect to A from B, then start a listener in A by running the command `nc -l -p 2334` . Inorder to connect to A from B., execute `nc 
192.168.1.2 2334` (where 192.168.1.2 is the IP address for machine A)

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
- Use faillog command to set user account lockouts after certain failure attempts.
- Ensure the linux kernel and software are up to date.
- Never use root account to login, use sudo command whenever neccessary.
- Disable unwanted services with high privileges. 
- Check for world writeable files and disable it wherever neccessary.

### 27. If there are a total of 65535 TCP Ports, then how many UDP Ports are available?
There are 65535 UDP ports as well.

### 28. How to check for Click-Jacking and state atleast one method to prevent it?

Write a normal html code, add an iframe something like this `<iframe src="vulnerableCSRFwebsite.com">`, save it as test.html. Open this html in the browser. If vulnerableCSRFwebsite.com 
opens up within the iframe, then the site is vulnerable to Click-Jacking.

**Prevention:** By configuring X-Frame Options Headers to `DENY` or `SAMEORIGIN` or the site using `ALLOW-FROM`. See the code below.

`X-Frame-Options: DENY` <br>
`X-Frame-Options: SAMEORIGIN` <br>
`X-Frame-Options: ALLOW-FROM https://example.com/`

### 29. List some steps in securing any Web Application.

- Make sure "Security Testing" is part of the SDLC.
- If not, Immediately enforce VA on the application and find the vulnerabilities.
- Remediate the vulnerabilities and redo the VA to make sure they are gone.
- Go for PT of the web application, if required.
- Perform security checks every once in a while depending on the application active releases.
- Install a web-application firewall if neccessary.

### 30. List some steps in securing any Web Server.

- Check whether the webserver is up to date and does not contain any vulnerabilities.
- Install an application monitoring tool like New Relic to monitor the requests.
- Make sure certain services are not running with root/SYSTEM level privileges.
- Ensure PT is done on the webserver atleast once.
- Periodically check for available patches.

### 31. Compare and Contrast NIDS and HIDS.

NIDS are deployed in "strategic points" like in DMZ and other inter connections of the network, whereas HIDS are deployed on individual hosts. NIDS are the first line of defence whereas HIDS are considered as the last line of defence. NIDS has a greater challenge to inspect encrypted packets whereas HIDS will be able to analyze those packets as well.

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

**Open Source Intelligence** (OSINT) is a type of reconnaisance of the target that is available on public sources and on the internet. This can also be considered as collection of data about the target through Google Hacking, gathering DNS and other information through websites like Shodan, Netcraft. etc.

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
XPath is a language that is very similar to SQL which is used to address XML documents. XML databases use XPath as their standard query language., Again similar to SQL Injection, there 
exists XPath Injection. Even XPath Injection is done by the usage of a single quote ('). The attack is carried out in depth by knowing the errors that the XML parser throws. There also 
exists Blind XPath Injection Attack, which is carried out with the help of result set returned.

### 44. What is an Incident Response Plan and a Disaster Recovery Plan. Are they same?
No they are not the same. An Incident Response Plan is a set of steps that has to be followed immediately when an incident happens., For instance; A fire outbreak in a building is an 
incident, an incident plan would be: usage of fire extinguishers to douse the fire, call the fire personnel, use the stairs, etc. That would be a clear example for that. A Disaster Recovery 
Plan comes in effect after the execution of Incident Response Plan. It also lists efficient steps that has to be followed after the Disaster has occured. For instance; Restore backups from 
Cloud Storage, Refurnishing the office, etc.

### 45. How to prevent website from Google hacking or getting dorked?
Use a robots.txt to tell the search engline which pages to crawl and what not to. Remove sensitive data from the web, if that's not possible use better authorization schemes to protect it 
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
BYOD - Bring Your Own Device is a type of policy in any organization that lets employees to bring in their own computers, laptops or other devices that would let them connect to office's network and do the official work. Employees personal devices maybe faster than that of the gadgets their companies provide. Worst part is if the personal gadget is affected by any virus or malware if will spread through the entire network.


### 50. What are the different modules of Metasploit Architecture?
- Auxiliary
- Encoders
- Exploits
- Nops
- Payloads

---
