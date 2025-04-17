## Descripción 
Why search for the flag when I can make a bookmarklet to print it for me?
Browse [here](http://titan.picoctf.net:61058/), and find the flag!

Hint:
1. A bookmarklet is a bookmark that runs JavaScript instead of loading a webpage.
2. What happens when you click a bookmarklet?
3. Web browsers have other ways to run JavaScript too.
## Solución 1

Nos metemos a la página que se nos presenta, nos da un código en javascript así que simplemente buscamos un javascript compiler y metemos el código y obtenemos así la bandera.

```
JavaScript Online Compiler

Input:         javascript:(function() {
            var encryptedFlag = "àÒÆÞ¦È¬ëÙ£ÖÓÚåÛÑ¢ÕÓÔÅÐÙí";
            var key = "picoctf";
            var decryptedFlag = "";
            for (var i = 0; i < encryptedFlag.length; i++) {
                decryptedFlag += String.fromCharCode((encryptedFlag.charCodeAt(i) - key.charCodeAt(i % key.length) + 256) % 256);
            }
            alert(decryptedFlag);
        })();

Output: picoCTF{p@g3_turn3r_1d1ba7e0}

=== Code Execution Successful ===

flag: picoCTF{p@g3_turn3r_1d1ba7e0}
```

## Referencias
https://www.programiz.com/javascript/online-compiler/