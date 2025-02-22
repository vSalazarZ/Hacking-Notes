## Descripción 
What is 0x3D (base 16) in decimal (base 10)?

Hint:
1. Submit your answer in our flag format. For example, if your answer was '22', you would submit 'picoCTF{22}' as the flag.
## Solución 1

Con cyberchef

```
Input: 0x3D

Recipe: From Hex
        To Decimal

Output: 61

picoCTF{61}
```
## Solución 2

Usando python

```
vSalazarZ-picoctf@webshell:~$ python
Python 3.10.12 (main, Sep 11 2024, 15:47:36) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> print(int("0x3D", 16))
61

picoCTF{61}
```


