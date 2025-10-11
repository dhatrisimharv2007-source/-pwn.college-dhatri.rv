## challenge 1-changing file ownership
 we will practice changing the owner of the /flag file to the hacker user, and then read the flag. For this challenge only, I made it so that you can use chown to your heart's content as the hacker user (again, typically, this requires you to be root)

 ## flag:
 pwn.college{MM0Ybz03I9B4VUhL4z8CkwcT9Fj.QXxEjN0wiMxIzNzEzW}

 ## mysolve:
 ```
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{MM0Ybz03I9B4VUhL4z8CkwcT9Fj.QXxEjN0wiMxIzNzEzW}
```

## new learning
1. On pwn.college, this is the hacker user, regardless of what your username is.
root. This is the administrative account and, in most security situations, the ultimate prize.
2.If you take over the root user, you've almost certainly achieved your hacking objective
3.we can change the ownership of files! This is done via the chown
4. chown can only be invoked by the root user

## challenge 2-groups and files

## flag:
pwn.college{cLYUnCtIiZsv9mA-TOTFiKKac0g.QXxcjM1wiMxIzNzEzW}

## mysolve:
```
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{cLYUnCtIiZsv9mA-TOTFiKKac0g.QXxcjM1wiMxIzNzEzW}
```

## new learning:
1.group ownership can be changed with the chgrp (change group) command! Unless you have write access to the file and membership in the new group,
2.this typically requires root access, so let's check it out as root

## challenge 3-fun with group name
Follow the prompts from /challenge/run to set permissions on /challenge/pwn correctly eight times to unlock /flag.

## flag:
