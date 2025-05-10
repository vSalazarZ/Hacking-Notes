## Descripción 
How about some hide and seek?Download this file [here](https://artifacts.picoctf.net/c_titan/5/unknown.zip).

Hint:
1. How can you view the information about the picture?
2. If something isn't in the expected form, maybe it deserves attention?

## Solución 

Descargamos un archivo comprimido, lo descomprimimos y obtuvimos la imagen ukn_reality.jpg. Luego, utilizamos exiftool para analizar sus metadatos y encontramos una cadena oculta en los metadatos de la imagen, simplemente decodificamos esa cadena y obtenemos la bandera

```
omarsalazar@DESKTOP-H97NF1C:~$ wget https://artifacts.picoctf.net/c_titan/5/unknown.zip
--2025-05-09 19:34:59--  https://artifacts.picoctf.net/c_titan/5/unknown.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.26, 3.161.55.64, 3.161.55.61, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.26|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2252228 (2.1M) [application/octet-stream]
Saving to: ‘unknown.zip’

unknown.zip                   100%[=================================================>]   2.15M  5.91MB/s    in 0.4s

2025-05-09 19:35:00 (5.91 MB/s) - ‘unknown.zip’ saved [2252228/2252228]

omarsalazar@DESKTOP-H97NF1C:~$ ls
unknown.zip
omarsalazar@DESKTOP-H97NF1C:~$ unzip unknown.zip
Archive:  unknown.zip
  inflating: ukn_reality.jpg
omarsalazar@DESKTOP-H97NF1C:~$ ls
ukn_reality.jpg  unknown.zip
omarsalazar@DESKTOP-H97NF1C:~$ open ukn_reality.jpg
omarsalazar@DESKTOP-H97NF1C:~$ exitfool ukn_reality.jpg
Command 'exitfool' not found, did you mean:
  command 'exiftool' from deb libimage-exiftool-perl (12.67+dfsg-1)
Try: sudo apt install <deb name>
omarsalazar@DESKTOP-H97NF1C:~$ exiftool ukn_reality.jpg
ExifTool Version Number         : 12.76
File Name                       : ukn_reality.jpg
Directory                       : .
File Size                       : 2.3 MB
File Modification Date/Time     : 2024:02:15 16:40:17-06:00
File Access Date/Time           : 2025:05:09 19:35:17-06:00
File Inode Change Date/Time     : 2025:05:09 19:35:09-06:00
File Permissions                : -rw-r--r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.01
Resolution Unit                 : inches
X Resolution                    : 72
Y Resolution                    : 72
XMP Toolkit                     : Image::ExifTool 11.88
Attribution URL                 : cGljb0NURntNRTc0RDQ3QV9ISUREM05fNGRhYmRkY2J9Cg==
Image Width                     : 4308
Image Height                    : 2875
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 4308x2875
Megapixels                      : 12.4
omarsalazar@DESKTOP-H97NF1C:~$

Cadena: cGljb0NURntNRTc0RDQ3QV9ISUREM05fNGRhYmRkY2J9Cg
```

Cyberchef
```
Input: cGljb0NURntNRTc0RDQ3QV9ISUREM05fNGRhYmRkY2J9Cg

Recipe: From Base64

Output: picoCTF{ME74D47A_HIDD3N_4dabddcb}
```

## Referencias 
https://gchq.github.io/CyberChef/
