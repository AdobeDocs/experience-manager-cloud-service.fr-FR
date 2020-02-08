---
title: Fonctions obsolètes et supprimées
description: Notes de mise à jour spécifiques aux fonctionnalités obsolètes et supprimées d’Adobe Experience Manager en tant que service Cloud.
translation-type: tm+mt
source-git-commit: b31ae32285080075d2531edd2c4976cf801d1c89

---


# Deprecated and removed features {#deprecated-and-removed-features}

Adobe évalue constamment les fonctionnalités du produit afin de réinventer ou de remplacer au fil du temps des fonctionnalités plus anciennes par des solutions de remplacement plus modernes afin d’améliorer la valeur globale du client, toujours en tenant compte de la compatibilité ascendante. En outre, comme Adobe Experience Manager en tant que service Cloud fournit un modèle de déploiement natif au cloud, certaines fonctionnalités et fonctionnalités ont été remplacées par des homologues natifs au cloud.

Pour communiquer la suppression/le remplacement imminent de fonctionnalités d’AEM, les règles suivantes s’appliquent :

1. L’annonce de la suppression arrive en premier. Les capacités obsolètes demeurent disponibles, mais ne sont pas encore améliorées.
1. Les fonctionnalités annoncées comme obsolètes sont supprimées dans la version majeure suivante, au plus tôt. La date cible réelle de suppression est annoncée.

Ce processus donne aux clients au moins un cycle de publication afin d’adapter leur implémentation à une nouvelle version ou produit de remplacement d’une fonctionnalité obsolète, avant que la suppression ne soit effective.

## Deprecated features {#deprecated-features}

Cette section répertorie les fonctionnalités qui ont été marquées comme obsolètes dans Experience Manager en tant que service Cloud. En règle générale, les fonctionnalités qui doivent être supprimées dans une version ultérieure sont définies comme obsolètes en premier, avec une alternative fournie.

Il est conseillé aux clients de réfléchir à leur utilisation de la fonctionnalité dans leur déploiement actuel et de prévoir la modification de leur mise en œuvre de façon à utiliser l’alternative proposée.

| Zone | Fonctionnalité | Remplacement |
| ------------ | ------------------ | ----------- |
| Ressources | L’assimilation et le traitement des ressources n’utilisent plus `DAM Asset Update` le processus | L’assimilation de ressources utilise maintenant les microservices [de](/help/assets/asset-microservices-overview.md) ressources. |
| Ressources | Téléchargement direct de fichiers vers AEM - voir API de téléchargement de fichiers [obsolètes](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api) | [Le transfert](/help/assets/add-assets.md) binaire direct est utilisé dans Experience Manager en tant que service Cloud. Pour plus d’informations techniques, voir API [de téléchargement](/help/assets/developer-reference-material-apis.md#overview-binary-upload)direct. |
| Ressources | [Certaines étapes](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps) de flux de travail dans `DAM Asset Update` le flux de travail ne sont pas prises en charge, notamment l’appel d’outils de ligne de commande tels que ImageMagick | [Les microservices](/help/assets/asset-microservices-overview.md) de ressources remplacent de nombreux processus. Pour le traitement personnalisé, utilisez des processus de [post-traitement](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows). |

## Removed features {#removed-features}

Cette section répertorie les fonctionnalités et fonctionnalités qui ont été supprimées d’AEM avec Experience Manager en tant que service Cloud.

| Zone | Fonctionnalité | Remplacement |
| ------------ | ------------------ | ----------- |
| Interface utilisateur | Bien que certaines boîtes de dialogue de l’interface utilisateur classique restent pour l’instant réservées à quelques fonctionnalités sélectionnées, telles que le vérificateur de liens, la purge de version et certaines configurations du service Cloud, l’accès à l’interface utilisateur classique en général a été supprimé dans l’interface utilisateur du produit AEM. | Interface utilisateur standard |
| Dynamic Media | Les intégrations précédentes avec [Dynamic Media Classic (Scene7)](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/scene7.html) et le mode [hybride de médias](https://helpx.adobe.com/experience-manager/6-5/assets/using/config-dynamic.html) dynamiques ne sont pas disponibles dans AEM en tant que service Cloud. | Utilisez [Contenu multimédia](/help/assets/dynamic-media/dynamic-media.md) dynamique fourni avec Experience Manager en tant que service Cloud. |
| Sites | Composant Portal Director et Portlet | Ces fonctionnalités ont été abandonnées dans AEM 6.4 et ont été supprimées d’AEM. |
| Sites | Importateur de conception | Cette fonctionnalité a été supprimée car les sections immuables du référentiel AEM ne sont pas accessibles au moment de l’exécution. |
| Ressources | [Le partage des ressources AEM avec le service principal Ressources Marketing Cloud et les services](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/configure-assets-cc-integration.html) Creative Cloud n’est pas disponible. | Pour l’intégration à Creative Cloud, utilisez [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html). |
