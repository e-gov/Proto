---
permalink: Tood
---

<img src='img/ARHI-01.PNG' width='600'>

Joonis 1. 

## MISP 3 Proof of Concept

tööde kirjeldus

v 0.1, 14.03.2018

### Eesmärk

Tööde eesmärk on luua tehniline lahendus, koodnimetusega MISP 3, mis põhineb:
- MISP2 täiendatud [1] tarkvaral
- eraldiseisval autentimisteenusel (Autentija)
- responsive kujundusel, EMTA stiili alusel
- "vana" portaali XForms teenusekirjeldustel.

Tehniline lahendus peab võimaldama olemasolevaid portaali teenuseid kasutada:
- uues, responsive kujunduses
- väiksemate sõltuvustega vana portaali komponentidest (AAR, portaali raamistik jms)

Tehniline lahendus peab teostama kasutusvoo:

1. Kodanik leiab "uues" portaalis artikli juures talle huvipakkuva teenuse
2. Kodanik logib portaali sisse (autenditakse)
3. Kodanik avaldab soovi kasutada teenust
4. MISP 3 tõmbab X-tee abil andmekogudest vajalikud andmed
5. MISP 3 genereerib ja eeltäidab vormi ning esitab vormi kasutajale
6. Kodanik kasutab vormi (teeb toimingu)
7. MISP 3 salvestab kasutaja toimingu tulemuse vajalikku andmekogusse.

### Tehnilised nõuded

1. Autentimine tehakse eraldi paigaldatud mooduliga (Autentija). Autentimise tulemuseks on JWT-vormingus seansitõend. Seansitõendit hoitakse sirvikus, küpsises. Rakendus peab kontrollima seansitõendi kehtivust. Autentijas hoitakse nimekirja tühistatud seansitõenditest. Autentija kood ja dokumentatsioon [2] on olemas.
2. Peab arvestama perspektiiviga autentimisel kasutada [TARA teenust](https://e-gov.github.io/TARA-Doku/).
3. Kasutajaliideses kasutada kujundusraamistikku Bootstrap ja EMTA stiililaade.
4. Vormimootorina kasutada Orbeon XForms.
5. X-teega suhtlus teostada eraldi komponendiga, võttes aluseks MISP 2 vastava komponendi (joonisel nimetatud Mediatoriks).
6. MISP 2.0 koodist eemaldada mittevajalik osa (pääsuhaldus, mis ei ole vajalik kodanikuteenustes)
7. MISP 2.5 paigaldatakse uuest portaalist ja Autentijast eraldi (kuid kasutab sama domeeni).
8. Portaali peab olema võimalik paigaldada mitu MISP 2.5.

### Proof of concept

Tehniline lahendus koostada _proof of concept_ (POC) ulatuses.

### Tööde koosseis

| nr | töö | selgitus |
|:-----:|-----|---------|
|  1  | Autentimise eraldamine | Eraldada autentimine eraldi moodulisse.<br> Autentimismoodul peab võimaldama kasutada nii staatilist portaali kui ka MISP-teenuseid kasutaja ühekordse autentimisega.<br> Võimalusel kasutada JWT kontseptsiooni [aut] ja selle alusel tehtud arendust. |
|  2  | UI uuendamine | Vahetada MISP-i kujundus välja Bootstrap-põhise, responsive võimalustega kujundusega.<br> Aluseks on tellija antud stiiliraamat koos kujunduselementidega.<br> _Proof-of-concept_ lahenduses ei pea UI olema viimistletud; piisab uue kujunduse teostatavuse demonstreerimisest. |
|  3  | MISP-i sidumine staatilise portaaliga | 1) Projekteerida mehhanism. millega e-teenus valitakse staatilises portaalis ja valitud teenus antakse kasutaja liikumisel MISP-i ette parameetrina. Portaali koosseisus võib olla rohkem kui üks MISP.<br> 2) Uurida ja katsetada mehhanismi MISP-i kasutajaliidese kasutajale märkamatuks lõimimiseks staatilise portaaliga (iFrame). Kui see osutub probleemseks, siis teostada e-teenuse avamine kas lehevahetusega või eraldi sakil.<br> 3) Kasutajaliidesest eemaldada menüüd, e-teenuste nimekirja kuvamine ja e-teenuse valimine. |
|  4  | Kasutajagruppide loogika lihtsustamine | Eemaldada pääsuõigustega seotud funktsionaalsus, mis ei ole vajalik kodanikuteenuste osutamiseks. |
|  5  | Teenuste ülekandmine | Teostada kahe portaalis oleva kodanikuteenuse üleviimine MISP-lahendusse. |

### Üleantavad tulemid

| nr | tulem | selgitus |
|:-----:|-----|---------|
|  1    | arhitektuuridokument | esitab ja spetsifitseerib: lahenduse eesmärgi, liidesed, komponentide koosseisu ja tehnilised omadused, toetatud kasutuslood, sõnumivahetuse jms tehnilised vood; sisaldab arhitektuurijoonist; võib olla nimetatud tehniliseks spetsifikatsiooniks. Ei pea olema viimistletud. |
|  2    | paigaldusjuhend |  |
|  3    | töötav kood |  |
|  4    | POC lahenduse esitlus tellijale | |

#### Viited

[1] Aktors OÜ (2015) MISP2 arhitektuur v 1.10.<br>
[2] Riigi Infosüsteemi Amet (2017) eesti.ee autentimislahenduse tehniline lähteülesanne.