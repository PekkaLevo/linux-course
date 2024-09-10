# h3 Hello Web Server


## x) Lue ja tiivistä



### Name-based Virtual Host Support

- IP-based virtual hosting käyttää Ip-osoitetta oikean palvelimen määrittämiseen. Jokainen palvelin tarvitsee siten oman Ip-osoitteen.

- Name-based virtual hosting jakaa Ip-osoitteen ja konfiguroivat DNS-palvelimen oikeaan Ip-osoitteeseen ja konfiguroida Apache-palvelin tunnistamaan verkkotunnuksia.

- Name-based virtual hosting:n avulla vähennetään Ip-osoitteita määrää, joka on suositeltavaa, ellei erikseen tarvita Ip-pohjaista isännöintiä.


### Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address

- Apachella voidaan yhden Ip-tunnuksen ja monen verkkosivun käytön sijaan, yhdellä Ip-osoitteella isännöidä monia verkkotunnuksia.

- Komentojen avulla asennetaan ja konfiguroidaan verkkopalvelin.

- Voidaan lisätä uusi nimeen perustuva virtuaalipalvelin ja määritetään palvelin tiedostoon komennoilla.

- Sivusto otetaan käyttöön ja käynnistetään uudelleen annetuilla komennoilla.

- Verkkosivun luonti käyttäjänä tapahtuu annetuilla komennoilla.

- Lopuksi komennot palvelimen testaamiseen.


### Lähteet

The Apache Software Foundation 2023: Apache HTTP Server Version 2.4 Documentation: Name-based Virtual Host Support. https://httpd.apache.org/docs/2.4/vhosts/name-based.html

Karvinen 2018: Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address. https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/


## Järjestelmätiedot

## Virtuaalikone

- Virtualisointi: VirtualBox 7.0.20

- Käyttöjärjestelmä: Debian 12.6.0 AMD64

- Muistikapasiteeti: 4096 MB

- Prosessori: 4 CPU

## Fyysisen kone

- Konetyyppi: Kannettavatietokone

- Käyttöjärjestelmä: Windows 11 Home, 64bit, x64-suoritin

- Prosessori: 11th Gen Interl(R) COre(TM) i3

- Muisti: 8GB

## a) Weppipalvelimen testaus

#### Tehtävänanto: Testaa, että weppipalvelimesi vastaa localhost-osoitteesta. Asenna Apache-weppipalvelin, jos se ei ole jo asennettuna.

Asensin Apachen jo oppitunnin aikana, joten siirryin suoraan testaamaan. Weppipalvelimen testaamiseksi kirjoitin selaimen hakuun `localhost`.

![kuva](https://github.com/user-attachments/assets/c43f21b3-ae39-4d78-8034-62dd7a6d286a)

Tämä avasi Apachen oletussivun, jossa luki "it works", josta voin päätellä, että palvelin toimii. Testasin tämän lisäksi myös komentorivin kautta, että sama oletussivu avautuisi, komennolla `curl localhost`. 

![kuva](https://github.com/user-attachments/assets/91ed6e56-aa30-48d1-970c-c98e4707ec1b)

Vastauksena sain Apache2 Debianin Default page-näkymän, josta löytyi sama "it works"-teksti <title>-rivin kohdalta, kuin selainnäkymässä.


## b) Lokista etsiminen

#### Tehtävänanto: Etsi lokista rivit, jotka syntyvät, kun lataat omalta palvelimeltasi yhden sivun. Analysoi rivit.

Kurssin kotisivuilta löysin vinkkejä, joiden avulla voisin löytää halutut lokin rivit. Kokeilin jo tunnilla mainittua ja esitettyä komentoa `sudo tail /var/log/apache2/access.log` tarkastelin tuloksia.

`sudo tail /var/log/apache2/accss.log`-komento antoi vastaukseksi seuraavaa tietoa:

![kuva](https://github.com/user-attachments/assets/3db1f89c-3419-43de-a8bd-f90a1d1cecce)

Etsin Apachen omilta verkkosivuilta tietoa, mitä tietoa `access.log`-komennolla saatiin. Sivujen mukaan `access.log`-komennolla saadaan lokitiedoston tiedot kaikista Apache-palvelimen vastaanottamista pyynnöistä, jotka se on tallentanut. Kyseessä on siis pääsyloki.

Pääsylokin rivien alussa löytyy Ip-osoite(127.0.0.1), josta pyyntö tehtiin. Yritin selvittää minkä tahon Ip-osoite voisi olla kyseessä. Lifewire-verkkosivun(https://www.lifewire.com/network-computer-special-ip-address-818385) mukaan kyseessä olisi ns. "loopback address", joka tarkoittaa samaa kuin localhost eli omaa konettani. 

Apachen omien verkkosivujen(https://httpd.apache.org/docs/current/logs.html) mukaan, "-"-merkki Ip-osoitteen jälkeen on korvike, jos kyseisen tunnisteen tiedot puuttuvat. Ensimmäisen "-"-merkin kohdalla on `identd`-ohjelman määrittämä RFC 1413-tunniste ja toinen "-"-merkin kohtaan tulisi käyttäjätunnus, joka korvataan "-"-merkillä, jos dokumenttia ei ole salasanasuojattu.

Tämän jälkeen on päiväys ja kellonaika. Päiväys ja kellonaika kertovat, mikä päivä, millä aikavyöhykkeellä ja mihin kellonaikaan tekemäni selainhaut ja komentorivillä tehdyt komennot on suoritettu. Päiväys oli pääsylokissa asetettu tälle päivälle ja kellon aika piti paikkansa. Lokista näkyi myös edellisviikon oppitunnilla tehtyjen localhost selainhakujen ja komentorivillä tehtyjen `curl localhost`-komentojen päiväykset ja kelloajat.

Seuraavaksi tutkin "Get / HTTP / 1.1" merkitystä. Apachen sivujen mukaan kyseessä olisi annettu pyyntörivi. "Get" on pyynnössä käytetty metodi ja "HTTP / 1.1" protokollaa. Näiden jälkeen tulevat tiedot "200" ja " 10956 / 3380" tarkoittavat tilakoodia ja vastauksen kokoa. Tilakoodi on tärkeää tietoa, sillä se kertoo saiko pyyntö onnistuneen vastauksen(alkaa numerolla 2), uudelleenohjauksen(alkaa numerolla 3), käyttäjän aiheuttaman virheen(alkaa numerolla 4) vaiko palvelimen virheen(alkaa numerolla 5).

Tämän jälkeen näkyy URL-osoite, mutta jos sitä ei ole tarjolla, käytetään korviketta "-".

Viimeisenä tämän jälkeen löytyy tunnistetieto, jonka käytetty selain tai komentorivi raportoi itsestään.


## c) Etusivu uusiksi

#### Tehtävänanto: Etusivu uusiksi. Tee uusi name based virtual host. Sivun tulee näkyä suoraan palvelimen etusivulla http://localhost/. Sivua pitää pystyä muokkaamaan normaalina käyttäjänä, ilman sudoa. Tee uusi, laita vanhat pois päältä. Uusi sivu on hattu.example.com, ja tämän pitää näkyä: asetustiedoston nimessä, asetustiedoston ServerName-muuttujassa sekä etusivun sisällössä (esim title, h1 tai p).

Aloitin tehtävän hakemalla ohjeet oppitunnilla neuvotulta opettajan sivulta(https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/). Suoritettuani aikaisemmin Apache-weppipalvelimen asennuksen, kokeilin ensimmäiseksi oletussivun vaihtamista komennolla `echo "Default"|sudo tee /var/www/html/index.html`.

![kuva](https://github.com/user-attachments/assets/73ad8645-58ce-4c92-89e0-65650f226c9d)

Vastauksesta oletin, että kyseinen "default"-teksti oli nyt localhost-sivun uusi näkymä, joten tarkistin selaimen kautta, jos sivulle oli tullut muutoksia. Ja näin olikin käynyt. Etusivulla näkyi vain pieni "default"-teksti vasemmassa yläkulmassa.

![kuva](https://github.com/user-attachments/assets/0e316a16-94ed-443e-a767-0a24043a68d9)

Seuraavaksi ohjeiden mukaan lisätään uusi Name Based Virtual Host. Vaihdoin tämän sivun nimeksi hattu.example.com tehtävänannon mukaisesti, komennolla `sudoedit /etc/apache2/sites-available/hattu.example.com.conf`.

![kuva](https://github.com/user-attachments/assets/822ddfce-4f9f-4b84-8873-180232db4ac1)

Komento avasi tyhjän tiedoston, jonka oletin olevan verkkosivun tiedosto.

![kuva](https://github.com/user-attachments/assets/4f1cff0f-d253-43eb-8852-b3d45cb1663a)

Määritin tiedoston ServerName:n, ServerAlias:n, DocumentRoot:n ja Directoryn. Vaihdoin ohjeissa esiintyvän `xubuntu`-käyttäjän omaan käyttäjääni, sillä virtuaalikoneessa ei ole sen nimistä käyttäjää. Lopuksi tallensin tiedoston.

![kuva](https://github.com/user-attachments/assets/ffbe4e33-5a00-4881-b994-f2a6fa974e25)

Jatkoin ohjeiden mukaan ja kokeilin aktivoida sivuston `sudo a2ensite hattu.example.com`-komennolla.

![kuva](https://github.com/user-attachments/assets/de777447-8c25-45a4-b099-69d50a89a35c)

Sain vastaukseksi pyynnön käynnistää Apache2 uudelleen, joten suoritin ehdotetun komennon. 

![kuva](https://github.com/user-attachments/assets/a47b91c4-5bbc-4f62-a980-da8508e3e99a)

Seuraavaksi loin hakemiston sivulle ja lisäsin index.html hakemistoon ja tarkistin, että "hattu"-teksti näkyy eli että sivu vastaa. Tässä kohti olin unohtanut tallentaa tiedoton oikeaan sijaintiin, joten aluksi sivulla luki vielä "default"-teksti kunnes tein tallennuksen oikein. 

![kuva](https://github.com/user-attachments/assets/e1187282-cdbe-427b-9265-6da1f74f3664)

Selaimen puolella päivitys ei kuitenkaan ollut vielä päivittynyt "hattu"-teksti, joten etsin ohjeista komennon `sudoedit /etc/hosts`, jolla sain tekstitiedoston avattua ja lisäsin 127.0.0.1 riviin hattu.example.com:n.

![kuva](https://github.com/user-attachments/assets/282cc076-49d3-4402-9921-493b6ddb7436)

Nyt teksti näkyy. Tehtävänannossa kuitenkin tuli hattu.example.com:n näkyä asetustiedoston nimessä, ServerName-muuttujassa ja etusivun sisällössä. Minun tuli siis vielä muokata sivun sisältöä.

Etsin ensin hattu.example.com:n sijainnin ja avasin tiedoston microlla, jotta voin muokata tiedostoa. Käytin apunani opettajan antamaa esimerkkipohjaa(https://terokarvinen.com/2012/short-html5-page/).

![kuva](https://github.com/user-attachments/assets/811bb886-617d-4f3e-844f-740166b7521f)

![kuva](https://github.com/user-attachments/assets/a913b88f-9a02-4382-8599-357498f9666a)



Ja näin sivu saatiin muokattua halutulla tavalla.

![kuva](https://github.com/user-attachments/assets/56302e9a-dfe2-4f36-a584-144c99c06386)

## e) Tee validi HTML5 sivu

Minun tuli seuraavaksi tarkistaa weppisivuni validisuus Validator-verkkosivulta(https://validator.w3.org/#validate_by_input+with_options). Tässä vaiheessa kun sivuni ei ollut löydettävissä verkosta, joten ainoa optioni oli kopioda tekstin suoraan validatorin "Direct input"-osioon.

![kuva](https://github.com/user-attachments/assets/2b3a7368-225c-4f04-b10b-35b56dda1c44)

Validator ei antanut muita muutosohjeita, kuin "trailing slash"-kohdan voisi poistaa, joten muokkasin tekstiä ja poistin ylimääräisen "/"-merkin.

![kuva](https://github.com/user-attachments/assets/24fe95d7-80b1-4737-a799-202b9aa808d0)

![kuva](https://github.com/user-attachments/assets/b962edff-0117-4670-bee9-f3cf36cfb91d)

## f) Anna esimerkit 'curl -I' ja 'curl' -komennoista. Selitä 'curl -I' muutamasta näyttämästä otsakkeesta (response header), mitä ne tarkoittavat.


#### "curl"-komento

`curl`-komennolla saamme näkyviin halutun sivun html-lähdekoodin. 

![kuva](https://github.com/user-attachments/assets/f2d35467-4ddc-412a-aed6-33d398a8a3fe)



#### "curl -I"-komento

`curl -I`-komentoa käyttämällä saamme otsikkotiedot haetusta osoitteesta. Seuraavaksi kokeilin `curl -I`-komentoa `hattu.example.com`-osoittella.

![kuva](https://github.com/user-attachments/assets/9818768c-b9d8-4b1d-9fc2-2f2279062222)

`curl -I`-komentoa käytettäessä `hattu.example.com`-osoitteeseen, saamme seuraavia tietoja:

- HTTP/1.1 200 OK: Protokolla, sekä HTTP-vastauskoodi 200 ja "OK" eli onnistunut.

- Date: Aika, jolloin pyyntö tehtiin. 

- Server: Käytetyn palvelimen tyyppi.

- Last-Modified: Viimeinen aika kun kyseistä osoitetta on muokattu.

- ETag: MDN Web Docsin mukaan kyseessä on resurssin eli verkkosivun versio.

- Accept-Ranges: Kertoo, tukeeko palvelin osittain latausta tavualueilla.

- Content-Length: Kertoo pyynnön koon tavuina.

- Vary: Smashing magazinen mukaan se kertoo, että resurssia välimuistitetaan erikseen.

- Content-Type: Minkä tyyppistä sisältö on.

## Lähteet

The Apache Software Foundation 2023 Apache HTTP Server Version 2.4 Documentation: Name-based Virtual Host Support: (https://httpd.apache.org/docs/2.4/vhosts/name-based.html)

What Is the 127.0.0.1 IP Address? (https://www.lifewire.com/network-computer-special-ip-address-818385)

Apache: Log Files (https://httpd.apache.org/docs/current/logs.html)

Apache: Module Index (https://httpd.apache.org/docs/2.4/mod/#N)

Karvinen 2018: Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address: (https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/)

Karvinen 2012: Short HTML5 page (https://terokarvinen.com/2012/short-html5-page/)

Markup Validation Service (https://validator.w3.org/#validate_by_input+with_options)

MDN Web Docs (https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/ETag)

Smashing magazine: Understanding The Vary Header (https://www.smashingmagazine.com/2017/11/understanding-vary-header/)
