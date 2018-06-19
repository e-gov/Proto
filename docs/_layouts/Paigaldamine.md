---
permalink: Paigaldamine
footer: true
---

# Ehitamine, paigaldamine ja seadistamine

süsteemianalüüs

**Süsteem** koosneb osadest (komponentidest). Osa võib olla **rakendus**, aga ka muu, teisiti nimetatav artefakt (andmebaas, server jms).

**Rakendusel** on olek.

**Paigaldamine** on tarkvara kopeerimine vm viisil viimine ettenähtud **keskkonda**.

Paigaldamine hõlmab ka:
- eelmise paigaldatud tarkvara seiskamist
- eelmise tarkvara kõrvaldamist
- rakenduse **seadistamist** (e konfigureerimist)
- rakenduse käivitamist
- eelmiste tegevustega seotud kontrolli- ja testitegevusi.

**Paigaldaja** on paigaldustööd tegev, vastavate õigustega isik.

**Keskkond** on taristu osa, kuhu rakendus paigaldatakse. Keskkonda iseloomustab elutsükliline suunitlus (arendus, test, toodang), oma võrgu- ja turvareeglid.

**Repo** (e koodihoidla) on, kust tarkvara paigaldatakse. Repod võivad olla:
- avalikud (nt GitHub) või privaatsed (BitBucket, privaat-GitHub)
- üldotstarbelised või spetsialiseeritud (nt Nexus)
- välised (nt Maven Central Repository) või organisatsiooni omad

**Reliis** on repos oleva koodi seis, millele on omistatud **versiooninumber** ja mille juures on reliisikirjeldus (release notes).

**Paigaldusskript** on automaatselt või dialoogis täidetav paigaldusprogramm.

**Seadistus** e konfiguratsioon on rakenduse seadistuste kogum.

**Paigaldustellimus** on tellimus paigaldutoimingute tegemiseks.

**Seadistustellimus** on tellimus paigaldatud rakenduse seadistuse muutmiseks.

Paigaldis 

**Eraldipaigaldatav** tähendab, et tarkvara saab paigaldada eraldi töötava rakendusena.

**Masin** on virtuaalne v füüsiline arvuti, kuhu tarkvara paigaldatakse.

**Pipeline** on lineaarne paigaldustegevuste jada.


