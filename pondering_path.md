## challenge 1-the path variable
 you will disrupt the operation of the /challenge/run program. This program will DELETE the flag file using the rm command. However, if it can't find the rm command, the flag will not be deleted, and the challenge will give it to you! Thus, you must make it so that /challenge/run also can't find the rm command

## flag:
pwn.college{0Da3NBZ6fj2jBuY2M9sYoY1Xmp-.QX2cDM1wiMxIzNzEzW}

## my solve:
```
hacker@path~the-path-variable:~$ rm /flag
rm: remove write-protected regular file '/flag'?
hacker@path~the-path-variable:~$ export PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{0Da3NBZ6fj2jBuY2M9sYoY1Xmp-.QX2cDM1wiMxIzNzEzW}
```

## new learning:
1. There is a special shell variable, called PATH, that stores a bunch of directory paths in which the shell will search for programs corresponding to commands.

## challenge 2-setting path


## flag:
pwn.college{spxuV1vG5ZkeT0Tvins-Qgk3-0C.QX1cjM1wiMxIzNzEzW}

## mysolve:
```
hacker@path~setting-path:~$ PATH=/challenge/more_commands /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{spxuV1vG5ZkeT0Tvins-Qgk3-0C.QX1cjM1wiMxIzNzEzW}
```
## new learning:
1.Recall that PATH stores a list of directories to find commands in and, for commands in nonstandard places, we must typically execute them via their path
```
hacker@dojo:~$ ls /home/hacker/scripts
goodscript	badscript	okayscript
hacker@dojo:~$ goodscript
bash: goodscript: command not found
hacker@dojo:~$ /home/hacker/scripts/goodscript
YEAH! This is the best script!
hacker@dojo:~$
```

## challenge 3-finding commands
In this challenge, we added a win command somewhere in your $PATH, but it won't give you the flag. Instead, it's in the same directory as a flag file that we made readable by you! You must find win (with the which command), and cat the flag out of that directory!

## flag:
pwn.college{0reXVbGIPb1JJVauvJoMAr5HXuF.01NzEzNxwiMxIzNzEzW}

## my solve:
```
hacker@path~finding-commands:~$ which win
/challenge/paths/940/win
hacker@path~finding-commands:~$ cat /challenge/paths/940/flag
pwn.college{0reXVbGIPb1JJVauvJoMAr5HXuF.01NzEzNxwiMxIzNzEzW}
```

## new learning:
1.Mirroring what the shell does when searching for commands, which looks at each directory in $PATH in order and prints the first file it finds whose name matches the argument you passed.

## challenge 4-adding commands
 the win command that /challenge/run executed was stored in /challenge/more_commands. This time, win does not exist! Recall the final level of Chaining Commands, and make a shell script called win, add its location to the PATH, and enable /challenge/run to find it!

## flag:
pwn.college{o-gVZXgBkRFvTshhAaYZ0Jleybd.QX2cjM1wiMxIzNzEzW}

## new learning:
1. /challenge/run runs as root and will call win.
2. Thus, win can simply cat the flag file. Again, the win command is the only thing that /challenge/run needs,
3.  so you can just overwrite PATH with that one directory. But remember,
4.   if you do that, your win command won't be able to find cat


## challenge 5-hijacking commands
 You have experience creating the win command when the previous challenge needed it. What else can you create?

## flag:
pwn.college{cGqP9B_DCHbr6JbHNPZ_u8kBgyI.QX3cjM1wiMxIzNzEzW}

## mysolve:
```
hacker@path~hijacking-commands:~$ mkdir -p /home/hacker/mybin
cat > /home/hacker/mybin/rm <<'EOF'
#!/bin/sh
IFS= read -r flag < /flag
printf '%s\n' "$flag"
EOF
chmod +x /home/hacker/mybin/rm
export PATH=/home/hacker/mybin:$PATH
which rm
/challenge/run
/home/hacker/mybin/rm
Trying to remove /flag...
Found 'rm' command at /home/hacker/mybin/rm. Executing!
pwn.college{cGqP9B_DCHbr6JbHNPZ_u8kBgyI.QX3cjM1wiMxIzNzEzW}
```

## new learning:

Armed with your knowledge, you can now carry out some shenanigans. This challenge is almost the same as the first challenge in this module. Again, this challenge will delete the flag using the rm command. But unlike before, it will not print anything out for you
