---
title: Règlement sur la protection et la confidentialité des données – Niveau de préparation d’Adobe Experience Manager as a Cloud Service Sites
description: Découvrez la prise en charge d’Adobe Experience Manager as a Cloud Service Sites relative aux différents règlements sur la protection et la confidentialité des données ; notamment le Règlement général sur la protection des données (RGPD) de l’UE et la Loi sur la protection de la vie privée des consommateurs de Californie, ainsi que la manière de se conformer à ces règlements lors de la mise en œuvre d’un nouveau projet AEM as a Cloud Service.
exl-id: fdcad111-0cdd-46cc-964c-3f8669ca2030
source-git-commit: e9c1ec6807f86ab00f89ef292a89a0c8efdf802b
workflow-type: tm+mt
source-wordcount: '1032'
ht-degree: 100%

---

# Niveau de préparation d’Adobe Experience Manager as a Cloud Service Sites aux réglementations sur la protection et la confidentialité des données {#aem-sites-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>Le contenu de ce document ne constitue pas un avis juridique et ne vise pas à le remplacer.
>
>Consultez le service juridique de votre entreprise pour obtenir des conseils concernant les réglementations sur la protection des données et la confidentialité des données.

>[!NOTE]
>
>Pour plus d’informations sur la réponse d’Adobe à ces questions de données personnelles et sur ce que cela signifie pour vous en tant que client Adobe, consultez le [Centre de traitement des données personnelles d’Adobe](https://www.adobe.com/fr/privacy.html).

Adobe Experience Manager as a Cloud Service Sites est prêt à accompagner ses clients pour les aider à respecter leurs obligations en matière de confidentialité et de protection des données. Cette page guide les clients à travers les procédures de gestion des demandes RGPD dans AEM Sites. Elle décrit l’emplacement des données privées stockées et la procédure pour les supprimer manuellement ou à l’aide de code.

Pour plus d’informations, consultez le [Centre de traitement des données personnelles d’Adobe](https://www.adobe.com/privacy.html).

>[!NOTE]
>
>Consultez [Niveau de préparation d’Adobe Experience Manager as a Cloud Service Sites aux réglementations sur la protection et la confidentialité des données](/help/compliance/data-privacy-and-protection-readiness/aem-readiness.md) pour plus d’informations.

## Niveau de création AEM {#aem-author-tier}

Les comptes utilisateur et le contenu généré par les utilisateurs sur le serveur de création sont abordés dans la [documentation d’AEM Foundation](/help/compliance/data-privacy-and-protection-readiness/foundation-readiness.md).

## Niveau de publication AEM {#aem-publish-tier}

Les comptes utilisateur utilisés pour authentifier les visiteurs sur le site et le contenu généré par les utilisateurs sur le serveur de publication sont abordés dans la [documentation d’AEM Foundation](/help/compliance/data-privacy-and-protection-readiness/aem-readiness.md).

Par défaut, les composants AEM Sites ne stockent pas les données de formulaires saisies par les visiteurs sur le serveur de publication. Il est recommandé de transférer les données vers un système tiers ou vers Adobe Campaign pour traitement ultérieur.

## Souscription/exclusion {#opt-in-opt-out}

<!--
AEM has a [cookie opt-out service](/help/sites-developing/cookie-optout.md ) that can be used for managing the opt-in/opt-out for users.
-->

Adobe Experience Manager est soumis à un service d’exclusion des cookies utilisé pour gérer l’inclusion ou l’exclusion des utilisateurs.

Pour l’exclusion :

1. Accédez à :
   [Centre de traitement des données personnelles Adobe – Exclusion](https://www.adobe.com/fr/privacy/opt-out.html)

1. Faites défiler l’écran jusqu’à **Services** – **Données d’utilisation du service Experience Cloud**.

1. Sélectionnez le lien référencé ; actuellement intitulé **ici**.

1. Les informations suivantes s’affichent, ainsi que les options d’exclusion ou d’inclusion :

   * Pour exclure l’agrégation et l’analyse des données relatives à votre visite sur ce site, il est nécessaire d’installer un cookie sur votre navigateur. Ce cookie identifie que vous avez choisi l’exclusion.

      Si vous supprimez le cookie d’exclusion, ou si vous changez d’ordinateur ou de navigateur web, vous devez procéder à nouveau à l’exclusion.

      Exclusion : excluez-moi de l’agrégation et de l’analyse des sessions visiteur (installez le cookie d’exclusion `amcglobal.sc.omtrdc.net`) – Cliquez ici.

      Inclusion : incluez-moi dans l’agrégation et l’analyse des sessions visiteur (n’installez pas le cookie d’exclusion `amcglobal.sc.omtrdc.net`) – Cliquez ici.
   Suivez les étapes ci-dessus pour accéder aux liens réels.

   >[!NOTE]
   >
   > Une description supplémentaire est disponible dans la section **2. Confidentialité.** des Conditions générales d’utilisation d’[Adobe](https://www.adobe.com/fr/legal/terms.html).

## Analytics Foundation {#analytics-foundation}

AEM Sites comprend une intégration facultative à Analytics Foundation qui utilise la fonctionnalité incluse dans le service On-demand d’Adobe Analytics.

Pour plus d’informations sur la gestion des requêtes RGPD des personnes titulaires de ces données liées à Adobe Analytics, voir [Adobe Analytics et la confidentialité des données](https://experienceleague.adobe.com/docs/analytics/admin/data-governance/gdpr-view-settings.html?lang=fr).

## Personalization Foundation by Target {#personalization-foundation-by-target}

AEM Sites comprend une intégration facultative à Personalization Foundation by Target utilisant la fonctionnalité incluse dans le service On-demand Adobe Target.

Pour plus d’informations sur la gestion des requêtes des personnes titulaires de ces données liées à Adobe Target, consultez [Adobe Target : Confidentialité et Règlement général sur la protection des données (RGPD)](https://experienceleague.adobe.com/docs/target/using/implement-target/before-implement/privacy/cmp-privacy-and-general-data-protection-regulation.html?lang=fr).

## ContextHub {#contexthub}

<!--
AEM provides an optional data layer with [ContextHub](/help/sites-developing/contexthub.md).
-->

AEM fournit une couche de données facultative avec ContextHub. Cette option conserve les données spécifiques aux visiteurs dans le navigateur, afin qu’elles soient utilisées pour la personnalisation basée sur des règles.

Par défaut, ces données sur les visiteurs ne sont pas stockées dans AEM ; AEM envoie des règles à la couche de données de façon à prendre des décisions de personnalisation dans le navigateur.

### Mise en œuvre de la souscription/l’exclusion {#implementing-opt-in-opt-out}

Le propriétaire du site doit mettre en œuvre un composant d’exclusion en suivant les instructions ci-après.

Ces instructions mettent en œuvre la souscription comme valeur par défaut. Ainsi, un visiteur du site web doit clairement donner son accord avant que toute donnée personnelle soit stockée dans la persistance du navigateur (côté client).

* Le composant d’exclusion doit être inclus à chaque fois que le composant ContextHub est inclus.
* Les conditions qui renvoient à la protection et à la confidentialité des données pour le site web doivent être présentées à ce visiteur du site web, afin de lui permettre :

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
   * Internet Explorer :

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

   * `ContextHub.Utils.Persistence.Modes.LOCAL` (par défaut)
   * `ContextHub.Utils.Persistence.Modes.SESSION`
   * `ContextHub.Utils.Persistence.Modes.COOKIE`
   * `ContextHub.Utils.Persistence.Modes.WINDOW`
