---
title: Migration vers le service Cloud à partir d’Adobe Experience Manager 6.x
description: Migration vers le service Cloud à partir d’Adobe Experience Manager 6.x
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Déplacement vers Adobe Experience Manager Assets as a Cloud Service {#move-to-assets-cloud-service}

<!-- About the need to move from previous AEM deployment to a cloud service deployment. And how does Adobe help do it OOTB?
-->

## A propos de l’outil de migration {#migration-tool}

<!-- 
Link back to information about the tool in the Experience Manager as a Cloud Service docs if the tool works the same for Sites and Assets. Document the Assets-specific information here.

* What is the migration tool called? Is there a branding term for it?
* How much do we want to elaborate about the Pattern Detector rules? Is there a branding term for it?
* Before migrating using the tool, is any prepping required?
* See CQ-4271901

-->

L’outil de migration permet d’effectuer les opérations suivantes :

* Convertissez les modèles de processus existants en profils de traitement qui fonctionnent avec le service de calcul des ressources.
* Supprimez les étapes non prises en charge des modèles de processus.
* Désactivez les lanceurs de processus.
* Fusionnez les configurations, après confirmation/validation de l’utilisateur, dans le code source existant.

L’outil de migration crée des profils de traitement dans un module expert que les utilisateurs peuvent utiliser de deux manières :

* Fusion dans l’un de leurs projets existants.
* Ajoutez le module en tant que nouveau sous-module.

L’outil de migration fournit un rapport sur les modifications qu’il a apportées et des informations sur les modifications.

<!--  

What is the output of the tool, besides migrated content.

Give details about reports and logs of the tool. 

* How to access the report, including required permissions.
* How to read/interpret the report.
* Location of logs. How to read the logs.
* What common errors to look for. Troubleshooting for these errors.

-->

## Migration de contenu vers un nouveau déploiement {#content-migration-across-deployments}
