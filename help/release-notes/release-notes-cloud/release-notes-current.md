---
title: Notes de mise à jour d’Adobe Experience Manager en tant que service Cloud pour la version 2020.4.0
description: Notes de mise à jour d’Experience Manager pour la version 2020.4.0
translation-type: tm+mt
source-git-commit: 031e2de3b3e1d7a5d57dbdaf16a96800927e98f2

---


# Release Notes for Adobe Experience Manager as a Cloud Service 2020.4.0 {#release-notes}

La section suivante décrit les notes de mise à jour générales de [!DNL Experience Manager] as a Cloud Service 2020.4.0.

## Date de publication {#release-date}

La date de publication de [!DNL Experience Manager] as a Cloud Service 2020.4.0 est le 9 avril 2020.

## What&#39;s New in Assets {#assets}

Découvrez les nouvelles fonctionnalités, les améliorations et les correctifs pour [!DNL Experience Manager Assets] et [!DNL Dynamic Media] dans la version actuelle.

* [Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/home.html) prend en charge les cas d’utilisation de la distribution des ressources pour les ressources Experience Manager. [!DNL Brand Portal] aide les organisationsentreprises à répondre à leurs besoins marketing en distribuant en toute sécurité des ressources de marque et de produit approuvées à des agences extérieures, partenaires, équipes internes et revendeurs en vue de leur téléchargement.
   * [!DNL Brand Portal] est effectuée via [!DNL Adobe I/O] la console.
   * L’approvisionnement en ressources dans [!DNL Brand Portal] n’est pas encore pris en charge avec [!DNLEExperience Manager] en tant que service Cloud.

* [Adobe Asset Link](https://helpx.adobe.com/fr/enterprise/using/adobe-asset-link.html) v2.0 fonctionne avec [!DNL Experience Manager] comme un service Cloud. [!DNL Adobe Asset Link] simplifie la collaboration entre les créatifs et les marketeurs dans le processus de création de contenu en établissant une connexion [!DNL Experience Manager Assets] avec les applications de [!DNL Creative Cloud] bureau [!DNL Adobe Photoshop], [!DNL Adobe Illustrator]et [!DNL Adobe InDesign] via le [!DNL Asset Link] panneau intégré à l’application.
   * [!DNL Experience Manager] est préconfigurée pour [!DNL Adobe Asset Link], ce qui permet une configuration [](https://helpx.adobe.com/enterprise/using/configure-aem-assets-for-asset-link.html) facile et un déploiement plus rapide pour les professionnels de la création.
   * [!DNL Asset Link] prend désormais en charge un sélecteur [de  de](https://helpx.adobe.com/fr/enterprise/using/manage-assets-using-adobe-asset-link.html#UseAdobeAssetLink) Experience Manager qui permet aux utilisateurs créatifs de se connecter facilement à un autre [!DNL Experience Manager] de. Cette fonctionnalité est utile, par exemple, pour les concepteurs d’agences qui travaillent avec plusieurs clients utilisant différents [!DNL Experience Manager Assets] déploiements.

* Les utilisateurs peuvent configurer le post-traitement [en  de automatique dans l’interface utilisateur des](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) propriétés  du dossier pour les hiérarchies de dossiers spécifiques.
   * L’interface utilisateur des [!UICONTROL propriétés] du dossier est simplifiée, grâce au nouvel onglet Traitement [!UICONTROL des] ressources qui contient les  de métadonnées, les  de traitement et la nouvelle configuration de flux de travail de l’ de traitement et de l’automatique desressources.
   * La boîte de dialogue de retraitement des ressources permet de sélectionner un de traitement spécifique et de décider de le retraiter dans des sous-dossiers.
   * [!DNL Dynamic Media]: Ajout d’une configuration de publication sélective afin que les ressources soient publiées automatiquement pour les  sécurisés uniquement. En outre, les ressources peuvent être publiées explicitement dans Experience Manager sans être publiées dans DMS7 pour des  de dans le domaine public.

* Les questions suivantes sont abordées :
   * Correctifs des problèmes de traitement des ressources.
   * Correctifs dans [!DNL Dynamic Media] la configuration et la publication des ressources vers le service de  [!DNL Dynamic Media] .

>[!MORELIKETHIS]
>
>* [A propos d’Adobe Asset Link](https://www.adobe.com/creativecloud/business/enterprise/adobe-asset-link.html)
>* [Configuration du portail des marques](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/configure-aem-assets-with-brand-portal.html)
>* [Configuration d’Experience Manager pour une utilisation avec Asset Link](https://helpx.adobe.com/enterprise/using/configure-aem-assets-for-asset-link.html)
>* [Création d’un flux de travail dans Experience Manager à l’aide de microservices de ressources](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/manage/asset-microservices-configure-and-use.html#post-processing-workflows)


## Mises à jour de Cloud Manager {#cloud-manager}

## Nouveautés de Cloud Manager {#whats-new-cloud-manager}

* Les URL de l’éditeur sont désormais disponibles à partir de la page  du  dans l’interface utilisateur de Cloud Manager.
* Modifications de la navigation pour permettre à l’utilisateur de modifier, de changer ou d’ajouter un  à partir de la page d’aperçu de Cloud Manager.
* Modifications permettant à l’utilisateur de modifier des  à partir de la carte  sur la  de Cloud Manager.
* Nouvel état du pipeline **Pipeline En cours d’exécution** s’affichait par rapport au  auquel il est associé.
* Améliorations de la lisibilité de la page d&#39;exécution du pipeline. Ceci inclut l&#39;affichage du nom et du type du pipeline (non-production du pipeline uniquement) et un badge pour indiquer si l&#39;état du pipeline est En cours/Annulé/Échec.
* Cette section contient des info-bulles destinées à améliorer l’expérience utilisateur et la compréhension de la raison pour laquelle Ajouter bouton / de/ est désactivé.
* Les  de ayant échoué peuvent désormais être supprimés via l’interface utilisateur et l’API.
* Le processus utilisé pour générer les mots de passe Git a été rendu plus résistant aux problèmes de la couche de service sous-jacente.

## Correctifs {#bug-fixes-cloud-manager}

* Les liens vers l’étape  le  sur la page des détails de l’exécution du pipeline ne se rendaient pas toujours à l’emplacement correct.
* Les étapes individuelles du processus de création de  de  expireraient plus tôt que nécessaire, provoquant l’échec du processus.
* La configuration Maven utilisée dans le de génération a été mise à jour afin d’éviter les blocages lors du téléchargement des métadonnées d’artefact.
* Dans certains cas, l’étape de création d’image ne parvient pas à télécharger les packs clients.
* Certaines conditions peu fréquentes empêcheraient   d’être supprimées.
* Les notifications Experience Cloud n’ont pas été reçues de manière cohérente.