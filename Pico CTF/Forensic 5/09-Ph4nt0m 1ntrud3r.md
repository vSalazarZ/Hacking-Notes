## Descripción 
A digital ghost has breached my defenses, and my sensitive data has been stolen! 😱💻 Your mission is to uncover how this phantom intruder infiltrated my system and retrieve the hidden flag.To solve this challenge, you'll need to analyze the provided PCAP file and track down the attack method. The attacker has cleverly concealed his moves in well timely manner. Dive into the network traffic, apply the right filters and show off your forensic prowess and unmask the digital intruder!Find the PCAP file here [Network Traffic PCAP file](https://challenge-files.picoctf.net/c_verbal_sleep/960abba2fdbc9be5013ef87f1df67213e9b63d4561d7a8c8c1ce7a4ce40a547e/myNetworkTraffic.pcap) and try to get the flag.

Hint:
1. Filter your packets to narrow down your search.
2. Attacks were done in timely manner.
3. Time is essential

## Solución 

Descargamos el archivo .pcap y lo abrimos con el wireshark, vemos los paquetes y nos damos cuenta que algunos archivos, en especial los de longitud 12 y 4, tienen en su contenido pequeños trozos de codificaciones en base64, las pistas nos dicen que el tiempo es esencial por lo tanto, filtramos por longitud 4 y 12 y acomodamos por tiempo, sacamos el contenido de los paquetes y decodificamos con cyberchef

```
Usando cyberchef

Input:  cGljb0NURg==
		ezF0X3c0cw==
		bnRfdGg0dA==
		XzM0c3lfdA==
		YmhfNHJfZQ==
		NWU4Yzc4ZA==
		fQ==

Recipe: From Base64

Output: picoCTF{1t_w4snt_th4t_34sy_tbh_4r_e5e8c78d}
```

## Referencias
https://gchq.github.io/CyberChef/