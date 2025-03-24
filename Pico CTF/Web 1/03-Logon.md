## Descripción 
The factory is hiding things from all of its users. Can you login as Joe and find what they've been looking at? `https://jupiter.challenges.picoctf.org/problem/44573/` ([link](https://jupiter.challenges.picoctf.org/problem/44573/)) or http://jupiter.challenges.picoctf.org:44573

Hint:
1. Hmm it doesn't seem to check anyone's password, except for Joe's?
## Solución 1

Inspeccionamos la página  veemos como funciona la página y en la sección de aplicación vemos que en las cookies nos da un false al momento de querer obtener la flag, modificamos las cookies y cambiamos el false por "True" y recargamos la página y obtenemos la flag
```
flag: picoCTF{th3_c0nsp1r4cy_l1v3s_0c98aacc}
```
