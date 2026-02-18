# SAÉ 3.02 - Développer des applications communicantes

Ces projets répondent aux exigences de la **SAÉ 3.02** en combinant l'administration réseau, le déploiement de services et le développement d'outils logiciels pour les R&T.
Les détails techniques complets, les codes sources et les procédures d'installation sont disponibles sur les dépôts dédiés.

## Projets

- **[WakeJS](https://github.com/cristianmeyers/wakejs)** – Gestion centralisée du Wake-on-LAN
- **[Wiki.js](https://github.com/cristianmeyers/)** – Déploiement d’un wiki collaboratif

> **NOTE :** Cliquez sur les noms des projets pour accéder aux dépôts.

---

# WakeJS (Gestion centralisée du Wake-on-LAN)

### 🎯 Contexte du Projet

Développé au sein de l'**IUT de Brest Morlaix**, ce projet répond à une problématique d'administration système et réseau : optimiser et centraliser l'allumage et l'extinction du parc informatique réparti sur plusieurs bâtiments et **VLANs**.

**WakeJS** a été conçu pour :

- **Centraliser** le réveil (Wake-on-LAN) et le monitoring d'état des salles via **ICMP**.
- **Automatiser** la consultation des postes en temps réel en analysant (**parsing**) directement le fichier de configuration du serveur **ISC DHCP**.
- **Segmenter** les actions par départements et salles pour répondre aux besoins des techniciens de proximité.

### 📂 Ressources

- **[R3.08 – Consolidation de la programmation](../../Ressources/R3.08%20-%20Consolidation%20de%20la%20programmation/README.md)**
- **[R3.09 – Programmation événementielle](../../Ressources/R3.09%20-%20Programmation%20%C3%A9v%C3%A9nementielle/README.md)**
- **[R3.10 – Systèmes de gestion de bases de données](../../Ressources/R3.10%20-%20Syst%C3%A8mes%20de%20gestion%20de%20bases%20de%20donn%C3%A9es/README.md)**
- **[R4.05 – Automatisation des tâches d'administration](../../Ressources/R4.05%20-%20Automatisation%20des%20t%C3%A2ches%20d'administration/README.md)**

### 🔗 Justification par rapport au Référentiel

| Composante du Référentiel           | Justification                                                                                           |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------- |
| **AC23.03 : Protocole réseau**      | Utilisation du protocole **UDP** (Port 9) pour l'envoi de Magic Packets et **ICMP** pour le monitoring. |
| **AC23.02 : Interface Web**         | Développement d'une interface dynamique en **HTML5, CSS3 (Tailwind)** et **Vanilla JS**.                |
| **AC23.04/05 : Gestion de données** | Analyse (**Parsing**) et extraction de données depuis un fichier de configuration **ISC DHCP**.         |
| **Client/Serveur**                  | Architecture basée sur une **API REST Node.js (Express)** et un client web asynchrone.                  |
| **Mots-clés : Protocoles**          | Implémentation de **HTTP**, **UDP** (WOL) et **SSH** (commandes distantes).                             |
| **Mots-clés : Sérialisation**       | Manipulation et structuration des données au format **JSON**.                                           |

### 🛠️ Stack Technique mobilisée

- **Backend :** Node.js, Express, PM2 (Gestionnaire de process)
- **Frontend :** HTML, Tailwind CSS, JavaScript ES6
- **Ligne de commande :** Script Bash pour utilisation en CLI
- **Réseau & Sécurité :** Sockets UDP, ICMP Ping, SSH, adresse broadcast selon VLAN
- **Serveur Web :** Nginx (Reverse Proxy pour l'exposition de l'API)

---

# Wiki.js (Déploiement d’un wiki collaboratif)

### 🎯 Contexte du Projet

Déployé au sein de l'**IUT de Brest Morlaix**, ce projet avait pour objectif de **moderniser la documentation interne** en migrant un wiki obsolète vers une solution plus ergonomique et collaborative.

Mon rôle a été principalement de **déployer et maintenir le service** :

- Installation sur serveur Linux
- Configuration des bases **MariaDB** et **PostgreSQL**
- Lancement du service via **PM2**
- Personalisation et maintenance du wiki

Cette solution a été validée par le **chef du service informatique** et l’équipe, conformément aux besoins identifiés dans le **cahier des charges implicite** (sécurité, accessibilité, portabilité).

### 📂 Ressources

- **[R4.01 – Infrastructures de sécurité](../../Ressources/R4.01%20-%20Infrastructures%20de%20s%C3%A9curit%C3%A9/README.md)**
- **[R4.05 – Automatisation des tâches d'administration](../../Ressources/R4.05%20-%20Automatisation%20des%20t%C3%A2ches%20d'administration/README.md)**

### 🔗 Justification par rapport au Référentiel

| Composante du Référentiel           | Justification                                                          |
| ----------------------------------- | ---------------------------------------------------------------------- |
| **AC23.04/05 : Gestion de données** | Installation et configuration des bases de données MariaDB/PostgreSQL. |
| **Client/Serveur**                  | Déploiement d’un service Node.js accessible via une interface web.     |
| **Mots-clés : Protocoles**          | HTTP/HTTPS via Nginx, gestion des sessions et accès sécurisés.         |

### 🛠️ Stack Technique mobilisée

- **Serveur Linux :** installation et configuration de Wiki.js
- **Bases de données :** MariaDB et PostgreSQL
- **Gestion du service :** PM2 pour Node.js, déploiement Docker
- **Sécurité :** Nginx en reverse proxy avec SSL

> Ce projet est principalement orienté **déploiement et administration de service**, et non développement de l’application.
