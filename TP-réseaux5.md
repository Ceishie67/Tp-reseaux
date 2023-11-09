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