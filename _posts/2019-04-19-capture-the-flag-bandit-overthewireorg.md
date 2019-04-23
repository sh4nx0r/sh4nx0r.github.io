---
layout: post
title: "CaptureTheFlag #1: 'Bandit' Walkthrough for OverTheWire.Org"
description: Bandit CaptureTheFlag Walkthrough.
headline:
modified: 2019-04-24
category: infosec
tags: [linux, bash, code, sh, capturetheflag, walkthrough, bandit ]
imagefeature: blogimages/2019-04-24/cover-2019-04-24.jpg
mathjax:
chart:
comments: true
featured: false
---


This is one of the first **_CaptureTheFlag_** challenges of OverTheWire.Org Team. This writeup contains information on how to solve the challenges of **Bandit** box, most importantly, this post **does** contain spoilers so use this walkthrough only if you _really_ need to. However, I strongly suggest not to read this walkthrough if you are planning to take up the challenge.

Kindly use this walkthrough only if you had already completed the challenges and lost access to the passwords you use to level up at **WeChall**.


---

## Bandit Level - 1

Simply SSH with the login credentials that was provided on Level 0. Use the below command to SSH to the host and once you have successfully logged in, do an `ls` command to find out any files laying around the current directory. As you discover a file named **readme**, run the `cat` command to display the contents of the file. The following commands let you complete the first level.

`ssh bandit0@bandit.labs.overthewire.org -p 2220`
<br>
`ls`
<br>
`cat readme`

<img src="/images/blogimages/2019-04-24/bandit1.PNG">

> Password: `boJ9jbbUNNfktd78OOpsqOltutMc3MY1`

## Bandit Level - 2

Use the above password to SSH in as user `bandit1`. Your password to the next level will be stored in the same directory with a filename `-` (just a dash or hyphen). Well, if you do a `cat` command or `vi` on the `-`, you will be getting an indefinitely waiting prompt. The linux kernel does not recognize when a `-` is in conjunction with `cat` or `vi` commands. To solve this challenge, try to access this file with the full path name. Use `pwd` command to know the current directory you are in. Copy the full path of the `pwd` output and concatenate along with `-` filename and run the command to get the password.

<img src="/images/blogimages/2019-04-24/bandit2.PNG">

> Password: `CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9`

## Bandit Level - 3

This challenge is pretty straightforward as the filename that has password has **spaces** in between. To use the `cat` command on this filename, wrap the filename with single quotes or double quotes and run the command to get the password for the next level.

<img src="/images/blogimages/2019-04-24/bandit3.PNG">

> Password: `UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK`

## Bandit Level - 4

In this challenge, the password file is stored inside the same directory named **inhere**. This directory has a hidden file inside this **inhere** directory. Run the command `ls` with `-a` flag to view the hidden files present in the directory.

<img src="/images/blogimages/2019-04-24/bandit4.PNG">

> Password: `pIwrPrtPN36QITSp3EQaw936yaFoFgAB`

## Bandit Level - 5

You will find a directory named **inhere** which has a couple of files laying around. If you do a `cat` on the first file to check the password, you will be presented with some non-readable characters. Doing a `cat` on each and every file is one way to get the password, but consider if there are a million files then the above will not be an ideal solution. In this case, let us write a small code to inspect the file type of the files using the `file` command and check whether the file has `ASCII` property (in other ways readable files as the challenge suggests).

`find -exec file {} + | grep ASCII`

  <img src="/images/blogimages/2019-04-24/bandit5.PNG">

> Password: `koReBOKuIDDepwhWk7jZC0RTdopnAYKh`

## Bandit Level - 6

This challenge has certain rules to retrieve the password, to my luck one of the rule was more than enough to solve the challenge. (_One of the criteria is the filesize should be around 1033 bytes in size_)

`find . -size 1033c`

<img src="/images/blogimages/2019-04-24/bandit6.PNG">

> Password: `DXjZPULLxYr17uwoI01bNLQbtFemEgo7`

## Bandit Level - 7

Almost a similar challenge to the above, all you need is to give greater importance to `man` for `find` command to know what attributes to be used for retrieving the password.

The below code finds all files which are 33 in bytes and is owned by the user **bandit7** and belongs to the group **bandit6**. Now go to the root directory by entering the command `cd /` and then run the below command.

`find . -size 33c -user 'bandit7' -group 'bandit6'`

<img src="/images/blogimages/2019-04-24/bandit7_1.PNG">
<p></p>
<img src="/images/blogimages/2019-04-24/bandit7_2.PNG">
<p></p>
<img src="/images/blogimages/2019-04-24/bandit7_3.PNG">
<p></p>

> Password: `HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs`

## Bandit Level - 8

You need to find the password hidden inside the file **data.txt** which is rightfully available under the very same directory. The only hint available is the password is next to the word _millionth_ , thus by doing by simple `grep` command we would be able to retrieve the password.

The code: `grep 'millionth' data.txt`

<img src="/images/blogimages/2019-04-24/bandit8.PNG">

> Password: `cvX2JJa4CFALtqS87jk27qwqGhBM9plV`

## Bandit Level - 9

Once again the password is hidden under the file **data.txt** which has almost 1000 lines with patterns similar to level passwords. The challenge gives us a single hint, saying that the password to next level which is stored inside the file is repeated only once. This gives us an opportunity to use the `uniq` command which displays unique results from any file that is provided as input. However, `sort` command is first used to sort out the results and we then pipe the input to the `uniq` command to get the results. The below code gets you the password.

The code: `sort data.txt | uniq -u`

<img src="/images/blogimages/2019-04-24/bandit9.PNG">

> Password: `UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR`

## Bandit Level - 10

Almost a straightforward challenge, you can even issue a `cat` command on the **data.txt** file to view the contents and search for a series of *=*. The password will be right next there. However, for better readability, I recommend using `xxd` command on the data file.

The code: `xxd data.txt`

<img src="/images/blogimages/2019-04-24/bandit10.PNG">

> Password: `truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk`

## Bandit Level - 11

Another simpler challenge, this is about encoding and decoding. The file that contains the password is encoded using Base64 Algorithm. As we all know, Base64 has a decoding algorithm as well, make use of the command `base64` with `-d` flag on the encoded file to retrieve the password.

The Code: `base64 -d data.txt`

<img src="/images/blogimages/2019-04-24/bandit11.PNG">

> Password: `IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR`

## Bandit Level - 12

This challenge is based on substitution algorithm known as **ROT-13**. The password contained with the file **data.txt** has been encoded using the ROT-13 algorithm. The below command makes use of the `tr` command to retrieve the plain text from the file. As we have  26 alphabets, dividing by 2 gives 13 (2 Sets). Set 1: A-M and Set 2: N-Z. Working of the ROT-13 algorithm is very simple, For encoding purposes, the characters from the first set (Set 1) is replaced with the characters in (Set 2), and the decoding process is as simple as it is. For eg: A will be encoded to N, G will be encoded to T, vice-versa. Make use of the below code to solve the challenge.

`cat data.txt |  tr '[A-Za-z]' '[N-ZA-Mn-za-m]'`

<img src="/images/blogimages/2019-04-24/bandit12.PNG">

> Password: `5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu`

## Bandit Level - 13

It was quite a good challenge. After logging in, you will have the file **data.txt** on the home directory. You will be making use of **/tmp** directory because, it has world-writable access, as you need to do some decompression according to the algorithm. (_Guess I gave some hint_).

By doing a `cat` command on the file, it seems like that the file is garbled up with some hex related data. Let us make use of the `xxd` command we used it **Bandit Level - 10** challenge.

Well, why are making use of `xxd` command? _When you did a `cat` command on the file, the contents of the file revealed **data2.bin** and this is the ultimate reason we are using this._

Since we need a directory to work with, Let us create a directory on the **/tmp** folder. _Follow the commands to get the password_

The crux behind the challenge is we analyze the file with `file` command and notice the algorithm used for the compression and we then use the appropriate decompression algorithm to unravel the password.

<img src="/images/blogimages/2019-04-24/bandit13_1.PNG">
<p></p>
<img src="/images/blogimages/2019-04-24/bandit13_2.PNG">
<p></p>

> Password: `8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL`

## Bandit Level - 14

Pretty straightforward, your home directory will be having the private key of user **bandit14**, all you need is to connect to the local SSH server with the private key file provided. After logging in, `cat` the password from the usual **/etc/bandit_pass/** directory.

<img src="/images/blogimages/2019-04-24/bandit14_1.PNG">
<p></p>
<img src="/images/blogimages/2019-04-24/bandit14_2.PNG">
<p></p>

> Password: `4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e`

## Bandit Level - 15

There seems a service running on the port 30000, it reveals the password for **Bandit Level - 15** when the password of **Bandit Level - 14** is subjected. This challenge lets you understand how to connect to any service and run commands. This challenge can be completed by using many tools like `nc`, `telnet`, etc.

<img src="/images/blogimages/2019-04-24/bandit15.PNG">
<p></p>

> Password: `BfMYroe26WYalil77FoDi9qh59eK5xNr`

## Bandit Level - 16

As the challenge clearly points out that a service is running on port 30001 that can speak SSL, make use of `openssl` command to complete the challenge. Connect to localhost using `openssl` on the port and provide the password of **Bandit Level - 15** to unravel the password for **Bandit Level - 16**

<img src="/images/blogimages/2019-04-24/bandit16_1.PNG">
<p></p>
<img src="/images/blogimages/2019-04-24/bandit16_2.PNG">

> Password: `cluFn7wTiGryunymYOu4RcffSxQluehd`


## Bandit Level - 17

As per the challenge, you need to find out the service that is running between the port 31000 to 32000 that speaks to SSL. Better off with `nmap` and with `--open` flag, the open ports can be found. After finding the open port, connect to the service using `openssl` and then paste the password of **Bandit Level - 16** to obtain the RSA Private Key for the user **_bandit17_**. Once you retrieve the private key, copy the private key file to the **/tmp** directory and connect to localhost using SSH private key file you just copied and login as user **_bandit17_**. As you try to do this step, your request will be rejected as precautionary safety measure. Since your private key file is in the **/tmp** directory and is readable by other users, you should make sure that is readable only by **you**. For this, you will be using the `chmod` command as shown. After assigning the appropriate permissions for your private key file, you will be able to authenticate as **_bandit17_**. After logging, the password for the user can be read from the usual **/etc/bandit_pass/** directory.

<img src="/images/blogimages/2019-04-24/bandit17_1.PNG">
<p></p>
<img src="/images/blogimages/2019-04-24/bandit17_2.PNG">
<p></p>
<img src="/images/blogimages/2019-04-24/bandit17_3.PNG">
<p></p>
<img src="/images/blogimages/2019-04-24/bandit17_4.PNG">
<p></p>

> Password: `xLYVMN9WE5zQ5vHacb0sZEVqbrp7nBTn`

## Bandit Level - 18

Your home directory consists of two files, the password to the next level is stored in the **passwords.new** file and there is a condition regarding a _change_. So we use a `diff` command to reveal the password for the next level.

<img src="/images/blogimages/2019-04-24/bandit18.PNG">

> Password: `kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd`

## Bandit Level - 19

With the above password you will be able to SSH as user **_bandit19_** , but as soon as you authenticate the code under ~/.bashrc on the home directory of the **_bandit19_** executes and terminates the connection. Also, it seems that there is file named **readme** on the home directory which has the password to the next level. To tackle this, make use of `-t` argument along with the SSH connection.

_For WeChall Users Only:_ If you are playing **wechall** challenges, then you could also so run the `wechall` command  along with the `-t` argument to add to the score board.

<img src="/images/blogimages/2019-04-24/bandit19.PNG">

> Password: `IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x`

## Bandit Level - 20

You will find a Self-Executable file under your home directory. This can be found when you run the `file` command on it. When you do `id` command with that you see that the file has EID (Effective ID as a different user ID **_bandit20_** , which gives you a pointer that this file can run commands as user **_bandit20_**). So make use of this opportunity and `cat` the password file to reveal the password for next level.

<img src="/images/blogimages/2019-04-24/bandit20.PNG">

> Password: `GbKksEFF4yrVs6il55v6gwY5aVje5f0j`

## Bandit Level - 21

To complete this challenge, make yourself comfortable with the `screen` command. The target is running a service which will connect to any port on the localhost that you specify.
1. First run `screen` command, now you are inside separate process so run a `netcat` listening service as `nc localhost -p9090 -vvl`
2. Press `Enter` key and paste the previous level (**Bandit Level - 20**) password on the console.
3. Press `Ctrl+A` to come out of the screen. (Eg. type `screen -r <id>` to get into that screen session)
4. From the home directory, run the `./suconnect 9090`
5. Now press `Ctrl+A` to go back to the screen session to retrieve the password from the `netcat` service.

<img src="/images/blogimages/2019-04-24/bandit21_1.PNG">
<p></p>
<img src="/images/blogimages/2019-04-24/bandit21_2.PNG">
<p></p>
<img src="/images/blogimages/2019-04-24/bandit21_3.PNG">
<p></p>

> Password: `gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr`


## Bandit Level - 22

All you need is to read and analyze the cron job file. Since you need the password for **Bandit Level - 22**, you ought to look into the file **cronjob_bandit22.sh**. From the cron job file you see that, the password is being written to a file in the **/tmp** directory. Everything here is straightforward and no twists.

<img src="/images/blogimages/2019-04-24/bandit22.PNG">

> Password: `Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI`

## Bandit Level - 23

As the challenge suggests, make a copy of the bash script **cronjob_bandit23.sh** that is under the **/usr/bin** directory. Copy the contents of the script, create a folder under for you under the **/tmp** directory and paste the contents of the script under a test script named **test.sh**, give it executable permission using `chmod +x`. Run the script and note the output hash after the **/tmp** directory. Now, doing a `cat` on the file which was created by the script under the **/tmp** directory reveals the password of **Bandit Level - 22** , so in this case by replacing the `whoami` command to `bandit23` will reveal the path of the hash that will be created under the **/tmp** directory. By doing a `cat` command on that particular hash will lead to the password for the next level.

<img src="/images/blogimages/2019-04-24/bandit23.PNG">

> Password: `jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n`

## Bandit Level - 24

An interesting level. The cron job executes this file **cronjob_bandit24.sh** that is under the **/usr/bin** directory, that frequently deletes the user created scripts under the folder **/var/spool/bandit24** directory.

Copy the below script and paste it in on the command line of the directory **/var/spool/bandit24**

`echo '#!/bin/bash`
<br>
`myname=$(cat /etc/bandit_pass/bandit24)`
<br>
`mkdir "/tmp/sh423"`
<br>
`touch "/tmp/sh423/$myname"`
<br>
`cp "/etc/bandit_pass/bandit24 /tmp/sh423/"' > sh4.sh | chmod +x sh4.sh`

Code Explained: Since the cron job will make the code run with the privileges of **_bandit24_**, our code makes a copy of the password and pastes it to the **/tmp** directory.

<img src="/images/blogimages/2019-04-24/bandit24.PNG">

> Password: `UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ`


## Bandit Level - 25

Another beautiful level that lets you under the concept of **Brute-Forcing**. A service is running on the port 30002 that takes the password of **Bandit Level - 24**  and a four digit number ranging from **0000** to **9999** separated by a space in between. So you need to write a program that generates all the **10000** numbers to a file and subject that file as input to the service that is running on the port 30002.

As I am more comfortable with **PHP** than **Bash**, I had to write a program in PHP to generate all the number combinations and the password of the previous level has to be concatenated along with it.

`<?php`
<br>
`ini_set('display_errors', 1);`
<br>
`ini_set('display_startup_errors', 1);`
<br>
`error_reporting(E_ALL);`
<br>
`set_time_limit(0);`
<br>
`ini_set('max_execution_time', 1600); //300 seconds = 5 minutes`
<br>
`ini_set('max_execution_time', 0); // for infinite time of execution `
<p></p>

`for($i=0;$i<10000;$i++)`
<br>
`{`
<br>
        &nbsp;&nbsp;&nbsp;&nbsp;`if(strlen($i)==1)`
	<br>
        &nbsp;&nbsp;&nbsp;&nbsp;`{`
	<br>
                &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`echo "UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ "."000".$i."\n";`
	<br>
        &nbsp;&nbsp;&nbsp;&nbsp;`}`
	<br>
        &nbsp;&nbsp;&nbsp;&nbsp;`else if(strlen($i)==2)`
	<br>
        &nbsp;&nbsp;&nbsp;&nbsp;`{`
	<br>
                &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`echo "UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ "."00".$i."\n";`
	<br>
        &nbsp;&nbsp;&nbsp;&nbsp;`}`
	<br>
        &nbsp;&nbsp;&nbsp;&nbsp;`else if(strlen($i)==3)`
	<br>
        &nbsp;&nbsp;&nbsp;&nbsp;`{`
	<br>
                &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`echo "UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ "."0".$i."\n";`
	<br>
        &nbsp;&nbsp;&nbsp;&nbsp;`}`
	<br>
        &nbsp;&nbsp;&nbsp;&nbsp;`else`
	<br>
	&nbsp;&nbsp;&nbsp;&nbsp;`{`
	<br>
		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`echo "UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ ".$i."\n";`
	<br>
	&nbsp;&nbsp;&nbsp;&nbsp;`}`
	<br>
`}`

Now copy the output and paste it a file.

I had issues sending the whole 10000 entries to the service on port  30002 while using the command `cat numberfile | nc 127.0.0.1 30002 > output.txt` as it was timing out at **7178**<sup>th</sup> entry. (The above specified command will try all the 10000 entries starting from 0000 to 10000, it pipes each and every entry to the `nc` command and then appends the output to that file named **output.txt**)

Another tip to avoid timeouts is to check the combinations in sets, Use `uniq` command to find the password in the file. `uniq output.txt`. If you are getting timeouts, send inputs in 4000, such that    such that the password can be found in 2-3 attempts.

After running the command `cat numberfile | nc 127.0.0.1 30002 > output.txt`, we will be left with **output.txt**. On doing a `cat`
 command we see that the timeout occurred at **7178**, in this case we subject last **4000** entries using `tail '4000q' | nc 127.0.0.1 30002 > final_result.txt`

 <img src="/images/blogimages/2019-04-24/bandit25_1.PNG">
 <p></p>
 <img src="/images/blogimages/2019-04-24/bandit25_2.PNG">
 <p></p>
 <img src="/images/blogimages/2019-04-24/bandit25_3.PNG">
 <p></p>

> Password: `uNG9O58gUE7snukf3bvZ0rxhtnjzSGzG`


## Bandit Level - 26

Honestly, this was the toughest challenge for me on the whole **Bandit** box, took me a couple of days to think _**laterally**_ and overcome this challenge.

In the home directory of bandit25, you will find the private key of user **_bandit26_**, when you login with `ssh bandit26@localhost -i bandit26.sshkey` , you will authenticated and immediately logged out. You will see a certain amount of text before you logout. Even if you add the `-t` argument while doing SSH, still you won't be able to complete this level. This is where you need to think **more**.

You need to make use of `more` command. Follow these steps to complete the challenge.
1. Before doing the SSH, try to resize your terminal screen as smaller as possible. such that you could see only one line of what you are typing.
2. After doing that and while you do the SSH command, you will be presented with `more` prompt.
3. Now type `v` to get into the `vi` edit mode. You will be presented with the editing mode for **text1.txt** file that is available on the **_bandit26_**'s home directory.
4. Now press `Esc` key and run the command to read the password file `:vi /etc/bandit_pass/bandit26` and press enter. You will now able to view the password of the file.
5. Now you need to **JailBreak** to obtain a proper shell. Again type `Esc` key and enter these commands.
<br>
`:set shell=/bin/bash`
<br>
`:shell`

<img src="/images/blogimages/2019-04-24/bandit26_1.PNG">
<p></p>
<img src="/images/blogimages/2019-04-24/bandit26_2.PNG">
<p></p>
<img src="/images/blogimages/2019-04-24/bandit26_3.PNG">
<p></p>
<img src="/images/blogimages/2019-04-24/bandit26_4.PNG">
<p></p>
<img src="/images/blogimages/2019-04-24/bandit26_5.PNG">
<p></p>
<img src="/images/blogimages/2019-04-24/bandit26_6.PNG">
<p></p>
<img src="/images/blogimages/2019-04-24/bandit26_7.PNG">
<p></p>
<img src="/images/blogimages/2019-04-24/bandit26_8.PNG">
<p></p>

> Password: `5czgV9L3Xx8JPOyRbXh6lQbmIOWvPT6Z`


## Bandit Level - 27

This is a straightforward level and is similar to **Bandit Level - 18**, use the Self-Executable binary to `cat` the password from the usual **/etc/bandit_pass** directory.

<img src="/images/blogimages/2019-04-24/bandit27.PNG">

> Password: `3ba3118a22e93127a4ed485be72ef5ea`

## Bandit Level - 28

Hail Git! The upcoming four to five consecutive challenges will be totally focused towards `git` commands. So if you have been contributing to open-source community in the past, these forthcoming levels would be a glide in the air.

The task is to clone the remote repository and then open the file to find the password. Pretty straightforward if you know the right command. Use the **/tmp** directory to clone your repository as it has the world-writable access.

The `git clone` command lets you complete the level. It clones the repository to your local directory as it is. You could then enter the password of **Bandit Level - 27** to clone the repository from the remote space.

`git clone ssh://bandit27-git@localhost/home/bandit27-git/repo`

<img src="/images/blogimages/2019-04-24/bandit28.PNG">

> Password: `0ef186ac70e04ea33b4c1853d2526fa2`

## Bandit Level - 29

After downloading the repository and doing a `cat` command on **README.md**, you notice that the password has been masked.
As you know GIT is a version system and it keeps track of all changes to the file as **_commits_**. You can view list of commits done to the file by issuing the command `git log`.

You can see there are 3 different commits done to the file. Inspect each of the commits by running the command. `git show <commithashid>` or simply do `git show` to directly get the password.

<img src="/images/blogimages/2019-04-24/bandit29_1.PNG">
<p></p>
<img src="/images/blogimages/2019-04-24/bandit29_2.PNG">
<p></p>

> Password: `bbc96594b4e001778eee9975372716b2`

## Bandit Level - 30

After downloading the repository and doing a `cat` command on **README.md**, it shows that _password is not in the production_. This clearly tells us to see elsewhere in the development branch areas.
1. Run the command `ls -lia` to find the hidden directory **.git**.
2. Get into the directory
3. Read the file **packed-refs** to get the hashes of the branches.
4. Cycle the hash ids the branches to get the password for the next level.
5. Use the command, `git show <commithashid>` to find the password to the next level.

<img src="/images/blogimages/2019-04-24/bandit30_1.PNG">
<p></p>
<img src="/images/blogimages/2019-04-24/bandit30_2.PNG">
<p></p>

> Password: `5b90576bedb2cc04c86a9e924ce42faf`

## Bandit Level - 31

I totally don't understand the purpose of this challenge as it is very similar to **Bandit Level - 30** challenge. Follow the same procedure the obtain the password for the next level.

<img src="/images/blogimages/2019-04-24/bandit31.PNG">

> Password: `47e603bb428404d265f59c42920d81e5`

## Bandit Level - 32

In this challenge, you need to push a file named **key.txt** to the root directory of the remote git using the content provided. You could follow these commands.
1. This command `echo 'May I come in?' > key.txt` creates a file **key.txt** and writes the content inside it.
2. The `git status` command lets you know that if any files have been added, deleted, updated in the current repository. So after creating the file and as you run `git status` command, nothing shows up. However, if you create any other file for instance `touch bla` and do a `git status` command, it shows that a new file named **bla** has been added to the repository.
3. So this has something to do with the file **.gitignore** which is a hidden file in the current directory. Inspecting the file `cat .gitignore` shows that it has **\*.txt** in it. (which means the file changes for **txt** files will not be shown)
4. All you have to do is edit the **.gitignore** file and replace the **\*.txt** with **\*.gitignore**.
5. Now add the file using the command `git add key.txt`
6. Now commit the changes using the command `git commit -m 'Adding key.txt'`
7. At last push the changes to the remote repository by using the command `git push origin`
8. You will be providing the password of **Bandit Level - 31** during the push operation.
9. The password will be revealed as the push operation completes.

<img src="/images/blogimages/2019-04-24/bandit32.PNG">

> Password: `56a9bf19c63d650ce78e6ec0354ee45e`

## Bandit Level - 33

The final level of Bandit box as of April 2019. Interesting level as it converts all the commands to uppercase rendering the output useless. This challenge can be solved by making use of one of the **Bash Special Parameters** listed below.
- `$*`
- `$@`
- `$#`
- `$?`
- `$-`
- `$$`
- `$_`
- `$!`
- `$0`

The special parameter `$0` helped to me to break out from the upper shell prompt and finding the password was again straightforward.

<img src="/images/blogimages/2019-04-24/bandit33.PNG">

> Password: `c9c3199ddf4121b10cf581a98d51caee`

---

### If you have better ways to solve the challenges, feel free to post/discuss it over the comments section.
<p></p>
### Thank you for being here.
