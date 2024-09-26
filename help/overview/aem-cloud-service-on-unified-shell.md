---
title: AEM as a Cloud Service sur Unified Shell
description: Découvrez les avantages d’AEM as a Cloud Service sur Unified Shell.
exl-id: ea739307-dc99-4621-a239-dbe60ab6b52e
feature: Release Information
role: Admin
source-git-commit: 55cf6a10c2cb4c62aa8f89fac7f9d1fb4c012d26
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 95%

---

# AEM as a Cloud Service sur Unified Shell {#aem-as-a-cloud-service-on-unified-shell}

## Vue d’ensemble {#overview}

AEM as a Cloud Service (service de création) est intégré à Unified Shell pour améliorer l’expérience client et l’unifier avec toutes les autres applications Experience Cloud. L’impact de cette intégration est visible dans l’en-tête supérieur de l’application, comme illustré ci-dessous.

![image](/help/overview/assets/unifiedshell_header.png)

Les avantages sont les suivants :

* Authentification unique sur toutes les applications Experience Cloud
* Changement aisé entre les entreprises ou basculement vers une autre application
* Amélioration de l’aide sur les produits
* Bouton de retour d’information facile sur le produit pour signaler les problèmes ou partager des idées avec Adobe
* Accéder aux annonces et notifications de produits globales en plus des notifications spécifiques à AEM as a Cloud Service

## Désactiver Unified Shell {#disabling-unified-shell}

Lorsqu’il est prêt à l’emploi, AEM as a Cloud Service active Unified Shell. Toutefois, si la partie supérieure de l’en-tête a été personnalisée, il est recommandé de désactiver Unified Shell afin d’éviter tout problème lié aux personnalisations. Pour désactiver Unified Shell, procédez comme suit :

>[!NOTE]
>Unified Shell ne peut être désactivé que par un compte disposant des droits d’administration.

1. Cliquez sur **Outils > Services Cloud**.

   Une personne administratrice voit la carte Configuration de Unified Shell comme illustré ci-dessous :

   ![image](/help/overview/assets/unifiedshell2.png)

1. Cliquez sur **Configuration de Unified Shell**. Décochez ensuite la case affichée ci-dessous pour désactiver Unified Shell :

   ![image](/help/overview/assets/unifiedshell3.png)

>[!NOTE]
>
>Un Shell unifié peut également être désactivé à partir du code de votre projet. Voir [Structure de l’interface utilisateur AEM - Shell unifié](/help/implementing/developing/introduction/ui-structure.md#unified-shell).

## Passer au thème sombre {#changing-to-dark-theme}

Pour passer au thème sombre, cliquez sur l’icône de votre profil. Cette action affiche une fenêtre contextuelle comme illustré ci-dessous. Vous pouvez utiliser le bouton d’activation/désactivation pour passer à un thème sombre pour Unified Shell.

>[!INFO]
>
>Le thème sombre s’applique uniquement à Unified Shell (voir la barre supérieure).

![image](/help/overview/assets/unifiedshell4.png)

## Identifier l’environnement AEM as a Cloud Service {#identify-aemaacs-environment}

AEM as a Cloud Service fournit trois types d’environnements : Production, Évaluation et Développement. Voir [Types d’environnements](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-environments.html?lang=fr) pour plus d’informations. Grâce à cette intégration avec Unified Shell, le type d’environnement dans lequel l’utilisateur ou l’utilisatrice est connecté(e) au service de création s’affiche dans l’en-tête supérieur via un libellé comme illustré ci-dessous.

![image](/help/overview/assets/unifiedshell_header_label.png)

## Accéder à la boîte de réception AEM {#accessing-the-aem-inbox}

Pour accéder à la boîte de réception AEM, vous pouvez cliquer sur l’icône représentant une cloche dans Unified Shell.

>[!INFO]
>
> Le nombre indiqué sur l’icône représentant une cloche comprend des notifications non lues sur toutes les solutions au sein de cette organisation IMS et les tâches répertoriées dans la boîte de réception AEM.

![image](/help/overview/assets/unifiedshell5.png)

Cliquez sur le bouton Boîte de réception dans la fenêtre contextuelle pour accéder à votre boîte de réception AEM :

![image](/help/overview/assets/unifiedshell6.png)

