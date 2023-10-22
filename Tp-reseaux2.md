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
 [capture Wireshark](./TP-réseaux2capture.pcapng)

# II. ARP my bro

### 🌞 Check the ARP table
 
```
arp -a
``` 
Adresse MAC de mon PC fixe :  50-3e-aa-cf-7a-9e

Adresse MAC du gateway du wifi de ma maison : 7c-c1-77-5e-59-f0

### 🌞 Manipuler la table ARP
```
arp -d
```
avant suppression:

Interface : 192.168.1.45 --- 0x6

  Adresse Internet      Adresse physique      Type

  192.168.1.1           7c-c1-77-5e-59-f0     dynamique
  
  192.168.1.11          18-1e-78-84-c1-33     dynamique
  
  192.168.1.13          20-df-b9-3a-83-85     dynamique
  
  192.168.1.19          74-72-b0-23-aa-da     dynamique
  192.168.1.20          50-3e-aa-cf-7a-9e     dynamique
  
  192.168.1.33          cc-d3-c1-16-48-23     dynamique
  
  192.168.1.255         ff-ff-ff-ff-ff-ff     statique
  
  224.0.0.2             01-00-5e-00-00-02     statique
  
  224.0.0.22            01-00-5e-00-00-16     statique
  
  224.0.0.251           01-00-5e-00-00-fb     statique
  
  224.0.0.252           01-00-5e-00-00-fc     statique
  
  
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  
  239.255.255.251       01-00-5e-7f-ff-fb     statique
  
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique

Interface : 192.168.159.1 --- 0x15
  
  Adresse Internet      Adresse physique      Type
  
  192.168.159.254       00-50-56-fc-cf-e7     dynamique
  
  192.168.159.255       ff-ff-ff-ff-ff-ff     statique
  
  224.0.0.2             01-00-5e-00-00-02     statique
  
  224.0.0.22            01-00-5e-00-00-16     statique
  
  224.0.0.251           01-00-5e-00-00-fb     statique
  
  224.0.0.252           01-00-5e-00-00-fc     statique
  
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  
  239.255.255.251       01-00-5e-7f-ff-fb     statique
  
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique

Interface : 192.168.80.1 --- 0x17
  
  Adresse Internet      Adresse physique      Type
  
  192.168.80.254        00-50-56-e0-6a-c7     dynamique
  
  192.168.80.255        ff-ff-ff-ff-ff-ff     statique
  
  224.0.0.2             01-00-5e-00-00-02     statique
  
  224.0.0.22            01-00-5e-00-00-16     statique
  
  224.0.0.251           01-00-5e-00-00-fb     statique
  
  224.0.0.252           01-00-5e-00-00-fc     statique
  
  239.255.255.250       01-00-5e-7f-ff-fa     statique
  
  239.255.255.251       01-00-5e-7f-ff-fb     statique
  
  255.255.255.255       ff-ff-ff-ff-ff-ff     statique
