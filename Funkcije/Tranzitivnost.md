###  Funkcija za ispitivanje tranzitivnosti binarne relacije <a id="2"></a>
Neka je ρ binarna relacija na skupu A.
Binarna relacija je tranzitivna ako za sve **(x,y) ∈ ρ ∧ (y,z) ∈ ρ** ⇒ **(x,z) ∈ ρ**.


|   Algoritam:                                        |
|:--------------------------------------------------- |
| 1. Funkcija uzima kao parametar listu parova        |
| 2. Uspoređuje elemente svakog pojedinog para (index [1] i index [0])  |
| 3. Ako su isti preskoči na drugi par u listi parova |
| 4. Napravi novu listu **B** koja se sastoji samo od onih parova čiji je prvi član jednak drugom članu trenutnog para koji se promatra                    |
| 5. Ako takvih članova nema (lista B je prazna), preskoči na slijedeći član listeParova                                                   |
| 6. Za svaki član liste B napravi novi implicirani član koji se sastoji od prvog elementa iz listaParova (element[0]) i drugog elementa para iz liste B (e[1]) |
| 7. Provjeri nalazi li se implicirani par u listi parova, te ako ne - ispiši "NE" i razlog te vrati *False*                                                    |
| 8. Inače ispiši "DA" i vrati *True*                                                    |


**Programski kod:**
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
