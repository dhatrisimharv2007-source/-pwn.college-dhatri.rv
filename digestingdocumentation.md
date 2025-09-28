## challenge 1-learning from documentation
The program for this challenge is /challenge/challenge, and you'll need to invoke it properly in order for it to give you the flag
## flag:
pwn.college{Qo349tw_isGF2PpvPfEAoCVpqYh.QX0ITO0wiMxIzNzEzW}
## my solve:
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{Qo349tw_isGF2PpvPfEAoCVpqYh.QX0ITO0wiMxIzNzEzW}
## new learnings:
1.Documentation is essential for understanding program usage and available arguments
2.Command-line arguments modify program behavior and functionality
3.Proper argument specification is crucial for correct program execution
4.Arguments like --giveflag are often documented in program help or manuals
5.Reading documentation saves time and prevents trial-and-error approaches
## references:
pwn.college explanation of the challenges and refernce videoes 

## challenge 2-learning complex usuage
Welcome to the documentation for /challenge/challenge! This program allows you to print arbitrary files to the terminal when given the --printfile argument. The argument to the --printfile argument is the path of the flag to read.
## flag:
pwn.college{stktjhllpwx9NTJIliQqxCBO97N.QX1ITO0wiMxIzNzEzW}
## my solve:
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{stktjhllpwx9NTJIliQqxCBO97N.QX1ITO0wiMxIzNzEzW}
## new learnings:
1. how to print the contents of a file
2. learnt that arguments can have arguments of their own.
3. eg, find has an argument name which in return has an argument of the file name.
## references:
pwn.college explanation of the challenges and refernce videoes 

## challenge 3-reading manuals
This level introduces the man command. man is short for manual, and will display (if available) the manual of the command you pass as an argument
## flag:
 pwn.college{c3iLsrING6l9zthvWfN2hCbJPsW.QX0EDO0wiMxIzNzEzW}
 ## my solve:
hacker@man~reading-manuals:~$ man challenge
hacker@man~reading-manuals:~$ /challenge/challenge --cisrlz 369
Correct usage! Your flag: pwn.college{c3iLsrING6l9zthvWfN2hCbJPsW.QX0EDO0wiMxIzNzEzW}
## new learning:
1.man command stands for manual
2.it opens the entire manual page for a given command
3.syntax man command.
4.pressing q will take you back to the terminal page exiting the manual page
## references:
pwn.college explanation of the challenges and refernce videoes

## challenge 4-searching manuals
You can scroll man pages with the arrow keys (and PgUp/PgDn) and search with /. After searching, you can hit n to go to the next result and N to go to the previous result. Instead of /, you can use ? to search backwards
## flag:
pwn.college{EJ_q83y8Dfj5EkQe6wh-iz0tVzp.QX1EDO0wiMxIzNzEzW}
## my solve:
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge --kwcvpp
Initializing...
Correct usage! Your flag: pwn.college{EJ_q83y8Dfj5EkQe6wh-iz0tVzp.QX1EDO0wiMxIzNzEzW}
## new learning
1.learnt how to search the man page using / sign
2.learnt how to search the man page backwards using ?
## references:
pwn.college explanation of the challenges and refernce videoes

## challenge 5-searching for manuals
This level is tricky: it hides the manpage for the challenge by randomizing its name. Luckily, all of the manpages are gathered in a searchable database, so you'll be able to search the man page database to find the hidden challenge man page! To figure out how to search for the right manpage, read the man page manpage by doing: man man!
## flag:
pwn.college{EwR82mMR7GiIwJ4x98QLpmwmp7_.QX2EDO0wiMxIzNzEzW}
## my solve:
hacker@man~searching-for-manuals:~$ man man
hacker@man~searching-for-manuals:~$ man -k challenge
wmiwxpmwmp (1)       - print the flag!
hacker@man~searching-for-manuals:~$ man wmiwxpmwmp
hacker@man~searching-for-manuals:~$ /challenge/challenge --wmiwxp 827
Correct usage! Your flag: pwn.college{EwR82mMR7GiIwJ4x98QLpmwmp7_.QX2EDO0wiMxIzNzEzW}
## new learning:
1.
## references:
pwn.college explanation of the challenges and refernce videoes

## challenge 6-helpful programs
Some programs don't have a man page, but might tell you how to run them if invoked with a special argument. Usually, this argument is --help, but it can often be -h or, in rare cases, -?, help, or other esoteric values like /? (though that latter is more frequently encountered on Windows).
## flag
 pwn.college{M6tLhGfp3B97noAgiYYM_2y0wDX.QX3IDO0wiMxIzNzEzW}
 ## my solve
 hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 639
hacker@man~helpful-programs:~$ /challenge/challenge -g 639
Correct usage! Your flag: pwn.college{M6tLhGfp3B97noAgiYYM_2y0wDX.QX3IDO0wiMxIzNzEzW}
## new learning
Some programs don't have a man page, but might tell you how to run them if invoked with a special argument. Usually, this argument is --help, but it can often be -h or, in rare cases, -?, help, or other esoteric values like /?
## references:
pwn.college explanation of the challenges and refernce videoe

challenge 7-help for bulletins
Some commands, rather than being programs with man pages and help options, are built into the shell itself. These are called builtins. Builtins are invoked just like commands, but the shell handles them internally instead of launching other programs. You can get a list of shell builtins by running the builtin help
## flag:
pwn.college{gIS91C2-eNiKOF9I1pIIh4Ja5bj.QX0ETO0wiMxIzNzEzW}
## my solve:
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!

    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "gIS91C2-".
hacker@man~help-for-builtins:~$ challenge --secret gIS91C2-
Correct! Here is your flag!
pwn.college{gIS91C2-eNiKOF9I1pIIh4Ja5bj.QX0ETO0wiMxIzNzEzW}
## new learning:
1. Some commands, rather than being programs with man pages and help options, are built into the shell itself. These are called builtins. Builtins are invoked just like commands, but the shell handles them internally instead of launching other programs
## references:
pwn.college explanation of the challenges and refernce videoe










