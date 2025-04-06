## Descripción 
The flag is somewhere on this web application not necessarily on the website. Find it.

Additional details will be available after launching your challenge instance.

## Solución 1

Ingresamos a la página y nos metemos a código fuente para ver si encontramos la bandera, no encontramos nada, después nos metemos a la página pero ingresando /robots.txt y vemos que hay como cadenas codificadas, las metemos al cyberchef y nos indica que es js/myfile.txt, ingresamos y nos da la bandera

```
Ingresamos con robots.txt: http://saturn.picoctf.net:54141/robots.txt

User-agent *
Disallow: /cgi-bin/
Think you have seen your flag or want to keep looking.

ZmxhZzEudHh0;anMvbXlmaW
anMvbXlmaWxlLnR4dA==
svssshjweuiwl;oiho.bsvdaslejg
Disallow: /wp-admin/

Cyberchef: 

Input: anMvbXlmaWxlLnR4dA==

Recipe: from Base64

Output: js/myfile.txt

ingresamos: http://saturn.picoctf.net:54141/js/myfile.txt

flag: picoCTF{Who_D03sN7_L1k5_90B0T5_22ce1f22}
```
## Referencias
https://gchq.github.io/CyberChef/#recipe=From_Base64('A-Za-z0-9%2B/%3D',true,false)&input=YW5NdmJYbG1hV3hsTG5SNGRBPT0