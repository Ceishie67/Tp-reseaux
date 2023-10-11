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