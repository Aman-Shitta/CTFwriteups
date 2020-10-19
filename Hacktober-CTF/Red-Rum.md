DESCRIPTION:
```
Red Rum

We want you to infiltrate DEADFACE as a programmer. Thing is, they're picky about who they bring in.
They want to make sure you're the real deal when it comes to programming. Generate a list of numbers 1-500.
For each number divisible by 3, replace it with Red; for each number divisible by 5, replace it with Rum. For numbers divisible by both 3 AND 5, replace it with RedRum.

nc env2.hacktober.io 5000

```

1. Use netcat utility to connect with the service/programm running 
  -> ncat (windows)
  -> nc (unix)
  
    The Description asks for generating a list of numbers form 1 to 500 and replace (%3 == 0) by "Red" and (%5==0) by "Rum" and (%5 == 0 and %3 == 0) by "RedRum".
    so with the help of python script 

2. Create a script to generate list 

##### redrum.py
```
l = [i for i in range(1,500)]

s = ""
for _ in l:
	if (_%3 == 0 and _%5 == 0):
		s += "RedRum,"
	elif _%3 == 0:
		s += "Red,"
	elif _%5 == 0:
		s += "Rum,"
	else:
		s += str(_)+","

s = s.strip(',')  # strip out the last un-necessasry comma in the end.
s += "\n"
print(s)
```
--> Run the Program!
##### OUTPUT
```
root@ScottThePC:/mnt/c/Users/Aman Shitta/Desktop# python3 redrum.py
1,2,Red,4,Rum,Red,7,8,Red,Rum,11,Red,13,14,RedRum,16,17,Red,19,Rum,Red,22,23,Red,Rum,26,Red,28,29,RedRum,31,32,Red,34,Rum,Red,37,38,Red,Rum,41,Red,43,44,RedRum,46,47,Red,
49,Rum,Red,52,53,Red,Rum,56,Red,58,59,RedRum,61,62,Red,64,Rum,Red,67,68,Red,Rum,71,Red,73,74,RedRum,76,77,Red,79,Rum,Red,82,83,Red,Rum,86,Red,88,89,RedRum,91,92,Red,94,Rum,
Red,97,98,Red,Rum,101,Red,103,104,RedRum,106,107,Red,109,Rum,Red,112,113,Red,Rum,116,Red,118,119,RedRum,121,122,Red,124,Rum,Red,127,128,Red,Rum,131,Red,133,134,RedRum,136,137,
Red,139,Rum,Red,142,143,Red,Rum,146,Red,148,149,RedRum,151,152,Red,154,Rum,Red,157,158,Red,Rum,161,Red,163,164,RedRum,166,167,Red,169,Rum,Red,172,173,Red,Rum,176,Red,178,179
,RedRum,181,182,Red,184,Rum,Red,187,188,Red,Rum,191,Red,193,194,RedRum,196,197,Red,199,Rum,Red,202,203,Red,Rum,206,Red,208,209,RedRum,211,212,Red,214,Rum,Red,217,218,Red,Rum,
221,Red,223,224,RedRum,226,227,Red,229,Rum,Red,232,233,Red,Rum,236,Red,238,239,RedRum,241,242,Red,244,Rum,Red,247,248,Red,Rum,251,Red,253,254,RedRum,256,257,Red,259,Rum,Red,
262,263,Red,Rum,266,Red,268,269,RedRum,271,272,Red,274,Rum,Red,277,278,Red,Rum,281,Red,283,284,RedRum,286,287,Red,289,Rum,Red,292,293,Red,Rum,296,Red,298,299,RedRum,301,302,
Red,304,Rum,Red,307,308,Red,Rum,311,Red,313,314,RedRum,316,317,Red,319,Rum,Red,322,323,Red,Rum,326,Red,328,329,RedRum,331,332,Red,334,Rum,Red,337,338,Red,Rum,341,Red,343,344,
RedRum,346,347,Red,349,Rum,Red,352,353,Red,Rum,356,Red,358,359,RedRum,361,362,Red,364,Rum,Red,367,368,Red,Rum,371,Red,373,374,RedRum,376,377,Red,379,Rum,Red,382,383,Red,Rum,
386,Red,388,389,RedRum,391,392,Red,394,Rum,Red,397,398,Red,Rum,401,Red,403,404,RedRum,406,407,Red,409,Rum,Red,412,413,Red,Rum,416,Red,418,419,RedRum,421,422,Red,424,Rum,Red,
427,428,Red,Rum,431,Red,433,434,RedRum,436,437,Red,439,Rum,Red,442,443,Red,Rum,446,Red,448,449,RedRum,451,452,Red,454,Rum,Red,457,458,Red,Rum,461,Red,463,464,RedRum,466,467,
Red,469,Rum,Red,472,473,Red,Rum,476,Red,478,479,RedRum,481,482,Red,484,Rum,Red,487,488,Red,Rum,491,Red,493,494,RedRum,496,497,Red,499 
```
3. Input the list genrated as the input to programm running on the server

```
root@ScottThePC:/mnt/c/Users/Aman Shitta/Desktop# nc env2.hacktober.io 5000
DEADFACE gatekeeper: If you want to join our programmers circle, you need to show that you can at least do the basics. 
Send the first 500 (1 - 500) Red Rums to show you're serious. You answer should be comma-separated with no spaces.

1,2,Red,4,Rum,Red,7,8,Red,Rum,11,Red,13,14,RedRum,16,17,Red,19,Rum,Red,22,23,Red,Rum,26,Red,28,29,RedRum,31,32,Red,34,Rum,Red,37,38,Red,Rum,41,Red,43,44,RedRum,46,47,Red,
49,Rum,Red,52,53,Red,Rum,56,Red,58,59,RedRum,61,62,Red,64,Rum,Red,67,68,Red,Rum,71,Red,73,74,RedRum,76,77,Red,79,Rum,Red,82,83,Red,Rum,86,Red,88,89,RedRum,91,92,Red,94,Rum,
Red,97,98,Red,Rum,101,Red,103,104,RedRum,106,107,Red,109,Rum,Red,112,113,Red,Rum,116,Red,118,119,RedRum,121,122,Red,124,Rum,Red,127,128,Red,Rum,131,Red,133,134,RedRum,136,
137,Red,139,Rum,Red,142,143,Red,Rum,146,Red,148,149,RedRum,151,152,Red,154,Rum,Red,157,158,Red,Rum,161,Red,163,164,RedRum,166,167,Red,169,Rum,Red,172,173,Red,Rum,176,Red,178,
179,RedRum,181,182,Red,184,Rum,Red,187,188,Red,Rum,191,Red,193,194,RedRum,196,197,Red,199,Rum,Red,202,203,Red,Rum,206,Red,208,209,RedRum,211,212,Red,214,Rum,Red,217,218,Red,
Rum,221,Red,223,224,RedRum,226,227,Red,229,Rum,Red,232,233,Red,Rum,236,Red,238,239,RedRum,241,242,Red,244,Rum,Red,247,248,Red,Rum,251,Red,253,254,RedRum,256,257,Red,259,Rum,Red,
262,263,Red,Rum,266,Red,268,269,RedRum,271,272,Red,274,Rum,Red,277,278,Red,Rum,281,Red,283,284,RedRum,286,287,Red,289,Rum,Red,292,293,Red,Rum,296,Red,298,299,RedRum,301,302,Red,
304,Rum,Red,307,308,Red,Rum,311,Red,313,314,RedRum,316,317,Red,319,Rum,Red,322,323,Red,Rum,326,Red,328,329,RedRum,331,332,Red,334,Rum,Red,337,338,Red,Rum,341,Red,343,344,RedRum,
346,347,Red,349,Rum,Red,352,353,Red,Rum,356,Red,358,359,RedRum,361,362,Red,364,Rum,Red,367,368,Red,Rum,371,Red,373,374,RedRum,376,377,Red,379,Rum,Red,382,383,Red,Rum,386,Red,388,
389,RedRum,391,392,Red,394,Rum,Red,397,398,Red,Rum,401,Red,403,404,RedRum,406,407,Red,409,Rum,Red,412,413,Red,Rum,416,Red,418,419,RedRum,421,422,Red,424,Rum,Red,427,428,Red,Rum,
431,Red,433,434,RedRum,436,437,Red,439,Rum,Red,442,443,Red,Rum,446,Red,448,449,RedRum,451,452,Red,454,Rum,Red,457,458,Red,Rum,461,Red,463,464,RedRum,466,467,Red,469,Rum,Red,472,
473,Red,Rum,476,Red,478,479,RedRum,481,482,Red,484,Rum,Red,487,488,Red,Rum,491,Red,493,494,RedRum,496,497,Red,499,Rum        

flag{h33eeeres_j0hnny!!!}
```

FALG : flag{h33eeeres_j0hnny!!!}
--------------------------------
