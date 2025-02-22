## Descripción 
Our flag printing service has started glitching!
Additional details will be available after launching your challenge instance.

Hint:
1. ASCII is one of the most common encodings used in programming
2. We know that the glitch output is valid Python, somehow!
3. Press Ctrl and c on your keyboard to close your connection and return to the command prompt.
## Solución 1

Usando python
```
vSalazarZ-picoctf@webshell:~$ nc saturn.picoctf.net 63204
'picoCTF{gl17ch_m3_n07_' + chr(0x61) + chr(0x34) + chr(0x33) + chr(0x39) + chr(0x32) + chr(0x64) + chr(0x32) + chr(0x65) + '}'

vSalazarZ-picoctf@webshell:~$ python
Python 3.10.12 (main, Sep 11 2024, 15:47:36) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 'picoCTF{gl17ch_m3_n07_' + chr(0x61) + chr(0x34) + chr(0x33) + chr(0x39) + chr(0x32) + chr(0x64) + chr(0x32) + chr(0x65) + '}'

'picoCTF{gl17ch_m3_n07_a4392d2e}'
>>> 
```
## Solución 2

Usando cyberchef

Primero usamos el nc para sacar el contenido

```
vSalazarZ-picoctf@webshell:~$ nc saturn.picoctf.net 63204
'picoCTF{gl17ch_m3_n07_' + chr(0x61) + chr(0x34) + chr(0x33) + chr(0x39) + chr(0x32) + chr(0x64) + chr(0x32) + chr(0x65) + '}'
```

Después metemos la cadena + chr(0x61) + chr(0x34) + chr(0x33) + chr(0x39) + chr(0x32) + chr(0x64) + chr(0x32) + chr(0x65) + '}'
de caracteres a cyberchef, pero solo los números

```
Input: 61 34 33 39 32 64 32 65

Recipe: From Hex

Output: a4392d2e
```

Y por último nomas juntamos el pico+cadena

```
'picoCTF{gl17ch_m3_n07_' + chr(0x61) + chr(0x34) + chr(0x33) + chr(0x39) + chr(0x32) + chr(0x64) + chr(0x32) + chr(0x65) + '}'

picoCTF{gl17ch_m3_n07_' + a4392d2e }'

'picoCTF{gl17ch_m3_n07_a4392d2e}'
```


