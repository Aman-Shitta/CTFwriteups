```
Description:
There's a vault hidden find it and retrieve the information. Note: Do not use any automated tools.

ssh ctf@vault.darkarmy.xyz -p 10000
Alternate: ssh ctf@13.126.135.177 -p 10000 password: wolfie
```

1. Connect via SSH.
2. Looking for a secret I found a hidden diretory in /home ```.secretdoor```

```
dark@b16af518a916:/home$ ls -al 
total 16
drwxr-xr-x 1 root root 4096 Sep 26 17:27 .
drwxr-xr-x 1 root root 4096 Sep 27 14:49 ..
drwxr-xr-x 1 root root 4096 Sep 26 17:27 .secretdoor
drwxr-xr-x 2 dark dark 4096 Sep 26 17:27 dark

dark@7db0b8b9ce7d:/home$ cd .secretdoor/

dark@7db0b8b9ce7d:/home/.secretdoor$ ls -al
total 28
drwxr-xr-x 1 root root  4096 Sep 26 17:27 .
drwxr-xr-x 1 root root  4096 Sep 26 17:27 ..
-rwxr-xr-x 1 root root 16704 Sep 24 06:56 vault

dark@7db0b8b9ce7d:/home/.secretdoor$ ./vault

wrong pin: (null)
dark@7db0b8b9ce7d:/home/.secretdoor$ ./vault 1

wrong pin: 1
dark@7db0b8b9ce7d:/home/.secretdoor$ ./vault 1234

wrong pin: 1234

```

The valut is an executable which takes asks for a PIN as an argument and check weather the PIN is correct.

So I automated the task using a simple bash script

```
#!/bin/bash
for i in {0..9999}
do
  /home/.secretdoor/vault $i
done


dark@7db0b8b9ce7d:/home/dark$ bash vault_sc.sh 
.
.
.
.
.
wrong pin: 8790

wrong pin: 8791

wrong pin: 8792

wrong pin: 8793

Vault Unlocked :A79Lo6W?O%;D;Qh1NIbJ0lp]#F^no;F)tr9Ci!p(+X)7@ 

wrong pin: 8795

wrong pin: 8796

wrong pin: 8797

wrong pin: 8798

wrong pin: 8799


.
.
.
.
```

``` DECODE : A79Lo6W?O%;D;Qh1NIbJ0lp]#F^no;F)tr9Ci!p(+X)7@ with BASE85 ```

```flag : darkCTF{R0bb3ry_1s_Succ3ssfullll!!}```
