---
title: X86 Registers Descriptions
date: 2017-06-21 15:22:08
---

Bellow is a short explanition of the different X86 registers.

General registers
```ASM
EAX - Main register used in arithmetic calculations. Also known as accumulator, as it holds results
      of arithmetic operations and function return values.
EBX - The Base Register. Pointer to data in the DS segment. Used to store the base address of the
      program.
ECX - The Counter register is often used to hold a value representing the number of times a process
      is to be repeated. Used for loop and string operations.
EDX - A general purpose registers. Also used for I/O operations. Helps extend EAX to 64-bits.
```

Segment registers
```ASM
CS - Holds the Code segment in which your program runs. Changing its value might make the computer hang.
DS - Holds the Data segment that your program accesses. Changing its value might give erroneous data.

ES -
FS -
GS - These are extra segment registers available for far pointer addressing like video memory and such.

SS - Holds the Stack segment your program uses. Sometimes has the same value as DS. Changing its value
     can give unpredictable results, mostly data related.
```

Index of pointers registers
```ASM
ESI - Source Index register. Pointer to data in the segment pointed to by the DS register.  Used as
      an offset address in string and array operations. It holds the address from where to read data.
EDI - Destination Index register. Pointer to data (or destination) in the segment pointed to by the
      ES register.  Used as an offset address in string and array operations. It holds the implied
      write address of all string operations.
EBP - Base Pointer. Pointer to data on the stack (in the SS segment).  It points to the bottom of the
      current stack frame. It is used to reference local variables.
EIP - Instruction Pointer (holds the address of the next instruction to be executed)
ESP - Stack Pointer (in the SS segment). It points to the top of the current stack frame. It is used
      to reference local variables.
```

Indicator
```ASM
EFLAGS

Bit   Label    Description
---------------------------
0      CF      Carry flag
2      PF      Parity flag
4      AF      Auxiliary carry flag
6      ZF      Zero flag
7      SF      Sign flag
8      TF      Trap flag
9      IF      Interrupt enable flag
10     DF      Direction flag
11     OF      Overflow flag
12-13  IOPL    I/O Priviledge level
14     NT      Nested task flag
16     RF      Resume flag
17     VM      Virtual 8086 mode flag
18     AC      Alignment check flag (486+)
19     VIF     Virutal interrupt flag
20     VIP     Virtual interrupt pending flag
21     ID      ID flag

```
