---
title: Programmes Sandbox - Cloud Service
description: Programmes Sandbox - Cloud Service
translation-type: tm+mt
source-git-commit: 8383dc023b35cf76f7dc0e41cedef8cfab7753aa
workflow-type: tm+mt
source-wordcount: '1184'
ht-degree: 0%

---


# Programmes Sandbox {#sandbox-programs}

## Présentation {#introduction}

Un programme Sandbox est l&#39;un des deux types de programmes disponibles en Cloud Service AEM, l&#39;autre étant un programme régulier.

Un sandbox est généralement créé pour servir à la formation, à l’exécution de démonstrations, à l’activation ou au BAT de concept (POC). Ils ne sont pas destinés à transporter du trafic réel. Ils ne sont pas soumis à l&#39; [AEM en tant qu&#39;engagements](https://www.adobe.com/legal/service-commitments.html)Cloud Service.

Les environnements créés dans un Sandbox ne sont pas configurés pour la mise à l’échelle automatique. Par conséquent, ils ne conviennent pas aux tests de performances ou de charge.

Les programmes de sandbox comprennent les sites et les ressources et sont automatiquement renseignés avec un référentiel Git, un environnement de développement et un pipeline de non-production.  Le référentiel Git est renseigné avec un exemple de projet basé sur l&#39;archétype de projet AEM.

Consultez la section [Présentation des Programmes et des types](/help/onboarding/getting-access-to-aem-in-cloud/understand-program-types.md) de Programme pour en savoir plus sur les types de Programme.

### Attributs des Programmes Sandbox {#attributes-sandbox}

Les Programmes Sandbox ont les attributs suivants :

1. **Création de programme :** La création du programme Sandbox inclut des éléments automatiques :
   * configuration d&#39;un projet avec un exemple de code et de contenu
   * création d&#39;environnement de développement
   * création d&#39;un canal de production non déployé vers l&#39;environnement de développement (branche principale déployée vers l&#39;environnement de développement)

1. **Solutions :** Les programmes de sandbox incluent AEM Sites et Assets.

1. **Mises à jour AEM :** aem mises à jour peuvent être appliquées manuellement aux environnements d’un programme Sandbox et ne sont pas automatiquement poussées.

1. **Hibernation :** Les Environnements d’un programme Sandbox sont automatiquement mis en veille prolongée si aucune activité n’est détectée pendant une certaine période. Les environnements en veille prolongée peuvent être désactivés manuellement.

### Création d’un Programme Sandbox {#creating-sandbox-program}

Un assistant de création de programme vous permet de créer un Programme Sandbox.

Pour savoir comment créer un Programme Sandbox, consultez [Création d’un Programme](/help/onboarding/getting-access-to-aem-in-cloud/creating-a-program.md#create-sandbox-program) Sandbox pour plus d’informations.

### Création d’Environnements de sandbox {#creating-sandbox-environments}

Les Programmes Sandbox sont livrés à un environnement de développement au moment de la création du programme de manière automatique. L’environnement de développement comprend par défaut un niveau d’auteur et de publication.

Le jeu d&#39;environnements de la phase de production peut être ajouté manuellement au Programme Sandbox lorsque l&#39;utilisateur est prêt à configurer un pipeline de production.

Pour savoir comment créer manuellement un environnement, reportez-vous à la section Environnement [](/help/implementing/cloud-manager/manage-environments.md) Ajoutant pour plus de détails.

### Suppression d&#39;Environnements de sandbox {#deleting-sandbox-environments}

L’utilisateur disposant des autorisations requises peut supprimer un ou plusieurs environnements de développement ou de production/étape.

Pour supprimer un environnement, reportez-vous à la section [Suppression d’Environnement](/help/implementing/cloud-manager/manage-environments.md#deleting-environment) pour plus d’informations.


## Mise en hibernation et déshibernation des Environnements de sandbox {#hibernating-introduction}

Les environnements de Programme Sandbox passent en mode ** hibernation si aucune activité n’est détectée pendant une certaine période.

>[!NOTE]
>L&#39;hibernation est unique aux environnements de Programme Sandbox. Les environnements de programme réguliers n&#39;hibernent pas.

### Hibernation {#hibernation-introduction}

La mise en veille prolongée peut se produire automatiquement ou manuellement. Les environnements de Programme Sandbox peuvent prendre jusqu’à quelques minutes pour passer en mode *d’* hibernation. Les données sont conservées pendant l’hibernation.

L’hibernation est classée comme suit :

* **Les environnements de Programme de sandbox automatiques** sont automatiquement mis en veille prolongée après huit heures d’inactivité, ce qui signifie que ni les services d’auteur ni de publication ne reçoivent de demandes.

* **Manuel**: En tant qu’utilisateur, vous pouvez mettre en veille prolongée manuellement un environnement de Programme Sandbox, bien qu’il n’y ait aucune obligation de le faire, car l’hibernation se produit automatiquement après une certaine période (huit heures) d’inactivité.

>[!CAUTION]
>Dans la dernière version, la création de liens vers la Console développeur directement à partir de Cloud Manager ne vous permet pas d’hiberner un environnement de Programme Sandbox. La solution consiste à ajouter le modèle suivant à la fin de l’URL `#release-cm-p1234-e5678 where 1234` 1234 correspond à votre ID *de* Programme et 5678 à votre ID *d’* Environnement.

#### Utilisation de la mise en veille prolongée manuelle {#using-manual-hibernation}

Vous pouvez mettre en veille prolongée manuellement votre Programme Sandbox à partir de la Console développeur de deux manières différentes, à l’aide des éléments suivants :

* Écran des détails de l&#39;Environnement
* Ecran de liste des Environnements

>[!NOTE]
>Tout utilisateur de Cloud Manager peut accéder à Developer Console pour un Programme Sandbox.

Suivez les étapes ci-dessous pour mettre en veille prolongée manuellement vos environnements de Programme Sandbox :

1. Accédez à la Console ****développeur.
Consultez [Accès à la Console](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console) développeur pour savoir comment accéder à la Console **** développeur à partir de la carte **Environnements** .
   >[!IMPORTANT]
   >La création d’un lien vers la Console **** développeur directement à partir de Cloud Manager ne vous permet pas de mettre en veille prolongée un environnement de Programme Sandbox. La solution consiste à ajouter le modèle suivant à la fin de l’URL `#release-cm-p1234-e5678 where 1234` 1234 correspond à votre ID *de* Programme et 5678 à votre ID *d’* Environnement.

1. Click **Hibernate**, as shown in the figure below:

   ![](assets/hibernate-1.png)

   Ou,

   Cliquez sur le lien **Environnements** en haut à gauche pour vue de la liste des environnements, puis cliquez sur **Mettre en veille prolongée**, comme illustré dans la figure ci-dessous :

   ![](assets/hibernate-1b.png)

1. Cliquez sur **Mettre en veille prolongée** pour confirmer l’étape.

   ![](assets/hibernate-2.png)

1. Une fois l’hibernation terminée, vous verrez la notification complète du processus d’hibernation pour votre environnement dans l’écran Console **** développeur.

   ![](assets/hibernate-4.png)


### Déhibernation {#de-hibernation-introduction}

1. Accédez à la Console ****développeur.
Consultez [Accès à la Console](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console) développeur pour savoir comment accéder à la Console **** développeur à partir de la carte **Environnements** .

   >[!IMPORTANT]
   >La création d’un lien vers la Console **** développeur directement à partir de Cloud Manager ne vous permet pas de désactiver l’option de dé-hibernation d’un environnement de Programme Sandbox. La solution consiste à ajouter le modèle suivant à la fin de l’URL `#release-cm-p1234-e5678 where 1234` 1234 correspond à votre ID *de* Programme et 5678 à votre ID *d’* Environnement.

   >[!NOTE]
   >Vous pouvez également accéder à la Console **** développeur pour annuler la mise en veille prolongée en essayant d’accéder au service d’auteur ou de publication d’un environnement déjà mis en veille prolongée ; dans ce cas, un landing page s’affiche avec un lien vers la Console développeur. Voir la section Accès à un Environnement mis en veille prolongée ci-dessous.

   >[!IMPORTANT]
   >L’accès à la Console développeur est défini par le rôle **Développeur de** Cloud Manager dans le **Admin Console**. Un utilisateur disposant d’une autorisation de rôle de développeur peut désactiver la mise en veille prolongée d’un environnement de Programme Sandbox.

1. Click on **De-hibernate**, as shown in the figure below:

   ![](assets/de-hibernation-img1.png)

   Ou,

   Cliquez sur le lien **Environnements** en haut à gauche pour vue de la liste des environnements, puis cliquez sur **Déhibernate**, comme illustré dans la figure ci-dessous.

   ![](assets/de-hibernate-1b.png)


1. Cliquez sur **De Hibernate** pour confirmer l’étape.

   ![](assets/de-hibernation-img2.png)

1. Vous recevrez la notification du début du processus de déshibernation et vous serez mis à jour avec la progression.

   ![](assets/de-hibernation-img3.png)

1. Une fois le processus terminé, l&#39;environnement de Programme Sandbox est à nouveau principal.

   ![](assets/de-hibernation-img4.png)

#### Autorisations de déshibernation {#permissions-de-hibernate}

Tout utilisateur disposant d’un profil de produit qui lui donne accès à AEM en tant que Cloud Service doit pouvoir accéder à la Console **développeur**, ce qui lui permet de dé-hiberner l’environnement.

#### Accès à un Environnement mis en veille prolongée {#accessing-hibernated-environment}

Lors de toute requête de navigateur à l’encontre de la couche d’auteur ou de publication d’un environnement mis en veille prolongée, l’utilisateur rencontre un landing page décrivant l’état mis en veille prolongée de l’environnement, comme indiqué dans la figure ci-dessous :

![](assets/de-hibernation-img5.png)

### Points importants {#important-considerations}

Peu de considérations clés liées aux environnements en hibernation et en hibernation sont les suivantes :

* Un utilisateur peut utiliser un pipeline pour déployer du code personnalisé sur des environnements mis en veille prolongée. L’environnement reste en hibernation et le nouveau code apparaît dans l’environnement une fois déshiberné.

* aem mises à niveau peuvent être appliquées aux environnements en veille prolongée, que les clients peuvent déclencher manuellement à partir de Cloud Manager. L’environnement reste en hibernation et la nouvelle version apparaît dans l’environnement une fois l’hibernation terminée.

>[!NOTE]
>Actuellement, Cloud Manager n’indique pas si un environnement est mis en veille prolongée.

## aem mises à jour des Environnements Sandbox {#aem-updates-sandbox}

Refer to [AEM version updates](/help/implementing/deploying/aem-version-updates.md) for more details.

Un utilisateur peut manuellement appliquer AEM mises à jour aux environnements dans un Programme Sandbox.

Reportez-vous à [Mise à jour de l’Environnement](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment) pour savoir comment mettre à jour un environnement.

>[!NOTE]
>* Une mise à jour manuelle ne peut être exécutée que si l&#39;environnement ciblé dispose d&#39;un pipeline correctement configuré.
>* Une mise à jour manuelle de *Production* ou de l’environnement *Stage* met automatiquement à jour l’autre. Le jeu d’environnements Production+Phase doit se trouver dans la même version AEM.






