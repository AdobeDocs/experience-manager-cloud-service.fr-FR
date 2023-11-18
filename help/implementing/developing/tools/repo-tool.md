---
title: Outil AEM Repo
description: L’outil AEM Repo est une solution simple pour transférer du contenu JCR entre votre système de fichiers local et le serveur AEM via une ligne de commande comparable à FTP.
exl-id: fb887ba3-e40b-4ab1-b142-0748c6d9f18e
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 93%

---

# Outil AEM Repo {#aem-repo-tool}

L’outil AEM Repo est une solution simple pour transférer du contenu JCR entre votre système de fichiers local et le serveur AEM via une ligne de commande comparable à FTP. L’outil AEM Repo est similaire au [module externe Jackrabbit FileVault Maven](https://jackrabbit.apache.org/filevault-package-maven-plugin), à la différence qu’il est plus rapide, a des dépendances minimales et est un simple script Bash.

Cet outil simplifie les transferts de fichiers qu’effectuent le développeur et peut également être intégré à Eclipse et IntelliJ pour optimiser l’activité de développement.

## Vue d’ensemble {#overview}

Pour un chemin donné dans une structure `jcr_root` FileVault sur le système de fichiers, AEM Repo Tool crée un package avec un seul filtre pour l’ensemble de la sous-arborescence et le transmet via push au serveur (similaire à la méthode `put` du FTP), l’extrait du serveur (`get`) ou compare les différences (`status` et `diff`).

Cet outil ne prend pas en charge les chemins de filtre multiples ou `filter.xml` de FileVault.

>[!CAUTION]
>
>L’outil AEM Repo Tool remplace toujours l’intégralité du fichier ou du répertoire spécifié.

## Téléchargement et documentation {#download-and-documentation}

L’outil [AEM Repo Tool est disponible sur GitHub via ce lien](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/repo) et s’accompagne d’instructions d’installation et d’utilisation détaillées.

Si vous souhaitez télécharger la source de l’outil Repo AEM, consultez le projet GitHub lié ci-dessous.

CODE SUR GITHUB

Vous pouvez trouver le code de cette page sur GitHub.

* [Ouvrir le projet outils sur GitHub](https://github.com/Adobe-Marketing-Cloud/tools)
* Téléchargez le projet sous la forme d’[un fichier ZIP](https://github.com/Adobe-Marketing-Cloud/tools/archive/master.zip).
