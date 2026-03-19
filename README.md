# Enterprise Multi-Layer Network Architecture

Ce projet démontre la conception et l'implémentation d'une infrastructure réseau d'entreprise complète, allant de la couche d'accès jusqu'à la bordure Internet (Edge).

## Key Technologies Used

Ce lab met en œuvre plusieurs technologies critiques utilisées dans les réseaux d'entreprise modernes :

### LAN & Core Infrastructure
* **Redondance de couche 2 :** Rapid-PVST et segmentation VLAN
* **Redondance de couche 3 :** HSRP pour la passerelle par défaut
* **EtherChannel :** Agrégation de liens de couche 3 pour la haute disponibilité
* **Routage interne :** EIGRP AS 100 entre les switchs de Distribution et de Core

### Routing & Redistribution
* **OSPF Area 0 :** Utilisé pour la connectivité entre le Core et l'ASA
* **Redistribution de routes :** Redistribution bidirectionnelle entre EIGRP et OSPF
* **Internet Edge :** BGP AS 65010 sur FortiGate avec peering vers les routeurs de transit (AS 65020)
* **Dual ISP :** Connectivité redondante vers Verizon (AS 64512) et AT&T (AS 64513)

### Security & High Availability
* **ASA Failover :** Mode Active/Standby avec réseau de failover dédié
* **FortiGate HA :** Cluster Active/Passive avec synchronisation des sessions
* **SD-WAN :** Utilisation de deux membres WAN avec surveillance des SLAs (Health Checks)
* **DMZ :** Isolation des services publics dans un réseau dédié 172.16.10.0/26

### Quality of Service (QoS)
* **Class-maps :** Identification du trafic Web, Voix, Vidéo et ICMP
* **Policy-maps :** Priorisation de la Voix (LLQ) et garantie de bande passante pour le Web et la Vidéo
* **Default Class :** Mise en œuvre du Fair-Queueing pour le trafic restant

## Addressing Overview

### Internal Networks
* **VLAN 10, 20, 30 :** Réseaux utilisateurs (10.10.x.0/24)
* **VLAN 50 :** Management (10.10.50.0/24)
* **VLAN 60 :** Serveurs (25.25.25.0/29)

### Public & WAN
* **SD-WAN Members :** 100.64.1.0/30 et 100.64.2.0/30
* **ISP Networks :** 198.51.100.0/30 (Verizon) et 203.0.113.0/30 (AT&T)
