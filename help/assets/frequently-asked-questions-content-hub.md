---
title: Questions fréquentes sur Content Hub
description: Obtenez des réponses à certaines des questions les plus fréquemment posées (FAQ) pour Content Hub.
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '1100'
ht-degree: 0%

---

# Questions fréquentes sur Content Hub {#content-hub-frequently-asked-questions}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [ Bonnes pratiques en matière de métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Dynamic Media avec fonctionnalités OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation destinée aux développeurs AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

![Questions fréquentes sur Content Hub](assets/content-hub-faqs.png)

## Qu’est-ce que Content Hub ? {#what-is-content-hub}

Content Hub est une fonctionnalité d’Adobe Experience Manager Assets as a Cloud Service.

Content Hub permet aux équipes plus larges de découvrir facilement des ressources pertinentes et approuvées grâce à un portail intuitif et de les adapter rapidement à leurs besoins.  En outre, Content Hub fournit un mécanisme d’ingestion qui permet à ces utilisateurs de se servir facilement lorsqu’ils chargent des ressources dans la gestion des ressources numériques. Cela permet de répondre directement aux besoins des entreprises en termes de vitesse de création de contenu supérieure, tout en préservant la cohérence de la marque et la conformité avec les garanties appropriées.

## Pourquoi ne puis-je pas activer Content Hub dans mon programme/environnement Cloud Manager ? {#cannot-enable-content-hub}

Content Hub n’est à ce stade disponible que sur les programmes de production AEM Cloud Manager, qui incluent une licence Assets. Lorsque vous cliquez sur [Content Hub](/help/assets/deploy-content-hub.md#enable-content-hub) pour l’activer, il est déployé et associé à l’environnement de production de création d’AEM dans ce programme. Voir [Déploiement de Content Hub](/help/assets/deploy-content-hub.md) pour plus d’informations et connaître les conditions préalables.

Il existe un programme d’accès anticipé à Content Hub sur les programmes Sandbox / les environnements de production de création. Pour plus d’informations, voir [Introduction aux programmes Sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md). Pour en savoir plus sur le programme d’accès anticipé, contactez votre équipe de compte d’Adobe.

Content Hub n’est pas disponible pour les environnements hors production (évaluation, développement, etc.) à ce stade.

## J’ai activé Content Hub dans mon programme/environnement de production, puis-je le désactiver ? {#can-i-disable-content-hub}

L’activation de Content Hub sur un programme de production le déploie dans une partie de l’infrastructure de production. AEM Cloud Manager ne permet pas de supprimer ou de désactiver l’infrastructure de production afin de minimiser les risques d’utilisation de la production en raison d’erreurs humaines.

Si vous ne souhaitez pas fournir Content Hub à vos utilisateurs une fois qu’il a été déployé, n’affectez aucun utilisateur au profil de produit Content Hub dans Admin Console. Voir [Déploiement de Content Hub](/help/assets/deploy-content-hub.md#content-hub-instance-product-profile) pour plus d’informations.

## Comment évaluer Content Hub dans mon entreprise, étant donné qu’il est uniquement disponible pour les programmes de production/les environnements de création de production ? {#how-can-i-evaluate-content-hub}

Content Hub est une fonctionnalité que Adobe fournit et gère et qui ne comporte pas de code personnalisé qui nécessiterait une validation type via dev/stage/production. En outre, l’accès à la fonctionnalité pour les utilisateurs est entièrement contrôlé par l’administrateur, de sorte que vous pouvez l’évaluer sans l’exposer à tous les utilisateurs.

Il est possible d’évaluer Content Hub sans affecter le contenu des utilisateurs/de production géré dans AEM as a Cloud Service Assets. Une procédure d’évaluation peut se présenter comme suit :

* [Activer Content Hub](/help/assets/deploy-content-hub.md#enable-content-hub) dans l’environnement de production (programme Cloud Manager)
* [Ajoutez un utilisateur administrateur AEM](/help/assets/deploy-content-hub.md#onboard-content-hub-administrator) de l’auteur de production au profil de produit Content Hub.
* AEM administrateur [ configure Content Hub](/help/assets/configure-content-hub-ui-options.md)
* AEM’administrateur ou un utilisateur AEM sur l’auteur de production d’AEM [approuve un certain nombre de ressources pour Content Hub](/help/assets/approve-assets-content-hub.md) ; si vous ne souhaitez pas modifier le contenu de production dans la gestion des ressources numériques, vous pouvez créer un dossier d’évaluation distinct dans l’instance d’auteur d’, puis charger/baliser ou copier certaines ressources de la gestion des ressources numériques dans cette instance.
* L’administrateur Admin Console ajoute [ quelques utilisateurs sélectionnés](/help/assets/deploy-content-hub.md#onboard-content-hub-users) au profil de produit Content Hub, afin qu’ils puissent commencer l’évaluation.
* Une fois l’évaluation terminée, AEM utilisateurs de l’instance d’auteur peuvent supprimer l’approbation des ressources de test, approuver les ressources de production pour Content Hub, puis l’administrateur Admin Console peut ajouter tous les utilisateurs qui ont besoin d’accéder à Content Hub et au contenu approuvé. Félicitations, votre Content Hub est en ligne maintenant.

Adobe propose également un programme d’accès anticipé à Content Hub dans les environnements intermédiaires. Pour plus d’informations, reportez-vous à la question [Pourquoi ne puis-je pas activer Content Hub dans mon programme/environnement Cloud Manager ?](#cannot-enable-content-hub) pour plus de détails.

## Pourquoi les ressources ne s’affichent-elles pas une fois que je me suis connecté à Content Hub ? {#no-assets-in-content-hub}

Les ressources marquées comme approuvées dans Assets as a Cloud Service sont automatiquement disponibles dans Content Hub. Si vous ne voyez aucune ressource après vous être connecté à Content Hub, approuvez les ressources à l’aide de l’environnement de création AEM as a Cloud Service pour les rendre disponibles dans Content Hub. Pour plus d’informations, voir [Approbation de ressources pour Content Hub](/help/assets/approve-assets-content-hub.md).

## Pourquoi mes ressources que je charge directement à l’aide de Content Hub ne s’affichent-elles pas, ou ne sont-elles pas importées à partir de comptes Dropbox ou OneDrive à l’aide de Content Hub ? {#no-assets-uploaded-from-content-hub}

L’affichage des ressources chargées à l’aide de Content Hub dépend de l’activation ou non du bouton [Validation automatique](/help/assets/configure-content-hub-ui-options.md#configure-import-options-content-hub) disponible dans l’interface utilisateur de configuration :

* Si le bouton d’approbation automatique **est activé, les ressources que vous chargez à l’aide de Content Hub sont automatiquement disponibles.**

* Si le bouton d’approbation **automatique** est désactivé, les ressources que vous chargez à l’aide de Content Hub ne s’affichent pas automatiquement. Les ressources sont disponibles dans le dossier `hydrated-assets` de votre environnement as a Cloud Service Assets. Accédez au dossier et [modifiez en masse](/help/assets/approve-assets-content-hub.md) l’état de ces ressources sur `Approved` pour que ces ressources s’affichent dans Content Hub.

## Comment rechercher rapidement des ressources chargées à l’aide de Content Hub dans l’environnement AEM as a Cloud Service ? {#find-uploaded-assets-on-aem-cloud}

Vous pouvez rapidement trouver les ressources chargées à l’aide de Content Hub dans l’environnement AEM as a Cloud Service en procédant comme suit :

1. Accédez au dossier `hydrated-assets`.

1. Cliquez sur **[!UICONTROL Filters]** et définissez **[!UICONTROL No Status]** dans le champ **[!UICONTROL Asset Status]**.

1. Tri des ressources à l’aide du champ **[!UICONTROL Date de modification]**.

## Pourquoi l’option Modifier à l’aide de l’Adobe Express de ma carte de ressources ne s’affiche-t-elle pas pour pouvoir remixer des ressources afin de créer de nouvelles variations ? {#edit-using-express-not-available}

Pour afficher la modification à l’aide de l’option d’Adobe Express sur la carte des ressources, vous devez disposer de droits d’Adobe Express en plus des privilèges pour les utilisateurs de [Content Hub ayant les droits de remix assets to new variations](#onboard-content-hub-users-add-assets). Adobe Express doit être déployé dans la même organisation dans Adobe Admin Console où Adobe Experience Manager est déployé.

## Puis-je configurer Content Hub de sorte que les directives de marque de mon entreprise s’affichent sous la forme d’un lien sur la page d’accueil ? {#content-hub-setup-brand-guidelines}

Vous pouvez ajouter des liens personnalisés sous forme d’onglets distincts en plus des onglets standard Toutes les Assets, Collections et Statistiques sur la page d’accueil de Content Hub. Pour plus d’informations sur la configuration, voir [Liens personnalisés](/help/assets/configure-content-hub-ui-options.md#configure-custom-links-content-hub).

## Existe-t-il un plan pour migrer les clients Brand Portal existants vers Content Hub ? {#migration-brand-portal}

Adobe fournit une assistance pour la migration de Brand Portal vers Content Hub que vous pouvez utiliser en créant un ticket d’assistance pour les Adobes.

## Pourquoi ne puis-je pas voir l’option Paramètres/configuration du produit dans Content Hub ? {#ui-configuration-option-missing}

Pour accéder à l’ [interface utilisateur de configuration](/help/assets/configure-content-hub-ui-options.md), vous devez être un [administrateur Content Hub](/help/assets/deploy-content-hub.md##onboard-content-hub-administrator). Si vous êtes affecté au profil de produit Administrateurs AEM sur l’instance d’auteur de production dans Adobe Admin Console et que vous ne pouvez toujours pas voir l’option de configuration, assurez-vous que le profil de produit Administrateurs AEM n’est pas renommé. Pour plus d’informations, voir [Équipe AEM as a Cloud Service et Profils de produit](/help/onboarding/aem-cs-team-product-profiles.md) .


