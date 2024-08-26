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
  Aloitin tehtävän tekemisen klo 19.05 ja ensimmäisenä avasin Virtualbox Manager ohjelman. Ensimmäisenä painoin VirtualBox Managerin etusivulla "new" kuvaketta sivun oikeassa yläreunassa. 
  ![kuva](https://github.com/user-attachments/assets/b63ace6f-bf98-45a6-bd28-6e317f02f1c3)

  Helpottakseni virtuaalikoneen tekemistä painoin "expert mode" painiketta, jotta saan kaikki vaadittavat kentät yhdelle sivulle. 
  ![kuva](https://github.com/user-attachments/assets/01bc054f-1bff-40c4-892e-3e223636eaca)

  Painiketta painettuani, avautui uusi ikkuna. "Name and Operating System"-palkin alla olevaan täytin "name:"-palkkiin haluamani nimen virtuaalikoneelle, "Folder:"-palkkiin kansion, johon halusin tallentaa koneen, valitsen    "ISO image" painikkeesta "other" vaihtoehdon ja etsin lataamani Linux "image", jonka haluan asentaa virtuaalikoneeseen. Seuraavaksi "Type:"-palkkiin valitsin "Linux" ja "Version:"-palkkiin valitsin "Debian (64-bit). 
  ![kuva](https://github.com/user-attachments/assets/ce373eba-5dc0-4df5-b3fa-9773d0dd7fe6)
  ![kuva](https://github.com/user-attachments/assets/19ef6140-e040-41bb-beec-60b2442310f1)
  ![kuva](https://github.com/user-attachments/assets/41ae3e13-f4ff-43b8-874e-188227e77a9e)

  
  Seuraavaksi painoin "Hardware" palkkia. Siirsin "Base memory" mittarin nuolen 4000 mb kohdalle. 
  ![kuva](https://github.com/user-attachments/assets/3e0e2a31-4aaa-453e-a907-6c4f630f5b2e)

  Seuraavaksi painoin "Hard disk" painiketta ja merkitsin "Create a Virtual Hard Disk Now" painikkeen "kyllä". 
  Tämän jälkeen painoin painiketta "Finish" ja VirtualBox loi onnistuneesti uuden virtuaalikoneen. 
  ![kuva](https://github.com/user-attachments/assets/7396deb2-80d8-4c57-8168-4634882fff72)
  ![kuva](https://github.com/user-attachments/assets/7cd7b65c-30c6-4e26-8c0d-edabc8b67541)

  
  Sitten painoin hiiren oikeaa näppäintä luomani virtuaalikoneen päällä ja valitsin "settings".
  ![kuva](https://github.com/user-attachments/assets/728d2b75-84ca-4904-98d1-ef1c73f083a7)

  
  Asetuksista painoin vasemmassa reunassa sijaitsevaa "Storage" kuvaketta ja avautuneelta sivulta cd-levyn näköistä kuvaketta "empty". 
  ![kuva](https://github.com/user-attachments/assets/a6599175-b159-4f5f-a62a-777d9368cdaa)

  
  Tämä avasi sivun oikeaan reunaan palkin, josta painoin cd-levy näköistä kuvaketta, palkin oikeassa reunassa. 
  ![kuva](https://github.com/user-attachments/assets/e1908094-3c80-4b6b-8ded-a819ac80ec8a)

  
  Kuvake avasi pienen valintalaatikon, josta valitsin "Choose/Create a Virtual Optical Disk...". 
  ![kuva](https://github.com/user-attachments/assets/ca6e61aa-1a87-4bc2-b017-17c830846fac)

  
  Seuraavaksi etsin lataamani "imagen", joka minun tapauksessani oli debian-live-12.6.0-amd64-xfce.iso.
   ![kuva](https://github.com/user-attachments/assets/788dd970-a132-4326-9d79-ca41993adbb0)
   
  Tämän jälkeen painoin "OK" painiketta ja virtuaalikone oli valmis. Kello oli tällöin 19.10. Luonnin aikana ei esiintynyt odottamattomia tuloksia.
   ![kuva](https://github.com/user-attachments/assets/d44bb96c-3e67-4651-9eae-2ce14ca7e058)


  Seuraavaksi siirryin Linuxin asennukseen virtuaalikoneeseen. Tupla klikkasin uutta virtuaalikoneen kuvaketta, joka avasi "bootloaderin". 
  ![kuva](https://github.com/user-attachments/assets/9ac557cb-2c4d-4680-993e-250417ef8336)

   Valitsin valikosta ylimmän vaihtoehdon "Live system(amd64)" painamalla "enter"-painiketta.
  ![kuva](https://github.com/user-attachments/assets/24a01af9-6841-4a5d-b848-e5cbd020d221)

  Virtuaalikone latautui noin minuutin verran ja avautui virtuaalikoneen etusivulle. Sitten tupla klikkasin "Install Debian"-kuvaketta ja käynnistin installerin. 
  ![kuva](https://github.com/user-attachments/assets/cd6147da-f524-4c1a-8cd9-a16d1fcce275)
  ![kuva](https://github.com/user-attachments/assets/d7f16143-75c8-48f7-9f43-6d8bbc2bfcbc)

  
  Ohjelma kysyy käynnistyksen alussa, että luotanko ohjelman "launcheriin", johon painoin painiketta "Mark Executable" ja ohjelman asennus käynnistyi. 
  ![kuva](https://github.com/user-attachments/assets/7d0b257f-4c9c-4c1a-a94e-8c0c304ab124)

  Käynnistyksen alussa valitsin sivun painikkeesta oletuskielen "American English" ja painoin seuraavaksi painiketta "Next".
  ![kuva](https://github.com/user-attachments/assets/8b368e6f-a628-46f5-a439-4f1b03d43dca)

  
  Asennuksen seuraavassa vaiheessa valitsin "Region" kohdan painikkeesta "Europe" valinnan, sekä "Zone" kohdasta "Helsinki" vaihtoehdon ja valitsin nämä vaihtoehdot ja painoin "Next"-painiketta. 
  ![kuva](https://github.com/user-attachments/assets/4f564b26-0eae-4409-95e6-3080e7d622e9)

  Seuraavaksi asennuksessa tuli määrittää näppäimistö, johon valitsin "Generic 105-key PC" vaihtoehdon ja etsin vasemmanpuoleisesta listasta "Finnish" vaihtoehdon ja oikeasta listasta "Default" vaihtoehdon ja valitsin ne. 
  ![kuva](https://github.com/user-attachments/assets/d7bee82b-2125-4a3a-97ea-76b93b99c259)

  Seuraavaksi valitsin "Erase disk" painikkeseen "kyllä" ja varmistin, että "Encrypt" painikkeseen ei ollut valittu "kyllä". Sitten vielä valitsin "Boot loader location" palkkiin vaihtoehdon "Master Boot Record of VBOX       HARDDISK(/dev/sda)" valinnan ja jatkoin painamalla "Next"-painiketta. 
  ![kuva](https://github.com/user-attachments/assets/e00a1d65-fff6-43aa-9405-e21a6a8299dc)

  Seuraavalla sivulla loin täytin nimeni, määritellin tietokoneen nimen, loin käyttäjätunnuksen, salasanan ja varmistin, ettei automaattinen kirjautuminen ollut painettu "kyllä" valinnalla.
  ![kuva](https://github.com/user-attachments/assets/cf712fc4-f9ee-4394-86bf-dad46a686875)

  Jatkoin painamalla "Next"-painiketta, jonka jälkeen siirryin "Summary" sivulle, jossa tarkistin valitsemani tiedot ja jatkoin asennukseen "Next"-painikkeella. Ohjelmassa esiintyi tässä vaiheessa ongelma, jossa "Next" ja    "Back"-painikkeet eivät näy kuin pieninä viivoina sivun alalaidassa. Tämä ongelma jatkui asennuksen loppuun saakka, vaikkei estänyt asennuksen loppuun ajamista täysin. 
  ![kuva](https://github.com/user-attachments/assets/5be57d89-0026-4bbb-9e28-f3a5e81b1e80)

  Asennus kesti noin 5 minuuttia, tässä vaiheessa kello oli 19.21. Viimesitelynä valitsin "Restart now"-painikkeeseen "kyllä" ja sitten painiketta "Done". Nyt asennus on valmis ja lopullinen kellon aika asennuksen jälkeen    oli 19.22.
  ![kuva](https://github.com/user-attachments/assets/64f8d2f5-eb53-4291-bd2f-94870d45affb)
  ![kuva](https://github.com/user-attachments/assets/ffcde0b4-4a97-43ae-a5be-65a2c75d900e)


  Seuraavaksi siirryin tekemään mahdolliset päivitykset Linuxiin. Ensin minun täytyi kirjautua sisään luomillani käyttäjätunnuksilla. 
  ![kuva](https://github.com/user-attachments/assets/5dd33af2-d703-4f33-8222-066c401dc8f2)

  Sitten siirryin "Terminal Emulator"-painikkeesta komento-ohjelmaan. 
  ![kuva](https://github.com/user-attachments/assets/8bc0bfd0-f998-4eef-83be-acd5d56758f5)

  Komento- ohjelmasta etsin mahdolliset Linuxin päivitykset komennolla:
  
  $ sudo apt-get update

  ![kuva](https://github.com/user-attachments/assets/b753ca4b-3540-43a5-96b0-76adfb76cf01)

  Seuraavaksi syötin salasanani ja painoin "Enter" -näppäintä.
  ![kuva](https://github.com/user-attachments/assets/a4609fbc-5eb9-4237-b647-4a2ce7fc480d)

  Seuraavaksi suoritin päivitykset komennolla:

  $ sudo apt-get -y dist-upgrade

  ![kuva](https://github.com/user-attachments/assets/8572cb82-31f7-4bec-9db9-47893aa300e6)

  Päivitys onnistui ongelmitta.
  ![kuva](https://github.com/user-attachments/assets/f7b2ba31-b00b-411f-addf-63853d5242b1)

  Sitten vielä asensin vielä palomuurin virtuaalikoneeseen. Asennuksen suoritin komennoilla:

  $ sudo apt-get -y install ufw
  $ sudo ufw enable

  ![kuva](https://github.com/user-attachments/assets/bd4fd1e3-b1a8-4ae9-81c8-943a969de66e)

  ![kuva](https://github.com/user-attachments/assets/7cb93482-3222-43de-a371-6fc52a9f66f7)


  Viimeiseksi suoritin uudelleenkäynnistyksen "Applications"-painikkeen kohdasta "Log out" ja "Restart".

  ![kuva](https://github.com/user-attachments/assets/feaefc7a-ae15-483e-bc9c-1c448c60ee51)
  ![kuva](https://github.com/user-attachments/assets/bed9ebab-0fcb-445b-8a12-b49805d9effa)

  Linuxin asennus, päivitys ja palomuurin asennus olivat täten valmiit.
    
## Viittaukset
https://terokarvinen.com/2023/create-a-web-page-using-github/

https://www.gnu.org/philosophy/free-sw.html
