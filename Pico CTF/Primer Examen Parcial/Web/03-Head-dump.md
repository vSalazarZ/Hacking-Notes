## Descripción 
Welcome to the challenge! In this challenge, you will explore a web application and find an endpoint that exposes a file containing a hidden flag.The application is a simple blog website where you can read articles about various topics, including an article about API Documentation. Your goal is to explore the application and find the endpoint that generates files holding the server’s memory, where a secret flag is hidden.
The website is running [picoCTF News](http://verbal-sleep.picoctf.net:56551/).

Hint:
1. Explore backend development with us
2. The head was dumped.
## Solución 1

Corremos la instancia y nos metemos a la página, revisamos el API Documentation e ingresamos al API diagnosis en headdump y ejecutamos los parametros, nos va dar un link de descarga para un archivo que contiene datos, lo descargamos y abrimos y nos damos cuenta que es mucho contenido simplemente filtramos el contenido buscando la palabra "pico" y obtenemos la bandera.

```
Abrimos el archivo en note++ en mi caso y filtramos la palabra "pico" y nos manda directamente a la bandera

274794 ,3,45939,231510  
274795 ,3,31222,316734  
274796 ,3,31223,231516  
274797 ,3,45940,135186  
274798 ,3,45941,231522  
274799 ,3,45942,122358  
274800 ,3,31225,231528  
274801 ,3,31226,317178  
274802 ,3,45943,231534  
274803 ,3,459  

274804 picoCTF{Pat!3nt_15_Th3_K3y_439bb394}  

274805 44,135270  
274806 ,3,45945,231540  
274807 ,3,45946,121686  
274808 ,3,31232,231546  
274809 ,3,31234,320160  
274810 ,3,31235,231552  
274811 ,3,45947,317790  
274812 ,3,45948,231558  
274813 ,3,45949,125880  
274814 ,3,31240,231564  
274815 ,3,31242,320130  

flag: picoCTF{Pat!3nt_15_Th3_K3y_439bb394}
```
