**Virtuaalipalvelimen ottaminen käyttöön**

1. Kirjaudu sisään palvelimelle saamillasi tunnuksilla: 
```$ ssh root@SERVER_IP_ADDRESS```

2. Luo uusi käyttäjä (vaihda haluamasi nimi kohtaan DEMO): 
```# adduser demo```

3. Aseta käyttäjälle salasana (vaihda luomasi käyttäjä kohtaan DEMO): 
```# passwd demo```

4. Seuraavaksi liitetään luotu käyttäjä superuser-ryhmään: 
```# gpasswd -a demo wheel```

5. Kirjaudu ulos, ja loggaa sisään uudestaan luomanasi käyttäjänä: 
```# exit```

```$ ssh demo@SERVER_IP_ADDRESS```

**LAMP-asennus**

1. Ensimmäiseksi tyhjennetään asennuspalvelun cache: 
```$ sudo yum clean all```

2. Seuraavaksi päivitetään viimeisimmät versiotiedot: 
```$ sudo yum -y update```

3. Asenna Apache: 
```$ sudo yum -y install httpd```

4. Aukaistaan HTTP ja HTTPS -portit palomuurista: 
```$ sudo firewall-cmd --permanent --add-port=80/tcpl```
```$ sudo firewall-cmd --permanent --add-port=443/tcpl```
lataa palomuuri uusiksi
```sudo firewall-cmd --reload```

5. Käynnistä Apache: 
```$ sudo systemctl start httpd```

6. Lisää Apache bootissa käynnistettäviin sovelluksiin: 
```$ sudo systemctl enable httpd.service```

7. Asennetaan seuraavaksi MySQL (MariaDB): 
```$ sudo yum install mariadb-server mariadb```

8. Lisää MySQL bootissa käynnistettäviin sovelluksiin: 
```$ sudo systemctl start mariadb```

9. Seuraavaksi tehdään tietokannasta turvallisempi: 
```$ ssudo mysql_secure_installation```
Aseta uusi pääkäyttäjä-salasana tietokantapalvelulle. Älä käytä samaa kuin kahdessa aikaisemmassa tapauksessa. Vastaa muihin kysymyksiin ENTER-painalluksella.

10. Lisää MySQL bootissa käynnistettäviin sovelluksiin: 
```$ sudo systemctl enable mariadb.service```

11. Asennetaan php ja php-mysql: 
```$ sudo yum install php php-mysql```

12. Käynnistetään Apache uudestaan: 
```$ sudo systemctl restart httpd.service```

13. Asennetaan nano:  
```$ sudo yum install nano```

14. Tehdään testiskripti php:lle: 
  ```$ sudo nano /var/www/html/info.php```
  Kirjoita seuraava rivi editoriin ja tallenna
  ```<?php phpinfo(); ?>```

15. Puhkaistaan sopivat reiät palomuuriin: 

```sudo firewall-cmd --permanent --zone=public --add-service=http``` 

```sudo firewall-cmd --permanent --zone=public --add-service=https```

```sudo firewall-cmd --reload```

testaa toiminta selaimella ```http://your_server_IP_address/info.php```

poista testitiedosto turvallisuussyistä ```$ sudo rm /var/www/html/info.php```

Seuraavaksi asennetaan [Wordpress](https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-on-centos-7)

FFMPEGIN asennus https://gist.github.com/mustafaturan/7053900 (toimivuus testaamatta)
