---
title: Terminologie as a Cloud Service AEM
description: Avant de vous connecter à AEMaaCS, il est utile de comprendre la terminologie du système et sa structure de base.
source-git-commit: 709a80683357b0d56280ff14aa5f4ba6bf2c6b23
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 18%

---


# Terminologie as a Cloud Service AEM {#terminology}

Dans cette partie du [parcours d&#39;intégration,](overview.md) vous découvrirez la terminologie d&#39;AEM as a Cloud Service et sa structure de base.

## Objectif {#objective}

Maintenant que vous comprenez ce qui a conduit au processus d’intégration en lisant le document [Préparation à l’intégration,](preparation.md) il est utile de comprendre la terminologie du système et sa structure de base avant de vous connecter.

AEM as a Cloud Service est un outil puissant et flexible, et pour utiliser n&#39;importe quel outil, vous devez connaître son organisation, la terminologie et la langue utilisées pour la décrire. Ce document résume certains termes clés que vous devez comprendre avant de commencer à utiliser le système.

Après avoir lu ce document, vous comprendrez :

* Les différents calques qui constituent AEMaaCS.
* Principes de base de chaque calque.

## Structure AEMaaCS {#structure}

Pour les besoins de ce parcours d’intégration, une compréhension complète de la structure de l’AEM as a Cloud Service n’est pas nécessaire. Mais la connaissance des concepts suivants facilitera la poursuite ultérieure dans le parcours.

![Structure de Cloud Manager](/help/journey-sites/quick-site/assets/cloud-manager-structure.png)

* **CLIENT** - Chaque client est configuré avec un client. Un client est également appelé organisation IMS (plus d’informations sur IMS plus loin dans ce parcours).
* **PROGRAMMES** - Chaque client dispose d’un ou de plusieurs programmes, qui reflètent souvent les solutions sous licence du client.
* **ENVIRONNEMENTS** - Chaque programme comporte plusieurs environnements, un de production pour le contenu en direct, un d’évaluation pour le test et un à des fins de développement.
* **RÉFÉRENTIEL** - Les environnements disposent d’un ou de plusieurs référentiels Git où le code d’application et le code frontal sont conservés.
* **OUTILS ET WORKFLOWS** - Les pipelines gèrent le déploiement du code des référentiels vers les environnements.

Un exemple est souvent utile pour contextualiser cette hiérarchie.

* Disons que WKND Travel and Adventure Enterprises est un **client** qui se concentre sur les médias liés aux voyages.
* Le client WKND Travel and Adventure Entreprises peut avoir deux **programmes**:
   * Un programme Sites pour sa division WKND Magazine
   * Un programme Assets pour la division Média WKND
* Les programmes WKND Magazine et WKND Media auraient tous deux un développement, une mise en scène et une production. **environnements**.
* **Référentiels** sont utilisés pour gérer le code personnalisé et les applications pour WKND Magazine et WKND Media.
* Divers **outils et workflows** travailler sur les référentiels pour déployer le code à l’aide des pipelines CI/CD, des journaux d’accès, des AEM d’accès, etc. ;

## Prochaines étapes {#what-is-next}

Maintenant que vous avez terminé cette partie du parcours d’intégration d’AEM, vous devez comprendre :

* Les différents calques qui constituent AEMaaCS.
* Principes de base de chaque calque.

Tenez compte de ces connaissances et continuez votre parcours d’intégration AEM en lisant le document suivant. [Accès au Admin Console](admin-console.md), où vous apprendrez comment accéder à la console et vérifier votre statut en tant qu’administrateur système.
