---
layout: about
title: Obaveze studenata 
---


## Izborni predmet
- 8 ESPB bodova
- 2 časa predavanja
- 3 časa vežbi

Obaveze studenata uključuju predispitne obaveze i ispit. Predispitne obaveze se mogu ispuniti u formi praktičnih i teorijskih seminarskih radova. Praktični seminarski rad može, po izboru, biti samostalni ili grupni. Teorijski seminarski rad je samostalni. Da bi se uspesno položio ispit, neophodno je ispuniti prag na predispitnim obavezama i ispitu. Više detalja u nastavku.

## Predispitne obaveze (od 40 do 70 poena)

Predispitne obaveze obuhvataju praktični seminarski rad (koji je **obavezan**) i teorijski seminarski rad (koji **nije obavezan**). Da bi se položio ispit minimalni broj poena na predispitnim obavezama je 20.

### Seminarski rad (obavezan, od 40 do 60 poena)

Studenti imaju opciju da biraju između dva tipa praktičnog seminarskog rada. Praktični seminarski rad je **obavezan**. Pratiti [Obaveštenja](archives.html) radi blagovremenog izbora teme. Praktični seminarski rad je neophodno prijaviti do **1. decembra** tekuće godine. 

Praktični seminarski radovi se brane **u terminu ispita** uz prisustvo asistenta **uz prethodnu prijavu u formi** koja će biti okačena nedelju dana pred ispit. Očekuje se da student dođe pripremljen za prezentovanje seminarskog rada u svom okruženju (npr. tako što će doneti laptop), predstaviti projekat i odgovoriti na pitanja od strane asistenta. Pitanja mogu uključiti i pokretanje alata korišćenih za izradu seminarskog rada ili korišćenih na vežbama, kao i pisanje dodatnih testova tokom odbrane ukoliko su testovi deo seminarskog rada. Praktični seminarski radovi se moraju raditi u repozitorijumima otvorenim od strane asistenta, u okviru [GitHub organizacije](https://github.com/MATF-Software-Verification).

#### Samostalni praktični seminarski rad (40 poena)

Manjeg obima, praktičnog tipa. Izrada podrazumeva pokretanje alata za verifikaciju softvera ili pisanje testova za jedan projekat otvorenog koda. Prilikom odabira projekta, **uveriti se da je projekat u dobrom stanju za analizu** (prevodi se, kod je citljiv i modularan itd.). Nakon odabira projekta, i odgovarajućeg odobrenja od strane asistenta, biće kreirani repozitorijumi za izradu seminarskih radova. Odbrana je **praktična**, uz reprodukciju delova seminarskog rada.

Ciljevi i uslovi izrade praktičnog seminarskog rada:
- Projekat koji se analizira mora biti otvorenog koda. Popularni kandidati su studentski projekti, u kom slučaju oni moraju biti projekti **ranijih generacija** koji **nisu** već bili tema seminarskog rada iz ovog kursa. Ohrabrujemo odabir nestudentskih projekata.
- Cilj projekta je pronalazak bagova ili uskih grla programa. Nije neophodno da se zapravo pronađu bagovi kako bi seminarski rad bio uspešan - analiza i izveštaji čine seminarski rad.
- Neophodno je iskoristiti barem **5** alata/tehnika u okviru seminarskog rada. Pritom:
  - Testovi se broje kao jedna stavka, i mogu se pisati u bilo kom radnom okviru. Kategorije testova (jedinični, integracioni, i sl.) se broje kao zasebni alati. Uz testove je neophodno pratiti pokrivenost koda proizvoljnim alatom.
  - Jedan od alata mora biti alat za formatiranje izvornog koda i stilske provere (npr. `clang-format` ili `clang-tidy`).
  - Jedan od alata mora biti alat koji nije rađen na vežbama.
  - Svaki `Valgrind` alat se broji zasebno s tim što je dozvoljeno koristiti maksimalno **2** Valgrind` alata.
  - Praćenje pokrivenosti koda bez testova nema smisla i nije validna metrika. Dakle, alati za pokrivenost (npr. `gcov`) se **ne broje** kao validni alati, osim ako ih ne prate odgovarajući testovi.
- Za svaki korišćeni alat treba da budu dodate i skripte koje reprodukuju dobijene rezultate.

U okviru repozitorijuma za izradu seminarskog rada, potrebno je da bude napisan detaljan `README` fajl koji sadrži:
- Informacije o autoru seminarskog rada.
- Opis projekta koji je analiziran i odgovarajući linkovi do izvornog koda projekta - grana koja je analizirana i heš kod commit-a.
- Spisak alata koji su korišćeni za analizu i uputstva za reprodukciju rezultata.
- Spisak zaključaka.

Pored `README` fajla, potrebno je da postoji i (markdown ili PDF) fajl `ProjectAnalysisReport` koji sadrži detaljan opis analize projekta i zaključcima koji su napravljeni. Referencu na projekat koji se analizira dodati kao [git submodul](https://git-scm.com/docs/git-submodule). Svaki alat koji je korišćen treba da ima poseban direktorijum u kome se nalaze rezultati rada alata kao i opcione skripte za pokretanje.

Organizacija repozitorijuma:
```txt
.
├── git-submodule-of-project-to-analyze @ commit-hash
├── src
│   ├── run_tests.py
│   ├── RunningTests.md
│   ├── RunningTests.pdf
│   └── tests
│       ├── MyUnitTests1.cpp
│       └── MyUnitTests2.cpp
├── klee
│   ├── run_klee.sh
│   ├── failed-tests
│   │   ├── test00001.ktest
│   │   └── ...
|   └── klee-test-corpus.zip
├── cbmc
│   ├── run_cbmc.sh
│   ├── cbmc-outputs
│   │   ├── run1.stdout
│   │   ├── run2.stdout
│   │   ├── run3.stdout
│   │   ├── run3.stderr
│   │   └── ...
│   └── counterexamples
│       ├── counterexample1
│       ├── counterexample2
│       ├── counterexample3
│       └── ...
├── valgrind
│   ├── callgrind
│   │   ├── callgrind.out.12312
│   │   ├── callgrind.out.12313
│   │   ├── callgrind.out.12314
│   │   ├── callgrind.out.12315
│   │   ├── kcachegrind_12315_1.png
│   │   ├── kcachegrind_12315_2.png
│   │   ├── kcachegrind_12315_3.png
│   │   ├── kcachegrind_12315_4.png
│   │   └── run_callgrind.sh
│   └── massif
│       ├── massif.out.12312
│       ├── massif.out.12313
│       ├── massif.out.12314
│       ├── massif.out.12315
│       └── run_massif.sh
├── .gitignore
├── .gitmodules
├── README
├── ProjectAnalysisReport.md
└── ProjectAnalysisReport.pdf
```

**Napomena: Repozitorijumi koji ne prate strukturu prikazanu iznad ili nemaju tražene informacije u README fajlu neće biti prihvaćeni!**

Forma za prijavu samostalnih seminarskih radova se može naći na sledećem [linku](https://forms.gle/uhDiDK2R75J7vdjH6) (odabrati opciju _samostalni seminarski rad_). Repozitorijumi koji su već bili tema za samostalni seminarski rad iz ovog kursa se mogu naći na sledećem [linku](https://docs.google.com/spreadsheets/d/1tSoUTqnhZ7V26ov_o9QCxz_I1JAxEwFAkB34PmzVOhQ/edit?usp=sharing).

#### Istraživački praktični seminarski rad (preporuka 2+ člana, 60 poena)

*Napomena: Iako zamišljen da se radi timski, moguće je ovaj tip seminarskog rada raditi samostalno ali pritom se obim projekta ne smanjuje.*

Većeg obima, istraživačkog tipa. Teme za projekat su dostupne unapred. Izuzetno, ukoliko imate neku ideju možete da je predložite. 

Izrada podrazumeva kreiranje novih ili nadograđivanje postojećih alata za verifikaciju softvera, kao i njihovu verifikaciju koristeći barem alate pomenute na vežbama. Nakon odabira projekta, i odgovarajućeg odobrenja od strane nastavnika, biće kreirani repozitorijumi za izradu seminarskih radova. Odbrana je usmena, uz prikaz rada. Nakon odbrane istraživačkog seminarskog rada biće sa profesorkom dogovoren termin za prezentovanje rada.

Spisak predviđenih tema se može naći [ovde](https://docs.google.com/document/d/1yueEK1Cs7Oru6gCFrSjrf4FfK5-P9P4TB21XBr-gXLs/edit?usp=sharing). 

U okviru repozitorijuma za izradu seminarskog rada, potrebno je da bude napisan detaljan `README` fajl koji sadrži:
- Informacije o autorima 
- Na koji način se projekat može prevesti i pokrenuti (sve neophodne biblioteke, alati i zavisnosti)
- Na koji način se izvršna verzija koristi (primeri upotrebe)
- Koji ulazni primeri se mogu koristiti za upotrebu i testiranje programa.
- Spisak alata koji su korišćeni za analizu.
    - Ukoliko su testovi deo projekta, testovi treba da bude unutar repozitorijuma zajedno sa opisom kako se pokreću. Uključiti potencijalne skripte za pokretanje testova ukoliko su korišćene.

Pored `README` fajla, potrebno je da postoji i fajl `SystemDescription` (pdf ili markdown fajl) koji sadrži:
- imena autora
- opis problema
- opis arhitekture sistema (opis osnovnih modula implementacije),
- opis rešenja problema (osnovne ideje, obrazloženja za ključne odluke, opis osnovnog algoritma)

Forma za prijavu istraživačkih seminarskih radova se može naći na sledećem [linku](https://forms.gle/uhDiDK2R75J7vdjH6) (ignorisati pitanja vezana za samostalne seminarske radove).

### Samostalni teorijski seminarski rad (izborni, 10 poena)

Teorijski seminarski radovi se biraju u toku meseca novembra, a rok za predavanje je početkom januara. Teorijski seminarski rad nije obavezan. Precizni termini su uvek istaktnutu u okviru [Obaveštenja](archives.html).

Teme za teorijske seminarske radove možete da nađete na narednoj [adresi]({{site.poincare-vs}}/seminarski/temeZaTeorijskiSeminarski2022.pdf). Teme koje su već izabrane možete da pratite [ovde]({{site.poincare-vs}}/seminarski/temeZaTeorijskiSeminarski2022.txt). Šablon za izradu seminarskog rada možete naći [ovde](http://www.verifikacijasoftvera.matf.bg.ac.rs/vs/seminarski/sablon_za_seminarski_rad.zip).

Prijava tema vrši se u **novembru** a rok za izradu teorijskog seminarskog rada je do **početka prvog ispitnog roka u januaru 2023**. 

Prijava teme radi se preko naredne [forme](https://forms.gle/tWCw3H9Sed2QYux29). 

Teorijski seminarski rad se predaje preko naredne [forme](http://www.alas.matf.bg.ac.rs/~milena/vs_seminarski.html). Pratite uputstva data u okviru forme. 

## Završni ispit (50 poena)
**Teorijski ispit (50 poena)**: Polaže se pismeno, izvlači se pet ispitnih pitanja sa [spiska ispitnih pitanja]({{site.poincare-vs}}/predavanja/VS_IspitanaPitanja.pdf).

Da bi se položio ispit, neophodno je imati **51** poen, pri čemu je neophodno ostvariti bar **20 poena** na teoriji na završnom ispitu i bar **20 poena** na predispitnim obavezama.

**U terminu ispitnog roka** možete polagati sve delove ispita ili samo jedan deo. Pred izlazak na ispit potrebno je preko forme u okviru strane kursa prijaviti namere (odbrana seminarskog rada, teorijski ispit ili oba). Odbrana praktičnog seminarskog rada može i ne mora da prethodi izlasku na teorijski ispit. 

Za sve potencijalne nejasnoće, javite se mejlom! 
