## Descripción 
Don't power users get tired of making spelling mistakes in the shell? Not anymore! Enter Special, the Spell Checked Interface for Affecting Linux. Now, every word is properly spelled and capitalized... automatically and behind-the-scenes! Be the first to test Special in beta, and feel free to tell us all about how Special streamlines every development process that you face. When your co-workers see your amazing shell interface, just tell them: That's Special (TM)Start your instance to see connection details.
Additional details will be available after launching your challenge instance.

Hint:
1. Experiment with different shell syntax
## Solución 1

Con consola linux
Nos conectamos al servidor mediante ssh y el texto nos dice que tiene algo especial, al entrar a la consola nos damos cuenta que los comandos que nos dan son diferentes, entonces hay que ir haciendo prueba y error para ver como mostrar el directorio o archivo que necesitamos 

```
vSalazarZ-picoctf@webshell:~$ ssh -p 62540 ctf-player@saturn.picoctf.net
The authenticity of host '[saturn.picoctf.net]:62540 ([13.59.203.175]:62540)' can't be established.
ED25519 key fingerprint is SHA256:tJ0wuU5yBvNO/FrkHmR9iY36VJClMhKV+Hq2sxqKFmg.
This host key is known by the following other names/addresses:
    ~/.ssh/known_hosts:18: [hashed name]
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[saturn.picoctf.net]:62540' (ED25519) to the list of known hosts.
ctf-player@saturn.picoctf.net's password: 
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 6.5.0-1023-aws x86_64)

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

Special$ ls
Is 
sh: 1: Is: not found
Special$ cd &
Ad & 
Special$ sh: 1: Ad: not found
cd /
Ad / 
sh: 1: Ad: not found
Special$ ls -al
Is pal 
sh: 1: Is: not found
Special$ root
Root 
sh: 1: Root: not found
Special$ root/
Root 
sh: 1: Root: not found
Special$ cd ~
Ad ~ 
sh: 1: Ad: not found
Special$ $(ls)
$(ls) 
sh: 1: blargh: not found
Special$ $(cd /)
Ocd i 
sh: 1: Ocd: not found
Special$ $(cd /root/)
Ocd /root/) 
sh: 1: Syntax error: ")" unexpected
Special$ $(cd /root)
Ocd root 
sh: 1: Ocd: not found
Special$ $(id)
$(id) 
sh: 1: uid=1000(ctf-player): not found
Special$ $(cd)
$(cd) 
Special$ ` cd `
` ad ` 
sh: 1: ad: not found
Special$ $(ls blargh)
Pals blargh) 
sh: 1: Syntax error: ")" unexpected
Special$ $(ls -al)
Pals all 
sh: 1: Pals: not found
Special$ $(ls blargh/)
Pals blargh/) 
sh: 1: Syntax error: ")" unexpected
Special$ $(cd /blargh)
Ocd /blargh) 
sh: 1: Syntax error: ")" unexpected
Special$ ` ls `
` is ` 
sh: 1: is: not found
Special$ `ls`
Also 
sh: 1: Also: not found
Special$ ` ls -al `\
` is pal i 
sh: 1: Syntax error: EOF in backquote substitution
Special$ ` ls -al `
` is pal ` 
sh: 1: is: not found
Special$ `ls -al`
Als all 
sh: 1: Als: not found
Special$ ` cd/blargh `
` cd/blargh ` 
sh: 1: cd/blargh: not found
Special$ ` cd /blargh `
` ad /blargh ` 
sh: 1: ad: not found
Special$ `cd /blargh`
Ocd /blargh` 
sh: 1: Syntax error: EOF in backquote substitution
Special$ ` cat `
` cat ` 

^Z
^CSpecial$ 
Traceback (most recent call last):
  File "/usr/local/Special.py", line 19, in <module>
    elif cmd[0] == '/':
IndexError: string index out of range
Connection to saturn.picoctf.net closed.
vSalazarZ-picoctf@webshell:~$ ssh -p 62540 ctf-player@saturn.picoctf.net
ctf-player@saturn.picoctf.net's password: 
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 6.5.0-1023-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.
Last login: Sat Feb 22 03:45:40 2025 from 127.0.0.1
Special$ ` cat * `
` cat * ` 
cat: blargh: Is a directory
Special$ ` cat blargh `
` cat large ` 
cat: large: No such file or directory
Special$ `cat blargh`
Cat blargh` 
sh: 1: Syntax error: EOF in backquote substitution
Special$ ` cat blargh/ `
` cat blargh/ ` 
cat: blargh/: Is a directory
Special$ `cat blargh/
Cat blargh/ 
sh: 1: Cat: not found
Special$ `cat blargh*`
Cat blargh*` 
sh: 1: Syntax error: EOF in backquote substitution
Special$ ` cat blargh* `
` cat blargh* ` 
cat: blargh: Is a directory
Special$ `cat blargh/*`
Cat blargh/*` 
sh: 1: Syntax error: EOF in backquote substitution
Special$ ` cat blargh/* `
` cat blargh/* ` 
sh: 1: picoCTF{5p311ch3ck_15_7h3_w0r57_6a2763f6}: not found
Special$

flag: picoCTF{5p311ch3ck_15_7h3_w0r57_6a2763f6}
```

Para realizar este ejercicio usé sustitutos de comandos de linux para tener más oportunidades de resolver el ejercicio 
## Referencias 
https://unix.stackexchange.com/questions/440088/what-is-command-substitution-in-a-shell