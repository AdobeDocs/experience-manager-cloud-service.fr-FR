---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: f12e60cdfce24dd2f6c1400157180d16b1b98653
workflow-type: tm+mt
source-wordcount: '998'
ht-degree: 20%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 17393 {#release-17393}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 17393, publiée le mercredi 13 août 2024.  La version de maintenance précédente était la version 17258.

L’activation des fonctionnalités de la version 2024.8.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-17393}

* FORMS-15436 - Gérez élégamment l’exception dans le planificateur de statut Adobe Sign.
* FORMS-15362 - Ajoutez une configuration pour forms-foundation dans aemds afin d’activer la connexion.
* FORMS-15261 - SPA ne s’affiche pas dans l’éditeur Forms.
* FORMS-15138 - Gestion de la compatibilité ascendante des données doubles en raison de la mise à niveau de json sling commons.
* FORMS-15113 - Modification du nom de la clé pour sid à partir de vistorId pour le suivi RUM.
* FORMS-15103 - Les Assets jointes à un formulaire ne sont pas publiées dans la diffusion Edge.
* FORMS-15082 - Schéma JSON à mapper aux composants de formulaire adaptatif personnalisés.
* FORMS-15002 - Enregistrement du type de modèle des fragments v1.
* FORMS-14845 - Prise en charge de xdpRef dans le formulaire des bases de composants principaux via Forms Manager.
* FORMS-14840 - Erreurs du service de préremplissage Forms.
* FORMS-14836 - Amélioration de l’interface utilisateur du gestionnaire de formulaires pour répertorier les modèles de fragments AF1.
* FORMS-14834 - Prise en charge des modèles pour les fragments dans AF1.
* FORMS-14275 - Remplacement de la page de remerciement et du message de remerciement dans le conteneur intégré.
* FORMS-13623 - Activez la fonctionnalité basée sur le gain de temps automatique pour V2.
* FORMS-8651 - Boîte de dialogue d’avertissement relative à la modification de la configuration du modèle de données sur la page des propriétés du formulaire.
* SITES-23310 - API REST des fragments de contenu : prévention des dépendances circulaires dans les références imbriquées pour les fragments de contenu.
* SITES-23285 - API REST des fragments de contenu : créez un point de terminaison pour répertorier toutes les langues disponibles.
* SITES-22857 - API REST des fragments de contenu : les champs d’énumération de case à cocher ne doivent pas autoriser la définition de plusieurs propriétés sur false.
* SITES-22813 - API REST des fragments de contenu : définissez les propriétés min./max. pour les champs d’énumération.
* SITES-22031 - API REST des fragments de contenu : Obtenez les modèles de fragments de contenu autorisés pour le dossier d’un fragment.
* SITES-17640 - API REST de fragments de contenu : validation de l’opération Publish de fragments de contenu.
* SITES-22677 - API REST des fragments de contenu : récupération d’une liste plate de références descendantes
* SITES-22207 - Modèle dupliqué lors de la création de fragments de contenu.
* SITES-23093 - Eventing : ajoutez des balises aux charges utiles pour les événements de modèle de fragment de contenu.
* SITES-23092 - Eventing : ajoutez des balises aux payloads pour les événements de fragment de contenu.
* SITES-22447 - Ajoutez la prise en charge de l’héritage des propriétés du fragment d’expérience à l’onglet Propriétés de base .
* SITES-12209 - Améliorez les performances de l’éditeur de stratégies en ajoutant cq:policy à l’index.

### Problèmes résolus {#fixed-issues-17393}

* CQ-4358028 - Échec de la création du projet si la miniature est chargée.
* CQ-4357891 - Problème de séquence du fichier XLIFF exporté.
* CQ-4357059 - La tâche de traduction prend des heures, ce qui entraîne un délai d’attente de 503 dans AEMaaCS.
* FORMS-15320 - L’envoi d’un courrier électronique ne fonctionne pas dans un formulaire basé sur des composants principaux.
* FORMS-15272 - AEM Forms - Groupe de cases à cocher envoyant uniquement une valeur 1.
* FORMS-15269 - Problèmes liés aux produits après la version de maintenance 16461.
* FORMS-15174 - Problème JsonSchemaParser isValid .
* FORMS-15095 - La zone de texte multiligne peut être étirée au-delà de la contenant des panneaux dans AEM Forms.
* FORMS-15057 - Liste FDM SharePoint renvoyant une erreur de pièce jointe pour envoi > 999.
* FORMS-15011 - L’éditeur principal provoque une erreur de console lors de l’ouverture d’un formulaire dans l’éditeur.
* FORMS-14809 - Le dossier SDK n’est pas automatiquement créé dans le répertoire temporaire partagé.
* FORMS-14327 - API du service Forms : Extraction de données : - donne le code de réponse 500 lorsqu’un pdf non interactif est fourni en entrée.
* FORMS-7475 - Le tri ne fonctionne pas sur la page de création de formulaire adaptatif.
* FORMS-3309 - Si plusieurs options sont sélectionnées lors de l’envoi d’un formulaire, une seule option s’affiche dans un document d’enregistrement généré.
* SITES-23646 - Le point de terminaison des modèles GraphQL échoue pour les modèles créés avec OpenAPI si les champs contiennent des valeurs uniques.
* SITES-23637 - API REST des fragments de contenu : OpenAPI n’utilise pas le type de valeur correct pour les énumérations.
* SITES-23573 - API REST des fragments de contenu : les relations en direct ne sont pas respectées sur les fragments de contenu GET par uuid.
* SITES-23535 - API REST des fragments de contenu : l’énumération modèle de fragment de contenu plusieurs champs ont des valeurs vides.
* SITES-23534 - API REST des fragments de contenu : Classe de validation des fragments de contenu CastException.
* SITES-23524 - Adaptez le point de terminaison des modèles BFF GraphQL pour prendre en charge les champs d’énumération à champs multiples.
* SITES-23467 - API REST des fragments de contenu : les modèles de recherche échouent en raison d’un problème de curseur.
* SITES-23327 - ArrayIndexOutOfBoundsException dans AuditLogTimelineEventProvider pendant le traitement de l’événement de la chronologie Description.
* SITES-23277 - API REST des fragments de contenu : la vérification de la relation dynamique du champ de fragment de contenu ne doit être effectuée que pour les Live Copies.
* SITES-23232 - La validation personnalisée ne fonctionne pas dans la nouvelle interface utilisateur de l’éditeur de CF.
* SITES-23090 - API REST de fragments de contenu : impossible de mettre à jour le titre d’un fragment de contenu verrouillé.
* SITES-22981 - La promotion d’un lancement imbriqué qui n’est pas profond n’est pas publiée.
* SITES-22870 - PathAttributesHandler.processSrcAttr ArrayIndexOutOfBoundsException.
* SITES-22814 - API REST des fragments de contenu : les valeurs des champs de fragment d’énumération case à cocher doivent être triées par les clés définies dans le modèle.
* SITES-22716 - Problème avec la liste d’utilisation en direct des composants prêts à l’emploi.
* SITES-22457 - La promotion d’un lancement qui n’est pas profond ne met pas à jour le contenu source.
* SITES-22449 - Impossible d’enregistrer les modifications dans les fragments de contenu après AEM mise à niveau P20.
* SITES-22279 - API REST des fragments de contenu : le fragment de contenu ne contient pas l’attribut unique pour les types d’énumération.
* SITES-22203 - API REST des fragments de contenu : Align Management APIs pour répondre à la même situation.
* SITES-21973 - API REST des fragments de contenu : l’attribut unique du modèle pour les types d’énumération est absent.
* SITES-20364 - 302 Redirections Non-utilisation du sélecteur dans l’URL.
* SITES-21198 - VersionPreviewServlet : le nettoyage s’exécute simultanément sur tous les noeuds de la grappe, ce qui provoque des conflits de fusion et des validations de blocs.
* GRANITE-53094 - Les objets d’utilisation JS basés sur le référentiel ne peuvent pas être localisés lors de l’utilisation de chemins relatifs.

### Problèmes connus {#known-issues-17393}

Aucun.

### Avis de modification {#change-notice-17393}

* À compter de septembre 2024, AEM as a Cloud Service désactivera la sérialisation des résolveurs de ressources via le framework de l’exportateur de modèle Sling. Voir la [documentation](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md) pour plus d’informations.

### Fonctionnalités et API obsolètes {#deprecated-17393}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées ](/help/release-notes/deprecated-removed-features.md).

### Technologies intégrées {#embedded-tech-17393}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.66.0 | [API Oak 1.66.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.66.0/index.html) |
| API SLING AEM | 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.25.4 | [Composants principaux de la gestion de contenu Web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
