## Descripción 
Using a Secure Shell (SSH) is going to be pretty important.Can you `ssh` as `ctf-player` to `titan.picoctf.net` at port `51690` to get the flag?You'll also need the password `f3b61b38`. If asked, accept the fingerprint with `yes`.If your device doesn't have a shell, you can use: [https://webshell.picoctf.org](https://webshell.picoctf.org/)If you're not sure what a shell is, check out our Primer: [https://primer.picoctf.com/#_the_shell](https://primer.picoctf.com/#_the_shell)

Hint:
1. [https://linux.die.net/man/1/ssh](https://linux.die.net/man/1/ssh)
2. You can try logging in 'as' someone with `<user>`@titan.picoctf.net
3. How could you specify the port?
4. Remember, passwords are hidden when typed into the shell
## Solución 1

Con consola linux
Nos conectamos al servidor con ssh usando el user y contraseña, solo nos conectamos y nos da la flag

```
vSalazarZ-picoctf@webshell:~$ ssh ctf-player@titan.picoctf.net -p 51690
The authenticity of host '[titan.picoctf.net]:51690 ([3.139.174.234]:51690)' can't be established.
ED25519 key fingerprint is SHA256:4S9EbTSSRZm32I+cdM5TyzthpQryv5kudRP9PIKT7XQ.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[titan.picoctf.net]:51690' (ED25519) to the list of known hosts.
ctf-player@titan.picoctf.net's password: 
Welcome ctf-player, here's your flag: picoCTF{s3cur3_c0nn3ct10n_3e293eea}
Connection to titan.picoctf.net closed.
vSalazarZ-picoctf@webshell:~$ 

flag: picoCTF{s3cur3_c0nn3ct10n_3e293eea}
```
