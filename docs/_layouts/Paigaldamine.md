---
permalink: Konfiguratsioonihaldus
---

## Küsimused

Mis seisundis (olekus) on süsteem?
Mis seisundis (olekus) on süsteemi iga komponent v osa?
Mis on paigaldatud?
Kas süsteem töötab?
Millised süsteemi osad ei tööta?
Mis on muutunud?
Milliseid teisi osi mõjutab muutus süsteemi ühes osas?

##Süsteem

Süsteem on rakendus, e-, IT- vm –teenus koos kõigi osadega, mis on vajalikud süsteemi terviklikuks toimimiseks.

## Süsteemi konfiguratsioon
Süsteemi konfiguratsioon. Süsteemi osad võivad olla nimetatud mitu moodi: komponendid, alamsüsteemid, sõltuvused. Süsteemi osade nimekiri on süsteemi koosseis.

Süsteemi osad:
-	rakendus
o	kood
o	ressursid; nt pildifailid
o	seadistused (konf-ifailid)
-	teegid (libraries)
-	süsteemitarkvara
o	runtime; nt JVM (Java virtuaalmasin)
o	teenindav tarkvara
	nt Tomcat (rakendusserver)
-	op-süsteem; nt Ubuntu
-	ümbritsev teenindav tarkvara
-	välisteenused; nt DigiDocService
-	andmebaas vm salvestuslahendus
o	nt PostgreSQL
o	MongoDB
-	andmed
-	võtmed ja salasõnad (secrets)
-	kasutajakontod
o	õigused
-	logifailid
-	skriptid
-	repod
-	dokumentatsioon
-	arendustaskid (JIRA ticketid)
-	seadistused ümbritsevates teenustes ja süsteemides
o	seadistused tulemüüris, proxy-des, koormusjaoturis

## Süsteemi olek

Süsteemi olek on süsteemi seisund tervikuna, aga ka süsteemi osade seisund. Olek võib olla hetkeolek, kavandatav tulevikuolek või minevikuolek. Kui on vaja objekti erinevaid olekuid eristada, siis rakendatakse versioonihaldust.

Süsteemi olek ei ole kontsentreeritud ühte komponenti. Süsteemi koosneb (kitsamas mõttes): 1) ühest või mitmest rakendusest; 2) andmetest; 3) seadistustest; 4) võtmetest; 5) õigustest ja juurdepääsudest. Laiemas mõttes on süsteemi osad ka: 6) kasutusdokumentatsioon; 7) rakenduse lähtekood (repos); 8) muu süsteemi kirjeldav dokumentatsioon; 9) arendusprotsessi dok-n. Veel laiemas mõttes: ka virtuaalmasin, op-süsteem, süsteemitarkvara. Nt Väikeses TARA-Stat teenuses:
•	VM
•	Ubuntu
•	Node.js
•	Node.js teegid
•	rakendus (Node.js)
•	rakenduse seadistus (config.js)
•	MongoDB
•	MongoDB seadistus, sh andmebaasikasutajad
•	andmebaasikasutajate paroolid
•	logibaas (andmed MongoDB-s)
•	veebirakenduse võtmed

## Ajakohane pilt süsteemi konfiguratsioonist ja olekust

Ajakohase pildi loomine ja hoidmine süsteemi koosseisust on konfiguratsioonihalduse ülesanne. Konfiguratsioonikirjeldus on tekstiline või visuaalne, masin- või/ja inimloetav kirjeldus koosseisust. Suures süsteemis on mitmeid konfiguratsioonikirjeldusi. Ajakohase pildi loomine ja hoidmine süsteemi olekust on monitooringu, aga ka paljude teiste protsesside ülesanne.

## Paigaldamine

Paigaldamine on süsteemi või komponendi ülesseadmine käitlus- v kasutuskeskkonda.

Seadistamine e konfigureerimine on süsteemi või komponendi juhtparameetrite muutmine.

Ehitamine e kooste on süsteemi kokkupanek komponentidest. Ehitamine tüüpiliselt sisaldab lähtekoodi kompileerimist jm teisendusi, pakendamist, aga ka testimist.

Paigaldamine on süsteemi või selle komponendi viimine ühest olekust teise. Seadistamine on samuti viimine ühest olekust teise.

Primitiivse ettekujutuse kohaselt on paigaldamine süsteemi viimine nullolekust (puhas, uus masin) ettenähtud, nõuetekohasesse tööolekusse. Tegelikult on paigaldamisel palju vorme. Paigaldamise üks vorm on näiteks süsteemi või süsteemiosa kustutamine; sellisel juhul, vastupidi, alustatakse tööolekust ja lõpetatakse nullolekus.

Primitiivse ideaalmudeli kohaselt saab paigaldamise lõppedes süsteem olla ühes kahest olekust – kas ettenähtud tööolekus või tagasi nullolekus. Esimesel juhul öeldakse, et paigaldus õnnestus. Teisel juhul paigaldus ebaõnnestus.

Tegelikkus ei ole nii lihtne. Algolekusse tagasipöördumine ei ole alati võimalik. Alustatakse paigaldamist, tekkisid probleemid, algolekut ei õnnestu taastada –süsteem on määramata olekus.

Süsteem võib määratama olekusse minna ka "ise" s.t kasutamise või keskkonna muutumise käigus.

Süsteem ei tohiks olla määramata olekus. Määramata olek tähendab, et süsteemi käitumine: 1) ei ole ennustatav; 2) ei ole arusaadav; 3) ei vasta dokumentatsioonile (kui dokumentatsioon üldse eksisteerib); 4) ei ole arusaadav, kuidas komponendid on üksteisega seotud; 5) ei ole arusaadav, millised komponendid on ajakohased.

Dokumentatsiooni puhul tähendab määramatus seda, et ei ole selge: 1) kas dokumentatsioon on ajakohane; 2) kas tegu on viimase versiooniga; 3) kas dokumentatsioon on täielik.

Erinevad muutumistsüklid. Süsteemi igal osal on oma muutumistsükkel (elukaar). See tähendab, et süsteemi kõik osad ei muutu ühes rütmis. Süsteemi ühe osa väljavahetamine ei too kaasa vajadust kogu süsteem uuesti ehitada. Võtmeküsimused seetõttu on: 1) milliste osade muutmist on eesmärgi saavutamiseks vaja? 2) kuidas ühe osa muutmine mõjutab teisi osa s.t kas ühe osa muutmine nõuab teise osa muutmist?

Nt kas MongoDB (andmebaasi) uuesti paigaldamisel:
•	kustuvad andmed (ei)
•	kustuvad andmebaasikasutajad (jah)
•	andmebaasi logifailid (?).
Nt: rakenduse uuesti paigaldamine kirjutab üle ka seadistused (ei peaks kirjutama).

Süsteemi oleku väljaselgitamine on paigalduse alus. Primitiivne ettekujutus: paigaldame kõik uuesti nullist. Küsimused:
•	mis on paigaldatud?
•	kuhu tahame jõuda?
•	milliseid kõrvalefekte võib paigaldustoiming anda?

Süsteemi oleku väljaselgitamise vahendid (diagnostikavahendid):
•	--version (versioonipäring komponendi poole käsurealt), heartbeat-päring vms
•	eelmiste paigaldus- ja seadistustoimingute logi
•	konf-ifailid
•	süsteemi jälgitav käitumine
o	järgiproovimine
o	kasutajate teated 

Süsteemi osadevaheliste seoste jälgitavus ja arusaadavus. Nt: paigaldise kuupäev -> repo commit -> ticket -> featuuri kirjeldus ?? Süsteemi puudumisel ei ole seosed jälgitavad. Me ei tea, mis täpselt on paigaldatud, kuidas paigaldatud suhtestub repos (millises repos) oleva koodiga, dokumentatsiooniga (millised dokumentatsiooniga).

Esmakordne paigaldamine on uue süsteemi või komponendi paigaldamine, „puhtasse“ masinasse. Nullist paigaldamine on süsteemi või komponendi täiesti uuesti paigaldamine (vana kustutatakse maha või kirjutatakse üle).

Täispaigaldus on süsteemi kõigi osade paigaldus. Osa paigaldus on süsteemi ühe osa lisamine, väljavahetamine või eraldi paigaldamine.

Paigaldusprotseduur on paigaldustöö sammude algoritmiline kogum.

Paigaldustöö

Skript on automaatselt täidetav paigaldus- v seadistusprogramm. Interaktiivne skript küsib paigaldaja käest juhiseid.

Käivitamise poolest jagunevad skriptid: 1) paigaldaja poolt käivitatavateks; 2) taimeri poolt käivitatavateks (Linux cron job); 3) suurema juhtprogrammi või teise skripti poolt väljakutsutavateks.

Skript väljastab (konsoolile või logifaili) teavet paigaldustoimingute õnnestumise kohta. Skript võib tagastada tulemuskoodi (nt 0 – paigaldamine õnnestus, -1 – viga jne).




