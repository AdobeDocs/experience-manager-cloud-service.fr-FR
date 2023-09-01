---
title: Notes de mise à jour de la version 2023.7.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2023.7.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
source-git-commit: 1158508cc28d33e5799b3102381f227db05a0107
workflow-type: tm+mt
source-wordcount: '942'
ht-degree: 33%

---


# Notes de mise à jour 2023.7.0 pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour techniques de la version 2023.7.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2021 ou 2022.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] la version actuelle des fonctionnalités (2023.7.0) est le 27 juillet 2023. La prochaine version de la fonctionnalité (2023.8.0) est prévue pour le 31 août 2023.

## Vidéo de mise à jour {#release-video}

Regardez la vidéo Aperçu de la version de juillet 2023 pour un résumé des fonctionnalités ajoutées dans la version 2023.7.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3422016/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités de [!DNL Experience Manager Sites] {#sites-features}

* MSM pour les fragments de contenu. AEM Multi-site Manager est désormais disponible pour les fragments de contenu, ce qui permet de créer des Live Copies de fragments de contenu pour la distribution de contenu en bloc. Les contrôles d’héritage granulaires sont disponibles jusqu’au niveau Elément de fragment de contenu et Niveau de variation.

### Nouvelles fonctionnalités de la préversion de [!DNL Experience Manager Sites] {#prerelease-sites}

* La variable [Console de fragments de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/content-fragments-console.html?lang=en) permet désormais aux utilisateurs d’afficher les balises et de rechercher par balises appliquées en tant que métadonnées aux fragments de contenu. Les utilisateurs n’auront plus à passer à l’interface utilisateur d’Assets pour cette fonctionnalité, ce qui réduit le changement de contexte et améliore l’efficacité.

![Balisage dans la console de fragments de contenu](/help/assets/content-fragments-console-tags.png)

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités dans la vue Assets {#assets-view-features}

<!--

**Assign metadata form to a folder**

You can now assign metadata form to a specific folder within your Assets Essentials deployment. All assets in the folder, including assets in the sub-folders, then display properties defined in the assigned metadata form.

![assign metadata form to a folder](/help/release-notes/assets/assign-to-folder.png)

-->

**Amélioration du framework d’intelligence artificielle pour les balises intelligentes d’image**

Experience Manager Assets utilise désormais un framework d’intelligence artificielle amélioré pour les balises intelligentes d’image. Celui-ci améliore la pertinence et la précision des balises intelligentes disponibles pour toutes les ressources d’image lors de l’ingestion.

**Configurer l’affichage des colonnes pour le mode Liste des ressources**

Assets Essentials permet désormais de sélectionner les colonnes qui s’affichent en mode Liste des ressources, telles que Statut, Format, Dimensions, Taille, etc.

![Configurer les colonnes](/help/release-notes/assets/configure-columns.png)

**Trier les résultats de recherche en fonction de la pertinence**

Assets Essentials trie désormais les résultats de la recherche en fonction de la pertinence, par défaut. Vous pouvez trier les ressources recherchées par ordre croissant ou décroissant de `Name`, `Relevance`, `Size`, `Modified` et `Created`.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités disponibles dans [!DNL Forms] {#new-features-available-in-forms-channel}

* [**Thèmes prêts à l’emploi**](/help/forms/using-themes-in-core-components.md) **et modèles**: lancez le processus de création de formulaires grâce à nos thèmes et modèles prêts à l’emploi, conçus pour offrir aux professionnels chevronnés et aux nouveaux auteurs de formulaires les moyens d’agir. Créés en toute simplicité à l’aide des composants principaux de Forms adaptatif, ces thèmes et modèles soigneusement traités vous permettent de commencer rapidement à créer des formulaires pour des cas d’utilisation courants.

  ![Modèles prêts à l’emploi](/help/forms/assets/form-templates-ootb.png)

* **[Composants React pour Forms sans affichage](https://github.com/adobe/aem-forms-headless-components/tree/main/packages/react-vanilla-components)**: vous pouvez désormais prévisualiser et personnaliser les rendus de formulaire adaptatif sans affichage avec les composants React prêts à l’emploi. Ces composants tirent parti des classes BEM des composants principaux de Forms adaptatif pour la mise en forme, ce qui vous permet de personnaliser facilement leur aspect en fonction de vos besoins spécifiques.

* [**Création d’un Forms adaptatif avec des sections répétables**](/help/forms/create-forms-repeatable-sections.md): vous pouvez désormais effectuer les opérations suivantes : [Accordéon](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html), [Assistant](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html), [Panneau](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html), et [Onglets horizontaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html) formulaire adaptatif basé sur des composants répétable pour plusieurs enregistrements de données.  Ces sections répétables vous permettent de fournir facilement plusieurs entrées de données. Elle est utile lorsque les instances de données requises sont inconnues à l’avance. L’utilisateur d’un formulaire peut facilement ajouter ou supprimer des sections, ce qui rend les formulaires adaptables à différents scénarios de saisie de données et simplifie la collecte de plusieurs occurrences d’un même enregistrement de données.


### Fonctionnalités de préversion disponibles dans [!DNL Forms] {#pre-release-features-available-in-forms-channel}

* [**Support aux entreprises pour Google reCAPTCHA**](/help/forms/captcha-adaptive-forms.md): utilisez Google reCAPTCHA Enterprise dans un formulaire adaptatif pour offrir une meilleure protection contre les activités frauduleuses et les spams, offrant ainsi une expérience utilisateur plus sûre. Grâce à une analyse avancée des risques et à une intégration transparente, les utilisateurs authentiques peuvent facilement envoyer des formulaires lorsque les robots sont effectivement bloqués.

  >[!VIDEO](https://video.tv.adobe.com/v/3422097/adaptive-forms-recaptcha-core-components-captcha/?quality=12&learn=on)

### Programme des formulaires adaptatifs découplés destiné aux utilisateurs et utilisatrices précoces {#forms-early-adopter}

Utilisation [Forms adaptatif sans affichage](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=fr) pour permettre aux développeurs de créer, publier et gérer des formulaires interactifs accessibles et interactifs via des API, plutôt que par le biais d’une interface utilisateur graphique classique. Les formulaires adaptatifs découplés vous aident à :

* créer des formulaires multicanaux de haute qualité dans le langage de programmation de votre choix ;
* intégrer nativement les formulaires à vos applications de bureau et mobiles, à vos sites web et à vos applications de chat ;
* réutiliser vos composants d’IU propriétaires avec des applications de formulaires ;
* utiliser la puissance d’Adobe Experience Manager Forms ;

Vous pouvez envoyer un courrier électronique à `aem-forms-headless@adobe.com` à partir de votre ID de courrier électronique officiel pour rejoindre le programme des premiers adopteurs.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Centre d’actions {#actions-center}

Abonnez-vous aux notifications par e-mail qui vous alertent lorsque des incidents critiques se produisent et nécessitent une action immédiate, ainsi que des recommandations personnalisées pour optimiser votre site. [Centre d’actions](/help/operations/actions-center.md) sert de hub où vous pouvez consulter ces alertes, telles que les files d’attente de réplication bloquées ou les informations d’identification arrivant à expiration, et les marquer comme résolues.

![Capture d’écran du Centre d’actions](/help/assets/assets/actions-center.png)

### Réseau de diffusion de contenu et règles WAF : programme d’adoption précoce {#waf-early-adopter}

Filtrez le trafic sur le réseau de diffusion de contenu selon :
* en-têtes de requête et propriétés (par exemple, adresse IP) ;
* schémas de trafic connus pour être associés à un trafic malveillant

Vous souhaitez tester la fonctionnalité et partager vos commentaires ? Envoi d’un courrier électronique à **aemcs-waf-adopter@adobe.com** à partir de votre ID de courrier électronique officiel pour en savoir plus sur le programme des premiers adopteurs. L&#39;espace est limité.

En savoir plus sur la fonctionnalité de l’article [here](/help/security/cdn-and-waf-rules.md).

### Autres modifications apportées à la base {#other-foundation-changes}

* Au cours de la semaine du 7 août, AEM renverra le code d’erreur 429 au lieu du code d’erreur 503 lorsque les demandes d’AEM d’instances dépassent un niveau sain. [En savoir plus](/help/implementing/developing/introduction/development-guidelines.md).

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
