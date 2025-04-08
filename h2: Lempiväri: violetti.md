# h2 Lempiväri violetti

## x) Selityksiä konsepteista:  
**Tuskien pyramidi**
idea: Tuskien pyramidi. Alaosassa on helpommin väärennettävät tai muutettavat arvot ja mitä korkeammalle mennään niin arvojen muuntaminen vaikeutuu.   
![image](https://github.com/user-attachments/assets/6fb90499-3c51-4289-9db3-dd7c8340706d)  


  **Timanttimalli** 
Timanttimallin avulla analysoidaan kybertapahtuma läpi neljän pääkohdan kautta eli Hyökkääjän, Kyvykkyyden, Infran ja Kohteen. Kuka teki, Miten teki, Missä teki ja Kenelle tehtiin?   
![timanttimalli](https://github.com/user-attachments/assets/e65266f5-4098-48d2-82d9-07f1bc8e6026)  
kuva: Caltagirone et al 2013 s. 9/61

## a) Apache log  

<img width="829" alt="localhost 22 53" src="https://github.com/user-attachments/assets/f82fb734-fdd6-49a2-88a3-a58dd4c1f985" />  
<img width="568" alt="logit" src="https://github.com/user-attachments/assets/5d71e27c-e898-43b6-91cc-f71c19a8ac4a" />  

 1 rivi: Olen lähettänyt osoitteesta 127.0.0.1 8.4.2025 klo 22:53:12 (UTC+3) pyynnön GET HTTP/1.1(protokolla) 200(onnistui) 3383 (koko tavuina?) >User agent: Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0. Useragent kertoo, että pyyntö on tehty Linux x86_64 -käyttöjärjestelmällä.  
 2. rivi: järjestelmä on avannut samalla sadasosasekunnilla openlogo-75 kuvan localhostiin.  
 3. rivi: Järjestelmä on yrittänyt avata seuraavalla sadasosalla Favicon.ico tiedostoa, mutta epäonnistui (404) sen hakemisessa http://localhost- osoitteesta. 

 ## b) nmapped  
 
 ┌──(maija㉿kaliMaija)-[~]  
└─$ **sudo nmap -A localhost**                    
[sudo] password for maija:   
Starting Nmap 7.95 ( https://nmap.org ) at 2025-04-08 23:37 EEST  // nmap-skannaus on aloitettu versiolla 7.95 tuohon kellonaikaan   
Nmap scan report for localhost (127.0.0.1)    //skannataan tätä osoitetta eli localhostia osoitteessa 127.0.0.1  
Host is up (0.000051s latency).  //skannattava hostkone on käynnissä. paketti kulkee edestakaisin skannaajan ja hostin koneiden välillä tuon ajan eli 0.00051s  
Other addresses for localhost (not scanned): ::1   // localhostilla on toinen osoite, joka on ::1  
All 1000 scanned ports on localhost (127.0.0.1) are in ignored states.  // tämän kohteen 1000 yleisintä porttia ovat suljettuja.  
Not shown: 1000 closed tcp ports (reset)   
Too many fingerprints match this host to give specific OS details  // OS järjestelmän yksityskohtia ei saatu selvitettyä 
Network Distance: 0 hops   // Skannaus on tapahtunut paikallisessa verkossa eikä verkkosolmuja ole ollut matkalla.  

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .  
Nmap done: 1 IP address (1 host up) scanned in 2.14 seconds  // Skannaukseen kulunut aika.  

 
 
 








LÄHTEET:  
Tero Karvinen 2025 [kurssisivu](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/)  luettu tehtävänanto 8.4.2025  
David J Bianco 2013 [The Pyramid pf pain](https://detect-respond.blogspot.com/2013/03/the-pyramid-of-pain.html) luettu 8.4.2025  
Caltagirone et al 2013: [Diamond Model](https://www.threatintel.academy/wp-content/uploads/2020/07/diamond-model.pdf) kuva kopioitus s. 9 vilkaistu 8.4.2025  
Caltagirone 7/2020 [Diamond model summary](https://www.threatintel.academy/wp-content/uploads/2020/07/diamond_summary.pdf)  tiivistetty ja suomennettu chatgpt:n avulla 8.4.2025  

