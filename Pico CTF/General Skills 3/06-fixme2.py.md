## Descripción 
Fix the syntax error in the Python script to print the flag.[Download Python script](https://artifacts.picoctf.net/c/6/fixme2.py)

Hint:
1. Are equality and assignment the same symbol?
2. To view the file in the webshell, do: `$ nano fixme2.py`
3. To exit `nano`, press Ctrl and x and follow the on-screen prompts.
4. The `str_xor` function does not need to be reverse engineered for this challenge.
## Solución 1

Con consola linux y python
Primero descargamos el archivo con wget, después veemos su contenido con un cat. Después lo corremos en python y nos dice que hay un error.
En el hint 2 nos dice que usemos `$ nano fixme2.py` en pyhton para arreglar el error, lo arreglamos y tenemos la flag
Nos dice: SyntaxError: invalid syntax. Maybe you meant '== or ':=' instead of '='?
Usamos nano fixme2.py y ponemos un = extra y nos da la flag

```
vSalazarZ-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/6/fixme2.py
--2025-02-20 05:13:35--  https://artifacts.picoctf.net/c/6/fixme2.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.128, 3.160.22.43, 3.160.22.16, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.128|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1029 (1.0K) [application/octet-stream]
Saving to: 'fixme2.py'

fixme2.py                                                  100%[=======================================================================================================================================>]   1.00K  --.-KB/s    in 0s      

2025-02-20 05:13:35 (330 MB/s) - 'fixme2.py' saved [1029/1029]

vSalazarZ-picoctf@webshell:~$ ls
fixme2.py
vSalazarZ-picoctf@webshell:~$ cat fixme2.py

import random



def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])


flag_enc = chr(0x15) + chr(0x07) + chr(0x08) + chr(0x06) + chr(0x27) + chr(0x21) + chr(0x23) + chr(0x15) + chr(0x58) + chr(0x18) + chr(0x11) + chr(0x41) + chr(0x09) + chr(0x5f) + chr(0x1f) + chr(0x10) + chr(0x3b) + chr(0x1b) + chr(0x55) + chr(0x1a) + chr(0x34) + chr(0x5d) + chr(0x51) + chr(0x40) + chr(0x54) + chr(0x09) + chr(0x05) + chr(0x04) + chr(0x57) + chr(0x1b) + chr(0x11) + chr(0x31) + chr(0x0d) + chr(0x5f) + chr(0x05) + chr(0x40) + chr(0x04) + chr(0x0b) + chr(0x0d) + chr(0x0a) + chr(0x19)

  
flag = str_xor(flag_enc, 'enkidu')

# Check that flag is not empty
if flag = "":
  print('String XOR encountered a problem, quitting.')
else:
  print('That is correct! Here\'s your flag: ' + flag)


vSalazarZ-picoctf@webshell:~$ python fixme2.py
  File "/home/vSalazarZ-picoctf/fixme2.py", line 22
    if flag = "":
       ^^^^^^^^^
SyntaxError: invalid syntax. Maybe you meant '==' or ':=' instead of '='?
vSalazarZ-picoctf@webshell:~$ nano fixme2.py
vSalazarZ-picoctf@webshell:~$ python fixme2.py
That is correct! Here's your flag: picoCTF{3qu4l1ty_n0t_4551gnm3nt_f6a5aefc}
vSalazarZ-picoctf@webshell:~$ 

flag: picoCTF{3qu4l1ty_n0t_4551gnm3nt_f6a5aefc}
```
