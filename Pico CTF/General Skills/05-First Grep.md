## Descripción 
Can you find the flag in [file](https://jupiter.challenges.picoctf.org/static/315d3325dc668ab7f1af9194f2de7e7a/file)? This would be really tedious to look through manually, something tells me there is a better way.
## Solución 
- Descargamos el archivo con wget
```
vSalazarZ-picoctf@webshell:~$ wget https://jupiter.challenges.picoctf.org/static/315d3325dc668ab7f1af9194f2de7e7a/file
--2025-02-13 02:52:28--  https://jupiter.challenges.picoctf.org/static/315d3325dc668ab7f1af9194f2de7e7a/file
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14551 (14K) [application/octet-stream]
Saving to: 'file'

file                                                       100%[=======================================================================================================================================>]  14.21K  --.-KB/s    in 0s      

2025-02-13 02:52:28 (369 MB/s) - 'file' saved [14551/14551]

vSalazarZ-picoctf@webshell:~$ ls
README.txt  file
```

Aplicamos el comando grep para obtener la bandera

```
vSalazarZ-picoctf@webshell:~$ file file
file: ASCII text, with very long lines (4200)
vSalazarZ-picoctf@webshell:~$ cat file | grep pico

picoCTF{grep_is_good_to_find_things_f77e0797}
```

