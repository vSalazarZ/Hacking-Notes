## Descripción 
Can you get the flag?

Additional details will be available after launching your challenge instance.
Go to this [website](http://saturn.picoctf.net:56916/) and see what you can discover.

Hint:
1. Do you know how to modify cookies?
## Solución 1

La pista nos dice que si sabemos modificar cookies, si sabemos, entonces nos metemos a la página y le damos en continuar como invitado y nos dice que no podemos ingresar, miramos la cookie y en value está en "0" la cambiamos a "1" y recargamos página y nos deja entrar para poder ver la bandera en ella

```
--continue as a guest
--We apologize, but we have no guest services at the moment.

Cookie: value "0"
Cookie: value "1"

flag: picoCTF{gr4d3_A_c00k13_0d351e23}
```
