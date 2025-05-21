## Descripción 
In RSA, a small `e` value can be problematic, but what about `N`? Can you decrypt this? [values](https://mercury.picoctf.net/static/12d820e355a7775a2c9129b2622a7eb6/values)

Hint:
1. Bits are expensive, I used only a little bit over 100 to save money
## Solución 1

Obtenemos un mensaje cifrado, se factoriza el número n en sus primos p y q porque es pequeño. Luego se calcula la función totient y la clave privada d. Con d se descifra el mensaje cifrado c y se obtiene la bandera. Finalmente, convertimos el número a texto y obtuve la bandera.

```
omarsalazar@DESKTOP-H97NF1C:~$ cat values
Decrypt my super sick RSA:
c: 843044897663847841476319711639772861390329326681532977209935413827620909782846667
n: 1422450808944701344261903748621562998784243662042303391362692043823716783771691667
e: 65537omarsalazar@DESKTOP-H97NF1C:~$
omarsalazar@DESKTOP-H97NF1C:~$

Usando Python

omarsalazar@DESKTOP-H97NF1C:~$ python3
Python 3.12.3 (main, Feb  4 2025, 14:48:35) [GCC 13.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> c = 843044897663847841476319711639772861390329326681532977209935413827620909782846667
>>> n = 1422450808944701344261903748621562998784243662042303391362692043823716783771691667
>>> e = 65537
>>> p = 2159947535959146091116171018558446546179
>>> q = 658558036833541874645521278345168572231473
>>> p * q
1422450808944701344261903748621562998784243662042303391362692043823716783771691667
>>> tn = (p-1) * (q-1)
>>> tn
1422450808944701344261903748621562998783582944057933890341955406374353056752914016
>>> d = pow(e,-1,tn)
>>> m = pow(c,d,n)
>>> m
13016382529449106065927291425342535437996222135352905256639555294957886055592061
>>> bytes.fromhex(hex(m)[2:]))
  File "<stdin>", line 1
    bytes.fromhex(hex(m)[2:]))
                             ^
SyntaxError: unmatched ')'
>>> bytes.fromhex(hex(m)[2:])
b'picoCTF{sma11_N_n0_g0od_00264570}'
>>>

flag: picoCTF{sma11_N_n0_g0od_00264570}
```

## Solución 2

Se usó una herramienta llamada RsaCtfTool con un ataque llamado ataque Factordb que permite encontrar la clave privada cuando ciertas condiciones se cumplen, y así obtener la bandera automáticamente.

```
omarsalazar@DESKTOP-H97NF1C:~$ source tools/bin/activate
(tools) omarsalazar@DESKTOP-H97NF1C:~$
(tools) omarsalazar@DESKTOP-H97NF1C:~$ RsaCtfTool -n 1422450808944701344261903748621562998784243662042303391362692043823716783771691667 -e 65537 --decrypt 843044897663847841476319711639772861390329326681532977209935413827620909782846667 --attack factordb
private argument is not set, the private key will not be displayed, even if recovered.
['/tmp/tmpc2fnsauw']

[*] Testing key /tmp/tmpc2fnsauw.
[*] Performing factordb attack on /tmp/tmpc2fnsauw.
[*] Attack success with factordb method !

Results for /tmp/tmpc2fnsauw:

Decrypted data :
HEX : 0x007069636f4354467b736d6131315f4e5f6e305f67306f645f30303236343537307d
INT (big endian) : 13016382529449106065927291425342535437996222135352905256639555294957886055592061
INT (little endian) : 3710929847087427876431838308943291274263296323136963202115989746100135819907526656
utf-8 : picoCTF{sma11_N_n0_g0od_00264570}
utf-16 : 瀀捩䍯䙔獻慭ㄱ也湟弰で摯た㈰㐶㜵細
STR : b'\x00picoCTF{sma11_N_n0_g0od_00264570}'
(tools) omarsalazar@DESKTOP-H97NF1C:~$

flag: picoCTF{sma11_N_n0_g0od_00264570}
```

## Referencias
1. https://github.com/RsaCtfTool/RsaCtfTool