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
  
  -----------------------------------------------
  flag{728ec98bfaa302b2dfc2f716d3de7869f3eadcbf}
  -----------------------------------------------
