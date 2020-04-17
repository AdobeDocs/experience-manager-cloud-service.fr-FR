---
title: Fonctionnalités obsolètes et supprimées
description: Notes de mise à jour dédiées aux fonctionnalités obsolètes et supprimées dans Adobe Experience Manager as a Cloud Service.
translation-type: ht
source-git-commit: b31ae32285080075d2531edd2c4976cf801d1c89

---


# Fonctionnalités obsolètes et supprimées {#deprecated-and-removed-features}

Adobe étudie constamment les fonctionnalités du produit de façon à les réinventer au fil du temps ou à remplacer les fonctions plus anciennes par des variantes plus modernes, pour améliorer la valeur client globale, le tout en faisant toujours attention à la compatibilité ascendante. En outre, comme Adobe Experience Manager as a Cloud Service fournit un modèle de déploiement natif au cloud, certaines capacités et fonctionnalités ont été remplacées par des homologues natives sur le cloud.

Pour communiquer la suppression/le remplacement imminent de fonctionnalités d’AEM, les règles suivantes s’appliquent :

1. L’annonce de la suppression arrive en premier. Les capacités obsolètes demeurent disponibles, mais ne sont plus améliorées.
1. Les fonctionnalités annoncées comme obsolètes sont supprimées au plus tôt dans la version majeure qui suit. La date cible réelle de la suppression est annoncée.

Ce processus donne aux clients au moins un cycle de version afin d’adapter leur implémentation à une nouvelle version ou produit de remplacement d’une fonctionnalité obsolète, avant que la suppression ne soit effective.

## Fonctionnalités obsolètes {#deprecated-features}

Cette section répertorie les fonctionnalités qui ont été marquées comme obsolètes dans Experience Manager as a Cloud Service. En règle générale, les fonctionnalités qui doivent être supprimées dans une version ultérieure sont d’abord définies comme obsolètes, et une alternative est fournie.

Il est conseillé aux clients de réfléchir à leur utilisation de la fonctionnalité dans leur déploiement actuel et de prévoir la modification de leur mise en œuvre de façon à utiliser l’alternative proposée.

| Zone | Fonctionnalité | Remplacement |
| ------------ | ------------------ | ----------- |
| Ressources | L’assimilation et le traitement des ressources n’utilisent plus le workflow `DAM Asset Update` | L’assimilation de ressources utilise maintenant les [microservices de ressources](/help/assets/asset-microservices-overview.md). |
| Ressources | Transfert direct de ressources vers AEM : consultez [API de téléchargement de ressources obsolètes](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api) | [Le transfert binaire direct](/help/assets/add-assets.md) est utilisé dans Experience Manager as a Cloud Service. Pour plus d’informations techniques, consultez [API de transfert direct](/help/assets/developer-reference-material-apis.md#overview-binary-upload). |
| Ressources | [Certaines étapes de workflow ](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps) dans le workflow `DAM Asset Update` ne sont pas prises en charge, notamment l’appel d’outils de ligne de commande tels que ImageMagick. | [Les microservices de ressources](/help/assets/asset-microservices-overview.md) remplacent de nombreux workflows. Pour le traitement personnalisé, utilisez des [workflows de post-traitement](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows). |

## Fonctionnalités supprimées {#removed-features}

Cette section répertorie les capacités et fonctionnalités qui ont été supprimées d’AEM avec Experience Manager as a Cloud Service.

| Zone | Fonctionnalité | Remplacement |
| ------------ | ------------------ | ----------- |
| Interface utilisateur | Bien que certaines boîtes de dialogue de l’interface utilisateur classique restent pour l’instant réservées à quelques fonctionnalités sélectionnées, telles que le vérificateur de liens, la purge de version et certaines configurations du Cloud Service, l’accès à l’interface utilisateur classique en général a été supprimé dans l’interface utilisateur du produit AEM. | Interface utilisateur standard |
| Dynamic Media | Les intégrations précédentes avec [Dynamic Media Classic (Scene7)](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/scene7.html) et le mode [hybride de médias](https://helpx.adobe.com/fr/experience-manager/6-5/assets/using/config-dynamic.html) dynamiques ne sont pas disponibles dans AEM as a Cloud Service. | Utilisez [Dynamic Media](/help/assets/dynamic-media/dynamic-media.md) fourni avec Experience Manager as a Cloud Service. |
| Sites | Composant Portal Director et Portlet | Ces fonctionnalités ont été abandonnées dans AEM 6.4 et ont été supprimées d’AEM. |
| Sites | Importateur de conception | Cette fonctionnalité a été supprimée, car les sections immuables du référentiel AEM ne sont pas accessibles au moment de l’exécution. |
| Ressources | [Le partage d’AEM Assets avec le service principal Marketing Cloud Assets et les services Creative Cloud](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/configure-assets-cc-integration.html) n’est pas disponible. | Pour l’intégration à Creative Cloud, utilisez [Adobe Asset Link](https://helpx.adobe.com/fr/enterprise/using/adobe-asset-link.html). |
