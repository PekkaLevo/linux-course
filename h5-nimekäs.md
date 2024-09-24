# h5 Nimekäs

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

## a) Kotisivu

Tehtävän aloitus Maanantai 23.9.2024 klo 18.07

#### Tehtävänanto: Tee vähintään kolmen erillisen weppisivun kotisivu ja kopioi se näkymään palvelimellesi. Jos sinulla on oikea palvelin Internetissä, kannattaa käyttää sitä. Käytä name based virtual hosting tekniikkaa. Sivujen muokkaamisen pitää onnistua ilman pääkäyttäjän oikeuksia, niiden kopioiminen pääkäyttäjänä testisivun paikalle ei käy. Kotisivujen ei tarvitse olla hienoja, mutta niiden tulee olla validia HTML:ää ja linkittää toisiinsa.


Aloitin tehtävän suorittamalla `sudo apt-get update` ja `sudo apt-get upgrade`-komennot päivitysten varalta. Seuraavaksi kaivoin esiin aikaisemman name based virtual host-tehtäväni, sekä opettajan ohjeet kyseeseen aiheeseen (https://terokarvinen.com/2018/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/?fromSearch=name%20based).

Sillä peklev.com oli jo aikaisemmin minulla olemassa oleva palvelin, käytin sitä tässä tehtävässä.
Seuraavaksi loin uudet tiedostot `/etc/apache2/sites-available`-hakemistoon.
ja sitten suoritin opettajan name based virtual host-ohjeiden mukaisesti `sudo a2ensite`-komennon.
Sitten vielä käynnistin apachen uudelleen `sudo systemctl restart apache2`-komennolla.

![kuva](https://github.com/user-attachments/assets/58be583e-f559-4d09-ac95-dcc084a8030b)

![kuva](https://github.com/user-attachments/assets/31da5997-fb84-4fe0-b5b6-e57364ebec84)

![kuva](https://github.com/user-attachments/assets/74de87f7-f18c-434f-a855-867c99940ac4)


Muokkasin tämän jälkeen micro-editorilla sivustojen `index.html`-tiedostoihin sisältöä.

![kuva](https://github.com/user-attachments/assets/1f7afcf0-c49f-459e-8da7-088bc0849ab5)


Kokeilin seuraavaksi `curl`-komennolla sivujen toimivuutta, mutta komentorivi antoikin virheilmoituksen.

![kuva](https://github.com/user-attachments/assets/cb802b6b-d5a3-4067-bf8b-1fdaab29959b)


Hieman tutkittuani asiaa netistä, en löytänyt sopivaa vastausta, joten päätin kysyä ongelmasta Chatgpt:ltä. Chatgpt neuvoi kokeilemaan komentoa ´sudo chmod 755 /home/peksi´. Tämä ei kuitenkaan auttanut
tapauksessani, joten etsin hieman lisää vinkkejä.

Jotain oli mennyt pieleen edetessä, sillä kokeilin myös oman nettisivuni `peklev.com`-hakua ja

![kuva](https://github.com/user-attachments/assets/55fecd70-c184-4bab-a529-acf2057f9584)

Sama tieto tuli myös komentoriviltä.

![kuva](https://github.com/user-attachments/assets/ccd8fecb-11d6-4c91-bb81-915d6b2ce9c3)

Huomasin myös kun kokeilin `host 172.234.116.108`-komentoa, antoi se Linoden osoitteen.

![kuva](https://github.com/user-attachments/assets/0ac278db-2cc1-4365-a9c4-16d65b957f42)

Jatkoin kuitenkin suorittamalla uusille `kuva.peklev.com` ja `info.peklev.com`-sivuille `mkdir -p`-komennot.

![kuva](https://github.com/user-attachments/assets/376e867b-85b0-4173-aedb-26c512441f41)

Päätin tässä vaiheessa jatkaa myöhemmin, kun jäin umpikujaan tehtävän kanssa.

Lopetus maanantai 23.9.2024 klo 20.26

Jatkoin tiistaina 24.9.2024 klo 9.36

Yön mietittyäni ja uusi aivoilla päivään lähtien muistin etten ollut vielä muokannut `etc/hosts`-tiedostoon oikeuksia uusiin tiedostoihin. 

![kuva](https://github.com/user-attachments/assets/0e4c010f-1e50-4c17-bbd7-c1f5ebb633d9)


Hosts-tiedot muokattuani, tein publicsites kansioon muutoksen ja siirsin `kuva.peklev.com` ja `info.peklev.com`-tiedostot `peklev.com`-tiedostoon.

![kuva](https://github.com/user-attachments/assets/b3bf81f3-5b88-43a2-9c38-26b91f885d0b)

Sivustoni ei kuitenkaan vielä näkynyt `curl`-komennon avulla, joten kysyin Chatgpt:ltä apua ja se neuvoi antamaan `sudo chmod 711 /home/peksi`-komennon sekä uudestaan `sudo chmod 755`-komennon mutta tarkemmin `/home/peksi/publicsites`-tiedostoon kohdentaen. Nämä komennot tehtyäni kokeilin `curl`-komentoa uudelleen, mutta mitään muutosta ei vielä ollut tapahtunut.

![kuva](https://github.com/user-attachments/assets/133e0b23-779a-4054-835b-87b358736f90)

Jatkoin kuitenki Chatgpt:n neuvoja tilanteen ratkaisemiseksi ja kopioin `sudo tail -f /var/log/apache2/error.log`-tiedot Chatgpt:lle. Tähän Chatgpt kertoi virhelokin tiedoista, ettei minulla ollut `peklev.com`-tiedostossa `index.html`-tiedostoa, jonka loin tämän jälkeen.

![kuva](https://github.com/user-attachments/assets/4d937ea6-5188-4279-a3b5-2e82ed0c11ca)

Nyt `curl`-komennolla sain tiedoston näkymään, mikä oli tässä vaiheessa jo iso edistys. Muokkasin tässä vaiheessa index.html tiedostoa hieman mieluisammaksi.

![kuva](https://github.com/user-attachments/assets/c03deead-2d04-4243-b595-00104c05c8ed)


Sivuni eivät kuitenkaa vieläkään toimineet, joten selvitin muita Chatgpt:n antamia neuvoja. Seuraavaksi Chatgpt ehdotti `apache2.conf`-tiedostoon `ServerName peklev.com` lisäämistä, joten kokeilin tätä vaihtoehtoa ja käynnistin Apachen uudelleen. 

![kuva](https://github.com/user-attachments/assets/a20f0d74-0447-4e80-8adc-3b1f99b6a85e)

Tämäkään ei tosin vielä muuttanut nettisivuani toimivaksi. Seuraavaksi tarkistin `host 172.234.116.108`-komennolla, mikä on ip-osoitteeni host. Komentorivi antoi
vastaukseksi: 

![kuva](https://github.com/user-attachments/assets/34c52415-ffe2-49ab-a692-61795ddfad75)

Chatgpt:n mukaan ilmeisesti DNS-asetuksissani oli nyt vikaa, joten kävin tarkistamassa tilanteen Namecheapista ja huomasin, että toinen A-tietueeni oli poistunut, joten tein A-tietueet sekä ´@´, että `www`-isännille, jotta sivu toimisi molemmilla hauilla.

![kuva](https://github.com/user-attachments/assets/8a4ef45f-156b-4b81-a746-1646af4373ac)

![kuva](https://github.com/user-attachments/assets/75da3e63-498e-4ee4-9f95-bc273423312a)

Tämän jälkeen Chatgpt neuvoi seuraamaan sivujeni tietueiden päivittymistä `dig peklev.com`-komennolla, sillä `Got answer: `-rivi oli tyhjä, mutta siihen pitäisi tulla sivuni ip-osoite kun DNS on päivittynyt.

![kuva](https://github.com/user-attachments/assets/c1e47fbd-e93f-4ee0-a55c-d56e5d5f2ab5)

Vihdoinkin DNS oli päivittynyt ja sivuni toimivat taas. Toki kaikille sivuille voisi tehdä paljon hienosäätöä, että olisivat hienommat, mutta toimivat halutulla tavalla mikä on tärkeintä.

![kuva](https://github.com/user-attachments/assets/62f7a353-0cb6-42b2-8d51-3999dc2b678b)

![kuva](https://github.com/user-attachments/assets/8d7167ff-13ec-4b65-b1d1-da0933b0653e)

![kuva](https://github.com/user-attachments/assets/89ba83dc-db58-4adf-b9e4-06e773073409)

Tein vielä viimeiseksi validatorin kautta tarkastuksen sivun validisuudesta.

![kuva](https://github.com/user-attachments/assets/b5a0e684-2189-4762-a78d-eda404838f16)





## b) Alidomain

Maanantai 23.9.2024 klo 20.26

Vaikka ensimmäinen tehtäväni ei vielä toiminut halutulla tavalla päätin tehdä ainakin alidomainit valmiiksi ennen a-tehtävän onnistumista. Hain Namecheapin omilta sivuilta (https://www.namecheap.com/support/knowledgebase/article.aspx/9776/2237/how-to-create-a-subdomain-for-my-domain/) ohjeet alidomainien tekemiseen.

Aloitin luomalla Advanced DNS-asetusten alta painamalla add new record-painiketta ja täytin sekä A-tietueen tiedot, että CNAME-tiedot luomistani alidomaintiedostoista.

![kuva](https://github.com/user-attachments/assets/50c20bcc-5080-4d66-8a0f-d7c9d6e55122)

Alidomanien näkyvyyden tarkistinkin jo edellisessä tehtävässä.

## c) Pubkey

Tiistai 24.9.2024 klo 12.10

Lähdin ensimmäisenä tutkimaan mikä pubkey on ja miten se toimii. SSH Academyn-sivuilta (https://www.ssh.com/academy/ssh/public-key-authentication) löysin paljon tietoa asiasta. Kyseessä on lyhenne julkisesta avaimesta ja kyseessä on salaustekniikka, tarkemmin epäsymmetrinen salaus. Tässä salauksessa käytetään avain paria, julkinen- ja yksityinen avain. Julkinen avain on julkisesti jaetavissa, kun taas yksityinen avain pidetään salassa muilta. 

Varsinaiseen avaimenluontiin käytin SSH Academyn ohjeita (https://www.ssh.com/academy/ssh/keygen). Alotin luomalla avaimen komennolla `ssh-keygen -t rsa -b 4096`.

![kuva](https://github.com/user-attachments/assets/8db308b5-57d2-49e4-be07-0e353cd24d21)

Sitten kopioin ohjeiden mukaisesti avaimella. Näin avaimesta tulee authorisoitu avain.

![kuva](https://github.com/user-attachments/assets/90f3b89a-71d6-4330-9c1e-3afba195b494)

Nyt minun ei tarvinnut kirjautua salasanalla palvelimeni käyttäjään.

![kuva](https://github.com/user-attachments/assets/8d4e6e35-38b4-4d5b-8f8e-7c2ee4135604)

Tarkistin vielä kaiken varalta uudelta komentoriviltä, että kirjautuminen onnistuu ilman salasanaa myös uudelleen, ja tämäkin onnistui.

![kuva](https://github.com/user-attachments/assets/61285a95-bf53-4925-a6c6-22dcee7c09b6)

## d) DNS-tiedot "host" ja "dig"-komennoilla

Tiistai 24.9.2024 klo 14.34

`Tehtävänanto: Tutki jonkin nimen DNS-tietoja 'host' ja 'dig' -komennoilla. Käytä kumpaakin komentoa kaikkiin nimiin ja vertaa tuloksia. Katso man-sivulta, miten komennot toimivat - esimerkiksi miten 'dig' näyttää kaikki kentät. Analysoi tulokset. Etsi tarvittaessa uusia lähteitä haastaviin kohtiin. Sähköpostin todentamiseen liittyvät SPF ja DMARC -tietojen yksityiskohdat on jätetty vapaaehtoiseksi lisätehtäväksi. Tutkittavat nimet:

-  Oma domain-nimesi. Vertaa tuloksia nimen vuokraajan (namecheap.com, name.com...) weppiliittymässä näkyviin asetuksiin.

- Jonkin pikkuyrityksen, kerhon tai yksittäisen henkilön weppisivut. (Ei kuitenkaan kurssikaverin tällä viikolla vuokrattua nimeä).

- Jonkin suuren ja kaikkien tunteman palvelun tiedot.

Pidin hetken taukoa a-tehtävän onnistumisen jälkeen.`

Lähdin aloittamaan tehtävää tarkastamalla mahdollisien ohjelmien latauksen tarvetta. Komentoa `dig` käyttämiseen tarvittavan `dnsutils`-ohjelman olinkin jo ladannut,     sillä käytin ´dig´-komentoa a-tehtävässä. Selvitin kuitenkin `man dig`-komennolla `dig`-komennon käyttötarkoituksen. Komennolla voidaan tutkia DNS-serverien lähettämää vastausta kun niitä haetaan komentoriviltä. Komennolla ´dig -h´ saadaan yhteenveto käytettävistä komennoista. 

Kokeilin ensin komentoa omiin `peklev.com`-sivuihin, jonka olinkin jo aikasemmin tehnyt a-tehtävässä. 

![kuva](https://github.com/user-attachments/assets/8673daf7-e576-4aaa-a8d9-834d3626965e)

Etsin lisätietoa siitä, mitä kaikkea tietoa ´dig´-komennon vastauksessa annetaan ja löysin Digitaloceanin (https://www.digitalocean.com/community/tutorials/how-to-retrieve-dns-information-using-dig) ja Matthias Geniarin sivuilta (https://ma.ttias.be/making-full-use-of-dig-in-linux/) apua tiedon tarkastamisessa.

- `GOT ANSWER`-kohdan alla saadaan tieto statuksesta, joka tässä tapauksessa oli `NOERROR` eli onnistunut kysely.

- `flags`- osiossa voi olla monia vastauksia ja niiden merkitys riippuu niiden arvosta:

      - AA tarkoittaa auktoritatiivistä vastausta eli kyselyyn vastasi auktoritatiivinen nimipalvelin.

      - RD tarkoittaa, että rekursiota on pyydetty.

      - RA tarkoittaa, että rekursio on saatavilla

      - QR tarkoittaa yleisesti kyselyn vastausta, joka näkyi myös omassa ´dig´-kyselyssäni.

- `QUESTION SECTION`: ´dig´-kysely pyytää isäntänimeä, joka tässä tapauksessa oli peklev.com ja kysyy myös tietoa A-tietueesta.

- `ANSWER SECTION`: ´dig´-kyselyn palauttamat tietueet, joka usein on tärkein tieto kyselyn tekijälle. Vastauksena ´dig´-kysely palautti IP-osoitteeni ja kyselyyn kestäneen ajan.

- Omassa haussani ei näkynyt `AUTHORITY SECTION`, joka kertoisi auktoriset palvelimet, jotka ylläpitävät domainnimen tietueita. Tällaisia minulla ei ollut.

- Myöskään `ADDITIONAL SECTION` ei näkynyt oman sivuni ´dig´-kyselyssä, mutta se voi sisältää mahdollisia lisätietoja, joita saatetaan välittää vastauksen mukana.

Vertaillakseni vastauksia, kokeilin ´dig´-kyselyä myös alidomainilleni, joihin sain hyvin samanlaiset vastaukset. Molemmissa näkyy IP-osoitteeni 172.234.116.108.

![kuva](https://github.com/user-attachments/assets/d5ea3ef1-a511-4175-af26-0abd8c3fa836)

![kuva](https://github.com/user-attachments/assets/d77a44c7-20c6-4972-89ce-b6d8fc8641d2)

Tein vertailuksi ´dig´-kyselyn `store.steampowered.com`, sekä `lautapeliseura.fi`-sivustoille. Kummastakin hausta näkyi hyvin paljolti samanlaista teitoa kuin omilta sivuiltani.

![kuva](https://github.com/user-attachments/assets/5d87b809-01f9-4ca4-b5a0-516db172c175)

![kuva](https://github.com/user-attachments/assets/46b9ca61-5649-48be-a1de-e68aa02742b4)



Myös `host`-komentoa olin jo ehtinyt käyttää aikasemmassa tehtävässä, joten sitäkään varten ei minun tarvinnut ladata ohjelmaa erikseen.

Tein `host`-kyselyn kaikkiin domaineihini sekä vielä Steam-verkkosivuun. `host peklev.com`-kyselyn olinkin jo tehnyt a-tehtävässä.

![kuva](https://github.com/user-attachments/assets/6c307c82-2009-4898-bff0-7f7e3568ec36)

![kuva](https://github.com/user-attachments/assets/cb8f5e13-a6cf-45d1-b0b5-9992fc56b1ab)

Toisin kuin CNAME-tietueena tekemäni alidomani `kuva.peklev.com`, A-tietueena tekemäni ìnfo.peklev.com` antoi ainoastaan IP-osoitteeni vastauksena, mutta ei MX-tietuetta.

![kuva](https://github.com/user-attachments/assets/04a3273f-a70a-4563-b36e-f3ffe5d3e2d1)

Viimeiseksi tein `host`-kyselyn ´store.steampowered.com`-sivustolle, joka antoi ainoastaan sivun IP-osoitteen vastaukseksi. Kokeilin myös kyselyä `lautapeliseura.fi`-sivustolle, joka antoi myös MX-tietueen. MX-tietue kertoo mihin palvelimiin sähköposti tulisi toimittaa verkkotunnusta varten.

![kuva](https://github.com/user-attachments/assets/c8d629c0-86c6-423d-9fcd-a30d65307694)

![kuva](https://github.com/user-attachments/assets/e3eab5ec-38bb-4681-91f8-1dcafe74181d)

Lopetus tiistai 24.9.2024 klo 15.56.

## Lähteet



Markup Validation Service https://validator.w3.org/

Miten luon A-tietueen? https://help.one.com/hc/fi/articles/360000799298-Miten-luon-A-tietueen

How do I create a CNAME record? https://help.one.com/hc/fi/articles/360000803517-How-do-I-create-a-CNAME-record

Namecheap: How to Create a Subdomain for my Domain https://www.namecheap.com/support/knowledgebase/article.aspx/9776/2237/how-to-create-a-subdomain-for-my-domain/

SSH Academy: What is SSH Public Key Authentication? https://www.ssh.com/academy/ssh/public-key-authentication#setting-up-public-key-authentication-for-ssh

SSH Academy: Creating an SSH Key Pair for User Authentication https://www.ssh.com/academy/ssh/keygen

DigitalOcean: How to Retrieve DNS Information Using Dig https://www.digitalocean.com/community/tutorials/how-to-retrieve-dns-information-using-dig

Matthias Geniar: Making Full Use Of ‘Dig’ In Linux  https://ma.ttias.be/making-full-use-of-dig-in-linux/
  
