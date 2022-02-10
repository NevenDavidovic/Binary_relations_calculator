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
