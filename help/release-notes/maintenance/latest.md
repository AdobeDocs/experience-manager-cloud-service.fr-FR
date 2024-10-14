---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 6fa6fc9015624bec9113a198285531a3bdd7e29c
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 91%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 18175 {#release-18175}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 18175, publiée le vendredi 10 octobre 2024. La version de maintenance précédente était la version 17964. La version 18099 a été rendue privée en raison d’un problème.

L’activation des fonctionnalités de la version 2024.10.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-18175}

* ASSETS-38322 : activation de l’événement de requête HTTP pour AEM.
* ASSETS-41448 : mise à jour du lot auth.ims pour prendre en charge les mappages FI vers les groupes.
* ASSETS-41684 : ajout des configurations OSGI prêtes à l’emploi pour définir le mappage FI vers les groupes pour Assets, Foundation, Sites et Forms.
* ASSETS-43015 : mise à jour vers le dernier lot auth.ims.
* CQ-4356633 : ajout d’un caractère supplémentaire dans l’info-bulle « Contenu uniquement ».
* GRANITE-50948 : intégration du service de référentiel à la prise en charge AEM du service de référentiel.
* GRANITE-52454 : ajout de l’assistant de prise en charge 0.1.2.
* GRANITE-52454 : mise à niveau de l’assistant pour utiliser la dernière version d’AEMaaCS.
* GRANITE-53287 : mise à jour de la version de test d’intégration security-privileges.
* GRANITE-53485 : prise en charge de l’authentification de l’entité de sécurité du service pour la réplication du stockage Blob Azure.
* GRANITE-53514 : activation de l’arborescence mise à jour vers la version 1.0.26.
* GRANITE-53870 : création d’un mécanisme interne pour ignorer la vérification de version JVM maximale pour le démarrage rapide.
* GRANITE-53914 : correction des échecs de test de Platform avec Java 17 Mise à jour de la version du module.
* GRANITE-53966 : utilisation d’un pool de threads distinct pour la distribution de contenu.
* GRANITE-53453 : mise à jour de Jackson vers la version 2.17.2.
* GRANITE-54038 : ajout du client ou de la cliente IMS Enterprise Creative Cloud à la liste autorisée de clientes et clients IMS AEM.
* GRANITE-54054 : variable d’environnement pour com.adobe.granite.repository.impl.SystemUserValidation warnOnly.
* GRANITE-54266 : absence du service Search Suggestor du SDK de production.
* GRANITE-54274 : acceptation du client ou de la cliente IMS Firefly.
* GRANITE-54300 : mettre à jour Oak vers la dernière version publique (1.70.0).
* GUIDES-19069 : ajout de guidesPeerLinkIndex pour le module complémentaire AEM Guides.
* SITES-23584 : test de correction de l’échec du composant Foundation sur Java 17.
* SKYOPS-69768 : les modèles Sling ne désérialisent pas ResourceResolvers.
* SKYOPS-76378 : amélioration de la sécurité des threads de l’enregistrement/annulation de l’enregistrement de ResourceBundle dans i18n.
* SKYOPS-79285 : mise à jour de Sling XSS vers la version 2.4.2.
* SKYOPS-82383 : exposition du résultat « helm-values » convert-merge-analyse dans le descripteur d’exécution de la commande.
* SKYOPS-84810 : exécution de « 40-initialize-publish.sh » ignorée au démarrage pour RDE.
* SKYOPS-84951 : correction du code de génération de somme de contrôle du contenu mutable.
* SKYOPS-68091 : mise à jour de org.apache.sling.jcr.repoinit vers la version 1.1.52.
* SKYOPS-82660 : mise à jour de Sling Commons Threads vers la version 3.3.0.
* SKYOPS-86329 : mise à jour des versions des modules de test de plateforme pour la prise en charge du SDK Java 21.

### Problèmes résolus {#fixed-issues-18175}

* CNTBF-298 : suppression de jcr:uuid des packages exportés par CC.
* SKYOPS-83910 : correction des problèmes de simultanéité détectés dans SKYOPS-82371.
* GRANITE-52876 : mise à jour vers com.adobe.granite.ui.content 0.8.1448.
* GUIDES-14445 : la génération du PDF natif échoue avec une erreur liée à l’obtention des dépendances pour Node.js.
* GUIDES-16961 : le titre avec `<conref>` ne se résout pas dans les tableaux de bord de référence et de traduction de l’éditeur web.
* GUIDES-17283 : lorsque vous sélectionnez l’option **Utiliser les métadonnées ajoutées dans l’élément topicmeta**, les propriétés de métadonnées ne sont pas propagées dans les propriétés de document de la sortie de PDF natif.
* GUIDES-17793 : le PDF référencé n’est pas activé à partir du **tableau de bord de publication en masse** lors de l’activation en masse du contenu publié.

Pour plus d’informations sur les fonctionnalités nouvelles et améliorées de Guides, ainsi que sur les problèmes résolus dans la version, consultez la [Feuille de route des versions d’Experience Manager Guides](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Problèmes connus {#known-issues-18175}

* FORMS-15818 : entrée du descripteur de composant `OSGI-INF/com.adobe.aemfd.docmanager.impl.*.xml` introuvable dans les journaux de serveur. Ce sont des instructions de journal inoffensives.

### Fonctionnalités et API obsolètes {#deprecated-18175}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées ](/help/release-notes/deprecated-removed-features.md).

Vous trouverez ci-après un récapitulatif des fonctionnalités devenues ou en passe de devenir obsolètes.

#### API JavaScript Use {#javascript-use-api}

[L’API JavaScript Use](https://github.com/adobe/htl-spec/blob/master/SPECIFICATION.md#42-javascript-use-api) est désormais considérée comme obsolète, notamment en raison des difficultés de débogage et de maintenance du code par les utilisateurs et les utilisatrices ainsi que de ses limites de performances face à l’alternative Java.

Utilisez à la place [l’API Java Use](https://experienceleague.adobe.com/fr/docs/experience-manager-htl/content/java-use-api) qui offre de meilleures performances, un débogage plus facile et une prise en charge plus étendue à long terme.

#### com.day.cq.wcm.api {#com-day-cq-wcm-api}

Notez qu’Adobe procède actuellement à la mise à jour de `com.day.cq.wcm.api`. Certaines de ses méthodes et classes ont été déclarées `@Deprecated` dans la version actuelle. Elles seront supprimées dans les prochaines versions. Envisagez d’adopter les alternatives recommandées.

#### org.apache.jackrabbit.oak.plugins.blob {#org.apache.jackrabbit.oak.plugins.blob}

* GRANITE-54165 : org.apache.jackrabbit.oak.plugins.blob obsolète dans l’API publique.

### Correctifs de sécurité {#security-18175}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 2 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-18175}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.70.0 | [API Oak 1.70.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.70.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.27.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
