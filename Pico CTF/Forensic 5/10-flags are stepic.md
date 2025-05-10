## Descripción 
A group of underground hackers might be using this legit site to communicate. Use your forensic techniques to uncover their message
Try it [here](http://standard-pizzas.picoctf.net:56355/)!

Hint:
1. In the country that doesn't exist, the flag persists

## Solución 

Lanzamos el ejercicio y nos metemos a la página, y miramos que hay un país que no existe, descargamos la imagen y la analizamos, nos damos cuenta que es muy pesada, intentamos de todo pero no funciona. En el título del ejercicio está la palabra stepic, la metemos en la terminal y usamos ese comando, al usar la herramienta stepic para decodificar datos ocultos en la imagen, se obtuvo la bandera oculta 

```
omarsalazar@DESKTOP-H97NF1C:~$ wget http://standard-pizzas.picoctf.net:56355/flags/upz.png
--2025-05-09 21:48:54--  http://standard-pizzas.picoctf.net:56355/flags/upz.png
Resolving standard-pizzas.picoctf.net (standard-pizzas.picoctf.net)... 3.22.195.189
Connecting to standard-pizzas.picoctf.net (standard-pizzas.picoctf.net)|3.22.195.189|:56355... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1788393 (1.7M) [image/png]
Saving to: ‘upz.png’

upz.png                       100%[=================================================>]   1.71M  2.58MB/s    in 0.7s

2025-05-09 21:48:55 (2.58 MB/s) - ‘upz.png’ saved [1788393/1788393]

omarsalazar@DESKTOP-H97NF1C:~$ ls
upz.png
omarsalazar@DESKTOP-H97NF1C:~$ file upz.png
upz.png: PNG image data, 14173 x 10630, 8-bit/color RGBA, non-interlaced
omarsalazar@DESKTOP-H97NF1C:~$ strings upz.png | grep pico
omarsalazar@DESKTOP-H97NF1C:~$ exiftool upz.png
ExifTool Version Number         : 12.76
File Name                       : upz.png
Directory                       : .
File Size                       : 1788 kB
File Modification Date/Time     : 2025:03:05 21:59:14-06:00
File Access Date/Time           : 2025:05:09 21:49:05-06:00
File Inode Change Date/Time     : 2025:05:09 21:48:55-06:00
File Permissions                : -rw-r--r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 14173
Image Height                    : 10630
Bit Depth                       : 8
Color Type                      : RGB with Alpha
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Image Size                      : 14173x10630
Megapixels                      : 150.7
omarsalazar@DESKTOP-H97NF1C:~$ open upz.png
omarsalazar@DESKTOP-H97NF1C:~$ stepic 
usage: stepic [-h] [--version] [--debug] [-d] [-e] [-f FORMAT] [-i FILE] [-t FILE] [-o FILE]
stepic: error: unrecognized arguments: upz.png
omarsalazar@DESKTOP-H97NF1C:~$ stepic -h
usage: stepic [-h] [--version] [--debug] [-d] [-e] [-f FORMAT] [-i FILE] [-t FILE] [-o FILE]

Hide data in an image, or read hidden data from an image.

options:
  -h, --help            show this help message and exit
  --version             show program's version number and exit
  --debug
  -d, --decode          given an image, write out the hidden data file
  -e, --encode          given an image and data file, write out a new image file with the data hidden in it
  -f FORMAT, --format FORMAT
                        output image format (optional)
  -i FILE, --image-in= FILE
                        read in image FILE for decoding or encoding
  -t FILE, --data-in= FILE
                        read in data FILE for encoding
  -o FILE, --out= FILE  write out to FILE, data when decoding, image when encoding
omarsalazar@DESKTOP-H97NF1C:~$ stepic -i upz.png -d
/usr/local/lib/python3.12/dist-packages/pillow-11.2.1-py3.12-linux-x86_64.egg/PIL/Image.py:3442: DecompressionBombWarning: Image size (150658990 pixels) exceeds limit of 89478485 pixels, could be decompression bomb DOS attack.
  warnings.warn(
picoCTF{fl4g_h45_fl4g4a37da4c}omarsalazar@DESKTOP-H97NF1C:~$

flag: picoCTF{fl4g_h45_fl4g4a37da4c}
```
