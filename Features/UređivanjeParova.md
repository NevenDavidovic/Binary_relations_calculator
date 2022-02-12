# Uređivanje parova  

Ova funkcija omogućava korisniku da dodaje ili briše pojedine parove binarne relacije nad skupom.
Svrha ove mogućnosti je kako bi se lakše vidjele promjene svojstava binarne relacije promjenom skupa parova, bez da se ponovno unose svi podaci.
 
 
| Algoritam                                                                         |
| --------------------------------------------------------------------------------- |
| 1. Unos odabira korisnika                             |
| 2. Ako korisnik ne želi uređivati parove, funkcija završava |
| 3. Odabir između dodavanja novi parova ili brisanja postojećih  |
| 4. Pretvaranje stringa unosa u listu parova **noviParovi** | 
| 5. Provjera točnosti unosa |
| 6. Dodavanje novih parova ili brisanje postojećih parova iz listuParova, ispis i ispitivanje relacija |
  
    
      
 **Programski kod:**       
    
    
```python
def uredjivanjeParova():
    global skupA
    global listaParova
    while (True):
        odabir = input("\nZelite li editirati parove binarne relacije?(da/ne):")
        if(odabir != "DA" and odabir != "da" and odabir != "Da"): break
        else:
            while(True):
                odabir = int(input("Zelite li: 1) dodati nove parove ili 2) obrisati pojedine parove:"))
                if(odabir == 1 or odabir == 2): break
            if(odabir == 1):
                parovi = input("Unesite parove koje Zelite DODATI u ovom formatu (x,y) (x,z) (z,x):")
                parovi = parovi.split() #lista stringova, potrebno je pretvoriti ju u listu tuople parova
                noviParovi = list()
                for item in parovi:
                    noviParovi.append((item[1],item[3]))
                #provjeri odgovaraju li uneseni parovi elementima zadanog skupa
                if provjeraUnosa(noviParovi,skupA): 
                    listaParova = listaParova + noviParovi
                    ispisUlaznihPodataka()
                    ispitivanjeRelacija()
            elif(odabir == 2):
                parovi = input("Unesite parove koje Zelite OBRISATI u ovom formatu (x,y) (x,z) (z,x):")
                parovi = parovi.split() #lista stringova, potrebno je pretvoriti ju u listu tuople parova
                noviParovi = list()
                for item in parovi:
                    noviParovi.append((item[1],item[3]))
                #provjeri odgovaraju li uneseni parovi elementima zadanog skupa
                if provjeraUnosa(noviParovi,skupA):
                    #brisanje iz liste
                    for item in noviParovi:
                        listaParova.remove(item)
                    ispisUlaznihPodataka()
                    ispitivanjeRelacija()
```
