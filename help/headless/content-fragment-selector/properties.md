---
title: Propriétés du sélecteur de fragment de contenu micro front-end pour Adobe Experience Manager as a Cloud Service
description: Propriétés pour configurer le sélecteur de fragments de contenu micro front-end afin de rechercher, rechercher et récupérer des fragments de contenu de votre application.
role: Admin, User
exl-id: c81b5256-09fb-41ce-9581-f6d1ad316ca4
source-git-commit: 58995ae9c29d5a76b3f94de43f2bafecdaf7cf68
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 4%

---

# Sélecteur de fragment de contenu - Propriétés connexes {#content-fragment-selector-related-properties}

Le sélecteur de fragment de contenu micro front-end vous permet de parcourir ou de rechercher des fragments de contenu dans le référentiel et de les utiliser dans votre application.

Vous pouvez utiliser les propriétés suivantes pour personnaliser le rendu du sélecteur de fragment de contenu et son utilisation :

## Propriétés du sélecteur de fragment de contenu {#content-fragment-selector-properties}

| Propriété | Type | Requis | Valeur par défaut | Description |
|--- |--- |--- |--- |--- |
| `ref` | FragmentSelectorRef | | | Référence à l’instance `ContentFragmentSelector`, permettant l’accès aux fonctionnalités fournies telles que `reload`. |
| `imsToken` | chaîne | Non | | Jeton IMS utilisé pour l’authentification. S’il n’est pas fourni, le flux de connexion IMS est lancé. |
| `repoId` | chaîne | Non | | ID de référentiel utilisé pour le sélecteur de fragments. Lorsqu’il est fourni, le sélecteur se connecte automatiquement au référentiel spécifié et la liste déroulante du référentiel est masquée. S’il n’est pas fourni, l’utilisateur peut sélectionner un référentiel dans la liste des référentiels auxquels il a accès. |
| `defaultRepoId` | chaîne | Non | | Identifiant du référentiel qui sera sélectionné par défaut lorsque le sélecteur de référentiel s’affiche. Utilisé uniquement lorsque `repoId` n’est pas fourni. Si `repoId` est défini, le sélecteur de référentiel est masqué et cette valeur est ignorée. |
| `orgId` | chaîne | Non | | Identifiant de l’organisation utilisé pour l’authentification. S’il n’est pas fourni, l’utilisateur peut sélectionner un référentiel parmi les différentes organisations auxquelles il a accès. Si l’utilisateur ou l’utilisatrice n’a accès à aucun référentiel ou organisation, le contenu n’est pas chargé. |
| `locale` | chaîne | Non | « en-US » | Paramètre régional. |
| `env` | chaîne | Non | | Environnement de déploiement. Voir le type de `Env` pour les noms d’environnement autorisés. |
| `filters` | FragmentFilter | Non | `{ folder: "/content/dam" }` | Filtres à appliquer sur la liste des fragments de contenu. Par défaut, les fragments situés sous `/content/dam` s’affichent. |
| `isOpen` | booléen | Non | `false` | Indicateur utilisé pour spécifier si le sélecteur est ouvert ou fermé. |
| `noWrap` | booléen | Non | `false` | Détermine si le sélecteur de fragments est rendu sans boîte de dialogue d’encapsulation. Lorsqu’il est défini sur `true`, le sélecteur de fragments est directement incorporé au conteneur parent. Utile pour intégrer le sélecteur dans des mises en page ou des workflows personnalisés. |
| `onSelectionChange` | ({ contentFragments : `ContentFragmentSelection`, domainName ? : `string`, tenantInfo ? : `string`, repoId ? : `string`, deliveryRepos ? : `DeliveryRepository[]` }) => void | Non | | Fonction de rappel déclenchée à chaque modification de la sélection de fragments de contenu. Fournit les fragments actuellement sélectionnés, le nom de domaine, les informations du client, l’identifiant de référentiel et les référentiels de diffusion. |
| `onDismiss` | () => void | Non | | Fonction de rappel déclenchée lorsque l’action d’ignorance est effectuée (par exemple, fermeture du sélecteur). |
| `onSubmit` | ({ contentFragments : `ContentFragmentSelection`, domainName ? : `string`, tenantInfo ? : `string`, repoId ? : `string`, deliveryRepos ? : `DeliveryRepository[]` }) => void | Non | | Fonction de rappel déclenchée lorsque l’utilisateur confirme sa sélection. Reçoit les fragments de contenu sélectionnés, le nom de domaine, les informations du client, l’identifiant de référentiel et les référentiels de diffusion. |
| `theme` | « clair » ou « sombre » | Non | | Thème du sélecteur de fragments. Par défaut, il est défini sur le thème de l’environnement unifiedShell. |
| `selectionType` | « single » ou « multiple » | Non | `single` | Le type de sélection peut être utilisé pour restreindre la sélection du sélecteur de fragments. |
| `dialogSize` | « fullscreen » ou « fullscreenTakeover » | Non | `fullscreen` | Prop facultative pour contrôler la taille de la boîte de dialogue. |
| `runningInUnifiedShell` | booléen | Non | | Si DestinationSelector s’exécute sous UnifiedShell ou en mode autonome. |
| `readonlyFilters` | ResourceReadonlyFiltersField[] | Non | | Filtres en lecture seule appliqués à la liste des fragments de contenu. Ces filtres ne peuvent pas être supprimés par l’utilisateur. |
| `selectedFragments` | ContentFragmentIdentifier[] | Non | `[]` | Sélection initiale des fragments de contenu à présélectionner à l’ouverture du sélecteur. |
| `hipaaEnabled` | booléen | Non | `false` | Indique si la conformité HIPAA est activée. |
| `inventoryView` | InventoryViewType | Non | `table` | Type de vue par défaut du stock à utiliser dans le sélecteur. |
| `inventoryViewToggleEnabled` | booléen | Non | `false` | Indique si le bouton (bascule) de la vue d&#39;inventaire est activé, ce qui permet à l&#39;utilisateur de basculer entre les vues tableau et grille. |

## Propriétés ImsAuthProps {#imsauthprops-properties}

Les propriétés `ImsAuthProps` définissent les informations d’authentification et le flux que le sélecteur de fragment de contenu utilise pour obtenir une `imsToken`. En définissant ces propriétés, vous pouvez contrôler le comportement du flux d’authentification et enregistrer des écouteurs pour divers événements d’authentification.

| Nom de la propriété | Description |
|--- |--- |
| `imsClientId` | Valeur de chaîne représentant l’identifiant client IMS utilisé à des fins d’authentification. Cette valeur est fournie par Adobe et est spécifique à votre organisation Adobe AEM CS. |
| `imsScope` | Décrit les portées utilisées dans l’authentification. Les portées déterminent le niveau d’accès de l’application aux ressources de votre organisation. Plusieurs portées peuvent être séparées par des virgules. |
| `redirectUrl` | Représente l’URL de redirection de l’utilisateur après l’authentification. Cette valeur est généralement définie sur l’URL actuelle de l’application. Si un `redirectUrl` n’est pas fourni, `ImsAuthService` utilisera l’URL de redirection utilisée pour enregistrer le `imsClientId` |
| `modalMode` | Valeur booléenne indiquant si le flux d’authentification doit être affiché dans une fenêtre modale (pop-up) ou non. S’il est défini sur `true`, le flux d’authentification s’affiche dans un pop-up. S’il est défini sur `false`, le flux d’authentification s’affiche lors d’un rechargement complet de la page.<br>**Remarque :** pour une meilleure expérience utilisateur, vous pouvez contrôler dynamiquement cette valeur si le pop-up du navigateur est désactivé. |
| `onImsServiceInitialized` | Une fonction de rappel appelée lors de l’initialisation du service d’authentification Adobe IMS. Cette fonction accepte un paramètre, `service`, qui est un objet représentant le service Adobe IMS. Voir [`ImsAuthService`](#imsauthservice-ims-auth-service) pour plus d’informations. |
| `onAccessTokenReceived` | Une fonction de rappel appelée lorsqu’un `imsToken` est reçu du service d’authentification Adobe IMS. Cette fonction accepte un paramètre, `imsToken`, qui est une chaîne représentant le jeton d’accès. |
| `onAccessTokenExpired` | Fonction de rappel appelée lorsqu’un jeton d’accès a expiré. Cette fonction est généralement utilisée pour déclencher un nouveau flux d’authentification afin d’obtenir un nouveau jeton d’accès. |
| `onErrorReceived` | Une fonction de rappel appelée lorsqu’une erreur se produit lors de l’authentification. Cette fonction utilise deux paramètres : le type d’erreur et le message d’erreur. Le type d’erreur est une chaîne représentant le type d’erreur et le message d’erreur est une chaîne représentant le message d’erreur. |

## Propriétés ImsAuthService {#imsauthservice-properties}

La classe `ImsAuthService` gère le flux d’authentification pour le sélecteur de fragment de contenu. Il est chargé d’obtenir un `imsToken` du service d’authentification Adobe IMS. Le `imsToken` permet d’authentifier l’utilisateur et d’autoriser l’accès au référentiel CS de Adobe Experience Manager (AEM). ImsAuthService utilise les propriétés `ImsAuthProps` pour contrôler le flux d’authentification et enregistrer des écouteurs pour divers événements d’authentification. Vous pouvez utiliser la fonction `registerContentFragmentSelectorAuthService` pratique pour enregistrer l’instance `ImsAuthService` avec le sélecteur de fragment de contenu. Les fonctions suivantes sont disponibles dans la classe `ImsAuthService`. Cependant, si vous utilisez la fonction `registerContentFragmentSelectorAuthService`, vous n’avez pas besoin d’appeler directement ces fonctions.

| Nom de la fonction | Description |
|--- |--- |
| `isSignedInUser` | Détermine si l’utilisateur est actuellement connecté au service et renvoie une valeur booléenne en conséquence. |
| `getImsToken` | Récupère les `imsToken` d’authentification de l’utilisateur actuellement connecté, qui peuvent être utilisées pour authentifier les requêtes adressées à d’autres services, tels que la génération de ressources _rendu._ |
| `signIn` | Lance le processus de connexion de l’utilisateur. Cette fonction utilise le `ImsAuthProps` pour afficher l’authentification dans un pop-up ou un rechargement complet de la page. |
| `signOut` | Déconnecte l’utilisateur du service, invalide son jeton d’authentification et exige qu’il se reconnecte pour accéder aux ressources protégées. Appeler cette fonction recharge la page active. |
| `refreshToken` | Actualise le jeton d’authentification de l’utilisateur actuellement connecté, ce qui empêche son expiration et garantit un accès ininterrompu aux ressources protégées. Renvoie un nouveau jeton d’authentification pouvant être utilisé pour les requêtes suivantes. |
