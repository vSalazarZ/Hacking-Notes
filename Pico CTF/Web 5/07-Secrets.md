## Descripción 
We have several pages hidden. Can you find the one with the flag?

Additional details will be available after launching your challenge instance.
The website is running [here](http://saturn.picoctf.net:52558/).

Hint:
1. folders folders folders
## Solución 1

Nos metemos a la página y vemos el código fuente y nos fijamos que tiene un secret, nos metemos a la página usando /secret, después nos sale un gif diciendo que vamos por buen camino, nos metemos al código fuente y hay un hidden fil y agregamos el /hidden, por último miramos el código fuente de esa página y hay un superhidden lo agregamos y nos da la bandera

```
http://saturn.picoctf.net:50846/secret/
http://saturn.picoctf.net:50846/secret/hidden/
http://saturn.picoctf.net:50846/secret/hidden/superhidden/

Aparece un texto que dice que "Finally. You found me. But can you see me"

Hacemos ctrl+a y selecciona todo el texto de la página y vemos la bandera seleccionada en la página

flag: picoCTF{succ3ss_@h3n1c@10n_790d2615}
```
