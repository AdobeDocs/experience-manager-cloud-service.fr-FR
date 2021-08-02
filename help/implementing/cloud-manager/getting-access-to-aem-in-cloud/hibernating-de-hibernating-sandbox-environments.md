---
title: 'Mise en veille et réactivation d’environnements Sandbox '
description: Mise en veille et réactivation d’environnements Sandbox
exl-id: c0771078-ea68-4d0d-8d41-2d9be86408a4
source-git-commit: 09d5d125840abb6d6cc5443816f3b2fe6602459f
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 88%

---

# Mise en veille et réactivation d’environnements Sandbox {#hibernating-introduction}

Les environnements de programme Sandbox passent en *mode veille* si aucune activité n’est détectée pendant une certaine période.

>[!NOTE]
>La veille est unique aux environnements de programme Sandbox. Les environnements de programme de production ne connaissent pas de veille.

## Mise en veille {#hibernation-introduction}

La mise en veille peut se produire automatiquement ou manuellement. Les environnements de programme Sandbox peuvent prendre jusqu’à quelques minutes pour passer en *mode veille*. Les données sont conservées pendant la veille.

La veille est classée comme suit :

* ****  Les environnements de programme d’environnement de test automatique sont automatiquement mis en veille après huit heures d’inactivité, ce qui signifie que ni les services de création, ni de prévisualisation ni de publication ne reçoivent de requêtes.

* **Manuelle** : en tant qu’utilisateur, vous pouvez manuellement mettre en veille un environnement de programme Sandbox, bien qu’il n’y ait aucune obligation de le faire, car le passage en veille se produit automatiquement après une certaine période (huit heures) d’inactivité.

>[!CAUTION]
>Dans la dernière version, l’établissement d’un lien vers Developer Console directement à partir de Cloud Manager ne vous permet pas de mettre en veille un environnement de programme Sandbox. Pour contourner ce problème, dans Developer Console, ajoutez le motif suivant à la fin de l’URL : `#release-cm-p1234-e5678 where 1234` 1234 correspond à votre *ID de programme* et 5678 à votre *ID d’environnement*.

### Utilisation de la veille manuelle {#using-manual-hibernation}

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


## Réactivation {#de-hibernation-introduction}

1. Accédez à **Developer Console**.
Consultez [Accès à Developer Console](/help/implementing/cloud-manager/manage-environments.md#accessing-developer-console) pour savoir comment accéder à **Developer Console** à partir de la carte **Environnements**.

   >[!IMPORTANT]
   >L’établissement d’un lien vers **Developer Console** directement à partir de Cloud Manager ne vous permet pas de réactiver un environnement de programme Sandbox. Pour contourner ce problème, dans Developer Console, ajoutez le motif suivant à la fin de l’URL : `#release-cm-p1234-e5678 where 1234` 1234 correspond à votre *ID de programme* et 5678 à votre *ID d’environnement*.

   >[!NOTE]
   >Vous pouvez également accéder à **Developer Console** pour réactiver en essayant d’accéder au service de création, de prévisualisation ou de publication d’un environnement déjà mis en veille. dans ce cas, une page d’entrée s’affiche avec un lien vers Developer Console. Reportez-vous à la section Accès à un environnement mis en veille ci-dessous.

   >[!IMPORTANT]
   >L’accès à Developer Console est défini par le **rôle Cloud Manager – Développeur** dans **Admin Console**. Un utilisateur disposant d’une autorisation de rôle de développeur peut réactiver un environnement de programme Sandbox.

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

### Autorisations de réactiver {#permissions-de-hibernate}

Tout utilisateur disposant d’un profil de produit qui lui donne accès à AEM as a Cloud Service doit pouvoir accéder à **Developer Console**, qui lui permet de réactiver l’environnement.

## Accès à un environnement mis en veille {#accessing-hibernated-environment}

Lors d’une requête de navigateur au niveau de création, de prévisualisation ou de publication d’un environnement en veille, l’utilisateur rencontre une page d’entrée décrivant l’état de mise en veille de l’environnement, comme illustré dans la figure ci-dessous :

![](assets/de-hibernation-img5.png)

## Points importants {#important-considerations}

Voici quelques considérations clés liées aux environnements mis en veille et réactivés :

* Un utilisateur peut utiliser un pipeline pour déployer du code personnalisé sur des environnements mis en veille. L’environnement demeure en veille et le nouveau code apparaît dans l’environnement une fois ce dernier réactivé.

* Les mises à niveau d’AEM peuvent être appliquées aux environnements mis en veille, et les clients peuvent les déclencher manuellement à partir de Cloud Manager. L’environnement demeure en veille et la nouvelle version apparaît dans l’environnement une fois ce dernier réactivé.

* Les environnements de test sont placés dans le nœud de veille après 8 heures d’inactivité, après quoi ils peuvent être réactivés.

* Les environnements de test sont supprimés après 6 mois de mise en veille continue, après quoi ils peuvent être recréés.

   >[!NOTE]
   >Actuellement, Cloud Manager n’indique pas si un environnement est en veille.

## Mises à jour AEM des environnements Sandbox {#aem-updates-sandbox}

Pour plus d’informations, voir [Mises à jour de la version AEM](/help/implementing/deploying/aem-version-updates.md).

Un utilisateur peut appliquer manuellement des mises à jour AEM aux environnements dans un programme Sandbox.

Reportez-vous à [Mise à jour de l’environnement](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment) pour savoir comment mettre à jour un environnement.

>[!NOTE]
>* Une mise à jour manuelle ne peut être exécutée que si l’environnement ciblé dispose d’un pipeline correctement configuré.
>* Une mise à jour manuelle d’un environnement de *production* met automatiquement à jour l’environnement d’*évaluation*, et vice-versa. Le jeu d’environnements Production+Évaluation doit se trouver dans la même version AEM.

