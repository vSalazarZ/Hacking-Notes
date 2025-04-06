## Descripción 
Can you get the flag?
Additional details will be available after launching your challenge instance.
Go to this [website](http://saturn.picoctf.net:57045/) and see what you can discover.

Hint:
1. Is there more code than what the inspector initially shows?
## Solución 1

Inicialmente nos metemos a la página y miramos el código fuente y nos metemos al style.css y script.js y en ambos nos da una parte de la bandera, solo los juntamos y obtenemos la bandera

```
style.css
body {
  background-color: lightblue;
}

/*  picoCTF{1nclu51v17y_1of2_  */

script.js
function greetings()
{
  alert("This code is in a separate file!");
}

//  f7w_2of2_df589022}

flag: picoCTF{1nclu51v17y_1of2_f7w_2of2_df589022}
```
