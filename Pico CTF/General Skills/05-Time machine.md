## Descripción 
What was I last working on? I remember writing a note to help me remember...You can download the challenge files here:
- [challenge.zip](https://artifacts.picoctf.net/c_titan/161/challenge.zip)

Hint:
1. The `cat` command will let you read a file, but that won't help you here!
2. Read the chapter on Git from the picoPrimer [here](https://primer.picoctf.org/#_git_version_control).
3. When committing a file with git, a message can (and should) be included.
## Solución 1

Con consola linux
Primero descargamos el zip con wget, le damos unzip y en el hint 2 nos manda a una página que nos da unos comandos con git, los usamos para llegar a la flag, usamos git log y git checkout

```
vSalazarZ-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c_titan/161/challenge.zip
--2025-02-22 04:20:32--  https://artifacts.picoctf.net/c_titan/161/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.18, 3.160.5.93, 3.160.5.71, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.18|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17739 (17K) [application/octet-stream]
Saving to: 'challenge.zip'

challenge.zip                                              100%[=======================================================================================================================================>]  17.32K  --.-KB/s    in 0.007s  

2025-02-22 04:20:32 (2.56 MB/s) - 'challenge.zip' saved [17739/17739]

vSalazarZ-picoctf@webshell:~$ ls
challenge.zip
vSalazarZ-picoctf@webshell:~$ unzip challenge.zip
Archive:  challenge.zip
   creating: drop-in/
  inflating: drop-in/message.txt     
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
   creating: drop-in/.git/objects/43/
 extracting: drop-in/.git/objects/43/246218ab4fc7b30e9a9dff073e012316851469  
   creating: drop-in/.git/objects/25/
 extracting: drop-in/.git/objects/25/16effb8d70e33bdd0023629b164a77225e1ec2  
   creating: drop-in/.git/objects/10/
 extracting: drop-in/.git/objects/10/228f3d6437701ef5aaac04213757031f30ebec  
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
message.txt
vSalazarZ-picoctf@webshell:~/drop-in$ cat message.txt
This is what I was working on, but I'd need to look at my commit history to know why...vSalazarZ-picoctf@webshell:~/drop-in$ git log

[1]+  Stopped                 git log
vSalazarZ-picoctf@webshell:~/drop-in$ git checkout 10228f3d6437701ef5aaac04213757031f30ebec
Note: switching to '10228f3d6437701ef5aaac04213757031f30ebec'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 10228f3 picoCTF{t1m3m@ch1n3_8defe16a}
vSalazarZ-picoctf@webshell:~/drop-in$ 

flag: picoCTF{t1m3m@ch1n3_8defe16a}
```

## Referencias 
https://primer.picoctf.org/#_git_version_control