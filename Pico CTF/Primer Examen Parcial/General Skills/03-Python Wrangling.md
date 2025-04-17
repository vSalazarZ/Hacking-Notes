## Descripción 
Python scripts are invoked kind of like programs in the Terminal... Can you run [this Python script](https://mercury.picoctf.net/static/0bf545252b5120845e3b568b9ad0277e/ende.py) using [this password](https://mercury.picoctf.net/static/0bf545252b5120845e3b568b9ad0277e/pw.txt) to get [the flag](https://mercury.picoctf.net/static/0bf545252b5120845e3b568b9ad0277e/flag.txt.en)?

Hint:
1. Get the Python script accessible in your shell by entering the following command in the Terminal prompt: `$ wget https://mercury.picoctf.net/static/0bf545252b5120845e3b568b9ad0277e/ende.py`
2. $ man python
## Solución 1

Descargamos los 3 archivos con wget, visualizamos los archivos con cat, el programa pide una contraseña, vemos la contraseña y después con un cat corremos el programa principal y metemos la contraseña para obtener la bandera

```
omarsalazar@DESKTOP-H97NF1C:~$ wget https://mercury.picoctf.net/static/0bf545252b5120845e3b568b9ad0277e/ende.py
--2025-04-15 20:41:16--  https://mercury.picoctf.net/static/0bf545252b5120845e3b568b9ad0277e/ende.py
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1328 (1.3K) [application/octet-stream]
Saving to: ‘ende.py’

ende.py                       100%[=================================================>]   1.30K  --.-KB/s    in 0s

2025-04-15 20:41:16 (249 MB/s) - ‘ende.py’ saved [1328/1328]

omarsalazar@DESKTOP-H97NF1C:~$ wget https://mercury.picoctf.net/static/0bf545252b5120845e3b568b9ad0277e/flag.txt.en
--2025-04-15 20:41:21--  https://mercury.picoctf.net/static/0bf545252b5120845e3b568b9ad0277e/flag.txt.en
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 140 [application/octet-stream]
Saving to: ‘flag.txt.en’

flag.txt.en                   100%[=================================================>]     140  --.-KB/s    in 0s

2025-04-15 20:41:21 (116 MB/s) - ‘flag.txt.en’ saved [140/140]

omarsalazar@DESKTOP-H97NF1C:~$ wget https://mercury.picoctf.net/static/0bf545252b5120845e3b568b9ad0277e/pw.txt
--2025-04-15 20:41:25--  https://mercury.picoctf.net/static/0bf545252b5120845e3b568b9ad0277e/pw.txt
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 33 [application/octet-stream]
Saving to: ‘pw.txt’

pw.txt                        100%[=================================================>]      33  --.-KB/s    in 0s

2025-04-15 20:41:25 (24.5 MB/s) - ‘pw.txt’ saved [33/33]

omarsalazar@DESKTOP-H97NF1C:~$ cat ende.py

import sys
import base64
from cryptography.fernet import Fernet



usage_msg = "Usage: "+ sys.argv[0] +" (-e/-d) [file]"
help_msg = usage_msg + "\n" +\
        "Examples:\n" +\
        "  To decrypt a file named 'pole.txt', do: " +\
        "'$ python "+ sys.argv[0] +" -d pole.txt'\n"



if len(sys.argv) < 2 or len(sys.argv) > 4:
    print(usage_msg)
    sys.exit(1)



if sys.argv[1] == "-e":
    if len(sys.argv) < 4:
        sim_sala_bim = input("Please enter the password:")
    else:
        sim_sala_bim = sys.argv[3]

    ssb_b64 = base64.b64encode(sim_sala_bim.encode())
    c = Fernet(ssb_b64)

    with open(sys.argv[2], "rb") as f:
        data = f.read()
        data_c = c.encrypt(data)
        sys.stdout.write(data_c.decode())


elif sys.argv[1] == "-d":
    if len(sys.argv) < 4:
        sim_sala_bim = input("Please enter the password:")
    else:
        sim_sala_bim = sys.argv[3]

    ssb_b64 = base64.b64encode(sim_sala_bim.encode())
    c = Fernet(ssb_b64)

    with open(sys.argv[2], "r") as f:
        data = f.read()
        data_c = c.decrypt(data.encode())
        sys.stdout.buffer.write(data_c)


elif sys.argv[1] == "-h" or sys.argv[1] == "--help":
    print(help_msg)
    sys.exit(1)


else:
    print("Unrecognized first argument: "+ sys.argv[1])
    print("Please use '-e', '-d', or '-h'.")

omarsalazar@DESKTOP-H97NF1C:~$ cat pw.txt
6008014f6008014f6008014f6008014f
omarsalazar@DESKTOP-H97NF1C:~$ python3 ende.py -d flag.txt.en
Please enter the password:6008014f6008014f6008014f6008014f
picoCTF{4p0110_1n_7h3_h0us3_6008014f}
omarsalazar@DESKTOP-H97NF1C:~$

flag: picoCTF{4p0110_1n_7h3_h0us3_6008014f}
```
