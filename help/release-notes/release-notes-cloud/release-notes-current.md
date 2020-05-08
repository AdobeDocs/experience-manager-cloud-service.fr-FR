---
title: Notes de mise à jour d’Adobe Experience Manager as a Cloud Service version 2020.4.0
description: Notes de mise à jour d’Experience Manager version 2020.4.0
translation-type: ht
source-git-commit: 98de3a6674aaef5228e96e0bf72e67de861f858e

---


# Notes de mise à jour d’Adobe Experience Manager as a Cloud Service version 2020.4.0 {#release-notes}

La section suivante présente les notes de mise à jour générales d’[!DNL Experience Manager] as a Cloud Service version 2020.4.0.

## Date de publication {#release-date}

La date de publication d’[!DNL Experience Manager] as a Cloud Service version 2020.4.0 est le 9 avril 2020.

## Nouveautés d’Assets {#assets}

Découvrez les nouvelles fonctionnalités, les améliorations et les correctifs d’[!DNL Experience Manager Assets] et de [!DNL Dynamic Media] dans la version actuelle.

* [Brand Portal](https://docs.adobe.com/content/help/fr-FR/experience-manager-brand-portal/using/home.html) prend en charge les cas d’utilisation de distribution des ressources pour Experience Manager Assets. [!DNL Brand Portal] aide les organisations à répondre à leurs besoins marketing en distribuant en toute sécurité des ressources de marque et de produit approuvées à des agences extérieures, partenaires, équipes internes et revendeurs en vue de leur téléchargement.
   * La configuration de [!DNL Brand Portal] est effectuée via la console [!DNL Adobe I/O]. Voir [Configuration de Brand Portal](https://docs.adobe.com/content/help/fr-FR/experience-manager-brand-portal/using/publish/configure-aem-assets-with-brand-portal.html).
   * L’approvisionnement en ressources dans [!DNL Brand Portal] n’est pas encore pris en charge dans [!DNL Experience Manager] as a Cloud Service.

* [Adobe Asset Link](https://helpx.adobe.com/fr/enterprise/using/adobe-asset-link.html) v2.0 fonctionne avec [!DNL Experience Manager] as a Cloud Service. [!DNL Adobe Asset Link] simplifie la collaboration entre les créatifs et les spécialistes du marketing dans le processus de création de contenu en connectant [!DNL Experience Manager Assets] aux applications de bureau [!DNL Creative Cloud], [!DNL Adobe Photoshop], [!DNL Adobe Illustrator] et [!DNL Adobe InDesign] via le panneau [!DNL Asset Link] dans l’application.
   * [!DNL Experience Manager] est préconfiguré pour [!DNL Adobe Asset Link], ce qui permet une [configuration facile](https://helpx.adobe.com/fr/enterprise/using/configure-aem-assets-for-asset-link.html) et un déploiement plus rapide pour les professionnels de la création.
   * [!DNL Asset Link] prend désormais en charge un [commutateur d’environnement Experience Manager](https://helpx.adobe.com/fr/enterprise/using/manage-assets-using-adobe-asset-link.html#UseAdobeAssetLink) qui permet aux utilisateurs créatifs de se connecter facilement à un autre environnement [!DNL Experience Manager]. Cette fonctionnalité est utile, par exemple, pour les designers en agence qui travaillent avec plusieurs clients utilisant différents déploiements [!DNL Experience Manager Assets].

* Les utilisateurs peuvent configurer des [workflows de post-traitement](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) démarrant automatiquement dans l’interface utilisateur [!UICONTROL Propriétés] de dossier pour les hiérarchies de dossiers spécifiques.
   * L’interface utilisateur [!UICONTROL Propriétés] de dossier est simplifiée, avec un nouvel onglet [!UICONTROL Traitement du ou des fichier(s)] contenant un profil de métadonnées, un profil de traitement et la nouvelle configuration de workflow qui démarre automatiquement.

      ![Les profils de traitement peuvent s’appliquer facilement aux dossiers et toutes les ressources téléchargées dans les dossiers sont traitées à l’aide de ces profils](/help/assets/assets/asset-processing-folder-properties.png)

   * L’option de retraitement des ressources permet de sélectionner un profil de traitement spécifique pour retraiter des ressources sélectionnées par l’utilisateur dans des sous-dossiers.

      ![Retraiter des ressources sélectionnées à l’aide d’un profil de traitement spécifique](/help/assets/assets/fpo-existing-asset-reprocess.gif)

   * [!DNL Dynamic Media] : Ajout d’une configuration de publication sélective afin que les ressources soient publiées automatiquement pour un aperçu sécurisé uniquement. En outre, les ressources peuvent être publiées explicitement dans Experience Manager sans être publiées dans DMS7 pour une diffusion dans le domaine public.

### Correctifs {#assets-bug-fixes}

* Correctifs des problèmes de traitement des ressources.
* Correctifs dans la configuration [!DNL Dynamic Media] et la publication des ressources dans le service de diffusion [!DNL Dynamic Media].

>[!MORELIKETHIS]
>
>* [À propos d’Adobe Asset Link](https://www.adobe.com/creativecloud/business/enterprise/adobe-asset-link.html)
>* [Configuration de Brand Portal](https://docs.adobe.com/content/help/fr-FR/experience-manager-brand-portal/using/publish/configure-aem-assets-with-brand-portal.html)
>* [Configuration d’Experience Manager pour une utilisation avec Asset Link](https://helpx.adobe.com/fr/enterprise/using/configure-aem-assets-for-asset-link.html)
>* [Création d’un workflow dans Experience Manager à l’aide de microservices de ressources](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/assets/manage/asset-microservices-configure-and-use.html#post-processing-workflows)


## Nouveautés de Cloud Manager {#whats-new-cloud-manager}

* Les URL de l’éditeur sont désormais disponibles à partir de la page Environnement de l’interface utilisateur Cloud Manager.
* Modifications de la navigation pour permettre à l’utilisateur de modifier, de changer ou d’ajouter un programme à partir de la page d’aperçu de Cloud Manager.
* Modifications permettant à l’utilisateur de modifier un programme à partir de la carte de programme sur la page d’entrée de Cloud Manager.
* Nouveau statut du pipeline **Exécution de pipeline** affiché au niveau de l’environnement auquel il est associé.
* Améliorations de la lisibilité de la page d’exécution de pipeline. Cela inclut l’affichage du nom du pipeline (pipeline hors production uniquement) et du type, ainsi qu’un badge pour indiquer si le statut du pipeline est En cours/Annulé/Échec.
* Ajout d’info-bulles destinées à améliorer l’expérience utilisateur et à expliquer pourquoi le bouton Ajouter un programme/environnement est désactivé.
* Les environnements ayant échoué peuvent désormais être supprimés via l’interface utilisateur et l’API.
* Le processus utilisé pour générer les mots de passe Git est maintenant plus résilient face aux problèmes de la couche de service sous-jacente.

### Correctifs {#bug-fixes-cloud-manager}

* Les liens vers l’environnement d’évaluation sur la page des détails d’exécution de pipeline ne menaient pas toujours à l’emplacement correct.
* Les étapes individuelles du processus de création d’environnement expiraient plus tôt que nécessaire, provoquant l’échec du processus.
* La configuration Maven utilisée dans le conteneur de build a été mise à jour afin d’éviter les blocages lors du téléchargement des métadonnées d’artefact.
* Dans certains cas, l’étape de création d’image ne parvenait pas à télécharger les modules clients.
* Certaines conditions peu fréquentes empêchaient la suppression des environnements.
* Les notifications Experience Cloud n’étaient pas toujours reçues.
