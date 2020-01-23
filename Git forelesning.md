# Terminal og Git

## Terminal 

Hvorfor ikke bare bruke GUI-program til å løse problemet? 

1. Lar deg snakke direkte med operativsystemet med tilgang til hundrevis av verktøy. Alternativet ville vært å ha flere program åpne samtidig.
2. Hjelper på forståelsen av hvordan et verktøy faktisk fungerer.
3. Gir deg muligheten til å skripte og automatisere oppgaver; du lager bare en fil med alle kommandoene du vil kjøre.
4. Terminalen i seg selv krever omtrent ingen cpu eller minne.
5. Servere er often ut grafikk, da har man ingen valg.

Ulemper:
- Vanskelig i begynnelsen. Det er ingen menyer eller knapper som viser mulighetene dine, og du får lite assistanse og hint.


Grunnleggende kommandoer: 
- `man` for dokumentasjon 
- `ls` for å vise innholdet i mappen 
- `cd` for å navigere
- `pwd` for å printer banen til der du er
- `cat` for å vise innholdet i en fil
- `touch` for å opprette en fil
- `cp` for å kopiere filer
- `mv` for å flytter filer eller gi de nytt navn
- `echo` for å printe
- `grep` for å søke

Hvis manualen fra `man` er for vanskelig, så gir programmet tldr deg eksempler på vanlig bruk av en kommando.

Man kan også redigere filer direkte i terminal. _Emacs_ og _Vim_ er populære teksteditorer, men tar tid å lære seg. Vi anbefaler _Nano_:

Eks: `nano minfil.txt`

## Git

Se for deg utvikling der kode deles via minnepenn eller Dropbox.

Utfordringer:
 - Når flere redigerer på samme prosjekt. Hvem har den "riktige" kodebasen?
 - Hvilke endringer har jeg gjort på kodebasen i dag?
 - Gå tilbake til en tidligere versjon av kodebasen 
 - Finne ut hvem som har gjort hva
 - Hva om man ønsker å implementere en funksjonalitet uten å forstyrre resten av prosjektet.

Dette er problemer som vanligvis ikke oppstår når man jobber med f.eks. dokumenter.

Versjonskontrollsystem er til for å løse disse problemene. 

Git har blitt standard. (Subversion, Mercurial)

__Merk: Git gjør det meste lokalt på maskinen, det er bare en liten del av Git som faktisk kommuniserer med serveren.__

### Git kommandoer lokalt:
- `git init`
- `git status`
- `git diff`

Scenario: Initialisere et git-repositorie og følge med på status og diff mens vi endrer filer.

Å "committe" vil si å lagre et sett med endringer. Endringer er først unstaged og må stages før de kan committes. Dette lar deg håndforme endringene som skal være med i en commit.

- `git add`
- `git commit`
- `git log`
- `git checkout`
- `git reset`

Scenario: committ noen endringer mens vi følger med på log. Checkout noen committer og checkout head. Gjør noen endringer og reset 

### Git kommandoer til server:
- `git pull`
- `git push`

## Konflikter
Git prøver så godt den kan å løse _merge konflikter_, men det er ikke alltid det går. Da må du manuelt løse de ved å velge hvilke endringer du skal beholde.

Vi har foreløpig bare skrapt på overflaten av git sine muligheter, men med det vi har lært så langt kan vi allerede bli mye mer effektive som utviklere.

## Ekstra: 
- GUI-verktøy til å diffe og løse konflikter
- Branching
