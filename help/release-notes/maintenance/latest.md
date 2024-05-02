---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 79dcf8a4e9834beeb466ed9270a3f5c6aa67aa9a
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 29%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 16145 {#release-16145}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 16145, rendue publique le jeudi 1 mai 2024. La version de maintenance précédente était la version 15977.

L’activation des fonctionnalités de la version 2024.4.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-16145}

* ASSETS-23489 : améliorations des informations du référentiel.
* ASSETS-26926 : Améliorations de l’interrogation du téléchargement Dynamic Media.
* ASSETS-30351 : la boîte de dialogue Télécharger doit charger les tailles de rendu Dynamic Media de manière asynchrone.
* ASSETS-30379 : Améliorer la résolution des licences DRM en téléchargement.
* ASSETS-31058 : Reportez les rendus de recadrage intelligent dans AEM interface utilisateur des ressources dans l’onglet Rendus et générez des images recadrées intelligentes lorsque l’utilisateur clique sur ces rendus.
* ASSETS-31218 : Ajoutez la prise en charge du recadrage intelligent nommé dans l’api de diffusion des ressources.
* ASSETS-31979 : Ajoutez un indicateur visuel et désactivez les fonctions de l’interface utilisateur lors des opérations Async Assets.
* ASSETS-32735 : améliorations apportées à l’événement de métadonnées de ressource mis à jour.
* ASSETS-34661 : API pour l’aperçu DM et/ou les URL de diffusion à partir d’AEMaaCS Publish.
* ASSETS-37259 : XMP améliorations de l’analyse.
* ASSETS-37263 : Autorisez l’annulation des tâches asynchrones Assets en échec.
* CNTBF-114 : Améliorations du retour de contenu.
* CNTBF-148 : Améliorations du retour de contenu.
* CQ-4356992 : Dernières AEM et dernières traductions Granite.
* SITES-19326 : mise à jour de liens dans l’interface utilisateur d’Assets pour ouvrir des fragments de contenu (CF) dans le nouvel éditeur de fragments de contenu.
* SITES-20686 : GraphQL - Exposez l’URL Dynamic Media via _dmS7Url (pour les ressources autres que les images).
* SKYOPS-68091 : mise à jour vers Java 11.0.20.

### Problèmes résolus {#fixed-issues-16145}

* ASSETS-32321 : la résolution du workflow de post-traitement échoue si le sous-noeud &quot;jcr:content&quot; est absent du dossier ancêtre.
* ASSETS-33856 : le fichier de paramètres d’image prédéfinis du JPEG est téléchargé au format TXT.
* ASSETS-34096 : Fix Touch UI view for async download report.
* ASSETS-34493 : échec lors du chargement de la boîte de dialogue de téléchargement après activation du basculement de fonctionnalités multi-entreprise.
* ASSETS-34824 : l’URL de copie s’affiche vide pour les dossiers DM désactivés.
* ASSETS-35226 : le workflow de post-traitement n’est pas résolu s’il est spécifié à la racine DAM.
* ASSETS-35559 : réduisez le journal des erreurs de transfert par lots DM à WARN.
* ASSETS-35860 : Conversion de fuseau horaire incorrecte dans la vue Colonne d’AEM Assets.
* ASSETS-35935 : navigation du dossier incorrecte après la fermeture de la révision de la payload.
* ASSETS-35961 : le bouton Ajouter un recadrage ne fonctionne pas sous le profil d’image.
* ASSETS-36227 : Désactivez le service FolderPreviewUpdaterImpl lors de la publication.
* ASSETS-36943 : colonnes alignées manquées lorsque des éléments CF et d’autres éléments non CF sont présents dans un dossier en mode Liste.
* ASSETS-36990 : les tâches de métadonnées exportées échouent/ralentissent avec un grand nombre de propriétés.
* ASSETS-37113 : la tâche de retraitement des ressources se termine immédiatement si la requête renvoie uniquement les résultats des FC.
* ASSETS-37260 : L’exportation de métadonnées dans AEM peut produire un fichier CSV non valide.
* ASSETS-37261 : problème d’annotation PPTx et PDF sur AEM Assets.
* ASSETS-37282 : demande lente potentielle ouvrant un dossier volumineux.
* ASSETS-37330 : L’importation en bloc à partir de OneDrive crée une structure de dossiers AEM incorrecte.
* ASSETS-37609 : Supprimez la recherche de conf scene7 héritée.
* ASSETS-38016 : Certaines mises à jour de métadonnées ne sont pas correctement suivies dans les événements.
* CQ-4357161 : L’écran AEM charge utile de boîte de réception renvoie 404.
* GRANITE-50041 : l’option Ajouter le rendu ne fonctionne pas lorsque la résolution est supérieure à 1 440 px lorsque seule l’option &quot;Ajouter le rendu&quot; figure dans la liste déroulante.
* GRANITE-50279 : noms de semaine non classés dans le composant de sélecteur de date Coral.
* SCRNS-3949 : le délai de demande de récupération du canal Screens est trop long.
* SCRNS-3981 : [Canal de séquence] Un écran noir se produisait lorsque la séquence d’événements de chargement/déchargement d’élément était déformée.
* SCRNS-4180 : [Canal de séquence] La séquence s’arrête avec un écran vierge pour les canaux avec des vidéos de durée -1 lors de la récupération de la miniature de secours.
* SCRNS-4245 : [Canal de séquence] Durée limitée de l’écran vierge lorsqu’une vidéo est chargée et basculée à partir de la miniature de secours.
* SITES-16055 : correction des liens Source Live Copy et Live Copy dans la page des propriétés respectives.
* SCRNS-4243 : Boutons manquants dans le fournisseur de contenu pour les utilisateurs non-administrateurs.

### Problèmes connus {#known-issues-16145}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-16145}

* [Obsolescence des informations d’identification JWT dans Adobe Developer Console](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md)

* À compter du 1er mai 2024, Adobe Dynamic Media ne prendra plus en charge les éléments suivants :

   * SSL (Secure Socket Layer) 2.0
   * SSL 3.0
   * TLS (Transport Layer Security) 1.0 et 1.1
   * Les chiffrements faibles suivants dans TLS 1.2 :
      * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384`
      * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA`
      * `TLS_RSA_WITH_AES_256_GCM_SHA384`
      * `TLS_RSA_WITH_AES_256_CBC_SHA256`
      * `TLS_RSA_WITH_AES_256_CBC_SHA`
      * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256`
      * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA`
      * `TLS_RSA_WITH_AES_128_GCM_SHA256`
      * `TLS_RSA_WITH_AES_128_CBC_SHA256`
      * `TLS_RSA_WITH_AES_128_CBC_SHA`
      * `TLS_RSA_WITH_CAMELLIA_256_CBC_SHA`
      * `TLS_RSA_WITH_CAMELLIA_128_CBC_SHA`
      * `TLS_ECDHE_RSA_WITH_3DES_EDE_CBC_SHA`
      * `TLS_RSA_WITH_SDES_EDE_CBC_SHA`


Pour savoir ce qui est obsolète ou supprimé dans AEM as a Cloud Service, voir [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Technologies intégrées {#embedded-tech-16145}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.62.0 | [API Oak 1.62.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.62.0/index.html) |
| API SLING AEM | 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.20-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.24.6 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
