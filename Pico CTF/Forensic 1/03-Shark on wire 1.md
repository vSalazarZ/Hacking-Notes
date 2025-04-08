## Descripción 
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap). Recover the flag.

Hint:
1. Try using a tool like Wireshark
2. What are streams?
## Solución 1

Descargamos el wireshark y el archivo del ejercicio de pico, lo descargamos con wget en consola y abrimos el wireshark. Nos vamos a los paquetes UDP y miramos el contenido de estos paquetes y vamos a encontrar la bandera en uno de estos paquetes

```
omarsalazar@DESKTOP-H97NF1C:~$ wget https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap
--2025-04-07 13:01:04--  https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 239455 (234K) [application/octet-stream]
Saving to: ‘capture.pcap’

capture.pcap                  100%[=================================================>] 233.84K   950KB/s    in 0.2s

2025-04-07 13:01:05 (950 KB/s) - ‘capture.pcap’ saved [239455/239455]

omarsalazar@DESKTOP-H97NF1C:~$ wireshark capture.pcap
 ** (wireshark:5333) 13:01:12.927232 [GUI CRITICAL] -- Failed to create wl_display (No such file or directory)
nl80211 not found.

Vamos a paquetes UDP y miramos el contenido de esos paquetes y buscamos de uno por uno hasta encontrar la bandera

flag: picoCTF{StaT31355_636f6e6e}
```
