---
title: Programmes Sandbox - Service Cloud
description: Programmes Sandbox - Service Cloud
translation-type: tm+mt
source-git-commit: eb874176c71d7f3d03d953f7bae4cb3db2ffb3b9
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 0%

---


# Programmes Sandbox {#sandbox-programs}

## Présentation {#introduction}

Un programme Sandbox est l’un des deux types de programmes disponibles dans le service AEM Cloud, l’autre étant un programme régulier.

Un sandbox est généralement créé pour répondre aux besoins de la formation, de l’exécution de démos, de l’activation ou des points de vue. Ils ne sont pas destinés à transporter du trafic réel.

Les programmes de sandbox comprennent les sites et les ressources et seront livrés automatiquement avec une branche Git comprenant un exemple de code, un environnement de développement et un pipeline non productif.

Pour plus d&#39;informations sur les types de programme, consultez [Présentation des Programmes et des types](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/understand-program-types.html)de Programme.

### Attributs des Programmes Sandbox {#attributes-sandbox}

Les Programmes Sandbox ont les attributs suivants :

1. **Création de Programme :** La création du programme Sandbox inclut des éléments automatiques :
   * configuration d&#39;un projet avec un exemple de code et de contenu
   * création d&#39;environnement de développement
   * création d&#39;un canal de production non déployé vers l&#39;environnement de développement (direction générale du déploiement vers l&#39;environnement de développement)

1. **Les solutions incluent :** Les programmes de sandbox comprennent les sites et les ressources.

1. **Mises à jour d’AEM :** Les mises à jour AEM peuvent être appliquées manuellement aux environnements d’un programme Sandbox et ne sont pas automatiquement poussées.

1. **Hibernation :** Les Environnements d’un programme Sandbox sont automatiquement mis en veille prolongée si aucune activité n’est détectée pendant une certaine période. Les environnements en veille prolongée peuvent être désactivés manuellement.

### Création d’un programme Sandbox {#creating-sandbox-program}

Un assistant de création de programme demande à l&#39;utilisateur d&#39;envoyer des détails.

Pour plus d’informations sur la création d’un programme de sandbox, voir [Création d’un Programme](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/creating-a-program.html#create-demo-program)de sandbox.

### Création d’Environnements de sandbox {#creating-sandbox-environments}

Les programmes Sandbox seront livrés avec un environnement de développement au moment de la création du programme de manière automatique. L’environnement de développement est fourni par défaut avec un niveau d’auteur et de publication.

Le jeu d&#39;environnements de la phase de production peut être ajouté manuellement au programme Sandbox lorsque l&#39;utilisateur est prêt à configurer un pipeline de production.

Pour plus d’informations sur la création manuelle d’un environnement, voir [Ajout d’Environnements](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#adding-environments).

### Suppression d&#39;Environnements de sandbox  {#deleting-sandbox-environments}

L&#39;utilisateur disposant des autorisations requises peut supprimer un environnement/ensemble de développement ou de production/étape.

Pour plus d&#39;informations sur la suppression d&#39;un environnement, consultez [Suppression d&#39;Environnements](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#deleting-environment).


## Mise en hibernation et déshibernation des Environnements de sandbox {#hibernating-introduction}

Les environnements de programme Sandbox entrent en mode ** hibernation après une période d’inactivité.

>[!NOTE]
>L’hibernation est propre aux environnements de programme de sandbox. Les environnements de programme réguliers ne seront pas mis en hibernation.

### Hibernation {#hibernation-introduction}

La mise en veille prolongée peut se produire automatiquement ou manuellement. L&#39;hibernation d&#39;un environnement peut prendre jusqu&#39;à quelques minutes. Les données sont conservées pendant l’hibernation.

L’hibernation est classée comme suit :

* **Les environnements de programme de sandbox automatiques** sont automatiquement mis en veille prolongée après huit heures d’inactivité, ce qui signifie que ni l’auteur ni les services de publication ne reçoivent de demande.

* **Manuel**: Les clients peuvent mettre en veille prolongée manuellement un environnement de programme sandbox, bien qu’il n’y ait aucune obligation à cet égard, car l’hibernation se produit automatiquement après une période d’inactivité.

#### Utilisation de la mise en veille prolongée manuelle {#using-manual-hibernation}


La mise en veille prolongée manuelle peut être effectuée à partir de l’un des deux écrans de la console de développement.

Suivez les étapes ci-dessous pour mettre en veille prolongée manuellement vos environnements d’programme :

1. Accédez à la Console développeur.
1. Cliquez sur Mettre en veille prolongée.
1. Cliquez sur Mettre en veille prolongée pour confirmer.
1. Lorsque l’hibernation est réussie, l’écran suivant s’affiche.
1. Dans l’écran des listes d’environnements, illustré ci-dessous et accessible en cliquant sur le lien Environnements de l’écran des détails de l’environnement, vous pouvez cliquer sur le bouton Mettre en veille prolongée dans la ligne de l’environnement prévu. Un écran de confirmation s’affiche alors.

### Déhibernation {#de-hibernation-introduction}

>[!IMPORTANT]
>L’accès à la Console développeur est défini par &quot;Cloud Manager - Developer Role&quot; (Rôle du développeur) dans la Console d’administration. Avec cette autorisation, un utilisateur peut dé-hiberner un environnement.

### Accès à un Environnement mis en veille prolongée {#accessing-hibernated-environment}

Lors de toute requête de navigateur à l’encontre de la couche d’auteur ou de publication d’un environnement en hibernation, l’utilisateur rencontre un landing page décrivant l’état en hibernation de l’environnement, comme illustré ci-dessous :

Un utilisateur doté du &quot;Cloud Manager - Developer Role&quot; peut cliquer sur le bouton de la Console développeur pour accéder à la console développeur et annuler la mise en veille prolongée de l’environnement. Vous trouverez des informations sur la définition des rôles dans la documentation de Cloud Manager.

Si un utilisateur d’une organisation ne peut pas cliquer sur le bouton Console développeur pour accéder à la Console développeur, il est probable qu’il lui faille se voir attribuer le &quot;Rôle développeur de Cloud Manager&quot;.




## Mises à jour d’AEM vers les environnements Sandbox {#aem-updates-sandbox}


Reportez-vous aux mises à jour des [versions d’](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/deploying/overview.html#version-updates)AEM.

L’utilisateur peut appliquer manuellement les mises à jour AEM aux environnements d’un programme Sandbox (voir la figure ci-dessous). Vous pouvez effectuer cette opération lorsque l’état affiché est MISE À JOUR DISPONIBLE. L&#39;option Mettre à jour sera disponible dans le menu déroulant de la carte Environnements. Il peut également être sélectionné dans le menu Gérer de l’écran ENVIRONNEMENTS.

>[!NOTE]
>Un pipeline de non-production déployé vers l&#39;environnement de développement intéressant doit être configuré pour qu&#39;un pipeline de mise à jour manuelle soit lancé.

>[!NOTE]
>Un pipeline de production doit être configuré pour qu’un pipeline de mise à jour manuelle de l’environnement Production+Stage soit lancé.

>[!NOTE]
>La mise à jour manuelle vers Production ou environnement d’étape met automatiquement à jour l’autre. Le jeu d’environnements Production+Phase doit se trouver dans la même version d’AEM.





