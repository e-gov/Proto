---
permalink: AJ-soovitused
---

# Soovitusi andmejälgija rakendamiseks
{: .no_toc}

- TOC
{:toc}

## Ülevaade

Andmejälgija, [https://github.com/e-gov/AJ](https://github.com/e-gov/AJ), (AJ), on standardne protokoll ja tarkvara, mille paigaldamisega saab asutus kodanikule pakkuda ülevaadet (logi) kodaniku isikuandmete kasutamisest.

Käesolevas dokumendis anname mõningaid soovitusi AJ kasutuselevõtuks.

<img src='img/AJ.PNG' style='width:600px;'>

AJ protokoll näeb ette iga isikuandmete töötlemise fakti salvestamist 12 andmeväljast koosneva logikirjena.

Andmeväljad jagunevad andmesubjektile esitatavateks ja asutuse sisekasutuseks mõeldud, tehnilisteks andmeväljadeks. Lähemalt on andmeväljadest juttu AJ [tehnilises dokumentatsioonis](https://github.com/e-gov/AJ/blob/master/doc/spetsifikatsioonid/Tehniline_kontseptsioon.md)).

## Andmesubjektile esitatavad andmeväljad

Logikirjed kuvatakse andmesubjektile (s.t kodanikule) eesti.ee AJ kuvamisteenuses. Avalikud andmeväljad on järgmised:

nr | nimetus    | tüüp       | kohustuslik | semantika
---|------------|------------|-------------|------------
1  | `personcode` | tekst | ei          | Isikukood: kelle andmeid töödeldi. Peab algama riigi prefiksiga EE.
2  | `logtime` | datetime   | jah         | Logikirje salvestamise aeg. Eeldatakse, et tegelik andmete kasutamise aeg on lähestikku.
3  | `action` | tekst  | jah | Menetluse/tegevuse inimloetav nimi. Tuletatakse kas X-tee päringu nimest ja/või on andmetöötleja poolt seatav. Võib, aga ei pruugi langeda kokku väljaga `actioncode` s.o sisekasutuseks ettenähtud nimetusega. 
4  | `receiver` | tekst | ei | Asutus, kellele andmed väljastati. Täidetakse andmete väljastamisel andmekogust teisele asutusele X-tee kaudu. Anda asutuse inimloetav nimi.
5  | `sender` | tekst | Asutus, kellelt andmed saadi. Täidetakse andmete saamisel teisest asutusest X-tee kaudu. Anda asutuse, vajadusel ka andmekogu inimloetav nimi.

## Sisekasutuseks mõeldud andmeväljad

nr | nimetus    | tüüp       | kohustuslik | semantika
---|------------|------------|-------------|------------
6  | `id`         | integer    | jah         | Logikirje identifikaator
7  | `restrictions` | char | ei | Kui väärtus ei ole `A`, siis logikirjet eesti.ee-s ei kuvata.
8  | `receivercode` | tekst | ei | Asutuse või andmekogu registrikood/sisekasutuse nimi, kellele andmeid edastatakse.
9  | `sendercode` | tekst | ei | Asutuse või andmekogu registrikood/sisekasutuse nimi, kellelt andmed saadi. 
10 | actioncode | tekst | ei | Menetluse/tegevuse sisekasutuseks ettenähtud nimi. Võib olla X-tee päringu nimi, andmeteenuse või andmekogu nimi vms.
11 | xroadrequestid | tekst | ei | X-tee päringu identifikaator.
12 | usercode | tekst | ei | X-tee kaudu andmeid pärinud isiku või asutusesisese töötleva isiku isikukood.

Välja `action` täitmine