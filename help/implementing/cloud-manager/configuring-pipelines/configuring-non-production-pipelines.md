---
title: Ajout d’un pipeline hors production
description: Découvrez comment ajouter un pipeline hors production pour tester la qualité de votre code avant le déploiement dans les environnements de production.
index: true
exl-id: eba608eb-a19e-4bff-82ff-05860ceabe6e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: 10b54f1870113f6a94811df3976017c854ccf1eb
workflow-type: tm+mt
source-wordcount: '1729'
ht-degree: 21%

---


# Ajout d’un pipeline hors production {#configuring-non-production-pipelines}

Après avoir configuré un programme et créé au moins un environnement dans l’interface utilisateur de Cloud Manager, vous pouvez ajouter des pipelines hors production. Ces pipelines vous permettent de tester la qualité du code avant le déploiement dans les environnements de production.

Un utilisateur doit disposer du rôle **[Responsable de déploiement](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** pour configurer des pipelines hors production.

>[!NOTE]
>
>Vous pouvez [modifier les paramètres du pipeline](managing-pipelines.md) après la configuration initiale.

## Ajout d’un nouveau pipeline hors production

Après avoir configuré un programme et créé au moins un environnement dans l’interface utilisateur de Cloud Manager, vous pouvez ajouter des pipelines hors production. Utilisez ces pipelines pour tester la qualité du code avant de le déployer dans des environnements de production.

**Pour ajouter un nouveau pipeline hors production, procédez comme suit**

{{sign-in-to-cloud-manager}}

1. Sur la console **Mes programmes**, cliquez sur un programme.
1. Dans le panneau de gauche, cliquez sur **Pipelines**.
1. Sur la page **Pipelines**, près du coin supérieur droit, cliquez sur **Ajouter un pipeline** > **Ajouter un pipeline hors production**.

   ![Ajouter un pipeline hors production](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. Sous l’onglet **Configuration** de la boîte de dialogue **Ajouter un pipeline hors production**, sélectionnez l’un des pipelines hors production suivants que vous souhaitez créer :

   * **Pipeline de qualité du code** - Crée un pipeline qui génère le code sur une branche GIT, exécute des tests unitaires et évalue la qualité du code sans le déployer dans un environnement.
   * **Pipeline de déploiement** - Crée un pipeline qui génère le code, exécute des tests unitaires, évalue la qualité du code et le déploie dans un environnement hors production.

   ![Boîte de dialogue Ajouter un pipeline hors production](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. Sous la section **Configuration du pipeline**, dans le champ **Nom du pipeline hors production**, saisissez une description de votre pipeline hors production.
1. Sous la section **Options de déploiement**, sélectionnez l’un des déclencheurs de déploiement suivants que vous souhaitez utiliser :

   * **Manuel** : vous permet de lancer le pipeline manuellement.
   * **Lors des modifications Git** : démarre le pipeline lorsque des validations sont ajoutées à la branche Git configurée. Avec cette option, vous pouvez toujours démarrer le pipeline manuellement, si nécessaire.

1. Sélectionnez le **Comportement en cas d’échecs de mesure importants** à utiliser.

   * **Demander à chaque fois** – Ce comportement est le paramètre par défaut qui nécessite une intervention manuelle lors de tout échec important.
   * **Défaillance immédiate** – Si cette option est sélectionnée, le pipeline sera interrompu dès qu’une défaillance importante aura lieu. Il émule essentiellement un utilisateur rejetant manuellement chaque échec.
   * **Continuer immédiatement** – Si cette option est sélectionnée, le pipeline se poursuivra automatiquement chaque fois qu’une défaillance importante se produira. Il émule essentiellement la validation manuelle de chaque échec par un utilisateur.

1. Cliquez sur **Continuer**.

1. Les étapes restantes que vous utilisez pour terminer la configuration de votre pipeline hors production dépendent du type de code source que vous choisissez d’utiliser.
Sous l’onglet **Code** de la boîte de dialogue **Ajouter un pipeline hors production**, sélectionnez le type de code que le pipeline hors production doit traiter.

   * **[J’utilise le code de pile complète](#full-stack-code)**
   * **[J’utilise le déploiement ciblé](#targeted-deployment)**

   Voir [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) pour plus d’informations sur les types de pipelines.


### J’utilise le code de pile complète.

Un pipeline de code full stack déploie simultanément des versions de code front-end et back-end contenant une ou plusieurs applications de serveur AEM avec une configuration HTTPD/Dispatcher.

>[!NOTE]
>
>Si un pipeline de code full stack existe pour l’environnement sélectionné, cette sélection est désactivée.

Pour terminer la configuration du pipeline hors production de code full stack, procédez comme suit :

1. Dans la section **Code**, définissez les options suivantes.

   * **Environnements de déploiement éligibles** - Disponible uniquement lorsque vous modifiez un pipeline hors production. Si votre pipeline est un pipeline de déploiement, vous devez sélectionner les environnements à déployer.
   * **Référentiel** - Dans la liste déroulante, sélectionnez le référentiel Git que le pipeline utilise comme source. Cloud Manager crée le code à partir du référentiel que vous choisissez ici.

     >[!TIP]
     > 
     >Consultez [Ajout et gestion de référentiels](/help/implementing/cloud-manager/managing-code/managing-repositories.md) pour découvrir comment ajouter et gérer des référentiels dans Cloud Manager.

   * **Branche Git** - Dans la liste déroulante, choisissez la branche du référentiel sélectionné à partir de laquelle le pipeline doit être créé. La valeur par défaut est `main`. Le pipeline utilise la branche choisie comme source pour la création et le déploiement. Si nécessaire, cliquez sur **Actualiser** pour mettre à jour la liste des branches disponibles pour le référentiel sélectionné. Utilisez cette option si une branche créée récemment n’apparaît pas dans la liste.
   * **Créer une stratégie**
      * **Version complète** - Génère tous les modules du référentiel à chaque fois
      * BETA **Smart Build** - crée uniquement les modules qui ont été modifiés depuis la dernière validation.<br>En savoir plus sur [l’utilisation de la création intelligente dans un pipeline hors production](#about-smart-build-non-production-pipeline).

        >[!IMPORTANT]
        >
        >Le build intelligent est disponible uniquement pour les pipelines de qualité du code et de déploiement de code de pile complète de développement.

   * Case à cocher **Ignorer la configuration de niveau web** - Lorsque cette case est cochée, le pipeline ne déploie pas votre configuration de niveau web.

1. Dans la section **Pipeline** , si votre pipeline est un pipeline de déploiement, vous pouvez choisir d’exécuter une phase de test. Cochez les options que vous souhaitez activer pour cette phase. Si aucune des options n’est sélectionnée, la phase de test n’est pas affichée pendant l’exécution du pipeline.

   * **Tests fonctionnels du produit** - Exécutez [tests fonctionnels du produit](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing) dans l’environnement de développement.
   * **Tests fonctionnels personnalisés** - Exécutez [tests fonctionnels personnalisés](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) dans l’environnement de développement.
   * **Test d’interface utilisateur personnalisé** - Exécutez [tests d’interface utilisateur personnalisés](/help/implementing/cloud-manager/ui-testing.md) pour les applications personnalisées.
   * **Contrôle de l’expérience** - Exécuter [contrôle de l’expérience](/help/implementing/cloud-manager/reports/report-experience-audit.md)

   ![Pipeline full stack](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. Cliquez sur **Enregistrer**.

Le pipeline est enregistré et vous pouvez maintenant [gérer vos pipelines]&#x200B;(managing-pipe
lines.md) sur la carte **Pipelines** sur la page **Présentation du programme**.

### J’utilise le déploiement ciblé {#targeted-deployment}

Un déploiement ciblé déploie le code uniquement pour les parties sélectionnées de votre application AEM. Dans un tel déploiement, vous pouvez choisir d’**Inclure** l’un des types de code suivants :

![Options de déploiement ciblé](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-targeted-deployment1.png)

<!--
* **Config** - Configure settings for various features in your AEM environment.
  * See [Using Config Pipelines](/help/operations/config-pipeline.md) for a list of supported configurations, which include log forwarding, purge-related maintenance tasks, and various CDN configurations, and to manage them in your repository so they are deployed properly.
  * When running a targeted deployment pipeline, configurations are deployed, provided they are saved to the environment, repository, and branch you defined in the pipeline.
  * At any time, there can only be one config pipeline per environment.
* **Configure Edge Delivery Services config pipeline** - Edge Delivery Configuration Pipelines do not have separate development, staging, and production environments. In AEM as a Cloud Service, changes move through development, stage, and production tiers. In contrast, an Edge Delivery Configuration Pipeline applies its configuration directly to all Edge Delivery Sites domains registered in Cloud Manager. To learn more, see [Add an Edge Delivery Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md).
-->


* **Code front-end** - Configurez JavaScript et CSS pour le front-end de votre application AEM.
   * Avec les pipelines front-end, les développeurs front-end bénéficient d’une plus grande indépendance et le processus de développement peut être accéléré.
   * Consultez le document [Développement de sites avec le pipeline front-end](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) pour connaître le fonctionnement de ce processus ainsi que certaines considérations à prendre en compte pour en tirer le meilleur parti.
* **Configuration de niveau web** - Configurez les propriétés Dispatcher pour stocker, traiter et diffuser des pages web au client.
   * Voir le document [Pipelines CI/CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) pour plus d’informations.
   * Si un pipeline de code de niveau web existe pour l’environnement sélectionné, cette sélection est désactivée.
   * Si un pipeline full stack est déjà déployé vers un environnement, vous pouvez toujours créer un pipeline de configuration de niveau web pour ce même environnement. Dans ce cas, Cloud Manager ignore la configuration de la couche web dans le pipeline full stack.

     >[!NOTE]
     >
     >Les pipelines de niveau web et de configuration ne sont pas pris en charge pour les référentiels privés. Voir [Ajout de référentiels privés dans Cloud Manager](/help/implementing/cloud-manager/managing-code/private-repositories.md) pour plus d’informations et la liste complète des limitations.

<!--
The steps to complete the creation of your non-production, targeted deployment pipeline are the same once you choose a deployment type.

1. Choose which deployment type you require.

![Targeted deployment options](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-targeted-deployment.png)

1. Define the **Eligible Deployment Environments**.

   * If your pipeline is a deployment pipeline, you must select to which environments it should deploy.
-->

1. Dans la section **Code**, définissez les options suivantes :

   * **Référentiel** - cette option définit à partir de quel référentiel GIT le pipeline hors production doit récupérer le code.

     >[!TIP]
     > 
     >Consultez [Ajout et gestion de référentiels](/help/implementing/cloud-manager/managing-code/managing-repositories.md) pour découvrir comment ajouter et gérer des référentiels dans Cloud Manager.

   * **Branche Git** – Cette option définit à partir de quelle branche le pipeline sélectionné doit récupérer le code. Saisissez les premiers caractères du nom de la branche et la fonction de saisie automatique de ce champ. Elle trouve les branches correspondantes que vous pouvez sélectionner.
   * **Emplacement du code** - Cette option définit le chemin d’accès dans la branche du référentiel sélectionné à partir duquel le pipeline doit récupérer le code.

<!--
   * **Pipeline** - For front-end non-production pipelines, you have the option to enable **[Experience Audit](/help/implementing/cloud-manager/reports/report-experience-audit.md)**.
   
   ![Config pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config-deployment-experience-audit.png)
-->

1. Si vous avez activé le contrôle de l’expérience, cliquez sur **Continuer** pour accéder à l’onglet **Contrôle de l’expérience** où vous pouvez définir les chemins qui doivent toujours être inclus dans le contrôle de l’expérience.

   * Si vous avez activé **contrôle de l’expérience**, consultez le document [contrôle de l’expérience](/help/implementing/cloud-manager/reports/report-experience-audit.md) pour plus d’informations sur la configuration.
   * Si ce n’est pas le cas, ignorez cette étape.

1. Cliquez sur **Enregistrer** pour enregistrer le pipeline.

Le pipeline est enregistré et vous pouvez maintenant [gérer vos pipelines](managing-pipelines.md) dans le carte **Pipelines** dans la page **Aperçu du programme**.


## À propos de l’utilisation de la création dynamique dans un pipeline hors production{#about-smart-build-non-production-pipeline}

La **version intelligente** dans Cloud Manager est une stratégie de création optimisée pour les pipelines hors production. La génération intelligente réduit les temps de génération en mettant en cache les modules et en ne reconstruisant que les modules qui ont été modifiés depuis la dernière exécution réussie. Les modules inchangés sont réutilisés à partir du cache, tandis que seuls les modules modifiés et leurs dépendances sont reconstruits, ce qui améliore l’efficacité des workflows de développement itératifs.

La génération intelligente n&#39;est actuellement disponible que pour les éléments suivants :

* Pipelines de la qualité du code.
* Développez des pipelines de déploiement full stack.

>[!NOTE]
>
>La première exécution après l’activation de la création dynamique se comporte comme une création complète, car le cache est vide.

Le build intelligent est recommandé lorsque vous disposez des éléments suivants :

* Vous développez et validez activement des modifications incrémentielles fréquentes.
* Votre projet contient plusieurs modules Maven.
* Les versions complètes prennent beaucoup de temps.

La création intelligente n’est pas toujours idéale lorsque vous disposez des éléments suivants :

* Votre version repose principalement sur des modules externes qui effectuent des opérations en dehors du graphique de dépendance de Maven.
* Vous avez besoin d’une validation de reconstruction complète à chaque exécution.

### Présentation des performances de build{#smart-build-performance}

Le gain de performances de l’utilisation de la création dynamique dépend de plusieurs facteurs, notamment des éléments suivants :

* Nombre de modules dans le projet.
* La fréquence et l’étendue des modifications de code.
* La distribution des dépendances entre les modules.

En règle générale, les projets comportant de nombreux modules indépendants peuvent bénéficier de la plus grande amélioration.

### Désinscription du cache par module{#smart-build-cache-optout}

Smart Build fournit un contrôle affiné qui vous permet de désactiver la mise en cache pour des modules spécifiques. Cette fonctionnalité est utile lorsque certains modules :

* Utilisez des plug-ins, tels que `exec-maven-plugin` ou `maven-antrun-plugin`.
* Effectuer des opérations de fichier non suivies par les dépendances Maven.
* Le contenu mis en cache génère des résultats incohérents.

### Désactiver la mise en cache pour un module{#smart-build-disable-caching}

Vous pouvez ajouter la propriété suivante au `pom.xml` du module concerné :

```xml
<properties>
  <maven.build.cache.enabled>false</maven.build.cache.enabled>
</properties>
```

Cette syntaxe force le module à se recréer à chaque exécution de pipeline tandis que les autres modules continuent à bénéficier de la mise en cache.

### Restrictions et considérations lors de l’utilisation de la création dynamique{#smart-build-limitations}

Gardez les points suivants à l’esprit lorsque vous utilisez la création dynamique :

* Smart Build repose sur l’analyse des dépendances Maven.
* Les modifications en dehors du graphique de dépendance peuvent ne pas déclencher de reconstructions.
* Certains plug-ins peuvent ne pas être entièrement compatibles avec la mise en cache.
* Vous pouvez revenir à la **version complète** à tout moment en modifiant le pipeline hors production.

Si vous rencontrez un comportement de build inattendu, envisagez de désactiver la mise en cache de modules spécifiques ou de changer temporairement votre stratégie de build en **Version complète**.

### Dépannage des problèmes de création dynamique{#smart-build-troubleshoot}

| Problème | Solutions suggérées |
| --- | --- |
| Les résultats de build sont incohérents | · Désactivez la mise en cache pour les modules concernés.<br>· Vérifiez le comportement des plug-ins (en particulier des plug-ins `exec`/`antrun`). |
| Aucune amélioration des performances | · Assurez-vous que plusieurs exécutions ont eu lieu (préchauffage du cache).<br>· Vérifiez si la plupart des modules changent fréquemment. |
| Artefacts inattendus ou modifications manquantes | · Vérifiez si les modifications ne se trouvent pas en dehors du suivi des dépendances Maven.<br>· Utilisez **Version complète** pour la vérification. |

Voir [Ajouter un pipeline hors production](#adding-non-production-pipeline) pour activer la création intelligente.











<!--
## Add a non-production pipeline

Once you have set up your program and have at least one environment using the Cloud Manager UI, you are ready to add a non-production pipeline by following these steps.

{{sign-in-to-cloud-manager}}

1. On the **My Programs** console, click a program. 

1. Access the **Pipelines** card from the Cloud Manager home screen. Click **+Add** and select **Add Non-Production Pipeline**. 

   ![Add non-production pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. On the **Configuration** tab of the **Add Non-Production Pipeline** dialog, select the type of non-production pipeline you with to add.

   * **Code Quality Pipeline** - Create a pipeline that builds your code, runs unit tests, and evaluates code quality but does NOT deploy.
   * **Deployment Pipeline** - Create a pipeline that builds your code, runs unit tests, evaluates code quality, and deploys to an environment.

   ![Add Non-Production pipeline dialog](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. Provide a **Non-Production Pipeline Name** to identify your pipeline along with the following additional information.

   * **Deployment Trigger** - You have the following options when defining the deployment triggers to start the pipeline.
   
     * **Manual** - Use this option to start the pipeline manually.
     * **On Git Changes** - This option starts the CI/CD pipeline whenever commits are added to the configured Git branch. With this option, you can still start the pipeline manually as required.

1. If you choose to create a **Deployment Pipeline**, you must also define the **Important Metric Failures Behavior**.

   * **Ask every time** - This behavior is the default setting and requires manual intervention on any important failure.
   * **Fail Immediately** - If selected, the pipeline is canceled whenever an important failure occurs. It is essentially emulating a user manually rejecting each failure.
   * **Continue Immediately** - If selected, the pipeline procedes automatically whenever an important failure occurs. It is essentially emulating a user manually approving each failure.

1. Click **Continue**.

1. On the **Source Code** tab of the **Add Non-Production Pipeline** dialog, you must select which type of code the pipeline should process.

   * **[Full Stack Code](#full-stack-code)**
   * **[Targeted deployment](#targeted-deployment)**

See [CI/CD Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) for more information about the types of pipelines.

The steps to complete the creation of your non-production pipeline vary depending on the type of source code you selected. Follow the links above to jump to the next section of this document so you can complete the configuration of your pipeline.

### Full Stack Code

A full-stack code pipeline simultaneously deploys back-end and front-end code builds containing one or more AEM server applications along with HTTPD/Dispatcher configuration.

>[!NOTE]
>
>If a full-stack code pipeline exists for the selected environment, this selection is disabled.

To finish the configuration of the full-stack code non-production pipeline, follow these steps.

1. On the **Source Code** tab, you must define the following options.

   * **Eligible Deployment Environments** - If your pipeline is a deployment pipeline, you must select to which environments it should deploy.
   * **Repository** - This option defines from which git repo that the pipeline should retrieve the code.

   >[!TIP]
   > 
   >See [Adding and Managing Repositories](/help/implementing/cloud-manager/managing-code/managing-repositories.md) so you can learn how to add and manage repositories in Cloud Manager.

   * **Git Branch** - This option defines from which branch in the selected pipeline should retrieve the code.
     * Enter the first few characters of the branch name and the auto-complete feature of this field. It helps you find the matching branches that you can select.
   * **Ignore Web Tier Configuration** - When checked, the pipeline does not deploy your web tier configuration.
   * **Pipeline** - If your pipeline is a deployment pipeline, you can choose to run a testing phase. Check the options that you want to enable in this phase. If none of the options are selected, the testing phase is not displayed during the pipeline's run.

     * **Product Functional Testing** - Execute [product functional tests](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing) against the development environment.
     * **Custom Functional Testing** - Execute [custom functional tests](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) against the development environment.
     * **Custom UI Testing** - Execute [custom UI tests](/help/implementing/cloud-manager/ui-testing.md) for custom applications.
     * **Experience Audit** - Execute [Experience Audit](/help/implementing/cloud-manager/reports/report-experience-audit.md)

   ![Full-stack pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. Click **Save**.

The pipeline is saved and you can now [manage your pipelines](managing-pipelines.md) on the **Pipelines** card on the **Program Overview** page.

-->



## Exclure les packages Dispatcher {#exclude-dispatcher-packages}

Si vous souhaitez que les packages Dispatcher soient créés dans votre pipeline mais ne soient pas chargés pour créer du stockage, désactivez la publication. Cela peut raccourcir le temps d’exécution du pipeline.

Ajoutez la configuration suivante à votre fichier de `pom.xml` de projet pour désactiver la publication des packages Dispatcher. Définissez une variable d’environnement dans le conteneur de création Cloud Manager pour indiquer quand ignorer les packages Dispatcher. Le pipeline lit cet indicateur et l’ignore en conséquence.

```xml
<profile>
  <id>only-include-dispatcher-when-it-isnt-ignored</id>
  <activation>
    <property>
      <name>env.IGNORE_DISPATCHER_PACKAGES</name>
      <value>[!NOTE]rue</value>
    </property>
  </activation>
  <modules>
    <module>dispatcher</module>
  </modules>
</profile>
```
