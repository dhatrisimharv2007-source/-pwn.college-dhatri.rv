## challenge 1-translating charecters

In this level, /challenge/run will print the flag but will swap the casing of all characters (e.g., A will become a and vice-versa). Can you undo it with tr and get the flag?

## flag:
pwn.college{UF4ifsLSmyuAhIgfhSbwlrGLb_E.01MxEzNxwiMxIzNzEzW}

## my solve:
```
hacker@data~deleting-characters:~$ /challenge/run | tr A-Z,a-z a-z,A-Z
yOUR CASE-SWAPPED FLAG:
pwn.college{UF4ifsLSmyuAhIgfhSbwlrGLb_E.01MxEzNxwiMxIzNzEzW}
```
## new learning:

1. using the tr command we can replace any letter or charecter by another letter or charecter
2.syntax: | tr xyz XYZ

## challenge 2-deleteing charecters

 I'll intersperse some decoy characters (specifically: ^ and %) among the flag characters. Use tr -d to remove them!

## flag:

pwn.college{0x3Cz27He4m7f3lSHkiXJP9pg6U.0FNxEzNxwiMxIzNzEzW}

## mysolve:
```
hacker@data~deleting-characters:~$ /challenge/run | tr -d ^,%
Your character-stuffed flag:
pwn.college{0x3Cz27He4m7f3lSHkiXJP9pg6U.0FNxEzNxwiMxIzNzEzW}
```
## new learning:

1.we can also use tr to delete with another command -d
2. syntax | tr -d x y z

## challenge 3-deleting new lines

In this challenge, we'll inject a bunch of newlines into the flag. Delete them with tr's -d flag and the escaped newline specification!

## flag:

 pwn.college{0ZgqLLTQitpgh450MbPLBDmFgTD.0VNxEzNxwiMxIzNzEzW}

 ## mysolve
 ```
hacker@data~deleting-newlines:~$ /challenge/run | tr -d "\n"
Your line-split flag: pwn.college{0ZgqLLTQitpgh450MbPLBDmFgTD.0VNxEzNxwiMxIzNzEzW}
```

## new learning:

1.\n goes to a new line
2. using -d and \n deletes the line

## challenge 4-extracting the first files with head

This challenge's /challenge/pwn outputs a bunch of data, and you'll need to pipe it through head to grab just the first 7 lines and then pipe them onwards to /challenge/college, which will give you the flag if you do this right!

## flag:

pwn.college{I4_okl-2Tk8n8uvuv-LtgAVi8_v.0lNxEzNxwiMxIzNzEzW}

## mysolve:
```
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn |head
 -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{I4_okl-2Tk8n8uvuv-LtgAVi8_v.0lNxEzNxwiMxIzNzEzW}
```
## new learnings:
1. by using the head command we can view the first few lines of the file
2. we can also control the numver of lines that we want to view by using -n some num

## challenge 5-extracting specific sections of the text

In this challenge, the /challenge/run program will give you a bunch of lines with random numbers and single characters (characters of the flag) as columns. Use cut to extract the flag characters, then pipe them to tr -d "\n" (like the previous level!) to join them together into a single line. Your solution will look something like /challenge/run | cut ??? | tr ???, with the ??? filled out.

## flag:
pwn.college{AZZg7U8YXTIdo6N_R6XXk__EPAw.01NxEzNxwiMxIzNzEzW}

## mysolve:
```
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f 2 | tr -d "\n"
pwn.college{AZZg7U8YXTIdo6N_R6XXk__EPAw.01NxEzNxwiMxIzNzEzW}
```

## new leraning:

1.by using " " -f2.txt_name we can view certain sections of the text file
2. it can be used with multiple other commands as well using piping

## challenge 6-sorting data

In this challenge, there's a file at /challenge/flags.txt containing 100 fake flags, with the real flag mixed among them. When sorted alphabetically, the real flag will be at the end (we made sure of this when generating fake flags)

## flag:

pwn.college{sQL-sVwsr8cly1m5o2rwlP112Au.0FM0MDOxwiMxIzNzEzW}

## my solve:
```
hacker@data~sorting-data:~$ sort /challenge/flags.txt
pwn.college{sQL-sVwsr8cly1m5o2rwlP112Au.0FM0MDOxwiMxIzNzEzW}
```

## newlearning:

1.using the sort command we can sort the contantents of the file in alphabetical order default
2.we can also sort in order -r: reverse order (Z to A)
-n: numeric sort (for numbers)
-u: unique lines only (remove duplicates)
-R: random order!




