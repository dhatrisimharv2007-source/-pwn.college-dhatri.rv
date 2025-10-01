## challenge 1-the root
You can invoke a program by providing its path on the command line. In this case, you'll be giving the exact path, starting from /, so the path would be /pwn. This style of path, one that starts with the root directory, is referred to as an "absolute path

## flag:
pwn.college{MCs9X3H86VGtOJ5_a5tVLAYq2AT.QX4cTO0wiMxIzNzEzW}

## mysolve:

command /pwn
pwn.college{MCs9X3H86VGtOJ5_a5tVLAYq2AT.QX4cTO0wiMxIzNzEzW}

## new learning:
1. Absolute paths start from the root directory (/) and provide the complete path to a file

 ## refernces:
 none
 
   
## challenge 2-program and absolute path
Let's explore a slightly more complicated path! Except for in the previous level, challenges in pwn.college are in the challenge directory and the challenge directory is, in turn, right in the root directory (/). The path to the challenge directory is, thus, /challenge

## flag:

pwn.college{AbcxtvtqnEjk2OKnbETqqi36rqb.QX1QTN0wiMxIzNzEzW}

## mysolve:
command /challenge/run
pwn.college{AbcxtvtqnEjk2OKnbETqqi36rqb.QX1QTN0wiMxIzNzEzW}

## new learning:
Absolute paths always begin with / to indicate they start from the root

## references:
none

## challenge 3-postion thy self
The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it as an argument

## flag:
pwn.college{QIKYLLcOB-qBlluBgRRkQS8GHMG.QX2QTN0wiMxIzNzEzW}

## my solve:
command /challenge/run
command cd /usr/include
hacker@paths~position-thy-self:/usr/include$ /challenge/run
pwn.college{QIKYLLcOB-qBlluBgRRkQS8GHMG.QX2QTN0wiMxIzNzEzW}

## new learning:


challenge 4
pwn.college{EzK-nc0rYHjOLqsCX4ZoqBSknJq.QX3QTN0wiMxIzNzEzW}

challenge 5
pwn.college{UldGrFwzsex84z1kDYrWQkuub4a.QX4QTN0wiMxIzNzEzW}

challenge 6
pwn.college{wZYJEf-fkroey4v2sydlL9quOMc.QX5QTN0wiMxIzNzEzW}

challenge 7
pwn.college{MMfIeBJp-iLapRR51e3G_Fr_Cr6.QXwUTN0wiMxIzNzEzW}

challenge 8 
pwn.college{0jCWe3X_9N5yTI3_lPNfoc3vs4o.QXxUTN0wiMxIzNzEzW}

challenge 9
pwn.college{kU_JoaARjuwFwTU2IMDH3TS-4Ra.QXzMDO0wiMxIzNzEzW}
