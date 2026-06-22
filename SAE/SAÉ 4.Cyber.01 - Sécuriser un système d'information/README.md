# SAÉ 4.Cyber.01 - Sécuriser un système d'information

Ce projet répond aux exigences de la **SAÉ 4.Cyber.01** (Sécuriser un système d'information) du programme national **PN-BUT-RT 2022 Annexe 22** et contribue fortement aux SAÉ complémentaires **3.Cyber.03** (Concevoir un réseau informatique sécurisé multi-sites) et **3.Cyber.04** (Découvrir le pentesting).

## Projet

- **[cyberenv](https://github.com/cristianmeyers/cyberenv)** - Lab d'apprentissage de cybersécurité

> **NOTE IMPORTANTE** : Projet strictement pédagogique, isolé et contrôlé - utilisation réservée à la formation en cybersécurité. Respect total du RGPD (données anonymisées/minimisées), recommandations ANSSI (CyberEdu, hygiène informatique, durcissement des systèmes), et principes ISO 27001 (analyse de risques, traçabilité, sensibilisation, charte éthique). Aucun accès externe, aucune exploitation réelle.

### 🎯 Contexte et objectifs

Développé dans le cadre du **BTS SIO SISR** (alternance) et en préparation du **BUT R&T parcours Cybersécurité**, ce volet du lab **cyberenv** porte sur la **sécurisation et le durcissement (hardening)** des systèmes hébergés : hyperviseur Proxmox, machines Linux et machines Windows (Active Directory).

Une fois l'infrastructure réseau conçue (SAÉ 3.Cyber.03) et les vulnérabilités identifiées via les exercices de pentesting (SAÉ 3.Cyber.04), l'enjeu de cette SAÉ est de **réduire la surface d'attaque** de chaque brique du système d'information : hyperviseur, systèmes d'exploitation, services exposés, comptes et droits d'accès.

**Objectifs alignés PN-BUT-RT** :

- Durcir l'hyperviseur Proxmox (accès, mises à jour, services superflus, sauvegardes/snapshots).
- Durcir les systèmes Linux (services, comptes, SSH, pare-feu local, mises à jour automatiques).
- Durcir l'environnement Windows / Active Directory (GPO de sécurité, politique de mots de passe, comptes à privilèges, journalisation).
- Mettre en place une supervision minimale (journalisation centralisée, IPS/IDS) permettant de détecter les écarts par rapport à l'état durci.
- Documenter une démarche de sécurisation reproductible et auditable (charte éthique, conformité RGPD/ANSSI/ISO 27001).

Ce lab a été **validé par mon formateur** et sera validé par **le rectorat** pour l'utilisation pédagogique en salle informatique (préparation examen BTS).

### 📂 Infrastructure et durcissement

- **Hyperviseur Proxmox** : mises à jour régulières, accès à l'interface de gestion restreint (réseau dédié), comptes d'administration séparés des comptes courants, sauvegardes et snapshots réguliers pour permettre une remise en état rapide après incident
- **Systèmes Linux** : limitation des services actifs au strict nécessaire, configuration SSH durcie (désactivation de l'authentification par mot de passe root, changement de port si pertinent), pare-feu local (iptables/nftables/ufw), mises à jour de sécurité automatisées
- **Active Directory / Windows** : politique de mots de passe renforcée, séparation des comptes à privilèges (admin du domaine vs comptes utilisateurs), GPO de sécurité (restrictions d'exécution, verrouillage de session), audit des connexions
- **Services applicatifs** (GLPI, OPSI) : restriction des accès par ACL, authentification renforcée, mise à jour des composants pour limiter les vulnérabilités connues
- **NAS** : accès restreint, séparation des partages, sauvegardes isolées du reste de l'infrastructure
- **Supervision** : IPS/IDS pour détecter les anomalies (tentatives de connexion suspectes, scans), journalisation centralisée des événements systèmes et réseau

### 📂 Ressources mobilisées (PN-BUT-RT 2022)

- R4.Cyber.11 - Sécurisation de services réseaux
- R4.01 - Infrastructures de sécurité
- R4.05 - Automatisation des tâches d'administration
- R2.02 / R3.02 - Administration système et virtualisation
- R3.04 / R4.04 - Services d'annuaires
- SAÉ 3.Cyber.03 - Concevoir un réseau informatique sécurisé multi-sites
- SAÉ 3.Cyber.04 - Découvrir le pentesting

### 🔗 Justification par rapport au Référentiel (PN-BUT-RT 2022)

| Composante du Référentiel                           | Justification (alignée PN-BUT-RT + RGPD/ANSSI/ISO 27001)                                                                                                                                                                                                                    |
| --------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **SAÉ 4.Cyber.01 : Sécuriser un SI**                | Durcissement systématique de l'hyperviseur Proxmox, des systèmes Linux et de l'environnement Active Directory ; sauvegardes/snapshots réguliers pour la résilience ; supervision IPS/IDS et journalisation centralisée ; charte éthique et conformité ANSSI/RGPD/ISO 27001. |
| **R4.Cyber.11 : Sécurisation des services réseaux** | Restriction des accès aux services GLPI/OPSI (ACL, authentification renforcée), mise à jour des composants exposés, réduction de la surface d'attaque des services réseau.                                                                                                  |
| **R4.01 : Infrastructures de sécurité**             | Hardening Proxmox (accès restreint, mises à jour, sauvegardes), hardening Linux (services, SSH, pare-feu local), hardening Windows/AD (GPO, comptes à privilèges, politique de mots de passe).                                                                              |
| **R4.05 : Automatisation admin**                    | Scripts Shell pour l'application systématique des règles de durcissement, les mises à jour automatisées et la gestion des sauvegardes/snapshots Proxmox.                                                                                                                    |
| **R2.02 / R3.02 : Admin sys/virtualisation**        | Configuration sécurisée de l'hyperviseur (comptes, accès, snapshots) ; durcissement des serveurs Linux et Windows hébergés.                                                                                                                                                 |
| **R3.04 / R4.04 : Services d'annuaires**            | Sécurisation de l'Active Directory : GPO de sécurité, séparation des comptes à privilèges, politique de mots de passe, audit des connexions.                                                                                                                                |

### 🛠️ Stack technique mobilisée

- Langages : Shell (scripts de durcissement, automatisation des mises à jour et sauvegardes)
- Hyperviseur : Proxmox (gestion des accès, snapshots, sauvegardes)
- Systèmes : Linux (SSH durci, pare-feu local, gestion des services), Windows/Active Directory (GPO de sécurité, comptes à privilèges)
- Services & annuaires : Active Directory, GLPI, OPSI (ACL, authentification renforcée)
- Stockage : NAS sécurisé (accès restreint, sauvegardes isolées)
- Supervision / Sécurité : IPS/IDS, journalisation centralisée, audit des connexions
- Outils d'audit du durcissement : scanners de vulnérabilités, vérification post-hardening (réutilisation des outils issus de la SAÉ 3.Cyber.04)

### 📚 Livrables pédagogiques

- Procédures de durcissement par brique (Proxmox, Linux, Windows/AD)
- Scripts d'automatisation du hardening et des sauvegardes
- Politique de sécurité documentée (mots de passe, comptes à privilèges, accès)
- Charte éthique + consignes sécurité (RGPD/ANSSI/ISO 27001)
- Rapport de vérification post-durcissement (comparaison avant/après)
