h5 kotitehtävät 

Sain mininetin käyttöön lataamalla kurssin moodelsta Lari Iso-Anttilan [linkin](https://hhmoodle.haaga-helia.fi/mod/url/view.php?id=3246688).  
Lisäksi latasin VMwaren Workstationin Windowsille. Tähän vaadittiin sisäänkirjautuminen Broadcomin VMware-verkkosvulle(https://www.vmware.com/products/desktop-hypervisor/workstation-and-fusion).  
mininetin tar-paketin sai avattua 7-zip-ohjelmalla. 

En saanut mininettiä toimimaan, joten kokeilin toista konetta, jossa avasin sen oracle virtual Boxiin. Samaan mihin on alussa asennettu Kali. Ei pelittänyt.  

$ sudo loadkeys fi  //Vaihtaa näppäimistön suomeksi  
$ sudo apt-get update  
$ ryu-manager ryu.app.simple_switch_13   // Chat gpt kertoi,että on normaalia että Ryu-managerin toimiessa mitään ei tapahdu komentokehotteessa.   
$ sudo mn --topo single,3 --mac --switch ovsk --controller remote //ei toiminut, mininet ei käynnistynyt.      
jäi pyörittämään tyhjää.  
Kävin chatGPT:n avulla läpi erri mininetin osia neljä tuntia, mutta en saanut verkkoa pystyyn. 

En saanut VMtoolseja käyttöön CLI:stä enkä GUI:sta. 
Olisi ollut hyvä päästä kokeilemaan itse asiaa. 

menin siitä mistä aita oli matalin ja käynnistin mn:  
$ sudo mn  
$ pingall  
  ![sudo mn](https://github.com/user-attachments/assets/266b104b-3389-441a-b001-1d22b48608a1)  

$ xterm h1 
    >cannot connect to display

    xtermiä en saanut toimimaan. 
$ sudo apt install open-vm-tool //ei löytänyt toimivaa pakettia.  


Palasin alkuperäiseenkoneeseen ja latasin VMWare Tools 11.3.5 [Broadcomin sivulta](https://support.broadcom.com/group/ecx/productfiles?subFamily=VMware%20Tools&displayGroup=VMware%20Tools%2011.x&release=11.3.5&os=&servicePk=203551&language=EN&freeDownloads=true)
Avasin mininetin seuraavilla komennoilla: 
$ ryu-manager ryu.app.simple_switch_13
$ sudo mn --topo single,3 --mac --switch ovsk --controller remote







a) Tutustu seuraavaan työkaluun
https://github.com/kgretzky/evilginx2
Vastaa seuraaviin kysymyksiin
Asensitko työkalun, jos asensit niin kirjoita miten sen teit.
Mitä teit työkalun kanssa?
Onnistuitko huijaamaan liikennettä
b) Sinulla on käytössäsi mininet ympäristö. Luo ympäristö, jossa voit tehdä TCP SYN-Flood hyökkäyksen.
Kirjoita miten loit mininet ympäristön ja miten toteutit hyökkäyksen.
