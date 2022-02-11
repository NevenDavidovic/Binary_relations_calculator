## Glavna funkcija  

Glavna funkcija prima cjelobrojni tip podatka(*int*) od funkcije **GlavniIzbornik()**.  
Ukoliko je je izabran izbor koji nije ponuđen funkcija se ponavlja unutar while petlje.
Ovisno je li korisnik odabrao opciju 1 ili 2 pokreće se blok funkcija za:
1. Unos podataka o skupu i binarnoj relaciji **od strane korisnika**
2. **Nasumično generiranje** skupa i binarne relacije nad njim

Blok funkcija za **prvu** opciju poziva funkciju za:
1. Unos podataka od strane korisnika
2. Provjeru podataka za greške prilikom unosa
3. Ispis početnih podataka i grafički prikaz relacija
4. Ispitivanje svojstava binarnih relacija nad skupom
5. Uređivanje (dodavanje ili brisanje) parova

Blok funkcija za **drugu** opciju poziva funkciju za:
1. Nasumično generiranje skupa i binarne relacije nad njim
3. Ispis početnih podataka i grafički prikaz relacija
4. Ispitivanje svojstava binarnih relacija nad skupom
5. Uređivanje (dodavanje ili brisanje) parova

Nakon ispitanih svojstava i ispisanih rezultata u tekstualnu datoteku i konzolu glavna funkcija završava, te se korisniku postavlja upit
želi li nastaviti s novim unosom tj. zadatkom. Ako je odgovor DA tada se ponovno pokreće glavna funkcija i prikazuje glavni izbornik.
U slučaju da je odgovor NE, izlazi se iz while petlje i program završava.
Prilikom prvog pokretanja programa pokreće se funkcija **welcome()** koja ispisuje ime programa i upisuje u tekstualnu datoteku vremensku oznaku.

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
        
        
###___POCETAK_PROGRAMA___

welcome()
while True:
    mainFunc()
    izbor = input('\nZelite li novi unos? da/ne:')
    print('\n')
    if izbor == 'NE' or izbor == 'ne' or izbor == 'Ne': break
   
input("Kraj programa! Pritisnite ENTER.")          
```
