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
-----------------------------------------------------
FLAG : flag{cb07e9d6086d50ee11c0d968f1e5c4bf1c89418c}
-----------------------------------------------------
