---
permalink: AJ-20
---

# Andmejälgija 2.0
{: .no_toc}

- TOC
{:toc}

## Kokkuvõte

Vaatleme võimalusi andmejälgija (AJ) edasiarendamiseks, eelkõige selliseid,mille tulemusel kasutuselevõtu barjäär asutusele oleks madalam ja andmesubjektile tekiks andmetest rohkem väärtust.

Vaadeldud võimalustest kõige atraktiivsem tundub AJ pakkumine teenusena. Ideedega tuleb siiski edasi töötada.

## 1 Sissejuhatus

### 1.1 kontekst

Andmejälgija (AJ), on 2015-2016 RIA poolt arendatud isikuandmete kasutuse jälgimise originaalne lahendus.

Pilootprojektina AJ õigustas end. AJ võeti kasutusele 4-5 asutuses. Kuid edasine rakendamine on seiskunud.

Nüüd on ühtse andmekaitsemääruse (GDPR)  mõjul huvi asutustes AJ vastu tõusnud. Ühtse andmekaitsemääruse jõustumisel 2018. a mais tuleb asutustel hakata andma andmesubjektidele teavet isikuandmete töötlemise kohta. 

Oluline on täita need õigusest tulenevad andmekohustused kokkuhoidlike kuludega, kiiresti ja kodanikule mugavalt kasutataval kujul.

Standardlahendused või -komponendid, ühiselt kasutatavad teenused või vähemalt ühtlustatud andmevormingud võimaldaksid GDPR nõuete täitmisel suurt kokkuhoidu. Samas on andmekogud ja taristud erinevad, mille tõttu universaalse lahenduse leidmine on problemaatiline.

Seetõttu väärib analüüsi, kuidas AJ võiks GDPR nõuete täitmisel asutustele võimalikult kasulik olla.

### 1.2 Kogemus

AJ retseptsiooni ei ole süstemaatiliselt uuritud. Seetõttu on siinsed hinnangud subjektiivsed.

eesti.ee kasutusstatistika näitab AJ suhteliselt suurt kasutajaskonda (kuni 10 000 unikaalset kasutajat kuus). Need andmed vajaksid siiski kontrollimist.

Riigi Infosüsteemi Ametini ei ole jõudnud suuri kaebusi ega probleeme ei andmesubjektidelt ega AJ-t käitavatelt asutustelt. See tõendab AJ kontseptsiooni elujõulisust. 

AJ abil ei ole teadaolevalt avastatud suuri, meediasse jõudnud isikuandmete töötlusnõuete rikkumisi. Kuid võib-olla, et rikkumisi polegi olnud.

Ei ole selge, kui suurena andmesubjektid AJ kasu tajuvad.

Me ei tea ka mida nad AJ andmetest vaatavad ja milliseid järeldusi teevad. Kas nad käivad andmetest silmadega üle, otsides kahtlast või vaatavad midagi muud?

_Kodaniku "suurandmed". Kui AJ pakuks täielikumat pilti, siis võiks kodanikku huvitada nende andmete analüüs. eesti.ee ei paku praegu AJ andmete analüüsivõimalusi._ 

Võib päris kindlalt väita, et AJ ja analoogilised lahendused aitavad teha e-riigi toimimist kodanikule läbipaistvamaks ja arusaadavamaks ning selle kaudu suurendavad usaldust riigi vastu.

## 2 Andmejälgija

Andmejälgija ([https://github.com/e-gov/AJ](https://github.com/e-gov/AJ)) on modulaarse arhitektuuriga standardne lahendus. AJ on kasutusel 4-5 asutuses.

### 2.1 Komponendid

AJ komponendid on:

- _Eraldusfilter_ püüab isikuandmete kasutusfakte välja X-tee andmeliiklusest
- _Andmesalvestaja_ kogub ja säilitab isikuandmete kasutusfakte
- _Sisekontrollija rakendus_ võimaldab kogutud kasutusfakte kontrollide asutuse sisekontrolli eesmärkidel
- _Esitusteenus_ võimaldab andmesubjektil eesti.ee-s vaadata isikuandmete kasutusi.  
AJ on ühtaegu nii:

- andmevorming
- andmevahetusprotokoll
- e-teenus
- kui ka erinevatesse asutustesse paigaldatav tarkvara.

### 2.2 Ühtlustatud andmevorming

AJ isikuandmete kasutusandmete ühtlustajana. See on oluline. Ühtlustatud andmevorming võimaldab andmete andmesubjektile näitamist automatiseerida ja aitab tagada andmete mõistetavust.

```json
{
  "personcode": "36107120334",
  "logtime": "2018-04-23 T12:04:10",
  "action": "andmepäring",
  "receiver": "Eesti Haigekassa",
  "sender": "Rahvastikuregister",
  "sendercode": "70000562",
  "receivercode": "74000091"
}
```

AJ-s salvestatav isikuandmete kasutuse fakt (HTTP POST päringu kehana (JSON-vormingus))

### 2.3 Andmevahetusprotokoll

AJ-s on fikseeritud viis isikuandmete kasutusandmete edastamiseks eesti.ee-le.

### 2.4 Teenus

Teenusena käsitame rakendust, mida asutus ei pea ise paigaldama ega hooldama. AJ koosseisus on üks teenus - esitusteenus eesti.ee-s. Esitusteenust pakub RIA.

## 3 AJ edasiarendusettepanekud

Edasiarenduse all mõistame nii tarkvaraarendust kui ka toetavaid standardimis- ja kommunikatsioonitegevust, samuti lahenduste pakkumist pilveteenustena.

### 3.1 Laiendada andmejälgijaga haaratavate töötlussündmuste hulka

Praegu on fookus kahel töötlusliigil:
- andmete vaatamine (kes on andmeid vaadanud?)
- andmete edastamine teise andmekogusse (X-teega)

Lisada:
- andmete salvestamine
- andmete kustutamine

Tehniliselt on see ka praeguses lahenduses võimalik (`action`). Küsimus on metoodiline.

### 3.2 Keskse esitusteenuse aktiivne propageerimine

Isikuandmete töötlusandmete keskne vaatamiskoht on oluline. Praegu on eesti.ee esitusteenuse kasutamine vabatahtlik.
 
Lisada kohustus pakkuda isikuandmete töötlusandmeid eesti.ee-s.

### 3.3 Esitusteenuse laiendamine

Olukord pole halb, kuid esitusteenus upub riigiportaali arvukate artiklite ja teenuste hulka. Esitusteenus võiks olla paremini ülesleitav. 

_Paralleelina Ervinal, kunagine efektne visuaalne vastus küsimusele "Mida riik minu kohta teab?"_

Palju arutatud küsimus on kas kodanik peaks saama andmed ühe päringuga. (Praegu peab iga andmekogu eraldi avama).

Esitusteenus ei paku kodanikule analüütilisi vahendeid. Vähemalt teoreetiliselt võiks Kodanik teha esitlusteenuse andmete põhjal andmeanalüüsi või -kaevet. See eeldab vist siiski suuremat andmehulka.  

### 3.4 Andmesubjekti kohta kogutavate andmete koosseisu kättesaadavaks tegemine

_Mis liiki andmeid minu kohta kogutakse?_

Jutt on metaandmetest, s.t mitte andmeüksus ise, vaid andmeüksuse kategooria.

Näide. Autentimisteenuses TARA kogutakse järgmisi isikuandmeid:

```yaml
- autenditav isik (kasutaja)
  - isikukood, välismaalase puhul muu isiku identifikaator
  - ees- ja perekonnanimi
  - riik
  - muud kasutaja isikuandmed, eIDASE terminoloogias 'atribuudid' vastavalt eIDAS määruse alusel väljatöötatud eIDAS tehnilisele spetsifikatsioonile (välismaalase puhul)
  - autentimistoimingu andmed
    - kuupäev ja kellaaeg
    - klientrakendus, kust kasutaja autentimisele suunati
    - autentimismeetod
    - autentimise tulemus (autenditud või mitte)
- klientrakenduse kontaktisik
  - ees- ja perekonnanimi
  - e-post, telefon
```

RIHA kogemuse põhjal võib väita, et piirajaks on siin mitte tehniline lahendus, vaid asutuste valmisolek andmekoosseise asjakohasel abstraktsioonitasemel,  arusaadavas keeles ja piisava süsteemsusega kirjeldada.

RIHA kogemus näitab ka, et andmekoosseisu kirjelduskeel peab olema maksimaalselt lihtne. Näites on kasutatud YAML-i alamhulka.

Oleks küll loogiline ja ilus ning looks lisaväärtust, kui andmesubjekt saaks andmetöötlusfaktide nimekirja (ja see nimekiri võib olla tühi) kõrval ka loetelu andmekogus tema kohta hoitavatest andmetest (andmekategooriatest).

### 3.5 Andmesubjekti kohta säilitatavate andmete kuvamise lisamine

Ühtse vormingu väljatöötamine pole raske. Lihtne, üldistatud vorming, millega saab kirjeldada peaaegu kõike võiks olla järgmine:
- andmekirjeldus on kirjete kogum
- kirje koosneb väljadest
- väli koosneb välja nimest ja välja väärtusest
- välja nimi on sõne
- välja väärtus on kas sõne või kirje.

Andmekogude ümbertegemine selliseid andmeid tootma panemiseks oleks aga hinnanguliselt väga kulukas.

### 3.6 "AJ teenusena"

#### 3.6.1 Konfigureerimine, paigaldamine ja haldamine kui kasutuselevõtu barjäärid

AJ praegune versioon on arendatud tarkvarana, mida asutus peab oma infosüsteemidega ja oma IT-taristusse sobitama, konfigureerima ja paigaldama. Praegune tarkvara on tehtud paindlikuna, seda saab paigaldada mitmel erineval viisil, suuremas või väiksemas komplektis. See nagu peaks suurendama tarkvara kasutust, kuid samas lisab keerukust. AJ tarkvara ise ei ole keeruline,selles ei ole erilisi algoritme. Tegu on nn plumbing tüüpi lahendusega. Seetõttu on paljudel asutustel kiusatus teostada AJ funktsionaalsus ise.

Paljudele asutustele on takistuseks isikuandmeid töötlevate infosüsteemide suur arv (kümnetes). AJ on projekteeritud paigaldatavana ühe andmekogu külge. Selle põhjuseks 2016. a oli tahtmine hoida disain lihtsana ja vältida "superandmebaasi" teket. Asutus peab paigaldama PostgreSQL andmebaasi, turvama ja haldama seda. 40 infosüsteemi puhul on vaja 40 AJ instantsi. Seetõttu tuntakse huvi (Tallinna Linnavalitsus), kas AJ saaks toetada enamat kui üht andmekogu. 

Praegu otseselt ei saa. Oskusliku seadistusega võiks isegi praegu saada (andmete hoidmine ühes PostgreSQL instantsis, eraldi schema-des). Kuid ei tohi alahinnata barjääri, mida keerukama konfigureerimise vajadus AJ kasutuselevõtmisele püstitab. Näiteks, 2016. a viidi läbi AJ paigaldamine viies pilootasutuses. Need olid tavalisemast kõrgema IT-võimekusega asutused. Kuid ka neis võttis AJ seadistamine ja paigaldamine pool aastat või enamgi.

*Paigaldamist nõudva tarkvara arendamine ei ole perspektiivne. Kuigi "põhimõtteliselt" lihtne, on tänapäeva keerukates taristutes tarkvara endale paigaldamine seotud raskesti kokkuarvutatavate, kuid märgatavate kuludega.*

*Aja vaimule vastab tarkvara pakkumine teenusena.*

#### 3.6.2 "AJ teenusena"

 tähendaks, et 
- asutusele pakutakse lihtsat REST API-t, millega asutus saab isikuandmete töötlust logida.
- isikuandmete logi peetakse "pilves". S.t logi salvestamine, säilitamine, turvamine ja haldamine on teenusepakkuja kätes
- logi hoitakse asutuse või andmekogu lõikes.
- isikuandmete logi tehakse kättesaadavaks ainult kahele sihtrühmale:
  - andmesubjekt ise
  - andmeid logiva asutuse sisekontroll
- isikuandmete logile seatakse säilitustähtaeg, nt üks aasta.
- andmesubjektile pakutakse logiga tutvumiseks veebipõhist e-teenust.
- teenus tehakse kättesaadavaks eesti.ee alt, kuid võib olla iseseisva "brändinguga"

<img src='img/AJ-teenusena.PNG' style='width:500px;'>

REST API, üle avaliku interneti. Turvatud API võtmega.

### 3.7 AJ protokolli selgem väljatoomine

AJ kui protokoll on hea - kuid protokoll pole piisavalt selgelt välja toodud. Üks võimalus on AJ protokoll selgemalt välja tuua. Eesti tingimustes peame siiski arvestama, et protokoll üksi ei pane asju liikuma.

### 3.8 Terminoloogia arendamine

AJ on hea - meeldejääv, tähendust kandev ja suupärane nimetus. Kuid isikuandmete töötluse kodanikule läbipaistvaks tegemisega seotud terminid on pikad ja lohisevad. Paljusid ei asju ei saagi suupäraselt öelda. AJ leviks kergemini, kui AJ dokumentatsiooni saaks kompaktsemalt ja kodanikulähedasemas keeles esitada.  

Lühemaid termineid vajavad mõisted:

- _andmed isikuandmete kasutamise (või laiemalt - töötlemise) kohta_
- _isikuandmete kasutusandmete andmebaas_ 
- _isikuandmete kasutusandmetega tutvumine (andmesubjekti poolt)_.

### 3.9 Kuvandimuutus

AJ nimi seondub negatiivse tegevuse peegeldusega. Riik jälgib kodanikke. Selle neutraliseerimiseks AJ annab kodanikule võimaluse jälgida riiki.

AJ andmetest tõusev tulu võiks mitte piirduda negatiivse tegevuse vältimisega teise negatiivse tegevuse abil. AJ positiivne efekt võiks olla kodanikul tekkivas paremas pildis ja arusaamises e-riigi toimimisest.

_Kodaniku andmeait_, _Kodaniku andmekaeve_ vms võiksid ehk AJ kuvandit muuta positiivsemaks. 