---
title: Outil AEM Repo
description: L’outil AEM Repo est une solution simple pour transférer du contenu JCR entre votre système de fichiers local et le serveur AEM via une ligne de commande comparable à FTP.
translation-type: tm+mt
source-git-commit: c40d668cb6dcf5c3e2d09504b547457306a99c85
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 51%

---


# Outil AEM Repo {#aem-repo-tool}

L’outil AEM Repo est une solution simple pour transférer du contenu JCR entre votre système de fichiers local et le serveur AEM via une ligne de commande comparable à FTP. L&#39;outil AEM Repo Tool est similaire au [module externe ](https://jackrabbit.apache.org/filevault-package-maven-plugin)Jackrabbit FileVault Maven &lt;a1/>, mais il est plus rapide, avec des dépendances minimales et est un script bash simple.

Cet outil simplifie le transfert de fichiers pour le développeur et peut également être intégré dans Eclipse et IntelliJ pour rendre le développement encore plus efficace.

## Présentation {#overview}

Pour un chemin donné dans une structure `jcr_root` FileVault sur le système de fichiers, l&#39;outil AEM Repo crée un package avec un filtre unique pour l&#39;ensemble de la sous-arborescence et l&#39;envoie au serveur (semblable au FTP `put`), le récupère du serveur ( `get`) ou compare les différences ( `status` et `diff`).

L&#39;outil ne prend pas en charge plusieurs chemins de filtre ou l&#39;élément `filter.xml` de FileVault.

>[!CAUTION]
>
>Veuillez noter que l’outil Repo AEM écrase toujours le fichier ou le répertoire spécifié dans son intégralité.

## Téléchargement et documentation  {#download-and-documentation}

L&#39;[AEM Repo Tool est disponible sur GitHub via ce lien](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/repo) ainsi que des instructions détaillées d&#39;installation et d&#39;utilisation.

Si vous souhaitez télécharger la source de l’outil Repo AEM, reportez-vous au projet GitHub ci-dessous.

CODE SUR GITHUB

Vous pouvez trouver le code de cette page sur GitHub.

* [Projet d&#39;outils ouverts sur GitHub](https://github.com/Adobe-Marketing-Cloud/tools)
* Téléchargez le projet sous la forme d’[un fichier ZIP](https://github.com/Adobe-Marketing-Cloud/tools/archive/master.zip).
