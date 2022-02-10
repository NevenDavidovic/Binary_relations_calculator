# Korištenje Pythona pri ispitivanju svojstava binarne relacije nad zadanim skupom
<a id="top"></a>
## Opći podaci projekta:
**Predmet:** Matematika 1  
**Studenti:** Tin Pritišanac, Neven Davidović, Noel Modrušan  
**Vrsta projekta:** Računalno riješen matematički problem  
**Ime programa:** Ispitivac binarnih relacija v1.0  
**Programski jezik:** Python  
**Literatura:** Papić, P., Uvod u teoriju skupova, HMD, 2000.  

_____________________________________________________________________________
### Sažetak

U ovom projektu smo izradili računalni program u programskom jeziku Python koji će na temelju korisnikovog unosa ili generiranog nasumičnog skupa parova binarne relacije  ispitati njena svojstva (refleksivnost, simetričnost, asimetričnost, antisimetričnost, tranzitivnost) te korisniku jasno naznačiti rezultate ovog ispitivanja.  
Cilj izrade ove vrste programa je da se koristi za brzu provjeru rješenja zadataka iz područja binarnih relacija nad skupovima, te brže rješavanje dužih tipova zadataka. Isto tako korisniku želimo prikazati razloge zbog kojih su pojedina svojstva točna ili netočna, kako bi stekao bolje razumijevanje procesa ispitivanja binarnih relacija nad zadanim skupom. 

_____________________________________________________________________________

### Opis programa

Program počinje sa izbornikom koji omogućava korisniku da ili sam izabere skup i uređene parove ili da to program napravi umjesto njega.
Osim izbornika program se sastoji od zasebnih funkcija čija je zadaća ispitati svojstva binarne relacije. Korisniku su dostupne mogućnosti unosa nove liste parova, brisanje postojećih i dodavanje novih parova, nakon čega će se ponovo ispisati odgovarajući rezultat. 
Svaka od funkcija ispituje po jedno svojstvo binarne relacije te vraća tip podatka *bool* glavnoj funkciji iz koje su pozvane.   Ono što prethodi vraćanju rezultata je grafički prikaz odnosa uređenih parova unutar same konzole.  
Nakon provjere nad zadanim skupom i listom parova rezultati se ispisuju u tekstualnu datoteku. 
_____________________________________________________________________________
**Struktura programa:**  
Pomoćne funkcije:
 
 <a href="#1">Funkcija za unos podataka</a>
 
 <a href="#2">Funkcija za ispitivanje tranzitivnosti binarne relacije</a>  
 <a href="#3">Funkcija za ispitivanje refleksivnosti binarne relacije</a>  
 <a href="#4">Funkcija za ispitivanje antirefleksivnosti binarne relacije</a>  
 <a href="#5">Funkcija za ispitivanje simetričnosti binarne relacije</a>  
 <a href=#6>Funkcija za ispitivanje antisimetričnosti binarne relacije</a>  
 <a href=#7>Glavna funkcija</a>  


**Ostale značajke:**
- Grafički prikaz uređenih parova unutar tablice
- Nasumično generiranje zadataka
- Ispis rezultata u tekstualnu datoteku

____

###  Funkcija za unos podataka <a id="1"></a>




Jednostavna funkcija koja traži od korisnika unos elemenata skupa, broj parova i same parove. Ovako unešeni podaci služe kao parametri funkcijama.

| Algoritam: | 
| -------- | 
| 1. Unos elemenata skupa
|2. Učitavanje željenog broja uređenih parova
| 3. Unos uređenih parova     |

----
###  Funkcija za ispitivanje tranzitivnosti binarne relacije <a id="2"></a>
Binarna relacija je relacija sa svojstvom da ako su **(x,y)∈A i (y,z)∈A** tada mora biti i da su **(x,z)∈A**.


|   Algoritam:                                           |
|:--------------------------------------------------- |
| 1. Funkcija uzima kao parametar listu parova        |
| 2. Uspoređuje elemente na indexu  [1] i indexu [0]  |
| 3. Ako su isti preskoči na drugi par u listi parova |
| 4.  Ako nisu spremi ih u listu B                    |
|                                                     |
|                                                     |
|                                                     |
|                                                     |


*Programski kod:*
```python
#Funkcija koja provjerava tranzitivnost binarne relacije

def tranzitivnost(listaParova:list)->bool:
    print('Tranzitivna:',end=' ')
    for element in listaParova:
        if element[0]==element[1]: continue
        B = list(e for e in listaParova if e[0]==element[1])
        if len(B) == 0: continue
        #ispitaj postoji li u orignialnoj listi (listaParova) implicirani član (ako su xRy i yRz, postoji li xRz)
        for e in B:
            implicElement = (element[0],e[1])
            # ako takav element nije pronađen Relacija nije tranzitivna - vrati False inače vrati True
            if not implicElement in listaParova: 
                print(f"NE jer za {formatStr(element)} i {formatStr(e)} ne postoji {formatStr(implicElement)} unutar liste parova")
                return False
    print("DA")
    return True

```

----
###  Funkcija za ispitivanje refleksivnosti binarne relacije <a id="3"></a>
Relacija je **refleksivna** ako za **∀x∈A :(xRx)** .To znači da je relacija refleksivna ako je element u odnosu sam sa sobom. 
Ispitivanje refleksivnosti relacije smo programski riješili uz pomoć dolje navedenog algoritma. 


| Algoritam                                                                         |
| --------------------------------------------------------------------------------- |
| 1. Funkcija prima 2 parametra (skupA i listaParova )                              |
| 2. Za svaki element u skupu A, stvori uređeni par s istim elementom |
| 3. Usporedi takav par sa parovima u listi parova                                  |
| 4. Ako jedan od tako stvorenih parova nije u listi vrati *False*                    |
| 5. Ako su pak svi tako stvoreni parovi unutar liste parova                        |
| 6.  Ispiši na ekran "DA"                                                                               |
| 7.  Vrati *True*                                                                            |

*Programski kod:*
```python
#Funkcija koja provjerava refleksivnost binarne relacije

def refleksivnost(skupA:list,listaParova:list)->bool:
    print('Refleksivna:',end=' ')
    # za svaki x ∈ skupa A u mora postojati (x,x) u listi parova 
    for element in skupA:
        trazeniE = (element[0],element[0])
        if not trazeniE in listaParova:
            print(f'NE jer za element "{element}" ne postoji par {formatStr(trazeniE)} unutar liste parova')
            return False
    print("DA")
    return True
```
----
###  Funkcija za ispitivanje antirefleksivnosti binarne relacije <a id="4"></a>

Binarna je relacija **antirefleksivna** ako za **∀x∈A: ~(xRx)**. To znači da niti jedan element nekog zajedničkog skupa nije u u odnosu sam sa sobom.

| Algoritam                                        |
| ------------------------------------------------ |
| 1. Funkcija prima 2 parametra(skupA i listaParova )                                                |
| 2. Za svaki element u skupu A, stvori uređeni par s istim elementom                                                 |
| 3. Ukoliko je najmanje jedan takav par u listi parova                                                 |
| 4. Ispiši ne                                                 |
| 5. Vrati *False* 
|6. Ako nema takvog para vrati *True*

*Programski kod:*
```python
def antirefleksivnost(skupA:list,listaParova:list)->bool:
    print('Antirefleksivna:',end=' ')
    # za svaki x ∈ skupa A u NE SMIJE postojati (x,x) u listi parova 
    for element in skupA:
        trazeniE = (element[0],element[0])
        if trazeniE in listaParova:
            print(f'NE jer za element "{element}" postoji par {formatStr(trazeniE)} unutar liste parova')
            return False
    print("DA")
    return True

```
----
###  Funkcija za ispitivanje simetričnosti binarne relacije <a id="5"></a>
Binarna relacija se naziva **simetričnom** ako ima svojstvo da ako je lement x u relaciji sa y, tad ujedno i y u relaciji sa x. To znači ako je uređeni par **(x,y)∈A** onda je i **(y,x)∈A**. 

| Algoritam |
| --------- |
| 1. Funkcija prima 1 parametar( listaParova )          |
| 2. Za svaki element(x,y) u listi parova tvori par sa zamijenjenim elementima (y,x)          |
| 3. Ako barem jedan takav par nije u listi parova vrati *False*          |
| 4. Ako su svi tako tvoreni parovi u listi parova ispiši "DA"         |
| 5. I vrati *True*          |


*Programski kod:*
```python
#Funkcija koja provjerava simetričnost binarne relacije

def simetricnost(listaParova:list)->bool:
    print('Simetrična:',end=' ')
    # za svaki (x,y) mora postojati (y,x) unutar liste parova
    for element in listaParova:
        if element[0] == element[1]: continue
        trazeniE = (element[1],element[0])
        if not trazeniE in listaParova:
            print(f'NE jer za {formatStr(element)} ne postoji {formatStr(trazeniE)} unutar liste parova')
            return False
    print('DA')
    return True

```
----
###  Funkcija za ispitivanje antisimetričnosti binarne relacije <a id="6"></a>

Binarna je relacija antirefleksivna kada ima svojstvo da za **∀x,y∈A:(xRy ∧ yRx)->x=y.** To znači da je relacija antisimetrična za svaki uređeni par koji je dio zajedničkog skupa, ako su elementi unutar uređenog para su jednaki i u relaciji sa sobom.


| Algoritam |
| --------- |
| 1. Funkcija prima listu parova kao parametar(listaParova)           |
| 2. Za svaki x,y u listi parova provjeri          |
| 3. Ako je x==y onda nastavi na kraj petlje           |
| 4. Ako nije tvori par y,x unutar varijable(trazeniE)          |
| 5. Ako je trazeniE u listi ispiši "NE" i razlog te vrati *False*          |
| 6. Ako nije ispiši "DA" 
|7. Vrati *True*

*Programski kod:*
```python
#Funkcija koja provjerava antisimetričnost binarne relacije

def antisimetricnost(listaParova:list)->bool:
    print('Antisimetrična:',end=' ')
    # za svaki (x,y) ne smije postojati (y,x) unutar liste parova osim kada je x==y
    for x,y in listaParova:
        if x==y: continue
        trazeniE = (y,x)
        if trazeniE in listaParova:
            print(f'NE jer za {formatStr((x,y))} postoji {formatStr(trazeniE)} unutar liste parova')
            return False
    print('DA')
    return True   

```
----
###  Glavna funkcija i interpretacija rezultata <a id="7"></a>

Glavna funkcija()

----




## Zaključak

---

<a href="#top">Povratak na vrh</a>



