# Bandit Over The Wire
---------------------------------------------------------------------------------------------------------------
## Bandit level 0
key-The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.
- So I used ```ssh bandit0@bandit.labs.overthewire.org -p 2220``` to login into bandit level 0 using password as bandit0, then ls from ls I got ```readme``` so I used ```cat readme```. 
- From this I got the password.
```
bandit0@bandit:~$ ls
readme
bandit0@bandit:~$ cat readme
NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
```
## Bandit level 1-2
key-The password for the next level is stored in a file called - located in the home directory.
- I used ```ssh bandit1@bandit.labs.overthewire.org -p 2220``` and password as ```NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL``` to login to bandit level1.
```
bandit1@bandit:~$ ls
-
bandit1@bandit:~$ ls -l
total 4
-rw-r----- 1 bandit2 bandit1 33 Apr 23 18:04 -
bandit1@bandit:~$ cat ./-
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
```
## Bandit level 2-3
key-The password for the next level is stored in a file called spaces in this filename located in the home directory.
- Login with ```ssh bandit2@bandit.labs.overthewire.org -p 2220```
- Doing an ls shows that the filename has spaces in it. To deal with passing it as a command parameter, it needs to be enclosed within quotes - " ".```cat "spaces in this filename"```
- to open dash file name we use ""
```
bandit2@bandit:~$ ls
spaces in this filename
bandit2@bandit:~$ ls -l
total 4
-rw-r----- 1 bandit3 bandit2 33 Oct 16  2018 spaces in this filename
bandit2@bandit:~$ cat "spaces in this filename"
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
```
## Bandit level 3-4
key-The password for the next level is stored in a hidden file in the inhere directory.
-Login with ```ssh bandit3@bandit.labs.overthewire.org -p 2220```
- To view the hidden files in a directory the ```-a``` option for ls should be used, and to obtain the password for the next level, i.e. bandit5, a cat on that hidden file would do it.
- Before that, we need to change into the inhere directory using the cd command.
- Here . represents the current directory and .. represents the parent directory.
```
bandit3@bandit:~$ ls
inhere
bandit3@bandit:~$ cd inhere/
bandit3@bandit:~/inhere$ ls
bandit3@bandit:~/inhere$ ls -a
.  ..  .hidden
bandit3@bandit:~/inhere$ cat .hidden
2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
```
## Bandit level 4-5
key-The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.
-Login with ssh bandit4@bandit.labs.overthewire.org -p 2220
- cd into inhere and check what it contains. Inside we have many files.
```
bandit4@bandit:~/inhere$ ls
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file0
```
-Now again, doing it for each and every file is very inefficient. Here the Linux wildcard character asterisk (*) would be useful. It matches one or more occurrences of any character, including no character. So, using it to match all file names to check with file would help.
```
bandit4@bandit:~/inhere$ file ./*
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
bandit4@bandit:~/inhere$ cat ./-file07
lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
```
## Bandit level 5-6
-Login with ssh bandit5@bandit.labs.overthewire.org -p 2220
```
bandit5@bandit:~$ ls
inhere
bandit5@bandit:~$ cd inhere/
bandit5@bandit:~/inhere$ ls
maybehere00  maybehere02  maybehere04  maybehere06  maybehere08  maybehere10  maybehere12  maybehere14  maybehere16  maybehere18
maybehere01  maybehere03  maybehere05  maybehere07  maybehere09  maybehere11  maybehere13  maybehere15  maybehere17  maybehere19
bandit5@bandit:~/inhere$ find . -readable -size 1033c
./maybehere07/.file2
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU
```
## Bandit level 6-7
- Login with ssh bandit7@bandit.labs.overthewire.org -p 2220
- This requires a similar thought process to what bandit6 required, but this time we search from the root directory - /.
- The following options along with their respective value according to the constraints are given to find 
- Now, in since we cant search through all the directories in the file system due to lack of permissions, we do have our resultant file in that output. To extract that, an inverse search with the string "find:" on the piped output with the grep command should work. v is the grep command option to do a sort of negation on the pattern match, i.e. inverse search.
```
bandit6@bandit:~$ find / -group bandit6 -user bandit7 -size 33c | grep -v "find:"
/var/lib/dpkg/info/bandit7.password
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99
```
## Bandit level 7-8
- Login with ssh bandit7@bandit.labs.overthewire.org -p 2220
- This a simple pipe - | and grep on data.txt, with the search pattern being the string "millionth".
```
bandit7@bandit:~$ ls
data.txt
bandit7@bandit:~$ cat data.txt | grep millionth
millionth        TESKZC0XvTetK0S9xNwm25STk5iWrBvP
```
## Bandit level 8-9
- Login with ssh bandit8@bandit.labs.overthewire.org -p 2220
- A quick cat on data.txt gives out a lost of potential possible passwords for the next level. This does seem like a combo of commands and piping will be useful.
- Referring to the "Commands you may need to solve this level" section on the webpage, I checked out the man pages of sort and uniq.
- uniq has an option c which gives the count of a particular unique line in the given data if they are contiguous. The sort - command helps us make repeated occurances of possible passwords sorted one after the other, i.e. contiguous. So, it has become a matter of piping the sorted data to uniq -c and then grep "1 ".
```
bandit8@bandit:~$ ls
data.txt
bandit8@bandit:~$ sort data.txt | uniq -c | grep "1 "
      1 EN632PlfYiZbn3PhVK3XOGSlNInNE00t
```
## Bandit level 9-10
- Login with ssh bandit9@bandit.labs.overthewire.org -p 2220
- This is what the cat on data.txt gives.
```
bandit9@bandit:~$ cat data.txt
�pE 0NNyzb[a}okJ��#yf68~"SĬ72�z�8ϻ0˼5m)L���Ap=z�Fv]9DLW
```

- Here, the string command is what has to be used, and this is what the man page for it say: strings - print the strings of printable characters in files.. Which is pretty much the reason it has to be used for this level.
- After looking at the the output from strings on data.txt the password for the next level is in the line that has === in it. So, piping that command with a grep on the string pattern should give us a clear view of the password.

```
bandit9@bandit:~$ strings data.txt | grep ===
2========== the
========== password
========== isa
========== G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
```
## Bandit level 10-11
- Login with ssh bandit10@bandit.labs.overthewire.org -p 2220
- Since the content in data.txt is base64 encoded we should use the command base64 with the option -d to decode it.
- Base64 is a way to encode binary data into an ASCII character set known to pretty much every computer system, in order to transmit the data without loss or modification of the contents itself.
```
bandit10@bandit:~$ base64 -d data.txt
The password is 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
```
## Bandit level 11-12
- Login with ssh bandit11@bandit.labs.overthewire.org -p 2220
- Looking at the commands that might help section in the description of this level, I see the tr command. This automatically made me think it was a translation commands keeping in context the level's goal, since lower and uppercase letters need to be rotated/translated by 13 positions.
- Looking up the man page for tr tells us that's exactly what it does. It takes in sets of characters that are to be translated, which in our case means rotating the alphabet by 13 positions.
```
bandit11@bandit:~$ bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
The password is JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
```
