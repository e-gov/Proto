---
permalink: AJ-20
---

# Andmejälgija 2.0

## Sissejuhatus

Andmejälgija, lühendatult AJ, on 2015-2016 RIA poolt arendatud isikuandmete kasutuse jälgimise lahendus. Käesolev dokument esitab ettepanekud AJ edasiarendamiseks.

Isikuandmete töötlemise jälgimise teema on aktualiseerunud ühtne andmekaitsemääruse (GDPR) jõustumisega 2018. a mais. Asutustel tuleb hakata andma andmesubjektidele teavet isikuandmete töötlemise kohta. 

Eriti oluline on täita õigusega pandud kohustus kokkuhoidlike kuludega, kiiresti ja kodanikule mugavalt kasutataval kujul.

Standardlahendused või -komponendid, ühiselt kasutatavad teenused või vähemalt ühtlustatud andmevormingud võimaldaksid GDPR nõuete täitmisel suurt kokkuhoidu.

Seetõttu väärib analüüsi, kuidas AJ võiks GDPR nõuete täitmisel asutustele võimalikult kasulik olla.

## Andmejälgija

Andmejälgija ([https://github.com/e-gov/AJ](https://github.com/e-gov/AJ)) on modulaarse arhitektuuriga standardne lahendus, mis praegu on kasutusel 4-5 asutuses.

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

### AJ kui ühtlustatud andmevorming

AJ isikuandmete kasutusandmete ühtlustajana. See on oluline. Ühtlustatud andmevorming võimaldab andmete andmesubjektile näitamist automatiseerida ja aitab tagada andmete mõistetavust.

```
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


### AJ kui andmevahetusprotokoll

AJ-s on fikseeritud viis isikuandmete kasutusandmete edastamiseks eesti.ee-le.

### AJ kui teenus

Esitusteenus eesti.ee-s

## AJ edasiarendusettepanekud

Laiendada andmejälgijaga haaratavate töötlussündmuste hulka
Praegu: andmete vaatamine (kes on andmeid vaadanud?)
andmete edastamine teise andmekogusse (X-teega)

Lisada: andmete salvestamine
andmete kustutamine

Isikuandmete töötlusandmete keskne vaatamiskoht
Lisada kohustus pakkuda isikuandmete töötlusandmeid eesti.ee-s  

## Andmesalvestaja pakkumine teenusena

Paljudele asutustele on takistuseks isikuandmeid töötlevate infosüsteemide suur arv. Kümnetes.
AJ on projekteeritud paigaldatavana ühe andmekogu külge (selle põhjuseks 2016. a oli tahtmine hoida disain lihtsana ja vältida "superandmebaasi" teket).
Asutus peab paigaldama Postgre andmebaasi, turvama ja haldama seda. 40 infosüsteemi puhul on vaja 40 AJ instantsi. Seetõttu tuntakse huvi (Tallinna Linnavalitsus), kas AJ saaks toetada enamat kui üht andmekogu.

Oskusliku seadistusega võiks see isegi praegu olla võimalik (andmete hoidmine ühes PostgreSQL instantsis, eraldi schema-des). Kuid ei tohi alahinnata barjääri, mida keerukama konfigureerimise vajadus AJ kasutuselevõtmisele püstitab. (2016. a viidi läbi AJ paigaldamine viies pilootasutuses. Need olid tavalisemast kõrgema IT-võimekusega asutused. Kuid ka neis võttis AJ seadistamine ja paigaldamine kuid).

### "AJ teenusena"

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


AJ praegune versioon on arendatud tarkvarana, mida asutus peab oma infosüsteemidega ja oma IT-taristusse sobitama. Tarkvara on paindlik, seda saab paigaldada mitmel erineval viisil. See nagu peaks suurendama tarkvara kasutust, kuid samas lisab keerukust. Tarkvara ise ei ole keeruline. Tegu on nn plumbing tüüpi lahendusega, selles ei ole erilisi algoritme.
Seetõttu on paljudel asutustel kiusatus teostada AJ funktsionaalsus ise.

AJ kui protokoll on hea - kuid protokoll pole piisavalt selgelt välja toodud. Üks võimalus on AJ protokoll selgemalt välja tuua. Eesti tingimustes peame siiski arvestama, et protokoll üksi ei pane asju liikuma.



REST API, üle avaliku interneti. Turvatud API võtmega.

