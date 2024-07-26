---
title: Intégration de contents credentials
description: Content credentials, intégré à AEM Assets et présenté dans la vue Assets, peut fournir un contexte dans l’historique d’une ressource, y compris la manière dont elle a été créée et qui a été impliqué dans sa création. Tout comme une étiquette nutritionnelle pour les contenus numériques, les Contents credentials peuvent contribuer à accroître la transparence et à établir la confiance avec les publics.
role: User
source-git-commit: 1c0ffe9d6e45f1d6b3574d1ac5611b2c2e2d00e0
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---


# Informations de traçabilité du contenu {#content-credentials}

Les marques s’intéressent plus que jamais à la transparence du contenu, à la divulgation par l’IA et à la prévention de la falsification des ressources. L’Initiative d’authentification du contenu (CAI) d’Adobe crée des outils conformes à la norme technique [Coalition for Content Provenance and Authenticity](https://c2pa.org/specifications/specifications/1.1/specs/C2PA_Specification.html#_trust_model) (C2PA). Les contents credentials, qui sont un nouveau type de métadonnées chiffrées et dont l’affichage est estampillé, peuvent aider les visiteurs à comprendre la traçabilité du contenu et à garantir l’intégrité des ressources de marque. Ils peuvent inclure un large éventail de données de provenance qui offrent des informations sur l’historique d’une ressource numérique.

Ces informations peuvent inclure :

* **Émetteur ou signataire :** Informations sur l’entité ou la société qui a émis la signature numérique pour certifier la ressource ou la signer.
* **Date de publication :** date à laquelle les informations d’identification du contenu ont été appliquées à la ressource.
* **Crédit et utilisation :** Informations sur le producteur de la ressource, y compris le nom, les gestionnaires de médias sociaux ou d’autres informations liées à l’identité.
* **Processus :** Enregistrements de toute modification ou modification apportée à la ressource.
* **Détails du périphérique :** Informations sur l’application ou le périphérique utilisé pour créer ou modifier la ressource.
* **Outil d’IA utilisé :** Si l’IA générative a été utilisée pour modifier ou créer la ressource, le nom du modèle utilisé peut être inclus.
* **Autres informations permanentes :** Des données supplémentaires peuvent également être incluses pour offrir plus de contexte sur l’historique d’une ressource.

Pour une vue complète, [Vérifier](https://contentcredentials.org/verify) peut offrir un aperçu plus complet de l’historique des ressources.

Adobe Experience Manager Assets prend désormais en charge les Contents credentials, ce qui permet aux utilisateurs d’afficher les Contents credentials directement dans la vue Assets d’AEM. Lorsque vous examinez les détails de la ressource, toute image contenant des Contents credentials (tels que ceux créés avec les services GenAI) affiche les détails du manifeste dans un panneau dédié. Si la ressource est téléchargée, publiée ou partagée, les Contents credentials restent intacts avec la ressource.

![ressources](/help/assets/assets/content-credentials.png)

## Accès aux Contents credentials {#access-content-credentials}

1. Accédez à l’interface utilisateur de la vue Assets et cliquez sur **Assets** dans le volet de gauche.
1. Accédez à un dossier et sélectionnez la ressource souhaitée.
1. Cliquez sur **Details** et sélectionnez `Cr pin` dans le volet le plus à droite. L’onglet Contents credentials affiche les informations suivantes sur la ressource.
   1. **Image générée :** Date et heure auxquelles les Contents credentials ont été appliqués.
   1. **Résumé du contenu :** Indique si la ressource est partiellement ou complètement générée par l’IA ou comment elle a été modifiée.
      ![contents credentials](/help/assets/assets/content-credentials1.png)
   1. **Processus :** présente l’application, le périphérique et l’outil d’IA (tel que Adobe Firefly) utilisés pour générer la ressource, ainsi que les modifications apportées par la suite.
      ![process](/help/assets/assets/CR-Process.png)
   1. **À propos de ces Contents credentials :** Nom de l’émetteur ainsi que la date et l’heure d’émission.
      ![issuer](/help/assets/assets/CR-issuer.png)
