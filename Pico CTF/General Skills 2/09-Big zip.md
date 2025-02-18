## Descripción 
Unzip this archive and find the flag.
- [Download zip file](https://artifacts.picoctf.net/c/505/big-zip-files.zip)

Hint:
1. Can grep be instructed to look at every file in a directory and its subdirectories?
## Solución 1

Con consola Linux
Primero descargamos el zip con wget, le damos unzip y con un grep -r pico sacamos la flag

```
vSalazarZ-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/505/big-zip-files.zip
--2025-02-17 19:21:30--  https://artifacts.picoctf.net/c/505/big-zip-files.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.128, 3.160.22.92, 3.160.22.43, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.128|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3182988 (3.0M) [application/octet-stream]
Saving to: 'big-zip-files.zip'

big-zip-files.zip                                          100%[=======================================================================================================================================>]   3.04M  1.80MB/s    in 1.7s    

2025-02-17 19:21:32 (1.80 MB/s) - 'big-zip-files.zip' saved [3182988/3182988]

vSalazarZ-picoctf@webshell:~$ ls
big-zip-files.zip

vSalazarZ-picoctf@webshell:~$ grep -r pico
.wget-hsts:mercury.picoctf.net  0       0       1739416979      0
.python_history:echo "picoCTF{$((0x3D))}"
big-zip-files/folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt:information on the record will last a billion years. 

Genes and brains and books encode picoCTF{gr3p_15_m4g1c_ef8790dc}

vSalazarZ-picoctf@webshell:~$ grep -r picoCTF
```
