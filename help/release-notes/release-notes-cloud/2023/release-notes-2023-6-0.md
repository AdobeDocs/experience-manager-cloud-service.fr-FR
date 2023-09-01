---
title: Notes de mise à jour de la version 2023.6.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2023.6.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
source-git-commit: 7d09cafc4f8518fee185d3f9efc76c33ec20f9a3
workflow-type: tm+mt
source-wordcount: '1409'
ht-degree: 38%

---


# Notes de mise à jour 2023.6.0 pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour techniques de la version 2023.6.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2021 ou 2022.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] la version actuelle des fonctionnalités (2023.6.0) est le 29 juin 2023. La prochaine version de la fonctionnalité (2023.7.0) est prévue pour le 27 juillet 2023.

## Vidéo de mise à jour {#release-video}

Consultez la vidéo Aperçu de la version de juin 2023 pour obtenir un résumé des fonctionnalités ajoutées dans la version 2023.6.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3420971/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités de [!DNL Experience Manager Sites] {#sites-features}

* Les fragments de contenu et leurs références peuvent désormais être publiés dans la [Service d’aperçu AEM](/help/implementing/cloud-manager/manage-environments.md#access-preview-service) en utilisant la variable [Console de fragments de contenu](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console), permettant aux utilisateurs de prévisualiser l’expérience finale sur une application d’aperçu découplée avant la mise en ligne.

![Aperçu dans la console de fragments de contenu](/help/assets/content-fragments-console-preview.png)

* Les images peuvent désormais être optimisées dynamiquement pour une diffusion web dans des scénarios sans interface utilisateur via GraphQL AEM. [Variables de requête](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/images.html?lang=en#query-variables) peut être défini dans les requêtes GraphQL pour permettre aux applications clientes découplées de demander des images optimisées en conséquence à partir d’AEM.
* Balises sur [Variations de fragments de contenu](https://experienceleague.adobe.com/docs/experience-manager-65/assets/content-fragments/content-fragments-variations.html?lang=en) peut désormais être généré au format JSON à l’aide de l’API de diffusion de contenu GraphQL AEM.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

**Disponibilité de la vue New Assets**

La variable [nouvelle vue Assets](/help/assets/assets-view-introduction.md) est désormais disponible dans Experience Manager Assets. La vue Assets offre une interface utilisateur simplifiée qui facilite la gestion, la découverte et la distribution de vos ressources numériques. L’expérience est destinée aux créatifs, aux consommateurs de ressources en lecture seule et aux utilisateurs DAM plus légers.

![Gestion du balisage.](/help/assets/assets/my-workspace.png)

**Améliorations de l’expérience de recherche**

Experience Manager Assets vous permet désormais d’en faire plus à partir de l’interface utilisateur des résultats de recherche : Vous pouvez désormais :

* [Effectuer une recherche dans l’emplacement actuel du référentiel](/help/assets/search-assets.md) par défaut au lieu de rechercher le mot-clé dans le référentiel entier.

* [Accédez à l’emplacement du dossier](/help/assets/search-assets.md#aftersearch) pour les ressources qui s’affichent dans les résultats de recherche.

**Aperçus de miniatures pour les ressources 3D**

[!DNL Experience Manager Assets] génère désormais des aperçus de miniatures pour les formats de fichiers 3D courants, notamment gLB, USDz, FBX, 3DS, OBJ et SBSAR.[](/help/assets/file-format-support.md) Lorsque ces fichiers sont chargés, les miniatures sont automatiquement générées par défaut.

**Configuration du partage de lien**

Une nouvelle expérience utilisateur améliorée pour [création de partages de lien](/help/assets/share-assets.md) ainsi qu’un tout nouveau jeu de configurations qui permet aux administrateurs de personnaliser le comportement par défaut de cette fonctionnalité pour vos utilisateurs.

![Gestion du balisage.](/help/assets/assets/config-email-service.png)

**Dynamic Media : mise à jour des champs liés au recadrage intelligent dans le profil d’image**

L’interface utilisateur de certains champs liés au recadrage intelligent dans un profil d’image est désormais mise à jour afin de prendre en compte les instructions actuelles de définition d’un recadrage intelligent. Voir [Options de recadrage](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles.html?lang=en#crop-options).

### Nouvelles fonctionnalités dans la vue Assets {#assets-view-features}

**Balisage hiérarchique des ressources pour une expérience de recherche plus rapide**

Les listes plates de vocabulaires contrôlés deviennent ingérables au fil du temps. La vue Assets prend désormais en charge [structure hiérarchique du balisage](/help/assets/tagging-management-assets-view.md), qui facilite l’application des métadonnées pertinentes, la classification des ressources, la prise en charge de la recherche, la réutilisation des balises, l’amélioration de la visibilité, etc.

![Gestion du balisage.](/help/assets/assets/tags-hierarchy.png)

**Épingler les fichiers, les dossiers et les collections pour un accès rapide**

Vous pouvez désormais [épingler des fichiers, dossiers et collections pour un accès plus rapide ;](/help/assets/my-workspace-assets-view.md) à ces éléments lorsque vous en avez besoin ultérieurement. Les éléments épinglés s’affichent dans la section **Accès rapide** de Mon espace de travail. Vous pouvez y accéder à l’aide de Mon espace de travail au lieu d’accéder à l’emplacement où ils sont enregistrés dans le référentiel.

![Tâches dans l’espace de travail.](/help/assets/assets/quick-access.png)

**Filtrer les ressources dans le dossier Corbeille**

La vue Assets vous permet désormais de [filtrer les ressources disponibles dans le dossier Corbeille](/help/assets/navigate-assets-view.md). Vous pouvez appliquer des filtres standard ou personnalisés pour rechercher les ressources appropriées dans le dossier Corbeille afin de les restaurer ou de les supprimer définitivement.

**Aperçus de miniatures pour les ressources 3D**

La vue Assets génère désormais des aperçus miniatures pour les formats de fichiers 3D courants, notamment gLB, USDz, FBX, 3DS, OBJ et SBSAR. Lorsque ces fichiers sont chargés en mode Ressources, les miniatures sont automatiquement générées par le système, par défaut.

![Tâches dans l’espace de travail.](/help/assets/assets/3d-preview.png)

**Afficher les termes les plus recherchés**

La vue Assets prend désormais en charge [affichage des principaux termes recherchés dans votre déploiement](/help/assets/my-workspace-assets-view.md) en utilisant la variable **Informations** de My Workspace. Vous pouvez également accéder à Insights pour afficher les principales recherches effectuées au cours des 30 ou 12 derniers jours.

![Tâches dans l’espace de travail.](/help/assets/assets/insights-top-searches.png)

**Améliorations des formulaires de métadonnées**

La vue Assets vous permet désormais de [ajouter des composants de propriété texte à plusieurs valeurs et liste déroulante ;](/help/assets/metadata-assets-view.md#property-components) aux formulaires de métadonnées.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités disponibles dans [!DNL Forms] {#new-features-available-in-channel}

* [Formulaires adaptatifs dans l’éditeur de page AEM](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md) : vous pouvez désormais utiliser l’éditeur de page AEM pour créer et ajouter rapidement plusieurs formulaires à vos pages Sites. Cette fonctionnalité permet aux auteurs et autrices de contenu de créer des expériences fluides de capture de données dans les pages Sites à l’aide de la puissance des composants de formulaires adaptatifs, notamment le comportement dynamique, les validations, l’intégration de données, la génération d’un document d’enregistrement et l’automatisation de la gestion commerciale. Vous pouvez :

   * Créer un formulaire adaptatif en faisant glisser les composants de formulaire vers le composant de conteneur de Forms adaptatif dans l’éditeur AEM Sites ou les fragments d’expérience.
   * Utiliser l’assistant de formulaires adaptatifs dans l’éditeur AEM Sites pour créer des formulaires indépendants de n’importe quelle page Sites, ce qui vous permet de réutiliser ces formulaires sur plusieurs pages.
   * Ajouter plusieurs formulaires à une page Sites, en rationalisant l’expérience client et en offrant une plus grande flexibilité.

     >[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

* [Adobe Acrobat Sign Solutions for Government](/help/forms/adobe-sign-integration-adaptive-forms.md): AEM Forms s’intègre désormais à Adobe Acrobat Sign Solutions for Government. Cette intégration offre un niveau avancé de conformité et de sécurité pour les signatures électroniques avec les envois de formulaires adaptatifs pour les comptes associés au gouvernement (ministères et organismes gouvernementaux).

  L’intégration à Adobe Acrobat Sign Solutions for Government permet aux partenaires d’Adobe et aux clients gouvernementaux d’utiliser des signatures électroniques dans Adaptive Forms pour certains secteurs d’activité les plus critiques et les plus sensibles. Cette couche supplémentaire de sécurité garantit que toutes les signatures électroniques sont entièrement conformes à la norme FedRAMP Moderate, offrant ainsi la tranquillité d’esprit aux clients gouvernementaux d’Adobe.

* [Amélioration de la gestion des erreurs avec les gestionnaires d’erreurs personnalisés dans l’éditeur de règles](/help/forms/add-custom-error-handler-adaptive-forms.md): vous pouvez désormais appeler une fonction personnalisée (à l’aide de la bibliothèque cliente) en réponse à une erreur renvoyée par un service externe et fournir une réponse personnalisée aux utilisateurs finaux. Vous pouvez également effectuer des actions spécifiques pour les erreurs renvoyées par un service. Par exemple, vous pouvez appeler un workflow personnalisé dans le serveur principal pour des codes d’erreur spécifiques ou informer le client que le service est hors service.

  Cette fonctionnalité contribue à améliorer votre fonctionnalité globale de gestion des erreurs en introduisant des réponses d’erreur basées sur des normes qui sont rétrocompatibles avec les gestionnaires d’erreurs prêts à l’emploi, avec une plus grande flexibilité et un meilleur contrôle.

* [Méthodes d’authentification améliorées pour le modèle de données de formulaire](/help/forms/configure-data-sources.md): bénéficiez d’une sécurité renforcée grâce à l’introduction de l’authentification basée sur les informations d’identification client pour connecter AEM Forms à des sources de données compatibles. Cette amélioration élimine le besoin d’usurpation d’identité ou de connexion utilisateur, renforçant la protection de vos données.

* [Forms adaptatif avec des sections répétables](/help/forms/create-forms-repeatable-sections.md): vous pouvez désormais effectuer les opérations suivantes : [Accordéon](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html), [Assistant](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html), [Panneau](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html), et [Onglets horizontaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html) composants dans un formulaire adaptatif basé sur les composants principaux pour créer des sections répétables.

  >[!VIDEO](https://video.tv.adobe.com/v/3421052/adaptive-forms-repeatable-sections-repeat-sections/?quality=12&learn=on)

  Ces sections répétables vous permettent de fournir un nombre illimité d’entrées sans nombre fixe de champs. Elle est utile lorsque les instances de données requises sont inconnues à l’avance. Les utilisateurs de Forms peuvent facilement ajouter ou supprimer des sections, en adaptant les formulaires à différents scénarios de saisie de données et en simplifiant la collecte de plusieurs occurrences des mêmes données.

* **[Envoyer le Forms adaptatif à Microsoft® SharePoint et Microsoft® OneDrive](/help/forms/configuring-submit-actions.md)**: améliorez l’agilité des utilisateurs professionnels afin que vous puissiez lancer rapidement de nouveaux formulaires et stocker les données envoyées dans les outils quotidiens qu’ils utilisent comme le site SharePoint Microsoft® ou le dossier OneDrive.

### Programme des formulaires adaptatifs découplés destiné aux utilisateurs et utilisatrices précoces {#forms-early-adopter}

Utilisation [Forms adaptatif sans affichage](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=fr) pour permettre aux développeurs de créer, publier et gérer des formulaires interactifs accessibles et interactifs via des API, plutôt que par le biais d’une interface utilisateur graphique classique. Les formulaires adaptatifs découplés vous aident à :

* créer des formulaires multicanaux de haute qualité dans le langage de programmation de votre choix ;
* intégrer nativement les formulaires à vos applications de bureau et mobiles, à vos sites web et à vos applications de chat ;
* réutiliser vos composants d’IU propriétaires avec des applications de formulaires ;
* utiliser la puissance d’Adobe Experience Manager Forms ;

Vous pouvez envoyer un courrier électronique à `aem-forms-headless@adobe.com` à partir de votre ID de courrier électronique officiel pour rejoindre le programme des premiers adopteurs.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
