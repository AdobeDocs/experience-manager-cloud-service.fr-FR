---
title: Règlement sur la protection des données et la confidentialité des données - Adobe Experience Manager en tant que site Cloud Service Prêt
description: 'Découvrez Adobe Experience Manager en tant que site Cloud Service pris en charge par les divers règlements sur la protection des données et la confidentialité des données ; y compris le règlement général de l''UE sur la protection des données (RGPD), la loi sur la protection des renseignements personnels des consommateurs de Californie et la façon de se conformer lors de la mise en oeuvre d''une nouvelle AEM en tant que projet Cloud Service. '
translation-type: tm+mt
source-git-commit: 7b5a427853075054d56bc7ea6569d5d839e282a1
workflow-type: tm+mt
source-wordcount: '1036'
ht-degree: 43%

---


# Adobe Experience Manager en tant que site Cloud Service Prêt pour la protection des données et la confidentialité des données {#aem-sites-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>Le contenu de ce document ne constitue pas un conseil juridique et ne se substitue pas à un conseil juridique.
>
>Veuillez consulter le service juridique de votre société pour obtenir des conseils sur les réglementations relatives à la protection des données et à la confidentialité des données.

>[!NOTE]
>
>Pour plus d&#39;informations sur la réponse des Adobes aux questions de confidentialité et sur ce que cela signifie pour vous en tant que client d&#39;Adobe, voir [Centre de confidentialité des Adobes](https://www.adobe.com/privacy.html).

Adobe Experience Manager en tant que site Cloud Service est prêt à aider les clients à respecter leurs obligations en matière de confidentialité et de protection des données. Cette page guide les clients tout au long des procédures de traitement de ces demandes en AEM Sites. Elle décrit l’emplacement des données privées stockées et la procédure pour les supprimer manuellement ou à l’aide de code.

Pour plus d&#39;informations, consultez le [Centre de confidentialité des Adobes](https://www.adobe.com/privacy.html).

>[!NOTE]
>
>Voir [Adobe Experience Manager as a Cloud Service Readiness for Data Protection and Data Privacy Regulations](/help/onboarding/data-privacy-and-protection-readiness/aem-readiness.md) pour plus de détails.

## Niveau de création AEM {#aem-author-tier}

Les comptes d’utilisateurs et le contenu du CDU sur le serveur d’auteur sont traités dans la [documentation de AEM Foundation](/help/onboarding/data-privacy-and-protection-readiness/aem-readiness.md).

## Niveau de publication AEM {#aem-publish-tier}

Les comptes utilisateur utilisés pour authentifier les visiteurs sur le site et le contenu UGC sur le serveur de publication sont traités dans la [documentation de AEM Foundation](/help/onboarding/data-privacy-and-protection-readiness/aem-readiness.md).

Par défaut, les composants AEM Sites ne stockent pas les données de formulaire saisies par les visiteurs sur le serveur de publication. Il est recommandé de transférer les données vers un système tiers ou vers Adobe Campaign pour traitement ultérieur.

## Souscription/exclusion {#opt-in-opt-out}

<!--
AEM has a [cookie opt-out service](/help/sites-developing/cookie-optout.md ) that can be used for managing the opt-in/opt-out for users.
-->

Adobe Experience Manager fait l’objet d’un service d’exclusion des cookies qui est utilisé pour gérer l’inclusion/exclusion des utilisateurs.

Pour exclure :

1. Accédez à:
   [Centre de traitement des données personnelles des Adobes - Exclusion](https://www.adobe.com/privacy/opt-out.html)

1. Faites défiler l&#39;écran jusqu&#39;à **Services** - **Données d&#39;utilisation du service Experience Cloud**.

1. Sélectionnez le lien référencé ; actuellement intitulé **ici**.

1. Vous recevrez les détails suivants, ainsi que les options pour opt-out ou dans :

   * Pour exclure l’agrégation et l’analyse des données relatives à votre visite sur ce site, il est nécessaire d’installer un cookie sur votre navigateur. Ce cookie identifie que vous avez choisi de ne pas participer.

      Si vous supprimez le cookie d’exclusion, ou si vous changez d’ordinateur ou de navigateur Web, vous devrez à nouveau vous désinscrire.

      Exclusion - Exclure mon compte de l&#39;agrégation et de l&#39;analyse des sessions du visiteur (installer le `amcglobal.sc.omtrdc.net` cookie d&#39;exclusion) - Cliquez ici.

      Inscription : incluez-moi dans l&#39;agrégation et l&#39;analyse des sessions de visiteur (n&#39;installez pas le `amcglobal.sc.omtrdc.net` cookie d&#39;exclusion) - Cliquez ici.
   Suivez les étapes ci-dessus pour accéder aux liens réels.

   >[!NOTE]
   >
   > La section **2 contient une autre description. Confidentiel.** de l&#39; [Adobe Conditions générales d&#39;utilisation](https://www.adobe.com/fr/legal/terms.html).

## Analytics Foundation {#analytics-foundation}

AEM Sites comprend une intégration facultative avec Analytics Foundation qui utilise les fonctionnalités du service Adobe Analytics On-demand.

Pour plus d&#39;informations sur la gestion des demandes de sujet de données liées à Adobe Analytics, voir [Adobe Analytics and Data Privacy](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/gdpr-view-settings.html).

## Fondation de la personnalisation par Cible {#personalization-foundation-by-target}

AEM Sites inclut une intégration facultative à la base de personnalisation par Cible qui utilise les fonctionnalités du service à la demande Adobe Target.

Pour plus d&#39;informations sur la gestion des demandes de personnes concernées liées à Adobe Target, voir [Adobe Target - Règlement sur la protection des données et la protection des données générales](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/cmp-privacy-and-general-data-protection-regulation.html).

## ContextHub {#contexthub}

<!--
AEM provides an optional data layer with [ContextHub](/help/sites-developing/contexthub.md).
-->

AEM fournit une couche de données facultative avec ContextHub. Cette option conserve les données spécifiques aux visiteurs dans le navigateur, afin qu’elles soient utilisées pour la personnalisation basée sur des règles.

Par défaut, ces données sur les visiteurs ne sont pas stockées dans AEM ; AEM envoie des règles à la couche de données de façon à prendre des décisions de personnalisation dans le navigateur.

### Mise en œuvre de la souscription/l’exclusion {#implementing-opt-in-opt-out}

Le propriétaire du site doit mettre en œuvre un composant d’exclusion en suivant les instructions ci-après.

Ces instructions mettent en œuvre la souscription comme valeur par défaut. Ainsi, un visiteur de site Web doit clairement accepter, avant que toute donnée personnelle ne soit stockée dans la persistance (côté client) du navigateur.

* Le composant d’exclusion doit être inclus à chaque fois que le composant ContextHub est inclus.
* Les termes et conditions relatifs à la protection des données et à la confidentialité du site Web doivent être affichés au visiteur du site Web, ce qui leur permet de :

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
