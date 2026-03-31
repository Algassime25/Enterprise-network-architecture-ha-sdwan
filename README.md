# Enterprise Multi-Layer Network Architecture

## Overview | Aperçu

**EN:**  
This project demonstrates the design and implementation of a complete enterprise network infrastructure, from the access layer to the Internet edge, integrating redundancy, routing, security, and high availability.

**FR :**  
Ce projet démontre la conception et l’implémentation d’une infrastructure réseau d’entreprise complète, de la couche d’accès jusqu’à la bordure Internet, intégrant redondance, routage, sécurité et haute disponibilité.

---

## Key Technologies Used | Technologies clés

This lab integrates critical technologies used in modern enterprise networks.  
Ce laboratoire met en œuvre des technologies essentielles utilisées dans les réseaux d’entreprise modernes.

---

### LAN & Core Infrastructure | Infrastructure LAN & Core

**EN:**
* **Layer 2 Redundancy:** Rapid-PVST and VLAN segmentation  
* **Layer 3 Redundancy:** HSRP for default gateway  
* **EtherChannel:** Layer 3 link aggregation for high availability  
* **Internal Routing:** EIGRP AS 100 between Distribution and Core switches  

**FR :**
* **Redondance couche 2 :** Rapid-PVST et segmentation VLAN  
* **Redondance couche 3 :** HSRP pour la passerelle par défaut  
* **EtherChannel :** Agrégation de liens couche 3 pour la haute disponibilité  
* **Routage interne :** EIGRP AS 100 entre les switchs Distribution et Core  

---

### Routing & Redistribution | Routage et redistribution

**EN:**
* **OSPF Area 0:** Connectivity between Core and ASA  
* **Route Redistribution:** Bidirectional redistribution between EIGRP and OSPF  
* **Internet Edge:** BGP AS 65010 on FortiGate with peering to transit routers (AS 65020)  
* **Dual ISP:** Redundant connectivity to Verizon (AS 64512) and AT&T (AS 64513)  

**FR :**
* **OSPF Area 0 :** Connectivité entre le Core et l’ASA  
* **Redistribution :** Redistribution bidirectionnelle entre EIGRP et OSPF  
* **Internet Edge :** BGP AS 65010 sur FortiGate avec peering vers les routeurs de transit (AS 65020)  
* **Double ISP :** Connectivité redondante vers Verizon (AS 64512) et AT&T (AS 64513)  

---

### Security & High Availability | Sécurité et haute disponibilité

**EN:**
* **ASA Failover:** Active/Standby mode with dedicated failover link  
* **FortiGate HA:** Active/Passive cluster with session synchronization  
* **SD-WAN:** Dual WAN members with SLA monitoring (health checks)  
* **DMZ:** Public services isolated in a dedicated network (172.16.10.0/26)  

**FR :**
* **ASA Failover :** Mode actif/passif avec lien dédié  
* **FortiGate HA :** Cluster actif/passif avec synchronisation des sessions  
* **SD-WAN :** Deux liens WAN avec surveillance des SLA  
* **DMZ :** Isolation des services publics dans un réseau dédié (172.16.10.0/26)  

---

### Quality of Service (QoS) | Qualité de service

**EN:**
* **Class-maps:** Traffic classification (Web, Voice, Video, ICMP)  
* **Policy-maps:** Voice prioritization (LLQ) and bandwidth guarantees  
* **Default Class:** Fair-Queueing for remaining traffic  

**FR :**
* **Class-maps :** Identification du trafic (Web, Voix, Vidéo, ICMP)  
* **Policy-maps :** Priorisation de la voix (LLQ) et garantie de bande passante  
* **Classe par défaut :** Fair-Queueing pour le reste du trafic  

---

## Addressing Overview | Plan d’adressage

### Internal Networks | Réseaux internes

**EN:**
* VLAN 10, 20, 30: User networks (10.10.x.0/24)  
* VLAN 50: Management (10.10.50.0/24)  
* VLAN 60: Servers (25.25.25.0/29)  

**FR :**
* VLAN 10, 20, 30 : Réseaux utilisateurs (10.10.x.0/24)  
* VLAN 50 : Management (10.10.50.0/24)  
* VLAN 60 : Serveurs (25.25.25.0/29)  

---

### Public & WAN | Réseaux publics et WAN

**EN:**
* SD-WAN Members: 100.64.1.0/30 and 100.64.2.0/30  
* ISP Networks: 198.51.100.0/30 (Verizon) and 203.0.113.0/30 (AT&T)  

**FR :**
* Membres SD-WAN : 100.64.1.0/30 et 100.64.2.0/30  
* Réseaux ISP : 198.51.100.0/30 (Verizon) et 203.0.113.0/30 (AT&T)  
