## Descripción 
I found this cipher in an old book. Can you figure out what it says? Connect with `nc jupiter.challenges.picoctf.org 5726`.

Hint:
1. There are tools that make this easy.
2. Perhaps looking at history will help
## Solución 1

Ingresamos al servidor que se nos da en el ejercicio y nos proporciona un texto encriptado con cipher, usamos un decodificador para saber que dice el texto, lo hacemos y nos damos cuenta que las llaves de decodificación tienen una escritura parecida a "flag", entonces usamos flag de llave para ver si obtenemos la bandera y así es, en el texto se ve la bandera si usamos "flag" como key

```
flag: picoCTF{b311a50_0r_v1gn3r3_c1ph3r6fe60eaa}
```

## Referencias
1. https://cryptii.com/pipes/caesar-cipher