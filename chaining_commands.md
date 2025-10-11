## challenge 1-chaining with semicolons

In this level, you must run /challenge/pwn and then /challenge/college, chaining them with a semicolon.

## flag:
pwn.college{gtQ7vVoCxAv_yJMhE9qzkP_EN5V.QX1UDO0wiMxIzNzEzW}

## mysolve:
```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn;/challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{gtQ7vVoCxAv_yJMhE9qzkP_EN5V.QX1UDO0wiMxIzNzEzW}
```

## new learnings:
1.using semicolons we can merge more than one statements in one single statement 

## challenge 2-building on success

In this challenge, you need to chain the programs /challenge/first-success and /challenge/second using the && operator. Try running each command separately first to see what happens (which is that you will not get the flag). But if you chain them with &&, the flag will appear

## flag:
 pwn.college{oJBtb7BbZrBQaaHPLp1aDXZSRD8.0lM0MDOxwiMxIzNzEzW}

## mysolve:
```
hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{oJBtb7BbZrBQaaHPLp1aDXZSRD8.0lM0MDOxwiMxIzNzEzW}
```
## new learnings:
1. we can merge two statements using the && operator
2. and it only runs when both the conditions are true
3. it fails to run if either of the conditions are false


## challenge 3-handling failures:
In this challenge, you need to chain /challenge/first-failure and /challenge/second using the || operator. Go for it!

## flag:
pwn.college{8nWsaJymWPvJc9iUcFjjrqqOGbc.01M0MDOxwiMxIzNzEzW}

## mysolve:
```
hacker@chaining~handling-failure:~$ /challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{8nWsaJymWPvJc9iUcFjjrqqOGbc.01M0MDOxwiMxIzNzEzW}
```
## new learning:
1.we can merge two statements using the || operator
2.it runs if either of the condition satisfies

## challenge 4-your first shell script

it's your turn! Same as last level, run /challenge/pwn and then /challenge/college, but this time in a shell script called x.sh, then run it with bash!

## flag:
pwn.college{YyUjww41baahBagVWEEUNHlNGbC.QXxcDO0wiMxIzNzEzW}

## mysolve:
```
hacker@chaining~your-first-shell-script:~$ echo /challenge/pwn > x.sh ; echo /challenge/college >> x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{YyUjww41baahBagVWEEUNHlNGbC.QXxcDO0wiMxIzNzEzW}
```

## new learning:
1.attaching many statement toghether using the above mentioned types can bcome very confusing at times so we create shell script
2.by convention, shell scripts are frequently named with a sh suffix

## challenge 5-redirecting script output


## flag:
pwn.college{wGAa7DITPygaLuT4hhe3yXRJfvI.QX4ETO0wiMxIzNzEzW}

## mysolve:

hacker@chaining~redirecting-script-output:~$ echo /challenge/pwn > script.sh ; echo /challenge/college >> script.sh
hacker@chaining~redirecting-script-output:~$ bash script.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{wGAa7DITPygaLuT4hhe3yXRJfvI.QX4ETO0wiMxIzNzEzW}

## new learning:
1.send the output of several programs to one command
2. > for stdout, 2> for stderr, < for stdin, >> and 2>> for append-mode redirection, >& for redirecting to other file descriptors, and | for piping to another command.


## challenge 6-executable shell scripts
Make a shellscript that will invoke /challenge/solve, make it executable, and run it without explicitly invoking bash!

## flag:
pwn.college{8VKnbgBg0ZIihvqR61tc7nAnZDz.QX0cjM1wiMxIzNzEzW}

## mysolve:
```
hacker@chaining~executable-shell-scripts:~$ echo '/challenge/solve' > script.sh
hacker@chaining~executable-shell-scripts:~$ chmod u=rwx ./script.sh
hacker@chaining~executable-shell-scripts:~$ ./script.sh
Congratulations on your shell script execution! Your flag:
pwn.college{8VKnbgBg0ZIihvqR61tc7nAnZDz.QX0cjM1wiMxIzNzEzW}
```

## new learning:
When you invoke bash script.sh, you are, of course launching the bash command with the script.sh argument. This tells bash to read its commands from script.sh instead of standard input, and thus your shell script is executed.
It turns out that you can avoid the need to manually invoke bash
If your shell script file is executable (recall File Permissions), you can simply invoke it via its relative or absolute path

## challenge 7-understanding shebangs
For this challenge, create a script at /home/hacker/solve.sh that has a proper shebang and outputs "hack the planet". Remember to make it executable, then run /challenge/run to verify your script works correctly!

## flags:
pwn.college{AzSe90HKPNcGXXLpiSuv363KYQt.0VOzMDOxwiMxIzNzEzW}

## mysolve:
```
command echo '#!/bin/bash 
"hack the planet"' > /home/hacker/solve.sh
comamnd chmod +x /home/hacker/solve.sh
```

## new learning:

1.When a program is invoked in Linux, the Linux kernel first inspects the file to determine how it should be run. This does NOT use the extension
(which is why you don't have to name your shell scripts with a .sh extension, or your Python scripts with a .py extension, or so on). Rather, Linux looks at the first few bytes of the file for this information.
2.There are a bunch of different types of programs, but if the program file starts with the characters #! (often termed a "shebang")
3.Linux treats the file as an interpreted program, and the contents of the rest of the line as the path to the interpreter
4.When ./script.sh was executed, Linux opened the file, read the first line, extracted /bin/bash as the interpreter, and executed /bin/bash ./script.sh to launch the script
5.Note, the shebang line must be the VERY FIRST line of the file - no blank lines or spaces before it!

FUN FACT: Common shebangs you might see:
#!/bin/bash for bash scripts
#!/usr/bin/python3 for Python scripts
#!/bin/sh for POSIX shell scripts --- this is a more primitive predecessor to bash with fewer features, but more compatibility to non-Linux systems!
Use -e after echo to make it read the escape characters otherwise it doesn't work

## challenge 8-scripting with arguments
For this challenge, you need to write a script at /home/hacker/solve.sh that:

1.Takes two arguments
2.Outputs them in REVERSE order (second argument first, then the first argument)

## flag:
pwn.college{QTYDrffnrrwU2UWUMA5fJQHONaJ.0VNzMDOxwiMxIzNzEzW}

## mysolve:
```
hacker@chaining~scripting-with-arguments:~$ cat > /home/hacker/solve.sh <<'EOF'
#!/bin/bash
printf "%s %s\n" "$2" "$1"

chmod +x /home/hacker/solve.sh
/challenge/run
```
## new learning:
The script can access these arguments using special variables:

$1 contains the first argument ("hello")
$2 contains the second argument ("world")
$3 would contain the third argument (if there had been one)

## challenges 9-scripting with conditionals
For this challenge, write a script at /home/hacker/solve.sh that:

Takes one argument
If the argument is "pwn", output "college"
For any other input, output nothing

## flag:
pwn.college{MwQTmJN64noRTjiEdBVHI9B5sns.0lNzMDOxwiMxIzNzEzW}

## mysolve:

hacker@chaining~scripting-with-conditionals:~$ cat > /home/hacker/solve.sh <<
#!/bin/bash
if [ "$1" = "pwn"]; then
  echo "college"

chmod +x /home/hacker/solve.sh

/challenge/run
Correct! Your script properly handles all the conditions.
Here's your flag:
pwn.college{MwQTmJN64noRTjiEdBVHI9B5sns.0lNzMDOxwiMxIzNzEzW}

## new learnings:
1.In bash, you can use if statements
2.First, you must have spaces after if (if you're used to a language like C, this is different), after [, and before ]
3.Second, if, then, and fi must all be on different lines (or separated by semicolons)
4.instead of endif or end or something like that, the terminator of the if statement is fi (if backwards)


## challenge 10-scripting with default case

For this challenge, write a script at /home/hacker/solve.sh that:

Takes one argument
If the argument is "pwn", output "college"
For any other input, output "nope"

## flag:
pwn.college{kOM3YedojbPkFaMrTCVfh-g09Ht.01NzMDOxwiMxIzNzEzW}

## mysolve:
```
#!/bin/bash
if [ "$1" = "pwn" ]; then
  echo "college"
else
  echo "nope"

chmod +x /home/hacker/solve.sh
/challenge/run
```

## new learning:
1.In bash, you can use if statements
2.First, you must have spaces after if (if you're used to a language like C, this is different), after [, and before ]
3.Second, if, then, and fi must all be on different lines (or separated by semicolons)
4.instead of endif or end or something like that, the terminator of the if statement is fi (if backwards)

## challenge 11-scripting with multiple conditions
For this challenge, write a script at /home/hacker/solve.sh that:

Takes one argument
If the argument is "hack", output "the planet"
If the argument is "pwn", output "college"
If the argument is "learn", output "linux"
For any other input, output "unknown"

## flag:
pwn.college{sSz8bvhizWzlJ-4Dp5QUDb8QAg3.0FOzMDOxwiMxIzNzEzW}

## mysolve:

#!/bin/bashased on the first argument
if [ "$1" = "hack" ]; then
  echo "the planet" ]; then
elif [ "$1" = "pwn" ]; then
  echo "college"earn" ]; then
elif [ "$1" = "learn" ]; then
  echo "linux"
elseho "unknown"
  echo "unknown"
chmod +x /home/hacker/solve.sh
chmod +x /home/hacker/solve.sh
/challenge/run
Correct! Your script properly handles all the conditions with elif.
Here's your flag:
pwn.college{sSz8bvhizWzlJ-4Dp5QUDb8QAg3.0FOzMDOxwiMxIzNzEzW}

## new learning:
none

## challenge 12-reading shell scripts



