### x) Lue ja tiivistä. 
    Hubacek 2019: Universal Radio Hacker SDR Tutorial on 433 MHz radio plugs (Video, alkaen 3:19 ja päättyen 7:40. Yhteensä noin 4 min.)   
    
Universal radio hacker -ohjeet, Ensin käytetään URH-työkalun spktrianalysaattoria määrittelemään testattavan kaukosäätimen taajuus. Alasvetovalikosta Device : RTL-SDR ja taajuus arvioidaan lähelle 433 MHz ja analysaattori käynnistetään samalla painaen kaukosäätimen nappia. Analysaattori osoittaa taajuuden lähellä 433. Tästä ei pidä ottaa suoraan korkeinta kohtaa van hieman huipun vierestä. Analysaattori voidaan tämän jälkeen sulkea. Sen jälkeen äännitetään lähetystä File > Rcord Signal  Painetaan testattavasta laitteesta nappia signaali kerätään ja se tallennetaan. Tallennettu data avautuu suoraan pääsovelluksessa ja Molulaatioksi valitaan ASK (amplitude shift keying) ja sen jälkeen pyritään selvittämään parametrit. Bitlenght pitää tarkastaa. Ensimmäisen packetin osalta voidaan tarkastaa manuaalisesti. Demodulated versio, kynnystä voi manuaalisesti siirtää. Signaalin tilan voi muuttaa tässä vaiheeksi hexaksi alasvetovalikosta. Yhden hexa-paketin voi tässä vaiheessa kopioida.    

    Cornelius 2022: Decode 433.92 MHz weather station data  
Käyttäjä osti yksinkertaisen sääaseman, joka osoitti lämpötilan ja kosteuden sisätilastata ja kolmesta langattomasta ulkopisteestä. Ulkosensori oli käyttäjällä rikki ka vaikka hän sai korvaavan tuotteen halusi hän kokeilla luoda itse vastaavan sensorin. Hän sai selville tästä laitteesta ainoastaan taajuuden 433.92MHz. Tekijä käytti työkalua rtl-433 ja se onnistui purkamaan laitteen. Työkalussa oli myös database, joka tunnistaa Nexus-laitteen lähdekoodin. 
Tämän älkeen tekijä tallensi sääaseman koodia URH:n sprektianalysaattorilla ja otti talleenteelta talteen taajuuden ja signaalin voimakkuuden. Hän avasi uuden prohejtin ja teki sille kansion, johon voi tallentaa dataa. Tämän jälkeen hän tallensi signaalia, joka on kaapatun taajuuden molemmilta puolilta noin 20-100 kHz leveydeltä. Näitä datasettejä puitää saada talteen ainakin kaksi purskahdusta. purskahdusten amplitudet pitäisi olla ainakin tuplat kohinasta. Raahaa tallenne Interpretation sivulle. Ensin pitää mitata kahden  onnistuneen lähetyksen väli. Tästä selviää kuinka usein laite lähettää tietoa.  Tässä tapauksessa noin 56 sekunnin välein. Sitten hän tallensi vain yhden lähetyksen oikea klikkaus: Create signal from selection. Hän havaitsi, että sensori lähettää 36 bittiä 12 kertaa, mutta tämä sensori lähetti bitit vain kymmenen kertaa. ASK pystyy havaitsemaan parametrit automaattisesti. Jos tekijä haluaa kopioda lähetystä, niin hänen pitää selvittää myös melko tarkka signalin taajuus. Tässä testissä hän otti taajuuden 29kHz välein ja URH sekoitti vastaanotetun signaalin taajuuden sopivaksi. Kantoaalto (carrier) on päällä 500µs ja sen jälkeen pois päältä 1000µs, 2000µs tai 4000µs ennen seuraavaa lähetystä. Yhtä tällaista pulssia kutsutaan PDM:ksi (Pulse distance modulation). Kantoaallon off-alueet ovat bittejä eli 1ms tai 2 ms. Tekijä oletti, että lyhyt (1 millisekunti) off on 0-bit ja pitkä tauko (2ms) on 1-bit. Tämä riippuu kuitenkin ohjelmoinnista. Kantoaallon signaalista löytyneistä numeroista 500, 1000, 2000 ja 4000 lasketaan suurin yhteinen nimittäjä eli 500. Tämä on demoduloinnin edellyttämä näytteiden numero. URH:n analyysimoodissa tässä vaiheessa pitäisi näkyä sama määrä lähetyspurskeita eli 10 (piti olla 12) eli tätä kautta pääsee koodia editoimaan **Edit-Decoding** Käyttäjä käytti morsekoodin analytiikkaa rakentamaan lyhyistä ja pitkistä koodeista (bitit) uutta signaalia.   


    Vapaaehtoinen, vaikeahko: Lohner 2019: Decoding ASK/OOK_PPM Signals with URH and rtl_433

    
### a) WebSDR. Etäkäytä WebSDR-ohjelmaradiota, joka on kaukana sinusta ja kuuntele radioliikennettä. 

Kuuntelin webSDR -radiota kanavaa #es'hail-2 osoitteessa https://eshail.batc.org.uk/nb/  10489829.75 - .88 kHz filter 2.70 kHz 
Kyseessä oli Qatarin radioamatöörien, saksalaisten radioamatöörien sekä satelliittiyrityksen Es'hailSatin yhteistyössä luoma kanava. Viestiliikennettä oli Isle of Wightin, Intian, Italian ja Saksan välillä. Lähinnä yhteyskokeiluja ympäri maailman.   

Googletin useita websdr-radiokanavia, mutta en saanut kuuluviin juurikaan selkokielistäpuhetta ennen tätä.   

![image](https://github.com/user-attachments/assets/3de8f71e-d3cd-489a-bced-5949c5a127b5)  

Kyseiseltä verkkosivulta sai suoraan audio tallennusta ja tallenteen pystyi downloadata suoraan omalle koneelle. 
Testasin hertzejä muuttamalla millä lukemalla saan vielä selkokielisestä puheesta selvää.  
10489829.75 - .88 kHz 2.70kHz  

### b) rtl_433. Asenna rtl_433 automaattista analyysia varten. Kokeile, että voit ajaa sitä. './rtl_433' vastaa "rtl_433 version 25.02 branch..."  

Käytössäni on windows.kone ja Linux kali, joten rtl_433 löytyi komennolla sudo apt-get install rtl_433

┌──(maija㉿kaliMaija)-[~]  
└─$ sudo apt-get install rtl-433  
ohjelma ei käynnistynyt Karvisen vinkillä ./rtl_433   

└─$ rtl_433 -h  

Usage:  
  A "rtl_433.conf" file is searched in "./", XDG_CONFIG_HOME e.g. **"$HOME/.config/rtl_433/"**,  cd  /us

Ohjelmaa ei löytynyt etsinnöistä huolimatta...  Kysyin apua chatgpt:ltä. 
Olihan se ollut hienoa, että Kalissa asennus olisi mennyt muutamalla komennolla.  

$ sudo apt install git cmake build-essential libtool libusb-1.0-0-dev librtlsdr-dev rtl-sdr   //Asensi tarvittavat riippuvuudet  
ei auttanut. Annoin ohjelmalle chmodilla 775 -oikeudet. 
tehtävästä jäi epäselväksi, että pitikö ladata uusin sopiva versio vai soapy. Sain Soapyn lopulta toimimaan lataamalla sen suoraan Karvisen linkistä ja antamalla sille 775 -oikeudet. Kopioin ohjelman /usr/local/bin/ osoitteeseen.  

![image](https://github.com/user-attachments/assets/41587e99-c589-49ab-94c8-4c989a700dfa)


### c) Automaattinen analyysi. Mitä tässä näytteessä tapahtuu? Mitä tunnisteita (id yms) löydät? Converted_433.92M_2000k.cs8. Analysoi näyte 'rtl_433' ohjelmalla.  
Latasin näytteen ja avasin sen seuraavalla komennolla  
└─$ rtl_433 -r ~/Downloads/Converted_433.92M_2000k.cs8  

time      : @0.083284s                                                                                                                    
model     : KlikAanKlikUit-Switch                  id        : 8785315
Unit      : 0            Group Call: No            Command   : Off           Dim       : No            Dim Value : 0
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
time      : @0.083284s                                                                                                                    
model     : Proove-Security                        House Code: 8785315
Channel   : 3            State     : OFF           Unit      : 3             Group     : 0
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
time      : @0.083284s                                                                                                                    
model     : Nexa-Security House Code: 8785315
Channel   : 3            State     : OFF           Unit      : 3             Group     : 0
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
time      : @0.163125s                                                                                                                    
model     : KlikAanKlikUit-Switch                  id        : 8785315
Unit      : 0            Group Call: No            Command   : Off           Dim       : No            Dim Value : 0
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
time      : @0.163125s                                                                                                                    
model     : Proove-Security                        House Code: 8785315
Channel   : 3            State     : OFF           Unit      : 3             Group     : 0
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
time      : @0.163125s                                                                                                                    
model     : Nexa-Security House Code: 8785315
Channel   : 3            State     : OFF           Unit      : 3             Group     : 0
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
time      : @0.242956s                                                                                                                    
model     : KlikAanKlikUit-Switch                  id        : 8785315
Unit      : 0            Group Call: No            Command   : Off           Dim       : No            Dim Value : 0
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
time      : @0.242956s                                                                                                                    
model     : Proove-Security                        House Code: 8785315
Channel   : 3            State     : OFF           Unit      : 3             Group     : 0
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
time      : @0.242956s                                                                                                                    
model     : Nexa-Security House Code: 8785315
Channel   : 3            State     : OFF           Unit      : 3             Group     : 0
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
time      : @0.383568s                                                                                                                    
model     : KlikAanKlikUit-Switch                  id        : 8785315
Unit      : 0            Group Call: No            Command   : Off           Dim       : No            Dim Value : 0
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
time      : @0.383568s                                                                                                                    
model     : Proove-Security                        House Code: 8785315
Channel   : 3            State     : OFF           Unit      : 3             Group     : 0
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
time      : @0.383568s                                                                                                                    
model     : Nexa-Security House Code: 8785315
Channel   : 3            State     : OFF           Unit      : 3             Group     : 0






### d) Too compex 16? Olet nauhoittanut näytteen 'urh' -ohjelmalla .complex16s-muodossa. Muunna näyte rtl_433-yhteensopivaan muotoon ja analysoi se. Näyte Recorded-HackRF-20250411_183354-433_92MHz-2MSps-2MHz.complex16s

### e) Ultimate. Asenna URH, the Ultimate Radio Hacker.
Tarkastele näytettä 1-on-on-on-HackRF-20250412_113805-433_912MHz-2MSps-2MHz.complex16s. Siinä Nexan pistorasian kaukosäätimen valon 1 ON -nappia on painettu kolmesti. Käytä Ultimate Radio Hacker 'urh' -ohjelmaa.

### f) Yleiskuva. Kuvaile näytettä yleisesti: kuinka pitkä, millä taajuudella, milloin nauhoitettu? Miltä näyte silmämääräisesti näyttää?

## g) Bittistä. Demoduloi signaali niin, että saat raakabittejä. Mikä on oikea modulaatio? Miten pitkä yksi raakabitti on ajassa? Kuvaile tätä aikaa vertaamalla sitä johonkin. (Monissa singaaleissa on line encoding, eli lopullisia bittejä varten näitä "raakabittejä" on vielä käsiteltävä)

## h) Vapaaehtoinen: Sdr++. Kokeile sdr++ -sovellusta ja esittele sillä jokin "hei maailma" -tyyppinen esimerkki.

## i) Vapaaehtoinen, vaikeahko: GNU Radio. Asenne GNU Radio ja tee sillä yksinkertainen "Hei maailma".


LÄHTEET: 
Hubareck 2019 [Universal radio Hacker SDR Tutorial on 433MHz radio plugs](https://youtu.be/sbqMqb6FVMY?t=199) katsottu 13.4.2025  
Cornelius 2022 [Decode 433.92 MHz weather station data ](https://www.onetransistor.eu/2022/01/decode-433mhz-ask-signal.html) luettu 13.4.2025    
RTL Asennus: Merbanan https://github.com/merbanan/rtl_433  luettu osittain 14.4.2025  
Apuna myös chatgpt  
AMSAT DL [tausta](https://amsat-dl.org/en/eshail-2-amsat-phase-4-a/) luettu 14.4.2025  
Qatar-OSCAR 100 Narrowband [WebSDR](https://eshail.batc.org.uk/nb/) kuunneltu 14.4.2025
Karvinen 2025 [läksyt ja vinkit](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/) luettu 14.4.2025  
