---
layout: post
title: "The Mega Guide to Information Security Interview Questions."
description: Information Security Terminologies and Interview Questions.
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

**11** questions and still counting, I've been contributing to this post on a regular basis. This is beneficial for anyone who wants to recall their knowledge on information security topics. This can also be used as a **Guide** to prepare for Information Security Openings. The Information Security topics were intentionally shuffled to achieve robustness to the reader.


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
<br>Hence, there is no prefect answer that can be provided to the above question.

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

### 10. On which port does Nessus runs?

**8834**. Nessus can be accessed through any browser by accessing https://127.0.0.1:8834.

### 11.How do you differentiate "Bind Payloads" and "Reverse Payloads"?

Bind Payloads are a piece of code which is sent by the attacker to the target machine. The exploit then runs on the machine as a process on a certain port say 4444 passively. The attacker can connect to this target by establishing connection to this particular port.
<br>Reverse Payloads are also a piece of code that is sent by attacker and in the background the attacker runs another process that keeps listening to the port say 4444., when this exploit is executed, the target machine immediately sends a connection to the attacker machine that is passively listening on the background.





---
