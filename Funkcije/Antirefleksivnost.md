###  Funkcija za ispitivanje antirefleksivnosti binarne relacije <a id="4"></a>

Binarna je relacija **antirefleksivna** ako za **∀ x ∈ A: ~(xRx)**. To znači da niti jedan element nekog zajedničkog skupa nije u u odnosu sam sa sobom.

| Algoritam                                        |
| ------------------------------------------------ |
| 1. Funkcija prima 2 parametra(skupA i listaParova )                                                |
| 2. Za svaki element u skupu A, stvori uređeni par s istim elementom                                                 |
| 3. Ukoliko je najmanje jedan takav par u listi parova                                                 |
| 4. Ispiši "NE"                                                 |
| 5. Vrati *False* 
| 6. Ako nema takvog para
| 7. ispiši "DA" i vrati *True*  |
| 8. Ispiši sve u tekstualnu datoteku|

**Programski kod:**
```python
def antirefleksivnost(skupA:list,listaParova:list)->bool:
    with open('Relacije.txt', 'a') as f:
        print('Antirefleksivna:',end=' ')
        print('Antirefleksivna:',end=' ',file=f)
        # za svaki x ∈ skupa A u NE SMIJE postojati (x,x) u listi parova 
        for element in skupA:
            trazeniE = (element[0],element[0])
            if trazeniE in listaParova:
                print(f'NE jer za element "{element}" postoji par {formatStr(trazeniE)} unutar liste parova')
                print(f'NE jer za element "{element}" postoji par {formatStr(trazeniE)} unutar liste parova',file=f)
                return False
        print("DA")
        print("DA",file=f)
        return True

```
