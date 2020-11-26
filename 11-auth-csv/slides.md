%title: JMeter
%author: xavki

# JMeter : CSV config et Auth


<br>



* example app :

```
docker run -d --name httpbin -p 80:80 kennethreitz/httpbin

http://127.0.0.1/basic-auth/user/passwd

user : user  && password: passwd
```

<br>


* création d'un fichier CSV (exemple)
		* format = path,user,password

```
basic-auth/user/password,user,password
basic-auth/xavki/pppsss,xavki,pppsss
basic-auth/user/dswp,user,dswp
```


-------------------------------------------------------------------------

# PLAN : settings


<br>


* configuration thread : nb users = nb lignes

<br>


* CSV data set config :
		* filename : location
		* variables : path,u,p
		* delimiter : ,

<br>


* HTTP Authorization Manager :
		* url : http://127.0.0.1/${path}
		* username : ${u}
		* password : ${p}
		* mechanism : BASIC_DIGEST

<br>


* HTTP Request :
		* protocol : http
		* url : 127.0.0.1
		* path : /${path}

<br>


* Listener : View Results Tree
