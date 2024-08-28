---
title: Mise en production
description: Découvrez comment effectuer la migration une fois que le code et le contenu sont prêts pour le cloud
exl-id: 10ec0b04-6836-4e26-9d4c-306cf743224e
feature: Migration
role: Admin
source-git-commit: 5b0dfb847a1769665899d6dd693a7946832fe7d1
workflow-type: tm+mt
source-wordcount: '1223'
ht-degree: 93%

---

# Mise en production {#go-live}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_prep"
>title="Préparation de l’activation"
>abstract="Pour garantir une activation fluide et réussie d’AEM as a Cloud Service, vous devez prévoir des périodes de gel du code et du contenu, des itérations de test, des compléments de contenu, des tests de performance, des tests de sécurité, etc."

Dans cette partie du parcours, vous apprenez à planifier et à effectuer la migration une fois que le code et le contenu sont prêts à être déplacés vers AEM as a Cloud Service. En outre, vous découvrez les bonnes pratiques et les limites connues lors de la migration.

## Un peu d’histoire…  {#story-so-far}

Dans les phases précédentes du parcours :

* Vous avez appris comment démarrer la migration vers AEM as a Cloud Service à la page [Prise en main](/help/journey-migration/getting-started.md).
* Vous avez déterminé si votre déploiement est prêt à être déplacé vers le cloud en consultant la [Phase de préparation](/help/journey-migration/readiness.md).
* Vous vous êtes familiarisé avec les outils et le processus qui vous permettent de préparer votre code et votre contenu pour le cloud avec la [phase d’implémentation](/help/journey-migration/implementation.md).

## Objectif {#objective}

Ce document vous aidera à comprendre comment effectuer la migration vers AEM as a Cloud Service une fois que vous maîtriserez les étapes précédentes du parcours. Vous apprendrez comment effectuer la migration de production initiale, ainsi que les bonnes pratiques à suivre lors de la migration vers AEM as a Cloud Service.

## Migration de production initiale {#initial-migration}

Avant d’effectuer la migration de production, suivez les étapes d’adaptation et de preuve de migration décrites dans la section [Stratégie et calendrier de la migration de contenu](/help/journey-migration/implementation.md##strategy-timeline) de la [phase d’implémentation](/help/journey-migration/implementation.md).

* Lancez la migration de production en vous appuyant sur l’expérience acquise lors de la migration d’évaluation AEM as a Cloud Service effectuée sur des clones :
   * Création-Création
   * Publication-Publication

* Validez le contenu ingéré dans les niveaux de création et de publication d’AEM as a Cloud Service.
* Demandez à l’équipe de création de contenu d’éviter de déplacer le contenu à la fois sur la source et la destination jusqu’à ce que l’ingestion soit terminée.
* Vous pouvez ajouter, modifier ou supprimer du nouveau contenu, mais évitez de le déplacer. Ceci s’applique à la fois à la source et à la destination.
* Enregistrez le [temps nécessaire](/help/journey-migration/implementation.md#gathering-data) à l’extraction et à l’ingestion complètes afin de disposer d’une estimation pour les futures délais de migration complémentaire.
* Créez un [planificateur de migration](/help/journey-migration/implementation.md#migration-plan) pour les créations et les publications.

## Compléments incrémentiels {#top-up}

Après la migration initiale depuis la production, vous devez effectuer des compléments incrémentiels pour vous assurer que votre contenu est à jour sur l’instance cloud. C’est pourquoi il est recommandé de suivre les bonnes pratiques suivantes :

* Rassemblez les données sur la quantité de contenu. Par exemple : par semaine, par quinzaine ou par mois.
* Veillez à planifier les compléments de manière à éviter l’extraction et l’ingestion de contenu pendant plus de 48 heures. Cette action vous est recommandée afin que les compléments de contenu puissent être effectués pendant le week-end.
* Prévoyez le nombre de compléments nécessaires et utilisez ces estimations pour planifier la date de mise en production.

## Déterminer les délais de gel du code et du contenu pour la migration {#code-content-freeze}

Comme mentionné précédemment, vous devrez planifier une période de gel du code et du contenu. Répondez aux questions suivantes pour vous aider à planifier la période de gel :

* Combien de temps dois-je geler les activités de création de contenu ?
* Pendant combien de temps dois-je demander à mon équipe de diffusion de cesser d’ajouter de nouvelles fonctionnalités ?

Pour répondre à la première question, prenez en compte le temps nécessaire pour effectuer des essais dans des environnements de non-production. Pour répondre à la seconde question, il faut une collaboration étroite entre l’équipe qui ajoute de nouvelles fonctionnalités et l’équipe qui remanie le code. L’objectif est de s’assurer que tout le code qui est ajouté au déploiement existant est également ajouté, testé et déployé dans la branche des services cloud. En général, cela signifie que la quantité de code gelé est inférieure.

En outre, vous devez prévoir un gel du contenu lorsque le complément final de contenu est planifié.

## Bonnes pratiques {#best-practices}

Lors de la planification ou de l’exécution de la migration, tenez compte des recommandations suivantes :

* Migrer de création à création et de publication à publication
* Demandez un clone de production qui peut être utilisé pour :
   * Capturer les statistiques du référentiel
   * Prouver les activités de migration
   * Préparer le programme de migration
   * Identifier les besoins de gel du contenu
   * Identifier les besoins de mise à niveau de la production lors de la migration depuis la production

**Bonnes pratiques de l’outil de transfert de contenu**

Lors de la mise en production, assurez-vous d’exécuter la migration du contenu sur la production plutôt que sur un clone. Une bonne approche consiste à utiliser [AZCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) pour la migration initiale, puis à exécuter fréquemment (voire quotidiennement) des extractions complémentaires afin d’extraire de plus petits blocs et d’éviter toute charge à long terme sur l’AEM source.

Lors de la migration de production, évitez d’exécuter l’outil de transfert de contenu à partir d’un clone, et ce, pour les raisons suivantes :

* Si un client exige que les versions de contenu soient migrées pendant les migrations complémentaires, l’exécution de l’outil de transfert de contenu à partir d’un clone ne permet pas de migrer les versions. Même si le clone est fréquemment recréé à partir de l’instance de création en direct, chaque fois qu’un clone est créé, les points de contrôle qui sont utilisés par l’outil de transfert de contenu pour calculer les deltas sont réinitialisés.
* Puisqu’un clone ne peut pas être actualisé dans son ensemble, le package de requêtes ACL doit être utilisé pour combiner et installer le contenu ajouté ou modifié de la production au clone. Le problème avec cette approche est que tout contenu supprimé sur l’instance source n’aura jamais accès au clone, sauf s’il est supprimé manuellement de la source et du clone. Il est donc possible que le contenu supprimé en production ne soit pas supprimé sur le clone et sur AEM as a Cloud Service.

**Optimiser la charge de votre source AEM lors de la migration du contenu**

Souvenez-vous que la charge sur la source AEM est plus importante pendant la phase d’extraction. Tenez compte des points suivants :

* L’outil de transfert de contenu est un processus Java externe qui utilise un tas JVM de 4 Go.
* La version non-AzCopy télécharge les fichiers binaires, les stocke dans un espace temporaire sur l’auteur de l’AEM source, consommant des E/S de disque, puis les charge dans le conteneur Azure, ce qui consomme de la bande passante réseau.
* [AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) transfère les blobs directement de la banque d’objets blob vers le conteneur Azure, ce qui permet d’économiser les E/S de disque et la bande passante du réseau. La version AzCopy utilise toujours la bande passante du disque et du réseau pour extraire et charger les données du magasin de segments dans le conteneur Azure.
* Le processus de l’outil de transfert de contenu est moins gourmand en ressources système pendant la phase d’ingestion, car il ne diffuse que les journaux d’ingestion et qu’il n’y a pas beaucoup de charge sur l’instance source en ce qui concerne les E/S de disque ou la bande passante du réseau.

## Limites connues {#known-limitations}

Veuillez tenir compte du fait que l’ingestion entière échoue si l’une des limites suivantes fait partie du jeu de migration extrait :

* Un nœud JCR dont le nom comporte plus de 150 caractères
* Un nœud JCR dont la taille est supérieure à 16 Mo
* Si une ressource extraite et ingérée change de chemin d’accès à la source ou à la destination avant l’itération suivante de la migration.

## Intégrité des ressources {#asset-health}

Comparé à la section ci-dessus, l’ingestion n’échoue **pas** en raison des problèmes de ressources suivants. Toutefois, il est vivement recommandé de prendre les mesures appropriées dans ces scénarios :

* Toute ressource dont le rendu original est manquant.
* Tout dossier qui comporte un noeud `jcr:content` manquant.

Les deux éléments ci-dessus sont identifiés et signalés dans le rapport de [Best Practice Analyzer](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md).

## Liste de contrôle de mise en production {#Go-Live-Checklist}

Pour plus d’informations, consultez la documentation [Liste de contrôle d’activation](/help/journey-onboarding/go-live-checklist.md) .

## Prochaines étapes {#what-is-next}

Une fois que vous avez compris comment effectuer la migration vers AEM as a Cloud Service, vous pouvez consulter la page [Post-mise en production](/help/journey-migration/post-go-live.md) pour assurer le bon fonctionnement de votre instance.
