---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 05c34d45e27a8ef22c1ebca72d362529669339fa
workflow-type: tm+mt
source-wordcount: '1713'
ht-degree: 43%

---

# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour techniques de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2023 ou 2024.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Pour recevoir chaque mois une notification par e-mail concernant des informations sur les notes de mise à jour d’Experience Cloud, abonnez-vous aux [Mises à jour de produits prioritaires d’Adobe](https://www.adobe.com/subscription/priority-product-update.html).

## Date de publication {#release-date}

La date de publication de la version actuelle (2025.4.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le vendredi 24 avril 2025. La prochaine mise à jour des fonctionnalités (2025.5.0) est prévue pour le vendredi 5 juin 2025.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the February 2025 Release Overview video for a summary of the features added in the 2025.2.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités de Experience Manager Sites {#enhancements-sites}

**Nouvelle interface utilisateur d’administration de modèle de fragment de contenu**

Pour compléter la liste des nouvelles interfaces utilisateur côté client lors de l’utilisation de fragments de contenu AEM, une nouvelle interface d’administration est désormais disponible pour les modèles de fragment de contenu. La nouvelle interface utilisateur fournit une vue de liste épurée et moderne qui permet de rechercher des modèles avec des filtres et qui affiche les balises de modèle et les fragments de contenu existants basés sur un certain modèle. La documentation se trouve [ici](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md).

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Dynamic Media (Scene7) {#dynamic-media-scene7}

**Dynamic Media (Scene7) non pris en charge dans les environnements de sécurité renforcée**

Dynamic Media (Scene7) sur AEM as a Cloud Service n’est pas compatible avec la norme HIPAA et ne peut pas être utilisé dans les environnements AEM où la sécurité renforcée est activée.

À compter de la version d’avril 2025 d’AEM as a Cloud Service, une restriction technique empêche Dynamic Media (Scene7) d’être configuré dans les environnements dotés d’une sécurité renforcée. Par conséquent, la vignette **Configuration Dynamic Media** sous **Outils** > **Services cloud** n’est plus visible dans ces environnements.

En outre, les clients qui utilisent AEM 6.5 doivent savoir que la pile Dynamic Media (Scene7) n’est pas conforme à la norme HIPAA.

### Dynamic Media Classic {#dynamic-media-classic}

**Création de rapports**

L’onglet Bande passante du tableau de bord de création de rapports Dynamic Media Classic n’est plus pris en charge depuis avril 2025.

Consultez [Bande passante et stockage, types de rapports](https://experienceleague.adobe.com/fr/docs/dynamic-media-classic/using/setup/administration-setup#types-of-reports).


## Nouvelles fonctionnalités de la vue Assets {#new-features-assets-view}

**Relations des ressources**

La vue Assets prend désormais en charge l’affichage et la modification des relations de ressources dans un panneau simplifié de détails des ressources. Ajoutez facilement des relations telles que Source et Dérivé au contenu afin que les utilisateurs puissent trouver plus efficacement du contenu clé pertinent.

![Exemple de relation Assets](/help/assets/assets/asset-relations-example.png)

**Comparer les versions d’une ressource**

Vous pouvez désormais sélectionner et comparer rapidement n’importe quelle version d’une ressource à sa dernière version à l’aide de la vue Assets.

![comparaison de versions de ressources](/help/assets/assets/version-compare2.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Fonctionnalités de version préliminaire

* [Éditeur universel - Fragments de formulaire](/help/edge/docs/forms/universal-editor/creating-form-fragments.md) : l’éditeur universel vous permet désormais de créer et de réutiliser des fragments de formulaire pour le Forms adaptatif. Ces fragments sont des sections de formulaire réutilisables (par exemple, coordonnées, champs de consentement) qui peuvent être créées une seule fois et appliquées à plusieurs formulaires. Cette fonctionnalité simplifie la création de formulaires, assure la cohérence et améliore l’efficacité de création.

* [Bibliothèque de documents SharePoint - Enregistrez les pièces jointes avec les noms de fichier d&#39;origine](/help/forms/connect-forms-to-sharepoint-document-library.md#connect-an-adaptive-form-to-microsoft-sharepoint-document-library) : vous avez désormais la possibilité d&#39;enregistrer les pièces jointes de formulaire en utilisant leurs noms de fichier d&#39;origine lors de leur stockage dans une bibliothèque de documents SharePoint. Cette amélioration simplifie l’identification et la gestion des fichiers chargés.

* **Éditeur de règles** :
   * [Condition binaire avec événement de clic dans la clause « When »](/help/forms/rule-editor-core-components-events-operators.md#available-operator-types-and-events-in-rule-editor) : l’éditeur de règles permet désormais de combiner un événement de clic de bouton (_Est cliqué_) avec d’autres conditions dans la clause « When ». Cela permet un contrôle plus précis de l’exécution des règles en fonction de l’interaction utilisateur et d’autres facteurs. Remarque : lorsque vous utilisez plusieurs conditions, l’événement de clic doit être la première condition répertoriée.
   * [Conditions de validation des champs et des panneaux](/help/forms/rule-editor-core-components-usecases.md) : l’éditeur de règles inclut désormais les conditions _IsValid_ et _IsNotValid_. Ils vous permettent de vérifier l’état de validation de champs spécifiques ou de panneaux entiers (y compris des dispositions telles que les onglets horizontaux, verticaux, accordéons et assistants), ce qui améliore la navigation dans les formulaires et l’expérience utilisateur en fonction des résultats de validation.
* **Amélioration de la gestion de l’étendue pour les listes SharePoint** : les sites SharePoint prennent désormais en charge tous les chemins gérés, par exemple /sites et /team. Cette amélioration permet une intégration plus large entre différentes structures de site SharePoint, offrant ainsi une plus grande flexibilité pour se connecter au contenu organisationnel.
* **Prise en charge de l’enregistrement du document d’enregistrement dans la liste SharePoint** : Forms créé à l’aide d’un modèle de données de formulaire (FDM) basé sur une liste SharePoint peut désormais enregistrer le document d’enregistrement (DoR) dans les listes SharePoint en configurant la propriété de champ Référence de liaison de document d’enregistrement . Cette amélioration permet une intégration transparente des données de formulaire et des documents pris en charge avec le stockage SharePoint.

### Fonctionnalités d’accès anticipé dans AEM Forms {#forms-new-early-access-features}

Le programme d’accès anticipé d’AEM Forms vous offre une opportunité unique d’accéder de manière exclusive à des innovations de pointe et de contribuer à façonner leur développement.

Les notes de mise à jour répertorient les innovations apportées à la version actuelle. Pour obtenir la liste complète des innovations disponibles dans le cadre du programme d’accès anticipé, voir [Documentation du programme d’accès anticipé d’AEM Forms](/help/forms/early-access-ea-features.md).

#### Intégration de Adobe Experience Platform (AEP) à Forms

Les fonctionnalités d’intégration entre Forms et AEP sont désormais disponibles pour les utilisateurs et utilisatrices précoces.

## Module complémentaire CIF {#cloud-services-cif}

### Améliorations {#enhancements-cif}

* Ajout de la sélection de variantes de produits pour le type de données de référence de produit CIF
* [Expérimental] : JSON+LD dans les composants principaux CIF dans les PDP
* [Expérimental] : capacité de CIF à effacer le cache

### Correctifs {#bug-fixes-cif}

* Correction d’un problème de recherche dans le champ de produit
* Le format d’URL du produit ne fonctionne pas comme prévu pour #variant_sku
* Impossible d’ajouter plus de 20 SKU au composant Liste de produits

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### API OpenAPI {#open-apis}

Les développeurs et développeuses peuvent intégrer des fonctionnalités AEM as a Cloud Service en profondeur dans leurs propres applications et outils. Les nouvelles API AEM as a Cloud Service suivent la spécification OpenAPI dans le but d’être cohérentes, bien documentées et conviviales. Les informations d’identification des points d’entrée nécessitant une authentification sont générées en créant des projets Adobe Developer Console et en prenant en charge OAuth de serveur à serveur, l’application web et l’application monopage (SPA).

[Consultez la liste complète](https://developer.adobe.com/experience-cloud/experience-manager-apis/#openapi-based-apis) des API basées sur OpenAPI, [en savoir plus](/help/implementing/developing/open-api-based-apis.md) et essayez un [tutoriel de bout en bout](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/aem-apis/openapis/invoke-api-using-oauth-s2s) illustrant la configuration et l’utilisation.

Regardez cette vidéo pour savoir comment configurer une API authentifiée pour une utilisation ultérieure :

>[!VIDEO](https://video.tv.adobe.com/v/3457510?quality=12&learn=on)

### Améliorations liées à la configuration du réseau CDN {#cdn-enhancements}

Le réseau CDN géré par Adobe offre des options de configuration flexibles, comme décrit dans l’article [Configurer le pipeline](/help/operations/config-pipeline.md#configurations). Voici quelques fonctionnalités récentes :

#### Inclure des propriétés supplémentaires dans les journaux CDN {#props-in-cdnlogs}

Utile pour les scénarios comprenant le débogage et l’analyse des données, vous pouvez inclure plus d’informations dans vos journaux CDN au-delà des propriétés par défaut en définissant l’action `logProperty` dans [transformations des requêtes et des réponses](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations).

#### Propriétés de région, de continent et d’organisation en tant que conditions correspondantes {#matching-conditions}

Les règles du réseau CDN peuvent désormais correspondre en fonction de la région, du continent et de l’organisation pour des cas d’utilisation, y compris le blocage du trafic et les redirections. `clientRegion` et `clientContinent` augmentent le `clientCountry` déjà pris en charge pour qu’il corresponde en fonction de la géographie, tandis que `clientAsName` et `clientAsNumber` correspondent aux systèmes autonomes pour identifier les grands FAI, les entreprises ou les fournisseurs de cloud. En savoir plus sur ces [propriétés de requête nouvellement exposées](/help/security/traffic-filter-rules-including-waf.md#condition-structure).

#### Définir la valeur du cookie {#cookie-attributes}

Vous pouvez définir des attributs de cookie dans [transformations de réponse](/help/implementing/dispatcher/cdn-configuring-traffic.md#response-transformations).

### Prise en charge de Java 21 {#java21}

Depuis la version de janvier, vous pouvez créer du code avec Java 21 et Java 17. Vous avez accès à de nouvelles fonctionnalités telles que la correspondance de motifs, les classes scellées et diverses améliorations des performances. Pour connaître les étapes de configuration, notamment la mise à jour des versions de votre projet Maven et de votre bibliothèque, consultez l’article [Environnement de création](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#using-java-support).

L’**exécution** de Java 21 la plus performante est automatiquement déployée lorsqu’une version Java 17 ou 21 est détectée. Cependant, Adobe recommande également d’opter pour l’exécution de Java 21 pour les environnements créés avec Java 11, en envoyant un e-mail à [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com). Découvrez les [exigences d’exécution de Java 21](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements).

>[!IMPORTANT]
>
> L’**exécution** Java 21 a été déployée dans vos environnements de développement/RDE en février. Elle sera appliquée à vos environnements d’évaluation/de production les **28 et 29 avril**. Notez que la **création de code** avec Java 21 (ou Java 17) est indépendante de l’exécution Java 21. Vous devez engager des mesures explicites pour créer du code avec Java 21 (ou Java 17).

### Application de la politique de configuration de la journalisation d’AEM {#logconfig-policy}

Pour assurer une surveillance efficace des environnements client, les journaux Java d’AEM doivent conserver un format cohérent et ne doivent pas être remplacés par des configurations personnalisées. La sortie du journal doit rester redirigée vers les fichiers par défaut. Pour le code de produit AEM, les niveaux de journal par défaut doivent être conservés. Cependant, il est acceptable d’ajuster les niveaux de journal pour le code développé par le client.

À cette fin, aucune modification ne doit être apportée aux propriétés OSGi suivantes :
* **Configuration du journal Apache Sling** (PID : `org.apache.sling.commons.log.LogManager`) — *toutes les propriétés*
* **Configuration de l’enregistreur de journaux Apache Sling** (PID d’usine : `org.apache.sling.commons.log.LogManager.factory.config`) :
   * `org.apache.sling.commons.log.file`
   * `org.apache.sling.commons.log.pattern`

À la mi-mai, AEM appliquera une politique selon laquelle toute modification personnalisée de ces propriétés sera ignorée. Passez en revue vos processus en aval et ajustez-les en conséquence. Par exemple, si vous utilisez la fonction de transfert de journal :
* Si votre destination de journalisation s’attend à un format de journal personnalisé (autre que celui par défaut), vous devrez peut-être mettre à jour vos règles d’ingestion.
* Si les modifications apportées aux niveaux de journal réduisent la verbosité du journal, sachez que les niveaux de journal par défaut peuvent entraîner une augmentation significative du volume du journal.

### Transfert de journal AEM vers d’autres destinations - Programme Beta {#log-forwarding-earlyadopter}

Avec la version bêta, vous pouvez désormais transférer les journaux AEM vers New Relic (à l’aide de HTTPS), Amazon S3 et Sumo Logic. Notez que les journaux AEM (y compris Apache/Dispatcher) sont pris en charge, contrairement aux journaux de réseau CDN. Envoyer un e-mail à l’adresse [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com) pour obtenir l’accès.

Bien que les journaux puissent être téléchargés depuis Cloud Manager, de nombreuses organisations préfèrent diffuser ces journaux vers une destination de journalisation spécifique. AEM prend déjà en charge le transfert de journaux AEM (disponibilité générale) et de réseau CDN vers Azure Blob Storage, Datadog, HTTPS, Elasticsearch (et OpenSearch) et Splunk. Cette fonctionnalité est configurée en libre-service et déployée à l’aide du pipeline de configuration.

Pour en savoir plus, consultez la [documentation sur le transfert de journaux](/help/implementing/developing/introduction/log-forwarding.md).

### Edge Computing - Demande de commentaires {#edge-computing-feedback}

L’Edge Computing rapproche le traitement des données du navigateur, ce qui présente des avantages, notamment une latence réduite. Adobe aimerait savoir si cette technologie est utile pour la diffusion de publications AEM et les projets Edge Delivery Services. De plus, faites-nous part de l’utilisation que vous envisagez d’en faire afin de contribuer à la feuille de route du produit.

Exemples de cas d’utilisation possibles :

* Authentification avec un IdP pour accéder au contenu
* Personalization en effectuant le rendu du contenu dynamique en fonction de la géolocalisation, du type d’appareil, des attributs utilisateur, etc.
* Manipulation d’image avancée
* Middleware entre le réseau CDN et une origine
* Couche entre le navigateur et une API tierce, peut-être pour reformater la réponse de l’API
* Agrégation des données provenant de plusieurs origines afin de faciliter leur rendu par le navigateur client

Envoyez un e-mail à [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) avec vos questions et commentaires.

## [!DNL Experience Manager] Guides {#guides}

Vous trouverez une liste complète des nouvelles fonctionnalités améliorées de la dernière version d’Adobe Experience Manager Guides [ici](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).

## Éditeur universel {#universal-editor}

Vous trouverez une liste complète des versions de l’éditeur universel [ici](/help/release-notes/universal-editor/current.md).

## Générer des variations {#generate-variations}

Vous trouverez une liste complète des versions de la génération de variations [ici](/help/generative-ai/release-notes-generate-variations.md).

## Notes de mise à jour dʼExperience Cloud {#experience-cloud}

Vous trouverez des informations sur les versions d’autres applications Experience Cloud [ici](https://experienceleague.adobe.com/fr/docs/release-notes/experience-cloud/current).
