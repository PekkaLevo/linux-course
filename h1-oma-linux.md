# h1 - Oma linux

## x) Tiivistelmät kahdesta tehtävän annossa annetusta artikkelista

  ### Raportin kirjoittaminen
  - Raportin tulee olla toistettavissa ja kattaa myös ympäristö, jossa raportin aihe suoritettiin.
  - Raportin tulee myös olla täsmällinen, eli tulisi sisältää tarkat tiedot, ajan kulun ja työvaiheet.
  - Raportin sisällön tulee olla helppolukuista ja selkeää, sekä viitata mahdollisiin käytettyihin lähteisiin.
  - Raportissa ei saa esiintyä sepittämistä, plagiointia ja kuvien luvatonta kopiointia.

  ### Free Software Foundation: FSF Free Software Definition
  Vapaa ohjelmisto(free software) tarkoittaa ohjelmistoa, joka kunnioittaa käyttäjien ja yhteisön vapautta, sekä tarjoaa käyttäjilleen
  neljä vapaan ohjelmistolle vaadittua kriteeriä:
    - Vapaus käyttää ohjelmistoa haluamaansa käyttötarkoitukseen, ilman rajoitteita
    - Vapaus tutkia ja muokata ohjelmistoa ja sen toimintaa haluamallaan tavalla, edellyttäen oikeuksia lähdekoodiin.
    - Vapaus jakaa ja levittää kopioita muita auttaaksesi.
    - Vapaus jakaa ja levittää myös omia muokattuja ja paranneltuja versioita.
  Vapaalla ohjelmistolla korostetaan käyttäjän vapautta. Ohjelmiston ei tarvitse olla ilmainen, jotta se olisi vapaa ohjelmisto, 
  vaan vapaudella tarkoitetaan käyttäjän oikeuteen ohjelmiston vapaaseen käyttöön. Vapaa ohjelmiston kaupallinen käyttö on myös 
  sallittua, päinvastoin sen pitää olla vapaa myös kaupalliseen käyttöön, jos tämä käyttö tapahtuu lain mukaisesti. 
  Ohjelmiston manuaalien eli käyttöoppaiden tulee tosin olla ilmaisia. 

## a) Linuxin asennus virtuaalikoneeseen

  Suoritin harjoituksen asunnossani Helsingissä maanantaina 26.8.2024 , HP 250 G8 Notebook tietokoneellani.
  Aloitin tehtävän tekemisen klo 19.05 ja ensimmäisenä avasin Virtualbox Manager ohjelman. Ensimmäisenä painoin VirtualBox Managerin etusivulla "new" kuvaketta sivun oikeassa yläreunassa. Helpottakseni
  virtuaalikoneen tekemistä painoin "expert mode" painiketta, jotta saan kaikki vaadittavat kentät yhdelle sivulle. Painiketta painettuani, avautui uusi ikkuna. 
  "Name and Operating System"-palkin alla olevaan täytin "name:"-palkkiin haluamani nimen virtuaalikoneelle, "Folder:"-palkkiin kansion, johon halusin tallentaa koneen, valitsen "ISO image" painikkeesta "other"
  vaihtoehdon ja etsin lataamani Linux "image", jonka haluan asentaa virtuaalikoneeseen. Seuraavaksi "Type:"-palkkiin valitsin "Linux" ja "Version:"-palkkiin valitsin "Debian (64-bit). Seuraavaksi painoin 
  "Hardware" palkkia. Siirsin "Base memory" mittarin nuolen 4000 mb kohdalle. Seuraavaksi painoin "Hard disk" painiketta ja merkitsin "Create a Virtual Hard Disk Now" painikkeen "kyllä". 
  Tämän jälkeen painoin painiketta "Finish" ja VirtualBox loi onnistuneesti uuden virtuaalikoneen. Sitten painoin hiiren oikeaa näppäintä luomani virtuaalikoneen päällä ja valitsin "settings".
  Asetuksista painoin vasemmassa reunassa sijaitsevaa "Storage" kuvaketta ja avautuneelta sivulta cd-levyn näköistä kuvaketta "empty". Tämä avasi sivun oikeaan reunaan palkin, josta painoin cd-levy näköistä kuvaketta,         palkin oikeassa reunassa. Kuvake avasi pienen valintalaatikon, josta valitsin "Choose/Create a Virtual Optical Disk...". Seuraavaksi etsin lataamani "imagen", joka minun tapauksessani oli debian-live-12.6.0-amd64-xfce.iso.
  Tämän jälkeen painoin "OK" painiketta ja virtuaalikone oli valmis. Kello oli tällöin 19.10. Luonnin aikana ei esiintynyt odottamattomia tuloksia.

  Seuraavaksi siirryin Linuxin asennukseen virtuaalikoneeseen. Tupla klikkasin uutta virtuaalikoneen kuvaketta, joka avasi "bootloaderin". Valitsin valikosta ylimmän vaihtoehdon "Live system(amd64)" painamalla "enter"-        painiketta. Virtuaalikone latautui noin minuutin verran ja avautui virtuaalikoneen etusivulle. Sitten tupla klikkasin "Install Debian"-kuvaketta ja käynnistin installerin. Ohjelma kysyy käynnistyksen alussa, että luotanko
  ohjelman "launcheriin", johon painoin painiketta "Mark Executable" ja ohjelman asennus käynnistyi. Käynnistyksen alussa valitsin sivun painikkeesta oletuskielen "American English" ja painoin seuraavaksi painiketta "Next".
  Asennuksen seuraavassa vaiheessa valitsin "Region" kohdan painikkeesta "Europe" valinnan, sekä "Zone" kohdasta "Helsinki" vaihtoehdon ja valitsin nämä vaihtoehdot. Seuraavaksi asennuksessa tuli määrittää näppäimistö,        johon valitsin "Generic 105-key PC" vaihtoehdon ja etsin vasemmanpuoleisesta listasta "Finnish" vaihtoehdon ja oikeasta listasta "Default" vaihtoehdon ja valitsin ne. Seuraavaksi vaiheessa valitsin "Erase disk"             painikkeseen "kyllä" ja varmistin, että "Encrypt" painikkeseen ei ollut valittu "kyllä". Sitten vielä valitsin "Boot loader location" palkkiin vaihtoehdon "Master Boot Record of VBOX HARDDISK(/dev/sda)" valinnan ja jatkoin
  painamalla "Next"-painiketta. Seuraavalla sivulla loin täytin nimeni, määritellin tietokoneen nimen, loin käyttäjätunnuksen, salasanan ja varmistin, ettei automaattinen kirjautuminen ollut painettu "kyllä" valinnalla.
  Jatkoin painamalla "Next"-painiketta, jonka jälkeen siirryin "Summary" sivulle, jossa tarkistin valitsemani tiedot ja jatkoin asennukseen "Next"-painikkeella. Asennus kesti noin 5 minuuttia, tässä vaiheessa kello oli        19.21. Viimesitelynä valitsin "Restart now"-painikkeeseen "kyllä" ja sitten painiketta "Done". Nyt asennus on valmis ja lopullinen kellon aika asennuksen jälkeen oli 19.22.
    
## Viittaukset
https://terokarvinen.com/2023/create-a-web-page-using-github/

https://www.gnu.org/philosophy/free-sw.html
