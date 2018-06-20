---
permalink: Olek
footer: true
---

# Süsteemi seisundist ja paigaldamisest

Levinud ettekujutuse kohaselt on paigaldamine süsteemi viimine **nullolekust** (puhas, uus masin) ettenähtud, nõuetekohasesse **tööolekusse**. Tegelikult on paigaldamisel rohkem vorme. Näiteks, paigaldamise üks erijuht on süsteemi või süsteemiosa kustutamine. Kustutamisel, vastupidi, alustatakse tööolekust ja lõpetatakse nullolekus.

Levinud ideaalmudeli kohaselt saab paigaldamise lõppedes süsteem olla ühes kahest olekust – kas ettenähtud tööolekus või tagasi nullolekus. Esimesel juhul öeldakse, et paigaldus **õnnestus**. Teisel juhul paigaldamine **ebaõnnestus**.

Tegelikkus ei ole nii must-valge. Algolekusse tagasipöördumine ei ole alati võimalik. Alustatakse paigaldamist, tekkisid probleemid, veateated, algolekut ei õnnestu taastada – paigaldamise lõppedes süsteem on **määramata olekus**.

Süsteem võib määratama olekusse minna ka iseeneslikult, s.t kasutamise või keskkonna muutumise käigus.

Määramata olek tähendab, et me ei tea, mis seisus komponent või kogu süsteem on – ja puudub lihtne, kiire meetod selle teadmise tekitamiseks.

Määramata olek tähendab, et süsteemi käitumine: ei ole ennustatav; ei ole arusaadav; ei vasta dokumentatsioonile (kui dokumentatsioon üldse eksisteerib); ei ole arusaadav, kuidas komponendid on üksteisega seotud; ei ole arusaadav, millised komponendid on ajakohased.

Määramatus tegelikult ei ole süsteemi enda omadus – IT-süsteemid tavaliselt on determineeritud. Määramatus on teadmise puudumine.

Määramatuse näiteid:
- repos on mitu haru ja hulgaliselt commit-e. Millised nendest on paigaldatud tootmisse?
- dokumentatsiooni koosseisus on arhitektuurijoonis? Kas see vastab paigaldatud süsteemile?
- paigaldusjuhendis on (soovituslikud?) konf-iparameetrid. Kuidas tegelikult süsteem on seadistatud?
- meil on paigaldatud rakendus. Kust võiks leida selle koodirepo?
- millised featuurid on paigaldatud rakendusel?
- kas test- ja toodangukeskkonnas on üks või sama paigaldis ja kui ei ole, siis mille poolest need erinevad?

Dokumentatsiooni puhul tähendab määramatus seda, et ei ole selge: kas dokumentatsioon on ajakohane; kas tegu on viimase versiooniga; kas dokumentatsioon on täielik.

**Paigaldamine** on süsteemi või komponendi ülesseadmine käitlus- v kasutuskeskkonda. **Seadistamine** e konfigureerimine on süsteemi või komponendi juhtparameetrite muutmine. **Ehitamine** e **koostamine** on süsteemi kokkupanek komponentidest. Ehitamine tüüpiliselt sisaldab lähtekoodi kompileerimist jm teisendusi, pakendamist, aga ka testimist.

**Esmakordne** paigaldamine on uue süsteemi või komponendi paigaldamine, „puhtasse“ masinasse. **Nullist uuesti paigaldamine** on süsteemi või komponendi täiesti uuesti paigaldamine (vana kustutatakse maha või kirjutatakse üle). **Täispaigaldus** on süsteemi kõigi osade paigaldus. **Osapaigaldus** on süsteemi ühe osa lisamine, väljavahetamine või eraldi paigaldamine. **Korduspaigaldamine** on paigaldamise uuesti läbitegemine.

**Tagasipööramine** on paigaldamise (aga samuti igasuguse muu süsteemi mõjutuse) lähteseisundi taastamine. Tagasipööratavus on sageli nõutav, kuid mitte alati saavutatav. Lihtne tehnika on teha lähteseisust tõmmis (_snapshot_) ja see vajadusel uuesti üles seada.

Süsteemi oleku vaatepunktist on nii paigaldamine kui ka seadistamine süsteemi või selle komponendi viimine ühest olekust teise.

Nullist uuesti paigaldamine on pigem teoreetiline võimalus. Kõik muutub; ei ole võimalik kaks korda astuda samasse jõkke. Midagi - kasvõi ümbruses - on kindlasti muutunud. Midagi on tekkinud, mida ei saa või ei tasu üle kirjutada. Seetõttu paigaldamine - kui esmapaigaldus välja jätta - alati olemasoleva süsteemi oleku suurem või väiksem muutmine. Mõned osad jäävad seejuures paika, teised jälle vahetuvad või muutuvad.

Süsteemi erinevatel osadel on **erinev muutumiskiirus**. Süsteemi osad ei muutu ühes rütmis. Igal osal võib olla oma elukaar. Näiteks, väikeses TARA-Stat süsteemis (mis on omakorda suurema süsteemi komponent) on üle erineva muutustsükliga osa:
- VM (virtuaalmasin)
. Ubuntu (op-süsteem)
- Node.js (rakenduse platvorm)
- teegid (u 6-8)
- rakendus (paigaldatud VM-i)
- rakenduse seadistus (konf-ifail)
- MongoDB (andmebaasisüsteem)
- MongoDB seadistus (logitasemed jms)
- andmebaasikasutajad (kontod)
- süsteemikasutajad (kontod, mille alt VM jooksutab rakendust ja andmebaasi)
- ülalnimetatud kasutajate paroolid
- võtmed ja salasõnad (vajalikud komponentide omavahelise ja välisteenustega suhtlemise turvamiseks)
- andmebaasisüsteemi logid
- andmed (andmebaasis)
- seadistused tulemüüris
- rakenduse lähtekood (avalik repo)
- rakenduse lähtekood (organisatsiooni siserepo)
- rakenduse dokumentatsioon (avalikus ja siserepos)

Op-süsteemi versiooniuuendus nõuab VM kogu sisu uuestipaigaldamist. Seda võib, aga ei pea tegema nullist peale. Mis on paigas, seda ei ole mõtet liigutada.

**Paigaldamise** (aga ka seadistamise jm süsteemi oleku mõjutamiste) **planeerimise** juures on seetõttu olulised küsimused:
- mis olekusse süsteem paigaldamise või seadistamise tulemusena peab minema?
- mis komponente muudetakse?
- kuidas see mõjutab teisi komponente?
- mis on lähteolek?

Viimane küsimus on on oluline alati, kui me just uuesti nullist ei taha alustada.

Plaan peab tegelikkusega kokku minema. Seetõttu on **süsteemi oleku väljaselgitamine** igasuguse paigaldamise (aga samuti seadistamise) lähtekoht. Süsteemi oleku väljaselgitamiseks on mitmeid võimalusi:
- kasutada süsteemi sisseehitatud olekupäringut vm diagnostikavahendit. Nt: `--version` (versioonipäring komponendi poole käsurealt), heartbeat-päring vms
- tutvuda konfiguratsiooni- vm kirjeldusega – kui need on olemas ja ajakohased
- uurida varasemate paigaldus- ja seadistustoimingute logidega, märkmetega vms jälgedega (kuid need on olemas, ülesleitavad ja dateeritavad)
- jälgida süsteemi _de facto_ käitumist ja tuletada sellest teooria süsteemi seisundi kohta
- küsida kasutajatelt

**Dashboard**. Levinud idealisatsioon on süsteemi "olekulaud" - keskne koht, kuhu - automaatselt või automaagiliselt kõik vajalik teave kokku jookseb.



