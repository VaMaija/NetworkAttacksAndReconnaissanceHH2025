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





## e) Mitä tuli surffattua? Avaa surfing-secure-pcap ja kuvaile kaappausta. 


## f) Mitä selainta käyttäjä käyttää.  (vapaaehtoinen tehtävä)   

## g) Minkä merkkinen verkkokortti käyttäjällä on?  

## h) Millä webbipalvelimella käyttäjä on surffannut. TLS salaus  

## i) Analyysi omasta liikenteestä. Analysoi ja selitä. 




LÄHTEET: 
Karvinen 2025: [läksysivu](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/#laksyt) luettu 30.3.2025  
Karvinen 2025: [Wireshark - Getting Started](https://terokarvinen.com/wireshark-getting-started/) luettu 30.3.2025  
Kali Linux https://www.kali.org/get-kali/#kali-live  
Karvinen 2025: [Network Interface Names on Linux](https://terokarvinen.com/network-interface-linux/) luettu 31.3.2025  
Gianglex [h1 Sniff](https://github.com/gianglex/Courses/blob/6e74794c2e27752698f9bff0455a927843d9f934/Verkkoon-Tunkeutuminen-ja-Tiedustelu/h1-sniff.md#f-mit%C3%A4-selainta-k%C3%A4ytt%C3%A4j%C3%A4-k%C3%A4ytt%C3%A4%C3%A4) luettu 31.3.2025  
