###  Funkcija za ispitivanje antisimetričnosti binarne relacije <a id="6"></a>

Binarna je relacija antirefleksivna kada ima svojstvo da za **∀x,y∈A:(xRy ∧ yRx)->x=y.** To znači da je relacija antisimetrična za svaki uređeni par koji je dio zajedničkog skupa, ako su elementi unutar uređenog para su jednaki i u relaciji sa sobom.


| Algoritam |
| --------- |
| 1. Funkcija prima listu parova kao parametar(listaParova)           |
| 2. Za svaki x,y u listi parova provjeri          |
| 3. Ako je x==y onda nastavi na kraj petlje           |
| 4. Ako nije tvori par y,x unutar varijable(trazeniE)          |
| 5. Ako je trazeniE u listi ispiši "NE" i razlog te vrati *False*          |
| 6. Ako nije ispiši "DA" 
|7. Vrati *True*

*Programski kod:*
```python
#Funkcija koja provjerava antisimetričnost binarne relacije

def antisimetricnost(listaParova:list)->bool:
    print('Antisimetrična:',end=' ')
    # za svaki (x,y) ne smije postojati (y,x) unutar liste parova osim kada je x==y
    for x,y in listaParova:
        if x==y: continue
        trazeniE = (y,x)
        if trazeniE in listaParova:
            print(f'NE jer za {formatStr((x,y))} postoji {formatStr(trazeniE)} unutar liste parova')
            return False
    print('DA')
    return True   

```
