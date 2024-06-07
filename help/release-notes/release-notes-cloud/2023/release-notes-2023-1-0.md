---
title: Notes de mise à jour de la version 2023.1.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2023.1.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: f134fdbc-224b-404c-b20f-44cae8bad681
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: ht
source-wordcount: '975'
ht-degree: 100%

---

# Notes de mise à jour 2023.1.0 pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour techniques de la version 2023.1.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2021, 2022 et ainsi de suite.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version 2023.1.0 d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le 9 février 2023. La prochaine disponibilité des fonctionnalités (2023.2.0) est prévue pour le 12 avril 2023.

## Vidéo de mise à jour {#release-video}

Consultez la vidéo Aperçu de la version de janvier 2023 pour un résumé des fonctionnalités ajoutées dans la version 2023.1.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3413479/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités de la préversion de [!DNL Sites] {#prerelease-features-sites}

* L’API de diffusion de contenu AEM GraphQL prend désormais en charge la [pagination](/help/headless/graphql-api/content-fragments.md#paging) et le [tri](/help/headless/graphql-api/content-fragments.md#sorting) GraphQL, afin de rendre la récupération et le rendu des jeux de contenu volumineux plus efficaces. La pagination GraphQL permet d’améliorer le temps de réponse des requêtes en renvoyant les résultats dans des sous-ensembles et non tous en même temps. Le tri GraphQL permet de placer les jeux de contenu dans l’ordre souhaité, ce qui facilite le traitement du contenu par une application cliente.  Le temps de réponse des requêtes est également amélioré avec le filtrage hybride dans le moteur GraphQL AEM. Le contenu est maintenant lu à partir de JCR dans des jeux plus petits qui correspondent aux filtres de requête.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* Les rapports de ressources offrent désormais aux administrateurs et aux administratrices la possibilité de [générer des rapports de téléchargement de ressources](/help/assets/asset-reports.md) à partir du déploiement d’Experience Manager Assets as a Cloud Service. Ces données permettent en outre aux administrateurs et aux administratrices d’obtenir des informations sur les principales mesures de succès, afin de mesurer l’adoption d’Assets au sein de votre entreprise et par les clientes et clients.

  ![Rendu PDF pour d’autres formats](/help/release-notes/assets/choose_report.png)

* Experience Manager Assets [prend désormais en charge le jeton SAS](/help/assets/add-assets.md#asset-bulk-ingestor), en plus de la clé d’accès, pour l’authentification lors de la connexion à la source de données du stockage Blob Azure, à des fins d’ingestion de ressources à l’aide de l’outil d’importation en bloc.

* La gestion des images CMJN a été améliorée dans Asset Compute, ce qui permet de générer des balises et un recadrage intelligents pour les images CMJN.

### Nouvelles fonctionnalités de la préversion d’[!DNL Assets] {#prerelease-features-assets}

* Experience Manager Assets prend désormais en charge l’[ingestion à grande échelle de ressources à partir de Google Cloud Platform](/help/assets/add-assets.md#asset-bulk-ingestor) à l’aide de l’outil d’importation en bloc.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités disponibles dans [!DNL Forms] {#new-features-available-in-channel}

* **[Étapes de workflow permettant de générer des documents PDF non interactifs et une sortie imprimable](/help/forms/aem-forms-workflow-step-reference.md)** : automatisez la création de documents PDF non interactifs et de sorties imprimables pour vos processus d’entreprise avec les étapes de workflow AEM, en rationalisant votre processus de génération de documents et en gagnant du temps.
* **[Utiliser des notes de bas de page pour fournir des citations ou des informations supplémentaires dans les formulaires adaptatifs](/help/forms/footnotes-richtextsupport.md)** : utilisez les notes de bas de page dans un formulaire adaptatif pour afficher les informations sur la manière de remplir ou d’utiliser un formulaire. Vous pouvez également les utiliser pour fournir des informations entre parenthèses, des droits d’auteur et d’autres informations utiles.

### Nouvelles fonctionnalités de la préversion de [!DNL Forms] {#prerelease-features-forms}

* **[Utiliser des composants principaux de capture de données pour créer des formulaires adaptatifs](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr)** : [utilisez l’éditeur de formulaires adaptatifs](/help/forms/creating-adaptive-form-core-components.md) pour créer des formulaires basés sur des composants de capture de données normalisés (composants principaux). Ces composants offrent des fonctionnalités de personnalisation, un délai de développement réduit et de plus bas coûts de maintenance pour vos expériences d’inscription numérique.
* **[Prise en charge du pipeline front-end pour la mise en forme des formulaires adaptatifs basés sur des composants principaux](/help/forms/using-themes-in-core-components.md)** : utilisez des thèmes basés sur la méthodologie BEM facilement personnalisables pour les formulaires adaptatifs basés sur les composants principaux en les déployant avec le pipeline de déploiement front-end afin d’améliorer l’aspect de vos formulaires.
* **[Générer un document d’enregistrement pour les formulaires adaptatifs basés sur les composants principaux](/help/forms/generate-document-of-record-core-components.md)** : créez un enregistrement pour un formulaire adaptatif basé sur les composants principaux lors de son envoi pour un archivage à long terme, en version imprimée ou au format de document.

![https://www.aemcomponents.dev/](/help/forms/assets/sample-core-components-based-adaptive-form.png)

* **[Envoyer des formulaires adaptatifs à Microsoft SharePoint et Microsoft OneDrive](/help/forms/configuring-submit-actions.md)** : rationalisez l’envoi des données et envoyez directement vos données de formulaire adaptatif à Microsoft SharePoint et Microsoft OneDrive. Vous pouvez envoyer des données basées sur des schémas et des données sans schéma. Ces actions d’envoi s’ajoutent aux actions d’envoi déjà disponibles.
* **[Créer efficacement des formulaires à l’aide de la fonction Enregistrer un formulaire adaptatif en tant que modèle](/help/forms/template-editor.md#save-an-adaptive-form-as-template-saving-adaptive-form-as-template)** : rationalisez votre processus de création de formulaires en enregistrant un formulaire adaptatif en tant que modèle et en réutilisant les modèles pour votre prochain formulaire adaptatif.
* **[Connecter AEM Forms à des bases de données prises en charge par JDBC](/help/forms/configure-data-sources.md#configure-relational-database-configure-relational-database)** : connectez facilement votre modèle de données AEM Forms à des bases de données qui prennent en charge JDBC, afin de lire et écrire des données en toute simplicité.
* **[Effectuer l’intégration aux points d’entrée REST à l’aide de l’API Open 3.0](/help/forms/configure-data-sources.md#configure-restful-services-open-api-specification-version-20-configure-restful-services-swagger-version30)** : connectez les modèles de données de formulaire AEM Forms as a Cloud Service aux points d’entrée REST qui prennent en charge la spécification d’API ouverte version 3.0, afin d’envoyer et recevoir facilement des données.
* **[Partager un formulaire adaptatif pour révision](/help/forms/create-reviews-forms.md)** : utilisez le mécanisme de révision des formulaires adaptatifs pour permettre à une ou plusieurs personnes de réviser le formulaire.

## [!DNL Experience Manager as a Cloud Service] Foundation {#foundation}

### Nouveautés {#what-is-new-foundation}

* [Environnements de développement rapide](/help/implementing/developing/introduction/rapid-development-environments.md) - Les RDE permettent aux développeurs et aux développeuses de résoudre rapidement les problèmes et de déployer de nouvelles fonctionnalités sur AEM as a Cloud Service.

  Les environnements de développement rapide sont un nouveau type d’environnement cloud conçu comme une méthode rapide, cohérente et extensible de validation du code. Le travail en local fonctionne également en mode cloud. À l’aide des outils de ligne de commande, synchronisez rapidement les modules de contenu, les bundles, les fichiers de contenu, la configuration OSGI ou la configuration du Dispatcher avec le RDE. Regardez cette vidéo pour consulter un exemple concret :

  >[!VIDEO](https://video.tv.adobe.com/v/3413508/?quality=12&learn=on)

  Une fois le code validé dans le RDE, nous vous conseillons de le déployer dans un environnement de développement cloud, de sorte à utiliser les points de contrôle qualité de Cloud Manager avant d’effectuer le déploiement via un pipeline de production dans vos environnements d’évaluation et de production.

  Chaque programme comprend un RDE. Vous pouvez en acquérir d’autres sous licence.

  >[!NOTE]
  >
  >Les RDE seront progressivement déployés au cours des prochaines semaines ; vous pouvez envoyer un e-mail à aemcs-rde-support@adobe.com pour passer en tête.

* [Prise en charge étendue des jetons d’accès aux API côté serveur](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) - Vous pouvez désormais générer plusieurs informations d’identification, ce qui s’avère utile dans les cas où les API présentent des caractéristiques différentes. Il est également désormais possible de révoquer des informations d’identification en libre-service.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
