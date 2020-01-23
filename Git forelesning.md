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

I denne forelesning går vi gjennom unix-kommandoer (mac og linux). Dersom du bruker Windows kan du bruke _git bash_, som blir installert sammen med Git.

Grunnleggende unix-kommandoer: 
- `man` for dokumentasjon. Ex: `man echo`
- `ls` for å vise innholdet i mappen.
- `cd` for å navigere. Ex: `cd minmappe` for å gå inn i _minmappe_, og `cd ..` for å gå en mappe ut.
- `pwd` for å printer banen til der du er.
- `cat` for å vise innholdet i en fil. Ex: `cat HelloWorld.java`
- `touch` for å opprette en fil. Ex: `touch nyfil.txt`
- `cp` for å kopiere filer. Ex: `cp fil.txt kopi_av_fil.txt`
- `mv` for å flytter filer eller gi de nytt navn. Ex: `mv fil.txt fil2.txt`
- `echo` for å printe
- `grep` for å søke

Hvis manualen fra `man` er for vanskelig, så gir programmet tldr deg eksempler på vanlig bruk av en kommando. Dette må installeres.

Man kan også redigere filer direkte i terminal. _Emacs_ og _Vim_ er populære teksteditorer, men tar tid å lære seg. Vi anbefaler _nano_:

Eks: `nano minfil.txt`

Git kan finne på å åpne din standard teksteditor dersom den trenger en "beskjed" fra deg. Hvis du ønsker å endre _nano_ til å være standard, så kan du legge følgende inn på bunnen av terminalen sin konfigurasjonsfil. For unix-brukere og Git Bash i Windows er dette `~/.bashrc`. Det kan være du må opprette denne filen dersom den ikke eksisterer.

```
export VISUAL=nano
export EDITOR="$VISUAL"
```

Lagre filen og lukk og åpne terminalen, så skal nano være standard tekstredigeringsprogram.

## Git

Se for deg utvikling der kode deles via minnepenn eller Dropbox.

Utfordringer:
 - Når flere redigerer på samme prosjekt. Hvem har den "riktige" kodebasen?
 - Hvordan skal koden merges sammen når endringer har skjedd flere plasser?
 - Hvilke endringer har jeg gjort på kodebasen i dag?
 - Gå tilbake til en tidligere versjon av kodebasen 
 - Finne ut hvem som har gjort hva
 - Hva om man ønsker å implementere en funksjonalitet uten å forstyrre resten av prosjektet.

Dette er problemer som vanligvis ikke oppstår når man jobber med f.eks. dokumenter.

Versjonskontrollsystem (VCS) er til for å løse disse problemene. 

Git har blitt standard. (Subversion, Mercurial er eksmpler på andre VCS)

__Merk: Git gjør det meste lokalt på maskinen, det er bare en liten del av Git som faktisk kommuniserer med serveren.__

Dersom Git åpner et READ\_ONLY-vindu, lukker du dette med tasten 'q'.

Dersom Git åpner et tekstredigeringsprogram så er det for å få en melding av deg. Skriv meldingen, lagre og lukk redigeringsprogrammet. 
Skulle Git finne på å åpne Vim for å få en melding av deg (prøv helst å unngå at det skjer... instruks lenger oppe), så 
1. trykker du på tasten 'i' for å gå i skrivemodus, 
2. skriver meldingen til git ,
3. så på 'esc' for å gå ut av skrivemodus
4. så ':wq' etterfulgt av 'Enter' for å gå ut av Vim.
Du har nå klart å komme deg ut av Vim og kan klappe deg selv på skulderen 👏

### Git kommandoer lokalt:
- `git init` i en mappe for å gjøre mappen til et git-repositorie. I praksis oppretter git en skjult `.git`-mappe med noen filer i mappen du er i.
- `git status` viser deg om du har commits som ikke er pushet til serveren, og om du har gjort endringer som er staged eller unstaged.
- `git diff` viser deg endringene du har gjort siden forrige commit. Du kan også putte på to commit-IDer for å se hva som har blitt endret mellom de to committene. (`git diff 23jgsl9 sdfjf98`).

Scenario: Initialisere et git-repositorie og følge med på status og diff mens vi endrer filer.

Å "committe" vil si å lagre et sett med endringer. Endringer er først unstaged og må stages før de kan committes. Dette lar deg håndforme endringene som skal være med i en commit.

- `git add <fil>` stager en fil, det vil si alle endringene du har gjort i filen.
- `git commit -m "Melding"` committer alle endringene som har blitt staged.
- `git log` viser deg alle committene i repoet (rettere sagt i branchen du befinner deg på).
- `git checkout <commit-id>` lar deg hoppe til (sjekke ut) en tidligere versjon av koden. Du hopper fram igjen til siste commit ved å sjekke ut branchen du befinner deg på (som regel "master" ved mindre du har laget en ny branch): `git checkout master`
- `git reset --hard`: OBS: Fjerner alt arbeidet du har gjort siden forrige committ. 

Scenario: committ noen endringer mens vi følger med på log. Checkout noen committer og checkout head. Gjør noen endringer og reset 

### Git kommandoer til server:
- `git pull` hent ned siste endringer fra serveren. Kan medføre konflikt.
- `git push` last opp siste endringer til serveren. Dersom du får rejected må du pulle fra serveren først.

Scenario: Opprett et repositorie på en server og push repoet ditt. Gjør endringer i en fil lokalt og en fil online og prøv å pushe.

## Konflikter
Git prøver så godt den kan å løse _merge konflikter_, men det er ikke alltid det går. Da må du manuelt løse de ved å gå inn i filene og velge hvilke endringer du skal beholde. Etterpå kan du committe - _nå trenger du ingen commit-melding_.

Scenario: Gjør ulike endringer i samme fil online first, og så online, og prøv å pulle. Løs konflikten.

Vi har foreløpig bare skrapt på overflaten av git sine muligheter, men med det vi har lært så langt kan vi allerede bli mye mer effektive som utviklere.

## Ekstra: 
 - GUI-verktøy for diff og merge-konflikter
 - Branching
 
