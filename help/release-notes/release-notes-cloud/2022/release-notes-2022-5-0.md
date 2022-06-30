---
title: Notes de mise à jour de la version 2022.5.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour de la version 2022.5.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
source-git-commit: 9c76ff2e0b789894ef5492ee940ce79cddb47e11
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 21%

---


# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour générales de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] la version actuelle (2022.5.0) est le 9 juin 2022.
La prochaine version (2022.6.0) est prévue pour le 30 juin 2022.

## Vidéo de mise à jour {#release-video}

Regardez la vidéo Présentation de la version de mai 2022 pour un résumé des fonctionnalités ajoutées dans la version 2022.5.0 :

>[!VIDEO](https://video.tv.adobe.com/v/343321/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Sites] {#prerelease-features-sites}

* Diverses fonctionnalités de GraphQL
* A [nouvelle console](/help/headless/content-fragments/content-fragment-console.md) optimisé pour une utilisation sans affichage des fragments de contenu

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* [Imagerie dynamique Dynamic Media](https://medium.com/adobetech/one-solution-fits-all-smart-imaging-with-aem-dynamic-media-be690b62df9f) prend désormais en charge le format de fichier AVIF. Améliorez davantage la Google Core Web Vital (avec la plus grande peinture contextuelle), l’AVIF offrant une réduction de taille supplémentaire de 20 % par rapport à WebP. Au total, l’AVIF offre une réduction de taille moyenne de 41 % sur le JPEG (dans certaines images même si elle atteint 76 %).

* [!UICONTROL Experience Manager Assets Brand Portal] exécute désormais des tâches automatiques toutes les douze heures afin de supprimer toutes les ressources Brand Portal publiées sur AEM. Par conséquent, vous n’avez pas besoin de supprimer manuellement les ressources du dossier Contribution pour que la taille du dossier reste inférieure à la limite de seuil. [Nouveautés d’Experience Manager Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html?lang=fr).

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Assets] {#prerelease-features-assets}

Experience Manager Assets utilise désormais les fonctionnalités d’Adobe Sensei AI pour [faire la distinction entre les couleurs d’une image et les appliquer automatiquement sous forme de balises lors de l’ingestion ;](/help/assets/color-tag-images.md). Ces balises permettent d’améliorer l’expérience de recherche en fonction de la composition des couleurs de l’image. Vous pouvez configurer le nombre de couleurs, comprises entre 1 et 4, qui sont balisées vers une image afin de pouvoir rechercher ultérieurement des images en fonction de ces couleurs.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Forms] {#prerelease-features-forms}

* **Intégration de Forms adaptatif à Microsoft® Power Automate**: Vous pouvez désormais configurer un formulaire adaptatif pour exécuter un flux cloud Microsoft® Power Automate Cloud lors de l’envoi. Le formulaire adaptatif configuré envoie les données, les pièces jointes et le document d’enregistrement capturés à Power Automate Cloud Flow pour traitement. Il vous permet de créer une expérience de capture de données personnalisée tout en tirant parti de la puissance de Microsoft® Power Automate pour élaborer des logiques commerciales autour des données capturées et automatiser les workflows client.

* **Assistant de création d’un formulaire adaptatif**: Vous pouvez utiliser l’assistant convivial destiné aux entreprises pour créer rapidement un Forms adaptatif. L’assistant fournit une navigation rapide par onglets pour sélectionner facilement un modèle, un style, des champs et des options d’envoi préconfigurés afin de créer un formulaire adaptatif.

   ![Assistant de création d’un formulaire adaptatif](/help/release-notes/assets/wizard.png)

## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Accès rapide au cockpit du produit : Accédez facilement à des informations détaillées sur les produits en un seul clic dans l’éditeur de sites.

   ![Activer la liste bloquée](/help/assets/CIF/enable-wishlist.png)

* Prise en charge de composants commerciaux marketing supplémentaires : Les composants peuvent être configurés pour afficher un appel à l’action de type &quot;ajouter au panier&quot; et &quot;ajouter à une liste de souhaits&quot;.

   ![Raccourci de l’éditeur de sites vers le cockpit du produit](/help/assets/CIF/sites-editor-shortcut-to-cockpit.png)


## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Nouveautés {#what-is-new-foundation}

* L’option &quot;Ajouter une arborescence&quot; sous l’écran de l’administrateur de l’agent de réplication **Onglet Répartir**, précédemment annoncé comme obsolète, sera supprimé le 20 juin 2022 ou peu de temps après. Les modules avec une arborescence de contenu doivent plutôt être répliqués à l’aide de [Gérer la publication](/help/operations/replication.md#manage-publication) ou le [Processus de publication de l’arborescence de contenu](/help/operations/replication.md#publish-content-tree-workflow).

* L’utilisation de l’écran d’administration de l’agent de réplication ou de l’API de réplication pour distribuer des modules de contenu de plus de 10 Mo (noeuds avec des propriétés, sans inclure les fichiers binaires) est obsolète et sera appliquée le 12 septembre 2022 ou peu de temps après. Au lieu de cela, [Gérer la publication](/help/operations/replication.md#manage-publication) ou le [Processus de publication de l’arborescence de contenu](/help/operations/replication.md#publish-content-tree-workflow) doit être utilisé pour répliquer ces modules de contenu volumineux. En juillet, un message d’avertissement s’affiche dans l’écran de l’administrateur de l’agent de réplication. **Onglet Répartir** si vous tentez de répliquer ces packages de contenu volumineux et également dans le journal d’erreurs AEM chaque fois que l’API de réplication est utilisée pour répliquer ces packages de contenu volumineux. En septembre, les avertissements seront remplacés par des erreurs. Ajustez vos processus en conséquence.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Experience Manager] {#prerelease-features-foundation}

* AEM as a Cloud Service est désormais intégré à Unified Shell pour améliorer l’expérience utilisateur et l’unifier avec toutes les autres applications Experience Cloud. Voir [AEM as a Cloud Service sur Shell unifié](/help/overview/aem-cloud-service-on-unified-shell.md) pour plus d’informations.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation Security {#foundation-security}

### Dépréciation de TLS 1.0, 1.1

À compter du 30 juin 2022, l’as a Cloud Service Experience Manager devra disposer d’une communication réseau plus sécurisée et d’un échange de données avec les systèmes utilisateurs. AEM utilisera exclusivement le protocole TLS (Transport Layer Security), version 1.2. Les anciennes versions de TLS 1.0 et 1.1 seront obsolètes.

Si vous continuez à utiliser des versions antérieures de TLS as 1.0, 1.1, vous risquez de perdre l’accès à Experience Manager as a Cloud Service.

## Cloud Manager {#cloud-manager}

Vous trouverez une liste complète des versions mensuelles de Cloud Manager [here](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [here](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
