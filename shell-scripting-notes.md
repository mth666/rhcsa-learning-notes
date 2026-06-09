# Scripting
The shebang line `#!/bin/bash` 
first line, always. this tells the system which interpreter to use. Scripts without having it, the system doesn't know what to do with the file. it consists of a hash (#) and an exclamation point (!), followed by the absolute path to the interpreter engine.

The commands - all the usual commands like `echo, find, grep, cp` all of it works the same inside a script.

Executable permission

the file needs `+x` or the system refuses to run it as a program. 
by default, when creating a new text file using vi, vim, or nano, Linux marks it as a read/write data file-not as a program.

To make it as a script so that the system can run it, chmod must grant execution rights : `chmod +x /path/to/scripts/script.sh`

Exit status codes (exit)

Every commands or script run in Linux leaves behind an invisible report card called an Exit Status (an integer between 0 and 255).

- 0 means Success, Everything completed perfectly.
- any number from 1 to 255 means failure or an error has occurred.
In a script, the script will automatically return the exit status of the very last command that ran inside it. declaring `exit 0` at the very bottom when a script fulfills its duties cleanly would be a good habbit.

And everything else - variables, loops, conditionals are just building on top of the above foundational things.