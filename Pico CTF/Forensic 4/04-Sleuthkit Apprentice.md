## Descripción 
Download this disk image and find the flag.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.
- [Download compressed disk image](https://artifacts.picoctf.net/c/137/disk.flag.img.gz)

## Solución 1

Descargamos una imagen comprimida disk.flag.img.gz y la descomprimimos, obteniendo disk.flag.img. Luego analizamos la imagen con mmls para ver sus particiones y usamos fsstat y fls para explorar el sistema de archivos ext4 que contenía. Encontramos una carpeta llamada my_folder que está en el root que tenía archivos como flag.txt y flag.uni.txt. Finalmente, con icat recuperamos el contenido de esos archivos directamente para obtener la bandera

```
omarsalazar@DESKTOP-H97NF1C:~$ wget https://artifacts.picoctf.net/c/137/disk.flag.img.gz
--2025-05-07 20:24:47--  https://artifacts.picoctf.net/c/137/disk.flag.img.gz
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.64, 3.161.55.100, 3.161.55.26, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.64|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 47534568 (45M) [application/octet-stream]
Saving to: ‘disk.flag.img.gz’

disk.flag.img.gz              100%[=================================================>]  45.33M  10.2MB/s    in 4.9s

2025-05-07 20:24:53 (9.29 MB/s) - ‘disk.flag.img.gz’ saved [47534568/47534568]

omarsalazar@DESKTOP-H97NF1C:~$ ls
disk.flag.img.gz
omarsalazar@DESKTOP-H97NF1C:~$ gunzip disk.flag.img.gz
omarsalazar@DESKTOP-H97NF1C:~$ ls
disk.flag.img
omarsalazar@DESKTOP-H97NF1C:~$ mmls disk.flag.img
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)
003:  000:001   0000206848   0000360447   0000153600   Linux Swap / Solaris x86 (0x82)
004:  000:002   0000360448   0000614399   0000253952   Linux (0x83)
omarsalazar@DESKTOP-H97NF1C:~$ fsstat -o 2048 disk.flag.img
FILE SYSTEM INFORMATION
--------------------------------------------
File System Type: Ext4
Volume Name:
Volume ID: 8e023955b4e7dab7e04b7643076ccf0f

Last Written at: 2021-09-29 13:10:02 (CDT)
Last Checked at: 2021-09-29 10:57:16 (CDT)
.
.
.
.
.
.
Group: 12:
  Inode Range: 23617 - 25584
  Block Range: 98305 - 102399
  Layout:
    Data bitmap: 271 - 271
    Inode bitmap: 284 - 284
    Inode Table: 6189 - 6680
    Data Blocks: 6681 - 102399
  Free Inodes: 1968 (100%)
  Free Blocks: 4095 (99%)
  Total Directories: 0
  
omarsalazar@DESKTOP-H97NF1C:~$ fls -f ext4 -o 2048 -r disk.flag.img
d/d 11: lost+found
r/r 12: ldlinux.sys
r/r 13: ldlinux.c32
r/r 15: config-virt
r/r 16: vmlinuz-virt
r/r 17: initramfs-virt
l/l 18: boot
r/r 20: libutil.c32
r/r 19: extlinux.conf
r/r 21: libcom32.c32
r/r 22: mboot.c32
r/r 23: menu.c32
r/r 14: System.map-virt
r/r 24: vesamenu.c32
V/V 25585:      $OrphanFiles

omarsalazar@DESKTOP-H97NF1C:~$ fls -f ext4 -o 360448 -r disk.flag.img
d/d 451:        home
d/d 11: lost+found
d/d 12: boot
d/d 1985:       etc
+ r/r 23:       group
+ r/r 24:       group-
+ r/r 25:       shadow
+ r/r 26:       shadow-
+ r/r 27:       passwd
+ r/r 28:       passwd-
+ r/r 29:       hosts
.
.
.
.
.
.
.
+ l/l * 867(realloc):   .apk.8daa2bfebb2ec3d1b662a69a8a2b9fa01bf4bb1549031d86
+ l/l 862:      fsck.ext3
+ r/r * 694(realloc):   .apk.b55f52d6d50c4d3b3308783c421b4f836b24585f35b4c8bc
+ r/r * 696(realloc):   .apk.d1e6a1a00216b3f77818b33f76a1028c2c2d9f8d1dda23da
+ r/r * 700(realloc):   .apk.db9c8e8e2411ff40c53fb3ab28055ca9ae14a65722eb2e25
d/d 1992:       media
+ d/d 457:      cdrom
+ d/d 458:      floppy
+ d/d 459:      usb
d/d 1993:       mnt
d/d 1994:       opt
d/d 1995:       root
+ r/r 2363:     .ash_history
+ d/d 3981:     my_folder
++ r/r * 2082(realloc): flag.txt
++ r/r 2371:    flag.uni.txt
d/d 1996:       run
d/d 1997:       srv
d/d 1998:       sys
d/d 2358:       swap
V/V 31745:      $OrphanFiles

omarsalazar@DESKTOP-H97NF1C:~$ icat -f ext4 -o 360448 disk.flag.img 2082
            3.449677            13.056403
omarsalazar@DESKTOP-H97NF1C:~$ icat -f ext4 -o 360448 disk.flag.img 2371
picoCTF{by73_5urf3r_adac6cb4}
omarsalazar@DESKTOP-H97NF1C:~$

flag: picoCTF{by73_5urf3r_adac6cb4}
```
