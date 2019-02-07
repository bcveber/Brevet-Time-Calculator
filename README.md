# Brevet-Time-Calculator
Randonneurs USA cycling brevet (opening and closing) time calculator

## Info
Author: Brian Veber, contact: bveber@uoregon.edu

## About
* <b>Client</b> - AJAX, jQuery, UI (Flask-Login, Flask-WTF), CSS Consumers using jQuery and php
* <b>Server</b> - Flask-based backend. Storage using MongoDB (NoSQL)
* <b>Protocols</b> - HTTP, TCP/UDP, IP
* <b>User session management</b>
* <b>RESTful API integration</b>
* <b>Basic HTTP and token-based authentication</b>
* <b>Deployed using Docker</b>
* <b>Git versioning</b>

## About Brevets
Randonneuring is long distance non-competive cycling. A cycling event for randonneurs is known as a "brevet." "Controls" are checkpoints within a brevet. Thus, this calculator calculates the open and close times for the entire brevet and its individual controls. 

## How to run
Download the program and add your credentials.ini file into DockerMongo folder. On the command line, enter `docker-compose build` and then `docker-compose up` once build is completed. From there, access your localhost and the respective port you want to visit mentioned below.


## Rundown
To begin using the features of the program, the user can first go to `localhost:5002` where they can find the calculator to enter open/close times with distances and submit and/or diplsay them. Next, the user can go to `localhost:5001` (the homepage) where they can either register, login, or logout. User should first register an account, and the proceed to login. Upon login success the user will recieve a token for which they can access the APIs. User can also have <b>remember me</b> enabled for the session. <b>CSRF protection</b> is enabled. These are the API's the program supports:

```
(port should be 5001)
* "http://<host:port>/listAll" should return all open and close times in the database
* "http://<host:port>/listOpenOnly" should return open times only
* "http://<host:port>/listCloseOnly" should return close times only

* "http://<host:port>/listAll/csv" should return all open and close times in CSV format
* "http://<host:port>/listOpenOnly/csv" should return open times only in CSV format
* "http://<host:port>/listCloseOnly/csv" should return close times only in CSV format

* "http://<host:port>/listAll/json" should return all open and close times in JSON format
* "http://<host:port>/listOpenOnly/json" should return open times only in JSON format
* "http://<host:port>/listCloseOnly/json" should return close times only in JSON format

* "http://<host:port>/listOpenOnly/csv?top=3" should return top 3 open times only (in ascending order) in CSV format 
* "http://<host:port>/listOpenOnly/json?top=5" should return top 5 open times only (in ascending order) in JSON format
* "http://<host:port>/listCloseOnly/csv?top=6" should return top 5 close times only (in ascending order) in CSV format
* "http://<host:port>/listCloseOnly/json?top=4" should return top 4 close times only (in ascending order) in JSON format
```

These APIs require your token. To access, take the link of the API above and add `?token=<your token>` to the end of the link. All APIs can be displayed on `localhost:5000`. Once the user is done, they can then logout of their session. 

## Calculator Rules
The km you enter should not exceed your distance significantly. Open to close times on the first 0km will have 1 hour added. Km values cannot be negative. Values less than 20% of the original distance will be rounded down. Values less than the distance will be treated as normal.

## Examples

* <b>Calculator:</b>

![alt text](https://github.com/bcveber/Brevet-Time-Calculator/blob/master/examples/calculator.png)

* <b>Home Page:</b>

![alt text](https://github.com/bcveber/Brevet-Time-Calculator/blob/master/examples/homePage.png)

* <b>Register Success:</b>

![alt text](https://github.com/bcveber/Brevet-Time-Calculator/blob/master/examples/register.png)

* <b>Login Page:</b>

![alt text](https://github.com/bcveber/Brevet-Time-Calculator/blob/master/examples/login.png)

* <b>Login Success Token:</b>

![alt text](https://github.com/bcveber/Brevet-Time-Calculator/blob/master/examples/loginSuccessToken.png)

* <b>REST API failure without token:</b>

![alt text](https://github.com/bcveber/Brevet-Time-Calculator/blob/master/examples/apiTokenFailure.png)

* <b>REST API access success with token:</b>

![alt text](https://github.com/bcveber/Brevet-Time-Calculator/blob/master/examples/apiWithTokenSuccess.png)
