---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 0dab7428d8ae5ec4c11a88ff310fad649a365868
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 20%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 13665 {#release-13665}

Vous trouverez ci-dessous un résumé des améliorations continues apportées à la version de maintenance 13665, publiée publiquement le 27 septembre 2023. Cette version de maintenance remplace la version 13420.

2023.10.0 Feature Activation fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions du Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour plus d’informations.

### Améliorations {#enhancements-13665}

* Diverses améliorations apportées aux API de fragment de contenu.
* ASSETS-26713 : Tableau de bord des ressources : nouveau tableau de bord de l’interface utilisateur d’Experience est désormais accessible à partir de l’interface utilisateur tactile.
* SITES-11206 : Fragments de contenu : API de recherche de fragments de contenu.
* SITES-11262 : Fragments de contenu : bouton pour passer au nouvel éditeur de fragments de contenu.
* SITES-15447 : Core Components : Version 2.23.4.

### Problèmes résolus {#fixed-issues-13665}

* Différentes mises à jour liées aux traductions.
* CQ-4354428 : Workflows : impossible d’effectuer une tâche dans la boîte de réception.
* SITES-9733 : Fragments de contenu : les références de ressources dans le panneau de référence des fragments de contenu affichent 0 (zéro) référence.
* SITES-14561 : Fragments de contenu : correction et amélioration du HTML de la conversion Markup.
* SITES-14882 : Fragments de contenu : une fois que nous avons modifié le fragment de contenu et fermé l’onglet sans cliquer sur le bouton Enregistrer ou fermer, les valeurs sont stockées.
* SITES-15167 : Fragments de contenu : le correctif d’une variation avec une charge utile non valide ne renvoie pas 400 mais 500.
* SITES-15514 : Fragments de contenu : sortie Markdown incorrecte pour le tableau dans l’éditeur de texte enrichi.
* SITES-15661 : Fragments de contenu : n’utilisez pas de contrainte unique et ne réorganisez pas les éléments dans les champs de référence de l’API Fragments.
* SITES-15730 : Screens : la fonctionnalité Aperçu du canal Screens ne fonctionne pas sur le tableau de bord.
* SITES-15995 : Fragments de contenu : les types MIME des champs de texte long de modèle et de fragment sont codés en dur.
* SITES-16074 : Fragments de contenu : Balisez les champs qui ne sont pas des chaînes[] ne peut pas être récupéré depuis JCR.
* SITES-16084 : Fragments de contenu : le navigateur cible est absent de CFHomeCardModelImpl.
* SITES-14773 : Fragments d’expérience : la référence de lien n’est pas mise à jour dans le fragment d’expérience.
* SITES-14899 : Fragments d’expérience : plusieurs offres créées pour des variations XF dans Target.
* SITES-8590 : GraphQL : problèmes de codage des variables dans les requêtes persistantes.
* SITES-9224 : GraphQL : exception &quot;Writer a déjà été fermé&quot; dans GraphQLServlet.
* SITES-14800 : GraphQL : exception dans les requêtes GraphQL persistantes avec des variables.
* SITES-15586 : GraphQL : problème lié au filtrage de requêtes persistantes avec des valeurs &quot;null&quot;.
* SITES-15622 : GraphQL : problème avec les requêtes persistantes avec les paramètres numériques et bool.
* SITES-15654 : GraphQL : problème avec les unions et propriétés du même nom.
* SITES-15267 : Lancements : la promotion ne sélectionne pas les pages de lancement modifiées avant la modification de la configuration du lancement.
* SITES-15406 : Lancements : impossible d’ajouter une page de lancement.
* SITES-15427 : Lancements : comportement incohérent de la portée &quot;Promouvoir la page active et les sous-pages&quot;.
* SITES-15429 : Lancements : création de pages supprimées lors de la promotion de lancements.
* SITES-15462 : Lancements : le processus de promotion automatique publie des pages hors du cadre de la promotion.
* SITES-15815 : Lancements : la suppression de la page du lancement entraîne la non-promotion de Launch.
* SITES-15223 : Éditeur de page : impossible de redimensionner les composants dans l’émulateur de taille de tablette.
* SITES-15463 : Modèles de page : les modèles ne peuvent pas être publiés.

### Problèmes connus {#known-issues-13665}

Aucun

### Technologies intégrées {#embedded-tech-13665}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.54-T20230817132355-3800a65 | [API Oak 1.54.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.54.0/index.html) |
| API SLING AEM | Version 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | Version 2.23.4 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
