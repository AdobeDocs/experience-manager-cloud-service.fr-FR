---
title: Règles relatives à la protection des données et à la confidentialité des données - Adobe Experience Manager comme outil de préparation des sites de services Cloud
description: 'Découvrez la prise en charge d’Adobe Experience Manager en tant que sites de services Cloud pour les différentes réglementations sur la protection des données et la confidentialité des données ; y compris le règlement général de protection des données (RDPC) de l’UE, la loi sur la protection des renseignements personnels des consommateurs de Californie et la façon de s’y conformer lors de la mise en oeuvre d’un nouveau projet AEM en tant que service cloud. '
translation-type: tm+mt
source-git-commit: 1130e8a07bc3826380483a7560ebda7e8a17e238

---


# Adobe Experience Manager en tant que site de services Cloud - Règles de préparation pour la protection des données et la confidentialité des données {#aem-sites-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>Le contenu de ce document ne constitue pas un avis juridique et ne se substitue pas à un avis juridique.
>
>Veuillez consulter le service juridique de votre entreprise pour obtenir des conseils concernant les règles de protection des données et de confidentialité des données.

>[!NOTE]
>
>Pour plus d’informations sur la réponse d’Adobe aux problèmes de confidentialité et sur ce que cela signifie pour vous en tant que client Adobe, consultez le Centre [de confidentialité d’](https://www.adobe.com/privacy.html)Adobe.

Adobe Experience Manager en tant que sites de services Cloud est prêt à aider les clients à respecter leurs obligations en matière de confidentialité et de protection des données. Cette page guide les clients tout au long des procédures de traitement de ces demandes dans les sites AEM. Elle décrit l’emplacement des données privées stockées et la procédure pour les supprimer manuellement ou à l’aide de code.

Pour plus d’informations, consultez le Centre [de confidentialité](https://www.adobe.com/privacy.html)Adobe.

>[!NOTE]
>
>Pour plus d’informations, reportez-vous à la section [Adobe Experience Manager as a Cloud Service Readiness for Data Protection and Data Privacy Regulations](/help/onboarding/data-privacy-and-protection-readiness/aem-readiness.md) (en anglais).

## Niveau Auteur AEM {#aem-author-tier}

User accounts and UGC content on the author server are covered in the [AEM Foundation documentation](/help/onboarding/data-privacy-and-protection-readiness/aem-readiness.md).

## Niveau de publication AEM {#aem-publish-tier}

User accounts used to authenticate visitors on the site, and UGC content on the publish server are covered in the [AEM Foundation documentation](/help/onboarding/data-privacy-and-protection-readiness/aem-readiness.md).

Par défaut, les composants Sites AEM ne stockent pas les données de formulaire saisies par les visiteurs sur le serveur de publication. Il est recommandé de transférer les données vers un système tiers ou vers Adobe Campaign pour traitement ultérieur.

## Souscription/exclusion {#opt-in-opt-out}

<!--
AEM has a [cookie opt-out service](/help/sites-developing/cookie-optout.md ) that can be used for managing the opt-in/opt-out for users.
-->

Adobe Experience Manager fait l’objet d’un service d’exclusion des cookies utilisé pour gérer l’inclusion/exclusion des utilisateurs.

Pour exclure :

1. Accédez à:
   [Centre de traitement des données personnelles Adobe - Exclusion](https://www.adobe.com/privacy/opt-out.html)

1. Faites défiler l’écran jusqu’à **Services** - Données **d’utilisation du service** Experience Cloud.

1. Sélectionnez le lien référencé ; actuellement intitulé **ici**.

1. Vous recevrez les détails suivants, ainsi que les options d’exclusion ou d’inclusion :

   * Pour exclure l’agrégation et l’analyse des données relatives à votre visite sur ce site, vous devez installer un cookie dans votre navigateur. Ce cookie identifie que vous avez choisi de ne pas participer.

      Si vous supprimez le cookie d’exclusion, ou si vous changez d’ordinateur ou de navigateur Web, vous devrez à nouveau vous désinscrire.

      Exclusion : excluez-moi de l’agrégation et de l’analyse des sessions des visiteurs (installez le cookie d’exclusion) - Cliquez ici. `amcglobal.sc.omtrdc.net`

      Exclusion - Incluez-moi dans l’agrégation et l’analyse des sessions des visiteurs (n’installez pas le cookie d’exclusion) - Cliquez ici. `amcglobal.sc.omtrdc.net`
   Suivez les étapes ci-dessus pour accéder aux liens réels.

   >[!NOTE]
   >
   > La section Politique **de** confidentialité des [Conditions d&#39;utilisation](https://marketing.adobe.com/resources/help/en_US/terms.html)contient une description plus détaillée.

## Analytics Foundation {#analytics-foundation}

Les sites AEM incluent une intégration facultative avec Analytics Foundation qui utilise les fonctionnalités du service à la demande Adobe Analytics.

For further information on managing data subject requests related to Adobe Analytics see [Adobe Analytics and Data Privacy](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/gdpr-view-settings.html).

## Fondation de la personnalisation par Target {#personalization-foundation-by-target}

Les sites AEM incluent une intégration facultative à la base de personnalisation par Target, qui utilise les fonctionnalités du service à la demande Adobe Target.

For further information on managing data subject requests related to Adobe Target see [Adobe Target - Privacy and General Data Protection Regulation](https://marketing.adobe.com/resources/help/en_US/target/target/privacy-and-general-data-protection-regulation.html).

## ContextHub {#contexthub}

<!--
AEM provides an optional data layer with [ContextHub](/help/sites-developing/contexthub.md).
-->

AEM fournit une couche de données facultative avec ContextHub. Cette option conserve les données spécifiques aux visiteurs dans le navigateur, afin qu’elles soient utilisées pour la personnalisation basée sur des règles.

Par défaut, ces données sur les visiteurs ne sont pas stockées dans AEM ; AEM envoie des règles à la couche de données de façon à prendre des décisions de personnalisation dans le navigateur.

### Mise en œuvre de la souscription/l’exclusion {#implementing-opt-in-opt-out}

Le propriétaire du site doit mettre en œuvre un composant d’exclusion en suivant les instructions ci-après.

Ces instructions mettent en œuvre la souscription comme valeur par défaut. Ainsi, le visiteur du site Web doit être clairement d’accord avant que les données personnelles ne soient stockées dans la persistance (côté client) du navigateur.

* Le composant d’exclusion doit être inclus à chaque fois que le composant ContextHub est inclus.
* Les termes et conditions relatifs à la protection des données et à la confidentialité du site Web doivent être affichés au visiteur du site Web, ce qui lui permet de :

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

   * Chrome :

      * Ouvrez Outils de développement > Application > Stockage :

         * Stockage local > (site web) > ContextHubPersistence
         * Stockage de session > (site web) > ContextHubPersistence
         * Cookies > (site web) > SessionPersistence
   * Firefox :

      * Ouvrez Outils de développement > Stockage :

         * Stockage local > (site web) > ContextHubPersistence
         * Stockage de session > (site web) > ContextHubPersistence
         * Cookies > (site web) > SessionPersistence
   * Safari :

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

      * `ContextHub.Utils.Persistence.Modes.LOCAL` (default)
      * `ContextHub.Utils.Persistence.Modes.SESSION`
      * `ContextHub.Utils.Persistence.Modes.COOKIE`
      * `ContextHub.Utils.Persistence.Modes.WINDOW`
      Le magasin ContextHub définit la couche de persistance utilisée pour afficher l’état actuel de la persistance. Toutes les couches devraient être cochées.


Par exemple, pour afficher les données enregistrées dans le stockage local :

```
var storage = new ContextHub.Utils.Persistence({ mode: ContextHub.Utils.Persistence.Modes.LOCAL });
console.log(storage.getTree());
```

### Effacement de la persistance de ContextHub {#clearing-persistence-of-contexthub}

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

   * `ContextHub.Utils.Persistence.Modes.LOCAL` (default)
   * `ContextHub.Utils.Persistence.Modes.SESSION`
   * `ContextHub.Utils.Persistence.Modes.COOKIE`
   * `ContextHub.Utils.Persistence.Modes.WINDOW`
