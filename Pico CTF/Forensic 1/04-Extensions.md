## Descripción 
This is a really weird text file [TXT](https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt)? Can you find the flag?

Hint:
1. How do operating systems know what kind of file it is? (It's not just the ending!
2. Make sure to submit the flag as picoCTF{XXXXX}
## Solución 1

Descargamos el archivo y lo intentamos abrir con un cat para ver su contenido y nos damos cuenta que es un .png no .txt, entonces cambiamos la extensión de .txt a .png y lo abrimos y veremos la bandera en la imagen 

```
omarsalazar@DESKTOP-H97NF1C:~$ wget https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt --2025-04-07 21:39:25-- https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8 Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected. HTTP request sent, awaiting response... 200 OK Length: 9984 (9.8K) [application/octet-stream] Saving to: ‘flag.txt’ flag.txt 100%[=================================================>] 9.75K --.-KB/s in 0s 2025-04-07 21:39:26 (632 MB/s) - ‘flag.txt’ saved [9984/9984] omarsalazar@DESKTOP-H97NF1C:~$ file flag.txt flag.txt: PNG image data, 1697 x 608, 8-bit/color RGB, non-interlaced

omarsalazar@DESKTOP-H97NF1C:~$ mv flag.txt flag.png

Y abrimos la imagen y veremos la bandera 

omarsalazar@DESKTOP-H97NF1C:~$ explorer.exe flag.png
flag: picoCTF{now_you_know_about_extensions}
```
