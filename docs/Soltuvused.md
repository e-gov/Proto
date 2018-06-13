---
permalink: Soltuvused
header: false
---

# Tarkvarasõltuvustest (ja nende ravist)

Priit Parmakson

Eesti on sõltumatu riik. See tähendab, et ÜRO-s, Euroopa Nõukogus vms hääletamisel lähtutakse ainult eesti rahva huvist. Ainult eesti rahva tahe. Keegi ei saa väljast juhtnööre anda. Ega Eesti delegaat vaata, kuidas teised hääletavad. Eesti esindajad on oma otsustustes ja seisukohtades sõltumatud ja vabad.

Tegelikult see muidugi nii ei ole. Enne hääletamist paljud tulevad mõjutama, meelitama, diili tegema, ära rääkima.  Tahetakse saada Eesti toetust. Pakutakse ka midagi vastu. Või tahetakse hoopis lihtsameelset ära kasutada. Telgitagune diplomaatia on olnud, on ja jääb. Seetõttu lähemalt vaadates Eesti võib-olla ei olegi oma otsustustes nii väga vaba. Vaid on (käest-jalust?) seotud riikidevaheliste suhete keeruka võrgustikuga.

Ka tarkvaras on sõltuvused. Java rakenduses on need kirjas `pom.xml` failis:

```xml
    <dependencies>
        <!-- https://mvnrepository.com/artifact/javax.servlet/servlet-api -->
        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>javax.servlet-api</artifactId>
            <version>3.0.1</version>
            <scope>provided</scope>
        </dependency>
...
```

Node.js (Javascript) rakenduses failis `package.json`:

```json
"dependencies": {
    "basic-auth": "^2.0.0",
    "body-parser": "^1.18.2",
    "ejs": "^2.6.1",
    "express": "^4.16.3",
    "mongodb": "^3.0.7",
    "request": "^2.85.0",
    "request-debug": "^0.2.0"
}
```
Nii on igas levinud programmeerimiskeeles. Kitsamas mõttes on sõltuvus (_dependency_) väline tarkvarateek, mida rakenduses kasutatakse. Kuid laiemas, arhitektuurses mõttes on sõltuvus igasugune tegur, mis ei ole täielikult meie kontrolli all. Sõltuvused on näiteks:
- välised andmeteenused, mida kasutame 
- välised nõuded, millega peab arvestama
- keskkond v taristu, milles süsteem peab elama
- inimesed ja organisatsioonid, kellest süsteemi arendamine, rahastamine või käitamine sõltub
- olukord tööjõuturul
- olukord IT turul
- üldine majanduslik olukord ja selle muutumine
- õigusruumi muutused
- tehnoloogiad ja nende areng
- teised süsteemid ja nende areng
- sõltuvus teistest projektidest, nende ajakavas püsimisest
- sõltuvus kasutajate ebaselgetest soovidest
- sõltuvus tellija heitlikest tahtmistest
- sõltuvus vajaduste äralangemisest
- sõltuvus uute, ettearvamatute asjaolude ilmumisest
- jne. _Whatever_

Omamoodi sõltuvus on ka sõltuvus ideedest.

Sõltuvus tööriistadest. Need on tihti mingitest kõrvalistest, projektiga üldse mitte seotud eesmärkidest lähtudes ette antud. Või valitakse võimas tööriist, kuid selle kasutamise õppimine nõuab aega. Või võetakse see, mida on varem kasutatud ja mida tuntakse. Sõltuvus harjumusest.

Sõltuvus moetrendidest on IT-s väga levinud ja seetõttu oluline nähtus. 

Sõltuvus võtmeinimestest.

Funktsionaalsed sõltuvused.

Mittefunktsionaalsed sõltuvused.

Teegisõltuvuste juures on sageli probleemiks tarkvara muutlikkus. Kui teekide vanu versioone enam ei toetata, siis tuleb need uuemate vastu välja vahetada. Muidu ei peeta tarkvara enam turvaliseks.

Ühe enam levib tarkvara kokkupanemine tükkidest (_packages_). See tähendab, et ei kirjutata enam ühesainsas programmeerimiskeeles, standardteegi abil, vaid assembleeritakse erinevaid, reeglina vabavaralisi koodipakette. Koosluse kooshoidmine võib olla problemaatiline, sest paketid ei tarvitse olla üksteisega kokkusobivad. Paketihaldur (_package manager_) on tarkvara, mis aitab komponte hallata ja kokku panna.

Igas suuremas programmeerimiskeeles või -platvormil on üks või mitu paketihaldurit. Paketihaldur ühitab tavaliselt arvutis kasutatavat tööriista ja keskset paketihoidlat. Nt:
- [npm](https://www.npmjs.com/) (Javascript)
- [Maven](https://maven.apache.org/) ja [Maven Central Repository](https://search.maven.org/) (Java)
- [Cargo](https://doc.rust-lang.org/cargo/index.html) ja [crates.io](https://crates.io/) (Rust)
- [APT](https://en.wikipedia.org/wiki/APT_(Debian)), [Nexus](https://www.sonatype.com/nexus-repository-sonatype) (Linux).

Arendusajast kulubki märkimisväärne osa tööks paketihaldurite - ja repodega. Pakettide otsimine, uurimine ja hindamine. Nagu märgib üks asjatundja: raske ei ole mitte Java kui programmeerimiskeel, vaid Maven, Gradle jms.

<p>* * *</p>

Sõltuvusi ei saa täielikult vältida. Üheski reaalses projektis ei saa täiesti läbi väliste ressurssideta. Teiselt poolt peab rakendus välistele osapooltele midagi pakkuma.

Välised ressursid ja osapooled ei ole täielikult meie kontrolli all. Meil ei ole võimalik saada isegi täielikku, usaldusväärset teavet kõigi sõltuvuste kohta. Sellele vaatamata on käibel maagiline termin _dependency management_, sõltuvuste juhtimine. See tähistab tegevusi, mis peaksid sõltuvusprobleeme kuidagi lahendama või vähemalt leevendama.

Sõltuvused on üksteisega seotud, tihti mittetriviaalselt. Seda väljendab kujund _dependency hell_ [1]. Teoreetiline tulemus on "Dependency hell is NP-complete." [2] Tavakeelde ümberpandult tähendab see, et sõltuvuste "juhtimine" täieliku optimeerimise mõttes on matemaatiliselt võimatu. Reaalsem on rääkida sõltuvustega toimetulemisest.

Sõltuvuste väljaselgitamine on oluline. Tavaliselt sõltuvusi on palju ja pilt ei ole staatiline.

Projekti alguses üritatakse tihti võimalikult kõik sõltuvused ära kaardistada. See on nii hea kui ka halb.
Käies kõik osa- ja mõjupooled läbi, selgub, et igaühel on midagi nõuda või soovida. 

A paneb ette, et projektis rakendatakse räsiaheldamist. Räsiaheldamine on äge ja võimalik, et teatud kontekstides ka kasulik või isegi hädavajalik  - kuid mittetriviaalne tehnoloogia. Projekt oleks hea katselava tehnoloogia tundmaõppimiseks.<br>
B soovib, et kasutataks JSON Web Token andmevormingut. Programmeerijatel ei ole JSON Web Token-i kogemust.<br>
C soovib, et kasutataks innovatiivset turvatehnoloogiat CSP. CSP võiks lisada (marginaalselt) turvalisust.<br>
D seab väga oluliseks nõudeks, et laadilehtede vormistamisel kasutatakse Sass-i. Sass on kasutusel suurtes süsteemides. Meie süsteem ei ole suur.<br>
E paneb ette kasutada tehnoloogiat X, "kuna seda kasutab Facebook". Meie insenerid ei ole Facebook-st.<br>
F seab nõudeks, et projektis kasutatakse täisautomatiseeritud ehitustsüklit. Täisautomatiseeritud ehitustsüklit on üritatud juurutada kaks aastat.<br>
G  võtab sõna, ja nõuab, et üleantav kood peab vastama koodi dokumenteerimisstandardile Y. Koodistandardit Y kasutab Google. Kuid internetis ringi vaadates, asjatundjate arvamusi lugedes kujuneb pilt, et koodistandardites ei ole ühtset seisukohta, kui palju ja kas üldse kood peaks olema dokumenteeritud.<br>
jne.

 Kui kõik nõuded-soovid kirja panna, siis tõenäoliselt kujuneb töömaht üüratuks või süsteem üldse võimatuks, sest soovid on vastuolulised.

<p>* * *</p>

Seetõttu arenduse alustamisel, aga ka hiljem, oluline liigsetest sõltuvustest vabanemine – sõltuvuste ravi – kui soovite. Võib-olla on see projekti edu saavutamiseks üks tähtsamaid asju.

Ravi ei ole kerge. Kuid ei ole mõtet viivitada.

Iga nõude, elemendi, töömeetodi, komponendi, tehnoloogia juures saab küsida:
- Kas seda on tingimata vaja? Kas seda on veel vaja?
- Kas sama tulemuse saaks kuidagi teisiti, lihtsamalt?

Kriitiliselt läbi vaadata `pom.xml`, `package.json` jms teeginimekirjad, nõuete loetelud, aga ka arenduse protsessikirjeldused - ja vabaneda ballastist vabaneda.

Vabaneda kommertstarkvarast, põgeneda _walled garden_-test [3]. See tähendab vaba tarkvara ja standardsete andmevormingute kasutamist. 

Vabaneda "tootjalukkudest". Kuid ühest-ainsast teenusepakkujast või arendajast sõltuvusest vabanemine ei ole alati võimalik, sest piiratud turu ja ebaühtlaselt koondunud kompetentsi tingimustes võib see tähendada üldse kvalifitseeritud teenusest või tööjõust ilmajäämist. 

Sõltuvuste kõrval (_dependency_-nimekirjad) panna kirja ka "sõltumatused". Nii võiks kujuneda teatud "tarkvara iseseisvusdeklaratsioon".

[1] [https://en.wikipedia.org/wiki/Dependency_hell](https://en.wikipedia.org/wiki/Dependency_hell)<br>
[2] [https://research.swtch.com/version-sat](https://research.swtch.com/version-sat)<br>
[3] [https://en.wikipedia.org/wiki/Closed_platform](https://en.wikipedia.org/wiki/Closed_platform)