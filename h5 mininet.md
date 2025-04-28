h5 kotitehtävät 

Sain mininetin käyttöön lataamalla kurssin moodelsta Lari Iso-Anttilan [linkin](https://hhmoodle.haaga-helia.fi/mod/url/view.php?id=3246688).  
Lisäksi latasin VMwaren Workstationin Windowsille. Tähän vaadittiin sisäänkirjautuminen Broadcomin VMware-verkkosvulle(https://www.vmware.com/products/desktop-hypervisor/workstation-and-fusion).  
mininetin tar-paketin sai avattua 7-zip-ohjelmalla. 

En saanut mininettiä toimimaan, joten kokeilin toista konetta, jossa avasin sen oracle virtual Boxiin. Samaan mihin on alussa asennettu Kali. Ei pelittänyt.  

$sudo loadkeys fi  //Vaihtaa näppäimistön suomeksi  
$

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
