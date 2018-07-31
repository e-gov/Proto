---
permalink: GDPR
---

# Kodanike GDPR-küsimused ja tehnilised lahendused neile vastamiseks

25.06.2018, täiendatud 31.07.2018<br>
Priit Parmakson

# Ülevaade

Dokument kaardistab küsimusi, mis kodanikul tema isikuandmete kasutamise kohta võivad tekkida.

Näitame, millistele neist küsimustest olemasolevad asutuseülesed tehnilised lahendused -  [Andmejälgija (AJ)](https://github.com/e-gov/AJ) ja [RIHA](http://www.riha.ee/) - praegu suudavad vastuseid pakkuda.

Kaardistus võib olla kasulik AJ ja RIHA edasiarenduste, aga samuti võimalike uute tehniliste lahenduste kavandamisel.

RIA ülesanne võiks olla välja pakkuda asutuseüleseid tehnilisi lahendusi - seal, kus need on võimalikud ja tõhusad.

## Küsimused

Kodaniku andmed peavad olema hallatud andmete kogu elutsükli (-käigu) vaates. Kodanik võib selles veendumiseks küsida alljärgnevaid küsimusi. Ühtse andmekaitsemääruse (GDPR) valguses tuleb neile küsimustele leida vastused. Vastamist hõlbustavad tehnilised lahendused. (Kuid ükski tehniline lahendus ei tööta ilma organisatsiooniliste meetmeteta).

### 1 Mida te minu kohta teate?

1.1 _Kas teie süsteemis on minu kohta andmeid?_ Oodatakse selget, lühikest, jah-või-ei vastust.

1.2  _Mis andmeid (andmekategooriaid) te minu kohta oma süsteemides hoiate?_ Oodatakse metaandmeid e üldistust, mitte detailseid, konkreetseid andmeväärtusi.

1.3  _Mis andmeid te konkreetselt minu kohta oma süsteemides hoiate?_ Nõutakse detailset andmekogumit.

1.4 _Millistes teie süsteemides on minu kohta andmeid?_ Oodatakse süsteeminimede loetelu. Peab olema arusaadav, mis on iga süsteemi eesmärk.

1.5 _Väljastage palun mulle minu andmed_ Soovitavalt masinloetaval kujul - et oleks võimalik andmeid teise süsteemi üle kanda.

### 2 Kes ja milleks minu andmeid kasutab?

2.1  _Milleks te minu kohta käivaid andmeid kasutate?_ Oodatakse põhjendust, andmekasutuse sisulist äraseletamist.

2.2 _Kellel on juurdepääs minu andmetele?_ 

2.3 _Kellele olete minu kohta käivaid andmeid edastanud?_ Oodatakse detailset andmeedastuse logi.

2.4 _Kes on minu andmeid vaadanud?_ Oodatakse detailset andmevaatamiste logi.

2.5 _Kuidas ma ise teie süsteemi olen kasutanud?_ Kodanik soovib näha oma süsteemikasutuse ajalugu.

2.6 _Kas minu andmeid on kombineeritud teiste andmetega?_ Oodatakse kinnitust, et andmeid hoitakse eraldi või teavet kombineerimise kohta.

2.7 _Avage juurdepääs minu andmetele!_ Koos isiku äranäitamisega, kellele juurdepääs avada.

2.8 _Sulgege juurdepääs minu andmetele!_ Koos isiku äranäitamisega, kellelt juurdepääs ära võtta.

### 3 Õiguspärasus

3.1 _Mille alusel (mis õigusega) te minu kohta andmeid kogute?_ Vastamiseks on vaja siduda süsteemid, andmekategooriad ja/või andmekirjed õiguslikku alust loovate õigusaktidega.

3.2 _Kas minu andmete töötlus teie süsteemides on seaduslik?_ Sarnane eelmise küsimusega, kuid terviku vaatenurgast.

3.3 _Kas minu andmete töötlus teie süsteemides on minimaalne (õiguspäraste eesmärkide suhtes)?_ Tõenäoliselt ei oska inimene seda küsida. Siiski on see oluline küsimus.

### 4 Kas minu andmed on kaitstud?

4.1 _Kas minu andmed on lekkinud või muul viisil leidnud väärkasutust?_ 

4.2 _Kas minu andmed on kaitstud?_ Oodatakse kinnitust, et isiku andmed on tõesti kaitstud - või teavet rikkumiste kohta. Kinnitus peab olema usutav, s.o mingilgi määral toetatud faktiteabega.

4.3 _Kas keegi on teie süsteemis minu nimel tegutsenud?_

### 5 Andmete tähendus ja õigsus

5.1 _Mida need andmed tähendavad?_ Küsimus tekib, kui andmed ei ole arusaadavad (arusaamatu kodeering, kontekstiteabe puudumine vms).

5.2 _Kas minu kohta hoitavad andmed on õiged?_ Loogilise järeldusena:

5.3 _Parandage minu andmed!_

5.4 _Sulgege juurdepääs minu andmetele?_

### 6 Kustutamine

6.1  _Kustutage palun minu andmed!_ See ei ole infopäring, vaid korraldus. Vastuseks oodatakse kinnitust, et kõik andmed on kustutatud.

6.2 _Kas olete minu andmed kustutanud?_ 

## Tehnilised lahendused

### Andmejälgija

Praegu [Andmejälgija (AJ)](https://github.com/e-gov/AJ) annab vastuseid küsimustele:

- Mis andmeid ja kellele olete andmekogust X-tee kaudu minu kohta edastanud?
- Kes on minu andmeid vaadanud? - kui [Andmejälgija (AJ)](https://github.com/e-gov/AJ) on seadistatud andmevaatamiste logimiseks.

### RIHA

[RIHA](http://www.riha.ee/) pakub:
- Mis andmeid (andmekategooriaid) te minu kohta oma süsteemides hoiate? - üldistatud, konkreetse isikuga mitteseotud vastus - kui andmekogu andmekoosseis on RIHAs kirjeldatud.
- Mille alusel (mis õigusega) te minu kohta andmeid kogute? - RIHA sisaldab viiteid Riigi Teatajasse andmekogu põhimäärusele. Põhimäärus ise on õigusakt ja sisaldab viidet kõrgemale õigusaktile (seadusele).
- Kellel on juurdepääs minu andmetele? - Võib olla kirjeldatud andmekogu põhimääruses.