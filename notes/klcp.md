# Guide to KLCP


## Chapter 1: About Kali Linux


- Kali Linux project established in the year 2012.
- Kali Linux is an enterprise-ready security auditing distribution.
- Kali Linux is based on Debian GNU/Linux.
- Kernel is a piece of software that handles the interactions between the hardware and end-user applications.
- Distribution is an operating system that is built over the Kernel.
- The main purposed of Kali Linux would be Advanced Pentesting, Forensic Analysis and Security Auditing.
- Debian was chosen for Kali Linux as it is well known for quality, stability and wide selection of software.
- Kali Linux v1.0 was released on March 2013 on Debian Wheezy.
- Debian Jessie came out in 2015 and Kali Linux v1.0 avoided GNOME Shell. In order to embrace it, some of GNOME Shell Extensions were added which was the result of Kali 2.0 evolution.
- Kali Linux v2.0 (Sana) was released on August 2015 (The month & year I cleared my OSCP :D)
- GNOME is Kali Linux's default desktop environment.
- Rolling Distribution pros are like you get newer updates each and every day.
- Rolling Distribution cons are like some softwares may not work due to backward compatibility.
- The Kali Package Tracker helps us to keep track of our divergence with Debian.
- The package repositories are maintained in Git.
- Updating a forked package
  - update the debian branch.
  - merge it to kali branch.
- Kali Linux can also installed on ARM devices (Advanced RISC Machines).
- Using a Live ISO, you can boot Kali Linux from a USB Key even though if your day-to-day system is not Linux.
- Kali Linux has a **forensics mode** that can be enabled from the boot menu. It will disable features like auto-detect, auto-mount etc.
- Kali Linux has root as a single user by default as most of the tools require root privileges to run.
- Kali Linux does not let you create un-privileged accounts in the beginning.
Network services are disabled by default in Kali Linux System. (especially the HTTP and SSH).
- Debian stages are comprised of: Debian Unstable -> Debian Testing -> Debian Stable.
- Debian Testing will be in a usable state.
- Kali Linux distribution is based on Debian Testing.
- Packages to Kali Linux comes from Debian Repository.
- Kali Linux relies heavily on Debian, it is also entirely independent as it has its own infrastructure and make changes whenever necessary.
- The Kali Linux system has easy access menus to vulnerability analysis, web application analysis, database assessment, password attacks, wireless attacks, reverse engineering, exploitation tools, sniffing and spoofing, post exploitation tools, forensics, reporting tools, social engineering tools and system services.
- Kali Linux has many advanced features including a non-installed (live) system, a robust and safe forensics mode, a custom Linux kernel, ability to completely customize the system, a trusted and secure base operating system, ARM installation capability, secure default network policies, and a curated set of applications.
- In the Kali Linux Live mode, Installation is not necessary and the operating system can be booted up from USB. However, default configuration will not be preserved while reboot. Hence, to achieve this; enabling the **persistence** option while adding the version to the USB key.
- This Live version can be used to do Forensic operations. Kali Linux has a forensics mode available on the boot menu.
- `/lib/firmware/` contains the latest hardware firmware files.
- Kali Package Tracker consists of the live revisions of Kali Linux code and can be reviewed anytime.
-Kali Linux can also be deployed in smart phones, tablets, WiFi routers, etc.
- Network services like SSH and HTTP are disabled by default to avoid being exposed. However, the services can be manually enabled using `systemctl enable service` command.
- Kali Linux has a multitude of security tools, However, adding a new tool to the distribution requires these conditions to be satisfied:
  - the usefulness of the tool.
  - the unique functionality of the tool.
  - the license
  - the resource requirements
- To contribute to a new tool, check out the _New Tool Requests_ section in the **Kali Bug Tracker**.

