---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 7d93af706d8b0556e9e26282d339794447eb0a41
workflow-type: tm+mt
source-wordcount: '1514'
ht-degree: 21%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 20133 {#20133}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 20133, rendue publique le mercredi 1 avril 2025. La version de maintenance précédente était la version 19823.

L’activation des fonctionnalités de la version 2025.4.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-20133}

* ASSETS-47850 : permet de restreindre l’ajout de configurations Scene7 si AEM CS est activé pour ES.
* CQ-4359547 : suppression complète de Guava du référentiel https://git.corp.adobe.com/target-sdk/tsdk-core.
* FORMS-17551 : ajout de la prise en charge du document d’enregistrement pour les intégrations de listes SharePoint.
* FORMS-18432 : implémentation d’une configuration de préremplissage côté client spécifique au formulaire (basée sur la regex) pour activer la fonctionnalité de préremplissage sélectif sans modifications au niveau OSGI.
* FORMS-18513 : prise en charge de la transformation de l’arbre de données implémentée dans le connecteur AEP pour améliorer les fonctionnalités de l’assistant et les fonctionnalités de gestion des données.
* FORMS-19068 : ajout de la prise en charge des actions d’envoi du connecteur AEP dans les API Forms Manager pour améliorer les fonctionnalités d’intégration des données de formulaire.
* GRANITE-57717 : mise à jour du bundle client dans AEM.
* SITES-10469 : AdapterFactory doit toujours renvoyer la même instance PageManager.
* SITES-25130 : version 2.28.0 des composants principaux.
* SITES-25433 : prend en charge le rendu de page complète lors de la comparaison d’anciennes versions.
* SITES-25923 : LinkInfoStorageImpl peut bloquer lorsqu’aucune URL n’est plus stockée.
* SITES-26208 : la suppression d’un fragment de contenu par le biais d’un workflow permet désormais d’actualiser les ressources de référencement en supprimant le fragment nouvellement supprimé.
* SITES-26500 : ajout de l’option permettant de déplacer des fragments de contenu via le workflow - `move-fragments`.
* SITES-26711 : déclencheur de déploiement - les liens ne sont pas mis à jour.
* SITES-27583 : fragments d’expérience perdant leur historique de version après avoir été déplacés.
* SITES-27618 : la recherche de références à un fragment dans les pages ne renvoie pas tous les résultats.
* SITES-27781 : validation au niveau du modèle implémentée pour les références de fragment de contenu, ce qui permet de valider les fragments référencés par rapport à leurs contraintes de modèle et à la balise requise.
* SITES-27784 : mettez à jour la génération des requêtes SQL pour utiliser la fonction PATH au lieu de `jcr:path`.
* SITES-28040 : Adobe Target ExperienceFragmentsReplicationListener endommagé.
* SITES-28051 : obtenez les autorisations de l’utilisateur actuel sur un fragment de contenu : GET /cf/fragments/{fragmentId}/permissions.
* SITES-28190 : configuration pour le test d’intégration de prévisualisation.
* SITES-28227 : lors de l’ajout de ressources en tant que références à un fragment, nous vérifions que la ressource existe.
* SITES-28248 : basculement des événements Sites en fonction de la configuration OSGI.
* SITES-28255 : le nom complet est manquant dans les 3 propriétés d’audit : créé, modifié, publié.
* SITES-28390 : PageImpl : Optimiser hasContent().
* SITES-28404 : la suppression de pages sur l’instance de création doit les dépublier à partir du service d’aperçu.
* SITES-28446 : ajout de 2 nouveaux champs qui n’étaient pas visibles dans la réponse : l’espace réservé dans NumberModelField et les modèles autorisés de LongTextModelField.
* SITES-28536 : créez `RENAME` point d’entrée pour les fragments de contenu.
* SITES-28537 : ajout de l’option permettant de renommer les fragments de contenu via le workflow - `rename-fragments`.
* SITES-28538 : les références doivent être republiées pour conserver un contenu valide sur les instances de création et de publication.
* SITES-28549 : créez des `/cf/domains` pour renvoyer l’ID de domaine en fonction du niveau AEM.
* SITES-29026 : ajout d’un paramètre facultatif qui spécifie les paramètres régionaux du fragment de contenu à l’aide d’un code de langue et de pays.
* SITES-29031 : amélioration de la logique des fragments PATCH-ing, offrant ainsi de meilleures performances.
* SITES-29169 : toutes les ressources publiées (qu’elles aient le statut PUBLIÉ ou MODIFIÉ) seront republiées si elles font référence à une ressource qui a été déplacée, renommée ou supprimée.
* SITES-29376 : activer/désactiver l’ajout de code pour valider la suppression de ressources publiées.
* SITES-29417 : mettez à jour /libs/cq/Page/proxy.jsp pour transférer la requête vers le nœud jcr:content au lieu d’inclure .
* SITES-2947 : créer/modifier la visualisation kibana pour comparer le râpage de publication.
* SITES-29733 : performances accrues de la recherche de modèles par balises de fragments de contenu.
* SITES-8316 : politiques de contenu : mettez en cache ContentPolicyManager.
* SITES-24906 : Edge Delivery avec éditeur universel : prise en charge des feuilles de calcul créées par l’auteur sans mappage (accès anticipé)
* SITES-24907 : Edge Delivery avec éditeur universel : prise en charge de la publication d’Assets sur plusieurs sites pour les cas d’utilisation de MSM (accès anticipé)
* SITES-27956 : Edge Delivery avec éditeur universel : amélioration du débit de publication (accès anticipé)
* SITES-27956 : Edge Delivery avec éditeur universel : amélioration de la gestion des erreurs pour la publication sur Edge Delivery Services (accès anticipé)

### Problèmes résolus {#fixed-issues-20133}

* CQ-4358378 : gestion des erreurs de licence dans l’exécution de traduction.
* CQ-4359263 : aucun message ne s’affiche dans la boîte de dialogue lorsque la tâche est terminée.
* CQ-4359386 : impossible d’ajouter le dictionnaire i18n au projet de traduction dans AEMaaCS.
* FORMS-18068 : problèmes de rendu de texte en gras dans le document d’enregistrement pour les groupes de boutons radio et de cases à cocher utilisant des champs de texte enrichi.
* FORMS-18189 : modification de la gestion des fonctions personnalisées pour empêcher la journalisation des erreurs pour les bibliothèques clientes vides et améliorer l’affichage des erreurs dans l’interface utilisateur.
* FORMS-18213 : fonctionnalité implémentée pour masquer/exclure les champs désactivés du document d’enregistrement (DE) afin d’améliorer la clarté du document et l’expérience utilisateur.
* FORMS-18271 : l’éditeur de thèmes Forms affiche des messages d’erreur non localisés, ce qui affecte l’expérience utilisateur dans la configuration des formulaires et la personnalisation des thèmes.
* FORMS-18304 : les documents PDF/A-1b qui réussissent la validation dans Acrobat et LiveCycle ES4 sont incorrectement marqués comme non conformes dans AEM 6.5 Forms en raison d’erreurs de couleur dépendantes de l’appareil.
* FORMS-18325 : ajout de la configuration cloud de Adobe Experience Platform (AEP) pour améliorer l’intégration et les fonctionnalités de traitement des données de formulaire.
* FORMS-18360 : amélioration de la gestion de la portée de la liste SharePoint pour les sites des équipes dans la gestion des documents Forms afin d’améliorer l’organisation des données et le contrôle d’accès.
* FORMS-18375 : les formulaires basés sur les composants de base sélectionnent incorrectement les configurations Recaptcha `conf/global` dossier lorsqu’aucun conteneur de configuration spécifique n’est sélectionné.
* FORMS-18426 : la fonctionnalité de recherche de liste SharePoint échoue lorsque les noms de liste contiennent des caractères spéciaux (par exemple, « - »), ce qui affecte l’intégration des formulaires aux listes SharePoint.
* FORMS-19028 : la fonctionnalité de préremplissage côté client interrompt la gestion des événements de formulaire, ce qui empêche le déclenchement correct des événements Validation de valeur et DOMContentLoaded au chargement du formulaire.
* FORMS-6950 : ajout des rôles et attributs ARIA requis aux composants d’aperçu de l’arborescence du navigateur du système de fichiers pour améliorer l’accessibilité du lecteur d’écran et se conformer à la norme WCAG 4.1.2 Nom, rôle, valeur (niveau A).
* FORMS-7016 : l’ordre de focus au clavier dans l’éditeur de formulaire ne suit pas la navigation logique.
* SITES-1960 : amélioration des performances de l’opération d’aperçu JSON de l’éditeur de fragment de contenu.
* SITES-24308 : une barre de défilement horizontale s’affiche lorsque le contenu est redimensionné à 400 %.
* SITES-24493 : l’élément interactif n’a pas le rôle requis.
* SITES-24669 : le séparateur de fenêtre du rail de références n’est pas accessible au clavier.
* SITES-26881 : bogue d’accessibilité AEMaaCS - rôle incorrect est fourni pour l’icône « Trois points » qui se trouve en regard du champ de saisie de commentaire.
* SITES-26956 : suivi sur SITES-24920 Impossible de déplacer la page dans l’environnement de production.
* SITES-27707 : la liste des ressources de l’outil de recherche de contenu échoue en raison de problèmes liés aux noms des ressources (régression de la version 6.5 SP22).
* SITES-27757 : Edge Delivery avec éditeur universel : réécrivez les icônes en fonction de la sémantique helix-html-pipeline.
* SITES-27780 : une balise &lt;br> inattendue apparaît dans l’éditeur de texte enrichi avec le DefaultPasteMode en texte brut sur le SP22.
* SITES-27958 : le vérificateur de liens renvoie des erreurs « Cette session est fermée ».
* SITES-28149 : ExperienceFragmentLinkRewriterProvider personnalisé non déclenché lors de l’exportation XF vers Target.
* SITES-28449 : bogue de l’interface utilisateur du widget de workflow - inclure les enfants qui n’affichent pas toutes les pages enfants dans AEM.
* SITES-28456 : notification manquante dans l’interface utilisateur en cas d’enregistrement d’une requête persistante incorrecte dans l’explorateur GraphiQL (Suivi - SITES-28313).
* SITES-28464 : mettez à jour la requête de fragment pour utiliser des dates formatées avec des millisecondes.
* SITES-28486 : la modification statique dans le nouvel éditeur de fragment de contenu ne redirige pas vers l’ancien éditeur.
* SITES-28570 : les métadonnées de ressources manquantes sont correctement gérées par le GraphQL du fragment de contenu.
* SITES-28580 : l’outil de recherche de ressources d’image classique est rompu après la mise à niveau vers le SP22.
* SITES-28600 : lancements - Contenu dupliqué.
* SITES-28668 : impossible de promouvoir Launch avec LaunchPromotionParameters.
* SITES-28820 : préfixe Launch ajouté deux fois dans la nouvelle variation créée sur Rebase.
* SITES-28877 : le service d’URL UE renvoie une exception lorsque le point d’entrée de l’externaliseur local n’est pas défini.
* SITES-28956 : l’opération de suppression de balise affiche un avertissement, si la balise est référencée par des fragments de contenu.
* SITES-29208 : les références et les variations sont correctement renvoyées dans les cas où un champ de référence contient un chemin d’accès non valide.
* SITES-29363 : le bouton Réinitialiser la Live Copy ne fonctionne pas pour la hiérarchie de contenu de Live Copy imbriquée.
* SITES-29369 : problème d’événement Assets dans l’AIO | Déclenchement incorrect des événements de page publiés/dépubliés.
* SITES-29972 : les actions Supprimer et Renommer génèrent parfois de faux commentaires sur le workflow.

### Problèmes connus {#known-issues-20133}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-20133}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées ](/help/release-notes/deprecated-removed-features.md).

#### Modifications concernant la synchronisation des groupes d’utilisateurs et d’utilisatrices et des profils de produits {#changes-user-groups}

Lors de l’utilisation d’Adobe Admin Console pour la gestion des autorisations, les groupes suivants NE DOIVENT PAS être utilisés car ils ne seront plus synchronisés avec AEM :
* Groupes AEM se terminant par _GROUP_NAME_SUFFIX.
* Profils de produit provenant d’autres environnements, programmes ou produits.

Pour plus d’informations, consultez la section [Modifications dans la synchronisation des groupes d’utilisateurs et d’utilisatrices et des profils de produit](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/security/changes-in-user-group-and-product-profile-synchronization).

#### Abandon de l’éditeur de SPA {#deprecate-spa-editor}

[L’éditeur de SPA](/help/implementing/developing/hybrid/introduction.md) a été abandonné pour les nouveaux projets à partir de la version 2025.4.0. L’éditeur de SPA reste pris en charge pour les projets existants, mais ne doit pas être utilisé pour de nouveaux projets.

Les éditeurs privilégiés pour la gestion du contenu découplé dans AEM sont les suivants :

* [Éditeur universel](/help/edge/wysiwyg-authoring/authoring.md) pour la modification visuelle.
* [Éditeur de fragments de contenu](/help/assets/content-fragments/content-fragments-managing.md) pour la modification basée sur les formulaires.

Vous trouverez plus d’informations sur cette obsolescence dans le document [ Obsolescence de l’éditeur de SPA ](/help/implementing/developing/hybrid/spa-editor-deprecation.md).

### Correctifs de sécurité {#security-20133}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 34 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-20133}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.76.0 | [API Oak 1.76.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.76.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.26-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.28.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
