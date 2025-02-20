## Descripción 
Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/13/level2.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/13/level2.flag.txt.enc) in the same directory too.

Hint:
1. Does that encoding look familiar?
2. The `str_xor` function does not need to be reverse engineered for this challenge.
## Solución 1

Con consola linux y python
Con consola linux y python
Primero descargamos el archivo con wget.
Nos pide una contraseña al intentar correr el archivo .py en pyhton
Usamos cat para ver el contenido de python de level2.py
y es una suma de chr en hexa así que usamos cyberchef
Y ahora si ponemos la contraseña usando python y nos da la flag

```
vSalazarZ-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/13/level2.py
--2025-02-20 05:27:03--  https://artifacts.picoctf.net/c/13/level2.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.43, 3.160.22.92, 3.160.22.16, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.43|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 914 [application/octet-stream]
Saving to: 'level2.py'

level2.py                                                  100%[=======================================================================================================================================>]     914  --.-KB/s    in 0s      

2025-02-20 05:27:03 (20.9 MB/s) - 'level2.py' saved [914/914]

vSalazarZ-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/13/level2.flag.txt.enc
--2025-02-20 05:27:09--  https://artifacts.picoctf.net/c/13/level2.flag.txt.enc
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.43, 3.160.22.128, 3.160.22.92, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.43|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31 [application/octet-stream]
Saving to: 'level2.flag.txt.enc'

level2.flag.txt.enc                                        100%[=======================================================================================================================================>]      31  --.-KB/s    in 0s      

2025-02-20 05:27:09 (1.59 MB/s) - 'level2.flag.txt.enc' saved [31/31]

vSalazarZ-picoctf@webshell:~$ ls
level2.flag.txt.enc  level2.py
vSalazarZ-picoctf@webshell:~$ cat level2.py
### THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
###############################################################################

flag_enc = open('level2.flag.txt.enc', 'rb').read()



def level_2_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == chr(0x64) + chr(0x65) + chr(0x37) + chr(0x36) ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")



level_2_pw_check()
vSalazarZ-picoctf@webshell:~$ python level2.py
Please enter correct password for flag: 
That password is incorrect
vSalazarZ-picoctf@webshell:~$ python level2.py
Please enter correct password for flag: de76
Welcome back... your flag, user:
picoCTF{tr45h_51ng1ng_489dea9a}
vSalazarZ-picoctf@webshell:~$ 

flag: picoCTF{tr45h_51ng1ng_489dea9a}
```

Con cyberchef

```
Input: 64 65 37 36

Recipes:
From Hex

Output: de76
```
