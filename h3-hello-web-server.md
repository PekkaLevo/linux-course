# h3 Hello Web Server


## x) Lue ja tiivistä



### Name-based Virtual Host Support

- IP-based virtual hosting käyttää Ip-osoitetta oikean palvelimen määrittämiseen. Jokainen palvelin tarvitsee siten oman Ip-osoitteen.

- Name-based virtual hosting jakaa Ip-osoitteen ja konfiguroivat DNS-palvelimen oikeaan Ip-osoitteeseen ja konfiguroida Apache-palvelin tunnistamaan verkkotunnuksia.

- Name-based virtual hosting:n avulla vähennetään Ip-osoitteita määrää, joka on suositeltavaa, ellei erikseen tarvita Ip-pohjaista isännöintiä.


### Karvinen 2018: Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address

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

## a) Testaus ja Apachen asennus

- 
