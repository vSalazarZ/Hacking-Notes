## Descripción 
Sometimes you need to handle process data outside of a file. Can you find a way to keep the output from this program and search for the flag? Connect to `jupiter.challenges.picoctf.org 4427.

Hint:
1. Remember the flag format is picoCTF{XXXX}
2. What's a pipe? No not that kind of pipe... This [kind](http://www.linfo.org/pipes.html)
## Solución 1

Me conecte con netcat, después mandé la salida a un archivo y luego saqué la bandera con un grep

```
vSalazarZ-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 4427 > salida
vSalazarZ-picoctf@webshell:~$ cat salida | grep pico

picoCTF{digital_plumb3r_5ea1fbd7}
```
## Solución 2

Me conecté y redirigí la salida al grep para encontrar la bandera

```
vSalazarZ-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 4427 | grep pico
picoCTF{digital_plumb3r_5ea1fbd7}

vSalazarZ-picoctf@webshell:~$ ls
README.txt  file  flag  salida
```


