%title: JMeter
%author: xavki

-> JMeter : Post Processor <-
========


<br>


* Post Processor : traitement des datas reçues

* ex : application d'une regex pour parser la page

<br>


1- Thread : 10 users - loop 1

<br>


2- création du sampler : HTTP Request ( https://xavki.blog - GET / )

<br>


3- HTTP request > add post processor : regular expression extractor
  - Body
  - name : urls
  - href="https://xavki.blog/(databases|awk)/"
  - template : $1$
  - match : -1
  - default : NOLINK

<br>


4- Debug - Post Processor

<br>


5- Insert Parent > ForEach Controller
	- input : urls
	- output : url
	- coche add before

<br>


6- HTTP request 
	- name : ${url}
	- path : ${url}

7- view result tree

