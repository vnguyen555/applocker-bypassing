
Checking for writable directory since applocker have trusted directories
-w to locate writable directories
-u to suppress any errors 
-s to recurse through all subdirectories.
```
C:\Users\User\Desktop\SysinternalsSuite>accesschk.exe "user" C:\Windows -wus

Accesschk v6.15 - Reports effective permissions for securable objects
Copyright (C) 2006-2022 Mark Russinovich
Sysinternals - www.sysinternals.com

RW C:\Windows\appcompat
RW C:\Windows\apppatch
RW C:\Windows\AppReadiness
```

Checking if a folder is exectuable from above results
```
C:\Users\User\Desktop\SysinternalsSuite>icacls.exe C:\Windows\Tasks
C:\Windows\Tasks NT AUTHORITY\Authenticated Users:(RX,WD)
                 BUILTIN\Administrators:(F)
                 BUILTIN\Administrators:(OI)(CI)(IO)(F)
                 NT AUTHORITY\SYSTEM:(F)
                 NT AUTHORITY\SYSTEM:(OI)(CI)(IO)(F)
                 CREATOR OWNER:(OI)(CI)(IO)(F)

Successfully processed 1 files; Failed processing 0 files
```
