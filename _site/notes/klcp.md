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
- Kali Linux does not let you create un-privileged accounts in the beginning unlike other linux distributions.
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


## Chapter 2: Getting Started with Kali Linux


- Kali Linux's Live ISO makes life easier by running the operating system without installation. They can also be used for forensics, pentesting, etc where installations are not necessary.
- Since Kali Linux is open source and the source code can be easily tampered and can result in fake distributions, it is important to verify the authenticity of the source before downloading.
- https://www.kali.org/downloads is the official website to download the images. The HTTP links for download points to http://cdimage.kali.org is actually a mirror.
- Modern machines have 64-bit processors. Older machines that has 32-bit processors cannot run 64-bit applications, however modern machines with 64-bit processors can run 32-bit and 64-bit applications as well.
- Kali Linux's `armel` or `armhf` images are used to install in the devices like Chromebox, Access Points, Smart Phones, Embedded Devices or any other devices with an ARM processor.
- By inspecting the flags field in the `/proc/cpuinfo` virtual file it is possible to determine the 32 bit or 64 bit. Make use of `uname -m` in OS X/MacOS.
- The default Kali Linux image and Kali Linux Light variant are the both live ISOs that can be used to run the live system or to start the installation process.
- Kali Linux comes with GNOME and Kali Linux Light comes with XFCE desktop environments.
- The images of these downloads has **SHA256** Checksums.
- Well how do you verify the image? Once you have downloaded the ISO image on your drive, do a checksum by running this command `sha256sum kali-image.iso`. The hash generated from this output should match the hash with the Kali website.
- If you don't trust TLS, then you can verify the archive using PGP/GPG and compare the checksum using the `gpg` set of commands.
- Make use of Win32 Disk Imager for creating Bootable Kali USB Drive on Windows. (e.g. KaliLinux-Light-2016.1.amd64.iso)
- The `gnome-disks` (verified in Kali Linux 2017.3 Rolling) gives a list of devices that are connected to the disk. Select the removeable device and click the menu on top right and choose **Restore Disk Image**. Select the ISO Image that you downloaded and click on **Start Restoring...** button to burn the ISO image on the USB key.
- For creating a bootable USB in linux (through commandline), Insert your USB drive and type the command `dmesg`. You will now able to find the name of the USB key. Now, issue this command on the prompt to copy the iso content to the USB. `dd if=kali-linux-light-2017.1-amd64.iso of=/dev/sdb` Here `if` stands for `input file` and `of` stands for `output file`. The dd command reads the content from the input file and writes back to the output file.
- For creating a bootable USB in MacOS/OS X (through commandline). First run the `diskutil list` command to list the available disks on the system. Now insert your USB disk and run the `diskutil list` command again. You will now able to find the newly found disk. Eg. (`/dev/disk5`). Make sure the USB disk is unmounted, to unmount it type `diskutil unmount /dev/disk5`. Now issue the `dd` command along with another flag `-bs` (blocksize). So the command goes like `dd if=kali-linux-2017.1-amd64.iso of=/dev/disk5 bs=1M`
- Kali Linux images can be booted in UEFI/BIOS mode. They do not support **secure boot**. You should disable that feature in Setup.
- Virtualization makes dangerous operations like Malware analysis easier as they operate on a sandbox type environment.
- Virtualbox, VMware, Xen, KVM, Hyper-V etc are a few examples of Virtualization tools.
- Virtualization should be enabled in the BIOS/UEFI in order for the virtualization tools to work.
- 768MB is acceptable for Debian Virtual Machine but it won't be suffice for a Kali Linux Live System. However, recommended size should not be less than 2GB of RAM.
- Kali Linux Live does not require a hard disk to run.
- VDI corresponds to VirtualBox format, VMDK for VMware and QCOW for QEMU.
- A dynamically allocated hard disk grows by increasing the space on the physical disk only when the totally allocated fixed size is full. Also, in a dynamic allocated hard disk, the space does not shrinks as you clear data on your virtual disk. Once the disk is grown, it cannot shrink.
- In the virtualbox processor settings, make sure you check **Enable PAE/NX** under the extended features in order for Kali Linux to boot properly. PAE stands for Physical Address Extension.
- While setting up the virtual machine under VMware, 512MB of RAM is the default selection which is not sufficient and hence you need to increase it.
