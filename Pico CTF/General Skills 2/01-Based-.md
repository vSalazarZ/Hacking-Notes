## Descripción 
To get truly 1337, you must understand different data encodings, such as hexadecimal or binary. Can you get the flag from this program to prove you are on the way to becoming 1337? Connect with `nc jupiter.challenges.picoctf.org 15130`.

Hint:
1. I hear python can convert things.
2. It might help to have multiple windows open.
## Solución 1

Con cyberchef
Nos conectamos al servidor con ssh y nos aparecen números que debemos decodificar, así que cada vez que aparezcan los metemos al cyberchef y los transformamos
```
vSalazarZ-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 15130
Let us see how data is stored
nurse
Please give the 01101110 01110101 01110010 01110011 01100101 as a word.
...
you have 45 seconds.....

Input:
nurse
Please give me the  163 157 143 153 145 164 as a word.
Input:
socket
Please give me the 6e75727365 as a word.
Input:
nurse
You've beaten the challenge
Flag: picoCTF{learning_about_converting_values_02167de8}
```
