%title: JMeter
%author: xavki

# JMeter : Authentication 


<br>



* example app :

```
docker run -d --name httpbin -p 80:80 kennethreitz/httpbin

http://127.0.0.1/basic-auth/user/passwd

user : user  && password: passwd
```

<br>


* config element : HTTP Authorization Manager
		* ajout url 
		* user et password
		* mechanism : BASIC_DIGEST
		* attention : enable/disable (clic droit)

* ajout requête : http request
		* http://127.0.0.1/basic-auth/user/passwd

* ajout d'un listener
