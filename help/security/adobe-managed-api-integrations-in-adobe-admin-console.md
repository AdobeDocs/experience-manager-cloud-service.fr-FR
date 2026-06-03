---
title: Intégrations d’API gérées par Adobe dans Adobe Admin Console
description: Découvrez les intégrations de services gérés par Adobe dans Adobe Admin Console pour AEM as a Cloud Service, ce qu’elles font et comment les désactiver ou les restaurer.
feature: Security
role: Admin
source-git-commit: dfa8d82358db48b37917e9bc7fb4a7c645138305
workflow-type: tm+mt
source-wordcount: '1174'
ht-degree: 2%

---


# Intégrations d’API gérées par Adobe dans Adobe Admin Console {#adobe-managed-api-integrations-in-adobe-admin-console}

Adobe fournit un petit nombre d’intégrations de **services** dans votre organisation IMS dans le cadre d’AEM as a Cloud Service et des fonctionnalités Adobe Experience Cloud associées. Ces intégrations apparaissent dans [&#128279;](https://adminconsole.adobe.com/) à côté des intégrations que vous créez vous-même. Les services Adobe les possèdent et les exploitent en votre nom.

En tant qu’administrateur système ou administrateur de produit de votre organisation IMS, vous pouvez examiner les fonctions de chaque intégration, déterminer la fonctionnalité Adobe qui en dépend et décider si elle reste activée. Vous pouvez désactiver à tout moment toute intégration de service gérée par Adobe et la restaurer ultérieurement si nécessaire.

## Vue d’ensemble {#overview}

Cet article vous permet d’effectuer les opérations suivantes :

* Identifier les intégrations gérées par Adobe qui ont accès à vos environnements AEM.
* Découvrez l’objectif de chaque intégration et la fonctionnalité Adobe qu’elle prend en charge.
* Désactivez ou restaurez les intégrations à partir d’Admin Console lorsque votre entreprise l’exige.

Adobe applique les principes suivants pour chaque intégration de service répertoriée ici :

* **Nommée de manière transparente** : chaque intégration utilise un nom lisible par l’utilisateur qui décrit son objectif.
* **Documenté** — Chaque intégration est décrite ici avec la fonctionnalité qu&#39;elle prend en charge.
* **Privilèges minimum** — Chaque intégration reçoit uniquement le profil de produit, le rôle ou l&#39;autorisation requis pour sa fonction, et non les droits d&#39;administrateur généraux.
* **Contrôlable par le client** — Chaque intégration est visible dans votre Admin Console et vos administrateurs peuvent la désactiver ou la restaurer.

## Emplacement de ces intégrations {#where-to-find-these-integrations}

1. Connectez-vous à [&#128279;](https://adminconsole.adobe.com/) avec un compte d’administrateur système ou d’administrateur de produit pour votre organisation IMS.
1. Pour afficher toutes les informations d’identification d’API, accédez à **Utilisateurs** > **Informations d’identification d’API**. Pour inspecter les intégrations disposant d’une autorisation spécifique, accédez à **Produits** > *le produit Adobe nommé dans le catalogue* > *le profil de produit approprié*.
1. Recherchez les intégrations de services dont le nom commence par `Adobe` ou qui correspondent à un nom dans le catalogue ci-dessous.

>[!NOTE]
>
>Chaque entrée de catalogue répertorie le produit Adobe et le profil, le rôle ou l’autorisation de produit pour cette intégration de service. Utilisez ce chemin d’accès lorsque vous inspectez, désactivez ou restaurez une intégration.
>
>Le nom affiché dans Admin Console est l’identifiant qui fait autorité. Si une intégration de service qui ne figure pas dans la liste ci-dessous s’affiche, contactez le [Service clientèle d’](https://helpx.adobe.com/fr/support.html) avant de la désactiver.

## Catalogue des intégrations gérées par Adobe {#catalog-of-adobe-managed-integrations}

Le tableau suivant répertorie les intégrations de services qu’Adobe met en service pour les clients AEM as a Cloud Service.

| Nom, comme indiqué dans Admin Console | Effets | Utilisé par | Autorisations accordées | Activé par défaut |
|---|---|---|---|---|
| **Intégration du réseau CDN géré par** | Permet au service LLM Optimizer de mettre à jour pour votre compte votre réseau CDN géré par AEM as a Cloud Service **règles de routage de trafic dynamique** afin que les robots d&#39;exploration d’IA et d’agent (tels que ChatGPT, Perplexity et Claude) puissent être acheminés vers des origines optimisées de LLM Optimizer sans modification manuelle du réseau CDN par votre équipe. | **&#x200B;**&#x200B;via la fonctionnalité [Optimiser sur Edge](https://experienceleague.adobe.com/fr/docs/llm-optimizer/using/resources/optimize-at-edge/overview) | Rôle Cloud Manager **Responsable de déploiement** | Oui |

La capture d’écran suivante est un exemple de l’**intégration du réseau CDN géré par** mentionnée dans le tableau ci-dessus.

![Intégration du réseau CDN géré par AEM dans le profil de produit Gestionnaire de déploiement Cloud Manager dans Adobe Admin Console](assets/aem-managed-cdn-integration-admin-console.png)

>[!NOTE]
>
>Adobe fournit actuellement une intégration de service sous ce modèle. Adobe met à jour ce tableau lorsque d’autres services utilisent la même approche. Si votre Admin Console affiche une autre intégration de service configurée par Adobe qui n’est pas répertoriée ici, utilisez Admin Console comme source de vérité et contactez le [Service clientèle d’Adobe](https://helpx.adobe.com/fr/support.html) pour plus d’informations.

## Impact de la désactivation d’une intégration {#impact-of-disabling-an-integration}

Vous pouvez désactiver une intégration de service gérée par Adobe à tout moment. Dans ce cas, la fonctionnalité Adobe qui dépend de cette intégration cesse de fonctionner pour votre organisation jusqu’à ce que vous la restauriez. Consultez le tableau suivant avant de désactiver une intégration.

| Intégration | Ce qui cesse de fonctionner en cas de désactivation | Ce qui continue de fonctionner |
|---|---|---|
| **Intégration du réseau CDN géré par** | <ul><li><strong>Les utilisateurs de LLM Optimizer ne pourront plus mettre à jour les règles de routage de trafic agent du réseau de diffusion de contenu géré par AEM as a Cloud Service</strong> pour vos domaines. Toute tentative ultérieure par un administrateur LLMO d&#39;activer, de modifier ou de révoquer le routage agentique échouera l&#39;autorisation au niveau de la couche CDN.</li><li>Routage des robots d&#39;exploration AI/agent (ChatGPT, Perplexity, Claude, etc.) Les origines optimisées pour LLM Optimizer ne peuvent pas être (re)configurées tant que l’intégration n’est pas rétablie.</li><li>Les règles de routage d’agent déjà appliquées restent en vigueur à la périphérie, mais ne peuvent pas être modifiées ou supprimées sans réactiver l’intégration (ou se coordonner manuellement avec le service clientèle d’Adobe).</li></ul> | <ul><li>Vos environnements de création, de publication et de prévisualisation AEM as a Cloud Service continuent à traiter le trafic normalement.</li><li>La diffusion standard (non agentique) sur le réseau CDN de vos sites déjà déployés reste inchangée.</li><li>Les pipelines et déploiements de Cloud Manager continuent à fonctionner pour vos opérateurs humains avec les droits de Responsable de déploiement .</li><li>Toutes les fonctionnalités LLM Optimizer qui ne dépendent pas du routage Edge continuent à fonctionner.</li></ul> |

## Désactivation d’une intégration {#how-to-disable-an-integration}

**Qui peut effectuer cette tâche :** une organisation IMS **administrateur système** ou l’**administrateur de produit** pour le produit Adobe dont le profil, le rôle ou l’autorisation accorde l’accès à l’intégration de service (voir *Autorisations accordées* dans la ligne de catalogue).

Dans cet article, les étapes sont les mêmes pour chaque intégration de service. Seul le chemin de navigation dans Admin Console change en fonction du profil de produit pour cette intégration.

1. Connectez-vous à [&#128279;](https://adminconsole.adobe.com/).
1. Identifiez le produit **Adobe et le** profil de produit **rôle ou autorisation** pour l&#39;intégration de service. Les deux sont répertoriés dans la ligne du catalogue.
1. Accédez à **Produits** > *le produit Adobe* > *le profil du produit*.
1. Ouvrez l’onglet **Informations d’identification de l’API** ou **Utilisateurs** pour ce profil.
1. Recherchez l’intégration de service avec le nom exact de la ligne du catalogue.
1. Supprimez l’intégration de service du profil de produit. L’intégration est désactivée pour votre organisation. La prochaine fois que le service Adobe agira en votre nom, l’autorisation sera refusée.

**Exemple — Intégration de réseau CDN géré par AEM :** accédez à **Produits** > **Adobe Experience Manager as a Cloud Service** > **Cloud Manager** > **Responsable de déploiement**, recherchez **Intégration de réseau CDN géré par AEM** et supprimez-la du profil de produit.

## Restauration d’une intégration {#how-to-restore-an-integration}

Si vous avez précédemment désactivé une intégration et souhaitez la réactiver :

1. Connectez-vous à [&#128279;](https://adminconsole.adobe.com/) en tant qu&#39;administrateur système ou produit.
1. Accédez au **même produit et profil de produit** identifié pour l’intégration de service dans le catalogue ci-dessus. Il s’agit du profil duquel l’intégration de service a été supprimée lorsqu’elle a été désactivée.
1. Sélectionnez **Ajouter un utilisateur** ou **Ajouter une API**, puis recherchez l’intégration de service par le nom exact répertorié dans le catalogue.
1. Ajoutez à nouveau l’intégration de service au profil de produit. L’intégration reprend lors de sa prochaine exécution planifiée ou initiée par l’utilisateur.

**Exemple — Intégration de réseau CDN géré par AEM :** accédez à **Cloud Manager** > **Gestionnaire de déploiement** et ajoutez **Intégration de réseau CDN géré par AEM** à nouveau à l’aide de **Ajouter un utilisateur** ou **Ajouter une API**.

>[!NOTE]
>
>Si vous ne trouvez pas l’intégration de service dans la boîte de dialogue d’ajout d’utilisateur (par exemple, parce qu’Adobe l’a supprimée de votre organisation plutôt que du profil uniquement), contactez le [service clientèle d’Adobe](https://helpx.adobe.com/fr/support.html) pour demander la mise en service. Adobe ne rajoute pas automatiquement une intégration de service supprimée par votre administrateur.
