---
title: "Serveurs"
linkTitle: "Serveurs"
date: 2017-01-05
weight: 1
description: >
  A short lead descripton about this content page. It can be **bold** or _italic_ and can be split over multiple paragraphs.
---

# Pré-requis

## Compte sur les serveurs UNF

Il faut disposer d’un compte sur les serveurs informatiques de l’UNF pour pouvoir les utiliser.
Ce compte doit être personnel.

Pour obtenir un compte ou pour toutes questions contacter le [support UNF](mailto:support.unf@criugm.qc.ca).

# Prêt(e) !

## Connexion aux serveurs de calcul

### -> Linux ou Mac
Ouvrez un terminal sur votre ordinateur et connectez-vous à un des serveurs de l’UNF (elm ou jacaranda).

~~~bash
# Remplacer 'username' par votre identifiant de votre compte UNF
ssh -Y username@elm.criugm.qc.ca
~~~

Le serveur vous demandera alors le mot de passe de votre compte UNF.

### -> Windows 10

Vous trouverez les informations utiles [ici](https://docs.microsoft.com/fr-ca/windows/wsl/install-win10) pour installer le sous-système pour avoir accès à un terminal linux.
Suivez ensuite les instructions pour Linux et Mac.

## Votre espace

Vous avez accès à trois espaces de stockage différents pour différentes utilisations.

**HOME** et **DATA** sont des espaces de stockages à distance tandis que **SCRATCH** est un espace local (propre au serveur) qui doit être utilisé pour stocker temporairement des données le temps d'une analyse.

### -> HOME

Quand vous vous connectez sur elm ou jacaranda vous êtes directement dans votre **HOME**.
Chaque dossier HOME est restreint à 50Go par personne. Nous vous suggérons fortement de privilégier votre dossier DATA pour vos analyses.

~~~bash
/home/username
~~~

### -> DATA

~~~bash
# Trouver à quel groupe vous appartenez
id -gn
# Remplacer 'groupname' par le nom de votre groupe
# Remplacer 'username' par votre identifiant de votre compte UNF
cd /data/groupname/username
~~~


### -> SCRATCH

L'espace de scratch est spécifique à la machine à laquelle vous vous connectez.
C'est un espace qui doit être utilisé de façon temporaire pour lancer des analyses.

Une fois l'analyse terminée vous devrez déplacer vos données dans votre dossier **DATA**.

~~~bash
cd /scratch/
mkdir /scratch/username
~~~


## Sauvegarde de vos données

Pour ce qui est des comptes utilisateurs sur les serveurs de l'UNF (elm et jacaranda), Tous les documents dans vos **HOME** et ceux dans **DATA** sont sauvegardés respectivement les soirs pairs et impairs. Les documents dans **SCRATCH** ne sont pas sauvegardés. Notez que des copies des documents effacés sont conservés pendant un mois. C'est à dire que si vous créé un document dans votre **HOME**, qu'il a été sauvegardé pendant la nuit et que vous l’effacer ultérieurement vous avez un mois, à partir de la date de destruction du fichier, pour faire une demande de restoration avant qu'il ne disparaisse pour toujours. Les demandes de restauration peuvent être faite à <support.unf@criugm.qc.ca>. Aucune action de votre part n'est nécessaire pour activer les sauvegardes.

# Serveurs

| Nom | Mémoire | Coeurs |
|:----:|:-------:|:------:|
| elm | 252Go | 64 |
| jacaranda | 64Go | 25 |

## Outils d'analyse disponibles

L'ensemble des outils disponibles sur les serveurs se font à l'aide de la commande **module**. Ces outils sont centralisés ce qui vous permet d'obtenir les mêmes résultats que vous effectuyez vos analyses sur elm ou sur jacaranda.

~~~bash
# Liste des outils disponibles
module avail

# Liste des outils actifs
module list

# Activer un outil
module load freesurfer

# Désactiver un outil
module unload freesurfer
~~~

Si vous souhaitez ajouter un outils en particulier n'hésitez pas à nous envoyer un [mail](mailto:support.unf@criugm.qc.ca).