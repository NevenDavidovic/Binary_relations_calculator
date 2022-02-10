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
def tranzitivnost(listaParova:list)->bool:
    with open('Relacije.txt', 'a') as f:
        print('Tranzitivna:',end=' ')
        print('Tranzitivna:',end=' ',file=f)
        for element in listaParova:
            if element[0]==element[1]: continue
            B = list(e for e in listaParova if e[0]==element[1])
            if len(B) == 0: continue
            #ispitaj postoji li u orignialnoj listi (listaParova) implicirani clan (ako su xRy i yRz, postoji li xRz)
            for e in B:
                implicElement = (element[0],e[1])
                # ako takav element nije pronađen Relacija nije tranzitivna - vrati False inace vrati True
                if not implicElement in listaParova: 
                    print(f"NE jer za {formatStr(element)} i {formatStr(e)} ne postoji {formatStr(implicElement)} unutar liste parova")
                    print(f"NE jer za {formatStr(element)} i {formatStr(e)} ne postoji {formatStr(implicElement)} unutar liste parova",file=f)
                    return False
        print("DA")
        print("DA",file=f)
        return True

```
