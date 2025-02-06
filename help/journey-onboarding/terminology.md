---
title: Terminologie d’AEM as a Cloud Service
description: Avant de vous connecter à AEMaaCS, il est utile de comprendre une partie de la terminologie du système et sa structure de base.
exl-id: d02776a7-836a-4894-a5d5-ae88cc7e4e76
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 87%

---

# Terminologie d’AEM as a Cloud Service {#terminology}

Dans cette partie du [parcours d’intégration](overview.md), vous découvrirez certains aspects de la terminologie d’AEM as a Cloud Service et sa structure de base.

## Objectif {#objective}

Maintenant que vous comprenez ce qui a conduit au processus d’intégration en lisant le document [Préparation à l’intégration](preparation.md), il est utile de comprendre certains aspects de la terminologie du système et sa structure de base avant de vous connecter.

AEM as a Cloud Service est un outil puissant et flexible, et pour utiliser n’importe quel outil, vous devez connaître son organisation ainsi que sa terminologie et le langage utilisés pour le décrire. Ce document résume certains termes clés que vous devez comprendre avant de commencer à utiliser le système.

Après avoir lu ce document, vous comprendrez :

* Les différents calques qui constituent AEMaaCS.
* Les principes de base de chaque calque.

## La structure AEMaaCS. {#structure}

Pour les besoins de ce parcours d’intégration, une compréhension complète de la structure d’AEM as a Cloud Service n’est pas nécessaire. Mais la connaissance des concepts suivants facilitera votre poursuite du parcours.

![Structure de Cloud Manager](/help/journey-sites/quick-site/assets/cloud-manager-structure.png)

* **CLIENT** - Chaque client est configuré avec un client. Un client est également appelé organisation IMS (vous aurez d’autres informations sur IMS plus loin dans ce parcours).
* **PROGRAMMES** - Chaque client dispose d’un ou de plusieurs programmes, qui reflètent souvent les solutions sous licence du client.
* **ENVIRONNEMENTS** - Chaque programme comporte plusieurs environnements, un de production pour le contenu en direct, un d’évaluation pour le test et un à des fins de développement.
* **RÉFÉRENTIEL** - Les environnements disposent de référentiels Git où l’application et le code front-end sont conservés.
* **OUTILS ET WORKFLOWS** - Les pipelines gèrent le déploiement du code des référentiels vers les environnements.

Un exemple est souvent utile pour contextualiser cette hiérarchie.

* Disons que WKND Travel and Adventure Enterprises est un **client** qui se concentre sur les médias liés aux voyages.
* Le client WKND Travel and Adventure Entreprises peut avoir deux **programmes** :
   * Un programme Sites pour sa division WKND Magazine
   * Un programme Assets pour la division WKND Media
* Les programmes pour WKND Magazine et WKND Media auraient tous les deux des **environnements** de développement, d’évaluation et de production.
* **Des référentiels** sont utilisés pour gérer le code personnalisé et les applications pour WKND Magazine et WKND Media.
* Divers **outils et workflows** travaillent sur les référentiels pour déployer le code à l’aide des pipelines CI/CD, accéder aux logs, accéder à AEM, etc.

## Prochaines étapes {#what-is-next}

Maintenant que vous avez terminé cette partie du parcours d’intégration AEM, vous devriez comprendre :

* Les différents calques qui constituent AEMaaCS.
* Les principes de base de chaque calque.

Tirez parti de ces connaissances et poursuivez votre parcours d’intégration AEM en consultant le document [Accès à Admin Console](admin-console.md), où vous apprendrez comment accéder à la console et vérifier votre statut en tant qu’administrateur système.
