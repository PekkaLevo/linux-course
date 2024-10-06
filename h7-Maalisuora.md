# h7-Maalisuora

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

## a) Kirjoita ja aja "Hei maailma" kolmella kielellä

Aloitus sunnuntai 6.10.2024 klo 16.15
Valitsemani kielet tehtävään olivat Python, Ruby ja Bash. Käytin tehtävässä opettajan [ohjeita](https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/), jossa näytettiin komennot, joiden avulla tekstin saisi ajettua onnistuneesti kaikilla valitsemillani kielillä.

Ensimmäiseksi tein `sudo apt-get update` ja `sudo apt-get upgrade`-komennot mahdollisten päivitysten varalta. Lähdin ensimmäisenä tekemään tehtävää Pythonilla, jonka olin jo aikaisemmin asentanut virtuaalikoneelleni. Tein ensin uuden tiedoston ja muokkasin siihen tesktin "Hei maailma" komennolla `micro heimaailma.py`.

![kuva](https://github.com/user-attachments/assets/b92c0205-9f24-42b3-9f69-0adc49e1473c)

![kuva](https://github.com/user-attachments/assets/6c6a5c51-7db8-4b3e-8959-2c78971909ef)

Tein vielä erillisen "tiedostoja"-kansion tehtävässä ajettaville eri kielille `mkdir tiedostoja`-komennolla ja siirsin `heimaailma.py`-tiedoston sinne. Tämän jälkeen ajoin komennon `python3 heimaailma.py`, jolla sain tiedoston sisällön näkyviin komentoriville.

![kuva](https://github.com/user-attachments/assets/a9e0b837-10fa-4e27-bc28-f4168c3b7aa1)

![kuva](https://github.com/user-attachments/assets/49741b03-5cba-4440-add5-917c147537fd)

Seuraavaksi tein saman ruby-kielellä, johon minun tarvitsi asentaa kyseinen ohjelma tehtävän suorittamiseksi. Tein asennuksen komennolla `sudo apt-get install ruby-full`. Asennuksen jälkeen loin uuden `heimaailma.rb` tiedoston "tiedostoja"-kansioon `micro heimaailma.rb`-komennolla, lisäsin sisältöä tiedostoon ja tallensin tiedoston poistuessani. 

![kuva](https://github.com/user-attachments/assets/517ec3ea-1b2c-4cf8-ad28-d6ceb8e596ba)

![kuva](https://github.com/user-attachments/assets/5f68f591-e28d-4fd6-89b9-a8ed85b00f68)

Sitten ajoin komennon `ruby heimaailma.rb` ja "Hei maailma"-teksti saatiin onnistuneesti kirjoitettua Ruby-kielellä näkyviin.

![kuva](https://github.com/user-attachments/assets/ca433238-03cc-4449-8cbe-ee30dda77873)

Viimeinen valitsemani kieli, jolla tehtvän suoritin oli Bash. Ensimmäiseksi tein bash-tiedoston `micro heimaailma.sh`-komennolla `tiedostoja`-kansioon, johon lisäsin samalla "Hei maailma"-tekstin.

![kuva](https://github.com/user-attachments/assets/c5b30349-64c9-498a-be45-e5735c8f7cac)

![kuva](https://github.com/user-attachments/assets/534795d2-2c1f-4aa6-8aa5-1103b7af8797)

Sitten vielä ajoin komennon `bash heimaailma.sh`, joka tuotti vastauksena "Hei maailma"-tekstin komentoriville, kuten haluttiin.

![kuva](https://github.com/user-attachments/assets/0063765c-d7c8-4dbc-979a-fb6c26028458)

## b) Laita Linuxiin uusi komento niin, että kaikki käyttäjät voivat ajaa sitä

Tässä tehtävässä minun tuli luoda Shell script, jota kaikki koneen käyttäjät voivat ajaa. Tutkin ensin internetistä, mitä Shell scriptillä tehdään. Tech targeting [sivujen](https://www.techtarget.com/searchdatacenter/definition/shell-script) mukaan shell script sisältää sarjan komentoja, jotka voidaan suorittaa shellissä. Kyseessä on siis automatisointia.

Aloitin tehtävän tekemällä `tervehdys`-tiedoston, johon kirjoitin sisällöksi tervehdyksiä, joka voi olla eri kielellä, jokainen kerta kun shell scriptiä kutsutaan.

![kuva](https://github.com/user-attachments/assets/5db8897a-d0a9-4ba1-bc4c-84c1c80d12c1)


Tallennettuani tiedoston, ryhdyin määrittelmään tiedoston oikeuksia. Annoin komennolla `chmod a+x tervehdys` kaikille oikeuden suorittaa tiedoston sisällön ajo.

![kuva](https://github.com/user-attachments/assets/289129f8-36fe-44b5-8c9e-d9b1c481c175)

Kopioin tiedoston vielä **/usr/local/bin** hakemistoon `sudo cp tervehdys /usr/local/bin`-komennolla, jotta `tervehdys`-komennon voi suorittaa mistä tahansa kansiosta.

![kuva](https://github.com/user-attachments/assets/c12e4cdf-da31-488b-bbde-4e9778fa4ae6)

Tämän jälkeen kokeilin shell scriptin toimintaa käytänössä.

![kuva](https://github.com/user-attachments/assets/b4b92272-db70-4817-a653-d336e60a6240)

Hienosti toimii!

Lopetin tehtävien tekemisen tältä päivältä tähän ja päätin jatkaa muiden tehtävien tekemistä myöhemmin.

Lopetus sunnuntai 6.10.2024 klo 18.05.

## C) Ratkaise vanha arvioitava laboratorioharjoitus soveltuvin osin

Aloitus sunnuntai 6.10.2024 klo 20.01

Päätin käyttää tehtävään kevään 2023 kurssin labraharjoitusta ja sovelsin tehtäviä siten, että a, b ja c-kohdat jätin tekemättä, sillä kohdat eivät olleet oleellisia harjoituksessa.

d) 'howdy'

Lisäsin päivämäärän ja tekstin "Labraharjoitus" kansion `labraharj` tiedostoon `howdy`, sekä oikeudet tiedostoon.

![kuva](https://github.com/user-attachments/assets/56bae571-5822-4073-a826-f23caca20dd8)


![kuva](https://github.com/user-attachments/assets/8a741f00-7eb8-4f00-9255-a2295678eb5a)

Komennon toimivuus eri hakemistoista.

![kuva](https://github.com/user-attachments/assets/c0d51acd-6727-4d7f-aa8b-e76878394838)

e) Etusivu uusiksi

Tehtävässä tuli asentaa apache, joka minulta löytyikin jo, sekä tehdä yritykselle "AI Kakone"-kotisivut, jota tulisi voida muokata normaalin käyttäjän oikeuksilla.

![kuva](https://github.com/user-attachments/assets/1af05f26-da98-4703-9edc-23f0a968a03f)

sivun `aikakone.com`.oikeudet.

![kuva](https://github.com/user-attachments/assets/439a0455-b11e-488a-af1f-e020de454866)

g) Salattua hallintaa

Tehtävässä tuli asentaa ssh-palvelin, tehdä uusi käyttäjä ja automatisoida kirjautuminen julkisen avaimen menetelmällä.

![kuva](https://github.com/user-attachments/assets/ae24ef95-f3fd-4dbe-85f4-7b2cf48673f3)

h) Djangon lahjat

Tehtävässä tuli asentaa omalle käyttäjälle django kehitysympäristö jatehdä tietokantaan lista, jossa on kirjautuminen salasanalla, Djangon omalla ylläpitoliittymällä tietokannan muokkausta wepin kautta, käyttäjälle Erkki, jossa ei ole ylläpito-oikeuksia ja taulu Assistants, johon jokaiselle tietueelle oma nimi.

h) Tuotantopropelli

Tehtävässä tuli tehdä tuotantotyyppinen asennus Djangosta ja laittaa Django-lahajtietokanta tuotantotyyppiseen asennukseen.

### Lähteet

Karvinen, Tero 2024 https://terokarvinen.com/linux-palvelimet/

Karvinen, Tero 2018 https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/

Karvinen, Tero 2007 https://terokarvinen.com/2007/12/04/shell-scripting-4/

Tech target: What is a shell script and how does it work? https://www.techtarget.com/searchdatacenter/definition/shell-script
