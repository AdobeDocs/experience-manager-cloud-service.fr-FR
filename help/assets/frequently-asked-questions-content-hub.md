---
title: Questions fréquentes sur Content Hub
description: Obtenez des réponses à certaines des questions les plus fréquentes (FAQ) pour Content Hub.
exl-id: 74b5c308-c1d3-4787-9f1f-f64cf09d298a
source-git-commit: 31c9e742d8bdf69c12788794670817864c9c027a
workflow-type: tm+mt
source-wordcount: '1293'
ht-degree: 98%

---

# Questions fréquentes sur Content Hub {#content-hub-frequently-asked-questions}

![Questions fréquentes sur Content Hub](assets/content-hub-faqs.png)

## Qu’est-ce que Content Hub ? {#what-is-content-hub}

Content Hub est une fonctionnalité d’Adobe Experience Manager Assets as a Cloud Service.

Content Hub permet aux équipes plus larges de découvrir facilement des ressources pertinentes et approuvées grâce à un portail intuitif et de les adapter rapidement à leurs besoins. En outre, Content Hub fournit un mécanisme d’ingestion qui permet à ces utilisateurs et utilisatrices de se servir facilement lorsqu’ils chargent des ressources dans la gestion des ressources numériques. Cela permet de répondre directement aux besoins des entreprises en termes de vitesse de création de contenu, tout en préservant la cohérence de la marque et la conformité avec les garanties appropriées.

## Pourquoi ne puis-je pas activer Content Hub sur mon programme/environnement Cloud Manager ? {#cannot-enable-content-hub}

Content Hub n’est à ce stade disponible que sur les programmes de production AEM Cloud Manager, qui incluent une licence Assets (Assets Cloud Service, Assets Ultimate, Assets Prime). Lorsque vous cliquez sur [Content Hub](/help/assets/deploy-content-hub.md#enable-content-hub) pour l’activer, il est déployé et associé à l’environnement de production de création d’AEM dans ce programme. Voir [Déploiement de Content Hub](/help/assets/deploy-content-hub.md) pour plus d’informations et connaître les conditions préalables.

## J’ai activé Content Hub sur mon programme/environnement de production, puis-je le désactiver ? {#can-i-disable-content-hub}

L’activation de Content Hub sur un programme de production le déploie dans une partie de l’infrastructure de production. AEM Cloud Manager ne permet pas de supprimer ou de désactiver l’infrastructure de production afin de minimiser les risques d’utilisation de la production en raison d’erreurs humaines.

Si vous ne souhaitez pas fournir Content Hub à vos utilisateurs et utilisatrices une fois qu’il a été déployé, n’affectez personne au profil de produit Content Hub dans Admin Console. Voir [Déploiement de Content Hub](/help/assets/deploy-content-hub.md#content-hub-instance-product-profile) pour plus d’informations.

## Comment évaluer Content Hub dans mon entreprise, étant donné qu’il est uniquement disponible pour les programmes de production/environnements de création de production ? {#how-can-i-evaluate-content-hub}

Content Hub est une fonctionnalité qu’Adobe fournit et gère et qui ne comporte pas de code personnalisé qui nécessiterait une validation typique via les environnements de développement, d’évaluation ou de production. En outre, l’accès à la fonctionnalité pour les utilisateurs et utilisatrices est entièrement contrôlé par l’administrateur ou l’administratrice, de sorte que vous pouvez l’évaluer sans l’exposer à tous les utilisateurs et utilisatrices.

Il est possible d’évaluer Content Hub sans affecter le contenu des utilisateurs et utilisatrices/de la production géré dans AEM as a Cloud Service Assets. Une procédure d’évaluation peut se présenter comme suit :

* [Activez Content Hub](/help/assets/deploy-content-hub.md#enable-content-hub) dans l’environnement de production (programme Cloud Manager).
* [Ajoutez un utilisateur administrateur ou une utilisatrice administratrice AEM](/help/assets/deploy-content-hub.md#onboard-content-hub-administrator) de l’instance de création de production au profil de produit Content Hub.
* L’administrateur ou l’administratrice AEM [ configure Content Hub](/help/assets/configure-content-hub-ui-options.md).
* L’administrateur ou l’administratrice AEM ou une personne utilisant AEM sur l’instance de création de production AEM [approuve un certain nombre de ressources pour Content Hub](/help/assets/approve-assets-content-hub.md) ; si vous ne souhaitez pas modifier le contenu de production dans la gestion des ressources numériques, vous pouvez créer un dossier d’évaluation distinct dans l’instance de création AEM, puis charger/baliser ou copier certaines ressources de la gestion des ressources numériques dans cette instance.
* L’administrateur ou l’administratrice Admin Console ajoute [quelques utilisateurs et utilisatrices sélectionnés](/help/assets/deploy-content-hub.md#onboard-content-hub-users) au profil de produit Content Hub, afin qu’ils puissent commencer l’évaluation.
* Une fois l’évaluation terminée, les utilisateurs et utilisatrices AEM de l’instance de création peuvent supprimer l’approbation des ressources de test et approuver les ressources de production pour Content Hub, puis l’administrateur ou l’administratrice Admin Console peut ajouter tous les utilisateurs et utilisatrices qui ont besoin d’accéder à Content Hub et au contenu approuvé. Félicitations, Content Hub est maintenant actif.

Il existe un programme d’accès anticipé à Content Hub sur les programmes Sandbox et leurs environnements de production de création. Pour en savoir plus, voir [Présentation des programmes Sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md). Pour en savoir plus sur le programme d’accès anticipé, contactez votre équipe Adobe en charge des comptes.

Content Hub n’est pas encore disponible pour les environnements hors production (évaluation et développement). La disponibilité attendue des environnements d’évaluation/de développement pour Assets Ultimate est mars 2025.

## Pourquoi les ressources ne s’affichent-elles pas une fois que ma connexion à Content Hub est effective ? {#no-assets-in-content-hub}

Les ressources marquées comme approuvées dans Assets as a Cloud Service sont automatiquement disponibles dans Content Hub. Si vous ne voyez aucune ressource après votre connexion à Content Hub, approuvez les ressources à l’aide de l’environnement de création AEM as a Cloud Service pour les rendre disponibles dans Content Hub. Pour plus d’informations, voir [Approbation de ressources pour Content Hub](/help/assets/approve-assets-content-hub.md).

## Pourquoi mes ressources que je charge directement à l’aide de Content Hub ne s’affichent-elles pas ou ne sont-elles pas importées à partir de comptes Dropbox ou OneDrive à l’aide de Content Hub ? {#no-assets-uploaded-from-content-hub}

L’affichage des ressources chargées à l’aide de Content Hub dépend de l’activation ou non du bouton [Approbation automatique](/help/assets/configure-content-hub-ui-options.md#configure-import-options-content-hub) disponible dans l’interface d’utilisation de configuration :

* Si le bouton **Approbation automatique** est activé, les ressources que vous chargez à l’aide de Content Hub sont automatiquement disponibles.

* Si le bouton **Approbation automatique** est désactivé, les ressources que vous chargez à l’aide de Content Hub ne s’affichent pas automatiquement. Les ressources sont disponibles dans le dossier `hydrated-assets` de votre environnement Assets as a Cloud Service. Accédez au dossier et [modifiez en masse](/help/assets/approve-assets-content-hub.md) le statut de ces ressources sur `Approved` pour que ces ressources s’affichent dans Content Hub.

## Comment rechercher rapidement des ressources chargées à l’aide de Content Hub dans l’environnement AEM as a Cloud Service ? {#find-uploaded-assets-on-aem-cloud}

Vous pouvez rapidement trouver les ressources chargées à l’aide de Content Hub dans l’environnement AEM as a Cloud Service en procédant comme suit :

1. Accédez au dossier `hydrated-assets`.

1. Cliquez sur **[!UICONTROL Filtres]** et définissez **[!UICONTROL Pas de statut]** dans le champ **[!UICONTROL Statut de la ressource]**.

1. Triez les ressources à l’aide du champ **[!UICONTROL Date de modification]**.

## Pourquoi l’option Modifier à l’aide d’Adobe Express ne s’affiche pas sur ma carte de la ressource pour pouvoir remixer des ressources afin de créer de nouvelles variations ? {#edit-using-express-not-available}

Pour afficher l’option **Modifier à l’aide d’Adobe Express** sur la carte de la ressource, vous devez disposer de droits Adobe Express Enterprise ou Équipe (voir [formules](https://www.adobe.com/fr/express/pricing)) en plus des privilèges pour les [utilisateurs et utilisatrices Content Hub ayant les droits de remixer des ressources en nouvelles variations](#onboard-content-hub-users-add-assets).

Il existe quelques configurations de la manière dont les utilisateurs et utilisatrices sont affectés à [!DNL Content Hub] et à [!DNL Adobe Express] :

1. L’organisation dispose d’une licence [Assets Ultimate](/help/assets/assets-ultimate-overview.md) ou [Assets Prime](/help/assets/assets-prime.md) et la personne est affectée à l’un des profils Experience Manager dans Admin Console qui incluent les droits Adobe Express (utilisateur collaborateur ou utilisatrice collaboratrice, ou utilisateur expert ou utilisatrice experte). L’intégration fonctionne sans configuration supplémentaire.

1. [!DNL Adobe Express] est déployé dans la même [!DNL Adobe Admin Console] qu’[!DNL Experience Manager Assets] avec [!DNL Content Hub]. L’intégration fonctionne sans configuration supplémentaire.

1. [!DNL Adobe Express] est déployé dans une [!DNL Adobe Admin Console] différente d’[!DNL Experience Manager Assets] avec [!DNL Content Hub]. Dans ce cas, l’administrateur ou l’administratrice [!DNL Assets] peut configurer l’intégration (voir [documentation](/help/assets/connect-assets-with-creative-cloud.md)) pour qu’elle fonctionne.

   >[!NOTE]
   >
   >La personne affectée aux profils de produits Express et Assets dans deux Admin Consoles doit avoir la même adresse e-mail et utiliser un compte professionnel **d’entreprise ou d’établissement scolaire**, et non **personnel**. La configuration idéale consiste à configurer les deux Admin Consoles en tant que **Federated ID** avec une relation de confiance entre elles, de sorte que l’utilisateur ou l’utilisatrice bénéficie d’une expérience d’authentification unique fluide. Certaines formules Express (par exemple, Express Équipe) ne prennent pas en charge Federated ID/l’authentification unique.

Outre les droits appropriés sur les produits, l’intégration d’Adobe Express à Content Hub nécessite que la personne affectée dispose au moins des autorisations [!UICONTROL Peut modifier] sur l’environnement de création Assets qui alimente Content Hub, au moins sur la hiérarchie de dossiers **[#UICONTROL /content/dam/hydrated-assets/]**, où les utilisateurs et utilisatrices Content Hub peuvent enregistrer le contenu créé à l’aide d’Express. Consultez [Gestion des autorisations](/help/security/touch-ui-principal-view.md) dans la vue Administration (interface d’utilisation tactile) ou [Gestion des autorisations dans la vue simplifiée Assets](https://experienceleague.adobe.com/fr/docs/experience-manager-assets-essentials/help/get-started-admins/folder-access/manage-permissions).

## Puis-je configurer Content Hub de sorte que les directives de marque de mon entreprise s’affichent sous la forme d’un lien sur la page d’accueil ? {#content-hub-setup-brand-guidelines}

Vous pouvez ajouter des liens personnalisés sous forme d’onglets distincts en plus des onglets standard Toutes les ressources, Collections et Informations sur la page d’accueil de Content Hub. Pour plus d’informations sur la configuration, voir [Liens personnalisés](/help/assets/configure-content-hub-ui-options.md#configure-custom-links-content-hub).

## Existe-t-il un plan pour migrer les clients et clientes Brand Portal existants vers Content Hub ? {#migration-brand-portal}

Adobe fournit une assistance pour la migration de Brand Portal vers Content Hub que vous pouvez utiliser en créant un ticket d’assistance Adobe.

## Pourquoi l’option Paramètres/configuration du produit ne s’affiche pas dans Content Hub ? {#ui-configuration-option-missing}

Pour accéder à l’[interface utilisateur de configuration](/help/assets/configure-content-hub-ui-options.md), vous devez être [administrateur ou administratrice Content Hub](/help/assets/deploy-content-hub.md##onboard-content-hub-administrator). Si vous possédez un profil de produit Administration AEM sur l’instance de création de production dans Adobe Admin Console, mais que vous ne pouvez toujours pas voir l’option de configuration, vérifiez que le profil de produit Administration AEM n’ait pas été renommé. Pour plus d’informations, voir [Équipe et profils de produit AEM as a Cloud Service](/help/onboarding/aem-cs-team-product-profiles.md).
