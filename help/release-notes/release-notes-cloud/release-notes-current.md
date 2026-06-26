---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
nudge: please
source-git-commit: 50a64c8968182ac1fb5a57082da991c9efd4dc46
workflow-type: tm+mt
source-wordcount: '3855'
ht-degree: 17%

---

# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour techniques de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes telles que 2024 ou 2025.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Pour recevoir chaque mois une notification par e-mail concernant des informations sur les notes de mise à jour d’Experience Cloud, abonnez-vous aux [Mises à jour de produits prioritaires d’Adobe](https://www.adobe.com/subscription/priority-product-update.html).

## Date de publication {#release-date}

La date de publication de la version actuelle (2026.6.0) de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le 25 juin 2026. La prochaine version des fonctionnalités (2026.7.0) est prévue pour le 30 juillet 2026.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the May 2026 Release Overview video for a summary of the features added in the 2026.5.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3491492/?captions=fre_fr&quality=12)

-->

## Programmes AEM Beta {#aem-beta-programs}

Les programmes bêta Adobe Experience Manager (AEM) permettent aux clients d’accéder aux fonctionnalités et au code de version préliminaire, de faire part de leurs commentaires et de guider l’avenir d’AEM.

>[!IMPORTANT]
>
>Les versions de Beta peuvent contenir des défauts et sont fournies « EN L’ÉTAT » sans garantie d’aucune sorte. Adobe n’a aucune obligation de tenir à jour, corriger, mettre à jour, modifier, remplacer ou prendre en charge (par le biais des services d’assistance Adobe ou d’une autre manière) les versions bêta. Adobe conseille aux clients d’être prudent et de ne pas se fier au bon fonctionnement ou aux performances des versions bêta, ni à la documentation ou aux documents d’accompagnement. Les fonctionnalités et API de la version bêta peuvent être modifiées sans préavis. Par conséquent, toute utilisation des versions bêta s’effectue entièrement aux risques et périls du client.

**Avantages de la participation**

L’accès anticipé aux fonctionnalités développées par Adobe permet aux clients et aux partenaires de faire part de leurs commentaires et de façonner le développement des produits. Cela les aide également à se préparer à adopter de nouvelles fonctionnalités avant leur disponibilité générale.

**Programmes bêta actuels**

Les sections suivantes répertorient les programmes bêta actifs.

### Agents dans AEM {#agents-in-aem}

Si vous souhaitez explorer les nouvelles et puissantes fonctionnalités d’AEM dans les domaines de la production, de la gouvernance, de l’optimisation, de la découverte et du développement, [découvrez comment y accéder ici.](/help/ai-in-aem/agents/overview.md)

<!--
### Agents in AEM (Explorer program) {#agents-in-aem-beta-program}

Gain early access to powerful, new AEM agentic capabilities across production, governance, optimization, discovery, and development. Your feedback directly shapes Adobe's roadmap and final features. See [Overview of Agents in AEM](/help/ai-in-aem/agents/overview.md) to learn more.

This program typically lasts 4-6 weeks, but can be tailored to be flexible around your ability to actively participate. 

To opt in to participate in this program, email [aemagentsteam@adobe.com](mailto:aemagentsteam@adobe.com) and include the following details to the extent possible:

* Names and Adobe ID's of team members who will actively use agents.
* List Specific agents that you or your team will want to use. Or simply say "All Agents."

Customers selected for participation will be notified directly by Adobe. Participation is subject to eligibility considerations, including customer licensing and limited program capacity. While not all requests can be accommodated initially, additional customers may be considered in future beta waves.
-->

### AEM Foundation (programmes Beta) {#aem-foundation-beta-programs}

Voir [Programmes bêta AEM Foundation](#foundation-early-adopter).

### Cloud Manager (programmes Beta) {#cloud-manager-beta-programs}

Voir [Programmes bêta &#x200B;](/help/implementing/cloud-manager/release-notes/current.md).

### AEM Assets (programmes Beta) {#aem-assets-beta-programs}

Voir [Programmes bêta &#x200B;](#assets-beta-program-features).

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Fragments de contenu visuels {#visual-content-fragments}

AEM prend désormais en charge les [fragments de contenu visuels](/help/sites-cloud/administering/content-fragments/visual-content-fragments.md), qui effectuent le rendu de la sortie de fragment de contenu en tant qu’expériences HTML formatées à l’aide de modèles HTML joints. Cela permet aux auteurs de contenu de prévisualiser et de valider le contenu structuré sous sa forme visuelle finale avant publication, et de fournir des expériences modulaires de manière cohérente sur l’ensemble des canaux (web, e-mail et Edge Delivery Services, par exemple). Un modèle générique intégré est disponible pour l’assurance qualité de base sans nécessiter de modèle personnalisé.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**Modifier des fichiers PSD dans l’éditeur Adobe Express intégré**

Vous pouvez désormais modifier des fichiers PSD en plus des formats JPEG et PNG dans l’éditeur incorporé d’Adobe Express à partir de la vue Assets. Cette amélioration permet aux équipes créatives et marketing de travailler avec des fichiers de conception superposés sans quitter AEM Assets, en rationalisant les mises à jour de contenu et en réduisant la nécessité de basculer entre les applications. La prise en charge de PSD permet d’accélérer les workflows de création de contenu tout en préservant la flexibilité des ressources de conception source.

**Importation de ressources Adobe Illustrator et Adobe InDesign d’AEM Assets dans Adobe Express**

Adobe Express prend désormais en charge l’importation de fichiers Adobe Illustrator (.ai) et Adobe InDesign (.indd) à partir d’AEM Assets. Cette fonctionnalité permet aux équipes créatives et marketing d’accéder aux ressources de conception approuvées et de les réutiliser plus facilement, ce qui accélère la création de contenu et permet d’assurer des expériences de marque cohérentes sur l’ensemble des canaux.


**Conserver la parenté des ressources entre Adobe Express et AEM Assets**

AEM Assets conserve désormais les informations de parenté pour les ressources créées dans Adobe Express à l’aide de ressources provenant d’AEM. Cette fonctionnalité enregistre les relations entre les ressources sources et le contenu résultant, ce qui permet aux entreprises de suivre la manière dont les ressources approuvées sont réutilisées dans les workflows de création.

En conservant les métadonnées de lignage des ressources, les équipes peuvent améliorer la gouvernance, la conformité et la transparence du supply chain de contenu. Il permet également aux spécialistes marketing et aux administrateurs de contenu de mieux comprendre la réutilisation des ressources, de prendre en charge les initiatives de gestion des droits et de suivre l’origine des ressources utilisées dans le contenu publié.

>[!IMPORTANT]
>
>Cette fonctionnalité est disponible en tant que fonctionnalité à disponibilité limitée. Vous pouvez [créer et envoyer un dossier d’assistance client Adobe](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html) pour l’activer pour votre déploiement.

**Intégration d’AEM avec les métadonnées de campagne Workfront planning standard**

Lorsqu’AEM Assets est intégré à Workfront Planning, les champs de métadonnées de campagne, notamment Campagne, Région, Canal, Persona et Produit, sont désormais disponibles dans les propriétés de la ressource sous un onglet Campagne en lecture seule dédié.

L’intégration permet aux utilisateurs de découvrir et de rechercher rapidement des ressources en fonction des attributs de campagne. Cette amélioration améliore la recherche des ressources, rationalise les workflows de gestion de contenu et aide les équipes à localiser plus efficacement les ressources appropriées pour des initiatives marketing spécifiques.

>[!IMPORTANT]
>
>Cette fonctionnalité est disponible en tant que fonctionnalité à disponibilité limitée. Vous pouvez [créer et envoyer un dossier d’assistance client Adobe](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html) pour l’activer pour votre déploiement.


### Nouvelles fonctionnalités de Dynamic Media avec OpenAPI {#new-features-dynamic-media-openapi}

**Sous-titres vidéo générés par l’IA**

Les sous-titres vidéo générés par l’IA dans Dynamic Media avec des fonctionnalités OpenAPI utilisent l’intelligence artificielle pour générer automatiquement des sous-titres pour le contenu vidéo. Cette fonctionnalité est conçue pour améliorer l’accessibilité et l’expérience d’utilisation en fournissant des sous-titres précis en temps réel. L’IA analyse la piste audio de la vidéo pour transcrire la parole et créer des sous-titres, qui peuvent être modifiés pour plus de précision ou de personnalisation. Ces sous-titres permettent de répondre aux exigences d’accessibilité et d’améliorer l’engagement vidéo pour les audiences qui dépendent d’une prise en charge vidéo basée sur le texte ou qui préfèrent ce système.

>[!IMPORTANT]
>
>Cette fonctionnalité est disponible en tant que fonctionnalité à disponibilité limitée. Vous pouvez [créer et envoyer un dossier d’assistance client Adobe](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html) pour l’activer pour votre déploiement.

**Transcriptions vidéo intégrées pour une meilleure accessibilité et un meilleur référencement**

Le composant Dynamic Media incorpore désormais des transcriptions pour les vidéos afin d’améliorer l’accessibilité pour vos clients. Il s’agit de transcriptions générées côté serveur (SSR) qui augmentent directement la visibilité de l’optimisation pour les moteurs de recherche et de la gestion du cycle de vie des vidéos. Il intègre également un VideoObject conforme [réf https://schema.org/VideoObject] qui aide les moteurs de recherche et les outils LLM à reconnaître les vidéos dans votre page.

>[!IMPORTANT]
>
>Cette fonctionnalité est disponible en tant que fonctionnalité à disponibilité limitée. Vous pouvez [créer et envoyer un dossier d’assistance client Adobe](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html) pour l’activer pour votre déploiement.

**Miniatures personnalisées pour les vidéos**

Dynamic Media avec des fonctionnalités OpenAPI permet désormais de charger des miniatures personnalisées pour les ressources vidéo. En remplaçant les miniatures générées automatiquement par des images de marque ou personnalisées, les entreprises peuvent améliorer la présentation du contenu, faciliter la découverte des ressources et créer une expérience de visionnage plus attrayante.



## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités d’AEM Forms

#### Éditeur de communication interactive

L’éditeur de communication interactive et l’interface utilisateur associée incluent de nouvelles fonctionnalités de collaboration, de mise en page et de modification des associés pour aider les auteurs à concevoir plus rapidement et permettre aux associés d’établir des communications client avec plus de précision.

L’éditeur de communication interactive (IC) est désormais disponible dans AEM Forms as a Cloud Service. Il s’agit d’une solution de navigateur permettant la création, la gestion et la diffusion de correspondances interactives pilotées par les données, telles que la correspondance commerciale, les documents, les déclarations, les avis de prestations, les e-mails marketing, les factures et les kits de bienvenue.

![Éditeur de communication interactive](/help/forms/assets/ic-editor.png)

* **Éditeur basé sur le cloud** : contrairement à AEM Forms Desktop Designer qui ne peut être installé que sur des machines Windows, l’éditeur de communications interactives s’exécute dans n’importe quel navigateur moderne sans qu’une installation ne soit nécessaire. Cette approche basée sur le cloud élimine les problèmes d’installation, offre une accessibilité sur plusieurs plateformes et permet la collaboration depuis n’importe quel emplacement avec un accès Internet. Pour plus d’informations, voir [Prise en main de l’éditeur IC](/help/forms/interactive-communication/getting-started.md).

* **Composants et propriétés** : créez des communications à l’aide d’une bibliothèque de composants par glisser-déposer — champs de texte, tableaux, images, codes à barres, sous-formulaires, etc. Configurez la disposition, la typographie, les marges et l’apparence via le panneau Propriétés. Pour plus d’informations, voir [Présentation de l’éditeur de communication interactive](/help/forms/interactive-communication/introduction.md).

* **Liaison de données** : connectez les composants aux modèles de données de formulaire (FDM) à l’aide du mappage visuel pour générer une sortie personnalisée basée sur les données. Pour plus d’informations, voir [Liaison de données dans l’éditeur de communication interactive](/help/forms/interactive-communication/configure-data-binding.md).

* **Éditeur de règles** : créez des actions dynamiques basées sur les données directement dans vos documents à l’aide d’une interface intuitive de type pointer-cliquer. Définissez facilement une logique conditionnelle, automatisez les workflows et personnalisez le contenu sans écrire de code. Pour plus d’informations, voir [Création de règles dans l’éditeur de communication interactive](/help/forms/interactive-communication/use-the-rule-editor.md).

* **Modèles et fragments de document** : créez des modèles réutilisables et des blocs de contenu modulaires (en-têtes, pieds de page, clauses de non-responsabilité) pour une cohérence et une efficacité optimales dans plusieurs communications. Pour plus d’informations, voir [Créer un modèle](/help/forms/interactive-communication/create-interactive-communication-template.md) et [Créer un fragment](/help/forms/interactive-communication/create-interactive-communication-fragment.md).

* **Verrouillage de modèle** : verrouillez le contenu et les éléments de disposition dans les modèles pour maintenir l’intégrité de la marque et empêcher toute modification non autorisée. Pour plus d’informations, voir [&#x200B; Verrouillage de modèle &#x200B;](/help/forms/interactive-communication/enable-template-lock.md).

* **Aperçu PDF** : prévisualisez une communication interactive sans données, sans fichiers JSON locaux ou sans modèles de données pour des tests flexibles pilotés par les données. Pour plus d&#39;informations, voir Aperçu de [&#128279;](/help/forms/interactive-communication/generate-pdf-preview.md).

* **Polices personnalisées** : incorporez des polices personnalisées ou approuvées par l’organisation pour garantir un rendu PDF cohérent de la marque sur tous les appareils. Pour plus d’informations, voir [Ajouter des polices personnalisées](/help/forms/interactive-communication/add-custom-fonts.md).

* **Importer et exporter** : migrez et réutilisez facilement la communication interactive avec ses fragments et modèles de données dans les environnements. Pour plus d’informations, voir [Importer et exporter](/help/forms/interactive-communication/import-and-export-the-interactive-communication.md).

* **Débordement de contenu** : l’option « Autoriser les sauts de page dans le contenu » pour les dispositions fluides permet une modification fluide de plusieurs pages et une meilleure gestion du texte pour les documents complexes. Pour plus d’informations, voir [Gestion des débordements de contenu](/help/forms/interactive-communication/handle-content-overflow.md).

* **Modification de fichiers XDP** : modifiez les fichiers XDP dans un navigateur au lieu de Forms Designer qui s’exécute uniquement sur l’ordinateur de bureau Microsoft Windows. Pour plus d’informations, voir [Prise en charge de l’édition XDP](/help/forms/interactive-communication/support-xdp-editing.md).

* **Interface utilisateur d’association** : interface d’exécution simplifiée permettant aux collaborateurs en contact avec la clientèle de saisir des données et de générer des communications personnalisées en temps réel. Appelez l’interface utilisateur associée directement sur les instances de publication pour simplifier l’intégration et accélérer le déploiement dans les environnements. Pour plus d’informations, consultez [Présentation de l’interface utilisateur associée](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md), [Activation et configuration de l’interface utilisateur associée](/help/forms/interactive-communication/enable-configure-associate-ui.md) et [Intégration de l’interface utilisateur associée](/help/forms/interactive-communication/invoke-associate-ui.md).

* **Numérotation dynamique de page** : affichez automatiquement la mention « Numéro de page de ## » sur les gabarits de page pour une pagination claire et cohérente dans les documents de plusieurs pages. Pour plus d’informations, voir [Numérotation dynamique de page](/help/forms/interactive-communication/implement-dynamic-page-numbering.md).

* **Contrôle de version et commentaires dans l’éditeur de communication interactive** : l’éditeur de communication interactive prend désormais en charge le contrôle de version et les commentaires afin que les auteurs puissent enregistrer des versions étiquetées, capturer les commentaires des réviseurs, revenir à des états antérieurs et gérer un journal d’audit tout au long du cycle de vie du contenu. Pour plus d’informations, voir [Contrôle de version et commentaires dans l’éditeur de communication interactive](/help/forms/interactive-communication/versioning-and-commenting-in-interactive-communication-editor.md).

* **Réviser et annoter une communication interactive** : les réviseurs et réviseuses peuvent désormais annoter des communications interactives dans une vue dédiée en lecture seule, épingler des commentaires à des composants spécifiques sur la zone de travail et partager leurs commentaires à un seul endroit sans modifier la conception. Les auteurs peuvent suivre et résoudre les annotations directement dans l’éditeur. Pour plus d’informations, voir [Vérifier et annoter une communication interactive](/help/forms/interactive-communication/howto/review-and-annotate-interactive-communication.md).

* **Comparer les versions de la communication interactive** : vous pouvez désormais comparer côte à côte deux versions enregistrées d’une communication interactive en tant qu’aperçus PDF pour passer en revue les modifications de disposition et de contenu statique avant la publication. Pour plus d’informations, voir [Comparer les versions de la communication interactive](/help/forms/interactive-communication/howto/compare-interactive-communication-versions.md).

* **Fusion et division des cellules de tableau** : l’éditeur de communication interactive prend désormais en charge la fusion de cellules de tableau adjacentes et le fractionnement des cellules fusionnées en colonnes individuelles, ce qui permet d’étendre les en-têtes, les lignes de résumé et des dispositions de tableau plus flexibles. Pour plus d&#39;informations, voir [Fusionner et fractionner des cellules de tableau](/help/forms/interactive-communication/howto/merge-and-split-table-cells.md).

* **Déplacer un composant vers la page de Principal** : vous pouvez désormais déplacer un composant d’une page de conception vers le gabarit de page en une seule action afin qu’il apparaisse de manière cohérente sur chaque page d’une communication interactive sans le recréer. Pour plus d’informations, voir [Déplacer un composant vers la page de Principal &#x200B;](/help/forms/interactive-communication/howto/move-component-to-master-page.md).

* **Configurer les options de liste déroulante pour l’IU associée** : les champs de liste déroulante de l’IU associée utilisent désormais un modèle **Liaison d’options**. Les auteurs configurent **Liaison à partir des données** pour les listes d’options dynamiques ou les options statiques manuelles afin que les associés voient les choix corrects et la valeur présélectionnée. La **liaison de données** n’est pas prise en charge pour les champs de liste déroulante. Pour plus d’informations, voir [Configurer les options de liste déroulante pour l’interface utilisateur associée](/help/forms/interactive-communication/associateui/configure-dropdown-options-binding.md).

* **Configurer les variables liées et non liées pour l’interface utilisateur associée** : les variables liées et non liées dans les composants **Texte** peuvent désormais être configurées pour l’interface utilisateur associée. Les auteurs choisissent si les associés modifient le bloc de texte entier en ligne dans l’aperçu du document ou saisissent des valeurs pour des variables individuelles dans le panneau de saisie de données. Les noms de variables en double propagent les valeurs sur toutes les occurrences correspondantes dans l’aperçu. Pour plus d’informations, voir [Configurer des variables liées et non liées pour l’interface utilisateur associée](/help/forms/interactive-communication/associateui/configure-bound-unbound-variables-associate-ui.md).

## Fonctionnalités des premiers utilisateurs

### Document d’enregistrement pour les formulaires incorporés dans AEM Sites

Les auteurs peuvent désormais configurer et générer un document d’enregistrement (PDF d’envoi) pour les composants principaux de Forms adaptatif incorporés dans des pages AEM Sites. Les paramètres de document d’enregistrement, notamment la génération automatique, les modèles XDP personnalisés et le branding, sont disponibles directement à partir du **conteneur de formulaires adaptatifs** dans l’éditeur de page Sites. [En savoir plus](/help/forms/generate-document-of-record-core-components.md#configure-document-of-record-for-forms-embedded-in-aem-sites).

### Modèles XDP personnalisés spécifiques aux paramètres régionaux pour les documents d’enregistrement

Lorsque vous associez un modèle XDP personnalisé pour le document d’enregistrement, vous pouvez fournir des versions spécifiques aux paramètres régionaux dans le même dossier à l’aide de la convention de `basename.<locale>.xdp` (par exemple, `a.xdp` et `a.fr.xdp`). AEM Forms sélectionne automatiquement le modèle correspondant aux paramètres régionaux du formulaire lors de la génération de la PDF d’envoi, avec solution de secours au modèle par défaut. [En savoir plus](/help/forms/generate-document-of-record-core-components.md#locale-specific-custom-xdp-templates-for-document-of-record).

### Expiration du contrat Adobe Sign

Vous pouvez définir la durée pendant laquelle les destinataires doivent terminer la signature en indiquant **Expiration du document (jours)** dans la section **Signature électronique** d’un formulaire adaptatif. La valeur est envoyée à Adobe Sign en tant que `daysUntilSigningDeadline`. Si rien n’est indiqué, l’accord n’expire pas. [En savoir plus](/help/forms/working-with-adobe-sign.md#set-document-expiration-for-an-adobe-sign-agreement).

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation Nouvelles fonctionnalités {#foundation-new}

#### Interface de l’IA dédiée à la conversation pour les questions sur Cloud Manager {#devagent-cloudmanager}

L’agent de développement se développe pour gérer les questions liées à Cloud Manager via la [tâche Cloud Manager](/help/ai-in-aem/agents/brand-experience/development/development.md#cloud-manager-job). Dans l’assistant AI, récupérez des informations sur les programmes, les environnements et les pipelines (par exemple, le statut d’exécution). Trouvez rapidement des liens vers les journaux d’erreurs, les journaux d’accès et les journaux de build.

#### Améliorations apportées au travail de l’agent de dépannage du pipeline {#devagent-pipeline-troubleshooting}

La [&#x200B; tâche de dépannage du pipeline de l’agent de développement](/help/ai-in-aem/agents/brand-experience/development/development.md#cloud-manager-pipeline-troubleshooting) aide les développeurs à diagnostiquer et à résoudre les problèmes liés aux déploiements d’AEM as a Cloud Service. Les nouvelles fonctionnalités incluent :

* Prise en charge du pipeline de configuration de niveau web - En plus de la prise en charge des pipelines de pile complète (déploiement et qualité du code), l’agent de développement prend désormais en charge la résolution des problèmes liés au **pipeline de configuration de niveau web**

* Widget Experience Home pour les pipelines en échec - Le rôle Admin et IT verra un [nouveau widget](/help/ai-in-aem/agents/brand-experience/development/development.md#troubleshoot-from-experience-home) mettant en évidence les échecs de pipeline. Un bouton cliquable lance la tâche de dépannage du pipeline dans l’assistant AI.

#### Gérer les heures calmes et mettre à jour les périodes libres avec l’assistant AI {#quiet-hours-ai}

Vous pouvez désormais afficher, créer et modifier des [heures creuses et mettre à jour les périodes libres](/help/ai-in-aem/agents/brand-experience/development/development.md#control-updates-job) directement via l’assistant AEM AI.
L’avantage clé est la réduction des erreurs de planification. Lorsque vous effectuez une demande, l’assistant vous guide tout au long des étapes possibles et signale les limites qui s’appliquent, telles que la limite de trois périodes, l’intervalle obligatoire d’une semaine entre les périodes et les fenêtres d’exclusion de la maintenance planifiée que vous ne pouvez pas planifier. Ainsi, au lieu de découvrir une contrainte après une configuration ayant échoué, les propriétaires d’entreprise et les responsables de déploiement sont dirigés vers un planning valide dans la même conversation. Cela permet de protéger les fenêtres d’activité critiques contre les mises à jour de maintenance automatique tout en réduisant les allers-retours et les erreurs de configuration.

### [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation Avis importants {#foundation-notices}

#### Erreurs enrichies d’authentification IMS {#ims-auth-rich-errors}

Pour faciliter le dépannage des intégrations IMS, `imsauth` a ajouté la prise en charge des *erreurs riches*.

Au lieu de renvoyer uniquement un code d’état HTTP, ces erreurs fournissent un contexte supplémentaire pour aider à diagnostiquer et à résoudre les problèmes qui peuvent bloquer l’authentification et l’accès.

#### Obsolescence des API Java {#java-api-deprecation}

Il est essentiel de supprimer l’utilisation des API obsolètes.

Depuis le **14 avril 2026**, les pipelines Cloud Manager qui contiennent du code à l’aide d’API ciblant la suppression du 2/26/2026 **échouent lors de l’étape Qualité du code**. Les déploiements seront bloqués jusqu’à ce que l’utilisation obsolète de l’API soit supprimée. *Cela peut vous empêcher de publier des mises à jour urgentes et peut avoir un impact sur vos opérations commerciales.*

À compter du **23 juillet 2026**, les environnements qui utilisent toujours ces API obsolètes **ne recevront pas de mises à jour de versions Adobe critiques** et ne seront pas soumis aux engagements standard d’Adobe en matière de performances et de disponibilité. Par conséquent, vous ne recevrez pas de nouvelles fonctionnalités ou de nouveaux correctifs, la stabilité et la disponibilité des applications peuvent être affectées négativement, et l&#39;exposition aux risques de sécurité peut encore augmenter.

Pour plus d’informations, consultez l’[article sur l’obsolescence](/help/release-notes/deprecated-removed-features.md#aem-apis), mais pour plus de commodité, ces API sont répertoriées ci-dessous :

+++ Développer pour afficher les éléments obsolètes de l’API Java

* `org.apache.sling.commons.auth`
* `org.apache.felix.webconsole`
* `org.eclipse.jetty`
* `com.mongodb`
* `org.apache.abdera`
* `org.apache.felix.http.whiteboard`
* `org.apache.cocoon.xml`
* `ch.qos.logback`
* `org.slf4j.spi`
* `org.slf4j.event`
* `org.apache.log4j`
* `com.google.common`
* `com.drew`
* `org.apache.jackrabbit.oak.plugins.memory`

+++

#### Le serveur MCP local Dispatcher fait partie d’AEM SDK {#local-dispatcher-mcp}

Le serveur MCP local Dispatcher est désormais inclus dans **AEM SDK** dans le [portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?lang=fr), compressé dans le fichier zip des outils AEM Dispatcher. Auparavant, le serveur MCP local Dispatcher était inclus dans une liste bêta distincte des outils AEM Dispatcher.

Le serveur MCP local Dispatcher permet aux outils d’IA de valider la configuration Dispatcher et Apache HTTPD, de suivre la gestion des requêtes et d’inspecter le comportement du cache par rapport à une instance Dispatcher s’exécutant localement dans Docker.

#### Préparation à Java 25 : calendrier de mise à niveau de l’exécution d’AEM Cloud Service

Java 25 est la prochaine version d’assistance à long terme (LTS) après Java 21, offrant des améliorations en termes de performances, de productivité des développeurs et de sécurité :

&#x200B;- **Performances** : la réduction de l’encombrement de la mémoire, une récupération de l’espace mémoire plus efficace et un préchauffage JVM plus rapide bénéficient aux déploiements natifs dans le cloud.
&#x200B;- **Productivité du développeur** — Une initialisation plus épurée de l’objet, une correspondance plus expressive des modèles et une gestion simplifiée des tâches simultanées réduisent la complexité et améliorent la clarté du code.
&#x200B;- **Sécurité** — API de dérivation de clé cryptographique modernisée pour simplifier les workflows de sécurité courants.

Pour aider les entreprises à planifier les tests et la validation avant la mise à niveau de l’exécution Java 25 nécessaire, Adobe fournit les dates cibles suivantes. Toutes les mises à jour de cette chronologie seront communiquées via les notes de mise à jour.

| Période | Jalon |
|---|---|
| **Mi-Octobre 2026** | AEM Cloud Service SDK prend en charge l’exécution de Java 25. Le JDK Java 25 peut être téléchargé à partir du portail de distribution logicielle d’Adobe. |
| **Novembre 2026** | Nous recommandons aux clients d’activer éventuellement l’exécution Java 25 dans leurs environnements cloud pour valider le comportement. L’adoption précoce optimise le temps nécessaire pour faire apparaître et résoudre les problèmes. |
| **Février - Mai 2027** | Adobe migrera progressivement les environnements inférieurs (RDE, Dev) vers le runtime Java 25. Les clients doivent valider le comportement et signaler les problèmes inattendus, et sont encouragés à activer également les environnements d’évaluation et de production. Une restauration temporaire vers Java 21 est disponible lors de la résolution des problèmes. |
| **Juin 2027** | Tous les runtimes d’environnement (y compris d’évaluation et de production) migrent vers Java 25. L’exécution de Java 21 est désactivée. AEM Cloud Service SDK ne prend plus en charge Java 21. |

AEM Cloud Service continue à prendre en charge la compilation de code client avec Java 11, Java 17 et Java 21. Cependant, Adobe recommande de créer avec Java 25 (une fois disponible dans AEM) pour tirer pleinement parti des dernières fonctionnalités de langue et améliorations des performances.

### [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation Early Adopter Caractéristiques {#foundation-early-adopter}

#### Fonctions D’AEM Edge (Programme *Public Beta*) {#edge-functions}

[Fonctions d’AEM Edge](/help/implementing/developing/introduction/edge-functions.md) est désormais en version bêta publique. Vous pouvez donc l’essayer en libre-service sans contacter Adobe pour l’activer.

Cette fonctionnalité vous permet d’exécuter JavaScript au niveau de la couche CDN, ce qui rapproche le traitement des données de l’utilisateur final. Cela réduit la latence et permet d’obtenir des expériences réactives et dynamiques en périphérie. Il est disponible pour les projets Java Stack et Edge Delivery Services d’AEM Cloud Service, pour les clients AEM Sites.

Cas d’utilisation courants :

* Personnalisation du contenu en fonction de la géolocalisation, du type d’appareil ou des attributs d’utilisateur ou d’utilisatrice
* Fonctionnement en tant que middleware entre le réseau CDN et votre origine
* Remise en forme des réponses d’API tierces (et éventuellement agrégation de plusieurs réponses d’API) avant de les diffuser au navigateur
* Composition et diffusion de HTML rendu sur le serveur Edge à l’aide de contenu assemblé à partir de divers serveurs principaux

*En utilisant le Beta Fonctions d’AEM Edge, vous reconnaissez qu’il est toujours en développement et que vous ne devriez pas vous fier au bon fonctionnement de la technologie ou à la disponibilité des données. Cette fonctionnalité est fournie en l’état,
peut changer sans préavis et n’est pas couvert par les contrats de niveau de service de production.*

#### Instantanés pour les RDE (programme *Public Beta*) {#rde-snapshot-program}

Les instantanés des environnements de développement rapide (RDE) sont désormais en version bêta publique afin que vous puissiez les tester en libre-service sans contacter Adobe pour les activer.

Les RDE prennent désormais en charge une fonctionnalité [pour prendre un instantané](/help/implementing/developing/introduction/rapid-development-environments.md#snapshots) de l’état actuel du code et du contenu, qui peut être restaurée ultérieurement. Cela peut s’avérer utile lors de la synchronisation du code qui peut devoir être restauré à un état précédent ou, lorsqu’au cours du développement, il est nécessaire d’alterner entre plusieurs fonctionnalités différentes. Il est également possible de restaurer uniquement le contenu modifiable en tant que point de départ connu pour les tests.

*En utilisant le Beta d’instantanés du RDE, vous reconnaissez qu’il est toujours en cours de développement et que vous ne devez pas vous fier au bon fonctionnement de la technologie ou à la disponibilité des données. Bien que nous ayons largement testé cette fonctionnalité, il existe une petite possibilité que votre RDE devienne instable. Si cela se produit, une réinitialisation la restaurera à un état de fonctionnement.*

#### Dépannage de l’IA dédiée à la réplication (programme Beta) {#replication-ai-troubleshooting-beta}

À l’aide de l’assistant AI dans l’instance de création AEM et d’autres interfaces, vous pouvez résoudre les problèmes liés à la réplication, tels que les files d’attente bloquées. Pour rejoindre le programme Beta, envoyez un e-mail à l’adresse [aem-devagent@adobe.com](mailto:aem-devagent@adobe.com) pour décrire votre intérêt.

#### Déploiements en production Canary pour tester le code avant d’accepter le trafic réel (programme Beta) {#canary-beta}

Validez une build de production avec du trafic de test interne uniquement avant de l’exposer aux utilisateurs finaux. Déployez en production, acheminez uniquement le trafic Canary (à l’aide d’un en-tête spécial), surveillez le comportement, puis convertissez-le en trafic réel ou restaurez, sans affecter les clients et clientes.

Envoyez un e-mail à [aemcs-canary-deployments-beta@adobe.com](mailto:aemcs-canary-deployments-beta@adobe.com) pour demander l’accès et partager vos commentaires.

#### Évaluation du code AEM et correction automatique via l’agent IDE AI (programme Beta) {#ide-ai-aemcode-issues}

Les équipes Java-stack AEM Cloud Service utilisant le développement assisté par IA dans des outils tels que Cursor, Claude Code, Visual Studio et IntelliJ peuvent désormais aller plus loin. Une nouvelle [compétence de l’agent IDE d’évaluation du code](/help/ai-in-aem/local-development-with-ai-tools.md#use-the-code-assessment-skill) détecte et corrige automatiquement les problèmes directement dans votre base de code AEM, ce qui réduit les cycles de révision et permet de détecter les problèmes plus tôt dans le développement.

Les contrôles pris en charge sont les suivants :
* Remplacer les API obsolètes
* modernisation de l’injection de dépendance du modèle Sling
* Mise à jour des dépendances Maven obsolètes
* ajout de délais d’expiration manquants aux appels HTTP sortants
* limite de requêtes illimitées
* Planificateurs Sling
* les écouteurs de modification de ressource de la réplication.
* Gestion des événements JCR ou OSGi

Cette fonctionnalité est en version bêta. Faites un essai et partagez vos commentaires avec l’équipe sur [&#128279;](mailto:aemcs-ai-ide-tools-feedback@adobe.com).

#### Authentification Edge pour Edge Delivery Services (programme Beta) {#edge-authentication}

L’authentification Edge vous permet de restreindre l’accès aux pages Edge Delivery Services aux personnes qui se sont authentifiées auprès de votre fournisseur d’identité (IdP). Pour ce faire, déployez un fichier YAML de configuration OpenID Connect (OIDC).

Si cela vous intéresse, envoyez un e-mail à [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) avec une brève description de votre cas d’utilisation et toute question éventuelle.

#### OpenTelemetry pour la surveillance des performances des applications (APM) (programme Alpha) {#apm-alpha}

AEM as a Cloud Service prend désormais en charge l’exportation de télémétrie basée sur OpenTelemetry, ce qui vous permet de surveiller AEM parallèlement au reste de vos systèmes dans les outils APM que vos équipes utilisent déjà.

Utilisez cette intégration pour :

&#x200B;- Enquête sur les requêtes lentes ou en échec
&#x200B;- Suivre l’intégrité de la JVM et l’utilisation des ressources au fil du temps
&#x200B;- Créer des tableaux de bord et des alertes pour votre niveau AEM
&#x200B;- Mise en relation du comportement d’AEM avec d’autres services lors d’incidents

Pour rejoindre la version alpha, envoyez un e-mail à l’adresse [&#128279;](mailto:aemcs-apm-beta@adobe.com) pour décrire votre cas d’utilisation.

### [!DNL Experience Manager] as a [!DNL Cloud Service] Assets Beta Fonctionnalités {#assets-beta-program-features}

#### Extensibilité de l’interface utilisateur pour la vue Assets {#ui-extensibility-assets-view}

La vue Assets prend en charge l’extensibilité de l’interface utilisateur, une fonctionnalité réservée aux développeurs qui permet aux clients de personnaliser l’expérience prête à l’emploi pour répondre à leurs besoins spécifiques.
Les clients peuvent tirer parti des points d’extension stables existants en suivant la documentation destinée aux développeurs d’Adobe pour créer et déployer des extensions avec un effort minimal. Pour les cas d’utilisation où un point d’extension requis n’est pas encore disponible, Adobe travaille directement avec les clients pour explorer les exigences et évaluer la faisabilité technique de la diffusion de nouvelles API d’extensibilité adaptées à leurs besoins, et peut fournir de nouvelles API telles que les **versions de Beta**.
En outre, Adobe a développé un outil de génération d’extensions optimisé par **GenAI** actuellement disponible dans une phase d’adoption précoce interne. Cet outil peut accélérer considérablement le temps de développement d’extensions. Les clients participant à ce programme bêta auront accès à l’outil et sont encouragés à partager leurs commentaires pour aider à façonner son évolution.
Pour participer ou en savoir plus, envoyez un e-mail à `GRP-ASSETSVIEWUIEXTENSIBILITY@adobe.com`.

#### Métadonnées basées sur la marque (BAM) {#brand-aware-metadata}

AEM Assets prend désormais en charge les métadonnées basées sur la marque, une fonctionnalité optimisée par l’IA qui génère automatiquement des métadonnées personnalisées pour les ressources lorsqu’elles sont chargées ou retraitées. Cela réduit le besoin de saisie manuelle par ordre d’importance, ce qui permet aux équipes de trouver des ressources et de diffuser de nouvelles expériences beaucoup plus rapidement. Les clients gèrent une bibliothèque d’invites qui définissent la manière dont l’IA doit renseigner un champ de métadonnées donné, adapté au vocabulaire et à la taxonomie de leur propre marque. Cette bibliothèque d&#39;invites comprend un terrain de jeu pour prévisualiser les résultats et un optimiseur d&#39;invites qui dessine automatiquement les améliorations suggérées.

Adobe développe activement les capacités de BAM par le biais d’une co-innovation directe avec les clients. Lorsqu’un cas d’utilisation spécifique n’est pas encore pris en charge, Adobe travaille avec les clients participants pour comprendre leurs besoins et peut fournir des fonctionnalités étendues au fur et à mesure de la progression de la version bêta. Les clients participant à ce programme bénéficient d’un accès anticipé aux nouvelles fonctionnalités lors de leur livraison et sont encouragés à partager leurs commentaires qui façonnent directement la feuille de route.

Pour participer ou en savoir plus, envoyez un e-mail à `GRP-AEM-ASSETS-BRANDAWAREMETADATA@adobe.com`.

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

