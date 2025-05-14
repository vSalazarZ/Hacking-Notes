## Descripción 
The [numbers](https://jupiter.challenges.picoctf.org/static/f209a32253affb6f547a585649ba4fda/the_numbers.png)... what do they mean?

Hint:
1. The flag is in the format PICOCTF{}
## Solución 1

En este reto se presentó una imagen con una serie de números que ocultaban un mensaje. Al analizarlos e investigando nos damos cuenta que los números son la posición de las letras del alfabeto y hay un decodificador para eso, usamos cyberchef para convertir esa serie de números a texto, obteniendo así la bandera

```
Cyberchef

Input: 16 9 3 15 3 20 6 20 8 5 14 21 13 2 5 18 19 13 1 19 15 14

Recipe: A1Z16 cipher Decode

Output: picoctfthenumbersmason

flag: picoCTF{thenumbersmason}
```

## Referencias
1. https://www.worldometers.info/languages/english-alphabet/#:~:text=The%20English%20alphabet%20consists%20of,%E2%80%9Csmall%20letter%E2%80%9D)%20form.
2. https://gchq.github.io/CyberChef/