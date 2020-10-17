---
title: "Téléchargez vos données"
linkTitle: "Télécharger vos données"
date: 2020-03-06
weight: 2
type: "docs"
description: >
  Récupération de vos données
---

Afin de télécharger vos données vous avez deux possibilités:
- Utiliser un client SFTP (Windows, Mac, Linux)
- Utiliser un terminal (Linux, Mac)

# Utilisation d'un client SFTP

## Installation

Filezilla est un logiciel disponible sur tous les OS (Windows, Mac, Linux) que nous recommandons. Vous pouvez le télécharger en suivant le lien suivant [Filezilla](​https://filezilla-project.org/​)

## Configuration - première utilisation

Démarrez Filezilla et ouvrez le menu File -> Site Manager
Vous devriez obtenir la fenêtre suivante:


Créez un nouveau site que vous pouvez nommer 'unf-dicom' par exemple et remplissez les différents champs:
*Host*: elm.criugm.qc.ca
*Protocol*: SFTP-SSH File Transfer Protocol
*Login Type*: Ask for password
*User*: c'est le nom d'usager UNF qui vous a été créé lorsque vous avez fait votre demande [ici]()

Ensuite cliquer sur le bouton *Connect*
Vous devriez voir apparaitre la fenêtre suivante:

Cliquez sur `Always trus` et cliquez sur OK

Finalement Filezilla vous demandera votre mot pas de passe UNF comme présenter dans la fenêtre suivante:

IMAGE

En rouge vous trouvez votre système de fichier sur votre ordinateur.
En vert, le système de fichier sur le serveur.

Vous pouvez déplacer des fichiers de droite à gauche ou inversement pour télécharger et/ou envoyer des données sur le serveur.

# Utilisation du terminal (Mac, Linux, Windows usagers avancés)

Ouvrez un terminal et utilisez la commande ssh pour récupérer vos données IRM dans une archive tar.gz. Remplassez les champs unf_login et le chemin vers vos dicoms ainsi que le fichier tar.gz de destination

## Télécharger un dossier et créer une archive tar.gz
`ssh unf_login@elm.criugm.qc.ca tar czf - /path/vers/vos/dicom/ > fichier_destination_sur_votre_ordinateur.tar.gz`

## Télécharger une archive tar.gz

`rsync -azv unf_login@elm.criugm.qc.ca:/unf/dicoms/by_groups_tar/chemin_vers_vos_dicoms dossier_destination_sur_votre_ordinateur`

# Accès à vos données IRM

Vos données IRM peuvent se trouver à 3 différents endroits.

- `/unf/bids` si vous avez demandé/coordonné une conversion BIDS automatique
- `/unf/dicoms/by_groups_tar/` si vos données sont relativement vieilles (avant 2016)
- `/unf/dicoms/by_groups/` si vos données ont été acquises plus récemment

Connectez-vous sur les serveurs afin de
