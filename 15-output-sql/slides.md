%title: JMeter
%author: xavki

-> JMeter :  <-
========


<br>
* combinaison des dernières vidéos :
		* scraping de pages
		* chargement en bdd postgres

<br>
0- Création d'une database postgres
		* create user
		* create database owner to 
		* create table
		

<br>
1- Thread : 10 users - loop 1

<br>
2- connexion au serveur postgres
		* jdbc connexion configuration
				* variable pool : postgres
				* database url : jdbc:postgresql://192.168.60.3:5432/xavier
				* ajout driver jdbc postgres
				* user /password

<br>
3- création du sampler : HTTP Request ( https://xavki.blog - GET / )

<br>
4- HTTP request > add post processor : regular expression extractor
  - Body
  - name : urls
  - href="https://xavki.blog/(.*)/"\S
  - template : $1$
  - match : -1
  - default : NOLINK

<br>
5- Debug - Post Processor

<br>
6- ForEach controller
		* urls / url

<br>
7- JDBC Request
		* name pool : postgres
		* query type : callable statement
		* requête : INSERT INTO table1 VALUES ('${url}','test');

8- View result tree


