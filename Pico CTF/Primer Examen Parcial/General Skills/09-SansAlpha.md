## Descripción 
The Multiverse is within your grasp! Unfortunately, the server that contains the secrets of the multiverse is in a universe where keyboards only have numbers and (most) symbols.`ssh -p 51219 ctf-player@mimas.picoctf.net`Use password: `1ad5be0d`

Hint:
1. Where can you get some letters?
## Solución 1

Nos conectamos a un servidor remoto a través de SSH. Luego, usamos varios comandos con comodines como * y ? para intentar listar archivos y explorar directorios. Finalmente damos con el comando que nos encuentra la flag.txt en base64. Ahora, necesitamos decodificar esa cadena para obtener la bandera que tenemos que encontrar.

```
omarsalazar@DESKTOP-H97NF1C:~$ ssh -p 51219 ctf-player@mimas.picoctf.net
ctf-player@mimas.picoctf.net's password:
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 6.5.0-1016-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.
Last login: Thu Apr 17 01:08:26 2025 from 127.0.0.1
SansAlpha$ ls
SansAlpha: Unknown character detected
SansAlpha$ *
bash: blargh: command not found

SansAlpha$ */
bash: blargh/: Is a directory

SansAlpha$ */*
bash: blargh/flag.txt: Permission denied

SansAlpha$ /*/???
E: Invalid operation /bin/awk

SansAlpha$ /*/??????
/bin/base32: extra operand ‘/bin/base64’
Try '/bin/base32 --help' for more information.

SansAlpha$ /*/????64 */*
/bin/base64: extra operand ‘/bin/x86_64’
Try '/bin/base64 --help' for more information.

SansAlpha$ /*/???[!_] */*
/bin/arch: extra operand ‘/bin/bash’
Try '/bin/arch --help' for more information.

SansAlpha$ /*/???[!_]64 */*
/bin/base64: extra operand ‘blargh/flag.txt’
Try '/bin/base64 --help' for more information.

SansAlpha$ /*/???[!_]64 */????.???
cmV0dXJuIDAgcGljb0NURns3aDE1X211MTcxdjNyNTNfMTVfbTRkbjM1NV83NzVhYzEyZH0=

SansAlpha$  Connection to mimas.picoctf.net closed by remote host.
Connection to mimas.picoctf.net closed.
omarsalazar@DESKTOP-H97NF1C:~$
```

Usando cyberchef para decodificar en base64

```
Input: cmV0dXJuIDAgcGljb0NURns3aDE1X211MTcxdjNyNTNfMTVfbTRkbjM1NV83NzVhYzEyZH0=

Recipe: From Base64

Output: return 0 picoCTF{7h15_mu171v3r53_15_m4dn355_775ac12d}

flag: picoCTF{7h15_mu171v3r53_15_m4dn355_775ac12d}
```

## Referencias
https://tldp.org/LDP/GNU-Linux-Tools-Summary/html/x11655.htm
https://gchq.github.io/CyberChef/