---
title: Phase d’exécution
description: Phase d’exécution
translation-type: tm+mt
source-git-commit: 0dd05c1f6dc197daf154d4df6e6661e00455b233
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 100%

---


# Exécution {#execution-phase}

Avant de démarrer la phase d’exécution, vous devez être intégré à Cloud Service. Vous devez également vous familiariser avec Cloud Manager, car il s’agit du seul mécanisme de déploiement du code vers AEM Cloud Service.

Cloud Manager permet aux entreprises de gérer elles-mêmes AEM dans le cloud. Il comprend une structure d’intégration et de diffusion continues (CI/CD) qui permet aux équipes informatiques et aux partenaires d’implémentation d’accélérer la diffusion des personnalisations ou des mises à jour sans compromettre les performances ou la sécurité.

Pour plus d’informations, référez-vous aux ressources ci-dessous :

* [Intégration à Experience Manager as a Cloud Service](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/onboarding/home.html) pour comprendre les ressources d’aide autonome relatives à l’intégration à Experience Manager as a Cloud Service.

* [Intégration de Git à Adobe Cloud Manager](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/managing-code/integrating-with-git.html) pour en savoir plus sur l’utilisation d’un référentiel Git unique pour déployer du code.

* [Configuration d’Adobe Experience as a Cloud Service](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/security/ims-support.html#aem-configuration) pour en savoir plus sur la gestion des produits et de l’accès utilisateur dans Admin Console.


## Présentation {#introduction}

Les étapes exactes de votre transition vers Cloud Service dépendent des systèmes achetés et de vos pratiques de cycle de vie du développement logiciel.

La figure suivante montre les principales étapes de la phase d’exécution :

![image](/help/move-to-cloud-service/assets/exec-image1.png)

## Transfert de contenu {#content-transfer}

Pour transférer du contenu entre votre instance AEM actuelle et l’instance Cloud Service, vous pouvez utiliser l’outil de transfert de contenu d’Adobe.

Il permet de spécifier le sous-ensemble de contenu que vous souhaitez transférer entre votre instance AEM source et l’instance AEM Cloud Service.

>[!NOTE]
>Il est recommandé d’effectuer fréquemment des compléments différentiels pour réduire la période de gel du transfert final de contenu différentiel avant de passer en ligne sur Cloud Service.

Pour plus d’informations, voir [Outil de transfert de contenu](/help/move-to-cloud-service/content-transfer-tool/overview-content-transfer-tool.md).

>[!IMPORTANT]
>La configuration minimale requise pour l’outil de transfert de contenu est AEM 6.3+ et JAVA 8. Si vous utilisez une version antérieure d’AEM, vous devrez mettre à niveau votre référentiel de contenu à la version AEM 6.5 pour utiliser l’outil de transfert de contenu.

## Refactorisation du code {#code-refactor}

Le développement et l’exécution du code dans AEM as a Cloud Service nécessitent un changement d’état d’esprit. Le code doit être résilient, d’autant plus qu’une instance peut être arrêtée à tout moment. Le code s’exécutant dans Cloud Service doit savoir qu’il s’exécute toujours dans une grappe. Cela signifie qu’il y a toujours plusieurs instances en cours d’exécution.

Certaines modifications sont nécessaires pour que les projets AEM Maven soient compatibles avec AEM as a Cloud Service. AEM as a Cloud Service nécessite de séparer le *contenu* et le *code* dans des modules distincts pour le déploiement dans AEM.

* `/apps` et `/libs` sont considérées comme des zones non modifiables d’AEM, car elles ne peuvent faire l’objet d’aucune modification (création, mise à jour ou suppression) après le démarrage d’AEM (c’est-à-dire lors de l’exécution). Toute tentative de modification d’une zone de ce type au moment de l’exécution sera vouée à l’échec.

* Toutes les autres zones du référentiel (`/content`, `/conf`, `/var`, `/home`, `/etc`, `/oak:index`, `/system`, `/tmp`, etc.) peuvent, en revanche, être modifiées au moment de l’exécution.

Pour plus d’informations, voir [Structure de module recommandée](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html#recommended-package-structure).

Il existe d’autres directives de développement à connaître concernant le développement sur AEM as a Cloud Service. Pour en savoir plus, consultez les [Conseils de développement pour AEM as a Cloud Service](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/developing/development-guidelines.html).

À partir de la phase de planification, vous devez disposer d’une liste des zones à reconfigurer pour qu’elles soient compatibles avec Cloud Service. Vous devez également consulter les [Conseils de développement](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/developing/development-guidelines.html) pour en savoir plus sur la refactorisation et l’optimisation du code nécessaires au passage vers Cloud Service.

Pour accélérer certaines de vos tâches de refactorisation du code, vous pouvez utiliser les outils suivants :

* [Migration des workflows de ressources](/help/move-to-cloud-service/moving-to-aem-assets/asset-workflow-migration-tool.md)
* [Convertisseur du Dispatcher](/help/move-to-cloud-service/refactoring-tools/dispatcher-transformation-utility-tools.md)
* [Outils de modernisation](/help/move-to-cloud-service/refactoring-tools/aem-modernization-tools.md)

Il est recommandé de refactoriser et tester le code localement avant de le placer dans un environnement Cloud Service à l’aide de Cloud Manager Git.

Pour en savoir plus, consultez la documentation du [SDK AEM](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/deploying/overview.html#aem-as-a-cloud-service-sdk).

Une liste contenant un certain nombre de ressources supplémentaires est proposée ci-dessous :

* Regardez la vidéo relative à l’installation du SDK Dispatcher pour comprendre comment procéder :

   >[!VIDEO](https://video.tv.adobe.com/v/30601)

* Regardez la vidéo relative à la configuration du SDK Dispatcher pour comprendre comment procéder :

   >[!VIDEO](https://video.tv.adobe.com/v/30602)

* Consultez la documentation relative à la [Configuration du développement local](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html) pour configurer un environnement de développement local.


Pour gérer le développement continu de votre code sur votre AEM actif, ainsi que la refactorisation du code au cours du parcours de transition, il est recommandé de planifier une période de gel du code jusqu’à la fin de la restructuration du projet Maven pour assurer la compatibilité avec AEM as a Cloud Service.

Une fois la restructuration du projet terminée, vous pouvez reprendre le développement du code à l’aide de la nouvelle structure. Les défaillances de pipeline de Cloud Manager seront ainsi réduites au cours du déploiement et du test du code.

>[!NOTE]
>Les tâches de transfert de contenu et de refactorisation du code n’ont pas à être effectuées séquentiellement, et peuvent être réalisées indépendamment les unes des autres. Toutefois, une structure de projet appropriée est requise pour que le contenu soit correctement rendu dans votre environnement Cloud Service.

## Bonnes pratiques de déploiement et de test du code {#best-practices}

Les exécutions du pipeline Cloud Manager for Cloud Services prennent en charge l’exécution de tests sur l’environnement d’évaluation.

Consultez [Test de qualité du code](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/developing/understand-test-results.html#code-quality-testing) pour en savoir plus sur l’écriture de scripts de test et sur la couverture recommandée d’au moins 50 %.

Vous pouvez en outre consulter la section [Présentation des règles de qualité du code personnalisé](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/using-cloud-manager/custom-code-quality-rules.html) pour en savoir plus sur les règles de qualité du code personnalisé exécutées par Cloud Manager et créées conformément aux bonnes pratiques en matière d’ingénierie AEM.

L’utilisation de Cloud Manager est le seul mécanisme de déploiement de code pour les environnements Cloud Service.

Consultez les ressources ci-dessous pour découvrir comment utiliser Cloud Manager pour gérer et déployer votre code.

* [Gestion des environnements](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html)

* [Configuration du pipeline CI-CD](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html)

* [Déploiement de votre code](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html)

## Bonnes pratiques pour la préparation de l’activation {#go-live}

Pour garantir une activation fluide et réussie d’AEM as a Cloud Service, vous pouvez procéder comme suit :

* Planifier la période de gel du code et du contenu
* Effectuer le traitement du complément du contenu final
* Terminer les itérations de test
* Exécuter les tests de sécurité et de performance
* Procéder à la mise en service
