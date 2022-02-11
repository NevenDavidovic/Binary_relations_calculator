### Nasumično generirani zadatci od strane računala

Ova funkcija osmišljena je da korištenjem biblioteke **random** nasumično generira skup elemenata sačinjen od slova engleske abecede,te
parove binarne relacije nad tim skupom.

>Za potrebe ovog progama odlučili smo ograničiti broj elemenata skupa u rasponu od **4-7**

|                    Algoritam                          |
|--------------------------------------------------- |
| 1. Funkcija čisti skupA i listuParova od mogućih prijašnjih unosa     |
| 2. Funkcija **randrange** generira broj od 4 do uključujući 6 i sprema ga u varijablu **brElemenata**  |
| 3. skup slova je definiran kao string svih slova abecede i pohranjen u varijablu **abeceda**|
| 4. Dok god skupA nije popunjen željenim brojem elemenata radi                |
| 5. Pohrani nasumično odabrano slovo iz funkcije **randomSlovo(abeceda)** u varijablu **randSlovo**                                                    |
| 6. Provjeri sadrži li skupA već to slovo i ako da preskoči (kako bi eliminirali duplikate) |
| 7. Ako skupA ne sadrži to slovo, dodaj ga listi skupA metodom append() |
| 8. Nasumično odaberi broj parova binarne relacije i pohrani taj broj u varijablu **brParova** |
| 9. Dok god listaParova nije popunjena sa zadanim brojem parova radi |
| 10. Sastavi novi par od dva nasumična slova |
| 11. Provjeri postoji li taj par već u listiParova i ako da preskoči |
| 12. Dodaj novi par listiParova metodom append()  |

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
