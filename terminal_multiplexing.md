## challenge 1-launching screen
For this challenge, we've hooked things up so that just launching screen will get you the flag

## flag:
pwn.college{QIbsiuMfDpMHIA1OHvRUReRDmCQ.0VN4IDOxwiMxIzNzEzW}

## mysolve:
```
Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{QIbsiuMfDpMHIA1OHvRUReRDmCQ.0VN4IDOxwiMxIzNzEzW}
```
## new learning:
1.screen is a program that creates virtual terminals inside your terminal.
2.syntax-screen

## challenge 2-detaching and attaching
For this challenge, you'll need to:

Launch screen
Detach from it.
Run /challenge/run (this will secretly send the flag to your detached session!)
Reattach to see your prize

## flag:
pwn.college{0gCf3DJFVCD9-uPPu5QvwtECAd0.0lN4IDOxwiMxIzNzEzW}

## my solve:
```
hacker@terminal-multiplexing~detaching-and-attaching:~$ /challenge/run
Found detached screen session: 139.pts-0.terminal-multiplexing~detaching-and-attaching
Sending flag to your screen session...-screen:~$ screen

Flag sent! Now reattach to your screen session with:

  screen -r

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen -r
[detached from 139.pts-0.terminal-multiplexing~detaching-and-attaching]

hacker@terminal-multiplexing~detaching-and-attaching:~$
hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{0gCf3DJFVCD9-uPPu5QvwtECAd0.0lN4IDOxwiMxIzNzEzW}
Yes! Flag is: pwn.college{0gCf3DJFVCD9-uPPu5QvwtECAd0.0lN4IDOxwiMxIzNzEzW}
```

## new learning:
1.You detach by pressing Ctrl-A, followed by d 
2.To reattach, you can use the -r argument to screen

## challenge 3-finiding sessions
In this challenge, we've created three screen sessions for you. One of them contains the flag. The other two are decoys!

You'll need to check each one until you find it

## flag:

pwn.college{USltzE6GLgi57g-pKvu4pk_hW4D.01N4IDOxwiMxIzNzEzW}

## mysolve:
```
screen -ls
screen -r session ------
flag
```

## learnings

1. we can list sessions using screen -ls
2. The identifiers of the sessions are the PID of each respective screen process, a dot, and the name of the screen session. To attach to a specific one, you use its name or its PID by giving it as an argument to screen -r.

## challenge 4-switching windows
Attach to the session with screen -r, then use one of the key combinations above to switch to Window 1. Go get that flag!

## flag:
pwn.college{8eegnBa295zlqlfaqK0QRZZSo_E.0FO4IDOxwiMxIzNzEzW}

## mysolve:
```
hacker@terminal-multiplexing~switching-windows:~$ screen -r
[detached from 135.challenge_session]

hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{8eegnBa295zlqlfaqK0QRZZSo_E.0FO4IDOxwiMxIzNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{8eegnBa295zlqlfaqK0QRZZSo_E.0FO4IDOxwiMxIzNzEzW}
```

## new learnings:
Ctrl-A c - Create a new window
Ctrl-A n - Next window
Ctrl-A p - Previous window
Ctrl-A 0 through Ctrl-A 9 - Jump directly to window 0-9
Ctrl-A " - bring up a selection menu of all of the windows

## challenge 5-detaching and attaching tmux
For this challenge:

Launch tmux
Detach from it.
Run /challenge/run (this will send the flag to your detached session!)
Reattach to see your prize

## flag:
 pwn.college{0l3u3Xpq0nQFs6xsTSPQI32cKic.0VO4IDOxwiMxIzNzEzW}

 ## mysolve:
 ```
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux a
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$  echo Congratulations, here is your flag: pwn.college{0l3u3Xpq0nQFs6xsTSPQI32cKic.0VO4IDOxwiMxIzNzEzW}
Congratulations, here is your flag: pwn.college{0l3u3Xpq0nQFs6xsTSPQI32cKic.0VO4IDOxwiMxIzNzEzW}
```

## new learning:

1.tmux (terminal multiplexer) is screen's younger, more modern cousin
2.Instead of Ctrl-A, tmux uses Ctrl-B as its command prefix.
3.The commands also differ:

tmux ls - List sessions
tmux attach or tmux a - Reattach to session

## challenge 6-swicthing windows tmux
We've created a tmux session with two windows:

Window 0 has the flag!
Window 1 has your warm welcome.
Go get that flag!

## flag:
pwn.college{MLDEV306kPjS2Kz4Qw3VUMbMpVl.0FM5IDOxwiMxIzNzEzW}

## new learning:
Ctrl-B c - Create a new window
Ctrl-B n - Next window
Ctrl-B p - Previous window
Ctrl-B 0 through Ctrl-B 9 - Jump to window 0-9
Ctrl-B w - See a nice window picker

