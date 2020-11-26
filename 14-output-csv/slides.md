%title: JMeter
%author: xavki

## JMeter : PostProcessor > CSV


<br>


* récupérer les résultats généré par les vidéos précédentes

* injecter en format csv

<br>


1- Thread : 1 user - loop 1

<br>


2- création du sampler : HTTP Request ( https://xavki.blog - GET / )

<br>


3- PostProcessor : regular expression extractor
  - Body
  - name : urls
  - href="https://xavki.blog/(.*)/"\S
  - template : $1$
  - match : -1
  - default : NOLINK

4- Debug - Post Processor

-------------------------------------------------------------------------------------

## JMeter : extract CSV


<br>


5- InsertParent - ForEach Controller
		* urls/url

6- HTTP Request :
		* name : ${url} 
		* /${url}/

<br>


7- PostProcessor 
		* response code
		* variable : status
		* (.*)
		* $1$
		* -1
		* coche use empty

<br>


8- BeanShell Processor

* reset interpreter : false

```
result = vars.get("url") + "," + vars.get("status_1");
log.info(result);
vars.put("result", result);
```

<br>


9- JSR223 PostProcessor

* language : groovy

```
def file = new File("/home/oki/result.csv");
file << vars.get("result") + "\n";
vars.put("result";"");
```

<br>


10 - view result tree
