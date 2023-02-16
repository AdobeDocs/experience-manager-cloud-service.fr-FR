---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 2216d4a299c23a88659692d600b5995ff98cdde7
workflow-type: tm+mt
source-wordcount: '1032'
ht-degree: 23%

---


# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante décrit les notes de mise à jour des fonctionnalités de la version actuelle (la plus récente) de [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2021, 2022 et ainsi de suite.
>
>Consultez la section [Feuille de route des versions du Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] la version actuelle des fonctionnalités (2023.1.0) est le 9 février 2023. La prochaine version de la fonctionnalité (2023.2.0) est prévue pour le 16 mars 2023.

## Vidéo de mise à jour {#release-video}

Consultez la vidéo Aperçu de la version de décembre 2023 pour un résumé des fonctionnalités ajoutées dans la version 2023.1.0:

>[!VIDEO](https://video.tv.adobe.com/v/3413479/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités de la préversion d’[!DNL Sites] {#prerelease-features-sites}

* L’API de diffusion de contenu GraphQL AEM prend désormais en charge GraphQL. [Pagination](/help/headless/graphql-api/content-fragments.md#paging) et [Tri](/help/headless/graphql-api/content-fragments.md#sorting), afin de rendre la récupération et le rendu des jeux de contenu volumineux plus efficaces. La pagination GraphQL permet d’améliorer le temps de réponse des requêtes en renvoyant les résultats dans des sous-ensembles, par opposition à tous en même temps. Le tri GraphQL permet de placer les jeux de contenu dans l’ordre souhaité, ce qui facilite le traitement du contenu par une application cliente.  Le temps de réponse des requêtes est également amélioré avec le filtrage hybride dans le moteur GraphQL AEM. Le contenu est maintenant lu à partir de JCR dans des jeux plus petits qui correspondent aux filtres de requête.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* Les rapports de ressources offrent désormais aux administrateurs la possibilité de [générer des rapports de téléchargement de ressources ;](/help/assets/asset-reports.md) à partir du déploiement Experience Manager Assets as a Cloud Service. Ces données permettent en outre aux administrateurs d’obtenir des informations sur les principales mesures de succès afin de mesurer l’adoption d’Assets au sein de votre entreprise et par les clients.

   ![Rendu PDF pour d’autres formats](/help/release-notes/assets/choose_report.png)

* Experience Manager Assets [prend désormais en charge le jeton SAS](/help/assets/add-assets.md#asset-bulk-ingestor), en plus de la clé d’accès, pour l’authentification lors de la connexion à la source de données Azure Blob Storage, à des fins d’ingestion de ressources à l’aide de l’outil d’importation en bloc.

* Amélioration de la gestion des images CMJN dans Asset compute, ce qui vous permet de générer un recadrage intelligent et des balises intelligentes pour les images CMJN.

### Nouvelles fonctionnalités de la préversion d’[!DNL Assets] {#prerelease-features-assets}

* Experience Manager Assets prend désormais en charge [ingestion à grande échelle de ressources à partir de Google Cloud Platform](/help/assets/add-assets.md#asset-bulk-ingestor) à l’aide de l’outil d’importation en bloc.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités disponibles dans [!DNL Forms] {#new-features-available-in-channel}

* **[Étapes de workflow pour générer des documents de PDF non interactifs et une sortie imprimable](/help/forms/aem-forms-workflow-step-reference.md)**: Automatisez la création de documents de PDF non interactifs et de sorties imprimables pour vos processus d’entreprise avec les étapes de processus AEM, en rationalisant votre processus de génération de documents et en gagnant du temps.
* **[Utilisation des notes de bas de page pour fournir des citations ou des informations supplémentaires dans Forms adaptatif](/help/forms/footnotes-richtextsupport.md)**: Utilisez les notes de bas de page dans un formulaire adaptatif pour afficher les informations sur la manière de remplir ou d’utiliser un formulaire. Vous pouvez également l’utiliser pour fournir des informations entre parenthèses, des droits d’auteur et d’autres informations utiles.

### Nouvelles fonctionnalités de la préversion d’[!DNL Forms] {#prerelease-features-forms}

* **[Utilisation des composants principaux de capture de données pour créer le Forms adaptatif](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=en)**: [Utilisation de l’éditeur de Forms adaptatif](/help/forms/creating-adaptive-form-core-components.md) pour créer des formulaires basés sur des composants de capture de données normalisés (composants principaux). Ces composants fournissent des fonctionnalités de personnalisation, un temps de développement réduit et des coûts de maintenance réduits pour vos expériences d’inscription numérique.
* **[Prise en charge du pipeline Frontend pour le style d’un Forms adaptatif basé sur des composants principaux](/help/forms/using-themes-in-core-components.md)**: Utilisez des thèmes basés sur BEM facilement personnalisables pour les Forms adaptatives basées sur les composants principaux en les déployant avec le pipeline de déploiement Frontend afin d’améliorer l’aspect de vos formulaires.
* **[Générer un document d’enregistrement pour le Forms adaptatif basé sur les composants principaux](/help/forms/generate-document-of-record-core-components.md)**: Créez un enregistrement pour le formulaire adaptatif basé sur les composants principaux lors de l’envoi pour un archivage à long terme, en version imprimée ou au format de document.

![https://www.aemcomponents.dev/](/help/forms/assets/sample-core-components-based-adaptive-form.png)

* **[Envoyer le Forms adaptatif à Microsoft SharePoint et Microsoft OneDrive](/help/forms/configuring-submit-actions.md)**: Rationalisation de l’envoi des données avec possibilité d’envoyer directement des données de formulaire adaptatif à Microsoft SharePoint et Microsoft OneDrive. Vous pouvez envoyer des données basées sur des schémas et des données sans schéma. Ces actions d’envoi s’ajoutent aux actions d’envoi déjà disponibles.
* **[Création de formulaires efficace à l’aide de la fonction Enregistrer un formulaire adaptatif en tant que modèle](/help/forms/template-editor.md#save-an-adaptive-form-as-template-saving-adaptive-form-as-template)**: Rationalisez votre processus de création de formulaires en enregistrant un formulaire adaptatif en tant que modèle et en réutilisant les modèles pour votre prochain formulaire adaptatif.
* **[Connexion d’AEM Forms à des bases de données prises en charge par JDBC](/help/forms/configure-data-sources.md#configure-relational-database-configure-relational-database)**: Connectez facilement votre modèle de données AEM Forms à des bases de données qui prennent en charge JDBC, ce qui vous permet de lire et d’écrire des données en toute simplicité.
* **[Intégration aux points de fin REST à l’aide de l’API Open 3.0](/help/forms/configure-data-sources.md#configure-restful-services-open-api-specification-version-20-configure-restful-services-swagger-version30)**: Connectez les modèles de données de formulaire as a Cloud Service AEM Forms aux points de terminaison REST qui prennent en charge la spécification d’API ouverte version 3.0, ce qui vous permet d’envoyer et de recevoir facilement des données.
* **[Partager un formulaire adaptatif pour révision](/help/forms/create-reviews-forms.md)**: Utilisez le mécanisme de révision de Forms adaptatif pour permettre à un ou plusieurs réviseurs de réviser le formulaire.


## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Les auteurs peuvent enrichir dynamiquement des listes de produits avec des fragments d’expérience (par exemple : placement d’une bannière entre des listes de produits).
* Le composant Liste prend désormais en charge les pages de produits/catégories associées afin de les afficher de manière dynamique.
* Ajout de la prise en charge des composants Peregrine 12.5.
* Ajout de la prise en charge du chargement des prix côté client dans le teaser du produit et le carrousel.

## [!DNL Experience Manager as a Cloud Service] Foundation {#foundation}

### Nouveautés {#what-is-new-foundation}

* [Environnements de développement rapide](/help/implementing/developing/introduction/rapid-development-environments.md) - Les RDE permettent aux développeurs de résoudre rapidement les problèmes et de déployer de nouvelles fonctionnalités sur AEM as a Cloud Service.

   Les environnements de développement rapide sont un nouveau type d’environnement cloud conçu comme une méthode rapide, cohérente et extensible de validation du code qui fonctionne localement fonctionne également comme prévu dans le cloud. À l’aide des outils de ligne de commande, synchronisez rapidement les modules de contenu, les lots, les fichiers de contenu, la configuration OSGI ou la configuration du Dispatcher avec l’éditeur de texte enrichi. Voir ceci en action dans la vidéo ci-dessous :

   >[!VIDEO](https://video.tv.adobe.com/v/3413508/?quality=12&learn=on)

   Une fois le code validé dans l’éditeur de texte enrichi, il est conseillé de le déployer dans un environnement de développement cloud pour utiliser les points de contrôle qualité de Cloud Manager avant de le déployer via un pipeline de production dans les environnements intermédiaire et de production.

   Chaque programme comprend un RDE et, éventuellement, d’autres peuvent être sous licence.

   >[!NOTE]
   >
   >Les RDE seront progressivement déployés au cours des prochaines semaines; vous pouvez envoyer un courrier électronique à aemcs-rde-support@adobe.com pour passer au premier plan.

* [Prise en charge étendue des jetons d’accès aux API côté serveur](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) - Vous pouvez désormais générer plusieurs informations d’identification, ce qui s’avère utile dans les cas où les API présentent des caractéristiques différentes. Il est également désormais possible de révoquer des informations d’identification en libre-service.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [here](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
