# Monitoring System Project

Bienvenue dans le projet ! Ce document a pour but de vous guider à travers l'architecture, la configuration et les objectifs de notre système, afin de moderniser et de sécuriser l'infrastructure informatique de l'entreprise.

## Table des Matières
1. [Introduction](#introduction)
2. [Architecture du Système](#architecture-du-système)
   - [Serveurs Physiques](#serveurs-physiques)
   - [Virtualisation avec Proxmox](#virtualisation-avec-proxmox)
   - [Haute Disponibilité](#haute-disponibilité)
3. [Configuration des Machines Virtuelles](#configuration-des-machines-virtuelles)
   - [Windows Server 2022 avec Zabbix](#windows-server-2022-avec-zabbix)
   - [Ubuntu Server avec OpenSSH et Nginx](#ubuntu-server-avec-openssh-et-nginx)
4. [Surveillance et Visualisation des Données](#surveillance-et-visualisation-des-données)
   - [Grafana et les Dashboards](#grafana-et-les-dashboards)
5. [Objectifs et Bénéfices](#objectifs-et-bénéfices)
6. [Conclusion](#conclusion)

## Introduction
Le projet de système de Monitoring a pour ambition de transformer l'infrastructure IT d'une entreprise en intégrant des solutions de virtualisation et de surveillance avancées. Ce projet est conçu pour assurer une haute disponibilité et une gestion optimisée des ressources à travers une architecture de cluster interconnecté.

![Infrastructure Diagram](images/infrastructure.png)

## Architecture du Système

### Serveurs Physiques
Nous disposons de trois serveurs physiques, chacun équipé de 8 disques :
- **Disques pour Proxmox:** 2 disques en RAID 1 pour une installation en miroir et backup.
- **Disques SSD de cache:** 2 disques SSD pour accélérer le démarrage des serveurs.
- **Disques pour VM:** 4 disques de 300 Go pour héberger les machines virtuelles.

![Serveur Physique](images/server.png)

### Virtualisation avec Proxmox
Proxmox est installé sur les serveurs pour gérer les machines virtuelles (VMs). Grâce aux disques SSD, le démarrage des VMs et du serveur est optimisé. Chaque serveur fait partie d’un cluster interconnecté pour assurer une gestion centralisée et une haute disponibilité.

![Proxmox](images/proxmox.png)

### Haute Disponibilité
En cas de panne d'un serveur, les VMs sont automatiquement transférées aux autres serveurs du cluster, garantissant ainsi une redondance et une continuité de service.

![Haute Disponibilité](images/haute_disponibilite.png)

## Configuration des Machines Virtuelles

### Windows Server 2022 avec Zabbix
- **Installation:** Une VM sous Windows Server 2022 a été créée et l'agent Zabbix y a été installé facilement via un fichier MSI.
- **Usage:** Zabbix est configuré pour surveiller et afficher les informations des différentes localisations sur la géomap de Grafana.

![Windows Server avec Zabbix](images/zabbix.png)

### Ubuntu Server avec OpenSSH et Nginx
- **Installation:** Une VM sous Ubuntu Server a été configurée avec OpenSSH pour permettre un accès facile via PuTTY.
- **Configuration:** Nginx est installé pour servir de serveur web, et MySQL est utilisé pour gérer les bases de données nécessaires au projet.

![Ubuntu Server](images/ubuntu_server.png)

## Surveillance et Visualisation des Données

### Grafana et les Dashboards
Grafana est utilisé pour visualiser les données provenant de différentes sources :
- **Dashboards:** Affichent le trafic réseau, l’utilisation de la mémoire vive, l’espace disque, la charge CPU, etc.
- **Sources de Données:** La principale source de données est Zabbix, ainsi qu'une base de données MySQL sur la même machine.

![Grafana Dashboards](images/grafana.png)

## Objectifs et Bénéfices
- **Modernisation:** Mise à jour de l’infrastructure IT pour une gestion plus efficace.
- **Sécurité et Fiabilité:** Grâce à la haute disponibilité et à la redondance des données.
- **Surveillance Optimale:** Visualisation en temps réel de l’état du réseau et des ressources via Grafana.
- **Facilité de Gestion:** Accès simplifié et configuration centralisée pour les administrateurs système.

![Objectifs et Bénéfices](images/benefits.png)

## Conclusion
Le projet Monitoring System représente une avancée significative pour l'infrastructure IT de l'entreprise, offrant des solutions de virtualisation, de surveillance et de gestion de haute qualité. Ce projet, bien que complexe, apporte une robustesse et une modernisation essentielles pour répondre aux besoins actuels et futurs de l’entreprise.

![Conclusion](images/conclusion.png)
