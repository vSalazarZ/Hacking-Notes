## Descripción 
Can you look at the data in this binary: [static](https://mercury.picoctf.net/static/66932732825076cad4ba43e463dae82f/static)? This [BASH script](https://mercury.picoctf.net/static/66932732825076cad4ba43e463dae82f/ltdis.sh) might help!
## Solución 1

Con consola
Primero descargamos con wget static y wget bash, después vemos el contenido que contienen los archivos, le damos chmod a static y hacemos un grep para sacar el pico

```
vSalazarZ-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/66932732825076cad4ba43e463dae82f/static
--2025-02-17 18:26:39--  https://mercury.picoctf.net/static/66932732825076cad4ba43e463dae82f/static
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8376 (8.2K) [application/octet-stream]
Saving to: 'static'

static                                                     100%[=======================================================================================================================================>]   8.18K  --.-KB/s    in 0s      

2025-02-17 18:26:39 (282 MB/s) - 'static' saved [8376/8376]

vSalazarZ-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/66932732825076cad4ba43e463dae82f/ltdis.sh
--2025-02-17 18:26:48--  https://mercury.picoctf.net/static/66932732825076cad4ba43e463dae82f/ltdis.sh
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 785 [application/octet-stream]
Saving to: 'ltdis.sh'

ltdis.sh                                                   100%[=======================================================================================================================================>]     785  --.-KB/s    in 0s      

2025-02-17 18:26:48 (277 MB/s) - 'ltdis.sh' saved [785/785]

vSalazarZ-picoctf@webshell:~$ ls
README.txt  file  flag  ltdis.sh  salida  static  strings  warm
vSalazarZ-picoctf@webshell:~$ chmod +x ./static
vSalazarZ-picoctf@webshell:~$ ls
README.txt  file  flag  ltdis.sh  salida  static  strings  warm
vSalazarZ-picoctf@webshell:~$ ./static
Oh hai! Wait what? A flag? Yes, it's around here somewhere!
vSalazarZ-picoctf@webshell:~$ cat ltdis.sh
#!/bin/bash



echo "Attempting disassembly of $1 ..."


#This usage of "objdump" disassembles all (-D) of the first file given by 
#invoker, but only prints out the ".text" section (-j .text) (only section
#that matters in almost any compiled program...

objdump -Dj .text $1 > $1.ltdis.x86_64.txt


#Check that $1.ltdis.x86_64.txt is non-empty
#Continue if it is, otherwise print error and eject

if [ -s "$1.ltdis.x86_64.txt" ]
then
        echo "Disassembly successful! Available at: $1.ltdis.x86_64.txt"

        echo "Ripping strings from binary with file offsets..."
        strings -a -t x $1 > $1.ltdis.strings.txt
        echo "Any strings found in $1 have been written to $1.ltdis.strings.txt with file offset"



else
        echo "Disassembly failed!"
        echo "Usage: ltdis.sh <program-file>"
        echo "Bye!"
fi
vSalazarZ-picoctf@webshell:~$ ./ltdis.sh
-bash: ./ltdis.sh: Permission denied
vSalazarZ-picoctf@webshell:~$ bash ltdis.sh
Attempting disassembly of  ...
objdump: 'a.out': No such file
objdump: section '.text' mentioned in a -j option, but not found in any input file
Disassembly failed!
Usage: ltdis.sh <program-file>
Bye!
vSalazarZ-picoctf@webshell:~$ bash ltdis.sh <static>
-bash: syntax error near unexpected token `newline'
vSalazarZ-picoctf@webshell:~$ bash ltdis.sh static

vSalazarZ-picoctf@webshell:~$ cat static.ltdis.strings.txt | grep pico

   1020 picoCTF{d15a5m_t34s3r_f5aeda17}
   
```
