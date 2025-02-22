## Descripción 
How well can you perfom basic binary operations?Start searching for the flag here `nc titan.picoctf.net 49793`
## Solución 1

Con consola linux y calculadora binaria online
Nos conectamos al servidor mediante ssh y este nos va dar a realizar operaciones binarias, después de hacerlas todas (6), nos pedirá que transformemos el último resultado a hexadecimal

```
vSalazarZ-picoctf@webshell:~$ nc titan.picoctf.net 49793

Welcome to the Binary Challenge!"
Your task is to perform the unique operations in the given order and find the final result in hexadecimal that yields the flag.

Binary Number 1: 00110101
Binary Number 2: 10100110


Question 1/6:
Operation 1: '>>'
Perform a right shift of Binary Number 2 by 1 bits .
Enter the binary result: 1010011
Correct!

Question 2/6:
Operation 2: '<<'
Perform a left shift of Binary Number 1 by 1 bits.
Enter the binary result: 1101010
Correct!

Question 3/6:
Operation 3: '*'
Perform the operation on Binary Number 1&2.
Enter the binary result: 10001001011110
Correct!

Question 4/6:
Operation 4: '+'
Perform the operation on Binary Number 1&2.
Enter the binary result: 11011011
Correct!

Question 5/6:
Operation 5: '|'
Perform the operation on Binary Number 1&2.
Enter the binary result: 10110111
Correct!

Question 6/6:
Operation 6: '&'
Perform the operation on Binary Number 1&2.
Enter the binary result: 00100100
Correct!

Enter the results of the last operation in hexadecimal: 24

Correct answer!
The flag is: picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_6862762d}

```
## Referencias 
https://www.rapidtables.com/calc/math/binary-calculator.html?num1=00110101&op=5&num2=10100110