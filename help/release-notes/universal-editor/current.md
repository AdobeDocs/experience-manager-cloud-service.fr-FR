---
title: Notes de mise à jour de l’éditeur universel version 2025.02.17
description: Il s’agit des notes de mise à jour de la version 2025.02.17 de l’éditeur universel.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: c88aa13c6bc75c8f9cd624d00ef768290981c840
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 23%

---


# Notes de mise à jour de l’éditeur universel version 2025.02.17 {#release-notes}

Voici les notes de mise à jour de la version du 17 février 2025 de l’éditeur universel.

>[!TIP]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service.

## Nouveautés {#what-is-new}

* **Publier pour prévisualiser** - [Lors de la publication (ou de la dépublication) de votre contenu](/help/sites-cloud/authoring/universal-editor/publishing.md) à l’aide de l’éditeur universel, vous pouvez désormais choisir si vous souhaitez publier dans votre [environnement de prévisualisation](/help/sites-cloud/authoring/sites-console/previewing-content.md) en plus de votre environnement de publication
   * Cela permet de réviser votre contenu avant sa publication publique.
* **Le modèle et le filtre peuvent être définis dans la définition du composant** - Vous pouvez désormais définir le modèle et le filtre qu’un composant utilise [dans la définition du composant](/help/implementing/universal-editor/component-definition.md#template).
   * Ces informations peuvent être conservées de manière centralisée dans la définition et n’ont pas besoin d’être spécifiées dans l’instrumentation.
   * Vous pouvez ainsi déplacer des composants entre des conteneurs.
* **Les éléments enfants des conteneurs sont implicitement considérés comme des composants** - Si [ un élément avec `data-aue-resource`](/help/implementing/universal-editor/attributes-types.md#data-properties) est placé en tant qu’enfant direct dans un conteneur, il est considéré comme un composant et peut être déplacé sans avoir à spécifier de `data-aue-behavior="component"`.

## Autres améliorations {#other-improvements}

* **Sélecteur de ressources AEM 6.5** - Le sélecteur de ressources 6.5 s’ouvre désormais correctement lors de l’[exécution de l’éditeur universel avec AEM 6.5.](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction)
