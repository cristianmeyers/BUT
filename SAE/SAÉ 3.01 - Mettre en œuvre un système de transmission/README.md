# SAÉ 3.01 - Mettre en œuvre un système de transmission

Ce projet répond aux exigences de la **SAÉ 3.01** (Mettre en œuvre un système de transmission) du programme national **PN-BUT-RT 2022**, rattachée à la compétence **C3.2 - Connecter les entreprises et les usagers**, et contribue à la SAÉ complémentaire **3.Cyber.03** (Concevoir un réseau informatique sécurisé multi-sites).

## Projet

- **Liaison WiFi point-à-point OpenWrt** - Interconnexion sans fil entre une Freebox et un lab Proxmox personnel, via un routeur OpenWrt configuré en mode client WiFi (WDS/repeater)

> **NOTE IMPORTANTE** : Projet réalisé en environnement personnel maîtrisé, sur du matériel et un réseau dont je suis propriétaire/administrateur. Aucune interception ni interférence sur des réseaux tiers. Respect des bonnes pratiques ANSSI d'hygiène informatique et de cloisonnement réseau.

### 🎯 Contexte et objectifs

Développé en complément du lab **cyberenv** dans le cadre du **BTS SIO SISR** (alternance) et en préparation du **BUT R&T parcours Cybersécurité**, ce projet met en œuvre un **système de transmission radio (WiFi 802.11)** comme média d'interconnexion entre une box opérateur (Freebox) et un réseau local isolé hébergeant un lab de virtualisation Proxmox.

Le routeur OpenWrt agit comme **client WiFi** sur le SSID de la Freebox (mode WDS/repeater), capte le signal radio, puis distribue une connexion filaire/WiFi isolée vers le lab Proxmox. Ce montage permet de raccorder un environnement de virtualisation à Internet sans câblage direct vers la box, tout en gardant un cloisonnement réseau strict entre le réseau domestique et le réseau du lab.

**Objectifs alignés PN-BUT-RT (C3.2)** :

- Mettre en œuvre une liaison de transmission sans fil (WiFi 802.11) entre deux équipements réseau distincts.
- Étudier et configurer un équipement en mode client WiFi (association, authentification, association au SSID, gestion du signal).
- Évaluer les performances de la liaison radio (débit, latence, puissance du signal, taux de perte) selon le placement et les conditions de propagation.
- Isoler le réseau du lab vis-à-vis du réseau domestique tout en s'appuyant sur la liaison radio comme unique passerelle Internet.

Ce montage a été conçu et déployé personnellement comme socle réseau du lab cyberenv.

### 📂 Infrastructure et configuration

- **Source de transmission** : Freebox (box opérateur, diffusion WiFi 802.11 domestique)
- **Équipement intermédiaire** : routeur grand public reflashé **OpenWrt**, configuré en **mode client WiFi (WDS/repeater)** sur le SSID de la Freebox
- **Administration** : interface web **LuCI** pour la configuration courante (interfaces, WiFi, DHCP, firewall) et **SSH** (commandes `uci`, `iptables`/`nftables`) pour les réglages avancés et le diagnostic
- **Réseau aval isolé** : le routeur OpenWrt génère un réseau local séparé (VLAN/subnet dédié, NAT propre) qui alimente le **lab Proxmox**, sans pont direct vers le réseau domestique de la Freebox
- **Cloisonnement** : règles de pare-feu OpenWrt empêchant toute communication entre le réseau du lab et les autres équipements du réseau domestique (zones firewall distinctes, forwarding contrôlé)

### 📂 Ressources mobilisées (PN-BUT-RT 2022)

- C3.2 - Connecter les entreprises et les usagers (SAÉ 3.01, coefficient 20)
- R3.01 - Systèmes de transmission
- R3.02 - Administration système et réseau
- R4.Cyber.09 - Sécurité des réseaux LAN
- SAÉ 3.Cyber.03 - Concevoir un réseau informatique sécurisé multi-sites

### 🔗 Justification par rapport au Référentiel (PN-BUT-RT 2022)

| Composante du Référentiel                                 | Justification                                                                                                                                                                                                                                        |
| --------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **SAÉ 3.01 : Mettre en œuvre un système de transmission** | Liaison radio WiFi 802.11 opérationnelle entre la Freebox (point d'accès) et le routeur OpenWrt (mode client/WDS) ; mise en service, supervision du signal et du débit de la liaison sans fil utilisée comme accès Internet d'un réseau local isolé. |
| **C3.2 : Connecter les entreprises et les usagers**       | Mise en œuvre concrète d'une connexion réseau reliant un usager final (lab Proxmox) à un point d'accès opérateur via une transmission radio, avec administration de l'équipement intermédiaire (LuCI/SSH).                                           |
| **R3.01 : Systèmes de transmission**                      | Configuration d'une interface radio en mode client (association SSID, sécurité WPA, gestion du canal) ; compréhension des paramètres de propagation WiFi (puissance, débit, interférences).                                                          |
| **R3.02 : Administration système et réseau**              | Configuration OpenWrt via LuCI et SSH (uci, interfaces réseau, DHCP, NAT, firewall) ; diagnostic réseau (état de la liaison, débit, qualité du signal).                                                                                              |
| **R4.Cyber.09 : Sécurité des réseaux LAN**                | Cloisonnement strict entre le réseau domestique et le réseau du lab Proxmox via zones de pare-feu OpenWrt distinctes, malgré une passerelle Internet commune issue de la liaison radio.                                                              |

### 🛠️ Stack technique mobilisée

- Firmware : OpenWrt (LuCI + ligne de commande)
- Transmission : WiFi 802.11 (mode client / WDS-repeater) sur SSID Freebox
- Administration : LuCI (interface web), SSH, `uci`, `iptables`/`nftables`
- Réseau aval : DHCP, NAT, VLAN/subnet isolé vers le lab Proxmox
- Sécurité : zones de pare-feu séparées, cloisonnement domestique/lab

### 📚 Livrables pédagogiques

- Schéma de la chaîne de transmission (Freebox → liaison radio → OpenWrt → réseau lab isolé)
- Captures de configuration OpenWrt (interface WiFi client, zones firewall, DHCP)
- Mesures de performance de la liaison (débit, puissance du signal, latence)
- Procédure de configuration et de diagnostic de la liaison radio
