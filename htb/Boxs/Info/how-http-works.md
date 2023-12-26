## How HTTP works

- Analogy

Think that you are in restaurant and you want to do a command to restaurant server this the restaurant menu

Here in Web you are the `Client` ,the menu is the web page where you are at the moment and you make a order to a `server` and you can make also multiple order (mp4 files, png, html  files) .It also possible for `server` to receive multiples orders from multiples `Client` and sand any command answers at any `Client`


- So **HTTP** = **stateless** ?
Yes `HTTP` is `stateless` because any `HTTP request` is independant with others `request` and the `server` don't keep in memory historical of `back request`


- **URL vs URI**
URL and URI are all two the identificator to locate of web ressources

`URL` : Uniform Ressource Locator (Web address to identify the location of a ressources in internet like image, or web page or downloaded file)
URL doing understand any things : Access path to ressources, domain name,protocol used (http, https, ftp),and the request parameter

Ex: https://google.com/www.google.com/search?q=chat
      1		2			3	4

1- Protocole
2- Domain name
3- path
4- parameter