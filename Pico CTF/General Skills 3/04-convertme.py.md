## Descripción 
Run the Python script and convert the given number from decimal to binary to get the flag.[Download Python script](https://artifacts.picoctf.net/c/23/convertme.py)

Hint:
1. Look up a decimal to binary number conversion app on the web or use your computer's calculator!
2. The `str_xor` function does not need to be reverse engineered for this challenge.
3. If you have Python on your computer, you can download the script normally and run it. Otherwise, use the `wget` command in the webshell.
4. To use `wget` in the webshell, first right click on the download link and select 'Copy Link' or 'Copy Link Address'
5. To use `wget` in the webshell, first right click on the download link and select 'Copy Link' or 'Copy Link Address'
6. Finally, to run the script, type everything after the dollar sign and then press enter: `$ python3 convertme.py`
## Solución 1

Con consola linux
Usamos wget para descargar el archivo y usamos cat para ver el contenido.
Después nos pide usamos una consola python para correr el programa y nos pide una contraseña

```
vSalazarZ-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/23/convertme.py
--2025-02-20 04:57:33--  https://artifacts.picoctf.net/c/23/convertme.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.92, 3.160.22.128, 3.160.22.16, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.92|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1189 (1.2K) [application/octet-stream]
Saving to: 'convertme.py'

convertme.py                                               100%[=======================================================================================================================================>]   1.16K  --.-KB/s    in 0.03s   

2025-02-20 04:57:33 (44.8 KB/s) - 'convertme.py' saved [1189/1189]

vSalazarZ-picoctf@webshell:~$ ls
convertme.py
vSalazarZ-picoctf@webshell:~$ cat convertme.py

import random



def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])


flag_enc = chr(0x15) + chr(0x07) + chr(0x08) + chr(0x06) + chr(0x27) + chr(0x21) + chr(0x23) + chr(0x15) + chr(0x5f) + chr(0x05) + chr(0x08) + chr(0x2a) + chr(0x1c) + chr(0x5e) + chr(0x1e) + chr(0x1b) + chr(0x3b) + chr(0x17) + chr(0x51) + chr(0x5b) + chr(0x58) + chr(0x5c) + chr(0x3b) + chr(0x4c) + chr(0x06) + chr(0x5d) + chr(0x09) + chr(0x5e) + chr(0x00) + chr(0x41) + chr(0x01) + chr(0x13)


num = random.choice(range(10,101))

print('If ' + str(num) + ' is in decimal base, what is it in binary base?')

ans = input('Answer: ')

try:
  ans_num = int(ans, base=2)
  
  if ans_num == num:
    flag = str_xor(flag_enc, 'enkidu')
    print('That is correct! Here\'s your flag: ' + flag)
  else:
    print(str(ans_num) + ' and ' + str(num) + ' are not equal.')
  
except ValueError:
  print('That isn\'t a binary number. Binary numbers contain only 1\'s and 0\'s')
vSalazarZ-picoctf@webshell:~$ python convertme.py
If 81 is in decimal base, what is it in binary base?
Answer: 01010001
That is correct! Here's your flag: 

picoCTF{4ll_y0ur_b4535_9c3b7d4d}
```

Usamos cyberchef
Usamos cyberchef para convertir 81 decimal a binario
```
Input: 81

Recipes:
From Decimal
To Binary

Output: 01010001
```
