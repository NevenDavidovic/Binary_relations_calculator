# Grafički prikaz  
  
![Grafički prikaz elemenata binarne relacije unutar tablice](Ispitivać binarnih relacija v1.0.png)
    
    
```python
#funkcija koja graficki iscrtava elemente binarne relacije
def graficki(listaParova:list,skupA:list):
    with open('Relacije.txt', 'a') as f:

        skupA.sort()
        print()
        print("", file=f)
        print('  ',end='')
        print('  ',end='', file=f)

        #header tablice
        for e in skupA:
            print(e,end=" ")
            print(e,end=" ", file=f)
        print(' ')
        print(' ', file=f)
        #sadrzaj tablice
        for e in skupA:
            redak = e
            elementiRetka = [el[1] for el in listaParova if el[0]==e] 
            for y in skupA:
                jednak = False
                for i in elementiRetka:
                    if i == y: 
                        redak = redak + ' x'
                        jednak = True
                        break
                if not jednak: redak = redak + ' .'
            print(redak)
            print(redak, file=f)
```
