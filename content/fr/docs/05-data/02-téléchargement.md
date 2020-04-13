---
title: "Téléchargements"
linkTitle: "Téléchargements"
date: 2017-01-05
weight: 2
description: >
  A short lead descripton about this content page. It can be **bold** or _italic_ and can be split over multiple paragraphs.
---

# 1. Depuis les serveurs de l'UNF

## Connexion aux serveurs

### Linux ou Mac
Ouvrez un terminal sur votre ordinateur et connectez-vous à un des serveurs de l’UNF (elm ou jacaranda).

~~~bash
# Remplacer 'username' par votre identifiant de votre compte UNF
ssh -Y username@elm.criugm.qc.ca
~~~

Le serveur vous demandera alors le mot de passe de votre compte UNF.

### Connexion via Windows 10

Vous trouverez les informations utiles [ici](https://docs.microsoft.com/fr-ca/windows/wsl/install-win10) pour installer le sous-système pour avoir accès à un terminal linux.
Suivez ensuite les instructions pour Linux et Mac.

## Format des données IRM

Vos données aquises à l'IRM sont accessibles en deux formats distincts:

- BIDS (Brain Image Data Structure)
- DICOMS (format brute)

Afin de connaitre le chemin vers vos données, il vous faut savoir le groupe principal (GID) auquel vous appartenez:
~~~bash
# Trouver à quel groupe vous appartenez
id -gn
~~~

## Accès à vos données BIDS

Si vous avez accepté que vos données soient converties en BIDS automatiquement vous trouverez ces données converties en faisant cette commande:

~~~bash
# Remplacer 'GID' par votre groupe principal
cd /unf/bids/GID/NomDeVotreProjet
~~~

## Accès à vos données dicoms IRM

Si vous ne souhaitez pas utiliser les données BIDS converties ou que vous nVous trouverez l'ensemble de vos données au format DICOM à cet emplacement

~~~bash
# Remplacer 'GID' par votre groupe principal
cd /unf/dicoms/by_groups_flat/GID/NomDeVotreProjet
~~~

# 2. Depuis la plateforme de l’UNF sur votre propre ordinateur

La solution la plus simple et pratique pour la récupération des données de neuroimagerie acquises à l’unité de neuroimagerie fonctionnelle (UNF) est d’utiliser la plateforme mise à disposition sur le site internet de l’UNF.
Cette plateforme s’occupe de la préparation des données et de leur compression pour un téléchargement et partage simplifié. Tous les scans fait à l'UNF sont archivés en deux copies, une copie sur le serveur web ou vous pouvez récupérer vos images, et une copie sur notre système d'archivage. Les scans sont archivés et accessibles ad vitam æternam. Il n'est donc pas nécessaire pour vous de faire des sauvgardes supplémentaires de vos scans.
Elle est accessible soit depuis **le site internet de l‘[unité de neuroimagerie](http://www.unf-montreal.ca)** (Menu `Services` puis `Récupération des données IRM`), soit directement depuis **la [plateforme de téléchargement](https://unf-montreal.ca)**.

![Page d’accueil de l’UNF](/images/docs/fr/website_home.png)

## Préparation des données

1. Connectez-vous à [https://unf-montreal.ca](https://unf-montreal.ca)
2. Entrer votre identifiant et mot de passe de votre compte UNF
3. Sélectionner les données à récupérer et cliquer sur `Préparer les images` (garder le choix par défaut pour la compression des images `tar.gz`)
4. Donner un nom à l’archive à télécharger, pour notre exemple `unf-data` et cliquer sur `Soumettre`

![Interface pour télécharger des sessions d’imagerie](/images/docs/fr/unf_get_data.png)

Les données seront prêtes à télécharger après quelques instants.
**Ne fermez pas** votre fenêtre de navigation, nous y reviendrons après.

## Téléchargement des données

Une fois que le lien pour de téléchargement est prêt vous pouvez télécharger vos données sur votre ordinateur.

Pendant ce temps, ouvrez un terminal sur votre ordinateur et connectez-vous en ssh à un des serveurs de l’UNF (elm ou jacaranda).

~~~bash
# Remplacer 'username' par votre identifiant de votre compte UNF
ssh -Y username@elm.criugm.qc.ca
~~~

Le serveur vous demandera alors le mot de passe de votre compte UNF.

![Connexion SSH à elm](/images/docs/terminal_ssh.png)

Une fois connecté, naviguez  dans votre répertoire de données :

~~~bash
# Remplacer 'labname' par le nom du laboratoire
# Remplacer 'username' par l’identifiant de votre compte UNF
cd /data/labname/username/
~~~

Au besoin, créez un nouveau répertoire pour votre projet et déplacez-vous dans ce répertoire :

~~~bash
# Remplacer 'project_name' par le nom du projet
mkdir project_name

# Aller dans le nouveau répertoire
cd project_name
~~~

Téléchargement des données préparées par l’UNF :

1. Retourner sur la page internet du site internet de l’UNF (si vous avez fermé votre navigateur, le lien est disponible pendant 7 jours dans la section `Services/Récupération des données IRM`)
2. Dans l’encadré en bas à gauche de la fenêtre, vous trouverez le lien (en bleu) des données préparées (le nom donné auparavant, comme 'unf-data.tar.gz'). **Copier le lien préparé par le système (clic droit, `Copier le lien`/`Copy link location`)**, dans notre exemple `http://downloads.criugm.qc.ca/username/unf-data.tar.gz`
3. Dans le terminal, entrer la commande suivante pour télécharger les données

~~~bash
# Taper wget puis un espace et faite un clic droit `Coller` ou control-shift-v
wget http://downloads.criugm.qc.ca/username/unf-data.tar.gz
~~~

![Téléchargement des données avec WGET](/images/docs/terminal_wget.png)

Vos données sont maintenant prêtes à être converties pour TOAD ([voir section '3 Conversion des données'](#conversion)).