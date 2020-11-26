%title: JMeter
%author: xavki

# JMeter : test de FTP


<br>


* création rapide d'un ftp

```
docker run -itd --name ftpd_server -p 21:21 -p 30000-30009:30000-30009 -v files_volume_name_here:/var/www/html -e "PUBLICHOST=localhost" stilliard/pure-ftpd:hardened
```

* création du user ftp

```
docker exec -ti ftpd_server /bin/bash
pure-pw useradd xavki -f /etc/pure-ftpd/passwd/xavki.passwd -m -u ftpuser -d /var/www/html
chown -R ftpuser /var/www
```

* test filezilla


-----------------------------------------------------------


# Test Jmeter

