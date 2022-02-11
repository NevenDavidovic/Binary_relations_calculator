###  Funkcija za unos podataka <a id="1"></a>




Jednostavna funkcija koja traži od korisnika unos elemenata skupa, broj parova i same parove. Ovako unešeni podaci služe kao parametri ostalim funkcijama.


| Algoritam: | 
| -------- | 
| 1. Unos elemenata skupa
| 2. Pretvaranje unešenog stringa u listu i pohrana skupa u listu **SkupA**
| 3. Učitavanje željenog broja uređenih parova koristeći for petlju
| 4. Unos uređenih parova u listu **listaParova**     |

**Programski kod:**

```python
def unosPodataka():
    # ukloni prethodne unose (ako ih ima)
    global skupA
    global listaParova
    listaParova.clear()
    skupA.clear()

    elementiSkupa = input('Unesite elemente skupa A u jednoj liniji\nodvajajući ih zarezom (npr. f,g,d,e,r,t):')
    skupA = list(set(elementiSkupa.split(',')))
    n = int(input('Koliko parova zelite unijeti?:'))
    #unos n broja parova u glavnu listu (listaParova)
    print('Unesite oba clana para odvojena zarezom.')
    for i in range(n):
         par = input(f'{i+1})PAR:')
         par = tuple(par.split(','))
         listaParova.append(par)
```
