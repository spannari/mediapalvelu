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

12. Lisää Apache bootissa käynnistettäviin sovelluksiin: 
```$ sudo systemctl enable httpd```

13. Lisää Apache bootissa käynnistettäviin sovelluksiin: 
```$ sudo systemctl enable httpd```

13. Lisää Apache bootissa käynnistettäviin sovelluksiin: 
```$ sudo systemctl enable httpd```

13. Lisää Apache bootissa käynnistettäviin sovelluksiin: 
```$ sudo systemctl enable httpd```

13. Lisää Apache bootissa käynnistettäviin sovelluksiin: 
```$ sudo systemctl enable httpd```


