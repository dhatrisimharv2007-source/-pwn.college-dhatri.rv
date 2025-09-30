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

1.




