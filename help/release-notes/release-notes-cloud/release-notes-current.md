---
title: Notes de mise à jour de la version 2020.4.0
description: Notes de mise à jour de la version 2020.4.0
translation-type: tm+mt
source-git-commit: c6c0e93d881762a2b501abb3d8c8356046a5f082

---


# Notes de mise à jour d’AEM en tant que service Cloud 2020.4.0 {#release-notes}

La section suivante décrit les Notes de mise à jour générales d’Experience Manager en tant que service Cloud 2020.4.0.

## Date de publication {#release-date}

La date de publication pour Experience Manager en tant que service Cloud 2020.4.0 est le 9 avril 2020.

## Ressources {#assets}

Suivez cette section pour en savoir plus sur les nouveautés et les mises à jour des ressources Experience Manager et des médias dynamiques dans AEM as a Cloud Service Release 2020.4.0.

### Nouveautés {#assets-what-is-new}

* [Le portail](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/home.html) de marque est disponible pour AEM en tant que ressources de service Cloud, ce qui prend en charge les cas d’utilisation de la distribution des ressources. Brand Portal aide les entreprises à répondre à leurs besoins marketing en distribuant, en toute sécurité, des ressources de marque et de produit approuvées à des agences extérieures, partenaires, équipes internes et revendeurs en vue de leur téléchargement.
   * La configuration du portail de marque s’effectue via la console d’E/S Adobe.
   * La source de ressources dans Brand Portal n’est pas encore prise en charge avec AEM en tant que service Cloud.
* La nouvelle version d’ [Adobe Asset Link](https://helpx.adobe.com/fr/enterprise/using/adobe-asset-link.html) 2.0 est prise en charge avec AEM en tant que service Cloud. Adobe Asset Link simplifie la collaboration entre les créatifs et les marketeurs dans le processus de création de contenu en connectant AEM Assets aux applications de bureau Creative Cloud Photoshop, Illustrator et InDesign via le panneau de lien d’actif intégré.
   * AEM en tant que service Cloud est préconfiguré pour Adobe Asset Link, ce qui entraîne une configuration [](https://helpx.adobe.com/enterprise/using/configure-aem-assets-for-asset-link.html)simplifiée.
   * Asset Link prend désormais en charge un sélecteur [de](https://helpx.adobe.com/fr/enterprise/using/manage-assets-using-adobe-asset-link.html#UseAdobeAssetLink)AEM, ce qui permet aux utilisateurs créatifs de se connecter plus facilement à différents environnements AEM (par exemple, dans le cas des concepteurs d’agences travaillant avec plusieurs clients avec des actifs AEM).
* Les  de automatique pour les tâches [de](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) post-traitement peuvent être configurées dans l’interface utilisateur Propriétés du dossier pour des hiérarchies de dossiers spécifiques.
   * L’interface utilisateur des propriétés du dossier a été simplifiée, grâce au nouvel onglet Traitement des ressources qui contient le de métadonnées, le de traitement et la nouvelle configuration de flux de travail de l’ detraitement automatique.
* La boîte de dialogue de retraitement des ressources permet de sélectionner un de traitement spécifique et de décider de le retraiter dans des sous-dossiers.
* Contenu multimédia dynamique : Ajout d’une configuration de publication sélective, ce qui signifie que les ressources sont publiées automatiquement pour les  sécurisées uniquement et peuvent être publiées explicitement dans AEM sans publication dans DMS7 pour les  de dans le domaine public.

### Correctifs  {#assets-bug-fixes}

* Correctifs dans le traitement des ressources
* Correctifs dans la configuration de Contenu multimédia dynamique et publication de fichiers vers le service  de Contenu multimédia dynamique
