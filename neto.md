# Korištenje Pythona pri ispitivanju svojstava binarne relacije nad zadanim skupom

## Opći podaci projekta:
**Predmet:** Matematika 1  
**Studenti:** Tin Pritišanac, Neven Davidović, Noel Modrušan  
**Vrsta projekta:** Računalno riješen matematički problem  
**Programski jezik:** Python  
**Literatura:** Papić, P., Uvod u teoriju skupova, HMD, 2000.  

_____________________________________________________________________________
### Sažetak

U ovom projektu smo izradili računalni program u programskom jeziku Python koji će na temelju korisnikovog unosa parova binarne relacije ispitati njena svojstva (refleksivnost, simetričnost, asimetričnost, antisimetričnost, tranzitivnost) te korisniku jasno naznačiti rezultate ovog ispitivanja.
Cilj izrade ove vrste programa je da se koristi za brzu provjeru rješenja zadataka iz područja binarnih relacija nad skupovima, te brže rješavanje dužih tipova zadataka. Isto tako korisniku želimo prikazati razloge zbog kojih su pojedina svojstva točna ili netočna, kako bi stekao bolje razumijevanje procesa ispitivanja binarnih relacija nad zadanim skupom. 

_____________________________________________________________________________

### Opis programa

Program se sastoji od zasebnih funkcija čija je zadaća ispitati svojstva binarne relacije. Korisniku su dostupne mogućnosti unosa nove liste parova, brisanje postojećih i dodavanje novih parova, nakon čega će se ponovo ispisati odgovarajući rezultat. 
Svaka od funkcija ispituje po jedno svojstvo binarne relacije te vraća tip podatka *bool* glavnoj funkciji iz koje su pozvane. Ono što prethodi vraćanju rezultata je grafički prikaz odnosa uređenih parova unutar same konzole. 
_____________________________________________________________________________
**Struktura programa:**
1. [Funkcija za unos podataka](-1.-Funkcija-za-unos-podataka)
2. [Funkcija za ispitivanje tranzitivnosti binarne relacije](-2.-Funkcija-za-ispitivanje-tranzitivnosti-binarne-relacije)
3. [Funkcija za ispitivanje refleksivnosti binarne relacije](-3.-Funkcija-za-ispitivanje-refleksivnosti-binarne-relacije)
4. [Funkcija za ispitivanje antirefleksivnosti binarne relacije](-4.-Funkcija-za-ispitivanje-antirefleksivnosti-binarne-relacije)
5. [Funkcija za ispitivanje simetričnosti binarne relacije](-5.-Funkcija-za-ispitivanje-simetričnosti-binarne-relacije)
6. [Funkcija za ispitivanje antisimetričnosti binarne relacije](-6.-Funkcija-za-ispitivanje-antisimetričnosti-binarne-relacije)
7. [Glavna funkcija](-7.-Glavna-funkcija)


**Ostale značajke:**
- Grafički prikaz uređenih parova unutar tablice
- Nasumično generiranje zadataka
- Ispis rezultata u tekstualnu datoteku

____

### 1. Funkcija za unos podataka




Jednostavna funkcija koja traži od korisnika unos elemenata skupa, broj parova i same parove.

| Algoritam: | 
| -------- | 
| 1. Unos elemenata skupa
|2. Učitavanje željenog broja uređenih parova
| 3. Unos uređenih parova     |

----
### 2. Funkcija za ispitivanje tranzitivnosti binarne relacije



| Algoritam                                         |
| ------------------------------------------------- |
| 1. Funkcija uzima kao parametar listu parova      |
| 2.Uspoređuje elemente na indexu  [1] i indexu [0] |
| 3.                                                   |
|                                                   |
|                                                   |
|                                                   |
|                                                   |


```python=
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
### 3. Funkcija za ispitivanje refleksivnosti binarne relacije
```python=
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
### 4. Funkcija za ispitivanje antirefleksivnosti binarne relacije

```python=
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
### 5. Funkcija za ispitivanje simetričnosti binarne relacije
```python=
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
### 6. Funkcija za ispitivanje antisimetričnosti binarne relacije
```python=
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
### 7. Glavna funkcija

Glavna funkcija()

----
**Ostale značajke:**
- Grafički prikaz uređenih parova unutar tablice
- Nasumično generiranje zadataka
- Ispis rezultata u tekstualnu datoteku


____
## Zaključak

---
[Povratak na vrh](-Opći-podaci-projekta)



