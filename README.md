# Kali Configuration
```bash
## set keyboard layout
setxkbmap -layout de
# set timezone
sudo dpkg-reconfigure tzdata
```

# Find without errors
```bash
find / -name test.py 2>/dev/null
```

# Save all Terminal Output to File
https://unix.stackexchange.com/questions/200637/save-all-the-terminal-output-to-a-file
```bash
# Convert RAW Output to TXT
cat $SCRIPT_LOG_FILE | perl -pe 's/\e([^\[\]]|\[.*?[a-zA-Z]|\].*?\a)//g' | col -b > $txtfile
```

# NTFS Alternate Datastream
```bash
# show alternate datastreams
dir /R

# output alternate datastreams
powershell Get-Content -Path "hm.txt" -Stream "root.txt"
```
