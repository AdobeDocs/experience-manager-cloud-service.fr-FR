---
title: Intégration de Content Credentials
description: Content Credentials, intégré à AEM Assets et présenté dans la vue Assets, peut fournir un contexte dans l’historique d’une ressource, y compris la manière dont elle a été créée et les personnes impliquées dans sa création. Tout comme une étiquette nutritionnelle pour le contenu numérique, Content Credentials peut contribuer à accroître la transparence et à établir la confiance du public.
role: User
badgeSaas: label="AEM Assets" type="Positive" tooltip="S’applique à AEM Assets)."
exl-id: 27c25ae0-4477-40c3-85c8-3e0aa725aba7
source-git-commit: 80a32672ec018274b0410abfa14fdd761fdb5aba
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 82%

---

# Content Credentials {#content-credentials}

Les marques sont plus préoccupées que jamais par la transparence du contenu, la déclaration d’utilisation de l’IA et la prévention de l’altération des ressources. Le Content Authenticity Initiative (CAI) d’Adobe crée des outils conformes à la norme technique [C2PA](https://c2pa.org/specifications/specifications/1.1/specs/C2PA_Specification.html#_trust_model) (Coalition for Content Provenance and Authenticity). Les identifiants de contenu, qui sont un nouveau type de métadonnées chiffrées et inviolables, peuvent aider les visiteurs à comprendre la traçabilité du contenu et garantir l’intégrité des ressources de la marque. Ils peuvent inclure un large éventail de données de provenance qui fournissent des informations dans l’historique d’une ressource numérique.

Ces informations peuvent inclure :

* **Émetteur ou signataire :** informations sur l’entité ou la société qui a émis la signature numérique pour certifier l’élément certifie ou signe l’élément.
* **Date de l’événement :** date à laquelle Content Credential a été appliqué à la ressource.
* **Crédit et utilisation :** informations sur le producteur de la ressource, y compris le nom, les identifiants de médias sociaux ou d’autres informations relatives à l’identité.
* **Processus :** les enregistrements des modifications apportées à la ressource.
* **Détails de l’appareil :** informations sur l’application ou l’appareil utilisé pour créer ou modifier la ressource.
* **Outil d’IA utilisé :** si l’IA générative a été utilisée pour modifier ou créer la ressource, le nom du modèle utilisé peut être inclus.
* **Autres informations pertinentes :** des données supplémentaires peuvent également être incluses pour offrir plus de contexte sur l’historique d’une ressource.

Pour une vue complète, la fonction [Vérifier](https://contentcredentials.org/verify) peut proposer une insight plus complète de l’historique des ressources.

Adobe Experience Manager Assets prend désormais en charge Content Credentials, ce qui permet aux utilisateurs d’afficher Content Credentials directement dans la vue Assets d’AEM. Lorsque vous examinez les détails de la ressource, toute image avec Content Credentials (telle que celles créées avec les services GenAI) affiche les détails du manifeste dans un panneau dédié. Si la ressource est téléchargée, publiée ou partagée, le Content Credentials reste intact avec la ressource.

![ressources](/help/assets/assets/content-credentials.png)

## Accéder à Content Credentials {#access-content-credentials}

1. Accédez à l’interface utilisateur de l’affichage Assets, puis cliquez sur **Assets** dans le volet de gauche.
1. Accédez à un dossier et sélectionnez la ressource souhaitée.
1. Cliquez sur **Détails** et sélectionnez `Cr pin` dans le volet le plus à droite. L’onglet Content Credentials affiche les informations suivantes sur la ressource.
   1. **Image générée :** date et heure d’application de Content Credentials.
   1. **Résumé du contenu :** indique si la ressource est partiellement ou entièrement générée par l’IA, ou comment elle a été modifiée.
      ![informations d’identification du contenu](/help/assets/assets/content-credentials1.png)
   1. **Processus :** décrit l’application, l’appareil et l’outil d’IA (comme Adobe Firefly) utilisés pour générer la ressource, ainsi que les modifications apportées ultérieurement.
      ![processus](/help/assets/assets/CR-Process.png)
   1. **À propos de ce Content Credentials :** nom de l’émetteur, ainsi que la date et l’heure d’émission.
      ![émetteur](/help/assets/assets/CR-issuer.png)


**Voir également**

* [Traduire les ressources](/help/assets/translate-assets.md)
* [API HTTP Assets](/help/assets/mac-api-assets.md)
* [Formats de fichiers pris en charge par Assets](/help/assets/file-format-support.md)
* [Rechercher des ressources](/help/assets/search-assets.md)
* [Ressources connectées](/help/assets/use-assets-across-connected-assets-instances.md)
* [Rapports de ressources](/help/assets/asset-reports.md)
* [Schémas de métadonnées](/help/assets/metadata-schemas.md)
* [Télécharger des ressources](/help/assets/download-assets-from-aem.md)
* [Gestion des métadonnées](/help/assets/manage-metadata.md)
* [Gérer les modèles Dynamic Media](/help/assets/dynamic-media/manage-dynamic-media-templates.md)
* [Gérer les rapports](/help/assets/manage-reports-assets-view.md)
* [Facettes de recherche](/help/assets/search-facets.md)
* [Gérer les collections](/help/assets/manage-collections.md)
* [Import des métadonnées en bloc](/help/assets/metadata-import-export.md)
* [Publier des ressources sur AEM et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

