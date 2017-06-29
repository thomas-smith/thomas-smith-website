---
title: Base64 PHP Nuke user credentials
date: 2017-06-29 05:38:33
---

### A simple script to base64 user credentials

To encode text to base64, use the following syntax:
```bash
$ echo -n "admin:PWD_FROM_DATABASE:" | base64
YWRtaW46UFdEX0ZST01fREFUQUJBU0U6
```

To decode text to base64, use the following syntax:
```bash
$ echo -n YWRtaW46UFdEX0ZST01fREFUQUJBU0U6 | base64 -d
"admin:PWD_FROM_DATABASE:"
```
