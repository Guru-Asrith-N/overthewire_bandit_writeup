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
