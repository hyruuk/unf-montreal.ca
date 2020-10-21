---
title: "Download your MRI data"
linkTitle: "Download your MRI data"
date: 2020-10-18
weight: 2
type: "docs"
description: >
  Récupération de vos données IRM
---

## Requirements

In order to download your data you need a __[UNF account](../../../en/documentation/welcome/account/)__.
You also need to know your group.

You have two different ways to get your MRI data:
- Use a SFTP client (Windows, Mac, Linux)
- Use a terminal (Linux, Mac)

## How to use a SFTP client

### Installation

Filezilla client is a multiplatform software (Windows, Mac, Linux) that we recommand. You can download it using the following link __[Filezilla](​https://filezilla-project.org/​)__

![Menu](/images/documentation/fr/download_mri/filezilla-menu.png)

### Configuration - first use

Start Filezilla and open menu menu File -> Site Manager
You should see the following window:

![Configuration](/images/documentation/fr/download_mri/filezilla-config.png)

Create a new site that you can name __unf-dicom__ for instance and fill the following fields:

**Host**: elm.criugm.qc.ca

**Protocol**: SFTP-SSH File Transfer Protocol

**Login Type**: Ask for password

**User**: this is the UNF username we've created when you asked for an [account](https://unf-montreal.ca/en/documentation/welcome/account/).

Then, click the *Connect* button.

The following window could show up.

![Certificate](/images/documentation/fr/download_mri/filezilla-trust.png)

Tick `Always trust` and click OK.

It will prompt for your UNF password:

![password](/images/documentation/fr/download_mri/filezilla-password.png)

Enter it, click OK, you are now connected.

![Main window](/images/documentation/fr/download_mri/filezilla-main_window.png)

- Red: your computer file system
- Bleu: the computer file system on the server
- Vert: path used for the server

You can move data from left to right or right to left to download or upload data on the server.

## Using the terminal (Mac, Linux, Windows advanced users)

Open a terminal and use the ssh command to get your MRI data into a tar.gz archive. Don't forget to use your own unf_login and change the path to your data and the destination.

- Download a folder and put everything into a tar.gz archive

`ssh unf_login@elm.criugm.qc.ca tar czf - /path/to/your/dicom/ > destination_file_on_your_computer.tar.gz`

- Download a tar.gz archive

`rsync -azv unf_login@elm.criugm.qc.ca:/unf/dicoms/by_groups_tar/path_to_your_data destination_folder_on_your_computer`

## Access to your MRI data

Your MRI data can be at 3 different places. Don't forget to change groupeName by your own group.

- `/unf/bids/groupName` if you asked and coordinated the automatic BIDS conversion
- `/unf/dicoms/by_groups_tar/groupName` if your data are somehow old (before 2016)
- `/unf/dicoms/by_groups/groupName` if your data have recently been acquired.

If you need help to have access to your MRI data please don't hesitate to send us an email using the following link: __[support.unf](mailto:support.unf@criugm.qc.ca?subject=Help-Download-MRI)__.
