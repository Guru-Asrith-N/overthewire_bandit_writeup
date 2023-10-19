#### writeup on https://overthewire.org/wargames/bandit/

#### level 0 

```
tried logging in
forgot to enter username as bandit0
did not enter -p for port
```

#### level 0 -> level 1

```
entered readme first
after going through commands entered cat readme
looked up in google for how to exit a server
password NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
```

#### level 1 -> level 2 

```
first entered cat -
looked up in google for what to enter
finally entered cat ./-
password rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
```

#### level 2 -> level 3

```
if space is there in between filename then linux considers it as 2 seperate files rather than a single one
we can place a filename with spaces in double quotes
finally entered cat "spaces in this filename"
password aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
```

#### level 3 -> level 4

```
since file is hidden read about find command
entered find inhere
then finally entered cat inhere/.hidden
password 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
```

#### level 4 -> level 5 

```
used cat *
used cd inhere
cat *
used cat -A
used cat -v
none of them worked

so went through everything manually using cat ./-file00 , etc
found human readable text in file 07
password lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
```

#### level 5 -> level 6
