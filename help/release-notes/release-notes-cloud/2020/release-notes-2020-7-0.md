---
title: Notes de mise à jour de la version 2020.7.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour d’[!DNL Adobe Experience Manager] as a Cloud Service version 2020.7.0.
exl-id: 75d354a3-6987-4de0-aec8-24043461c516
feature: Release Information
role: Admin
source-git-commit: 281a8efcd18920dd926d92db9c757c0513d599fd
workflow-type: tm+mt
source-wordcount: '1012'
ht-degree: 93%

---

# Notes de mise à jour pour [!DNL Adobe Experience Manager] as a Cloud Service 2020.7.0 {#release-notes}

La section suivante décrit les notes de mise à jour générales d’Experience Manager as a Cloud Service 2020.7.0.

## Date de publication {#release-date}

La date de publication d’[!DNL Experience Manager] as a Cloud Service version 2020.7.0 est le 30 juillet 2020.

## Adobe Experience Manager Sites as a Cloud Service {#cloud-services-sites}

### Nouveautés {#what-is-new-sites}

Les connecteurs [!DNL Experience Manager] as a Cloud Service pour [!DNL Adobe Target] et [!DNL Adobe Analytics] sont améliorés de la manière suivante :

* Une nouvelle implémentation de l’interface utilisateur remplace l’implémentation basée sur l’interface utilisateur classique.

* Simplification des boîtes de dialogue de l’interface utilisateur, attribuant la création de framework pour le mappage des variables et d’autres configurations à [!DNL Adobe Launch]. Voir [Intégration d’Adobe Analytics](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/integrations/integrating-adobe-analytics.html?lang=fr) et [Intégration d’Adobe Target](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/integrations/integrating-adobe-target.html?lang=fr).

* Les configurations sont désormais stockées dans `/conf` plutôt que `/etc/cloudsettings` dans le référentiel Experience Manager.

## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

### Nouveautés d’[!DNL Assets]  {#what-is-new-assets}

* [!DNL Asset Compute Service] est un service évolutif et extensible permettant de traiter les ressources. Les administrateurs peuvent configurer [!DNL Experience Manager] pour appeler des applications personnalisées créées à l’aide du [!DNL Asset Compute Service]. Les développeurs peuvent utiliser ce service pour créer des applications personnalisées spécialisées qui répondent à des cas d’utilisation complexes. Ce service web peut générer des miniatures pour différents types de fichiers et des rendus d’images haute qualité à partir de formats de fichiers Adobe, coder des vidéos (à venir), extraire des métadonnées, extraire du texte intégral en tant que précurseur de l’indexation et exécuter une ressource via tous les services [!DNL AI] disponibles. Voir [Utilisation des microservices de ressources et des profils de traitement](/help/assets/asset-microservices-configure-and-use.md).

* La configuration initiale de [!DNL Dynamic Media] dans [!DNL Experience Manager] as a Cloud Service est améliorée pour être plus robuste. Elle indique désormais aux administrateurs la progression des processus.

* La publication des ressources dans [!DNL Dynamic Media] est simplifiée et rendue plus robuste en faisant une partie intégrante du processus de traitement global des ressources à l’aide de microservices de ressources et en améliorant le serveur principal de publication par lots.

* Les étapes de workflow qui ne sont pas compatibles avec un déploiement de Cloud Service sont désormais signalées par un avertissement dans l’éditeur de [!UICONTROL modèle de workflow]. En outre, lors de l’exécution des workflows existants dans l’environnement Cloud Service, les étapes de workflow incompatibles sont ignorées.

* Les modèles de workflow créés par les clients qui sont déployés vers `/conf/global` dans le projet Git associé à l’environnement dans [!DNL Cloud Manager] sont automatiquement déployés vers `/var` et sont donc disponibles dans [!DNL Experience Manager]. Les modèles de workflow de produit sous `/libs` ayant été modifiés par le client ne sont pas automatiquement déployés vers `/var`.

### Bogues résolus {#assets-bugs-fixed}

* L’assistant de déplacement de ressources ne se charge pas comme prévu pour les ressources incluses dans les collections. (CQ-4296756)
* Les valeurs de `dam:size` et `dam:sha1` sont exclues de l’écriture différée XMP. (CQ-4237355)
* Lors de la dépublication de ressources en bloc, [!DNL Brand Portal] génère une erreur suggérant que l’URI de requête est trop longue. (CQ-4299474)

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

AEM Commerce est désormais disponible dans Cloud Service.

Consultez [Prise en main d’AEM Commerce as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/commerce/getting-started.html?lang=fr) pour plus d’informations.

## Composants principaux {#core-components}

### Nouveautés {#what-is-new-core-components}

La version 2.11.0 des [composants principaux AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr) est maintenant disponible dans AEM Sites, notamment :

* Introduction d’un nouveau [composant Visionneuse PDF](https://www.aemcomponents.dev/content/core-components-examples/library/core-content/pdf-viewer.html).

* La prise en charge AMP (Accelerated Mobile Pages) des composants principaux est désormais disponible. Elle permet de générer des expériences client plus rapides en rendant la transition de page instantanée lors de l’accès au site à partir d’un résultat de recherche mobile Google, ce qui améliore l’engagement des utilisateurs et l’optimisation du moteur de recherche.
Pour plus d’informations, consultez [Prise en charge AMP des composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/amp.html?lang=fr).

* Compatibilité avec la version 1.0.2 de la [couche de données client Adobe](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/overview.html?lang=fr).

* Correctifs de bogues et amélioration de la qualité du code.

## Cloud Manager {#cloud-manager}

### Date de publication {#release-date-cm}

La date de publication de la mise à jour 2020.7.0 de [!UICONTROL Cloud Manager] est le 09 juillet 2020.

### Nouveautés {#what-is-new-cloud-manager}

* La page Environnements a été repensée.

* Les environnements en veille affichent désormais un état discret dans Cloud Manager.

* Le nombre de variables d’environnement par environnement a été porté à 200.

* Les pipelines de Cloud Manager prennent désormais en charge les variables et les secrets définis par le client.

  Pour plus d’informations, consultez la section Variables de pipeline.

* Les référentiels Maven privés liés à l’authentification sont désormais pris en charge.

* Le conteneur de création Cloud Manager prend désormais en charge Java 8 et Java 11.
Consultez Utilisation de la prise en charge de Java 11 pour plus d’informations.

### Correctifs {#bug-fixes-cm}

* Le lien entre Cloud Manager et Developer Console était actif avant la création complète des environnements alors qu’il ne devait pas l’être.

* Le lien direct vers Developer Console à partir de Cloud Manager n’affichait pas l’option permettant de mettre en veille/réactiver un environnement de programme Sandbox.

* Les options **Annuler** et **Enregistrer** sur la page Modification d’un pipeline hors production n’étaient pas toujours visibles.

* Certaines erreurs liées au u processus de qualité du code peuvent entraîner la génération incorrecte du fichier journal.

* Lors de la création d’un programme, le nom suggéré renvoyait parfois un duplicata de nom de programme existant.

* Certains journaux d’étape de pipeline volumineux n’ont pas pu être téléchargés de manière cohérente via l’interface utilisateur.

* La validation des noms d’environnement comportait une erreur de décalage d’une unité.

* La page Environnements affichait parfois des segments de publication et de répartiteur alors qu’aucun segment n’était présent.

### Problèmes connus {#known-issues}

* En raison d’un changement dans le mode de calcul de la couverture du code, la version *minimale* du plug-in Jacoco est désormais 0.7.5.201505241946 (publiée en mai 2015). Les clients référençant explicitement une ancienne version reçoivent un message d’erreur dans le processus de qualité du code.

## Adobe Experience Manager as a Cloud Service Foundation {#cloud-foundation}

### Nouveautés {#what-is-new-foundations}

* [Les journaux peuvent être transférés vers les comptes Splunk](/help/implementing/developing/introduction/logging.md#splunk-logs), ce qui permet aux entreprises d’utiliser leur investissement Splunk.

* [Une adresse IP de sortie statique et dédiée](/help/implementing/developing/introduction/development-guidelines.md#dedicated-egress-ip-address) peut être affectée au trafic sortant programmé dans le code Java, ce qui peut s’avérer utile pour certaines intégrations.

* L’interface utilisateur du service cloud AEM Analytics est passée de l’interface classique à la nouvelle interface AEM. De plus, l’emplacement du service cloud Analytics dans le référentiel AEM est passé de `/etc` à `/conf` pour refléter les autres services cloud AEM.

* L’interface utilisateur du service cloud AEM Target est passée de l’interface classique à la nouvelle interface AEM. De plus, l’emplacement du service cloud Target dans le référentiel AEM est passé de `/etc` à `/conf` pour refléter les autres services cloud AEM.

## Cloud Readiness Analyzer {#cloud-readiness-analyzer}

Suivez cette section pour en savoir plus sur les nouveautés et les mises à jour de la version 1.0.2 de Cloud Readiness Analyzer.

### Correctifs {#cra-bug-fixes}

* La version antérieure de CRA ne pouvait pas s’exécuter sur Adobe Experience Manager (AEM) 6.1. Nous avons ajouté la prise en charge explicite de l’autorisation des utilisateurs dans le groupe d’administrateurs.

  Voir [Installation du CRA sur AEM 6.1](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/cloud-readiness-analyzer/using-cloud-readiness-analyzer.html?lang=fr#installing-on-aem61) pour plus d’informations.

* L’horodatage d’expiration affiché sur le rapport résumé était incorrect.

* CRA détectait des doublons de composants personnalisés.

* Dans AEM 6.1, l’inspection du contenu se terminait avant la fin de l’analyse complète. Nous avons ajouté la gestion des exceptions pour permettre à l’inspecteur d’ignorer et de continuer jusqu’à ce que l’inspection complète soit terminée.
