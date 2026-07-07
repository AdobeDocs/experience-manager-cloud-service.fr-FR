---
title: Contrôle d’accès basé sur les attributs
description: Découvrez comment activer le contrôle d’accès basé sur les attributs pour définir des règles basées sur les métadonnées afin de définir le niveau d’accès aux ressources disponibles dans Content Hub
role: Admin
badgeSaas: label="AEM Assets" type="Positive" tooltip="S’applique à AEM Assets)."
exl-id: 05f54b05-40b8-4a6c-af8f-5c3f7a2089d4
source-git-commit: bcdfc9bb418ab405faa82c55820a6ec6062c2b17
workflow-type: tm+mt
source-wordcount: '2182'
ht-degree: 4%

---


# Contrôle d’accès basé sur les attributs {#attribute-based-access-control}

Le contrôle d’accès basé sur les attributs (ABAC) permet aux administrateurs Content Hub de définir des règles basées sur les métadonnées pour contrôler le niveau d’accès aux ressources disponibles dans Content Hub.

Les administrateurs d’une organisation définissent des règles pour les groupes d’utilisateurs, qui sont mappés à un ID de groupe. Les règles sont un mélange d’opérateurs [logiques et de comparaison](#supported-rule-constructs) et les administrateurs peuvent définir autant de règles que nécessaire pour gérer l’accès aux ressources dans Content Hub.

Les règles sont basées sur les métadonnées. Si les conditions définies dans une règle correspondent aux métadonnées de la ressource, celle-ci est affichée pour le groupe d’utilisateurs. Content Hub analyse les métadonnées de la ressource, y compris les métadonnées personnalisées, pour toutes les ressources disponibles dans **Toutes les Assets** et **Collections** afin d’afficher les résultats aux groupes d’utilisateurs.

Par exemple, AUTORISER l’accès à un groupe d’utilisateurs avec un ID de groupe = 1011 lorsque les métadonnées de la ressource correspondent à « Marque = Brand X » ET « Région = EMEA OU Amériques ». Content Hub affiche uniquement les ressources du groupe d’utilisateurs avec l’ID = 1011 où « Marque = Brand X » et « Région = EMEA ou Amériques ».

Les règles ABAC dans Content Hub peuvent être configurées selon les approches suivantes :

* **Configuration en libre-service** à l’aide de l’assistant [AI dans Content Hub](#configure-abac-using-ai-assistant-in-content-hub), optimisé par l’agent de gouvernance AEM
* **Configuration basée sur une feuille de calcul** via la [prise en charge d’Adobe](#configure-abac-using-spreadsheet)

Avec l’assistant AI dans Content Hub, les administrateurs peuvent définir et gérer des règles ABAC à l’aide de métadonnées et du langage naturel. Cela permet une configuration plus rapide des règles et réduit la dépendance aux workflows de prise en charge manuels.

Voici quelques-uns des principaux avantages du contrôle d’accès basé sur les attributs :

* Élimine la dépendance à la structure de dossiers pour les autorisations
* Permet aux administrateurs et administratrices de charger des ressources et de déterminer rétroactivement les structures d’autorisation
* Réduit le nombre de doublons et améliore l’intégrité des ressources. Des doublons sont nécessaires dans les autorisations basées sur des dossiers lorsque les mêmes ressources sont partagées avec différents groupes.
* Permet un accès granulaire basé sur des règles
* Prend en charge la gouvernance évolutive entre les marques et les régions
* Améliore la gestion des ressources

>[!VIDEO](https://video.tv.adobe.com/v/3475413/?learn=on&enablevpops){transcript=true}

## Activation du contrôle d’accès basé sur les attributs {#enable-attribute-based-access-control}

Les règles ABAC dans Content Hub peuvent être configurées selon les approches suivantes :

* **Configuration en libre-service à l’aide de l’assistant AI dans Content Hub (optimisée par l’agent de gouvernance AEM)**\
  Les administrateurs peuvent définir et gérer les règles ABAC directement en utilisant le langage naturel dans Content Hub.

* **Configuration basée sur une feuille de calcul via la prise en charge d’Adobe**\
  Les administrateurs peuvent définir des règles ABAC dans une feuille de calcul et les envoyer via la prise en charge d’Adobe pour configuration.

## Configuration d’ABAC à l’aide de l’assistant AI dans Content Hub

Avec l’assistant AI dans Content Hub, optimisé par l’agent de gouvernance AEM, vous pouvez créer et gérer des règles ABAC directement dans Content Hub à l’aide du langage naturel.

Vous pouvez effectuer les actions suivantes :
* Rechercher des règles existantes
* Créer des règles
* Mettre à jour les règles
* Supprimer les règles

Cela permet aux administrateurs et administratrices de créer et de gérer des règles d’accès sans avoir à recourir à des workflows de prise en charge.

### Avant de commencer {#before-you-begin-ai-assistant}

Assurez-vous des points suivants avant d’utiliser l’assistant AI dans Content Hub pour la configuration des règles ABAC :

* Vous disposez d’une licence pour AEM as a Cloud Service
* L’assistant AI optimisé par l’agent de gouvernance AEM est disponible pour votre organisation
* Si vous n’y avez pas encore accès, contactez votre représentant Adobe et suivez les étapes requises pour l’obtention des licences
* Un pilote GenAI n’est pas nécessaire pour le programme try-buy

### Étapes de configuration des règles ABAC à l’aide de l’assistant AI {#steps-ai-assistant}

1. Ouvrez l’assistant d’IA dans Content Hub.

1. Commencez par une simple instruction.

   Par exemple :

   `Create a new rule in Content Hub`

   L’assistant AI vous guide sur les informations requises pour créer la règle.

1. Définissez la règle en langage naturel.

   Par exemple :

   `Frescopa Web Marketers user group should have access to assets where product equals Frescopa`

1. Sélectionnez l&#39;environnement auquel la règle ABAC doit s&#39;appliquer.

1. Vérifiez la règle avant de l’appliquer.

   L’assistant AI génère un aperçu structuré de la règle. Rien n’est appliqué automatiquement. Vous pouvez vérifier la règle générée, l’ajuster si nécessaire ou annuler l’action avant de l’appliquer.

1. Enregistrez et appliquez la règle.

   Une fois enregistrée, la règle est appliquée dynamiquement en fonction des métadonnées.

Cette étape de révision permet de garantir la précision avant l’application de la règle.

### Gestion des règles ABAC à l’aide d’invites {#manage-abac-rules-using-prompts}

Après avoir commencé à utiliser l’assistant AI, vous pouvez gérer les règles ABAC par conversation.

**Découvrir les règles**

* Afficher toutes les règles ABAC Content Hub existantes

**Créer des règles**

* Créer une règle qui donne au groupe marketing produit l’accès à toutes les ressources
* Accorder au groupe des ventes l’accès aux ressources dont la région est égale à EMEA

**Mettre à jour les règles**

* Mettre à jour la règle pour que le groupe marketing EMEA inclue APAC

**Supprimer des règles**

* Supprimer la règle pour le groupe Marketing produit

**Explorer les métadonnées et les groupes**

* Afficher les groupes disponibles et les propriétés de métadonnées pour définir des règles

## Configuration d’ABAC à l’aide d’une feuille de calcul

Si l’assistant AI n’est pas activé pour votre organisation, vous pouvez configurer des règles ABAC à l’aide du workflow basé sur une feuille de calcul.

Cliquez sur **Télécharger la feuille de calcul** pour télécharger et définir des règles dans une feuille de calcul. Créez un ticket d’assistance Adobe et fournissez à Adobe les règles définies dans la feuille de calcul.

[!BADGE Télécharger la feuille de calcul]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/ABAC_Get_Started_Template.xlsx"}

Définissez des règles dans la feuille de calcul à l’aide des instructions décrites dans cet article.

>[!IMPORTANT]
>
>Après avoir défini les règles, accédez à l’onglet **Erreurs de validation** de la feuille de calcul et cliquez sur **Exécuter les validations ABAC**. Le message **Toutes les validations effectuées** confirme que vous pouvez fournir les règles définies à Adobe.

### Étapes de configuration des règles ABAC à l’aide d’une feuille de calcul {#steps-spreadsheet}

1. Téléchargez le modèle de feuille de calcul ABAC.
1. Définissez des règles dans la feuille de calcul à l’aide de conditions basées sur les métadonnées.
1. Mappez chaque règle à l’ID de groupe IMS approprié.
1. Capturez l’intention commerciale de la règle dans les commentaires.
1. Envoyez un ticket d’assistance Adobe et partagez la feuille de calcul remplie avec Adobe.
1. Adobe configure les règles pour votre organisation.

## Exemple de cas d’utilisation de contrôle d’accès basé sur les attributs {#example-metadata-based-rules}

Pour prendre en charge un déploiement marketing à grande échelle, divers membres des équipes des différentes régions et marques doivent avoir accès aux ressources numériques. Chaque personnage a une portée spécifique basée sur la région et la marque. ABAC applique automatiquement ces règles à l’aide des métadonnées des ressources. Le tableau suivant illustre les rôles de ce cas d’utilisation et les règles appliquées :

| Personne | Rôle | Description du rôle | ID de groupe | Règle ABAC |
|---|---|---|---|---|
| John | Responsable marketing EMEA | Supervise l’exécution marketing pour toutes les marques dans la zone EMEA. Nécessite l’accès aux ressources approuvées pour toutes les marques destinées aux marchés EMEA. | group-emea-marketing | région = « EMEA » |
| Mike | Responsable marketing APAC | Supervise l’exécution marketing sur toutes les marques dans APAC. Nécessite l’accès aux ressources approuvées pour toutes les marques destinées aux marchés APAC. | group-apac-marketing | région = « APAC » |
| Sophie | Brand X Manager (EMEA) | Gère l’identité Brand X dans la zone EMEA. Ne doit afficher que le contenu approuvé par Brand X adapté aux marchés de la zone EMEA. | group-emea-brandx | région = « EMEA » et marque = « Brand X » |
| Tom | Brand Y Manager (APAC) | Gère l’identité de la marque Y dans APAC. Ne doit afficher que le contenu approuvé par la marque Y adapté aux marchés APAC. | group-apac-brandy | région = « APAC » et marque = « Marque Y » |

Grâce à ces règles, les administrateurs Content Hub disposent des éléments suivants :

* **Accès granulaire, basé sur des règles** : les utilisateurs voient uniquement les ressources pertinentes pour leur région et leur marque sans attribution manuelle d’autorisations.
* **Collaboration mondiale transparente** : les équipes régionales et de marque travaillent en parallèle sans conflits d’accès.
* **Autorisations évolutives et pérennes** : à mesure que de nouvelles régions ou marques sont ajoutées, les règles peuvent être mises à jour en fonction des métadonnées.

### Scénarios supplémentaires dans lesquels l’ABAC est utile {#additional-scenarios-abac}

L’ABAC peut également vous aider à résoudre les scénarios suivants :

* **Marque mondiale et accès régional** : les équipes ne voient que les ressources pertinentes pour leur marque et leur marché.
* **Collaboration entre agences et partenaires** : les agences et partenaires externes ne peuvent accéder qu’aux ressources de la campagne qui les concernent.
* **Accès en fonction du rôle pour différentes équipes** : les équipes telles que les équipes marketing, commerciales et juridiques peuvent accéder aux ressources liées à leur fonction.
* **Conformité juridique spécifique à la région** : les utilisateurs peuvent être limités à des ressources approuvées pour des exigences réglementaires ou régionales spécifiques.

>[!IMPORTANT]
>
>Par défaut, tous les autres groupes d’utilisateurs qui ne sont pas spécifiés avec des règles dans la [ feuille de calcul](#configure-abac-spreadsheet) se voient refuser l’accès. Si un utilisateur ou une utilisatrice ne fait partie d’aucun groupe pour lequel des règles ABAC sont définies, il ou elle ne peut accéder à aucune ressource. Si certains utilisateurs doivent avoir accès à toutes les ressources (les administrateurs, par exemple), incluez un groupe avec un ID de groupe dans la feuille de calcul et indiquez que ce groupe doit avoir accès à toutes les ressources afin qu’Adobe puisse le configurer en conséquence.

## Éléments de règle pris en charge {#supported-rule-constructs}

* **Opérateurs logiques** :
   * AND : toutes les conditions doivent être vraies
   * OR : au moins une condition doit être vraie

* **Opérateurs de comparaison** :
   * Est égal à (=) : vérifie si un attribut d’utilisateur ou de ressource correspond à une valeur
   * Différent de (!=) : vérifie si un attribut d’utilisateur ou de ressource ne correspond à aucune valeur

Lorsque les champs de métadonnées de ressource contiennent des tableaux, par exemple plusieurs régions ou balises, Est égal à fait référence à la logique contient et N’est pas égal à fait référence à ne contient pas de logique.

Cela vous permet d’écrire des règles simples et expressives, telles que ALLOW si region = emea ET assetType != prototype ET les balises != confidentielles.

## Directives {#guidelines-attribute-based-access-control}

Les instructions suivantes s’appliquent à la fois à la configuration basée sur un assistant d’IA et à la configuration basée sur une feuille de calcul :

* Les règles ABAC s’appliquent uniquement aux ressources approuvées pour Content Hub. Pour plus d’informations, voir [ Approuver Assets pour Content Hub ](/help/assets/approve-assets-content-hub.md).
* Ne définissez pas de règles DENY. Convertissez toujours les règles DENY en règles ALLOW. Par exemple, AUTORISER si région = user-region DENY si assetType = prototype ET confidentiel = oui peut être converti en AUTORISER si région = user-region ET (assetType != prototype OU confidentiel != oui).
* Les règles ABAC sont appliquées aux groupes d’utilisateurs à l’aide de l’identifiant de groupe IMS, disponible dans Admin Console.
* Vous pouvez définir la [cible d’approbation](/help/assets/approve-assets-content-hub.md#set-approval-target) pour les ressources à l’aide de l’environnement de création AEM as a Cloud Service. Les règles ABAC sont appliquées aux ressources approuvées avec Cible de validation = Content Hub, car Cible de validation = Diffusion concerne les ressources disponibles pour la diffusion + Content Hub. Assets marqué comme Cible de validation = Diffusion est visible par tous dans Content Hub.
* Vérifiez que les schémas de métadonnées utilisés dans les règles ABAC sont correctement définis et disponibles dans AEM. Indiquez le chemin d’accès complet du ou des schémas de métadonnées dans AEM qui définissent les propriétés référencées dans les règles ABAC. Vous pouvez éventuellement créer un dossier de test avec des exemples de ressources qui correspondent aux conditions ABAC pour vous aider à vérifier le comportement des règles et à évaluer l’accès avec précision.
* Capturez l’intention commerciale de la règle dans les commentaires, même si la condition est correctement écrite, car l’intention permet de valider et de corriger la logique si nécessaire.
* Assurez-vous que les valeurs de métadonnées utilisées pour les règles d’accès, telles que la marque, la région et le produit, sont conservées de manière cohérente dans toutes les ressources.
* Commencez par des cas d’utilisation clés tels que l’accès basé sur la marque ou la région.
* Utiliser des invites claires lors de la définition de règles avec l&#39;assistant AI Décrivez l’intention dans un langage professionnel afin que l’assistant AI puisse la traduire en une règle structurée.
* Les fichiers PDF de licence définis pour DRM doivent rester visibles par tous les utilisateurs afin qu’ils puissent consulter les informations de licence lors du téléchargement de la ressource avec licence.

## Questions fréquemment posées {#faqs-attribute-based-access-control-content-hub}

### Qu’est-ce que le contrôle d’accès basé sur les attributs (ABAC) dans AEM Assets Content Hub ?

Le contrôle d’accès basé sur les attributs (ABAC) dans AEM Assets Content Hub permet aux administrateurs de définir des règles basées sur les métadonnées pour contrôler le niveau d’accès aux ressources numériques de différents groupes d’utilisateurs. L’accès est déterminé par le fait que les métadonnées de la ressource correspondent ou non aux conditions spécifiées dans les règles, ce qui permet une gestion granulaire et dynamique de la visibilité des ressources.

### Comment les administrateurs définissent-ils les règles d’accès à l’aide d’ABAC dans AEM Assets Content Hub ?

Les administrateurs définissent les règles d’accès en créant des conditions basées sur les métadonnées des ressources, telles que la marque ou la région, et en les liant à des ID de groupe d’utilisateurs spécifiques. Ces règles utilisent des opérateurs logiques et de comparaison pour spécifier exactement quelles ressources sont visibles pour quels groupes d’utilisateurs.

### Quels sont les principaux avantages de l’utilisation d’ABAC par rapport aux autorisations traditionnelles basées sur les dossiers dans AEM Assets Content Hub ?

ABAC élimine la dépendance aux structures de dossiers pour les autorisations, permet aux administrateurs de charger des ressources et d’attribuer des autorisations rétroactivement et réduit le nombre de ressources en double nécessaires. Cela améliore l’intégrité des ressources et simplifie la gestion des autorisations, en particulier lorsque des ressources doivent être partagées avec plusieurs groupes.

### Les administrateurs peuvent-ils configurer des règles ABAC directement dans l’interface Content Hub d’AEM Assets ?

Les administrateurs peuvent configurer des règles ABAC à l’aide de l’assistant AI dans Content Hub, si elles sont activées pour leur organisation. Ils peuvent également continuer à utiliser le workflow basé sur une feuille de calcul via l’assistance Adobe.

### Quels types de conditions de métadonnées peuvent être utilisés lors de la configuration de règles ABAC dans AEM Assets Content Hub ?

Les règles ABAC dans AEM Assets Content Hub peuvent utiliser des opérateurs logiques tels que AND et OR, et des opérateurs de comparaison tels que égal à et différent de. Les propriétés de métadonnées utilisées dans les règles doivent être correctement définies et disponibles dans les schémas de métadonnées AEM. Elles peuvent inclure des champs tels que la région, la marque, le produit, la campagne, le type de ressource ou le statut de publication.

### Pourquoi l’ABAC Content Hub d’AEM Assets est-il particulièrement utile pour les organisations disposant d’équipes nombreuses et de besoins en ressources divers ?

ABAC est utile pour les organisations disposant de grandes équipes, car il permet un accès granulaire et basé sur des règles aux ressources en fonction des rôles utilisateur, des régions, des marques ou des besoins de l’entreprise. Cela permet de s’assurer que les utilisateurs voient uniquement les ressources correspondant à leurs responsabilités, sans affectation manuelle d’autorisations ni duplication excessive des ressources.

### Comment les administrateurs doivent-ils préparer la feuille de calcul ABAC pour AEM Assets Content Hub avant de l’envoyer à l’assistance Adobe ?

Les administrateurs doivent créer des groupes d’utilisateurs dans le Adobe Admin Console, noter leurs ID de groupe, définir clairement les autorisations et conditions de chaque groupe dans la feuille de calcul, s’assurer que toutes les propriétés de métadonnées sont correctement mappées aux schémas appropriés et utiliser la colonne de commentaires pour clarifier l’intention commerciale de chaque règle.

**Voir également**

* [Traduire les ressources](/help/assets/translate-assets.md)
* [API HTTP Assets](/help/assets/mac-api-assets.md)
* [Formats de fichiers pris en charge par Assets](/help/assets/file-format-support.md)
* [Rechercher des ressources](/help/assets/search-assets.md)
* [Ressources connectées](/help/assets/use-assets-across-connected-assets-instances.md)
* [Rapports de ressources](/help/assets/asset-reports.md)
* [Schémas de métadonnées](/help/assets/metadata-schemas.md)
* [Télécharger des ressources](/help/assets/download-assets-from-aem.md)
* [Gestion des métadonnées](/help/assets/manage-metadata.md)
* [Gérer les modèles Dynamic Media](/help/assets/dynamic-media/manage-dynamic-media-templates.md)
* [Gérer les rapports](/help/assets/manage-reports-assets-view.md)
* [Facettes de recherche](/help/assets/search-facets.md)
* [Gérer les collections](/help/assets/manage-collections.md)
* [Import des métadonnées en bloc](/help/assets/metadata-import-export.md)
* [Publier des ressources sur AEM et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

