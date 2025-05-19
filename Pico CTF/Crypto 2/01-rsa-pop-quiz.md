## Descripción 
Class, take your seats! It's PRIME-time for a quiz... `nc jupiter.challenges.picoctf.org 18821`

Hint:
1. [RSA info](https://simple.wikipedia.org/wiki/RSA_algorithm)
## Solución 1

Este problema nos da un servidor al que hay que conectarnos, nos conectamos y miramos que nos habla de temas de criptografía, así que investigamos sobre eso y RSA, una vez hacemos eso hacemos un formulario para tener las formulas para resolver los ejercicios de uno por uno, pero el ejercicio tiene un tiempo limite por lo que nunca da tiempo de resolver todo en una sola sesión.
Así que realizamos un archivo python llamado exploit para resolver las preguntas que nos hacen en el servidor de manera automatizada y eso es lo que hacemos, un archivo .py y vamos realizando las preguntas y respuestas de una a uno, una vez hechas todas, corremos el comando python3 exploit.py y este nos resuelve todas las preguntas del servidor, únicamente convertimos el resultado que se nos de en hexadecimal a texto para obtener la bandera.

```
Información necesaria para hacer el exploit:
RSA	- Llave pública - asimétrico

m	- mensaje en original o mensaje en texto plano
c	- mensaje cifrado (ciphertext)
p, q 	- son dos números primos distintos y muy grandes
n	- es el módulo (lo comparten las llaves públicas y privada)
tn	- totient n (función de euler)
e	- llave pública - 65537 (exponente) 2^16+1
d	- llave privada

Cálculos
-----------------------------
n  = p * q
tn = (p-1) * (q-1)
d  = e ^ -1 (mod tn)   -   pow(e, -1, tn)
-----------------------------
Cifrar (encriptar)

c = m ^ e (mod n)      -   pow(m, e, n)
-----------------------------
Descifrar (desencriptar)

m = c ^ d (mod n)      -   pow(c, d, n)

Resultados: 
1: 4636878989
2: 93089
3: no
4: 836623060

exploit.py: 
from pwn import *

s = remote("jupiter.challenges.picoctf.org", 18821)
#Paso 1
print(s.recvuntil(b'):').decode())
s.sendline(b'Y')
print(s.recvuntil(b': ').decode())
q = 60413
p = 76753
n = p * q
print('n='+str(n))
s.sendline(str(n).encode())
#Paso 2
print(s.recvuntil(b'):').decode())
s.sendline(b'Y')
print(s.recvuntil(b': ').decode())
p = 54269
n = 5051846941
q = n // p
print('q='+str(q))
s.sendline(str(q).encode())
#Paso 3
print(s.recvuntil(b'):').decode())
s.sendline(b'N')
#Paso 4
print(s.recvuntil(b'):').decode())
s.sendline(b'Y')
print(s.recvuntil(b': ').decode())
q = 66347
p = 12611
tn = (p-1) * (q-1)
print('tn=' + str(tn))
s.sendline(str(tn).encode())
#Paso 5
print(s.recvuntil(b'):').decode())
s.sendline(b'Y')
print(s.recvuntil(b': ').decode())
m = 63572941714893115471909876155445751335819678864994840913526614064140444>
e = 3
n = 29129463609326322559521123136222078780585451208149138547799121083622333>
c = pow(m, e, n)
print('c='+str(c))
s.sendline(str(c).encode())
#Paso 6
print(s.recvuntil(b'):').decode())
s.sendline(b'N')
#Paso 7
print(s.recvuntil(b'):').decode())
s.sendline(b'Y')
print(s.recvuntil(b': ').decode())
q = 92092076805892533739724722602668675840671093008520241548191914215399824>
p = 97846775312392801037224396977012615848433199640105786119757047098757998>
e = 65537
tn = (p-1) * (q-1)
d = pow(e, -1, tn)
print('d='+str(d))
s.sendline(str(d).encode())
#Paso 8
print(s.recvuntil(b'):').decode())
s.sendline(b'Y')
print(s.recvuntil(b': ').decode())
p = 15314304227252786879841261241720443415693514687428299094238669402046286>
c = 13433290949680532374013867441263154634705815037382789341947905025573905>
e = 65537
n = 23952937352643527451379227516428377705004894508566304313177880191662177>
q = n // p
tn = (p-1) * (q-1)
d = pow(e, -1, tn)
m = pow(c, d, n)
print('m=' + str(m))
s.sendline(str(m).encode())
print(s.recvall().decode())

flag = hex(m)
print(bytes.fromhex(flag[2:]).decode())

flag: picoCTF{wA8_th4t$_ill3aGal..oa2d2239b}
```

## Referencias
1. https://es.wikipedia.org/wiki/Criptograf%C3%ADa_asim%C3%A9trica
2. https://simple.wikipedia.org/wiki/RSA_algorithm