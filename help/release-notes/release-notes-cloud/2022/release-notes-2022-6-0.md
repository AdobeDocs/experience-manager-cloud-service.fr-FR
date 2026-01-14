---
title: Notes de mise à jour de la version 2022.6.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2022.6.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: cf2133dc-56cd-4a07-ab11-72e16f015ff5
feature: Release Information
role: Admin
source-git-commit: 281a8efcd18920dd926d92db9c757c0513d599fd
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 77%

---

# Notes de mise à jour de la version 2022.6.0 d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section ci-dessous présente les notes de mise à jour des fonctionnalités de la version 2022.6.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle (2022.6.0) de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le 30 juin 2022.

La prochaine version (2022.7.0) est prévue pour le 8 août 2022.

## Vidéo de mise à jour {#release-video}

Consultez la vidéo Aperçu de la version de juin 2022 pour obtenir un résumé des fonctionnalités ajoutées dans la version 2022.6.0 :

>[!VIDEO](https://video.tv.adobe.com/v/344308/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités de [!DNL Sites] {#sites-features}

* Une nouvelle [interface utilisateur](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console) est désormais disponible pour que les administrateurs et les auteurs de contenu puissent gérer efficacement (comme publier, dépublier, copier, déplacer, etc.), rechercher/filtrer et créer des fragments de contenu pour des cas d’utilisation découplés.

  ![Console Fragments de contenu](/help/release-notes/assets/cf-ui.png)

* Le nouveau [Composant Table des matières](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/tableofcontents.html?lang=fr) fonctionne non seulement avec les composants principaux, mais aussi avec tous les composants. Il effectue automatiquement le rendu des tables des matières sur les pages de contenu. Et comme il est rendu côté serveur et entièrement mis en cache par le Dispatcher, il est également efficace à charger.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

Experience Manager Assets utilise désormais les fonctionnalités de l’IA d’Adobe pour [faire la distinction entre les couleurs d’une image et les appliquer automatiquement sous forme de balises lors de l’ingestion](/help/assets/color-tag-images.md). Ces balises permettent d’améliorer l’expérience de recherche en fonction de la composition des couleurs de l’image. Vous pouvez configurer le nombre de couleurs, comprises entre 1 et 40, qui sont balisées vers une image afin de pouvoir rechercher ultérieurement des images en fonction de ces couleurs.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités de [!DNL Forms] {#forms-features}

* **[Intégrer des formulaires adaptatifs à Microsoft® Power Automate](/help/forms/forms-microsoft-power-automate-integration.md)** : vous pouvez désormais configurer un formulaire adaptatif pour exécuter un flux cloud Microsoft® Power Automate lors de l’envoi. Le formulaire adaptatif configuré envoie les données capturées, les pièces jointes et le document d’enregistrement au flux Cloud Power Automate pour traitement. Il vous permet de créer une expérience de capture de données personnalisée tout en tirant parti de la puissance de Microsoft® Power Automate pour élaborer des logiques commerciales autour des données capturées et automatiser les workflows client.

* **Assistant de création d’un formulaire adaptatif** : vous pouvez utiliser l’assistant convivial destiné aux utilisateurs professionnels pour créer rapidement des formulaires adaptatifs. L’assistant fournit une navigation rapide par onglets pour sélectionner facilement un modèle, un style, des champs et des options d’envoi préconfigurés afin de créer un formulaire adaptatif.

  ![Assistant de création d’un formulaire adaptatif](/help/release-notes/assets/wizard.png)

## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Nouvelle page des propriétés du cockpit du produit pour un aperçu plus pertinent et simplifié

![Présentation des propriétés du cockpit du produit](/help/assets/CIF/product_cockpit_properties_overview.png)

* Amélioration de la compatibilité et de la robustesse pour les connecteurs tiers sur I/O Runtime

* Amélioration de la prise en charge des remplacements de la configuration du client GQL (par exemple, définition du comportement de mise en cache personnalisée)

* Plusieurs points d’entrée commerciaux sont désormais pris en charge par défaut et peuvent être configurés via Cloud Manager. Vous trouverez des informations détaillées sur le blog CIF [ici](https://medium.com/adobetech/use-aem-as-a-cloud-service-with-multiple-adobe-commerce-systems-9295612a9554).


### Correctifs {#bug-fixes-cif}

* Le champ de sélecteur de produits à plusieurs valeurs affiche le second produit et les produits supplémentaires comme non valides.

* Le sélecteur de produit est parfois masqué derrière les composants.

## Module complémentaire Demos de référence {#cloud-services-demos}

### Nouveautés {#what-is-new-demos}

* Nouveau modèle Content and Commerce WKND qui ajoute au WKND une expérience d’achat E2E comprenant un catalogue de produits, un panier, un passage en caisse et myAccount. Ce modèle utilise CIF et ses composants principaux CIF. Vous devez donc également installer le module complémentaire CIF. Vous trouverez des informations détaillées sur le blog CIF [ici](https://medium.com/adobetech/learn-how-to-create-a-shoppable-experience-with-the-new-wknd-reference-site-and-cif-b3b2c161f67e).

![Boutique WKND](/help/assets/CIF/wknd_shop.png)

![Pdp WKND](/help/assets/CIF/wknd_pdp.png)

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Nouveautés {#what-is-new-foundation}

* Comme indiqué dans les notes de mise à jour de mai (2022.5.0), l’option « Ajouter une arborescence » sous l’onglet **Distribuer** de l’écran d’administration de l’agent de réplication a été supprimée. Les packages avec une arborescence de contenu doivent plutôt être répliqués à l’aide de [Gérer la publication](/help/operations/replication.md#manage-publication) ou du workflow [Publier l’arborescence de contenu](/help/operations/replication.md#manage-publication#publish-content-tree-workflow).

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
