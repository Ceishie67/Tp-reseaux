# TP5 : TCP, UDP et services réseau
![Alt text](image.png)

## 0. Prérequis

➜ Pour ce TP, on va se servir de VMs Rocky Linux quand des VMs seront nécessaires. On va en faire plusieurs, n'hésitez pas à diminuer la RAM (512Mo ou 1Go devraient suffire). Vous pouvez redescendre la mémoire vidéo aussi.
➜ Si vous voyez un 🦈 c'est qu'il y a une capture PCAP à produire et à mettre dans votre dépôt git de rendu
➜ L'emoji 🖥️ indique une VM à créer. Pour chaque VM, vous déroulerez la checklist suivante :


 Créer la machine (avec une carte host-only)

 Définir une IP statique à la VM

 Donner un hostname à la machine

 Utiliser SSH pour administrer la machine

 Remplir votre fichier hosts, celui de votre PC, pour accéder au VM avec un nom

 Dès que le routeur est en place, n'oubliez pas d'ajouter une route par défaut aux autres VM pour qu'elles aient internet


Toutes les commandes pour réaliser ces opérations sont dans le mémo Rocky. Aucune de ces étapes ne doit figurer dan le rendu, c'est juste la mise en place de votre environnement de travail.
## I. First steps

### 🌞 Déterminez, pour ces 5 applications, si c'est du TCP ou de l'UDP

titanfall 2 : IP : 10.33.71.246 port serveur : 37005  port local : 38115  UDP

discord :  IP : 85.195.105.222 port serveur : 55561  port local : 443  TCP

youtube  : IP : 162.247.243.29 port serveur : 443 port local : 57403  TCP

Instant Gaming : IP : 54.174.212.222 port serveur : 443 port local : 55540 UDP/TCP

### 🌞 Demandez l'avis à votre OS
Connexions actives

Proto  Adresse locale         Adresse distante       État

TCP    10.33.71.246:49417     20.199.120.151:443     ESTABLISHED

TCP    10.33.71.246:55542     20.199.120.85:443      ESTABLISHED

TCP    10.33.71.246:57586     3.235.71.115:443       ESTABLISHED

TCP    10.33.71.246:57601     3.235.71.115:443       ESTABLISHED

TCP    10.33.71.246:57691     140.82.113.26:443      ESTABLISHED

TCP    10.33.71.246:57700     52.112.100.5:443       ESTABLISHED

TCP    10.33.71.246:57701     162.159.136.234:443    ESTABLISHED

TCP    10.33.71.246:57714     52.112.238.116:443     ESTABLISHED

TCP    10.33.71.246:57723     20.82.247.147:443      ESTABLISHED
  
TCP    10.33.71.246:57744     107.22.88.255:443      ESTABLISHED

TCP    10.33.71.246:57747     54.197.104.77:443      ESTABLISHED

TCP    10.33.71.246:57748     52.73.220.41:9000      ESTABLISHED

TCP    10.33.71.246:57757     54.173.179.105:8095    ESTABLISHED

TCP    10.33.71.246:57759     54.173.179.105:8095    ESTABLISHED

TCP    10.33.71.246:57771     20.250.77.142:443      ESTABLISHED

TCP    10.33.71.246:57788     155.133.248.38:27030   ESTABLISHED

TCP    10.33.71.246:57797     52.10.185.17:443       ESTABLISHED

TCP    10.33.71.246:57812     44.205.50.241:443      ESTABLISHED

TCP    10.33.71.246:57868     64.233.184.188:5228    ESTABLISHED

TCP    10.33.71.246:57869     162.247.241.14:443     ESTABLISHED

TCP    10.33.71.246:57893     151.101.134.214:443    ESTABLISHED

TCP    10.33.71.246:57898     162.247.243.29:443     ESTABLISHED

TCP    10.33.71.246:57916     18.235.205.188:443     ESTABLISHED

TCP    10.33.71.246:57941     44.224.95.5:443        FIN_WAIT_2

TCP    10.33.71.246:57953     18.213.90.161:443      ESTABLISHED

TCP    10.33.71.246:57959     23.57.81.28:443        ESTABLISHED

TCP    10.33.71.246:57960     44.239.146.66:443      ESTABLISHED

TCP    10.33.71.246:57962     3.123.117.219:443      TIME_WAIT

TCP    10.33.71.246:57964     104.46.162.224:443     TIME_WAIT

TCP    10.33.71.246:57965     52.109.76.62:443       ESTABLISHED

TCP    10.33.71.246:57971     104.208.16.88:443      TIME_WAIT

TCP    10.33.71.246:57972     95.100.200.82:443      ESTABLISHED

TCP    10.33.71.246:57974     3.123.117.219:443      TIME_WAIT

TCP    10.33.71.246:57975     150.171.22.254:443     ESTABLISHED

TCP    10.33.71.246:57976     52.113.196.254:443     ESTABLISHED

TCP    10.33.71.246:57977     13.107.6.254:443       ESTABLISHED

TCP    10.33.71.246:57978     204.79.197.222:443     ESTABLISHED

TCP    127.0.0.1:1042         127.0.0.1:49672        ESTABLISHED

TCP    127.0.0.1:1042         127.0.0.1:49673        ESTABLISHED

TCP    127.0.0.1:3216         127.0.0.1:57599        ESTABLISHED

TCP    127.0.0.1:9012         127.0.0.1:49712        ESTABLISHED

TCP    127.0.0.1:13030        127.0.0.1:49670        ESTABLISHED

TCP    127.0.0.1:17532        127.0.0.1:49678        ESTABLISHED

TCP    127.0.0.1:27060        127.0.0.1:56089        ESTABLISHED

TCP    127.0.0.1:49670        127.0.0.1:13030        ESTABLISHED

TCP    127.0.0.1:49672        127.0.0.1:1042         ESTABLISHED

TCP    127.0.0.1:49673        127.0.0.1:1042         ESTABLISHED

TCP    127.0.0.1:49678        127.0.0.1:17532        ESTABLISHED

TCP    127.0.0.1:49696        127.0.0.1:65001        ESTABLISHED

TCP    127.0.0.1:49699        127.0.0.1:57690        ESTABLISHED

TCP    127.0.0.1:49699        127.0.0.1:57950        TIME_WAIT

TCP    127.0.0.1:49699        127.0.0.1:57968        FIN_WAIT_2

TCP    127.0.0.1:49699        127.0.0.1:57969        ESTABLISHED

TCP    127.0.0.1:49712        127.0.0.1:9012         ESTABLISHED

TCP    127.0.0.1:56089        127.0.0.1:27060        ESTABLISHED

TCP    127.0.0.1:57599        127.0.0.1:3216         ESTABLISHED

TCP    127.0.0.1:57690        127.0.0.1:49699        ESTABLISHED

TCP    127.0.0.1:57968        127.0.0.1:49699        CLOSE_WAIT

TCP    127.0.0.1:57969        127.0.0.1:49699        ESTABLISHED

TCP    127.0.0.1:65001        127.0.0.1:49696        ESTABLISHED

TCP    [::1]:4699             [::1]:57543            ESTABLISHED

TCP    [::1]:57543            [::1]:4699             ESTABLISHED

TCP    [::1]:57548            [::1]:57551            ESTABLISHED

TCP    [::1]:57549            [::1]:57592            ESTABLISHED

TCP    [::1]:57551            [::1]:57548            ESTABLISHED

TCP    [::1]:57592            [::1]:57549            ESTABLISHED

# II. Setup Virtuel

## 1. SSH

### 🌞 Examinez le trafic dans Wireshark
