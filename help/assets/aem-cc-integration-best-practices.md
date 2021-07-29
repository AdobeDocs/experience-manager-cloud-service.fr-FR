---
title: Bonnes pratiques pour l’intégration à [!DNL Adobe Creative Cloud]
description: Bonnes pratiques pour intégrer un déploiement Experience Manager à Adobe Creative Cloud de façon à rationaliser les workflows de transfert de ressources et à obtenir un maximum d’efficacité.
contentOwner: AG
mini-toc-levels: 1
feature: Collaboration,Adobe Asset Link,Application de bureau
role: Architect,User,Admin
exl-id: cbed0d62-5148-45eb-b6a0-9fd164060fdc
source-git-commit: 09aecfac8bab0377e9e777b80e7db986d7aa4914
workflow-type: tm+mt
source-wordcount: '3451'
ht-degree: 57%

---

# Bonnes pratiques d’intégration d’Adobe Experience Manager et de Creative Cloud {#aem-and-creative-cloud-integration-best-practices}

Adobe Experience Manager Assets est une solution de gestion des ressources numériques (DAM) qui peut s’intégrer à Adobe Creative Cloud pour aider les utilisateurs de DAM à travailler avec des équipes créatives, en rationalisant la collaboration dans le processus de création de contenu.

Adobe Creative Cloud offre aux équipes créatives un écosystème de solutions et de services pour leur permettre de créer des ressources numériques. Il comprend des applications de bureau et mobiles, des services de cloud tels que le stockage avec une synchronisation sur poste de travail ou une expérience web, ainsi que des places de marché telles qu’Adobe Stock.

Lisez ce qui suit pour savoir quelles intégrations choisir entre poste de travail et DAM d’entreprise selon votre cas d’utilisation et découvrir quelles sont les bonnes pratiques associées aux workflows de connexion.

>[!NOTE]
>
>Le partage de dossiers Experience Manager à Creative Cloud est désormais obsolète et n’est plus traité ci-dessous. Adobe recommande des fonctionnalités plus récentes, telles qu’Adobe Asset Link ou l’appli de bureau Experience Manager, pour permettre aux utilisateurs créatifs d’accéder aux ressources gérées dans Experience Manager.

## Besoins en matière de collaboration des créatifs, spécialistes marketing et utilisateurs de DAM  {#collaboration-need-of-creatives-marketers-and-dam-users}

| Conditions requises | Cas d’utilisation | Surfaces impliquées |
|---|---|---|
| Simplifier l’expérience pour les créatifs utilisant un poste de travail | Simplifiez l’accès aux ressources à partir d’une gestion des ressources numériques ([!DNL Assets]) pour les professionnels de la création ou, plus largement, pour les utilisateurs de bureau travaillant dans des applications de création de ressources natives. Ils ont besoin d’une méthode simple et simple pour découvrir, utiliser (ouvrir), modifier et enregistrer les modifications dans Experience Manager, ainsi que charger de nouveaux fichiers. | Poste de travail Windows ou Mac ; applications Creative Cloud |
| Fournir des ressources de haute qualité et prêtes à l’emploi à partir de [!DNL Adobe Stock] | Les spécialistes marketing accélèrent le processus de création de contenu en contribuant à la recherche et à la découverte de ressources. Les créatifs utilisent les ressources approuvées directement dans leurs outils de création. | [!DNL Assets];  [!DNL Adobe Stock] le marché; Champs de métadonnées |
| Distribution et partage de ressources par sociétés | Les services internes/succursales locales et les partenaires externes, les distributeurs et les agences utilisent les ressources approuvées, partagées par la société mère. La société souhaite partager de manière sécurisée et transparente les ressources créées pour une réutilisation plus large. | [!DNL Brand Portal], [!DNL Asset Share Commons] |
| Générer automatiquement des variations prédéfinies des ressources chargées | Traitez automatiquement les ressources à l’aide de la technologie de transformation et de gestion des médias unique d’un Adobe pour les actions prédéfinies. Créez une logique personnalisée pour définir vos propres actions à l’aide des API et des microservices de ressources. | Interface utilisateur d’[!DNL Assets] |

## Offres d’Adobe pour répondre aux besoins en matière de collaboration {#adobe-offerings-to-support-the-collaboration-need}

| Proposition de valeur pour les personnes impliquées | Offre d’Adobe | Surfaces impliquées |
|---|---|---|
| Les utilisateurs créatifs découvrent des ressources à partir de [!DNL Experience Manager], les ouvrent et les utilisent, modifient et chargent les modifications dans [!DNL Experience Manager], ainsi que chargent de nouveaux fichiers dans [!DNL Experience Manager], sans quitter leur application [!DNL Creative Cloud]. | [Adobe Asset Link](https://helpx.adobe.com/fr/enterprise/using/adobe-asset-link.html) | Photoshop, Illustrator et InDesign. |
| Les utilisateurs professionnels simplifient l’ouverture et l’utilisation des ressources, la modification et le chargement des modifications dans [!DNL Experience Manager] et le chargement de nouveaux fichiers dans [!DNL Experience Manager] à partir de l’environnement de bureau. Ils utilisent une intégration générique pour ouvrir n’importe quel type de ressource dans l’application de bureau native, y compris les applications autres qu’Adobe. | Application de bureau [[!DNL Experience Manager] ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=fr) | Application de bureau Experience Manager sur un poste de travail Windows et Mac |
| Les marketeurs et les utilisateurs professionnels découvrent, prévisualisent, attribuent une licence et enregistrent les ressources Adobe Stock et les gèrent depuis Experience Manager. Les ressources sous licence et enregistrées fournissent des métadonnées Adobe Stock pour une meilleure gouvernance. | [Intégration d’Experience Manager et d’Adobe Stock](aem-assets-adobe-stock.md) | [!DNL Experience Manager] interface web |
| Améliorez la collaboration entre les concepteurs de produits numériques et les marketeurs. Permet aux concepteurs d’utiliser les ressources numériques dans les modèles de conception et de structure filaire sur la zone de travail Adobe XD. | [[!DNL Adobe Asset Link] pour [!DNL Adobe XD]](https://helpx.adobe.com/fr/enterprise/using/adobe-asset-link-for-xd.html) | [!DNL Adobe XD] |
| Les marketeurs peuvent créer automatiquement des variations et des dérivés en fonction des ressources chargées et des actions prédéfinies créées à l’aide de la personnalisation. Utilisez cette automatisation pour améliorer la vitesse du contenu et réduire les efforts manuels. | [Automatisation du contenu](/help/assets/cc-api-integration.md) | [!DNL Experience Manager Assets] interface web |

Cet article se concentre principalement sur les deux premiers aspects des besoins de collaboration. La distribution et la source des ressources à grande échelle sont brièvement mentionnées comme cas d’utilisation. Pour répondre à ces besoins, pensez à Adobe Brand Portal ou à Asset Share Commons. D’autres solutions telles que [Experience Manager Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html), des solutions qui peuvent être créées en fonction des [composants Asset Share Commons](https://opensource.adobe.com/asset-share-commons/), [Partage de liens](share-assets.md), à l’aide de [l’interface utilisateur web des ressources Experience Manager](/help/assets/manage-digital-assets.md) doivent être examinées en fonction de besoins spécifiques.

![Connexions de Creative Cloud pour Experience Manager : Choix de la fonctionnalité à utiliser](assets/creative-connections-aem.png)

Choix de la fonctionnalité à utiliser

### Correspondance des cas d’utilisation aux solutions Adobe  {#mapping-of-use-cases-and-adobe-solutions}

| Cas d’utilisation | Adobe Asset Link | Application de bureau Experience Manager | Remarques ou autres méthodes |
|----------------------------------------------------------|-----------------------------------------------------------------------------------|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| Discover - dossiers de navigation | Oui | Interface utilisateur web du Experience Manager + actions de bureau | Lors du parcours du partage réseau, désactivez les miniatures pour éviter de télécharger des fichiers binaires de ressources. |
| Discover - Accès aux collections | Oui | Interface utilisateur web du Experience Manager + actions de bureau |  |
| Discover - Recherche de ressources | Oui | Interface utilisateur web du Experience Manager + actions de bureau |  |
| Utilisation - ouverture de la ressource | Oui | Oui - pour toutes les applications | [Ouverture depuis l’interface web](/help/assets/manage-digital-assets.md#previewing-assets) ou de l’outil de recherche |
| Utilisation : placer la ressource du Experience Manager dans un document | Oui - incorporation | Oui - liaison ou incorporation | L’appli de bureau Experience Manager permet d’accéder aux ressources sous forme de fichiers sur le système de fichiers local. Ces liens dans les applications natives sont représentés par des chemins d’accès locaux. |
| Modification - ouvrir pour modification | Oui - action d’extraction | Oui - action d’ouverture (dans le partage réseau) | L’[extraction dans AAL](https://helpx.adobe.com/fr/enterprise/using/manage-assets-using-adobe-asset-link.html) enregistre la ressource dans le compte de stockage Creative Cloud de l’utilisateur (synchronisé par l’application Creative Cloud) par défaut. |
| Modifier : travail en cours en dehors du Experience Manager | Oui - ressource disponible dans le compte de stockage Creative Cloud de l’utilisateur synchronisé avec le poste de travail. | Oui |  |
| Modification - téléchargement des modifications | Oui - [Action d’archivage](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html) avec des commentaires facultatifs | Oui |  |
| Téléchargement - fichier unique | Oui - téléchargement du document actif | Oui | [Chargement via l’interface web](/help/assets/manage-digital-assets.md#uploading-assets) |
| Téléchargement - plusieurs fichiers/structures de dossiers hiérarchiques | Non | Oui | [Chargement via l’interface web](/help/assets/manage-digital-assets.md#uploading-assets) ; outil ou script personnalisé |
| Divers - utilisateur et connexion | L’utilisateur Creative Cloud connecté à l’application de bureau Creative Cloud est reconnu (SSO) | Utilisateur/connexion Experience Manager | Les utilisateurs des deux solutions comptent par rapport au nombre d’utilisateurs Experience Manager. |
| Divers - réseau et accès | Nécessite un accès depuis l’ordinateur de bureau de l’utilisateur au déploiement Experience Manager sur le réseau | Nécessite un accès depuis l’ordinateur de bureau de l’utilisateur au déploiement Experience Manager sur le réseau | Adobe Asset Link ne partage pas l’environnement du proxy réseau. |


<!-- Removing this row from table as migration guide is not yet final.
| Misc - Migrate large number of assets | No | No | [Migration Guide](/help/assets/assets-migration-guide.md) |
-->

Pour prendre en charge les cas d’utilisation de la distribution des ressources, tenez compte des options suivantes :

* [Experience Manager Assets Brand ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) Portal pour un module complémentaire configurable d’Assets afin de publier des ressources.

* Les solutions personnalisées sont créées à partir de la base de code [Asset Share Commons](https://opensource.adobe.com/asset-share-commons/).
* Experience Manager [partage de lien](/help/assets/share-assets.md) pour partager des ressources ad hoc à l’aide de liens.
* [L’](/help/assets/manage-digital-assets.md) interface web d’Assets avec des zones pour les parties externes sécurisées par la configuration du contrôle d’accès du Experience Manager et avec les réglages nécessaires de la configuration informatique/réseau, ce qui permet à ces utilisateurs externes d’accéder à Experience Manager.

## Concepts clés et cas d’utilisation {#key-concepts-and-use-cases}

### Glossaire des termes courants {#glossary-of-common-terms}

* **Travail en cours ou travail créatif en cours (WIP) :** phase dans le cycle de vie des ressources où une ressource est soumise à de multiples modifications et n’est généralement pas encore prête à être partagée avec les équipes élargies.
* **Ressources prêtes après création :** ressources prêtes à être partagées avec l’équipe élargie ou sélectionnées/approuvées par l’équipe créative pour le partage avec les équipes marketing ou métier.

* **Approbation des ressources :** processus d’approbation traitant des ressources déjà transférées dans la gestion des ressources numériques (DAM), qui inclut généralement les approbations de marque, les validations juridiques, etc.
* **Ressource finale :** ressource qui a passé l’ensemble des   approbations/balisages de métadonnées et qui est prête à être utilisée par l’équipe élargie. Une telle ressource est stockée dans la gestion des ressources numériques (DAM) et est accessible à tous les utilisateurs (ou à tous les utilisateurs intéressés). Il peut être utilisé dans les canaux marketing ou par des équipes créatives pour créer des conceptions.

* **Mise à jour/modification mineure des ressources :** modification rapide et petite d’une ressource numérique. Cette opération est souvent effectuée en réponse à une demande de retouche ou de modification mineure, de révision ou d’approbation de fichier (par exemple, repositionnement, modification de la taille du texte, ajustement de la saturation/luminosité, couleur, etc.).
* **Mise à jour/modification majeure des ressources :** modification d’une ressource numérique qui nécessite un travail considérable et qui doit parfois être effectuée sur une plus longue période de temps. Celle-ci implique généralement plusieurs modifications. La ressource doit être enregistrée plusieurs fois lors de la mise à jour. En règle générale, les mises à jour majeures de la ressource entraînent le passage à une étape en cours.
* **DAM :** gestion des ressources numériques (en anglais, Digital Asset Management). Dans ce document, il est synonyme d’Adobe Experience Manager () Assets, sauf mention contraire.
* **Utilisateur créatif :** professionnel de la création, qui crée des ressources numériques à l’aide des applications et services Creative Cloud. Dans certains cas, un utilisateur créatif peut faire partie d’une équipe créative qui peut utiliser Creative Cloud, mais ne crée pas de ressources numériques (comme un directeur créatif ou un chef d’équipe créative).
* **Utilisateur de la gestion des ressources numériques :** utilisateur ordinaire d’un système de gestion des ressources numériques (DAM, Digital Asset Management). Selon l’organisation, l’utilisateur de gestion des ressources numériques (DAM) peut être un utilisateur marketing ou non, par exemple, un utilisateur métier, un bibliothécaire, un commercial, etc.

### Remarques concernant l’utilisation de l’intégration de Experience Manager et de Creative Cloud {#considerations-when-using-aem-and-creative-cloud-integration}

<!--incomplete and TBD: 

* DA2.0 best practices: See troubleshooting.md
* Stock integration: See ?
* AAL: See ?
* BP: See ?

-->

Il s’agit d’un bref résumé des bonnes pratiques pour l’intégration de Experience Manager et de Creative Cloud. Lisez la suite de ce document pour obtenir une description détaillée des points suivants.

* **Pour les utilisateurs créatifs, travaillant dans Photoshop, InDesign ou Illustrator :** Adobe Asset Link offre la meilleure expérience utilisateur, y compris une gestion propre du travail en cours sur les ressources extraites à partir du Experience Manager.
* **Pour simplifier l’accès aux ressources du bureau pour tout format de fichier ou application générique :**  utilisez l’appli de bureau Experience Manager
* **Déterminer pourquoi et quand stocker des ressources dans la gestion des ressources numériques (DAM) :** identifiez quelles mises à jour doivent être mises à la disposition de l’équipe élargie au sein de votre organisation.
* **Tenez compte du volume des ressources partagées :** si votre cas d’utilisation est la distribution des ressources, la gouvernance et la sécurité peuvent être les aspects les plus importants. Envisagez d’utiliser des outils conçus pour effectuer les tâches à grande échelle, comme Brand Portal.
* **Comprendre le cycle de vie des ressources :** comprenez la façon dont les ressources sont traitées par les différentes équipes au sein de votre organisation.
* **Gérer avec soin les enregistrements fréquents des ressources :** Adobe Asset Link s’en charge à votre place avec PS, IA, ID. Pour d’autres applications, ne conservez pas de tâches en cours dans le dossier mappé/partagé, sauf si vous avez besoin de toutes les modifications dans DAM.

### Accès aux ressources Adobe Stock à partir de ressources Experience Manager {#access-to-adobe-stock-assets-from-aem-assets}

[L’](/help/assets/aem-assets-adobe-stock.md) intégration Experience Manager et Adobe Stock permet aux utilisateurs Experience Manager de rechercher, de prévisualiser, d’acquérir sous licence et d’enregistrer des ressources d’Adobe Stock dans Experience Manager. Les ressources sous licence et enregistrées d’Adobe Stock possèdent des métadonnées Stock qui peuvent être utilisées pour les rechercher avec des filtres supplémentaires.

Quelques points importants à savoir concernant cette intégration :

* Lorsque des ressources du stock d’Adobe sont enregistrées dans Experience Manager, elles deviennent des ressources de Experience Manager standard, avec un fichier binaire enregistré dans le référentiel de Experience Manager. Certaines métadonnées liées à Adobe Stock sont enregistrées pour la ressource dans Experience Manager, sinon le processus d’ingestion ressemble à celui de tout autre fichier. Par exemple, si les balises dynamiques sont actives, les balises sont ajoutées à ces fichiers lors de l’enregistrement.
* La ressource enregistrée dans Experience Manager est une copie et non un lien vers Adobe Stock.

**Utilisation de ressources enregistrées à partir d’Adobe Stock dans Experience Manager dans Creative Cloud**. Cette intégration est indépendante d’Adobe Asset Link, mais cette fonction reconnaît ces ressources enregistrées depuis Stock de cette manière et affiche d’autres métadonnées et une icône Stock sur ces ressources dans l’interface utilisateur de l’extension Adobe Asset Link dans Photoshop, Illustrator et InDesign. Les fichiers sont disponibles pour la navigation, l’ouverture, etc., car il s’agit de ressources Experience Manager standard lorsqu’elles sont enregistrées dans Experience Manager.
Les utilisateurs créatifs qui travaillent dans des applications de Creative Cloud avec l’extension Adobe Asset Link sont présents, mais qui ont également accès à des ressources déjà sous licence d’Adobe Stock dans Experience Manager, peuvent également utiliser le panneau Bibliothèques Creative Cloud pour rechercher, prévisualiser et acquérir sous licence des ressources Adobe Stock.
Les ressources d’Adobe Stock sous licence et enregistrées dans Experience Manager sont disponibles pour les équipes élargies qui accèdent au déploiement des ressources Experience Manager, tandis que les équipes créatives qui achètent des licences pour les ressources d’Adobe Stock via le panneau Bibliothèques Creative Cloud les rendent disponibles uniquement par défaut dans leur compte de Creative Cloud.

## À propos du stockage de ressources dans un système de gestion des ressources numériques (DAM)  {#about-storing-assets-in-a-dam}

Pour établir un workflow efficace entre les équipes créatives et marketing/métier, et sélectionner les meilleures fonctionnalités de prise en charge, il est important de comprendre quand et pourquoi les ressources sont stockées dans la gestion des ressources numériques (DAM).

### Pourquoi les ressources sont-elles stockées dans la gestion des ressources numériques (DAM) ?  {#why-assets-are-stored-in-dam}

Le stockage des ressources dans la gestion des ressources numériques (DAM) permet d’en faciliter l’accès et de les retrouver plus aisément. Cela garantit que les ressources peuvent être exploitées par de nombreux utilisateurs au sein de votre organisation ou écosystème, qui comprend les partenaires, les clients, etc.

La plupart des organisations choisissent de stocker uniquement les ressources pertinentes pour les processus marketing/métier en aval (publication sur des canaux tels que le canal web via des sites Experience Manager ou d’autres canaux traités par Adobe Experience Cloud - Marketing Cloud, Advertising Cloud et mesurés par Analytics Cloud, satisfaction des besoins des utilisateurs/partenaires, etc.). En outre, les entreprises stockent les ressources qui peuvent être soumises à un processus de révision/approbation dans la gestion des ressources numériques (DAM). De cette manière, la gestion des ressources numériques (DAM) stocke principalement les ressources ayant de grandes chances d’être exploitées, en évitant de stocker les ressources inactives.

Le stockage des ressources est soumis à des considérations techniques et d’utilisation des ressources. La gestion des ressources numériques (DAM) fournit des services supplémentaires pour les ressources stockées, notamment l’extraction de métadonnées, le contrôle de version, la génération d’aperçus/de transcodage, la gestion des références et l’ajout d’informations de contrôle d’accès. Ces services utilisent davantage de temps et de ressources de votre infrastructure.

Souvent, le stockage de toutes les ressources et mises à jour n’est pas souhaitable. Par exemple, si les mises à jour de ressources spécifiques sont de mauvaise qualité et utilisent les ressources en excès, les ressources peuvent être stockées dans la gestion des ressources numériques (DAM).

#### Quand les ressources sont-elles stockées dans la gestion des ressources numériques (DAM) ?  {#when-assets-are-stored-in-dam}

Les équipes créatives (et les organisations) ne sont généralement pas intéressées par le stockage des ressources à chaque étape de leur cycle de vie. Par exemple, elles évitent de stocker des ressources dans les cas suivants :

* Si les ressources doivent être finalisées ou sont soumises à expérimentation
* Si les ressources ne passent pas le cycle de révision de l’équipe interne/créative
* L’équipe dispose de ressources plus pertinentes que celle en question pour présenter son travail à des équipes externes

En règle générale, les classes de ressources suivantes sont stockées dans la gestion des ressources numériques (DAM) :

* Les ressources ayant atteint une certaine maturité et que l’on estime prêtes à être partagées
* Les ressources qui ont été présélectionnées par l’équipe créative
* Les formats de ressources spécifiques qui sont utilisables ou demandés par le marketing, selon un contrat ou un accord spécifique (par exemple, des fichiers JPG convertis à partir de fichiers RAW, des TIFF/images à partir d’originaux PSD)

#### Quand les mises à jour de ressources sont-elles stockées dans la gestion des ressources numériques (DAM) ?  {#when-updates-to-assets-are-stored-in-dam}

En règle générale, seules les mises à jour des ressources pertinentes pour un large ensemble d’utilisateurs de la gestion des ressources numériques doivent être stockées dans la gestion des ressources numériques (DAM). Cela garantit que les utilisateurs (marketing et fonctions similaires) voient uniquement les versions appropriées dans la chronologie des ressources de la gestion des ressources numériques (DAM).

Généralement, il s’agit des modifications en rapport avec les principaux jalons dans le cycle de vie des ressources. Par exemple, la ressource initiale prête pour les spécialistes marketing ou une mise à jour officielle basée sur une demande/révision fournie par l’équipe créative doit être enregistrée et versionnée dans la gestion des ressources numériques (DAM).

Il peut s’agir, par exemple, d’une mise à jour de l’équipe créative pour révision par l’équipe marketing après une demande de modification de la ressource existante dans la gestion des ressources numériques (DAM). Elle doit être stockée et versionnée dans la gestion des ressources numériques (DAM) à des fins de référence ou pour revenir à la version précédente.

Voici quelques exemples de mises à jour qui ne sont généralement pas pertinentes :

* Les premières versions des ressources transférées avant qu’elles ne soient prêtes pour révision par le marketing
* Les modifications fréquentes de la ressource par l’équipe créative pendant la phase de travail en cours et avant que l’équipe créative ne décide que la ressource est prête

### Accès des utilisateurs à la gestion des ressources numériques (DAM)  {#user-access-to-dam}

Experience Manager Assets prend en charge deux types d’utilisateurs en fonction de leur accès au déploiement de Experience Manager Assets. En règle générale, les utilisateurs à l’intérieur du réseau d’entreprise (pare-feu) ont un accès direct à la gestion des ressources numériques (DAM). Les autres utilisateurs à l’extérieur du réseau d’entreprise n’auront pas d’accès direct. Le type d’utilisateur détermine les intégrations qui peuvent être utilisées du point de vue technique.

#### Utilisateurs créatifs avec un accès direct à la gestion des actifs numériques {#creative-users-with-direct-access-to-dam}

En règle générale, les équipes créatives internes ou les agences/créatifs professionnels  Les ressources intégrées au réseau interne ont accès à l’instance DAM, y compris la connexion au Experience Manager. L’infrastructure de Experience Manager et réseau peut être mise en place pour permettre un accès direct à des tiers externes (généralement des organisations de confiance comme des agences travaillant pour un client), pour avoir accès à un Experience Manager via un réseau, par exemple par le biais d’une liste autorisée VPN ou IP.

Dans ce cas, Adobe Asset Link ou l’appli de bureau Experience Manager permet d’accéder facilement aux ressources finales/approuvées et d’enregistrer les ressources prêtes pour les créatifs dans la gestion des ressources numériques.

#### Utilisateurs créatifs sans accès à la gestion des ressources numériques (DAM)  {#creative-users-without-access-to-dam}

Les agences externes et les indépendants sans accès direct à l’instance de la gestion des ressources numériques peuvent avoir besoin de l’accès aux ressources approuvées ou souhaiter ajouter leurs nouvelles créations dans la gestion des ressources numériques (DAM).

Utilisez les stratégies suivantes pour fournir un accès aux ressources finales/approuvées :

* Utilisez l’application de bureau si Asset Link ne fonctionne pas.
* Utilisez [Experience Manager Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) pour distribuer les ressources en toute sécurité aux partenaires externes.
* Utilisez une implémentation personnalisée d’un portail de distribution et de source basé sur [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/)
* Utilisez la configuration du contrôle d’accès dans l’infrastructure réseau Experience Manager et nécessaire (par exemple, les listes autorisées d’adresses IP et VPN) pour permettre à des tiers externes d’accéder à une zone de contenu dédiée dans la gestion des ressources numériques. Ils peuvent utiliser l’interface utilisateur web de Experience Manager pour obtenir des ressources et charger du nouveau contenu dans la gestion des ressources numériques.

#### Travail en cours sur les ressources du Experience Manager {#work-in-progress-on-assets-from-aem}

Comme indiqué dans ce document, il est recommandé d’effectuer des mises à jour majeures sur les ressources, parfois appelées travaux en cours, sans que toutes les modifications enregistrées dans le fichier local soient également chargées dans Experience Manager en tant que modifications. Cela accélère le travail d’un utilisateur sur poste de travail, limite la bande passante réseau utilisée et maintient le calendrier des ressources ciblé sur les mises à jour majeures et contrôlées.

Adobe Asset Link est adapté à cas d’utilisation :

* Lorsque les utilisateurs de Photoshop, InDesign ou Illustrator souhaitent modifier un fichier, ils effectuent une opération d’extraction sur la ressource donnée.
* La ressource est téléchargée en arrière-plan, placée dans le compte de Creative Cloud des utilisateurs synchronisé sur le disque par l’appli de bureau Creative Cloud, et l’indicateur d’extraction est activé sur Experience Manager sur la ressource afin de minimiser les conflits de modification.
* À ce stade, l’utilisateur utilise un fichier stocké localement dans l’emplacement synchronisé et peut continuer à travailler et à enregistrer les modifications nécessaires selon la fréquence nécessaire.
* De plus, comme la ressource figure dans le compte Creative Cloud, elle est également disponible sur d’autres appareils appartenant à l’utilisateur (par exemple, elle peut être ouverte ou modifiée dans une application mobile Creative Cloud dédiée) et peut être partagée avec d’autres utilisateurs Creative Cloud à des fins de collaboration.
* Lorsque l’utilisateur créatif a terminé d’apporter des modifications, il peut effectuer une opération d’archivage sur ce fichier dans son application Creative Cloud, en fournissant un commentaire facultatif. La ressource correspondante dans Experience Manager est versionnée et mise à jour vers avec le nouveau fichier binaire. Les utilisateurs de Experience Manager tels que les marketeurs ou les utilisateurs de la plate-forme de gestion des actifs numériques ont accès aux modifications majeures de ressources, ou jalons, via l’interface utilisateur de chronologie des ressources de Experience Manager.

L’appli de bureau Experience Manager fournit un partage réseau pour les ressources ouvertes dans l’application native. Par défaut, toutes les modifications effectuées localement sont automatiquement chargées vers Experience Manager après un bref moment. Avec une telle configuration, de fréquents enregistrements pendant la phase de travail en cours seraient tous transférés dans Experience Manager et versionnés, ce qui créerait un grand trafic réseau et des défis d’évolutivité potentiels - sans parler des versions inutiles en Experience Manager.

L’approche recommandée consiste à utiliser une option dans l’appli de bureau Experience Manager pour désactiver les mises à jour automatisées et charger manuellement les modifications apportées aux ressources dans Experience Manager, en exploitant l’action de chargement des modifications dans l’interface utilisateur État des ressources de l’application.

#### Chargement en masse dans DAM {#bulk-upload-to-dam}

Dans certains cas, il est possible que vous deviez charger simultanément un plus grand nombre de fichiers dans la gestion des ressources numériques (DAM), par exemple :

* Chargement des résultats de  séances photo ou de projets de plus grande envergure
* Chargement de ressources fournies par les agences de création
* Transfert de ressources sélectionnées à partir d’un plus grand ensemble si la sélection est effectuée en dehors de la gestion des ressources numériques (DAM)

Notez que cette description fait référence aux chargements de fichiers du point de vue des opérations (par exemple, chaque semaine ou à chaque   séance photo), comme composante normale du workflow de l’utilisateur de bureau. Les migrations de ressources de grande taille ne sont pas abordées ici.

Vous pouvez utiliser les fonctionnalités de transfert suivantes :

* Pour charger des dossiers hiérarchiques/volumineux en bloc, utilisez l’appli de bureau Experience Manager qui fournit la fonctionnalité [de chargement de dossiers](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#bulk-upload-assets). Vous pouvez également transférer des structures de dossiers hiérarchiques. Les ressources sont transférées en arrière-plan et, par conséquent, le transfert n’est pas associé à une session du navigateur web.
* Pour charger quelques fichiers à partir d’un seul dossier, faites-les glisser directement vers l’interface web ou utilisez l’option Créer de l’interface web Ressources du Experience Manager.
* En fonction des besoins de votre entreprise, vous pouvez également utiliser un outil de chargement personnalisé.

#### Gestion directe des ressources numériques depuis l’ordinateur de bureau {#managing-digital-assets-directly-from-desktop}

Si vous utilisez des partages de fichiers réseau pour gérer des ressources numériques, le simple utilisation du partage réseau mappé par l’appli de bureau Experience Manager peut être considéré comme une alternative pratique. Lors de la transition à partir des partages de fichiers réseau, l’interface web de Experience Manager propose un large éventail de fonctionnalités de gestion des ressources numériques qui vont bien au-delà de ce qui est possible sur un partage réseau (recherche, collections, métadonnées, collaboration, aperçus, etc.). L’appli de bureau Experience Manager fournit un lien pratique pour connecter le référentiel DAM côté serveur au travail sur l’ordinateur de bureau.

Évitez d’utiliser l’appli de bureau Experience Manager pour gérer les ressources directement dans le partage réseau des ressources du Experience Manager. Par exemple, évitez d’utiliser l’appli de bureau Experience Manager pour déplacer/copier plusieurs fichiers. Utilisez plutôt l’interface utilisateur web de Ressources du Experience Manager pour faire glisser des dossiers du Finder/de l’Explorateur vers le partage réseau ou utilisez la fonction de téléchargement de dossiers de Ressources du Experience Manager.
