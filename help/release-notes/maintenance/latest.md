---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: f728db32f77c58d47f52373987ed9bc83f22fdba
workflow-type: tm+mt
source-wordcount: '1354'
ht-degree: 17%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 17882 {#release-17882}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 17882, publiée le mercredi 24 septembre 2024. La version de maintenance précédente était la version 17689.

L’activation des fonctionnalités de la version 2024.10.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-17882}

* ASSETS - 37750 : [Priorité 4] [GraphQL] Prise en charge des URL DM scene7 : recadrage intelligent d’image.
* CQ - 4354583 : [AEMaaCS] Envoyez des événements de processus de traduction via Adobe Pipeline.
* CQ - 4357642 : Mettez à jour les informations d’identification MSFT dans le connecteur OOTB.
* CQ - 4358217 : désérialisez le corps de la requête de l’entité de requête.
* CQ - 4358342 : Enregistrez RequestProcessors sur une seule méthode HTTP.
* FORMS - 10781 : améliorez l’éditeur de règles pour créer des règles pour l’élément suivant/précédent dans un panneau.
* FORMS - 14595 : [Fonctionnalité sans navigateur] Les valeurs sont manquantes dans le DE lorsque des données préremplies sont utilisées pour calculer le DE pour le rendu sans navigateur.
* FORMS - 15619 : Kit de traduction mis à jour par AEM Forms.
* FORMS - 16113 : [Adobe Sign]Impossible de mettre à jour le statut du contrat par un autre utilisateur.
* FORMS - 16155 : [Éditeur de règles] Mettez en oeuvre la fonction asynchrone.
* GRANITE - 53872 : Ajout de nouvelles variables d’environnement pour l’identifiant client IMS.
* SITES - 23738 : Version 2.27.0 des composants principaux.
* SITES - 16610 : Fragments de contenu : Obtenez le point de terminaison des détails de lancement.
* SITES - 16614 : Fragments de contenu : point de terminaison Rebase Launch.
* SITES - 16615 : Fragments de contenu : Convertir le point de terminaison Launch.
* SITES - 24215 : Fragments de contenu : implémentation du point de terminaison Get Launch sources .
* SITES - 20336 : Fragments de contenu : amélioration de la validation lors de la suppression d’un modèle de fragment de contenu.
* SITES - 21090 : Fragments de contenu : ajout de la prise en charge des valeurs fractionnaires min/max pour les champs de nombre
* SITES - 21658 : Fragments de contenu : effectuez une mise à niveau pour utiliser les références UID.
* SITES - 23054 : Fragments de contenu : Copier des modèles de fragment de contenu.
* SITES - 23264 : Fragments de contenu : créez un schéma statique d’un modèle.
* SITES - 23265 : Fragments de contenu : Exposez le schéma statique d’un modèle via le point de terminaison de schéma d’interface utilisateur.
* SITES - 23266 : Fragments de contenu : possibilité d’ajouter des contraintes aux modèles de fragment de contenu.
* SITES - 23778 : Fragments de contenu : les modèles de fragment de contenu de recherche doivent permettre la recherche de modèles qui n’ont jamais été publiés.
* SITES - 23335 : Fragments de contenu : ajout de la prise en charge des références de ressources externes.
* SITES - 24626 : Fragments de contenu : RTC : Autorisations pour la migration UID : 2.
* SITES - 24786 : Fragments de contenu : améliorations pour le point de terminaison `referencesTree`.
* SITES - 24833 : Fragments de contenu : supprimez la validation de l’entrée d’HTML par rapport à une liste de balises d’HTML autorisées.
* SITES - 23380 : GraphQL : utilisez une API appropriée pour lire les métadonnées des ressources.
* SITES - 22864 : [Edge Delivery] Éditeur universel avec nouvelle intégration de structure de contenu d’AEM H2 2024.
* SITES - 23584 : les tests des composants de base échouent sur Java 17.
* SITES - 23662 : Eventing : l’utilisateur qui déclenche une requête de publication ne peut pas être extrait des instructions de journal JCR dans les journaux du serveur.
* SITES - 23301 : ajout de la prise en charge du démarrage d’un nouveau workflow pour créer des structures de dossiers lors de la création de traductions de fragments de contenu.
* SITES - 23336 : Fragments de contenu : ajout de la prise en charge des références de ressources externes
* SITES - 24091 : partage du package de contenu MSM : master.
* SITES - 24114: isSourceRenderCondition: Réduire le message du journal des erreurs à DEBUG.
* SITES - 24166 : Réduction des ressources à distance pour l’éditeur d’interface utilisateur tactile.
* SITES - 24409 : enregistrez tous les processeurs de requêtes sur une seule méthode HTTP.
* SITES - 25008 : amélioration de la gestion des problèmes de persistance, d’exceptions et d’autorisations.
* SITES - 24821 : [Xwalk] Faites de aem.page / aem.live la valeur par défaut.

### Problèmes résolus {#fixed-issues-17882}

* CQ - 4356887 : Incohérence dans l’état du projet de traduction pour Akamai Technologies Inc.
* CQ - 4357878 : La structure de traduction ne définit pas l’état d’erreur lors de la traduction de l’échec du fournisseur .
* CQ - 4358028 : Échec de la création du projet si la miniature est chargée.
* CQ - 4358290 : Le paramètre Target ne fonctionne PAS sur la page publiée.
* FORMS - 13173 : Désalignement de la liste déroulante dans Formulaire adaptatif > Éditeur de règles > Champ d’objet de dépôt.
* FORMS - 13873 : AFv2: (&quot;-&quot;) dans le nom du composant entraîne l’échec des règles.
* FORMS - 14340 : erreur lors de l’instanciation de FormsAndDocumentOmniSearchHandler et CloudStorageSubmitActionInserter.
* FORMS - 15363 : nom affiché dans l’éditeur de règles.
* FORMS - 15381 : amélioration de l’interface utilisateur du message Portée de l’autorisation .
* FORMS - 15595 : AEM composant Form TnC Consent Problème de saut de ligne de texte de consentement.
* FORMS - 15623 : AEMaaCS Forms - Alternatives à la mise à jour de plusieurs tables dans Dynamics avec un seul POST.
* FORMS - 15682 : AEM Forms - Impossible de lier DOR à Dynamics FDM.
* FORMS - 15799 : La page Adobe Sign GovCloud Signature note le rendu dans iframe.
* FORMS - 15835 : problème de réécriture de l’URL du formulaire après envoi.
* FORMS - 16091 : Consommation du fichier Binary.java restructuré.
* FORMS - 16096 : l’utilisateur de Forms n’a pas accès à la boîte de dialogue de point de restauration.
* FORMS - 16139 : ajout de la journalisation requise pour le DE dans le formulaire des composants principaux.
* FORMS - 6935 : l’état du composant actif n’a pas de rapport de contraste de 3 à 1.
* FORMS - 7018 : l’élément vide reçoit le focus.
* GRANITE - 53028 : NPE dans ExternalProcessPollingHandler.
* GRANITE - 53907 : impossible d’identifier l’utilisateur du service comme super-utilisateur du workflow.
* SITES - 24405 : Fragments de contenu : les informations étendues pour les énumérations doivent être plus résilientes
* SITES - 23024 : Fragments de contenu : l’énumération ne renvoie pas verrouillé : vrai dans les fragments de GET.
* SITES - 23269 : Fragments de contenu : la création de fragments de contenu permet de définir des champs verrouillés.
* SITES - 23337 : Fragments de contenu : le point de terminaison par lots avec `body` échoue avec l’exception de diffusion.
* SITES - 23474 : Fragments de contenu : la pagination doit exclure les ressources rompues dans les fragments de contenu de recherche.
* SITES - 23615 : Fragments de contenu : la copie de fragment de contenu AuthoringInfo n’est pas mise à jour
* SITES - 23668 : Fragments de contenu : le correctif de la Live Copy avec plusieurs champs échoue avec 400
* SITES - 23695 : Fragments de contenu : la description de l’onglet n’est pas disponible dans UiSchema
* SITES - 23704 : fragments de contenu : énumérations à plusieurs valeurs non prises en charge dans _extendedInfo
* SITES - 23781 : Fragments de contenu : Duplication des valeurs non autorisées dans les champs d&#39;énumération
* SITES - 24150 : Fragments de contenu : Version de fragment de contenu La création de données sur la création est manquante
* SITES - 24230 : Fragments de contenu : correction du filtrage après l’état de réplication `modified` dans les modèles de fragment de contenu de recherche
* SITES - 24233 : Fragments de contenu : le filtrage par `publishedBy` peut inclure des ressources non publiées dans les modèles de fragment de contenu de recherche
* SITES - 24355 : Fragments de contenu : la relation en direct n’est pas respectée pour les fragments de contenu créés par le dossier
* SITES - 24816 : Fragments de contenu : l’ordre des messages ValidationStatus est incohérent.
* SITES - 23896 : Événement : d’autres événements se combinent avec un événement Déplacé de page
* SITES - 23899 : Eventing : les événements de page sont retardés ou ne sont pas générés du tout
* SITES - 23961 : Eventing : la création de modèles de fragment de contenu avec des références échoue lorsque le dossier de configuration est présent
* SITES - 23963 : Événement : les événements de suppression de page ne se produisent parfois pas
* SITES - 23443 : GraphQL : comportement de requête du curseur GraphQL incohérent.
* SITES - 10994 : L’ordre de focus du clavier n’est pas logique.
* SITES - 16357 : AEM : le bouton est tronqué dans l’onglet Configuration d’Analytics du menu Sites.
* SITES - 19836 : le composant Ghost dans le conteneur s’affiche sur les instances de publication et de prévisualisation.
* SITES - 22348 : la page Aperçu de la Live Copy ne parvient pas à se charger si elle contient plus de 100 Live Copies pour un projet.
* SITES - 22960 : résolveur de ressources non fermé dans ContentFragmentModelOmniSearchHandler.
* SITES - 23284 : l’encodage de l’URL provoque une boîte de dialogue de navigateur de chemin d’accès vide.
* SITES - 23505 : les composants affichent des URL incorrectes lorsque la page est déplacée vers un autre emplacement.
* SITES - 23574 : impossible de prévisualiser/comparer les versions actuelles de nombreuses pages
* SITES - 23585 : problème lié à la restauration de l’héritage pour les composants dont le noeud cq:responsive
* SITES - 23650 : Incohérence dans le nombre de liens entrants dans AEM environnement de création
* SITES - 23659 : régression du servlet de langue de contenu causée par le basculement FT_* SITES - 9757
* SITES - 23759 : Les Assets ajoutées sur le fragment d’expérience ne sont pas publiées avec les lancements
* SITES - 24025 : 302 Redirections dans AEM renvoi de l’en-tête de l’emplacement à l’aide d’un DNS interne au lieu du DNS public
* SITES - 24036 : enquête nécessaire pour AEM caractères persistants de l’éditeur de texte enrichi au format ASCII
* SITES - 24317 : La configuration du proxy ne fonctionne pas avec l’authentification de base
* SITES - 24918 : [Xwalk] corrige les erreurs 504 renvoyées occasionnellement lors de l’utilisation d’une sortie ip dédiée.
* SITES - 2864 : Accessibilité - La fonction de glisser-déposer n’est pas accessible via le clavier.

### Problèmes connus {#known-issues-17882}

* FORMS - 15818 : entrée du descripteur de composant `OSGI-INF/com.adobe.aemfd.docmanager.impl.*.xml` introuvable dans les journaux de serveur. Ce sont des instructions de journal inoffensives.

### Fonctionnalités et API obsolètes {#deprecated-17882}

Nous actualisons en ce moment `com.day.cq.wcm.api`. Dans la version actuelle, nous avons déclaré certaines de ses méthodes et classes comme `@Deprecated`. Celles-ci seront supprimées des prochaines versions. Envisagez donc de passer à leurs alternatives qui sont suggérées si vous utilisez l’une d’elles.

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-17882}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 16 vulnérabilités identifiées, renforçant notre engagement envers une protection système robuste.

### Technologies intégrées {#embedded-tech-17882}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.68.0 | [API Oak 1.68.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.68.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.27.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
