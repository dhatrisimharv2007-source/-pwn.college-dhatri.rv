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
pwn.college{QuXDZ4wfyB7tzoSC68jKFDlld2e.QXycjM1wiMxIzNzEzW}

## mysolve:
```
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp11026) groups=1000(grp11026)
hacker@permissions~fun-with-groups-names:~$ chgrp grp11026 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{QuXDZ4wfyB7tzoSC68jKFDlld2e.QXycjM1wiMxIzNzEzW}
```

## new learning:
none

## challenge 4-changing permissions

In this challenge, you must change the permissions of the /flag file to read it! Typically, you need to have write access to the file in order to change its permissions, but I have made the chmod command all-powerful for this level, and you can chmod anything you want even though you are the hacker user. This is an ultimate power. The /flag file is owned by root, and you can't change that, but you can make it readable.

## flag:
pwn.college{wugeVyab9uwLjod2NvYD5olHz0c.QXzcjM1wiMxIzNzEzW}

## mysolve:
```
hacker@permissions~changing-permissions:~$ chmod o+r /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{wugeVyab9uwLjod2NvYD5olHz0c.QXzcjM1wiMxIzNzEzW}
```

## new learning:
r: the user that owns the file (user hacker) can read it
w: the user that owns the file (user hacker) can write to it
-: the user that owns the file (user hacker) cannot execute it
r: users in the group that owns the file (group hacker) can read it
-: users in the group that owns the file (group hacker) cannot write to it
-: users in the group that owns the file (group hacker) cannot execute it
r: all other users can read it
-: all other users cannot write to it
-: all other users cannot execute it
1.chmod allows you to tweak permissions with the mode format of WHO+/-WHAT, where WHO is user/group/other and WHAT is read/write/execute. 
u+r, as above, adds read access to the user's permissions
g+wx adds write and execute access to the group's permissions
o-w removes write access for other users
a-rwx removes all permissions for the user, group, and world

## challenge 5-excecutable files
In this challenge, the /challenge/run program will give you the flag, but you must first make it executable! Remember your chmod, and get /challenge/run to tell you the flag!

## flag:
pwn.college{ArajCscXEIH8rTjUNkKzw0Yf74f.QXyEjN0wiMxIzNzEzW}

## mysolve:
```
hacker@permissions~executable-files:~$ chmod o+x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
pwn.college{ArajCscXEIH8rTjUNkKzw0Yf74f.QXyEjN0wiMxIzNzEzW}
```

## new learning:

1.the file is owned by the root user and root group, this requires that the execute bit is set on the other permissions

## challenge 6-permission tweaking practice 

This challenge will ask you to change the permissions of the /challenge/pwn file in specific ways a few times in a row. If you get the permissions wrong, the game will reset and you can try again. If you get the permissions right eight times in a row, the challenge will let you chmod /flag to make it readable for yourself :-) Launch /challenge/run to get started!

## flag:
pwn.college{wKHbPWbdm7S21fMbm3qd_kje1xW.QXwEjN0wiMxIzNzEzW}

## mysolve:
/challenge/run
chmod 666 /challenge/pwn
chmod 664 /challenge/pwn
chmod 675 /challenge/pwn
chmod 677 /challenge/pwn
chmod 001 /challenge/pwn
chmod 013 /challenge/pwn
chmod 003 /challenge/pwn
chmod 033 /challenge/pwn
chmod u+r /flag
cat /flag

## newlearnings:
none

## challenge 7-permission setting practice



## challenge 8-the SUIDbit
we are going to let you add the SUID bit to the /challenge/getroot program in order to spawn a root shell for you to cat the flag yourself!

## flag:
pwn.college{gLF7Pbotyc8ZuASYJYtJpStLoI4.QXzEjN0wiMxIzNzEzW}

## new learnings:
The s part in place of the executable bit means that the program is executable with SUID. It means that, regardless of what user runs the program (as long as they have executable permissions), the program will execute as the owner user (in this case, the root user).
