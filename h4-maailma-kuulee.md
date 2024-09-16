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
