```
Description:

Squids in the linux pool

Note: No automation tool required.

ssh ctf@squid.darkarmy.xyz -p 10000 password: wolfie
```

1. With the name of the challenge Its quite clear that it has something to do with the SUID

   So, connect via the ssh. 
   
   ```
   wolf@d4c4a8eb634e: find . -type f -perm /4000 2> /dev/null
   wolf@d4c4a8eb634e: 
                        ./opt/src/src/iamroot
                        ./usr/bin/passwd
                         ./usr/bin/newgrp
                         ./usr/bin/mount
                         ./usr/bin/umount
                         ./usr/bin/chfn
                         ./usr/bin/chsh
                         ./usr/bin/su
                         ./usr/bin/gpasswd
                         ./usr/bin/sudo
                         
   wolf@d4c4a8eb634e: ./opt/src/src/iamroot
    Segmentation fault (core dumped)

   wolf@d4c4a8eb634e: ./opt/src/src/iamroot flag
      cat : flag: No such file or directory    
      
   wolf@cacef6d31c7f:/$ ./opt/src/src/iamroot /root/flag.txt
      darkCTF{y0u_f0und_the_squ1d}

```

flag: darkCTF{y0u_f0und_the_squ1d}

