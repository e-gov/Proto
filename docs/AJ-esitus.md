---
permalink: AJ-esitus
---

# AJ esitusteenus
{: .no_toc}

_arenduskava_

12.06.2018

<img src='img/AJ-ESITUS.PNG' style='width:750px;'>

Andmejälgija, [https://github.com/e-gov/AJ](https://github.com/e-gov/AJ), (AJ), on standardne protokoll ja tarkvara, mille paigaldamisega saab asutus kodanikule pakkuda ülevaadet (logi) kodaniku isikuandmete kasutamisest.

AJ esitusteenus on võimaldab kodanikul eesti.ee-s tutvuda kõigi andmekogude AJ-logidega.

Eesmärk (III-IV kv) on uuendada praegust piiratud võimalustega ja vananenud platvormil toimivat eesti.ee AJ esitusteenust:
- kodanikule päring üle kõigi andmekogude
- uuendatud platvorm

Ideaallahendus (vt joonis):
- AJ esitusteenust pakutakse eesti.ee domeeninime all
- Kodanik autenditakse eesti.ee-s, TARA abil
- AJ esitusteenus tugineb eesti.ee seansihoidjale (_session management_)
- AJ esitusteenuse koosseisus on komponent (X-tee adapter), mis teeb päringud andmekogude `findUsage` teenuste poole, teisendab saadud andmed JSON-kujule ja pakub neid API kaudu veebisirvikus töötavale UI-le.
- AJ esitusteenuse kujunduslahendus kasutab eesti.ee kujundust (mille aluseks on EMTA litsentseeritud kujundus)
- sirvikus töötav komponent on lahendatud ühelehelahendusena (SPA). Vajadusel kasutatakse sobivat veebiraamistikku, nt Angular.
- AJ esitusteenust seadistatakse konfiguratsioonifaili abil. Eraldi haldusliidest ei tehta.
- AJ on võimeline edastama statistikateavet - push välisesse statistikakogumisteenusesse.

Statistikakogumise vajadus analüüsitakse läbi. Statistikakogumine ei tohi saada andmekaitseliseks ohuks.
{:.note}

- AJ on võimeline väljastama elutukseteavet välisesse monitooringusüsteemi.
