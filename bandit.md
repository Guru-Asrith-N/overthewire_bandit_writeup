#### writeup on https://overthewire.org/wargames/bandit/

#### level 0 

tried logging in
forgot to enter username as bandit0
did not enter -p for port

#### level 0 -> level 1

entered readme first
after going through commands entered cat readme
looked up in google for how to exit a server
```
password NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
```

#### level 1 -> level 2 

first entered `cat -`
looked up in google for what to enter
finally entered `cat ./-`
```
password rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
```

#### level 2 -> level 3

if space is there in between filename then linux considers it as 2 seperate files rather than a single one
we can place a filename with spaces in double quotes
finally entered `cat "spaces in this filename"`
```
password aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
```

#### level 3 -> level 4

since file is hidden read about find command
entered `find inhere`
then finally entered `cat inhere/.hidden`
```
password 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
```

#### level 4 -> level 5 

used `cat *`
used `cd inhere`
`cat *`
used `cat -A`
used `cat -v`
none of them worked

so went through everything manually using `cat ./-file00` , etc
found human readable text in file 07
```
password lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
```

#### level 5 -> level 6

tried `cd ` command , `du` command and `file ` command to check size of file 
searched in google in multiple sites 
finally found a blog pertaining to the problem
changed filename and made it not exectuble 
```
password P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU
```

#### level 6 -> level 7 

went to `find` manual and searched for how to find username and group name 
in the code found one line which didn't have access denied
used `cat` command for that one line
```
password z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
```

#### level 7 -> level 8

read the manual of all the commands given for solving level 7 -> level 8 
`grep` is the command needed to find a word in a file
```
password TESKZC0XvTetK0S9xNwm25STk5iWrBvP
```

#### level 8 -> level 9

tried `uniq data.txt`
tried `uniq -u data.txt`
tried `uniq -u 1 data.txt`

went through piping and redirection
 tried `uniq data.txt > data` to create a new file and read it 
 tried `uniq data.txt >> data`
 tried `cat data.txt | uniq`
 tried `cat data.txt | sort`

 finally did `cat data.txt | sort | uniq` and got the password
```
password EN632PlfYiZbn3PhVK3XOGSlNInNE00t
```

#### level 9 -> level 10

tried `sort -i data.txt`
tried `sort -i data.txt | cat`
tried `sort -d data.txt | cat`
tried `sort -h data.txt | cat`
tried `cat data.txt | grep '=' | sort -i`
tried `cat data.txt | grep '=' | sort -i | cat`
tried `man strings` it didn't show anything so tried searching it in google 
finally entered `strings data.txt`
```
password G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
```

#### level 10 -> level 11

used `base64 -d data.txt`
```
password 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
```

#### level 11 -> level 12

referred the manual for tr 
used the link 'ROT13 on wikipedia' given in level
enterred `cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'`
```
password JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
```

#### level 12 -> level 13

made directory using `mkdir /tmp/myname12345`
tried using `zcat data.txt | xxd | cp /tmp/myname12345`
tried using `zcat data.txt | xxd | cat /tmp/myname12345`
tried using `xxd -d data.txt`
tried using `xxd -d data.txt | cat /tmp/myname12345`

finally realized you are supposed to use `xxd -r` in a new directory

made new directory using `mkdir /tmp/myname123456`
copied text to new directory using `cp data.txt /tmp/myname123456/name` and stored in a file named 'name'
since password is in a hex dump file used `xxd -r name | cat > name1` and saved data  in file named 'name1'
used `file` command to detemine compression type `file name1` . It is a gzip compression
tried using `gzip -d name1`  didn't work 
used `mv` command to change file extension `mv name1 name2.gz`
used `gzip -d name2.gz | cat > name2`
used `file` command to detemine compression type `file name2` . It is a bzip2 compression
used `mv` command to change extension `mv name2 name3.bz`
used `bzip2 -d name3.bz | cat > name3` and saved data in file named 'name3'
used `file` command to detemine compression type `file name3` . It is a gzip compression
used `mv` command to change file extension `mv name3 name4.gz`
used `gzip -d name4.gz | cat > name4`
used `file` command to detemine compression type `file name4` . It is a tar compression
searched in google to find how to extract tar files
used `mv` command to change file extension `mv name4 name5.tar`
used `tar xvf name5.tar` . Recieved output as data5.bin
searched google for how to extract '.bin' files
tried using `chmod` and `sudo` command. Didn't work
tried using `file` command `file data5.bin` file is a tar compressed file
used `mv` command to change file extension `mv data5.bin name6.tar`
used `tar xvf name6.tar` . Recieved output as data6.bin
tried using `file` command `file data6.bin` file is a bzip2 compressed file
used `mv` command to change file extension `mv data6.bin name6.bz`
used `bzip2 -d name6.bz ` 
used `file name6` . It is a tar compressed file
used `mv` command to change file extension `mv name6 data6.tar`
used `tar xvf data6.tar` . Recieved output as data8.bin
used `file data8.bin`. It is a gzip compressed file
used `mv` command to change file extension `mv data8.bin data9.gz`
used `gzip -d data9.gz`. recieved output as 'data9'
used `file  data9` . It is a ASCII texted file
used `cat data9`. Got password
```
password wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw
```

#### level 13 -> level 14

entered the level
read the manual of `ssh` and helpful reading material
used `ls` command
used `cat sshkey.private` 
used `file sshkey.private`
exited the server and tried to use `ssh bandit14@localhost -i sshkey.private`. Didn't work
searched in google 
entered the bandit13 server again and entered `ssh bandit14@localhost -i sshkey.private` . Didn't work
searched in google
entered `ssh bandit14@localhost -i sshkey.private -p 2220` entered the localhost server
since they said password is in '/etc/bandit_pass/bandit14' . tried using `cat` command . Found the password
exit all servers 
```
password fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
```

#### level 14 -> level 15

entered level 
read all helpful materials and commands
tried using `ls` and `ls -a`
used `ssh bandit14@localhost -p 30000` to enter server. Didn't work
used `s_client` command to see if connection is opened
used `s_client` command and other commands to see if it is possible to enter the localhost server
used `openssl s_client -connect localhost:30000` 
read all helpful materials again 
finally searched in google . Didn't get it 
read the question and saw that the password of the current level is to be submitted at localhost in port 30000
got the password of current level
searched for all commands again
while searching in nc command found a webpage 
entered `nc -v localhost 30000` and password of current level in next line
```
password jN2kgmIXJ6fShzhT2avhotn4zcka6tnt
```

#### level 15 -> level 16

used `nc -v localhost 30001`
used `nc -v localhost 30001 -d ssl`
used `nc -d ssl -v localhost 30001`
nothing worked

tried searching in google for something related to openssl as it is ssl encrypted
found a blog pertaining to the problem
used `openssl s_client -connect localhost:30001`
```
password JQttfApK4SeyHwDlI9SXGR50qclOAil1
```

#### level 16 -> level 17

used `nmap -p 31000:32000`
used `nmap -p 31000-32000`
used `nmap -p T:31000-32000`
used `nmap -sV -p 31000-32000`
used `nmap --p 31000-32000 -sV`

finally realised that target is localhost

used `nmap -p 31000-32000 localhost`
got 5 open servers
used `openssl s_client -connect localhost:<portnumber>` for each port individually 
the port is 31790 and it gives a private RSA key

used `mkdir /tmp/RSA`
entered file using `cd /tmp/RSA`
used `cat > 2.key`
copied RSA key and pasted inside 2.key
used `ssh -i 2.key bandit17@localhost` . Didn't work
used `ssh -i 2.key bandit17@localhost -p 31790` . Didn't work
used `chmod 2.key` . Didn't work
used `chmod 600 2.key` 
used `ssh -i 2.key bandit17@localhost -p 2220`

used `cat passwords.new`
used `cat passwords.old`
tried `sort`, `uniq`, etc
finally used `cat /etc/bandit_pass/bandit17`
```
password VwOSWtCA7lRKkTfbr2IDh6awj9RNZM5e
```

#### level 17 -> level 18

used `man diff`
tried `diff -q passwords.new passwords.old`
tried `diff passwords.new passwords.old`
```
password hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg
```

#### level 18 -> level 19

used `ssh bandit18@bandit.labs.overthewire.org -p 2220`
used `ssh -4 bandit18@bandit.labs.overthewire.org -p 2220`
used `ssh -6 bandit18@bandit.labs.overthewire.org -p 2220`
used `ssh -t bandit18@bandit.labs.overthewire.org -p 2220`
used `ssh -f bandit18@bandit.labs.overthewire.org -p 2220`
used `ssh -k bandit18@bandit.labs.overthewire.org -p 2220`
searched in google 
found a blog regarding problem
tried used `ssh -t bandit18@bandit.labs.overthewire.org /bin/sh`
tried used `ssh -t bandit18@bandit.labs.overthewire.org /bin/sh -p 2220`
used `ssh -t bandit18@bandit.labs.overthewire.org -p 2220 /bin/sh`
entered the server 
used `ls`
used `cat readme`
```
password awhqfNnAbclnaukrpqDYcF95h7HoMTrC
```

#### level 19 -> level 20

read all helpful materials
used `ls`
used `cat bandit20-do`
used `file bandit-do`

searched in google 

used `ls -l`
login should be done as user bandit20

used `su`, `sudo`, `runuser` none of them worked

searched in google 

used `./bandit20`
used `./bandit20-do`
used `./bandit20-do cat /etc/bandit_pass`
used `./bandit20-do cd /etc/bandit_pass`

used `./bandit20-do cat /etc/bandit_pass/bandit20`
```
password VxCazJaVykI6W36BkBU0mJTCM8rR95XT
```

#### level 20 -> level 21

used `ls`
used `cat suconnect`
used `file suconnect`
used `ls -l`
used `./suconnect ls` . Didn't work

searched in google. found a link regarding `nc` and how it listens 

https://www.geeksforgeeks.org/practical-uses-of-ncnetcat-command-in-linux/

used another terminal 
used `nc -lp 100` in terminal 2 . Didn't work
read in the link again
used `nc -lvp 100` in terminal 2

came to terminal 1
used `./suconnect nc -lp 100`
used `./suconnect nc -p 100`. Didn't work 
used `./suconnect` . Showed how suconnect is used
used `./suconnect 100` . Didn't work

realised that both terminals should be in same server for it to connect. Changed server of terminal 2 to bandit20

connection was established

entered password of level 20 in terminal 2
password of level 21 was sent to terminal 2
```
password NvEJF7oVjkddltPSrdKEFOllh9V1IVcq
```

#### level 21 -> level 22

used `ls`
used `cron`
mentioned in the question to look into /etc/cron.d/
used `cat /etc/cron.d` . It is a directory
used cd `/etc/cron.d`
used `ls`
searched in cronjob_bandit22 as it is most likely to have password
used `cat cronjob_bandit22` . 
searched in google
found repeating file was given '/usr/bin/cronjob_bandit22'
used `cat /usr/bin/cronjob_bandit22 `
```
password WdDozAdTM2z9DiFEQ2mGlwngMfj4E2ff
```
