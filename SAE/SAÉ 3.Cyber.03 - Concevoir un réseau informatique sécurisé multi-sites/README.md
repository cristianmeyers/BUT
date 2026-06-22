# SAÉ 3.Cyber.03 - Concevoir un réseau informatique sécurisé multi-sites

Ce projet répond aux exigences de la **SAÉ 3.Cyber.03** (Concevoir un réseau informatique sécurisé multi-sites) du programme national **PN-BUT-RT 2022 Annexe 22** et contribue fortement aux SAÉ complémentaires **3.Cyber.04** (Découvrir le pentesting) et **4.Cyber.01** (Sécuriser un système d'information).

## Projets

- **[cyberenv](https://github.com/cristianmeyers/cyberenv)** - Lab d'apprentissage de cybersécurité

> **NOTE IMPORTANTE** : Projet strictement pédagogique, isolé et contrôlé - utilisation réservée à la formation en cybersécurité. Respect total du RGPD (données anonymisées/minimisées), recommandations ANSSI (CyberEdu, hygiène informatique, cloisonnement), et principes ISO 27001 (analyse de risques, traçabilité, sensibilisation, charte éthique). Aucun accès externe, aucune exploitation réelle.

### 🎯 Contexte et objectifs

Développé dans le cadre du **BTS SIO SISR** (alternance) et en préparation du **BUT R&T parcours Cybersécurité**, **cyberenv** est un laboratoire pédagogique dédié à la conception d'une infrastructure réseau sécurisée et multi-sites.

Je simule une infrastructure d'entreprise répartie sur deux sites distincts, reliés de façon sécurisée, avec :

- Postes attaquants (Kali) et machines cibles vulnérables intentionnellement, pour valider l'étanchéité de la segmentation
- Services réels (Wiki.js, GLPI, OPSI, Active Directory, DHCP, NAS...)
- Une interconnexion sécurisée entre les deux sites via **VPN Tailscale**

**Objectifs alignés PN-BUT-RT** :

- Concevoir et déployer une architecture réseau multi-sites cloisonnée et sécurisée.
- Interconnecter deux sites Proxmox distincts via un VPN mesh (Tailscale) sans exposer les services en accès public.
- Automatiser déploiement, isolation réseau, sauvegardes et réinitialisation pour reproductibilité/sécurité.
- Sensibiliser à l'hygiène informatique et aux risques (charte + règles d'usage).

Ce lab a été **validé par mon formateur** et sera validé par **le rectorat** pour l'utilisation pédagogique en salle informatique (préparation examen BTS).

### 📂 Infrastructure et services

- **Hyperviseur / Virtualisation** : Proxmox (VMs, clones, snapshots, haute disponibilité) déployé sur **deux sites distincts**
- **Interconnexion multi-sites** : VPN mesh **Tailscale** (WireGuard) entre les deux sites Proxmox, sans exposition de ports publics
- **Réseau & Isolation** : VLANs, trunk ports (802.1Q), NAT, firewalls, points d'accès WiFi sécurisés (WPA3, isolation SSID/guest)
- **Services & Annuaires** : Active Directory (authentification centralisée), ISC DHCP (adresses VLAN-isolées), GLPI (inventaire/tickets), Wiki.js (documentation), OPSI (déploiement massifs)
- **Stockage** : NAS sécurisé (accès restreint, backups isolés)
- **Supervision / Sécurité** : IPS/IDS (détection anomalies logs/outils), journalisation centralisée, hardening services

### 📂 Ressources mobilisées (PN-BUT-RT 2022)

- R4.Cyber.09 - Sécurité des réseaux LAN
- R4.Cyber.11 - Sécurisation de services réseaux
- R4.05 - Automatisation des tâches d'administration
- R4.01 - Infrastructures de sécurité
- R2.02 / R3.02 - Administration système et virtualisation
- R3.04 / R4.04 - Services d'annuaires
- R3.10 - Gestion de bases de données
- SAÉ 3.Cyber.04 - Découvrir le pentesting
- SAÉ 4.Cyber.01 - Sécuriser un système d'information

### 🔗 Justification par rapport au Référentiel (PN-BUT-RT 2022)

| Composante du Référentiel                                     | Justification (alignée PN-BUT-RT + RGPD/ANSSI/ISO 27001)                                                                                                                                                                                                                                                                  |
| ------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **SAÉ 3.Cyber.03 : Concevoir un réseau sécurisé multi-sites** | Infrastructure isolée multi-machines répartie sur **deux sites Proxmox** : interconnexion par VPN mesh Tailscale (WireGuard, chiffré, sans port public exposé), VLANs, trunk (802.1Q), NAT, firewalls, segmentation attaquants/cibles, WiFi sécurisé (WPA3/isolation SSID), prévention fuites externes (AC24.01-04Cyber). |
| **SAÉ 3.Cyber.04 : Découvrir le pentesting**                  | Lab complet avec reconnaissance (scanners), identification vulnérabilités (Wiki.js/GLPI/OPSI), exploitation contrôlée (Kill Chain éthique), scénarios progressifs (AC24.05Cyber, AC25.01-02Cyber). Respect RGPD (données anonymisées) et ANSSI (environnement cloisonné).                                                 |
| **SAÉ 4.Cyber.01 : Sécuriser un SI**                          | Hardening services, journalisation, sauvegardes/réinitialisation Proxmox, NAS sécurisé, supervision IPS/IDS ; charte éthique + règles d'usage ; conformité ANSSI/RGPD/ISO 27001 (risques, durcissement).                                                                                                                  |
| **R4.Cyber.09 : Sécurité réseaux LAN**                        | Configuration VLANs, trunk, NAT, firewall, WiFi sécurisé ; isolation stricte lab pentest ; interconnexion multi-sites chiffrée via Tailscale.                                                                                                                                                                             |
| **R4.Cyber.11 : Sécurisation services réseaux**               | Services vulnérables contrôlés + audit/supervision ; durcissement (HTTPS/ACL/auth) ; AD pour identités centralisées.                                                                                                                                                                                                      |
| **R4.05 : Automatisation admin**                              | Scripts Shell pour déploiement/isolation/sauvegarde/réinitialisation ; auto ISC DHCP, Proxmox, OPSI/GLPI.                                                                                                                                                                                                                 |
| **R2.02 / R3.02 : Admin sys/virtualisation**                  | Gestion Proxmox (VMs/snapshots/HA) sur deux sites ; serveurs Linux/Windows (NAS/AD/services).                                                                                                                                                                                                                             |
| **R3.04 / R4.04 : Services d'annuaires**                      | Active Directory (auth centralisée, GPO) ; intégration SSO-like GLPI/Wiki.js/OPSI.                                                                                                                                                                                                                                        |
| **R3.10 : Gestion BD**                                        | Bases GLPI (inventaire), Wiki.js (contenu), OPSI (parc) ; sécurisation ACL MariaDB/PostgreSQL.                                                                                                                                                                                                                            |

### 🛠️ Stack technique mobilisée

- Langages : Shell (~80 %), RouterOS Script (~20 %)
- Automatisation : Scripts déploiement infra, DHCP update, Proxmox auto, réinitialisation cibles, sauvegardes
- Interconnexion multi-sites : **VPN Tailscale** (WireGuard) entre deux sites Proxmox
- Services & annuaires : Active Directory, ISC DHCP, GLPI, Wiki.js, OPSI
- Réseau & isolation : VLANs, trunk, NAT, firewalls, WiFi isolé (WPA3)
- Stockage : NAS sécurisé
- Supervision / Sécurité : IPS/IDS, journalisation, durcissement services
- Outils audit intégrés : Scanners, fuzzers, sniffers (configs dans Services/), NMAP, DVWA, Wireshark, SQLMAP

### 📚 Livrables pédagogiques

- Catalogue d'exercices progressifs + corrigés
- Guides d'installation et procédures ateliers
- Charte éthique + consignes sécurité (RGPD/ANSSI/ISO 27001)
- Scripts d'automatisation pour reproductibilité totale
