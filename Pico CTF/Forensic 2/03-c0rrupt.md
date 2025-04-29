## Descripción 
We found this [file](https://jupiter.challenges.picoctf.org/static/ab30fcb7d47364b4190a7d3d40edb551/mystery). Recover the flag.

Hint:
1. Try fixing the file header
## Solución 1

Descargamos el archivo mystery de pico y vimos que estaba dañado. Corregimos su formato hexadecimal con xxd y hexedit, ajustando el encabezado y los chunks para hacerlo un archivo PNG válido. Analizamos el contenido para asegurarnos de que los datos estaban en el orden correcto. Finalmente, abrimos la imagen usando la consola 

```
omarsalazar@DESKTOP-H97NF1C:~$ xxd mystery | head
00000000: 8965 4e34 0d0a b0aa 0000 000d 4322 4452  .eN4........C"DR
00000010: 0000 066a 0000 0447 0802 0000 007c 8bab  ...j...G.....|..
00000020: 7800 0000 0173 5247 4200 aece 1ce9 0000  x....sRGB.......
00000030: 0004 6741 4d41 0000 b18f 0bfc 6105 0000  ..gAMA......a...
00000040: 0009 7048 5973 aa00 1625 0000 1625 0149  ..pHYs...%...%.I
00000050: 5224 f0aa aaff a5ab 4445 5478 5eec bd3f  R$......DETx^..?
00000060: 8e64 cd71 bd2d 8b20 2080 9041 8302 08d0  .d.q.-.  ..A....
00000070: f9ed 40a0 f36e 407b 9023 8f1e d720 8b3e  ..@..n@{.#... .>
00000080: b7c1 0d70 0374 b503 ae41 6bf8 bea8 fbdc  ...p.t...Ak.....
00000090: 3e7d 2a22 336f de5b 55dd 3d3d f920 9188  >}*"3o.[U.==. ..
omarsalazar@DESKTOP-H97NF1C:~$ hexeditor mystery
omarsalazar@DESKTOP-H97NF1C:~$ open mystery
Warning: unknown mime-type for "mystery" -- using "application/octet-stream"
Error: no "view" mailcap rules found for type "application/octet-stream"
omarsalazar@DESKTOP-H97NF1C:~$ hexedit mystery
omarsalazar@DESKTOP-H97NF1C:~$ file mystery
mystery: PNG image data, 1642 x 1095, 8-bit/color RGB, non-interlaced
omarsalazar@DESKTOP-H97NF1C:~$ open mystery
Warning: unknown mime-type for "mystery" -- using "application/octet-stream"
Error: no "view" mailcap rules found for type "application/octet-stream"
omarsalazar@DESKTOP-H97NF1C:~$ hexedit mystery
omarsalazar@DESKTOP-H97NF1C:~$ hexedit mystery
omarsalazar@DESKTOP-H97NF1C:~$ file mystery
mystery: PNG image data, 1642 x 1095, 8-bit/color RGB, non-interlaced
omarsalazar@DESKTOP-H97NF1C:~$ hexedit mystery
omarsalazar@DESKTOP-H97NF1C:~$ file mystery
mystery: PNG image data, 1642 x 1095, 8-bit/color RGB, non-interlaced
omarsalazar@DESKTOP-H97NF1C:~$ xdg-open imagen.png

flag: picoCTF{c0rrupt10n_1847995}
```

## Referencias
https://en.wikipedia.org/wiki/PNG