---
title: Notes de mise à jour de la version 2022.5.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour de la version 2022.5.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 1b867582-e34c-435b-b8f8-fc71dddcaccb
feature: Release Information
role: Admin
source-git-commit: 281a8efcd18920dd926d92db9c757c0513d599fd
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 64%

---

# Notes de mise à jour de la version 2022.5.0 d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section ci-dessous présente les notes de mise à jour des fonctionnalités de la version 2022.5.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle (2022.5.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le 9 juin 2022.
La prochaine version (2022.6.0) est prévue pour le 30 juin 2022.

## Vidéo de mise à jour {#release-video}

Consultez la vidéo Aperçu de la version de mai 2022 pour obtenir un résumé des fonctionnalités ajoutées dans la version 2022.5.0 :

>[!VIDEO](https://video.tv.adobe.com/v/343321/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Sites] {#prerelease-features-sites}

* Diverses fonctionnalités GraphQL
* [Nouvelle console](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console) optimisée pour une utilisation headless des fragments de contenu

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* L’[imagerie dynamique Dynamic Media](https://medium.com/adobetech/one-solution-fits-all-smart-imaging-with-aem-dynamic-media-be690b62df9f) prend désormais en charge le format de fichier AVIF. Améliorez davantage les Signaux Web essentiels de Google (Largest Contentful Paint) avec l’AVIF, qui offre une réduction de taille supplémentaire de 20 % par rapport à WebP. Au total, l’AVIF offre une réduction de taille moyenne de 41 % sur le JPEG (pouvant aller jusqu’à 76 % dans certaines images).

* [!UICONTROL Experience Manager Assets Brand Portal] exécute désormais des tâches automatiques toutes les 12 heures afin de supprimer toutes les ressources Brand Portal publiées sur AEM. Par conséquent, vous n’avez pas besoin de supprimer manuellement les ressources du dossier Contribution pour que la taille du dossier reste inférieure à la limite de seuil. [Nouveautés d’Experience Manager Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html?lang=fr).

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Assets] {#prerelease-features-assets}

Experience Manager Assets utilise désormais les fonctionnalités de l’IA d’Adobe pour [faire la distinction entre les couleurs d’une image et les appliquer automatiquement sous forme de balises lors de l’ingestion](/help/assets/color-tag-images.md). Ces balises permettent d’améliorer l’expérience de recherche en fonction de la composition des couleurs de l’image. Vous pouvez configurer le nombre de couleurs, comprises entre 1 et 40, qui sont balisées vers une image afin de pouvoir rechercher ultérieurement des images en fonction de ces couleurs.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Forms] {#prerelease-features-forms}

* **Intégrer des formulaires adaptatifs à Microsoft® Power Automate** : vous pouvez désormais configurer un formulaire adaptatif pour exécuter un flux cloud Microsoft® Power Automate lors de l’envoi. Le formulaire adaptatif configuré envoie les données capturées, les pièces jointes et le document d’enregistrement au flux Cloud Power Automate pour traitement. Il vous permet de créer une expérience de capture de données personnalisée tout en tirant parti de la puissance de Microsoft® Power Automate pour élaborer des logiques commerciales autour des données capturées et automatiser les workflows client.

* **Assistant de création d’un formulaire adaptatif** : vous pouvez utiliser un assistant convivial destiné aux utilisateurs professionnels pour créer rapidement un Forms adaptatif. L’assistant fournit une navigation rapide par onglets pour sélectionner facilement un modèle, un style, des champs et des options d’envoi préconfigurés afin de créer un formulaire adaptatif.

  ![Assistant de création d’un formulaire adaptatif](/help/release-notes/assets/wizard.png)

## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Accès rapide au cockpit du produit : accédez facilement à des informations détaillées sur les produits en un seul clic dans l’éditeur de sites.

<!-- Image was not found during PR validation despite correct path   ![Enable wantlist](/help/assets/CIF/enable-wishlist.png) -->

* Prise en charge de composants commerciaux marketing supplémentaires : les composants peuvent être configurés pour afficher un call-to-action de type « ajouter au panier » et « ajouter à une liste de souhaits ».

  ![Raccourci de l’éditeur de sites vers le cockpit du produit](/help/assets/CIF/sites-editor-shortcut-to-cockpit.png)


## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Nouveautés {#what-is-new-foundation}

* L’option « Ajouter une arborescence » sous l’onglet **Distribuer** de l’écran d’administration de l’agent de réplication, précédemment annoncée comme obsolète, a été supprimée le 20 juin 2022 ou peu de temps après. Les packages avec arborescence de contenu doivent plutôt être répliqués à l’aide des workflows [Gérer la publication](/help/operations/replication.md#manage-publication) ou [Publier l’arborescence de contenu](/help/operations/replication.md#publish-content-tree-workflow).

* L’utilisation de l’écran d’administration de l’agent de réplication ou de l’API de réplication pour distribuer des packages de contenu de plus de 10 Mo (nœuds avec des propriétés, sans inclure les fichiers binaires) est obsolète et mise en œuvre le 12 septembre 2022 ou peu de temps après. À la place, les workflows [Gérer la publication](/help/operations/replication.md#manage-publication) ou [Publier l’arborescence de contenu](/help/operations/replication.md#publish-content-tree-workflow) seront utilisés pour répliquer ces modules de contenu volumineux. En juillet, un message d’avertissement s’affichera dans l’écran de l’administrateur de l’agent de réplication **onglet Distribution** si vous tentez de répliquer ces packages de contenu volumineux, ainsi que dans le journal d’erreurs AEM chaque fois que l’API de réplication est utilisée pour répliquer ces packages de contenu volumineux. En septembre, les avertissements ont été remplacés par des erreurs. Ajustez vos processus en conséquence.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Experience Manager] {#prerelease-features-foundation}

* AEM as a Cloud Service est désormais intégré à Unified Shell pour améliorer l’expérience utilisateur et l’unifier avec toutes les autres applications Experience Cloud. Voir [AEM as a Cloud Service sur Unified Shell](/help/overview/aem-cloud-service-on-unified-shell.md) pour plus d’informations.

## Couche de sécurité [!DNL Experience Manager] as a [!DNL Cloud Service] {#foundation-security}

### Dépréciation de TLS 1.0 et 1.1

À compter du 30 juin 2022, Experience Manager as a Cloud Service aura besoin d’une communication réseau plus sécurisée et d’un échange de données avec les systèmes utilisateurs. AEM utilisera exclusivement le protocole TLS (Transport Layer Security), version 1.2. Les anciennes versions de TLS 1.0 et 1.1 sont désormais obsolètes.

Si vous continuez à utiliser des versions antérieures à TLS 1.0 et 1.1, vous risquez de perdre l’accès à Experience Manager as a Cloud Service.

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
