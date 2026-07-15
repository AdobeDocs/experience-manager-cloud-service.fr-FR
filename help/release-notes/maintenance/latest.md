---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 09c52e32e6ffff2c69fb24f28e99a65477b434ec
workflow-type: tm+mt
source-wordcount: '1311'
ht-degree: 15%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## 27083 de publication {#release-27083}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 27083, rendue publique le 15 juillet 2026. La version de maintenance précédente était la version 26908.

L’activation de la fonctionnalité 2026.7.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-27083}

* Possibilité de supprimer la configuration de traduction dans CQ-4354303:Added.
* FORMS-23746 : incompatibilité de type de données entre les étapes de workflow InvokeDDX et Chargement de ressources qui empêchaient de les utiliser en séquence.
* FORMS-24585 : connecteur AEP avec un approvisionnement plus facile.
* FORMS-25250 : introduction du service ConvertPdf.
* FORMS-26044 : ajout de l’analyse des virus/programmes malveillants des pièces jointes pour les chargements sur AF1 et les formulaires basés sur les composants principaux.
* GRANITE-69298 : permet d’ajouter des index `cqPageContent-5` et `graphqlConfig-3`.
* SITES-42563 : Edge Delivery avec l’éditeur universel : afficher les erreurs de publication dans l’éditeur universel et l’administration de sites (accès anticipé).
* SITES-42792 : espace réservé « Sélectionner le chemin du Source Launch » tronqué dans le panneau de filtrage dans « Outils » > « Général » > « Lancements ».
* SITES-43178 : AEM : le format d’heure localisé inclut AM/PM dans Outils > Sites > Lancements.
* SITES-44344 : API de contenu : traitez les copies de langue/MSM comme faisant partie du site parent.
* SITES-44598 : bouton Afficher le contrôle en amont dans la barre d’en-tête de l’éditeur.
* SITES-44676 : les résultats de la recherche de fragments de contenu incluent désormais l’identifiant de schéma de métadonnées pour chaque fragment.
* SITES-44767 : ajout d’un schéma de métadonnées par défaut pour les fragments de contenu.
* SITES-45651 : correction de l’exemple de fragment de contenu OpenAPI dans la spécification d’API.
* SITES-45664 : ajout d’un nouveau point d’entrée de `/cf/metadata/schemas` GET pour récupérer les propriétés de métadonnées filtrables.
* SITES-45725 : API de contenu : ajoutez le filtre de corrélation des demandes pour activer les alertes de traversée SLO d’Oak.
* SITES-45817 : Edge Delivery avec éditeur universel : vérifiez les rôles et autorisations de diffusion Edge lors de la publication (accès anticipé).
* SITES-45842 : Edge Delivery avec éditeur universel : conservez l’instrumentation de l’éditeur universel pour les cas d’utilisation en lecture seule et en révision/commentaire.
* SITES-45848 : Edge Delivery avec éditeur universel : validation du `json-ld` avant publication.
* SITES-46768 : Edge Delivery avec éditeur universel : permet d’afficher les problèmes de création de site dans l’assistant de création de site.

### Problèmes résolus {#fixed-issues-27083}

* CQ-4364078 : correction de la réécriture des liens internes dans les fragments d’expérience par la copie de langue.
* CQ-4364077 : Correction d’une interruption de la création de la copie de langue en raison de conflits OakState0001.
* CQ-4363949 : correction d’un ajout incorrect de fragments d’expérience référencés inchangés dans la traduction uniquement des mises à jour.
* CQ-4363942 : IU Balises : le menu déroulant « Ajouter une langue » affiche désormais les paramètres régionaux non répertoriés qui n’étaient pas visibles bien qu’ils soient conservés dans JCR.
* CQ-4363527 : correction d’un problème d’interface utilisateur du widget de copie de la langue pour la méthode et le fournisseur Agentic.
* FORMS-25979 : mise à niveau de la bibliothèque Underscore.js (1.13.6 → 1.13.8+) dans le module complémentaire AEM Forms.
* FORMS-18969 : correction d’un problème en raison duquel les thèmes AEM Forms empêchaient les utilisateurs de mettre à jour l’aperçu du formulaire.
* FORMS-25184 : correction des points indicateurs de liaison de données manquants dans le panneau latéral Sources de données pour les formulaires basés sur les composants principaux (AF v2).
* FORMS-18721 : correction d’un problème qui empêchait les thèmes AEM Forms de mettre à jour la bibliothèque cliente de base.
* FORMS-19235 : correction d’une erreur d’application qui pouvait exposer des informations sensibles dans Forms Manager.
* FORMS-25369 : correction d’un problème en raison duquel la copie d’un thème ne transférait pas les dépendances de bibliothèque cliente à partir des métadonnées de la bibliothèque cliente de base.
* FORMS-25372 : correction des échecs de préremplissage et des problèmes de fusion JSON affectant les Forms adaptatives incorporées.
* FORMS-24853 : correction d’un problème de tabulation du composant Signature tactile (composant de base) dans le Forms adaptatif.
* SITES-41928 : le chevauchement Contexthub + Unified Shell rend le menu de composant inaccessible dans l’éditeur.
* SITES-46579 : API de contenu : correction de la traversée du référentiel dans la requête de copie de langue du service de relation ; définition de la requête d’index et de réécriture.
* SITES-44192 : API Forms/Content : l’API Content renvoie la valeur 404 pour les formulaires EDS utilisant `sling:configRef` au lieu de `cq:conf`.
* SITES-29367 : GraphQL : permet de protéger ModelManager des personnalisations d’index de `cqPageLucene` défectueuses.
* SITES-46521 : API de contenu : la `jcr:path` dans la requête entraîne le parcours transversal des requêtes.
* SITES-46784 : GraphQL : les modèles de ModelManager doivent être dédupliqués.
* SITES-46304 : API de contenu : la recherche de page de l’API de contenu exclut silencieusement les `/content/campaigns`.
* SITES-46769 : GraphQL : le cache de données par demande avec des modèles de fragment de contenu volumineux entraîne des exceptions OOM.
* SITES-46570 : API de contenu : utilisez l’opérande path() indexé dans la requête de modèles pour le pushdown d’index.
* SITES-24497 : des libellés distincts sont désormais fournis pour les repères répétés afin que les technologies d’assistance puissent les différencier.
* SITES-24525 : correction d’un rôle d’en-tête incorrect attribué aux boutons modaux ; les lecteurs d’écran les annoncent désormais comme des boutons.
* SITES-24703 : l’indicateur de sélection des boutons contextuels de la zone de liste est désormais entièrement visible et n’est plus tronqué.
* SITES-25217 : l’icône d’informations a été agrandie pour répondre aux exigences de taille cible minimale.
* SITES-25263 : correction de la valeur aria-haspopup dans le champ de date Timewarp afin que les lecteurs d’écran l’annoncent correctement.
* SITES-25308 : contraste accru sur les indicateurs de focus du bouton de la barre d’outils démographique pour atteindre le minimum de WCAG.
* SITES-25318 : amélioration du contraste du texte des champs de saisie dans la barre d’outils Démographie.
* SITES-25364 : les instructions de saisie sont désormais liées par programmation à leur case à cocher, de sorte que les techniciens d’assistance les annoncent ensemble.
* SITES-25377 : le rail latéral Assets ne recharge plus son contenu lorsque le champ de filtrage reçoit le focus.
* SITES-40752 : amélioration de la navigation au clavier dans la liste des composants du panneau latéral.
* SITES-41121 : empêchait les lecteurs d’écran d’annoncer un libellé de groupe masqué à côté du nom du composant.
* SITES-43802 : suppression d’une chaîne « false » indésirable qui apparaissait dans la boîte de dialogue modale Insérer un composant.
* SITES-46720 : les radios Page-Properties perdent la sélection enregistrée après la mise à jour 2026.05+ (SDK ≥ 26353) - valeurs effacées côté client.
* SITES-46680 : impossible de créer CF Launch en raison du mappage du servlet Sling dans le code personnalisé.
* SITES-46327 : lors de la création d’un lancement avec l’option « Hériter des données actives de la page source » activée, le fragment d’expérience de la page source n’est pas hérité, et certains liens sont également rompus.
* SITES-45969 : pages enfants supprimées lors de la promotion de lancement lors de l’utilisation de « nouveau modèle » + « inclure les sous-pages ».
* SITES-45723 : la correction SITES-44245 interrompt les lancements : empty-genericFrom Guard supprime les réécritures de référence de lancement légitimes.
* SITES-45689 : échecs de déploiement MSM intermittents - « Aucun chemin Source » et AccessDeniedException.
* SITES-44918 : code de langue indonésien affiché dans au lieu de l’ID.
* SITES-41427 : le déploiement XF signale un succès, mais échoue silencieusement lorsqu’il n’existe aucune Live Copy - demande de gestion appropriée ou de création automatique
* SITES-36149 : duplication de composant dans Launch après la promotion avec synchronisation en direct.
* SITES-25970 : la boîte de dialogue Déploiement pour l’interface utilisateur du composant est coupée.
* SITES-30707 : correction d’un libellé « Général » codé en dur dans l’éditeur de fragment de contenu pour prendre en charge la localisation.
* SITES-44228 : correction d’un problème en raison duquel la suppression d’un fragment de contenu référencé via l’uuid ne faisait pas l’objet d’un ajustement des fragments référencés.
* SITES-45171 : correction d’un problème en raison duquel la demande de publication pouvait déclencher de manière incorrecte un workflow de Demande d’activation .
* SITES-46303 : récupération de version fixe pour éviter les tentatives inutiles de migration de carte.
* SITES-46713 : correction de l’échec des opérations PATCH lorsque l’utilisateur ne dispose pas des autorisations de suppression requises pour la migration des cartes.
* SITES-46590 : correction d’une régression en raison de laquelle le retour à une version précédente dans le journal n’actualisait pas la miniature de la carte de la ressource dans la vue Administration d’Assets.
* SITES-47292 : Edge Delivery avec éditeur universel : correction du rendu des balises fusionnées dans les métadonnées de page.

### Problèmes connus {#known-issues-27083}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-27083}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-27083}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 18 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-27083}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 2.2.0 | [API Oak 2.2.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/2.2.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Serveur HTTP Apache | 2.4.67 | [Apache Httpd 2.4.67](https://apache.googlesource.com/httpd/+/refs/tags/2.4.67/CHANGES) |
| Dispatcher | 2.0.274 |  |
| Composants principaux AEM | 2.31.2 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (par défaut) | [Versions de Node.js prises en charge](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
| Java 21 | 21.0.11 | [JDK 21.0.11](https://www.oracle.com/java/technologies/javase/21-0-11-relnotes.html) |
