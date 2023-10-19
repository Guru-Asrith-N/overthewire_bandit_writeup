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
