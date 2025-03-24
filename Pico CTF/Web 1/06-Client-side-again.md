## Descripción 
Can you break into this super secure portal? `https://jupiter.challenges.picoctf.org/problem/6353/` ([link](https://jupiter.challenges.picoctf.org/problem/6353/)) or http://jupiter.challenges.picoctf.org:6353

Hint:
1. What is obfuscation?
## Solución 1

El script verifica si la contraseña ingresada coincide con una cadena predefinida ofuscada en el código. Usamos el jsnice para ver el código ofuscado y reconstruimos la bandera 

```
flag: picoCTF{not_this_again_50a029}
```
## Referencias 
http://jsnice.org/