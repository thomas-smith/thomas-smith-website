---
title: GDB
date: 2017-05-18 20:22:33
---

### Start GDB (with optional core dump).
```
gdb <program> [core dump]
```

### Start GDB and pass arguments
```
# gdb --args <program> <args…>
```

### Start GDB and attach to process.
```
# gdb --pid <pid>
```

### Set arguments to pass to program to be debugged.

```
set args <args...>
```

### Run the program to be debugged.
```
run
```

### Kill the running program.
```
kill
```

## Breakpoints

### Set a new breakpoint.
```
break <where>
```

### Remove a breakpoint.
```
delete <breakpoint#>
```

### Delete all breakpoints.
```
clear
```

### Enable a disabled breakpoint.
```
enable <breakpoint#>
```

### Disable a breakpoint.
```
disable <breakpoint#>
```

## Watchpoints

### Set a new watchpoint.
```
watch <where>
```
