###  Funkcija za ispitivanje refleksivnosti binarne relacije 
Relacija je **refleksivna** ako za **∀ x ∈ A :(xRx)** .Ovo znači da je relacija refleksivna ako je svaki element u odnosu sam sa sobom. 
Ispitivanje refleksivnosti relacije smo programski riješili uz pomoć slijedećeg algoritma. 


| Algoritam                                                                         |
| --------------------------------------------------------------------------------- |
| 1. Funkcija prima 2 parametra (skupA i listaParova )                              |
| 2. Za svaki element u skupu A, stvori uređeni par s istim elementom |
| 3. Usporedi takav par sa parovima u listi parova                                  |
| 4. Ako traženi par nije u listi parova vrati *False* i ispiši pripadajuću poruku     |
| 5. Ako su pak svi tako stvoreni parovi unutar liste parova                        |
| 6.  Ispiši na ekran "DA"                                                           |
| 7.  Vrati *True*                                                                            |

**Programski kod:**
```python
def refleksivnost(skupA:list,listaParova:list)->bool:
    with open('Relacije.txt', 'a') as f:
        print('Refleksivna:',end=' ')
        print('Refleksivna:',end=' ',file=f)
        # za svaki x ∈ skupa A mora postojati (x,x) u listi parova 
        for element in skupA:
            trazeniE = (element[0],element[0])
            if not trazeniE in listaParova:
                print(f'NE jer za element "{element}" ne postoji par {formatStr(trazeniE)} unutar liste parova')
                print(f'NE jer za element "{element}" ne postoji par {formatStr(trazeniE)} unutar liste parova',file=f)
                return False
        print("DA")
        print("DA",file=f)
        return True
```
