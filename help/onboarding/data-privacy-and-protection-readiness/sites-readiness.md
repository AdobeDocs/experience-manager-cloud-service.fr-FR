---
title: Règlement sur la protection et la confidentialité des données - Préparation d’Adobe Experience Manager en tant que Cloud Service Sites
description: Découvrez la prise en charge d’Adobe Experience Manager as a Cloud Service Sites pour les différents règlements sur la protection et la confidentialité des données ; notamment le règlement général sur la protection des données (RGPD) de l’UE, la loi sur la protection de la vie privée des consommateurs de Californie et la manière de se conformer lors de la mise en oeuvre d’une nouvelle AEM en tant que projet Cloud Service.
exl-id: fdcad111-0cdd-46cc-964c-3f8669ca2030
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '1036'
ht-degree: 43%

---

# Adobe Experience Manager en tant que site Cloud Service Préparation aux réglementations sur la protection et la confidentialité des données {#aem-sites-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>Le contenu de ce document ne constitue pas un avis juridique et ne vise pas à remplacer un avis juridique.
>
>Veuillez consulter le service juridique de votre entreprise pour obtenir des conseils concernant les réglementations sur la protection des données et la confidentialité des données.

>[!NOTE]
>
>Pour plus d’informations sur la réponse de l’Adobe aux problèmes de confidentialité et sur ce que cela signifie pour vous en tant que client Adobe, voir [Centre de traitement des données personnelles de l’Adobe](https://www.adobe.com/privacy.html).

Adobe Experience Manager as a Cloud Service Sites est prêt à aider les clients à respecter leurs obligations en matière de confidentialité et de protection des données. Cette page guide les clients à travers les procédures de gestion de ces requêtes dans AEM Sites. Elle décrit l’emplacement des données privées stockées et la procédure pour les supprimer manuellement ou à l’aide de code.

Pour plus d’informations, voir [Centre de traitement des données personnelles des Adobes](https://www.adobe.com/privacy.html).

>[!NOTE]
>
>Voir [Adobe Experience Manager as a Cloud Service Readiness for Data Protection and Data Privacy regulation](/help/onboarding/data-privacy-and-protection-readiness/aem-readiness.md) pour plus d’informations.

## Niveau de création AEM {#aem-author-tier}

Les comptes utilisateur et le contenu généré par l’utilisateur sur le serveur de création sont traités dans la [documentation AEM Foundation](/help/onboarding/data-privacy-and-protection-readiness/aem-readiness.md).

## Niveau de publication AEM {#aem-publish-tier}

Les comptes utilisateur utilisés pour authentifier les visiteurs sur le site et le contenu généré par l’utilisateur sur le serveur de publication sont abordés dans la [documentation AEM Foundation](/help/onboarding/data-privacy-and-protection-readiness/aem-readiness.md).

Par défaut, les composants AEM Sites ne stockent pas les données de formulaire saisies par les visiteurs sur le serveur de publication. Il est recommandé de transférer les données vers un système tiers ou vers Adobe Campaign pour traitement ultérieur.

## Souscription/exclusion {#opt-in-opt-out}

<!--
AEM has a [cookie opt-out service](/help/sites-developing/cookie-optout.md ) that can be used for managing the opt-in/opt-out for users.
-->

Adobe Experience Manager est soumis à un service d’exclusion des cookies utilisé pour gérer l’inclusion/exclusion des utilisateurs.

Pour exclure :

1. Accédez à:
   [Centre de traitement des données personnelles des Adobes - Exclusion](https://www.adobe.com/privacy/opt-out.html)

1. Faites défiler l’écran jusqu’à **Services** - **Données d’utilisation du service Experience Cloud**.

1. Sélectionnez le lien référencé ; actuellement intitulé **ici**.

1. Les informations suivantes s’affichent, ainsi que les options d’exclusion ou de participation :

   * Pour exclure l’agrégation et l’analyse des données relatives à votre visite sur ce site, il est nécessaire d’installer un cookie sur votre navigateur. Ce cookie identifie que vous avez exercé votre droit d’opposition.

      Si vous supprimez le cookie d’exclusion, ou si vous changez d’ordinateur ou de navigateur Web, vous devez procéder à nouveau à l’exclusion.

      Exclusion : excluez-moi de l’agrégation et de l’analyse des sessions du visiteur (installez le `amcglobal.sc.omtrdc.net` cookie d’exclusion) - Cliquez ici.

      Opt-in : incluez-moi dans l’agrégation et l’analyse de la session du visiteur (n’installez pas le `amcglobal.sc.omtrdc.net` cookie d’exclusion) - Cliquez ici.
   Suivez les étapes ci-dessus pour accéder aux liens réels.

   >[!NOTE]
   >
   > La section **2 contient une description supplémentaire. Confidentiel.** de la section Conditions d’utilisation générales de l’ [Adobe](https://www.adobe.com/fr/legal/terms.html).

## Analytics Foundation {#analytics-foundation}

AEM Sites comprend une intégration facultative avec Analytics Foundation qui utilise les fonctionnalités du service à la demande Adobe Analytics.

Pour plus d’informations sur la gestion des demandes des titulaires de données liées à Adobe Analytics, voir [Adobe Analytics et Confidentialité des données](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/gdpr-view-settings.html).

## Base de personnalisation par Target {#personalization-foundation-by-target}

AEM Sites comprend une intégration facultative avec Personalization Foundation par Target, qui utilise les fonctionnalités du service à la demande Adobe Target.

Pour plus d’informations sur la gestion des demandes des titulaires de données liées à Adobe Target, voir [Adobe Target - Confidentialité et Règlement général sur la protection des données](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/cmp-privacy-and-general-data-protection-regulation.html).

## ContextHub {#contexthub}

<!--
AEM provides an optional data layer with [ContextHub](/help/sites-developing/contexthub.md).
-->

AEM fournit une couche de données facultative avec ContextHub. Cette option conserve les données spécifiques aux visiteurs dans le navigateur, afin qu’elles soient utilisées pour la personnalisation basée sur des règles.

Par défaut, ces données sur les visiteurs ne sont pas stockées dans AEM ; AEM envoie des règles à la couche de données de façon à prendre des décisions de personnalisation dans le navigateur.

### Mise en œuvre de la souscription/l’exclusion {#implementing-opt-in-opt-out}

Le propriétaire du site doit mettre en œuvre un composant d’exclusion en suivant les instructions ci-après.

Ces instructions mettent en œuvre la souscription comme valeur par défaut. Ainsi, un visiteur du site web doit clairement accepter, avant que toute donnée personnelle ne soit stockée dans la persistance (côté client) du navigateur.

* Le composant d’exclusion doit être inclus à chaque fois que le composant ContextHub est inclus.
* Les conditions générales relatives à la protection des données et à la confidentialité du site web doivent être présentées au visiteur du site web, ce qui lui permet de :

   * d’accepter ;
   * de refuser ;
   * de modifier son choix précédent.

* Si un visiteur du site accepte les conditions du site, le cookie d’exclusion ContextHub doit être supprimé :

   ```
   ContextHub.Utils.Cookie.removeItem('cq-opt-out');
   ```

* Si un visiteur du site n’accepte pas les conditions du site, le cookie d’exclusion ContextHub doit être défini :

   ```
   ContextHub.Utils.Cookie.setItem('cq-opt-out', 1);
   ```

* Pour vérifier si ContextHub s’exécute en mode d’exclusion, l’appel suivant doit être effectué dans la console du navigateur :

   ```
   var isOptedOut = ContextHub.isOptedOut(true) === true;
   // if isOptedOut is true, ContextHub is running in opt-out mode
   ```

### Aperçu de la persistance de ContextHub {#previewing-persistence-of-contexthub}

Pour afficher un aperçu de la persistance utilisée par ContextHub, l’utilisateur peut :

* utiliser la console du navigateur, par exemple :

   * Chrome:

      * Ouvrez Outils de développement > Application > Stockage :

         * Stockage local > (site web) > ContextHubPersistence
         * Stockage de session > (site web) > ContextHubPersistence
         * Cookies > (site web) > SessionPersistence
   * Firefox:

      * Ouvrez Outils de développement > Stockage :

         * Stockage local > (site web) > ContextHubPersistence
         * Stockage de session > (site web) > ContextHubPersistence
         * Cookies > (site web) > SessionPersistence
   * Safari:

      * Ouvrez Préférences > Avancé > Afficher le menu Développement dans la barre de menus
      * Ouvrez Développement > Afficher la console JavaScript

         * Console > Stockage > Stockage local > (site web) > ContextHubPersistence
         * Console > Stockage > Stockage de session > (site web) > ContextHubPersistence
         * Console > Stockage > Cookies > (site web) > ContextHubPersistence
   * Internet Explorer:

      * Ouvrez Outils de développement > Console :

         * `localStorage.getItem('ContextHubPersistence')`
         * `sessionStorage.getItem('ContextHubPersistence')`
         * `document.cookie`




* utiliser l’API ContextHub dans la console du navigateur :

   * ContextHub fournit les couches de persistance des données suivantes :

      * `ContextHub.Utils.Persistence.Modes.LOCAL` (default)
      * `ContextHub.Utils.Persistence.Modes.SESSION`
      * `ContextHub.Utils.Persistence.Modes.COOKIE`
      * `ContextHub.Utils.Persistence.Modes.WINDOW`

      Le magasin ContextHub définit la couche de persistance utilisée pour afficher l’état actuel de la persistance. Toutes les couches devraient être cochées.


Par exemple, pour afficher les données enregistrées dans le stockage local :

Pour afficher un aperçu de la persistance utilisée par ContextHub, l’utilisateur peut :

* utiliser la console du navigateur :

   * Dans Chrome : ouvrez Outils de développement > Application > Stockage :

      * Stockage local > (site web) > ContextHubPersistence
      * Stockage de session > (site web) > ContextHubPersistence
      * Cookies > (site web) > SessionPersistence
   * Dans Firefox : ouvrez Outils de développement > Stockage :

      * Stockage local > (site web) > ContextHubPersistence
      * Stockage de session > (site web) > ContextHubPersistence
      * Cookies > (site web) > SessionPersistence


* utiliser l’API ContextHub dans la console du navigateur :

   * ContextHub fournit les couches de persistance des données suivantes :

      * `ContextHub.Utils.Persistence.Modes.LOCAL` (par défaut)
      * `ContextHub.Utils.Persistence.Modes.SESSION`
      * `ContextHub.Utils.Persistence.Modes.COOKIE`
      * `ContextHub.Utils.Persistence.Modes.WINDOW`

      Le magasin ContextHub définit la couche de persistance utilisée pour afficher l’état actuel de la persistance. Toutes les couches devraient être cochées.


Par exemple, pour afficher les données enregistrées dans le stockage local :

```
var storage = new ContextHub.Utils.Persistence({ mode: ContextHub.Utils.Persistence.Modes.LOCAL });
console.log(storage.getTree());
```

### Effacement de la persistance de ContextHub  {#clearing-persistence-of-contexthub}

Pour effacer la persistance de ContextHub :

* Pour effacer la persistance des magasins actuellement chargés :

   ```
   // in order to be able to fully access persistence layer, Opt-Out must be turned off
   ContextHub.Utils.Cookie.removeItem('cq-opt-out');
   
   // following call asks all currently loaded stores to clear their data
   ContextHub.cleanAllStores();
   
   // following call asks all currently loaded stores to set back default values (provided in their configs)
   ContextHub.resetAllStores();
   ```

* Pour effacer une couche spécifique de persistance, par exemple, sessionStorage :

   ```
   var storage = new ContextHub.Utils.Persistence({ mode: ContextHub.Utils.Persistence.Modes.SESSION });
   storage.setItem('/store', null);
   storage.setItem('/_', null);
   
   // to confirm that nothing is stored:
   console.log(storage.getTree());
   ```

* Pour effacer toutes les couches de persistance ContextHub, le code approprié doit être appelé pour l’ensemble des couches :

   * `ContextHub.Utils.Persistence.Modes.LOCAL` (par défaut)
   * `ContextHub.Utils.Persistence.Modes.SESSION`
   * `ContextHub.Utils.Persistence.Modes.COOKIE`
   * `ContextHub.Utils.Persistence.Modes.WINDOW`
