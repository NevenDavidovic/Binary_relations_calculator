## Funkcija za ispitivanje svojstava binarnih relacija nad skupom

Ova funkcija je logička jedinica koja povezuje sve druge funkcije i na temelju njihovih rezultata ispisuje konačni rezultat u konzolu i datoteku "Relacije.txt"

Pozivaju se funkcije za ispitivanje svakog pojedinog svojstva binarne relacije nad skupom te sprema vrijednost **bool** koje te funkcije vraćaju u pripadajuću varijablu.

Primjer 1:
```python
#testiranje tranzitivnosti
tranzitivna = tranzitivnost(listaParova) #vraća True ili False

#testiranje simetricnosti
simetricna = simetricnost(listaParova) #vraća True ili False
...
```
Neka svojstva se testiraju ovisno o drugim svojstvima. 

Primjer 2: 

> Antirefleksivnost se testira ovisno o refleksivnosti koja se testira prva.
> Naime ako je funkcija refleksivna, ne može biti antirefleksivna, stoga nije potrebno dalje testirati pozivajući funkciju **antirefleksivnost()**


```python
#testiranje refleksivnosti i antirefleksivnosti
    refleksivna = refleksivnost(skupA,listaParova)
    if refleksivna:
        with open('Relacije.txt', 'a') as f: 
            print('Antirefleksivna: NE jer je refleksivna')
            print('Antirefleksivna: NE jer je refleksivna', file=f)
        antirefleksivna = False
    else: antirefleksivna = antirefleksivnost(skupA,listaParova)
```

Asimetričnost ovisi o drugim svojstvima, i ovisno o njima drugačiji će razlozi biti prikazani.

```python
#testiranje asimetričnosti
    if (simetricna):
        with open('Relacije.txt', 'a') as f:
            print('Asimetricna: NE jer je simetricna')
            print('Asimetricna: NE jer je simetricna',file=f)
    elif (antisimetricna and antirefleksivna):
        with open('Relacije.txt', 'a') as f:
            print('Asimetricna: DA jer je antisimetricna i antirefleksivna')
            print('Asimetricna: DA jer je antisimetricna i antirefleksivna',file=f)
    elif (antisimetricna and not antirefleksivna):
        with open('Relacije.txt', 'a') as f:
            print('Asimetricna: NE jer nije antirefleksivna')
            print('Asimetricna: NE jer nije antirefleksivna',file=f)
    elif (not antisimetricna and not antirefleksivna):
        with open('Relacije.txt', 'a') as f:
            print('Asimetricna: NE jer nije antirefleksivna niti antisimetricna')
            print('Asimetricna: NE jer nije antirefleksivna niti antisimetricna',file=f)
    else:
        with open('Relacije.txt', 'a') as f:
            print('Asimetricna: NE jer nije antisimetricna')
            print('Asimetricna: NE jer nije antisimetricna',file=f)
```

- Najprije se provjerava je li relacija **simetrična**, ako jest ne može biti asimetrična
- Ako je **antisimetrična i antirefleksivna** relacija je asimetrična
- Ako je **antisimetrična ali NE i antirefleksivna** relacija nije asimetrična jer nije antirefleksivna
- Ako **nije niti antisimetrična niti antirefleksivna** relacija nije asimetrična jer nije antirefleksivna niti antisimetricna
- Relacija nije asimetrična jer nije antisimetrična

Također testiraju se i svojstva ekvivalencije i vrsta uređaja.

```python
with open('Relacije.txt', 'a') as f:
        #ispitivanje ekvivalencije
        if refleksivna and simetricna and tranzitivna:
            print('Relacija ekvivalencije: DA - Relacija je tranzitivna, simetricna i refleksivna')
            print('Relacija ekvivalencije: DA - Relacija je tranzitivna, simetricna i refleksivna',file=f)

        #ispitivanje relacije uređaja
        if tranzitivna and antirefleksivna and antisimetricna: 
            print('Strogi uređaj! Antirefleksivna, tranzitivna, antisimetricna')
            print('Strogi uređaj! Antirefleksivna, tranzitivna, antisimetricna',file=f)
        elif tranzitivna and refleksivna and antisimetricna:
            print('Parcijalni uređaj! Refleksivna, tranzitivna, antisimetricna')
            print('Parcijalni uređaj! Refleksivna, tranzitivna, antisimetricna',file=f)
```

**Ukupni rezultat** koji će biti prikazan u konzoli i ispisan u datoteku je slijedećeg formata:

<pre>
Binarna relacija je:

Svojstvo1: DA|NE <b>prvi razlog</b> zbog kojega je svojstvo True ili False
Svojstvo2: DA|NE <b>prvi razlog</b> zbog kojega je svojstvo True ili False
...
</pre>

> Kao rezultat daje se samo **prvi razlog** zbog kojega je pojedino svojstvo istinito ili ne. Razlog je optimizacija, jer se podprogram
> prekida kada je došao do riješenja


Primjer 3:
```txt
Binarna relacija je:

Tranzitivna: NE jer za (b, j) i (j, t) ne postoji (b, t) unutar liste parova
Refleksivna: NE jer za element "b" ne postoji par (b, b) unutar liste parova
Antirefleksivna: NE jer za element "o" postoji par (o, o) unutar liste parova
Simetricna: NE jer za (b, j) ne postoji (j, b) unutar liste parova
Antisimetricna: DA
Asimetricna: NE jer nije antirefleksivna
```


