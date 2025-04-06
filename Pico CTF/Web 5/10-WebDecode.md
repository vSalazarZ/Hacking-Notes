## Descripción 
Do you know how to use the web inspector?

Additional details will be available after launching your challenge instance.
Start searching [here](http://titan.picoctf.net:52393/) to find the flag

Hint:
1. Use the web inspector on other files included by the web page.
2. The flag may or may not be encoded
## Solución 1

Usando cyberchef

Nos metemos a la página y vamos inspeccionando, le picamos en *about* e inspeccionamos ahí y vemos una cadena de caracteres que está decodificada, la matemos en un decodificador y nos dá la bandera

```
Cadena: cGljb0NURnt3ZWJfc3VjYzNzc2Z1bGx5X2QzYzBkZWRfMjgzZTYyZmV9

Cyberchef

input: cGljb0NURnt3ZWJfc3VjYzNzc2Z1bGx5X2QzYzBkZWRfMjgzZTYyZmV9

Recipe: Base64

Output: picoCTF{web_succ3ssfully_d3c0ded_283e62fe}

flag: picoCTF{web_succ3ssfully_d3c0ded_283e62fe}
```

## Reference
https://gchq.github.io/CyberChef/#recipe=From_Base64('A-Za-z0-9%2B/%3D',true,false)&input=Y0dsamIwTlVSbnQzWldKZmMzVmpZek56YzJaMWJHeDVYMlF6WXpCa1pXUmZNamd6WlRZeVptVjk