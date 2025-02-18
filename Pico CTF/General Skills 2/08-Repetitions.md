## Descripción 
Can you make sense of this file?Download the file [here](https://artifacts.picoctf.net/c/471/enc_flag).

Hint:
1. Multiple decoding is always good.
## Solución 1

Con consola Linux
Primero descargamos el zip con wget, le damos cat para encontrar la flag
```
vSalazarZ-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/471/enc_flag
--2025-02-17 19:15:18--  https://artifacts.picoctf.net/c/471/enc_flag
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.92, 3.160.22.128, 3.160.22.16, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.92|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 349 [application/octet-stream]
Saving to: 'enc_flag'

enc_flag                                                   100%[=======================================================================================================================================>]     349  --.-KB/s    in 0s      

2025-02-17 19:15:19 (116 MB/s) - 'enc_flag' saved [349/349]

vSalazarZ-picoctf@webshell:~$ ls
enc_flag
vSalazarZ-picoctf@webshell:~$ cat enc_flag|base64 -d|base64 -d|base64 -d|base64 -d|base64 -d|base64 -d

picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_9b59b35c}

```
