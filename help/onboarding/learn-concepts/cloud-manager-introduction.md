---
title: Découvrez Cloud Manager
description: Consultez cette page pour en savoir plus sur Cloud Manager, les programmes Cloud Manager et les environnements.
exl-id: b743f126-b34e-4f48-a3f0-5dbd4e1ac34e
source-git-commit: c206bc241bccf6f8a5bfb4946d6231f53438861a
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 99%

---

# Présentation de Cloud Manager {#intro-cloud-manager}

Cloud Manager est un composant essentiel d’AEM as a Cloud Service et constitue le point d’entrée unique de votre équipe.

Pour prendre en charge les clients disposant de configurations de développement d’entreprise, AEM as a Cloud Service s’intègre entièrement à Cloud Manager et à ses pipelines CI/CD conçus spécifiquement pour garantir des tests approfondis et une qualité de code optimale afin d’offrir des expériences exceptionnelles.

Pour que les clients puissent commencer rapidement à utiliser AEM as a Cloud Service, Cloud Manager fournit tout ce dont ils ont besoin pour une prise en main en libre-service, notamment la possibilité de créer des ressources et des environnements cloud. Ainsi, vos développeurs AEM peuvent accéder au référentiel Git via Cloud Manager. Grâce à Cloud Manager, les équipes de développement peuvent travailler à la validation fréquente des modifications en libre-service.

Votre administrateur système sera chargé de configurer votre équipe Cloud Manager, qui comprendra les personnes qui créeront vos ressources cloud et vos développeurs. Reportez-vous à [Configuration du développement d’équipe d’entreprise pour AEM as a Cloud Service](/help/implementing/cloud-manager/managing-code/enterprise-team-dev-setup.md) pour découvrir comment Cloud Manager prend en charge la configuration du développement d’équipe d’entreprise.

## Accès à la page de présentation de Cloud Manager {#navigate-cloud-manager}

Pour accéder à Cloud Manager, procédez comme suit :

1. Accédez directement à la page de connexion de Cloud Manager à partir de [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/).

   >[!NOTE]
   >Mettez cette page en signet pour vous y référer ultérieurement et pour accéder directement à la page d’entrée de Cloud Manager.

1. Sélectionnez le programme dans la page **Programmes et produits** de Cloud Manager pour lancer la page **Présentation**.

De plus, vous pouvez également accéder à la page Programmes et produits de Cloud Manager à partir de la page d’accueil d’Adobe Experience Cloud. Suivez les étapes ci-dessous :

1. Accédez directement à [Adobe Experience Cloud](https://experience.adobe.com/#/@foundationinternal/home) et connectez-vous à l’aide de votre Adobe ID.

1. Sélectionnez **Experience Manager**.

1. Cliquez sur **Launch** à l’aide de la carte Cloud Manager. Une fois que vous êtes connecté à Cloud Manager, vous êtes prêt à utiliser l’interface utilisateur.

   Une fois votre connexion établie, vous êtes dirigé vers la page d’entrée de Cloud Manager, comme indiqué ci-dessous.

## Permissions basées sur les rôles dans Cloud Manager {#role-based-permissions}

| Autorisation | Description | Propriétaire de l’entreprise | Responsable de déploiement | Responsable de programme | Développeur |
|--- |--- |--- |--- |--- |--- |
| Ajouter un programme<br>Modifier le programme | Ajout d’un nouveau programme.<br>Modification d’un programme – Ajout ou suppression de solutions ou de modules complémentaires | x |  |  |  |
| Créer un environnement | Créer des environnements Prod+Éval, Dév, etc. | x | x |  |  |
| Mettre à jour l’environnement | Mettre à jour Prod+Éval, Dév, Environnements. | x | x |  |  |
| Suppression de l’environnement de dév | Supprimer les environnements de développement. | x | x |  |  |
| Configuration du pipeline | Configurer ou modifier un pipeline. |  | x |  |  |
| Exécution du pipeline | Démarrer le pipeline. | x | x |  |  |
| Exécution du pipeline | Refuser/approuver des échecs importants de 3 niveaux. | x | x | x |  |
| Exécution du pipeline | Fournit l’approbation de GoLive. | x | x | x |  |
| Exécution du pipeline | Planning du déploiement en production. | x | x | x |  |
| Suppression de pipeline | Permet la suppression d’un pipeline. |  | x |  |  |
| Annuler l’exécution | Annuler l’exécution actuelle. |  | x |  |  |
| Génération d’un jeton d’accès personnel | Accéder à Git. |  | x |  | x |

>[!NOTE]
>Un utilisateur peut être affecté à plusieurs rôles. Par exemple, l’attribution des rôles Propriétaire de l’entreprise et Responsable de déploiement à un utilisateur leur donne la combinaison ou la somme de ces autorisations.

## Programmes Cloud Manager {#cloud-manager-programs}

Les programmes Cloud Manager représentent des ensembles d’environnements Cloud Manager prenant en charge des ensembles logiques d’initiatives commerciales, correspondant généralement à un contrat de niveau de service (SLA) acheté. Par exemple, un programme peut représenter les ressources AEM pour prendre en charge les sites Web publics globaux, tandis qu’un autre programme représente un DAM central interne. Regardez cette [vidéo](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=fr) pour en savoir plus sur l’utilisation des programmes Cloud Manager.

Un utilisateur peut créer un programme **Sandbox** ou de **Production**.

* Un *Programme de production* est créé pour activer dans le futur le trafic actif au moment approprié.
Consultez [Présentation des programmes de production](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/production-programs/introduction-production-programs.html?lang=fr) pour plus d’informations.

* Un *programme Sandbox* est généralement créé pour les besoins de formation, à des fins de démonstration, d’activation, de preuve de concept ou de documentation. Ces programmes ne sont pas destinés à gérer un trafic réel et comporteront des restrictions absentes d’un programme de production. Ils incluront Sites et Assets et seront pourvus automatiquement d’une branche Git comprenant un exemple de code, un environnement de développement et un pipeline non productif.
Consultez [Présentation des programmes Sandbox](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/sandbox-programs/introduction-sandbox-programs.html?lang=fr) pour plus d’informations.

## Environnements Cloud Manager {#cloud-manager-environments}

Vos environnements cloud seront créés, accessibles et visualisés via Cloud Manager. Il peut s’agir d’un environnement de production, d’un environnement d’évaluation ou d’un environnement de développement. Les différents environnements prennent en charge différents objectifs et peuvent être utilisés à l’aide de différents pipelines CI/CD. Les environnements sont composés de services tels que :

* [Services de création AEM](#author-services)
* [Services de publication AEM](#publish-services)
* [Services Dispatcher](#dispatcher-services)

   >[!NOTE]
   > Reportez-vous à la vidéo [Utilisation des environnements Adobe Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=fr#cloud-manager) pour en savoir plus sur les environnements disponibles. Voir également [Gestion des environnements](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=fr) pour en savoir plus sur les types d’environnement qu’un utilisateur peut créer et sur la manière dont l’utilisateur peut créer un environnement.

### Service de création AEM {#author-services}

Le service de création AEM est inclus dans un environnement dans lequel le contenu du site et les ressources numériques sont créés, gérés et mis à jour. En règle générale, seuls les utilisateurs internes ont accès au service de création et se trouvent derrière un écran de connexion. Le service de création est conçu comme un environnement de création et de prévisualisation.

### Service de publication AEM {#publish-services}

Le service de publication AEM est inclus dans un environnement qui héberge l’expérience de l’utilisateur final, comme un site web. Il s’agit du service que les visiteurs du site vont voir et avec lequel ils interagiront. En règle générale, le service de publication est disponible publiquement.

### Service AEM Dispatcher {#dispatcher-services}

Dispatcher est un module `Apache HTTP Web server` qui fournit une couche de sécurité et de performances se trouvant devant le service de publication AEM.
