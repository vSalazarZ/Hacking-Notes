## Descripción 
Can you get the flag?

Additional details will be available after launching your challenge instance.
Go to this [website](http://saturn.picoctf.net:59111/) and see what you can discover.

Hint:
1. What is the web inspector in web browsers?
## Solución 1

Nos metemos a la página y en la pista nos dice que usemos el inspector web, nos metemos al código fuente de la página y en la parte de abajo nos da la bandera directamente

```
|   |
|---|
|<!DOCTYPE html>|
||<html lang="en">|
||<head>|
||<meta charset="UTF-8">|
||<meta name="viewport" content="width=device-width, initial-scale=1.0">|
||<meta http-equiv="X-UA-Compatible" content="ie=edge">|
||<title>On Histiaeus</title>|
||</head>|
||<body>|
||<h1>On Histiaeus</h1>|
||<p>However, according to Herodotus, Histiaeus was unhappy having to stay in|
||Susa, and made plans to return to his position as King of Miletus by|
||instigating a revolt in Ionia. In 499 BC, he shaved the head of his|
||most trusted slave, tattooed a message on his head, and then waited for|
||his hair to grow back. The slave was then sent to Aristagoras, who was|
||instructed to shave the slave's head again and read the message, which|
||told him to revolt against the Persians.</p>|
||<br>|
||<p> Source: Wikipedia on Histiaeus </p>|
||<!--picoCTF{1n5p3t0r_0f_h7ml_fd5d57bd}-->|
||</body>|
||</html>|

flag: picoCTF{1n5p3t0r_0f_h7ml_fd5d57bd}
```
