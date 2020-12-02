---
title: Phase de planification
description: Phase de planification
translation-type: tm+mt
source-git-commit: df3eb65817a00fe31eff466565b9de5e0a72ccae
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 91%

---


# Planification {#planning-phase}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_planning"
>title="Planification de votre Transition"
>abstract="Avant de commencer votre parcours de transition vers Cloud Service, vous devez vous familiariser avec AEM as a Cloud Service, mais aussi examiner les modifications notables qui y ont été apportées, ainsi que les fonctionnalités remplacées ou obsolètes."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html" text="Analyseur des meilleures pratiques"

Avant de commencer votre parcours de transition vers Cloud Service, vous devez vous familiariser avec AEM as a Cloud Service, mais aussi examiner les modifications notables qui y ont été apportées, ainsi que les fonctionnalités remplacées ou obsolètes.

## Modifications notables {#notable-changes}

AEM as a Cloud Service offre de très nombreuses fonctionnalités et possibilités nouvelles pour gérer vos projets AEM.

Cependant, un certain nombre de différences existent entre AEM On-Premise ou Adobe Managed Services par rapport à AEM as a Cloud Service.

Pour comprendre ces différences importantes, voir [Modifications notables d’AEM Cloud Service](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/release-notes/aem-cloud-changes.html).

## Fonctionnalités obsolètes {#deprecated-features}

Adobe étudie constamment les fonctionnalités du produit de façon à les réinventer au fil du temps ou à remplacer les fonctions plus anciennes par des variantes plus modernes, pour améliorer la valeur client globale, le tout en faisant toujours attention à la compatibilité ascendante.

Pour en savoir plus sur les caractéristiques et les fonctionnalités signalées comme étant obsolètes dans Experience Manager as a Cloud Service, voir [Fonctionnalités obsolètes](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/release-notes/deprecated-removed-features.html#deprecated-features).

## Présentation de la phase de planification {#introduction}

La figure suivante présente les étapes clés de la phase de planification :

![image](/help/move-to-cloud-service/assets/planning-phaseimg1.png)

### Évaluation du niveau de préparation pour la transition vers Cloud Service {#access-cloud-readiness}

La première étape de la phase de planification consiste à évaluer votre capacité à passer de la version existante d’AEM Cloud Service et à déterminer les domaines qui nécessiteront une refactorisation pour être compatibles avec AEM as a Cloud Service.

Vous devrez effectuer une évaluation complète du code source AEM existant par rapport aux modifications notables et aux fonctionnalités obsolètes afin de déterminer le niveau d’effort attendu pour le parcours de transition.

Vous pouvez accélérer l’étape d’évaluation en exécutant l’analyseur des meilleures pratiques sur votre version d’AEM actuelle. Pour plus d&#39;informations, consultez [Best Practices Analyzer](/help/move-to-cloud-service/best-practices-analyzer/overview-best-practices-analyzer.md).

>[!NOTE]
>Si vous avez déjà accès à Cloud Manager et à un environnement Cloud Service, il est recommandé de faire fonctionner votre code actuel dans un pipeline de qualité de code Cloud Manager afin d’évaluer les modifications de code assurant la compatibilité avec Cloud Service.

### Examen de la planification des ressources {#review-resource-planning}

Une fois le niveau d’effort estimé pour passer à Cloud Service, vous devez identifier les ressources, créer une équipe ainsi que définir les rôles et les responsabilités pour le processus de transition.

### Définition des indicateurs de performance clés (IPC) {#establish-kpis}

Si vous n’avez pas encore défini d’indicateurs de performance clés (IPC), il est recommandé de les établir pour votre implémentation d’Adobe Experience Manager (AEM). Votre équipe pourra ainsi se concentrer sur l’essentiel.

Pour savoir comment choisir les IPC appropriés pour vos objectifs métier, voir [Développement d’indicateurs de performance clés](https://guided.adobe.com/welcome/aem/part6.html).

