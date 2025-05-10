## Descripción 
RED, RED, RED, REDDownload the image: [red.png](https://challenge-files.picoctf.net/c_verbal_sleep/831307718b34193b288dde31e557484876fb84978b5818e2627e453a54aa9ba6/red.png)

Hint:
1. The picture seems pure, but is it though?
2. Red?Ged?Bed?Aed?
3. Check whatever Facebook is called now.

## Solución 

Se descargó una imagen con wget. Al inspeccionarla con strings y exiftool, se encontró un poema en la metadata de la imagen. Después con zsteg se detectó una cadena oculta en los bits menos significativos del canal RGBA. Decodificamos esa cadena y obtenemos la bandera

```
omarsalazar@DESKTOP-H97NF1C:~$ wget https://challenge-files.picoctf.net/c_verbal_sleep/831307718b34193b288dde31e557484876fb84978b5818e2627e453a54aa9ba6/red.png
--2025-05-09 21:18:02--  https://challenge-files.picoctf.net/c_verbal_sleep/831307718b34193b288dde31e557484876fb84978b5818e2627e453a54aa9ba6/red.png
Resolving challenge-files.picoctf.net (challenge-files.picoctf.net)... 65.9.149.95, 65.9.149.24, 65.9.149.85, ...
Connecting to challenge-files.picoctf.net (challenge-files.picoctf.net)|65.9.149.95|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 796 [application/octet-stream]
Saving to: ‘red.png’

red.png                   100%[==================================>]     796  --.-KB/s    in 0s

2025-05-09 21:18:02 (100 MB/s) - ‘red.png’ saved [796/796]

omarsalazar@DESKTOP-H97NF1C:~$ ls
red.png
omarsalazar@DESKTOP-H97NF1C:~$ file red.png
red.png: PNG image data, 128 x 128, 8-bit/color RGBA, non-interlaced
omarsalazar@DESKTOP-H97NF1C:~$ strings
^Z
[1]+  Stopped                 strings
omarsalazar@DESKTOP-H97NF1C:~$ strings red.png
IHDR
tEXtPoem
Crimson heart, vibrant and bold,
Hearts flutter at your sight.
Evenings glow softly red,
Cherries burst with sweet life.
Kisses linger with your warmth.
Love deep as merlot.
Scarlet leaves falling softly,
Bold in every stroke.x
IDATx
IEND
omarsalazar@DESKTOP-H97NF1C:~$ exiftool red.png
ExifTool Version Number         : 12.76
File Name                       : red.png
Directory                       : .
File Size                       : 796 bytes
File Modification Date/Time     : 2025:03:05 21:34:15-06:00
File Access Date/Time           : 2025:05:09 21:18:39-06:00
File Inode Change Date/Time     : 2025:05:09 21:18:02-06:00
File Permissions                : -rw-r--r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 128
Image Height                    : 128
Bit Depth                       : 8
Color Type                      : RGB with Alpha
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Poem                            : Crimson heart, vibrant and bold,.Hearts flutter at your sight..Evenings glow softly red,.Cherries burst with sweet life..Kisses linger with your warmth..Love deep as merlot..Scarlet leaves falling softly,.Bold in every stroke.
Image Size                      : 128x128
Megapixels                      : 0.016
omarsalazar@DESKTOP-H97NF1C:~$ zsteg -s l red.png
meta Poem           .. text: "Crimson heart, vibrant and bold,\nHearts flutter at your sight.\nEvenings glow softly red,\nCherries burst with sweet life.\nKisses linger with your warmth.\nLove deep as merlot.\nScarlet leaves falling softly,\nBold in every stroke."
b1,rgba,lsb,xy      .. text: "cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ=="
b1,rgba,msb,xy      .. file: OpenPGP Public Key
b2,g,lsb,xy         .. text: "ET@UETPETUUT@TUUTD@PDUDDDPE"
b2,rgb,lsb,xy       .. file: OpenPGP Secret Key
b2,bgr,msb,xy       .. file: OpenPGP Public Key
b2,rgba,lsb,xy      .. file: OpenPGP Secret Key
b2,rgba,msb,xy      .. text: "CIkiiiII"
b2,abgr,lsb,xy      .. file: OpenPGP Secret Key
b2,abgr,msb,xy      .. text: "caciiiiicCK"
b3,rgba,msb,xy      .. text: "#~`#vr#7r#7b#"
b3,abgr,msb,xy      .. text: "7r#7r#7r"
b4,b,lsb,xy         .. file: 0421 Alliant compact executable not stripped
omarsalazar@DESKTOP-H97NF1C:~$

Cadena: cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ
```

Cyberchef
```
Input: cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ

Recipe: From Base64

Output: picoCTF{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_}
```

## Referencias
https://gchq.github.io/CyberChef/