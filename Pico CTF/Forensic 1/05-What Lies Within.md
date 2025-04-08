## Descripción 
There's something in the [building](https://jupiter.challenges.picoctf.org/static/011955b303f293d60c8116e6a4c5c84f/buildings.png). Can you retrieve the flag?

Hint:
1. There is data encoded somewhere... there might be an online decoder.
## Solución 1

Descargamos el archivo y miramos el contenido de la imagen png, es una imagen simple pero las pistas nos dice que puede haber un decodificador en línea, buscamos un decodificador que nos ayude a resolver este problema que en este caso es "Steganography Online" y obtenemos la bandera al ingresar la imagen png a este mismo.

```
El decodificador que usaremos es "Steganography Online"

Decode: Builidngs.png

Hidden message: picoCTF{h1d1ng_1n_th3_b1t5}

flag: picoCTF{h1d1ng_1n_th3_b1t5}
```

## Solución 2

Descargamos Ruby y zsteg, zsteg es una herramienta hecha en Ruby que sirve para detectar y extraer datos ocultos en archivos de imagen PNG y BMP, especialmente usando esteganografía.

```
omarsalazar@DESKTOP-H97NF1C:~$sudo apt update
omarsalazar@DESKTOP-H97NF1C:~$sudo apt install ruby ruby-dev imagemagick
omarsalazar@DESKTOP-H97NF1C:~$sudo gem install zsteg

Después escaneamos la imagen correspondiente para obtener datos ocultos:

omarsalazar@DESKTOP-H97NF1C:~$ zsteg buildings.png
b1,r,lsb,xy         .. text: "^5>R5YZrG"
b1,rgb,lsb,xy       .. text: "picoCTF{h1d1ng_1n_th3_b1t5}"
b1,abgr,msb,xy      .. file: PGP Secret Sub-key -
b2,b,lsb,xy         .. text: "XuH}p#8Iy="
b3,abgr,msb,xy      .. text: "t@Wp-_tH_v\r"
b4,r,lsb,xy         .. text: "fdD\"\"\"\" "
b4,r,msb,xy         .. text: "%Q#gpSv0c05"
b4,g,lsb,xy         .. text: "fDfffDD\"\""
b4,g,msb,xy         .. text: "f\"fff\"\"DD"
b4,b,lsb,xy         .. text: "\"$BDDDDf"
b4,b,msb,xy         .. text: "wwBDDDfUU53w"
b4,rgb,msb,xy       .. text: "dUcv%F#A`"
b4,bgr,msb,xy       .. text: " V\"c7Ga4"
b4,abgr,msb,xy      .. text: "gOC_$_@o"
omarsalazar@DESKTOP-H97NF1C:~$

flag: picoCTF{h1d1ng_1n_th3_b1t5}
```
## Referencias 
https://stylesuxx.github.io/steganography/
https://github.com/zed-0xff/zsteg