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

