## Descripción 
If you want to hash with the best, beat this test!
Additional details will be available after launching your challenge instance.
If you want to hash with the best, beat this test!`nc saturn.picoctf.net 63658`

Hint:
1. You can use a commandline tool or web app to hash text
2. Press Ctrl and c on your keyboard to close your connection and return to the command prompt.
## Solución 1

Nos conectamos al netcat `nc saturn.picoctf.net 63658` y nos dice el ejercicio que usemos un md5 hash generator para ciertas palabras que nos dan para descifrar la bandera, sacamos los hash de las 3 palabras y obtenemos la bandera

```
omarsalazar@DESKTOP-H97NF1C:~$ nc saturn.picoctf.net 64236
Please md5 hash the text between quotes, excluding the quotes: 'musicals'
Answer:
fb93d71bbad4b9be2e167c0914bbd83e
fb93d71bbad4b9be2e167c0914bbd83e
Correct.
Please md5 hash the text between quotes, excluding the quotes: 'bad dogs'
Answer:
60cc96ffdc458c98395d6e7b6878a6e9
60cc96ffdc458c98395d6e7b6878a6e9
Correct.
Please md5 hash the text between quotes, excluding the quotes: 'Michelangelo'
Answer:
0d46a3ff4160862bb8329524b99da972
0d46a3ff4160862bb8329524b99da972
Correct.
picoCTF{4ppl1c4710n_r3c31v3d_3eb82b73}
omarsalazar@DESKTOP-H97NF1C:~$

flag: picoCTF{4ppl1c4710n_r3c31v3d_3eb82b73}
```

## Referencias
https://www.md5hashgenerator.com/