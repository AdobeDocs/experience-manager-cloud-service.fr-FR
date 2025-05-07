---
title: Équipe et profils de produits AEM as a Cloud Service
description: Découvrez comment l’équipe et les profils de produits AEM as a Cloud Service accordent et limitent l’accès à vos solutions Adobe sous licence.
exl-id: 7b1474c9-aca0-4354-8798-1abdcda2f6dd
feature: Onboarding
role: Admin, User, Developer
source-git-commit: b9cc5450effb70afcb67725fe38826646d947da9
workflow-type: tm+mt
source-wordcount: '2124'
ht-degree: 100%

---


# Équipe et profils de produits AEM as a Cloud Service {#product-profiles}

Découvrez comment l’équipe et les profils de produits AEM as a Cloud Service accordent et limitent l’accès à vos solutions Adobe sous licence.

## Profils de produit {#profiles}

Lorsque vous accordez à un utilisateur l’accès à une solution Adobe spécifique, vous ne souhaitez pas nécessairement lui accorder un accès complet. Les profils de produit permettent à chaque solution d’avoir son propre jeu d’autorisations utilisateur. Ils sont disponibles et accessibles à partir de l’[Admin Console](/help/journey-onboarding/admin-console.md).

Adobe Admin Console comporte une hiérarchie structurée de produits, d’instances de produits et de profils de produits dans laquelle les utilisateurs et utilisatrices internes d’une organisation peuvent se voir attribuer une appartenance, leur donnant accès aux solutions et fonctionnalités qui ont reçu une licence.

<!-- Alexandru: Drafting for now 

Your AEM as a Cloud Service team members are added and assigned to one or more of the following product profiles via the Admin Console during onboarding.

* **AEM Administrators**: An AEM administrator is typically assigned to developers, in particular developers who need access to, for example, the development environments. The AEM administrator's product profile is used to grant administrator privileges in the associated AEM instance.

* **AEM Users**: AEM users are the users in your organization who use AEM as a Cloud Service generally to create content. These users need to access AEM to do their tasks. The AEM users product profile is typically assigned to an AEM content author who creates and reviews the content. This content can be of many types such as pages, assets, publications, and so on. The AEM users product profile shown below is assigned to these members.

![Product profiles](/help/onboarding/assets/admin-console-profiles.png) -->

## Profils de produit AEM as a Cloud Service {#aem-product-profiles}

AEM as a Cloud Service est une offre entièrement native cloud qui fournit AEM as a service. Elle fournit AEM de manière native au cloud, avec de nouveaux attributs comme toujours activé, toujours à jour, toujours sécurisé et toujours à grande échelle. Dans le même temps, elle conserve la proposition de valeur principale qu’AEM fournit en tant que plateforme personnalisable aux clients et permet aux équipes de niveau entreprise d’intégrer dans leur procédure de développement et de diffusion. Pour en savoir plus sur AEM as a Cloud Service, voir [Présentation d’Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md).

### Instances de produit au niveau de l’organisation {#org-level-product-instances}

>[!NOTE]
>
> Certaines instances de produit et certains profils de produit décrits dans cet article peuvent uniquement apparaître pour les environnements nouvellement créés. Consultez la section [Ajout de profils de produit pour les environnements existants](#adding-product-profiles-for-existing-environments) pour savoir comment moderniser vos environnements.

Lors du premier traitement par Adobe de la licence d’une solution AEM, deux instances de produit s’affichent dans Adobe Admin Console, sous le produit Adobe Experience Manager as a Cloud Service :

* **AEM au niveau de l’organisation** : contient un ou plusieurs profils de produit qui représentent l’accès aux fonctionnalités qui sont étendues à tous les environnements AEM, plutôt qu’à un seul.
* **Cloud Manager** : contient des profils de produit correspondant à différents niveaux d’accès aux fonctionnalités Cloud Manager.

<!--
>[!NOTE]
>
>For existing programs, the AEM Org-Level Product Instance is created upon selecting the **Update product** profiles action for a given environment.
-->

![Instances de produit au niveau de l’organisation](/help/onboarding/assets/orglevel.png)

Au sein de l’instance de produit AEM au niveau de l’organisation se trouve un profil de produit nommé AEM Org-Level Reporters, qui n’est pas utilisé pour l’instant, mais qui peut représenter à l’avenir l’accès à la récupération d’informations sur les licences de produit AEM.

Lorsqu’une solution de communication Forms est sous licence, un profil de produit correspondant s’affiche également sous l’instance de produit AEM au niveau de l’organisation.

![Profil de produit Reporters](/help/onboarding/assets/org-level-reporters.png)

### Instances de produit au niveau de l’environnement et du niveau {#environment-and-tier-level-product-instances}

Lors de la mise en service de nouveaux programmes avec un ou plusieurs environnements AEM, deux instances de produit s’affichent par environnement, contenant respectivement des profils de produit pour la création et la publication.

![Instances de produit d’environnement](/help/onboarding/assets/env-productinstances.png)

Vous trouverez ci-dessous les profils de produit dans une instance de produit de création, pour une organisation qui a configuré un environnement dans un programme contenant AEM Sites :

![Instances de produit Sites](/help/onboarding/assets/sites-product-instances.png)

Le tableau suivant décrit une liste des profils de produit possibles sous une instance de produit spécifique au niveau de l’environnement.

<table style="table-layout:auto">
    <tr>
        <th>Instance de produit</th>
        <th>Convention de nommage</th>
        <th>Service par défaut</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>Instance de création AEM</td>
        <td>Responsables du contenu AEM Sites - Création - Programme <code>id</code> - Environnement <code>id</code></td>
        <td>Responsables du contenu AEM Sites</td>
        <td>
            <ul>
                <li>Destiné à un accès contrôlé aux fonctionnalités de création d’AEM Sites dans cet environnement. Les utilisateurs et utilisatrices de ce profil de produit seront membres du groupe AEM de création de contenu AEM Sites, qui est automatiquement créé dans AEM. Les autorisations de groupe AEM doivent être configurées dans AEM avec le niveau d’accès souhaité.</li><br>
                <li>Si le service par défaut reste sélectionné,
                    <ul>
                        <li>les utilisateurs et utilisatrices de ce profil de produit seront également membres du groupe AEM « Responsables du contenu AEM Sites - Service ».</li>
                      <!--  <li>users in this product profile will have access to AEM Sites Content Management API.</li>
                        <li>an Adobe Developer Console API OAuth S2S project containing AEM Sites Content Management API can optionally be scoped to this environment.</li>-->
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>Administrateurs et administratrices AEM - Création - Programme <code>id</code> - Environnement <code>id</code></td>
        <td>Administrateurs et administratrices AEM</td>
        <td>
            <ul>
                <li>Prévu pour un accès illimité aux fonctionnalités de l’environnement de création et de publication d’AEM. Les utilisateurs et utilisatrices de ce profil de produit seront membres du groupe AEM Administrateurs et administratrices de création AEM automatiquement créé dans AEM.</li><br>
                <li>Si le service par défaut reste sélectionné,
                    <ul>
                        <li>Les utilisateurs et utilisatrices de ce profil de produit seront également membres du groupe AEM « Administrateurs et administratrices AEM - Service ».</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>Utilisateurs et utilisatrices AEM - Création - Programme <code>id</code> - Environnement <code>id</code></td>
        <td>Utilisateurs et utilisatrices AEM</td>
        <td>
            <ul>
                <li>Destiné à un accès très limité aux fonctionnalités de l’environnement de création AEM. Les utilisateurs et utilisatrices de ce profil de produit seront membres du groupe AEM « Contribution » automatiquement créé dans AEM.</li><br>
                <li>Si le service par défaut reste sélectionné,
                    <ul>
                        <li>Les utilisateurs et utilisatrices de ce profil de produit seront également membres du groupe AEM « Utilisateurs et utilisatrices AEM - Service ».</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM Reporters - Création - Programme <code>id</code> - Environnement <code>id</code></td>
        <td>AEM Reporters</td>
        <td>
            <ul>
                <li>N’est pas utilisé actuellement, mais à l’avenir, peut donner accès aux informations de création de rapports pour le niveau créateur/créatrice de cet environnement.</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>Collaboration AEM Assets - Création - Programme <code>id</code> - Environnement <code>id</code></td>
        <td>Utilisateurs collaborateurs et utilisatrices collaboratrices AEM Assets</td>
        <td>
        <ul>
                <li>Utiliser des ressources d’Experience Manager via des intégrations d’Assets disponibles pour votre entreprise dans d’autres produits Adobe et applications autres qu’Adobes.
                </li>
                <li>Créer et modifier des ressources à l’aide d’Adobe Express intégré et de Firefly en exploitant des modèles, des kits de marque, des ressources Adobe Stock, etc., tous conçus de manière professionnelle.</li>
                <li>Accéder aux ressources approuvées et les utiliser dans votre entreprise à l’aide du portail AEM Assets Content Hub.</li>
          <ul>
    </tr>
    <tr>
        <td></td>
        <td>Utilisateurs et utilisatrices experts AEM Assets - Création - Programme <code>id</code> - Environnement <code>id</code></td>
        <td>Utilisateurs et utilisatrices experts AEM Assets</td>
<td>
        <ul>
                <li>Accéder à toutes les fonctionnalités d’AEM Assets, notamment la gestion des ressources, des métadonnées et la gouvernance globale et l’automatisation autour des ressources numériques.</li>
                <li>Utiliser des ressources d’Experience Manager via des intégrations d’Assets disponibles pour votre entreprise dans d’autres produits Adobe et applications autres qu’Adobes.
                </li>
                <li>Créer et modifier des ressources à l’aide d’Adobe Express intégré et de Firefly en exploitant des modèles, des kits de marque, des ressources Adobe Stock, etc., tous conçus de manière professionnelle.</li>
                <li>Accéder aux ressources approuvées et les utiliser dans votre entreprise à l’aide du portail AEM Assets Content Hub.</li>
          <ul>
</td>
    </tr>
    <tr>
        <td></td>
        <td>Responsable de contenu AEM Forms - Création - Programme <code>id</code> - Environnement <code>id</code></td>
        <td>Responsables de contenu AEM Forms</td>
        <td>
            <ul>
                <li>Destiné à un accès contrôlé aux fonctionnalités de création d’AEM Forms dans cet environnement. Les utilisateurs et utilisatrices de ce profil de produit seront membres du groupe AEM « Utilisateurs et utilisatrices des formulaires AEM Forms », qui est automatiquement créé dans AEM.</li><br>
                <li>Si le service par défaut reste sélectionné,
                    <ul>
                        <li>Les utilisateurs et utilisatrices de ce profil de produit seront également membres du groupe d’AEM « Responsables de contenu AEM Forms - Service ».</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>Développement AEM Forms - Création - Programme <code>id</code> - Environnement <code>id</code></td>
        <td>Développement AEM Forms</td>
        <td>
            <ul>
                <li>Destiné à un accès contrôlé aux fonctionnalités de création d’AEM Forms dans cet environnement. Les utilisateurs et utilisatrices de ce profil de produit seront membres du groupe AEM « Utilisateurs et utilisatrices experts en formulaires AEM Forms », qui est automatiquement créé dans AEM. Ces utilisateurs et utilisatrices ont le droit de charger des fichiers XDP et de créer des modèles de données de formulaire en plus des tâches de création de formulaire normales.</li><br>
                <li>Si le service par défaut reste sélectionné,
                    <ul>
                        <li>Les utilisateurs et utilisatrices de ce profil de produit seront également membres du groupe AEM « Développement AEM Forms - Service ».</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>Utilisateurs et utilisatrices du service de communications AEM Forms - Création - Programme <code>id</code> - Environnement <code>id</code></td>
        <td>Utilisateurs et utilisatrices du service de communications AEM Forms</td>
        <td>
            <ul>
                <li>Destiné à un accès contrôlé aux fonctionnalités des services de communication AEM Forms sur cet environnement. Les utilisateurs et utilisatrices de ce profil de produit seront membres du groupe AEM « Utilisateurs et utilisatrices des formulaires AEM Forms », qui est automatiquement créé dans AEM.</li><br>
                <li>Si le service par défaut reste sélectionné,
                    <ul>
                        <li>Les utilisateurs et utilisatrices de ce profil de produit seront également membres du groupe AEM « Utilisateurs et utilisatrices AEM Forms Communications Service - Service ».</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td>Publication AEM</td>
        <td>Utilisateurs et utilisatrices AEM - Publication - Programme <code>id</code> - Environnement <code>id</code></td>
        <td>Utilisateurs et utilisatrices AEM</td>
        <td>
            <ul>
                <li>Destiné à un accès très limité aux fonctionnalités de l’environnement de création AEM. Les utilisateurs et utilisatrices de ce profil de produit seront membres du groupe AEM « Contrib » automatiquement créé dans AEM.</li><br>
                <li>Si le service par défaut reste sélectionné,
                    <ul>
                        <li>Les utilisateurs et utilisatrices de ce profil de produit seront également membres du groupe AEM « Utilisateurs et utilisatrices AEM - Service ».</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM Reporters - Publication - Programme <code>id</code> - Environnement <code>id</code></td>
        <td>AEM Reporters</td>
        <td>
            <ul>
                <li>N’est pas utilisé actuellement, mais à l’avenir, peut donner accès aux informations de création de rapports pour le niveau de publication de cet environnement.</li>
            </ul>
        </td>
    </tr>
   <tr>
        <td></td>
        <td>Utilisateurs et utilisatrices du service de communication AEM Forms - Publication - Programme <code>id</code> - Environnement <code>id</code></td>
        <td>Utilisateurs et utilisatrices du service de communications AEM Forms</td>
        <td>
            <ul>
                <li>Destiné à un accès contrôlé aux fonctionnalités des services de communication AEM Forms sur cet environnement. Les utilisateurs et utilisatrices de ce profil de produit seront membres du groupe AEM « Utilisateurs et utilisatrices des formulaires AEM Forms », qui est automatiquement créé dans AEM.</li><br>
                <li>Si le service par défaut reste sélectionné,
                    <ul>
                        <li>Les utilisateurs et utilisatrices de ce profil de produit seront également membres du groupe AEM « Utilisateurs et utilisatrices AEM Forms Communications Service - Service ».</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
</table>

Notez que le service de profil de produit associé est activé par défaut pour chaque profil de produit. À moins que vous n’ayez des exigences d’accès complexes, il est recommandé de ne conserver que le service par défaut sélectionné. Un groupe AEM correspondant sera créé dans AEM avec la convention de nommage `<Product Profile Prefix> - Service` (par exemple, **Responsables de contenu AEM Sites - Service**), et les utilisateurs et utilisatrices des profils de produit parent deviendront automatiquement membres de ce groupe AEM correspondant.

Le groupe AEM dans AEM associé au service aura l’ensemble agrégé d’utilisateurs et utilisatrices qui existent dans tous les profils de produit associés à ce service pour cette combinaison de niveau environnement.

![Services](/help/onboarding/assets/services.png)

L’image suivante représente les groupes AEM reflétant le profil de produit et le service de niveau Création des Responsables de contenu AEM Sites.

![Mappage Groupe vers Service AEM](/help/onboarding/assets/profile-to-service-mapping.png)

>[!NOTE]
>
>Chaque utilisateur/utilisatrice affecté(e) à un profil de produit AEM as a Cloud Service dispose d’un accès en lecture seule à Cloud Manager via le rôle **Utilisateur de Cloud Manager**.
>
>Les utilisateurs disposant uniquement du rôle **Utilisateur de Cloud Manager** peuvent se connecter à Cloud Manager et accéder aux environnements de création AEM (s’ils existent) à l’aide des options de menu **Programmes**. Le rôle **Utilisateur de Cloud Manager** n’est pas suffisant pour accéder aux détails du programme. Si cet accès est nécessaire, les utilisateurs doivent faire appel à leur administrateur/administratrice système pour recevoir des rôles supplémentaires.

>[!WARNING]
>
>Le nom du profil de produit **Administrateurs et administratrices AEM** ne doit pas être modifié. La modification du nom du profil de produit **Administrateurs et administratrices AEM** supprime les droits d’administration de toutes les personnes affectées à ce profil.

>[!TIP]
>
>* Pour en savoir plus sur les profils de produits d’AEM, consultez [Attribuer des profils de produit d’AEM](/help/journey-onboarding/assign-profiles-aem.md).
>* Pour plus d’informations sur le processus d’intégration, voir [parcours d’intégration](/help/journey-onboarding/overview.md).

### Ajout de profils de produit pour les environnements existants {#adding-product-profiles-for-existing-environments}

Il se peut que l’instance de produit au niveau de l’organisation décrite dans les sections ci-dessus ainsi que certains profils de produit soient absents des environnements créés avant le début d’avril 2024. Les bascules de service seront également absents des profils de produit existants. Il est recommandé de mettre à jour ces profils de produit, ce qui est un prérequis pour accéder à d’autres API à l’avenir.

Si un ou plusieurs environnements d’un programme nécessitent la mise à jour de leurs profils de produit, Cloud Manager affiche la note ci-dessous. Notez qu’un environnement doit se trouver sur la dernière version d’AEM pour que ses profils de produit puissent être mis à jour.

![Moderniser des profils de produit](/help/onboarding/assets/modernize-product-profiles.png)

Cliquez sur le bouton **Ajouter des profils de produit** pour ouvrir un menu qui affiche des options permettant d’ajouter de nouveaux profils de produit à tous les environnements disponibles dans le programme ou les environnements individuels.

![Remplacer des environnements](/help/onboarding/assets/choose-env-r.png)

Cliquez sur **Tous les environnements** pour ajouter les nouveaux profils de produit à tous les environnements du programme. Vous pouvez également cliquer sur **Environnements individuels** pour ajouter les nouveaux profils de produit aux environnements sélectionnés ; la personne accède ainsi à une page de liste Environnements, où une action **Ajouter des profils de produit** peut être sélectionnée à partir de l’icône **Plus d’options**.

![Environnements individuels](/help/onboarding/assets/individual-environments.png)

Vous pouvez également ajouter des profils de produit aux environnements sélectionnés en accédant à la section Environnements de la page Aperçu du programme, en cliquant sur l’icône Plus d’options correspondant à un environnement et en sélectionnant Ajouter des profils de produit.

Le statut de l’environnement affiche l’option Ajouter des profils de produit pendant l’ajout des nouveaux profils de produit, puis s’affiche comme étant En cours d’exécution lorsque le processus est terminé.


## Profils de produit Cloud Manager {#cloud-manager-product-profiles}

Cloud Manager dispose de profils de produit préconfigurés qui peuvent être considérés comme des autorisations basées sur les rôles. L’administrateur système est chargé de configurer votre équipe Cloud Manager en affectant ses membres à ces profils de produit.

>[!TIP]
>
>Pour plus d’informations, voir [Autorisations basées sur les rôles dans Cloud Manager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions).

Chacun des profils de produit est associé à des autorisations spécifiques.

* **Personne propriétaire de l’entreprise**
   * Ce rôle vous donne l’autorisation d’ajouter ou de modifier un programme, d’ajouter ou de mettre à jour un environnement, de déployer du code dans un environnement AEM ou d’exécuter des contrôles qualité du code.
   * Cette personne est chargée de définir les indicateurs de performance clés (KPI), d’approuver les déploiements en production et de remplacer les échecs importants à 3 niveaux si nécessaire.
* **Personne responsable du déploiement**
   * Ce rôle vous donne l’autorisation d’ajouter ou de mettre à jour un environnement, d’exécuter n’importe quel pipeline et de déployer du code dans un environnement AEM ou d’exécuter des contrôles qualité du code.
   * Cette personne gère les opérations de déploiement et utilise Cloud Manager pour exécuter des déploiements d’évaluation/de production, modifier les pipelines CI/CD ou approuver des échecs importants à 3 niveaux si nécessaire. Elle peut également accéder au référentiel Git.
* **Développeur ou développeuse**
   * Ce rôle vous donne l’autorisation de générer des jetons d’accès personnel à Git.
   * Cette personne développe et teste des codes d’application personnalisés et utilise principalement Cloud Manager pour afficher l’état du déploiement. Elle peut accéder au référentiel Git pour les validations de code.
* **Personne responsable de programme**
   * Ce rôle vous donne l’autorisation de planifier des pipelines, de remplacer les points de contrôle qualité à 3 niveaux et de fournir l’approbation de production.
   * Cette personne utilise Cloud Manager pour effectuer la configuration de l’équipe, réviser l’état, afficher les ICP et approuver les échecs importants à 3 niveaux si nécessaire.

Un utilisateur peut être affecté à plusieurs profils de produit. Par exemple, l’attribution des rôles **Propriétaire de l’entreprise** et **Responsable de déploiement** à un utilisateur leur donne la somme de ces autorisations.

Votre équipe Cloud Manager comprend au moins :

* Un **propriétaire d’entreprise**, qui est généralement aussi l’administrateur système et doit être la première personne à se connecter et accéder à Cloud Manager.
* Un **responsable de déploiement**
* Un **développeur**

>[!NOTE]
>
>Pour pouvoir accéder à AEM as a Cloud Service, les utilisateurs doivent appartenir à l’un des deux profils de produit suivants : `AEM Users` ou `AEM Administrators`. Les autorisations d’administration de Cloud Manager ne suffiront pas.

>[!TIP]
>
>* Pour en savoir plus sur les profils de produits Cloud Manager, consultez [Attribuer des personnes membres de l’équipe à des profils de produit Cloud Manager](/help/journey-onboarding/assign-profiles-cloud-manager.md).
>* Pour plus d’informations sur le processus d’intégration, voir [parcours d’intégration](/help/journey-onboarding/overview.md).
