### Nasumično generirani zadatci od strane računala
**Programski kod**:
```python
def generirajRelaciju():
    global skupA
    global listaParova
    skupA.clear()
    listaParova.clear()

    #random broj elemenata skupa 4-7
    brElemenata = random.randrange(4, 7)
    #popunjavanje skupa A sa jedinstvenim elementima (slova od a-z)
    abeceda = "abcdefghijklmnopqrstuvwxyz"
    while(len(skupA) != brElemenata):
        randSlovo = randomSlovo(abeceda)
        if(randSlovo in skupA): continue
        else: skupA.append(randSlovo)
    #popunjavanje liste parova binarnih relacija novim clanovima
    #broj mogućih parova je broj elemenata skupa^2
    brParova = random.randrange(1, brElemenata*brElemenata+1)
    while(len(listaParova) != brParova):
        noviPar = (randomSlovo(skupA),randomSlovo(skupA))
        if(noviPar in listaParova): continue
        else: listaParova.append(noviPar)
```
