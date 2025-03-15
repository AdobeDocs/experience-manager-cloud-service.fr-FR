---
title: API de communication d’AEM Forms as a Cloud Service
description: Générer, manipuler et sécuriser des documents avec les API de communication d’AEM Forms dans le cloud
Keywords: document generation, PDF manipulation, document security, batch processing, document conversion, PDF/A compliance
feature: Adaptive Forms, APIs & Integrations, Document Services
role: Admin, Developer, User
exl-id: b6f05b2f-5665-4992-8689-d566351d54f1
source-git-commit: a9eed5b6219163e721d81c9d77a31604666a2ac5
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 5%

---


# API de communication d’AEM Forms as a Cloud Service {#communications-apis-overview}

> **Disponibilité de la version**
>
> * **AEM 6.5** : [Présentation d’AEM Document Services](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-document-services/overview-aem-document-services.html)
> * **AEM as a Cloud Service** : cet article

## Présentation

Les API de communication d’AEM Forms as a Cloud Service vous permettent de créer des documents personnalisés, normalisés et approuvés par la marque, adaptés aux besoins de votre entreprise. Ces puissantes API vous permettent de générer, manipuler et sécuriser des documents par programmation, que ce soit à la demande ou dans les processus par lots à volume élevé.


### Principaux avantages

* **Génération de documents rationalisée** - Créez des documents personnalisés en fusionnant des modèles avec les données du client
* **Puissante manipulation de documents** - Combinez, réorganisez et validez les documents PDF par programmation
* **Options de déploiement flexibles** - Utilisez des API à la demande pour les besoins de faible latence ou des API par lots pour les opérations à débit élevé.
* **Sécurité renforcée** - Appliquez les signatures numériques, la certification et le chiffrement pour protéger les documents sensibles
* **Architecture native dans le cloud** - Tirez parti d’une infrastructure cloud évolutive et sécurisée sans frais de maintenance.

## Fonctionnalités essentielles

Les API Communications fournissent un ensemble complet de fonctionnalités de traitement des documents organisées en fonction des domaines fonctionnels suivants :


| Génération de documents | Manipulation de documents | Extraction de documents | Conversion de document | Document Assurance |
|---------------------|----------------------|---------------------|---------------------|-------------------|
| Générez des documents personnalisés en fusionnant des modèles avec des données dans divers formats, y compris les formats PDF et d’impression. | Combinez, réorganisez et validez des documents PDF par programmation pour créer de nouveaux packages de documents. | Extrayez des propriétés, des métadonnées et du contenu des documents PDF pour un traitement ultérieur. | convertir des documents entre différents formats, y compris la validation de conformité PDF/A pour les besoins d’archivage ; | Appliquez les signatures numériques, la certification et le chiffrement pour sécuriser et protéger les documents. |

## Génération de documents

Les API de génération de documents Communications combinent des modèles (XFA ou PDF) avec des données client (XML) pour créer des documents personnalisés dans PDF et divers formats d’impression (PS, PCL, DPL, IPL, ZPL).

### Fonctionnement de la génération de documents

Le workflow type comprend :

1. Création d&#39;un modèle à l&#39;aide de [Designer](use-forms-designer.md)
2. Préparation des données XML pour renseigner le modèle
3. Utilisation des API Communications pour fusionner le modèle avec les données
4. Génération de documents de sortie au format souhaité

![Workflow de génération de documents Communications](assets/communicaions-workflow.png)

### Créer des documents PDF

Les API de génération de documents vous permettent de créer des documents PDF non interactifs en fusionnant des données XML avec des modèles de formulaire :

![Créer des documents PDF](assets/outPutPDF_popup.png)

Vous pouvez diffuser les PDF générés aux utilisateurs par le biais de téléchargements, les stocker dans un référentiel ou les charger éventuellement dans Azure Blob Storage.

<span class="preview">Le téléchargement des PDF générés vers Azure Blob Storage est disponible via le [Programme des utilisateurs précoces](/help/forms/early-access-ea-features.md). Contactez aem-forms-ea@adobe.com à partir de votre e-mail officiel pour rejoindre.</span>

### Créer des documents au format d’impression

Générer des documents dans des formats d’impression, notamment :
* PostScript (PS)
* PCL (Printer Command Language)
* Langue d&#39;impression Zebra (ZPL)

Ces formats sont idéaux pour les opérations d&#39;impression de gros volumes et les besoins d&#39;impression spécialisés.

### Traitement par lots de plusieurs documents

Traitez des volumes importants de documents efficacement à l’aide des API par lots :

![Workflow de traitement par lots](assets/ou_OutputBatchMany_popup.png)

Le traitement par lots vous permet d’effectuer les opérations suivantes :

* Générer des documents distincts pour chaque enregistrement d&#39;une source de données XML
* Traitement asynchrone des documents pour de meilleures performances
* Configuration de différents paramètres de conversion pour le traitement par lots

## Manipulation de documents

Les API de manipulation de documents vous permettent de combiner, de réorganiser et de transformer des documents PDF par programmation.

### Assemblage de document

Regroupez plusieurs documents PDF ou XDP en un seul document cohérent :

![Assemblage d’un document PDF unique à de documents PDF multiples](assets/as_document_assembly.png)

Les fonctionnalités d’assemblage de documents incluent :
* Création de documents PDF simples à partir de plusieurs sources
* Création de portfolios PDF
* Assembler des documents chiffrés
* Ajout d’une numérotation Bates pour les documents juridiques
* Aplatissement et assemblage de formulaires interactifs

### Désassemblage du document

Répartissez les documents PDF volumineux en composants plus petits et plus faciles à gérer :

![La division d’un document source en fonction de signets en plusieurs documents](assets/as_intro_pdfsfrombookmarks.png)

Le désassemblage de documents permet d’effectuer les opérations suivantes :
* Extraction de pages spécifiques à partir de documents source
* Diviser les documents en fonction de signets
* Créer des ensembles de documents logiques à partir de compilations plus volumineuses

>[!NOTE]
>
> AEM Forms comprend de nombreuses polices intégrées qui s’intègrent de manière transparente aux fichiers PDF. Pour obtenir la liste complète des polices prises en charge, [cliquez ici](/help/forms/supported-out-of-the-box-fonts.md).

## Extraction de documents

<span class="preview">L’extraction de documents est disponible via le [Programme des utilisateurs et utilisatrices précoces](/help/forms/early-access-ea-features.md). Contactez aem-forms-ea@adobe.com à partir de votre e-mail officiel pour rejoindre.</span>

Les API d’extraction de documents vous permettent de récupérer des informations à partir de documents PDF, notamment :

* Propriétés du document (s’agit-il d’un formulaire à remplir, comporte-t-il des pièces jointes, etc.)
* Droits et autorisations d’utilisation
* Informations de métadonnées à l’aide de la plateforme de métadonnées extensible Adobe (XMP)

Cette fonctionnalité est particulièrement utile pour les systèmes de gestion des documents, les solutions d’archivage et l’automatisation des workflows.

## Conversion de document

### Conversion et validation PDF/A

Convertissez des documents PDF standard au format PDF/A à des fins d’archivage à long terme :

* Prise en charge des normes de conformité PDF/A-1a, 1b, 2a, 2b, 3a et 3b
* Validation de la conformité PDF/A
* Préservation de l’intégrité du document avec des polices incorporées et du contenu non compressé

### Conversion de PDF vers XDP

La conversion de <span class="preview">PDF vers XDP est disponible via le [Programme des utilisateurs et utilisatrices précoces](/help/forms/early-access-ea-features.md). Contactez aem-forms-ea@adobe.com à partir de votre e-mail officiel pour rejoindre.</span>

Convertissez des documents PDF contenant des flux XFA au format XDP pour l’édition et la réutilisation de modèles.

## Document Assurance {#doc-assurance}

Document Assurance comprend des API de signature et de chiffrement pour protéger vos documents tout au long de leur cycle de vie.

### API Signature

Protégez les documents PDF avec des signatures numériques et la certification :

* Ajouter des champs de signature visibles ou invisibles
* Signer numériquement les champs de signature
* Certifier l’intégrité des documents
* Supprimer des signatures des documents
* Supprimer des champs de signature des documents

<span class="preview">La suppression des signatures et des champs de signature est disponible via le [Programme des utilisateurs et utilisatrices précoces](/help/forms/early-access-ea-features.md). Contactez aem-forms-ea@adobe.com à partir de votre e-mail officiel pour rejoindre.</span>

### API Encryption

Sécuriser le contenu du document avec le chiffrement :

* Chiffrer des documents PDF avec des mots de passe
* Supprimer le chiffrement avec mot de passe
* Détermination des types de sécurité appliqués aux documents
* Récupérer des informations de sécurité à partir de documents protégés

### Utilitaires de document {#doc-utility}

Les utilitaires de document fournissent des fonctionnalités supplémentaires pour l’utilisation de documents PDF :

#### API des droits d’utilisation (extension Reader)

<span class="preview">Les droits d’utilisation (extension Reader) sont disponibles via le [programme des utilisateurs précoces](/help/forms/early-access-ea-features.md). Contactez aem-forms-ea@adobe.com à partir de votre e-mail officiel pour rejoindre.</span>

Étendez les fonctionnalités d’Adobe Reader en ajoutant des droits d’utilisation aux documents PDF, ce qui permet de bénéficier de fonctionnalités telles que :

* Remplissage et enregistrement du formulaire
* Ajouter des commentaires et des annotations
* Signature numérique
* Pièces jointes
* Import/export de données de formulaire
* Accès aux services Web et aux bases de données

Les droits d’utilisation disponibles sont les suivants :

* **Interaction de formulaire** : remplissage de formulaire, importation/exportation de données de formulaire, champs/pages de formulaire dynamique
* **Annotations** : commentaires (en ligne et hors ligne), signatures numériques
* **Gestion des documents** : fichiers incorporés, envoi autonome, décodage des codes-barres
* **Services en ligne** : Forms en ligne, accès aux services web

## Types d’API de communication {#types}

Communications fournit deux types d’API pour répondre à différents cas d’utilisation :

### API synchrones

**Idéal pour** : génération de documents à la demande, à faible latence et uniques.
**Cas pratiques** : génération de documents déclenchée par l’utilisateur, applications interactives
**Documentation** : [Référence d’API synchrone](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/)

### API Batch (asynchrones)

**Idéal pour** : génération planifiée de documents multiples à débit élevé
**Cas pratiques** : relevés mensuels, factures, avis, rapports planifiés
**Documentation** : [Référence de l’API Batch](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/)

## Prise en main des API Communications

### Processus d’intégration

Communications est disponible sous la forme d’un module autonome ou d’un module complémentaire pour les utilisateurs Forms as a Cloud Service :

1. Contactez le service commercial Adobe ou votre représentant Adobe pour demander l’accès
2. Adobe autorisera l’accès pour votre organisation et accordera les privilèges d’administrateur
3. Votre administrateur peut ensuite accorder l’accès aux développeurs de votre organisation

### Activation des communications dans votre environnement

Pour activer les communications dans votre environnement Forms as a Cloud Service, procédez comme suit :

1. Connectez-vous à Cloud Manager et ouvrez votre instance AEM Forms as a Cloud Service
2. Ouvrez l’option Modifier le programme et accédez à l’onglet Solutions et modules complémentaires .
3. Sélectionnez l’option **[!UICONTROL Forms - Communications]**

   ![Communications](assets/communications.png)

   Si vous avez déjà activé **[!UICONTROL Forms - Inscription numérique]**, sélectionnez l’option **[!UICONTROL Forms - Module complémentaire Communications]** à la place.

   ![Module complémentaire](assets/add-on.png)

4. Cliquez sur **[!UICONTROL Mettre à jour]**
5. Exécuter le pipeline de création : les API Communications seront activées une fois l’opération terminée.

>[!NOTE]
>
> Pour activer les API de manipulation de documents, ajoutez la règle suivante à votre configuration [Dispatcher ](setup-local-development-environment.md#forms-specific-rules-to-dispatcher) :
>
> `# Allow Forms Doc Generation requests`
> `/0062 { /type "allow" /method "POST" /url "/adobe/forms/assembler/*" }`

## Documentation de référence sur les API {#api-reference}

Les API Communications sont organisées en plusieurs catégories fonctionnelles, chacune avec une documentation de référence détaillée. Ces références d’API fournissent des informations complètes sur les points d’entrée, les paramètres, les formats de requête/réponse et les exigences d’authentification.

### API de génération de documents

| API | Description | Lien de référence |
|-----|-------------|----------------|
| Génération de documents - Synchrone | Génération de documents à la demande avec une faible latence pour les scénarios interactifs | [ Référence d’API ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-sync/) |
| Génération de documents - lot | Traitement asynchrone de volumes importants de documents pour les opérations planifiées | [ Référence d’API ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/) |

### API de manipulation de documents

| API | Description | Lien de référence |
|-----|-------------|----------------|
| Manipulation de documents - Synchrone | Combiner, fractionner et transformer des documents PDF à l’aide des instructions DDX | [ Référence d’API ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/assembler-sync/) |

### API Document Assurance

| API | Description | Lien de référence |
|-----|-------------|----------------|
| DocAssurance - Synchrone | Appliquer les signatures numériques, la certification, le chiffrement et les extensions Reader | [ Référence d’API ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/docassurance/) |

### Paramètres d’API courants

Chaque catégorie d’API comporte des paramètres spécifiques, mais certains paramètres courants incluent :

#### Paramètres De Génération De Documents

| Paramètre | Type | Requis | Description |
|-----------|------|----------|-------------|
| `template` | Chaîne | Oui | Chemin d’accès au fichier modèle XDP ou PDF |
| `data` | Chaîne | Non | Données XML à fusionner avec le modèle |
| `outputOptions` | Objet | Non | Options de configuration du document de sortie |

#### Paramètres de manipulation de documents

| Paramètre | Type | Requis | Description |
|-----------|------|----------|-------------|
| `ddx` | Chaîne | Oui | Instructions DDX pour l’assemblage ou le désassemblage de documents |
| `inputDocuments` | Objet | Oui | Mappage des documents d’entrée à traiter |
| `outputOptions` | Objet | Non | Options de configuration du document de sortie |

#### Paramètres de Document Assurance

| Paramètre | Type | Requis | Description |
|-----------|------|----------|-------------|
| `inputPDF` | Chaîne | Oui | Document PDF d’entrée à sécuriser ou à signer |
| `certificateAlias` | Chaîne | Conditionnel | Alias du certificat pour les opérations de signature |
| `credentialPassword` | Chaîne | Conditionnel | Mot de passe pour les informations d’identification utilisées lors de la signature |

Pour obtenir des détails complets sur les paramètres, les exigences d’authentification et des exemples de requêtes/réponses, reportez-vous à la documentation de référence spécifique à l’API liée dans les tableaux ci-dessus.

## Ressources supplémentaires {#see-also}

* [Traitement des communications - API synchrones](/help/forms/aem-forms-cloud-service-communications.md)
* [Traitement des communications - API par lots](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)
* [Architecture d’AEM Forms as a Cloud Service](/help/forms/aem-forms-cloud-service-architecture.md)
* [Documentation de référence sur les API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)
* [Fonctionnalités du programme des utilisateurs et utilisatrices précoces](/help/forms/early-access-ea-features.md)
