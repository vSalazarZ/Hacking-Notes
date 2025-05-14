## Descripción 
We made a lot of substitutions to encrypt this. Can you decrypt it? Connect with `nc jupiter.challenges.picoctf.org 43522`.

Hint:
1. Flag is not in the usual flag format
## Solución 1

Nos conectamos al servidor y observamos que hay un texto codificado y la descripción del ejercicio nos dice que busquemos un sustituto de desencriptamiento, buscamos y damos con uno, ponemos el texto que se nos da y obtenemos la bandera del ejercicio

```
Input: -------------------------------------------------------------------------------
xqhcbkoz ymbm iz aqjb rwkc - rbmtjmhxa_iz_x_qsmb_wkngfk_qcrnkjhbkr
-------------------------------------------------------------------------------
lm lmbm hqo njxy nqbm oykh k tjkbomb qr kh yqjb qjo qr qjb zyiv oiww lm zkl ymb zihd, khf oymh i jhfmbzoqqf rqb oym ribzo oinm lyko lkz nmkho ga k zyiv rqjhfmbihc ih oym zmk.  i njzo kxdhqlwmfcm i ykf ykbfwa mamz oq wqqd jv lymh oym zmknmh oqwf nm zym lkz zihdihc; rqb rbqn oym nqnmho oyko oyma bkoymb vjo nm ihoq oym gqko oykh oyko i nicyo gm zkif oq cq ih, na ymkbo lkz, kz io lmbm, fmkf lioyih nm, vkbowa lioy rbicyo, vkbowa lioy yqbbqb qr nihf, khf oym oyqjcyoz qr lyko lkz amo gmrqbm nm.

Output:
|------------------------------------------------------------------------------- congrats here is your flag - frequency_is_c_over_lambda_ogfmaunraf ------------------------------------------------------------------------------- we were not much more than a quarter of an hour out of our ship till we saw her sink, and then i understood for the first time what was meant by a ship foundering in the sea. i must acknowledge i had hardly eyes to look up when the seamen told me she was sinking; for from the moment that they rather put me into the boat than that i might be said to go in, my heart was, as it were, dead within me, partly with fright, partly with horror of mind, and the thoughts of what was yet before me.|

flag: frequency_is_c_over_lambda_ogfmaunraf
```

## Referencias
1. https://quipqiup.com/