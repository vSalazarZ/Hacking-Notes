## Descripción 
Want to play a game? As you use more of the shell, you might be interested in how they work! Binary search is a classic algorithm used to quickly find an item in a sorted list. Can you find the flag? You'll have 1000 possibilities and only 10 guesses.Cyber security often has a huge amount of data to look through - from logs, vulnerability reports, and forensics. Practicing the fundamentals manually might help you in the future when you have to write your own tools!You can download the challenge files here:
- [challenge.zip](https://artifacts.picoctf.net/c_atlas/4/challenge.zip)
`ssh -p 52121 ctf-player@atlas.picoctf.net`Using the password `83dcefb7`. Accept the fingerprint with `yes`, and `ls` once connected to begin. Remember, in a shell, passwords are hidden!

Hint:
1. Have you ever played hot or cold? Binary search is a bit like that.
2. You have a very limited number of guesses. Try larger jumps between numbers!
3. The program will randomly choose a new number each time you connect. You can always try again, but you should start your binary search over from the beginning - try around 500. Can you think of why?
## Solución 1

Con consola linux
Es un ejercicio a prueba y error, intentado adivinar el numero con un numero limitado de intentos

```
vSalazarZ-picoctf@webshell:~$ ssh -p 52121 ctf-player@atlas.picoctf.net
The authenticity of host '[atlas.picoctf.net]:52121 ([18.217.83.136]:52121)' can't be established.
ED25519 key fingerprint is SHA256:M8hXanE8l/Yzfs8iuxNsuFL4vCzCKEIlM/3hpO13tfQ.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[atlas.picoctf.net]:52121' (ED25519) to the list of known hosts.
ctf-player@atlas.picoctf.net's password: 
Welcome to the Binary Search Game!
I'm thinking of a number between 1 and 1000.
Enter your guess: 500
Lower! Try again.
Enter your guess: 400
Lower! Try again.
Enter your guess: 300
Lower! Try again.
Enter your guess: 250
Lower! Try again.
Enter your guess: 200
Lower! Try again.
Enter your guess: 100
Higher! Try again.
Enter your guess: 150
Lower! Try again.
Enter your guess: 140
Lower! Try again.
Enter your guess: 130
Lower! Try again.
Enter your guess: 120
Lower! Try again.
Sorry, you've exceeded the maximum number of guesses.
Connection to atlas.picoctf.net closed.
vSalazarZ-picoctf@webshell:~$ ssh -p 52121 ctf-player@atlas.picoctf.net
ctf-player@atlas.picoctf.net's password: 
Permission denied, please try again.
ctf-player@atlas.picoctf.net's password: 
Welcome to the Binary Search Game!
I'm thinking of a number between 1 and 1000.
Enter your guess: 500
Lower! Try again.
Enter your guess: 250
}Higher! Try again.
Enter your guess: 375
Please enter a valid number.
Enter your guess: 375
Lower! Try again.
Enter your guess: 300
Lower! Try again.
Enter your guess: 178
Higher! Try again.
Enter your guess: 192
Higher! Try again.
Enter your guess: 199
Higher! Try again.
Enter your guess: 205 
Lower! Try again.
Enter your guess: 200
Higher! Try again.
Enter your guess: 202
Higher! Try again.
Sorry, you've exceeded the maximum number of guesses.
Connection to atlas.picoctf.net closed.
vSalazarZ-picoctf@webshell:~$ 
vSalazarZ-picoctf@webshell:~$ ssh -p 52121 ctf-player@atlas.picoctf.net
ctf-player@atlas.picoctf.net's password: 
Welcome to the Binary Search Game!
I'm thinking of a number between 1 and 1000.
Enter your guess: 500
Higher! Try again.
Enter your guess: 750
Higher! Try again.
Enter your guess: 800
Higher! Try again.
Enter your guess: 850
Lower! Try again.
Enter your guess: 825
Lower! Try again.
Enter your guess: 815
Higher! Try again.
Enter your guess: 818
Higher! Try again.
Enter your guess: 123
Higher! Try again.
Enter your guess: 823
Lower! Try again.
Enter your guess: 820
Higher! Try again.
Sorry, you've exceeded the maximum number of guesses.
Connection to atlas.picoctf.net closed.
vSalazarZ-picoctf@webshell:~$ ssh -p 52121 ctf-player@atlas.picoctf.net
ctf-player@atlas.picoctf.net's password: 
Welcome to the Binary Search Game!
I'm thinking of a number between 1 and 1000.
Enter your guess: 500
Lower! Try again.
Enter your guess: 250
Lower! Try again.
Enter your guess: 125
Higher! Try again.
Enter your guess: 200
Lower! Try again.
Enter your guess: 175
Lower! Try again.
Enter your guess: 150
Lower! Try again.
Enter your guess: 132
Higher! Try again.
Enter your guess: 137
Higher! Try again.
Enter your guess: 142
Higher! Try again.
Enter your guess: 145
Lower! Try again.
Sorry, you've exceeded the maximum number of guesses.
Connection to atlas.picoctf.net closed.
vSalazarZ-picoctf@webshell:~$ ssh -p 52121 ctf-player@atlas.picoctf.net
ctf-player@atlas.picoctf.net's password: 
Welcome to the Binary Search Game!
I'm thinking of a number between 1 and 1000.
Enter your guess: 500
Lower! Try again.
Enter your guess: 250
Lower! Try again.
Enter your guess: 125
Higher! Try again.
Enter your guess: 175
Lower! Try again.
Enter your guess: 150
Lower! Try again.
Enter your guess: 135
Lower! Try again.
Enter your guess: 128
Lower! Try again.
Enter your guess: 126
Higher! Try again.
Enter your guess: 127
Congratulations! You guessed the correct number: 127
Here's your flag: picoCTF{g00d_gu355_ee8225d0}
Connection to atlas.picoctf.net closed.
vSalazarZ-picoctf@webshell:~$ 

flag: picoCTF{g00d_gu355_ee8225d0}
```
