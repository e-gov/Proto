---
permalink: Elutukse
---

# Elutukse

18.06.2018

standardikavand

Käesolev dokument koondab elutukse otspunktide ehitamise nõudeid ja head praktikat. Eesmärk on tõsta e-teenuste monitoorimise taset, sest palju on veel rakendusi, millel elutukse funktsionaalsus üldse puudub. Samuti on eesmärgiks elutukseteabe vorminguid ühtlustada. Ühtlustatud vorming võib hõlbustada nii otspunktide arendamist kui ka rakenduste monitoorimist.

Käesolev nõuetekogum ei ole "kivisse raiutud" ega käsitle kõiki võimalusi elutukse teostamiseks. Näiteks võib elutukset väljastada ka _push_-põhimõttel (s.t rakendus saadab omal algatusel seisunditeavet tarbijale). Siin on lähtutud _pull_-põhimõttest (tarbija pöördub ise elutukseotspunkti poole). Nõuete kasutamisel on mõistlik nende vajadust ja rakendatavust hinnata, vastavalt konkreetse rakenduse seirevajadustest.

Näide 1. Vastuse struktuur (eIDAS-Client)

```json
{
  "status": "UP",
  "name": "eidas-client-webapp",
  "version": "1.0.0-SNAPSHOT",
  "buildTime": 1528117155,
  "startTime": 1528121189,
  "currentTime": 1528121277,
  "dependencies": [
    {
      "status": "UP",
      "name": "eIDAS-Node"
    }
  ]
}
```

Näide 2. Vastuse struktuur (TARA-Demo)

```json
{
  "name":"TARA-Demo",
  "description":"TARA autentimisteenuse demo",
  "status":"UP"
}
```

1\. **Elutukse** (_heartbeat_) on rakenduse poolt reaalajas väljastatav teave iseenda seisundi kohta.

2\. **Kohustuslikkus**. Süsteemi iga eraldi paigaldatav osa peab väljastama elutukset.

Elutukse on eelkõige rakenduse tasandi enesediagnostika. Elutukse on üks, aga mitte ainus seirevahend. Rakendused paiknevad mitmekihilises IT-taristus. Igas kihis võib olla oma diagnostika ja seire.

3\. **Inim- ja masinkasutaja**. Elutukse kasutajaks on ka rakenduse haldur (teenusehaldur) - inimesel peab olema võimalus teha `GET` päring elutukse otspunkti vastu veebisirvikust. Kuid peamiseks kasutajaks on seirelahendus (nt Zabbix), kust tehakse päringuid elutukse otspunkti poole.

4\. **Sise- ja väliskasutaja**. Elutukset võib kasutada: 1) rakendust käitav organisatsioon ise; 2) rakendust kasutav teine organisatsioon või rakendus. Vastavalt võib elutuksest teha kaks versiooni: sise- ja väliskasutuseks.

5\. **Elutukse otspunkt**. Elutukset pakutakse HTTP(S) otspunktist, mille poole saab pöörduda `GET` päringuga.

6\. **Elutukse URL** moodustatakse rakenduse pea-URL-st, millele lisatakse `/heartbeat`, `/status` vms.

7\. **Masin- ja inimloetav**. Elutukse peab olema masinloetav. Võimalusel peab elutukse olema ka inimloetav. Kõige paremini vastab nendele nõuetele JSON.

8\. **Vorming**. Elemendid valida vastavalt konkreetsele seirevajadusele.

element | selgitus
--------|-----------
`status` | parameeter, mis indikeerib rakenduse töökorras olekut. Võimalikud väärtused: `UP`, `DOWN`
`name`  | rakenduse nimi
`description` | rakenduse pikem nimi või lühike kirjeldus
`version` | rakenduse versioon
`buildTime` | Rakenduse ehitamise aeg (datetime)
`startTime` | Rakenduse käivitamise aeg (datetime)
`uptime` | kaua rakendus on üleval olnud.
`dependencies` | Sisaldab nimekirja välistest süsteemidest, millest rakendus sõltub. Väliste süsteemide, millega on võimalik ühendust saada, status olekuna kuvatakse `UP`, mittevastavate süsteemide korral `DOWN`. Kui mõni väline süsteem, millest rakendus sõltub, on `DOWN`, siis on ka vastuse üldine staatus `DOWN`.
`dependencies.status` | Välise süsteemi status. Võimalikud väärtused: `UP`, `DOWN`. 
`dependencies.name` | Välise süsteemi lühinimetus.

9\. **Ajavorming**. Ajamomendid tuleks esitada nii masin- kui ka inimloetavalt:
- Unix epoch vorming on masinloetav
- ISO 8601 on nii masin- kui ka inimloetav
- Kestuse vormistamise kohta vt [nt](https://www.digi.com/resources/documentation/digidocs/90001437-13/reference/r_iso_8601_duration_format.htm)).

10\. **Lisateave**. Elutukse võiks pakkuda teatud määral ka jooksvat statistikat, lähtudes rakenduse halduse vajadustest. Nt:
- teenuse poole pöördumiste arv
  - nt jooksva päeva, eelmise päeva jooksul

11\. **Töökorras oleku tähendus**. Rakendus ei tohiks staatust `UP` saata ilma rakenduse oluliste sisemiste komponentide, aga samuti oluliste väliste sõltuvuste töökorras olekus veendumata. Näiteks, kuid rakenduse koosseisus on andmebaas, siis tuleks kontrollida, kas andmebaas vastab; vajadusel teha kontroll-kirjesalvestus (mis võimaldab veenduda, et andmebaasi salvestamine on ka tegelikult võimalik). 

12\. **Avalikkus**. Avaliku kasutajaliidesega või API-ga rakenduse elutukse peaks samuti olema avalik.

13\. **Turvalisus**. Tuleb jälgida, et avaliku elutukse kaudu ei edastata tundlikku taristuteavet. Tundlikku teavet väljastavat elutukseotspunkti tuleb kaitsta (ligipääsu piiramine tulemüüris, pöörduja autentimine vms).

14\. **Elutukse nõudena tarkvara hankimisel**. Elutukset ei ole vaja prototüüpides, POC-des jms rakendustes, kus käideldavus ei ole oluline. Muudes juhtudel peaks elutukse arendamine kavandatud omaette arendus-nõudena ja -tööna.

RIA MFN-is on elutuksenõue sõnastatud järgmiselt [https://e-gov.github.io/MFN/#17.3](https://e-gov.github.io/MFN/#17.3):

> "Süsteemi iga eraldi paigaldatav osa peab logimisel (näiteks aadressilt heartbeat.json) väljastama masinloetaval kujul oma nime ja versiooninumbri, oluliste väliste süsteemide oleku, viimase käivitamise aja, pakendamise aja ning serveriaja."

15\. **Arendusressurss**. Lihtsa elutukse lisamine peaks olema triviaalne. Täpsema ja usaldusväärsema olekuteabe tootmine aga nõuab ulatuslikuma enesediagnostika sisseehitamist, samuti meetodeid välisteenuste ülevaloleku kontrollimiseks. Praktiline lähenemine seetõttu võiks olla elutukse funktsionaalsuse arendamisel arvestada ka arendusressurssi. 

## Viiteid

- [MicroProfile Health](https://github.com/eclipse/microprofile-health), elutukse protokoll ja vorming (_wireformat_).
- [Hazelcast health check](http://docs.hazelcast.org/docs/latest/manual/html-single/#health-check).

