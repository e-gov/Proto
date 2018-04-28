---
permalink: Hello
---

## Tere, maailm!

teenuseplatvormi kontseptsioon

### API
- ma ei pea eraldi, suure raha eest arendama oma süsteemile masinloetavat liidest (API-t)
- masinloetava liidese tugi on sees juba alustehnoloogias

### Andmebaas
- ma ei pea ise tegelema andmebaasisüsteemi häälestamisega
- saan kasutada manageeritud andmebaasiteenust

### Autentimine
- ma ei pea tegelema autentimisega
- saan kasutada teenust, mis autendib kasutaja
- teenus toetab erinevaid autentimismeetodeid
- sh piiriülest (eIDAS)

### Avaandmed
- ma ei pea oma e-teenusesse tegema eraldi avaandmete publitseerimise moodulit
- vaikimisi on kõik andmed, millele ei ole kehtestatud juurdepääsupiirangut, avaandmed
- avaandmete publitseerimiseks on igas mallrakenduses sisseehitatud, konfigureeritav funktsionaalsus

### Dokumenteerimine
- ma ei pea ise otsast peale koostama andmekogu v infosüsteemi pidamiseks nõutud dokumentatsiooni
- mallteenuste dokumentatsioon on kergesti kohandatav

### GDPR
- ma ei pea läbi töötama sadu lk regulatsioone
- andmekaitse standardküsimustele on vastused juba platvormi tehnoloogias, nt logimine
- isikuandmete töötluse standardpoliitika dokument

### Integratsioon
- ma ei pea pead murdma, kuidas oma süsteem ühendada teiste infosüsteemidega
- platvorm pakub standardseid liideseid, nii X-tee/SOAP kui ka REST/JSON stiilis

### ISKE
- ma ei pea lugema tuhandeid lk ISKE materjale
- ma ei pea juhendama ja kontrollima arendajaid keerulistes küsimustes
- ma ei pea ise tellima turvatestimist
- vaikimisi turvaklass K2T2S2 on platvormi sisse ehitatud
- rakenduste mallid, millesse kaitsemeetmed (OWASP Top 10 jms) on juba sisse ehitatud
- auditi jaoks on lähtematerjalid platvormi poolt
- enamus ISKE auditeerimisest on juba kaetud platvormi enda auditeerimisega
- ma ei pea tellima suurt ja keerulist ISKE auditit

### Kasutajatugi
- ma ei pea ise palkama kasutajatuge
- esimese ja teise astme kasutajatugi on platvormi pakkumises
- ise pean tagama ainult äriloogikasse puutuvate küsimuste vastamise

### Koodikvaliteet
- ma ei pea tuginema arendaja suusõnalistele väidetele koodi kvaliteedi kohta
- platvormil on kasutada koodikvaliteedi automatiseeritud hindamise vahendid

### Kõrgkäideldavus
- ma ei pea tegelema tarkvarakomponentide mitmes instantsis paigaldamisega

### Logimine
- ma ei pea ise logide kogumise ja hoidmise lahendust 
- platvormi mallrakendustes on sisseehitatud turva- ja statistikalogid
- tõendusväärtuse vajaduse korral logid räsiaheldatakse

### MFN
- ma ei pea kartma, et oluline mittefunktsionaalne nõue ununeb arenduslepingust välja
- platvorm pakub standardset, samas kergestikohandatavat MFN-i
- mallrakendused ja platvormiteenused on juba MFN-ile vastavad

### Müügitöö
- ma ei pea muretsema, kuidas klient minu e-teenuse üles leiab
- platvormil on efektiivne otsingumootor ja kergesti navigeeritav teenustekataloog

### Paigaldamine
- mul ei ole vaja muret tunda serverite hankimise pärast

### Pääsuhaldus
- ma ei pea ise tellima pääsuõiguste haldamise funktsionaalsust
- saan kasutada platvormi pääsuõiguste moodulit

### Põhimäärus
- saan kasutada põhimääruse malli, et oma teenust õigusreguleerida

### RIHA
- ma ei pea ise koostama RIHAs nõutavat tehnilist dokumentatsiooni (andmemudel jms)

### Seansihaldus
- ma ei pea ise teostama kasutaja seansihaldust (session management)
- platvorm pakub turvalist seansihaldust
- sh SSO põhimõttel

### Seire
- ma pea pidevalt jälgima, kas teenus töötab
- ei pea ehitama selleks eraldi süsteemi
- “elutukse” funktsionaalsus on teenuseplatvormis sees

### Serdid
- ma ei pea uurima, milliseid veebi- jm serte on minu teenuses vaja
- ei peab ise serte ostma ega muret tundma nende aegumise pärast
- serdihaldus on teenuseplatvormi pakkumises

### Statistika
- ma ei pea ise arendama oma süsteemile statistikamoodulit
- statistika põhivajadused on juba teostatud teenuseplatvormil
- seadistatava statistikalogi näol 
- statistikalogi külge saan ühendada erinevaid visualiseerimisvahendeid

### Teavitused
- mul ei ole vaja ise teostada teavituste funktsionaalsust
- platvormi teavitusmoodul võimaldab kasutajatele sõnumeid saata, puhverdada jne

### Testimine
- ma ei pea üleś ehitama testkeskkonda
- platvorm pakub arendus-, test- ja toodangukeskkonda kõigile teenustele

### Tulemüür
- ma ei pea tegelema võrguliikluse kaitsega
- tulemüür on teenuseplatvormi standardvarustuses

### Turvanõrkused
- ma ei pea pidevalt jälgima IT uudiseid, et teada saada, kus minu e-teenuses võib olla turvaauk
- ma ei pea tegelema turvaaukude kõrvaldamisega
- platvormihaldaja jälgib CERT vms infoturbe teavitusi; turvanõrkustest teadasaamisel rakendatakse meetmeid

### UI/UX
- mul ei ole vaja tellida oma kujundust
- riigivapp jms sisaldav baaskujundus on teenuseplatvormil juba olemas

### Varundamine
- ma ei pea ise varundama
- konfigureeritav varundamine on platvormi poolt

### Versiooniuuendused
- ma ei pea tegelema rakenduses kasutatavate tarkvarateekide uuendamisega
- platvormil toimuvad teegiuuendused tsentraliseeritult

### X-tee
- mul ei ole vaja paigaldada X-tee turvaserverit
- turvaserver provisioneeritakse teenuseplatvormi osana
- liidesed enimtarvitatavate andmekogudega on platvormis juba teostatud, piisab nende aktiveerimisest

Kokkuvõttes: ma ei pea neid asju ikka ja jälle nullist alustama

## Mallteenus “Hello World”

- mul ei ole vaja kõike algusest teha
- paljusid asju ei ole mul üldse vaja ise teha
- “Hello, World!” on mudelrakendus, milles kõik ülalloetletu on juba tehtud
- saan teha mudelist koopia
- mudel on kasutusvalmis kohe
- täidan oma äriloogikaga

funktsionaalsused:
- veebirakendus > frontend > avaleht
- riigivapiga kujundus
- autentimine (platvormi standardkomponendi abil)
- sh siseriiklik (ID-kaart, m-ID, pangalingid, Smart-ID)
- ja piiriülene (eIDAS)
- seansihaldus
- väljalogimine
- kodanikuvaade
- ametnikuvaade
- menetlusseisundi säilitamine ja kuvamine
- avalik vaade
- avaandmete masinloetav liides (API)
- piiratud juurdepääsuga API
- turvalogi logi
- statistikalogi
- andmekogu andmete koosseisu kirjeldus (RIHA jaoks)
- andmekoosseisu tehniline kirjeldus (XML)
- isikuandmete käitluspoliitika dokument
