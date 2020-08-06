---
title: Notes de mise à jour de la version 2020.7.0 [!DNL Adobe Experience Manager] de Cloud Service.
description: '[ !DNL Adobe Experience Manager] en tant que notes de mise à jour Cloud Service pour la version 2020.7.0.'
translation-type: tm+mt
source-git-commit: 7f089e15deff87706e0ed3c38630b52832b277d4
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 37%

---


# Release Notes for [!DNL Adobe Experience Manager] as a Cloud Service 2020.7.0 {#release-notes}

La section suivante décrit les notes de mise à jour générales d’Experience Manager as a Cloud Service 2020.7.0.

## Date de publication {#release-date}

The release date for [!DNL Experience Manager] as a Cloud Service 2020.7.0 is July 30, 2020.

## L&#39;Adobe Experience Manager Sites comme Cloud Service {#cloud-services-sites}

### Nouveautés {#what-is-new-sites}

[!DNL Experience Manager] en tant que connecteurs Cloud Service pour [!DNL Adobe Target] et [!DNL Adobe Analytics] sont améliorés de la manière suivante :

* Une nouvelle implémentation de l’interface utilisateur remplace l’implémentation en fonction de l’interface utilisateur classique.

* Simplification des boîtes de dialogue de l’interface utilisateur, laissant la création de la structure pour le mappage des variables et d’autres configurations à [!DNL Adobe Launch]. Voir [Intégration d’Adobe Analytics](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/sites/integrations/integrating-adobe-analytics.html) et [Intégration de Adobe Target](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/sites/integrations/integrating-adobe-target.html).

* Les configurations sont désormais stockées dans `/conf` le référentiel du Experience Manager plutôt que `/etc/cloudsettings` dans celui-ci.

## Adobe Experience Manager Assets as a Cloud Service {#assets}

### Nouveautés {#what-is-new-assets}

* [!DNL Asset Compute Service] est un service évolutif et extensible permettant de traiter les ressources. Les administrateurs peuvent configurer le Experience Manager pour qu’il appelle le travailleur personnalisé créé à l’aide du [!DNL Asset Compute Service]. Les développeurs peuvent utiliser ce service pour créer des agents personnalisés spécialisés qui répondent à des cas d’utilisation complexes. Ce service Web peut générer des miniatures pour différents types de fichiers, des rendus d&#39;images de haute qualité à partir de formats de fichiers Adobes, coder des vidéos (à venir), extraire des métadonnées, extraire du texte intégral comme précurseur de l&#39;indexation et exécuter un fichier par l&#39;intermédiaire de tous les services Sensei disponibles. voir [Utilisation des microservices de ressources et des profils](/help/assets/asset-microservices-configure-and-use.md)de traitement.

* La configuration initiale de [!DNL Dynamic Media] en [!DNL Experience Manager] tant que Cloud Service est améliorée pour être plus robuste. Il fournit désormais aux administrateurs la progression des processus.

* La publication des ressources vers [!DNL Dynamic Media] est simplifiée et rendue plus robuste en en faisant partie intégrante du processus de traitement global des ressources à l’aide de microservices de ressources et en améliorant le serveur principal de publication par lots.

* Les étapes de flux de travaux qui ne sont pas compatibles avec un déploiement de Cloud Service sont désormais signalées par un avertissement dans l’éditeur de modèles [!UICONTROL de] flux de travaux. De plus, lors de l’exécution des workflows existants sur un environnement Cloud Service, les étapes de flux de travaux incompatibles sont ignorées.

* Les modèles de flux de travaux créés par les clients qui sont déployés dans `/conf/global` le projet Git associé à l’environnement dans Cloud Manager sont automatiquement déployés dans `/var` et sont donc disponibles dans le Experience Manager. Les modèles de processus des produits sous `/libs` lesquels le client a modifié n’ont pas été automatiquement déployés dans `/var`.

## Composants principaux {#core-components}

### Nouveautés {#what-is-new-core-components}

Release 2.11.0 of the [AEM Core Components](https://docs.adobe.com/content/help/fr-FR/experience-manager-core-components/using/introduction.html) is now available as part of AEM Sites including:

* Introduction d’un nouveau composant [de lecteur](https://aemcomponents.dev/content/core-components-examples/library/page-authoring/pdf-viewer.html)PDF.

* La prise en charge AMP (Accelerated Mobile Pages) des composants principaux est désormais disponible. Cela permet de générer des expériences client plus rapides en faisant de la transition de page instantanée lors de l&#39;entrée sur le site à partir d&#39;un résultat de recherche mobile Google, ce qui améliore l&#39;engagement des utilisateurs et l&#39;optimisation du référencement.
Pour plus d’informations, reportez-vous à la section Prise en charge [AMP des composants](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/amp.html) principaux.

* Compatibilité avec la version 1.0.2 de la couche [de données du client](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/data-layer/overview.html)Adobe.

* Correctifs de bogues et amélioration de la qualité du code.

## Cloud Manager {#cloud-manager}

### Date de publication {#release-date-cm}

La date de publication de la mise à jour 2020.7.0 de [!UICONTROL Cloud Manager] est le 09 juillet 2020.

### Nouveautés {#what-is-new-cloud-manager}

* La page Environnements a été repensée.

* Les environnements en veille prolongée affichent désormais un état discret dans Cloud Manager.

* Le nombre de variables d’environnement par environnement a été porté à 200.

* Les pipelines de Cloud Manager prennent désormais en charge les variables et les secrets définis par le client.

   Pour plus d’informations, consultez [Variables de pipeline](/help/onboarding/getting-access-to-aem-in-cloud/creating-aem-application-project.md#pipeline-variables).

### Correctifs {#bug-fixes-cm}

* Le lien entre Cloud Manager et Developer Console était actif avant la création complète des environnements alors qu’il ne devait pas l’être.

* Le lien direct vers Developer Console à partir de Cloud Manager n’affichait pas l’option permettant de mettre en veille/réactiver un environnement de programme sandbox.

* Les options **Annuler** et **Enregistrer** sur la page Modification d’un pipeline hors production n’étaient pas toujours visibles.

* Certaines erreurs liées au u processus de qualité du code peuvent entraîner la génération incorrecte du fichier journal.

* Lors de la création d’un programme, le nom suggéré renvoyait parfois un duplicata de nom de programme existant.

* Certains journaux d&#39;étape de pipeline volumineux n&#39;ont pas pu être téléchargés de manière cohérente via l&#39;interface utilisateur.

* La validation des noms d’environnement comportait une erreur de décalage d’une unité.

* La page Environnements affichait parfois des segments de publication et de répartiteur alors qu’aucun segment n’était présent.

### Problèmes connus {#known-issues}

* En raison d’un changement dans le mode de calcul de la couverture du code, la version *minimale* du module externe Jacoco est désormais 0.7.5.201505241946 (publiée en mai 2015). Les clients référençant explicitement une ancienne version reçoivent un message d’erreur dans le processus de qualité du code.

## Adobe Experience Manager as a Cloud Service Foundation {#cloud-foundation}

### Nouveautés {#what-is-new-foundations}

* [Les journaux peuvent être transférés vers des comptes](/help/implementing/developing/introduction/logging.md#splunk-logs)Splunk, ce qui permet aux entreprises d&#39;exploiter leur investissement Splunk.

* [Une adresse](/help/implementing/developing/introduction/development-guidelines.md#dedicated-egress-ip-address) IP de sortie statique et dédiée peut être affectée au trafic sortant programmé en code Java, ce qui peut s’avérer utile pour certaines intégrations.

* AEM interface utilisateur du service cloud Analytics de l’interface utilisateur classique vers la nouvelle interface AEM. Vous avez également déplacé l’emplacement du service cloud Analytics dans AEM référentiel de `/etc` vers `/conf`, afin de l’aligner sur d’autres services cloud AEM.

* Interface utilisateur du service Cloud d’Cible d’ intégrée depuis l’interface utilisateur classique vers la nouvelle interface utilisateur AEM. Vous avez également déplacé l’emplacement du service Cloud de Cible dans AEM référentiel de `/etc` vers `/conf`, afin de l’aligner sur d’autres services cloud AEM.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

AEM Commerce est désormais disponible sur Cloud Service.

Pour plus d’informations, reportez-vous à [Prise en main d’AEM Commerce en tant que Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/commerce/getting-started.html) .

## Cloud Readiness Analyzer {#cloud-readiness-analyzer}

Suivez cette section pour en savoir plus sur les nouveautés et les mises à jour de la version 1.0.2 de Cloud Readiness Analyzer.

### Correctifs {#cra-bug-fixes}

* La version antérieure de CRA ne pouvait pas s’exécuter sur Adobe Experience Manager (AEM) 6.1. Nous avons ajouté la prise en charge explicite de l’autorisation des utilisateurs dans le groupe d’administrateurs.

   Voir [Installation de CRA sur AEM 6.1](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/moving/cloud-migration/cloud-readiness-analyzer/using-cloud-readiness-analyzer.html#installing-on-aem61) pour plus d’informations.

* L’horodatage d’expiration affiché sur le rapport résumé était incorrect.

* CRA détectait des doublons de composants personnalisés.

* Dans AEM 6.1, l’inspection du contenu se terminait avant la fin de l’analyse complète. Nous avons ajouté la gestion des exceptions pour permettre à l’inspecteur d’ignorer et de continuer jusqu’à ce que l’inspection complète soit terminée.
