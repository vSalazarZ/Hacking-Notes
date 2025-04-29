## Descripción 
Decode this [message](https://jupiter.challenges.picoctf.org/static/14393e18d98fedbaedbc28896d7ef31a/message.wav) from the moon.

Hint:
1. How did pictures from the moon landing get sent back to Earth?
2. What is the CMU mascot?, that might help select a RX option
## Solución 1

Recibimos un archivo en .mav y tenemos que convertirlo a una forma legible, así que investigamos la primera pista, nos dice que como se enviaron las imágenes de la luna a la tierra, investigamos y vemos que se escondían imágenes usando SSTV, instalamos un convertidor de sstv a la consola y convertimos el .mav a sstv

```
omarsalazar@DESKTOP-H97NF1C:~$ cd 
omarsalazar@DESKTOP-H97NF1C:~$ sstv git clone https://github.com/colaclanth/sstv.git
omarsalazar@DESKTOP-H97NF1C:~$ sudo python3 setup.py install
omarsalazar@DESKTOP-H97NF1C:~$ sstv -d message.wav -o result.png
[sstv] Searching for calibration header... Found!
[sstv] Detected SSTV mode Scottie 1
[sstv] Decoding image...   [######################################################################################] 100%
[sstv] Drawing image data...
[sstv] ...Done!
omarsalazar@DESKTOP-H97NF1C:~$ open result.png

flag: picoCTF{beep_boop_im_in_space}
```

## Referencias
1. https://en.wikipedia.org/wiki/Apollo_11_missing_tapes#:~:text=NASA%20selected%20a%20scan%20converter,split%20it%20into%20two%20branches.
2. https://github.com/colaclanth/sstv