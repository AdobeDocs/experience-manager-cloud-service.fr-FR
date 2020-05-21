---
title: Programmes Sandbox - Service Cloud
description: Programmes Sandbox - Service Cloud
translation-type: tm+mt
source-git-commit: 168b3d28a36e4ec5258b2d2f391af25c466be6c6
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 0%

---


# Programmes Sandbox {#sandbox-programs}

## Présentation {#introduction}

Un programme Sandbox est l’un des deux types de programmes disponibles dans le service AEM Cloud, l’autre étant un programme régulier.

Un sandbox est généralement créé pour servir à la formation, à l’exécution de démonstrations, à l’activation ou au BAT de concept (POC). Ils ne sont pas destinés à transporter du trafic réel.

Les programmes de sandbox comprennent les sites et les ressources et sont automatiquement renseignés avec une branche Git qui comprend un exemple de code, un environnement de développement et un pipeline hors production.

Consultez la section [Présentation des Programmes et des types](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/understand-program-types.html) de Programme pour en savoir plus sur les types de Programme.

### Attributs des Programmes Sandbox {#attributes-sandbox}

Les Programmes Sandbox ont les attributs suivants :

1. **Création de Programme :** La création du programme Sandbox inclut des éléments automatiques :
   * configuration d&#39;un projet avec un exemple de code et de contenu
   * création d&#39;environnement de développement
   * création d&#39;un canal de production non déployé vers l&#39;environnement de développement (branche principale déployée vers l&#39;environnement de développement)

1. **Solutions :** Les programmes de sandbox incluent les sites et ressources AEM.

1. **Mises à jour d’AEM :** Les mises à jour AEM peuvent être appliquées manuellement aux environnements d’un programme Sandbox et ne sont pas automatiquement poussées.

1. **Hibernation :** Les Environnements d’un programme Sandbox sont automatiquement mis en veille prolongée si aucune activité n’est détectée pendant une certaine période. Les environnements en veille prolongée peuvent être désactivés manuellement.

### Création d’un Programme Sandbox {#creating-sandbox-program}

Un assistant de création de programme vous permet de créer un Programme Sandbox.

Pour savoir comment créer un Programme Sandbox, consultez [Création d’un Programme](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/creating-a-program.html#create-demo-program)Sandbox.

### Création d’Environnements de sandbox {#creating-sandbox-environments}

Les Programmes Sandbox reçoivent un environnement de développement au moment de la création du programme de manière automatique. L’environnement de développement comprend par défaut un niveau d’auteur et de publication.

Le jeu d&#39;environnements de la phase de production peut être ajouté manuellement au Programme Sandbox lorsque l&#39;utilisateur est prêt à configurer un pipeline de production.

Pour savoir comment créer manuellement un environnement, voir [Ajout d’Environnements](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#adding-environments) pour plus d’informations.

### Suppression d&#39;Environnements de sandbox  {#deleting-sandbox-environments}

L’utilisateur disposant des autorisations requises peut supprimer un ou plusieurs environnements de développement ou de production/étape.

Pour supprimer un environnement, reportez-vous à la section [Suppression d’Environnements](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#deleting-environment) pour plus d’informations.


## Mise en hibernation et déshibernation des Environnements de sandbox {#hibernating-introduction}

Les environnements de Programme Sandbox passent en mode ** hibernation si aucune activité n’est détectée pendant une certaine période.

>[!NOTE]
>L&#39;hibernation est unique aux environnements de Programme Sandbox. Les environnements de programme réguliers n&#39;hibernent pas.

### Hibernation {#hibernation-introduction}

La mise en veille prolongée peut se produire automatiquement ou manuellement. Les environnements de Programme Sandbox peuvent prendre jusqu’à quelques minutes pour passer en mode *d’* hibernation. Les données sont conservées pendant l’hibernation.

L’hibernation est classée comme suit :

* **Les environnements de Programme de sandbox automatiques** sont automatiquement mis en veille prolongée après huit heures d’inactivité, ce qui signifie que ni l’auteur ni les services de publication ne reçoivent de demande.

* **Manuel**: En tant qu’utilisateur, vous pouvez mettre en veille prolongée manuellement un environnement de Programme Sandbox, bien qu’il n’y ait aucune obligation de le faire, car l’hibernation se produit automatiquement après une certaine période (huit heures) d’inactivité.

#### Utilisation de la mise en veille prolongée manuelle {#using-manual-hibernation}

Vous pouvez mettre en veille prolongée manuellement votre Programme Sandbox à partir de la Console développeur de deux manières différentes, à l’aide des éléments suivants :

* Écran des détails de l&#39;Environnement
* Ecran de liste des Environnements

Suivez les étapes ci-dessous pour mettre en veille prolongée manuellement vos environnements de Programme Sandbox :

1. Accédez à la Console ****développeur.
Consultez [Accès à la Console](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#accessing-developer-console) développeur pour savoir comment accéder à la Console **** développeur à partir de la carte **Environnements** .

1. Cliquez sur Mettre en veille prolongée, comme illustré dans la figure ci-dessous.

   ![](assets/hibernate-1.png)
1. Cliquez sur **Mettre en veille prolongée** pour confirmer l’étape.

   ![](assets/hibernate-2.png)

1. Une fois l’hibernation terminée, vous verrez la notification complète du processus d’hibernation pour votre environnement dans l’écran Console **** développeur.

   ![](assets/hibernate-4.png)

#### Accès à un Environnement mis en veille prolongée {#accessing-hibernated-environment}

Lors de toute requête de navigateur à l’encontre de la couche d’auteur ou de publication d’un environnement en hibernation, l’utilisateur rencontre un landing page décrivant l’état en hibernation de l’environnement, comme illustré ci-dessous :

Un utilisateur disposant de **Cloud Manager - Developer Role** peut cliquer sur le bouton Developer Console pour accéder à la console de développement et annuler la mise en veille prolongée de l’environnement. Vous trouverez des informations sur la définition des rôles dans la documentation de Cloud Manager.

Si un utilisateur d’une organisation ne peut pas cliquer sur le bouton Console développeur pour accéder à la Console développeur, il est probable qu’il lui faille se voir attribuer le &quot;Rôle développeur de Cloud Manager&quot;.


### Déhibernation {#de-hibernation-introduction}

1. Accédez à la Console ****développeur.
Consultez [Accès à la Console](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#accessing-developer-console) développeur pour savoir comment accéder à la Console **** développeur à partir de la carte **Environnements** .

   >[!IMPORTANT]
   >L’accès à la Console développeur est défini par le rôle **Développeur de** Cloud Manager dans la Console **d’** administration. Un utilisateur disposant d’une autorisation de rôle de développeur peut désactiver la mise en veille prolongée d’un environnement de Programme Sandbox.

1. Click on **De-hibernate**, as shown in the figure below:

   ![](assets/de-hibernation-img1.png)

1. Cliquez sur **De Hibernate** pour confirmer l’étape.

   ![](assets/de-hibernation-img2.png)

1. Vous recevrez la notification du début du processus de déshibernation et vous serez mis à jour avec la progression.

   ![](assets/de-hibernation-img3.png)

1. Une fois le processus terminé, l’environnement de Programme Sandbox est de nouveau actif.

   ![](assets/de-hibernation-img4.png)


## Mises à jour d’AEM vers les Environnements Sandbox {#aem-updates-sandbox}


Reportez-vous aux mises à jour [de la version](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/deploying/overview.html#version-updates) AEM pour plus d’informations.

Un utilisateur peut appliquer manuellement les mises à jour AEM aux environnements d’un Programme Sandbox (voir la figure ci-dessous). Vous pouvez effectuer cette opération lorsque l’état affiché est **MISE À JOUR DISPONIBLE**.

L’option Mettre à jour est disponible dans le menu déroulant de la carte **Environnements** . Cette option est également disponible à partir du bouton **Gérer** si vous cliquez sur **Détails** dans la carte **Environnements** .

>[!NOTE]
>Un pipeline *de* non-production déployé dans l&#39;environnement de développement intéressant doit être configuré pour qu&#39;un pipeline de mise à jour manuelle puisse être lancé.

>[!NOTE]
>Un pipeline ** de production doit être configuré pour qu&#39;un pipeline de mise à jour manuelle vers l&#39;environnement Production+Phase soit lancé.

>[!NOTE]
>La mise à jour manuelle de *Production* ou de l&#39;environnement *Stage* met automatiquement à jour l&#39;autre. Le jeu d’environnements Production+Phase doit se trouver dans la même version d’AEM.





