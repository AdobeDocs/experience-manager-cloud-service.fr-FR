---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: c1e175128ab6e4b483e3940d9bd86a06540ef40f
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 27%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 24464 {#release-24464}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 24464, rendue publique le jeudi 18 février 2026. La version de maintenance précédente était la version 24288.

L’activation des fonctionnalités de la version 2026.2.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-24464}

* AEMARCH-264 : ajoutez la prise en charge de la validation des requêtes conditionnelles basées sur RequestEntity.
* AEMARCH-269 : exposer les API de validation JavaEE pour les implémentations OpenAPI.
* AEMARCH-276 : fournir la prise en charge d’i18n via RequestEntity.
* ASSETS-10995 : définir une limite de nombre de ressources dans le fichier compressé de téléchargement.
* ASSETS-50788 : mettez à jour l’API Search pour utiliser l’API GET des métadonnées de ressources.
* ASSETS-50946 : mappage du corps de la requête à l’aide de l’API Metadata GET aux métadonnées JCR.
* ASSETS-55866 : évitez d’envoyer une nouvelle demande pour la même ressource tant que le traitement précédent n’est pas terminé.
* ASSETS-60300 : fournit une API pour récupérer le contexte et le résultat asynchrones de la tâche.
* ASSETS-60574 : ajoutez la prise en charge de la dernière version du lot d’API Sling.
* ASSETS-61049 : poursuivre le développement du bundle du gestionnaire de métadonnées.
* ASSETS-61692 : effectuer une recherche sémantique par défaut dans l’API Search Open.
* ASSETS-61696 : itinéraire BAM et wrapper MFE dans la vue des ressources.
* ASSETS-61854 : envoi de la solution GenStudio dans le message d’activation/désactivation.
* ASSETS-61973 : création d’une API dans AEM pour gérer les invites.
* ASSETS-62182 : gestionnaire d’événements Asset Compute pour le rendu c2pa-manifest.
* ASSETS-62311 : problèmes de régression de la recherche.
* ASSETS-62413 : ajoute la prise en charge du champ customModifier dans chaque calque de JSON.
* ASSETS-62432 : API de suppression du dossier de fusion PR.
* ASSETS-62540 : amélioration de la version optimisée pour les écrans tactiles de l’interface utilisateur dans quickstart.
* ASSETS-62622 : gère le mode de recherche dans MatchQuery.
* ASSETS-62671 : correction de l’opérateur MatchQuery startsWith.
* ASSETS-62780 : bouton (bascule) Ajouter une fonctionnalité pour l’API de dossier.
* ASSETS-62988 : masque le rendu du manifeste c2pa pour l’affichage dans l’onglet Rendus.
* ASSETS-63336 : la synchronisation des modèles d’AEM vers DM ne doit se produire que pour les métadonnées d’espace de noms de gestion des ressources numériques.
* ASSETS-63375 : basculement des fonctionnalités derrière les OpenAPI expérimentales de chargement de ressources.
* ASSETS-63453 : assurez-vous que tous les utilisateurs peuvent lire la configuration Omnisearch.
* GRANITE-63744 : permet de connecter des tâches asynchrones aux tâches Sling.
* GRANITE-64567 : désactive automatiquement la recherche sémantique pour les recherches de SKU.
* GUIDES-41187 : ajoutez des en-têtes pour l’utilisation des guides.
* SITES-30452 : API de contenu avec ASO - suggestions de titre et de description.
* SITES-33116 : correction de la validation du chemin d’accès.
* SITES-34234 : éditeur de page : conserve l’état de l’arborescence de contenu.

### Problèmes résolus {#fixed-issues-24464}

* ASSETS-43198 : les e-mails de notification d’expiration de ressource ne respectent pas la préférence de langue de l’utilisateur.
* ASSETS-51840 : améliorations du traitement des ressources.
* ASSETS-52061 : impossible de revenir en arrière après avoir sélectionné la recherche enregistrée.
* ASSETS-53155 : améliorations du contenu des ressources.
* ASSETS-53745 : le flux de téléchargement Dynamic Media nécessite de désélectionner la ressource d’origine avant de choisir le préréglage web.
* ASSETS-54260 : correctifs de contenu de ressource.
* ASSETS-54787 : améliorations du contenu des ressources.
* ASSETS-57391 : mises à jour du contenu des ressources.
* ASSETS-59213 : cq-dynamicmedia-core dépend de la bibliothèque commons-lang obsolète.
* ASSETS-59214 : cq-scene7-imaging dépend de la bibliothèque commons-lang obsolète.
* ASSETS-59546 : cq-remotedam-client-core dépend de la bibliothèque commons-lang obsolète.
* ASSETS-59703 : cq-dam-core dépend de la bibliothèque commons-lang obsolète.
* ASSETS-59705 : cq-dam-handler dépend de la bibliothèque commons-lang obsolète.
* ASSETS-59707 : cq-dam-indesign dépend de la bibliothèque commons-lang obsolète.
* ASSETS-59709 : cq-scene7-core dépend de la bibliothèque commons-lang obsolète.
* ASSETS-59929 : le fichier CSV de l’exportation des métadonnées s’interrompt lorsque le champ comporte un caractère de nouvelle ligne.
* ASSETS-60241 : la tâche de déplacement asynchrone échoue lors du changement de nom du dossier.
* ASSETS-61134 : suppression des balises compareVersion des fichiers pom.
* ASSETS-61309 : le déplacement/la copie de fragment de contenu ne met plus à jour les références internes.
* ASSETS-61730 : la redirection vers Direct Binary Access doit respecter l’encodage des ressources.
* ASSETS-62358 : le fichier CSV de rapport Assets affiche des valeurs corrompues dans le chemin du contenu.
* ASSETS-62610 : bouton de licence Adobe Stock désactivé dans l’interface utilisateur Assets.
* ASSETS-62613 : NPE en `downloadasset`/`saveas`.
* ASSETS-62656 : indicateur Recherche optimisée par l&#39;IA Omnisearch incorrectement affiché pour les recherches non Assets.
* GRANITE-55387 : la correction d’un mot entre guillemets supprime le mot entier.
* GRANITE-61240 : RCE via le XSS stocké dans lazycontainer.js.
* GRANITE-64101 : les index OOTB convertis en ES sont rétablis dans Lucene au redémarrage.
* SITES-24530 : la cible tactile des boutons de fermeture/suppression dans la fenêtre modale de recherche n’est pas suffisamment grande.
* SITES-31425 : message d’erreur non localisé dans le workflow de démarrage.

### Problèmes connus {#known-issues-24464}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-24464}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-24464}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 14 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-24464}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.90.0 | [API Oak 1.90.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.90.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Serveur HTTP Apache | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| Composants principaux d’AEM | 2.30.4 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (par défaut) | [Versions de Node.js prises en charge](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |

