%title: JMeter
%author: xavki

# JMeter : Scrap vers bdd sql


<br>


* combinaison des dernières vidéos :
		* scraping de pages : date / url / status
		* chargement en bdd postgres

<br>


0- Création d'une database postgres
		* create user (admin/admin)
		* create database (jmeter)
		* create table (scrap_xavki)


```
create user admin encrypted password 'admin';
create database jmeter owner to admin;
create table scrap_xavki (timer varchar(255), path varchar(255), status varchar(255));
```
		

<br>


1- Thread : 1 user / loop 1

<br>


2- connexion au serveur postgres
		* jdbc connexion configuration
				* variable pool : postgres
				* database url : jdbc:postgresql://192.168.60.3:5432/jmeter
				* ajout driver jdbc postgres
				* admin / admin

----------------------------------------------------------------------------------------------

# Actions

<br>


3- création du sampler : HTTP Request ( https://xavki.blog - GET / )


<br>


4- PostProcessor : regular expression extractor
  - Body
  - name : urls
  - href="https://xavki.blog/(.*)/"\S
  - template : $1$
  - match : -1
  - default : NOLINK

<br>


5- ForEach controller
		* urls / url

<br>


6- HTTP Request 
		* ${url}

7- PostProcessor
		* code status
		* (.*)
		* pas de vide

<br>


7- JDBC Request
		* name pool : postgres
		* query type : callable statement
		* requête : 

```
INSERT INTO scrap_xavki VALUES ('${__time(yyyyMMdd-HHmmss)}','${url}','${status_1}');
```

8- View result tree


