---
title: Déploiement de votre code - Cloud Services
description: Déploiement de votre code - Cloud Services
translation-type: ht
source-git-commit: 7758c6df49583dafdf2bf262eae8db466bb3c504

---


# Déploiement de votre code {#deploy-your-code}

## Déploiement du code avec Cloud Manager {#deploying-code-with-cloud-manager}

Une fois que vous avez configuré le **pipeline** (référentiel, environnement et environnement de test), vous êtes prêt à déployer le code.

1. Cliquez sur **Déployer** dans Cloud Manager pour lancer le processus de déploiement.

   ![](assets/deploy-code1.png)


1. L’écran **Exécution du pipeline** s’affiche.

   Cliquez sur **Générer** pour lancer le processus.

   ![](assets/deploy-code2.png)

1. Le processus de création complet déploie le code.

   Les étapes suivantes sont impliquées dans le processus de création :

   1. Déploiement dans l’environnement intermédiaire
   1. Test dans l’environnement intermédiaire
   1. Déploiement dans l’environnement de production
   >[!NOTE]
   >
   >En outre, vous pouvez examiner les étapes de divers processus de déploiement en affichant les journaux ou en examinant les résultats pour les critères de test.

   Le **déploiement en environnement intermédiaire** comprend les étapes suivantes :

   * Validation : cette étape permet de s’assurer que le pipeline est configuré pour utiliser les ressources actuellement disponibles ; par exemple, la branche configurée existe, les environnements sont disponibles, etc.
   * Test de création et d’unité : cette étape exécute un processus de création en conteneur. Pour plus d’informations sur l’environnement de création, voir [Création d’un projet d’application AEM](/help/onboarding/getting-access-to-aem-in-cloud/creating-aem-application-project.md).
   * Analyse du code : cette étape évalue la qualité du code de votre application. Pour plus d’informations sur le processus de test, voir [Comprendre vos résultats de test](/help/implementing/developing/introduction/understand-test-results.md).
   * Compiler des images : cette étape comprend un fichier journal du processus utilisé pour compiler des images. Ce processus est responsable de la transformation du contenu et des modules du Dispatcher générés par l’étape de compilation en images Docker et en configuration Kubernetes.
   * Déploiement dans l’environnement d’évaluation.

      ![](assets/stage-deployment.png)
   Le **test dans l’environnement intermédiaire** comprend les étapes suivantes :

   * Tests fonctionnels du produit : les exécutions du pipeline Cloud Manager prennent en charge l’exécution de tests sur l’environnement d’évaluation. Pour plus d’informations sur le processus de test, voir [Comprendre vos résultats de test](/help/implementing/developing/introduction/understand-test-results.md).
   * Tests fonctionnels personnalisés : cette étape du pipeline est toujours présente et ne peut pas être ignorée. Cependant, si aucun fichier JAR de test n’est généré par la compilation, le test réussit par défaut. Pour plus d’informations sur le processus de test, voir [Comprendre vos résultats de test](/help/implementing/developing/introduction/understand-test-results.md).

      ![](assets/stage-testing.png)





>Attention :
>les sections suivantes doivent être mises à jour pour Cloud Manager for AEM Cloud Services. Cette opération est en cours.

## Processus de déploiement {#deployment-process}

La section suivante décrit le déploiement des packages AEM et dispatcher dans les phases intermédiaires et de production.

Cloud Manager télécharge tous les fichiers target/*.zip générés par le processus de création vers un emplacement de stockage. Ces artefacts sont récupérés à partir de cet emplacement pendant les phases de déploiement du pipeline.

Lorsque Cloud Manager se déploie sur des topologies autres que de production, l’objectif est de réaliser le déploiement aussi rapidement que possible ; les artefacts sont donc déployés simultanément sur tous les nœuds, comme suit :

1. Cloud Manager détermine si chaque artefact est un package AEM ou dispatcher.
1. Cloud Manager supprime tous les dispatchers de l’équilibreur de charge pour isoler l’environnement pendant le déploiement.

   Sauf configuration contraire, vous pouvez ignorer les modifications de l’équilibreur de charge dans les déploiements de développement et en environnement intermédiaire, c’est-à-dire détacher et attacher des étapes dans les deux pipelines hors production, pour les environnements de développement et le pipeline de production, pour les environnements intermédiaires.

   >[!NOTE]
   >
   >Cette fonctionnalité devrait principalement être utilisée par les clients 1-1-1.

1. Chaque artefact AEM est déployé sur chaque instance AEM par le biais des API de Package Manager, avec des dépendances de packages qui déterminent l’ordre de déploiement.

   Pour en savoir plus sur l’utilisation de packages pour installer de nouvelles fonctionnalités, transférer du contenu entre des instances et sauvegarder le contenu du référentiel, reportez-vous à la section Utilisation de packages.

   >[!NOTE]
   >
   >Tous les artefacts AEM sont déployés à la fois sur author et publishers. Les modes d’exécution doivent être utilisés lorsque des configurations spécifiques à un nœud sont requises. Pour en savoir plus sur la façon dont les modes d’exécution vous permettent d’ajuster votre instance AEM à des fins spécifiques, consultez Modes d’exécution.

1. L’artefact dispatcher est déployé sur chaque dispatcher comme suit :

   1. Les configurations actuelles sont sauvegardées et copiées vers un emplacement temporaire.
   1. Toutes les configurations sont supprimées, à l’exception des fichiers non modifiables. Pour plus d’informations, consultez la section Gestion des configurations du Dispatcher. Cela permet de vider les répertoires pour qu’aucun fichier orphelin ne soit abandonné.
   1. L’artefact est extrait dans le répertoire httpd. Les fichiers non modifiables ne sont pas remplacés. Toute modification apportée aux fichiers non modifiables dans votre référentiel git sera ignorée au moment du déploiement.  Ces fichiers sont essentiels à la structure du dispatcher AMS et ne peuvent pas être modifiés.
   1. Apache effectue un test de configuration. Si aucune erreur n’est trouvée, le service est rechargé. Si une erreur se produit, les configurations sont restaurées à partir de la sauvegarde, le service est rechargé et l’erreur est renvoyée à Cloud Manager.
   1. Chaque chemin spécifié dans la configuration de pipeline est invalidé ou purgé du cache du dispatcher.
   >[!NOTE]
   >
   >Cloud Manager exige que l’artefact du dispatcher contienne le jeu de fichiers complet.  Tous les fichiers de configuration du dispatcher doivent être présents dans le référentiel git. Les fichiers ou dossiers manquants entraînent l’échec du déploiement.

1. Après le déploiement réussi de tous les packages AEM et de dispatcher sur tous les nœuds, les dispatchers sont ajoutés à l’équilibreur de charge et le déploiement est terminé.

   >[!NOTE]
   >
   >Vous pouvez ignorer les modifications de l’équilibreur de charge dans les déploiements de développement et en environnement intermédiaire, c’est-à-dire, détacher et attacher des étapes dans les deux pipelines hors production, pour les environnements de développement et le pipeline de production, pour les environnements intermédiaires.

### Phase de déploiement en production {#deployment-production-phase}

Le processus de déploiement des topologies de production diffère légèrement afin de minimiser l’impact sur les visiteurs d’AEM Site.

Les déploiements en production suivent généralement les mêmes étapes que ci-dessus, mais par roulements :

1. Déploiement des packages AEM sur author.
1. Détachement de dispatcher1 de l’équilibreur de charge.
1. Déploiement des packages AEM sur publish1 et le package dispatcher sur dispatcher1. Purge du cache du dispatcher.
1. Replacement du dispatcher1 dans l’équilibreur de charge.
1. Lorsque dispatcher1 fonctionne à nouveau, détachement de dispatcher2 de l’équilibreur de charge.
1. Déploiement des packages AEM sur publish2 et le package dispatcher sur dispatcher2. Purge du cache du dispatcher.
1. Replacement du dispatcher2 dans l’équilibreur de charge.
Ce processus se poursuit jusqu’à ce que le déploiement ait atteint tous les publishers et dispatchers dans la topologie.


