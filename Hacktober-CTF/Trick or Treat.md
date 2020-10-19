DESCRIPTION
```
We found a script being used by DEADFACE. 
It should be relatively straightforward, but no one here knows Python very well. 
Can you help us find the flag in this Python file?
```

##### trickortreat.py
```
from hashlib import md5 as m5


def show_flag():
    b = 'gginmevesogithoooedtatefadwecvhgghu' \
        'idiueewrtsadgxcnvvcxzgkjasywpojjsgq' \
        'uegtnxmzbajdu'
    c = f"{b[10:12]}{b[6:8]}{b[4:6]}{b[8:10]}" \
        f"{b[4:6]}{b[12:14]}{b[2:4]}{b[0:2]}" \
        f"{b[14:16]}{b[18:20]}{b[16:18]}{b[20:22]}"
    m = m5()
    m.update(c.encode('utf-8'))
    d = m.hexdigest()
    return f"flag{{{d}}}"


def show_msg():
    print(f'Smell my feet.')


show_msg()
```

In the python file *show_flag()* function returns the flag. 
so simply add *print(show_flag())* to the end of the python file and run.

```
C:\Users\mrwhite\Desktop> python trickortreat.py
Smell my feet.
flag{2f3ba6b5fb8bb84c33b584f981c2d13d}
```

FLAG : flag{2f3ba6b5fb8bb84c33b584f981c2d13d}
---------------------------------------------
