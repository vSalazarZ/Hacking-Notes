## Descripción 
I've gotten bored of handing out flags as text. Wouldn't it be cool if they were an image instead?You can download the challenge files here:
- [challenge.zip](https://artifacts.picoctf.net/c_atlas/13/challenge.zip)
The same files are accessible via SSH here:`ssh -p 53848 ctf-player@atlas.picoctf.net`Using the password `f3b61b38`. Accept the fingerprint with `yes`, and `ls` once connected to begin. Remember, in a shell, passwords are hidden!

Hint:
1. QR codes are a way of encoding data. While they're most known for storing URLs, they can store other things too.
2. Mobile phones have included native QR code scanners in their cameras since version 8 (Oreo) and iOS 11
3. If you don't have access to a phone, you can also use zbar-tools to convert an image to text

## Solución 

Descargamos el archivo challenge.zip usando wget. Lo descomprimimos y encontramos una estructura de carpetas, vamos metiendonos de carpeta en carpeta hasta llegar a ctf-player y ahí está la bandera en flag.png, la abrimos y nos sale un código QR, lo escaneamos y obtenemos la bandera 

```
omarsalazar@DESKTOP-H97NF1C:~$ wget https://artifacts.picoctf.net/c_atlas/13/challenge.zip
--2025-05-09 19:19:35--  https://artifacts.picoctf.net/c_atlas/13/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.64, 3.161.55.26, 3.161.55.100, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.64|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 740 [application/octet-stream]
Saving to: ‘challenge.zip’

challenge.zip                 100%[=================================================>]     740  --.-KB/s    in 0s

2025-05-09 19:19:35 (216 MB/s) - ‘challenge.zip’ saved [740/740]

omarsalazar@DESKTOP-H97NF1C:~$ ls
challenge.zip
omarsalazar@DESKTOP-H97NF1C:~$ unzip challenge.zip
Archive:  challenge.zip
   creating: home/ctf-player/drop-in/
 extracting: home/ctf-player/drop-in/flag.png
omarsalazar@DESKTOP-H97NF1C:~$ ls
challenge.zip  home
omarsalazar@DESKTOP-H97NF1C:~$ cd home
omarsalazar@DESKTOP-H97NF1C:~/home$ ls
ctf-player
omarsalazar@DESKTOP-H97NF1C:~/home$ cd ctf-player
omarsalazar@DESKTOP-H97NF1C:~/home/ctf-player$ ls
drop-in
omarsalazar@DESKTOP-H97NF1C:~/home/ctf-player$ cd drop-in
omarsalazar@DESKTOP-H97NF1C:~/home/ctf-player/drop-in$ ls
flag.png
omarsalazar@DESKTOP-H97NF1C:~/home/ctf-player/drop-in$ open flag.png

flag: picoCTF{p33k_@_b00_d4ca652e}
```
