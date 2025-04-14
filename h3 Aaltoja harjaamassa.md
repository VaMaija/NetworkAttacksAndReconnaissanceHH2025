## x) Lue ja tiivistä. 
    Hubacek 2019: Universal Radio Hacker SDR Tutorial on 433 MHz radio plugs (Video, alkaen 3:19 ja päättyen 7:40. Yhteensä noin 4 min.)
    Universal radio hacker -ohjeet, Ensin käytetään URH-työkalun spktrianalysaattoria määrittelemään testattavan kaukosäätimen taajuus. Alasvetovalikosta Device : RTL-SDR ja taajuus arvioidaan lähelle 433 MHz ja analysaattori käynnistetään samalla painaen kaukosäätimen nappia. Analysaattori osoittaa taajuuden lähellä 433. Tästä ei pidä ottaa suoraan korkeinta kohtaa van hieman huipun vierestä. Analysaattori voidaan tämän jälkeen sulkea. Sen jälkeen äännitetään lähetystä File > Rcord Signal  Painetaan testattavasta laitteesta nappia signaali kerätään ja se tallennetaan. Tallennettu data avautuu suoraan pääsovelluksessa ja Molulaatioksi valitaan ASK (amplitude shift keying) ja sen jälkeen pyritään selvittämään parametrit. Bitlenght pitää tarkastaa. Ensimmäisen packetin osalta voidaan tarkastaa manuaalisesti. Demodulated versio, kynnystä voi manuaalisesti siirtää. Signaalin tilan voi muuttaa tässä vaiheeksi hexaksi alasvetovalikosta. Yhden hexa-paketin voi tässä vaiheessa kopioida.    
    Cornelius 2022: Decode 433.92 MHz weather station data  
Käyttäjä osti yksinkertaisen sääaseman, joka osoitti lämpötilan ja kosteuden sisätilastata ja kolmesta langattomasta ulkopisteestä. Ulkosensori oli käyttäjällä rikki ka vaikka hän sai korvaavan tuotteen halusi hän kokeilla luoda itse vastaavan sensorin. Hän sai selville tästä laitteesta ainoastaan taajuuden 433.92MHz. Tekijä käytti työkalua rtl-433 ja se onnistui purkamaan laitteen. Työkalussa oli myös database, joka tunnistaa Nexus-laitteen lähdekoodin. 
Tämän älkeen tekijä tallensi sääaseman koodia URH:n sprektianalysaattorilla ja otti talleenteelta talteen taajuuden ja signaalin voimakkuuden. Hän avasi uuden prohejtin ja teki sille kansion, johon voi tallentaa dataa. Tämän jälkeen hän tallensi signaalia, joka on kaapatun taajuuden molemmilta puolilta noin 20-100 kHz leveydeltä. Näitä datasettejä puitää saada talteen ainakin kaksi purskahdusta. purskahdusten amplitudet pitäisi olla ainakin tuplat kohinasta. Raahaa tallenne Interpretation sivulle. Ensin pitää mitata kahden  onnistuneen lähetyksen väli. Tästä selviää kuinka usein laite lähettää tietoa.  Tässä tapauksessa noin 56 sekunnin välein. Sitten hän tallensi vain yhden lähetyksen oikea klikkaus: Create signal from selection. Hän havaitsi, että sensori lähettää 36 bittiä 12 kertaa, mutta tämä sensori lähetti bitit vain kymmenen kertaa. ASK pystyy havaitsemaan parametrit automaattisesti. Jos tekijä haluaa kopioda lähetystä, niin hänen pitää selvittää myös melko tarkka signalin taajuus. Tässä testissä hän otti taajuuden 29kHz välein ja URH sekoitti vastaanotetun signaalin taajuuden sopivaksi. Kantoaalto (carrier) on päällä 500µs ja sen jälkeen pois päältä 1000µs, 2000µs tai 4000µs ennen seuraavaa lähetystä. Yhtä tällaista pulssia kutsutaan PDM:ksi (Pulse distance modulation). 

    Vapaaehtoinen, vaikeahko: Lohner 2019: Decoding ASK/OOK_PPM Signals with URH and rtl_433

    
## a) WebSDR. Etäkäytä WebSDR-ohjelmaradiota, joka on kaukana sinusta ja kuuntele radioliikennettä. Radioliikenne tulee siepata niin, että radiovastaanotin on joko eri maassa tai vähintään 400 km paikasta, jossa teet tätä tehtävää. Käytä esimerkkinä julkista, suurelle yleisölle tarkoitettua viestiä, esimerkiksi yleisradiolähetystä. Kerro löytämäsi taajuus, aallonpituus ja modulaatio. Kuvaile askeleet ja ota ruutukaappaus. (Tehtävässä ei saa ilmaista sellaisen viestin sisältöä tai olemassaoloa, joka ei ole tarkoitettu julkiseksi. Voit sen sijaan kuvailla, miten sait julkisen radiolähetyksen kuulumaan kaiuttimistasi. Julkisten, esimerkiksi yleisradiolähetysten sisältöä saa tietysti kuvailla.)

## b) rtl_433. Asenna rtl_433 automaattista analyysia varten. Kokeile, että voit ajaa sitä. './rtl_433' vastaa "rtl_433 version 25.02 branch..."

## c) Automaattinen analyysi. Mitä tässä näytteessä tapahtuu? Mitä tunnisteita (id yms) löydät? Converted_433.92M_2000k.cs8. Analysoi näyte 'rtl_433' ohjelmalla.

## d) Too compex 16? Olet nauhoittanut näytteen 'urh' -ohjelmalla .complex16s-muodossa. Muunna näyte rtl_433-yhteensopivaan muotoon ja analysoi se. Näyte Recorded-HackRF-20250411_183354-433_92MHz-2MSps-2MHz.complex16s

## e) Ultimate. Asenna URH, the Ultimate Radio Hacker.
Tarkastele näytettä 1-on-on-on-HackRF-20250412_113805-433_912MHz-2MSps-2MHz.complex16s. Siinä Nexan pistorasian kaukosäätimen valon 1 ON -nappia on painettu kolmesti. Käytä Ultimate Radio Hacker 'urh' -ohjelmaa.

## f) Yleiskuva. Kuvaile näytettä yleisesti: kuinka pitkä, millä taajuudella, milloin nauhoitettu? Miltä näyte silmämääräisesti näyttää?

## g) Bittistä. Demoduloi signaali niin, että saat raakabittejä. Mikä on oikea modulaatio? Miten pitkä yksi raakabitti on ajassa? Kuvaile tätä aikaa vertaamalla sitä johonkin. (Monissa singaaleissa on line encoding, eli lopullisia bittejä varten näitä "raakabittejä" on vielä käsiteltävä)

## h) Vapaaehtoinen: Sdr++. Kokeile sdr++ -sovellusta ja esittele sillä jokin "hei maailma" -tyyppinen esimerkki.

## i) Vapaaehtoinen, vaikeahko: GNU Radio. Asenne GNU Radio ja tee sillä yksinkertainen "Hei maailma".
