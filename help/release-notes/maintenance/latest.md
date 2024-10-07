---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: ee3e1bedddddff0aa41665359a91a0de48fd19c8
workflow-type: tm+mt
source-wordcount: '1411'
ht-degree: 90%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 17964 {#release-17964}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 17964, publiée le 25 septembre 2024. La version de maintenance précédente était la version 17689. La version 17882 a été rendue privée en raison d’un problème.

L’activation des fonctionnalités de la version 2024.10.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-17964}

* ASSETS - 37750 : [Priorité 4] [GraphQL] Prise en charge des URL DM scene7 : recadrage intelligent d’image.
* CQ - 4354583 : [AEMaaCS] Envoyer des événements de processus de traduction via Adobe Pipeline.
* CQ - 4357642 : mise à jour des informations d’identification MSFT dans le connecteur prêt à l’emploi.
* CQ - 4358217 : désérialiser le corps de la requête de l’entité de requête.
* CQ - 4358342 : enregistrer RequestProcessors dans une seule méthode HTTP.
* FORMS-10781 : amélioration de l’éditeur de règles afin de créer des règles pour l’élément suivant/précédent dans un panneau.
* FORMS - 14595 : [Fonctionnalité sans navigateur] Les valeurs sont manquantes dans le document d’enregistrement lorsque des données préremplies sont utilisées pour calculer le document d’enregistrement pour le rendu sans navigateur.
* FORMS - 15619 : mise à jour du kit de traduction AEM Forms.
* FORMS - 16113 : [Adobe Sign] Mise à jour impossible du statut du contrat par un autre utilisateur ou une autre utilisatrice.
* FORMS - 16155 : [Éditeur de règles] Implémentation de la fonction asynchrone.
* GRANITE - 53872 : ajout de nouvelles variables d’environnement pour l’identifiant client IMS.
* SITES - 23738 : version 2.27.0 des composants principaux.
* SITES - 16610 : fragments de contenu : obtention du point d’entrée des détails de lancement.
* SITES - 16614 : fragments de contenu : redéfinition du point d’entrée de lancement.
* SITES - 16615 : fragments de contenu : promotion du point d’entrée de lancement.
* SITES - 24215 : fragments de contenu : implémentation du point d’entrée Obtenir des sources de lancement.
* SITES - 20336 : fragments de contenu : amélioration de la validation lors de la suppression d’un modèle de fragment de contenu.
* SITES - 21090 : fragments de contenu : ajout de la prise en charge des valeurs fractionnaires minimales et maximales pour les champs de nombre.
* SITES - 21658 : fragments de contenu : mise à niveau pour utiliser les références UUID.
* SITES - 23054 : fragments de contenu : copie des modèles de fragment de contenu.
* SITES - 23264 : fragments de contenu : création d’un schéma statique d’un modèle.
* SITES - 23265 : fragments de contenu : exposition du schéma statique d’un modèle via le point d’entrée GET de schéma d’interface d’utilisation.
* SITES - 23266 : fragments de contenu : possibilité d’ajouter des contraintes aux modèles de fragment de contenu.
* SITES - 23778 : fragments de contenu : les modèles de fragment de contenu de recherche doivent permettre la recherche de modèles qui n’ont jamais été publiés.
* SITES - 23335 : fragments de contenu : ajout de la prise en charge des références de ressources externes.
* SITES - 24626 : fragments de contenu : RTC : autorisations pour la migration UUID : 2.
* SITES - 24786 : fragments de contenu : améliorations pour le point d’entrée `referencesTree`.
* SITES - 24833 : fragments de contenu : suppression de la validation de l’entrée HTML par rapport à une liste de balises HTML autorisées.
* SITES - 23380 : GraphQL : utilisation d’une API appropriée pour lire les métadonnées des ressources.
* SITES - 22864 : [Edge Delivery] Éditeur universel avec nouvelle intégration de structure de contenu AEM H2 2024.
* SITES - 23584 : échec des tests de composant de base sur Java 17.
* SITES - 23662 : Eventing : la personne qui déclenche une demande de publication ne peut pas être extraite des instructions de journal JCR dans les journaux du serveur.
* SITES - 23301 : ajout de la prise en charge du démarrage d’un nouveau workflow pour créer des structures de dossiers lors de la création de traductions de fragments de contenu.
* SITES - 23336 : fragments de contenu : ajout de la prise en charge des références de ressources externes
* SITES - 24091 : partage du package de contenu MSM : master.
* SITES - 24114 : isSourceRenderCondition : réduction du message du journal des erreurs à DEBUG.
* SITES - 24166 : réduction des ressources à distance pour l’éditeur d’interface d’utilisation tactile.
* SITES - 24409 : enregistrement de tous les processeurs de requêtes sur une seule méthode HTTP.
* SITES - 25008 : amélioration de la gestion des exceptions de persistance et des problèmes d’autorisation.
* SITES - 24821 : Faites d’aem.page / aem.live la valeur par défaut.

### Problèmes résolus {#fixed-issues-17964}

* CQ - 4356887 : incohérence dans le statut du projet de traduction pour Akamai Technologies Inc.
* CQ - 4357878 : le framework de traduction ne définit pas le statut d’erreur lors de la traduction de l’échec du fournisseur.
* CQ - 4358028 : échec de la création du projet si la miniature est chargée.
* CQ - 4358290 : le paramètre cible ne fonctionne PAS sur la page publiée.
* FORMS - 13173 : mauvais alignement de la liste déroulante dans le champ Formulaire adaptatif > Éditeur de règles > Déposer l’objet.
* FORMS - 13873 : AFv2 : (« - ») dans le nom du composant entraîne l’échec des règles.
* FORMS - 14340 : erreur lors de l’instanciation de FormsAndDocumentOmniSearchHandler et CloudStorageSubmitActionInserter.
* FORMS - 15363 : nom affiché dans l’éditeur de règles.
* FORMS - 15381 : amélioration de l’interface d’utilisation du message Champ d’application de l’autorisation.
* FORMS - 15595 : problème de saut de ligne du texte de consentement dans le composant AEM Form TnC.
* FORMS - 15623 : AEMaaCS Forms - alternatives à la mise à jour de plusieurs tableaux dans Dynamics avec une seule requête POST.
* FORMS - 15682 : AEM Forms - impossible de lier le document d’enregistrement à Dynamics FDM.
* FORMS - 15799 : la page Adobe Sign GovCloud Signature ne s’affiche pas dans l’iframe.
* FORMS - 15835 : problème de réécriture de l’URL du formulaire après envoi.
* FORMS - 16091 : consommation du fichier Binary.java restructuré.
* FORMS - 16096 : la personne utilisant Forms n’a pas accès à la boîte de dialogue de point d’entrée REST.
* FORMS - 16139 : ajout de la journalisation requise pour le document d’enregistrement dans le formulaire des composants principaux.
* FORMS - 6935 : l’état du composant actif ne présente pas de rapport de contraste de 3 à 1.
* FORMS - 7018 : l’élément vide reçoit le focus.
* GRANITE - 53028 : NPE dans ExternalProcessPollingHandler.
* GRANITE - 53907 : impossible d’identifier la personne utilisant le service comme super-utilisateur ou super-utilisatrice du workflow.
* SITES - 24405 : fragments de contenu - les informations étendues pour les énumérations doivent être plus résilientes.
* SITES - 23024 : fragments de contenu - l’énumération ne renvoie pas de valeur « locked: true » dans les fragments GET.
* SITES - 23269 : fragments de contenu : la création de fragments de contenu permet de définir des champs verrouillés.
* SITES - 23337 : fragments de contenu - échec du point d’entrée par lots avec `body` avec l’exception de conversion.
* SITES - 23474 : fragments de contenu - la pagination doit exclure les ressources rompues dans les fragments de contenu de recherche.
* SITES - 23615 : fragments de contenu - les informations de création de la copie de fragment de contenu ne sont pas mises à jour.
* SITES - 23668 : fragments de contenu - échec du correctif de la Live Copy avec plusieurs champs avec une erreur 400.
* SITES - 23695 : fragments de contenu : la description de l’onglet n’est pas disponible dans le schéma de l’IU.
* SITES - 23704 : fragments de contenu : énumérations à plusieurs valeurs non prises en charge dans _extendedInfo.
* SITES - 23781 : fragments de contenu : duplication des valeurs non autorisées dans les champs d’énumération.
* SITES - 24150 : fragments de contenu : les données de création de version de fragment de contenu sont manquantes.
* SITES - 24230 : fragments de contenu : correction du filtrage après le statut de réplication `modified` dans les modèles de fragment de contenu de recherche.
* SITES - 24233 : fragments de contenu : le filtrage par `publishedBy` peut inclure des ressources non publiées dans les modèles de fragment de contenu de recherche.
* SITES - 24355 : fragments de contenu : la relation en direct n’est pas respectée pour les fragments de contenu créés dans un dossier.
* SITES - 24816 : fragments de contenu : l’ordre des messages de statut de validation est incohérent.
* SITES - 23896 : Eventing : d’autres événements se combinent avec un événement Page déplacée.
* SITES - 23899 : Eventing : les événements de page sont retardés ou ne sont pas générés du tout.
* SITES - 23961 : Eventing : échec de la création de modèles de fragment de contenu avec des références lorsque le dossier de configuration est présent.
* SITES - 23963 : Eventing : les événements Page supprimée ne se produisent parfois pas.
* SITES - 23443 : GraphQL : comportement de requête du curseur GraphQL incohérent.
* SITES - 10994 : l’ordre de focus du clavier n’est pas logique.
* SITES - 16357 : AEM : le bouton est tronqué dans l’onglet Configurer Analytics du menu Sites.
* SITES - 19836 : le composant Ghost dans le conteneur s’affiche sur les instances de publication et de prévisualisation.
* SITES - 22348 : la page Vue d’ensemble des Live Copies ne parvient pas à se charger si elle contient plus de 100 Live Copies pour un projet.
* SITES - 22960 : résolveur de ressources non fermé dans ContentFragmentModelOmniSearchHandler.
* SITES - 23284 : l’encodage de l’URL provoque une boîte de dialogue d’explorateur de chemins d’accès vide.
* SITES - 23505 : les composants affichent des URL incorrectes lorsque la page est déplacée vers un autre emplacement.
* SITES - 23574 : impossible de prévisualiser/comparer avec les versions actuelles de nombreuses pages.
* SITES - 23585 : problème lié à la restauration de l’héritage pour les composants dont le nœud est cq:responsive.
* SITES - 23650 : incohérence dans le nombre de liens entrants dans l’environnement de création AEM.
* SITES - 23659 : régression du servlet de langue de contenu causée par le bouton (bascule) FT_*. SITES - 9757
* SITES - 23759 : les ressources ajoutées sur le fragment d’expérience ne sont pas publiées avec les lancements.
* SITES - 24025 : les redirections 302 dans AEM renvoient l’en-tête de l’emplacement à l’aide d’un DNS interne au lieu du DNS public.
* SITES - 24036 : enquête nécessaire pour les caractères persistants de l’éditeur de texte enrichi AEM au format ASCII.
* SITES - 24317 : la configuration du proxy ne fonctionne pas avec l’authentification de base.
* SITES - 24918 : correction des erreurs 504 renvoyées occasionnellement lors de l&#39;utilisation d&#39;une sortie ip dédiée.

### Problèmes connus {#known-issues-17964}

* FORMS - 15818 : entrée du descripteur de composant `OSGI-INF/com.adobe.aemfd.docmanager.impl.*.xml` introuvable dans les journaux de serveur. Ce sont des instructions de journal inoffensives.

### Fonctionnalités et API obsolètes {#deprecated-17964}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées ](/help/release-notes/deprecated-removed-features.md).

Vous trouverez ci-dessous un résumé des fonctions récemment obsolètes ou en cours d’obsolescence.

#### API JAVASCRIPT {#javascript-use-api}

[L’API d’utilisation de JavaScript](https://github.com/adobe/htl-spec/blob/master/SPECIFICATION.md#42-javascript-use-api) est officiellement obsolète en raison des défis auxquels les utilisateurs doivent faire face pour disposer d’un code de débogage et de maintenance qui tire parti de l’API, ainsi que des limites de performances par rapport à l’alternative Java.

Vous devez passer à [l’API d’utilisation de Java,](https://experienceleague.adobe.com/en/docs/experience-manager-htl/content/java-use-api) qui offre de meilleures performances, un débogage plus facile et une prise en charge plus étendue à long terme.

#### com.day.cq.wcm.api {#com-day-cq-wcm-api}

Veuillez noter que l’Adobe est en cours de mise à jour de `com.day.cq.wcm.api`. Certaines de ses méthodes et classes ont été marquées comme `@Deprecated` dans la version actuelle. Elles seront supprimées dans les prochaines versions. Veuillez envisager de passer à leurs alternatives proposées.

### Correctifs de sécurité {#security-17964}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 16 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-17964}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.68.0 | [API Oak 1.68.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.68.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.27.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
