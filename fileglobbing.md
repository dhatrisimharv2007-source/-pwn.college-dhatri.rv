## challenge 1-matching with *
The first glob we'll learn is *. When it encounters a * character in any argument, the shell will treat it as a "wildcard" and try to replace that argument with any files that match the pattern.
## flag:
pwn.college{kqlGvQHvWlFI9UfqWoyOLMyOstl.QXxIDO0wiMxIzNzEzW}
## my solve:
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{kqlGvQHvWlFI9UfqWoyOLMyOstl.QXxIDO0wiMxIzNzEzW}
## new learning:
1.how to change directory without the use cd command
2.when the compiler meet * symbol it treats it as a wildcard and displays all the files in that directory.

## challenge 2- matching with ?

When it encounters a ? character in any argument, the shell will treat it as a single-character wildcard. This works like *, but only matches one character.
## flag:
pwn.college{ctHxxhgjb2IXpMi3cOu5jAiHwhj.QXyIDO0wiMxIzNzEzW}

## my solve:
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /?ha??enge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{ctHxxhgjb2IXpMi3cOu5jAiHwhj.QXyIDO0wiMxIzNzEzW}

## new learnings:
1.using ? and changing directories 
2. using ? and running files

## reference:

pwn.college explanation and its refernce videos 

## challege 3-matching with []
we will cover []. The square brackets are, essentially, a limited form of ?, in that instead of matching any character, [] is a wildcard for some subset of potential characters, specified within the brackets

## flag:
pwn.college{otM40N7fmG90Xo3fWWlXs2cM5lF.QXzIDO0wiMxIzNzEzW}

## my solve:

hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{otM40N7fmG90Xo3fWWlXs2cM5lF.QXzIDO0wiMxIzNzEzW}

## new learning:
1. learnt to call all files together at once by using command_filename[]\

## references:

pwn.college explanation and its refernce videos 

## challenge 4-matching paths with []

Globbing happens on a path basis, so you can expand entire paths with your globbed arguments.

## flag:
pwn.college{0htAS7mEZwo619OY31AADUROo1M.QX0IDO0wiMxIzNzEzW}

## my solve:
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{0htAS7mEZwo619OY31AADUROo1M.QX0IDO0wiMxIzNzEzW}

## new learning :
1. learnt how to call multiple files from difeerent directories

## references:

pwn.college explanation and its refernce videos 

## challenge 5-multiple globs
So far, you've specified one glob at a time, but you can do more! Bash supports the expansion of multiple globs in a single word

## flag:
pwn.college{s2Evb3xjQMWbKZ1CdUriSc7QRwS.0lM3kjNxwiMxIzNzEzW}

## my solve:
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{s2Evb3xjQMWbKZ1CdUriSc7QRwS.0lM3kjNxwiMxIzNzEzW}

## new learning:
1.shell looks for all files in / that start with anything (including nothing), then have an f and an l, and end in anything (including ag, which makes flag).

## references:
pwn.college explanation and its refernce videos 

## challenge 6-mixing globs
Now, let's put the previous levels together! We put a few happy, but diversely-named files in /challenge/files.

## flag:
pwn.college{wDMWrga99FMl9TgqRMooC75fUBS.QX1IDO0wiMxIzNzEzW}

## my solve:

hacker@globbing~mixing-globs:/challenge$ cd /ch*/fi*
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{wDMWrga99FMl9TgqRMooC75fUBS.QX1IDO0wiMxIzNzEzW}

## new learning:

1.Combines bracket notation [] with wildcard * for sophisticated patterns
2.[cep]* matches files starting with c, e, or p followed by anything
3.Demonstrates the power of mixing different glob types

## references:
pwn.college explanation and its refernce videos

## challenge 7-exclusinary globbing
Sometimes, you want to filter out files in a glob! Luckily, [] helps you do just this. If the first character in the brackets is a ! or (in newer versions of bash) a ^, the glob inverts, and that bracket instance matches characters that aren't listed

## flag
pwn.college{MHt09OUwmlejSo8yqIQ2MggVV0-.QX2IDO0wiMxIzNzEzW}

## mysolve:
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [^pwn]*
You got it! Here is your flag!
pwn.college{MHt09OUwmlejSo8yqIQ2MggVV0-.QX2IDO0wiMxIzNzEzW}

## new learning:

[^characters] or [!characters] creates negated character classes
[^pwn]* matches files that do NOT start with p, w, or n
Useful for excluding specific patterns from matches

## reference:
pwn.college explanation and its refernce videos

## challenge 8-tab completion

This challenge has copied the flag into /challenge/pwncollege, and you can freely cat that file. But you can't type the filename: we used some serious trickery to make sure that you must tab-complete it.

## flag:
pwn.college{g9hnjMQZAMUsX682rlVmxmQ38tE.0VN0EzNxwiMxIzNzEzW}

## mysolve:
command:cat /challenge/pwn 
[hit tab]
pwn.college{g9hnjMQZAMUsX682rlVmxmQ38tE.0VN0EzNxwiMxIzNzEzW}

## new learning:
1.Press Tab key to automatically complete partial filenames
2.Reduces typing errors and increases command accuracy

## references:
pwn.college explanation and its refernce videos


## challenge 9-multiple options for tab completion 

What happens varies based on the specific shell and its options. By default bash will auto-expand until the first point when there are multiple options (in this case, fl). When you hit tab a second time, it'll print out those options. Other shells and configurations, instead, will cycle through the options.

## flag:
pwn.college{EuRO0kGjs1Mq_XB0Ev5AwkP3AGt.0lN0EzNxwiMxIzNzEzW}

## my solve:
hacker@globbing~multiple-options-for-tab-completion:~$ /challenge/files/pwn
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-flag
pwn.college{EuRO0kGjs1Mq_XB0Ev5AwkP3AGt.0lN0EzNxwiMxIzNzEzW}

## new learning:
1. click on Tab twice to see all available options when completion stops

## references:
pwn.college explanation and its refernce videos

## challenge 10-tab completion on demands
Tab completion is for more than files! You can also tab-complete commands. This level has a command that starts with pwncollege, and it'll give you the flag. Type pwncollege and hit the tab key to auto-complete it!

## flag
pwn.college{g9hnjMQZAMUsX682rlVmxmQ38tE.0VN0EzNxwiMxIzNzEzW}

## my solve:
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege​
pwn.college{gnauQ16Tl8uRjfKA2scKLbXViWL.0FN0EzNxwiMxIzNzEzW}

## new learning:
1.Tab completion works for commands, not just filenames
2.Shell can complete executable names in PATH directories

## references:

pwn.college explanation and its refernce videos

