---
title: Présentation de Cloud Manager
description: Découvrez comment Cloud Manager prend en charge votre projet AEM par le biais de ses programmes, environnements et pipelines.
exl-id: b743f126-b34e-4f48-a3f0-5dbd4e1ac34e
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 99%

---


# Présentation de Cloud Manager {#intro-cloud-manager}

Cloud Manager est un composant essentiel d’AEM as a Cloud Service et constitue le point d’entrée unique de votre équipe. Ses pipelines CI/CD spécialement conçus sont équipés pour garantir des tests approfondis et une qualité de code optimale afin de fournir des expériences exceptionnelles. Pour que les clients puissent démarrer rapidement leurs projets, Cloud Manager fournit tout ce dont ils ont besoin en libre-service, notamment la possibilité de créer vos ressources et environnements cloud et d’accéder à vos référentiels Git. Ces fonctionnalités prennent en charge les configurations de développement d’entreprise afin que les équipes puissent s’efforcer de réaliser fréquemment des modifications, de proposer rapidement des expériences digitales exceptionnelles et d’accélérer le délai de rentabilisation.

Votre administrateur système sera chargé de configurer votre équipe Cloud Manager, qui comprendra les personnes qui créeront vos ressources cloud ainsi que vos développeurs. Pour plus d’informations sur la configuration et la mise à l’échelle de votre équipe de développement d’entreprise et sur la manière dont AEM as a Cloud Service peut prendre en charge votre processus de développement, consultez [Configuration du développement de l’équipe Entreprise pour AEM as a Cloud Service](/help/implementing/cloud-manager/managing-code/enterprise-team-dev-setup.md).

## Accès à la page de présentation de Cloud Manager {#navigate-cloud-manager}

Pour accéder à Cloud Manager, procédez comme suit.

1. Accédez à la page de connexion de Cloud Manager à l’adresse [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/).

1. Sélectionnez le programme dans la page **Programmes et produits** de Cloud Manager pour lancer la page **Présentation**.

Vous pouvez également accéder à la page Programmes et produits de Cloud Manager à partir de la page d’accueil d’Adobe Experience Cloud.

1. Accédez à Adobe Experience Cloud à l’adresse [`https://experience.adobe.com`](https://experience.adobe.com) et connectez-vous à l’aide de votre Adobe ID.

1. Assurez-vous que vous vous trouvez dans la bonne organisation en vous référant au nom de l’organisation affiché dans le coin supérieur droit de la barre d’outils.

1. Sélectionnez **Experience Manager**.

1. Sur la vignette **Cloud Manager**, cliquez sur **Lancer**.

## Permissions basées sur les rôles dans Cloud Manager {#role-based-permissions}

| Autorisation | Description | Propriétaire de l’entreprise | Responsable de déploiement | Responsable de programme | Développeur ou développeuse |
|--- |--- |--- |--- |--- |--- |
| Ajouter le programme<br>Modifier le programme | Ajouter un nouveau programme<br>Ajouter ou supprimer des solutions ou des modules complémentaires | x |  |  |  |
| Créer un environnement | Créer des environnements de production, d’évaluation et de développement. | x | x |  |  |
| Mettre à jour l’environnement | Mettre à jour les environnements de production, d’évaluation et de développement | x | x |  |  |
| Suppression de l’environnement de dév | Supprimez les environnements de développement | x | x |  |  |
| Configuration du pipeline | Configurer et modifier les pipelines |  | x |  |  |
| Exécution du pipeline | Démarrer les pipelines | x | x |  |  |
| Exécution du pipeline | Rejeter/approuver les échecs importants du point de contrôle qualité à trois niveaux | x | x | x |  |
| Exécution du pipeline | Fournir une approbation de mise en production | x | x | x |  |
| Exécution du pipeline | Planifier des déploiements de production | x | x | x |  |
| Suppression de pipeline | Autoriser la suppression du pipeline |  | x |  |  |
| Annuler l’exécution | Annuler l’exécution actuelle |  | x |  |  |
| Génération d’un jeton d’accès personnel | Accéder à Git |  | x |  | x |
| Créer un RDE | Créer un environnement de développement rapide | x |  |  | x |
| Réinitialiser un RDE | Réinitialiser un environnement de développement rapide | x |  |  | x |
| Créer et modifier des jeux de contenu | Créer ou modifier un jeu de contenu pour la copie de contenu |  | x |  |  |
| Démarrer ou annuler la copie de contenu | Démarrer ou annuler un processus de copie de contenu |  | x |  |  |

>[!NOTE]
>
>Un utilisateur peut être affecté à plusieurs rôles. Par exemple, attribuer les deux rôles de **Propriétaire de l’entreprise** et de **Responsable de déploiement** à un utilisateur ou une utilisatrice lui donne la somme de ces autorisations.

>[!TIP]
>
>Des profils d’autorisation personnalisés avec des autorisations configurables sont également disponibles. Pour plus de détails, consultez le document [Autorisations personnalisées](/help/implementing/cloud-manager/custom-permissions.md).

## Programmes Cloud Manager {#cloud-manager-programs}

Les programmes Cloud Manager représentent des ensembles d’environnements Cloud Manager prenant en charge des regroupements logiques d’initiatives commerciales. Ces regroupements correspondent généralement à un contrat de niveau de service (SLA) acheté. Par exemple, un programme peut représenter les ressources AEM pour prendre en charge le site Web public d’une organisation, tandis qu’un autre programme représente la gestion des ressources numériques (DAM) internes.


Regardez cette [vidéo](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=fr) pour en savoir plus sur l’utilisation des programmes Cloud Manager.

Un utilisateur peut créer un programme **Sandbox** ou de **Production**.

* Un **programme de production** est créé pour activer dans le futur le trafic dynamique au moment approprié.
   * Consultez [Présentation des programmes de production](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md) pour plus d’informations.

* Un **programme Sandbox** est généralement créé à des fins de formation, de démonstration, d’activation, de création des POC ou de documentation.
   * Ces programmes ne sont pas destinés à gérer un trafic dynamique et comporteront des restrictions absentes d’un programme de production.
   * Il inclut Sites et Assets et est pourvu automatiquement d’une branche Git comprenant un exemple de code, un environnement de développement et un pipeline hors production.
   * Consultez [Présentation des programmes de sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md) pour plus d’informations.

## Environnements Cloud Manager {#cloud-manager-environments}

Vos environnements cloud sont créés, accessibles et visualisés via Cloud Manager. Ces environnements peuvent être des environnements de production, d’évaluation ou de développement. Les différents environnements prennent en charge différents objectifs et peuvent être utilisés à l’aide de différents pipelines CI/CD. Les environnements sont composés de services tels que :

* [Services de création AEM](#author-services)
* [Services de publication AEM](#publish-services)
* [Services Dispatcher](#dispatcher-services)

>[!TIP]
>
> Reportez-vous à la vidéo [Utilisation des environnements Adobe Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=fr) pour en savoir plus sur les environnements disponibles.
>
>Voir [Gestion des environnements](/help/implementing/cloud-manager/manage-environments.md) pour en savoir plus sur les types d’environnement qu’une personne utilisatrice peut créer et sur la manière dont elle peut créer un environnement.

### Service de création AEM {#author-services}

Un service de création AEM est inclus dans un environnement où le contenu du site et les ressources numériques sont créés, gérés et mis à jour. En règle générale, seuls les utilisateurs internes ont accès au service de création qui se trouve derrière un écran de connexion. Le service de création joue le rôle d’environnement de création et de prévisualisation.

### Service de publication AEM {#publish-services}

Un service de publication AEM est inclus dans les environnements qui hébergent l’expérience de l’utilisateur final, comme un site web. Il s’agit du service que les visiteurs du site vont voir et avec lequel ils interagiront. En règle générale, le service de publication est disponible publiquement.

### Service AEM Dispatcher {#dispatcher-services}

Dispatcher est un module `Apache HTTP Web server` qui fournit une couche de sécurité et de performances se trouvant devant le service de publication AEM.
