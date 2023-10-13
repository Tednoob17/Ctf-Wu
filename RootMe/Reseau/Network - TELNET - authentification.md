This Challenge is proposed by [Rootme Platform](https://www.root-me.org/) 
*Author* : [g0uz](https://www.root-me.org/g0uZ?lang=fr) 
*Chall Link* : [Telnet - Authentification](https://www.root-me.org/fr/Challenges/Reseau/TELNET-authentification?action_solution=proposer&lang=fr)  
*File* : [file](challenge01.root-me.org/reseau/ch2/ch2.pcap)  
Means: [RFC](https://repository.root-me.org/RFC/EN%20-%20rfc854.txt?_gl=1*ir4yt6*_ga*NDIxNzIzMDczLjE2OTIzODQyMzQ.*_ga_SRYSKX09J7*MTY5MzYyMTE2MS44LjEuMTY5MzYyMzc2My4wLjAuMA..) 
Date: 03/09/2023
#### Énoncé

Retrouvez le mot de passe de l’utilisateur dans cette capture réseau de session TELNET.


Let's go to open this pcap file with wireshark
![net1](net1.png)

Like means we can see that in this file the telnet can be a key, so i select the first Telnet packet  and follow tcp stream 
![net2](img/net2.png)

And we can see password: user

Flag: user
