# Tp-réseaux 1 
![Alt text](image.png)

# I.exploration en solo

# 1 Affichage d'informations sur la pile TCP/IP locale

### 🌞 Affichez les infos des cartes réseau de votre PC 

```
ipconfig
```
nom : Carte réseau sans fil Wi-Fi 2

adresse MAC : 2C-3B-70-6B-D7-F1

adresse IP : 10.33.48.136

nom : Carte Ethernet Connexion réseau Bluetooth 2

adresse MAC : 2C-3B-70-6B-D7-F0

adresse IP : none

### 🌞 Affichez votre gateway

```
ipconfig /all
```
adresse IP Passerelle : 10.33.51.254

### 🌞 Déterminer la MAC de la passerelle

```
arp -a 
```
adresse MAC Passerelle : 7c-5a-1c-cb-fd-a4

# En graphique (GUI : Graphical User Interface)

### 🌞 Trouvez comment afficher les informations sur une carte IP (change selon l'OS)

```
Paneau de configuration-réseau et Internet-Centre réseau et partage-Détail
```

adresse IP : 10.33.48.136

adresse MAC : 2C-3B-70-6B-D7-F1

adresse IP Passerelle : 10.33.51.254

# 2. Modifications des informations 

## A. Modification d'adresse IP (part 1)

### 🌞 Utilisez l'interface graphique de votre OS pour changer d'adresse IP :

adresse IP modifier : 10.33.48.12

### 🌞 Il est possible que vous perdiez l'accès internet.

Il est possible que on est pris la même IP qu'une autre personne

# II. Exploration locale en duo

## 1. Prérequis

deux PCs avec ports RJ45

un câble RJ45

firewalls désactivés sur les deux PCs

## 2. Câblage

Ok c'est la partie tendue. Prenez un câble. Branchez-le des deux côtés. Bap.

## 3. Modification d'adresse IP

### 🌞 Modifiez l'IP des deux machines pour qu'elles soient dans le même réseau

### 🌞 Vérifier que les deux machines se joignent
```
ping 10.10.10.1
```
PS C:\Users\champ> ping 10.10.10.1

Envoi d’une requête 'Ping'  10.10.10.1 avec 32 octets de données :
Réponse de 10.10.10.1 : octets=32 temps=1 ms TTL=64

Réponse de 10.10.10.1 : octets=32 temps<1ms TTL=64

Réponse de 10.10.10.1 : octets=32 temps<1ms TTL=64

Réponse de 10.10.10.1 : octets=32 temps<1ms TTL=64


Statistiques Ping pour 10.10.10.1:

Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),

Durée approximative des boucles en millisecondes :

Minimum = 0ms, Maximum = 1ms, Moyenne = 0ms

### 🌞 Déterminer l'adresse MAC de votre correspondant
```
arp -a
```
00-d8-61-8a-6e-78

## 4. Petit chat privé

### 🌞 sur le PC client
```
.\nc.exe 10.10.10.1 8888
```
### 🌞 Visualiser la connexion en cours
```
netstat -a -n -b

Connexions actives
```
## 5. Firewall

### 🌞 Activez et configurez votre firewall

ne marche pas

## 6. Utilisation d'un des deux comme gateway
```
PS C:\Users\champ> ping 1.1.1.1
Envoi d’une requête 'Ping'  1.1.1.1 avec 32 octets de données :
Réponse de 1.1.1.1 : octets=32 temps=37 ms TTL=56
Réponse de 1.1.1.1 : octets=32 temps=11 ms TTL=56
Réponse de 1.1.1.1 : octets=32 temps=13 ms TTL=56
Réponse de 1.1.1.1 : octets=32 temps=11 ms TTL=56

Statistiques Ping pour 1.1.1.1:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 11ms, Maximum = 37ms, Moyenne = 18ms
```
### 🌞 Prouver que la connexion Internet passe bien par l'autre PC
```
PS C:\Users\champ> tracert 1.1.1.1
Détermination de l’itinéraire vers one.one.one.one [1.1.1.1]
avec un maximum de 30 sauts :

  1    <1 ms    <1 ms    <1 ms  MakOS [10.42.0.1]
  2     4 ms     2 ms     8 ms  _gateway [10.33.51.254]
  3     8 ms     3 ms     2 ms  237.252.159.77.rev.sfr.net [77.159.252.237]
  4     3 ms     3 ms     3 ms  108.97.30.212.rev.sfr.net [212.30.97.108]
  5     5 ms     4 ms     7 ms  213.212.192.77.rev.sfr.net [77.192.212.213]
  6    12 ms    12 ms    13 ms  12.148.6.194.rev.sfr.net [194.6.148.12]
  7    15 ms    11 ms    11 ms  12.148.6.194.rev.sfr.net [194.6.148.12]
  8    11 ms    13 ms    11 ms  141.101.67.48
  9    11 ms    11 ms    13 ms  172.71.124.4
 10    14 ms    12 ms    13 ms  one.one.one.one [1.1.1.1]

Itinéraire déterminé.
```

# III. Manipulations d'autres outils/protocoles côté client

## 1. DHCP

### 🌞Exploration du DHCP, depuis votre PC
```
PS C:\Users\champ> ipconfig /all
```
serveur DHCP :  10.33.51.254

## 2. DNS

### 🌞** Trouver l'adresse IP du serveur DNS que connaît votre ordinateur**
```
PS C:\Users\champ> ipconfig /all
```
serveur DNS : 10.33.10.2

### 🌞 Utiliser, en ligne de commande l'outil nslookup (Windows, MacOS) pour faire des requêtes DNS à la main

```
nslookup google.com 8.8.8.8
```
Serveur :   dns.google

Address:  8.8.8.8

Réponse ne faisant pas autorité :

Nom :    google.com

Addresses:  2a00:1450:4007:818::200e

 142.250.179.110
```
nslookup ynov.com 10.33.10.2
```
DNS request timed out.
    timeout was 2 seconds.

Serveur :   UnKnown

Address:  10.33.10.2
```
nslookup 231.34.113.12
```
DNS request timed out.
    timeout was 2 seconds.

Serveur :   UnKnown

Address:  10.33.10.2

DNS request timed out.
    timeout was 2 seconds.

*** Le délai de la requête sur UnKnown est dépassé.
```
nslookup 78.34.2.17
```

DNS request timed out.
    timeout was 2 seconds.

Serveur :   UnKnown

Address:  10.33.10.2

DNS request timed out.
    timeout was 2 seconds.

*** Le délai de la requête sur UnKnown est dépassé.

# IV. Wireshark 

### 🌞 Utilisez le pour observer les trames qui circulent entre vos deux carte Ethernet. Mettez en évidence :