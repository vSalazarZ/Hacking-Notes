## Descripción 
Now you DON’T see me.This [report](https://artifacts.picoctf.net/c/84/Financial_Report_for_ABC_Labs.pdf) has some critical data in it, some of which have been redacted correctly, while some were not. Can you find an important key that was not redacted properly?

Hint:
1. How can you be sure of the redaction?

## Solución 

Descargamos el reporte y analizamos el pdf, tiene cubiertas con bandas negras unos textos, pero se pueden copiar y pegar en un editor txt y nos enseña su contenido, hacemos eso con todas la bandas y llegamos a encontrar la bandera

```
Financial Report for ABC Labs, Kigali, Rwanda for the year 2021. Breakdown - Just painted over in MS word. Cost Benefit Analysis Credit Debit This is not the flag, keep looking Expenses from the picoCTF{C4n_Y0u_S33_m3_fully} Redacted document.

flag: picoCTF{C4n_Y0u_S33_m3_fully}
```
