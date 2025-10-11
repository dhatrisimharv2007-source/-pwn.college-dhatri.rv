## challenge 1-becoming root with su
THIS challenge (and only this challenge) does have a root password. That password is hack-the-planet, and you must provide it to su to become root! Go do that, and read the flag

## flag:


## mysolve
```
hacker@users~becoming-root-with-su:~$ su
Password: 
root@users~becoming-root-with-su:/home/hacker# ls
COLLEGE  PWN  d  instructions  intercepted_data.txt  myflag  not-the-flag  stdout  the-flag
root@users~becoming-root-with-su:/home/hacker# cat not-the-flag
```

## new learning:
su is a setuid binary
Because it has the SUID bit set, su runs as root
Running as root, it can start a root shell
su is discerning: before allowing the user to elevate privileges to root, it checks to make sure that the user knows the root password


## challenge 2-other users with su
In this level, you must switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me

## flag:
pwn.college{QrPXpTCah7f_vNqDW3oVxrl5UHK.QX2UDN1wiMxIzNzEzW}

## mysolve:
```
hacker@users~other-users-with-su:~$ su zardus
Password: 
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{QrPXpTCah7f_vNqDW3oVxrl5UHK.QX2UDN1wiMxIzNzEzW}
```

## new learning:
1.With no arguments, su will start a root shell (after authenticating with root's password). However, you can also give a username as an argument to switch to that user instead of root.

## challenge 3-cracking passwords
This level simulates this story, giving you a leak of /etc/shadow (in /challenge/shadow-leak). Crack it (this could take a few minutes), su to zardus, and run /challenge/run to get the flag

## flag:
pwn.college{QZ_Nm9sfXB-X83ScXp4WqIvpWY3.QX3UDN1wiMxIzNzEzW}

## mysolve:
```
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
0g 0:00:00:03 40% 1/3 0g/s 290.0p/s 290.0c/s 290.0C/s .zardus99999..Mrzardus
0g 0:00:00:07 79% 1/3 0g/s 288.5p/s 288.5c/s 288.5C/s Zardus33..z99999000
0g 0:00:00:09 93% 1/3 0g/s 287.0p/s 287.0c/s 287.0C/s zardus999992002..zardus1963
0g 0:00:00:10 99% 1/3 0g/s 287.7p/s 287.7c/s 287.7C/s zardus999991915..999991900
0g 0:00:00:11 0% 2/3 0g/s 286.9p/s 286.9c/s 286.9C/s purple..larry
0g 0:00:00:13 0% 2/3 0g/s 287.5p/s 287.5c/s 287.5C/s francine..me
0g 0:00:00:15 0% 2/3 0g/s 288.1p/s 288.1c/s 288.1C/s grumpy..keeper
0g 0:00:00:19 1% 2/3 0g/s 289.1p/s 289.1c/s 289.1C/s 10sne1..nermal
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04962g/s 288.9p/s 288.9c/s 288.9C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su zardus
Password: 
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{QZ_Nm9sfXB-X83ScXp4WqIvpWY3.QX3UDN1wiMxIzNzEzW}
```

## new learning:
1.enter a password for su, it compares it against the stored password for that user. These passwords used to be stored in /etc/passwd
2.these were moved to /etc/shadow
3.Separated by :s, the first field of each line is the username and the second is the password
4.A value of * or ! functionally means that password login for the account is disabled
5.blank field means that there is no password


## challenge 4-using sudo

## flag:
pwn.college{AKocCmbXciCFlW0Rn4mA0L7HTHQ.QX4UDN1wiMxIzNzEzW}

## mysolve:
```
sudo: /flag: command not found
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{AKocCmbXciCFlW0Rn4mA0L7HTHQ.QX4UDN1wiMxIzNzEzW}
```
