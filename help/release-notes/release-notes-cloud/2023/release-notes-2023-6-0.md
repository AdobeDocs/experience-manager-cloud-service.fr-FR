---
title: Notes de mise à jour de la version 2023.6.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2023.6.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 29cf9548-e413-4e4f-b233-d6bb04918b22
feature: Release Information
role: Admin
source-git-commit: f28f212574dda0ece2cedb56a714d381e5bd7d3c
workflow-type: ht
source-wordcount: '1322'
ht-degree: 100%

---

# Notes de mise à jour de la version 2023.6.0 d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour de la version 2023.6.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2021 ou 2022.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle (2023.6.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le 29 juin 2023. La prochaine disponibilité des fonctionnalités (2023.7.0) est prévue pour le 27 juillet 2023.

## Vidéo de mise à jour {#release-video}

Consultez la vidéo Aperçu de la version de juin 2023 pour obtenir un résumé des fonctionnalités ajoutées dans la version 2023.6.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3420971/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités de [!DNL Experience Manager Sites] {#sites-features}

* Les fragments de contenu et leurs références peuvent désormais être publiés dans le [service de prévisualisation AEM](/help/implementing/cloud-manager/manage-environments.md#access-preview-service) en utilisant la [console de fragments de contenu](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console). Cela permet aux utilisateurs et utilisatrices de prévisualiser l’expérience finale sur une application de prévisualisation découplée avant la mise en ligne.

![Aperçu dans la console de fragments de contenu.](/help/assets/content-fragments-console-preview.png)

* Les images peuvent désormais être optimisées dynamiquement pour une diffusion web dans des scénarios découplés via GraphQL d’AEM. Les [variables de requête](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/images.html?lang=fr#query-variables) peuvent être définies dans les requêtes GraphQL pour permettre aux applications clientes découplées de demander à AEM des images optimisées en conséquence.
* Les balises sur les [variations de fragments de contenu](https://experienceleague.adobe.com/docs/experience-manager-65/assets/content-fragments/content-fragments-variations.html?lang=fr) peuvent désormais être générées au format JSON à l’aide de l’API de diffusion de contenu GraphQL d’AEM.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

**Disponibilité de la nouvelle vue Assets**

La [nouvelle vue Assets](/help/assets/assets-view-introduction.md) est désormais disponible dans Experience Manager Assets. La vue Assets propose une interface utilisateur simplifiée, qui facilite la gestion, la découverte et la distribution des ressources numériques. L’expérience est destinée aux créateurs et créatrices, aux consommateurs et consommatrices de ressources en lecture seule et aux utilisateurs et utilisatrices de DAM plus légers.

![Gestion du balisage](/help/assets/assets/my-workspace.png)

**Améliorations de l’expérience de recherche**

Experience Manager Assets vous permet maintenant d’en faire plus à partir de l’interface utilisateur des résultats de recherche. Vous pouvez désormais :

* [Effectuez une recherche dans l’emplacement actuel du référentiel](/help/assets/search-assets.md) par défaut au lieu de rechercher le mot-clé dans le référentiel entier.

* [Accédez à l’emplacement du dossier](/help/assets/search-assets.md#aftersearch) des ressources qui s’affichent dans les résultats de recherche.

**Aperçus de miniatures pour les ressources 3D**

[!DNL Experience Manager Assets] génère maintenant des [aperçus des miniatures pour les formats de fichiers 3D courants](/help/assets/file-format-support.md), notamment gLB, USDz, FBX, 3DS, OBJ et SBSAR. Lorsque ces fichiers sont chargés, les miniatures sont automatiquement générées par défaut.

**Dynamic Media : mise à jour des champs liés au recadrage intelligent dans le profil d’image**

L’interface utilisateur de certains champs liés au redrage intelligent dans un profil d’image est désormais mise à jour pour prendre en compte les instructions actuelles pour définir un recadrage intelligent. Voir [Options de recadrage](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles.html?lang=fr#crop-options).

### Nouvelles fonctionnalités de la vue Assets {#assets-view-features}

**Balisage hiérarchique des ressources pour une expérience de recherche plus rapide**

Les listes plates de vocabulaires contrôlés deviennent ingérables au fil du temps. La vue Assets prend désormais en charge la [structure hiérarchique du balisage](/help/assets/tagging-management-assets-view.md), qui facilite l’application des métadonnées pertinentes, la classification des ressources, la prise en charge de la recherche, la réutilisation des balises, l’amélioration de la visibilité, etc.

![Gestion du balisage](/help/assets/assets/tags-hierarchy.png)

**Épingler les fichiers, les dossiers et les collections pour un accès rapide**

Vous pouvez désormais [épingler des fichiers, des dossiers et des collections pour y accéder plus rapidement](/help/assets/my-workspace-assets-view.md) lorsque vous en aurez besoin ultérieurement. Les éléments épinglés s’affichent dans la section **Accès rapide** de Mon espace de travail. Vous pouvez y accéder à l’aide de Mon espace de travail au lieu d’accéder à l’emplacement où ils sont enregistrés dans le référentiel.

![Tâches dans l’espace de travail](/help/assets/assets/quick-access.png)

**Filtrer les ressources dans le dossier Corbeille**

La vue Assets vous permet désormais de [filtrer les ressources disponibles dans le dossier Corbeille](/help/assets/navigate-assets-view.md). Vous pouvez appliquer des filtres standard ou personnalisés pour rechercher les ressources appropriées dans le dossier Corbeille afin de les restaurer ou de les supprimer définitivement.

**Aperçus de miniatures pour les ressources 3D**

La vue Assets génère désormais des aperçus de miniatures pour les formats de fichiers 3D courants, notamment gLB, USDz, FBX, 3DS, OBJ et SBSAR. Lorsque ces fichiers sont chargés dans la vue Assets, par défaut, les miniatures sont automatiquement générées par le système.

![Tâches dans l’espace de travail](/help/assets/assets/3d-preview.png)

**Afficher les termes les plus recherchés**

La vue Assets prend désormais en charge l’[affichage des termes recherchés les plus courants dans votre déploiement](/help/assets/my-workspace-assets-view.md) à l’aide de la section **Insights** de Mon espace de travail. Vous pouvez également accéder aux informations pour afficher les principales recherches effectuées au cours des 30 derniers jours ou 12 derniers mois.

![Tâches dans l’espace de travail](/help/assets/assets/insights-top-searches.png)

**Améliorations des formulaires de métadonnées**

La vue Assets vous permet désormais d’[ajouter des composants de propriété texte et de liste déroulante à plusieurs valeurs](/help/assets/metadata-assets-view.md#property-components) aux formulaires de métadonnées.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités disponibles dans [!DNL Forms] {#new-features-available-in-channel}

* [Formulaires adaptatifs dans l’éditeur de page AEM](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md) : vous pouvez désormais utiliser l’éditeur de page AEM pour créer et ajouter rapidement plusieurs formulaires à vos pages Sites. Cette fonctionnalité permet aux auteurs et autrices de contenu de créer des expériences fluides de capture de données dans les pages Sites à l’aide de la puissance des composants de formulaires adaptatifs, notamment le comportement dynamique, les validations, l’intégration de données, la génération d’un document d’enregistrement et l’automatisation de la gestion commerciale. Vous pouvez effectuer les actions suivantes :

   * Créer un formulaire adaptatif en faisant glisser les composants de formulaire vers le composant de conteneur de Forms adaptatif dans l’éditeur AEM Sites ou les fragments d’expérience.
   * Utiliser l’assistant de formulaires adaptatifs dans l’éditeur AEM Sites pour créer des formulaires indépendants de n’importe quelle page Sites, ce qui vous permet de réutiliser ces formulaires sur plusieurs pages.
   * Ajouter plusieurs formulaires à une page Sites, en rationalisant l’expérience client et en offrant une plus grande flexibilité.

     >[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

* [Adobe Acrobat Sign Solutions pour le gouvernement](/help/forms/adobe-sign-integration-adaptive-forms.md) : AEM Forms s’intègre désormais à Adobe Acrobat Sign Solutions pour le gouvernement. Cette intégration offre un niveau avancé de conformité et de sécurité pour les signatures électroniques avec les envois de formulaires adaptatifs pour les comptes associés au gouvernement (ministères et organismes gouvernementaux).

  L’intégration à Adobe Acrobat Sign Solutions pour le gouvernement permet aux partenaires d’Adobe et aux clients gouvernementaux d’utiliser des signatures électroniques dans les formulaires adaptatifs pour certains secteurs d’activité les plus critiques et les plus sensibles. Cette couche supplémentaire de sécurité garantit que toutes les signatures électroniques sont entièrement conformes à la norme FedRAMP Moderate, offrant ainsi la tranquillité d’esprit aux clientes et clients gouvernementaux d’Adobe.

* [Amélioration de la gestion des erreurs avec les gestionnaires d’erreurs personnalisés dans l’éditeur de règles](/help/forms/add-custom-error-handler-adaptive-forms.md) : vous pouvez désormais appeler une fonction personnalisée (à l’aide de la bibliothèque cliente) en réponse à une erreur renvoyée par un service externe et fournir une réponse personnalisée aux utilisateurs et utilisatrices finaux. Vous pouvez également effectuer des actions spécifiques pour les erreurs renvoyées par un service. Par exemple, vous pouvez appeler un workflow personnalisé dans le serveur principal pour des codes d’erreur spécifiques ou informer le client ou la cliente que le service est indisponible.

  Cette fonctionnalité contribue à améliorer votre fonctionnalité globale de gestion des erreurs en introduisant des réponses d’erreur basées sur des normes qui sont rétrocompatibles avec les gestionnaires d’erreurs prêts à l’emploi, avec une plus grande flexibilité et un meilleur contrôle.

* [Méthodes d’authentification améliorées pour le modèle de données de formulaire](/help/forms/configure-data-sources.md) : une sécurité renforcée grâce à l’introduction de l’authentification basée sur les informations d’identification client pour connecter AEM Forms à des sources de données compatibles. Cette amélioration élimine le besoin d’emprunt d’identité ou de connexion de l’utilisateur ou de l’utilisatrice, renforçant ainsi la protection de vos données.

* [Formulaires adaptatifs avec des sections répétables](/help/forms/create-forms-repeatable-sections.md) : vous pouvez désormais créer des composants [Accordéon](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html#features?lang=fr), [Assistant](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html#features?lang=fr), [Panneau](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel), et [Onglets horizontaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html#features?lang=fr) dans un formulaire adaptatif basé sur les composants principaux pour créer des sections répétables.

  >[!VIDEO](https://video.tv.adobe.com/v/3421052/adaptive-forms-repeatable-sections-repeat-sections/?quality=12&learn=on)

  Ces sections répétables vous permettent de fournir un nombre illimité d’entrées sans nombre fixe de champs. Cela est utile lorsque les instances de données requises sont inconnues à l’avance. Les utilisateurs et les utilisatrices de Forms peuvent facilement ajouter ou supprimer des sections, ce qui permet d’adapter les formulaires à différents scénarios de saisie de données et de simplifier la collecte de plusieurs occurrences des mêmes données.

* **[Envoyer des formulaires adaptatifs à Microsoft® SharePoint et Microsoft® OneDrive](/help/forms/configuring-submit-actions.md)** : améliorez l’agilité des utilisateurs et utilisatrices professionnels pour lancer rapidement de nouveaux formulaires et stockez les données envoyées dans les outils quotidiens qu’ils utilisent comme les sites Microsoft® SharePoint ou les dossiers OneDrive.

### Programme des formulaires adaptatifs découplés destiné aux utilisateurs et utilisatrices précoces {#forms-early-adopter}

Utilisez les [formulaires adaptatifs découplés](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=fr) pour permettre à vos développeurs et développeuses de créer, publier et gérer des formulaires interactifs accessibles via des API, plutôt que par le biais d’une interface utilisateur graphique classique. Les formulaires adaptatifs découplés vous aident à :

* créer des formulaires multicanaux de haute qualité dans le langage de programmation de votre choix ;
* intégrer nativement les formulaires à vos applications de bureau et mobiles, à vos sites web et à vos applications de chat ;
* réutiliser vos composants d’IU propriétaires avec des applications de formulaires ;
* tirer profit de la puissance d’Adobe Experience Manager Forms

Vous pouvez envoyer un e-mail à `aem-forms-headless@adobe.com` à partir de votre ID d’e-mail officiel pour rejoindre le programme d’utilisateurs et utilisatrices précoces.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
