### working with echo commands
### What is echo?
echo command print text to the terminal (standard output). Its one of the most used commands in Linux, for scripting, writing to files, checking variables, and many more.
## redirection operators 
```bash
>   = write to file, overwrite everything
>>  = add to the end
```
### >  write (overwrite)
```
echo "Hello" > myfile.txt      # creates or overwrites myfile.txt
echo "New content" > myfile.txt # previous content is gone
```
### >>  append
```
echo "Line 1" > myfile.txt     # creates file with "line 1"
echo "Line 2" >> myfile.txt    # adds "line 2" below  file now has both
```
*** note : when unsure use >> accidentally overwriting a config file.
### echo flags
-n no newline at the end echo 
```
-n "no newline"
```
-e enable escape characters (like \n, \t) 
```
echo -e "line1\nline2"
```
### -e escape characters
```
\n new line
\t  tab
\\ backslash
echo -e "Name:\tJoe\nRole:\tSysadmin"
display as 
Name:   Joe
Role:   Sysadmin
```
### printing variables
NAME="joe"
echo $NAME           # joe
echo "Hello, $NAME"  # Hello, joe
echo "Hello, ${NAME}man"  # Hello, joeman  
note :  use {} to avoid confusion

### single quotes vs double quotes
"double" = variables and escapes are expanded
'single' = everything is treated as literal text

NAME="joe"
echo "$NAME"    # joe    (variable expanded)
echo '$NAME'    # $NAME  (printed literally as it is) 

### practical uses

add a line to a config file
```
echo "PermitRootLogin no" >> /etc/ssh/sshd_config
```
### make a quick file
```
echo "192.168.1.50  rhel-vm" >> /etc/hosts
```
### check an environment variable
```
echo $PATH
echo $HOME
echo $USER
```
### write a simple script header
```
echo "#!/bin/bash" > myscript.sh
echo "echo Hello from script" >> myscript.sh
```
## echo vs printf 
printf is more powerful and predictable than echo -e. and it is more prefer in scripts. 
```
printf "Name:\t%s\nRole:\t%s\n" "Joe" "Sysadmin"
```
display 
Name:   Joe
Role:   Sysadmin
note: use echo for quick one liners in the terminal. 
use printf inside shell scripts for consistent formatting.
## quick echo command references 
```
echo "text"                  # print to terminal
echo "text" > file.txt       # write to file (overwrites)
echo "text" >> file.txt      # append to file
echo -n "text"               # no trailing newline
echo -e "line1\nline2"       # interpret escape chars
echo $VARIABLE               # print variable value
echo "${VAR}text"            # variable with adjacent text
echo '$VARIABLE'             # print literally   
```