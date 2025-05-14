## Descripción 
Theres tapping coming in from the wires. What's it saying `nc jupiter.challenges.picoctf.org 21610`.

Hint:
1. What kind of encoding uses dashes and dots?
2. The flag is in the format PICOCTF{}
## Solución 1

Nos proporcionan unn servidor, nos conectamos y nos dan un código con puntos y guiones. En las pistas nos dice que que tipo de codificación usa puntos y guiones, es el código Morse, entonces usamos un decodificador de Código Morse y ponemos este código y obtenemos la bandera

```
Input: .--. .. -.-. --- -.-. - ..-.  -- ----- .-. ... ...-- -.-. ----- -.. ...-- .---- ... ..-. ..- -. ...-- ----. ----- ..--- ----- .---- ----. ..... .---- ----. 

Recipe: Decode Morse Code

Output: picoctfm0rs3c0d31sfun3902019519

flag: picoctf{m0rs3c0d31sfun3902019519}
```

## Referencias
1. https://cryptii.com/pipes/morse-code-translator