---
title: Migration vers le Experience Manager en tant que Cloud Service
description: Migration vers le Experience Manager en tant que Cloud Service
translation-type: tm+mt
source-git-commit: 3c1ff52d58f64d351507d20e4368a6aeb1bf6339
workflow-type: tm+mt
source-wordcount: '2070'
ht-degree: 12%

---


# Migration vers Adobe Experience Manager en tant que Cloud Service {#Overview}

>[!CONTEXTUALHELP]
>id="aemcloud_migration-overview"
>title="Migration vers AEM en tant que service cloud"
>abstract="Présente l’approche échelonnée recommandée pour les clients de transition de divers déploiements de Experience Manager vers le Experience Manager en tant que Cloud Service et aide les clients existants à fournir des expériences connectées et continues"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html?lang=en" text="Quoi de neuf et de différent ?"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=en" text="Présentation d’AEM as a Cloud Service."

Adobe Experience Manager (AEM), en tant qu’offre Cloud Service, est une fondation réarchitectée pour Experience Manager, construite sur une infrastructure basée sur le conteneur, un développement piloté par les API et un processus DevOps guidé, permettant aux marketeurs et aux développeurs de toujours garder une longueur d’avance sur les innovations de gestion de l’expérience client.

Cloud Service rassemble de riches capacités prêtes à l&#39;emploi et l&#39;extensibilité de Adobe Experience Manager avec l&#39;agilité de l&#39;architecture moderne native de cloud permettant aux marques de répondre à la demande toujours croissante des consommateurs.

Cette pagination unique décrit l&#39;approche échelonnée recommandée pour les clients transitions, depuis divers déploiements de Experience Manager jusqu&#39;à Experience Manager en tant que Cloud Service, et aide les clients existants à fournir des expériences connectées et continues sur cette plateforme moderne et personnalisée pour la gestion de l&#39;expérience.

<!-- It primarily focuses on:
* Getting Started with Adobe Experience Manager as a Cloud Service
* Developer Journey in Adobe Experience Manager as a Cloud Service
* Moving to Adobe Experience Manager as a Cloud Service -->

<br>

## Prise en main de Adobe Experience Manager en tant que Cloud Service {#getting-started}

| Qu&#39;y a-t-il de différent ? | Aperçu de l’architecture |
|--------------------------|--------------------------|
| <ul><li>[Architecture moderne](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/core-concepts/architecture.html)</li><li>[Mises à jour automatiques](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/aem-version-updates.html?lang=en#aem-version-updates)</li><li>[Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)</li><li>[Services de microressources](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/asset-microservices-overview.html)</li><li>[Binaires DirectAccess](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/asset-microservices-overview.html?lang=en#asset-upload-with-direct-binary-access)</li><li>[Séparation du code et du contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=en#developing)</li><li>[Réplication en tant que service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/replication.html?lang=en)</li><li>[Console d’administration, Appartenance à un groupe/utilisateur et liste de contrôle d’accès](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html)</li></ul> | <ul><li>[Présentation de l&#39;architecture AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-architecture.html?lang=en#underlying-technology)</li><li>[Environnement empilé](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/core-concepts/architecture.html)</li><li>[Niveau de création](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html?lang=en#underlying-technology)</li><li>[Niveau de publication](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html?lang=en#underlying-technology)</li><li>[Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=en#content-delivery)</li><li>[Réseau de diffusion de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/cdn.html?lang=en#content-delivery) </li><li>[Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)  (CI/CD)</li><li>[Gestion des ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=en#onboarding-users-in-admin-console) identités via la console  [d’administration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html)</li><li>[Asset Compute Service](https://experienceleague.adobe.com/docs/asset-compute/using/home.html)</li></ul> |

![AEM as a Cloud Service - Architecture d’exécution](/help/core-concepts/assets/concepts-03.png "AEM as a Cloud Service - Architecture d’exécution")

<br>

## Voyage du développeur à Adobe Experience Manager en tant que Cloud Service {#developer-journey}

### Développement

Les fondamentaux du développement du code sont similaires à Adobe Experience Manager en tant que Cloud Service par rapport aux solutions Adobe Experience Manager On Premise et Managed Services.

Les développeurs écrivent du code et le testent localement, qui est ensuite envoyé à Adobe Experience Manager distant en tant qu&#39;environnements Cloud Service.

Consultez des ressources d’auto-assistance sur la mise en oeuvre pour le Experience Manager en tant que Cloud Service pour savoir comment personnaliser votre Experience Manager en tant que déploiement Cloud Service.

| Configuration du développement local | Les choses à savoir avant votre début |
|-----------|------------|
| <ol><li>Consultez la documentation [Adobe Experience Manager SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#developing) pour en savoir plus.</li><li>Regardez [Installer le SDK du répartiteur](https://video.tv.adobe.com/v/30601?captions=fre_fr) pour comprendre comment installer le SDK du répartiteur.</li><li>Regardez [Configurer le SDK du répartiteur](https://video.tv.adobe.com/v/30602?captions=fre_fr) pour comprendre comment configurer le SDK du répartiteur.</li><li>Consultez la documentation [Configuration du développement local](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=en#local-development-environment-set-up) pour en savoir plus</li><li>Configuration de l’accès au Experience Manager [workflow](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=en#accessing)</li></ol> | <ol><li>[Essentiels de développement](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#developing)</li><li>[Conseils de développement ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#developing)</li><li>[Présentation de la structure du projet Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=en#developing)</li><li>[Composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)</li><li>[Plan directeur de Digital Foundation](https://solutionpartners.adobe.com/content/dam/spp_assets/restricted/community/community_31/digital_foundation_best_practices_and_documentation.zip)</li><li>[Système de style](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/features/style-system.html?lang=en#authoring)</li><li>[Recouvrements](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/overlays.html?lang=en#developing)</li><li>[Experience Manager en tant que référence d’API Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/)</li></ol> |

>[!TIP]
> Voir le didacticiel sur la façon de [développer et déployer WKND sur le SDK Experience Manager local](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=en).

### Déploiement

Les développeurs écrivent du code et le testent localement. Il est ensuite envoyé vers les environnements distants AEM as a Cloud Service.

Cloud Manager, qui était un outil de diffusion de contenu facultatif pour Managed Services, est requis. Il s’agit désormais du seul mécanisme permettant de déployer du code vers les environnements AEM as a Cloud Service.

Consultez les ressources d’auto-assistance sur la configuration et le déploiement en tant qu’environnements Cloud Service pour AEM.

1. [Configurer les pipelines CM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en#using-cloud-manager)
   * Pipeline de production
   * Pipelines de qualité de code et hors production uniquement
2. [Déploiement du code](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#using-cloud-manager)
3. [Présentation des résultats du test](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/overview-test-results.html?lang=en#using-cloud-manager)
4. **Accès aux journaux**
   * [via l’interface utilisateur de CM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html?lang=en#using-cloud-manager)
   * [via Adobe i/o cli](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=en#debugging)
5. [Exploitation et maintenance](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/home.html?lang=en)
   * [Configuration d’OSGI](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#deploying)
   * [Sauvegarde et restauration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/backup.html?lang=en)

>[!TIP]
> Voir le didacticiel sur la façon de [déployer WKND en Experience Manager Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/develop-wknd-tutorial.html?lang=en).

### Aide et ressources

1. [Conseils et astuces sur le débogage](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/overview.html?lang=en#debugging-aem-as-a-cloud-service)
2. [Developer Console](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=en#debugging)
3. [CRXDE Lite](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/crxde-lite.html?lang=en#debugging) (Disponible uniquement sur les environnements de développement SDK et Cloud Experience Manager locaux)
4. [Journaux et journalisation](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=en#debugging)
   * [Journaux](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html?lang=en#debugging)  CM (test de build-unit, analyse de code, image de build, déploiement)
   * [Journaux](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=en#debugging)  du Experience Manager Cloud Service (aemerror, aemaccess, aemrequest, aemdispatcher, httpderror, httpaccess)
   * Journaux du SDK local (sous host:port/crx-quickstart/logs)

>[!NOTE]
> Pour obtenir une aide supplémentaire, vous pouvez :
>1. [Contactez l&#39;équipe d&#39;assistance Experience Manager](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=en)
>2. Explorez [Communautés et forums Experience Manager](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community)


<br>

## Déplacement vers Adobe Experience Manager en tant que Cloud Service {#move-to-cloud}

**Experience Manager en tant que Cloud Service fournit une base technologique évolutive, sécurisée et agile pour les sites et ressources Experience Manager, ce qui permet aux spécialistes du marketing et de l’informatique de se concentrer sur la diffusion à grande échelle d’expériences performantes.**

Avec le Experience Manager en tant que Cloud Service, vos équipes peuvent se concentrer sur l&#39;innovation plutôt que sur la planification de la mise à niveau des produits. Les nouvelles fonctionnalités du produit sont soigneusement testées et mises en permanence à la disposition de vos équipes, qui ont toujours accès à l’application la plus avancée.

Le parcours de transition vers Cloud Service comprend trois phases : planification, exécution et post-activation.
Pour une transition réussie et fluide, vous devez veiller à une planification adéquate et respecter les bonnes pratiques décrites du présent guide.

La figure ci-dessous est une représentation graphique du parcours recommandé de transition vers Cloud Service.

![image](/help/move-to-cloud-service/assets/home-img1.png)

<br>

### Planification

Avant de commencer votre voyage de transition vers le Cloud Service, vous devez vous familiariser avec le Experience Manager en tant que Cloud Service et examiner les modifications notables qui y ont été apportées et examiner également les fonctions qui ont été remplacées ou abandonnées.

<table>
<tr>
<td>Découverte et évaluation des projets</td>
<td><ul><li>Voir <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/aem-cloud-changes.html?lang=en">Modifications notables apportées au Experience Manager en tant que Cloud Service</a> pour comprendre les différences importantes entre Adobe Experience Manager en tant que Cloud Service et Experience Manager 6.x.</li><li>Consultez <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/deprecated-removed-features.html?lang=en#deprecated-features">Fonctionnalités obsolètes</a> pour en savoir plus sur les fonctionnalités qui ont été marquées comme obsolètes.</li><li>[Pour les migrations de Cloud Service uniquement] Évaluer la préparation des Cloud Service : Exécutez <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration">Best Practices Analyzer (BPA)</a> sur l’environnement source. </li><li>Effectuez une évaluation en fonction des modifications notables et des fonctionnalités obsolètes dans la CS Experience Manager.</li></ul></td>
</tr>
<tr>
<td>Réviser</td>
<td><ul><li>En fonction de la découverte, effectuer des exercices d'estimation de l'effort et de ressourcement</li></ul></td>
</tr>
<tr>
<td>Mesure</td>
<td><ul><li><a href="https://experienceleague.adobe.com/welcome/aem/part6.html">Définition des IPC</a> du projet, des critères de réussite et des calendriers du projet</li></ul></td>
</tr>
</table>

>[!NOTE]
>Le rapport Analyseur des meilleures pratiques accélère le processus d’estimation du temps et du coût requis pour la transition à l’AEM en tant que Cloud Service en fournissant des informations qui autrement devraient être collectées et évaluées manuellement.


<br>

### Exécution

Avant de début de la phase d&#39;exécution d&#39;un projet, vous devez être inscrit au Cloud Service. Vous devez également vous familiariser avec Cloud Manager. Il s’agit du mécanisme de déploiement du code de projet sur une instance de Experience Manager Cloud Service.

Cloud Manager permet aux entreprises de gérer elles-mêmes les Experience Manager dans le Cloud. Il comprend une intégration continue et une diffusion continue ([CI/CD](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/overview/ci-cd-pipeline.html?lang=en#overview)) qui permet aux équipes informatiques et aux partenaires d&#39;implémentation d&#39;accélérer la diffusion des personnalisations ou des mises à jour sans compromettre les performances ou la sécurité.

#### Migration du contenu

1. [Outil](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=en#migration)  de transfert de contenu : permet de déplacer du contenu existant d’une instance d’AEM source (sur site ou AMS) vers l’instance d’Cloud Service d’cible AEM.
2. [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en#package-manager)  : utilisé pour importer et exporter du contenu modifiable du référentiel.


#### Refacer/Optimiser

| Prise en main | Révision et reformage du code | Révision du répartiteur |
|---|---|---|
| <ul><li>[Configuration du développement local](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=en#local-development-environment-set-up)</li><li>[Configuration du répartiteur local](https://video.tv.adobe.com/v/30602/?captions=fre_fr)</li><li>[Compiler votre code à l’aide du fichier JAR de l’API SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#developing)</li><li>[Revoir les directives AEM développement](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#developing)<ul><li>Tâches en arrière-plan et tâches à long terme</li><li>Planificateurs Sling</li><li>Utilisation du flux d’entrée et plus</li></ul></li></ul> | <ul><li>Exécutez l&#39;[analyseur des meilleures pratiques (BPA)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration) sur l&#39;environnement source.[**Migration uniquement**]<ul><li>Considérations relatives à la structure du projet (basées sur [l’archétype du cloud](https://github.com/adobe/aem-project-archetype))<ul><li>Séparation du code et du contenu (Mutable ou Immuable)</li><li>[Définitions d’index personnalisées](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#indexing)</li><li>[Modes d’exécution personnalisés](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=en#runmodes)</li></ul></li></ul></li><li>Révision et exécution des modifications nécessaires</li><li>[](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=en) Déploiement sur le SDK local</li><li>Effectuer des tests de fumée via AEM SDK</li></ul> | <ul><li>Examiner [les configurations du répartiteur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=en#local-validation-of-dispatcher-configuration) pour la refactorisation</li><li>Utilisez l&#39;outil [Convertisseur répartiteur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/dispatcher-transformation-utility-tools.html?lang=en#introduction-dispatcher), le cas échéant. [**Migration uniquement**]</li><li>Les tests peuvent être effectués à l&#39;aide du [SDK du répartiteur](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html?lang=en#prerequisites)</li></ul> |

>[!TIP]
> Clients Ressources : Révisez et refacturez les Workflows de ressources à l’aide de l’[outil de migration d’Asset Cloud](https://github.com/adobe/aem-cloud-migration)


#### Déploiement/Go-Live

1. [Déploiement sur Cloud ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/setup-cloud-manager-git-integration.html?lang=en#managing-code) Managergit
2. Exécutez le code client via le [pipeline de qualité de Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use).
3. [Déploiement sur l’Environnement de développement](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html?lang=en#debugging)
4. [**Migration**] uniquementTransfert de contenu à l’aide de packages ou de l’outil [ de transfert de ](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md)contenu (CTT)
5. Exécuter les cycles d&#39;essai recommandés (fumée, contrôle qualité, etc.)
6. Promouvoir dans le pipeline de production de Cloud Manager
7. Validation du test de fumée
8. Activation

<br>

### Post Go-Live

Lors de la phase de post-activation, vous devez veiller à nettoyer les fichiers temporaires, revoir les bonnes pratiques de développement continu et gérer les journaux.

>[!TIP]
> Des outils sont disponibles pour dépanner AEM en tant qu&#39;environnements Cloud Service
>1. [Console développeur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#aem-as-a-cloud-service-development-tools)
>2. [CRX/DE Lite](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/crxde-lite.html?lang=en#debugging)
>3. [Gestion des journaux](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html?lang=en#using-cloud-manager)


<br>

### Outils et ressources

| Évaluation | Réfactorisation | Modernisation des Experience Manager | Migration du contenu |
|------------|-------------|---------------------------------|-------------------|
| <ul><li>[Analyseur des meilleures pratiques](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration)</li></li> | <ul><li>[Module externe Expérience unifiée](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=en#refactoring-tools)</li></ul> | <ul><li>[Les modèles statiques en modèles modifiables](https://opensource.adobe.com/aem-modernize-tools/pages/tools/page-structure.html)</li><li>[Les configurations de la conception en stratégies](https://opensource.adobe.com/aem-modernize-tools/pages/tools/policy-importer.html) <li>[Les composants de base en composants principaux](https://opensource.adobe.com/aem-modernize-tools/pages/tools/component.html)</li><li>[L’interface utilisateur classique en interface utilisateur tactile](https://opensource.adobe.com/aem-modernize-tools/pages/tools/dialog.html)</li></ul> | <ul><li>[Outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#cloud-migration)</li><li>[le gestionnaire de modules](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en#contentmanagement)</li></ul> |

>[!NOTE]
> Pour obtenir une aide supplémentaire, vous pouvez :
>1. [Contactez l&#39;équipe d&#39;assistance Experience Manager](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=en)
>2. Explorez [Communautés et forums Experience Manager](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community)

