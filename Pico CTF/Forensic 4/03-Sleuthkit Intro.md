## Descripción 
Download the disk image and use `mmls` on it to find the size of the Linux partition. Connect to the remote checker service to check your answer and get the flag.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.[Download disk image](https://artifacts.picoctf.net/c/164/disk.img.gz)
Access checker program: `nc saturn.picoctf.net 57446`
## Solución 1

Descargamos y descomprimimos un archivo de imagen de disco. Luego, usamos mmls para ver la partición Linux, para obtener el tamaño de la partición, después nos conectamos con nc al servidodr dado, el cual nos va pedir el tamaño de la partición, ponemos el tamaño y obtenemos la bandera 

```
omarsalazar@DESKTOP-H97NF1C:~$ wget https://artifacts.picoctf.net/c/164/disk.img.gz
--2025-05-07 13:13:12--  https://artifacts.picoctf.net/c/164/disk.img.gz
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.165.190.105, 3.165.190.112, 3.165.190.16, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.165.190.105|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 29714372 (28M) [application/octet-stream]
Saving to: ‘disk.img.gz’

disk.img.gz                   100%[=================================================>]  28.34M  9.38MB/s    in 3.0s

2025-05-07 13:13:18 (9.38 MB/s) - ‘disk.img.gz’ saved [29714372/29714372]

omarsalazar@DESKTOP-H97NF1C:~$ ls
disk.img.gz
omarsalazar@DESKTOP-H97NF1C:~$ gunzip disk.img.gz
omarsalazar@DESKTOP-H97NF1C:~$ ls
disk.img
omarsalazar@DESKTOP-H97NF1C:~$ mmls disk.img
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000204799   0000202752   Linux (0x83)
omarsalazar@DESKTOP-H97NF1C:~$ nc saturn.picoctf.net 57446
What is the size of the Linux partition in the given disk image?
Length in sectors: 202752
202752
Great work!
picoCTF{mm15_f7w!}
^Z
[3]+  Stopped                 nc saturn.picoctf.net 57446
omarsalazar@DESKTOP-H97NF1C:~$

flag: picoCTF{mm15_f7w!}

```
