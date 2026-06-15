# Scripting
The shebang line `#!/bin/bash` 

first line as always. this tells the system which interpreter to use. Scripts without having it, the system doesn't know what to do with the file. it consists of a hash (#) and an exclamation point (!), followed by the absolute path to the interpreter engine.

The commands - all the usual commands like `echo, find, grep, cp` all of it works the same inside a script.

Executable permission

the file needs `+x` or the system refuses to run it as a program. 
by default, when creating a new text file using vi, vim, or nano, Linux marks it as a read/write file not as a program.

To make it as a script so that the system can run it, chmod must grant execution rights : `chmod +x /path/to/scripts/script.sh`

Exit status codes (exit)

Every commands or script run in Linux leaves behind an invisible report card called an Exit Status (an integer between 0 and 255).

- 0 means Success, Everything completed perfectly.
- any number from 1 to 255 means failure or an error has occurred.
In a script, the script will automatically return the exit status of the very last command that ran inside it. declaring `exit 0` at the very bottom when a script fulfills its duties cleanly would be a good habbit.
the variable `$?` holds the exit code of the last command that ran. example `echo $?    # prints 0 if last command succeeded, non-zero if it failed`

Simple example script 

```
#!/bin/bash

# display the current logged-in user
echo "Current Administrator:"
whoami

# terminate the script and declaring success
exit 0
```
---
# IF Statements
```bash
#!/bin/bash

if [ -f /etc/passwd ]
then
    echo "File exists"
fi
```
```bash
#!/bin/bash

if [ -f /etc/passwd ]
then
    echo "File exists"
fi
```
### Comparing Values
```bash
if [ "$name" = "Morty" ] equal 
if [ "$name" = "Morty" ] not equal
```
```bash
if [ $age -gt 18 ]
```

## Common operators
```
-eq  equal
-ne  not equal
-gt  greater than
-lt  less than
-ge  greater/equal
-le  less/equal
```
# FOR Loops
```bash
for user in john mary bob
do
    echo $user
done
```
Checking multiple servers
```bash
for server in web01 web02 db01
do
    ping -c 1 $server
done
```
## Process files
```bash
for file in *.txt
do
    echo $file
done
```

# WHILE Loops
```bash
count=1

while [ $count -le 5 ]
do
    echo $count
    count=$((count+1))
done
```
# Command Output
Capturing command output -  `Capture command output:`
using it `echo $hostname`
example 
```bash
disk=$(df -h / | tail -1 | awk '{print $5}')

echo $disk
```
# Exit Codes
```bash
0 = success
non-zero = failure
```
```bash
ping -c 1 google.com
echo $?
```
```bash
if ping -c 1 google.com
then
    echo "Network OK"
else
    echo "Network Down"
fi
```
# && and ||
```bash
if command
then
   echo success
fi
```
is same as 
```bash
command && echo success

example use case :  id morty && echo "User exists"
                    id morty || echo "User missing"
```
# Functions
```bash
check_disk() {
    df -h /
}

check_disk
```
examples 
```bash
#!/bin/bash

service=sshd

if systemctl is-active --quiet $service
then
    echo "$service running"
else
    echo "$service stopped"
fi
```
```bash
#!/bin/bash

for user in alice bob charlie
do
    useradd $user
done
```

```bash
#!/bin/bash

echo "===== HOSTNAME ====="
hostname

echo
echo "===== MEMORY ====="
free -h

echo
echo "===== DISK ====="
df -h
```