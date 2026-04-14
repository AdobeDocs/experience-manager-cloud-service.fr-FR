---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: d2c26a122bd2a0a970af7578932d88e6f93487d5
workflow-type: tm+mt
source-wordcount: '1772'
ht-degree: 13%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 25194 {#25194}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 25194, rendue publique le jeudi 1 avril 2026. La version de maintenance précédente était la version 24678.

L’activation des fonctionnalités de la version 2026.4.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

>[!NOTE]
>
>La version 24893 a été rendue privée.

### Améliorations {#enhancements-25194}

* ASSETS-65127 : métadonnées personnalisées d’événement : meilleure gestion des noms de métadonnées.
* ASSETS-63313 : création automatique de liens associés pour les ressources exportées et les parents en fonction des manifestes C2PA.
* ASSETS-10995 : limitation du nombre de ressources dans un fichier compressé de téléchargement.
* FORMS-24388 : ajout d’un environnement de développement local pour l’éditeur de communication interactive (IC) qui permet aux développeurs et aux développeuses de créer et de tester des configurations sans recourir à des serveurs partagés. Cette amélioration permet aux entreprises clientes d’itérer plus rapidement, de réduire les dépendances de l’environnement et d’améliorer la productivité globale du développement.
* FORMS-24014 : amélioration de l’éditeur de règles pour les composants de pièce jointe afin de prendre en charge les conditions de combinaison à l’aide de la logique « AND », par exemple en autorisant des règles telles que « Si la pièce jointe est modifiée et que le panneau est valide, procédez comme suit ». Auparavant, il n’était pas possible d’utiliser des conditions supplémentaires avec des pièces jointes. Cette mise à jour permet d’utiliser des définitions de règle plus complexes pour prendre en charge des workflows avancés.
* FORMS-23571 : amélioration de la vue de grammaire simplifiée existante pour les règles d’événement de déclenchement en ajoutant la prise en charge des événements prêts à l’emploi en plus des événements personnalisés. Auparavant, les utilisateurs ne pouvaient utiliser que la grammaire simplifiée pour les événements personnalisés et devaient basculer entre les règles « QUAND » et « ÉVÉNEMENT DÉCLENCHEUR ACTIVÉ » pour configurer les événements prêts à l’emploi et personnalisés séparément. Grâce à cette mise à jour, les événements prêts à l’emploi et personnalisés peuvent être utilisés dans la même grammaire simplifiée, ce qui simplifie la configuration des règles et réduit la nécessité de changer de contexte.
* FORMS-24462 : ajout de la prise en charge du composant Signature tactile dans les composants React Vanilla pour le Forms adaptatif découplé (AF). Cette amélioration permet aux utilisateurs de capturer des signatures manuscrites directement dans des formulaires basés sur React, ce qui prend en charge les workflows de signature numérique et les délais de mise en production planifiés pour les clients d’entreprise.
* FORMS-24343 : ajout d’une gestion optimisée des `custom:setProperty` dans le modèle de formulaire JavaScript Object Notation (JSON), ce qui permet un traitement plus rapide des mises à jour de propriétés dynamiques. Cette amélioration améliore les performances des Forms adaptatives (AF) complexes qui reposent sur des modifications d’exécution fréquentes, ce qui se traduit par des interactions utilisateur plus fluides et des temps de chargement réduits.
* FORMS-24358 : ajout de la prise en charge de l’utilisation de la propriété `items` dans la structure de modèle JavaScript Object Notation (JSON) au lieu de `:items` et `:itemsOrder`. Cette amélioration permet aux développeurs de travailler avec un modèle de données plus propre et plus intuitif, qui s’aligne mieux sur les conventions JSON courantes et simplifie l’intégration aux systèmes externes.
* FORMS-24087 : ajout de la prise en charge de la définition de règles et d’événements directement sur les conteneurs de fragments dans Adaptive Forms (AF). Cette amélioration permet aux auteurs d’appliquer une logique conditionnelle et des interactions au niveau du conteneur, ce qui améliore la réutilisation et réduit la nécessité de dupliquer les règles entre les champs de fragment individuels.
* FORMS-24440 : ajout d’une nouvelle action « Supprimer le champ » dans la liste déroulante THEN de l’éditeur de règles pour la communication interactive qui permet aux utilisateurs et utilisatrices de supprimer complètement un composant sélectionné du formulaire lorsqu’une condition de règle est remplie. Cette amélioration prend en charge les workflows qui nécessitent la restructuration dynamique des formulaires au lieu de masquer uniquement les champs, tout en déclenchant le script `forms_ready` approprié pour un comportement cohérent.
* FORMS-23898 : ajout de la prise en charge de la définition de variables à l’aide de la notation `@` dans l’éditeur de communication interactive (IC), ce qui permet aux utilisateurs de configurer les tableaux dynamiques de manière plus intuitive. Cette amélioration simplifie la configuration du contenu de tableau piloté par les variables et améliore la clarté de la gestion des données dynamiques dans l’expérience de création.
* FORMS-23702 : ajout d’une authentification par certificat pour les connexions à la liste SharePoint (SPList) qui permet un accès plus sécurisé et piloté par certificat aux données SharePoint. Cette amélioration aide les entreprises clientes à répondre à des exigences de sécurité et de conformité plus strictes tout en réduisant la dépendance à l’authentification par mot de passe.
* FORMS-23800 : ajout de la prise en charge du remplacement des clés secrètes reCAPTCHA dans les configurations sling, ce qui permet aux clients d’entreprise de s’aligner sur leurs propres exigences de sécurité et de conformité. Cette amélioration permet la gestion des clés secrètes spécifiques à un environnement afin que les administrateurs puissent intégrer reCAPTCHA en toute sécurité sans modifier le code.

### Problèmes résolus {#fixed-issues-25194}

* ASSETS-62882 : vue Administration : l’info-bulle se rompt lorsque plusieurs noms de fichier non valides sont chargés.
* ASSETS-63642 : le lien de partage ne parvient pas à effectuer le rendu de la ressource sur certains environnements de développement (SLA3).
* ASSETS-59267 : NPE lors du chargement des métadonnées d’application pour la payload de diffusion.
* ASSETS-59227 : exportation des métadonnées : les propriétés non sélectionnées ne sont plus incluses en raison d’une correspondance d’expression régulière.
* ASSETS-65187 : aperçu au format CSV dans le cloud lorsque les données de colonne contiennent des virgules d’échappement.
* ASSETS-63441 : assurez-vous que tous les utilisateurs sont autorisés à lire la configuration Assets Omnisearch.
* SITES-40095 : éditeur de métadonnées : références de fragment de contenu local au-delà de 10 entrées.
* FORMS-24811 : les utilisateurs ont rencontré des problèmes de gestion des règles de logique de formulaire. Lorsqu’ils ont essayé de modifier des règles qui avaient été créées précédemment, l’éditeur de règles n’a pas autorisé les modifications, obligeant les utilisateurs et utilisatrices à recréer des règles à partir de zéro et ralentissant la maintenance des formulaires.
* FORMS-24720 : des problèmes sont survenus lors de la configuration de variables nouvellement créées dans le Forms adaptatif (AF). Lorsqu’elles ont ajouté des règles à des variables liées aux données ou non liées, les règles ne se sont pas enregistrées comme prévu, ce qui a forcé les utilisateurs à recréer leur logique et ralenti les workflows de création de formulaires.
* FORMS-24195 : les utilisateurs ont présenté un comportement incohérent lors de la réinitialisation des champs déroulants dans Adaptive Forms (AF). Lorsqu’une liste déroulante disposait d’un espace réservé configuré et que le formulaire ou le composant était réinitialisé, le champ était vide au lieu de revenir à la valeur de l’espace réservé, ce qui entraînait une confusion quant aux sélections requises.
* FORMS-24718 : les utilisateurs ont rencontré des problèmes de navigation dans l’éditeur de communication interactive (IC) lors de la sélection du bouton Accueil . Au lieu de revenir à l’interface principale de Adobe Experience Manager (AEM), le bouton n’a pas redirigé comme prévu, perturbant le workflow des utilisateurs et utilisatrices lors du passage de la modification des IC à l’écran d’accueil d’AEM.
* FORMS-24810 : les utilisateurs ont rencontré des échecs intermittents lors du chargement de l’interface utilisateur adaptative (AUI) pour les formulaires lors de la première tentative. Dans certaines sessions, le rendu de la page initiale n’était pas correct, ce qui forçait les utilisateurs et utilisatrices à actualiser ou à réessayer avant de pouvoir commencer à remplir leurs formulaires.
* FORMS-24520 : les utilisateurs n’ont pas de numéro de page dans l’aperçu avant impression de l’interface utilisateur de l’agent pour les formulaires utilisant l’interface utilisateur adaptative (AUI). Lorsque les agents ouvraient l’aperçu avant impression, le champ du numéro de page apparaissait parfois vide, ce qui rendait plus difficile la référence à des pages spécifiques lors de la révision ou du partage de copies imprimées.
* FORMS-24532 : les utilisateurs ont rencontré des échecs lors de l’utilisation du préremplissage du modèle de données de formulaire (FDM) avec les configurations de liste de `/teams` SharePoint. Les organisations gouvernementales qui utilisaient ces listes ont vu les formulaires se charger sans données préremplies attendues, ce qui a interrompu les workflows de collecte de données et augmenté les efforts de saisie manuelle.
* FORMS-24516 : les utilisateurs ne disposaient pas des données de signature tactile dans le document d’enregistrement (DE) après une mise à niveau de SDK dans AEM Forms as a Cloud Service. Lorsque les formulaires étaient signés à l’aide de l’option de saisie tactile, le document d’enregistrement généré n’affichait pas la signature capturée, ce qui entraînait une confusion et des enregistrements incomplets pour les clients Grands comptes.
* FORMS-18631 : les utilisateurs ont rencontré des problèmes d’accessibilité liés à la mise en page de grille sur le bureau, la tablette Responsive Web Design (RWD) et les vues mobiles RWD. Lors de l’utilisation de Chrome sur Windows 11 avec le lecteur d’écran NVDA (NonVisual Desktop Access), les grilles ne comportaient pas les rôles et attributs appropriés, ce qui rendait difficile l’interprétation et la navigation correctes du contenu pour les technologies d’assistance.
* FORMS-24798 : les utilisateurs ont présenté un comportement incohérent lors de l’utilisation de conditions de `else` dans les règles de Forms adaptatif (AF) au sein de l’interface utilisateur (IU) d’AEM Forms. Lorsque la condition de la règle principale n’était pas remplie, les actions de `else` associées ne s’exécutaient pas, ce qui entraînait un comportement différent de la logique de formulaire et de la visibilité des champs par rapport à ce que les auteurs et autrices avaient configuré.
* FORMS-24334 : les utilisateurs ont rencontré des échecs de préremplissage et des problèmes de fusion JavaScript Object Notation (JSON) lors de l’utilisation d’un formulaire adaptatif (AF) incorporé dans Adobe Experience Manager (AEM) Forms as a Cloud Service. Lors du chargement des formulaires migrés, les données préremplies attendues n’apparaissaient pas et le contenu JSON fusionné était incomplet ou incorrect. Cela a bloqué la migration d’AEM 6.5 on-premise vers AEM Forms as a Cloud Service pour les environnements affectés.
* FORMS-24441 : les utilisateurs ont rencontré des problèmes lors de la configuration du modèle de document d’enregistrement (DE) dans Adobe Experience Manager (AEM) Forms as a Cloud Service. Lorsqu’ils ont enregistré un modèle de document d’enregistrement personnalisé dans l’environnement de développement rapide, le modèle est revenu à la version par défaut, ce qui les a empêchés de conserver la mise en page et les paramètres prévus.
* FORMS-24393 : les utilisateurs ont rencontré une confusion lorsque les anciens modèles ont continué à apparaître comme « Sans titre » au lieu d’afficher des noms significatifs. Il était donc difficile de distinguer et de réutiliser les modèles existants pendant le travail de création quotidien.
* FORMS-24163 : les utilisateurs ont rencontré des problèmes lors de la prévisualisation des formulaires version 2 contenant des fragments. En mode Aperçu, le contenu du formulaire ne s’est pas rendu comme prévu, ce qui a empêché les utilisateurs de valider la disposition et le comportement avant la publication.
* FORMS-24328 : certains utilisateurs ont rencontré des problèmes lors de l’envoi de formulaires lors de l’utilisation de reCAPTCHA v2 invisible avec l’option « Valider le CAPTCHA sur une action utilisateur ». Les entreprises clientes ont constaté que les formulaires des environnements affectés n’étaient pas envoyés comme prévu, ce qui a perturbé les workflows de contact et de demande de proposition.

#### AEM Guides {#guides-25194}

* GUIDES-38412 : lors de la modification d’un fichier de `(*.sch)` Schematron et de l’utilisation de la fonction de recherche et de remplacement, le panneau de recherche et de remplacement s’affiche partiellement hors écran en bas, empêchant l’accès à ses champs et contrôles de saisie.
* GUIDES-37806 : lorsque la même rubrique est réutilisée sur plusieurs mappages avec des paramètres prédéfinis conditionnels différents, la publication du dernier mappage sur Salesforce remplace le contenu de la rubrique, ce qui entraîne l&#39;affichage de données incorrectes aux utilisateurs de mappages précédemment publiés.
* GUIDES-39394 : lorsqu’une image initialement gérée en tant que ressource spécifique à la langue avec une version spécifique (par exemple, sous `/en/`) est déplacée vers un dossier global avec une version mise à jour et que l’exportation de la ligne de base est effectuée, la nouvelle ligne de base continue à référencer des versions obsolètes spécifiques à la langue de cette image, ce qui entraîne l’échec de l’exportation de la ligne de base.
* GUIDES-39054 : lors de la création d’une ligne de base dynamique, l’éditeur ne répond parfois plus en raison de plusieurs requêtes d’API simultanées, ce qui interrompt toutes les autres opérations.
* GUIDES-37781 : lors de l’affectation d’un utilisateur à une tâche de révision, la liste déroulante répertorie tous les utilisateurs au lieu de seulement ceux associés aux projets sélectionnés, ce qui entraîne la non-validité des options utilisateur.
* GUIDES-39385 : Lors de l’ouverture d’un rapport pour une carte, le chargement du panneau Filtres est retardé.

Pour plus d’informations sur les fonctionnalités nouvelles et améliorées, ainsi que sur les problèmes résolus dans la version, consultez la [Feuille de route de publication d’Experience Manager Guides](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Problèmes connus {#known-issues-25194}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-25194}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-25194}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 9 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-25194}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.90.0 | [API Oak 1.90.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.90.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Serveur HTTP Apache | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| Composants principaux d’AEM | 2.30.4 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (par défaut) | [Versions de Node.js prises en charge](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
