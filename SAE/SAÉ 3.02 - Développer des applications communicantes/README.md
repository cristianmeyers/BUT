# SAÉ 3.02 - Développer des applications communicantes

## Projet : WakeJS (Gestion centralisée du Wake-on-LAN)

Ce projet répond aux exigences de la SAÉ 3.02 en combinant l'administration réseau et le développement d'outils logiciels pour les R&T.

> Les détails techniques complets, le code source et les procédures d'installation sont disponibles sur le dépôt dédié : [https://github.com/cristianmeyers/wakejs](https://github.com/cristianmeyers/wakejs)

### 🎯 Contexte du Projet

Développé au sein de l'**IUT de Brest Morlaix**, ce projet répond à une problématique d'administration système et réseau : optimiser et centraliser l'allumage et l'extinction du parc informatique réparti sur plusieurs bâtiments et **VLANs**.

**WakeJS** a été conçu pour :

- **Centraliser** le réveil (Wake-on-LAN) et le monitoring d'état des salles via **ICMP**.
- **Automatiser** la consultation des postes en temps réel en analysant (**parsing**) directement le fichier de configuration du serveur **ISC DHCP**.
- **Segmenter** les actions par départements et salles pour répondre aux besoins des techniciens de proximité.

### 🔗 Justification par rapport au Référentiel

| Composante du Référentiel           | Justification par l'implémentation WakeJS                                                                             |
| ----------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **AC23.03 : Protocole réseau**      | Utilisation du protocole **UDP** (Port 9) pour l'envoi de Magic Packets et **ICMP** pour le monitoring d'état (Ping). |
| **AC23.02 : Interface Web**         | Développement d'une interface dynamique en **HTML5, CSS3 (Tailwind)** et **Vanilla JS**.                              |
| **AC23.04/05 : Gestion de données** | Analyse (**Parsing**) et extraction de données depuis un fichier de configuration **ISC DHCP** (`dhcpd.conf`).        |
| **Client/Serveur**                  | Architecture basée sur une **API REST Node.js (Express)** et un client web asynchrone.                                |
| **Mots-clés : Protocoles**          | Implémentation de **HTTP** (API), **UDP** (WOL) et **SSH** (Commandes distantes).                                     |
| **Mots-clés : Sérialisation**       | Manipulation et structuration des données au format **JSON**.                                                         |

### 🛠️ Stack Technique mobilisée

- **Backend :** Node.js, Express, PM2 (Gestionnaire de process).
- **Frontend :** HTML, Tailwind CSS, JavaScript ES6.
- **Réseau & Sécurité :** Sockets UDP, ICMP Ping, SSH.
- **Serveur Web :** Nginx (Reverse Proxy pour l'exposition de l'API).

### 📂 Organisation du Portfolio

Conformément au programme National, ce projet mobilise et valide les ressources suivantes :

- **R3.08 & R3.09** : Logique de programmation événementielle et batching des paquets.
- **R3.10** : Exploitation de la structure de données issue du service DHCP.
- **R4.05** : Automatisation des tâches d'administration via scripts Bash et SSH.

> La gestion de l’authentification des utilisateurs est traitée dans un autre projet transverse du portfolio, dédié à la sécurisation des accès et à la gestion des identités.
