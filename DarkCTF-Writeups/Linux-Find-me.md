```
Description
Mr.Wolf was doing some work and he accidentally deleted the important file can you help him and read the file?
ssh ctf@findme.darkarmy.xyz -p 10000 password: wolfie

Author : wolfy
```

1. The challenge description says the file was accidentally deleted while doing some work. 

   So looking at the processes running : 
   ```
   PID TTY      STAT   TIME COMMAND
      1 pts/0    Ss     0:00 /bin/bash PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin HOSTNAME=de3158a9a429 TERM=xterm HOME=/home/wolf1/
     10 pts/0    S      0:00 tail -f /home/wolf1/pass HOSTNAME=de3158a9a429 PWD=/home/wolf1 HOME=/home/wolf1/ LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35
     16 pts/0    R+     0:00 ps -eax HOSTNAME=de3158a9a429 PWD=/home HOME=/home/wolf1/ LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:c
   ```
   
   Process with PID 10 states that command ```tail -f /home/wolf1/pass``` is running.
   
   
2. But checking in ```/home/wolf1``` there is no such file named ```pass```
   So from this I get what file we need to see.
------------------------------------------------------------------------------------------
I tried looking up for how to view a contents of a backgroud process I came across this :
https://superuser.com/questions/283102/how-to-recover-deleted-file-if-it-is-still-opened-by-some-process

```/proc/<PID>/fd/```

```
These are links that point to the open files of the process whose pid is <PID> and fd is the "file descriptors",
which is an integer that identifies any program input or output in UNIX-like systems.
/proc/<PID>/fd/*
```
------------------------------------------------------------------------------------------

I read the contents of ```cat /proc/10/fd/*```
where ```/proc/10/fd/3``` gave the contents : ```mysecondpassword123```

wolf1@de3158a9a429: su wolf2
Password: 

``` and now we are wolf2. Now here we have a bunch of dirs so I listed them all recursively using ls -alR ```

```
wolf2@de3158a9a429: ls -alR
.
.
.
.
.
./proc/g:
total 12
drwxr-x--- 1 root wolf2 4096 Sep 17 04:39 .
drwxr-x--- 1 root wolf2 4096 Sep 17 04:39 ..
-rwxr-x--- 1 root wolf2   67 Sep 17 04:39 nice_work

wolf2@de3158a9a429: cat .proc/g/nicework | rev 
wolf2@de3158a9a429: }galf eht no gnidnats era uoy{FTCkrad 
                    darkCTF{w0ahh_n1c3_w0rk!!!}

```
```flag: darkCTF{w0ahh_n1c3_w0rk!!!} ```
