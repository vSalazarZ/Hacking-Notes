## Descripción 
Matryoshka dolls are a set of wooden dolls of decreasing size placed one inside another. What's the final one? Image: [this](https://mercury.picoctf.net/static/b6205dd933ec01c022c4e6acbdf11116/dolls.jpg)

Hint:
1. Wait, you can hide files inside files? But how do you find them?
2. Make sure to submit the flag as picoCTF{XXXXX}
## Solución 1

Descargamos la imagen dolls.jpg y al inspeccionarla con strings y binwalk, descubrimos que contenía archivos ZIP ocultos. Extraemos el primero y encontramos una imagen, la cual también tenía otra imagen oculta dentro. Repetimos este proceso varias veces, descomprimiendo y analizando cada nueva imagen hasta que encontramos un archivo flag.txt que contiene la bandera 

```
omarsalazar@DESKTOP-H97NF1C:~$ https://mercury.picoctf.net/static/b6205dd933ec01c022c4e6acbdf11116/dolls.jpg
-bash: https://mercury.picoctf.net/static/b6205dd933ec01c022c4e6acbdf11116/dolls.jpg: No such file or directory
omarsalazar@DESKTOP-H97NF1C:~$ wget https://mercury.picoctf.net/static/b6205dd933ec01c022c4e6acbdf11116/dolls.jpg
--2025-05-05 11:42:21--  https://mercury.picoctf.net/static/b6205dd933ec01c022c4e6acbdf11116/dolls.jpg
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 651630 (636K) [application/octet-stream]
Saving to: ‘dolls.jpg’

dolls.jpg                     100%[=================================================>] 636.36K  1.22MB/s    in 0.5s

2025-05-05 11:42:22 (1.22 MB/s) - ‘dolls.jpg’ saved [651630/651630]

omarsalazar@DESKTOP-H97NF1C:~$ open dolls.jpg
omarsalazar@DESKTOP-H97NF1C:~$ strings -n 10 dolls.jpg
eiCCPICC Profile
Screenshot
iTXtXML:com.adobe.xmp
<x:xmpmeta xmlns:x="adobe:ns:meta/" x:xmptk="XMP Core 5.4.0">
   <rdf:RDF xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#">
      <rdf:Description rdf:about=""
            xmlns:exif="http://ns.adobe.com/exif/1.0/">
         <exif:PixelXDimension>594</exif:PixelXDimension>
         <exif:UserComment>Screenshot</exif:UserComment>
         <exif:PixelYDimension>1104</exif:PixelYDimension>
      </rdf:Description>
   </rdf:RDF>
</x:xmpmeta>
IDEEb^*Qcb4
Z9vT?vA/_$
a#;s;[gyjD
n3zY[>GAD
=,e< =*?Yp
3Sn'&bbGf'
\sMKn$R`eG
~wkwwG;~A
base_images/2_c.jpgUT
C}-Zjvj"""Z
/\6c7l*18Mj
Hr~&    8Ja7i,
t+Vp`B2AYq
se\45~|_4Z
%(oQ1y~?e?
Db^!u"tE=O
9)IZ9Rj|Fn
|YrAkJI_S,
cG3CKkcs3G
=T*N+b_Io8
-8(Ly<7-"`
kT_S0/,0L3
mlKszlh<f$
>,\vxk~[        .R
l_(ZU2&?IX
>KO<K-j3|sD
base_images/2_c.jpgUT

omarsalazar@DESKTOP-H97NF1C:~$ binwalk dolls.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 594 x 1104, 8-bit/color RGBA, non-interlaced
3226          0xC9A           TIFF image data, big-endian, offset of first image directory: 8
272492        0x4286C         Zip archive data, at least v2.0 to extract, compressed size: 378950, uncompressed size: 383938, name: base_images/2_c.jpg
651608        0x9F158         End of Zip archive, footer length: 22

omarsalazar@DESKTOP-H97NF1C:~$ binwalk -e dolls.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 594 x 1104, 8-bit/color RGBA, non-interlaced
3226          0xC9A           TIFF image data, big-endian, offset of first image directory: 8
272492        0x4286C         Zip archive data, at least v2.0 to extract, compressed size: 378950, uncompressed size: 383938, name: base_images/2_c.jpg
651608        0x9F158         End of Zip archive, footer length: 22

omarsalazar@DESKTOP-H97NF1C:~$ ls
_dolls.jpg.extracted  dolls.jpg
omarsalazar@DESKTOP-H97NF1C:~$ cd _dolls.jpg.extracted
omarsalazar@DESKTOP-H97NF1C:~/_dolls.jpg.extracted$ ls
4286C.zip  base_images
omarsalazar@DESKTOP-H97NF1C:~/_dolls.jpg.extracted$ cd base_images
omarsalazar@DESKTOP-H97NF1C:~/_dolls.jpg.extracted/base_images$ ls
2_c.jpg
omarsalazar@DESKTOP-H97NF1C:~/_dolls.jpg.extracted/base_images$ open 2_c.jpg
omarsalazar@DESKTOP-H97NF1C:~/_dolls.jpg.extracted/base_images$ binwalk 2_c.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 526 x 1106, 8-bit/color RGBA, non-interlaced
3226          0xC9A           TIFF image data, big-endian, offset of first image directory: 8
187707        0x2DD3B         Zip archive data, at least v2.0 to extract, compressed size: 196043, uncompressed size: 201445, name: base_images/3_c.jpg
383805        0x5DB3D         End of Zip archive, footer length: 22
383916        0x5DBAC         End of Zip archive, footer length: 22

omarsalazar@DESKTOP-H97NF1C:~/_dolls.jpg.extracted/base_images$ binwalk -e 2_c.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 526 x 1106, 8-bit/color RGBA, non-interlaced
3226          0xC9A           TIFF image data, big-endian, offset of first image directory: 8
187707        0x2DD3B         Zip archive data, at least v2.0 to extract, compressed size: 196043, uncompressed size: 201445, name: base_images/3_c.jpg
383805        0x5DB3D         End of Zip archive, footer length: 22
383916        0x5DBAC         End of Zip archive, footer length: 22

omarsalazar@DESKTOP-H97NF1C:~/_dolls.jpg.extracted/base_images$ ls
2_c.jpg  _2_c.jpg.extracted
omarsalazar@DESKTOP-H97NF1C:~/_dolls.jpg.extracted/base_images$ cd _2_c.jpg.extracted/base_images
omarsalazar@DESKTOP-H97NF1C:~/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images$ ls
3_c.jpg
omarsalazar@DESKTOP-H97NF1C:~/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images$ open 3_c.jpg
omarsalazar@DESKTOP-H97NF1C:~/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images$ ls
3_c.jpg
omarsalazar@DESKTOP-H97NF1C:~/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images$ binwalk 3_c.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 428 x 1104, 8-bit/color RGBA, non-interlaced
3226          0xC9A           TIFF image data, big-endian, offset of first image directory: 8
123606        0x1E2D6         Zip archive data, at least v2.0 to extract, compressed size: 77651, uncompressed size: 79809, name: base_images/4_c.jpg
201423        0x312CF         End of Zip archive, footer length: 22

omarsalazar@DESKTOP-H97NF1C:~/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images$ binwalk -e 3_c.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 428 x 1104, 8-bit/color RGBA, non-interlaced
3226          0xC9A           TIFF image data, big-endian, offset of first image directory: 8
123606        0x1E2D6         Zip archive data, at least v2.0 to extract, compressed size: 77651, uncompressed size: 79809, name: base_images/4_c.jpg
201423        0x312CF         End of Zip archive, footer length: 22

omarsalazar@DESKTOP-H97NF1C:~/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images$ ls
3_c.jpg  _3_c.jpg.extracted
omarsalazar@DESKTOP-H97NF1C:~/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images$ cd _3_c.jpg.extracted/base_images
omarsalazar@DESKTOP-H97NF1C:~/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images$ ls
4_c.jpg
omarsalazar@DESKTOP-H97NF1C:~/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images$ open 4_c.jpg
omarsalazar@DESKTOP-H97NF1C:~/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images$ ls
4_c.jpg
omarsalazar@DESKTOP-H97NF1C:~/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images$ binwalk -e 4_c.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 320 x 768, 8-bit/color RGBA, non-interlaced
3226          0xC9A           TIFF image data, big-endian, offset of first image directory: 8
79578         0x136DA         Zip archive data, at least v2.0 to extract, compressed size: 65, uncompressed size: 81, name: flag.txt
79787         0x137AB         End of Zip archive, footer length: 22

omarsalazar@DESKTOP-H97NF1C:~/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images$ ls
4_c.jpg  _4_c.jpg.extracted
omarsalazar@DESKTOP-H97NF1C:~/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images$ cd _4_c.jpg.extracted/
omarsalazar@DESKTOP-H97NF1C:~/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images/_4_c.jpg.extracted$ ls
136DA.zip  flag.txt
omarsalazar@DESKTOP-H97NF1C:~/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images/_4_c.jpg.extracted$ cat flag.txt
picoCTF{4f11048e83ffc7d342a15bd2309b47de}omarsalazar@DESKTOP-H97NF1C:~/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images/_4_c.jpg.extracted$

flag: picoCTF{4f11048e83ffc7d342a15bd2309b47de}
```
