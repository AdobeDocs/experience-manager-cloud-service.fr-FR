---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: ea7e027b5247b64e78da1d14e4e602f39a37e4bd
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 39%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 18099 {#release-18099}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 18099, publiée le jeudi 9 octobre 2024. La version de maintenance précédente était la version 17964.

L’activation des fonctionnalités de la version 2024.10.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-18099}

* ASSETS-43015 : mise à jour vers le dernier lot auth.ims.
* ASSETS-41684 : Mise à jour src/main/features/docker/ethos/base-ims-oauth.json.
* ASSETS-38322 : activation de l’événement de requête http pour AEM.
* ASSETS-41684 : ajoutez des configurations OSGI OOB pour définir le mappage FI pour les groupes pour Assets, Foundation, Sites et Forms.
* ASSETS-41448 : mettez à jour le lot auth.ims pour prendre en charge les mappages FI pour les groupes.
* CQ-4356633 : ajoutez un caractère supplémentaire dans l’info-bulle &quot;Contenu uniquement&quot;.
* SITES-23584 : les tests des composants de base échouent sur Java 17.
* GUIDES-19069 : ajout de guidesPeerLinkIndex pour le module complémentaire guides aem.
* GRANITE-54300 : mettre à jour Oak vers la dernière version publique (1.70.0).
* GRANITE-54274 : Acceptez le client IMS Firefly.
* GRANITE-36205 : mettez à jour la version interne de oak vers la dernière version.
* GRANITE-45298 : Un utilisateur pauvre et privilégié peut obtenir un RCE en créant un formulaire malveillant sans JS mais à la manière de XSS.
* GRANITE-54266 : absence du service Search Suggestor du SDK de production.
* GRANITE-50948 - Intégrer le service de référentiel dans AEM Ajouter un service de référentiel alternatif pour le développement local.
* GRANITE-53966 : utilisez un pool de threads distinct pour la distribution de contenu.
* GRANITE-53514 : Treeactivation 1.0.26.
* GRANITE-54054 : variable d’environnement pour com.adobe.granite.repository.impl.SystemUserValidation warnOnly.
* GRANITE-50948 : Intégrez le service de référentiel à la prise en charge AEM du service de référentiel.
* GRANITE-52454 : Ajout de l’assistance d’assistance 0.1.2.
* GRANITE-53514 : Treeactivation 1.0.26.
* GRANITE-54038 : Ajoutez le client IMS Enterprise Creative Cloud à la liste autorisée de client IMS AEM.
* GRANITE-36205 : mettez à jour la version interne de oak vers la dernière version.
* GRANITE-53485 : Authentification de l’entité de sécurité du service de prise en charge pour la réplication du stockage Azure Blob.
* GRANITE-54006 : mettez à jour Jackson vers 2.17.2.
* GRANITE-53287 : mise à jour de la version de test d’intégration security-rights.
* GRANITE-53914 : Échec des tests de plateforme avec Java 17 Mise à jour de la version du module.
* GRANITE-53870 : créez un mécanisme interne pour ignorer la vérification de version maximale de la JVM pour le démarrage rapide.
* GRANITE-52454 : Aide à la mise à niveau de l’assistance d’assistance GRANITE-52454 Aide à la mise à niveau pour utiliser la dernière version d’AEMaaCS.
* SKYOPS-85335 : Mettez à jour org.apache.sling.jcr.repoinit vers la version 1.1.52.
* SKYOPS-85336 : Mise à jour de Sling Commons Threads vers la version 3.3.0.
* SKYOPS-76378 : amélioration de la sécurité des threads de l’enregistrement/de la désinscription de ResourceBundle dans i18n.
* SKYOPS-84951 : le code de génération de somme de contrôle du contenu mutable est incorrect.
* SKYOPS-82383 : Exposez le résultat &#39;helm-values&#39; convert-merge-analyse dans le descripteur d’exécution de la commande.
* SKYOPS-86329 : mise à jour des versions des modules de test de plateforme pour la prise en charge du sdk java 21.
* SKYOPS-69768 : les modèles Sling ne désérialisent pas ResourceResolvers.
* SKYOPS-84810 : ignore l’exécution &quot;40-initialize-publish.sh&quot; au démarrage pour RDE.
* SKYOPS-79285 : mise à jour de Sling XSS vers la version 2.4.2

### Problèmes résolus {#fixed-issues-18099}

* CNTBF-298 : Supprimez jcr:uuid des packages exportés par CC.
* SKYOPS-83910 : correction des problèmes de simultanéité détectés dans SKYOPS-82371.
* GRANITE-52876 : Mise à jour vers com.adobe.granite.ui.content 0.8.1448.
* GRANITE-53088 : régression introduite par le correctif de SITES-11992.
* GUIDES-14445 : la génération du PDF natif échoue avec une erreur liée à l’obtention des dépendances pour Node.js.
* GUIDES-16961 : le titre avec `<conref>` ne se résout pas dans les tableaux de bord de ligne de base et de traduction de l’éditeur web.
* GUIDES-17283 : lorsque vous sélectionnez l’option **Utiliser les métadonnées ajoutées dans la topicmeta** , les propriétés de métadonnées ne sont pas propagées dans les propriétés de document de la sortie de l’PDF natif.
* GUIDES-17793 : le PDF référencé n’est pas activé à partir du **tableau de bord Bulk Publish** lors de l’activation en masse du contenu publié.

Pour plus d’informations sur les nouvelles fonctionnalités et problèmes de Guides améliorés résolus dans la version, consultez la [feuille de route de la version de Experience Manager Guides](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Problèmes connus {#known-issues-18099}

* FORMS - 15818 : entrée du descripteur de composant `OSGI-INF/com.adobe.aemfd.docmanager.impl.*.xml` introuvable dans les journaux de serveur. Ce sont des instructions de journal inoffensives.

### Fonctionnalités et API obsolètes {#deprecated-18099}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées ](/help/release-notes/deprecated-removed-features.md).

Vous trouverez ci-après un récapitulatif des fonctionnalités devenues ou en passe de devenir obsolètes.

#### API JavaScript Use {#javascript-use-api}

[L’API JavaScript Use](https://github.com/adobe/htl-spec/blob/master/SPECIFICATION.md#42-javascript-use-api) est désormais considérée comme obsolète, notamment en raison des difficultés de débogage et de maintenance du code par les utilisateurs et les utilisatrices ainsi que de ses limites de performances face à l’alternative Java.

Utilisez à la place [l’API Java Use](https://experienceleague.adobe.com/fr/docs/experience-manager-htl/content/java-use-api) qui offre de meilleures performances, un débogage plus facile et une prise en charge plus étendue à long terme.

#### com.day.cq.wcm.api {#com-day-cq-wcm-api}

Notez qu’Adobe procède actuellement à la mise à jour de `com.day.cq.wcm.api`. Certaines de ses méthodes et classes ont été déclarées `@Deprecated` dans la version actuelle. Elles seront supprimées dans les prochaines versions. Envisagez d’adopter les alternatives recommandées.

#### org.apache.jackrabbit.oak.plugins.blob {#org.apache.jackrabbit.oak.plugins.blob}

* GRANITE-54165 : org.apache.jackrabbit.oak.plugins.blob obsolète dans l’API publique.

### Correctifs de sécurité {#security-18099}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 2 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-18099}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.70.0 | [API Oak 1.70.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.70.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.27.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
