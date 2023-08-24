---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 6b4fa2802b860c938f5085f047cc880f29698f3e
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 15%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 13206 {#release-13206}

Vous trouverez ci-dessous un résumé des améliorations continues apportées à la version de maintenance 13206, qui a été publiée publiquement le 21 août 2023. Cette version de maintenance remplace les versions 13173 et 13099 pour résoudre un problème affectant la fonctionnalité de boîte de réception.

2023.8.0 Feature Activation fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions du Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour plus d’informations.

### Améliorations {#enhancements-13206}

- SITES-13906 : GraphQL - Mise à niveau vers graphql-java 20.1.
- SITES-8972 : GraphQL - Ajout d’une étiquette d’option dans JSON pour le type de données Énumération .
- SITES-9689 : GraphQL - Ajoutez un titre et une description dans JSON pour le type de données de référence de contenu.
- SITES-13052 : Fragments de contenu - Exporter des fragments de contenu vers Adobe Target.

### Problèmes résolus {#fixed-issues-13206}

- SITES-14937 : MSM - Hériter des configurations de déploiement de la valeur Parent est activé lorsque vous appuyez sur Enregistrer et fermer sur les Live Copies.
- SITES-14847 : Fragments de contenu - Les liens de fragments de contenu ne sont pas mis en surbrillance.
- SITES-11620 : Fragments de contenu - Le chemin des références est légèrement coupé dans l’interface utilisateur.
- SITES-14171 : GraphQL - Dans certains cas, les références circulaires ne sont pas rompues pour les données mises en cache.
- SITES-14577 : Fragments d’expérience - La publication en bloc ne fonctionne pas pour les Live Copies.
- SITES-14341 : Interface utilisateur d’administration - Comportement incohérent du bouton &quot;Propriétés&quot; lorsque les autorisations de suppression sont supprimées.
- SITES-11000 : Interface utilisateur d’administration - Références : liens entrants manquants dans certaines pages.
- SITES-11559 : Interface utilisateur d’administration - Références : les liens entrants affichent des pages incorrectes.
- SITES-14337 : Interface utilisateur d’administration - L’ouverture de la page de l’éditeur génère une erreur dans des cas spécifiques.
- SITES-13425 : ContextHub - La barre de menus ne s’affiche pas lorsque vous cliquez sur le bouton ContextHub.
- CQ-4354266 : impossible d’ouvrir les éléments de boîte de réception.
- CQ-4354279 : impossible d’afficher le rapport d’activité sous l’onglet Personnalisation .
- FORMS-9971 : lorsqu’un formulaire adaptatif est rendu dans un autre paramètre régional, la visibilité des composants est interprétée et appliquée de manière incorrecte.
- FORMS-9888 : lorsqu’un formulaire adaptatif est défini pour rediriger vers une URL externe (page de remerciement) lors de l’envoi du formulaire, il ne parvient pas à rediriger vers l’URL externe.
- FORMS-9845 : après avoir effacé une liste déroulante à l’aide de l’éditeur de règles, les valeurs fournies précédemment persistent, malgré l’autorisation supposée.
- FORMS-9263 : lorsque le libellé d’une case à cocher contient des caractères spéciaux et qu’un utilisateur clique sur la case à cocher, la case correspondante n’est pas sélectionnée.
- FORMS-9254 : lorsqu’un utilisateur fait défiler le texte du composant Conditions générales, la case à cocher du composant est automatiquement activée, même avant que l’utilisateur n’ait fait défiler le texte entier.
- FORMS-9045 : la balise de script ne résout pas les références de fragments externes dans le fichier XDP de base.
- FORMS-9026 : lorsque vous tentez de créer un formulaire adaptatif à l’aide d’un schéma JSON comportant des énumérations avec des chaînes vides et des validations sans erreur, le processus échoue. Ensuite, lors de l’actualisation de la page, le formulaire ne se charge pas correctement, affichant un formulaire vide avec une erreur dans les journaux.
- FORMS-8964 : dans Android™ Chrome/Firefox, le texte ne peut plus être modifié dans le composant Zone de texte si la limite de caractères maximale est atteinte.
- FORMS-8668 : Les vidages de pile Java™ excessifs dans les journaux d’erreurs, malgré le rendu fonctionnel du formulaire, provoquent un remplissage du fichier journal.
- FORMS-8554 : Les Forms adaptatives avec chargement différé activé ne fonctionnent pas en mode d’aperçu de l’instance de création.
- FORMS-8177 : lorsque le service Forms est actif, une exception &quot;com.adobe.aem.formsndocuments.publish.AssetReferenceProvider Échec de la récupération des dépendances de ressources&quot; s’affiche. survient. L’erreur disparaît lors de la désactivation du service de formulaire.
- FORMS-3691 : l’application de plage IIFE (Expression de fonction immédiatement invoquée) manque à certains objets. L’utilisation d’un IIFE a pour principal objectif de créer une portée pour les variables au sein de la fonction, afin d’empêcher ces variables de polluer la portée globale.
- SITES-15463 : Modèles de sites - Les modèles ne peuvent pas être publiés.

### Problèmes connus {#known-issues-13206}

- SITES-15359 : Fragments de contenu - Le modèle de nom de variation ne parvient pas à faire correspondre correctement les variations qui ont ```'_'``` dans leurs noms de ressources.
- FORMS-10444 : Modèles Forms adaptatifs - Les modèles ne peuvent pas être publiés (solution : utilisez la console de distribution).
- CQ-4354191 : Workflows : le lanceur personnalisé peut se déclencher de nombreuses fois en raison des métadonnées de réplication présentes sur les noeuds non structurés nt:unstructured (solution : mise à jour des lanceurs pour exclure les propriétés de métadonnées de réplication afin d’éviter les chevauchements).
- SITES-15622 : GraphQL - Problème avec les requêtes persistantes avec les paramètres numériques et booléens.
- SITES-15654 : GraphQL - Problèmes liés aux unions et propriétés du même nom.

### Technologies intégrées {#embedded-tech-13206}

| Technologie | Version | Lien |
|---|---|---|
| AEM OAK | 1.52-T20230629133256-25c01b8 | [API Oak 1.52.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.52.0/index.html) |
| API SLING AEM | Version 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | Version 2.23.2 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
