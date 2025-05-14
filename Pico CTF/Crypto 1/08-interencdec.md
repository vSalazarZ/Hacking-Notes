## Descripción 
Can you get the real meaning from this file.Download the file [here](https://artifacts.picoctf.net/c_titan/110/enc_flag).

Hint:
1. Engaging in various decoding processes is of utmost importance
## Solución 1

Descargamos el archivo encriptado, después lo observamos y vemos que es un código base64, lo decodificamos y nos da otro en base 64, lo desencriptamos de nuevo y después obtenemos uno en codificado cipher, usamos el desencriptado de cipher y obtenemos la bandera

```
Primera cadena: YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6ZzJhMnd6TW1zeWZRPT0nCg==

Segunda cadena: d3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzg2a2wzMmsyfQ==

Tercera cadena: wpjvJAM{jhlzhy_k3jy9wa3k_86kl32k2}

Usando cipher decoder: wpjvJAM{jhlzhy_k3jy9wa3k_86kl32k2}

flag: picoCTF{caesar_d3cr9pt3d_86de32d2}
```

## Referencias
1. https://cryptii.com/pipes/caesar-cipher
2. https://gchq.github.io/CyberChef/