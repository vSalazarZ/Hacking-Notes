## Descripción 
Connect to this PostgreSQL server and find the flag!`psql -h saturn.picoctf.net -p 61192 -U postgres pico`Password is `postgres`

Hint:
1. What does a SQL database contain?
## Solución 1

Nos conectamos a una base de datos SQL, una vez dentro usé help para ver que obtenía y puse \h para ver los comandos de sql, después con \l listé las bases de datos y había una llamada pico, con \c pico nos metimos dentro de esa base de datos y sacamos la bandera con un simple select.

```
omarsalazar@DESKTOP-H97NF1C:~$ psql -h saturn.picoctf.net -p 63514 -U postgres pico
Password for user postgres:
psql (16.8 (Ubuntu 16.8-0ubuntu0.24.04.1), server 15.2 (Debian 15.2-1.pgdg110+1))
Type "help" for help.

pico=# help
You are using psql, the command-line interface to PostgreSQL.
Type:  \copyright for distribution terms
       \h for help with SQL commands
       \? for help with psql commands
       \g or terminate with semicolon to execute query
       \q to quit
pico=# \h
pico=# \l
pico=# \c pico
psql (16.8 (Ubuntu 16.8-0ubuntu0.24.04.1), server 15.2 (Debian 15.2-1.pgdg110+1))
You are now connected to database "pico" as user "postgres".
pico=# \dt
         List of relations
 Schema | Name  | Type  |  Owner
--------+-------+-------+----------
 public | flags | table | postgres
(1 row)

pico=# select * from flags;
 id | firstname | lastname  |                address
----+-----------+-----------+----------------------------------------
  1 | Luke      | Skywalker | picoCTF{L3arN_S0m3_5qL_t0d4Y_31fd14c0}
  2 | Leia      | Organa    | Alderaan
  3 | Han       | Solo      | Corellia
(3 rows)

pico=#

flag: picoCTF{L3arN_S0m3_5qL_t0d4Y_31fd14c0}
```
