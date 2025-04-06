## Descripción 
I don't like scrolling down to read the code of my website, so I've squished it. As a bonus, my pages load faster!

Additional details will be available after launching your challenge instance.

Hint:
1. Try CTRL+U / ⌘+U in your browser to view the page source. You can also add 'view-source:' before the URL, or try `curl <URL>` in your shell.
2. Minification reduces the size of code, but does not change its functionality.
3. What tools do developers use when working on a website? Many text editors and browsers include formatting.

Hay varias soluciones para este problema lo único que hay que hacer es buscar la bandera en el código fuente, pero el código fuente está en una sola linea por lo que hay que hacer scroll hasta encontrarla 

## Solución 1

Usando consola linux
Simplemente usamos un comando curl + página + grep pico para filtrar esa palabra en el código fuente

```
vSalazarZ-picoctf@webshell:~$ curl http://titan.picoctf.net:52445/ | grep picoCTF
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1352  100  1352    0     0  17206      0 --:--:-- --:--:-- --:--:-- 17333
<!doctype html><html lang="en"><head><meta charset="utf-8"><meta name="viewport" content="width=device-width,initial-scale=1"><title>picoCTF - picoGym | Unminify Challenge</title><link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png"><style>body{font-family:"Lucida Console",Monaco,monospace}h1,p{color:#000}</style></head><body class="picoctf{}" style="margin:0"><div class="picoctf{}" style="margin:0;padding:0;background-color:#757575;display:auto;height:40%"><a class="picoctf{}" href="/"><img src="picoctf-logo-horizontal-white.svg" alt="picoCTF logo" style="display:inline-block;width:160px;height:90px;padding-left:30px"></a></div><center><br class="picoctf{}"><br class="picoctf{}"><div class="picoctf{}" style="padding-top:30px;border-radius:3%;box-shadow:0 5px 10px #0000004d;width:50%;align-self:center"><img class="picoctf{}" src="hero.svg" alt="flag art" style="width:150px;height:150px"><div class="picoctf{}" style="width:85%"><h2 class="picoctf{}">Welcome to my flag distribution website!</h2><div class="picoctf{}" style="width:70%"><p class="picoctf{}">If you're reading this, your browser has succesfully received the flag.</p><p class="picoCTF{pr3tty_c0d3_622b2c88}"></p><p class="picoctf{}">I just deliver flags, I don't know how to read them...</p></div></div><br class="picoctf{}"></div></center></body></html>
vSalazarZ-picoctf@webshell:~$ 

No se ve aquí en este texto pero en el webshell se marcan en color la palabra picoCTF y solo son 3, es fácil identificar, la bandera es: 

flag: picoCTF{pr3tty_c0d3_622b2c88}
```

## Solución 2

En esta solución usaremos un método más fácil, nos metemos al código fuente y usamos ctrl+f
se nos abre un buscador de palabras y buscamos picoCTF, hay 18 resultados, simplemente vamos buscando rápidamente de uno por uno y en menos de 20 segundos encontramos la bandera

```
CTRL+U en la página
CTRL+F en el código fuente
Filtramos la palabra en la búsqueda "picoCTF" 1/18 ⌃ ⌄ x
Vamos viendo en la búsqueda y encontramos la flag 

flag: picoCTF{pr3tty_c0d3_622b2c88}
```
