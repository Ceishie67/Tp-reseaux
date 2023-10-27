# TP3 : On va router des trucs

![Alt text](image.png)

## 0. Prérequis

➜ Pour ce TP, on va se servir de VMs Rocky Linux. 1Go RAM c'est large large. Vous pouvez redescendre la mémoire vidéo aussi.
➜ Vous aurez besoin de deux réseaux host-only dans VirtualBox :

un premier réseau 10.3.1.0/24

le second 10.3.2.0/24

vous devrez désactiver le DHCP de votre hyperviseur (VirtualBox) et définir les IPs de vos VMs de façon statique

➜ Les firewalls de vos VMs doivent toujours être actifs (et donc correctement configurés sinon, ça fonctionnera po).
➜ Vous utiliserez toujours SSH (pas directement la console VirtualBox)
➜ Si vous voyez le p'tit pote 🦈 c'est qu'il y a un fichier PCAP à produire et à mettre dans votre dépôt git de rendu (une capture Wireshark).

Pour un TP plus clair, j'ai séparé chaque partie dans un doc dédié.

## I. ARP

## 1. Echange ARP

### 🌞Générer des requêtes ARP

marcel 
```
ping 10.3.1.11
64 bytes from 10.3.1.11: icmp_seq=78 ttl=64 time=0.661 ms
64 bytes from 10.3.1.11: icmp_seq=79 ttl=64 time=0.826 ms
64 bytes from 10.3.1.11: icmp_seq=80 ttl=64 time=0.586 ms
64 bytes from 10.3.1.11: icmp_seq=81 ttl=64 time=2.14 ms
64 bytes from 10.3.1.11: icmp_seq=82 ttl=64 time=0.643 ms
64 bytes from 10.3.1.11: icmp_seq=83 ttl=64 time=1.21 ms
--- 10.3.1.11 ping statistics ---
83 packets transmitted, 83 received, 0% packet loss, time 83674ms
rtt min/avg/max/mdev = 0.488/0.760/2.144/0.198 ms
```

john
```
ping 10.3.1.12
64 bytes from 10.3.1.12: icmp_seq=68 ttl=64 time=0.726 ms
64 bytes from 10.3.1.12: icmp_seq=69 ttl=64 time=0.825 ms
64 bytes from 10.3.1.12: icmp_seq=70 ttl=64 time=0.875 ms
64 bytes from 10.3.1.12: icmp_seq=71 ttl=64 time=0.716 ms
64 bytes from 10.3.1.12: icmp_seq=72 ttl=64 time=1.10 ms
64 bytes from 10.3.1.12: icmp_seq=73 ttl=64 time=0.785 ms
64 bytes from 10.3.1.12: icmp_seq=74 ttl=64 time=1.06 ms
--- 10.3.1.12 ping statistics ---
74 packets transmitted, 74 received, 0% packet loss, time 74340ms
rtt min/avg/max/mdev = 0.502/0.808/2.489/0.240 ms
```
Table ARP

marcel
```
ip neigh show
10.3.1.1 dev enp0s3 lladdr 0a:00:27:00:00:38 REACHABLE
10.3.1.11 dev enp0s3 lladdr 08:00:27:c5:00:9b STALE
```
john
```
ip neigh show
10.3.1.1 dev enp0s3 lladdr 0a:00:27:00:00:38 REACHABLE
10.3.1.12 dev enp0s3 lladdr 08:00:27:f3:91:7e STALE
```
address MAC marcel : 08:00:27:f3:91:7e

address MAC john : 08:00:27:c5:00:9b

## 2. Analyse de trames

[capture Wireshark](./Tp-réseaux3.pcap)

### 🌞Ajouter les routes statiques nécessaires pour que john et marcel puissent se ping
