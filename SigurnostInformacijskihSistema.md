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


* * *
# 📖 3 PASIVNI NAPADI
* * *

- Za razliku od aktivnih napada, pasivni napadi su oni napadi gdje napadač direktno ne napada žrtvinu mrežu.
- Jednostavno, napadač radije čeka i osluškuje da se nešto dogodi, nego da napada mrežu i pokušava doći do informacija.
- Neki od pasivnih napada su povezani sa prisluškivanjem ili špijuniranjem osoba koje vrše konverzaciju.

* * *

## 3.1. "SNIFFING" - PRISLUŠKIVANJE MREŽE
* * *

- **Sniffing** možemo jednostavno prevesti kao prisluškivanje mreže.
- Snifferi su alati koji prate i osluškuju kompletan promet u mreži (bilo žicom ili zrakom).
- Ovo je vrlo moćna tehnika za dijagnostiku mrežnih problema, ali također zna biti vrlo opasna, ukoliko se koristi u loše svrhe
( osluškivanje lozinki, e-mail poruka, i bilo čega što ide u čitljivom tekstu).
- TCPDUMP je najpoznatiji UNIX sniffing alat i dolazi sa skoro svim Linux distrama.
- SNOOP je program koji koristi SOLARIS.
- Oba ova alata su Shell bazirani, i jednostavno će snimati sve pakete koje vide u mreži, ali u čitljivom obliku - clear tekst.
- Ovi programi međutim nisu toliko detaljni i često se koriste da bi se dobile informacije o routiranju , hostovima i vrsti prometa u mreži.
- SNORT se koristi za detaljnije skeniranje u komandnoj liniji.
- Snort je besplatan alat koji posjeduje mnogo više mogućnosti nego tcpdump, kao što je "dump" kompletnog aplikacijskog sloja i
generiranje upozorenja baziranih prema tipu mrežnog prometa.
- Upravo zbog toga Snort se više koristi kao program koji će otkriti određene anomalije u mreži, napade i nepredviđen promet,
te tada obavijsetiti korisnika.
- Znači da se Snort koristi prvenstveno kao obrambeni alat!

- Najmoćniji program od svih nabrojanih je sigurno WIRESHARK.
- On može biti i shell varijanta (tshark), ali postoji i verzija sa odličnim GUI-jem (grafičkim interfejsom).
- Jedna od najmoćnijih stvari koju radi Wireshark je mogućnost da može ponovno skupiti TCP strimove i sesije.
- Nakon što se sakupi dovoljna količina podataka, napadač može jednostavno pregledati sve stvari koje su se dogodile u mreži
(pregledati web stranice, skinute datoteke, e-mail poruke, ... ), i to sve sa samo jednim klikom miša.

* * *

## 3.2. NAPADI NA LOZINKE
* * *

- Napadi na lozinke su vrlo uobičajeni , jer u većini slučajeva rezultiraju upadom u sustav.
- Naravno, , ukoliko je jedini vid autentifikacije na sustav lozinka, a ne neki vid multi-faktor autentitifikacije.

### Brute-force napadi na lozinke

- Brute force napadi , po definiciji jeste testiranje svih mogućih kombinacija lozinki sve dok ne naiđe na onu pravu.
- Ova metoda se vrlo često koristi, posebno ukoliko se posjeduje kriptirana lozinka.
- Obično je broj karaktera u lozinci nepoznat, no možemo pretpostaviti da je većina lozinki između 4 i 16 karaktera.
Kao što znamo za svaki karakter u lozinci postoji oko 100 različitih vrijednosti, koji su formirani u različite grupe
(mala slova, velika slova, brojevi i specijalni znakovi).
- Što onda znači da u zavisnosti od veličine lozinke to je : 1 000 000 ili 1 000 000 000 000 000 000 kombinacija.
- Ukoliko se koriste samo određene grupe (recimo samo mala slova) , ovaj broj kombinacija se drastično smanjuje.
- Kao što vidimo; iako je broj kombinacija dosta velik, on je ipak **konačan** !
=> **To onda znači da su sve lozinke ranjive na brute force napade , ali vrijeme i jačina procesora koja je potrebna da se razbije lozinka zna biti jednostavno prevelika i neisplativa!**

- Većina današnjih OS-ova koristi neki vid "hashiranja" lozinke , da bi je na neki način zamaskirali.
- A to znači da radi ovoga načina lozinke **nikada** na sustavu nisu spremljene u čistom tekstu (clear text),
tako da autentifikacijski sustav postaje još sigurniji.
- **Ukoliko netko i uspije na neki način doći do lozinke , neće je moći odmah i upotrijebiti, već je potrebno i da je razbije!**

- Kada se lozinka unosi u sustav , ona prolazi kroz "one-way" hash funkciju, kao što je MD5 (Message Digest 5) i
izlaz te funkicje se snimi u **hash obliku**.
- Hash funkcije su one-way funkcije, što znači da vrše enripciju samo u jednom smjeru ida rezultat funkcije nije moguće dekriptovati.
- Iz ovog možete zaključiti, da ni server ne zna koja je vaša lozinka!
Za njega je samo bitno da vi znate koja je vaša lozinka.
- Kada se pokušate autentificirati na sustav, lozinke koje upišete prolaze kroz istu hashing funkciju i izraz se onda uspoređuje, i 
ukoliko se hashovi poklapaju vi ste se tek onda autentificirali na sustav.
- Brute force pokušaji se obično svode na to da nekako došu do korisničkih imena i hashovanih lozinki, te se zatim testiraju sve moguće lozinkekoristeći istu hash funkicju i uspoređuju se izlazi.
Ukoliko se nađe poklapajući hash , smatra se da je lozinka tada razbijena!
- Neki od brute force napada se svode na to da se pokušaju direktno unositi na udaljeni terminal, ali to je kratkog daha jer server
nakon nekoliko neuspjelih pokušaja zatvori sesiju za taj račun.

* * *
### DICTIONARY-BASED napadi na lozinke
* * *

- Jednostavne lozinke kao što je jedna riječ iz nekog jezika (posebno engleskog), su vrlo lagane za razbiti koristeći osnovne 
funkcije ovog napada.
. U ovom napadu, velike liste riječi određenog jezika se jednostavno provlače kroz hash funkciju i uspoređuju se onda rezultati.
- Na ovaj način vrlo brzo možemo doći do linux lozinke.

* * *
## 3.3. NAPADI MALICIOZNIM KODOM
* * *
- Napadi malicioznim kodom su posebno dizajnirani programi , pisani od napadača i dizajnirani tako da naprave određenu štetu.
- **Trojanski konji , virusi (malware) su primjeri takvih napada!**
- Ovi programi su pisani da budu nezavisni i ne zahtijevaju uvijek intervenciju korisnika ili prisustvo napadača
da bi napravili štetu.

### MALWARE - MALICIOZNI SOFTWARE
* * *

- Malware je naziv za programe koji u sebi sadrže maliciozni kod.
- Dva najčešća predstavnika su : virusi i trojanci.
- Virusi se mogu samostalno replicirati i šire se bez korisnikove interakcije, te najpredniji od njih se mogu modificirati i mutirati
da izbjegnu detekcije i pronalaženje.
- Trojanci su programi koji se pretvaraju da rade jednu veliku stvar, a u biti osnovna svrha im je nešto sasvim drugo.
Trojanci obično zavaraju korisnike da ih pokrenu, obećavajući im neku posebnu funkcionalnost.

* * *
### 3.3.1. VIRUSI
* * *

- Računarski virusi su definirani kao samo-replicirajući računarski programi, koji na određen način utječu na hardware, OS ili 
aplikacijski software.
- Virus se može izvršavati u računarskoj memoriji (RAM), te nakon toga računar mora pratiti instrukcije koje je dobio od virusa.
- Te instrukcije mogu oštetiti ili izmjenuti određene podatke ili poruke, zatim izazvati probleme u radu sa OS-om itd.
- Virusi se šire kada se instrukcije (tj. izvršni kod) koji pokreće program, prebacuju sa jednog računara na drugi.
- Virusi se mogu replicirati na razne načine:
memory stickovi, hard diskovi, legitimni računarski programi, pa čak i putem mreže (e-mail).
- Pozitivna strana je da priključeni računar ne mora biti nužno i zaražen!
- **Kod mora biti izvršen, odnosno pokrenut kako bi računar bio zaražen!**
- No treba uvijek biti na oprezu, jer su velike šanse ako skinete virus sa Interneta, da on može sadržavati i neki vid logičkog trika,
tako da zavara vaš OS i sam se izvrši!
- Dosta virusa jednostavno preživljava , tako što se kači na druge legitimne programe.
- Ovo se može dogoditi kako se program kreira, otvori ili modificira.
- **Tako da, kad se taj program pokrene, pokrene se i sam virus.**
- Postoji dosta različitih načina kako se virusi mogu modificirati ili ubaciti u naš legitiman kod.
Na veliku žalost, programeri mogu učiniti vrlo malo kako bi spriječili ovakvu vrstu napada. 
Programeri jednostavno nisu u mogućnosti napisati tako savršen program, koji se ne bi onda mogao inficirati virusom.
- Naravno, uvijek se mogu otkriti modifikacije koje su napravljene i izvršiti **forenzička analiza.**

- Kategorije virusa:
1. paraziti;
2. bootstrap sektor virusi;
3. multi-parti virusi;
4. companion virusi;
5. lik virusi;
6. Data file virusi.

* * *
### 3.3.2. TROJANCI (TROJANSKI KONJI)
* * *

- Trojanci su po obliku najbliži virusima, ali se svrstavaju u posebnu kategoriju.
- Trojanci se obično manifestiraju kao najosnovniji oblik malicioznog koda.
- Trojanac je u biti program koji obično izgleda zanimljivo, no unutar njega se nalazi skriveni dio malicioznog koda , koji može
uraditi nešto opasno.
- Najčešći primjer da postanete žrtva trojanskog konja, jeste da nemate anti-virus na računaru, a netko vam pošalje putem e-maila
-izvršnu datoteku kao prilog, pretvarajući se da nešto korisno. Zatim je vi otvorite naivno.... i onda nastane problem!
No danas većina korisnika je svjesna ove vrste napada, te se uspješno brani od njega. No ono što je velika opasnost je da preko
ovih programa možete dobiti i udaljenu kontrolu na zaraženi računar.
- Dva najpoznatija programa za udaljenu kontrolu su:
- **Back Office i NetBUS**, a kasnije i **SubSeven**.
- Potrebno je još napomenuti da je danas postalo popularno pisanje posebno namjenjenih virusa i trojanaca za novac.

* * *
### 3.3.3. CRVI (WORMS)
* * *
- Crv je samo-replicirajući program, koji ne obuhvaća datoteke, već se nalazi u aktivnoj memoriji (RAM) i širi se putem računarskih mreža.
- Crvi koriste automatizirane funkcije OS-a i nevidljivi su za korisnike.
- Često se crvi i ne primjete u sistemu, dok se ne potroše mrežni resursi, ili dok žrtvin računar ne ostane bez raspoloživih resursa i 
- postane praaktički neupotrebljiv.
- Jedni od najpoznatijih crva su:
- **LoveBug, Nimbda i Code Red.**

* * *
### 3.3.4. BACKDOOR (STRAŽNJA VRATA)
* * *

- Postoji dosta različitih vrsta backdoor-a:
- **trojanci, rootkits**, pa čak i **neke vrste legitimnih programa** koji se mogu koristiti kao backdoors.
- **Backdoor je u osnovi bilo koji program ili konfiguracija sustava dizajnirana tako da dozvoli neautentificiran pristup u sustav.**
- **Nekada su backdoor skriveni, ali nekada i ne !**
- Rootkit je skup programa koji mogu maskirati napadača , tako da se ne može primjetiti njegovo prisustvo.
- Neke softverske kompaije ostave jednu vrstu backdoor-a, kako bi se kasnije moglo pristupiti nalozima sistemskih admina i
zaobići sistemske sigurnosne mehanizme.
