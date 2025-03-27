## Descripción 
There is some interesting information hidden around this site [http://mercury.picoctf.net:55079/](http://mercury.picoctf.net:55079/). Can you find it?

Hint:
1. You should have enough hints to find the files, don't run a brute forcer.
## Solución 1

Vamos a meternos al código fuente para buscar la bandera y vamos siguiendo los pasos y la información que se nos proporciona en el mismo código

```
1. Al ver el código fuente vemos que nos da la 1ra hasta abajo: 
   Here's the first part of the flag: picoCTF{t

2.Después nos metemos al mycss.css y hasta abajo nos da la 2da parte: 
  CSS makes the page look nice, and yes, it also has part of the flag: h4ts_4_l0

3. Después nos metemos al myjs.js y hasta abajo nos dice: /* How can I keep Google   from indexing my website? */, así que usamos el /robots.txt y nos da: 
  User-agent: *
  Disallow: /index.html
  # Part 3: t_0f_pl4c
  # I think this is an apache server... can you Access the next flag?

4.Para esta parte usamos la información del anterior que nos dice que es un          servidor apache, que como ingresamos y usamos: /.htaccess y nos da lo siguente:
  |# Part 4: 3s_2_lO0k|
  ||# I love making websites on my Mac, I can Store a lot of information there.|

5.Por último nos dice que donde se guarda la información en mac y es en     /.DS_Store, guarda archivos ocultos que macOS crea en cada carpeta para guardar   configuraciones, ponemos esto y nos da la última parte: 
||Congrats! You completed the scavenger hunt. Part 5: _74cceb07}

flag por partes: picoCTF{t --- h4ts_4_l0 --- t_0f_pl4c --- 3s_2_lO0k --- _74cceb07}

Simplemente juntamos las partes y tenemos la bandera completa

flag conjunta: picoCTF{th4ts_4_l0t_0f_pl4c3s_2_lO0k_74cceb07}
```
