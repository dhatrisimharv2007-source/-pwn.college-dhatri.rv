## challenge 1-printing variables:

You can also print out variables with echo, by prepending the variable name with a $. 

## flag:
pwn.college{AOYlcUbriSqjaP48b_AhwsekRdL.QX3UTN0wiMxIzNzEzW}

## my solve:

hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{AOYlcUbriSqjaP48b_AhwsekRdL.QX3UTN0wiMxIzNzEzW}

## challenge 2-setting variable:
as well as reading values stored in variables, you can write values to variables. This is done, as with many other languages, using =. 
## flag:

pwn.college{IfNabWzEZRRKvXxYNs7VdFTm2h_.QX5UTN0wiMxIzNzEzW}
## mysolve:
Connected!
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{IfNabWzEZRRKvXxYNs7VdFTm2h_.QX5UTN0wiMxIzNzEzW}


## challenge 3-multi word variable:

In this level, you will learn about quoting. Spaces have special significance in the shell, and there are places where you can't use them spuriously. 
## flag:
pwn.college{gX1brpj_d4qy4w7DepionipJgGQ.QXwYTN0wiMxIzNzEzW}

## my solve:
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{gX1brpj_d4qy4w7DepionipJgGQ.QXwYTN0wiMxIzNzEzW}

## challenge 4-exporting variable:

## flag:
pwn.college{gwUnhmxqEREnlWpW5SBJJIVFUut.QXyYTN0wiMxIzNzEzW}

## my solve:

You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great
job! Here is your flag:
pwn.college{gwUnhmxqEREnlWpW5SBJJIVFUut.QXyYTN0wiMxIzNzEzW}

## challenge 5-printed exported variables

## flag:
pwn.college{MpqnvPZxX8wwaUfs_nn23J_CQ7k.QX4UTN0wiMxIzNzEzW}

## my solve:
hacker@variables~printing-exported-variables:~$ env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
MANPATH=/run/dojo/share/man:
DOJO_AUTH_TOKEN=f833f7dc5b161e2b5febf878567d0d76eb54a2ddb720b21091f17780857a639a
HOME=/home/hacker
LANG=C.UTF-8
FLAG=pwn.college{MpqnvPZxX8wwaUfs_nn23J_CQ7k.QX4UTN0wiMxIzNzEzW}
TERMINFO=/run/dojo/share/terminfo
TERM=xterm-256color
SHLVL=2
LC_CTYPE=C.UTF-8
SSL_CERT_FILE=/run/dojo/etc/ssl/certs/ca-bundle.crt
PATH=/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
DEBIAN_FRONTEND=noninteractive
_=/run/dojo/bin/env

## challenge 6-
storing command outputn the course of working with the shell, you will often want to store the output of some command into a variable. Luckily, the shell makes this quite easy using something called Command Substitution

## flag:
 pwn.college{AYh3f9cfwrg2iqLjJB5ebJ4lUOl.QX1cDN1wiMxIzNzEzW}

## my solve:

hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out
and submit it!
hacker@variables~storing-command-output:~$ $PWN
bash: pwn.college{AYh3f9cfwrg2iqLjJB5ebJ4lUOl.QX1cDN1wiMxIzNzEzW}: command not found

## challenge 7-reading input

We'll start with reading input from the user (you). That's done using the aptly named read builtin, which reads input into a variable

## flag:
pwn.college{wOJhCjYm_xyH9CFsBN5tFpXW0E_.QX4cTN0wiMxIzNzEzW}

## my solve:
hacker@variables~reading-input:~$ read PWN
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{wOJhCjYm_xyH9CFsBN5tFpXW0E_.QX4cTN0wiMxIzNzEzW}

## challenge 8-reading files
 it represents what grouchy hackers call a "Useless Use of Cat". That is, running a whole other program just to read the file is a waste. It turns out that you can just use the powers of the shell!

## flag:

