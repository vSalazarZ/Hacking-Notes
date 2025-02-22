## Descripción 
Someone's commits seems to be preventing the program from working. Who is it?You can download the challenge files here:
- [challenge.zip](https://artifacts.picoctf.net/c_titan/156/challenge.zip)

Hint:
1. In collaborative projects, many users can make many changes. How can you see the changes within one file?
2. Read the chapter on Git from the picoPrimer [here](https://primer.picoctf.org/#_git_version_control).
3. You can use `python3 <file>.py` to try running the code, though you won't need to for this challenge.
## Solución 1

Con consola linux
Primero descargamos el zip con wget, le damos unzip y en el hint 2 nos manda a una página que nos da unos comandos con git, los usamos para llegar a la flag, usamos git log

```
vSalazarZ-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c_titan/156/challenge.zip
--2025-02-22 04:46:41--  https://artifacts.picoctf.net/c_titan/156/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.18, 3.160.5.42, 3.160.5.93, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.18|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 293739 (287K) [application/octet-stream]
Saving to: 'challenge.zip'

challenge.zip                                              100%[=======================================================================================================================================>] 286.85K  1.85MB/s    in 0.2s    

2025-02-22 04:46:42 (1.85 MB/s) - 'challenge.zip' saved [293739/293739]

vSalazarZ-picoctf@webshell:~$ ls
challenge.zip
vSalazarZ-picoctf@webshell:~$ unzip challenge.zip
Archive:  challenge.zip
   creating: drop-in/
 extracting: drop-in/message.py      
   creating: drop-in/.git/
   creating: drop-in/.git/branches/
  inflating: drop-in/.git/description  
   creating: drop-in/.git/hooks/
  inflating: drop-in/.git/hooks/applypatch-msg.sample  
  inflating: drop-in/.git/hooks/commit-msg.sample  
  inflating: drop-in/.git/hooks/fsmonitor-watchman.sample  
  inflating: drop-in/.git/hooks/post-update.sample  
  inflating: drop-in/.git/hooks/pre-applypatch.sample  
  inflating: drop-in/.git/hooks/pre-commit.sample  
  inflating: drop-in/.git/hooks/pre-merge-commit.sample  
  inflating: drop-in/.git/hooks/pre-push.sample  
  inflating: drop-in/.git/hooks/pre-rebase.sample  
  inflating: drop-in/.git/hooks/pre-receive.sample  
  inflating: drop-in/.git/hooks/prepare-commit-msg.sample  
  inflating: drop-in/.git/hooks/update.sample  
   creating: drop-in/.git/info/
  inflating: drop-in/.git/info/exclude  
   creating: drop-in/.git/refs/
   creating: drop-in/.git/refs/heads/
 extracting: drop-in/.git/refs/heads/master  
   creating: drop-in/.git/refs/tags/
 extracting: drop-in/.git/HEAD       
  inflating: drop-in/.git/config     
   creating: drop-in/.git/objects/
   creating: drop-in/.git/objects/pack/
   creating: drop-in/.git/objects/info/
   creating: drop-in/.git/objects/7d/
 extracting: drop-in/.git/objects/7d/f869a15e76c28afb609fa4dbc059144ad70161  
  inflating: drop-in/.git/index      
 extracting: drop-in/.git/COMMIT_EDITMSG  
   creating: drop-in/.git/logs/
  inflating: drop-in/.git/logs/HEAD  
   creating: drop-in/.git/logs/refs/
   creating: drop-in/.git/logs/refs/heads/
  inflating: drop-in/.git/logs/refs/heads/master  
vSalazarZ-picoctf@webshell:~$ ls
challenge.zip  drop-in
vSalazarZ-picoctf@webshell:~$ cd drop-in/
vSalazarZ-picoctf@webshell:~/drop-in$ ls
message.py
vSalazarZ-picoctf@webshell:~/drop-in$ python message.py
  File "/home/vSalazarZ-picoctf/drop-in/message.py", line 1
    print("Hello, World!"
         ^
SyntaxError: '(' was never closed
vSalazarZ-picoctf@webshell:~/drop-in$ git log

[2]+  Stopped                 git log
vSalazarZ-picoctf@webshell:~/drop-in$ git log

[3]+  Stopped                 git log
vSalazarZ-picoctf@webshell:~/drop-in$ 
```

### Resultado de git log en solución 1

En esta solución solo damos git log y buscamos entre todos los autores que han hecho cambios en el proyecto y los vamos a encontrar hasta abajo

```
 important business work

commit fdb14c072a0f1e483d795aab6371bdb5d4b40c9e
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:01 2024 +0000

    important business work

commit 4edee9486bba6fa754781d02371a8c845df267d0
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:01 2024 +0000

    important business work

commit a6ff118a4f2e4ac926c5e34c581d05ca15c44b69
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:01 2024 +0000

    important business work

commit 9500034198652af0286003cf435c22b769be8c4e
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:01 2024 +0000

    important business work

commit 7d97835ff37464c00cfc2089b2d7e8ea54b6e13f
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:01 2024 +0000

    important business work

commit 0351e0474493168ca76441c24630c17554fd09ca
Author: picoCTF{@sk_th3_1nt3rn_d2d29f22} <ops@picoctf.com>
Date:   Tue Mar 12 00:07:01 2024 +0000

    optimize file size of prod code

commit c9e851509190f5887e91339ee18087e3e77ebfda
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:01 2024 +0000

    create top secret project

flag: picoCTF{@sk_th3_1nt3rn_d2d29f22}
```

## Solución 2

En esta solución 2 en lugar de buscar en toda la lista nomas hacemos un grep a picoCTF y nos da solo lo que contenga ctf y es más sencillo buscarlo 
```
vSalazarZ-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c_titan/156/challenge.zip
--2025-02-22 04:46:41--  https://artifacts.picoctf.net/c_titan/156/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.18, 3.160.5.42, 3.160.5.93, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.18|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 293739 (287K) [application/octet-stream]
Saving to: 'challenge.zip'

challenge.zip                                              100%[=======================================================================================================================================>] 286.85K  1.85MB/s    in 0.2s    

2025-02-22 04:46:42 (1.85 MB/s) - 'challenge.zip' saved [293739/293739]

vSalazarZ-picoctf@webshell:~$ ls
challenge.zip
vSalazarZ-picoctf@webshell:~$ unzip challenge.zip
Archive:  challenge.zip
   creating: drop-in/
 extracting: drop-in/message.py      
   creating: drop-in/.git/
   creating: drop-in/.git/branches/
  inflating: drop-in/.git/description  
   creating: drop-in/.git/hooks/
  inflating: drop-in/.git/hooks/applypatch-msg.sample  
  inflating: drop-in/.git/hooks/commit-msg.sample  
  inflating: drop-in/.git/hooks/fsmonitor-watchman.sample  
  inflating: drop-in/.git/hooks/post-update.sample  
  inflating: drop-in/.git/hooks/pre-applypatch.sample  
  inflating: drop-in/.git/hooks/pre-commit.sample  
  inflating: drop-in/.git/hooks/pre-merge-commit.sample  
  inflating: drop-in/.git/hooks/pre-push.sample  
  inflating: drop-in/.git/hooks/pre-rebase.sample  
  inflating: drop-in/.git/hooks/pre-receive.sample  
  inflating: drop-in/.git/hooks/prepare-commit-msg.sample  
  inflating: drop-in/.git/hooks/update.sample  
   creating: drop-in/.git/info/
  inflating: drop-in/.git/info/exclude  
   creating: drop-in/.git/refs/
   creating: drop-in/.git/refs/heads/
 extracting: drop-in/.git/refs/heads/master  
   creating: drop-in/.git/refs/tags/
 extracting: drop-in/.git/HEAD       
  inflating: drop-in/.git/config     
   creating: drop-in/.git/objects/
   creating: drop-in/.git/objects/pack/
   creating: drop-in/.git/objects/info/
   creating: drop-in/.git/objects/7d/
 extracting: drop-in/.git/objects/7d/f869a15e76c28afb609fa4dbc059144ad70161  
  inflating: drop-in/.git/index      
 extracting: drop-in/.git/COMMIT_EDITMSG  
   creating: drop-in/.git/logs/
  inflating: drop-in/.git/logs/HEAD  
   creating: drop-in/.git/logs/refs/
   creating: drop-in/.git/logs/refs/heads/
  inflating: drop-in/.git/logs/refs/heads/master  
vSalazarZ-picoctf@webshell:~$ ls
challenge.zip  drop-in
vSalazarZ-picoctf@webshell:~$ cd drop-in/
vSalazarZ-picoctf@webshell:~/drop-in$ ls
message.py
vSalazarZ-picoctf@webshell:~/drop-in$ python message.py
  File "/home/vSalazarZ-picoctf/drop-in/message.py", line 1
    print("Hello, World!"
         ^
SyntaxError: '(' was never closed
vSalazarZ-picoctf@webshell:~/drop-in$ git log

[2]+  Stopped                 git log
vSalazarZ-picoctf@webshell:~/drop-in$ git log

[3]+  Stopped                 git log
vSalazarZ-picoctf@webshell:~/drop-in$ 
vSalazarZ-picoctf@webshell:~/drop-in$ git log | grep picoCTF
Author: picoCTF <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>
Author: picoCTF{@sk_th3_1nt3rn_d2d29f22} <ops@picoctf.com>
Author: picoCTF <ops@picoctf.com>

flag: picoCTF{@sk_th3_1nt3rn_d2d29f22}
```

## Referencias 
https://primer.picoctf.org/#_git_version_control