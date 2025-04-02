---
title: Propriétés du sélecteur de fragment de contenu micro front-end pour Adobe Experience Manager as a Cloud Service
description: Propriétés pour configurer le sélecteur de fragments de contenu micro front-end afin de rechercher, rechercher et récupérer des fragments de contenu de votre application.
role: Admin, User
source-git-commit: 32e1b3cef768b420f32b70202ddadc80db2b74e8
workflow-type: tm+mt
source-wordcount: '890'
ht-degree: 3%

---


# Sélecteur de fragment de contenu - Propriétés connexes {#content-fragment-selector-related-properties}

Le sélecteur de fragment de contenu micro front-end vous permet de parcourir ou de rechercher des fragments de contenu dans le référentiel et de les utiliser dans votre application.

Vous pouvez utiliser les propriétés suivantes pour personnaliser le rendu du sélecteur de fragment de contenu et son utilisation :

## Propriétés du sélecteur de fragment de contenu {#content-fragment-selector-properties}

| Propriété | Type | Requis | Valeur par défaut | Description |
|--- |--- |--- |--- |--- |
| `imsToken` | chaîne | Non | | Jeton IMS utilisé pour l’authentification. |
| `repoId` | chaîne | Non | | Identifiant du référentiel utilisé pour l’authentification. |
| `orgId` | chaîne | Oui | | Identifiant de l’organisation utilisé pour l’authentification. |
| `locale` | chaîne | Non | | Données de paramètres régionaux. |
| `env` | Environnement | Non | | Environnement de déploiement du sélecteur de fragments de contenu. |
| `filters` | FragmentFilter | Non | | Filtres à appliquer pour la liste des fragments de contenu. Par défaut, les fragments situés sous `/content/dam` s’affichent. Valeur par défaut : `{ folder: "/content/dam" }` |
| `isOpen` | booléen | Oui | `false` | Indicateur pour déclencher l’ouverture ou la fermeture du sélecteur. |
| `onDismiss` | () => void | Oui | | Fonction à appeler lorsque **Ignorer** est sélectionné. |
| `onSubmit` | ({ contentFragments : `{id: string, path: string}[]`, domainNames : `string[]` }) => void | Fonction à appeler lorsque l’option **Sélectionner** est utilisée après la sélection d’un ou de plusieurs fragments de contenu. <br><br>La fonction recevra :<br><ul><li> les fragments de contenu sélectionnés avec les champs `id` et `path` ;</li><li>et les noms de domaine liés à l’ID de programme et à l’ID d’environnement du référentiel, dont le statut est `ready` et l’`tier` de publication .</li></ul><br>En l’absence de noms de domaine, l’instance de publication sera utilisée comme domaine de secours. |
| `theme` | « light » | « sombre » | Non | | Thème du sélecteur de fragment de contenu. Le thème par défaut est défini sur le thème de l’environnement UnifiedShell. |
| `selectionType` | « célibataire » | « multiple » | Non | `single` | Type de sélection pouvant être utilisé pour restreindre la sélection du FragmentSelector. |
| `dialogSize` | « plein écran » | « fullscreenTakeover » | Non | `fullscreen` | Propriété facultative permettant de contrôler la taille de la boîte de dialogue. |
| `waitForImsToken` | booléen | Non | `false` | Indique si le sélecteur de fragment de contenu est rendu dans le contexte du flux SUSI et doit attendre que le `imsToken` soit prêt. |
| `imsAuthInfo` | ImsAuthInfo | Non | | Objet contenant les informations d’authentification IMS de l’utilisateur connecté. |
| `runningInUnifiedShell` | booléen | Non | | Indique si le sélecteur de fragment de contenu s’exécute sous UnifiedShell ou en mode autonome. |
| `readonlyFilters` | ResourceReadonlyFiltersField | Non | | Filtres en lecture seule pouvant être appliqués à la liste de contenu et ne pouvant pas être supprimés. |

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