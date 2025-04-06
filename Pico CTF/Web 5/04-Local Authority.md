## Descripción 
Can you get the flag?

Additional details will be available after launching your challenge instance.
Go to this [website](http://saturn.picoctf.net:54886/) and see what you can discover.

Hint:
1. How is the password checked on this website?
## Solución 1

Nos metemos a la página y nos logeamos, nos dice que el log in falló, nos metemos al código fuente en esa página y nos fijamos que hay un secuere.js, abrimos el archivo y ahí tenemos un checkpassword con el user y contraseña para logearnos 

```
secure.js

function checkPassword(username, password)
{
  if( username === 'admin' && password === 'strongPassword098765' )
  {
    return true;
  }
  else
  {
    return false;
  }
}

user: admin
password: strongPassword098765

flag: picoCTF{j5_15_7r4n5p4r3n7_05df90c8}
```
