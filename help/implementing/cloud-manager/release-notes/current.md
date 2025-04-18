---
title: Notes de mise à jour de la version 2025.4.0 de Cloud Manager
description: En savoir plus sur la version 2025.4.0 de Cloud Manager dans Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: fcd9ead02ca5061778001d954ae9a9fc6088d5d1
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 100%

---

# Notes de mise à jour de Cloud Manager 2025.4.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.03.0+Release -->

En savoir plus sur la version 2025.4.0 de Cloud Manager dans AEM (Adobe Experience Manager) as a Cloud Service.


Consultez également les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Dates de publication {#release-date}

La date de publication de la version 2025.4.0 de Cloud Manager dans AEM as a Cloud Service est le jeudi 10 avril 2025.

La prochaine version est prévue le jeudi 8 mai 2025.

## Nouveautés {#what-is-new}

* **Visibilité améliorée du déploiement (Interface d’utilisation)**

  La page des détails d’exécution du pipeline dans Cloud Manager affiche désormais un message de statut (« *En attente - autre mise à jour en cours* ») lorsqu’un déploiement attend la fin d’un autre déploiement. Ce workflow permet de comprendre plus facilement le séquencement lors du déploiement de l’environnement. <!-- CMGR-66890 -->

  ![Boîte de dialogue de déploiement de développement affichant les détails et la répartition](/help/implementing/cloud-manager/release-notes/assets/dev-deployment.png)

* **Amélioration de la validation du domaine (Interface d’utilisation)**

  Lors de l’ajout d’un domaine, Cloud Manager affiche désormais une erreur si le domaine est déjà installé dans un compte Fastly : « *Le domaine est déjà installé dans un compte Fastly. Supprimez-le d’abord de cet emplacement avant de l’ajouter à Cloud Service.* »

## Programme d’adoption précoce {#early-adoption}

Participez au programme d’adoption précoce de Cloud Manager pour obtenir un accès exclusif aux fonctionnalités à venir avant leur publication générale.

Les possibilités d’adoption précoce suivantes sont actuellement disponibles :

### Apportez votre propre Git - avec prise en charge de GitLab et Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

La fonctionnalité **Apportez votre propre Git** a été étendue pour inclure la prise en charge de référentiels externes tels que GitLab et Bitbucket. Cette nouvelle prise en charge s’ajoute à la prise en charge existante des référentiels GitHub privés et d’entreprise. Lorsque vous ajoutez ces nouveaux référentiels, vous pouvez également les lier directement à vos pipelines. Vous pouvez héberger ces référentiels sur des plateformes cloud publiques ou dans votre infrastructure ou cloud privés. Cette intégration élimine également la nécessité d’une synchronisation constante du code avec le référentiel d’Adobe et permet de valider les requêtes d’extraction avant de les fusionner dans une branche principale.

Les pipelines qui utilisent des référentiels externes (à l’exclusion de ceux hébergés par GitHub) et le **Déclencheur de déploiement** défini sur **Lors des modifications Git** démarrent désormais automatiquement.

Voir [Ajouter des référentiels externes dans Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

![Boîte de dialogue Ajouter un référentiel](/help/implementing/cloud-manager/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Actuellement, les contrôles de qualité du code des requêtes d’extraction prêts à l’emploi sont exclusifs aux référentiels hébergés par GitHub, mais une mise à jour permettant d’étendre cette fonctionnalité à d’autres fournisseurs Git est en cours.

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID. Veillez à inclure la plateforme Git à utiliser et indiquez si vous utilisez une structure de référentiel privée/publique ou d’entreprise.

<!--
### AEM Home {#aem-home}

AEM Home introduces a centralized starting point for managing content, assets, and sites within Adobe Experience Manager. Designed to deliver a personalized experience, AEM Home lets you navigate the AEM ecosystem seamlessly according to your roles and goals. Acting as a guide, it provides key insights and recommended actions to help you achieve your objectives efficiently. With a clear, persona-driven layout, AEM Home ensures quick access to essential tools, supporting a streamlined and effective experience across all AEM features.

Available to early adopters, AEM Home offers an optimized experience focused on improving workflows, prioritizing goals, and delivering results. Opting in lets you influence AEM Home's development by providing feedback that helps shape its future and enhances its value for the entire AEM community.

If you are interested in testing this new capability and sharing your feedback, send an email to [Grp-AemHome@adobe.com](mailto:Grp-AemHome@adobe.com) from your email address associated with your Adobe ID. Be sure to include the following information:

* The role that best fits your profile: Content author, Developer, Business owner, Admin, or Other (provide a description).
* Your primary AEM access surface: AEM Sites, AEM Assets, AEM Forms, Cloud Manager, or Other (provide a description). -->

## Correctifs

* **Problème lié à un champ de nom commun (NC) manquant dans les certificats**

  Cloud Manager ne renvoie plus de réponse NullPointerException (NPE) et HTTP 500 lors du traitement des certificats EV/OV qui n’incluent pas de nom commun (CN) dans le champ Objet. Les certificats modernes omettent souvent le CN et utilisent à la place le SAN (Subject Alternative Name). Ce correctif garantit que l’absence de réseau de diffusion de contenu ne provoque plus de panne pendant le processus de création de la configuration en présence du SAN. <!-- CMGR-67548 -->

* **Problème de vérification de domaine avec une correspondance de certificat incorrecte**

  Cloud Manager ne vérifie plus de manière erronée les domaines à l’aide de certificats incorrects. Auparavant, la logique de validation utilisait la correspondance basée sur les modèles au lieu de la correspondance exacte, ce qui faisait apparaître des domaines tels que `should-not-be-verified.example.com` comme vérifiés en raison du chevauchement avec des certificats valides pour `example.com`. Ce correctif garantit que la validation de domaine recherche désormais les correspondances exactes, empêchant les associations de certificats erronées. <!-- CMGR-67225 -->

* **Unicité appliquée pour les noms de transfert de port de réseau avancé**

  Cloud Manager applique désormais un nom unique pour les transferts de port de mise en réseau avancée. Auparavant, les noms en double étaient autorisés, ce qui pouvait entraîner des conflits. Ce correctif garantit que chaque entrée de transfert de port a un nom distinct, conformément aux bonnes pratiques en matière d’intégrité de la configuration réseau. <!-- CMGR-67082 -->


<!-- ## Known issues {#known-issues} -->

