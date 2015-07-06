# [WinDbg](http://expdev-kiuhnm.rhcloud.com/2015/05/17/windbg/)

1. Switch to 64bits
 > !wow64ext.sw

 - not working on 32-bits binary
2. Expression
 > bp EIP+1 == bp 11 #EIP = 10

3. Pseudo-Register and Register
 - '$' = pseudo-register
 - '@' = register
 > @teb , $@teb = address of `TEB`

4. Exception `sxe`:

 break when module is loaded
 > sxe ld < module1 >, ... ,< module2 >

 list exception
 > sx

 `Single chance` exception : When exception is raised and pass to debugger

 `Second chance` exception : When raised exception is not handled by program.
 - ignore single step exception
 > sxi sse

5. BreakPoint

 ###Software
 - break on address
 > bp 2137192
 - number of `passed` required to activate breakpoint
 > bp 2137192 3
 - resume execution
 > g
 - run untill certain address
 > g < address >

 ###Hardware
 - use specific register on CPU for breaking
 > ba < mode > < address > < passes (Default=1) >
 - `< mode >`:
 - `e` for execute
 - `r` for read/write memory access
 - `w` for write memory access

 note: Hardware breakpoint created after process is started.

6. Stepping
 - `step in / trace` : `t`
 > break after every instruction
 - `step over` : `p`
 > break on every instruction without following `call` or `ints`
 - `step out` : `gu`
 > use to exit function, break on next `ret`

7. Displaying Memory
 - `db`: display bytes
 - `dw`: display words (2 bytes)
 - `dd`: display dwords (4 bytes)
 - `dq`: display qwords (8 bytes)
 - `dyb`: display bits
 - `da`: display null-terminated ASCII strings
 - `du`: display null-terminated Unicode strings
 - [Range] dd < start address > < end address >

8. Edit address
>e[b|d|w] < address > [val1 val2 ... val3]

9. Search Memory
>s [-d|-w|-b|-a-U] < start address > L?< number of elements > < search value >
