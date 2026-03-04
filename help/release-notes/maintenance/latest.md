---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 4b05f571904384521b79dbaf0fa5f4a3a75fef2b
workflow-type: tm+mt
source-wordcount: '1561'
ht-degree: 13%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 24678 {#release-24678}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 24678, publiée le jeudi 4 mars 2026. La version de maintenance précédente était la version 24464.

L’activation des fonctionnalités de la version 2026.3.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-24678}

* FORMS-18927 : ajout de la prise en charge des types MIME personnalisés et des extensions de fichier dans le composant Pièce jointe d’AEM Forms, ce qui permet aux utilisateurs de joindre une plus grande variété de types de documents.
* FORMS-18211, FORMS-22936 : les utilisateurs et utilisatrices ont rencontré un problème d’accessibilité en raison duquel les cases à cocher n’étaient pas correctement regroupées au sein d’un élément `<fieldset>`, le libellé du groupe n’étant pas imbriqué dans un `<legend>` en tant que premier enfant. Cela affectait les utilisateurs présentant un handicap qui dépendent des lecteurs d’écran pour la navigation. Le Forms adaptatif basé sur les composants principaux a désormais introduit la prise en charge des champs et des légendes pour fournir une meilleure prise en charge de l’accessibilité.
Ajout de l’option Jeu de champs au panneau, qui permet aux utilisateurs et utilisatrices d’organiser et de regrouper plus efficacement les champs associés dans leurs formulaires.
* FORMS-23880 : ajout de la prise en charge de l’éditeur de thèmes dans les composants principaux. Cette amélioration permet aux utilisateurs et utilisatrices de personnaliser et gérer les thèmes plus efficacement dans les composants principaux, améliorant ainsi la flexibilité de leur conception et leur workflow.
* FORMS-21772 : ajout de la prise en charge des versions à l’interface utilisateur de gestion de Forms. Cette amélioration permet aux utilisateurs de créer et de récupérer des versions pour les Forms adaptatifs, les fragments de formulaire, les thèmes et les Assets binaires basés sur les composants principaux et les composants de base, ce qui améliore la gestion des ressources et le contrôle des versions.
* FORMS-23094 : ajout d’une analyse côté client pour le Forms adaptatif basé sur les composants de base, ce qui permet aux clients d’entreprise de migrer leurs formulaires vers le cloud. Cette amélioration prend en charge les fonctionnalités EcmaScript dans les règles de l’éditeur de code, qui n’étaient auparavant pas prises en charge, ce qui facilite le processus de migration.
* FORMS-23853 : ajout de la prise en charge du remplacement de reCAPTCHA dans le composant sling. Cette amélioration permet aux utilisateurs de personnaliser les paramètres reCAPTCHA, améliorant ainsi la flexibilité et la sécurité pour les clients d’entreprise.
* SITES-34936 : Edge Delivery avec éditeur universel : ajoutez le filtrage des fragments de contenu par modèle pour la publication.
* SITES-36203 : Edge Delivery avec éditeur universel : activez le bouton (bascule) Ajouter du code pour activer la prise en charge multichamp et multichamp composite.
* SITES-37037 : Edge Delivery avec éditeur universel : améliorez l’importation des feuilles de calcul pour détecter automatiquement le délimiteur.
* SITES-37804 : Edge Delivery avec éditeur universel : ajout de la prise en charge de la création de groupes d’utilisateurs fermés (accès anticipé).
* SITES-38990 : Edge Delivery avec éditeur universel : ajoutez la prise en charge des exclusions aux mappages de chemin d’accès.
* SITES-39171 : Edge Delivery avec éditeur universel : ajoutez la prise en charge des `cq:tags` dans les blocs et les éléments de bloc.
* SITES-40042 : Edge Delivery avec éditeur universel : faites du service de configuration la valeur par défaut pour les nouveaux sites.
* SITES-37649 : GraphQL : prend en charge le filtrage de champ de texte multiligne au niveau JCR.
* SITES-37843 : GraphQL : le filtrage des champs à plusieurs valeurs (collections) n’est pas pris en charge au niveau JCR.
* SITES-37540 : remplacer et remplacer toutes les opérations pour les valeurs de champ CF (rechercher et remplacer pour un nom de champ donné).
* SITES-37741 : ajoutez la propriété « card » dans la réponse de variation de fragment get (mode Carte dans l’interface utilisateur d’administration).
* SITES-37754 : publication du dossier via l’API : validation de l’arborescence à la demande lorsque la `validateReferences` est définie sur true.
* SITES-37756 : affichage des informations sur le statut d’archivage/d’extraction d’un fragment de contenu.
* SITES-37805 : mise à jour du schéma : les fragments MODIFIÉS ne peuvent pas être renommés/déplacés (documentation).
* SITES-37847 : amélioration des performances de la requête SQL-2 du fournisseur de contenu prêté (récupération de LentContent).
* SITES-39255 : mettez à jour l’implémentation OpenAPI vers les modifications récentes de l’API Java pour le champ Composite.
* SITES-37096 : suppression de la lenteur de la console Lancements en présence de nœuds orphelins.
* SITES-38117 : trouvez un moyen d’interroger les lancements enfants sans impact sur les performances.
* SITES-38317 : ajoutez l’utilisateur qui a démarré le workflow aux métadonnées (utilisateur réel au lieu d’un utilisateur générique lorsqu’il est exécuté par l’utilisateur du service).
* SITES-39203 : affiche l’utilisateur qui a démarré le workflow (au lieu de l’utilisateur générique lorsqu’il est exécuté par l’utilisateur du service).
* SITES-13083 : localisez les chaînes d’erreur dans la boîte de dialogue Sites > Création d’une Live Copy .
* SITES-13389 : localisez la chaîne « Version créée de ... avant la promotion du lancement » dans Sites > Chronologie.
* SITES-16176 : localisez les chaînes dans la boîte de dialogue de configuration du composant Éditeur de page > Image v3 .
* SITES-35702 : chaîne « Live Copy à jour avec héritage limité » non localisée dans l’onglet « Aperçu de la Live Copy ».
* SITES-35748 : libellé de case à cocher « Activer la sélection de la variante de produit » non localisé dans « Éditeur de modèle de fragment de contenu ».
* SITES-35750 : espace réservé « SKU(s) de produit séparé(s) par `#` caractère » non localisé dans le champ de saisie « Éditeur de modèle de fragment de contenu ».
* SITES-37113 : boîte de dialogue « Annuler l’héritage » non localisée dans l’onglet « Configurations de CIF ».
* SITES-25240 : correctif d’accessibilité pour le call to action modal du teaser.
* SITES-25531 : correctif d’accessibilité pour le contraste des couleurs dans la boîte de dialogue modale de recherche.
* SITES-37115 : icônes tronquées dans le magasin de démonstration de Vienia.

### Problèmes résolus {#fixed-issues-24678}

* CQ-4361552 : correction du dictionnaire JSON i18n qui conservait l’unicode avec échappement HTML dans les traductions d’importation.
* CQ-4361634 : correction de fragments d’expérience qui n’étaient pas sélectionnables ou qui étaient ajoutés au projet de traduction.
* CQ-4362072 : correction de l’échec de l’étape de workflow de traduction AEMaaCS - DE > ES pour ajouter une page au projet de traduction.
* FORMS-23741 : les utilisateurs ont rencontré des problèmes où les étapes InvokeDDX et de chargement de ressources ne s’exécutaient pas en cascade, ce qui a nécessité deux exécutions de workflow distinctes. Cela affectait l’environnement de production utilisant AEM as a Cloud Service avec le module complémentaire Sites et Forms.
* FORMS-23877 : des problèmes se sont produits avec les fonctions personnalisées qui ne se chargent pas au moment de l’exécution lors de la création de formulaires directement dans les pages Sites à l’aide d’une ancienne version des composants principaux.
* FORMS-24038 : des problèmes sont survenus avec le bouton de navigation lorsque d’autres onglets ont été ajoutés dynamiquement.
* FORMS-23721 : correction d’un problème en raison duquel les modèles de validation configurés pour les entrées de texte dans la boîte de dialogue Modifier n’étaient pas conservés. Auparavant, la valeur du modèle était enregistrée, mais n’était pas conservée ni affichée dans l’interface utilisateur, ce qui entraînait une confusion pour les auteurs de formulaires.
* FORMS-23456 : les utilisateurs ont fait l’objet d’annonces incorrectes par les lecteurs d’écran sur les appareils mobiles pour les lignes d’en-tête masquées dans un tableau lors de l’utilisation du composant Tableau dans Adaptive Forms. Un en-tête de tableau masqué a été annoncé hors contexte, ce qui a créé de la confusion pour les utilisateurs qui dépendent d&#39;iOS VoiceOver et d&#39;Android TalkBack.
* FORMS-23454 : des problèmes sont survenus avec le sélecteur de date du Forms adaptatif basé sur les composants principaux. Lors de la saisie de dates non valides, le système corrige automatiquement les dates possibles fermées.
* FORMS-23117 : les utilisateurs ont rencontré un hCaptcha qui ne se traduisait pas correctement dans le Forms adaptatif basé sur les composants de base.
* FORMS-22634 : les utilisateurs ont rencontré un problème en raison duquel les pièces jointes d’e-mail n’étaient pas incluses lorsque les options « Inclure la pièce jointe » et « Utiliser le modèle HTML » étaient utilisées conjointement.
* FORMS-23288 : les utilisateurs ont rencontré des problèmes avec le Forms adaptatif incorporé dans les modèles Asset Share Commons. Le formulaire ne s’est pas chargé correctement lorsque l’URL contenue dans le chemin intermédiaire `.html`.
* FORMS-19198 : les utilisateurs ont rencontré des erreurs 404 lors de l’incorporation de formulaires à l’aide de règles de Dispatcher. Les erreurs se sont produites pour des URL telles que /etc.clientlibs/toggles.json, la bibliothèque Rum et analyticsparserconfigparser.json, car le module de réécriture d’URL ne pouvait pas réécrire ces URL.
* SITES-33799 : Edge Delivery avec éditeur universel : correction du rendu vidéo optimisé non publié.
* SITES-35082 : Edge Delivery avec éditeur universel : permet de supprimer les paragraphes vides, les sauts de ligne de début et de fin des textes riches.
* SITES-35524 : Edge Delivery avec éditeur universel : correction des échecs de publication pour les chemins contenant des caractères spéciaux non-ASCII.
* SITES-38647 : Edge Delivery avec éditeur universel : correction des goulots d’étranglement en termes de performances dans les environnements comportant de nombreux sites.
* SITES-40521 : Edge Delivery avec éditeur universel : correction des noms de classe en double pour les blocs et les éléments de bloc.
* SITES-37887 : GraphQL : les recherches UUID pour des jeux de résultats plus volumineux peuvent entraîner une augmentation des temps de réponse.
* SITES-38412 : impossible d’appliquer un correctif aux fragments dans le lancement lorsqu’un champ/slug unique existe (la contrainte unique exclut désormais les CF dans les lancements).
* SITES-38606 : erreur de validation lors de l’ajout d’une variation à CF avec l’UUID de référence de fragment (hydrater les CF référencés par l’UUID dans les variations).
* SITES-39489 : interface utilisateur d’Assets affichant des fragments de dossiers cq:discarded (CF supprimés de manière réversible et supprimés des réponses de l’API de gestion).
* SITES-39517 : échec de GET CF avec le champ composite contenant l’énumération avec l’erreur 500.
* SITES-40072 : les champs composites avec onglets renvoient des valeurs d’espace réservé vides.
* SITES-39575 : l’enregistrement de la Live Copy supprime `cq:rolloutConfigs` - la configuration de déploiement est perdue.
* SITES-39694 : échecs des déploiements de production avec NPE.
* SITES-39761 : NavigationItem.getLink() renvoie la valeur null dans le composant Navigation de CIF v2.
* SITES-40519 : le déploiement du MSM échoue avec NullPointerException lorsque la ressource cible de la Live Copy est nulle.
* SITES-17531 : chaîne « Aperçu du recadrage intelligent » codée en dur dans Éditeur de page > Image > Recadrage intelligent.
* SITES-31575 : l’info-bulle d’information n’est pas entièrement visible dans l’éditeur de page > Composant de carrousel > Propriétés.
* SITES-34215 : le composant JS de saisie semi-automatique génère une erreur de validation immédiate sur le champ de chemin requis dans l’onglet de boîte de dialogue.
* SITES-35218 : certains composants principaux d’AEM ne génèrent pas correctement la balise de remplacement vide.
* SITES-37114 : info-bulle tronquée « Activer la prise en charge de Catalog UID » dans l’onglet « Configurations de CIF ».
* SITES-36138 : requête sans index détecté (incident).
* SITES-37682 : remplacement du type de contenu dans `/libs/cq/Page/Page.css.jsp` et `/libs/cq/Page/Page.js.jsp.`
* SITES-38709 : l’éditeur de texte enrichi de l’interface utilisateur classique affiche l’HTML brut après la mise à niveau vers la version 6.5.24.
* SITES-39630 : les mises à jour de fragments de contenu imbriqués ne sont pas répercutées dans les offres Target exportées.
* SITES-39696 : l’heure d’activation/de désactivation de la planification de l’activation/la désactivation ne fonctionne pas.
* SITES-39824 : l’exportation de fragments d’expérience vers Adobe Target renvoie 500 (NPE).
* SITES-40253 : erreurs 500 intermittentes sur `/bin/cif/invalidate-cache` - Conflits Oak sous `/var/cif/cacheinvalidation`.
* SITES-40341 : correction des images intégrées base64 dans la balise styles de `HtmlToJsonConvertorImpl`.

### Problèmes connus {#known-issues-24678}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-24678}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-24678}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 15 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-24678}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.90.0 | [API Oak 1.90.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.90.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Serveur HTTP Apache | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| Composants principaux d’AEM | 2.30.4 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (par défaut) | [Versions de Node.js prises en charge](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |

