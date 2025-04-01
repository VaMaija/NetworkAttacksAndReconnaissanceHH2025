## x) Lue ja tiivistä.  
   Karvinen 2025: [Wireshark - Getting Started](https://terokarvinen.com/wireshark-getting-started/)   
Wireshark on tietoliikenteen kaistelija ja analysointityökalu.   
Wiresharkin asennus onnistuu komennolla **$ sudo apt-get install wireshark**, jonka jälkeen sallitaan muidenkin kuin superusereiden wiresharkin käyttö.  
Wiresharkin käyttäjä tulee lisätä porukkaan komennolla **$ sudo adduser _nimi_ wireshark**  
Komennolla **$newgrp wireshark** luodaan shell-komento wireshark, joka avaa ryhmän jäsenille graafisen käyttöliittymän ohjelmalle. 
Karvisen sivu ohjaa alkuun paketien kaappaamisen ja tallentamisen kanssa.   

   
   Karvinen 2025: [Network Interface Names on Linux](https://terokarvinen.com/network-interface-linux/)    


## a) Linux. Asena Debian tai Kali virtuaalikoneeseen.
Asensin Kalin, sillä sitä en ole vielä kokeillut. Kali linux 2025.1a-live-amd64.iso.torrent osoitteesta https://www.kali.org/get-kali/#kali-live  

## b) Ei voi kalastaa. Katkaisen virtuaalikonen yhteys nettiin.  
Google avuksi: "miten katkaisen virrat virtuaalikoneesta?"  
<img width="548" alt="thumbnail_kaapelin irrotus" src="https://github.com/user-attachments/assets/b7bc9d4f-84e6-4112-9527-7e7ac9aba706" />

## c) Wireshark. Asenna ohjelman ja nappaa liikennettä.   

<img width="368" alt="thumbnail_wireshark versio" src="https://github.com/user-attachments/assets/bfdcaafc-80af-4347-98c0-9b1b3f47fe1c" />
  
**$ sudo apt-get install wireshark  
$ newgrp wireshark  
$ wireshark >> käynnistää ohjelman**  

Piti avata selain, jotta paketteja näkyi.   
<img width="383" alt="kaappausta" src="https://github.com/user-attachments/assets/caf16bc3-40c2-479b-90b4-3db384c1eb7d" />  


## d) Oikeesti TCP/IP osoita neljä verkkokerrosta yhdestä paketista.  

<img width="875" alt="koko frame" src="https://github.com/user-attachments/assets/6b8651ad-1fe8-4bdd-9cb9-66aa5d742585" />   

**Koko frame 6799**

<img width="904" alt="ethernet source destination" src="https://github.com/user-attachments/assets/d455fe48-8f88-4378-b9db-2130474b428e" />   

**"Hei! Olen laite jonka Mac-osoite on 52:55:0a:00:02:02, haluaisin yhteyden naapurin mac-osoitteeseen 08:00:27:c7:ab:94"** 

<img width="888" alt="network layer ip-osoite " src="https://github.com/user-attachments/assets/8dff22f7-6e80-4216-8a0d-e36d5e56cecc" />  

**"Terve Mac 52:55:0a:00:02:02, haluamasi naapuri löytyy IPv4 osoitteesta 10.0.2.15"**

<img width="916" alt="tcp portit" src="https://github.com/user-attachments/assets/5674bcbe-aee6-4da9-bd53-f45fc3ae3c54" />  

**"Asia kunnossa, täältä tulee portista 443 porttiin 60928 dataa, kuittaatko kun kaikki paketit on perillä. Lähetyksen pituus on 1128 tavua"**  

<img width="886" alt="datat siirretään applicationissa" src="https://github.com/user-attachments/assets/6e452e6f-24a9-4cbd-a59d-b9218eac0a97" />  

**vastaanotto + "Olen vastaanottanut 1128 tavua"**   



## e) Mitä tuli surffattua? Avaa surfing-secure-pcap ja kuvaile kaappausta. 
Tästä paketista en vielä tällä opetuksen määrällä osaa sanoa juuri mitään.  
En ole aiemmin käyttänyt wiresharkia.   
frameja on 283 ja paketin kaappaamiseen on kulunut aikaa n. 7,5 sekuntia  

## f) Mitä selainta käyttäjä käyttää.  (vapaaehtoinen tehtävä) 

En tiedä miten tämän selvittäisi. Giangin step-by-step -ohjeesta en ymmärtänyt juurikaan mitään.  😅    

## g) Minkä merkkinen verkkokortti käyttäjällä on?  

![Mac](https://github.com/user-attachments/assets/059f8f82-4727-4d4f-b22a-1ad46c7e027a)   

Otin ensimmäisestä framesta Ethernet sourcen MAC-osoitteen ja syötin sen verkkohakuun [https://mac.lc/#search](https://mac.lc/address/52:54:00:2f:e1:e5)   

![mac haku online](https://github.com/user-attachments/assets/d68aefdd-b240-4803-bc18-ace670ddbc6c)  
  
## h) Millä webbipalvelimella käyttäjä on surffannut.

![Millä webbipalvelimilla käyttäjä on surffannut](https://github.com/user-attachments/assets/d8b26c05-1121-4f43-a759-4949bb313017)  

Olisiko protokollan kohdentaminen DNS tietoihin tähän kysymykseen oikea vastaus?   

## i) Analyysi omasta liikenteestä. Analysoi ja selitä. 

Avasin taustalle youtuben videon pyörimään, koska halusin nähdä UDP-liikennettä. 

<img width="957" alt="oma liikenne" src="https://github.com/user-attachments/assets/6d6469d5-668c-4d1e-8e44-d2856b648d49" />  

Paketit 1-20 ovat liikkuneet ensimmäisen sadasosasekunnin aikana UDP-protokollalla kohdeosoitteesta 173.194.18.167 (Googlen ip-avaruus) 
Ethernet II kerroksessa näkyy source SCR mac-osoitteena 08:00:27:c7:ab:94 (PCS Systemtechnik GmbH), joka nopealla googlettelulla näytti olevan Virtualboxin ethernetin MACin haltija. 
IPv4 lähde on 10.0.2.15 eli sisäinen ip-osoite ja kohde 173.194.18.168 (googlen ip-avaruus)  
UDP protokollan lähdeportti on 443 ja kohdeportti 55313  yhden framen datan määrä on 1357 tavua  

Frameja on pystyi nappaamaan kymmenesosasekunnissa 230 kpl, joten manuaalinen analysointi veisi liikaa aikaa.   






LÄHTEET: 
Karvinen 2025: [läksysivu](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/#laksyt) luettu 30.3.2025  
Karvinen 2025: [Wireshark - Getting Started](https://terokarvinen.com/wireshark-getting-started/) luettu 30.3.2025  
Kali Linux https://www.kali.org/get-kali/#kali-live  
Karvinen 2025: [Network Interface Names on Linux](https://terokarvinen.com/network-interface-linux/) luettu 31.3.2025  
Gianglex [h1 Sniff](https://github.com/gianglex/Courses/blob/6e74794c2e27752698f9bff0455a927843d9f934/Verkkoon-Tunkeutuminen-ja-Tiedustelu/h1-sniff.md#f-mit%C3%A4-selainta-k%C3%A4ytt%C3%A4j%C3%A4-k%C3%A4ytt%C3%A4%C3%A4) luettu 31.3.2025  
madbackets.com [TCP Sequence and Acknowledgement Numbers Explained](https://madpackets.com/2018/04/25/tcp-sequence-and-acknowledgement-numbers-explained/) luettu 31.3.2025   
MACin perusteella valmistaja [https://mac.lc/#search](https://mac.lc/address/52:54:00:2f:e1:e5)  
