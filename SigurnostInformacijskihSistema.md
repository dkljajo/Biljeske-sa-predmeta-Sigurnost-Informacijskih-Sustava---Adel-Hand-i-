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


* * *
# 📖 2 AKTIVNI NAPADI 2
* * *

## Napadi sa ponavljanjem ( Replay )
* * *
- Napadi sa ponavljanjem (replay) , vrlo su rijetki u praksi, jer su teški za izvesti tj. teško možete pretpostaviti TCP sekvencne brojeve.
- Da bi se izvršio ovaj napad, napadač mora prvo uhvatiti velik broj osjetljivih podataka, te ih onda jednostavno ponoviti nazad prema
hostu pokušavajući ponoviti transmisiju.
- Druga vrsta ovog napada sa ponavljanjem jeste da napadač ponovi podatke, sa svim potencijalnim sekvencijalnim brojevima
u nadi da će mu se posrećiti i da će pogoditi jedan pravi, što će prouzrokovati da konekcija na strani klijenta prekine ili se u nekim
slučajevima da ubaci svoj dio podataka u sesiju.
* * *
## Kopanje po smeću (dumpster diving)
* * *

- Ova vrsta napada zna nekada biti prilično učinkovita.
- Traženjem vrijednih podataka po žrtvinom smeću može dovesti do zapanjujućih podataka.
- A posebno u kombinaciji sa drugim napadima, možete dobiti pun pogodak.
- Dosta zaposlenika kompanija bacaju u smeće nesvjesno vrlo vrijedne papire: informacije o mreži, konfiguracije routera,
firewalla, pa čak i same lozinke. :)
- Jednostavno, ljudi ne razmišljaju o tome što bacaju u smeće , a pogotovo kod kuće.
- Ljudi generalno, u smeće bacaju skoro sve ( izvode iz banaka, račune kreditnih kartica, telefonske račune, ...).
- U firmi, zavisno od sigurnosne politike je možda malo drugačije, ali kućna navika zna nekada prevagnuti.
- Kopanje po smeću nije uživanje, ali ono što dobijete zauzvrat zna nekada biti izvanredno.

* * *
## Socijalni inženjering (Napadi obmanjivanjem)
* * *
- Socijalni inžinjering označava prvenstveno manipuliranje ljudima ubjeđivanjem i lažnim predstavljanjem.
- Obmanjivač zloupotrebljava ljude , da bi došao do informacija , pri čemu može ali ne mora koristiti tehnologiju.
- Neka kompanija može da kupi najbolje sigurnosne dostupne tehnologije, razne firewall-e i IDS sustave, i da naloži
obavezno pridržavanje svakog sigurnosnog pravila koje preporučuju stručnjaci, zatim da obuči ljude da sve tajne informacije skrivaju prije nego što dođu kući, ali bez obzira koju tehnologiju koristili i koja sigurnosna pravila koristite, 
**ljudski faktor je najslabija točka sigurnosnog sustava.**
* * *
Što je točno socijalni inženjering:
1. "Najstručniji" oblik hackinga;
2. Ponekad je stvarno jednostavan;
3. Uporaba sa ili bez tehnologije;
4. U većini slučajeva, dobijaju su najbolji rezultati;
5. Upotreba ultimativne ljudske mane:
**"Pomozi onima koji pomoć trebaju!" :)**
