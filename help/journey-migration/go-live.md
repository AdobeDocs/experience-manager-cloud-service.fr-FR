---
title: Activation
description: Découvrez comment effectuer la migration une fois que le code et le contenu sont prêts pour le cloud
source-git-commit: bcbf4e4ba1330bef9f2c8c473419903e40ac0e58
workflow-type: tm+mt
source-wordcount: '1342'
ht-degree: 4%

---


# Activation {#go-live}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_prep"
>title="Préparation de l’activation"
>abstract="Pour garantir une activation fluide et réussie d’AEM as a Cloud Service, vous devez prévoir des périodes de gel du code et du contenu, des itérations de test, des compléments de contenu, des tests de performance, des tests de sécurité, etc."

Dans cette partie du parcours, vous apprendrez à planifier et à effectuer la migration une fois que le code et le contenu sont prêts à être déplacés vers AEM as a Cloud Service. En outre, vous découvrirez les bonnes pratiques et les limites connues lors de la migration.

## Un peu d’histoire...  {#story-so-far}

Dans les phases précédentes du parcours :

* Vous avez appris à vous familiariser avec le déplacement vers AEM as a Cloud Service dans la [Prise en main](/help/journey-migration/getting-started.md) page.
* Déterminé si votre déploiement est prêt à être déplacé dans le cloud en lisant la variable [Phase de préparation](/help/journey-migration/readiness.md)
* Familiarisez-vous avec les outils et le processus grâce auxquels vous pouvez préparer votre code et votre cloud de contenu à l’ [Phase de mise en oeuvre](/help/journey-migration/implementation.md).

## Objectif {#objective}

Ce document vous aidera à comprendre comment effectuer la migration vers AEM as a Cloud Service une fois que vous connaissez les étapes précédentes du parcours. Vous apprendrez à effectuer la migration de production initiale ainsi que les bonnes pratiques à suivre lors de la migration vers AEM as a Cloud Service.

## Migration initiale de la production {#initial-migration}

Avant d’effectuer la migration de production, suivez les étapes de configuration et de preuve de migration décrites dans la section [Stratégie de migration de contenu et chronologie](/help/journey-migration/implementation.md##strategy-timeline) de la section [Phase de mise en oeuvre](/help/journey-migration/implementation.md).

* Lancez la migration à partir de la production en fonction de l’expérience que vous avez acquise lors de la migration à l’étape as a Cloud Service AEM effectuée sur les clones :
   * Auteur-Auteur
   * Publier-Publier

>[!NOTE]
>
>L’auteur AEM as a Cloud Service s’affiche pendant l’ingestion, mais AEM publication as a Cloud Service s’affiche pendant l’ingestion.

* Validez le contenu ingéré aux niveaux de création et de publication as a Cloud Service AEM.
* Demandez à l’équipe de création de contenu d’éviter de déplacer le contenu à la fois sur la source et la destination jusqu’à ce que l’ingestion soit terminée.
* Le nouveau contenu peut être ajouté, modifié ou supprimé, mais évitez de le déplacer. Cela s’applique à la fois à la source et à la destination.
* Enregistrez la variable [temps pris](/help/journey-migration/implementation.md#gathering-data) pour une extraction et une ingestion complètes afin d’avoir une estimation des futures chronologies de migration de complément.
* Créez un [planificateur de migration](/help/journey-migration/implementation.md#migration-plan) pour l’auteur et la publication.

## Abandons incrémentiels {#top-up}

Après la migration initiale depuis la production, vous devez effectuer des compléments incrémentiels pour vous assurer que votre contenu est à jour sur l’instance cloud. C’est pourquoi il est recommandé de suivre les bonnes pratiques suivantes :

* Rassemblez les données sur la quantité de contenu. Par exemple : par semaine, deux semaines ou un mois.
* Veillez à planifier les compléments de manière à éviter l’extraction et l’ingestion de contenu pendant plus de 48 heures. Cela est recommandé afin que les compléments de contenu s’adaptent à une période du week-end.
* Planifiez le nombre de complément requis et utilisez ces estimations pour planifier la date d’activation.

## Identification du code et des chronologies de blocage du contenu pour la migration {#code-content-freeze}

Comme mentionné précédemment, vous devrez planifier une période de gel du code et du contenu. Répondez aux questions suivantes pour planifier la période de gel :

* Combien de temps dois-je geler les activités de création de contenu ?
* Pendant combien de temps dois-je demander à mon équipe de diffusion de cesser d’ajouter de nouvelles fonctionnalités ?

Pour répondre à la première question, prenez en compte le temps nécessaire pour effectuer des exécutions d’essai dans des environnements hors production. Pour répondre à la seconde question, vous avez besoin d’une collaboration étroite entre l’équipe qui ajoute de nouvelles fonctionnalités et l’équipe qui refactorise le code. L’objectif doit être de s’assurer que tout le code ajouté au déploiement existant est également ajouté, testé et déployé sur la branche des services cloud. En général, cela signifie que la quantité de code sera inférieure.

En outre, vous devez prévoir un gel du contenu lorsque le complément final de contenu est planifié.

## Bonnes pratiques {#best-practices}

Lors de la planification ou de l’exécution de la migration, tenez compte des recommandations suivantes :

* Migration de l’auteur vers l’auteur et la publication vers la publication
* Demandez un clone de production qui peut être utilisé pour :
   * Capture des statistiques du référentiel
   * Preuve des activités de migration
   * Préparation du plan de migration
   * Identifier les exigences de gel du contenu
   * Identifier les besoins de mise à niveau sur la production lors de la migration depuis la production

**Bonnes pratiques relatives à l’outil de transfert de contenu**

Assurez-vous que lors de la mise en ligne, vous exécutez la migration du contenu en production au lieu d’un clone. Une bonne approche consiste à utiliser [AZCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) pour la migration initiale, puis exécutez fréquemment des extractions de complément (voire quotidiennement) afin d’extraire de petits blocs et d’éviter toute charge à long terme sur l’AEM source.

Lors de la migration de production, évitez d’exécuter l’outil de transfert de contenu à partir d’un clone, car :

* Si un client nécessite la migration des versions de contenu lors des migrations de complément, l’exécution de l’outil de transfert de contenu à partir d’un clone ne migre pas les versions. Même si le clone est fréquemment recréé à partir de l’auteur en direct, chaque fois qu’un clone est créé, les points de contrôle qui seront utilisés par l’outil de transfert de contenu pour calculer les deltas sont réinitialisés.
* Puisqu’un clone ne peut pas être actualisé dans son ensemble, le package de requête ACL doit être utilisé pour empaqueter et installer le contenu ajouté ou modifié de la production au clone. Le problème avec cette approche est que tout contenu supprimé sur l’instance source n’aura jamais accès au clone, sauf s’il est supprimé manuellement de la source et du clone. Cela introduit la possibilité que le contenu supprimé en production ne soit pas supprimé sur le clone et AEM as a Cloud Service.

**Optimiser la charge sur votre source AEM lors de la migration du contenu**

Souvenez-vous que la charge sur la source AEM sera supérieure pendant la phase d&#39;extraction. Vous devez savoir que :

* L’outil de transfert de contenu est un processus Java externe qui utilise un tas JVM de 4 Go.
* La version non-AzCopy télécharge les fichiers binaires, les stocke dans un espace temporaire sur l’auteur de l’AEM source, consommant des E/S de disque, puis les charge dans le conteneur Azure qui consomme de la bande passante réseau.
* [AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) transfère les blobs directement de la banque d’objets blob vers le conteneur Azure qui enregistre les E/S de disque et la bande passante du réseau. La version AzCopy utilise toujours la bande passante du disque et du réseau pour extraire et charger les données du magasin de segments dans le conteneur Azure.
* Le processus de l’outil de transfert de contenu est plus léger sur les ressources système pendant la phase d’ingestion, car il ne diffuse que les journaux d’ingestion et la charge de l’instance source est faible en ce qui concerne les E/S du disque ou la bande passante du réseau.

## Limites connues {#known-limitations}

Veuillez tenir compte du fait que l’ingestion entière échoue si l’une des limites suivantes fait partie du jeu de migration extrait :

* Noeud JCR dont le nom comporte plus de 150 caractères
* Noeud JCR supérieur à 16 Mo
* N’importe quel utilisateur/groupe avec `rep:AuthorizableID` ingéré déjà présent sur AEM as a Cloud Service
* Si une ressource extraite et ingérée se déplace vers un autre chemin d’accès, que ce soit à la source ou à la destination, avant la prochaine itération de la migration.

## Asset Health {#asset-health}

Comparé à la section ci-dessus de l’ingestion **ne fait pas** échoue en raison des problèmes de ressources suivants. Toutefois, il est vivement recommandé de prendre les mesures appropriées dans ces scénarios :

* Toute ressource dont le rendu d’origine est manquant
* Tout dossier manquant `jcr:content` node

Les deux éléments ci-dessus seront identifiés et signalés dans la variable [Analyseur des bonnes pratiques](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md) rapport.

## Liste de contrôle d’activation {#Go-Live-Checklist}

Consultez la liste des activités présentées ci-dessous pour vous assurer que vous pouvez effectuer une migration fluide et réussie :

* Planifiez une période de gel du code et du contenu. Voir aussi [Chronologies du gel du code et du contenu pour la migration](#code-content-freeze).
* Effectuer le complément de contenu final
* Terminer les itérations de test
* Exécuter les tests de sécurité et de performance
* Procéder à la mise en service et effectuer la migration sur l’instance de production

Vous pouvez toujours référencer la liste au cas où vous auriez besoin de recalibrer vos tâches lors de la migration.

## Et après ? {#what-is-next}

Une fois que vous avez compris comment effectuer la migration vers AEM as a Cloud Service, vous pouvez vérifier la variable [Post-activation](/help/journey-migration/post-go-live.md) pour que votre instance fonctionne correctement.