###  Funkcija za ispitivanje refleksivnosti binarne relacije 
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
