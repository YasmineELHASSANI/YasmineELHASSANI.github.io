---
title: Travaux pratiques Machine Virtuelle
subtitle: Systèmes informatiques - 1e année
layout: product
image: https://via.placeholder.com/640x480
---

<h1>1-Introduction</h1>

<h2>1.1-Présentation</h2>

L’objectif du TP1 de système informatique est de configurer une machine bureautique et une machine serveur afin de prendre en main un système d’exploitation GNU/Linux plus précisément la distribution Ubuntu.
Nous allons donc configurer des machines virtuelles c’est-à-dire un système informatique possédant son propre processeur, son espace mémoire, son interface réseau et son espace de stockage mais installé sur un système physique (notre machine physique sur laquelle nous configurons la machine virtuelle).

<h2>1.2-Les outils</h2>

Pour réaliser ce TP nous avons besoin :
* Du logiciel VirtualBox pour installer nos machines virtuelles.
* Le système d’exploitation Ubuntu et les information fournie par son site officiel (voir lien en annexe)

<h1>2-Machine bureautique – Ubuntu Desktop</h1>

<h2>2.1-Présentation</h2>

Nous allons commencer par configurer la machine bureautique grâce aux information fournie par le TP et le site Ubuntu. La machine doit donc posséder un processeur dual-core cadencé à 2GHz, 4 GB de mémoire vive (RAM) soit 4096 MB, 50 GB de stockage comprenant 2 partitions.
Pour commencer à créer notre nouvelle machine il faut télécharger l’image ISO (International Organization for Standardization) d’Ubuntu. L'extension de fichier ISO ne se contente pas de stocker des fichiers et des dossiers : elle contient toutes les informations vitales du système de fichiers concernant la structure du disque. Ubuntu utilise le sytème Linux. 
Pendant le téléchargement de l’image ISO, on s’assure que le logiciel de virtualisation VirtualBox est installé sur la machine. Si ce n’est pas le cas, on peut télécharger l’installeur sur le site officiel d’Oracle (voir le lien en annexe) puis procéder à l’installation.

<h2>2.2-Création de la machine et allocution</h2>

Nous allons ouvrir VirtualBox et cliquer sur nouvelle (sous-entendue nouvelle machine). Tout d’abord nous choisissons un nom à notre machine, puis lui assignons le Bureau de l’ordinateur comme lieu de stockage pour le retrouver plus facilement et enfin nous sélectionnons l’image ISO Ubuntu Desktop.
Ensuite on configure les caractéristiques en termes de processeurs et d’espace de stockage cité dans 
le 2.1 du rapport (2 cœurs du processeur, 4 Go de ram soit 4096 MB et 50 Go d’espace disque).

<h2>2.3-Lancement de la machine et installation d’Ubuntu</h2>

Sur cette machine, l’utilisateur souhaite pouvoir utiliser au minimum 6 Go pour stocker ses documents, nous plaçons cette partition dans /home. Elle contiendra tous les répertoires utilisateur. Nous dédions le reste de l’espace disque à la partition / (c’est la partition racine).
Passons à la configuration de l’utilisateur : nous devons définir un utilisateur principal avec lequel on peut se connecter à la machine. Pour des raisons de simplicité, nous choisissons « ubuntu » comme nom d’utilisateur et mot de passe mais il est important de garder à l’esprit qu’un mot de passe robuste est à prescrire pour une machine utilisée en dehors d’un exercice pour des raisons de sécurité. L’installeur Ubuntu ajoute automatiquement cet utilisateur au groupe « sudo » qui permet d’exécuter des commandes en tant que super-utilisateur, ce n’est cependant pas le cas pour toutes les distributions.
Après l’installation, la machine virtuelle redémarre pour laisser place à Ubuntu. Prenons maintenant en main le système Ubuntu.

<h2>2.4-Prise en main du système</h2>

La première chose à faire après l’installation du système est la mise à jour des paquets (bien qu’elle soit faite par l’installeur). Rappelons que Ubuntu est basé sur Debian et utilise donc le gestionnaire de paquet apt. Ici update met à jour la liste des paquets et leurs versions et upgrade met à jour les paquets dans leur dernière version.
La consigne nous demande de nous familiariser avec l’environnement. Pour cela, installons une application en utilisant la logithèque.

<h1>3-Machine serveur – Ubuntu Server</h1>

<h2>3.1-Préparation</h2>

La machine virtuelle Ubuntu Desktop est installée et fonctionnelle, passons maintenant à l’installation de la machine virtuelle Ubuntu Server.
Pour Ubuntu Server nous allons suivre les étapes précédente mais pour une machine serveur. La différence réside dans la présentation. En effet, Ubuntu Server ne possède pas d’interface graphique donc tout se fait en ligne de code. 
Nous allons créée une nouvelle machine virtuelle avec la même démarche. Les caractéristiques de la nouvelle machine sont :
* Un processeur mono-core cadencé à 1GHz
* 1 GB de mémoire vive (RAM)
* 30 GB de stockage comprenant 2 partitions
  
Comme pour Ubuntu Desktop, on utilise une disposition de stockage personnalisée : l’utilisateur veut restreindre la partition contenant son espace personnel (/home) à 10 Go.

<h1>4-Installation d’Apache2</h1>

Comme précédemment, dès l’installation terminée et le redémarrage effectué, nous pensons à mettre à jour les paquets, puis nous passons à l’installation et la configuration du serveur http Apache2.
Nous installons apache2 avec la commande apt. Apache2 est un logiciel qui permet d’envoyer du contenu lisible à l’utilisateur (celui qui effectue une requête au serveur) via le serveur http. Dans ce cas l’adresse de la requête est sur le port 80. 
Après avoir installé Apache2 on l’active.

<h1>5-Page par défaut</h1>

Nous allons personnaliser notre page par défaut. Pour cela nous allons chercher le document index.html dont l’adresse absolue est /var/www/html. Nous supprimons le fichier (commande rm-rf, supprimer sans rien demander en retour possible seulement grâce aux droit de superadministrateur) et en recréons un du même nom grâce à l’éditeur de texte nano.
Pour pouvoir lire ce nouveau fichier il faut passer le mode d’accès réseau de NAT à Accès par pont pour que l’adresse de la machine virtuelle et celle de la machine physique sur laquelle on a configuré notre nouvelle machine soit la même. Après cette étape nous devons récupérer l’adresse de la machine avec la commande ip a. Cette commande nous donne les caractéristiques des interfaces réseau.
Maintenant pour lire notre document nous allons sur le navigateur de notre machine physique (machine hôte) et nous entrons l’adresse ip de la machine précédé de http.

<h1>6-Conclusion</h1>

Ce TP nous a permis de découvrir la création d’une machine virtuelle et la configuration d’Ubuntu. 
Nous nous sommes familiarisés avec l’utilisation des lignes de commandes les plus utiles lors de ce genre de réalisation. On en tire la conclusion suivante : l’utilisation d’une machine virtuelle facilite grandement l’introduction aux systèmes d’exploitation basés sur le noyau Linux.

<h1>7-Annexes</h1>

Site officiel Ubuntu : https://www.ubuntu-fr.org/

site officiel d’Oracle : https://www.virtualbox.org/
