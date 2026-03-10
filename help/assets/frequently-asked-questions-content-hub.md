---
title: Questions fréquentes sur Content Hub
description: Obtenez des réponses à certaines des questions les plus fréquentes (FAQ) pour Content Hub.
badgeSaas: label="AEM Assets" type="Positive" tooltip="S’applique à AEM Assets)."
exl-id: 74b5c308-c1d3-4787-9f1f-f64cf09d298a
source-git-commit: 59f97fc6ded4274c27400f56b50b4a3329cc471a
workflow-type: tm+mt
source-wordcount: '1635'
ht-degree: 67%

---

# Questions fréquentes sur Content Hub {#content-hub-frequently-asked-questions}

![Questions fréquentes sur Content Hub](assets/content-hub-faqs.png)

## Qu’est-ce qu’AEM Assets Content Hub ? {#what-is-content-hub}

AEM Assets Content Hub est une fonctionnalité d’Adobe Experience Manager Assets as a Cloud Service.

Content Hub permet aux équipes plus larges de découvrir facilement des ressources pertinentes et approuvées grâce à un portail intuitif et de les adapter rapidement à leurs besoins. En outre, Content Hub fournit un mécanisme d’ingestion qui permet à ces utilisateurs et utilisatrices de se servir facilement lorsqu’ils chargent des ressources dans la gestion des ressources numériques. Cela permet de répondre directement aux besoins des entreprises en termes de vitesse de création de contenu, tout en préservant la cohérence de la marque et la conformité avec les garanties appropriées.

<!--

## Why cannot I enable Content Hub on my Cloud Manager program/environment? {#cannot-enable-content-hub}

Content Hub is at this point is only available on AEM Cloud Manager Production programs, which include an Assets license (Assets Cloud Service, Assets Ultimate, Assets Prime). When you click [Content Hub](/help/assets/deploy-content-hub.md#enable-content-hub) to enable it, it is deployed and associated with the author production environment of AEM in that program. See [Deploy Content Hub](/help/assets/deploy-content-hub.md) for details and prerequisites.

-->

## J’ai activé AEM Assets Content Hub dans mon programme/environnement de production, puis-je le désactiver ? {#can-i-disable-content-hub}

L’activation d’AEM Assets Content Hub sur un programme de production le déploie dans le cadre de l’infrastructure de production. AEM Cloud Manager ne permet pas de supprimer ou de désactiver l’infrastructure de production afin de minimiser les risques d’utilisation de la production en raison d’erreurs humaines.

Si vous ne souhaitez pas fournir Content Hub à vos utilisateurs et utilisatrices une fois qu’il a été déployé, n’affectez personne au profil de produit Content Hub dans Admin Console. Voir [Déploiement de Content Hub](/help/assets/deploy-content-hub.md#content-hub-instance-product-profile) pour plus d’informations.

## Comment puis-je évaluer AEM Assets Content Hub dans mon entreprise ? {#how-can-i-evaluate-content-hub}

AEM Assets Content Hub est une fonctionnalité fournie et gérée par Adobe. Elle ne comporte aucun code personnalisé qui nécessiterait une validation standard via le développement/l’évaluation/la production. En outre, l’accès à la fonctionnalité pour les utilisateurs et utilisatrices est entièrement contrôlé par l’administrateur ou l’administratrice, de sorte que vous pouvez l’évaluer sans l’exposer à tous les utilisateurs et utilisatrices.

Il est possible d’évaluer Content Hub sans affecter le contenu des utilisateurs et utilisatrices/de la production géré dans AEM as a Cloud Service Assets. Une procédure d’évaluation peut se présenter comme suit :

* [Activez Content Hub](/help/assets/deploy-content-hub.md#enable-content-hub) dans l’environnement de production (programme Cloud Manager).
* [Ajoutez un utilisateur administrateur ou une utilisatrice administratrice AEM](/help/assets/deploy-content-hub.md#onboard-content-hub-administrator) de l’instance de création de production au profil de produit Content Hub.
* L’administrateur ou l’administratrice AEM [&#x200B; configure Content Hub](/help/assets/configure-content-hub-ui-options.md).
* L’administrateur ou l’administratrice AEM ou une personne utilisant AEM sur l’instance de création de production AEM [approuve un certain nombre de ressources pour Content Hub](/help/assets/approve-assets-content-hub.md) ; si vous ne souhaitez pas modifier le contenu de production dans la gestion des ressources numériques, vous pouvez créer un dossier d’évaluation distinct dans l’instance de création AEM, puis charger/baliser ou copier certaines ressources de la gestion des ressources numériques dans cette instance.
* L’administrateur ou l’administratrice Admin Console ajoute [quelques utilisateurs et utilisatrices sélectionnés](/help/assets/deploy-content-hub.md#onboard-content-hub-users) au profil de produit Content Hub, afin qu’ils puissent commencer l’évaluation.
* Une fois l’évaluation terminée, les utilisateurs et utilisatrices AEM de l’instance de création peuvent supprimer l’approbation des ressources de test et approuver les ressources de production pour Content Hub, puis l’administrateur ou l’administratrice Admin Console peut ajouter tous les utilisateurs et utilisatrices qui ont besoin d’accéder à Content Hub et au contenu approuvé. Félicitations, Content Hub est maintenant actif.

Il existe un programme d’accès anticipé à Content Hub sur les programmes Sandbox et leurs environnements de production de création. Pour en savoir plus, voir [Présentation des programmes Sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md). Pour en savoir plus sur le programme d’accès anticipé, contactez votre équipe Adobe en charge des comptes.

## Pourquoi est-ce que je ne vois aucune ressource après la connexion à AEM Assets Content Hub ? {#no-assets-in-content-hub}

Les ressources marquées comme approuvées dans Assets as a Cloud Service sont automatiquement disponibles dans Content Hub. Si vous ne voyez aucune ressource après votre connexion à Content Hub, approuvez les ressources à l’aide de l’environnement de création AEM as a Cloud Service pour les rendre disponibles dans Content Hub. Pour plus d’informations, voir [Approbation de ressources pour Content Hub](/help/assets/approve-assets-content-hub.md).

## Pourquoi est-ce que je ne vois pas mes ressources que je charge directement à l’aide d’AEM Assets Content Hub ou que je les importe à partir de comptes Dropbox ou OneDrive à l’aide de Content Hub ? {#no-assets-uploaded-from-content-hub}

L’affichage des ressources chargées à l’aide d’AEM Assets Content Hub dépend de l’activation ou non du bouton [Validation automatique](/help/assets/configure-content-hub-ui-options.md#configure-import-options-content-hub) disponible dans l’interface utilisateur de configuration :

* Si le bouton **Approbation automatique** est activé, les ressources que vous chargez à l’aide de Content Hub sont automatiquement disponibles.

* Si le bouton **Approbation automatique** est désactivé, les ressources que vous chargez à l’aide de Content Hub ne s’affichent pas automatiquement. Les ressources sont disponibles dans le dossier `hydrated-assets` de votre environnement Assets as a Cloud Service. Accédez au dossier et [modifiez en masse](/help/assets/approve-assets-content-hub.md) le statut de ces ressources sur `Approved` pour que ces ressources s’affichent dans Content Hub.

## Comment rechercher rapidement des ressources chargées à l’aide d’AEM Assets Content Hub dans l’environnement AEM as a Cloud Service ? {#find-uploaded-assets-on-aem-cloud}

Vous pouvez rechercher rapidement des ressources chargées à l’aide d’AEM Assets Content Hub dans l’environnement AEM as a Cloud Service en :

1. Accédez au dossier `hydrated-assets`.

1. Cliquez sur **[!UICONTROL Filtres]** et définissez **[!UICONTROL Pas de statut]** dans le champ **[!UICONTROL Statut de la ressource]**.

1. Triez les ressources à l’aide du champ **[!UICONTROL Date de modification]**.

## Pourquoi l’option Modifier à l’aide d’Adobe Express ne s’affiche-t-elle pas sur ma carte de ressources pour pouvoir mixer à nouveau les ressources et créer de nouvelles variations à l’aide d’AEM Assets Content Hub ? {#edit-using-express-not-available}

Pour afficher l’option **Modifier à l’aide d’Adobe Express** sur la carte des ressources dans AEM Assets Content Hub, l’utilisateur doit disposer des droits Adobe Express Enterprise ou Teams (voir [plans](https://www.adobe.com/fr/express/pricing)) en plus des privilèges pour les utilisateurs de [Content Hub disposant de droits pour remixer les ressources dans de nouvelles variations](#onboard-content-hub-users-add-assets).

Il existe quelques configurations de la manière dont les utilisateurs et utilisatrices sont affectés à [!DNL Content Hub] et à [!DNL Adobe Express] :

1. L’organisation dispose d’une licence [Assets Ultimate](/help/assets/assets-ultimate-overview.md) ou [Assets Prime](/help/assets/assets-prime.md) et la personne est affectée à l’un des profils Experience Manager dans Admin Console qui incluent les droits Adobe Express (utilisateur collaborateur ou utilisatrice collaboratrice, ou utilisateur expert ou utilisatrice experte). L’intégration fonctionne sans configuration supplémentaire.

1. [!DNL Adobe Express] est déployé dans la même [!DNL Adobe Admin Console] qu’[!DNL Experience Manager Assets] avec [!DNL Content Hub]. L’intégration fonctionne sans configuration supplémentaire.

1. [!DNL Adobe Express] est déployé dans une [!DNL Adobe Admin Console] différente d’[!DNL Experience Manager Assets] avec [!DNL Content Hub]. Dans ce cas, l’administrateur ou l’administratrice [!DNL Assets] peut configurer l’intégration (voir [documentation](/help/assets/connect-assets-with-creative-cloud.md)) pour qu’elle fonctionne.

   >[!NOTE]
   >
   >La personne affectée aux profils de produits Express et Assets dans deux Admin Consoles doit avoir la même adresse e-mail et utiliser un compte professionnel **d’entreprise ou d’établissement scolaire**, et non **personnel**. La configuration idéale consiste à configurer les deux Admin Consoles en tant que **Federated ID** avec une relation de confiance entre elles, de sorte que l’utilisateur ou l’utilisatrice bénéficie d’une expérience d’authentification unique fluide. Certaines formules Express (par exemple, Express Équipe) ne prennent pas en charge Federated ID/l’authentification unique.

Outre les droits appropriés sur les produits, l’intégration d’Adobe Express à Content Hub nécessite que la personne affectée dispose au moins des autorisations [!UICONTROL Peut modifier] sur l’environnement de création Assets qui alimente Content Hub, au moins sur la hiérarchie de dossiers **[!UICONTROL # /content/dam/hydrated-assets/]**, où les utilisateurs et utilisatrices Content Hub peuvent enregistrer le contenu créé à l’aide d’Express. Consultez [Gestion des autorisations](/help/security/touch-ui-principal-view.md) dans la vue Administration (interface d’utilisation tactile) ou [Gestion des autorisations dans la vue simplifiée Assets](https://experienceleague.adobe.com/fr/docs/experience-manager-assets-essentials/help/get-started-admins/folder-access/manage-permissions).

## Puis-je configurer AEM Assets Content Hub afin que les directives de marque de mon entreprise s’affichent sous la forme d’un lien sur la page d’accueil ? {#content-hub-setup-brand-guidelines}

Vous pouvez ajouter des liens personnalisés sous la forme d’onglets distincts en plus des onglets standard Toutes les Assets, Collections et Insights sur la page d’accueil d’AEM Assets Content Hub. Pour plus d’informations sur la configuration, voir [Liens personnalisés](/help/assets/configure-content-hub-ui-options.md#configure-custom-links-content-hub).

## Existe-t-il un plan de migration des clients Brand Portal existants vers AEM Assets Content Hub ? {#migration-brand-portal}

Adobe fournit une assistance pour la migration de Brand Portal vers AEM Assets Content Hub que vous pouvez utiliser en créant un ticket d’assistance pour Adobe.

## Pourquoi ne puis-je pas voir l’option Paramètres du produit/Configuration dans AEM Assets Content Hub ? {#ui-configuration-option-missing}

Pour accéder à l’[interface utilisateur de configuration](/help/assets/configure-content-hub-ui-options.md) dans AEM Assets Content Hub, vous devez être [administrateur Content Hub](/help/assets/deploy-content-hub.md##onboard-content-hub-administrator). Si vous possédez un profil de produit Administration AEM sur l’instance de création de production dans Adobe Admin Console, mais que vous ne pouvez toujours pas voir l’option de configuration, vérifiez que le profil de produit Administration AEM n’ait pas été renommé. Pour plus d’informations, voir [Équipe et profils de produit AEM as a Cloud Service](/help/onboarding/aem-cs-team-product-profiles.md).

## Comment AEM Assets Content Hub résout-il les limites de Brand Portal ? {#content-hub-brand-portal-comparison}


Le tableau ci-dessous présente les principales différences entre AEM Assets Content Hub et Brand Portal :

| Aire | Fonction | Content Hub | Brand Portal |
|---|---|----|----|
| Configurer l’expérience de distribution | Configurer des métadonnées pour les filtres, les détails des ressources et la page d’ajout de ressources | ✓ | − |
|  | Configurer des liens externes à partir du portail | ✓ | − |
|  | Configurer la messagerie par bannière | ✓ | ✓ |
|  | Configurer une image de bannière pour le branding | ✓ | ✓ |
|  | Configurer les couleurs primaires et secondaires de l’UI en fonction des exigences de branding | ✓ | − |
| Partager les ressources à partir de la gestion des ressources numériques | Partager les ressources approuvées d’origine à partir de la gestion des ressources numériques | ✓ | ✓ |
|  | Les modifications approuvées pour les ressources ont été automatiquement synchronisées. | ✓ | − |
| Recherche et filtres | Filtres dynamiques (les options s’affichent de manière dynamique en fonction des ressources affichées) | ✓ | − |
|  | Rechercher dans l’historique | ✓ | − |
| Chargement de ressources | Lecteur local | ✓ | ✓ |
|  | Ajouter des métadonnées configurables lors du chargement des ressources | ✓ | − |
| Téléchargement et rendus | Télécharger la ressource d’origine | ✓ | ✓ |
|  | Partager et télécharger des rendus statiques à partir de la gestion des ressources numériques | ✓ | ✓ |
|  | Télécharger des rendus dynamiques (paramètres prédéfinis et recadrages intelligents) | ✓ | ✓ |
|  | Possibilité de restreindre l’affichage et le téléchargement des ressources expirées | ✓ | − |
| Partage de liens et collections | Partage de liens pour les utilisateurs et utilisatrices connectés | ✓ | ✓ |
|  | Collections publiques | ✓ | ✓ |
|  | Recherche dans les collections | ✓ | − |
|  | Partage de lien anonyme | ✓ | ✓ |
|  | Collections privées | ✓ | ✓ |
| Autorisations | Autorisations basées sur ACL | − | ✓ |
|  | Contrôle d’accès basé sur les attributs | ✓ | − |
| Intégration d’Express | Modifier les ressources Content Hub dans Adobe Express et enregistrer dans la gestion des ressources numériques | ✓ | − |
| Tableaux de bord et rapports | Tableau de bord des informations | ✓ | − |
| Extensibilité de l’interface d’utilisation | Points d’extension personnalisés sur la page des détails de la ressource | Disponibilité limitée | − |
| Innovations bientôt disponibles | Collections favorites par utilisateur ou utilisatrice | ✓ | − |
|  | Collections épinglées par l’administrateur ou l’administratrice | ✓ | − |
|  | Recherche sémantique | ✓ | − |
|  | Recherche localisée et affichage des métadonnées | ✓ | − |

## Comment sélectionner un référentiel pour afficher les ressources uniquement pour l’environnement sélectionné dans AEM Assets Content Hub ? {#select-repository-multiple-environments}

Lorsque vous avez configuré AEM Assets Content Hub pour la production et d’autres environnements inférieurs pour le même programme, vous pouvez sélectionner le référentiel et afficher les ressources pour l’environnement sélectionné. Procédez comme suit :

1. Cliquez sur l’icône Utilisateur dans le volet de droite.

1. Dans la section **[!UICONTROL Paramètres du produit]**, sélectionnez **[!UICONTROL Sélectionner le référentiel]**.

1. Sélectionnez le référentiel dans le menu déroulant **[!UICONTROL Référentiel]**, puis cliquez sur **[!UICONTROL OK]** pour confirmer.

   Le hub de contenus affiche désormais les ressources pour l’environnement sélectionné.

## Comment AEM Assets Content Hub peut-il afficher l’aperçu des miniatures pour le type de fichier .ZIP ? {#thumbnail-preview-zip-file}

Pour fournir un aperçu des miniatures pour des types de fichiers tels que .ZIP dans AEM Assets Content Hub, vous pouvez ajouter un rendu nommé `cq5dam.preview.jpg` ou `cq5dam.preview.png` à la racine du chemin d’accès où le fichier .ZIP est disponible dans l’environnement de création AEM as a Cloud Service.

Image ajoutée en tant que rendu :

* Peut être au format JPG, JPEG ou PNG.

* Doit être inférieure à 50 Mo.

Lorsqu’elle est disponible, le hub de contenus affiche l’image comme miniature d’aperçu pour le fichier .ZIP dans le hub de contenus.


