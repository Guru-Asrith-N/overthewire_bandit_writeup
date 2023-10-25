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

