---
title: AEM as a Cloud Service sur Shell unifié
description: AEM as a Cloud Service sur Shell unifié
exl-id: ea739307-dc99-4621-a239-dbe60ab6b52e
source-git-commit: 9ef6bda76667b08b5fb62b90acdc75002889d420
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 1%

---

# AEM as a Cloud Service sur Shell unifié {#aem-as-a-cloud-service-on-unified-shell}

>[!NOTE]
>Cette fonctionnalité est disponible dans le canal de version préliminaire de mai 2022.
>
>Il s’agit d’une introduction à une nouvelle fonctionnalité qui sera disponible en général dans la version de juin 2022.
>
>Voir [Documentation sur les canaux de version préliminaire](/help/release-notes/prerelease.md#enable-prerelease) pour plus d’informations sur l’activation de la fonctionnalité dans votre environnement.

>[!INFO]
>En raison d’un problème récemment détecté, l’intégration de Shell unifié avec AEM as a Cloud Service a été temporairement désactivée. Il sera réactivé une fois le problème résolu. Merci pour votre compréhension.

## Présentation {#overview}

AEM as a Cloud Service est intégré à Unified Shell pour améliorer l’expérience utilisateur et l’unifier avec toutes les autres applications Experience Cloud. L’impact de cette intégration est visible dans l’en-tête supérieur de l’application, comme illustré ci-dessous.

![image](/help/overview/assets/unifiedshell1.png)

Les avantages sont les suivants :

* Connexion unique sur toutes les applications Experience Cloud
* Changement aisé entre les organisations ou basculement vers une autre application
* Amélioration de l’aide des produits
* Bouton de retour sur produit simple pour signaler les problèmes ou partager des idées avec Adobe
* Accès aux annonces et notifications de produits globaux en plus des notifications spécifiques AEM as a Cloud Service

## Désactivation de Shell unifié {#disabling-unified-shell}

AEM as a Cloud Service a un shell unifié activé prêt à l’emploi. Toutefois, si l’en-tête supérieur a été personnalisé, il est recommandé de désactiver l’interpréteur de commandes unifié afin d’éviter tout problème lié aux personnalisations. Pour désactiver l’interpréteur de commandes unifié, procédez comme suit :

>[!NOTE]
>Un Shell unifié ne peut être désactivé que par un compte disposant de privilèges d’administration.

1. Accédez à **Outils - Cloud Services**.

   Un utilisateur administrateur voit la carte Configuration de Shell unifiée comme illustré ci-dessous :

   ![image](/help/overview/assets/unifiedshell2.png)

1. Cliquez sur **Configuration de Shell unifiée**. Décochez ensuite la case affichée ci-dessous pour désactiver Unified Shell :

   ![image](/help/overview/assets/unifiedshell3.png)

## Modification d’un thème sombre {#chaning-to-dark-theme}

Pour passer au thème sombre, cliquez sur l’icône de votre profil. Une fenêtre contextuelle s’affiche, comme illustré ci-dessous. Vous pouvez utiliser le bouton d’activation/désactivation pour passer à un thème sombre pour le Shell unifié.

>[!INFO]
>
>Le thème sombre s’applique uniquement au Shell unifié (la barre supérieure).

![image](/help/overview/assets/unifiedshell4.png)

## Accès à la boîte de réception AEM {#accessing-the-aem-inbox}

Vous pouvez accéder à la boîte de réception AEM en cliquant sur l’icône représentant une cloche dans le shell unifié.

>[!INFO]
>
> Le nombre indiqué sur l’icône représentant une cloche comprend des notifications non lues sur toutes les solutions au sein de cette organisation IMS et les tâches répertoriées dans la boîte de réception AEM.

![image](/help/overview/assets/unifiedshell5.png)

Cliquez sur le bouton Boîte de réception de la fenêtre contextuelle pour accéder à votre boîte de réception AEM :

![image](/help/overview/assets/unifiedshell6.png)
