---
title: Préparation du HIPAA pour Adobe Experience Manager as a Cloud Service
description: Découvrez la prise en charge d’Experience Manager as a Cloud Service des réglementations HIPAA et comment vous y conformer lors de la mise en œuvre d’un nouveau projet AEM as a Cloud Service.
feature: Compliance
role: Admin, Developer, Leader
exl-id: 9928811e-3487-430a-9e2f-04959460c95f
source-git-commit: c2b849ef25afd0809891a822a99ddd3059bf1919
workflow-type: tm+mt
source-wordcount: '1029'
ht-degree: 8%

---

# Préparation du HIPAA pour Adobe Experience Manager as a Cloud Service {#hipaa-readiness-for-adobe-experience-manager-as-a-cloud-service}

>[!WARNING]
>
>Le contenu de ce document ne constitue pas un avis juridique et ne vise pas à le remplacer.
>
>Consultez le service juridique de votre entreprise pour obtenir des conseils sur les réglementations HIPAA.

>[!NOTE]
>
>Pour plus d’informations sur la réponse d’Adobe aux problèmes de confidentialité et sur ce que cela signifie pour vous en tant que client Adobe, consultez :
>
>* [Produits et services HIPAA et Adobe](https://www.adobe.com/trust/compliance/hipaa-hds/hipaa-ready.html) dans le Centre de gestion de la confidentialité Adobe
>* [Centre de traitement des données personnelles ](https://www.adobe.com/fr/privacy.html)

Pour Adobe Experience Manager (AEM) as a Cloud Service, Adobe fournit de la documentation pour vous aider à comprendre la préparation au HIPAA. Celles-ci pourront vous aider à vous conformer à ces règlements.

## Health Insurance Portability and Accountability Act (HIPAA) {#health-insurance-portability-and-accountability-act-hipaa}

### La Health Insurance Portability and Accountability Act (HIPAA) {#the-health-insurance-portability-and-accountability-act-hipaa}

Les règles de confidentialité, de sécurité et de notification des violations de la loi HIPAA établissent des protections importantes pour les informations de santé identifiables appelées informations de santé protégées (ISP).

En vertu de la loi HIPAA, une entité couverte est un prestataire de soins de santé, un régime d’assurance-maladie ou un centre d’information sur les soins de santé. Un associé d&#39;affaires est une entité qui fournit des services à une entité couverte qui implique l&#39;accès aux ISP. Les règles de confidentialité et de sécurité de la loi HIPAA exigent qu&#39;une entité couverte obtienne des assurances écrites d&#39;un associé commercial sous la forme d&#39;un accord d&#39;association (BAA) exigeant que l&#39;associé commercial protège la confidentialité et la sécurité des ISP de l&#39;entité couverte.

### Fournir des ISP à Adobe {#providing-phi-to-adobe}

Adobe agit en tant qu’associé commercial pour ses services conformes à la loi HIPAA, répertoriés sous [ Préparation des services conforme à la loi HIPAA dans AEM as a Cloud Service](#hipaa-readiness-of-services-in-aem-as-a-cloud-service).

Les clients qui disposent d’une licence pour un service conforme à la norme HIPAA d’Adobe pour traiter les ISP **doivent** disposer de la licence appropriée et d’un BAA signé avec Adobe.

>[!IMPORTANT]
>
>Les clients ne sont pas autorisés à créer, recevoir, gérer ou transmettre des ISP par l’intermédiaire de produits et services Adobe qui ne sont pas désignés comme des services conformes à la loi HIPAA ou sans la licence appropriée pour utiliser un service conforme à la loi HIPAA.

### HIPAA - Responsabilités partagées {#hipaa-shared-responsibilities}

Les services conformes à la norme HIPAA d’Adobe reposent sur un modèle de sécurité de responsabilité partagée, qui exige que le client et Adobe portent chacun des responsabilités distinctes pour le maintien de la sécurité des ISP. Dans le cadre de ce modèle de sécurité partagé, Adobe s’appuie sur le client pour utiliser et configurer les services conformes à la loi HIPAA.

Pour plus d’informations sur l’exécution d’un BAA Adobe pour les services conformes à la loi HIPAA, contactez votre représentant commercial Adobe ou votre responsable du succès client.

>[!IMPORTANT]
>
>**Clause de non-responsabilité** :
>
>Il est de la responsabilité du Client d&#39;utiliser les Services conformes à la norme HIPAA d&#39;Adobe et de s&#39;assurer que les Services conformes à la norme Adobe répondent aux exigences de conformité.

Pour plus d’informations, voir [Produits et services HIPAA et Adobe](https://www.adobe.com/trust/compliance/hipaa-hds/hipaa-ready.html) dans le Centre de gestion de la confidentialité d’Adobe.

## Terminologie HIPAA {#hipaa-terminology}

Le tableau suivant décrit les catégories des services AEM pour l’utilisation de la loi HIPAA.

| Préparation du HIPAA | Description |
| --- | --- |
| Conformité à la norme HIPAA | Conçu pour traiter les ISP lorsqu’ils sont configurés de manière appropriée et utilisés avec un BAA. |
| Non conforme à la norme HIPAA | Non conçu pour traiter des ISP et ne doit pas être utilisé dans des cas d’utilisation liés à la loi HIPAA. |

>[!NOTE]
>
>Les classifications de niveau de préparation HIPAA sont basées sur les fonctionnalités prévues de chaque service et peuvent changer au fil du temps.
>
>Les clients doivent se référer à la documentation la plus récente et aux conditions contractuelles applicables lors de la planification de déploiements liés à la loi HIPAA.

## Préparation des services selon la loi HIPAA dans AEM as a Cloud Service {#hipaa-readiness-of-services-in-aem-as-a-cloud-service}

Le tableau suivant décrit les services AEM compatibles avec la loi HIPAA et les services pouvant être utilisés avec eux. Les services conformes à la norme HIPAA nécessitent l’achat d’Extended Security for Healthcare, comme décrit dans la section [Additional Requirements](#additional-requirements).

| Produit/Fonctionnalité | Service(s) | Préparation du HIPAA |
| --- | --- | --- |
| AEM Sites | AEM Sites, Publication AEM, Edge Delivery Services | Conformité à la norme HIPAA |
| AEM Sites | Éditeur universel | Non conforme à la norme HIPAA<br>[1] peut être ajouté à un programme de sécurité étendu en l’absence d’ISP. |
| AEM Sites Optimizer | Sites Optimizer | Non conforme à la norme HIPAA<br>[1] peut être ajouté à un programme de sécurité étendu en l’absence d’ISP. |
| AEM Assets | AEM Assets | Conformité à la norme HIPAA |
| AEM Assets | Content Hub | Non conforme à la norme HIPAA<br>[1] peut être ajouté à un programme de sécurité étendu en l’absence d’ISP. |
| AEM Assets | Brand Portal | Non conforme à la norme HIPAA |
| AEM Assets | API Open Dynamic Media | Non conforme à la norme HIPAA<br>[1] peut être ajouté à un programme de sécurité étendu en l’absence d’ISP. |
| AEM Assets | Dynamic Media Scene7 | Non conforme à la norme HIPAA |
| AEM Forms | AEM Forms, service de façade d’authentification, service PDF Utility | Conformité à la norme HIPAA |
| AEM CIF | Commerce Integration Framework | Non conforme à la norme HIPAA |
| AEM Cloud Manager | AEM Cloud Manager, Release Orchestrator, Basculements de version, Programme de validation de version | Conformité à la norme HIPAA |
| AEM Cloud Manager | Distribution logicielle | Non conforme à la norme HIPAA<br>[1] peut être ajouté à un programme de sécurité étendu en l’absence d’ISP. |
|   |   |   |
| AEM Guides  | AEM Guides  | Non conforme à la norme HIPAA |
|   |   |   |
| LLM Optimizer | LLM Optimizer | Non conforme à la norme HIPAA<br>[1] peut être ajouté à un programme de sécurité étendu en l’absence d’ISP. |

>[!NOTE]
>
>[1]
>
>Pour les services non conformes à la loi HIPAA indiqués comme pouvant être ajoutés à un programme de sécurité étendue, les clients doivent s’assurer que les informations d’identification personnelle ne sont pas acheminées vers ces services ni stockées dans ceux-ci.
>
>L’introduction de l’ISP dans un service non conforme à la loi HIPAA peut entraîner une non-conformité.

### Exigences supplémentaires {#additional-requirements}

[Les services répertoriés](#hipaa-readiness-of-services-in-aem-as-a-cloud-service) conformes à la norme HIPAA nécessitent l’achat d’Extended Security for Healthcare.

Lors de l’achat d’Extended Security for Healthcare, les conditions suivantes sont requises :

* les produits sélectionnés pour ce programme sont conformes à la loi HIPAA (comme indiqué dans le tableau),
* Extended Security for Healthcare a été acheté pour *chaque produit*, ce qui garantit des crédits Cloud Manager suffisants.
* La sécurité étendue pour les soins de santé est appliquée au moment de la création du programme.

Si toutes les exigences sont remplies, le service Extended Security for Healthcare peut être appliqué lors de la création du programme AEM. Voir [Configuration](#setup) pour plus d’informations.

>[!NOTE]
>
>Pour plus d’informations sur la configuration et le prix, contactez votre représentant commercial.

## Environnements {#environments}

La mention *conforme à la norme HIPAA* ne s’applique pas aux environnements RDE (environnement de développement rapide), de développement ou d’évaluation, car les informations d’identification personnelles ne sont pas autorisées sur ces environnements.

Cela signifie que vous devez :

* utiliser des données factices à des fins de développement et de test ;
* ne traitez les ISP que depuis les environnements de production

Le tableau suivant indique où les types d’environnement peuvent être pris en charge en tant que conformes à la loi HIPAA.

| | RDE | Dev | Évaluation  | Prod |
| --- | --- | --- | --- | --- |
| Type d’environnement  | Non  | Non  | Non  | Oui  |

## Configuration {#setup}

Lorsque vous [Créer des programmes de production](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md), l’onglet [ Sécurité fournit les options permettant d’activer la protection HIPAA](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#security).
