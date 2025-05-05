## Descripción 
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/capture.pcap) and [key](https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/picopico.key). Recover the flag.

Hint:
1. Try using a tool like Wireshark.
2. How can you decrypt the TLS stream?
## Solución 1

Descargamos los archivos, después abrimos el wireshark e intentamos buscar el follow TLS que contenga la bandera, si no lo encontramos en las preferencias de TLS ingresamos la key y vemos que hay un archivo jpg, lo descargamos y lo abrimos en la terminal, después miramos el contenido de esa imagen y ahí adentro está la bandera 

```
omarsalazar@DESKTOP-H97NF1C:~$ wget https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/capture.pcap
--2025-05-05 11:28:52--  https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/capture.pcap
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 92525 (90K) [application/octet-stream]
Saving to: ‘capture.pcap’

capture.pcap                  100%[=================================================>]  90.36K   442KB/s    in 0.2s

2025-05-05 11:28:53 (442 KB/s) - ‘capture.pcap’ saved [92525/92525]

omarsalazar@DESKTOP-H97NF1C:~$ wget https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/picopico.key
--2025-05-05 11:28:59--  https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/picopico.key
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1704 (1.7K) [application/octet-stream]
Saving to: ‘picopico.key’

picopico.key                  100%[=================================================>]   1.66K  --.-KB/s    in 0s

2025-05-05 11:29:00 (279 MB/s) - ‘picopico.key’ saved [1704/1704]

omarsalazar@DESKTOP-H97NF1C:~$ wireshark capture.pcap
 ** (wireshark:632) 11:31:16.497913 [GUI CRITICAL] -- Failed to create wl_display (No such file or directory)
nl80211 not found.
^Z
[1]+  Stopped                 wireshark capture.pcap
omarsalazar@DESKTOP-H97NF1C:~$ open vulture.jpg
omarsalazar@DESKTOP-H97NF1C:~$ strings vulture.jpg

flag: picoCTF{honey.roasted.peanuts}
```

## Referencias 
https://en.wikipedia.org/wiki/Transport_Layer_Security