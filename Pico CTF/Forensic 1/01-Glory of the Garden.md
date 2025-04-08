## Descripción 
This [garden](https://jupiter.challenges.picoctf.org/static/d0e1ffb10fc0017c6a82c57900f3ffe3/garden.jpg) contains more than it seems.

Hint:
1. What is a hex editor?
## Solución 1

Descargamos la imagen jpg e intentemos buscar en contenido, después filtramos -n 18 para que no busque palabras menores a 18 caracteres y así encontramos la bandera 

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

omarsalazar@DESKTOP-H97NF1C:~$ strings -n 18 garden.jpg
strings: 'garden.jpg': No such file
omarsalazar@DESKTOP-H97NF1C:~$ wget https://jupiter.challenges.picoctf.org/static/d0e1ffb10fc0017c6a82c57900f3ffe3/garden.jpg
--2025-04-07 12:44:16--  https://jupiter.challenges.picoctf.org/static/d0e1ffb10fc0017c6a82c57900f3ffe3/garden.jpg
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2295192 (2.2M) [application/octet-stream]
Saving to: ‘garden.jpg’

garden.jpg                    100%[=================================================>]   2.19M  4.85MB/s    in 0.5s

2025-04-07 12:44:17 (4.85 MB/s) - ‘garden.jpg’ saved [2295192/2295192]

omarsalazar@DESKTOP-H97NF1C:~$ strings -n 18 garden.jpg
Copyright (c) 1998 Hewlett-Packard Company
IEC http://www.iec.ch
IEC http://www.iec.ch
.IEC 61966-2.1 Default RGB colour space - sRGB
.IEC 61966-2.1 Default RGB colour space - sRGB
,Reference Viewing Condition in IEC61966-2.1
,Reference Viewing Condition in IEC61966-2.1
%&'()*456789:CDEFGHIJSTUVWXYZcdefghijstuvwxyz
&'()*56789:CDEFGHIJSTUVWXYZcdefghijstuvwxyz
Here is a flag "picoCTF{more_than_m33ts_the_3y3eBdBd2cc}"
omarsalazar@DESKTOP-H97NF1C:~$

flag: picoCTF{more_than_m33ts_the_3y3eBdBd2cc}
```
