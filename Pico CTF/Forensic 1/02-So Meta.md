## Descripción 
Find the flag in this [picture](https://jupiter.challenges.picoctf.org/static/00efdf2961da1e21470ffc0d496c3cc2/pico_img.png).

Hint:
1. What does meta mean in the context of files?
2. Ever heard of metadata?
## Solución 1

Descargamos la imagen jpg e intentemos buscar en contenido, después hacemos un strings para ver las cadenas que contiene la imagen y hacemos un strings | grep pico para sacar directamente la bandera 

```
omarsalazar@DESKTOP-H97NF1C:~$ wget https://jupiter.challenges.picoctf.org/static/00efdf2961da1e21470ffc0d496c3cc2/pico_img.png
--2025-04-07 12:51:48--  https://jupiter.challenges.picoctf.org/static/00efdf2961da1e21470ffc0d496c3cc2/pico_img.png
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 108795 (106K) [application/octet-stream]
Saving to: ‘pico_img.png’

pico_img.png                  100%[=================================================>] 106.25K   635KB/s    in 0.2s

2025-04-07 12:51:49 (635 KB/s) - ‘pico_img.png’ saved [108795/108795]

omarsalazar@DESKTOP-H97NF1C:~$ strings pico_img.png | grep pico
picoCTF{s0_m3ta_fec06741}
omarsalazar@DESKTOP-H97NF1C:~$
```

## Referencias
https://es.wikipedia.org/wiki/Metadatos