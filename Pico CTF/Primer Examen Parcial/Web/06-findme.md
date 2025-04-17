## Descripción 
Help us test the form by submiting the username as `test` and password as `test!`
The website running [here](http://saturn.picoctf.net:50745/).

Hint:
1. any redirections?
## Solución 1

Nos vamos a la página proporcionada, ingresamos datos para login y nos dice que hay que poner test y test! como user y password, lo ingresamos y nos ingresa a otro login diferente, esta vez para ingresar una bandera pero no hace nada. En las pistas nos dice que si hay redirecciones, así que nos metemos al Burp para ver si tiene redirecciones y efectivamente si tiene, al ingresar a las redirecciones vemos que contienen unas redirecciones unas cadenas en base64, las sacamos y juntamos en cyberchef para decodificarlas y obtenemos la bandera.

```
GET /next-page/id=bF90aGVfd2F5X2EwZmUwNzRmfQ== HTTP/1.1
Host: saturn.picoctf.net:65254
Accept-Language: es-419,es;q=0.9
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/135.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://saturn.picoctf.net:65254/next-page/id=cGljb0NURntwcm94aWVzX2Fs
Accept-Encoding: gzip, deflate, br
Connection: keep-alive

GET /home HTTP/1.1
Host: saturn.picoctf.net:65254
Accept-Language: es-419,es;q=0.9
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/135.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://saturn.picoctf.net:65254/next-page/id=bF90aGVfd2F5X2EwZmUwNzRmfQ==
Accept-Encoding: gzip, deflate, br
Connection: keep-alive

cadena base64: cGljb0NURntwcm94aWVzX2FsbF90aGVfd2F5X2EwZmUwNzRmfQ==
```

Usando cyberchef para decodificar cadena de base64

```
Input: cGljb0NURntwcm94aWVzX2FsbF90aGVfd2F5X2EwZmUwNzRmfQ==

Recipe: From Base64

Output: picoCTF{proxies_all_the_way_a0fe074f}

flag: picoCTF{proxies_all_the_way_a0fe074f}
```

## Referencias
https://gchq.github.io/CyberChef/