## Descripción 
Download this disk image and find the flag.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.
- [Download compressed disk image](https://artifacts.picoctf.net/c/214/disk.flag.img.gz)

## Solución 1

Descargamos y descomprimimos una imagen de disco, luego exploramos su sistema de archivos del root donde miramos que está la bandera codificada, hallamos un historial de comandos que revelaba el procedimiento de encriptación de la bandera, corremos la operación a la inversa de la encriptación y obtenemos la bandera desencriptada, solo hacemos un cat y vemos el contenido de este archivo 

```
omarsalazar@DESKTOP-H97NF1C:~$ wget https://artifacts.picoctf.net/c/214/disk.flag.img.gz
--2025-05-07 20:42:38--  https://artifacts.picoctf.net/c/214/disk.flag.img.gz
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.100, 3.161.55.61, 3.161.55.26, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.100|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 44360927 (42M) [application/octet-stream]
Saving to: ‘disk.flag.img.gz’

disk.flag.img.gz              100%[=================================================>]  42.31M  10.4MB/s    in 4.2s

2025-05-07 20:42:43 (10.1 MB/s) - ‘disk.flag.img.gz’ saved [44360927/44360927]

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
003:  000:001   0000206848   0000411647   0000204800   Linux Swap / Solaris x86 (0x82)
004:  000:002   0000411648   0000819199   0000407552   Linux (0x83)
omarsalazar@DESKTOP-H97NF1C:~$ fls disk.flag.img -o 411648
d/d 460:        home
d/d 11: lost+found
d/d 12: boot
d/d 13: etc
d/d 81: proc
d/d 82: dev
d/d 83: tmp
d/d 84: lib
d/d 87: var
d/d 96: usr
d/d 106:        bin
d/d 120:        sbin
d/d 466:        media
d/d 470:        mnt
d/d 471:        opt
d/d 472:        root
d/d 473:        run
d/d 475:        srv
d/d 476:        sys
d/d 2041:       swap
V/V 51001:      $OrphanFiles
omarsalazar@DESKTOP-H97NF1C:~$ fls disk.flag.img -o 411648 472
r/r 1875:       .ash_history
r/r * 1876(realloc):    flag.txt
r/r 1782:       flag.txt.enc
omarsalazar@DESKTOP-H97NF1C:~$ icat -f ext4 -o 411648 disk.flag.img 1876
           -0.881573            34.311733
omarsalazar@DESKTOP-H97NF1C:~$ icat -f ext4 -o 411648 disk.flag.img 1782
Salted__S�+%���+�O��k�ђ(A����c��
                                @]ԣ
L�ޢȤ7� ���؎$�'%omarsalazar@DESKTOP-H97NF1C:~$
omarsalazar@DESKTOP-H97NF1C:~$ icat -f ext4 -o 411648 disk.flag.img 1875
touch flag.txt
nano flag.txt
apk get nano
apk --help
apk add nano
nano flag.txt
openssl
openssl aes256 -salt -in flag.txt -out flag.txt.enc -k unbreakablepassword1234567
shred -u flag.txt
ls -al
halt
omarsalazar@DESKTOP-H97NF1C:~$ icat -f ext4 -o 411648 disk.flag.img 1782 > flag.txt.enc
omarsalazar@DESKTOP-H97NF1C:~$ ls
disk.flag.img  flag.txt.enc
omarsalazar@DESKTOP-H97NF1C:~$ openssl aes256 -d -salt -in flag.txt.enc -out flag.txt -k unbreakablepassword1234567
*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
bad decrypt
407774600B7F0000:error:1C800064:Provider routines:ossl_cipher_unpadblock:bad decrypt:../providers/implementations/ciphers/ciphercommon_block.c:124:
omarsalazar@DESKTOP-H97NF1C:~$ ls
disk.flag.img  flag.txt  flag.txt.enc
omarsalazar@DESKTOP-H97NF1C:~$ cat flag.txt
picoCTF{h4un71ng_p457_1d02081e}omarsalazar@DESKTOP-H97NF1C:~$
omarsalazar@DESKTOP-H97NF1C:~$

flag: picoCTF{h4un71ng_p457_1d02081e}
```