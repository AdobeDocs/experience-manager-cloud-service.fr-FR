---
title: Phase d'exécution
description: Phase d'exécution
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 15%

---


# Exécution {#execution-phase}

Avant de début de la phase d’exécution, vous devez être intégré au service Cloud. Vous devez également vous familiariser avec Cloud Manager car il s’agit du seul mécanisme de déploiement du code vers le service AEM Cloud.

Cloud Manager permet aux entreprises de gérer elles-mêmes AEM dans le Cloud. Il comprend une structure d’intégration et de diffusion continues (CI/CD) qui permet aux équipes informatiques et aux partenaires d’implémentation d’accélérer la diffusion des personnalisations ou des mises à jour sans compromettre les performances ou la sécurité.

Consultez les ressources suivantes ci-dessous pour plus de détails :

* [Intégration à Experience Manager en tant que service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/home.html) Cloud pour comprendre les ressources d’auto-assistance relatives à l’intégration d’Experience Manager en tant que service Cloud.

* [Intégration de Git avec Adobe Cloud Manager](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/managing-code/integrating-with-git.html) pour en savoir plus sur l’utilisation d’un référentiel Git unique pour déployer du code.

* [Adobe Experience as a Cloud Service Configuration](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/security/ims-support.html#aem-configuration) pour en savoir plus sur la gestion des produits et de l’accès utilisateur dans la console d’administration.


## Présentation {#introduction}

Les étapes exactes de votre transition au service Cloud dépendent des systèmes que vous avez achetés et des pratiques de cycle de vie du développement logiciel que vous suivez.

La figure suivante montre les principales étapes de la phase d&#39;exécution :

![image](/help/move-to-cloud-service/assets/exec-image1.png)

## Transfert de contenu {#content-transfer}

Pour transférer du contenu de votre instance AEM actuelle vers votre instance de service Cloud, vous pouvez utiliser l’outil Adobe Content Transfer Tool.

Cet outil vous permet de spécifier le sous-ensemble de contenu que vous souhaitez transférer de votre instance AEM source à votre instance de service AEM Cloud.

>[!NOTE]
>Il est recommandé d’effectuer de fréquents ajouts différentiels de contenu afin de raccourcir la période de gel du contenu pour le transfert différentiel final de contenu avant de passer en ligne sur le service Cloud.

Consultez Outil [de transfert de](/help/move-to-cloud-service/content-transfer-tool/overview-content-transfer-tool.md) contenu pour plus d’informations.

>[!IMPORTANT]
>La configuration minimale requise pour l’outil de transfert de contenu est AEM 6.3 + et JAVA 8. Si vous utilisez une version AEM inférieure, vous devrez mettre à niveau votre référentiel de contenu vers AEM 6.5 pour utiliser l’outil de transfert de contenu.

## Refactorisation du code {#code-refactor}

Le développement et l’exécution du code dans AEM en tant que service Cloud nécessitent une modification de l’état d’esprit. Il convient de noter que le code doit être résilient, d’autant plus qu’une instance peut être arrêtée à tout moment. Le code s’exécutant dans Cloud Service doit savoir qu’il s’exécute toujours dans une grappe. Cela signifie qu’il y a toujours plusieurs instances en cours d’exécution.

Certaines modifications sont requises pour que les projets AEM Maven soient compatibles avec AEM en tant que service Cloud. AEM en tant que service Cloud requiert une séparation du *contenu* et du *code* dans des packs distincts pour le déploiement dans AEM.

* `/apps` et `/libs` sont considérées comme des zones non modifiables d’AEM, car elles ne peuvent faire l’objet d’aucune modification (création, mise à jour ou suppression) après le démarrage d’AEM (c’est-à-dire lors de l’exécution). Toute tentative de modification d’une zone de ce type au moment de l’exécution sera vouée à l’échec.

* Toutes les autres zones du référentiel (`/content`, `/conf`, `/var`, `/home`, `/etc`, `/oak:index`, `/system`, `/tmp`, etc.) peuvent, en revanche, être modifiées au moment de l’exécution.

Refer to [Recommended Package Structure](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html#recommended-package-structure) for more details.

Il existe d’autres directives de développement que vous devez connaître lors du développement sur AEM en tant que service Cloud. Pour en savoir plus, consultez les lignes directrices [sur le développement des services Cloud d’](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/development-guidelines.html) AEM.

À partir de la phase de planification, vous devez disposer d’une liste des zones qui doivent être reconfigurées pour être compatibles avec le service Cloud. Vous devez également consulter les directives [de](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/development-guidelines.html) développement pour plus d’informations sur la manière de reformater et d’optimiser le code pour passer au service Cloud.

Pour accélérer certaines de vos tâches de refactorisation du code, vous pouvez utiliser les outils suivants :

* [Migration du flux de travaux des ressources](/help/move-to-cloud-service/moving-to-aem-assets/asset-workflow-migration-tool.md)
* [Convertisseur répartiteur](/help/move-to-cloud-service/refactoring-tools/dispatcher-transformation-utility-tools.md)
* [Outils de modernisation](/help/move-to-cloud-service/refactoring-tools/aem-modernization-tools.md)

Il est recommandé de reformater et de tester le code localement avant de le placer dans un environnement de service Cloud via Cloud Manager Git.

Consultez la documentation du SDK [](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/deploying/overview.html#aem-as-a-cloud-service-sdk) AEM pour en savoir plus.

On trouvera ci-dessous la liste de quelques ressources supplémentaires :

* Regardez le SDK Install Dispatcher pour comprendre comment installer le SDK Dispatcher :

   > [!VIDEO](https://video.tv.adobe.com/v/30601)

* Regardez Configurer le SDK du répartiteur pour comprendre comment configurer le SDK du répartiteur :

   > [!VIDEO](https://video.tv.adobe.com/v/30602)

* Consultez la documentation relative à la configuration [du développement](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html) local pour configurer un environnement de développement local.


Pour gérer le développement de votre code en cours sur votre AEM actif, ainsi que la tâche de refactorisation du code dans le cadre de votre parcours de transition, il est recommandé de planifier une période de gel du code jusqu’à ce que vous ayez terminé la restructuration de votre projet Maven afin qu’il soit compatible avec AEM en tant que service Cloud.

Une fois la restructuration du projet terminée, vous pouvez reprendre le développement du nouveau code en fonction de cette nouvelle structure. Cela réduira les échecs de pipeline de Cloud Manager pendant le déploiement et le test du code.

>[!NOTE]
>Les tâches de transfert de contenu et de refactorisation du code n’ont pas été effectuées de manière séquentielle. Ces tâches peuvent être faites indépendamment les unes des autres. Toutefois, la structure de projet appropriée est requise pour s’assurer que le contenu est correctement rendu dans votre environnement de services Cloud.

## Bonnes pratiques pour le déploiement et le test du code {#best-practices}

Les exécutions du pipeline Cloud Manager for Cloud Services prennent en charge l’exécution de tests sur l’environnement d’évaluation.

Consultez Test [de qualité du](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/understand-test-results.html#code-quality-testing) code pour en savoir plus sur l’écriture de scripts de test et sur la couverture recommandée d’au moins 50 %.

En outre, consultez la section [Comprendre les règles](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/custom-code-quality-rules.html) de qualité du code personnalisé pour en savoir plus sur les règles de qualité du code personnalisé exécutées par Cloud Manager et créées en fonction des meilleures pratiques d’AEM Engineering.

L’utilisation de Cloud Manager est le seul mécanisme de déploiement du code sur les environnements de service Cloud.

Suivez les ressources ci-dessous pour savoir comment utiliser Cloud Manager pour gérer et déployer votre code.

* [Gestion des environnements](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html)

* [Configuration du pipeline CI-CD](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html)

* [Déploiement de votre code](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html)

## Bonnes pratiques pour la préparation en direct {#go-live}

Pour garantir une intégration fluide et réussie d’AEM en tant que service Cloud, vous devez envisager d’exécuter les étapes suivantes :

* Planification de la période de gel du code et du contenu
* Compléter le contenu final
* Terminer les itérations de test
* Exécution de tests de performances et de sécurité
* Découpe
