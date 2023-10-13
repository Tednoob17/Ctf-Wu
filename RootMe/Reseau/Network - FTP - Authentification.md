This Challenge is proposed by [Rootme Platform](https://www.root-me.org/) 
*Author* : [g0uz](https://www.root-me.org/g0uZ?lang=fr) 
*Chall Link* : [FTP - Authentification](https://www.root-me.org/fr/Challenges/Reseau/FTP-Authentification) 
*File* : [file](challenge01.root-me.org/reseau/ch1/ch1.pcap)  
Means: [RFC](https://repository.root-me.org/RFC/EN%20-%20rfc854.txt?_gl=1*ir4yt6*_ga*NDIxNzIzMDczLjE2OTIzODQyMzQ.*_ga_SRYSKX09J7*MTY5MzYyMTE2MS44LjEuMTY5MzYyMzc2My4wLjAuMA..) 
Date: 02/09/2023

It's pcap file let's go open wireshark and open this file with our software 
![net](./img/network1.png)
I see that the numbers of packets is not long so the decide to follow the TCP Stream
Right click 
Follow > TCP Stream 
![stream](img/stream.png)
And we can see the credentials cdts3500:cdts3500

Flag: cdts3500
