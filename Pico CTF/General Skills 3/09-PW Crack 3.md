## Descripción 
Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/16/level3.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/16/level3.flag.txt.enc) and the [hash](https://artifacts.picoctf.net/c/16/level3.hash.bin) in the same directory too.There are 7 potential passwords with 1 being correct. You can find these by examining the password checker script.

Hint:
1. To view the level3.hash.bin file in the webshell, do: `$ bvi level3.hash.bin`
2. To exit `bvi` type `:q` and press enter.
3. The `str_xor` function does not need to be reverse engineered for this challenge.
## Solución 1

Con consola linux y python
Primero descargamos el archivo con wget.
Nos pide una contraseña al intentar correr el archivo .py en pyhton
Usamos cat para ver el contenido de python de level3.py
Y al final del archivo nos dice que tiene una lista de diferentes contraseñas que son 7, podemos meter de una en una hasta dar con la correcta

```
vSalazarZ-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/16/level3.py
--2025-02-20 05:35:12--  https://artifacts.picoctf.net/c/16/level3.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.16, 3.160.22.43, 3.160.22.92, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.16|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1337 (1.3K) [application/octet-stream]
Saving to: 'level3.py'

level3.py                                                  100%[=======================================================================================================================================>]   1.31K  --.-KB/s    in 0s      

2025-02-20 05:35:12 (25.0 MB/s) - 'level3.py' saved [1337/1337]

vSalazarZ-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/16/level3.flag.txt.enc
--2025-02-20 05:35:21--  https://artifacts.picoctf.net/c/16/level3.flag.txt.enc
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.128, 3.160.22.16, 3.160.22.43, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.128|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31 [application/octet-stream]
Saving to: 'level3.flag.txt.enc'

level3.flag.txt.enc                                        100%[=======================================================================================================================================>]      31  --.-KB/s    in 0s      

2025-02-20 05:35:21 (2.06 MB/s) - 'level3.flag.txt.enc' saved [31/31]

vSalazarZ-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/16/level3.hash.bin
--2025-02-20 05:35:29--  https://artifacts.picoctf.net/c/16/level3.hash.bin
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.43, 3.160.22.128, 3.160.22.92, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.43|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16 [application/octet-stream]
Saving to: 'level3.hash.bin'

level3.hash.bin                                            100%[=======================================================================================================================================>]      16  --.-KB/s    in 0s      

2025-02-20 05:35:29 (189 KB/s) - 'level3.hash.bin' saved [16/16]

vSalazarZ-picoctf@webshell:~$ ls
level3.flag.txt.enc  level3.hash.bin  level3.py
vSalazarZ-picoctf@webshell:~$ python level3.py
Please enter correct password for flag: 
That password is incorrect
vSalazarZ-picoctf@webshell:~$ cat level3.py
import hashlib

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

flag_enc = open('level3.flag.txt.enc', 'rb').read()
correct_pw_hash = open('level3.hash.bin', 'rb').read()


def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()


def level_3_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    user_pw_hash = hash_pw(user_pw)
    
    if( user_pw_hash == correct_pw_hash ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")



level_3_pw_check()


# The strings below are 7 possibilities for the correct password. 
#   (Only 1 is correct)
pos_pw_list = ["6997", "3ac8", "f0ac", "4b17", "ec27", "4e66", "865e"]

vSalazarZ-picoctf@webshell:~$ python level3.py
Please enter correct password for flag: 6997
Please enter correct password for flag: 3ac8
Please enter correct password for flag: f0ac
Please enter correct password for flag: 4b17
Please enter correct password for flag: ec27
Please enter correct password for flag: 4e66
Please enter correct password for flag: 865e
Welcome back... your flag, user:
picoCTF{m45h_fl1ng1ng_2b072a90}
vSalazarZ-picoctf@webshell:~$ 

flag: picoCTF{m45h_fl1ng1ng_2b072a90}
```

## Solución 1

Con consola linux y python

El segundo metodo para la contraseña es: usar el comando del hint 2: `$ bvi level3.hash.bin`
Para ver el hash que es: 1B 18 E1 31 6F 92 18 CC 5B 05 3E 1C EA 28 E0 2E
Lo metemos en un decodificador de hash y tenemos la flag
```
vSalazarZ-picoctf@webshell:~$ ls
level3.flag.txt.enc  level3.hash.bin  level3.py
vSalazarZ-picoctf@webshell:~$ python level3.py
Please enter correct password for flag: 
That password is incorrect
vSalazarZ-picoctf@webshell:~$ cat level3.py
import hashlib

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

flag_enc = open('level3.flag.txt.enc', 'rb').read()
correct_pw_hash = open('level3.hash.bin', 'rb').read()


def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()


def level_3_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    user_pw_hash = hash_pw(user_pw)
    
    if( user_pw_hash == correct_pw_hash ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")



level_3_pw_check()


# The strings below are 7 possibilities for the correct password. 
#   (Only 1 is correct)
pos_pw_list = ["6997", "3ac8", "f0ac", "4b17", "ec27", "4e66", "865e"]

vSalazarZ-picoctf@webshell:~$ 
vSalazarZ-picoctf@webshell:~$  bvi level3.hash.bin
1B 18 E1 31 6F 92 18 CC 5B 05 3E 1C EA 28 E0 2E
vSalazarZ-picoctf@webshell:~$ python level3.py
Please enter correct password for flag: 865e
Welcome back... your flag, user:
picoCTF{m45h_fl1ng1ng_2b072a90}
vSalazarZ-picoctf@webshell:~$ 

flag: picoCTF{m45h_fl1ng1ng_2b072a90}
```

### Bibliografía
https://crackstation.net/