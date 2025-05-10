## Descripción 
The Network Operations Center (NOC) of your local institution picked up a suspicious file, they're getting conflicting information on what type of file it is. They've brought you in as an external expert to examine the file. Can you extract all the information from this strange file?Download the suspicious file [here](https://artifacts.picoctf.net/c_titan/97/flag2of2-final.pdf).

Hint:
1. This problem can be solved by just opening the file in different ways

## Solución 

Descargamos el archivo .pdf y al abrirlo tenemos un pedazo de la bandera, pero no está completa, entonces nos metemos a la terminal y ponemos el archivo con file y nos damos cuenta que era un archivo .png entonces renombramos el archivo a .png y lo abrimos, obteniendo así el otro trozo de la bandera que faltaba

```
omarsalazar@DESKTOP-H97NF1C:~$ wget https://artifacts.picoctf.net/c_titan/97/flag2of2-final.pdf
--2025-05-09 21:08:42--  https://artifacts.picoctf.net/c_titan/97/flag2of2-final.pdf
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.61, 3.161.55.64, 3.161.55.100, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.61|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3362 (3.3K) [application/octet-stream]
Saving to: ‘flag2of2-final.pdf’

flag2of2-final.pdf            100%[=================================================>]   3.28K  --.-KB/s    in 0s

2025-05-09 21:08:42 (1.30 GB/s) - ‘flag2of2-final.pdf’ saved [3362/3362]

omarsalazar@DESKTOP-H97NF1C:~$ ls
flag2of2-final.pdf
omarsalazar@DESKTOP-H97NF1C:~$ file flag2of2-final.pdf
flag2of2-final.pdf: PNG image data, 50 x 50, 8-bit/color RGBA, non-interlaced
omarsalazar@DESKTOP-H97NF1C:~$ cp flag2of2-final.pdf flag2of2-final.png
omarsalazar@DESKTOP-H97NF1C:~$ ls
flag2of2-final.pdf  flag2of2-final.png
omarsalazar@DESKTOP-H97NF1C:~$ open flag2of2-final.png
omarsalazar@DESKTOP-H97NF1C:~$

flag: picoCTF{f1u3n7_1n_pn9_&_pdf_724b1287}
```
