---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: b4df0abb43d69f629d2c643c408cb77af697b942
workflow-type: tm+mt
source-wordcount: '1090'
ht-degree: 19%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 23862 {#23862}

>[!CAUTION]
>
> La version 23862 a été rendue privée. Une nouvelle version de maintenance sera bientôt fournie.

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 23862, publiée le mercredi 23 décembre 2025. La version de maintenance précédente était la version 23482.

L’activation des fonctionnalités de la version 2026.1.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-23862}

* CQ-4361812 : ajout de la prise en charge du paramètre facultatif folderPath dans l’api REST. Description : un nouveau projet de traduction est créé par l’API et sera placé dans le chemin d’accès spécifié par le paramètre `folderPath` facultatif. Sinon, il est défini par défaut sur le chemin d’accès racine du projet `/content/projects`.
* FORMS-21960 : ajout de la prise en charge de l’édition de la zone de travail en local pour les communications interactives, similaire à forms-spa.
* FORMS-22001 : ajout de conseils pour réduire le volume élevé de requêtes `/etc.clientlibs/toggles.json` dans AEM Forms as a Cloud Service.
* FORMS-22496 : expose le ResponseBody brut dans le service d’appel.
* FORMS-22495 : ajoutez la propriété d’espace réservé dans la règle SetProperty.
* FORMS-21925 : UBS Footnotes Formatting : permet d’afficher toutes les notes de bas de page dans le formulaire lors du chargement du formulaire.
* FORMS-20536 : expose une option de réponse complète dans eventPayload dans l’éditeur de règles sans mappage.
* SITES-37199 : la fonction d’annotation déclenche la traversée du référentiel via un appel de `authorizables.json` non validé, ce qui entraîne une dégradation des performances.
* SITES-37118 : prise en charge de Commerce Optimizer dans le cockpit de produits.
* SITES-38029 : ajoutez des journaux pour le suivi des événements push MSM lors de la modification.
* SITES-37050 : prise en charge de la « dépublication forcée », ce qui permet de dépublier des fragments de contenu référencés par d’autres ressources publiées.
* SITES-37142 : ajout de la possibilité d’archiver/extraire un fragment de contenu via le PATCH de fragment de contenu.
* SITES-37613 : dans le point d’entrée des autorisations de l’API CF, renvoyez la case à cocher Archiver si l’utilisateur peut archiver un fragment de contenu ou Extraire s’il peut extraire un fragment de contenu.
* SITES-37835 : lorsque vous tentez de créer plusieurs fragments de contenu avec le même titre, mais sans nom fourni, générez automatiquement un nouveau nom au lieu d’échouer en raison d’un conflit.
* SITES-36823 : Edge Delivery avec éditeur universel : permet de supprimer la nécessité de mappages inverses pour les index.
* SITES-34751 : Edge Delivery avec éditeur universel : échec pour les types de fichiers et chemins d’accès non pris en charge lors de la publication (accès anticipé).
* SITES-37888 : Edge Delivery avec éditeur universel : utilisez le suffixe Alt comme synonyme de Texte pour les liens.
* SITES-19850 : Edge Delivery avec éditeur universel : ajoutez la prise en charge de plusieurs feuilles de calcul dans les feuilles de calcul.
* SITES-32490 : Edge Delivery avec éditeur universel : ajoutez la prise en charge du composant data-aue et du libellé data-aue défini par l’utilisateur aux blocs et au contenu par défaut.
* SITES-37794 : Edge Delivery avec éditeur universel : assistant de création de page simplifiée.
* SITES-36963 : migrez le point d’entrée Audience/Segment vers l’API Target v3 pour la prise en charge de Workspace.

### Problèmes résolus {#fixed-issues-23862}

* CQ-4361831 : correction d’un problème en raison duquel genai_dropdown_span n’était pas défini.
* CQ-4360895 : correction d’un nombre inexact de statuts de tâche de traduction dans le projet lors de mises à jour simultanées.
* CQ-4361599 : Correction d’un saut de fragments de contenu des tâches de traduction après la mise à niveau de 2025.7.
* CQ-4360747 : correction des tâches de traduction répétables qui créent des payloads vides et se déclenchent trop souvent (NullPointerException dans ScheduleRepeatTranslationProject).
* CQ-4359994 : correction d’une incohérence du type de champ destinationLanguage pour les projets unilingues et multilingues.
* SITES-38153 : correction du fournisseur de référence de publication cf pour les références basées sur l’uuid.
* SITES-37594 : améliorations des performances de la fonctionnalité de modèle par balises.
* SITES-37337 : FragmentCreateProcessor : fournissez des détails d’erreur supplémentaires dans les journaux.
* SITES-33666 : message d’erreur « Impossible d’imprimer le fichier JSON du fragment » non localisé dans l’éditeur de fragment de contenu.
* SITES-33675 : chaîne codée en dur « undefined » dans l’éditeur de fragments de contenu > Contenu associé.
* SITES-30715 : chaîne « General » non localisée dans l’éditeur de fragment de contenu.
* SITES-28592 : chaînes non localisées dans l’éditeur de modèles de fragments de contenu > Boîte de dialogue « Le modèle est verrouillé ».
* SITES-977 : les chaînes « Balises » et « collections » ne sont pas localisées sur la page de modification du fragment de contenu.
* SITES-29699 : types de ressources non localisés autorisés dans l’éditeur de fragment de contenu.
* SITES-25240 : les champs Call to action de la fenêtre modale du teaser n’ont pas de libellé visible.
* SITES-24869 : info-bulle tronquée dans l’éditeur de modèles > Séparateur > Politique.
* SITES-19313 : une erreur est délocalisée lorsque vous faites glisser et déposez un composant vers le modèle supprimé dans l’éditeur de modèles.
* SITES-18103 : chaînes non localisées dans l’éditeur de page > Workflow.
* SITES-17501 : chaînes non localisées dans l’éditeur de modèles > éditeur de politiques de composants.
* SITES-15091 : les chaînes sont délocalisées sur les propriétés du composant de texte du fragment d’expérience.
* SITES-8113 : la chaîne « Assets » n’est pas localisée dans la boîte de dialogue « Sélectionner une image » pour « Modèles » dans le menu Outils.
* SITES-37587 : la création d’une Live Copy échoue toujours dans PROD avec NPE dans RolloutManagerImpl.
* SITES-37335 : propriétés de page de la Live Copy affichant une erreur dans la console en rapport avec les balises cq.
* SITES-36972 : bouton « Déployer » manquant dans la barre d’outils modifiable.
* SITES-36570 : la création de Live Copies échoue une fois que le bouton Créer une Live Copy en bloc est activé.
* SITES-36158 : le déploiement échoue avec l’échec de la tâche en raison d’une exception.
* SITES-35655 : le nouvel éditeur CF affiche l’héritage actif après sa rupture.
* SITES-31425 : un message d’erreur non localisé `Error: {} field is required`’affiche dans le workflow Démarrer dans les sites.
* SITES-19802 : les info-bulles ne sont pas localisées dans Site des composants principaux > Table des matières.
* SITES-36543 : correction d’un problème en raison duquel l’administrateur pouvait modifier les fragments de contenu extraits.
* SITES-36967 : correction des exceptions NullPointerExceptions qui se produisent lors de la tentative de génération de données de miniature pour des fragments de contenu rompus.
* SITES-37791 : correction d’un problème en raison duquel l’appel de FindAndReplace pour les chaînes contenant des `$` échouait.
* SITES-37018 : fenêtre contextuelle d’erreur vide lors de la copie d’une page avec un chemin de modèle non autorisé.
* SITES-36243 : Edge Delivery avec éditeur universel : correctif des 404 lors de la publication des `sling:OrderedFolder`.
* SITES-37684 : Edge Delivery avec éditeur universel : correction de la dégradation des performances dans les environnements comportant de nombreux sites.
* SITES-37840 : Edge Delivery avec éditeur universel : correction des échecs de publication en raison de jetons d’accès obsolètes pour Edge Delivery.
* SITES-37933 : Edge Delivery avec éditeur universel : correction des échecs de (annulation) publication de ressources supprimées dans les lancements.
* SITES-37870 : Edge Delivery avec éditeur universel : correction du rendu endommagé des métadonnées de page personnalisées avec la prise en charge multichamp activée.
* SITES-37349 : Edge Delivery avec éditeur universel : effectue le rendu de plusieurs champs avec des entrées uniques en tant que liste avec un seul élément de liste.
* SITES-36148 : Edge Delivery avec éditeur universel : correction de data-aue-label pour les champs multiples composites.

### Problèmes connus {#known-issues-23862}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-23862}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-23862}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 23 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-23862}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1,88,0 | [API Oak 1.88.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.88.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Serveur HTTP Apache | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| Composants principaux d’AEM | 2.30.2 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (par défaut) | [Versions de Node.js prises en charge](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
