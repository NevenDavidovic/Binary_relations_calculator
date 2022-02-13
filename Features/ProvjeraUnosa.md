# Provjera unosa

Ova funkcija provjerava točnost korisnikovog unosa uspoređujući elemente parova koje korisnik unosi, sa elementima prethodno unešenog skupa
nad kojim se vrši ispitivanje binarnih relacija.
 
 
| Algoritam                                                                         |
| --------------------------------------------------------------------------------- |
| 1. Funkcija *findall* modula **re** izdvaja sve elemente iz liste parova koju je korisnik unio i pohranjuje ih u varijablu **određeniElementi**                       |
| 2. Pretvara ovu listu u set i natrag u listu kako bi se maknuli mogući duplikati |
| 3. Funkcija *all* vraća true ako svi elementi liste zadovoljavaju postavljeni uvjet |
| 4. Provjerava se nalazi li se svaki element para koji je korisnik unio ujedno i u skupu A | 
| 5. Ako je **provjera == True** , svi elementi odgovaraju elementima skupa A, funkcija vraća True |
| 6. U suprotnom ispisuje pogrešku i vraća False |
  
    
      
 **Programski kod:**       
    
    
```python
# Funkcija koja provjerava jesu li parovi relacije sastavljeni od elemenata skupa koji korisnik unosi
def provjeraUnosa(listaParova:list,skupA:list)->bool:
    određeniElementi = list(set(re.findall("[a-zA-z0-9]",formatStr(listaParova))))
    provjera =  all(item in skupA for item in određeniElementi)
    if not provjera:
        print('Pogreska! Uneseni elementi skupa ne odgovaraju elementima unutar unesenih parova.') 
        return False
    return True
```
