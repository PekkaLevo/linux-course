# h4 Maailma kuulee

## x) Lue ja tiivistä

### Susanna Lehto 2022: Teoriasta käytäntöön pilvipalvelimen avulla

#### a) Pilvipalvelimen vuokraus ja asennus

- Oman pilvipalvelin voidaan vuokrata esimerkiksi DigitalOceanilta ja domainnimen Namecheapilta, joihin voidaan hyödyntää GitHub Education kredittejä.

- Palvelimen vuokrauksessa tulee valita käyttöjärjestelmä, paketti, joka määrittää prosessorin ja kovalevyn koon sekä siirtodatan määrän.

- Datakeskus tulee valita mahdollisimman läheltä käyttäjiä, tiedonsiirron nopeuttamiseksi. GDPR:n vuoksi, EU:n sisäinen datakeskus on suositeltavaa.

- Suojaksessa käytettävän salasanan tulee olla vahva, murtautumisten ehkäisemiseksi.

- Virtuaalikoneen IP-osoite otetaan talteen.

- Domain-nimi voidaan vuokrata esimerkiksi NameCheap-sivustolta.

- Domain-nimi tulee osoittaa DigitalOceanin hankitulle virtuaalipalvelimelle, joka tehdään NameCheapin hallintapaneelista

#### d) Palvelin suojaan palomuurilla

- Luodaan yhteys virtuaalipalvelimeen `ssh root@IP-osoite`-komennolla ja syöttämällä salasana.

- Tehdään tarvittavat åäivitykset `sudo apt-get update`-komennolla.

- Asennetaan tulimuuri `sudo apt-get install ufw`-komennolla.

- Tehdään tulimuuriin reikä `sudo ufw allow 22/tpc`-komennolla.

- Aktivoidaan tulimuuri `sudo ufw enable`-komennolla.

#### e) Kotisivut palvelimelle

- Tehdään käyttäjä virtuaalipalvelimen terminaalissa `sudo adduser name`-komennolla ja luodaan salasana.

- Tehdään käyttäjästä pääkäyttäjä `sudo adduser name sudo`-komennolla.

- Testataan uusien käyttäjätunnusten toimivuus toisessa terminaalissa avaamalla SSH-yhteys virtuaalipalvelimeen ja päivittämällä uudet tiedot `ssh name@IP-osoite`-komennolla ja `sudo apt-get update`-komennolla.

- Lukitaan juuri `sudo usermod -lock root`-komennolla.

- Muodostetaan toiseen terminaaliin SSH-yhteys pääkäyttäjän tunnuksilla ja tehdään tarvittavat päivitykset ja tietoturvapäivitykset `sudo apt-get update`, `sudo apt-get upgrade` ja `sudo apt-get dist-upgrade`-komennoilla.

- Asennetaan virtuaalikoneelle Apache-weppipalvelin `sudo apt-get isntall apache2`-komennolla ja testataan sen tilaa `sudo systemctl status apache2`-komennolla.

- Tehdään toinen reikä tulimuurin porttia varten `sudo ufw allow 80/tcp`-komennolla.

- Korvataan Apachen testisivu `echo Hello world! |sudo tee /var/www/html/index.html`-komennolla.

- Otetaan userdir-moduulin käyttöönotto `sudo a2enmod userdir`-komennolla ja sen käynnistys `sudo service apache2 restart`-komennolla.

- Luodaan käyttäjälle julkinen kansio public_html käyttäjän kotihakemistoon ja varmistetaan kansion näkyminen selaimessa.

- Tekstitiedoston saamiseksi käyttäjän julkiseen hakemistoon, avataan SSH-yhteys `sudo systemctl start ssh`-komennolla ja asennetaan Micro `sudo apt-get install micro`-komennolla.

- Tehdään tekstitiedosto käyttäjän julkiseen hakemistoon `cd public_html` ja `micro index.html`-komennoilla.

- Tehdään nettisivu-runko tiedostoon ja testataan uuden käyttäjän kotisivujen näkymää.

#### f) Palvelimen ohjelmien päivitys

- Avataan terminaalissa SSH-yhteys virtuaalipalvelimeen pääkäyttäjän tunnuksilla.

- Suoritetaan kaikkien palvelimen ohjelmien päivitys `sudo apt-get update`, `sudo apt-get upgrade` ja `sudo apt-get dist-upgrade`-komennoilla.


### Karvinen 2012: First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS

- Virtuaalipalvelimien ja domain-nimien markkinalla on kova kilpailu.

- Opiskelijana voi saada GitHub Education-opiskelijapaketin ilmaiseksi.

- Anna aina hyvä uusi salasana.

- Virtuaalipalvelimen luonti:

  1. Ensimmäisellä kerralla rootiin, mutta jatkossa pääkäyttäjänä
  2. Asennetaan tulimuuri ja tehdään siihen reikä SSH:lle
  3. Tehdään pääkäyttäjätunnukset ja kokeillaan niitä
  4. Suljetaan root-käyttäjätunnus
  5. Päivitetään ohjelmisto
  6. Aloitetaan palvelimen käyttö ja muistetaan tehdään reikä tulimuuriin

### Lähteet

Susanna Lehto 2022: Teoriasta käytäntöön pilvipalvelimen avulla (h4) (opiskelijan esimerkkiraportti) https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/

Karvinen 2012: First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/?fromSearch=first%20steps

## Järjestelmätiedot

### Virtuaalikone

- Virtualisointi: VirtualBox 7.0.20

- Käyttöjärjestelmä: Debian 12.6.0 AMD64

- Muistikapasiteeti: 4096 MB

- Prosessori: 4 CPU

### Fyysisen kone

- Konetyyppi: Kannettavatietokone

- Käyttöjärjestelmä: Windows 11 Home, 64bit, x64-suoritin

- Prosessori: 11th Gen Interl(R) COre(TM) i3

- Muisti: 8GB

  ## a) Vuokraa oma virtuaalipalvelin

Aloitusaika: Maanantai 17.39 16.9.2024

Aloitin tehtävän käynnistämällä virtuaalikoneeni VirtualBoxista. Avasin terminaalin `applications` -> `terminal emulator` ja tein päivitykset terminaalissa `sudo apt-get update` ja `sudo apt-get -y dist-upgrade`-komennoilla.

Päätin kokeilla tehtävää varten vuokrata Linoden virtuaalipalvelimen, joka oli yksi opettejan tunnilla suosittelemista palvelimen vuokraajista. Linoden sivuilla 100 dollarin credittiä rekisteröitymisestä. Kuulosti hyvältä tarjoukselta, joten päätin rekisteröityä sivulle. Sivu antoi rekisteröitymisvaihtoehdoiksi google-tilin, joten päätin käyttää tiliäni rekisteröitymiseen.


![kuva](https://github.com/user-attachments/assets/e195a4cb-961e-4ae9-8acc-f06ab36af79f)

Seuraavaksi minun tuli määrittää käyttäjätunnus sivulle.

![kuva](https://github.com/user-attachments/assets/377cca1d-dcca-4bf0-867a-3fba8cd8b796)

Tämän jälkeen minun tuli vahvistaa puhelinnumeroni, johon sivu lähetti vahvistuskoodin.

![kuva](https://github.com/user-attachments/assets/90c25737-cb79-4860-bf71-cb31266d2eaa)

Vahvistuksen tehtyäni, minun tuli antaa pankkikorttitiedot, jotka annoin.


![kuva](https://github.com/user-attachments/assets/becfeffa-9957-45c5-a57c-e4c83f799f06)

Täytettyäni tiedot, pääsin suoraan käyttäjäni etusivulle. Kävin tarkistamassa löytyikö tuo 100 dollaria käyttäjältäni. Lopulta tuo summa löytyi "Promotions"-kohdasta, joten huijausta ei ainakaan ollut kyseessä. Rahalle tosin olli asetettu aikaraja, ennekuin summa erääntyy eikä ole enään käytettävissä.

![kuva](https://github.com/user-attachments/assets/c1e1dd12-af35-453d-846f-2f8f7f063db8)


Palasin takaisin etusivulle, josta klikkasin create linode-painiketta, luodakseni palvelimen.


![kuva](https://github.com/user-attachments/assets/9d668c4d-846d-435f-b3c3-0f31fb00633f)

Ensimmäisenä minun tuli valita palvelimen järjestelmä, johon valitsin Debian 12. 


![kuva](https://github.com/user-attachments/assets/eba4d28c-7064-41d2-b60d-9852c5787a5b)

Tämän jälkeen minun tuli valita palvelimen sijainti. Oppitunnilla mainittiin, että sijainnin tulisi olla mahdollisimman lähellä käyttäjiä, joten valitsin lähimmän sijainnin, joka oli Tukholma.


![kuva](https://github.com/user-attachments/assets/bf76856e-373c-4ed4-8eb1-6154e318453f)

Seuraavaksi minun tuli valita plan eli suunnitelma. Valitsin oppitunnin ohjeiden mukaan halvimman suunnitelman, jonka hinta olisi 5 euroa kuukaudessa, mikä ei kuulosta pahalta.


![kuva](https://github.com/user-attachments/assets/c9be6009-28db-4207-a6d2-37a8d79474d8)

Seuraavaksi minun tuli valita salasana root:lle. Valitsin hyvän ja pitkän salasanan, jota en käytä missään muussa nettisivussa tai ohjelmassa.


![kuva](https://github.com/user-attachments/assets/cd68cb70-97ab-4ff6-a28c-f826400ac2bf)

Koska loin salasanan palvelimelle, jätin SSH-avaimen tyhjäksi. En myöskään ottanut mitään ylimääräistä palvelimeen kuten opettaja tunnilla neuvoi, joten jätin loput osiot tyhjiksi.


![kuva](https://github.com/user-attachments/assets/ca177a2e-f528-4919-87f0-19e3ff4259f9)


![kuva](https://github.com/user-attachments/assets/51f94b7e-179d-4e79-95bb-939e6ec25125)

Täten palvelimen luonti oli valmis ja klikkasin Create linode-painiketta luodakseni palvelimen.


![kuva](https://github.com/user-attachments/assets/59681a39-fa91-40f7-8672-50e53bdf679d)

Ja näin palvelin oli nyt luotu ja toiminnassa.


![kuva](https://github.com/user-attachments/assets/9719c6ac-2028-4401-bd24-8c54375bf334)


## b) Tee alkutoimet omalla virtuaalipalvelimellasi: tulimuuri päälle, root-tunnus kiinni, ohjelmien päivitys

Aloitusaika: Maanantai 18.20 16.9.2024

Aloitin tehtävän suorittamisen katsomalla opettejan ohjeita (https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/?fromSearch=first%20steps) virtuaalipalvelimen tulimuurin asentamisesta. 

Ensimmäisenä kopion virtuaalikoneelleni uuden palvelimeni IP-osoitteen ja kirjauduin root-käyttäjänä.

![kuva](https://github.com/user-attachments/assets/ebc7db49-536c-4a8f-ba0f-a0b6fde7ee13)

Seuraavaksi minun täytyi tehdä reikä tulimuuriin SSH:lle. Tämän tekemiseen käyntin komentoa `sudo ufw allow 22/tcp`, jonka jälkeen minun tuli käynnistää palomuuri komennolla `sudo ufw enable`. Huomasinkin, ettei minulla ollutkaan ufw asennettuna, joten minun täytyi ensiksi asentaa se komennolla `sudo apt-get -y install ufw`.

![kuva](https://github.com/user-attachments/assets/7275e925-5a97-4ba6-b765-4446bb8acc1b)

Ja nyt yritin uudestaan tehdä reikä palomuuriin, joka onnistui.

![kuva](https://github.com/user-attachments/assets/1984fffd-2544-47fa-bdac-d6881fbb3631)

 Käynnistin vielä palomuurin seuraavaksi, joka vaati myös järjestelmän uudelleenkäynnistämisen komennon jälkeen.

![kuva](https://github.com/user-attachments/assets/c63989d3-c6de-4c3f-89c0-fad0cb1c4447)

Seuraavaksi lisäsin käyttäjän komennolla ´sudo adduser peksi´, sekä annoin sudo oikeudet käyttäjälle `sudo adduser peksi sudo`.

![kuva](https://github.com/user-attachments/assets/65caaa09-d510-4c02-a316-3819c49eb615)

![kuva](https://github.com/user-attachments/assets/1519a605-89b0-44b9-a5c5-f05d2ff82b1a)

Annoin käyttäjälle nimen ja salasanan, mutta jätin muut kohdat tyhjiksi.

Seuraavaksi ohjeiden mukaan minun tuli testata uutta käyttäjää palvelimessa.

![kuva](https://github.com/user-attachments/assets/f01a2b4b-0f8f-4951-b0d2-7c195923c0b4)

Käyttäjä toimii halutulla tavalla ja siihen pääsee kirjautumaan.

Seuraavaksi tehtävänäni oli sulkea root-tunnus käyttämällä komentoa `sudo usermod --lock root`.

![kuva](https://github.com/user-attachments/assets/4bd47b78-e3aa-4647-8049-3138396ee1a4)

Kuten näkyy nyt root-tunnuksella ei pääse kirjautumaan sivulle.

Seuraavaksi tuli vielä poistaa root:n kirjautuminen SSH:lle. Suoritin ohjeiden mukaisesti komennon `sudoedit /etc/ssh/sshd_config`.

![kuva](https://github.com/user-attachments/assets/bfee928b-d522-4fc6-8354-a290d20bbbc6)


Komennolla pääsin muokkaamaan root:n kirjautumisoikeudeksi haluttu "no", ja tallensin muutokset.

![kuva](https://github.com/user-attachments/assets/ec874058-c4d9-4a8f-a63d-c6485deae1f1)

![kuva](https://github.com/user-attachments/assets/8c638c45-2110-48c7-9a85-186be088874f)

Tämän jälkeen minun tuli vielä käynnistämään uudelleen SSH.

![kuva](https://github.com/user-attachments/assets/9f8cc358-08fc-4d7a-ad1c-d1604f5a89dc)

Suoritin vielä uudelleen päivitykset `sudo apt-get update` ja `sudo apt-get upgrade`-komennoilla viimeiseksi.

![kuva](https://github.com/user-attachments/assets/9eb38450-74de-4e14-99c5-0ef384899a9d)

![kuva](https://github.com/user-attachments/assets/e1302494-1b9d-47fa-a921-0adf22cfd044)

## c) Asenna weppipalvelin omalle virtuaalipalvelimellesi. Korvaa testisivu. Kokeile, että se näkyy julkisesti.

Aloitusaika: Maanantai 21.39 16.9.2024

Edellisen tehtävän jälkeen pidin parin tunnin tauon, jotta jaksoin suoriutua viimeisestä tehtävästä vielä samana päivänä.


Aloitin tekemällä palomuuriin reiän opettajan ohjeiden (https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean) mukaisesti komennolla `sudo ufw allow 80/tcp`.

![kuva](https://github.com/user-attachments/assets/2a2a3cd8-374b-418f-ae65-8937bb862dd4)

Seuraavaksi asensin Apachen uutta testisivua varten komennolla `sudo apt-get -y install apache2`.

![kuva](https://github.com/user-attachments/assets/214be001-c5c0-4523-88cf-5a6c61c2fd62)

Testasin uuden sivun toiminnan testaamalla Apachen oletussivut `curl localhost`-komennolla ja sitten lisäämällä `echo "Toimiiko?" |sudo tee /var/www/html/index.html`-komennolla "Toimiiko?"-tesktin.

![kuva](https://github.com/user-attachments/assets/715bda77-b51a-4c6b-9d53-913d346a71a9)

![kuva](https://github.com/user-attachments/assets/7da2ee85-83a8-43e4-b854-6e5ce7ffd8f2)

Ainakin komentorivillä teksti näkyi oikein. Vielä tämä ei kuitenkaan verkossa näy. Minun tuli vielä käynnistää Apache `sudo systemctl start apache2`-komennolla, jotta pystyin tarkistamaan, näkyikö teksti päivitettynä. Apachen käynnistettyä kokeilin `curl`-komentoa palvelimeni IP-osoitteella.

![kuva](https://github.com/user-attachments/assets/1ea75486-d98c-4ba1-8e71-14619ca2c147)

Hienosti näkyi se mitä haluttiiin. 

Kokeilin myös IP-osoitetta netin kautta, näkyykö teksti.

![kuva](https://github.com/user-attachments/assets/ba376092-71f6-42d6-821e-f6bb3fc065d9)

Onnistuneesti juuri sama teksti näkyi. Seuraavaksi halusin kokeilla puhelimellani, toimiiko palvelimeni myös toisen laitteen kautta, kun kirjoitan palvelimeni IP-osoitteen.



Kyllähän se sieltä näkyi, hieman pienellä fontilla teskti toki oli. Tehtävän lopputulema saavutettiin, suuria vaikeuksia ei syntynyt, mutta ajoittain pientä pohdintaa ja pysähtymisiä tarvitsi tehdä, mikä kulutti aikaa hieman enemmän kuin varsinainen testaaminen.

Lopetusaika: Maanantai 22.10 16.9.2024

![Oman palvelimen kuva](https://github.com/user-attachments/assets/48142fe5-e4d9-4c83-a206-2c07f7401762)


Päivitys tistaina 17.9.2024 klo 15.16.

Muokkasin hieman palvelimeni nettisivuja lataamalla Micro-tekstieditorin, poistamalla Apachen oletussivun ja luomalla uuden oletussivun.

![kuva](https://github.com/user-attachments/assets/977aecbf-efc0-4224-b960-6b68d2204b4e)

![kuva](https://github.com/user-attachments/assets/20724456-470a-4915-902a-b71ff7d257fe)


Lisäsin palvelimeni nettisivuun tekstieditorilla rungon, jotta sivulla olisi tulevaisuudessa valmis pohja, josta helppo jatkaa sivun muokkausta. 

![kuva](https://github.com/user-attachments/assets/dc88f1f5-2bfd-40fa-9aad-16152c18b02d)

![kuva](https://github.com/user-attachments/assets/331c2ce8-16cb-4bc9-8e15-156108eec95e)

Tältä palvelimeni etusivu näyttää muutosten jälkeen.

![kuva](https://github.com/user-attachments/assets/1105c0f3-5615-41a0-b19f-d36446346272)

### Lähteet

- Karvinen 2012: First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/?fromSearch=first%20steps

- Karvinen, Tero 2018: Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address. https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/

- Susanna Lehto 2022: Teoriasta käytäntöön pilvipalvelimen avulla https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/

- Linode https://www.linode.com/

