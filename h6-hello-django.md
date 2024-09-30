# h6 Hello Django

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

## a) Yksinkertainen esimerkkiohjelma Djangolla 

Tehtävänanto: Tee yksinkertainen esimerkkiohjelma Djangolla.

    - Voit käyttää testipalvelinta, kunhan se ei näy Internetiin.
    - Riittää, kun ohjelmasi näkyy esimerkiksi Django Adminsissa.
    - Voit halutessasi tehdä aivan samanlaisen kuin Teron CRM-esimerkissä. Jos olet jo taitavampi, voit hieman soveltaa.
    
Maanantai 30.9.2024 klo 15.17

Aloitin tehtävän lukemalla opettajan ohjeet django asentamisesta (https://github.com/niinaemil1a/LinuxPalvelimet/blob/main/h6.md). 

Ensimmäisenä suoritin mahdolliset päivitykset `sudo apt-get update`- sekä `sudo apt-get upgrade`-komennoilla. 

Seuraavaksi oli tarkoitus asentaa virtualenv-työkalu, jota tarvitaan djangon asennukseen. Suoritin virtualenv-työkalun asennuksen `sudo apt-get -y install virtualenv`-komennolla.

![kuva](https://github.com/user-attachments/assets/129b7cca-8c96-4e7f-a985-b2e8a29ca38d)

Tein seuraavaksi uuden virtuaaliympäristön tulevia asennuksia varten `virtualenv --system-site-packages -p python3 env/`-komennolla, joka loi samalla `env/`-kansion, jossa sijaitsee viimeisimmät paketit.

![kuva](https://github.com/user-attachments/assets/a519d8f3-7b2c-4e4e-8ef4-85cf9a73f6f3)

Jatkoin ottamalla käyttöön uuden luomani virtuaaliympäristön komennolla `source env/bin/activate`. Kun `(env)`-teksti näkyy käyttäjänimen edellä, voi tietää työskentelevänsä kyseisessä virtuaaliympäristössä, mikä on tärkeä muistaa. Varmistin tämän vielä antamalla komennon `which pip`.

![kuva](https://github.com/user-attachments/assets/f2ccd6a0-3acd-4576-a57b-e048cfca7c6d)

Hain netistä tarkempaa tietoa mikä 'pip' itsessään on ja löysin linuxin omilta sivuilta artikkelin (https://www.linux.fi/wiki/PIP), jonka mukaan pip on pythonilla ohjelmoitu ohjelmistopakettien asentamiseen ja hallintaan käytettävä paketinhallintajärjestelmä.

Seuraavaksi tein uuden tiedoston `requirements.txt` micro-editorilla, johon lisäsin `django`-tekstin, jonka jälkeen tallensin tiedoston `ctrl+S` ja poistuin tiedostosta `ctrl+Q`. Tarkistin vielä tiedoston sisällön komennolla `cat requirements.txt`, varmistaakseni tiedoston sisällön olevan oikein kirjoitettu. Kuten opettaja asiasta tunnilla mainitsi, on tärkeää kirjoittaa tiedoston sisältö oikein, sillä muuten voi ladata täysin väärän ohjelman koneelle, joka voi johtaa hakkerointiin esimerkiksi.

![kuva](https://github.com/user-attachments/assets/e0f2c4ff-fe6b-4e33-8eca-c6907bd813ee)

Kun olin varma, että tiedosto oli nyt valmis ja oikein kirjoitettu, siirryin asentamaan djangoa `pip install -r requirements.txt`-komennolla.

![kuva](https://github.com/user-attachments/assets/7bbd6a2e-7eb7-4091-894e-515d56700542)

Tarkistin seuraavaksi, että sain ladattua uusimman version djangosta komennolla `django-admin --version`.

![kuva](https://github.com/user-attachments/assets/fb45aa99-acb6-483b-a357-aa553dbf9d8c)

Seuraavaksi ryhdyin aloittamaan itse projektia djangossa komennolla `django-admin startproject pekkaco`, käynnistin serverin `cd pekkaco -> ./manage.py runserver`-komennoilla. Tarkistin sainko serveriini saman rakettikuvan kuin opettajan ohjeissa.

![kuva](https://github.com/user-attachments/assets/bf1c0679-64c6-4d34-8cb9-a8544073e846)

![kuva](https://github.com/user-attachments/assets/097ed973-6a14-4be8-a7f8-7fb3c22cbeb2)

Tämä osio onnistui ongelmitta. Seuraavaksi tarkoitus oli luoda pääkäyttäjä serverille. Lisäsin selaimeen hakemani url:n perään `/admin`, joka avasi kirjautumissivun, johon minulla ei tosin ollut vielä tunnuksia.

![kuva](https://github.com/user-attachments/assets/4d8db9a7-3f8d-4a95-b4b6-1462bd4b06c4)

Jatkoin terminaalin puolella ja suljin testin `ctrl+C`. Seuraavaksi päivitin tietokannat `./manage.py makemigrations` ja `./manage.py migrate`-komennoilla.

![kuva](https://github.com/user-attachments/assets/7cc5f131-18bf-402b-be2c-d4966010611a)

Sitten lähdin lisäämään uuden käyttäjän, johon tarvitsi ensin asentaa pwgen, joka on salasanageneraattori, `sudo apt-get install pwgen`-komennolla, jonka jälkeen loin vahvan salasanan komennolla `pwgen -s 20 1`. 

![kuva](https://github.com/user-attachments/assets/f859ccca-1eab-4bb9-b0a8-45457590acf7)

![kuva](https://github.com/user-attachments/assets/556b06f1-e68a-4bea-94d7-450c3ea10237)

Tämän jälkeen loin pääkäyttäjän komennolla `./manage.py createsuperuser`, ja lisäsin salasanan.

![kuva](https://github.com/user-attachments/assets/32393769-e1c8-4853-b2f6-4e363ca512bf)

Laitoin serverin uudelleen päälle `./manage.py runserver`-komennolla ja tein aikasemman haun uudelleen, jolla aikaisemmin pääsin kirjautumissivulle ja syötin tarvittavat käyttäjätunnukset.

![kuva](https://github.com/user-attachments/assets/4457c2ab-dc49-4c8e-b7d0-c915c0ab1d00)

Pääsin onnistuneesti kirjautumaan serveriin selaimenkautta.

![kuva](https://github.com/user-attachments/assets/a85d115b-00a7-4538-8e10-5d1b284c049f)

Seuraavaksi opettajan ohjeissa kehotettiin tekemään toinen käyttäjä ja antamaan tälle pääkäyttäjän oikeudet. Painoin ensin `Users`-kodassa `+Add`-painiketta, jonka jälkeen annoin käyttäjälle nimen ja generoin pwgen-ohjelmalla uuden salasanan tälle käyttäjälle, jonka lisäsin salasanaksi. Annoin käyttäjälle Staff statusksen ja Superuser statuksen ja tallensin muutokset.

![kuva](https://github.com/user-attachments/assets/7d226896-9979-4c11-b725-c9e3d614a239)

Nyt kun toinen käyttäjä oli tehty, siirryin luomaan tietokantaa. Suljin serverin ja siirryin takaisin komentoriville. Annoin ensin komennon `./manage.py startapp crm` luodakseni uuden kansion.

![kuva](https://github.com/user-attachments/assets/9f2b490a-e629-45f6-8151-9daf154b2959)

Sitten annoin komennon `micro pekkaco/settings.py` ja lisäsin `crm`-ohjelman `settings.py`-kansioon `INSTALLED_APPS`-osioon.

![kuva](https://github.com/user-attachments/assets/dbf3cb10-13f6-419b-b9f5-6f0c2118710a)

![kuva](https://github.com/user-attachments/assets/5a36bc20-fa41-407d-a926-c8833d87aa10)

Tallensin muutokset ja siirryin luomaan tietokantaa komennolla `micro crm/models.py `, ja lisäsin 'Customer'-luokan ja sarakkeen 'name'.

![kuva](https://github.com/user-attachments/assets/9e783cc8-2186-4b04-8b7d-0545c4400ecd)

![kuva](https://github.com/user-attachments/assets/387db96d-1d00-464a-9e0a-4b6037c443e4)

Tallensin muutokset ja ajoin komennot `./manage.py makemigrations` ja `./manage.py migrate`.

![kuva](https://github.com/user-attachments/assets/ae9a215e-0a34-444e-b7ed-f816728672b5)

Seuraavaksi, jotta voisin nähdä tietokannan, tuli minun rekisteröidä se ensin komennolla `micro crm/admin.py`.

![kuva](https://github.com/user-attachments/assets/ef022f87-e744-492b-8f7e-1918e3b649e7)

Tallennettuani tekemäni muutokset, käynnistin serverini `./manage.py runserver` ja siirryin selaimella `127.0.0.1/admin`-osoitteeseen.

![kuva](https://github.com/user-attachments/assets/f1d802b3-ae16-4b4b-8f08-d851a43cfa58)

Taulun päivitys onnistui! Lisäsin seuraavaksi kaksi asiakasta ja siirryin takaisin komentoriville. Ryhdyin muokkaamaan models.tiedostoa komennolla `micro crm/models.py`. Muokkasin Customer-luokkaan `def __str__(self):	` ja `return self.name`, jolloin luokan pitäisi palauttaa asiakkaiden nimet. 

![kuva](https://github.com/user-attachments/assets/ffc88d55-6f47-49c6-b5c5-825e753eb178)

Tallensin muutokset ja ajoin `./manage.py makemigrations` ja `./manage.py migrate`-komennot, sekä käynnistin serverin `.manage.py runserver`-komennolla. Ihmettelin miksi `./manage.py makemygrations` antoi 'no changes' vastauksen, mutta päätin katsoa oliko mitään muuttunut selainnäkymässä. Tietenkään mikään ei ollut selaimen näkymässä muuttunut ja asiakkaiden nimet olivat edelleen `customer object`-nimisä, kuten komentorivin vastauksesta olisi voinut päätellä. Lähdin tutkimaan, mitä koodissani oli vikana, sillä oli helppo nähdä, että vika oli lisäämässäni `crm/models.py`-sisällössä. Huomasin verratuani koodiani, ohjeiden antamiin koodeihin, että minulta oli jäänyt puuttumaan yksi alaviiva molemmin puolin string määritelmää, jonka korjasin oikein. 

![kuva](https://github.com/user-attachments/assets/92929190-d4d4-47d7-8938-d6120c864f7d)

![kuva](https://github.com/user-attachments/assets/d952ff84-b54e-469c-a128-a65cfeaed21f)

Tallensin muutokset ja tein `./manage.py makemigrations` ja `./manage.py migrate`-komennot uudelleen, ja käynnistin serverin.

![kuva](https://github.com/user-attachments/assets/e0b9b9fe-4cc1-4af6-a180-6e183d8c87bb)

Nyt nimet näkyvät oikein! Nyt ensimmäinen osa oli valmis ja päätin pitää pienen tauon ennen seuraavan tehtävän aloittamista.

## b) Djangon tuotantotyyppinen asennus



### Lähteet

Karvinen, Tero 2024: https://terokarvinen.com/linux-palvelimet/

Karvinen, Tero 2022: Django 4 Instant Customer Database Tutorial https://terokarvinen.com/2022/django-instant-crm-tutorial/

Linux: PIP https://www.linux.fi/wiki/PIP
