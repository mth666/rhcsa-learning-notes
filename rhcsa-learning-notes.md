# working with echo commands
## What is echo?
echo command print text to the terminal (standard output). Its one of the most used commands in Linux, for scripting, writing to files, checking variables, and many more.
## redirection operators 
```bash
>   = write to file, overwrite everything
>>  = add to the end
```
## >  write (overwrite)
```
echo "Hello" > myfile.txt      # creates or overwrites myfile.txt
echo "New content" > myfile.txt # previous content is gone
```
## >>  append
```
echo "Line 1" > myfile.txt     # creates file with "line 1"
echo "Line 2" >> myfile.txt    # adds "line 2" below  file now has both
```
*** note : when unsure use >> accidentally overwriting a config file.
## echo flags
-n no newline at the end echo 
```
-n "no newline"
```
-e enable escape characters (like \n, \t) 
```
echo -e "line1\nline2"
```
## -e escape characters
```
\n new line
\t  tab
\\ backslash
echo -e "Name:\tJoe\nRole:\tSysadmin"
display as 
Name:   Joe
Role:   Sysadmin
```
## printing variables

```bash
NAME="joe"
echo $NAME           # joe
echo "Hello, $NAME"  # Hello, joe
echo "Hello, ${NAME}man"  # Hello, joeman  
note :  use {} to avoid confusion
```

## single quotes vs double quotes
"double" = variables and escapes are expanded
'single' = everything is treated as literal text
```
NAME="joe"
echo "$NAME"    # joe    (variable expanded)
echo '$NAME'    # $NAME  (printed literally as it is) 
```

## practical uses

add a line to a config file
```
echo "PermitRootLogin no" >> /etc/ssh/sshd_config
```
## make a quick file
```
echo "192.168.1.50  rhel-vm" >> /etc/hosts
```
## check an environment variable
```
echo $PATH
echo $HOME
echo $USER
```
## write a simple script header
```
echo "#!/bin/bash" > myscript.sh
echo "echo Hello from script" >> myscript.sh
```
## echo vs printf 
printf is more powerful and predictable than echo -e. and it is more prefer in scripts. 
```
printf "Name:\t%s\nRole:\t%s\n" "Joe" "Sysadmin"
```
```
display 
Name:   Joe
Role:   Sysadmin
note: use echo for quick one liners in the terminal. 
use printf inside shell scripts for consistent formatting.
```
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

# tar command - archiving, compressing and decompressing files and directories

## tar command concepts 
### archiving 
(means tape archiving back in the days): combining multiple files and directories into a single file (.tar). 
however, archiving alone not reduce file size on its own.
for that we need to use 
### compressing: 
reducing the file size of the archive using an algorithm.
### decompressing: 
restoring the compressed archive back to its original size before extraction.
### 3 core operations
always have to choose exactly one of these primary modes:
```bash
-c : Create a new archive
-x : Extract an existing archive
-t : list (test) the contents of an archive without extracting
```
## compression modifiers or compression algorithm types
those flags tell tar which compression tool to use alongside the core operation:

```bash
-z means gzip compression type with tar.gz or .tgz extension and speed is fast.
-j means bzip2 compression type with tar.bz2 or .tbz2 extension and speed is slow.
-J means xz compression type with .tar.xz extension and speed is slowest among all. 
```
### additional flags
```bash
-f (f means File here): specifies the archive file name. -f flag must always be the last flag in the option block because tar command require the filename to immediately follows it.
-C (C means directory here or its' from Change directory): instruct tar to switch to the target directory before doing the extration. this command is use to prevents files from unpacking into current working directory.
```
## daily commands
### making archives
```bash
tar -cvf backup.tar /path/to/source

# create a gzip compressed archive (common)
tar -czvf backup.tar.gz /path/to/source

# create a highly compressed xz archive (usually for production backups)
tar -cJvf backup.tar.xz /path/to/source
```
### viewing archives without extrating
```bash
list contents of a compressed archive without extracting it
tar -tzf backup.tar.gz
```
### extracting archives
```bash
extract to the current working directory
tar -xzvf backup.tar.gz
# extract to a specific target directory (-C changes directory first)
tar -xzvf backup.tar.gz -C /tmp
```

# extract a single specific file from the archive
```bash
tar -xzvf backup.tar.gz path/to/file.txt
notes: modern versions of tar (including the one in RHEL 10) are intelligence enough to auto detect the compression formats during extraction. which means flags like -z, -j, or -J could be ignore when extrating. example:
tar -xvf any_archive.tar.xz -C /target/dir
```
## summarized commands table
```bash
tar -czvf archive.tar.gz folder/    create gzip compressed
tar -cjvf archive.tar.bz2 folder/   create bzip2 compressed
tar -cJvf archive.tar.xz folder/    create xz compressed
tar -xzvf archive.tar.gz            extract gzip
tar -xzvf archive.tar.gz -C /path/  extract to specific location
tar -tzvf archive.tar.gz            list contents without extracting
```
# using man pages and search inside it
```bash
man tar
/   press / to start searching (kinda like using less command) 
after that type what need to look for, for example
/-C (to find out more about tar -C )
press enter and it jumps straight to it. 
press n to find next stuffs
exit by pressing q
```
---
