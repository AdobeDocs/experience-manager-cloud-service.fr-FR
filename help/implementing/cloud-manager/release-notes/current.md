---
title: Notes de mise à jour de Cloud Manager 2024.10.0 dans Adobe Experience Manager as a Cloud Service
description: Découvrez les notes de mise à jour de Cloud Manager 2024.10.0 dans AEM as a Cloud Service.
feature: Release Information
role: Admin
source-git-commit: b90ace2250277005d8ac250c841104c93298a605
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 15%

---

# Notes de mise à jour de Cloud Manager 2024.10.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager version 2024.10.0 dans AEM as a Cloud Service.

>[!NOTE]
>
>Consultez les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Date de publication {#release-date}

La date de publication de Cloud Manager version 2024.10.0 dans AEM as a Cloud Service est le 3 octobre 2024.

La prochaine version est prévue pour le vendredi 14 novembre 2024.

## Nouveautés {#what-is-new}

* <!-- BOTH CS & AMS --> La version AEM Archetype utilisée dans Cloud Manager est désormais mise à jour vers la version 26. Voir [https://github.com/adobe/aem-project-archetype/releases](https://github.com/adobe/aem-project-archetype/releases)

<!-- (CMGR-59817) -->

* <!-- CS ONLY --> Lorsque vous ajoutez ou modifiez une infrastructure réseau, les valeurs des champs Adresse IP et Masque réseau sont validées selon les règles suivantes :

   * L’espace d’adresse ne doit pas chevaucher les adresses définies dans l’espace d’adresse de connexion.
   * Les adresses DNS doivent appartenir au masque de réseau défini dans l&#39;espace d&#39;adressage de la connexion ou être publiques.

  ![Boîte de dialogue Ajouter une infrastructure réseau](/help/implementing/cloud-manager/release-notes/assets/network-infrastructure-add.png)

* <!-- CS ONLY --> Des modifications sont apportées au format des journaux de déploiement de l’environnement pour l’indexation, l’installation de contenu modifiable et la transformation de tâches.

  >[!NOTE]
  >
  >Ce changement devrait être échelonné et devrait être achevé en décembre 2024.

  ![Déployer sur la carte de production](/help/implementing/cloud-manager/release-notes/assets/deploy-to-production-card.png)

  Le format du journal va changer à partir d’une entrée simple vue dans ce qui suit :

  ![Fichier journal présentant des entrées simples](/help/implementing/cloud-manager/release-notes/assets/log-file-simple-entry.png)

  À une entrée JSON vue dans :

  ![Fichier journal affichant les entrées json](/help/implementing/cloud-manager/release-notes/assets/log-file-json-entry.png)


## Programme d’adoption précoce {#early-adoption}

Faites partie du programme Cloud Manager d’adoption anticipée et avez la possibilité de tester les fonctionnalités à venir.

### Apportez votre propre Git - avec prise en charge de GitLab et Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

La fonctionnalité **Bring Your Own Git** a été étendue pour inclure la prise en charge de référentiels externes tels que GitLab et Bitbucket. Cette nouvelle prise en charge s’ajoute à la prise en charge déjà existante des référentiels GitHub privés et d’entreprise. Lorsque vous ajoutez ces nouveaux repos, vous pouvez également les lier directement à vos pipelines. Vous pouvez héberger ces référentiels sur des plateformes cloud publiques ou dans votre cloud ou infrastructure privée. Cette intégration élimine également la nécessité d’une synchronisation constante du code avec le référentiel d’Adobe et permet de valider les requêtes d’extraction avant de les fusionner dans une branche principale.

Voir [Ajout de référentiels externes dans Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

![Boîte de dialogue Ajouter un référentiel](/help/implementing/cloud-manager/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Actuellement, les contrôles de qualité du code de demande d’extraction prêts à l’emploi sont exclusifs aux référentiels hébergés par GitHub, mais une mise à jour pour étendre cette fonctionnalité à d’autres fournisseurs Git est en cours d’élaboration.

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un email à [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) à partir de votre adresse électronique associée à votre Adobe ID. Veillez à inclure la plateforme Git à utiliser et si vous utilisez une structure de référentiel privée/publique ou d’entreprise.


<!-- ## Bug fixes




## Known Issues {#known-issues} -->
