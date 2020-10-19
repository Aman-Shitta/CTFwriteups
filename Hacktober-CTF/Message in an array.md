DESCRIPTION


```
Message in an Array

Deadface has left a message in the code. Can you read the code and figure out what it says? 
You may also copy and paste the code in an emulator. Enter the answer as flag{Word Word Word Word}.

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace GhostTown
{
    class Program
    {
        static void Main(string[] args)
        {
           string[] str = new string[4] {"DEADFACE","Nothing", "Stop", "Will"};

           Console.WriteLine("{1} {3} {2} {0}", str);
         }
    }
}
```

str -> ["DEADFACE","Nothing", "Stop", "Will"].
```
str[1] -> Nothing
str[3] -> Will
str[2] -> Stop
str[4] -> DEADFACE
```
FALG : flag{Nothing Will Stop DEADFACE}
----------------------------------------
