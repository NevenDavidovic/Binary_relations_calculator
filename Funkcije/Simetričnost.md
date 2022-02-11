###  Funkcija za ispitivanje simetričnosti binarne relacije 
Neka je ρ binarna relacija na skupu A.
Binarna relacija je **simetrična** ako za svaki **(x,y) ∈ A × A vrijedi (x,y) ∈ ρ ⇒ (y,x) ∈ ρ**. To znači za svaki uređeni par **(x,y)** mora postojati i **(y,x)** kako bi bio zadovoljen uvjet simetričnosti. 

| Algoritam |
| --------- |
| 1. Funkcija prima 1 parametar( listaParova )          |
| 2. Za svaki element (x,y) u listi parova provjeri je li x == y, ako je, preskoči na sljedeći par liste          |
| 3. Za svaki element(x,y) u listi parova napravi novi par sa zamijenjenim elementima (y,x)          |
| 4. Ako svi tako tvoreni parovi nisu u listi parova ispiši NE i vrati *False*          |
| 5. Ako su svi tako tvoreni parovi u listi parova ispiši "DA"         |
| 6. Vrati *True*          |


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
