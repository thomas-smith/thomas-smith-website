---
title: Zero out EAX
date: 2017-05-18 19:32:08
---
To Zero out EAX we can use the following.

```ASM
AND EAX,554E4D4A
AND EAX,2A313235
```

If yo take **554E4D4A** and convert it to binary you will get **1010101010011100100110101001010** if we then take
**2A313235** and convert that to binary we get **101010001100010011001000110101**. If we then AND both the binary together we get **0000000000000000000000000000000**

```
1010101010011100100110101001010
0101010001100010011001000110101 - Added additional 0 to make the lengths the same
-------------------------------
0000000000000000000000000000000
```
