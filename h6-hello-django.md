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
    
Aloitus: maanantai 30.9.2024 klo 15.17

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

Tehtävänanto: Tee Djangon tuotantotyyppinen asennus

    - Voit halutessasi tehdä asennuksen omalle, paikalliselle virtuaalikoneelle. Sen ei tarvitse näkyä Internetiin.

Maanantai 30.9.2024 18.30

Jatkoin seuraavan tehtävän parissa tauon jälkeen ja käytin opettajan ohjeita tuotantotyypisen djangon asennuksesta (https://terokarvinen.com/2022/deploy-django/) apunani tehtävässä. Päätin olla asentamatta djangoa omalle palvelimelleni ja harjoitella ensin virtuaalikoneen puolella. Olin jo ennen edellistä tehtävää ehtinyt tehdä päivitykset, joten siirryin suoraan asentamaan bash-completion-ohjelmaa, jonka avulla 'tab' painike automaattisesti saadaan tiedostojen nimiä täytettyä. Asennuksen tein `sudo apt-get -y install bash-completion`-komennolla.

![kuva](https://github.com/user-attachments/assets/294826da-009f-41a6-bc1c-7e7561306a9b)

Olin jo aikaisemmin asentanut Micron ja Apache2:n, joita tässä tehtävässä pyydettiin asentamaan, joten siirryin eteenpäin ja loin uuden kansion ja tiedoston projektia varten. 

![kuva](https://github.com/user-attachments/assets/95703c88-3175-4845-a468-532064cc963a)

Seuraavaksi loin virtuaal hostin uuteen tiedostooni ja otin sivun käyttöön `sudo a2ensite pekkaco.conf` ja otin pois käytöstä vanhat sivut, jotka olivat käytössä samalta IP-osoitteelta `sudo a2dissite 000-default.conf`-komennolla, sekä käynnistin apachen uudelleen.

![kuva](https://github.com/user-attachments/assets/fd044ae0-d374-43a0-a694-fd9d26e689bb)

![kuva](https://github.com/user-attachments/assets/90c4783f-bf89-4784-9f4d-41aed4d3fe86)

![kuva](https://github.com/user-attachments/assets/c64646b2-0437-4b91-bd52-d497720a2f8f)

![kuva](https://github.com/user-attachments/assets/5d9846fa-aafb-4fab-914d-e2df39edce04)

Tarkistin, että configurointi toimii `/sbin/apache2ctl configtest`-komennolla ja kokeilin `curl http://localhost/static/`-komennolla tiedostojen toimintaa.

![kuva](https://github.com/user-attachments/assets/a7d73482-3606-43e6-b5f2-07645741735d)

`curl http://localhost/static/-komento antoi vastauksesksi '404 not found'-virheilmoituksen, eli jokin ei nyt toiminut oikein. Epäilen, että hattu.example.com on edelleen yhdistettynä localhost-osoitteeseen, sillä weppiselaimessa tämä sivu tulee kun haen 'localhost'-haulla.

![kuva](https://github.com/user-attachments/assets/5c4d7b71-7d93-4dcc-865c-05f54db2b351)

Lähdin selvittämään, miten saisin kytkettyä hattu.example.com:n pois, vaikka olin jo tehnyt `sudo a2dissite`-komennon. Chatgpt:n mukaan `sudo a2dissite`-komentoon kuuluisi lisätä haluttu tiedosto, jonka haluaa laittaa pois päältä. Kokeilin siis seuraavaksi `sudo a2dissite hattu.example.com.conf`-komentoa ja käynnistin  apachen uudelleen.

![kuva](https://github.com/user-attachments/assets/a36cd911-c1e2-4459-baf9-ad33ff7ac4f5)

Nyt sivu toimiikin oikein, joten voin jatkaa tehtävää.

![kuva](https://github.com/user-attachments/assets/cb262ea6-7628-40d2-a3eb-5d09c22c9698)

Seuraavaksi loin uuden virtuaaliympäristön `publicproject`-hakemistoon `virtualenv -p python3 --system-site-packages env`-komennolla. Tämän jälkeen aktivoin virtuaaliympäristön `source env/bin/activate`-komennolla ja tarkastin, että pip-paketin asentaja löytyy `env/`-hakemiston alta.

![kuva](https://github.com/user-attachments/assets/66c5b897-42f4-4cef-b82e-e8ee94f8767d)

Tein seuraavaksi `requirements.txt`-tekstitiedoston `micro requirements.txt`-komennolla ja lisäsin asennettavan paketin nimen 'django' ja tarkistin vielä, että se oli oikein kirjoitettu `cat requirements.txt`, ettei mitään hakkerointi-ohjelmaa tullut ladattua.

![kuva](https://github.com/user-attachments/assets/b3e3a5ed-b263-4c33-9581-97a694c653bf)

Seuraavaksi tein ohjelman asennuksen `pip install -r requirements.txt`-komennolla ja tarkistin djangon version `django-admin --version`-komennolla.

![kuva](https://github.com/user-attachments/assets/b882f0cf-ae96-4575-90b8-5f165fe0fb9c)

Sitten käynnistin projektin `django-admin startproject pekkaco`-komennolla ja jatkoin ohjeiden mukaisesti tehtävän tekemistä.

![kuva](https://github.com/user-attachments/assets/53247963-5249-4123-b600-bb02a6ff73a9)

Seuraavaksi lisäsin opettajan ohjeissa annetuja tietoja `sudoedit /etc/apache2/sites-available/pekkaco.conf`-komennolla ja tallensin muutokset. 

![kuva](https://github.com/user-attachments/assets/7e6fdbaf-f4ff-457f-a058-122847e11dec)

Tämän jälkeen asensin Apache WSGI moduulin `sudo apt-get -y install libapache2-mod-wsgi-py3`-komennolla ja tarkistin syntaxit `/sbin/apache2ctl configtest`-komennolla.

![kuva](https://github.com/user-attachments/assets/03d7df6f-24b6-48c1-aa49-c35b21f2b66b)

Käynnistin Apachen uudelleen komennolla `sudo systemctl restart apache2` ja tarkistin sivun toiminnan `curl -s localhost|grep title`-komennolla.

![kuva](https://github.com/user-attachments/assets/380a282e-6751-4a25-92ac-4b4e629e517b)

Tarkistin vielä, että kyseessä oli Apache.

![kuva](https://github.com/user-attachments/assets/997c1730-f059-40e2-901c-82622e88599a)

Sitten vielä hain selaimesta `localhost`-haulla, että sivu on oikein.

![kuva](https://github.com/user-attachments/assets/fa450544-71aa-4ace-a6ae-6883e64a9f0f)

Seuraavaksi otin virheen korjauksen pois päältä ja muutin `ALLOWED_HOSTS`-osioon vain localhost. 
![kuva](https://github.com/user-attachments/assets/420dd7f6-fe2b-4b4d-b232-a0352e7c9abd)

![kuva](https://github.com/user-attachments/assets/a2f3b7e7-303e-4a83-8614-004ecd90f8f5)

Sitten käynnistin Apachen uudelleen ja kokeilin komentoa `curl -s localhost|grep title`.

![kuva](https://github.com/user-attachments/assets/32f43cca-c5d9-407e-b420-706113dfeb9e)

![kuva](https://github.com/user-attachments/assets/f47b4a58-3dd9-4021-8060-87bca90ac529)

Kokeilin vielä `http://localhost/admin`-hakua, jolla sivu toimi, mutta käyttäjä minulta vielä puuttui. Ensin täytyi lisätä tyyli, jonka sai muokkaamalla `pekkaco/settings.py`-tiedostoon `STATIC_URL = 'static/'`-kohdan alle `import os` ja `STATIC_ROOT = os.path.join(BASE_DIR, 'static/')`.

![kuva](https://github.com/user-attachments/assets/96df2550-36f4-401b-ba40-4e75bc19fb8b)

![kuva](https://github.com/user-attachments/assets/682737c0-b6cf-4d27-a7fa-b2ac11eaa796)

Tämän jälkeen suoritin `./manage.py collectstatic`-komennon.

![kuva](https://github.com/user-attachments/assets/8f6b41e1-7fe6-4d6f-9d90-d685870056b0)

Tämän jälkeen hain `http://localhost/admin`-sivun uudelleen ja tyylin muutokset olivat heti nähtävissä.

![kuva](https://github.com/user-attachments/assets/d6f54d87-cc68-4912-8fb0-3edddfa8f1e1)

Vielä viimeiseksi pääkäyttäjän tekeminen, johon ensiksi ajamme komennot `./manage.py makemigrations` ja `./manage.py migrate`, sekä luomme uuden pääkäyttäjän `./manage.py createsuperuser`-komennolla, johon generoimme salasanan pwgen-ohjelmalla.

![kuva](https://github.com/user-attachments/assets/a7cb2d33-3925-4fab-be60-f4224d1af24a)

![kuva](https://github.com/user-attachments/assets/52b309ac-0ba6-44d3-a5c1-9f7a3cb64ef7)

Sitten vielä yritin kirjautua pääkäyttäjän tunnuksilla sisään.

![kuva](https://github.com/user-attachments/assets/3d72bb0d-5bce-4fed-8193-1b802c989f15)

Kirjautuminen onnistui ongelmitta.

Lopetus: maanantai 30.9.2024 klo 22.03

### Lähteet

Karvinen, Tero 2024: Linux Palvelimet 2024 alkusyksy https://terokarvinen.com/linux-palvelimet/

Karvinen, Tero 2022: Django 4 Instant Customer Database Tutorial https://terokarvinen.com/2022/django-instant-crm-tutorial/

Linux: PIP https://www.linux.fi/wiki/PIP

Karvinen, Tero 2022 Deploy Django 4 - Production Install https://terokarvinen.com/2022/deploy-django/

Chatgpt: https://chatgpt.com/
