## Descripción 
Using netcat (nc) is going to be pretty important. Can you connect to `jupiter.challenges.picoctf.org` at port `25103` to get the flag?

Hint:
1. nc [tutorial](https://linux.die.net/man/1/nc)
## Solución 

Conectarnos al servidor remoto usando netcat

```
vSalazarZ-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 25103
You're on your way to becoming the net cat master

picoCTF{nEtCat_Mast3ry_d0c64587}

```
## Referencias
- https://linux.die.net/man/1/nc