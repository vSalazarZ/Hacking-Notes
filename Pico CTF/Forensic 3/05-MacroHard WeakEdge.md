## Descripción 
I've hidden a flag in this file. Can you find it? [Forensics is fun.pptm](https://mercury.picoctf.net/static/3944a59474f9f676942282c50b9c3675/Forensics%20is%20fun.pptm)
## Solución 1

Descargamos el archivo y verificamos que al archivo es pptm que es un powerpoint, usamos ls -la para ver los archivos del directorio, descomprimimos el archivo y dentro hay carpetas, nos vamos metiendo a cada una hasta llegar a un hidden, usamos un cat al hidden y nos da una cadena en base64, la decodificamos y obtenemos la bandera

```
omarsalazar@DESKTOP-H97NF1C:~$ wget https://mercury.picoctf.net/static/3944a59474f9f676942282c50b9c3675/Forensics%20is%20fun.pptm
--2025-05-05 12:27:31--  https://mercury.picoctf.net/static/3944a59474f9f676942282c50b9c3675/Forensics%20is%20fun.pptm
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 100093 (98K) [application/octet-stream]
Saving to: ‘Forensics is fun.pptm’

Forensics is fun.pp 100%[==================>]  97.75K   371KB/s    in 0.3s

2025-05-05 12:27:32 (371 KB/s) - ‘Forensics is fun.pptm’ saved [100093/100093]

omarsalazar@DESKTOP-H97NF1C:~$ s
s: command not found
omarsalazar@DESKTOP-H97NF1C:~$ ls
'Forensics is fun.pptm'
omarsalazar@DESKTOP-H97NF1C:~$ file Forensic\ is\ fun.pptm
Forensic is fun.pptm: cannot open `Forensic is fun.pptm' (No such file or directory)
omarsalazar@DESKTOP-H97NF1C:~$ file Forensics is fun.pptm
Forensics: cannot open `Forensics' (No such file or directory)
is:        cannot open `is' (No such file or directory)
fun.pptm:  cannot open `fun.pptm' (No such file or directory)
omarsalazar@DESKTOP-H97NF1C:~$ file Forensics\ is\ fun.pptm
Forensics is fun.pptm: Microsoft PowerPoint 2007+
omarsalazar@DESKTOP-H97NF1C:~$ ls -la
total 204
drwxr-x--- 9 omarsalazar omarsalazar  32768 May  5 12:27  .
drwxr-xr-x 3 root        root          4096 Apr  7 12:37  ..
-rw------- 1 omarsalazar omarsalazar  10334 May  5 12:03  .bash_history
-rw-r--r-- 1 omarsalazar omarsalazar    220 Apr  7 12:37  .bash_logout
-rw-r--r-- 1 omarsalazar omarsalazar   3792 Apr 15 21:22  .bashrc
drwx------ 2 omarsalazar omarsalazar   4096 Apr  7 12:37  .cache
drwxr-xr-x 4 omarsalazar omarsalazar   4096 Apr 15 22:52  .cargo
drwxr-xr-x 4 omarsalazar omarsalazar   4096 May  5 11:46  .config
drwxr-xr-x 2 omarsalazar omarsalazar   4096 Apr  7 12:37  .landscape
-rw------- 1 omarsalazar omarsalazar     20 Apr 16 23:13  .lesshst
drwxr-xr-x 3 omarsalazar omarsalazar   4096 Apr 15 21:23  .local
-rw-r--r-- 1 omarsalazar omarsalazar      0 May  5 11:08  .motd_shown
-rw-r--r-- 1 omarsalazar omarsalazar    828 Apr 15 21:22  .profile
-rw------- 1 omarsalazar omarsalazar     42 Apr 16 23:27  .psql_history
drwxr-xr-x 6 omarsalazar omarsalazar   4096 Apr 15 21:23  .rustup
drwx------ 2 omarsalazar omarsalazar   4096 Apr 16 19:33  .ssh
-rw-r--r-- 1 omarsalazar omarsalazar      0 Apr  7 12:56  .sudo_as_admin_successful
-rw-r--r-- 1 omarsalazar omarsalazar    215 May  5 12:27  .wget-hsts
-rw-r--r-- 1 omarsalazar omarsalazar 100093 Mar 23  2021 'Forensics is fun.pptm'
omarsalazar@DESKTOP-H97NF1C:~$ unzip Forensics\ is\ fun.pptm
omarsalazar@DESKTOP-H97NF1C:~$ ls -la
total 228
drwxr-x--- 12 omarsalazar omarsalazar  32768 May  5 12:33  .
drwxr-xr-x  3 root        root          4096 Apr  7 12:37  ..
-rw-------  1 omarsalazar omarsalazar  10334 May  5 12:03  .bash_history
-rw-r--r--  1 omarsalazar omarsalazar    220 Apr  7 12:37  .bash_logout
-rw-r--r--  1 omarsalazar omarsalazar   3792 Apr 15 21:22  .bashrc
drwx------  2 omarsalazar omarsalazar   4096 Apr  7 12:37  .cache
drwxr-xr-x  4 omarsalazar omarsalazar   4096 Apr 15 22:52  .cargo
drwxr-xr-x  4 omarsalazar omarsalazar   4096 May  5 11:46  .config
drwxr-xr-x  2 omarsalazar omarsalazar   4096 Apr  7 12:37  .landscape
-rw-------  1 omarsalazar omarsalazar     20 Apr 16 23:13  .lesshst
drwxr-xr-x  3 omarsalazar omarsalazar   4096 Apr 15 21:23  .local
-rw-r--r--  1 omarsalazar omarsalazar      0 May  5 11:08  .motd_shown
-rw-r--r--  1 omarsalazar omarsalazar    828 Apr 15 21:22  .profile
-rw-------  1 omarsalazar omarsalazar     42 Apr 16 23:27  .psql_history
drwxr-xr-x  6 omarsalazar omarsalazar   4096 Apr 15 21:23  .rustup
drwx------  2 omarsalazar omarsalazar   4096 Apr 16 19:33  .ssh
-rw-r--r--  1 omarsalazar omarsalazar      0 Apr  7 12:56  .sudo_as_admin_successful
-rw-r--r--  1 omarsalazar omarsalazar    215 May  5 12:27  .wget-hsts
-rw-r--r--  1 omarsalazar omarsalazar 100093 Mar 23  2021 'Forensics is fun.pptm'
-rw-r--r--  1 omarsalazar omarsalazar  10660 Jan  1  1980 '[Content_Types].xml'
drwxr-xr-x  2 omarsalazar omarsalazar   4096 May  5 12:33  _rels
drwxr-xr-x  2 omarsalazar omarsalazar   4096 May  5 12:33  docProps
drwxr-xr-x  7 omarsalazar omarsalazar   4096 May  5 12:33  ppt
omarsalazar@DESKTOP-H97NF1C:~$ ls
'Forensics is fun.pptm'  '[Content_Types].xml'   _rels   docProps   ppt
omarsalazar@DESKTOP-H97NF1C:~$ cd ppt
omarsalazar@DESKTOP-H97NF1C:~/ppt$ ls
_rels          presentation.xml  slideMasters  tableStyles.xml  vbaProject.bin
presProps.xml  slideLayouts      slides        theme            viewProps.xml
omarsalazar@DESKTOP-H97NF1C:~/ppt$ cd slideMasters
omarsalazar@DESKTOP-H97NF1C:~/ppt/slideMasters$ ls
_rels  hidden  slideMaster1.xml
omarsalazar@DESKTOP-H97NF1C:~/ppt/slideMasters$ cat hidden
Z m x h Z z o g c G l j b 0 N U R n t E M W R f d V 9 r b j B 3 X 3 B w d H N f c l 9 6 M X A 1 f Qomarsalazar@DESKTOP-H97NF1C:~/ppt/slideMasters$
```

Usando cyberchef para decodificar cadena

```
Cyberchef

Input: ZmxhZzogcGljb0NURntEMWRfdV9rbjB3X3BwdHNfcl96MXA1fQ

Recipe: From Base64

Output: flag: picoCTF{D1d_u_kn0w_ppts_r_z1p5}

flag: picoCTF{D1d_u_kn0w_ppts_r_z1p5}
```

## Referencias 
https://gchq.github.io/CyberChef/