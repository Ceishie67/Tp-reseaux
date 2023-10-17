# TP2 : Ethernet, IP, et ARP

![Alt text](image.png)

## I. Setup IP

### 🌞 Mettez en place une configuration réseau fonctionnelle entre les deux machines

mon IP : 10.10.10.42

Masque de sous réseaux :  255.255.255.252

IP de l'autre ordi : 10.10.10.43

Masque de sous réseaux :  255.255.255.252

address Broadcast : 10.10.10.44

### 🌞 Prouvez que la connexion est fonctionnelle entre les deux machines

````
PS C:\Users\champ> ping 10.10.10.43

Envoi d’une requête 'Ping'  10.10.10.43 avec 32 octets de données :
Réponse de 10.10.10.43 : octets=32 temps=1 ms TTL=64
Réponse de 10.10.10.43 : octets=32 temps<1ms TTL=64
Réponse de 10.10.10.43 : octets=32 temps<1ms TTL=64
Réponse de 10.10.10.43 : octets=32 temps<1ms TTL=64

Statistiques Ping pour 10.10.10.43:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 1ms, Moyenne = 0ms
````

### 🌞 Wireshark it
 [TP-réseaux2 capture](./pcapng)


