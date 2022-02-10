###  Funkcija za ispitivanje simetričnosti binarne relacije 
Binarna relacija se naziva **simetričnom** ako ima svojstvo da ako je lement x u relaciji sa y, tad ujedno i y u relaciji sa x. To znači ako je uređeni par **(x,y)∈A** onda je i **(y,x)∈A**. 

| Algoritam |
| --------- |
| 1. Funkcija prima 1 parametar( listaParova )          |
| 2. Za svaki element(x,y) u listi parova tvori par sa zamijenjenim elementima (y,x)          |
| 3. Ako barem jedan takav par nije u listi parova ispiši NE i vrati *False*          |
| 4. Ako su svi tako tvoreni parovi u listi parova ispiši "DA"         |
| 5. I vrati *True*          |


**Programski kod:**
```python
def simetricnost(listaParova:list)->bool:
    with open('Relacije.txt', 'a') as f:
        print('Simetricna:',end=' ')
        print('Simetricna:',end=' ',file=f)
        # za svaki (x,y) mora postojati (y,x) unutar liste parova
        for element in listaParova:
            if element[0] == element[1]: continue
            trazeniE = (element[1],element[0])
            if not trazeniE in listaParova:
                print(f'NE jer za {formatStr(element)} ne postoji {formatStr(trazeniE)} unutar liste parova')
                print(f'NE jer za {formatStr(element)} ne postoji {formatStr(trazeniE)} unutar liste parova',file=f)
                return False
        print('DA')
        print('DA',file=f)
        return True

```
