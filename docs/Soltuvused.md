---
permalink: Soltuvused
---

# Sõltuvuste ravi

Eesti on sõltumatu riik. See tähendab, et ÜRO-s, Euroopa Nõukogus vms hääletamisel lähtutakse ainult eesti rahva huvist. Ainult eesti rahva tahe. Keegi ei saa väljast juhtnööre anda. Ega vaadata, kuidas teised hääletavad. Eesti esindajad on oma otsustustes ja seisukohtades sõltumatud ja vabad.

Tegelikult see muidugi nii ei ole. Enne hääletamist tulevad paljud mõjutama ja ära rääkima. Mõni libedamalt, teine brutaalsemalt. Tehakse ettepanekuid telgitagusteks diilideks. Tahetase saada Eesti toetust. Pakutakse ka midagi vastu. Jne. Lähemalt vaadates Eesti võib-olla ei olegi oma otsustustes nii väga vaba, vaid on (käest-jalust?) seotud riikidevaheliste suhete keeruka võrgustikuga.

Tarkvaras kohtame ka sõltuvusi. Java rakenduses leiame need `pom.xml` failis:

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

Node.js (Javascript) rakenduses tasub sisse vaadata faili `package.json`:

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
Nii on igas programmeerimiskeeles. Kitsamas mõttes on sõltuvus (_dependency_) väline tarkvarateek, mida rakenduses kasutatakse. Laiemas, arhitektuurses mõttes on sõltuvus igasugune tegur, mis ei ole täielikult meie kontrolli all. Sõltuvused on näiteks:
- välised andmeteenused, mida kasutame 
- välised nõuded, millega peab arvestama
- keskkond v taristu, milles süsteem peab elama
- inimesed ja organisatsioonid, kellest süsteemi arendamine, rahastamine või käitamine sõltub
- olukord tööjõuturul
- olukord IT turul
- üldine majanduslik olukord ja selle muutumine
- õigusruumi muutused
- tehnoloogiad ja nende areng
- teised süsteemid ja nende arengust
- sõltuvus teistest projektidest, nende ajakavas püsimisest
- sõltuvus kasutajate ebaselgetest soovidest
- sõltuvus tellija heitlikest tahtmistest
- sõltuvus vajaduste äralangemisest
- sõltuvus uute, ettearvamatute asjaolude ilmumisest (_whatever_)
- jne

Sõltuvuseks on ka sõltuvus ideedest. Sõltuvus võtmeinimestest. Whatever. 

Sõltuvuste väljaselgitamine on oluline. Sõltuvusi on palju ja pilt ei ole staatiline.
Projekti alguses üritatakse tihti võimalikult kõik sõltuvused ära kaardistada. See on nii hea kui ka halb.
Käia kõik osa- ja mõjupooled läbi. Igaühel on midagi nõuda või soovida. Kui need kõik kirja panna, siis võib töömaht kujuneda üüratuks või süsteem üldse võimatuks, sest soovid on vastuolulised.

Seetõttu - mida vähem sõltuvusi, seda vähem.

Sõltuvus tööriistadest. Need on tihti mingitest kõrvalistest, projektiga üldse mitte seotud eesmärkidest lähtudes ette antud. Või valitakse võimas tööriist, kuid selle kasutamise õppimine nõuab aega.

Sõltuvus moetrendidest - IT-s ülimalt oluline nähtus. 

Teegisõltuvuste juures kujuneb probleemiks tarkvara muutlikkus. Kui teekide vanu versioone enam ei toetata, siis tuleb need uuemate vastu välja vahetada. Muidu ei loeta tarkvara enam turvaliseks.

Sõltuvusi ei saa täielikult vältida. Igas reaalses projektis ei saa läbi väliste ressurssideta. Rakendus peab välistele osapooltele midagi pakkuma. Välised ressursid ja osapooled ei ole täielikult meie kontrolli all. Meil ei ole võimalik saada isegi täielikku, usaldusväärset teavat kõigi sõltuvuste kohta.

_Dependency management_, sõltuvuste juhtimine on maagiline termin, millega tähistatakse tegevusi, mis peaksid sõltuvusprobleeme kuidagi lahendama. Vt ka _dependency hell_ [1].

Ühe enam levib tarkvara kokkupanemine tükkidest (_packages_). See tähendab, et ei kirjutata enam ühesainsas programmeerimiskeeles, standardteegi abil, vaid assembleeritakse erinevaid, reeglina vabavaralisi koodipakette. Koosluse kooshoidmine võib olla problemaatiline, sest paketid ei tarvitse olla üksteisega kokkusobivad. Paketihaldur (_package manager_) on tarkvara, mis aitab komponte hallata ja kokku panna.

Igas suuremas programmeerimiskeeles on üks või mitu paketihaldurit. Paketihaldur ühitab tavaliselt arvutis kasutatavat tööriista ja keskset paketihoidlat. Nt:
- [npm](https://www.npmjs.com/) (Javascript)
- [Maven](https://maven.apache.org/) ja [Maven Central Repository](https://search.maven.org/)
- [Cargo](https://doc.rust-lang.org/cargo/index.html) ja [crates.io](https://crates.io/) (Rust)

[1] [https://en.wikipedia.org/wiki/Dependency_hell](https://en.wikipedia.org/wiki/Dependency_hell)