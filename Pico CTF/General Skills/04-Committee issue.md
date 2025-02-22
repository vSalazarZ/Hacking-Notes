## Descripción 
I accidentally wrote the flag down. Good thing I deleted it!You download the challenge files here:
- [challenge.zip](https://artifacts.picoctf.net/c_titan/136/challenge.zip)

Hint:
1. Version control can help you recover files if you change or lose them!
2. Read the chapter on Git from the picoPrimer [here](https://primer.picoctf.org/#_git_version_control)
3. You can 'checkout' commits to see the files inside them
## Solución 1

Con consola linux
Primero descargamos el zip con wget, le damos unzip y en el hint 2 nos manda a una página que nos da unos comandos con git, los usamos para llegar a la flag, usamos git log y git checkout

```
vSalazarZ-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c_titan/136/challenge.zip
--2025-02-22 04:04:13--  https://artifacts.picoctf.net/c_titan/136/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.18, 3.160.5.71, 3.160.5.93, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.18|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19196 (19K) [application/octet-stream]
Saving to: 'challenge.zip'

challenge.zip                                              100%[=======================================================================================================================================>]  18.75K  --.-KB/s    in 0.002s  

2025-02-22 04:04:13 (11.8 MB/s) - 'challenge.zip' saved [19196/19196]

vSalazarZ-picoctf@webshell:~$ ls
challenge.zip
vSalazarZ-picoctf@webshell:~$ unzip challenge.zip
Archive:  challenge.zip
   creating: drop-in/
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
   creating: drop-in/.git/objects/ba/
 extracting: drop-in/.git/objects/ba/e247ddd9f730bb7a2a9425d4616b116bc7b07b  
   creating: drop-in/.git/objects/68/
 extracting: drop-in/.git/objects/68/df36301019ecc05a65a4e87a754c83411ac925  
   creating: drop-in/.git/objects/87/
 extracting: drop-in/.git/objects/87/b85d7dfb839b077678611280fa023d76e017b8  
   creating: drop-in/.git/objects/d5/
 extracting: drop-in/.git/objects/d5/52d1ecd2d83fa2e65b6724d1ff73b45a7d59b7  
   creating: drop-in/.git/objects/0c/
 extracting: drop-in/.git/objects/0c/1ab266b7a3a1cd099bb509f82b7a2d03aecd03  
   creating: drop-in/.git/objects/8d/
 extracting: drop-in/.git/objects/8d/c51806c760dfdbb34b33a2008926d3d8e8ad49  
  inflating: drop-in/.git/index      
 extracting: drop-in/.git/COMMIT_EDITMSG  
   creating: drop-in/.git/logs/
  inflating: drop-in/.git/logs/HEAD  
   creating: drop-in/.git/logs/refs/
   creating: drop-in/.git/logs/refs/heads/
  inflating: drop-in/.git/logs/refs/heads/master  
 extracting: drop-in/message.txt     
vSalazarZ-picoctf@webshell:~$ ls
challenge.zip  drop-in
vSalazarZ-picoctf@webshell:~$ cd drop-in/
vSalazarZ-picoctf@webshell:~/drop-in$ ls
message.txt
vSalazarZ-picoctf@webshell:~/drop-in$ cat message.txt
TOP SECRET
vSalazarZ-picoctf@webshell:~/drop-in$ git checkout
vSalazarZ-picoctf@webshell:~/drop-in$ cat message.txt
TOP SECRET
vSalazarZ-picoctf@webshell:~/drop-in$ git log

[1]+  Stopped                 git log
vSalazarZ-picoctf@webshell:~/drop-in$ git checkout 87b85d7dfb839b077678611280fa023d76e017b8
Note: switching to '87b85d7dfb839b077678611280fa023d76e017b8'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 87b85d7 create flag
vSalazarZ-picoctf@webshell:~/drop-in$ cat message.txt
picoCTF{s@n1t1z3_ea83ff2a}
vSalazarZ-picoctf@webshell:~/drop-in$

flag: picoCTF{s@n1t1z3_ea83ff2a}
```

## Referencias 
https://primer.picoctf.org/#_git_version_control