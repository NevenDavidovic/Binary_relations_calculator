# Ispis rezultata

Ispis sadržava:
- vrijeme i datum  
- naziv programa   
- uneseni skup i unesene parove  
- grafički prikaz   
- rezultat koji govori koja svojstva ima binarna relacija          
  
 _____________________________________________________________________ 
 **Programski kod za ispis skupa i uređenih parova te grafičkog prikaza**
   ```python
   def ispisUlaznihPodataka():
    print('\nUneseni parovi su:')
    print(formatStr(listaParova))
    #ispis skupa
    stringSkupa = str(skupA).replace("[","{").replace("]","}")
    print(f'\nSkup A = {stringSkupa}')

    #ispis u file
    with open('Relacije.txt', 'a') as f:
        print('\nUneseni parovi su:', file=f)
        print(formatStr(listaParova), file=f)
        print(f'\nSkup A = {stringSkupa}', file=f)
    #graficki prikaz relacije
    graficki(listaParova,skupA)
   ```
  
____________________________________________________________________________  
      
**Primjer jednog ispisa**
```

Lokalno vrijeme: Thu Feb 10 23:25:32 2022
__________Dobrodosli u Ispitivac binarnih relacija v1.0__________

Lokalno vrijeme: Thu Feb 10 23:27:35 2022
__________Dobrodosli u Ispitivac binarnih relacija v1.0__________

Uneseni parovi su:
(d, d), (v, v), (k, n), (k, k)

Skup A = {'n', 'd', 'v', 'k', 'x'}

  d k n v x  
d x . . . .
k . x x . .
n . . . . .
v . . . x .
x . . . . .

Binarna relacija je:

Tranzitivna: DA
Refleksivna: NE jer za element "n" ne postoji par (n, n) unutar liste parova
Antirefleksivna: NE jer za element "d" postoji par (d, d) unutar liste parova
Simetricna: NE jer za (k, n) ne postoji (n, k) unutar liste parova
Antisimetricna: DA
Asimetricna: NE jer nije antirefleksivna

```
