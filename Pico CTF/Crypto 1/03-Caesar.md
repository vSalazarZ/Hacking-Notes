## Descripción 
Decrypt this [message](https://jupiter.challenges.picoctf.org/static/6385b895dcb30c74dbd1f0ea271e3563/ciphertext).

Hint:
1. caesar cipher [tutorial](https://learncryptography.com/classical-encryption/caesar-cipher)
## Solución 1

Se dio un mensaje cifrado usando el cifrado César. Investigamos como funciona con el contenido proporcionado, después de saber como funciona usamos un decodificador para resolver el problema. Metemos el cifrado de la bandera al decodificador cryptii y vamos moviendo el shift hasta que encontremos una cadena que tenga sentido, con shift 1 encontramos nuestra bandera, simplemente acomodamos el contenido dentro de las llaves y obtenemos la bandera del ejercicio 

```
Cryptii

VIEW-Ciphertext: picoCTF{dspttjohuifsvcjdpoabrkttds}

Decode-Caesar cipher: Shift --> 1

View-Plaintext: picoCTF{crossingtherubiconzaqjsscr}

flag: picoCTF{crossingtherubiconzaqjsscr}
```

## Referencias
1. https://privacycanada.net/classical-encryption/caesar-cipher/
2. https://cryptii.com/pipes/caesar-cipher