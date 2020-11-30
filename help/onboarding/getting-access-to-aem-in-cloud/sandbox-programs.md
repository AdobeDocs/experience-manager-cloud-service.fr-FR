---
title: Programmes Sandbox – Cloud Service
description: Programmes Sandbox – Cloud Service
translation-type: tm+mt
source-git-commit: 8383dc023b35cf76f7dc0e41cedef8cfab7753aa
workflow-type: tm+mt
source-wordcount: '1184'
ht-degree: 97%

---


# Programmes Sandbox {#sandbox-programs}

## Présentation {#introduction}

Un programme Sandbox est l’un des deux types de programmes disponibles dans AEM Cloud Service, l’autre étant un programme régulier.

Un sandbox est généralement créé pour servir à la formation, à l’exécution de démonstrations, à l’activation ou aux preuves de concept (POC). Ces tâches ne sont pas destinées à transporter du trafic en direct. Elles ne sont pas soumises aux [engagements d’AEM as a Cloud Service](https://www.adobe.com/fr/legal/service-commitments.html).

Les environnements créés dans un sandbox ne sont pas configurés pour la mise à l’échelle automatique. Par conséquent, ils ne conviennent pas aux tests de performances ou de charge.

Les programmes Sandbox comprennent les sites et les ressources et sont automatiquement renseignés avec un référentiel Git, un environnement de développement et un pipeline hors production.  Le référentiel Git est renseigné avec un exemple de projet basé sur l’archétype de projet AEM.

Consultez [Présentation des programmes et des types de programmes](/help/onboarding/getting-access-to-aem-in-cloud/understand-program-types.md) pour en savoir plus sur les types de programmes.

### Attributs des programmes Sandbox {#attributes-sandbox}

Les programmes Sandbox possèdent les attributs suivants :

1. **Création de programme :** la création du programme Sandbox inclut des éléments automatiques :
   * Configuration d’un projet avec un exemple de code et de contenu
   * Création d’un environnement de développement
   * Création d’un canal hors production se déployant vers l’environnement de développement (déploiement de branche principale vers l’environnement de développement)

1. **Solutions :** les programmes Sandbox incluent AEM Sites et Assets.

1. **Mises à jour AEM :** les mises à jour AEM peuvent être appliquées manuellement aux environnements d’un programme Sandbox et ne sont pas automatiquement exécutées.

1. **Veille :** les environnements d’un programme Sandbox sont automatiquement mis en veille si aucune activité n’est détectée pendant une certaine période. Les environnements mis en veille peuvent être réactivés manuellement.

### Création d’un programme Sandbox {#creating-sandbox-program}

Un assistant de création de programme vous permet de créer un programme Sandbox.

Pour savoir comment créer un programme Sandbox, consultez [Création d’un programme Sandbox](/help/onboarding/getting-access-to-aem-in-cloud/creating-a-program.md#create-sandbox-program) pour plus d’informations.

### Création d’environnements Sandbox {#creating-sandbox-environments}

Les programmes Sandbox sont livrés de manière automatique dans un environnement de développement au moment de la création du programme. L’environnement de développement comprend par défaut un niveau d’auteur et de publication.

Le jeu d’environnements de production-évaluation peut être ajouté manuellement au programme Sandbox lorsque l’utilisateur est prêt à configurer un pipeline de production.

To learn how to manually create an environment, refer to [Adding Environment](/help/implementing/cloud-manager/manage-environments.md) for more details.

### Suppression d’environnements Sandbox {#deleting-sandbox-environments}

L’utilisateur disposant des autorisations requises peut supprimer un environnement ou un jeu d’environnements de développement ou de production/d’évaluation.

To delete an environment, refer to [Deleting Environment](/help/implementing/cloud-manager/manage-environments.md#deleting-environment) for more details.


## Mise en veille et réactivation d’environnements Sandbox {#hibernating-introduction}

Les environnements de programme Sandbox passent en *mode veille* si aucune activité n’est détectée pendant une certaine période.

>[!NOTE]
>La veille est unique aux environnements de programme Sandbox. Les environnements de programme réguliers ne connaissent pas de veille.

### Mise en veille {#hibernation-introduction}

La mise en veille peut se produire automatiquement ou manuellement. Les environnements de programme Sandbox peuvent prendre jusqu’à quelques minutes pour passer en *mode veille*. Les données sont conservées pendant la veille.

La veille est classée comme suit :

* **Automatique** : les environnements de programme Sandbox sont automatiquement mis en veille après huit heures d’inactivité, ce qui signifie que ni les services de création ni les services de publication ne reçoivent de requêtes.

* **Manuelle** : en tant qu’utilisateur, vous pouvez manuellement mettre en veille un environnement de programme Sandbox, bien qu’il n’y ait aucune obligation de le faire, car le passage en veille se produit automatiquement après une certaine période (huit heures) d’inactivité.

>[!CAUTION]
>Dans la dernière version, l’établissement d’un lien vers Developer Console directement à partir de Cloud Manager ne vous permet pas de mettre en veille un environnement de programme Sandbox. Pour contourner ce problème, dans Developer Console, ajoutez le motif suivant à la fin de l’URL : `#release-cm-p1234-e5678 where 1234` 1234 correspond à votre *ID de programme* et 5678 à votre *ID d’environnement*.

#### Utilisation de la veille manuelle {#using-manual-hibernation}

Vous pouvez mettre votre programme Sandbox en veille manuellement à partir de Developer Console de deux manières différentes, à l’aide des éléments suivants :

* Écran des détails de l’environnement
* Écran de liste des environnements

>[!NOTE]
>Un utilisateur de Cloud Manager peut accéder à Developer Console pour un programme Sandbox.

Suivez les étapes ci-dessous pour mettre vos environnements de programme Sandbox en veille manuellement :

1. Accédez à **Developer Console**.
Consultez [Accès à Developer Console](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console) pour savoir comment accéder à **Developer Console** à partir de la carte **Environnements**.
   >[!IMPORTANT]
   >L’établissement d’un lien vers **Developer Console** directement à partir de Cloud Manager ne vous permet pas de mettre en veille un environnement de programme Sandbox. Pour contourner ce problème, dans Developer Console, ajoutez le motif suivant à la fin de l’URL : `#release-cm-p1234-e5678 where 1234` 1234 correspond à votre *ID de programme* et 5678 à votre *ID d’environnement*.

1. Cliquez sur **Hibernate** (Mettre en veille), comme illustré dans la figure ci-dessous :

   ![](assets/hibernate-1.png)

   Ou,

   Cliquez sur le lien **Environments** (Environnements) en haut à gauche pour afficher la liste des environnements, puis cliquez sur **Hibernate** (Mettre en veille), comme illustré dans la figure ci-dessous :

   ![](assets/hibernate-1b.png)

1. Cliquez sur **Hibernate** (Mettre en veille) pour confirmer l’étape.

   ![](assets/hibernate-2.png)

1. Une fois la veille effective, un message confirmant la fin du processus de mise en veille de votre environnement s’affiche à l’écran de **Developer Console**.

   ![](assets/hibernate-4.png)


### Réactivation{#de-hibernation-introduction}

1. Accédez à **Developer Console**.
Consultez [Accès à Developer Console](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console) pour savoir comment accéder à **Developer Console** à partir de la carte **Environnements**.

   >[!IMPORTANT]
   >L’établissement d’un lien vers **Developer Console** directement à partir de Cloud Manager ne vous permet pas de réactiver un environnement de programme Sandbox. Pour contourner ce problème, dans Developer Console, ajoutez le motif suivant à la fin de l’URL : `#release-cm-p1234-e5678 where 1234` 1234 correspond à votre *ID de programme* et 5678 à votre *ID d’environnement*.

   >[!NOTE]
   >Vous pouvez également accéder à **Developer Console** pour réactiver en essayant d’accéder au service de création ou de publication d’un environnement déjà mis en veille ; dans ce cas, une page d’entrée s’affiche avec un lien vers Developer Console. Reportez-vous à la section Accès à un environnement mis en veille ci-dessous.

   >[!IMPORTANT]
   >L’accès à Developer Console est défini par le **rôle Cloud Manager - Développeur** dans **Admin Console**. Un utilisateur disposant d’une autorisation de rôle de développeur peut réactiver un environnement de programme Sandbox.

1. Cliquez sur **De-hibernate** (Réactiver), comme illustré dans la figure ci-dessous :

   ![](assets/de-hibernation-img1.png)

   Ou,

   Cliquez sur le lien **Environments** (Environnements) en haut à gauche pour afficher la liste des environnements, puis cliquez sur **De-hibernate** (Réactiver), comme illustré dans la figure ci-dessous :

   ![](assets/de-hibernate-1b.png)


1. Cliquez sur **De-hibernate** (Réactiver) pour confirmer l’étape.

   ![](assets/de-hibernation-img2.png)

1. Un message s’affiche confirmant que le processus de réactivation a commencé et vous êtes informé de l’avancée de l’opération.

   ![](assets/de-hibernation-img3.png)

1. Une fois le processus terminé, l’environnement de programme Sandbox redevient actif.

   ![](assets/de-hibernation-img4.png)

#### Autorisations de réactiver {#permissions-de-hibernate}

Tout utilisateur disposant d’un profil de produit qui lui donne accès à AEM as a Cloud Service doit pouvoir accéder à **Developer Console**, qui lui permet de réactiver l’environnement.

#### Accès à un environnement mis en veille {#accessing-hibernated-environment}

Dans le cadre d’une requête de navigateur par rapport au niveau de création ou de publication d’un environnement mis en veille, l’utilisateur rencontre une page d’entrée décrivant l’état de mise en veille de l’environnement, comme indiqué dans la figure ci-dessous :

![](assets/de-hibernation-img5.png)

### Points importants {#important-considerations}

Voici quelques considérations clés liées aux environnements mis en veille et réactivés :

* Un utilisateur peut utiliser un pipeline pour déployer du code personnalisé sur des environnements mis en veille. L’environnement demeure en veille et le nouveau code apparaît dans l’environnement une fois ce dernier réactivé.

* Les mises à niveau d’AEM peuvent être appliquées aux environnements mis en veille, et les clients peuvent les déclencher manuellement à partir de Cloud Manager. L’environnement demeure en veille et la nouvelle version apparaît dans l’environnement une fois ce dernier réactivé.

>[!NOTE]
>Actuellement, Cloud Manager n’indique pas si un environnement est en veille.

## Mises à jour AEM des environnements Sandbox {#aem-updates-sandbox}

Pour plus d’informations, voir [Mises à jour de la version AEM](/help/implementing/deploying/aem-version-updates.md).

Un utilisateur peut appliquer manuellement des mises à jour AEM aux environnements dans un programme Sandbox.

Reportez-vous à [Mise à jour de l’environnement](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment) pour savoir comment mettre à jour un environnement.

>[!NOTE]
>* Une mise à jour manuelle ne peut être exécutée que si l’environnement ciblé dispose d’un pipeline correctement configuré.
>* Une mise à jour manuelle d’un environnement de *production* met automatiquement à jour l’environnement d’*évaluation*, et vice-versa. Le jeu d’environnements Production+Évaluation doit se trouver dans la même version AEM.






