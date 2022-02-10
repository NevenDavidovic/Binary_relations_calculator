## Glavna funkcija  

Glavna funkcija prima rezultate tipa *bool* iz funkcija za određivanje binarnih relacija te cjelobrojni tip podatka od izbora unutar glavnog izbornika.

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
