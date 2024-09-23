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


## b) Alidomain





## Lähteet



Markup Validation Service https://validator.w3.org/

Miten luon A-tietueen? https://help.one.com/hc/fi/articles/360000799298-Miten-luon-A-tietueen

How do I create a CNAME record? https://help.one.com/hc/fi/articles/360000803517-How-do-I-create-a-CNAME-record

Namecheap: How to Create a Subdomain for my Domain https://www.namecheap.com/support/knowledgebase/article.aspx/9776/2237/how-to-create-a-subdomain-for-my-domain/

  
