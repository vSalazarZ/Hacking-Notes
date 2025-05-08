## Descripción 
Use `srch_strings` from the sleuthkit and some terminal-fu to find a flag in this disk image: [dds1-alpine.flag.img.gz](https://mercury.picoctf.net/static/920731987787c93839776ce457d5ecd6/dds1-alpine.flag.img.gz)

Hint:
1. Have you ever used `file` to determine what a file was?
2. Relevant terminal-fu in picoGym: https://play.picoctf.org/practice/challenge/85
3. Mastering this terminal-fu would enable you to find the flag in a single command: https://play.picoctf.org/practice/challenge/48
4. Using your own computer, you could use qemu to boot from this disk!
## Solución 1

Descargamos el archivo que se nos da, observamos que está comprimido con .gz así que descomprimimos usando gunzip, tenemos el archivo descomprimido y usamos el comando que se nos da en el problema inicial que es `srch_strings`, nos salen muchos caracteres, así que filtramos con un grep pico y obtenemos la bandera

```
omarsalazar@DESKTOP-H97NF1C:~$ wget https://mercury.picoctf.net/static/920731987787c93839776ce457d5ecd6/dds1-alpine.flag.img.gz
--2025-05-07 13:06:40--  https://mercury.picoctf.net/static/920731987787c93839776ce457d5ecd6/dds1-alpine.flag.img.gz
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 29768910 (28M) [application/octet-stream]
Saving to: ‘dds1-alpine.flag.img.gz’

dds1-alpine.flag.img.gz       100%[=================================================>]  28.39M  6.01MB/s    in 5.0s

2025-05-07 13:06:47 (5.65 MB/s) - ‘dds1-alpine.flag.img.gz’ saved [29768910/29768910]

omarsalazar@DESKTOP-H97NF1C:~$ ls
dds1-alpine.flag.img.gz
omarsalazar@DESKTOP-H97NF1C:~$ gunzip dds1-alpine.flag.img.gz
omarsalazar@DESKTOP-H97NF1C:~$ ls
dds1-alpine.flag.img
omarsalazar@DESKTOP-H97NF1C:~$ srch_strings dds1-alpine.flag.img | grep pico
ffffffff81399ccf t pirq_pico_get
ffffffff81399cee t pirq_pico_set
ffffffff820adb46 t pico_router_probe
  SAY picoCTF{f0r3ns1c4t0r_n30phyt3_564ff1a0}
omarsalazar@DESKTOP-H97NF1C:~$

flag: picoCTF{f0r3ns1c4t0r_n30phyt3_564ff1a0}
```
