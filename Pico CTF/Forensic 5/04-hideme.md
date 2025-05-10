## Descripción 
Every file gets a flag.The SOC analyst saw one image been sent back and forth between two people. They decided to investigate and found out that there was more than what meets the eye [here](https://artifacts.picoctf.net/c/259/flag.png).

Hint:
1. 

## Solución 

Descargamos el archivo con wget. Al inspeccionarla con binwalk, descubrimos que contenía datos comprimidos, incluyendo un archivo ZIP con una carpeta llamada secret y dentro de ella otra imagen flag.png. Al abrir esta segunda imagen, encontramos la bandera

```
omarsalazar@DESKTOP-H97NF1C:~$ wget https://artifacts.picoctf.net/c/259/flag.png
--2025-05-09 19:15:08--  https://artifacts.picoctf.net/c/259/flag.png
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.100, 3.161.55.26, 3.161.55.64, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.100|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 42930 (42K) [application/octet-stream]
Saving to: ‘flag.png’

flag.png                      100%[=================================================>]  41.92K  --.-KB/s    in 0s

2025-05-09 19:15:09 (123 MB/s) - ‘flag.png’ saved [42930/42930]

omarsalazar@DESKTOP-H97NF1C:~$ ls
flag.png
omarsalazar@DESKTOP-H97NF1C:~$ strings
^Z
[1]+  Stopped                 strings
omarsalazar@DESKTOP-H97NF1C:~$ open flag.png
omarsalazar@DESKTOP-H97NF1C:~$ binwalk -e flag.png

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 512 x 504, 8-bit/color RGBA, non-interlaced
41            0x29            Zlib compressed data, compressed
39739         0x9B3B          Zip archive data, at least v1.0 to extract, name: secret/
39804         0x9B7C          Zip archive data, at least v2.0 to extract, compressed size: 2869, uncompressed size: 3024, name: secret/flag.png
42908         0xA79C          End of Zip archive, footer length: 22

omarsalazar@DESKTOP-H97NF1C:~$ ls
_flag.png.extracted  flag.png
omarsalazar@DESKTOP-H97NF1C:~$ cd _flag.png.extracted
omarsalazar@DESKTOP-H97NF1C:~/_flag.png.extracted$ ls
29  29.zlib  9B3B.zip  secret
omarsalazar@DESKTOP-H97NF1C:~/_flag.png.extracted$ cd secret
omarsalazar@DESKTOP-H97NF1C:~/_flag.png.extracted/secret$ ls
flag.png
omarsalazar@DESKTOP-H97NF1C:~/_flag.png.extracted/secret$ open flag.png
omarsalazar@DESKTOP-H97NF1C:~/_flag.png.extracted/secret$

flag: picoCTF{Hiddinng_An_imag3_within_@n_ima9e_cda72af0}
```
