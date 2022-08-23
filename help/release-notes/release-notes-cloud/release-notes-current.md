---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 1c27b66bcd0536ec10a878b39b9ec76073634c06
workflow-type: tm+mt
source-wordcount: '956'
ht-degree: 19%

---


# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour générales de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2022.7.0) est le 8 août 2022.

La prochaine version (2022.8.0) est prévue pour le 1er septembre 2022.

## Vidéo de mise à jour {#release-video}

Regardez la vidéo Aperçu de la version de juillet 2022 pour un résumé des fonctionnalités ajoutées dans la version 2022.7.0 :

>[!VIDEO](https://video.tv.adobe.com/v/345409/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités de [!DNL Sites] {#sites-features}

* Le [Console de fragments de contenu](/help/sites-cloud/administering/content-fragments/content-fragments-console.md) prend désormais en charge [raccourcis clavier](/help/sites-cloud/administering/content-fragments/content-fragments-console-keyboard-shortcuts.md).

* AEM en tant que Cloud Service [diffusion d’images optimisée pour le web](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/web-optimized-image-delivery.html) permet d’améliorer considérablement la vitesse de page en fournissant des formats tels que WebP. Ce nouveau service offre également des options de redimensionnement et de transformation d’image plus flexibles. Toutes les versions de [Composant d’image principal](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/image.html?lang=fr) vous permettent d’exploiter ce service et de diffuser des images sous forme WebP en cliquant sur une option de la stratégie du composant image.

* AEM activités de personnalisation peuvent désormais exploiter des fragments d’expérience au lieu de nos offres héritées. Cette fonctionnalité :
   * active un chemin de migration dans lequel AEM contenu promouvrait des offres de fragments d’expérience plutôt que des offres de bibliothèque héritées afin de fournir un contenu stylisé de manière appropriée et conforme à la personnalisation à grande échelle.
   * empêche les auteurs de contenu de diffuser accidentellement du contenu non stylisé sur leur site.
   * permet de convertir le mode de ciblage de n’importe quel composant en fragment d’expérience (types JSON et HTML) qui utilise des modèles modifiables.

>[!NOTE]
>
>Les activités de personnalisation existantes qui utilisent déjà des offres héritées peuvent continuer à le faire, mais de nouvelles activités de personnalisation doivent être créées en tant que fragments d’expérience, car c’est l’approche recommandée à l’avenir.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Assets] {#prerelease-features-assets}

Vous pouvez maintenant configurer Adobe Experience Manager Assets sur [restreindre le type de ressources que les utilisateurs peuvent charger en fonction du type MIME ;](/help/assets/configure-asset-upload-restrictions.md).

![Restrictions de chargement des ressources](/help/assets/assets/asset-upload-restrictions.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités de [!DNL Forms] {#forms-features}

* **[Prise en charge des entrées au clavier pour les signatures tactiles](/help/forms/signing-forms-using-scribble.md)**: Les Forms adaptatives sont de plus en plus utilisées sur les périphériques tactiles, et une exigence courante est de prendre en charge les signatures. La signature de documents sur les périphériques tactiles est devenue une méthode acceptée de signature de formulaires. Adaptive Forms prend en charge nativement les signatures tactiles et Adobe Sign pour de tels cas d’utilisation. Désormais, avec d’autres options déjà prises en charge, vous pouvez également utiliser le clavier pour apposer des signatures tactiles dans un formulaire adaptatif. Elle contribue également à améliorer la conformité en matière d’accessibilité.

![Prise en charge de la saisie au clavier pour les signatures tactiles sur iPhone](/help/release-notes/assets/scribble-keyboard-mobile.png)

* **Utilisation de l’assistant de Forms adaptatif en langue locale**: Vous pouvez utiliser l&#39;assistant dans la langue de votre choix. Il prend désormais en charge toutes les langues prises en charge par Adobe Experience Manager.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Forms] {#prerelease-features-forms}

<!-- 

* **[Launch Adaptive Form creation wizard from embed form component](/help/forms/using/embed-adaptive-form-aem-sites.md)**: You can now launch Adaptive Form creation wizard from embed form component. It helps improve content and forms authoring workflows for Sites and Forms practitioners trying to add enrollment experiences to a web page. 

![Keyboard input support for Scribble signatures on iphone](/help/release-notes/assets/froms-container.png) 

-->

* **[Invoke DDX - Une étape de processus AEM](/help/forms/aem-forms-workflow-step-reference.md#invokeddx)**: Document Description XML (DDX) est un langage de marquage déclaratif dont les éléments représentent des blocs de construction de documents. Ces blocs de création comprennent des documents PDF et XDP, ainsi que d’autres éléments tels que des commentaires, des signets et du texte stylisé. Les documents DDX sont des modèles pour les documents et décrivent les caractéristiques souhaitées des documents source qui doivent apparaître dans les documents créés. Un DDX unique peut être utilisé avec un éventail de documents source. Vous pouvez utiliser l’étape Appeler un workflow d’AEM pour effectuer diverses opérations, comme assembler des documents, créer et modifier Acrobat et XFA Forms, ainsi que d’autres opérations décrites dans la section [Référence DDX](https://helpx.adobe.com/content/dam/help/en/experience-manager/forms-cloud-service/ddxRef.pdf) documentation.

* **[Convertir en PDF/A - Une étape de processus AEM](/help/forms/aem-forms-workflow-step-reference.md##convert-pdfa)**: PDF/A est un format d’archivage pour la conservation à long terme du contenu du document, toutes les polices sont incorporées et le fichier est décompressé. Désormais, vous pouvez utiliser l’étape Convertir en PDF/A d’un processus AEM pour convertir vos documents ou fichiers dans n’importe quel format au format PDF/A.


## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* L’enrichissement du catalogue de produits prend désormais en charge AEM pages. Cela permet aux auteurs de gérer l’association page - produit.

* Diverses améliorations du composant principal CIF

### Correctifs {#bug-fixes-cif}

* Ajout d’un jeton de connexion à la récupération de prix côté client

* Composant de page incorrect dans le lecteur de données

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Nouveautés {#what-is-new-foundation}

* Le [Explorateur de référentiels](/help/implementing/developing/tools/repository-browser.md) dispose désormais d’un champ d’entrée de chemin d’accès, ce qui permet de passer directement à un dossier spécifique dans la hiérarchie du référentiel.
* Sling Content Distribution (SCD) prend désormais en charge une action d’&quot;invalidation&quot; explicite afin d’invalider le contenu sans que ce contenu soit publié. Reportez-vous à la section [Mise en cache dans AEM as a Cloud Service](/help/implementing/dispatcher/caching.md#explicit-invalidation) pour plus d’informations.
* mod_macro est désormais disponible dans AEM as a Cloud Service. Voir [ce tableau](/help/implementing/dispatcher/disp-overview.md) pour obtenir la liste des modules Apache pris en charge.

### AEM Améliorations apportées aux outils du Dispatcher SDK as a Cloud Service {#dispatcher-tools-enhancements}

* Apache peut être démarré avec `docker_run_hot_reload.sh` qui chargera et validera automatiquement toutes les modifications ultérieures apportées à la configuration apache et dispatcher, améliorant ainsi la vitesse du développeur. Prise en charge uniquement pour le mode flexible des outils Dispatcher. Voir aussi [Débogage de la configuration Apache et Dispatcher](/help/implementing/dispatcher/validation-debug.md#automatic-reloading) pour plus d’informations sur le rechargement et la validation automatiques.
* La configuration apache/dispatcher locale suit plus attentivement les modifications dans les environnements cloud, augmentant la parité entre les deux environnements.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Experience Manager] {#prerelease-features-foundation}

* AEM as a Cloud Service est désormais intégré à Unified Shell pour améliorer l’expérience utilisateur et l’unifier avec toutes les autres applications Experience Cloud. Voir [AEM as a Cloud Service sur Shell unifié](/help/overview/aem-cloud-service-on-unified-shell.md) pour plus d’informations.

## Connecteurs Adobe Learning Manager {#learn-manage}

* Le nouveau gestionnaire d’apprentissage Adobe dispose de connecteurs vers Adobe Experience Manager Sites, Marketo Engage et Adobe Commerce. Pour en savoir plus, voir : [Guide de l’utilisateur d’Adobe Learning Manager](https://helpx.adobe.com/learning-manager/user-guide.html).


## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
