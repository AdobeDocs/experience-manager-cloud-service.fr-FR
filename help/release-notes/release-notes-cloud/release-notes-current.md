---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: fa106c2e3fec70971e2c54572199e35c24db0aa7
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 38%

---

# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour techniques de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2021 ou 2022.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle (2024.1.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le vendredi 25 janvier 2024. La prochaine mise à jour des fonctionnalités (2024.2.0) est prévue pour le vendredi 29 février 2024.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the December 2023 Release Overview video for a summary of the features added in the 2023.12.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3425864?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Extension Manager dans AEM Sites {#sites-extension-manager}

**Découvrez la nouvelle [Extension Manager dans AEM Sites](https://developer.adobe.com/uix/docs/extension-manager/)** pour personnaliser votre configuration AEM en configurant les extensions de l’interface utilisateur.

![Extension Manager dans AEM Sites](/help/assets/sites/extension-manager/homepage.png)

L’Extension Manager dans AEM Sites permet aux développeurs et aux professionnels d’accéder aux extensions de l’interface utilisateur, de les gérer et de les personnaliser afin d’améliorer les fonctionnalités d’AEM Sites.
Avec l’Extension Manager, vous pouvez :

* Activer ou désactiver des extensions pour chaque instance ;
* Configuration des paramètres d’extension ;
* Prévisualisez les extensions et générez un lien d’aperçu partageable.
* Découvrez les fonctionnalités d’extensibilité de l’interface utilisateur au moyen de démonstrations interactives ;
* Accédez aux fonctionnalités expérimentales d’Adobe par le biais d’extensions propriétaires.

Nous recherchons activement des commentaires et de nouveaux cas d’utilisation pour les extensions de l’interface utilisateur. Si vous souhaitez vous connecter, veuillez envoyer un email à `uix@adobe.com`.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Fonctionnalités de préversion de la vue d’administration {#admin-view-prerelease}

**Aperçu des rendus pour tous les types de vidéo pris en charge**

Experience Manager Assets génère désormais par défaut des rendus d’aperçu de tous les types de vidéo pris en charge sans nécessiter de configuration de profil de traitement.

### Affichage des ressources {#assets-view-features}

**Liste bloquée des balises intelligentes**

Assets Essentials vous permet désormais de définir une liste bloquée contenant des mots qui ne doivent pas être ajoutés en tant que balises intelligentes aux ressources chargées dans le référentiel. Cette fonctionnalité vous aide à maintenir la conformité de la marque et réduit les efforts de modération des balises intelligentes.

![Liste bloquée Balises intelligentes](/help/assets/assets/block-tags.png)


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Programme d&#39;adoption précoce {#forms-early-adopter}

* **[Envoyer un formulaire adaptatif au scénario de fusion Adobe Workfront](/help/forms/submit-adaptive-form-to-workfront-fusion.md)**: Forms as a Cloud Service propose des options prêtes à l’emploi pour connecter facilement un formulaire adaptatif à Adobe Workfront. Cela simplifie le processus d’envoi d’un formulaire adaptatif à un scénario Adobe Workfront, ce qui vous permet de déclencher un scénario de fusion Workfront lors de l’envoi d’un formulaire adaptatif.

* **[Prise en charge des langues de droite à gauche](/help/forms/supporting-new-language-localization-core-components.md)**: les Forms adaptatives reposant sur les composants principaux peuvent désormais être présentées dans une langue de droite à gauche (RTL) telle que l’arabe, le persan et l’ourdou. Les langues de la durée de vie sont parlées par plus de 2 milliards de personnes dans le monde. L’utilisation d’un formulaire en langage RTL vous permet d’étendre la portée de vos formulaires adaptatifs pour répondre à ces diverses audiences et les sélectionner dans les marchés RTL. Dans certaines régions, il est également légal de fournir des formulaires dans la langue locale. En s&#39;adaptant aux langues locales, vous ouvrez non seulement les portes à un public plus large, mais vous garantissez également le respect des lois et réglementations pertinentes.

  ![Prise en charge de la langue de droite à gauche](/help/forms/assets/right-to-left-language-support.png)

* **[Protect de vos documents avec les API DocAssurance (partie des API de communication)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: les API DocAssurance vous permettent de protéger les informations sensibles en signant et en chiffrant les documents. Grâce au chiffrement, le contenu d’un document est transformé en un format illisible, ce qui garantit que seuls les utilisateurs autorisés peuvent y accéder. Cette couche renforcée de protection protège non seulement les données précieuses des yeux non autorisés, mais offre également une certaine tranquillité d’esprit. Le service Signature permet à votre entreprise de garantir la sécurité et la confidentialité des documents Adobe PDF qu’elle diffuse et reçoit. Ce service utilise les signatures numériques et la certification pour s’assurer que seules les personnes destinataires prévues peuvent modifier les documents.

  Vous pouvez écrire sur `aem-forms-early-adopter-program@adobe.com` de votre e-mail officiel pour rejoindre le programme des premiers adopteurs et demander l’accès à la fonctionnalité.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Prise en charge de la synchronisation {#dynatrace}

Les clients de la synchronisation peuvent surveiller leur utilisation AEM. [Lire comment](/help/implementing/cloud-manager/dynatrace.md) pour demander la connectivité à votre environnement de synchronisation afin de surveiller les performances de l’application. Notez que l’API New Relic, disponible pour tous les clients, cessera de collecter des données si la synchronisation est activée.

### Prise en charge de RDE pour le code frontal à l’aide des thèmes du site et des modèles de site : programme des Adopteurs anticipés {#rde-frontend-early-adopter}

[Environnements de développement rapide (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md) prend désormais en charge le code frontal basé sur [thèmes du site](/help/sites-cloud/administering/site-creation/site-themes.md) et [modèles de site](/help/sites-cloud/administering/site-creation/site-templates.md), pour les utilisateurs qui ont adopté l’heure. Avec les RDE, cela se fait à l’aide d’une directive de ligne de commande, plutôt que d’une [pipeline front-end](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md). Veuillez contacter **aemcs-rde-support@adobe.com** pour essayer et fournir des commentaires.

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
