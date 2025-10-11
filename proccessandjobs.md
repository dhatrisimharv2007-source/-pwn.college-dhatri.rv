## challenge 1-listing processes
 I have once again renamed /challenge/run to a random filename, and this time made it so that you cannot ls the /challenge directory! But I also launched it, so you can find it in the running process list, figure out the filename, and relaunch it directly for the flag!

 ## flag:
 pwn.college{k6_lEumlpXE8N4ERnvUU5sRVgaO.QX4MDO0wiMxIzNzEzW}

 ## mysolve:
 ```
hacker@processes~listing-processes:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.0   1056   640 ?        Ss   09:53   0:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-works
root           7  0.0  0.0 231708  2560 ?        S    09:53   0:00 /run/dojo/bin/sleep 6h
root         132  0.0  0.0   4132  2560 ?        S    09:53   0:00 /challenge/4308-run-28250
root         135  0.0  0.0   2744  1600 ?        S    09:53   0:00 sleep 6h
hacker       137  0.0  0.0 231576  3520 pts/0    Ss   09:53   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-inte
hacker       143  0.0  0.0 231940  4160 pts/0    S    09:53   0:00 /run/dojo/bin/bash --login
hacker       154  0.0  0.0 233600  3840 pts/0    R+   09:58   0:00 ps aux
hacker@processes~listing-processes:~$ /challenge/4308-run-28250
Yahaha, you found me! Here is your flag:
pwn.college{k6_lEumlpXE8N4ERnvUU5sRVgaO.QX4MDO0wiMxIzNzEzW}
Now I will sleep for a while (so that you could find me with 'ps')
```

## new learning:
1. ps either stands for "process snapshot" or "process status", and it lists processes.
2. By default, ps just lists the processes running in your termina
3. "Standard" Syntax: in this syntax, you can use -e to list "every" process and -f for a "full format" output, including arguments. These can be combined into a single argument -ef
4. "BSD" Syntax: in this syntax, you can use a to list processes for all users, x to list processes that aren't running in a terminal, and u for a "user-readable" output. These can be combined into a single argument aux
5. ps -ef and ps aux: both display the user (USER column), the PID, the TTY, the start time of the process (STIME/START), the total utilized CPU time (TIME), and the command (CMD/COMMAND).
6. ps -ef additionally outputs the Parent Process ID (PPID), which is the PID of the process that launched the one in question
7. ps aux outputs the percentage of total system CPU and Memory that the process is utilizing.
8. NOTE: Both ps -ef and ps aux truncate the command listing to the width of your terminal (which is why the examples above line up so nicely on the right side of the screen. If you can't read the whole path to the process, you might need to enlarge your terminal (or redirect the output somewhere to avoid this truncating behavior)! Alternatively, you can pass the w option twice (e.g., ps -efww or ps auxww) to disable the truncation.

## challenge 2-killing proccess
Now, it's time to terminate your first process! In this challenge, /challenge/run will refuse to run while /challenge/dont_run is running! You must find the dont_run process and kill it. If you fail, pwn.college will disavow all knowledge of your mission

## flag:
pwn.college{Ifsnx4ZyuXyw5dhMm0CK0kLv8aj.QXyQDO0wiMxIzNzEzW}

## mysolve:
```
hacker@processes~killing-processes:~$ ps aux | grep /challenge/dont_run
hacker       136  0.0  0.0 231576  3520 ?        Ss   10:06   0:00 /challenge/dont_run
hacker       158  0.0  0.0 230696  2560 pts/0    S+   10:08   0:00 grep --color=auto /challenge/dont_run
hacker       175  0.0  0.0 230696  2560 pts/1    S+   10:10   0:00 grep --color=auto /challenge/dont_run
hacker@processes~killing-processes:~$ /challenge/run kill 136
Great job! Here is your payment:
pwn.college{Ifsnx4ZyuXyw5dhMm0CK0kLv8aj.QXyQDO0wiMxIzNzEzW}
```

## new learning:

1.kill will terminate a process in a way that gives it a chance to get its affairs in order before ceasing to exist.


## challenge 3-interuptting processes

/challenge/run will refuse to give you the flag until you interrupt

## flag:
pwn.college{QiwgulNqcdFCDMWxQvwzWbmJaAr.QXzQDO0wiMxIzNzEzW}

## mysolve:
```
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{QiwgulNqcdFCDMWxQvwzWbmJaAr.QXzQDO0wiMxIzNzEzW}
```

## new learning:

1.Ctrl-C (e.g., holding down the Ctrl key and pressing C) sends an "interrupt" to whatever application is waiting on input from the terminal and, typically, this causes the application to cleanly exit

## challenge 4-killing misbehaving proccess


## challenge 5-suspending processes
This level's run wants to see another copy of itself running and using the same terminal. How? Use the terminal to launch it, then suspend it, then launch another copy while the first is suspended!

## flag:
pwn.college{AdKY4Mf39uUf7XYepav0ojUthMH.QX1QDO0wiMxIzNzEzW}

## mysolve:
```
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         145     129  0 10:25 pts/0    00:00:00 bash /challenge/run
root         147     145  0 10:25 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can
background me with Ctrl-Z or, if you're not ready to do that for whatever
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         145     129  0 10:25 pts/0    00:00:00 bash /challenge/run
root         152     129  0 10:25 pts/0    00:00:00 bash /challenge/run
root         154     152  0 10:25 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{AdKY4Mf39uUf7XYepav0ojUthMH.QX1QDO0wiMxIzNzEzW}
```

## new learning:
1. You can suspend processes to the background with Ctrl-Z

## challenge 6-resuming processes
 This challenge's run needs you to suspend it, then resume it.

 ## flag:
 pwn.college{UcAxENiixXn40Qyq-UWEG__X56L.QX2QDO0wiMxIzNzEzW}

 ## mysolve:
 ```
bash: /challene/run: No such file or directory
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{UcAxENiixXn40Qyq-UWEG__X56L.QX2QDO0wiMxIzNzEzW}
```

## new learning:
1.To resume processes, your shell provides the fg command

## challenge 7-backgrounding processes
This level's run wants to see another copy of itself running, not suspended, and using the same terminal.

## flag:
pwn.college{sdOCIZtsu9XDBkurspcPCjSsStX.QX3QDO0wiMxIzNzEzW}

## mysolve:
```
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         139 S+   bash /challenge/run
root         141 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the
background, and then launch a new version of me! You can background me with
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~backgrounding-processes:~$


Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out.

hacker@processes~backgrounding-processes:~$
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         139 S    bash /challenge/run
root         149 S    sleep 6h
root         150 S+   bash /challenge/run
root         152 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{sdOCIZtsu9XDBkurspcPCjSsStX.QX3QDO0wiMxIzNzEzW}
```

## new leaning:
1.you can also resume processes in the background with the bg command

## challenge 8-foregrounding processes
foregrounding proccess

## flag:
pwn.college{sgh0Bx5b5T2A8RxvgLsrg1wDdAf.QX4QDO0wiMxIzNzEzW}

## mysolve:
```
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         139 S    bash /challenge/run
root         149 S    sleep 6h
root         150 S+   bash /challenge/run
root         152 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{sdOCIZtsu9XDBkurspcPCjSsStX.QX3QDO0wiMxIzNzEzW}
hacker@processes~backgrounding-processes:~$
Connected!
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~foregrounding-processes:~$


Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.

hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{sgh0Bx5b5T2A8RxvgLsrg1wDdAf.QX4QDO0wiMxIzNzEzW}
```

## new learning:
1. you can foreground a backgrounded process with fg just like you foreground a suspended process

## challenge 9-starting background processes
sleep is actively running in the background, not suspended. Now it's your turn to practice! Launch /challenge/run backgrounded for the flag

## flag:
pwn.college{QoY0qjI6bPuaxvOwNBSNsgb6cA0.QX5QDO0wiMxIzNzEzW}

## mysolve:
```
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 138
hacker@processes~starting-backgrounded-processes:~$


Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{QoY0qjI6bPuaxvOwNBSNsgb6cA0.QX5QDO0wiMxIzNzEzW}
```

## new learning:
1.you don't have to suspend processes to background them: you can start them backgrounded right off the bat! It's easy; all you have to do is append a & to the command

## challenge 10-process exit codes
you must retrieve the exit code returned by /challenge/get-code and then run /challenge/submit-code with that error code as an argument

## flag:
pwn.college{YVy7o_oomgz0Woxj_4QsEqmkDuT.QX5YDO1wiMxIzNzEzW}

## mysolve:
```
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
239
hacker@processes~process-exit-codes:~$ /challenge/submit-code 239
CORRECT! Here is your flag:
pwn.college{YVy7o_oomgz0Woxj_4QsEqmkDuT.QX5YDO1wiMxIzNzEzW}
```

## new learning:
1.Every shell command, including every program and every builtin, exits with an exit code when it finishes running and terminates
2.You can access the exit code of the most recently-terminated command using the special ? variable (don't forget to prepend it with $ to read its value)


  

