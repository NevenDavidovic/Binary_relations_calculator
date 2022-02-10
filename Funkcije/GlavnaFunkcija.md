## Glavna funkcija  

Glavna funkcija prima cjelobrojni tip podatka(*int*) od funkcije **GlavniIzbornik()**.  
Ukoliko je je izabran izbor koji nije ponuđen funkcija se ponavlja unutar while petlje.  
Nakon pravilnog izbora nasumično se generira **skup** i **lista parova** ili ih korisnik unosi umjesto programa.  
Ispisuju se izabrani skup i lista parova te se ispituju svojstva binarne relacije.  
Nakon ispitanih svojstava i ispisanih rezultata u tekstualnu datoteku korisnik može ponovno izabrati unos skupa, broja uređenih parova i same uređene parove ili izaći iz programa.

```python
###___MAIN FUNKCIJA___

def mainFunc():
    
    
    while (True):
        odabir = GlavniIzbornik()
        if(odabir == 1 or odabir == 2): break
        else: print("Krivi odabir, pokusajte ponovo!")

    if(odabir == 1): 
        unosPodataka()
        if not provjeraUnosa(listaParova,skupA): return
        ispisUlaznihPodataka()
        ispitivanjeRelacija()
        uredjivanjeParova()
    elif(odabir == 2): 
        generirajRelaciju()
        ispisUlaznihPodataka()
        ispitivanjeRelacija()
        uredjivanjeParova()
```
