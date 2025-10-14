---
title: Utilisation de l’extension de références externes AJO de fragments de contenu
description: En savoir plus sur l’extension Références externes AJO de fragments de contenu
feature: Content Fragments
role: User, Developer, Architect
solution: Experience Manager Sites
source-git-commit: f755a5c621b68b3110642e6cfe150798555b6707
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 1%

---


# Extension Références externes AJO de fragments de contenu {#content-fragment-external-references-extension}

Pour prévisualiser les expériences d’AEM sur un autre produit Adobe, vous pouvez activer l’extension d’interface utilisateur :

* **Références externes AJO**

L’extension Références externes AJO fonctionne en récupérant des références à un fragment de contenu de toutes les organisations et de tous les sandbox associés à des balises prédéfinies. L’extension affiche ensuite les détails.

Par exemple, pour une intégration à Adobe Journey Optimizer (AJO), les détails dépendent du fait que la référence est une campagne, un Parcours ou un modèle.

>[!NOTE]
>
>Pour plus d’informations sur la manière d’activer l’extension, voir [Extension Manager dans AEM Experience Manager.](https://developer.adobe.com/uix/docs/extension-manager/)

Par exemple, pour utiliser l’extension avec AJO :

>[!NOTE]
>
>Voir aussi [Intégration d’AJO](https://experienceleague.adobe.com/fr/docs/journey-optimizer/using/integrations/aem-fragments).

1. Ouvrez la [&#x200B; Console Fragments de contenu &#x200B;](/help/sites-cloud/administering/content-fragments/overview.md#content-fragments-console).

1. Accédez à votre fragment de contenu : fragment qui a été créé et utilisé sur différents canaux AJO.

1. Ouvrez votre fragment de contenu dans l’[éditeur](/help/sites-cloud/administering/content-fragments/managing.md#editing-the-content-of-your-fragment).

1. L’extension Références externes AJO est disponible sous la forme d’un onglet dans le panneau de droite. Sélectionnez l’onglet pour ouvrir l’extension :

   ![Extension Références externes AJO](/help/sites-cloud/administering/content-fragments/assets/cf-ajo-fragment-external-references-extension.png)

   Une fois qu’un type de référence est sélectionné, l’extension affiche les références externes correspondantes sous la forme d’un tableau avec les colonnes :

   * **Name** : nom de la référence dans laquelle le fragment de contenu est utilisé
   * **Aperçu** sélectionnez ce lien pour démarrer l’aperçu
   * **Statut** : statut de la référence

1. Vous pouvez sélectionner le **Type de référence** dans la liste déroulante pour basculer entre trois types de référence :

   * **Campagne**
      * Affiche une liste de toutes les campagnes avec des liens vers le fragment de contenu actuel.
      * Vous pouvez ensuite prévisualiser une campagne sélectionnée.
      * Par défaut
   * **Parcours**
      * Affiche le dernier Parcours.
      * Vous pouvez ensuite sélectionner et prévisualiser un Parcours sélectionné.
   * **Modèle**
      * Affiche les modèles liés au fragment de contenu.
      * Vous pouvez ensuite sélectionner et prévisualiser un modèle sélectionné.