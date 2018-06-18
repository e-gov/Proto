---
permalink: Elutukse
header: false
---

# Elutuksestandard

(kavand)

Käesolev dokument koondab elutukse otspunktide ehitamise nõudeid ja head praktikat. Eesmärk on e-teenuste monitoorimise taset tõsta. Palju on veel rakendusi, millel elutukse funktsionaalsus üldse puudub. Samuti on eesmärgiks elutukseteabe vorminguid ühtlustada. Ühtlustatud vorming võib hõlbustada nii otspunktide arendamist kui ka rakenduste monitoorimist.

Elutukset võib teostada mitmel viisil. Käesolev nõuetekogum ei ole "kivisse raiutud", vaid seda tuleb kohandada ja täiendada, vastavalt konkreetse rakenduse seirevajadustele.

**Elutukse otspunkt** (_endpoint_) on liides, API osa, mille kaudu elutukset väljastatakse. 

## Elutukse kohustuslikkus

1. Süsteemi iga eraldi paigaldatav osa peab väljastama elutukset.

**Elutukse** (_heartbeat_) on rakenduse poolt reaalajas väljastatav teave iseenda seisundi kohta.

Elutukse on eelkõige rakenduse tasandi enesediagnostika. Elutukse on üks, aga mitte ainus seirevahend. Rakendused paiknevad mitmekihilises IT-taristus. Igas kihis oma 

## Elutukse kasutajad

6. **Inim- ja masinkasutaja**. Elutukse kasutajaks on ka rakenduse haldur (teenusehaldur) - inimesel peab olema võimalus teha `GET` päring elutukse otspunkti vastu veebisirvikust. Kuid peamiseks kasutajaks on seirelahendus (nt Zabbix), kust tehakse päringuid elutukse otspunkti poole.

7. **Sise- ja väliskasutaja**. Elutukset võib kasutada: 1) rakendust käitav organisatsioon ise; 2) rakendust kasutav teine organisatsioon või rakendus. Vastavalt võib elutuksest teha kaks versiooni: sise- ja väliskasutuseks.

## Elutukse protokoll

3. Elutukset pakutakse HTTP(S) otspunktist, mille poole saab pöörduda `GET` päringuga.

4. **Elutukse URL** moodustatakse rakenduse pea-URL-st, millele lisatakse `/heartbeat`, `/status` vms.

## Elutukse vorming

1. **Masin- ja inimloetav**. Elutukse peab olema masinloetav. Võimalusel peab elutukse olema ka inimloetav. Kõige paremini vastab nendele nõuetele JSON.

2. **Elemendid**.

element | kohustuslik | selgitus
--------|-------------|----------
`status` | jah | parameeter, mis indikeerib rakenduse töökorras olekut. Võimalikud väärtused: `UP`, `DOWN`
`name`  | jah | rakenduse nimi
`description` | ei | rakenduse pikem nimi või lühike kirjeldus
`version` |  | rakenduse versioon
`buildTime` |  | Rakenduse ehitamise aeg (datetime)
`startTime` |  | Rakenduse käivitamise aeg (datetime)
`uptime` | kaua rakendus on üleval olnud.
`dependencies` |  | Sisaldab nimekirja välistest süsteemidest, millest rakendus sõltub. Väliste süsteemide, millega on võimalik ühendust saada, status olekuna kuvatakse `UP`, mittevastavate süsteemide korral `DOWN`. Kui mõni väline süsteem, millest rakendus sõltub, on `DOWN`, siis on ka vastuse üldine staatus `DOWN`.
`dependencies.status` |  | Välise süsteemi status. Võimalikud väärtused: `UP`, `DOWN`. 
`dependencies.name` |  | Välise süsteemi lühinimetus.

3. **Ajavormingud**. Ajamomendid tuleks esitada nii masin- kui ka inimloetavalt:
- Unix epoch vorming on masinloetav
- ISO 8601 on nii masin- kui ka inimloetav
- Kestuse vormistamise kohta vt [nt](https://www.digi.com/resources/documentation/digidocs/90001437-13/reference/r_iso_8601_duration_format.htm)).

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

4. **Lisateave**. Elutukse võiks pakkuda teatud määral ka jooksvat statistikat, lähtudes rakenduse halduse vajadustest. Nt:
- teenuse poole pöördumiste arv
  - nt jooksva päeva, eelmise päeva jooksul

5. **Töökorras oleku tähendus**. Rakendus ei tohiks staatust `UP` saata ilma rakenduse oluliste sisemiste komponentide, aga samuti oluliste väliste sõltuvuste töökorras olekus veendumata. Näiteks, kuid rakenduse koosseisus on andmebaas, siis tuleks kontrollida, kas andmebaas vastab; vajadusel teha kontroll-kirjesalvestus (mis võimaldab veenduda, et andmebaasi salvestamine on ka tegelikult võimalik). 

## Turvalisus

1. Avaliku kasutajaliidesega või API-ga rakenduse elutukse peab samuti olema avalik.

2. Siiski peab jälgima, et avaliku elutukse kaudu ei edastata tundlikku taristuteavet. Tundlikku teavet väljastavat elutukseotspunkti tuleb kaitsta (ligipääsu piiramine tulemüüris, pöörduja autentimine vms).

## Elutukse nõudena tarkvara hankimisel

RIA MFN-is on elutuksenõue sõnastatud järgmiselt [https://e-gov.github.io/MFN/#17.3](https://e-gov.github.io/MFN/#17.3):

> "Süsteemi iga eraldi paigaldatav osa peab logimisel (näiteks aadressilt heartbeat.json) väljastama masinloetaval kujul oma nime ja versiooninumbri, oluliste väliste süsteemide oleku, viimase käivitamise aja, pakendamise aja ning serveriaja."


  

- Väliste teenuste (eIDAS Node, DigiDocService, pangalingid) ülevalolek (teostada vastavalt võimalustele)
- Elutukse teostus esimeses järgus võiks olla lihtne, ilma andmebaasi kasutamiseta
- Arvestada, et rakendus paigaldatakse toodangus kahes instantsis. Kummalgi instantsil erinev URL?
- Ülalkavandatud elutukseteenus on mõeldud RIA sisekasutuseks. Vajadusel piiratakse juurdepääsu ka RIA sees (IP vm meetodiga)

