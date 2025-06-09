---
title: Présentation des outils de refactorisation
description: Découvrez comment commencer à utiliser les outils de refactorisation d’AEM
exl-id: b8137e01-87e8-4298-b0cc-b376330cb730
source-git-commit: 879f4f3476ee369554188d6e3b7973d32454ed4b
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 1%

---

<!-- Alexandru: temporarily commeting this out, since it breaks validation

>[!CONTEXTUALHELP]
>id="aemcloud_rs_overview"
>title="Overview"
>abstract="Refactoring Tools is a solution developed by Adobe to help refactor existing AEM projects for compatibility with AEM as a Cloud Service. The tools are executed via Cloud Acceleration Manager (CAM) and automate key modernization tasks."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=fr" text="Guidelines and Best Practices"

-->

# Présentation des outils de refactorisation {#refactoring-tools-overview}

**Outils de refactorisation** rationalisez le processus de mise à jour des projets AEM existants pour les rendre compatibles avec **AEM as a Cloud Service (AEMaaCS)**. Ces outils automatisent les tâches courantes de refactorisation et de modernisation et sont intégrés à **Cloud Acceleration Manager (CAM)** pour une expérience transparente.

Auparavant disponibles uniquement en tant qu’utilitaires d’interface de ligne de commande, les outils de refactorisation fournissent désormais une interface unifiée avec des fonctionnalités telles que l’inspection automatisée, la génération de configurations et l’exécution de tâches, ce qui réduit les frais généraux manuels et améliore la visibilité.

## Workflow d’inspection {#inspection-workflow}

Le **workflow d’inspection** simplifie le processus de préparation pour l’exécution des outils de refactorisation.

### Fonctionnalités clés :

* **Déclencheur automatique** - Le chargement d’un projet lance automatiquement le contrôle.
* **Génération de configuration** - Les outils examinent le code source chargé et génèrent les configurations nécessaires.
* **Envoi de la payload** - Ces configurations sont transmises directement aux outils sélectionnés pour exécution.

## Outils de refactorisation disponibles

### Repository Modernizer {#repo-modernizer}

**Repository Modernizer** restructure la disposition et le contenu du référentiel de votre projet AEM pour s’aligner sur les normes et les bonnes pratiques d’AEMaaCS. Il remplace l’ancien outil de modernisation du référentiel par une automatisation et une précision améliorées.

### Transformateur de code {#code-transformer}

Le **transformateur de code** utilise la reconnaissance intelligente de motifs et l’analyse pilotée par l’IA pour détecter et mettre à jour les segments de code incompatibles avec AEMaaCS. Cet outil simplifie les tâches de migration et réduit les modifications manuelles du code.

## Refactorisation des phases de workflow {#phases-in-refactoring-tools}

Les outils de refactorisation suivent un processus structuré en deux phases :

### Phase 1 : chargement de votre code Source

* Chargez votre code source (au format ZIP) à l’aide de l’interface CAM.
* Une fois le chargement effectué, le **workflow d’inspection** est automatiquement déclenché pour analyser le projet et le préparer à l’exécution de l’outil.

>[!NOTE]
>Pendant le processus d&#39;inspection, il n&#39;est pas permis de charger un autre projet.

### Phase 2 : déclenchement d’une tâche de refactorisation

Après une inspection réussie, vous pouvez exécuter un ou plusieurs outils de refactorisation :

* **Exécuter Repository Modernizer** - Exécute la modernisation du référentiel.
* **Exécuter le transformateur de code** - Exécute la transformation de code en fonction de la sortie d’inspection.
* **Exécuter tous les outils ensemble** - Exécute tous les outils disponibles en une seule opération.

>[!NOTE]
>Les tâches de refactorisation ne peuvent être démarrées qu’une fois le code source chargé et inspecté avec succès.

>[!NOTE]
>Les utilisateurs peuvent déclencher plusieurs tâches de refactorisation en parallèle, mais chaque tâche sera exécutée séparément.
