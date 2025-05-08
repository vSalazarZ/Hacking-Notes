## Descripción 
Download this disk image, find the key and log into the remote machine.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.
- [Download disk image](https://artifacts.picoctf.net/c/71/disk.img.gz)
- Remote machine: `ssh -i key_file -p 59588 ctf-player@saturn.picoctf.net`

## Solución 1



```
omarsalazar@DESKTOP-H97NF1C:~$ wget https://artifacts.picoctf.net/c/71/disk.img.gz
--2025-05-07 13:24:45--  https://artifacts.picoctf.net/c/71/disk.img.gz
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.165.190.112, 3.165.190.16, 3.165.190.103, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.165.190.112|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 48132743 (46M) [application/octet-stream]
Saving to: ‘disk.img.gz’

disk.img.gz         100%[==================>]  45.90M  10.2MB/s    in 5.4s

2025-05-07 13:24:52 (8.54 MB/s) - ‘disk.img.gz’ saved [48132743/48132743]

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
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)
003:  000:001   0000206848   0000471039   0000264192   Linux (0x83)
omarsalazar@DESKTOP-H97NF1C:~$ fls disk.img -o 206848
d/d 458:        home
d/d 11: lost+found
d/d 12: boot
d/d 13: etc
d/d 79: proc
d/d 80: dev
d/d 81: tmp
d/d 82: lib
d/d 85: var
d/d 94: usr
d/d 104:        bin
d/d 118:        sbin
d/d 464:        media
d/d 468:        mnt
d/d 469:        opt
d/d 470:        root
d/d 471:        run
d/d 473:        srv
d/d 474:        sys
V/V 33049:      $OrphanFiles
omarsalazar@DESKTOP-H97NF1C:~$ fls disk.img -o 206848 470
r/r 2344:       .ash_history
d/d 3916:       .ssh
omarsalazar@DESKTOP-H97NF1C:~$ fls disk.img -o 206848 3919
omarsalazar@DESKTOP-H97NF1C:~$ fls disk.img -o 206848 3916
r/r 2345:       id_ed25519
r/r 2346:       id_ed25519.pub
omarsalazar@DESKTOP-H97NF1C:~$ icat disk.img o 206848 2345 > key_file
Error stat(ing) image file (raw_open: image "o" - No such file or directory)
omarsalazar@DESKTOP-H97NF1C:~$ icat disk.img -o 206848 2345 > key_file
omarsalazar@DESKTOP-H97NF1C:~$ chmod 600 key_file
omarsalazar@DESKTOP-H97NF1C:~$ ssh -i key_file -p 59588 ctf-player@saturn.picoctf.net
Welcome to Ubuntu 20.04.5 LTS (GNU/Linux 6.5.0-1023-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

ctf-player@challenge:~$ cat flag.txt
picoCTF{k3y_5l3u7h_af277f77}ctf-player@challenge:~$

flag: picoCTF{k3y_5l3u7h_af277f77}
```
