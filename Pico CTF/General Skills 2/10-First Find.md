## Descripción 
Unzip this archive and find the file named 'uber-secret.txt'
- [Download zip file](https://artifacts.picoctf.net/c/502/files.zip)
## Solución 1

Con consola Linux,
Primero descargamos el zip con wget, le damos unzip y buscamos la carpeta uber-secret.txt y con un cat sacamos el pico

```
vSalazarZ-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/502/files.zip
--2025-02-17 19:22:30--  https://artifacts.picoctf.net/c/502/files.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.128, 3.160.22.43, 3.160.22.16, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.128|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3995553 (3.8M) [application/octet-stream]
Saving to: 'files.zip'

files.zip                                                  100%[=======================================================================================================================================>]   3.81M  1.80MB/s    in 2.1s    

2025-02-17 19:22:32 (1.80 MB/s) - 'files.zip' saved [3995553/3995553]

vSalazarZ-picoctf@webshell:~$ ls
files.zip
vSalazarZ-picoctf@webshell:~$ }unzip files.zip
-bash: }unzip: command not found
vSalazarZ-picoctf@webshell:~$ unzip files.zip
Archive:  files.zip
   creating: files/
   creating: files/satisfactory_books/
   creating: files/satisfactory_books/more_books/
  inflating: files/satisfactory_books/more_books/37121.txt.utf-8  
  inflating: files/satisfactory_books/23765.txt.utf-8  
  inflating: files/satisfactory_books/16021.txt.utf-8  
  inflating: files/13771.txt.utf-8   
   creating: files/adequate_books/
   creating: files/adequate_books/more_books/
   creating: files/adequate_books/more_books/.secret/
   creating: files/adequate_books/more_books/.secret/deeper_secrets/
   creating: files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/
 extracting: files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt  
  inflating: files/adequate_books/more_books/1023.txt.utf-8  
  inflating: files/adequate_books/46804-0.txt  
  inflating: files/adequate_books/44578.txt.utf-8  
   creating: files/acceptable_books/
   creating: files/acceptable_books/more_books/
  inflating: files/acceptable_books/more_books/40723.txt.utf-8  
  inflating: files/acceptable_books/17880.txt.utf-8  
  inflating: files/acceptable_books/17879.txt.utf-8  
  inflating: files/14789.txt.utf-8   
vSalazarZ-picoctf@webshell:~$ find .-name uber-secret.txt
find: '.-name': No such file or directory
find: 'uber-secret.txt': No such file or directory
vSalazarZ-picoctf@webshell:~$ find . -name uber-secret.txt
./files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt
vSalazarZ-picoctf@webshell:~$ cat ./files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt

picoCTF{f1nd_15_f457_ab443fd1}

```
