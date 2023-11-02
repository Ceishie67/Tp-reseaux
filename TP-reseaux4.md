# TP4 : DHCP

![Alt text](image.png)

## I. DHCP Client

### 🌞 Déterminer

```
ipconfig /all
```
address du DHCP: 10.33.79.254

bail obtenus le vendredi 27 octobre 2023 09:16:48

Bail expirant le samedi 28 octobre 2023 09:16:36

### 🌞 Capturer un échange DHCP

[capture Wireshark](./tp4_dhcp_client.pcapng)

### 🌞 Analyser la capture Wireshark

parmis les 4 trames celle qui contient les informations proposées aux client est aucune car pour des raison que je ne conprends pas dans ma capture wireshark je n'ai que la request et la ack mais ce ne sont pas les bonnes la bonne réponse serais la DHCP offer qui n'est pas dans la capture wireshark
(j'ai essayer plusieur fois de relancer le procesus mais toujours la même chose j'obtiens toujours les mêmes résultats en boucle)

## II. Serveur DHCP

## 1. Topologie

## 2. Tableau d'adressage