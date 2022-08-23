---
title: Présentation de Cloud Manager
description: Découvrez comment Cloud Manager prend en charge votre projet AEM par le biais de ses programmes, environnements et pipelines.
exl-id: b743f126-b34e-4f48-a3f0-5dbd4e1ac34e
source-git-commit: 2d793f22e554c2a4bde8831b5053d1640ba07c70
workflow-type: tm+mt
source-wordcount: '834'
ht-degree: 26%

---

# Présentation de Cloud Manager {#intro-cloud-manager}

Cloud Manager est un composant essentiel d’AEM as a Cloud Service et constitue le point d’entrée unique de votre équipe. Ses pipelines CI/CD conçus spécifiquement sont équipés pour garantir des tests approfondis et une qualité de code optimale afin de fournir des expériences exceptionnelles. Pour que les clients puissent démarrer rapidement leurs projets, Cloud Manager fournit tout ce dont ils ont besoin en libre-service, notamment la possibilité de créer vos ressources et environnements cloud et d’accéder à vos référentiels Git. Ces fonctionnalités prennent en charge les configurations de développement d’entreprise afin que les équipes puissent s’efforcer de réaliser fréquemment des modifications, de proposer rapidement des expériences numériques exceptionnelles et d’accélérer le délai d’évaluation.

Votre administrateur système est chargé de configurer votre équipe Cloud Manager, qui comprend les personnes qui vont créer vos ressources cloud et vos développeurs. Pour plus d’informations sur la configuration et la mise à l’échelle de votre équipe de développement d’entreprise et sur la manière dont AEM as a Cloud Service peut prendre en charge votre processus de développement, reportez-vous au document . [Configuration du développement de l’équipe d’entreprise pour AEM as a Cloud Service.](/help/implementing/cloud-manager/managing-code/enterprise-team-dev-setup.md)

## Accès à la page de présentation de Cloud Manager {#navigate-cloud-manager}

Pour accéder à Cloud Manager, procédez comme suit.

1. Accédez à la page de connexion de Cloud Manager à l’adresse [`https://my.cloudmanager.adobe.com`.](https://my.cloudmanager.adobe.com/).

1. Sélectionnez le programme dans le **Programmes et produits** pour lancer la page **Présentation** page.

Vous pouvez également accéder à la page Programmes et produits de Cloud Manager à partir de la page d’accueil de Adobe Experience Cloud en procédant comme suit.

1. Accédez à Adobe Experience Cloud à l’adresse [`https://experience.adobe.com`](https://experience.adobe.com) et connectez-vous à l’aide de votre Adobe ID.

1. Assurez-vous que vous vous trouvez dans la bonne organisation en vous référant au nom de l’organisation affiché dans le coin supérieur droit de la barre d’outils.

1. Sélectionnez **Experience Manager**.

1. Sur le **Cloud Manager** carte, cliquez sur **Launch**

## Permissions basées sur les rôles dans Cloud Manager {#role-based-permissions}

| Autorisation | Description | Propriétaire de l’entreprise | Responsable de déploiement | Responsable de programme | Développeur |
|--- |--- |--- |--- |--- |--- |
| Ajouter un programme<br>Modifier le programme | Ajout d’un nouveau programme<br>Ajout ou suppression de solutions ou de modules complémentaires | x |  |  |  |
| Créer un environnement | Créer des environnements de production et d’évaluation et de développement | x | x |  |  |
| Mettre à jour l’environnement | Mise à jour des environnements de production et d’évaluation et de développement | x | x |  |  |
| Suppression de l’environnement de dév | Suppression des environnements de développement | x | x |  |  |
| Configuration du pipeline | Configuration et modification de pipelines |  | x |  |  |
| Exécution du pipeline | Démarrage de pipelines | x | x |  |  |
| Exécution du pipeline | Rejeter/approuver les échecs de points de contrôle de qualité à trois niveaux importants | x | x | x |  |
| Exécution du pipeline | Approbation de la mise en ligne | x | x | x |  |
| Exécution du pipeline | Planification des déploiements de production | x | x | x |  |
| Suppression de pipeline | Autoriser la suppression du pipeline |  | x |  |  |
| Annuler l’exécution | Annuler l’exécution actuelle |  | x |  |  |
| Génération d’un jeton d’accès personnel | Accéder à Git |  | x |  | x |

>[!NOTE]
>
>Un utilisateur peut être affecté à plusieurs rôles. Par exemple, si vous attribuez les **Propriétaire de l’entreprise** et **Responsable de déploiement** les rôles d’un utilisateur donnent à l’utilisateur la somme de ces autorisations.

## Programmes Cloud Manager {#cloud-manager-programs}

Les programmes Cloud Manager représentent des ensembles d’environnements Cloud Manager prenant en charge des regroupements logiques d’initiatives commerciales. Ces regroupements correspondent généralement à un contrat de niveau de service (SLA) acheté. Par exemple, un programme peut représenter les ressources AEM pour prendre en charge le site Web public d’une organisation, tandis qu’un autre programme représente un DAM interne.


Regardez cette [vidéo](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=fr) pour en savoir plus sur l’utilisation des programmes Cloud Manager.

Un utilisateur peut créer un programme **Sandbox** ou de **Production**.

* A **programme de production** est créé pour activer le trafic en direct au moment approprié à l’avenir.
   * Veuillez consulter le document [Présentation des programmes de production](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md) pour plus d’informations.

* A **programme sandbox** est généralement créé à des fins de formation, d’exécution de démonstrations, d’activation, de création de points ciblés ou à des fins de documentation.
   * Il n’est pas destiné à transporter du trafic en direct et aura des restrictions qu’un programme de production ne mettra pas en place.
   * Elle comprend des sites et des ressources et est fournie avec une branche git automatiquement renseignée avec un exemple de code, un environnement de développement et un pipeline hors production.
   * Veuillez consulter le document [Présentation des programmes Sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md) pour plus d’informations.

## Environnements Cloud Manager {#cloud-manager-environments}

Vos environnements cloud seront créés, accessibles et visualisés via Cloud Manager. Ces environnements peuvent être des environnements de production, d’évaluation ou de développement. Différents environnements ont des objectifs différents et peuvent être utilisés avec différents pipelines CI/CD. Les environnements sont composés de services tels que :

* [AEM Services de création](#author-services)
* [AEM des services de publication](#publish-services)
* [Services Dispatcher](#dispatcher-services)

>[!TIP]
>
> Reportez-vous à la vidéo [Utilisation des environnements Adobe Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=fr) un aperçu des environnements disponibles.
>
>Reportez-vous au document [Gestion des environnements](/help/implementing/cloud-manager/manage-environments.md) pour en savoir plus sur les types d’environnement qu’un utilisateur peut créer et sur la manière dont il peut créer un environnement.

### Service de création d’AEM {#author-services}

Un service de création d’AEM est inclus dans les environnements dans lesquels le contenu du site et les ressources numériques sont créés, gérés et mis à jour. En règle générale, seuls les utilisateurs internes ont accès au service de création et il est conservé derrière un écran de connexion. Le service de création agit comme un environnement de création et de prévisualisation.

### Service de publication d’AEM {#publish-services}

Un service de publication AEM est inclus dans les environnements qui hébergent l’expérience de l’utilisateur final, comme un site web. Il s’agit du service que les visiteurs du site vont voir et avec lequel ils interagiront. En règle générale, le service de publication est disponible publiquement.

### Service AEM Dispatcher {#dispatcher-services}

Dispatcher est un `Apache HTTP Web server` qui fournit une couche de sécurité et de performance devant le service de publication d’AEM.
