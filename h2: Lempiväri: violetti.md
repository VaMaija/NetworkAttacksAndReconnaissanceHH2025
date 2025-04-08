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
Starting Nmap 7.95 ( https://nmap.org ) at 2025-04-08 23:37 EEST  **// nmap-skannaus on aloitettu versiolla 7.95 tuohon kellonaikaan**
Nmap scan report for localhost (127.0.0.1)    **//skannataan tätä osoitetta eli localhostia osoitteessa 127.0.0.1**  
Host is up (0.000051s latency).  **//skannattava hostkone on käynnissä. paketti kulkee edestakaisin skannaajan ja hostin koneiden välillä tuon ajan eli 0.00051s**  
Other addresses for localhost (not scanned): ::1   **// localhostilla on toinen osoite, joka on ::1**  
All 1000 scanned ports on localhost (127.0.0.1) are in ignored states.  **// tämän kohteen 1000 yleisintä porttia ovat suljettuja.**  
Not shown: 1000 closed tcp ports (reset)   
Too many fingerprints match this host to give specific OS details  **// OS järjestelmän yksityskohtia ei saatu selvitettyä** 
Network Distance: 0 hops   **// Skannaus on tapahtunut paikallisessa verkossa eikä verkkosolmuja ole ollut matkalla.**  

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .  
Nmap done: 1 IP address (1 host up) scanned in 2.14 seconds // **Skannaukseen kulunut aika.**  

┌──(maija㉿kaliMaija)-[~]  
└─$ sudo nmap -T4 -vv -A -p 80 localhost  **//skannaa superuserina -T4 (Tehokkaasti) -vv (näyttää tiedot yksityiskohtaisesti skannauksen aikana) -A (aggressiivinen skannaus, tarkastaa mm verkon reitin -p (portti) 80**
Starting Nmap 7.95 ( https://nmap.org ) at 2025-04-08 23:46 EEST  
NSE: Loaded 157 scripts for scanning.  **// NSE valmiita työkaluja ladattu 157 kpl**  
NSE: Script Pre-scanning.  
NSE: Starting runlevel 1 (of 3) scan.  
Initiating NSE at 23:46  
Completed NSE at 23:46, 0.00s elapsed  
NSE: Starting runlevel 2 (of 3) scan.  
Initiating NSE at 23:46  
Completed NSE at 23:46, 0.00s elapsed  
NSE: Starting runlevel 3 (of 3) scan.  
Initiating NSE at 23:46  
Completed NSE at 23:46, 0.00s elapsed  
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.  
mass_dns: warning: Unable to determine any DNS servers. Reverse DNS is disabled. Try using --system-dns or specify valid servers with --dns-servers  
Initiating SYN Stealth Scan at 23:46  
Scanning localhost (127.0.0.1) [1 port]  
Completed SYN Stealth Scan at 23:46, 0.03s elapsed (1 total ports)  
Initiating Service scan at 23:46  
Initiating OS detection (try #1) against localhost (127.0.0.1)  
Retrying OS detection (try #2) against localhost (127.0.0.1)  
NSE: Script scanning 127.0.0.1.  
NSE: Starting runlevel 1 (of 3) scan.  
Initiating NSE at 23:46  
Completed NSE at 23:46, 0.01s elapsed  
NSE: Starting runlevel 2 (of 3) scan.  
Initiating NSE at 23:46  
Completed NSE at 23:46, 0.00s elapsed  
NSE: Starting runlevel 3 (of 3) scan.  
Initiating NSE at 23:46  
Completed NSE at 23:46, 0.00s elapsed  
Nmap scan report for localhost (127.0.0.1)  
Host is up, received localhost-response (0.000050s latency).  
Other addresses for localhost (not scanned): ::1  
Scanned at 2025-04-08 23:46:10 EEST for 2s  

PORT   STATE  SERVICE REASON       VERSION  
80/tcp closed http    reset ttl 64  
Too many fingerprints match this host to give specific OS details  
TCP/IP fingerprint:  
SCAN(V=7.95%E=4%D=4/8%OT=%CT=80%CU=40126%PV=N%DS=0%DC=L%G=N%TM=67F58B14%P=x86_64-pc-linux-gnu)  
SEQ(CI=Z%II=I)  
T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)  
T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)  
T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)  
U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)  
IE(R=Y%DFI=N%T=40%CD=S)  
  
Network Distance: 0 hops  
  
NSE: Script Post-scanning.  
NSE: Starting runlevel 1 (of 3) scan.  
Initiating NSE at 23:46  
Completed NSE at 23:46, 0.00s elapsed  
NSE: Starting runlevel 2 (of 3) scan.  
Initiating NSE at 23:46  
Completed NSE at 23:46, 0.00s elapsed  
NSE: Starting runlevel 3 (of 3) scan.  
Initiating NSE at 23:46  
Completed NSE at 23:46, 0.00s elapsed  
Read data files from: /usr/share/nmap  ⭐ Tästä löytyy reitti scripteihin ⭐  
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .  
Nmap done: 1 IP address (1 host up) scanned in 1.81 seconds  
           Raw packets sent: 13 (1.712KB) | Rcvd: 24 (2.700KB)  **//Analysoinnissa on käytetty apuna chatGPT**  


## c) Skriptit  
<img width="451" alt="Scripts" src="https://github.com/user-attachments/assets/22221592-3ea5-405d-adb5-b76faca8bb97" />  

## d) Jäljet lokissa    

<img width="368" alt="logitukset hukassa" src="https://github.com/user-attachments/assets/cd90173f-7397-4556-8810-00db33ebdd0e" />  

  En saanut logituksia näkymään tai sitten vaan etsin ihan väärästä paikasta.  
## e)  Wire sharking  
Kaappasim nmapituksen aikaista liikennettä, mutta en koska wireshark on uusi työkalu käytössöni, niin en osannut etsiä nmap tai NMAP tai NSE -tietoja kaappauksesta.  
yritin myös vinkeistä löytyvää **Dislay filter: frame contains "nmap"** mutta ei onnistunut. 
## f)  
jaahas. 6 tuntia myöhemmin on aika antaa periksi. Koska en tiedä mitä on olen todellisuudessa tekemässä... 
En saa edellisiä kohtia onnistumaan.  

 
 








LÄHTEET:  
Tero Karvinen 2025 [kurssisivu](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/)  luettu tehtävänanto 8.4.2025  
David J Bianco 2013 [The Pyramid pf pain](https://detect-respond.blogspot.com/2013/03/the-pyramid-of-pain.html) luettu 8.4.2025  
Caltagirone et al 2013: [Diamond Model](https://www.threatintel.academy/wp-content/uploads/2020/07/diamond-model.pdf) kuva kopioitus s. 9 vilkaistu 8.4.2025  
Caltagirone 7/2020 [Diamond model summary](https://www.threatintel.academy/wp-content/uploads/2020/07/diamond_summary.pdf)  tiivistetty ja suomennettu chatgpt:n avulla 8.4.2025  

