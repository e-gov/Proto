---
permalink: MISP
---

## MISP tarkvara kohandamine portaali vajadusteks (proof of concept)

tööde kirjeldus

v 0.2, 5.03.2018

### Mõisted

_kodanikuteenus_ - kodanikule portaalis osutatav e-teenus<br>
_MISP_ - X-tee valmiskomponent, võimaldab luua kasutajaliideseid X-tee teenustele [arh]<br>
_portaal_ - teabevärav eesti.ee (tervikuna)<br>
_staatiline portaal_ - eesti.ee artiklikogum

### Tööde eesmärk

Uurida võimalust võtta portaalis kodanikuteenuste pakkumisel kasutusele MISP tarkvara, seda vastavalt täiendades ja kohandades.

Tööd teostatakse _proof of concept_ ulatuses. _Proof of concept_ peab vähemalt 2 olemasoleva teenuse näitel võimaldama hinnata idee teostatavust.

### Tööde koosseis

| nr | töö | selgitus |
|:-----:|-----|---------|
|  1  | Autentimise eraldamine | Eraldada autentimine eraldi moodulisse.<br> Autentimismoodul peab võimaldama kasutada nii staatilist portaali kui ka MISP-teenuseid kasutaja ühekordse autentimisega.<br> Võimalusel kasutada JWT kontseptsiooni [aut] ja selle alusel tehtud arendust. |
|  2  | UI uuendamine | Vahetada MISP-i kujundus välja Bootstrap-põhise, responsive võimalustega kujundusega.<br> Aluseks on tellija antud stiiliraamat koos kujunduselementidega.<br> _Proof-of-concept_ lahenduses ei pea UI olema viimistletud; piisab uue kujunduse teostatavuse demonstreerimisest. |
|  3  | MISP-i sidumine staatilise portaaliga | 1) Projekteerida mehhanism. millega e-teenus valitakse staatilises portaalis ja valitud teenus antakse kasutaja liikumisel MISP-i ette parameetrina.<br> 2) Uurida ja katsetada mehhanismi MISP-i kasutajaliidese kasutajale märkamatuks lõimimiseks staatilise portaaliga (iFrame). Kui see osutub probleemseks, siis teostada e-teenuse avamine kas lehevahetusega või eraldi sakil. MISP-i<br> 3) Kasutajaliidesest eemaldada menüüd, e-teenuste nimekirja kuvamine ja e-teenuse valimine. |
|  4  | Kasutajagruppide loogika lihtsustamine | Eemaldada pääsuõigustega seotud funktsionaalsus, mis ei ole vajalik kodanikuteenuste osutamiseks. |
|  5  | Teenuste ülekandmine | Teostada 2 portaalis oleva kodanikuteenuse üleviimine MISP-lahendusse. |

### Üleantavad tulemid

| nr | tulem | selgitus |
|:-----:|-----|---------|
|  1    | arhitektuuridokument | esitab ja spetsifitseerib: lahenduse eesmärgi, liidesed, komponentide koosseisu ja tehnilised omadused, toetatud kasutuslood, sõnumivahetuse jms tehnilised vood; sisaldab arhitektuurijoonist; võib olla nimetatud tehniliseks spetsifikatsiooniks. |
|  2    | paigaldusjuhend |  |
|  3    | kood |  |

#### Viited

[arh] Aktors OÜ (2015) MISP2 arhitektuur v 1.10.<br>
[aut] Riigi Infosüsteemi Amet (2017) eesti.ee autentimislahenduse tehniline lähteülesanne.