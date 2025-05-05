## Descripción 
We found this [file](https://mercury.picoctf.net/static/d0129ad98ba9258ab59e7700a1b18c14/tunn3l_v1s10n). Recover the flag.

Hint:
1. Weird that it won't display right...
## Solución 1

Se descargó un archivo, se identificó como una imagen BMP oculta, se renombró con la extensión correcta y modificamos con hexedit el contenido para corregirlo a su formato BMP, una vez corregido abrimos el archivo y nos abre una imagen con la bandera en ella

```
omarsalazar@DESKTOP-H97NF1C:~$ wget https://mercury.picoctf.net/static/d0129ad98ba9258ab59e7700a1b18c14/tunn3l_v1s10n
--2025-05-05 12:05:04--  https://mercury.picoctf.net/static/d0129ad98ba9258ab59e7700a1b18c14/tunn3l_v1s10n
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2893454 (2.8M) [application/octet-stream]
Saving to: ‘tunn3l_v1s10n’

tunn3l_v1s10n                 100%[=================================================>]   2.76M  2.82MB/s    in 1.0s

2025-05-05 12:05:06 (2.82 MB/s) - ‘tunn3l_v1s10n’ saved [2893454/2893454]

omarsalazar@DESKTOP-H97NF1C:~$ file tunn3l_v1s10n
tunn3l_v1s10n: data
omarsalazar@DESKTOP-H97NF1C:~$ xxd tunn3l_v1s10n | head
00000000: 424d 8e26 2c00 0000 0000 bad0 0000 bad0  BM.&,...........
00000010: 0000 6e04 0000 3201 0000 0100 1800 0000  ..n...2.........
00000020: 0000 5826 2c00 2516 0000 2516 0000 0000  ..X&,.%...%.....
00000030: 0000 0000 0000 231a 1727 1e1b 2920 1d2a  ......#..'..) .*
00000040: 211e 261d 1a31 2825 352c 2933 2a27 382f  !.&..1(%5,)3*'8/
00000050: 2c2f 2623 332a 262d 2420 3b32 2e32 2925  ,/&#3*&-$ ;2.2)%
00000060: 3027 2333 2a26 382c 2836 2b27 392d 2b2f  0'#3*&8,(6+'9-+/
00000070: 2623 1d12 0e23 1711 2916 0e55 3d31 9776  &#...#..)..U=1.v
00000080: 668b 6652 996d 569e 7058 9e6f 549c 6f54  f.fR.mV.pX.oT.oT
00000090: ab7e 63ba 8c6d bd8a 69c8 9771 c193 71c1  .~c..m..i..q..q.
omarsalazar@DESKTOP-H97NF1C:~$ hexedit tunn3l_v1s10n.bmp
hexedit: tunn3l_v1s10n.bmp: Not a file.
omarsalazar@DESKTOP-H97NF1C:~$ mv tunn3l_v1s10n tunn3l_v1s10n.bmp
omarsalazar@DESKTOP-H97NF1C:~$ hexedit tunn3l_v1s10n.bmp

omarsalazar@DESKTOP-H97NF1C:~$ open tunn3l_v1s10n.bmp

flag: picoCTF{qu1t3_a_v13w_2020}
```

## Referencias 
1. https://en.wikipedia.org/wiki/List_of_file_signatures
2. https://en.wikipedia.org/wiki/BMP_file_format