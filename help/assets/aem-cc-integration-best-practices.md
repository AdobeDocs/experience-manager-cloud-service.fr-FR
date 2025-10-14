---
title: Bonnes pratiques pour l’intégration à [!DNL Adobe Creative Cloud]
description: Bonnes pratiques pour intégrer un déploiement Experience Manager à Adobe Creative Cloud de façon à rationaliser les workflows de transfert de ressources et à obtenir un maximum d’efficacité.
contentOwner: AG
mini-toc-levels: 1
feature: Collaboration, Adobe Asset Link, Desktop App
role: User, Architect, Admin
exl-id: cbed0d62-5148-45eb-b6a0-9fd164060fdc
source-git-commit: 9c1104f449dc2ec625926925ef8c95976f1faf3d
workflow-type: tm+mt
source-wordcount: '3438'
ht-degree: 94%

---

# Bonnes pratiques d’intégration d’Adobe Experience Manager et Creative Cloud {#aem-and-creative-cloud-integration-best-practices}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/aem-cc-integration-best-practices.html?lang=fr) |
| AEM as a Cloud Service | Cet article |

Adobe Experience Manager Assets est une solution de gestion des ressources numériques (DAM) qui peut s’intégrer à Adobe Creative Cloud pour aider les utilisateurs de DAM à travailler avec des équipes créatives, en rationalisant la collaboration en matière de création de contenu.

Adobe Creative Cloud offre aux équipes de contenu créatif un écosystème de solutions et de services pour leur permettre de créer des ressources numériques. Il comprend des applications de bureau et mobiles, des services cloud tels que le stockage avec une synchronisation sur poste de travail ou une expérience web, ainsi que des places de marché telles qu’Adobe Stock.

Lisez ce qui suit pour savoir quelles intégrations choisir entre poste de travail et gestion des ressources numériques d’entreprise selon votre cas d’utilisation et découvrir quelles sont les bonnes pratiques associées aux workflows de connexion.

>[!NOTE]
>
>Le partage de dossiers d’Experience Manager vers Creative Cloud est maintenant obsolète et n’est plus traité ci-après. Adobe recommande des fonctionnalités plus récentes, telles qu’Adobe Asset Link ou l’application de bureau Experience Manager, pour fournir aux utilisateurs créatifs un accès aux ressources gérées dans Experience Manager.

## Besoins en matière de collaboration des créatifs, spécialistes marketing et utilisateurs de DAM {#collaboration-need-of-creatives-marketers-and-dam-users}

| Conditions requises | Cas d’utilisation | Surfaces impliquées |
|---|---|---|
| Simplifier l’expérience pour les créatifs utilisant un poste de travail | Simplifiez l’accès aux ressources depuis une gestion des ressources numériques ([!DNL Assets]) pour les créatifs ou, plus largement, pour les utilisateurs sur poste de travail utilisant des applications de création de ressources natives. Ces derniers ont besoin d’une méthode simple et rapide pour découvrir, utiliser (ouvrir), modifier et enregistrer les modifications dans Experience Manager, ainsi que pour charger de nouveaux fichiers. | Poste de travail Windows ou Mac ; applications Creative Cloud |
| Fournir des ressources de grande qualité, prêtes à l’emploi depuis [!DNL Adobe Stock] | Les spécialistes marketing accélèrent le processus de création de contenu en contribuant à la recherche et à la découverte de ressources. Les créatifs utilisent les ressources approuvées directement dans leurs outils de création. | [!DNL Assets] ; marketplace [!DNL Adobe Stock] ; champs de métadonnées |
| Distribuer et partager des ressources par organisations | Les services internes/succursales locales et les partenaires externes, les distributeurs et les agences utilisent les ressources approuvées, partagées par la société mère. La société souhaite partager de manière sécurisée et transparente les ressources créées pour une réutilisation plus large. | [!DNL Brand Portal], [!DNL Asset Share Commons] |
| Génération automatique des variations prédéfinies des ressources chargées | Traitez automatiquement les ressources à l’aide de la technologie de transformation et de gestion des médias unique d’Adobe pour les actions prédéfinies. Créez une logique personnalisée pour définir vos propres actions à l’aide des API et des microservices de ressources. | Interface utilisateur d’[!DNL Assets] |

## Offres d’Adobe pour répondre aux besoins en matière de collaboration {#adobe-offerings-to-support-the-collaboration-need}

| Proposition de valeur pour les oersonnes impliquées | Offre Adobe | Surfaces impliquées |
|---|---|---|
| Les personnes créatives découvrent des ressources à partir de [!DNL Experience Manager], les ouvrent et les utilisent, les modifient et chargent les modifications dans [!DNL Experience Manager], ou encore chargent les nouveaux fichiers dans [!DNL Experience Manager] sans quitter leur application [!DNL Creative Cloud]. | [Adobe Asset Link](https://helpx.adobe.com/fr/enterprise/using/adobe-asset-link.html) | Photoshop, Illustrator et InDesign. |
| Les utilisateurs professionnels simplifient l’ouverture et l’utilisation des ressources, la modification et le chargement des modifications dans [!DNL Experience Manager] et le chargement de nouveaux fichiers dans [!DNL Experience Manager] à partir de l’environnement de poste de travail. Ils utilisent une intégration générique pour ouvrir n’importe quel type de ressource dans l’application de bureau native, y compris les applications autres qu’Adobe. | Application de bureau [[!DNL Experience Manager] &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=fr) | Application de bureau Experience Manager sous Windows et Mac |
| Les spécialistes marketing et les utilisateurs professionnels découvrent, prévisualisent, attribuent une licence et enregistrent les ressources Adobe Stock dans Experience Manager. Les ressources sous licence et enregistrées fournissent des métadonnées Adobe Stock pour une meilleure gouvernance. | [Intégration d’Experience Manager et d’Adobe Stock](aem-assets-adobe-stock.md) | Interface web [!DNL Experience Manager] |
| Améliorez la collaboration entre les concepteurs de produits numériques et les spécialistes marketing. Permettez aux concepteurs d’utiliser les ressources numériques dans les modèles de conception et de structure filaire sur la zone de travail Adobe XD. | [[!DNL Adobe Asset Link] pour [!DNL Adobe XD]](https://helpx.adobe.com/fr/enterprise/using/adobe-asset-link-for-xd.html) | [!DNL Adobe XD] |
| Les spécialistes marketing peuvent créer automatiquement des variations et des dérivés en fonction des ressources chargées et des actions prédéfinies créées à l’aide de la personnalisation. Utilisez cette automatisation pour améliorer la vitesse du contenu et réduire les efforts manuels. | [Automatisation du contenu](/help/assets/cc-api-integration.md) | Interface Web [!DNL Experience Manager Assets] |

Cet article se concentre principalement sur les deux premiers aspects des besoins de collaboration. La distribution et la source des ressources à grande échelle sont brièvement mentionnées comme cas d’utilisation. Pour répondre à ces besoins, pensez à Adobe Brand Portal ou à Asset Share Commons. D’autres solutions (par exemple, [Experience Manager Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html?lang=fr), les solutions pouvant être créées en fonction des composants [Asset Share Commons](https://opensource.adobe.com/asset-share-commons/), [Partage de lien](share-assets.md) à l’aide de l’[interface utilisateur web d’Experience Manager Assets](/help/assets/manage-digital-assets.md)) doivent être envisagées en fonction des besoins spécifiques.

![Connexions Creative Cloud pour Experience Manager : choix de la fonctionnalité à utiliser](assets/creative-connections-aem.png)

Choix de la fonctionnalité à utiliser

### Correspondance des cas d’utilisation aux solutions Adobe {#mapping-of-use-cases-and-adobe-solutions}

| Cas d’utilisation | Adobe Asset Link | Application de bureau Experience Manager | Remarques ou autres méthodes |
|----------------------------------------------------------|-----------------------------------------------------------------------------------|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| Découverte – parcours des dossiers | Oui | Interface utilisateur web Experience Manager + actions de bureau | Lors du parcours du partage réseau, désactivez les miniatures pour éviter de télécharger des fichiers binaires de ressources. |
| Découverte – accès aux collections | Oui | Interface utilisateur web Experience Manager + actions de bureau |  |
| Découverte – Recherche de ressources | Oui | Interface utilisateur web Experience Manager + actions de bureau |  |
| Utilisation – ouverture de la ressource | Oui | Oui – pour toutes les applications | [Ouverture depuis l’interface web](/help/assets/manage-digital-assets.md#previewing-assets) ou de l’outil de recherche |
| Utilisation – placement de la ressource d’Experience Manager dans un document | Oui – incorporation | Oui – liaison ou incorporation | L’application de bureau Experience Manager donne accès aux ressources sous forme de fichiers sur le système de fichiers local. Ces liens dans les applications natives sont représentés par des chemins d’accès locaux. |
| Modification – ouvrir pour modification | Oui – action d’extraction | Oui – action d’ouverture (dans le partage réseau) | L’[extraction dans AAL](https://helpx.adobe.com/fr/enterprise/using/manage-assets-using-adobe-asset-link.html) enregistre la ressource dans le compte de stockage Creative Cloud de l’utilisateur (synchronisé par l’application Creative Cloud) par défaut. |
| Modifier : travail en cours en dehors d’Experience Manager | Oui – ressource disponible dans le compte de stockage Creative Cloud de l’utilisateur synchronisé avec le poste de travail. | Oui |  |
| Modification – téléchargement des modifications | Oui – [Action d’archivage](https://helpx.adobe.com/fr/enterprise/using/manage-assets-using-adobe-asset-link.html) avec des commentaires facultatifs | Oui |  |
| Téléchargement – fichier unique | Oui – téléchargement du document actif | Oui | [Chargement via l’interface web](/help/assets/manage-digital-assets.md#uploading-assets) |
| Téléchargement – plusieurs fichiers/structures de dossiers hiérarchiques | Non | Oui | [Chargement via l’interface web](/help/assets/manage-digital-assets.md#uploading-assets) ; outil ou script personnalisé |
| Divers – utilisateur et connexion | L’utilisateur ou l’utilisatrice Creative Cloud connecté(e) à l’appli de bureau Creative Cloud est reconnu(e) (SSO). | Utilisateur/connexion Experience Manager | Les utilisateurs des deux solutions sont comptabilisés par rapport au quota d’utilisateurs Experience Manager. |
| Divers – réseau et accès | Nécessite un accès depuis le poste de travail de l’utilisateur vers le déploiement d’Experience Manager sur le réseau | Nécessite un accès depuis le poste de travail de l’utilisateur vers le déploiement d’Experience Manager sur le réseau | Adobe Asset Link ne partage pas l’environnement du proxy réseau. |


<!-- Removing this row from table as migration guide is not yet final.
| Misc - Migrate large number of assets | No | No | [Migration Guide](/help/assets/assets-migration-guide.md) |
-->

Pour prendre en charge les cas d’utilisation de la distribution des ressources, tenez compte des options suivantes :

* [Experience Manager Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html?lang=fr) pour un module complémentaire configurable pour Assets afin de publier des ressources.

* Les solutions personnalisées sont créées à partir de la base de code [Asset Share Commons](https://opensource.adobe.com/asset-share-commons/).
* Experience Manager [partage de liens](/help/assets/share-assets.md) pour partager des ressources à la demande à l’aide de liens.
* [Interface web d’Assets](/help/assets/manage-digital-assets.md) avec des zones destinées aux parties externes, sécurisées par la configuration du contrôle d’accès, et avec les ajustements de configuration informatique/réseau nécessaires pour permettre à ces utilisateurs externes d’accéder à Experience Manager.

## Concepts clés et cas d’utilisation {#key-concepts-and-use-cases}

### Glossaire des termes courants {#glossary-of-common-terms}

* **Travail en cours ou travail créatif en cours (WIP) :** phase dans le cycle de vie des ressources où une ressource est soumise à de multiples modifications et n’est généralement pas encore prête à être partagée avec les équipes élargies.
* **Ressources prêtes après création :** ressources prêtes à être partagées avec l’équipe élargie ou sélectionnées/approuvées par l’équipe créative pour le partage avec les équipes marketing ou métier.

* **Approbation des ressources** : processus d’approbation traitant des ressources déjà chargées dans la gestion des ressources numériques, qui inclut généralement les approbations de marque, les validations juridiques, etc.
* **Fichier final :** ressource qui a fait l’objet de toutes les approbations/balises de métadonnées et qui est prête à être utilisée par la grande équipe. Une telle ressource est stockée dans la gestion des ressources numériques (DAM) et est accessible à tous les utilisateurs (ou à tous les utilisateurs intéressés). Il peut être utilisé dans les canaux marketing ou par des équipes créatives pour créer des conceptions.

* **Mise à jour/modification mineure des ressources :** modification rapide et petite d’une ressource numérique. Cette opération est souvent effectuée en réponse à une demande de retouche ou de modification mineure, de révision ou d’approbation de fichier (par exemple, repositionnement, modification de la taille du texte, ajustement de la saturation/luminosité, couleur, etc.).
* **Mise à jour/modification majeure des ressources :** modification d’une ressource numérique qui nécessite un travail considérable et qui doit parfois être effectuée sur une plus longue période de temps. Celle-ci implique généralement plusieurs modifications. La ressource doit être enregistrée plusieurs fois lors de la mise à jour. En règle générale, les mises à jour majeures de la ressource entraînent le passage à une étape en cours.
* **DAM :** gestion des ressources numériques (en anglais, Digital Asset Management). Dans ce document, il est synonyme d’Adobe Experience Manager () Assets, sauf mention contraire.
* **Utilisateur créatif :** professionnel de la création, qui crée des ressources numériques à l’aide des applications et services Creative Cloud. Dans certains cas, un utilisateur créatif peut faire partie d’une équipe créative qui peut utiliser Creative Cloud, mais ne crée pas de ressources numériques (comme un directeur créatif ou un chef d’équipe créative).
* **Utilisateur de la gestion des ressources numériques :** utilisateur ordinaire d’un système de gestion des ressources numériques (DAM, Digital Asset Management). En fonction de l’organisation, un utilisateur ou une utilisatrice DAM peut être un utilisateur ou une utilisatrice marketing ou non marketing, par exemple un utilisateur ou une utilisatrice du secteur d’activité, un ou une bibliothécaire, un vendeur ou une vendeuse, etc.

### Remarques concernant l’utilisation de l’intégration Experience Manager et Creative Cloud {#considerations-when-using-aem-and-creative-cloud-integration}

<!--incomplete and TBD: 

* DA2.0 best practices: See troubleshooting.md
* Stock integration: See ?
* AAL: See ?
* BP: See ?

-->

Voici un bref résumé des bonnes pratiques pour l’intégration Experience Manager et Creative Cloud. Lisez la suite de ce document pour obtenir une description détaillée des points suivants.

* **Pour les utilisateurs créatifs, utilisant Photoshop, InDesign ou Illustrator :** Adobe Asset Link offre une expérience utilisateur optimale, notamment la gestion des tâches en cours sur les ressources extraites à partir d’Experience Manager.
* **Pour simplifier l’accès aux ressources depuis un poste de travail pour une application ou un format de fichier générique :** utilisez l’application de bureau Experience Manager.
* **Déterminer pourquoi et quand stocker des ressources dans la gestion des ressources numériques (DAM) :** identifiez quelles mises à jour doivent être mises à la disposition de l’équipe élargie au sein de votre organisation.
* **Tenez compte du volume des ressources partagées :** si votre cas d’utilisation est la distribution des ressources, la gouvernance et la sécurité peuvent être les aspects les plus importants. Envisagez d’utiliser des outils conçus pour effectuer les tâches à grande échelle, comme Brand Portal.
* **Comprendre le cycle de vie des ressources :** comprenez la façon dont les ressources sont traitées par les différentes équipes au sein de votre organisation.
* **Gérer avec soin les enregistrements fréquents des ressources :** Adobe Asset Link s’en charge à votre place avec PS, IA, ID. Pour d’autres applications, ne conservez pas de travaux en cours dans le dossier mappé/partagé, sauf si vous avez besoin de toutes les modifications dans DAM

### Accès aux ressources Adobe Stock depuis Experience Manager Assets {#access-to-adobe-stock-assets-from-aem-assets}

L’[intégration d’Experience Manager et Adobe Stock](/help/assets/aem-assets-adobe-stock.md) permet aux utilisateurs d’Experience Manager de rechercher, de prévisualiser, d’obtenir des licences et d’enregistrer des ressources Adobe Stock dans Experience Manager. Les ressources sous licence et enregistrées d’Adobe Stock possèdent des métadonnées Stock qui peuvent être utilisées pour les rechercher avec des filtres supplémentaires.

Quelques points importants à savoir concernant cette intégration :

* Lorsque des ressources Adobe Stock sont enregistrées dans Experience Manager, elles deviennent des ressources Experience Manager Assets standard, avec un binaire enregistré dans le référentiel Experience Manager. Certaines métadonnées liées à Adobe Stock sont enregistrées pour la ressource dans Experience Manager. Sinon, le processus d’ingestion ressemble à celui de tout autre fichier. Par exemple, si les balises dynamiques sont actives, les balises sont ajoutées à ces fichiers lors de l’enregistrement.
* La ressource enregistrée dans Experience Manager est une copie et non un lien vers Adobe Stock.

**Utilisation des ressources enregistrées depuis Adobe Stock dans Experience Manager dans Creative Cloud**. Cette intégration est indépendante d’Adobe Asset Link, mais cette fonction reconnaît ces ressources enregistrées depuis Stock de cette manière et affiche d’autres métadonnées et une icône Stock sur ces ressources dans l’interface utilisateur de l’extension Adobe Asset Link dans Photoshop, Illustrator et InDesign. Les fichiers peuvent être parcourus, ouverts, etc., car il s’agit de ressources Experience Manager standard lorsqu’ils sont enregistrés dans Experience Manager.
Les utilisateurs créatifs utilisant les applications Creative Cloud avec l’extension Adobe Asset Link ont accès aux ressources déjà sous licence d’Adobe Stock dans Experience Manager et peuvent aussi utiliser le panneau Bibliothèques Creative Cloud pour rechercher, prévisualiser et obtenir des licences pour les ressources Adobe Stock.
Les ressources d’Adobe Stock sous licence et enregistrées dans Experience Manager sont accessibles aux équipes élargies qui accèdent au déploiement Experience Manager Assets, tandis que les équipes créatives obtenant une licence pour des ressources d’Adobe Stock via le panneau Bibliothèques Creative Cloud y ont uniquement accès par défaut dans leur compte Creative Cloud.

## À propos du stockage de ressources dans un système de gestion des ressources numériques (DAM)  {#about-storing-assets-in-a-dam}

Pour établir un workflow efficace entre les équipes créatives et marketing/métier, et sélectionner les meilleures fonctionnalités de prise en charge, il est important de comprendre quand et pourquoi les ressources sont stockées dans la gestion des ressources numériques (DAM).

### Pourquoi les ressources sont-elles stockées dans la gestion des ressources numériques (DAM) ? {#why-assets-are-stored-in-dam}

Le stockage des ressources dans la gestion des ressources numériques (DAM) permet d’en faciliter l’accès et de les retrouver plus aisément. Cela permet de s’assurer que les ressources peuvent être utilisées par de nombreux utilisateurs et utilisatrices au sein de l’organisation ou de l’écosystème, qui comprend des partenaires, des clients ou clientes, etc.

La plupart des entreprises choisissent de stocker uniquement les ressources pertinentes pour les processus marketing/métier en aval (publication sur des canaux tels que le canal web via Experience Manager Sites ou d’autres canaux traités par Adobe Experience Cloud : Marketing Cloud, Advertising Cloud et mesurés par Analytics Cloud, satisfaction des besoins des utilisateurs et partenaires, etc.). En outre, les organisations stockent les ressources qui peuvent être soumises à un processus de révision/approbation dans la gestion des ressources numériques (DAM). De cette manière, la gestion des ressources numériques stocke principalement les ressources ayant de grandes chances d’être utilisées, évitant ainsi de stocker les ressources inactives.

Le stockage des ressources est soumis à des considérations techniques et d’utilisation des ressources. La gestion des ressources numériques (DAM) fournit des services supplémentaires pour les ressources stockées, notamment l’extraction de métadonnées, le contrôle de version, la génération d’aperçus/de transcodage, la gestion des références et l’ajout d’informations de contrôle d’accès. Ces services utilisent du temps et des ressources d’infrastructure supplémentaires.

Souvent, il n’est pas recommandé de stocker toutes les ressources et mises à jour. Par exemple, si les mises à jour de ressources spécifiques sont de mauvaise qualité et utilisent les ressources en excès, les ressources peuvent être stockées dans la gestion des ressources numériques (DAM).

#### Quand les ressources sont-elles stockées dans la gestion des ressources numériques (DAM) ? {#when-assets-are-stored-in-dam}

Les équipes de contenu créatif (et les organisations) ne sont généralement pas intéressées par le stockage des ressources à chaque étape du cycle de vie des ressources. Par exemple, elles évitent de stocker des ressources dans les cas suivants :

* Ressources qui doivent encore être finalisées ou qui font l’objet d’expérimentations.
* Ressources n’ayant pas passer le cycle de révision de l’équipe interne/de contenu créatif
* L’équipe dispose de ressources plus pertinentes que celle en question pour présenter son travail à des équipes externes

En règle générale, les classes de ressources suivantes sont stockées dans la gestion des ressources numériques (DAM) :

* Ressources ayant atteint une certaine maturité et que l’on estime prêtes à être partagées.
* Ressources qui ont été présélectionnées par l’équipe de contenu créatif.
* Les formats de ressources spécifiques qui sont utilisables ou demandés par le marketing, selon un contrat ou un accord spécifique (par exemple, des fichiers JPG convertis à partir de fichiers RAW, des TIFF/images à partir d’originaux PSD).

#### Quand les mises à jour de ressources sont-elles stockées dans la gestion des ressources numériques (DAM) ? {#when-updates-to-assets-are-stored-in-dam}

En règle générale, seules les mises à jour des ressources pertinentes pour un large ensemble d’utilisateurs de la gestion des ressources numériques doivent être stockées dans la gestion des ressources numériques (DAM). Cela garantit que les utilisateurs (marketing et fonctions similaires) voient uniquement les versions appropriées dans la chronologie des ressources de la gestion des ressources numériques (DAM).

En règle générale, les modifications liées aux jalons principaux du cycle de vie des ressources. Par exemple, la ressource initiale prête pour les spécialistes marketing ou une mise à jour officielle basée sur une demande/révision fournie par l’équipe créative doit être enregistrée et versionnée dans la gestion des ressources numériques (DAM).

Il peut s’agir, par exemple, d’une mise à jour de l’équipe créative pour révision par l’équipe marketing après une demande de modification de la ressource existante dans la gestion des ressources numériques (DAM). Elle doit être stockée et versionnée dans la gestion des ressources numériques (DAM) à des fins de référence ou pour revenir à la version précédente.

Voici des exemples de mises à jour qui ne sont généralement pas pertinentes :

* Les premières versions des ressources chargées avant qu’elles ne soient prêtes pour la révision marketing.
* Modifications créatives fréquentes de la ressource au cours de la phase de travail en cours avant que les équipes créatives et marketing ne décident que la ressource est prête

### Accès des utilisateurs à la gestion des ressources numériques (DAM)  {#user-access-to-dam}

Experience Manager Assets prend en charge deux types d’utilisateurs selon leur accès au déploiement d’ Experience Manager Assets. En règle générale, les utilisateurs à l’intérieur du réseau d’entreprise (pare-feu) ont un accès direct à la gestion des ressources numériques (DAM). Les autres utilisateurs à l’extérieur du réseau d’entreprise n’auront pas d’accès direct. Le type d’utilisateur détermine les intégrations qui peuvent être utilisées du point de vue technique.

#### Utilisateurs créatifs avec un accès direct à la gestion des ressources numériques (DAM) {#creative-users-with-direct-access-to-dam}

En règle générale, les équipes créatives internes ou les agences/professionnels de la création intégrés au réseau interne ont accès à l’instance de gestion des ressources numériques, y compris la connexion à Experience Manager. Experience Manager et l’infrastructure réseau peuvent être configurés afin d’autoriser un accès direct aux parties externes (généralement, des entreprises de confiance telles que des agences travaillant pour un client) pour disposer d’un accès à Experience Manager via le réseau (par le biais de la liste adresses IP autorisées ou d’un VPN, par exemple).

Dans ce cas, Adobe Asset Link ou l’application de bureau Experience Manager permet d’accéder facilement aux ressources finales/approuvées et d’enregistrer les ressources préparées par les créatifs dans la gestion des ressources numériques (DAM).

#### Utilisateurs créatifs sans accès à la gestion des ressources numériques (DAM)  {#creative-users-without-access-to-dam}

Les agences externes et les indépendants sans accès direct à l’instance de la gestion des ressources numériques peuvent avoir besoin de l’accès aux ressources approuvées ou souhaiter ajouter leurs nouvelles créations dans la gestion des ressources numériques (DAM).

Utilisez les stratégies suivantes pour fournir un accès aux ressources finales/approuvées :

* Utilisez l’application de bureau si Asset Link ne fonctionne pas.
* Utilisez [Experience Manager Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html?lang=fr) pour distribuer les ressources en toute sécurité aux partenaires externes.
* Utilisez une implémentation personnalisée d’un portail de distribution et de source basé sur [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/)
* Utilisez la configuration du contrôle d’accès dans Experience Manager et l’infrastructure réseau nécessaire (mise en liste d’adresses IP autorisées et VPN, par exemple) pour permettre aux parties externes d’accéder à une zone de contenu dédiée dans la gestion des ressources numériques (DAM). Ils peuvent utiliser l’interface utilisateur web d’Experience Manager pour obtenir des ressources et charger du nouveau contenu dans la gestion des ressources numériques (DAM).

#### Tâche en cours sur les ressources d’Experience Manager {#work-in-progress-on-assets-from-aem}

Comme nous l’avons vu dans ce document, il est recommandé d’effectuer des mises à jour importantes sur les ressources, parfois appelées tâche en cours, sans que toutes les modifications enregistrées dans le fichier local ne soient chargées dans Experience Manager en tant que modifications. Cela permet d’accélérer le travail sur les postes de travail, limite la bande passante réseau utilisée et maintient la chronologie des ressources propre et concentrée sur des mises à jour majeures contrôlées.

Adobe Asset Link offre une bonne prise en charge de ce cas pratique :

* Lorsque les utilisateurs et utilisatrices de Photoshop, InDesign ou Illustrator souhaitent modifier un fichier, ils ou elles effectuent une opération d’extraction sur la ressource donnée.
* La ressource est téléchargée en arrière-plan, placée dans le compte Creative Cloud des utilisateurs synchronisés sur le disque par l’application de bureau Creative Cloud et l’indicateur d’extraction est activé sur la ressource dans Experience Manager afin de minimiser les conflits de modification.
* À partir de là, la personne travaille dans un fichier qui est stocké localement à l’emplacement synchronisé et peut continuer à travailler et à enregistrer les modifications nécessaires à n’importe quelle fréquence.
* En outre, comme la ressource se trouve dans le compte Creative Cloud, elle est également disponible sur d’autres appareils que la personne peut posséder (par exemple, elle peut être ouverte ou modifiée dans une application mobile Creative Cloud dédiée) et peut être partagée avec d’autres personnes utilisatrices de Creative Cloud à des fins de collaboration.
* Lorsque l’utilisateur créatif a terminé d’apporter des modifications, il peut effectuer une opération d’archivage sur ce fichier dans son application Creative Cloud, en fournissant un commentaire facultatif. La ressource correspondante dans Experience Manager est versionnée et mise à jour avec le nouveau binaire. Les utilisateurs d’Experience Manager comme les spécialistes marketing ou les utilisateurs du cœur de métier ont accès aux modifications importantes des ressources, ou jalons, via l’interface utilisateur de chronologie d’ Experience Manager Assets.

L’application de bureau Experience Manager propose un partage réseau pour les ressources ouvertes dans l’application native. Par défaut, toutes les modifications apportées localement sont chargées automatiquement dans Experience Manager après un bref instant. Avec une telle configuration, les enregistrements fréquents durant la phase de travail en cours seraient tous chargés dans Experience Manager et versionnés, ce qui créerait un trafic réseau important et des défis d’évolutivité potentiels, sans mentionner les versions inutiles dans Experience Manager.

L’approche recommandée dans ce cas consiste à utiliser une option dans l’application de bureau Experience Manager pour désactiver les mises à jour automatisées et à charger manuellement les modifications des ressources dans Experience Manager, à l’aide de l’action de chargement des modifications dans l’interface utilisateur Statut de la ressource de l’application.

#### Chargement en masse dans DAM {#bulk-upload-to-dam}

Dans certains cas, il est possible que vous deviez charger simultanément un plus grand nombre de fichiers dans la gestion des ressources numériques (DAM), par exemple :

* Chargement des résultats de séance photo ou de projets plus volumineux
* Chargement de ressources fournies par les agences de création
* Chargement de ressources sélectionnées à partir d’un plus grand ensemble si la sélection est effectuée en dehors de la gestion des ressources numériques (DAM)

Cette description fait référence aux chargements de fichiers de manière opérationnelle (par exemple, chaque semaine ou chaque séance photo ), en tant qu’élément normal du workflow de l’utilisateur de l’application de bureau. Les migrations de ressources volumineuses ne sont pas abordées ici.

Vous pouvez utiliser les fonctionnalités de chargement suivantes :

* Pour charger des dossiers volumineux/hiérarchiques en bloc, utilisez l’application de bureau Experience Manager qui propose une fonctionnalité de [chargement de dossiers](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=fr#bulk-upload-assets). Vous pouvez également charger des structures de dossiers hiérarchiques. Les ressources sont chargées en arrière-plan et, par conséquent, le chargement n’est pas associé à une session du navigateur web.
* Pour charger quelques fichiers à partir d’un seul dossier, faites-les glisser directement jusqu’à l’interface web ou utilisez l’option Créer dans l’interface web d’Experience Manager Assets.
* En fonction des besoins de votre entreprise, vous pouvez également utiliser un outil de chargement personnalisé.

#### Gestion directe des ressources numériques depuis l’ordinateur de bureau {#managing-digital-assets-directly-from-desktop}

Si vous utilisez des partages de fichiers réseau pour gérer les ressources numériques, le fait d’utiliser uniquement un partage réseau mappé par l’application de bureau Experience Manager peut être considéré comme une alternative pratique. Si vous choisissez de ne plus utiliser les partages de fichiers réseau, l’interface utilisateur web d’Experience Manager propose un large éventail de fonctionnalités de gestion des ressources numériques qui vont bien au-delà de ce qui est possible sur un partage réseau (recherche, collections, métadonnées, collaboration, aperçus, etc.) et l’application de bureau Experience Manager fournit un lien pratique pour connecter le référentiel de gestion des ressources numériques (DAM) côté serveur au travail sur l’ordinateur de bureau.

Évitez d’utiliser l’application de bureau Experience Manager pour gérer les ressources directement dans le partage réseau d’Experience Manager Assets. Par exemple, évitez d’utiliser l’application de bureau Experience Manager pour déplacer/copier plusieurs fichiers. Au lieu de cela, utilisez l’interface utilisateur web d’Experience Manager Assets pour faire glisser des dossiers à partir du Finder/de l’Explorateur vers le partage réseau ou utilisez la fonctionnalité de chargement de dossier d’ Experience Manager Assets.

**Voir également**

* [Traduire les ressources](translate-assets.md)
* [API HTTP Assets](mac-api-assets.md)
* [Formats de fichiers pris en charge par Assets](file-format-support.md)
* [Rechercher des ressources](search-assets.md)
* [Ressources connectées](use-assets-across-connected-assets-instances.md)
* [Rapports de ressources](asset-reports.md)
* [Schémas de métadonnées](metadata-schemas.md)
* [Télécharger des ressources](download-assets-from-aem.md)
* [Gestion des métadonnées](manage-metadata.md)
* [Facettes de recherche](search-facets.md)
* [Gérer les collections](manage-collections.md)
* [Import des métadonnées en bloc](metadata-import-export.md)
* [Publier des ressources sur AEM et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
