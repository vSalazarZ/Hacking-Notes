## Descripción 
The one time pad can be cryptographically secure, but not when you know the key. Can you solve this? We've given you the encrypted flag, key, and a table to help `UFJKXQZQUNB` with the key of `SOLVECRYPTO`. Can you use this [table](https://jupiter.challenges.picoctf.org/static/1fd21547c154c678d2dab145c29f1d79/table.txt) to solve it?.

Hint:
1. Submit your answer in our flag format. For example, if your answer was 'hello', you would submit 'picoCTF{HELLO}' as the flag.
2. Please use all caps for the message.
## Solución 1

Se proporciona un mensaje cifrado, investigando nos damos cuenta que es con el cifrado Vigenere nuestro mensaje a decodificar es UFJKXQZQUNB  y su llave SOLVECRYPTO. Utilizando la tabla de Vigenere o un decodificador, se descifra el mensaje como CRYPTOISFUN, obteniendo así la bandera del ejercicio

```
Usando Vigenere Cipher

Vigenere ciphertext: UFJKXQZQUNB 

Key: SOLVECRYPTO

Output: CRYPTOISFUN

flag: picoCTF{CRYPTOISFUN}
```

## Referencias
1. https://www.dcode.fr/vigenere-cipher
2. https://es.wikipedia.org/wiki/Cifrado_de_Vigen%C3%A8re