## Descripción 
Files can always be changed in a secret way. Can you find the flag? [cat.jpg](https://mercury.picoctf.net/static/149ab4b27d16922142a1e8381677d76f/cat.jpg)

Hint:
1. Look at the details of the file
2. Make sure to submit the flag as picoCTF{XXXXX}

## Solución 

Descargamos la imagen con wget. Luego intentamos buscar texto oculto dentro del archivo usando strings y filtrando con grep pico. Después, abrimos la imagen en un editor hexadecimal con hexedit para examinar su contenido manualmente. Finalmente, encontramos una cadena en base64 que, al decodificarla obtenemos la bandera.

```
omarsalazar@DESKTOP-H97NF1C:~$ wget https://mercury.picoctf.net/static/149ab4b27d16922142a1e8381677d76f/cat.jpg
--2025-05-09 17:41:52--  https://mercury.picoctf.net/static/149ab4b27d16922142a1e8381677d76f/cat.jpg
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 878136 (858K) [application/octet-stream]
Saving to: ‘cat.jpg’

cat.jpg                       100%[=================================================>] 857.55K  1.87MB/s    in 0.4s

2025-05-09 17:41:53 (1.87 MB/s) - ‘cat.jpg’ saved [878136/878136]

omarsalazar@DESKTOP-H97NF1C:~$ strings 
omarsalazar@DESKTOP-H97NF1C:~$ strings cat.jpg | grep pico
omarsalazar@DESKTOP-H97NF1C:~$ strings | grep pico

^Z
[1]+  Stopped                 strings | grep --color=auto pico
omarsalazar@DESKTOP-H97NF1C:~$ hexedit cat.jpg

[2]+  Stopped                 hexedit cat.jpg
omarsalazar@DESKTOP-H97NF1C:~$

resource='cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9'
```

Cyberchef

```
Cyberchef

Input: cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9

Recipe: From Base64

Output: picoCTF{the_m3tadata_1s_modified}
```

## Referencias
https://gchq.github.io/CyberChef/