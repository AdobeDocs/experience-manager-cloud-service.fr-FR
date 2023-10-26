---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: aa9629c3e48ca0bf4654351462a94777af9ed651
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 22%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 14029 {#release-14029}

Vous trouverez ci-dessous un résumé des améliorations continues apportées à la version de maintenance 14029, qui a été publiée publiquement le 25 octobre 2023. Cette mise à jour de maintenance est une mise à jour de la version de maintenance 13804 précédente.

L’activation des fonctionnalités de la version 2023.11.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour plus d’informations.

### Améliorations {#enhancements-14029}

* ASSETS-28551 : amélioration de l’évolutivité de l’interface utilisateur de mes partages de lien
* ASSETS-28566 : Ajout de l’index dam:metadataForm Lucene
* ASSETS-29281 : mise à jour de RAPI pour envoyer des événements de téléchargement v2

### Problèmes résolus {#fixed-issues-14029}

* ASSETS-25199 : composant de base d’image n’affichant pas les recadrages intelligents appropriés
* ASSETS-26142 : unified-shell.js customEnvLabel non défini ou tenté de nouveau si la demande de découverte échoue ou est interrompue
* ASSETS-26416 : Prédicat de date relative toujours défini comme &quot;il y a 1 jour(s)&quot; dans le formulaire de recherche
* ASSETS-27321 : effacer le cache du groupe lors des modifications de l&#39;appartenance à l&#39;équipe
* ASSETS-27591 : correction de la dépendance à l’ancien org.json
* ASSETS-28439 : Liste bloquée NPE des balises intelligentes lorsque la liste bloquée globale n’est pas configurée
* ASSETS-28612 : correctif BlockedTagResolver dans &quot;repository-api&quot;
* ASSETS-28634 : Le champ Omni-recherche du stock d’Adobe n’ajoute pas automatiquement les données de ressource.
* ASSETS-28727 : La liste Configuration du profil de traitement n’affiche pas les valeurs de hauteur et de largeur personnalisées spécifiées.
* ASSETS-29056 : Ajout de rendus de transcodage AEM profil de traitement standard
* ASSETS-29105 : fournisseur de restriction manquant dans SecurityProviderRegistration requiredServicePids dans le modèle de fonctionnalité RDE
* ASSETS-29106 : l’affichage sur le stock d’Adobe renvoie une erreur sur le shell unifié activé AEM
* ASSETS-29115 : suppression de la propriété de configuration pour les chemins du fournisseur de restrictions
* ASSETS-29208 : erreurs de chargement de ressources dues aux demandes envoyées à une capsule de création avant l’enregistrement du service CompleteUploadAssetServlet
* ASSETS-29297 : Problème lors de la création de l’option Enregistrer la recherche avec le filtre extrait
* ASSETS-29363 : Profil de métadonnées n’appliquant pas les valeurs par défaut pour IPTC
* ASSETS-29404 : rapport Partages de lien atteignant la limite de requête
* ASSETS-29431 : suppression des anciens indicateurs de fonctionnalité
* ASSETS-29443 : L’héroïne de Shell unifiée reste visible et cliquable lorsque le mode En-tête de Shell Granite passe à &quot;sélection&quot;.
* ASSETS-29476 : l’appel de l’API scene7DAMService.getS7FileReference(asset) ne renvoie pas la valeur attendue.
* ASSETS-29515 : Ressources/noeuds avec &quot;jcr:lastModifiedBy&quot;: &quot;workflow-process-service&quot; s’affiche en tant qu’&quot;utilisateur externe&quot; en mode Liste
* ASSETS-29579 : Les utilisateurs non-administrateurs ne peuvent pas créer de visionneuse d’images
* ASSETS-29631 : Utilisez dam:fields pour une diffusion/recherche sécurisée
* ASSETS-29689 : dc:tasks (et la nouvelle propriété dam:rôles) doit être filtrée depuis AEM côté
* ASSETS-29738 : la restriction de chargement des ressources échoue avec NullPointerException
* ASSETS-29779 : les petites ressources ne peuvent pas être traitées sur le web car elles ne sont pas dans le stockage d’objets blob.
* ASSETS-29892 : l’exportation des métadonnées échoue sur un dossier contenant un grand nombre de ressources
* ASSETS-29996 : &quot;Utilisateur externe&quot; comme modificateur lors du chargement de ressources par intermittence uniquement sur l’instance PROD
* ASSETS-30167 : HTML pour adobe_dam:restrictions interrompt après le téléchargement d’une ressource.
* ASSETS-30276 : interface utilisateur de partage de lien : impossible de partager à partir des détails de ressource
* ASSETS-30434 : l’événement de fin du traitement des ressources n’est pas envoyé au pipeline
* ASSETS-30519 : Ajout de RAPI à REDMetricsServletFilter
* CQ-4354413 : QueryBuilder : les requêtes avec crochets sont incorrectement traduites en xpath.
* CQ-4354834 : impossible d’ajouter un commentaire dans la tâche de boîte de réception
* CQ-4354836 : impossible de démarrer un workflow ou de créer une tâche à partir de la console Projets
* CQ-4354867 : La référence ToggleCondition fait référence à un champ inexistant dans InstanceActionServlet
* CQ-4354895 : AEM Kit de traduction : 12 octobre
* GRANITE-45560 : Représentation de schéma commune dans l’enveloppe Eventing
* GRANITE-47267 : Mise à jour vers Apache Felix Http Jetty 4.2.18
* GRANITE-47599 : Échec des importations de contenu depuis la mise à niveau 13323 (JCRVLT-721)
* GRANITE-47873 : Mise à jour vers Apache Felix Webconsole 4.9.6

### Problèmes connus {#known-issues-14029}

* CQ-4354836 : impossible de démarrer un workflow ou de créer une tâche à partir de la console Projets.
* CQ-4354834 : les utilisateurs ne peuvent pas ajouter de commentaires dans une tâche de boîte de réception.

### Technologies intégrées {#embedded-tech-14029}

| Technologie | Version | Lien |
|---|---|---|
| AEM OAK | 1.56-T20230927085643-189caed | [API Oak 1.56.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.56.0/index.html) |
| API SLING AEM | Version 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | Version 2.23.4 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
