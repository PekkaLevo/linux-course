
# h2 Komentaja Pingviini




## x) Lue ja tiivistä: Command line basics revisited

Linux:issa ja BSD:ssä käytettävä komentorivi on säilynyt ajankohtaisena jo pitkään, vaikka se onkin vanhempi kuin itse internet. Se on kätevä, nopea, ilmaiseva ja helposti automatisoitava. 

- Komentorivillä voidaan suorittaa monia yksinkertaisia komentoja, kuten `pwd` joka näyttää nykyisen työhakemiston, `ls` listaa hakemiston sisällön, `cd` vaihtaa hakemistoa ja `less` näyttää tiedostojen sisällön.

- Tiedostoja voidaan muokata esimerkiksi pico- tai nano-editoreilla ja siirtää `mv`-komennolla, kopioida `cp`-komennolla ja poistaa tiedostoja `rm`-komennolla.

- SSH:n avulla voidaan hallita etäkoneita turvallisesti ja esimerkiksi kopioida kansioita etäkoneesta.

- Tab:n avulla voidaan kätevästi tarkistaa käytettävissä olevat komennot ja täyttää yksiselitteiset komennot. `history´-komennolla voidaan taas tarkistaa tehdyt komennot.

- `apt`:n avulla voidaan hallita ja asentaa ohjelmistoja helposti sekä poistaa niitä. `sudo`-komennolla suoritetaan, jotta saadaan komennoille korkeimmat oikeudet.

- oma idea: `alias` -komennolla voidaan luoda oikoteitä suosituille komennoille tai tiedoston nimille, mikä nopeuttaa komentorivin käyttöä.

### Lähteet

- Command line basics revisited https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited

### Käyttämäni virtuaalikoneen tiedot

Virtualisointi: VirtualBox 7.0.20

Käyttöjärjestelmä: Debian 12.6.0 AMD64

Muistikapasiteeti: 4096 MB

Prosessori: 4 CPU

### Käyttämäni fyysisen tietokoneen tiedot 

Konetyyppi: Kannettavatietokone

Käyttöjärjestelmä:  Windows 11 Home, 64bit, x64-suoritin

Prosessori: 11th Gen Interl(R) COre(TM) i3

Muisti: 8GB

## a) Asenna micro-editori

Ensitöikseni avasin virtuaalikoneeni ja kirjauduin sisään. Seuraavaksi avasin komentorivin "applications"-painikkeen alta. 

![kuva](https://github.com/user-attachments/assets/8f3f387f-6d8f-4e95-852a-20038252cdda)

Jatkoin tehtävää suorittamalla komennon: `sudo apt-get update` ja annoin käyttäjäni salasanan.

![kuva](https://github.com/user-attachments/assets/62a38b3b-176f-4f97-ab3f-165888943004)

Seuraavaksi tarkistin löytyykö micro-editori listalta komennolla `apt-cache search micro.

![kuva](https://github.com/user-attachments/assets/1de2dd50-6a2b-4dc9-902a-cfb3b8eac5c0)

Micro löytyikin pienen etsinnän jälkeen listalta.

![kuva](https://github.com/user-attachments/assets/5cfbdc19-ef58-4410-8eaa-07dd0bcfce0b)

Seuraavaksi asensin micron paketinhallinan kautta komennolla `sudo apt-get -y install micro`

![kuva](https://github.com/user-attachments/assets/15b320c6-5c5a-48aa-93b6-cd2f921a196b)

Tässä tapauksessa olin jo ehtinyt asentaa ohjelman etukäteen, joten komentorivi ilmoitti asiasta ja kertoi myös, että micro oli myös päivitetty uusimpaan versioonsa.

![kuva](https://github.com/user-attachments/assets/a648745e-4d15-4413-9fcc-69d764bf0cfb)

Tarkistin vielä micron olemassa olon suorittamalla komennon `dpkg --listfiles micro`.

![kuva](https://github.com/user-attachments/assets/61643a7a-b8f0-45ee-8e38-7c9ee23a9e1f)

Komento antoi vastauksena micron sijainnin ja täten olin varma, että micro löytyi koneeltani.

![kuva](https://github.com/user-attachments/assets/f55b99a2-b1d9-4fcd-8291-6ec56c7e1ce9)

### Lähteet

- https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited


## b) Apt

### Asenna kolme itsellesi uutta komentoriviohjelmaa

Jokainen komentoriviohjelma oli minulle uusi, joten minulla oli suuri määrä vaihtoehtoja mistä valita. Ensin minun kuitenkin tuli valita, mitkä ohjelmat halusin asentaa. Tämä osoittautuikin hieman haastavammaksi, sillä en ollut ollenkaan varma minkälaisia ohjelmia halusin asentaa, joten aloin etsiä suositeltavia vaihtoehtoja internetistä.

Ensimmäisenä vastaani tuli googler-ohjelma. Etsiessäni komentoriviohjelma ehdotuksia törmäsin tecmint-sivuston julkaisuun googlerista https://www.tecmint.com/google-commandline-search-terminal/. Tecmintin mukaan, ohjelman avulla voidaan suorittaa google-hakuja suoraan komentorivin kautta. Tämä vaikutti erittäin mielenkiintoiselta ja hauskalta ohjelmalta kokeilla, joten päätin valita googlerin ensimmäiseksi ohjelmakseni.

Päätin etsiä vielä nämä kaksi muuta komentoriviohjelmaa, jotka halusin asentaa. 

Toisena ohjelmana päätin asentaa wikit-ohjelman, jonka sain ehdotuksena tecmintin sivustolta, josta löysin googler-ohjelman https://www.tecmint.com/wikipedia-commandline-tool/. Wikitin tulisi avulla tulisi kyetä helposti nähdä tiivistelmiä wikipedian artikkeleista. Tämä vaikutti myös erittäin hauskalta ja hyödylliseltä ohjelmalta asentaa.

Kolmantena ohjelmana päätin valita musikcube-ohjelman, jonka löysin selatessani parhaita komentoriviohjelmia linuxin järjestelmälle. Päädyin musikcuben omille sivuille, josta näkyi demo-versio ohjelmasta https://musikcube.com/. Musikcube on komentoriviohjelma, jonka avulla voi soittaa musiikkia suoraan kometorivin kautta, sisältäen musiikkin toiston, kirjaston ja suoratoistoäänipalvelimen. Tämä kuulosti minulle erittäin lupaavalta ohjelmalta. 

Seuraavaksi päätin kokeilla ladata nämä kaikki kolme ohjelmaa samaan aikaan, kuten tehtävän annossa kysyttiin extrakysymyksenä.

Kokeilin ensimmäisenä, jos esimerkiksi laittamalla kaikki kolme haluamaani ohjelmaa peräkkäin `sudo apt-get -y `-komentoon, saisi tämän asennuksen suoritettua. Tämä ei kuitenkaan onnistunut, joten kokeilin asentaa kunkin ohjelman yksitellen.

![kuva](https://github.com/user-attachments/assets/b71f4577-e4ed-4ee6-90fe-7fb832ed3d20)

Aloitin googlerista, sillä komentorivi ei ilmoittanut ongelmista sen kanssa, kun yritin asentaa kaikkia kolmea ohjelmaa samanaikaisesti. Suoritin komennon `sudo apt-get -y install googler`.

![kuva](https://github.com/user-attachments/assets/0c101b07-9298-48d2-afe8-a76897e582b6)

Tämä onnistuikin vaivattomasti.

![kuva](https://github.com/user-attachments/assets/33817472-f618-467e-a854-3527f4794dcb)

Suoritinkin seuraavaksi ohjelman testikäytön tekemällä google-haun komentorivillä.

![kuva](https://github.com/user-attachments/assets/8d2c85c8-ba44-487c-8080-8f1078919de8)

Lopputuloksena sain vastaavan google-hakutuloksen kuin tavallisesti hakukoneella saisin.

![kuva](https://github.com/user-attachments/assets/0a7e7489-4b7e-41d0-b0e6-fa1bb970b4f8)

Seuraavaksi kokeilin onnistuuko wikitin tai musikcuben asennus yksitellen, mutta tämä ei onnistunut. 

![kuva](https://github.com/user-attachments/assets/1be7e7ff-3a9e-4295-8fc7-78f517f04b29)

Päätin vaihtaa näitä kahta muuta valitsemaani ohjelmaa. Tällä kertaa päätin asentaa tmux-ohjelman. Suoritin seuraavaksi asennuskomennon `sudo apt-get -y install `.

![kuva](https://github.com/user-attachments/assets/64cc1499-b218-45a4-ab01-62b8b7e1e9ea)

Ohjelman asennus onnistui ongelmitta, joten päätin kokeilla ohjelman käyttöä. Internetistä hakemalla löysin youtubesta tmux-tutorial videon, jonka avulla pystyin kokeilemaan ohjelman käyttöä https://www.youtube.com/watch?v=Yl7NFenTgIo . Aloitin ohjelman komennolla: ´tmux´ ja ohjelma avautui ongelmitta.

![kuva](https://github.com/user-attachments/assets/bbedb79a-b71d-44b1-94e5-8a414889f5e6)

![kuva](https://github.com/user-attachments/assets/7fe3bdde-9cd3-4cf6-abbd-576a55fe214d)

Kokeillakseni ohjelman toimintaa, kokeilin luoda toisen komentorivin painamalla `ctrl`+´b´ ja `%`-näppäintä, joka vaatii myös shiftin painamista. Lopputuloksena on jakautunut komentorivi.

![kuva](https://github.com/user-attachments/assets/d01a5727-1f9a-4839-992f-db7b4be9d390)

Ohjelmalla voi myös luoda lisää ikkunoita tai vaikkapa uusia sessioita. Ohjelma toimii kuten toivottu, eikä asennuksessa tai käytössä esiintynyt lainkaan ongelmia.

Viimeisenä ohjelmana päätin asentaa yksinkertaisen ohjelman lolcat. Aloitin tehtävän ohjelman asennuksella.

![kuva](https://github.com/user-attachments/assets/2b22b0a2-15fc-497a-a25b-2104652f2894)

Ohjelma latautui onnistuneesti. Päätin kokeilla ohjelmaa muuttamalla komentorivin tesktin väriä sateenkaren väreiksi.

![kuva](https://github.com/user-attachments/assets/139bae08-e679-49ff-9709-221ccd11b6d0)

Ohjelma toimii kuten haluttua, vielä minun täytyi vaihtaa värit takaisin alkuperäisiin väreihin, joka tapahtuu painamalla `ctrl + D`. 

## c) FHS

### Esittele kansiot ja näytä kuvaavat esimerkit. 

Juurikansio on linuxin ylin kansio, jonka alla kaikki muut kansiot sijaitsevat. `cd ..`-komennolla voidaan perääntyä niin kauan, että päästään juurikansioon. Sen sisältöä voidaan katsella komennolla `ls`.


![kuva](https://github.com/user-attachments/assets/6e30ee7f-2d26-4181-b69c-97a9be364e3e)

Home-kansio löytyy seuraavana juurikansion alta. Sen sisältä löytyy yleensä käyttän kansio käyttäjätunnuksen nimellä. Home-kansioon pääsemme komennolla `cd home/` ja sen sisältöä voimme jälleen tutkia komennolla `ls`.


![kuva](https://github.com/user-attachments/assets/e2c20396-8764-4de0-ac2b-24498340a323)

Käyttäjäkansio löytyy home-kansion alta. Pääsemme käyttäjäkansioon samalla tavalla kuin home kansioon, minun tapauksessani `cd levopek/`. Käyttäjäkansio esimerkiksi latauskansio ja mahdollisesti sinne tallennettuja omia tiedostoja, kuten itselläni testi.txt ja testi1.txt.

![kuva](https://github.com/user-attachments/assets/00ac7814-b19e-4c69-a6f2-9ae63562be2c)

Etc-kansio sijaitsee juurikansiossa, johon pääsin seuraavilla komennoilla.


![kuva](https://github.com/user-attachments/assets/63c84e5d-98c7-4076-9537-63f44433c62b)

Etc-kansio sisältää eitca.org:in mukaan tärkeitä järjestelmän asetustiedostoja ja hakemistoja. Kokeilin avata logcheck-kansiota etc-kansiossa.

![kuva](https://github.com/user-attachments/assets/c0297a68-b7cd-4ce3-bebf-300bad9eac2e)

Logcheck-kansiosta löytyi kaksi muuta kansiota, joista kokeilin avata violations.d-kansiota.

![kuva](https://github.com/user-attachments/assets/b528b26e-0200-4bcb-9dcf-563adb049874)

Violations.d-kansiosta löytyi mdadm-työkalu.

![kuva](https://github.com/user-attachments/assets/eab195ba-cc97-4c79-88c2-5d933f10dc11)

Media-kansion avulla voidaan päästä käsiksi cd-asemaan ja mahdollisiin USB-tikkuihin. Tutkin media-kansion sisältöä, josta pääsin käyttäjäkansioon ja ollettaen kansiosta ei löytynyt sisältöä, sillä virtuaalikoneessani ei ole USB-tikkua käytössä.

![kuva](https://github.com/user-attachments/assets/a06c04e8-bd19-4e56-94ac-bb9ff3a48ed0)

Viimeiseksi katsomme var/log-kansiota. Var/log-kansio sijaitsee juurikansion alla, tässätapauksesa nimettynä ´var´. Kyseinen kansio on itselle tuttu kansio, oman tietokoneen käytön kautta kun on syntynyt ongelmatilanteita ja tutkittu lokikansiota. Kyseessä on lokikansio, jonne tallennetaan lokitiedostoja, joita voi olla esimerkiksi tapahtumia ja aikaleimoja, yleisesti tietoja siitä, mitä palvelimella tai laitteessa on tehty ja tiedot kirjautumisista.

![kuva](https://github.com/user-attachments/assets/2a88c578-268e-4cd9-9867-cf881438f3d9)

### Lähteet

Karvinen, Tero 2020: Command line basics revisited. https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited

Mikä on "/etc"-hakemiston tarkoitus Linux-tiedostojärjestelmässä? https://fi.eitca.org/cybersecurity/eitc-is-lsa-linux-system-administration/linux-filesystem/filesystem-layout-overview/examination-review-filesystem-layout-overview/what-is-the-purpose-of-the-etc-directory-in-the-linux-file-system/

## d) The Friendly M

### Kolme esimerkkiä grep-komennon käytöstä

Tehtävän auttamisessa katsoin youtubesta videon, josta sain apua tehtävän suorittamiseen. Komennolla voidaan etsiä valitun sanan avulla haluttu rivi tiedostosta.

Tein tehtävää varten sisältöä aikasemmin tekemääni testi.txt tiedostoon. Kokeilin löytyykö tekemäni teksti komennolla `grep Tämän testi.txt`.

!![kuva](https://github.com/user-attachments/assets/d1f31561-2abb-48de-87ee-039a19fb1ce4)

Seuraavaksi lisäsin testi.txt tiedostoon saman lauseen kuin se aikaisemmin sisälsi mutta isolla kirjaimilla. Annoin uuden komennon tällä kertaa `grep -wi Tämän testi.txt` ja seurasin mitä tapahtuu.

![kuva](https://github.com/user-attachments/assets/a19308cc-e3d2-4679-9372-f7b757a3425e)

Tällä kertaa ohjelma tulosti tekstin myös isoilla kirjaimilla. Entäs, jos lisään komentoon -wi sijasta -win eli `grep -win Tämän testi.txt`, mitä tällöin tapahtuisi.

![kuva](https://github.com/user-attachments/assets/10bdd871-81d1-4f9b-a403-3e6804eaabfd)

Tällä kertaa ohjelma tulosti myös rivinumerot, joille haetut tekstirivit on kirjoitettu. Greg näyttäisi olevan hyvinki helppokäyttöinen ja kätevä työkalu tiedon etsinnässä.

### Lähteet

Linux/Mac Terminal Tutorial: The Grep Command - Search Files and Directories for Patterns of Text https://www.youtube.com/watch?v=VGgTmxXp7xQ

## e) Pipe

### Esimerkki putkista

Selvitin mitä putkittaminen tekisi, jos kokeilen sekä micron, että catin avulla lolcatin väritystä testi.txt tiedostooni.

![kuva](https://github.com/user-attachments/assets/1e8d69f9-5be3-4687-b335-eec0af70548f)

## f) Rauta

### Listaa testaamasi koneen rauta, selitä ja analysoi listaus.

Ensimmäiseksi asensin ishw-ohjelman, sillä koneellani ei sitä ollut.

![kuva](https://github.com/user-attachments/assets/1ee15d5a-c9f1-4343-9866-e0c57faa7e24)

Seuraavaksi testasin tehtävänannossa annettua komentoa: `sudo lshw -short -sanitize`.

![kuva](https://github.com/user-attachments/assets/fbd8ca30-52d3-47a2-885a-63a5450b1464)


![kuva](https://github.com/user-attachments/assets/6078a4b9-578c-4354-95af-16bbbd77f5b8)

En kaikkia listauksen tietoja osannut lukea, mutta selkeästi kyseessä on tiedot järjestelmästä.
Listauksesta selviää ainakin, että koneena toimii virtualbox ja virtualbox toimii kannettavan tietokoneen kautta, input9 toimii virutaalisesti hiirellä. Listaus kertoo myös käytettävissä olevan eli oman koneen intel core i3 prosessorin, mihin tallennukset tallennetaan eli tässä tapauksessa SATA C asemaan. Käytettävää muistia on 4GiB, jäljellä olevaa muistia on 21GB. Listauksen alhaalta näkyy myös eri inputien vastineet eli mitä inputia vastaavat painikkeet tekevät, kuten input2 on virtapainike ja input4 näytösäästöpainike.
