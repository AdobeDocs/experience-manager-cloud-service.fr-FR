---
title: Configurer des points d’entrée REST spécifiques à un environnement pour le même formulaire adaptatif | Adobe Experience Manager as a Cloud Service
description: Découvrez comment acheminer le même formulaire adaptatif vers différents points d’entrée d’envoi REST dans vos environnements de développement, d’évaluation et de production sans modifier le formulaire.
feature: Adaptive Forms, Core Components
role: User, Developer
badgeSaas: label="AEM Forms" type="Positive" tooltip="S’applique à AEM Forms)."
exl-id: 40410875-96d0-4728-8cbd-b1e1dfa438c4
source-git-commit: 8d60f09ffd3912f4a14df01baccf1c368a518a91
workflow-type: tm+mt
source-wordcount: '1098'
ht-degree: 3%

---


# Configurer des points d’entrée REST spécifiques à un environnement pour le même formulaire adaptatif

Lorsque vous promouvez un formulaire adaptatif du développement à l’évaluation en passant par la production, le formulaire doit généralement être envoyé à un point d’entrée REST *différent* dans chaque environnement, tandis que le formulaire lui-même reste identique. Le codage en dur de l’URL du point d’entrée dans l’action d’envoi du formulaire rompt cette étape, car la même URL accompagne ensuite le formulaire dans chaque environnement.

Cet article décrit comment conserver un seul formulaire adaptatif portable et faire en sorte que son action [Envoyer vers le point d’entrée REST](/help/forms/configure-submit-action-restpoint.md) soit résolue sur le point d’entrée correct dans chaque environnement. Le formulaire fait référence à une configuration REST *par nom* plutôt que par URL, et chaque environnement fournit sa propre valeur pour cette configuration.

## Conditions préalables {#prerequisites}

* Formulaire adaptatif basé sur les composants principaux.
* Un [&#x200B; Conteneur de configurations &#x200B;](/help/implementing/developing/introduction/configurations.md) créé via l’explorateur de configurations (**Outils** > **Général** > **Explorateur de configurations**) avec l’**Configurations cloud** activé.
* Autorisation d’accès à **Outils** > **Services cloud** et, pour la promotion, [Gestionnaire de packages](/help/implementing/developing/tools/package-manager.md) sur chaque environnement (ou un pipeline de déploiement Cloud Manager [&#128279;](/help/implementing/deploying/overview.md#deploying-content-packages-via-cloud-manager-and-package-manager)).

## Créer la configuration de service RESTful lors de l’évaluation {#create-rest-configuration}

>[!VIDEO](https://video.tv.adobe.com/v/3492383)

Sur l’instance d’auteur d’évaluation, créez la configuration nommée à laquelle votre formulaire fait référence. Définissez l’**URL du point d’entrée du service** sur le point d’entrée REST ou webhook pour l’évaluation.

1. Accédez à **Outils** > **Services cloud** > **Sources de données**.

1. Sélectionnez votre conteneur de configuration, puis sélectionnez **Créer**.

1. Dans l’onglet **Général**, indiquez un **Nom** pour la configuration (par exemple, `restTest`). Utilisez le *même* nom sur chaque environnement afin que le formulaire soit résolu de manière cohérente après la promotion.

1. Dans l’onglet **Paramètres d’authentification**, configurez :

   * **Sélectionnez le service RESTful** : **Point d’entrée du service**.
   * **Type de méthode** : **POST**.
   * **URL du point d’entrée du service** : URL du point d’entrée d’évaluation (par exemple, URL de webhook que vous utilisez pour tester les envois depuis l’évaluation).
   * **Type de contenu** par exemple, **Données de formulaire en plusieurs parties**.
   * **Type d’authentification** : selon les besoins de votre point d’entrée (par exemple, **Aucune** ou **Authentification de base**).

1. Sélectionnez **Enregistrer et fermer**.

## Pointez le formulaire adaptatif sur le conteneur de configuration . {#set-configuration-container}

>[!VIDEO](https://video.tv.adobe.com/v/3492384)

Lors de l’évaluation, associez le formulaire au conteneur de configuration qui contient votre configuration REST.

1. Dans **Forms et documents**, sélectionnez votre formulaire adaptatif et ouvrez **Propriétés**.

1. Dans l’onglet **De base**, définissez **Conteneur de configurations** sur le conteneur qui contient la configuration de votre service RESTful (par exemple, `/conf/restConfigTest`).

1. Sélectionnez **Enregistrer et fermer**.

## Configuration de l’action Envoyer vers le point d’entrée REST {#configure-submit-action}

>[!VIDEO](https://video.tv.adobe.com/v/3492385)

Lors de l’évaluation, configurez le formulaire à envoyer par le biais de la configuration REST nommée au lieu d’une URL codée en dur. Pour consulter la référence complète de l’action d’envoi, voir [Configurer un formulaire adaptatif pour l’action d’envoi de point d’entrée REST](/help/forms/configure-submit-action-restpoint.md).

1. Ouvrez le formulaire adaptatif pour le modifier, sélectionnez le composant **Conteneur de guides** et ouvrez ses propriétés **Conteneur de formulaires adaptatifs**.

1. Ouvrez l’onglet **Envoi** et, dans la liste déroulante **Action d’envoi**, sélectionnez **Envoyer vers le point d’entrée REST**.

1. Sous **Configuration de l’action**, sélectionnez **Activer la requête POST**.

1. Pour **Sélectionner une option**, choisissez **Configuration** (et non **URL**).

1. Sélectionnez la configuration nommée (par exemple, `restTest`) dans la liste.

1. Sélectionnez **Terminé**.

Le formulaire résout désormais son point d’entrée d’envoi par le biais de la configuration nommée plutôt qu’une URL fixe.

## Promouvoir le formulaire de l’évaluation à la production {#promote-across-environments}

Après avoir configuré et testé sur l’évaluation, déplacez le même formulaire et le même conteneur de configuration vers la production. Vous pouvez utiliser l’une des approches suivantes.

### Option 1 : approche auteur-package {#option-package}

>[!VIDEO](https://video.tv.adobe.com/v/3492386)

Utilisez cette option lorsque les auteurs et autrices gèrent le formulaire et la configuration directement dans chaque environnement.

1. Sur l’instance d’auteur **staging**, créez un package de contenu dans [Package Manager](/help/implementing/developing/tools/package-manager.md) qui inclut le formulaire et son conteneur de configuration, par exemple :

   * `/content/dam/formsanddocuments/<your-form-path>`
   * `/content/forms/af/<your-form-path>`
   * `/conf/<your-config-container>` (qui contient des `.../settings/cloudconfigs/fdm/<your-config>`)

1. Téléchargez le package et installez-le sur l’instance d’auteur **de production**.

>[!IMPORTANT]
>
>Le package installe la même configuration en production, y compris l’URL du point d’entrée du service **Service** à partir de l’évaluation. Ne laissez pas cette URL d’évaluation en place en production. Mettez à jour le point d’entrée en production après l’installation, comme décrit dans la section suivante.

### Option 2 : Approche de remplacement basée sur le contexte (recommandée pour l’automatisation) {#option-context-aware}

Utilisez cette option lorsque vous souhaitez une configuration empaquetée dont le point d’entrée, le nom d’utilisateur et le mot de passe sont résolus automatiquement par environnement, sans modification manuelle après le déploiement. Cette approche remplace les propriétés de configuration à l’aide des variables d’environnement Cloud Manager.

Pour les configurations REST, vous créez généralement des variables d’environnement pour les propriétés `serviceEndPoint`, `userName` et `password`, puis vous les référencez à partir d’un fichier de configuration `OsgiConfigurationOverrideProvider` dans votre projet.

Pour la procédure complète, voir [Configurations cloud contextuelles](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/forms/developing-for-cloud-service/context-aware-fdm).

## Mettre à jour l’URL du point d’entrée en production {#configure-endpoint-on-production}

>[!VIDEO](https://video.tv.adobe.com/v/3492387)

Après avoir installé le package en production, le formulaire adaptatif et la configuration REST **nom** (par exemple, `restTest`) correspondent à l’évaluation. L’**URL du point d’entrée du service** dans cette configuration pointe toujours vers le point d’entrée d’évaluation à partir du package. Ouvrez la configuration en production et remplacez-la par l’URL du point d’entrée de production.

1. Sur l’instance d’auteur **de production**, accédez à **Outils** > **Services cloud** > **Sources de données**.

1. Sélectionnez le conteneur de configurations que vous avez déployé (par exemple, `restConfigTest`), puis ouvrez la configuration nommée (par exemple, `restTest`).

1. Dans l’onglet **Paramètres d’authentification**, définissez **URL du point d’entrée du service** sur le point d’entrée REST de production ou webhook.

1. Sélectionnez **Enregistrer et fermer**.

Pendant le test, un inspecteur de requêtes, tel qu’un service de capture webhook, vous donne une URL unique par environnement afin que vous puissiez confirmer quel point d’entrée reçoit chaque envoi.

## Vérifier le routage {#verify}

>[!VIDEO](https://video.tv.adobe.com/v/3492388)

Envoyez le même formulaire d’évaluation et de production et confirmez chaque publication d’environnement à son propre point d’entrée, et non à l’URL de l’autre environnement.

1. Sur l’instance d’auteur **staging**, ouvrez le formulaire adaptatif et envoyez-le avec des données de test (par exemple, saisissez `stagetest` dans un champ de texte). Vérifiez que la requête POST arrive à l’URL **staging** **Service Endpoint** que vous avez configurée lors de l’évaluation.

1. Sur l’instance d’auteur **de production**, ouvrez le même formulaire adaptatif et envoyez-le avec des données de test (par exemple, saisissez `prodtest` dans un champ de texte). Vérifiez que la requête POST arrive à l’URL **de production** **de point d’entrée du service** que vous avez configurée en production, et non à l’URL d’évaluation.

1. Vérifiez que chaque requête utilise le type de contenu attendu (par exemple, **Données de formulaire en plusieurs parties**) et inclut les données de formulaire envoyées. Utilisez un véritable point d’entrée sécurisé (HTTPS) pour la production.

## Bonnes pratiques {#best-practices}

* Utilisez une configuration identique **nom** sur chaque environnement afin que le formulaire soit résolu de manière cohérente après la promotion.
* Conservez le point d’entrée **valeur** spécifique à l’environnement. Ne codez jamais en dur l’URL d’un seul environnement dans l’action d’envoi du formulaire.
* Pour les points d’entrée de production, assurez-vous que l’URL est sécurisée (HTTPS) et que le chemin de réception est configuré pour gérer la requête POST de manière appropriée pour votre modèle d’authentification.
* Privilégiez l’approche de remplacement basée sur le contexte lorsque vous souhaitez que le déploiement soit répétable et exempt de modifications manuelles après le déploiement.

## Articles connexes {#related-articles}

* [Configuration d’un formulaire adaptatif pour l’action d’envoi de point d’entrée REST](/help/forms/configure-submit-action-restpoint.md)
* [Configuration des sources de données](/help/forms/configure-data-sources.md)
* [Configurations cloud basées sur le contexte](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/forms/developing-for-cloud-service/context-aware-fdm)
* [Action Envoyer pour formulaire adaptatif](/help/forms/aem-forms-submit-action.md)

