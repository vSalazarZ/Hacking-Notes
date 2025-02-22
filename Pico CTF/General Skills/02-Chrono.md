## Descripción 
How to automate tasks to run at intervals on linux servers?Use ssh to connect to this server:

```
Server: saturn.picoctf.net
Port: 58339
Username: picoplayer 
Password: bLgSMmbY6X
```
## Solución 1

Con consola linux
Nos conectamos al servidor mediante ssh
Después nos dice la práctica que como podemos automatizar tareas en servidores linux, entonces buscamos comandos para automatizar servidores de linux y nos encontramos con el /etc/crontab
lo ponemos y nos da la flag automáticamente 

```
vSalazarZ-picoctf@webshell:~$ ssh picoplayer@saturn.picoctf.net -p 58339
The authenticity of host '[saturn.picoctf.net]:58339 ([13.59.203.175]:58339)' can't be established.
ED25519 key fingerprint is SHA256:dMTscRrUiURy7uMu5eGWwEKdd2FzqLzx6LfWhssWnNQ.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[saturn.picoctf.net]:58339' (ED25519) to the list of known hosts.
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

picoplayer@challenge:~$ /etc/crontab
-bash: /etc/crontab: Permission denied
picoplayer@challenge:~$ cat /etc/crontab
# picoCTF{Sch3DUL7NG_T45K3_L1NUX_1b4d8744}
picoplayer@challenge:~$ Connection to saturn.picoctf.net closed by remote host.
Connection to saturn.picoctf.net closed.
vSalazarZ-picoctf@webshell:~$ 

flag: picoCTF{Sch3DUL7NG_T45K3_L1NUX_1b4d8744}
```

## Referencias 
https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/4/html/system_administration_guide/automated_tasks#Cron-Configuring_Cron_Tasks