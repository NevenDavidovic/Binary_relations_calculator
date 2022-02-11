###  Funkcija za ispitivanje antisimetričnosti binarne relacije <a id="6"></a>

Neka je ρ binarna relacija na skupu A.
Binarna je relacija **antisimetrična** ako za svaki **(x,y) ∈ A × A, (x,y) ∈ ρ ∧ (y,x) ∈ ρ ⇒ x = y**. 
To znači da ako za svaki uređeni par relacije (x,y) postoji i (x,y), tada mora vrijediti x = y.


| Algoritam |
| --------- |
| 1. Funkcija prima listu parova kao parametar(listaParova)           |
| 2. Za svaki (x,y) par u listi parova provjeri je li x==y. Ako je preskoči na sljedeći par  |
| 4. Ako nije, tvori par (y,x) i spremi u varijablu **trazeniE**          |
| 5. Ako je **trazeniE** u listi parova ispiši "NE", pripadajuću poruku te vrati *False*          |
| 6. Ako nije ispiši "DA" i vrati *True* |


**Programski kod:**
```python
def antisimetricnost(listaParova:list)->bool:
    with open('Relacije.txt', 'a') as f:
        print('Antisimetricna:',end=' ')
        print('Antisimetricna:',end=' ',file=f)
        # za svaki (x,y) ne smije postojati (y,x) unutar liste parova osim kada je x==y
        for x,y in listaParova:
            if x==y: continue
            trazeniE = (y,x)
            if trazeniE in listaParova:
                print(f'NE jer za {formatStr((x,y))} postoji {formatStr(trazeniE)} unutar liste parova')
                print(f'NE jer za {formatStr((x,y))} postoji {formatStr(trazeniE)} unutar liste parova',file=f)
                return False
        print('DA')
        print('DA',file=f)
        return True

```
