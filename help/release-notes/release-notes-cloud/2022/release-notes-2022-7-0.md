---
title: Notes de mise à jour de la version 2022.7.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2022.7.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: b339ab48-e836-4589-a573-9c50917b9280
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 30%

---

# Notes de mise à jour d’202278.0 pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section ci-dessous présente les notes de mise à jour des fonctionnalités de la version 2022.7.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle (2022.7.0) de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le mardi 8 août 2022.

La prochaine version (2022.8.0) est prévue pour le 1er septembre 2022.

## Vidéo de mise à jour {#release-video}

Consultez la vidéo Vue d’ensemble de la version de juillet 2022 pour obtenir un résumé des fonctionnalités ajoutées dans la version 2022.7.0 :

>[!VIDEO](https://video.tv.adobe.com/v/345409/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités de [!DNL Sites] {#sites-features}

* La [&#x200B; Console de fragments de contenu &#x200B;](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console) prend désormais en charge [raccourcis clavier](/help/sites-cloud/administering/content-fragments/keyboard-shortcuts.md).

* AEM as a Cloud Service [diffusion d’images optimisée pour le web](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/web-optimized-image-delivery.html?lang=fr) permet d’améliorer considérablement la vitesse de page en fournissant des formats tels que WebP. Ce nouveau service offre également des options de redimensionnement et de transformation d’image plus flexibles. Toutes les versions du [composant d’image principal](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/image.html?lang=fr) vous permettent d’utiliser ce service et de diffuser des images au format WebP en cliquant sur une option de la politique du composant d’image.

* Les activités de personnalisation AEM peuvent désormais utiliser des fragments d’expérience au lieu de nos offres héritées. Cette fonctionnalité :
   * permet d’activer un chemin de migration dans lequel le contenu AEM promouvrait les offres de fragments d’expérience plutôt que les offres héritées de la bibliothèque afin de fournir un contenu de style approprié qui correspond à la personnalisation à grande échelle à l’avenir.
   * empêche les auteurs de contenu de diffuser accidentellement du contenu non stylisé sur leur site.
   * permet de convertir le mode de ciblage de n’importe quel composant en un fragment d’expérience (de types JSON et HTML) qui utilise des modèles modifiables.

>[!NOTE]
>
>Les activités de personnalisation existantes qui utilisent déjà des offres héritées peuvent continuer à le faire, mais les nouvelles activités de personnalisation doivent être créées en tant que fragments d’expérience, car il s’agit de l’approche recommandée pour l’avenir.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Assets] {#prerelease-features-assets}

Vous pouvez désormais configurer Adobe Experience Manager Assets pour [&#x200B; restreindre le type de ressources que les utilisateurs peuvent charger en fonction du type MIME &#x200B;](/help/assets/configure-asset-upload-restrictions.md).

![Restrictions de téléchargement des ressources](/help/assets/assets/asset-upload-restrictions.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités de [!DNL Forms] {#forms-features}

* **[Prise en charge des entrées au clavier pour les signatures tactiles](/help/forms/signing-forms-using-scribble.md)** : les Forms adaptatives sont de plus en plus utilisées sur les appareils tactiles et une exigence courante est de prendre en charge les signatures. La signature de documents sur les appareils tactiles est devenue une méthode acceptée de signature de formulaires. Le Forms adaptatif prend en charge nativement les signatures Scribble et Adobe Sign pour de tels cas d’utilisation. Désormais, avec d’autres options déjà prises en charge, vous pouvez également utiliser le clavier pour apposer des signatures Scribble dans un formulaire adaptatif. Cela permet également d’améliorer la conformité en matière d’accessibilité.

![Prise en charge des entrées au clavier pour les signatures tactiles sur iphone](/help/release-notes/assets/scribble-keyboard-mobile.png)

* **Utiliser l&#39;assistant de Forms adaptative en langue locale** : vous pouvez utiliser l&#39;assistant dans la langue de votre choix. Il prend désormais en charge toutes les langues prises en charge par Adobe Experience Manager.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Forms] {#prerelease-features-forms}

<!-- 

* **[Launch Adaptive Form creation wizard from embed form component](/help/forms/using/embed-adaptive-form-aem-sites.md)**: You can now launch Adaptive Form creation wizard from embed form component. It helps improve content and forms authoring workflows for Sites and Forms practitioners trying to add enrollment experiences to a web page. 

![Keyboard input support for Scribble signatures on iphone](/help/release-notes/assets/froms-container.png) 

-->

* **[Appeler DDX - une étape de workflow AEM](/help/forms/aem-forms-workflow-step-reference.md#invokeddx)** : DDX (Document Description XML) est un langage de balisage déclaratif dont les éléments représentent des blocs de création de documents. Ces blocs de création comportent des documents PDF et XDP, ainsi que d’autres éléments tels que des commentaires, des signets et du texte avec style. Les documents DDX sont des modèles pour les documents et décrivent les caractéristiques souhaitées des documents sources qui doivent apparaître dans les documents créés. Un DDX unique peut être utilisé avec un éventail de documents source. Vous pouvez utiliser l’étape Appeler un workflow AEM pour effectuer diverses opérations, comme assembler des documents, créer et modifier Acrobat et XFA Forms, ainsi que d’autres opérations décrites dans la documentation [Référence DDX](https://helpx.adobe.com/content/dam/help/en/experience-manager/forms-cloud-service/ddxRef.pdf).

* **[Convertir en PDF/A - Étape de workflow AEM](/help/forms/aem-forms-workflow-step-reference.md##convert-pdfa)** : PDF/A est un format d’archivage pour la conservation à long terme du contenu du document, toutes les polices sont incorporées et le fichier est décompressé. Vous pouvez désormais utiliser l’étape Convertir en PDF/A d’un workflow AEM pour convertir vos documents ou fichiers dans n’importe quel format au format PDF/A.


## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* L’enrichissement du catalogue de produits prend désormais en charge les pages AEM. Cela permet aux auteurs et autrices de gérer l’association page-produit.

* Diverses améliorations du composant principal CIF

### Correctifs {#bug-fixes-cif}

* Ajouter un jeton de connexion à la récupération des prix côté client

* Composant de page incorrect dans la couche de données

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Nouveautés {#what-is-new-foundation}

* Le [navigateur de référentiels](/help/implementing/developing/tools/repository-browser.md) dispose désormais d’un champ d’entrée de chemin d’accès, ce qui permet de passer directement à un dossier spécifique dans la hiérarchie du référentiel
* Sling Content Distribution (SCD) prend désormais en charge une action d’« invalidation » explicite, ce qui permet d’invalider le contenu sans qu’il ne soit publié. Consultez la page [&#x200B; Mise en cache dans AEM as a Cloud Service &#x200B;](/help/implementing/dispatcher/caching.md#explicit-invalidation) pour plus d’informations.
* mod_macro est désormais disponible dans AEM as a Cloud Service. Voir [ce tableau](/help/implementing/dispatcher/disp-overview.md) pour obtenir la liste des modules Apache pris en charge.

### Améliorations des outils AEM as a Cloud Service SDK Dispatcher {#dispatcher-tools-enhancements}

* Vous pouvez démarrer Apache avec `docker_run_hot_reload.sh` script qui charge et valide automatiquement toutes les modifications ultérieures apportées à la configuration Apache et Dispatcher, améliorant ainsi la vitesse du développeur. Uniquement pris en charge pour les outils du Dispatcher en mode flexible. Pour plus d’informations sur le rechargement et la validation automatiques[&#128279;](/help/implementing/dispatcher/validation-debug.md#automatic-reloading) consultez la section  Déboguer la configuration d’Apache et de Dispatcher .
* La configuration locale d’Apache/du Dispatcher suit plus étroitement les modifications dans les environnements cloud, ce qui augmente la parité entre les deux environnements.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Experience Manager] {#prerelease-features-foundation}

* AEM as a Cloud Service est désormais intégré à Unified Shell pour améliorer l’expérience utilisateur et l’unifier avec toutes les autres applications Experience Cloud. Voir [AEM as a Cloud Service sur Unified Shell](/help/overview/aem-cloud-service-on-unified-shell.md) pour plus d’informations.

## Connecteurs Adobe Learning Manager {#learn-manage}

* Le nouveau Adobe Learning Manager dispose de connecteurs vers Adobe Experience Manager Sites, Marketo Engage et Adobe Commerce. Pour en savoir plus, consultez : [Guide de l’utilisateur de &#x200B;](https://helpx.adobe.com/fr/learning-manager/user-guide.html).

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
