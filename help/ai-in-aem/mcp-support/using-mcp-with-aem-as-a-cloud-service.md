---
title: Utilisation de MCP avec AEM as a Cloud Service
description: Découvrez comment utiliser le protocole Model Context avec AEM as a Cloud Service
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: a5eeb2cedb16f7d0ba0b31e838b3b9fa27b0bf3f
workflow-type: tm+mt
source-wordcount: '2064'
ht-degree: 0%

---


# Utilisation de MCP avec AEM as a Cloud Service {#using-mcp-with-aem-as-a-cloud-service}

## Présentation {#introduction}

De nombreuses équipes Adobe Experience Manager (AEM) travaillent désormais dans des environnements de développement intégré (IDE) et des applications de chat telles que Cursor, ChatGPT, Anthropic Claude et Microsoft Copilot Studio. Ces applications prennent en charge le protocole MCP (Model Context Protocol), qui permet aux applications d’exposer les outils principaux à des modèles de langage (LLM) volumineux de manière normalisée.

Grâce à l’intégration d’AEM MCP, différentes personnes peuvent collaborer sur le même contenu :

* **Les développeurs** peuvent orchestrer les opérations et les workflows de contenu à partir de leur application IDE ou de chat
* **Les spécialistes et** architectes de contenu peuvent gérer des sites, des fragments de contenu et des ressources avec l’aide de l’IA, tout en restant dans le modèle d’autorisation existant d’AEM.

>[!IMPORTANT]
>
> Pour les scénarios qui modifient ou suppriment du contenu, les utilisateurs doivent utiliser l’interface de l’assistant AI plutôt que d’appeler directement les outils MCP, car les agents AEM exécutés par l’assistant AI incluent des mesures de protection intégrées.
>

Cet article explique ce que fournit la fonctionnalité MCP d’AEM, quelles applications MCP sont prises en charge, comment la configurer et comment l’utiliser en pratique.

## Pourquoi MCP est-il utile pour les clients AEM ? {#why-mcp-is-useful-for-aem-customers}

Les applications modernes d’IDE et de chat utilisent MCP comme moyen pour un LLM d’appeler les outils exposés derrière les serveurs MCP. Au lieu d’écrire du code par rapport aux spécifications d’API de bas niveau, les clients peuvent décrire leur intention en langage naturel (*« mettre à jour la bannière principale de cette campagne sur toutes les pages »*) et laisser le LLM appeler les outils de MCP appropriés, qui interagissent à leur tour avec les API d’AEM.

Les principaux bénéfices sont les suivants :

* **Interaction en langage naturel au lieu de la plomberie de l’API**
Les outils MCP décrivent les opérations disponibles et comment les appeler. Le LLM utilise ces schémas pour décider quels outils appeler et avec quels paramètres.
* **Expérience cohérente entre les applications**
Les mêmes outils AEM MCP peuvent être utilisés à partir de plusieurs applications compatibles MCP, ce qui permet aux équipes de travailler là où elles sont le plus productives tout en appelant les mêmes fonctionnalités AEM sous-jacentes.
* **Sécurité et gouvernance préservées**
Les requêtes envoyées aux outils de MCP AEM s’exécutent sous l’identité de l’utilisateur authentifié et chaque outil applique les autorisations AEM existantes de l’utilisateur. Les opérations assistées par l’IA suivent les mêmes règles d’accès que le travail manuel dans AEM.

## Serveurs MCP fournis par AEM {#mcp-servers-provided-by-aem}

AEM expose les serveurs MCP en tant que points d’entrée HTTP. Les points d’entrée répertoriés ci-dessous sont relatifs à :

`https://mcp.adobeaemcloud.com/adobe/mcp/`

### Serveurs MCP {#mcp-servers}

| **Serveur MCP** | **Point d’entrée** | **Description** |
|---|---|----------------------------------------------------------------------------------------------------------------------|
| **Contenu** | `/content` | Toutes les opérations de contenu de bas niveau, y compris la création, la lecture, la mise à jour et la suppression (CRUD) des pages, des fragments et des ressources. |
| **Contenu (lecture seule)** | `/content-readonly` | Opérations de contenu en lecture seule (Get, List/Search) pour des pages, des fragments et des ressources. |

Les outils spécifiques exposés par chaque serveur MCP peuvent évoluer au fil du temps. En pratique, vous pouvez demander à votre application compatible avec les MCP de découvrir les outils par le biais d’une invite telle que :

*« Répertoriez tous les outils AEM MCP disponibles sur ce serveur et décrivez leur fonctionnement. »*

Le client MCP utilisera le protocole MCP pour récupérer la liste d’outils et les schémas, que le LLM peut ensuite utiliser.

## Applications MCP prises en charge {#supported-mcp-applications}

Les serveurs MCP AEM sont conçus pour fonctionner avec un ensemble défini d’applications compatibles avec MCP. Les applications supportées sont les suivantes :

* Claude Anthropique
* Curseur
* OpenAI ChatGPT
* Microsoft Copilot Studio

Chaque application fournit sa propre expérience de configuration, mais les étapes de haut niveau sont similaires.

## Présentation de la configuration {#setup-overview}

La configuration de MCP pour AEM comprend deux parties principales :

1. **Configuration dans chaque application cliente MCP** de sorte que l’application sache comment se connecter aux serveurs MCP AEM et se connecter à OAuth.
1. **Sélectionnez le serveur MCP** avant de démarrer l&#39;invite, de sorte que le client MCP sache l&#39;utiliser.

### Configuration AEM {#aem-configuration}

Par défaut, l’accès aux serveurs MCP d’AEM est régi par les autorisations dont disposent les utilisateurs individuels dans AEM. Lorsqu’un utilisateur s’authentifie via une application cliente MCP, les outils MCP appliquent les mêmes règles d’accès que les opérations manuelles dans AEM. Un utilisateur ne peut effectuer que les actions qu’il est déjà autorisé à effectuer.

#### Applications clientes MCP autorisées {#permitted-mcp-client-applications}

Les applications clientes MCP suivantes sont autorisées par défaut :

* ChatGPT
* Claude
* MS Copilot Studio
* Curseur

#### Restreindre les serveurs MCP {#restricting-mcp-servers}

Placer sur la liste autorisée Tous les serveurs MCP sont traités par défaut. En tant qu’administrateur, vous avez la possibilité de restreindre l’accès à des serveurs MCP spécifiques au niveau de l’organisation, du programme ou de l’environnement. Vous pouvez ainsi contrôler de manière granulaire les fonctionnalités de MCP disponibles pour les utilisateurs de votre entreprise.

#### Gestion de l’accès client MCP {#managing-mcp-client-access}

Les administrateurs peuvent également désactiver l’accès à des applications clientes MCP spécifiques si les politiques de votre entreprise l’exigent. Si vous souhaitez qu’Adobe active la prise en charge de produits clients MCP supplémentaires, envoyez un lien vers le site web du produit. Si vous devez placer sur la liste autorisée un client MCP personnalisé, contactez-le également.

Pour toutes les demandes liées au serveur MCP, n&#39;hésitez pas à nous contacter à **aemcs-mcp-feedback@adobe.com**

### Configuration de l’application cliente MCP {#mcp-client-application-configuration}

Cette étape est effectuée par chaque utilisateur (ou par un administrateur de l’application cliente MCP, lorsque cela est pris en charge). Les détails de configuration varient légèrement selon les applications. Les clients MCP évoluent rapidement et la prise en charge des serveurs MCP distants est activement développée. Vous devrez peut-être activer le mode Développeur pour accéder à la fonctionnalité d’ajout de serveurs distants, mais le processus général est le suivant :

1. Ajouter les URL du serveur MCP AEM
   * Configurez le ou les points d’entrée MCP à partir du tableau ci-dessus. Par exemple :`https://mcp.adobeaemcloud.com/adobe/mcp/content-readonly`
1. Déclencher la connexion
   * Enregistrez ou activez la configuration afin que l’application cliente MCP tente de se connecter au serveur MCP AEM
1. Se connecter avec Adobe ID
   * Lorsque vous y êtes invité, complétez le flux de connexion Adobe afin que l’application puisse obtenir des jetons OAuth liés à votre Adobe ID
1. Vérification des outils découverts
   * Une fois authentifiée, l’application détecte les outils MCP à partir du serveur. Vous pouvez ensuite commencer à demander au LLM d’effectuer des opérations AEM.

Vous trouverez ci-dessous des exemples détaillés de la façon dont cela se présente dans chaque application prise en charge.

### ChatGPT {#chatgpt}

![Configurer ChatGPT - Paramètres](assets/chatgpt-1.png)

![Configurer ChatGPT - Applications et connecteurs - Paramètres avancés](assets/chatgpt-2.png)

![Configurer ChatGPT - Applications et connecteurs - Mode Développeur](assets/chatgpt-3.png)

![Configurer ChatGPT - Applications et connecteurs - Créer une application](assets/chatgpt-4.png)

![Configurer ChatGPT - Applications et connecteurs - Nouvelle application](assets/chatgpt-5.png)

![Configurer ChatGPT - Applications et connecteurs - Service AEM Content MCP](assets/chatgpt-6.png)

![Configurer le ChatGPT - Demandez au service AEM Content MCP](assets/chatgpt-7.png)

* Ajoutez les URL du serveur MCP AEM dans la zone où les connexions ou outils MCP sont configurés
* Déclenchez la connexion et connectez-vous avec votre Adobe ID en cas de redirection
* Dans une conversation, référencez les outils AEM configurés dans vos invites, par exemple :

  *« À l’aide des outils AEM MCP configurés, répertoriez tous les sites de votre environnement de création. »*

### Claude {#claude}

![Configurer Claude - Paramètres](assets/claude-1.png)

![Configurer Claude - Connecteurs](assets/claude-2.png)

![Configurer Claude - Connecteurs - Ajouter un connecteur personnalisé](assets/claude-3.png)

![Configurer Claude - Connecteurs - Connecter un connecteur personnalisé](assets/claude-4.png)

![Configurer Claude - Connecteurs - Configurer le connecteur personnalisé](assets/claude-5.png)

![Configuration de Claude - Connecteurs - Autorisations de l’outil de connecteur personnalisé](assets/claude-6.png)

![Configurer Claude - Demander au service AEM Content MCP](assets/claude-7.png)

* Dans la configuration MCP de Claude, enregistrez les URL du serveur MCP AEM
* Terminer le flux de connexion à Adobe
* Vous pouvez éventuellement activer la confirmation automatique pour certains outils dans la zone de configuration. Ceci est recommandé pour les opérations de recherche ou de lecture seule.
* Assurez-vous que le serveur MCP est sélectionné avant de commencer votre conversation
* Demandez à Claude d’effectuer des tâches liées à AEM ; Claude sélectionnera les outils AEM exposés par le serveur MCP en fonction de votre invite.

### Curseur {#cursor}

![Configurer le curseur - Paramètres](assets/cursor-1.png)

![Configurer le curseur - Outils et MCP - Ajouter un MCP personnalisé](assets/cursor-2.png)

![Configurer le curseur - Ajouter des paramètres MCP personnalisés](assets/cursor-3.png)

![Configurer le curseur - Se connecter](assets/cursor-4.png)

![Configurer le curseur - Demander le nouveau service](assets/cursor-5.png)

* Dans les paramètres MCP du curseur, créez une entrée de serveur MCP avec la ou les URL MCP AEM
* S’authentifier auprès de votre Adobe ID lorsque vous y êtes invité
* Vous pouvez éventuellement activer ou désactiver des outils individuels en cliquant sur leur nom. Tous les outils sont activés par défaut.
* Utilisez l’éditeur de curseur ou la conversation pour appeler les outils AEM dans le cadre des workflows de développement ou de contenu.

### Microsoft Copilot Studio {#microsoft-copilot-studio}

![Configuration du copilote - Agents](assets/copilot-1.png)

![Configurer Copilot - Ajouter un outil](assets/copilot-2.png)

![Configuration de Copilot - Ajout d’outil - Modèle de protocole de contexte](assets/copilot-3.png)

![Configuration de Copilot - Ajout d’un serveur Model Context Protocol (aperçu)](assets/copilot-4.png)

![Configuration de Copilot - Ajout d’un outil - Création d’une connexion](assets/copilot-5.png)

![Configurer Copilot - Ajouter un outil - Ajouter et configurer](assets/copilot-6.png)

![Configurer Copilot - Ajouter un outil - Configurer](assets/copilot-7.png)

![Configurer Copilot - Tester la connexion](assets/copilot-8.png)

![Configurer Copilot - Gérer les connexions](assets/copilot-9.png)

![Configuration de Copilot - Agent de test](assets/copilot-10.png)

* Créer un agent
* Accédez à la section Outil et cliquez sur **Ajouter un outil**
* Sélectionner un outil existant ou en créer un nouveau
* Configurez un nouvel outil MCP pointant vers les URL du serveur MCP AEM
* Établir une connexion qui peut être partagée ou dédiée entre les agents
* Se connecter à l’aide de votre Adobe ID en cas de redirection
* Vous pouvez éventuellement activer le mode de confirmation automatique ou exiger une confirmation de l’utilisateur final pour toutes les interactions de l’outil
* Lors du test de l’agent, ouvrez d’abord le gestionnaire de connexions pour attribuer une connexion à votre session, puis appuyez sur **Réessayer**.

## Authentification {#authentication}

Les serveurs MCP hébergés par Adobe mettent en œuvre OAuth et sont intégrés au système d’identités d’Adobe.

* Lorsqu’une application cliente MCP se connecte à un serveur MCP AEM, les utilisateurs voient une boîte de dialogue de connexion Adobe et s’authentifient avec leur **Adobe ID**
* Une fois la connexion établie, le système vérifie que l’application cliente MCP est autorisée dans votre organisation et que le serveur MCP demandé est autorisé. Si l’une de ces vérifications échoue, un message d’erreur s’affiche.

![Erreur Client MCP non autorisé &#x200B;](assets/MCP-Client-not-permitted.png)

* Une fois la vérification effectuée, le serveur MCP émet des jetons que l’application utilise pour les appels d’outil suivants
* Les outils MCP respectent les autorisations AEM de l’utilisateur. Un utilisateur non autorisé à modifier un fragment de contenu dans AEM ne pourra pas le modifier non plus via MCP.

Cela garantit que les opérations assistées par l’IA sont conformes à votre modèle de sécurité et de gouvernance AEM existant.

## Utilisation de MCP avec AEM {#using-mcp-with-aem}

Une fois AEM et vos applications clientes MCP configurées, vous pouvez travailler dans l’application de votre choix et demander au LLM d’effectuer des opérations AEM. Le LLM lit les schémas d’outils du MCP, sélectionne les outils à appeler et les séquence selon les besoins pour répondre à votre requête.

>[!IMPORTANT]
>
>Pour de meilleurs résultats, en particulier avec les invites qui contiennent plusieurs étapes ou qui ciblent différents types de contenu tels que des images et du texte, activez un modèle de réflexion ou sélectionnez l&#39;option Réflexion dans votre client MCP plutôt que de compter sur le mode automatique.

### Exemples de cas d’utilisation {#example-usecases}

Voici quelques scénarios représentatifs :

* **Découverte de l’environnement**
   * Répertoriez les environnements et les licences pour décider où exécuter un workflow.

* **Gestion des sites**
   * Liste des sites
   * Créer, lire, mettre à jour et supprimer des pages et du contenu de page.

* **Gestion des fragments de contenu**
   * Rechercher des fragments de contenu
   * Création de fragments
   * Mettre à jour les fragments existants lorsque les messages de campagne changent.

* **Gestion d’Assets**
   * Importation de ressources
   * Recherche de ressources existantes
   * Publier des ressources.

### Exemples de workflows {#example-workflows}

Les exemples suivants illustrent comment un LLM peut enchaîner des outils MCP.

1. **Utiliser un fragment de contenu référencé par une page**
   * **Obtenir le contenu de la page** - Appelez un outil tel que `get-aem-page-content` pour récupérer la page et localiser la propriété `fragmentPath`.
   * **Résoudre le chemin d’accès au fragment** - Utilisez `resolve_fragment_path` pour convertir le chemin en UUID.
   * **Récupérer des données de fragment** - Appelez `get_fragment` pour récupérer les champs actifs.
   * **Mettre à jour le fragment** - Appelez le `patch_fragment` pour appliquer des modifications au contenu du fragment.
1. **Création d’un nouveau contenu basé sur un modèle**
   * **Découvrir les modèles** - Utilisez des `list_models` pour voir quels modèles de fragment de contenu sont disponibles.
   * **Inspecter un modèle** - Utilisez `get_model` pour comprendre le schéma de champ du modèle.
   * **Créer du contenu** - Utilisez `create_fragment` pour créer un fragment avec des valeurs dérivées de votre invite.
1. **Mise à jour sécurisée du contenu existant**
   * **Lire les données actives** - Utilisez `get_fragment` pour récupérer les données existantes et une ETag.
   * **Application d’un correctif JSON** - Utilisez les `patch_fragment` avec l’ETag et un document JSON Patch pour mettre à jour le fragment, en prenant en charge la simultanéité optimiste.

Du point de vue de l’utilisateur, ces workflows peuvent être lancés à l’aide d’invites telles que :

*« Créez un fragment de contenu pour la campagne de printemps en vous basant sur notre modèle de bannière principale et renseignez ses champs à partir de ce brief. »*

Le LLM choisit et coordonne automatiquement les outils MCP nécessaires.

## Gestion des attentes {#expectation-management}

Lorsque vous travaillez avec des LLM par le biais de MCP, tenez compte des points suivants :

* **Hautement capable mais non infaillible**
Les LLM peuvent accomplir des tâches complexes, mais sont sujets à des erreurs occasionnelles. Une même invite peut donner des résultats ou des présentations légèrement différents sans raison évidente. Examinez toujours les sorties avant d’appliquer des modifications au contenu de production.

* **Évolution des capacités**
Les modèles LLM s&#39;améliorent continuellement. Au fil du temps, ils deviennent plus intelligents et découvrent de nouvelles façons de combiner les outils MCP pour atteindre vos objectifs. Une tâche qui nécessitait plusieurs invites aujourd&#39;hui peut fonctionner de manière transparente avec une seule invite demain.

* **La surveillance humaine est essentielle**
Considérez le LLM comme un assistant compétent qui a besoin d&#39;être supervisé. Elle possède une connaissance étendue et peut concevoir des solutions créatives, mais elle bénéficie de vos conseils et de votre examen. Vérifiez les résultats, en particulier pour les opérations critiques, et envoyez des commentaires lorsque la sortie ne correspond pas à vos attentes.

* **Faites attention avec les exécutions d’outils de reconnaissance automatique**
Certaines applications clientes MCP, telles que Claude, offrent la possibilité d’acquitter automatiquement les exécutions d’outils demandées par le LLM. Cela peut s’avérer pratique pour les opérations en lecture seule telles que la recherche ou la récupération de contenu, mais soyez prudent avec les outils qui mettent à jour ou suppriment du contenu. Examinez chaque demande d’exécution d’outil avant de confirmer les actions qui modifient votre environnement AEM.

## Limites {#limitations}

Les serveurs MCP AEM sont actuellement destinés à être configurés dans ChatGPT, Claude, Cursor et Microsoft Copilot Studio.

Si vous souhaitez utiliser une autre application cliente MCP, n’hésitez pas à contacter **aemcs-mcp-feedback@adobe.com** pour demander de l’aide pour d’autres clients ou pour en placer sur la liste autorisée une personnalisée.
