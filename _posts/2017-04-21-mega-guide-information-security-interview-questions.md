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

As of now **2** questions and counting, I've been contributing to this post on a regular basis. This is beneficial for anyone who wants to recall their knowledge on information security topics. This can also be used as a **Guide** to prepare for Information Security Openings. The informational security topics were intentionally shuffled to achieve robustness to the reader.


### 1. What is a Repudiation Attack?

An attacker can prove a vulnerability exists in an application without actually denying the attack made by him/her. This example can be compared with "Google Hacking". The attacker would have used Google Dork to find a weakness in the website without directly penetrating it. One more classic example would be the same website may have an information disclosure vulnerability in one of their pages if the error wasn't handled properly. Repudiation Attacks may also be termed as "Passive Attacks".


### 2. What is a False Positive and a False Negative?

False Positive: An automated scanner scans a website and it shows the website is prone to some attack (say, SQLi, CSRF, etc), which actually isn't. <font color='green'>The site is safe.</font>
<br>False Negative: An automated scanner scans a website and it shows the website is safe from attacks (say, SQLi, CSRF, etc), which actually isn't. <font color='red'>The site isn't safe.</font>


### 3. What is key difference between Penetration Testing and Vulnerability Assessment?

Penetration Testing is a process of breaking into the system and trying to gain the maximum privilege on the network. The ultimatum here is to get to the deepest level inside a network. This process is more similar to how an intruder would penetrate except there will be no damage caused. The steps has to be properly documented on how the actions were performed to gain the highest privilege.
<br>Vulnerability Assessment is a process of listing out all weaknesses in the machine (either by using a tool/manual ways) that is being assessed and list out the vulnerabilities in the highest order of risk. This process stops with this and does not further delve as of Penetration Testing. 

---