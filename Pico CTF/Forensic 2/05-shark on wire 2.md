## Descripción 
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap). Recover the flag that was pilfered from the network.

## Solución 1

Usando cyberchef

Descargamos el archivo de wireshark, lo abrimos en el programa y vamos viendo los paquetes udp, nos fijamos que contienen un start, contenido y un end, vamos a tomar los números de puertos de los paquetes y los ingresamos en un conversor a ascii, al convertir esos caracteres obtenemos la bandera 

```
Cyberchef

Input: 112 105 99 111 67 84 70 123 112 49 76 76 102 51 114 51 100 95 100 97 116 97 95 118 49 97 95 115 116 51 103 48 125

Recipe: From Decimal

Output: picoCTF{p1LLf3r3d_data_v1a_st3g0}

flag: picoCTF{p1LLf3r3d_data_v1a_st3g0}
```

## Solución 2

Usando python

Descargamos el archivo de wireshark, lo abrimos en el programa y vamos viendo los paquetes udp, nos fijamos que contienen un start, contenido y un end, vamos a realizar un programa de python con nano y usando un ciclo logramos sacar todos los números de los puertos para que lo obtenga el programa, después corremos este y capturamos la bandera

```
omarsalazar@DESKTOP-H97NF1C:~$ nano exp.py

from scapy.all import *

packets = rdpcap('capture.pcap')

flag = ''

for p in packets:
	if UDP in p and p[UDP].dport == 22:
		if p[UDP].sport > 5000:
			flag += chr(p[UDP].sport - 5000)
print(flag)

omarsalazar@DESKTOP-H97NF1C:~$ python3 exp.py
picoCTF{p1LLf3r3d_data_v1a_st3g0}
omarsalazar@DESKTOP-H97NF1C:~$

flag: picoCTF{p1LLf3r3d_data_v1a_st3g0}
```

## Referencias 
https://gchq.github.io/CyberChef/