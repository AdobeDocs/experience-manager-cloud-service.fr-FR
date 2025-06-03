---
title: Repository Modernizer (CAM)
description: Découvrez comment restructurer les packages de projets existants et les rendre compatibles avec la structure de projet définie pour Adobe Experience Manager as a Cloud Service.
feature: Migration
role: Admin
source-git-commit: 317ee65786d48d7b92d95c7c6b8782f617d6e346
workflow-type: tm+mt
source-wordcount: '1099'
ht-degree: 18%

---


# Repository Modernizer (CAM) {#repo-modernizer-cam}

Repository Modernizer est un utilitaire conçu pour restructurer les packages de projets existants en séparant le contenu et le code en packages discrets compatibles avec la structure de projet définie pour Adobe Experience Manager as a Cloud Service.

## Présentation {#introduction}

Adobe Experience Manager as a Cloud Service offre de nombreuses nouvelles fonctionnalités et possibilités pour vos projets AEM. Toutefois, certains changements sont nécessaires pour que les projets Maven Adobe Experience Manager soient compatibles avec AEM Cloud Service. À un niveau élevé, AEM exige une séparation du **contenu** et du **code** en sous-packages discrets pour respecter la division entre le contenu mutable et le contenu non mutable. Pour plus d’informations sur la nouvelle structure de projet AEM pour Cloud Service, reportez-vous à [Structure de projet AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html?lang=fr).

Repository Modernizer crée une structure de projet AEM Cloud Service compatible en créant la structure de déploiement suivante :

- Le package `ui.apps` se déploie sur `/apps` et contient l’intégralité du code.

- `ui.content` package se déploie sur des zones pouvant être écrites à l’exécution (par exemple, `/content`, `/conf`, `/home` ou toute zone non `/apps`) et contient l’ensemble du contenu et de la configuration.

- Le package `all` est un package de conteneur qui contient les sous-packages `ui.apps` et `ui.content`.

>[!NOTE]
>
> La structure de projet est basée sur _Archetype 48_ pour les packages et leurs `pom.xml/filter.xml files`. Pour plus d’informations, voir [Archetype 48](https://github.com/adobe/aem-project-archetype).

Repository Modernizer prend désormais en charge les types de projets suivants :

- **MULTI_PROJECT** : représente un projet multimodule sans POM parent commun, Dispatcher et tous les modules.
- **SINGLE_PROJECT** : représente un seul projet.
- **NESTED_PROJECT** : représente un projet multimodule avec un POM parent commun, le Dispatcher et tous les modules.
- **MONOLITHIC_PROJECT** : représente un projet principal avec un ou plusieurs sous-projets.

## Utilisation de Repository Modernizer {#using-repo-modernizer}

>[!VIDEO](https://video.tv.adobe.com/v/333057/?quality=12&learn=on)

- Repository Modernizer est désormais appelé automatiquement par le service de refactorisation, sous l’onglet Tâche de refactorisation . Les clients doivent simplement charger leur projet et déclencher la tâche de refactorisation, aucune configuration supplémentaire n’est nécessaire.

## Référence du code d’erreur

Si vous rencontrez un code d’erreur lors de l’utilisation de Repository Modernizer, reportez-vous au tableau ci-dessous pour obtenir des détails et connaître les actions recommandées.

| Code d’erreur | Message | Description | Action de l’utilisateur requise ? |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- | --------------------- |
| RM-100 | Erreur lors de la conversion du fichier de configuration OSGi {0} au format .cfg.json. Validez le fichier de configuration existant avant de réessayer. | Cette erreur se produit en cas de problème lors de la transformation d’un fichier de configuration OSGi au format .cfg.json. | Oui |
| RM-101 | Erreur lors de la tentative de copie du contenu de : {0} | Cette erreur se produit en cas d’échec lors de la tentative de copie de contenu à partir de la source spécifiée. | Non |
| RM-102 | Erreur lors de la tentative de déplacement du fichier {0} de {1} vers {2}. | Cette erreur se produit lorsqu’un problème se produit lors du déplacement d’un fichier d’un emplacement à un autre. | Non |
| RM-103 | Impossible de résoudre le chemin donné en un fichier valide : {0} | Cette erreur se produit lorsque le fichier est introuvable à l’emplacement donné. | Non |
| RM-104 | Une erreur s&#39;est produite lors de l&#39;itération sur le contenu de {0}. | Cette erreur se produit lors de la traversée de fichiers ou de répertoires, indiquant un problème d’accès ou de traitement du contenu. | Non |
| RM-105 | Erreur lors de l&#39;analyse du fichier XML : {0}. Validez le fichier XML avant de réessayer. | Cette erreur se produit en cas d’échec de l’analyse du fichier XML. | Oui |
| RM-106 | Erreur lors de l&#39;écriture dans le fichier XML : {0}. | Cette erreur se produit en cas de problème d’écriture dans le fichier XML. | Non |
| RM-107 | Aucun package de contenu trouvé dans le projet existant : {0}. Vérifiez que le projet correct a été chargé. | Cette erreur indique qu’aucun package de contenu n’a été trouvé dans le projet existant. | Oui |
| RM-108 | Fichier POM introuvable au chemin d&#39;accès attendu : {0}. Le fichier POM du projet ou du module doit se trouver directement dans son répertoire en tant que fichier enfant. | Cette erreur se produit lorsque le fichier POM est introuvable à l’emplacement attendu. | Oui |
| RM-109 | Erreur lors de l&#39;analyse du fichier pom.xml : {0}. Validez le fichier pom avant de réessayer. | Cette erreur se produit en cas de problème lors de l’analyse du fichier pom.xml. | Oui |
| RM-110 | Erreur lors de l&#39;écriture dans le fichier pom.xml : {0}. | Cette erreur se produit en cas de problème d’écriture dans le fichier pom. | Non |
| RM-111 | Erreur lors de l&#39;écriture dans le fichier de rapport. | Cette erreur se produit en cas d’échec lors du processus d’écriture dans le fichier de rapport. | Non |
| RM-112 | {0} est introuvable dans le fichier pom de la structure de référentiel à ({1}) | Cette erreur se produit lorsque la configuration attendue est introuvable dans le modèle d’archétype de projet AEM. | Non |
| RM-113 | Erreur lors de la tentative de copie des modèles de l’archétype de projet AEM vers la destination. | Cette erreur se produit en cas de problème de copie des modèles de l’archétype de projet AEM vers la destination. | Non |
| RM-115 | Erreur lors de la tentative de connexion au stockage Azure Blob. | Cette erreur se produit lorsqu’un problème se produit lors de la connexion au stockage Blob Azure. | Non |
| RM-116 | Erreur lors de la tentative de chargement du fichier : {0} vers Azure Blob Storage. | Cette erreur se produit en cas de problème de chargement d’un fichier dans Azure Blob Storage. | Non |
| RM-117 | Erreur lors de la tentative de téléchargement du fichier : {0} depuis Azure Blob Storage. | Cette erreur se produit lorsqu’un problème se produit lors du téléchargement d’un fichier depuis Azure Blob Storage. | Non |
| RM-118 | Une erreur d&#39;E/S s&#39;est produite lors de la gestion de : {0}. | Cette erreur se produit en cas de problème de lecture ou d’écriture dans un fichier de projet. | Non |
| RM-119 | Erreur d’E/S lors de la tentative d’archivage des résultats pour le chargement vers Azure. | Cette erreur se produit lorsqu’une erreur se produit lors de l’archivage des résultats générés par le processus. | Non |
| RM-120 | Erreur d’E/S lors de la tentative de désarchivage du fichier ZIP du projet fourni. Vérifiez si le fichier ZIP du projet fourni est valide. | Cette erreur se produit lorsqu’une erreur se produit lors de l’annulation de l’archivage du projet client donné. | Oui |
| RM-121 | Erreur lors de l&#39;écriture dans le fichier de configuration. | Cette erreur se produit en cas d’échec lors du processus d’écriture dans le fichier de configuration. | Non |
| RM-122 | Type de requête non pris en charge : {0}. | Cette erreur se produit lorsque le type de requête n’est pas pris en charge par le système. Vérifiez le type de requête et réessayez. | Non |

## Comprendre les conclusions et les priorités du rapport

Lorsque vous téléchargez le rapport des résultats généré par l’outil Repository Modernizer, chaque résultat se voit attribuer une **priorité**. Ces priorités vous aident à comprendre l’urgence et l’impact de chaque problème :

| Priorité | Description |
| -------- | ----------------------------------------------------------------------------------------------- |
| CRITIQUE | Doit être résolu pour réussir la création du projet. |
| ÉLEVÉE | Doit être résolu pour s’assurer que la fonctionnalité n’est pas endommagée dans AEM. |
| NORMAL | Cette question devrait être résolue pour garantir la santé mentale et l&#39;exhaustivité de la modernisation. |
| FAIBLE | Pour une vérification manuelle, ces résultats sont informatifs et peuvent ne pas nécessiter d&#39;action immédiate. |

>[!NOTE]
> 
>Il est recommandé de traiter d’abord les conclusions les plus prioritaires afin d’assurer un processus de modernisation et de déploiement sans heurts.
