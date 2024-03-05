---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 77a4b445d9117959ed8855aef445c02529178800
workflow-type: tm+mt
source-wordcount: '1097'
ht-degree: 12%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 15262 {#release-15262}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 15262, publiée le mercredi 5 mars 2024. La version de maintenance précédente était la version 14697.

L’activation des fonctionnalités de la version 2024.3.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour plus d’informations.

### Améliorations {#enhancements-15262}

* ASSETS-30632 : Ajout d’une colonne d’état de publication Brand Portal distincte en mode Liste.
* ASSETS-30934 : ajout de la prise en charge de `Iptc4xmpCore:AltTextAccessibility` et `Iptc4xmpCore:ExtDescrAccessibility` propriétés de l’éditeur de métadonnées de ressources.
* ASSETS-31297 : amélioration des contrôles pour empêcher la suppression des ressources copiées de Dynamic Media.
* ASSETS-33246 : Définition de l’index de publication `damAssetLucene-10`.
* ASSETS-33590 : Ajoutez la prise en charge des rendus web pour les vidéos dans les profils de traitement.
* GRANITE-36205 : mettez à jour la version Oak vers 1.60-T20240131102219-0cde853.
* SITES-19326 : Mise à jour de liens dans l’interface utilisateur d’Assets pour ouvrir CF dans le nouvel éditeur de CF.
* GUIDES-12945 : Suggestions intelligentes optimisées par l’IA pour ajouter des références de contenu lors de la création de contenu
* GUIDES-12706 : fonctionnalité d’historique des versions restructurée de l’éditeur web
* GUIDES-14948 : expérience utilisateur améliorée dans le panneau Traduction
* GUIDES-8782 : logique de recherche améliorée dans la boîte de dialogue Insérer l’élément
* GUIDES-14681 : possibilité de publier plusieurs paramètres prédéfinis de sortie avec des lignes de base dynamiques
* Pour obtenir la liste complète des améliorations apportées aux Guides d’AEM, reportez-vous à : [Nouveautés des AEM Guides](https://experienceleague.adobe.com/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2402-release/whats-new-2024-2-0.html?lang=en#release-info)

### Problèmes résolus {#fixed-issues-15262}

* ASSETS-15977 : Supprimez les événements de recherche v1 obsolètes et le producteur de pipeline.
* ASSETS-18088 : mettez à niveau les dépendances de bibliothèque batik vers la version 1.17.
* ASSETS-21965 : le workflow Écriture différée des métadonnées ne doit être lancé que lors des modifications apportées aux métadonnées des ressources.
* ASSETS-26368 : Les tâches d’importation en bloc planifiées ne sont pas supprimées si la configuration de la tâche n’existe pas.
* ASSETS-26549 : Ressources/noeuds avec &quot;jcr:lastModifiedBy&quot;: &quot;workflow-process-service&quot; s’affiche en tant qu’&quot;utilisateur externe&quot; en mode Liste.
* ASSETS-26842 : mettez à jour le texte &quot;Firefly&quot; pour qu’il lise &quot;Créateur d’applications&quot; dans le profil de traitement.
* ASSETS-28708 : réponse très lente pour certaines demandes de jeton IMS.
* ASSETS-28767 : état de publication incohérent sur les ressources si le dossier contenant un grand nombre de noms est vide. des ressources publiées.
* ASSETS-29011 : le recadrage intelligent est visible pour les utilisateurs en lecture seule.
* ASSETS-29348 : AssetMoveEventHandler peut consommer trop de mémoire.
* ASSETS-29738 : la restriction de chargement des ressources échoue avec NullPointerException pour les fichiers &quot;woff&quot;.
* ASSETS-30068 : Essentiels d’importation en bloc de ressources pour inclure l’état COMPLETED_WITH_ERROR pour &quot;tâche terminée, mais avec erreur&quot;.
* ASSETS-30261 : imsUserId incorrect envoyé au pipeline pour les événements de ressource.
* ASSETS-30538 : l’option Afficher la page est absente après le déplacement d’un fichier de PDF.
* ASSETS-30626 : échec de la création d’une demande de diffusion signalée pour les ressources avec assetId vide.
* ASSETS-30756 : l’action de l’assistant de déplacement des ressources échoue lorsque le nom du dossier se termine par &quot;html&quot;.
* ASSETS-30810 : assainissez les balises avant de générer la configuration YouTube héritée.
* ASSETS-31015 : impossible de charger les ressources avec l’extension de nom de fichier .msg.
* ASSETS-31038 : les événements de tâches reçus par le service de notification ne sont pas en cours de traitement.
* ASSETS-31097 : Désactivez la copie asynchrone pour le contenu WCM afin d’éviter les avertissements de requête transversale.
* ASSETS-31256 : Ressources/noeuds avec &quot;jcr:lastModifiedBy&quot;: &quot;workflow-process-service&quot; s’affiche en tant qu’&quot;utilisateur externe&quot; en mode Liste.
* ASSETS-31260 : le champ déroulant du formulaire de métadonnées de ressource ne fonctionne pas correctement lorsque le JSON de liste déroulante comporte une liste volumineuse.
* ASSETS-31280 : Effectuez le téléchargement des ressources dans une structure aplatie lorsqu’elles sont ajoutées à une collection.
* ASSETS-31301 : `dynamicmedia_sly.js` ne peut pas être correctement instancié par l’API Use.
* ASSETS-31330 : ko_KR : Chaînes non localisées dans les sous-titres et les pistes audio.
* ASSETS-31405 : le traitement du serveur d’InDesign échoue pour les mises en page d’InDesign volumineuses.
* ASSETS-31570 : Shell unifié - les détails de la ressource &quot;Enregistrer et fermer&quot;, les boutons &quot;Annuler&quot; doivent être enfoncés plusieurs fois pour fonctionner.
* ASSETS-31673 : l’importation en bloc a échoué pour les fichiers de Dropbox volumineux.
* ASSETS-32108 : AEM Assets n’enregistre pas la taille de carte définie par l’utilisateur dans les paramètres d’affichage.
* ASSETS-32230 : mettez à niveau la version d’exécution minimale du lot com.adobe.aem.repoapi.
* ASSETS-32544 : la tâche d’exportation des métadonnées échoue par intermittence.
* ASSETS-32679 : problèmes de mise en cache avec les aperçus de ressources (PDF).
* ASSETS-32754 : les tâches ne peuvent pas être affectées aux utilisateurs qui ne se sont pas connectés précédemment.
* ASSETS-32755 : configurez la rubrique de tâche com/adobe/cq/dam/assetmove pour utiliser une file d’attente ordonnée.
* ASSETS-32899 : la recherche dans les collections est extrêmement lente.
* ASSETS-33098 : Le &quot;prédicat Balises&quot; des facettes de recherche AEM Assets ne fonctionne pas comme prévu.
* ASSETS-33454 : l’activité Tâche de révision et les commentaires ne s’affichent pas dans la chronologie.
* ASSETS-34088 : l’aperçu du PDF ne fonctionne pas sur AEM Assets.
* ASSETS-34155 : Dynamic Media - Mise à jour AEM visionneuses / 2024.1.0.
* ASSETS-34684 : gérez dc:title à plusieurs valeurs dans l’arborescence de contenu.
* ASSETS-34789 : correction des problèmes de normalisation dans la vérification des conflits de nom de fichier.
* DXML-13276 : AEM Guides : intégrez les index dans GraniteContent et supprimez-les de la bibliothèque.
* GRANITE-47995 : les opérations de suppression peuvent échouer en raison de conflits avec la propriété &quot;cq:isDelivered&quot;.
* GRANITE-48079 : activez les demandes de POST pour la validation des jetons en ligne OAuth.
* GRANITE-48143 : Mettez à niveau org.apache.sling.resourcemerer vers la version 1.4.4 .
* GRANITE-49031 : Mise à jour à Jackson 2.16.1.
* SCRNS-3961 : Screens - canal de séquence : l’animation de la requête utilisée dans la transition Fondu mène à un écran noir.
* SITES-15868 : Améliorez les performances pour répertorier les fragments.
* SITES-16079 : `/fragments/{id}/references` a commencé à renvoyer des doublons.
* SITES-16118 : si un fragment est corrigé et qu’un champ de fragment est manquant dans le modèle, une exception est générée.
* SITES-16121 : la récupération d’un champ de date de modèle renvoie une exception.
* SITES-16207 : l’opération du POST /adobe/sites/cf/models renvoie deux codes d’état OK différents.
* SITES-17361 : réincorporez Jsoup dans le lot sans tête de sites.
* SITES-17768 : GraphQL pour générer l’URL Dynamic Media pour les ressources référencées dans les fragments de contenu.
* SKYOPS-66622 : blocage du déploiement de l’auteur après l’exécution d’un pipeline activé buildTransform.
* SKYOPS-69977 : Le servlet d’image adaptative ne charge pas l’image après la dernière mise à jour.
* GUIDES-15045 : La vérification orthographique dans l’éditeur n’autorise pas la sélection de suggestions.
* GUIDES-14968 : Le bouton de navigation globale ne fonctionne pas et le tableau de bord ne se charge pas.
* GUIDES-14943 : dans la publication avec PDF natif, les attributs personnalisés dans les paramètres prédéfinis de condition ne fonctionnent pas pour la publication avec PDF natif.
* GUIDES-15085 : dans la publication avec des PDF natifs, les références clés ne sont pas résolues pour la version de décembre 2023 des Guides Adobe Experience Manager.
* GUIDES-13486 : **Filtre de ligne de base** Les fichiers ne fonctionnent pas avec le nom de fichier dans l’éditeur web.
* Pour obtenir la liste complète des problèmes résolus dans AEM Guides, veuillez vous référer à : [Problèmes résolus dans AEM Guides](https://experienceleague.adobe.com/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2402-release/fixed-issues-2024-2-0.html?lang=en#release-info)

### Problèmes connus {#known-issues-15262}

Aucun.

### Avis de modification {#change-notice-15262}

**Action requise**

Les modifications à venir nécessiteront la bibliothèque . [aem-cloud-testing-clients](https://github.com/adobe/aem-testing-clients) utilisé dans vos tests fonctionnels personnalisés pour les mettre à jour vers au moins la version **1.2.1**

Assurez-vous que votre dépendance dans `it.tests/pom.xml` a été mis à jour.

```xml
<dependency>
   <groupId>com.adobe.cq</groupId>
   <artifactId>aem-cloud-testing-clients</artifactId>
   <version>1.2.1</version>
</dependency>
```

Cette modification sera requise après le 6 avril 2024.

Si vous ne mettez pas à jour la bibliothèque de dépendances, des échecs de pipeline se produiront à l’étape &quot;Tests fonctionnels personnalisés&quot;.

### Technologies intégrées {#embedded-tech-15262}

| Technologie | Version | Lien |
|---|---|---|
| AEM OAK | 1.60-T20240131102219-0cde853 | [API 1.60.0 Oak](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.60.0/index.html) |
| API SLING AEM | Version 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | Version 2.23.4 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
