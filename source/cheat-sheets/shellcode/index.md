---
title: Shellcode
date: 2017-06-24 17:21:33
---
# Shellcode x86 32bit

## Regdian
Converts a valid register address into hex code in little endian format.
```python
################################################################################
#                                                                              #
#  Author: Thomas Smith                                                        #
#  Description: Converts a valid register address into hex code in little      #
#               endian format.                                                 #
#  Usage: ./regdian 00112233                                                   #
#                                                                              #
################################################################################

#!/usr/bin/python
import sys
from termcolor import colored

def __string_is_hex(addr):
	try:
		int(addr, 16)
		return
	except ValueError:
		print colored("[x] The address must be valid.", 'red')
		sys.exit()


try:
	addr = sys.argv[1]

	__string_is_hex(addr)

	if len(addr) != 8:
		print colored("[x] The length of the input string should be 8", 'red')
	else:

		converted = r"\x" + r"\x".join(reversed([addr[i:i+2] for i in range(0, len(addr), 2)]))
		print "".join((
			colored("The original string was: ", 'green'),
			colored(addr, 'yellow'),
			colored(' the converted string is: "', 'green'),
			colored(converted, 'yellow'),
			colored('"', 'yellow')
		))

except IndexError:  
	print colored("[x] Usage ./regdian.py AABBCC", 'red')
   	sys.exit()

```
