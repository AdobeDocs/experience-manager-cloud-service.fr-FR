---
title: Configuration du pipeline CI/CD – Cloud Services
description: Configuration du pipeline CI/CD – Cloud Services
exl-id: d2024b42-9042-46a0-879e-110b214c7285
source-git-commit: 03c058c17e8a9ff5a0be9203a65207bb367a02a6
workflow-type: tm+mt
source-wordcount: '1402'
ht-degree: 37%

---

# Configuration du pipeline CI-CD {#configure-ci-cd-pipeline}

Dans Cloud Manager, il existe deux types de pipeline :

* **Pipeline de production** :

   Un pipeline de production ne peut être ajouté qu’une fois qu’un ensemble d’environnements de production et d’évaluation est créé.

   Pour plus d’informations, voir [Configuration d’un pipeline de production](configure-pipeline.md#setting-up-the-pipeline).

* **Pipeline hors production** :

   Vous pouvez ajouter un pipeline hors production à partir de la page **Aperçu** de l’interface utilisateur de Cloud Manager.

   Pour plus d’informations, consultez [Pipelines hors production et dédiés à la qualité du code](configure-pipeline.md#non-production-pipelines).

   >[!NOTE]
   >Pour configurer votre pipeline, vous devez :
   > * définir le déclencheur qui le démarrera ;
   > * définir les paramètres qui contrôlent le déploiement en production ;
   > * configurer les paramètres de test de performance.


## Configuration d’un pipeline de production {#setting-up-production-pipeline}

Le responsable de déploiement est chargé de la configuration du pipeline de production.

>[!NOTE]
>Un pipeline de production ne peut être configuré que lorsqu’un programme a été créé, que si le référentiel Git comporte au moins une branche et que si un ensemble d’environnements de production et d’évaluation a été créé.

Avant de commencer le déploiement du code, vous devez configurer les paramètres de votre pipeline à partir de [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Vous pouvez modifier les paramètres du pipeline après la configuration initiale.

### Ajout d’un nouveau pipeline de production {#adding-production-pipeline}

Une fois que vous avez configuré votre programme et que vous disposez au moins d’un environnement à l’aide de l’interface utilisateur [!UICONTROL Cloud Manager], vous êtes prêt à ajouter un pipeline de production.

Pour configurer le comportement et les préférences de votre pipeline de production, procédez comme suit :

1. Accédez à la carte **Pipelines** à partir de la page **Aperçu du programme**.
Cliquez sur **+Ajouter** et sélectionnez **Ajouter un pipeline de production**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. **La boîte de dialogue Ajouter un** pipeline de production s’affiche. Saisissez le nom du pipeline.

   De plus, vous pouvez également configurer **Déclencheur de déploiement** et **Comportement d’échec des mesures importantes** à partir des **Options de déploiement**. Cliquez sur **Continuer**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-add2.png)


   Vous pouvez définir les déclencheurs de déploiement pour démarrer le pipeline.

   * **Manuel** : l’utilisation de l’interface lance le pipeline manuellement.
   * **Lors des modifications Git** : démarre le pipeline CI/CD chaque fois que des validations sont ajoutées à la branche git configurée. Même si vous sélectionnez cette option, vous pouvez toujours démarrer le pipeline manuellement.

      Lors de la configuration ou de la modification du pipeline, le responsable de déploiement peut définir le comportement du pipeline en cas d’échec important à l’un des points de contrôle qualité.

      Cela s’avère utile pour les clients qui souhaitent davantage de processus automatisés. Les options disponibles sont les suivantes :
   Vous pouvez définir le comportement important des mesures d’échec pour démarrer le pipeline.

   * **Demander à chaque fois** : il s’agit du paramètre par défaut, qui nécessite une intervention manuelle lors de n’importe quel échec important.
   * **Échec immédiatement**  : si cette option est sélectionnée, le pipeline est annulé chaque fois qu’un échec important se produit. Cette option émule essentiellement un utilisateur rejetant manuellement chaque échec.
   * **Continuer immédiatement**  : si cette option est sélectionnée, le pipeline se poursuit automatiquement chaque fois qu’un échec important se produit. Cette option émule essentiellement la validation manuelle de l’utilisateur à chaque échec.


1. La boîte de dialogue **Ajouter un pipeline de production** comprend un second onglet intitulé **Code source**. **Codage de pile complet** sélectionné. Vous pouvez choisir le **référentiel** et la **branche Git**. Sélectionnez les options de déploiement en production, comme expliqué ci-dessous. Cliquez sur **Continuer**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-fullstack1.png)

   Options de déploiement en production :

   * **Mettre en pause avant le déploiement en production** : Cette option permet de suspendre l’étape de déploiement avant la production.
   * **Planifié** : Cette option permet à l’utilisateur d’activer le déploiement en production planifié.

1. La boîte de dialogue **Ajouter un pipeline de production** comprend un troisième onglet intitulé **Audit de l’expérience**. Cette option fournit un tableau pour les chemins d’URL qui doivent toujours être inclus dans le contrôle de l’expérience.

   >[!NOTE]
   >Vous devez cliquer sur **Ajouter une page** pour définir votre propre lien personnalisé.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit.png)

   Cliquez sur **Ajouter une nouvelle page** pour fournir un chemin d’URL à inclure dans le contrôle de l’expérience.

   Par exemple, si vous souhaitez inclure `https://wknd.site/us/en/about-us.html` dans le contrôle de l’expérience, entrez le chemin `us/en/about-us.html` dans ce champ et cliquez sur **Sauvegarder**.

   ![](assets/exp-audit4.png)

   L’URL qui apparaît dans le tableau présente les caractéristiques suivantes :

   `https://publish-p14253-e43686.adobeaemcloud.com/us/en/about-us.html`

   ![](assets/exp-audit5.png)

   25 lignes au maximum peuvent être incluses. Si aucune page n’est envoyée par l’utilisateur dans cette section, la page d’accueil du site est incluse par défaut dans le contrôle de l’expérience.

   Pour plus d’informations, voir [Compréhension des résultats du contrôle de l’expérience](/help/implementing/cloud-manager/experience-audit-testing.md).

   >[!NOTE]
   > Les pages configurées sont envoyées au service et évaluées en fonction des tests de performances, d’accessibilité, d’optimisation du moteur de recherche (SEO), de bonnes pratiques et d’application web progressive (PWA).

1. Cliquez sur **Enregistrer**. Le nouveau pipeline de production s’affiche désormais dans la carte **Pipelines** .

   Le pipeline s’affiche sur la carte de l’écran d’accueil avec trois actions, comme illustré ci-dessous :

   * **Ajouter**  : permet d’ajouter un nouveau pipeline.
   * **Accéder aux informations sur le référentiel**  : permet à l’utilisateur d’obtenir les informations nécessaires pour accéder au référentiel Git de Cloud Manager.
   * **En savoir plus** : suivez ce lient pour en savoir plus sur les ressources de documentation du pipeline CI/CD.

### Modification d’un pipeline de production {#editing-prod-pipeline}

Vous pouvez modifier les configurations de pipeline à partir de la page **Aperçu du programme**.

Pour modifier le pipeline configuré, procédez comme suit :

1. Accédez à la carte **Pipelines** à partir de la page **Aperçu du programme**.

1. Cliquez sur **...** à partir de la carte **Pipelines** et cliquez sur **Modifier**, comme illustré dans la figure ci-dessous.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit1.png)

1. La boîte de dialogue **Modifier le pipeline de production** s’affiche.

   1. L’onglet **Configuration** vous permet de mettre à jour le **Nom du pipeline**, **Déclencheur de déploiement** et **Comportement d’échec des mesures importantes**.

      >[!NOTE]
      >Voir [Ajout et gestion des référentiels](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) pour savoir comment ajouter et gérer des référentiels dans Cloud Manager.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit2.png)


   1. L’onglet **Source** vous permet de cocher ou de décocher les options **Mettre en pause avant le déploiement en production** et **Planifié** à partir des **Options de déploiement en production**.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-editnotier.png)

   1. L’option **Audit de l’expérience** vous permet de mettre à jour ou d’ajouter de nouvelles pages.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit4.png)

1. Cliquez sur **Mettre à jour** une fois la modification du pipeline terminée.

### Autres actions de pipeline de production {#additional-prod-actions}

#### Exécution d’un pipeline de production {#run-prod}

Vous pouvez exécuter le pipeline de production à partir de la carte Pipelines :

1. Accédez à la carte **Pipelines** à partir de la page **Aperçu du programme**.

1. Cliquez sur **...** à partir de la carte **Pipelines** et cliquez sur **Exécuter**, comme illustré dans la figure ci-dessous.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-run.png)

#### Suppression d’un pipeline de production {#delete-prod}

Vous pouvez supprimer le pipeline de production de la carte Pipelines :

1. Accédez à la carte **Pipelines** à partir de la page **Aperçu du programme**.

1. Cliquez sur **...** dans la carte **Pipelines** et cliquez sur **Supprimer**, comme illustré dans la figure ci-dessous.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-delete.png)

   >[!NOTE]
   >Un utilisateur disposant du rôle Gestionnaire de déploiement peut désormais supprimer le pipeline de production en libre-service via l’option **Supprimer** de la carte Pipeline.


## Pipelines de qualité de code et hors production uniquement {#non-production-pipelines}

En plus du pipeline principal qui se déploie vers les environnements intermédiaire et de production, les clients peuvent configurer des pipelines supplémentaires, appelés **Pipelines hors production**. Ces pipelines exécutent toujours les étapes de génération et de qualité de code. Il peut également être déployé dans AEM environnement as a Cloud Service.

### Ajout d’un nouveau pipeline hors production {#adding-non-production-pipeline}

Sur l’écran d’accueil, ces pipelines sont répertoriés dans une nouvelle carte :

1. Accédez à la carte **Pipelines** à partir de l’écran d’accueil de Cloud Manager. Cliquez sur **+Ajouter** et sélectionnez **Ajouter un pipeline hors production**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. **La boîte de dialogue Ajouter un**  pipeline hors production s’affiche. Sélectionnez le type de pipeline que vous souhaitez créer, **Pipeline de qualité du code** ou **Pipeline de déploiement**.

   De plus, vous pouvez également configurer **Déclencheur de déploiement** et **Comportement d’échec des mesures importantes** à partir des **Options de déploiement**. Cliquez sur **Continuer**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add2.png)

1. **Codage de pile complet** sélectionné. Vous pouvez choisir le **référentiel** et la **branche Git**. Cliquez sur **Enregistrer**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add3.png)

1. Le nouveau pipeline hors production s’affiche désormais dans la carte **Pipelines** .

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add4.png)


   Le pipeline s’affiche sur la carte de l’écran d’accueil avec trois actions, comme illustré ci-dessous :

   * **Ajouter**  : permet d’ajouter un nouveau pipeline.
   * **Accéder aux informations sur le référentiel**  : permet à l’utilisateur d’obtenir les informations nécessaires pour accéder au référentiel Git de Cloud Manager.
   * **En savoir plus** : suivez ce lient pour en savoir plus sur les ressources de documentation du pipeline CI/CD.

### Modification d’un pipeline hors production {#editing-nonprod-pipeline}

Vous pouvez modifier les configurations de pipeline à partir de la carte **Pipelines** de la page **Aperçu du programme**.

Suivez les étapes ci-dessous pour modifier le pipeline hors production configuré :

1. Accédez à la carte **Pipelines** à partir de la page **Aperçu du programme**.

1. Sélectionnez le pipeline hors production et cliquez sur **...**. Cliquez sur **Modifier**, comme illustré dans la figure ci-dessous.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit1.png)

1. La boîte de dialogue **Modifier le pipeline de production** s’affiche.

   1. L’onglet **Configuration** vous permet de mettre à jour le **Nom du pipeline**, **Déclencheur de déploiement** et **Comportement des échecs de mesure importants**.

      >[!NOTE]
      >Voir [Ajout et gestion des référentiels](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) pour savoir comment ajouter et gérer des référentiels dans Cloud Manager.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit2.png)


   1. L’onglet **Code source** vous permet de mettre à jour le **Référentiel** et la **Branche Git**.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit3.png)

1. Cliquez sur **Mettre à jour** une fois la modification du pipeline hors production terminée.

### Autres actions de pipeline hors production {#additional-nonprod-actions}

#### Exécution d’un pipeline hors production {#run-nonprod}

Vous pouvez exécuter le pipeline de production à partir de la carte Pipelines :

1. Accédez à la carte **Pipelines** à partir de la page **Aperçu du programme**.

1. Cliquez sur **...** à partir de la carte **Pipelines** et cliquez sur **Exécuter**, comme illustré dans la figure ci-dessous.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-run1.png)

#### Suppression d’un pipeline hors production {#delete-nonprod}

Vous pouvez supprimer le pipeline de production de la carte Pipelines :

1. Accédez à la carte **Pipelines** à partir de la page **Aperçu du programme**.

1. Cliquez sur **...** dans la carte **Pipelines** et cliquez sur **Supprimer**, comme illustré dans la figure ci-dessous.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-delete.png)


## Étapes suivantes {#the-next-steps}

Une fois que vous avez configuré le pipeline, vous devez déployer votre code.

Pour plus d’informations, consultez [Déploiement de votre code](deploy-code.md).
