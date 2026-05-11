---
title: Utilisation de MCP avec AEM as a Cloud Service
description: Découvrez comment utiliser le protocole Model Context avec AEM as a Cloud Service
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: ddb7fc8c-affc-4374-8e08-d45d96017109
source-git-commit: 0e011e464ba607edf1fce719263717cc8ce6ba61
workflow-type: tm+mt
source-wordcount: '1922'
ht-degree: 1%

---


# Utilisation de MCP avec AEM as a Cloud Service {#using-mcp-with-aem-as-a-cloud-service}

## Présentation {#introduction}

De nombreuses équipes Adobe Experience Manager (AEM) travaillent désormais dans des environnements de développement intégré (IDE) et des applications de chat telles que Cursor, OpenAI ChatGPT, Anthropic Claude et Microsoft Copilot Studio. Ces applications prennent en charge le protocole MCP (Model Context Protocol), qui permet aux applications d’exposer les outils principaux à des modèles de langage (LLM) volumineux de manière normalisée.

Grâce à l’intégration d’AEM MCP, différentes personnes peuvent collaborer sur le même contenu :

* **Les développeurs** peuvent orchestrer les opérations et les workflows de contenu à partir de leur application IDE ou de chat.
* **Les spécialistes et** architectes de contenu peuvent gérer les sites et les fragments de contenu et importer des ressources avec l’aide de l’IA, tout en restant dans le modèle d’autorisation existant d’AEM.

>[!IMPORTANT]
>
> Pour les scénarios qui modifient ou suppriment du contenu, les utilisateurs doivent utiliser l’interface de l’assistant d’IA plutôt que d’appeler directement les outils MCP. Les agents AEM exécutés par l’assistant AI incluent des mesures de sécurité intégrées.

Cet article explique ce que fournit la fonctionnalité MCP d’AEM, quelles applications MCP sont prises en charge, comment la configurer et comment l’utiliser en pratique.

## Pourquoi MCP est-il utile pour les clients AEM ? {#why-mcp-is-useful-for-aem-customers}

Les applications modernes d’IDE et de chat utilisent MCP comme moyen pour un LLM d’appeler les outils exposés derrière les serveurs MCP. Les clients peuvent décrire leur intention en langage naturel au lieu d’écrire du code par rapport aux spécifications d’API de bas niveau. Par exemple, une invite telle que *« mettre à jour la bannière principale de cette campagne sur toutes les pages »* permet au LLM d’appeler les outils de MCP appropriés, qui interagissent ensuite avec les API d’AEM.

Les principaux bénéfices sont les suivants :

* **Interaction en langage naturel au lieu de la plomberie de l’API** - Les outils MCP décrivent les opérations disponibles et comment les appeler. Le LLM utilise ces schémas pour décider quels outils appeler et avec quels paramètres.
* **Expérience cohérente entre les applications** - Les mêmes outils MCP AEM peuvent être utilisés à partir de plusieurs applications compatibles MCP, ce qui permet aux équipes de travailler là où elles sont le plus productives tout en appelant les mêmes fonctionnalités AEM sous-jacentes.
* **Sécurité et gouvernance conservées** - Les requêtes adressées aux outils de MCP AEM s’exécutent sous l’identité de l’utilisateur authentifié et chaque outil applique les autorisations AEM existantes de l’utilisateur. Les opérations assistées par l’IA suivent les mêmes règles d’accès que le travail manuel dans AEM.

## Serveurs MCP fournis par AEM {#mcp-servers-provided-by-aem}

AEM expose les serveurs MCP en tant que points d’entrée HTTP. Les points d’entrée répertoriés ci-dessous sont relatifs à `https://mcp.adobeaemcloud.com/adobe/mcp/`.

### Serveurs MCP {#mcp-servers}

| Serveur MCP | Point d’entrée | Description |
|---|---|---|
| **Contenu** | `/content` | Opérations de contenu dont la création, la lecture, la mise à jour et la suppression (CRUD) de pages et de fragments de contenu, ainsi que l’importation et la recherche de ressources.<br>Si vous êtes intéressé, vous devez vous inscrire à l’essai [&#x200B; agents ou disposer d’une licence payante](https://experienceleague.adobe.com/fr/docs/experience-cloud-ai/experience-cloud-ai/agents/trial) afin d’accéder au MCP de la gouvernance d’expérience. |
| **Contenu (lecture seule)** | `/content-readonly` | Opérations de contenu en lecture seule (get, list/search) pour les pages et les fragments de contenu, ainsi que recherche de ressources.<br>Si vous êtes intéressé, vous devez vous inscrire à l’essai [&#x200B; agents ou disposer d’une licence payante](https://experienceleague.adobe.com/fr/docs/experience-cloud-ai/experience-cloud-ai/agents/trial) afin d’accéder au MCP de la gouvernance d’expérience. |
| **Cloud Manager** | `/cloudmanager` | Gérez les entités Cloud Manager, notamment les programmes, les environnements, les référentiels et les pipelines, qui peuvent également être déclenchés. |
| **Gouvernance de l’expérience** | `/experience-governance` | Évaluez le contenu (texte, images, pages) par rapport aux règles de gouvernance de marque et répertoriez les configurations et les contrôles de marque.<br/>Si vous êtes intéressé, vous devez vous inscrire à l’essai [&#x200B; agents ou disposer d’une licence payante](https://experienceleague.adobe.com/fr/docs/experience-cloud-ai/experience-cloud-ai/agents/trial) afin d’accéder au MCP de la gouvernance d’expérience. |

Les outils spécifiques exposés par chaque serveur MCP peuvent évoluer au fil du temps. En pratique, vous pouvez demander à votre application compatible avec les MCP de découvrir les outils par le biais d’une invite telle que :

```
"List all AEM tools available from this server and describe what they do."
```

Le client MCP utilise le protocole MCP pour récupérer la liste d’outils et les schémas, que le LLM peut ensuite utiliser.

Pour plus d’informations sur leurs fonctionnalités et sur leur utilisation[&#128279;](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/ai/mcp-servers/accelerate-content-operations-with-aem-mcp-server) reportez-vous aux sections Tutoriel sur le serveur de MCP de contenu et [Vidéo sur le serveur de MCP de Cloud Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/ai/mcp-servers/cloud-manager).

## Applications MCP prises en charge {#supported-mcp-applications}

Les serveurs MCP AEM sont conçus pour fonctionner avec un ensemble défini d’applications compatibles avec MCP. Chaque application fournit sa propre expérience de configuration, mais les étapes de haut niveau sont similaires.

### Applications De Chat (Web Et Bureau) {#chat-applications}

* Claude Anthropique
* OpenAI ChatGPT

### Outils de développement (extensions IDE, applications de bureau, interfaces de ligne de commande) {#developer-tools}

* Code Claude Anthropique (CLI, JetBrains, VS Code, Cursor)
* Code d&#39;augmentation (CLI, JetBrains, VS Code, Cursor)
* Augmenter le retrait de l’application de bureau
* Cline (JetBrains, VS Code, Cursor)
* Curseur
* Copilote GitHub (JetBrains, VS Code)
* Kiro (application de bureau, interface de ligne de commande)
* Codex OpenAI (application de bureau)
* Interface de ligne de commande du Codex OpenAI
* Planche à voile

### Plateformes d’entreprise {#enterprise-platforms}

* Microsoft Copilot Studio

## Présentation de la configuration {#setup-overview}

La configuration de MCP pour AEM comprend deux parties principales :

1. **Configurez chaque application cliente MCP** de sorte que l’application sache comment se connecter aux serveurs MCP AEM et se connecter à OAuth.
1. **Sélectionnez le serveur MCP** avant de démarrer l&#39;invite, de sorte que le client MCP sache l&#39;utiliser.

Des guides détaillés couvrant les deux étapes sont disponibles pour :

* [Anthropic Claude (à la fois pour la configuration manuelle des serveurs MCP et l’installation du connecteur AEM Claude)](/help/ai-in-aem/mcp-support/setup-claude.md)
* [OpenAI ChatGPT](/help/ai-in-aem/mcp-support/setup-chatgpt.md)
* [Curseur](/help/ai-in-aem/mcp-support/setup-cursor.md)
* [JetBrains avec Copilote GitHub](/help/ai-in-aem/mcp-support/setup-jetbrains-copilot.md)
* [Microsoft Copilot Studio](/help/ai-in-aem/mcp-support/setup-microsoft-copilot-studio.md)

### Configuration AEM {#aem-configuration}

Par défaut, les autorisations dont disposent les utilisateurs individuels dans AEM régissent l’accès aux serveurs MCP d’AEM. Lorsqu’un utilisateur s’authentifie via une application cliente MCP, les outils MCP appliquent les mêmes règles d’accès que les opérations manuelles dans AEM. Un utilisateur ne peut effectuer que les actions qu’il est déjà autorisé à effectuer.

#### Applications clientes MCP autorisées {#permitted-mcp-client-applications}

Toutes les applications répertoriées sous [&#x200B; Applications MCP prises en charge &#x200B;](#supported-mcp-applications) sont autorisées par défaut.

#### Restreindre les serveurs MCP {#restricting-mcp-servers}

Tous les serveurs MCP sont traités par défaut. En tant qu’administrateur, vous avez la possibilité de restreindre l’accès à des serveurs MCP spécifiques au niveau de l’organisation, du programme ou de l’environnement. Cette restriction vous donne un contrôle granulaire sur les fonctionnalités MCP disponibles pour les utilisateurs de votre entreprise.

#### Gestion de l’accès client MCP {#managing-mcp-client-access}

Les administrateurs peuvent également désactiver l’accès à des applications clientes MCP spécifiques si les politiques de votre entreprise l’exigent. Si vous souhaitez qu’Adobe active la prise en charge de produits clients MCP supplémentaires, envoyez un lien vers le site web du produit. Si vous devez placer sur la liste autorisée un client MCP personnalisé, contactez-le également.

Pour toutes les demandes liées au serveur MCP, n’hésitez pas à contacter Adobe à l’adresse **`aemcs-mcp-feedback@adobe.com`**

### Configuration de l’application cliente MCP {#mcp-client-application-configuration}

Chaque utilisateur effectue cette étape ou un administrateur de l’application cliente MCP peut l’effectuer lorsqu’elle est prise en charge. Les détails de configuration varient légèrement selon les applications. Les clients MCP évoluent rapidement et la prise en charge des serveurs MCP distants est activement développée. Vous devrez peut-être activer le mode Développeur pour accéder à la fonctionnalité d’ajout de serveurs distants, mais le processus général est le suivant :

1. Ajoutez une ou plusieurs URL de serveur MCP.
   * Configurez un ou plusieurs points d’entrée MCP à partir du tableau ci-dessus. Par exemple :`https://mcp.adobeaemcloud.com/adobe/mcp/content-readonly`
1. Déclenchez la connexion.
   * Enregistrez ou activez la configuration afin que l’application cliente MCP tente de se connecter au serveur MCP
1. Connectez-vous avec Adobe ID.
   * Lorsque vous y êtes invité, complétez le flux de connexion Adobe afin que l’application puisse obtenir des jetons OAuth liés à votre Adobe ID
1. Vérification des outils découverts.
   * Une fois authentifiée, l’application détecte les outils MCP à partir du serveur. Vous pouvez ensuite commencer à demander au LLM d’effectuer des opérations AEM.

Pour obtenir la liste complète des applications prises en charge[&#128279;](#supported-mcp-applications) voir Applications MCP prises en charge.

## Authentification {#authentication}

Les serveurs MCP hébergés par Adobe mettent en œuvre OAuth et sont intégrés au système d’identités d’Adobe.

* Lorsqu’une application cliente MCP se connecte à un serveur MCP, les utilisateurs voient une boîte de dialogue de connexion Adobe et s’authentifient avec leur **Adobe ID**
* Une fois la connexion établie, le système vérifie que l’application cliente MCP est autorisée dans votre organisation et que le serveur MCP demandé est autorisé. Si l’une de ces vérifications échoue, un message d’erreur s’affiche.

![Erreur Client MCP non autorisé &#x200B;](assets/MCP-Client-not-permitted.png)

* Une fois la vérification effectuée, le serveur MCP émet des jetons que l’application utilise pour les appels d’outil suivants.
* Les outils MCP respectent les autorisations AEM de l’utilisateur. Seuls les utilisateurs autorisés à modifier un fragment de contenu dans AEM peuvent le modifier via MCP.

Cette approche garantit que les opérations assistées par l’IA sont conformes à votre modèle de sécurité et de gouvernance AEM existant.

## Utilisation de MCP avec AEM {#using-mcp-with-aem}

Une fois AEM et vos applications clientes MCP configurées, vous pouvez travailler dans l’application de votre choix et demander au LLM d’effectuer des opérations AEM. Le LLM lit les schémas d’outils du MCP, sélectionne les outils à appeler et les séquence selon les besoins pour répondre à votre requête.

>[!IMPORTANT]
>
>Les invites qui contiennent plusieurs étapes ou ciblent différents types de contenu, tels que des images et du texte, fonctionnent mieux avec un modèle de pensée. Activez un modèle de réflexion ou sélectionnez l’option Réflexion dans votre client MCP au lieu de vous reposer sur le mode automatique.

### Exemples de cas d’utilisation {#example-use-cases}

Voici quelques scénarios représentatifs :

* Découverte de l’environnement
   * Répertoriez les environnements et les licences pour décider où exécuter un workflow.
* Gestion des sites
   * Liste des sites
   * Créer, lire, mettre à jour et supprimer des pages et du contenu de page.
* Gestion des fragments de contenu
   * Rechercher des fragments de contenu
   * Création de fragments
   * Mettre à jour les fragments existants lorsque les messages de campagne changent.
* Importation de ressources
   * Importation de ressources avec vérification de l’état
* Recherche de ressources

  >[!NOTE]
  >
  >Envoyez un e-mail à `aemagentsteam@adobe.com` pour activer la recherche de ressources. Incluez le nom de l’organisation ainsi que le cas d’utilisation dans l’e-mail.

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

```
"Create a new content fragment for the spring campaign based on our hero banner model and fill in its fields from this brief."
```

Le LLM choisit et coordonne automatiquement les outils MCP nécessaires.

## Gestion des attentes {#expectation-management}

Lorsque vous travaillez avec des LLM par le biais de MCP, tenez compte des points suivants :

* **Hautement compétents mais non infaillibles** - Les LLM peuvent accomplir des tâches complexes, mais sont sujets à des erreurs occasionnelles. Une même invite peut donner des résultats ou des présentations légèrement différents sans raison évidente. Examinez toujours les sorties avant d’appliquer des modifications au contenu de production.
* **Évolution des capacités** - Les modèles de gestion du cycle de vie des informations s’améliorent constamment. Au fil du temps, ils deviennent plus intelligents et découvrent de nouvelles façons de combiner les outils MCP pour atteindre vos objectifs. Une tâche qui nécessitait plusieurs invites aujourd&#39;hui peut fonctionner de manière transparente avec une seule invite demain.
* **La supervision humaine est essentielle** - Considérez le LLM comme un assistant averti qui a besoin d’être supervisé. Elle possède une connaissance étendue et peut concevoir des solutions créatives, mais elle bénéficie de vos conseils et de votre examen. Vérifiez les résultats, en particulier pour les opérations critiques, et envoyez des commentaires lorsque la sortie ne correspond pas à vos attentes.
* **Soyez prudent avec les exécutions d’outils de reconnaissance automatique** - Certaines applications clientes MCP, telles que Claude, offrent la possibilité de reconnaître automatiquement les exécutions d’outils demandées par le LLM. Bien que cette option soit pratique pour les opérations en lecture seule telles que la recherche ou la récupération de contenu, soyez prudent avec les outils qui mettent à jour ou suppriment du contenu. Examinez chaque demande d’exécution d’outil avant de confirmer les actions qui modifient votre environnement AEM.

## Limites {#limitations}

AEM prend actuellement en charge la configuration des serveurs MCP dans les applications répertoriées sous [Applications MCP prises en charge](#supported-mcp-applications).

Si vous souhaitez utiliser une autre application cliente MCP, n&#39;hésitez pas à communiquer avec **`aemcs-mcp-feedback@adobe.com`** pour demander de l&#39;aide pour d&#39;autres clients ou pour en placer sur la liste autorisée une personnalisée.
