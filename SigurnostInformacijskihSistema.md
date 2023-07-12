# Sigurnost Informacijskih Sistema - Adel Handzic 🐧

Ispod možete naći bilješke iz materijala [**Sigurnost IS-a - Adel Handzic (FIT)**]
Navedeni materijali predstavljaju sjajan izvor informacija svima koji se počinju baviti sigurnoscu operativnih sustava.

- [📖 1 AKTIVNI NAPADI 1](#1-aktivni-napadi-1)
- [📖 2 AKTIVNI NAPADI 2](#2-aktivni-napadi-2)
- [📖 3 PASIVNI NAPADI](#3-pasivni-napadi)


# 📖 1 AKTIVNI NAPADI 1

## TCP/IP Hijacking

- **TCP/IP Hijacking ili "session hijacking"** je problem koji se pojavljuje u većini TCP/IP baziranih aplikacija, 
od običnih Telnet sesija pa do web baziranih aplikacija .
- Da bi se dogodio hijack (preuzimanje) TCP/IP konekcije, potrebno je samo da maliciozni korisnik (hacker) ima mogućnost presretanja 
ispravnih podataka potencijalne mete.
- Nakon toga se može jednostavno ubacivati u njegovu sesiju.
- Alati poznati kao T-sight za Windows i Hunt za Unix/Linux su vrlo često korišteni za monitoring i hijack sesije.
- Najlakše je preotimanje sesije kod običnih "clear text" sesija, kao što je FTP i Telnet , što je i logično.
- Naravno, puno interesantnije izanimljivije je preotimanje sesija Web baziranih aplikacija, posebno e-commerce aplikacija,
koje se oslanjaju na coockies da upravljaju stanjem sesije.
- Prvi dio uključuje preotimanje korisničkog session coockie-ja, kako bi se ušlo u korisnikovu sesiju.
- Krajnji korisnik (meta) će jednostavno dobiti poruku o isteku sesije ili neuspješnom logiranju, a to znači poruke koje neće navesti 
našu žrtvu da pomisli da se išta sumnjivo događa.
- Naravno ovo ovisi i od korisnika, tj. koliko je informatički pismen.
- Ali, činjenica je da većina korisnika neće ni pomisliti da im netko preuzima sesiju.
- Web aplikacije su većinom konfigurirane tako da vrijeme sesije istekne nakon određenog vremena neaktivnosti.
- Sada je pitanje, ako je vrijeme sesije neaktivno predugo, onda to otvara puno mogućnosti kod napadača:
1. mogućnost hijack coockie-ja;
2. mogućnost pretpostavke serijskog ID-ija;
- Da bi se obranili od ovakvih napada , potrebno je koristiti neki vid enkripcije (za web se koristi SSL enkripcija).

**- VAŽNO:
Session hijacking je vrsta napada gdje ostvarenu komunikaciju u sesiji, netko presretne (npr: napadač).
Znači: Hijacking je preuzimanje već ostvarene TCP sesije i ubacivanje vlastitih paketa u tu komunikaciju , tako da se te komande izvršavaju kao da ste vi vlasnik te sesije.**
