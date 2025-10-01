## challenge 1-redirecting output
edirecting stdout to files. You can accomplish this with the > character.This will redirect the output of echo hi (which will be hi) to the file asdf. You can then use a program such as cat to output this file

## flag:
pwn.college{ochUhxwVAKLuhKGenC2TI9fAdqP.QX0YTN0wiMxIzNzEzW}

## my solve:
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your
flag:
pwn.college{ochUhxwVAKLuhKGenC2TI9fAdqP.QX0YTN0wiMxIzNzEzW}

## new learning :
1.redirects stdout files by using the > symbol.

2.then by using the cat command we can excecute the file.

## reference:
pwn.college explanation and its explanatory videoes

## challenge 2- redirecting more output

## flag:
 pwn.college{gA7-ufOs8vooz7NLlSpc1EmMWVf.QX1YTN0wiMxIzNzEzW}

 ## mysolve:
 hacker@piping~redirecting-more-output:~$ /challenge/run > myflag

hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{gA7-ufOs8vooz7NLlSpc1EmMWVf.QX1YTN0wiMxIzNzEzW}

## new learning:
1. we can redirect output of any command , doesnt just have to be echo.
2. that is why we have done command > file_name
3. the file is redirected to the new file, which can be accessed by cat command.

## refernces:
pwn.college explanation and its explanatory videoes

## challenge 3-appending output
A common use-case of output redirection is to save off some command results for later analysis. Often times, you want to do this in aggregate: run a bunch of commands, save their output, and grep through it later. In this case, you might want all that output to keep appending to the same file, but > will create a new output file every time, deleting the old contents.

## flag:
pwn.college{clxA2T8YFGJXkjBbMqGhrkkb8ab.QX3ATO0wiMxIzNzEzW}

## my solve:
hacker@piping~appending-output:~$ /challenge/run > /home/hacker/the-flag

hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag

hacker@piping~appending-output:~$ cat /home/hacker/the-flag
 |
\|/ This is the first half:
 v
pwn.college{clxA2T8YFGJXkjBbMqGhrkkb8ab.QX3ATO0wiMxIzNzEzW}
                              ^
     that is the second half /|\
                              |

## new learning:

1. in this u can save a file to the same output by using >>.
2. if u use the truncated > it makes a new output everytime and overwrites the first one.
3. by using this we can save multiple files under the same output.

## reference:
pwn.college explanation and its explanatory videoes

## challenge 4-redirecting errors:

## flag:
pwn.college{sQRdzFRvp1kn_kaJghSBbl0jNzJ.QX3YTN0wiMxIzNzEzW}

## my solve:

hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{sQRdzFRvp1kn_kaJghSBbl0jNzJ.QX3YTN0wiMxIzNzEzW}

## new learning:

1.FD 0: Standard Input
FD 1: Standard Output
FD 2: Standard Error
2. > means 1> that is standard output

## references:

pwn.college explanation and its explanatory videoes

## challenge 5-redirecting input

Just like you can redirect output from programs, you can redirect input to programs! This is done using <, as so

## flag:

## my solve:

## new learning:

## references:
pwn.college explanation and its explanatory videoes

## challenge 6-grepping stored results
You know how to run commands, how to redirect their output (e.g., >), and how to search through the resulting file (e.g., grep)

## flag:
pwn.college{YClBw71EdrJVOuh3pygwks5hj18.QX4EDO0wiMxIzNzEzW}

## my solve:

hacker@piping~grepping-stored-results:~$ /challenge/run 1> /tmp/data.txt
hacker@piping~grepping-stored-results:~$ grep pwn. /tmp/data.txt
pwned
pwning
pwns
pwn.college{YClBw71EdrJVOuh3pygwks5hj18.QX4EDO0wiMxIzNzEzW}

## new learning:
1.used mixing of redirection and grepping of files together.
2.revision of grepping of files. grep search_word /path.

## references:
pwn.college explanation and its explanatory videoes

## challenge 7-grepping live output

It turns out that you can "cut out the middleman" and avoid the need to store results to a file, like you did in the last level. You can do this by using the | (pipe) operator. Standard output from the command to the left of the pipe will be connected to (piped into) the standard input of the command to the right of the pipe

## flag:
pwn.college{oiSdQDqFQ7q7d4657dJHSzYReyK.QX5EDO0wiMxIzNzEzW}

## my solve:

hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.
[PASS] Success! You have satisfied all execution requirements.
pwn.college{oiSdQDqFQ7q7d4657dJHSzYReyK.QX5EDO0wiMxIzNzEzW}
pwns
pwning
pwned
## new learning:

1.it removes the middle men out and avoids the requirement to store results in the file.
2. syntax /path | grep search element 

## reference:
pwn.college explanation and its explanatory videoes

## challenge 8-grepping errors
The shell has a >& operator, which redirects a file descriptor to another file descriptor. This means that we can have a two-step process to grep through errors: first, we redirect standard error to standard output (2>& 1) and then pipe the now-combined stderr and stdout as normal (|)

## flag:
pwn.college{Etmd6WSRLMPTQzTTn7HgRObnMZU.QX1ATO0wiMxIzNzEzW}

## my solve:

hacker@piping~grepping-errors:~$ /challenge/run 2>& 1 |grep pwn.
pwn.college{Etmd6WSRLMPTQzTTn7HgRObnMZU.QX1ATO0wiMxIzNzEzW}
pwning
pwned
pwns

## new learning:
1. we can grep errors directly witout using a middleman
2. syntax [2>& 1 |grep search_word]

## references:
pwn.college explanation and its explanatory videoes

## challenge 9- filtering with grep-v
The grep command has a very useful option: -v (invert match). While normal grep shows lines that MATCH a pattern, grep -v shows lines that do NOT match a pattern

## flag:
pwn.college{4qw8S0vX63AJ5ekfV5iPwr8ApXZ.0FOxEzNxwiMxIzNzEzW}

## my solve:

hacker@piping~filtering-with-grep-v:~$ /challenge/run | grep -v DECOY
pwn.college{4qw8S0vX63AJ5ekfV5iPwr8ApXZ.0FOxEzNxwiMxIzNzEzW}

## new learning:
1. how to grep the files by excluding the given search word
2. syntax /path | grep -v search_word

## references:
pwn.college explanation and its explanatory videos

## challenge 10-duplicating piped data with tee

## flag:
pwn.college{onJ2RpEpQFgVlgkHWHvZo1sbYpF.QXxITO0wiMxIzNzEzW}

## my solve:

hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee intercepted_data.txt | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat intercepted_data.txt
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "onJ2RpEp"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret onJ2RpEp | tee intercepted_data.txt | /challenge/college
Processing...
WARNING: you are overwriting file intercepted_data.txt with tee's output...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{onJ2RpEpQFgVlgkHWHvZo1sbYpF.QXxITO0wiMxIzNzEzW}

## new learnings:

1.duplicates data flowing through your pipes to any number of files provided on the command line.
2.one to stdout, one to the pwn file, and one to the college file. 

## reference:
pwn.college explanation and its explanatory videos

## challenge 11-process substitution for input


## flag:
pwn.college{YsDZxZSbRCK7G1c01TtNU32Au94.0lNwMDOxwiMxIzNzEzW}

## mysolve:

hacker@piping~process-substitution-for-input:~$ diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
73a74
> pwn.college{YsDZxZSbRCK7G1c01TtNU32Au94.0lNwMDOxwiMxIzNzEzW}

## new learning:
1. how to check difference between two different files without the use of command diff
2. For reading from a command (input process substitution), use <(command)
When you write <(command), bash will run the command and hook up its output to a temporary file that it will create

## references:

pwn.college explanation and its explanatory videos

## challenge 12- writing to multiple programs:
Now you've learned that process substitution can make command output appear as files for reading with <(command). But you can also use process substitution for writing to commands

## flag:
pwn.college{o0fAx7p08XEFyaxstbz2laANAXn.QXwgDN1wiMxIzNzEzW}:

## mysolve:

hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) >(/challenge/planet)
Congratulations, you have duplicated data into the input of two programs! Here
is your flag:
pwn.college{o0fAx7p08XEFyaxstbz2laANAXn.QXwgDN1wiMxIzNzEzW}

## new learning:
1.Now you've learned that process substitution can make command output appear as files for reading with <(command)
tee to duplicate data to a file and a command 

2.bash can make commands look like files using process substitution! For writing to a command (output process substitution), use >(command). If you write an argument of >(rev), bash will run the rev command (this command reads data from standard input, reverses its order, and writes it to standard output!), but hook up its input to a temporary named pipe file

## refernce:

pwn.college explanation and its explanatory videos

## challenge 13-split-piping stderr and stdout

## flag:
pwn.college{QzOMQX7ydRtylkumvwhZSGMtTK8.QXxQDM2wiMxIzNzEzW}

## mysolve:
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack 2> >(/challenge/the) | /challenge/planet
Congratulations, you have learned a redirection technique that even experts
struggle with! Here is your flag:
pwn.college{QzOMQX7ydRtylkumvwhZSGMtTK8.QXxQDM2wiMxIzNzEzW}

##reference:
pwn.college explanation and its explanatory videos

##challenge 14-named pipes

You've learned about pipes using |, and you've seen that process substitution creates temporary named pipes (like /dev/fd/63). You can also create your own persistent named pipes that stick around on the filesystem! These are called FIFOs, which stands for First (byte) In, First (byte) Out.

## flag:

## my solve:

## new learning:

## references:

pwn.college explanation and its explanatory videos


