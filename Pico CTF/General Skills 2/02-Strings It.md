## Descripción 
Can you find the flag in [file](https://jupiter.challenges.picoctf.org/static/fae9ac5267cd6e44124e559b901df177/strings) without running it?

Hint:
1. [strings](https://linux.die.net/man/1/strings)
## Solución 1

Con consola
Primero descargamos el archivo con wget después con un grep buscamos la flag pico
```
vSalazarZ-picoctf@webshell:~$ wget https://jupiter.challenges.picoctf.org/static/fae9ac5267cd6e44124e559b901df177/strings
--2025-02-18 02:21:10--  https://jupiter.challenges.picoctf.org/static/fae9ac5267cd6e44124e559b901df177/strings
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 776032 (758K) [application/octet-stream]
Saving to: 'strings'

strings                                                    100%[=======================================================================================================================================>] 757.84K  1.85MB/s    in 0.4s    

2025-02-18 02:21:11 (1.85 MB/s) - 'strings' saved [776032/776032]

vSalazarZ-picoctf@webshell:~$
vSalazarZ-picoctf@webshell:~$ strings -n 10 10 strings | grep pico
strings: '10': No such file
picoCTF{5tRIng5_1T_7f766a23}
```