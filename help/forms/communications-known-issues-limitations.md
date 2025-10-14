---
title: Quelles sont les considérations, les problèmes connus et les bonnes pratiques dans AEM Forms ?
description: Considérations sur les problèmes connus et les bonnes pratiques pour les API de communication AEM Forms.
exl-id: e95615dd-e494-40cd-9cdf-6e9761ca3b3e
feature: Adaptive Forms
role: Admin, Developer, User
source-git-commit: 975f767e75a268a1638227ae20a533f82724c80a
workflow-type: tm+mt
source-wordcount: '1733'
ht-degree: 94%

---

# Considérations, problèmes connus et bonnes pratiques {#best-practices-known-issues-and-limitations}

Avant de commencer à utiliser les API de communication, passez en revue les considérations, les problèmes connus et les questions fréquentes suivantes :

## Considérations  {#considerations-for-communications-apis}

### Données de formulaire {#form-data}

Les API Communications acceptent à la fois un type de formulaire généralement créé dans Designer et les données de formulaire XML en tant qu’entrée. Pour remplir un document avec des données, un élément XML doit exister dans les données de formulaire XML pour chaque champ de formulaire à remplir. Le nom de l’élément XML doit correspondre au nom du champ. Un élément XML est ignoré s’il ne correspond pas à un champ de formulaire ou si le nom de l’élément XML ne correspond pas au nom du champ. Il n’est pas nécessaire de correspondre à l’ordre dans lequel les éléments XML sont affichés. Le facteur important est que les éléments XML sont spécifiés avec les valeurs correspondantes.

Examinez l’exemple de formulaire de demande de prêt suivant :

![Formulaire de demande de prêt](assets/loanFormData.png)

Pour fusionner les données dans ce design de formulaire, créez une source de données XML correspondant au formulaire. Le code XML suivant représente une source de données XML correspondant à l’exemple de formulaire de demande de prêt immobilier.

```XML
<?xml version="1.0" encoding="UTF-8" ?>
- <xfa:datasets xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/">
- <xfa:data>
- <data>
    - <Layer>
        <closeDate>1/26/2007</closeDate>
        <lastName>Johnson</lastName>
        <firstName>Jerry</firstName>
        <mailingAddress>JJohnson@NoMailServer.com</mailingAddress>
        <city>New York</city>
        <zipCode>00501</zipCode>
        <state>NY</state>
        <dateBirth>26/08/1973</dateBirth>
        <middleInitials>D</middleInitials>
        <socialSecurityNumber>(555) 555-5555</socialSecurityNumber>
        <phoneNumber>5555550000</phoneNumber>
    </Layer>
    - <Mortgage>
        <mortgageAmount>295000.00</mortgageAmount>
        <monthlyMortgagePayment>1724.54</monthlyMortgagePayment>
        <purchasePrice>300000</purchasePrice>
        <downPayment>5000</downPayment>
        <term>25</term>
        <interestRate>5.00</interestRate>
    </Mortgage>
</data>
</xfa:data>
</xfa:datasets>
```

### Types de documents pris en charge {#supported-document-types}

Pour un accès complet aux fonctionnalités de rendu des API Communications, il est recommandé d’utiliser un fichier XDP comme entrée. Il est parfois possible d’utiliser un seul fichier PDF. Toutefois, l’utilisation d’un fichier PDF en entrée présente les restrictions suivantes :

Un document PDF qui ne contient pas de flux XFA ne peut pas être rendu au format PostScript, PCL ou ZPL. Les API Communications peuvent générer des documents PDF avec des flux XFA (c’est-à-dire des formulaires créés dans Designer) au format laser et d’étiquettes. Si le document PDF est signé, certifié ou contient des droits d’utilisation (appliqués à l’aide du service AEM Forms Reader Extensions), il ne peut pas être rendu dans ces formats d’impression.


### Zones imprimables {#printable-areas}

La marge non imprimable de 0,25 pouces par défaut n’est pas exacte pour les imprimantes d’étiquettes et varie d’une imprimante à l’autre. Il est toutefois recommandé de conserver la marge de 0,25 pouces ou de la réduire. Il est toutefois recommandé de ne pas augmenter la marge non imprimable. Dans le cas contraire, les informations de la zone imprimable ne s’impriment pas correctement.

Assurez-vous toujours d’utiliser le fichier XDC approprié pour l’imprimante. Par exemple, évitez de choisir un fichier XDC pour une imprimante 300 dpi et d’envoyer le document vers une imprimante 200 dpi.

### Scripts pour les formulaires XFA (XDP/PDF uniquement) {#scripts}

Un design de formulaire utilisé avec les API Communications peut contenir des scripts qui s’exécutent sur le serveur. Assurez-vous qu’un design de formulaire ne contient pas de scripts exécutés sur le client. Pour plus d’informations sur la création de scripts de design de formulaire, voir l’[aide de Designer](use-forms-designer.md).

<!-- #### Working with Fonts
 Document Considerations for Working with Fonts>> -->

### Mappage de polices {#font-mapping}

Pour concevoir un formulaire qui utilise des polices installées sur l’imprimante, choisissez dans Designer un nom de police correspondant aux polices disponibles sur l’imprimante. La liste des polices prises en charge pour PCL ou PostScript se trouve dans les profils d’appareils correspondants (fichiers XDC). Vous pouvez également créer un mappage des polices pour mapper les polices non installées sur l’imprimante aux polices installées sur l’imprimante d’un autre nom de police. Par exemple, dans un scénario PostScript, les références à la police Arial® peuvent être mappées à la police Helvetica® installée sur l’imprimante.

Si une police est installée sur un ordinateur client, elle est disponible dans la liste déroulante de Designer. Si la police n’est pas installée, il est nécessaire de la spécifier manuellement. L’option &quot;Remplacer définitivement les polices non disponibles&quot; dans Designer peut être désactivée. Dans le cas contraire, lorsque le fichier XDP est enregistré dans Designer, le nom de la police de substitution est écrit dans le fichier XDP. Cela signifie que la police installée sur l’imprimante n’est pas utilisée.

Il existe deux types de polices OpenType®. Un type est une police OpenType® TrueType prise en charge par PCL. L’autre est l’OpenType CFF®. Les sorties PDF et PostScript prennent en charge les polices Type-1, TrueType et OpenType® incorporées. La sortie PCL prend en charge les polices TrueType incorporées.

Les polices Type-1 et OpenType® ne sont pas incorporées dans la sortie PCL. Le contenu formaté avec les polices Type-1 et OpenType® est pixellisé et généré sous la forme d’une image bitmap pouvant être grande et plus lente à générer.

Les polices téléchargées ou incorporées sont automatiquement remplacées lors de la génération d’une sortie PostScript, PCL ou PDF. Cela signifie que seul le sous-ensemble des glyphes de police requis pour effectuer correctement le rendu du document généré est inclus dans la sortie générée.

### Utilisation des fichiers de profil de l’appareil (fichier XDC) {#working-with-xdc-files}

Un profil d’appareil (fichier XDC) est un fichier de description d’imprimante au format XML. Ce fichier permet aux API Communications de produire des documents sous la forme de formats d’imprimantes laser ou d’imprimantes d’étiquettes. Les API de communication utilisent les fichiers XDC, notamment les suivants :

* hppcl5c.xdc

* hppcl5e.xdc

* ps_plain_level3.xdc

* ps_plain.xdc

* zpl300.xdc

* zpl600.xdc

* zpl300.xdc

* ipl300.xdc

* ipl400.xdc

* tpcl600.xdc

* dpl300.xdc

* dpl406.xdc

* dpl600.xdc

Vous pouvez utiliser les fichiers XDC fournis pour générer des documents d’impression ou les modifier en fonction de vos besoins.
<!-- It is not necessary to modify these files to create documents. However, you can modify them to meet your business requirements. -->

Ces fichiers sont des fichiers XDC de référence qui prennent en charge les fonctionnalités d’imprimantes spécifiques, telles que les polices propres à l’imprimante, les bacs d’alimentation papier et les agrafeuses. L’objectif de cette référence est de vous aider à comprendre comment configurer vos propres imprimantes à l’aide de profils d’appareil. Les références sont également un point de départ pour des imprimantes similaires dans la même gamme de produits.

### Utilisation du fichier de configuration XCI {#working-with-xci-files}

Les API Communications utilisent un fichier de configuration XCI pour effectuer des tâches, comme contrôler si la sortie est un panneau unique ou si elle est paginée. Bien que ce fichier contienne des paramètres qui peuvent être définis, il n’est pas courant de modifier cette valeur. <!-- The default.xci file is located in the svcdata\XMLFormService folder. -->

Vous pouvez transmettre un fichier XCI modifié en utilisant une API Communications. Pour ce faire, créez une copie du fichier par défaut, modifiez uniquement les valeurs qui doivent être modifiées pour répondre aux besoins de votre entreprise et utilisez le fichier XCI modifié.

Les API Communications commencent par le fichier XCI par défaut (ou le fichier modifié). Ensuite, elles appliquent les valeurs spécifiées à l’aide des API Communications. Ces valeurs remplacent les paramètres XCI.

Le tableau suivant indique les options XCI.

| Option XCI | Description |
| ------------------------------------| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| config/present/pdf/creator | Identifie le créateur du document à l’aide de l’entrée Créateur du dictionnaire d’informations sur le document. Pour plus d’informations sur ce dictionnaire, consultez le guide de référence PDF. |
| config/present/pdf/producer | Identifie le producteur du document à l’aide de l’entrée Producteur du dictionnaire d’informations sur le document. Pour plus d’informations sur ce dictionnaire, consultez le guide de référence PDF. |
| config/present/layout | Contrôle si la sortie est un panneau unique ou si elle est paginée. |
| config/present/pdf/compression/level | Indique le degré de compression à utiliser lors de la génération d’un document PDF. |
| config/present/pdf/scriptModel | Contrôle si des informations spécifiques à XFA sont incluses dans le document PDF de sortie. |
| config/present/common/data/adjustData | Contrôle si l’application XFA ajuste les données après la fusion. |
| config/present/pdf/renderPolicy | Contrôle si la génération du contenu de la page est effectuée sur le serveur ou différée au client. |
| config/present/common/locale | Spécifie le paramètre régional par défaut utilisé dans le document de sortie. |
| config/present/destination | Lorsque contenu par un élément présent, indique le format de sortie. Lorsqu’il est contenu par un élément openAction, spécifie l’action à effectuer lors de l’ouverture du document dans un client interactif. |
| config/present/output/type | Spécifie le type de compression à appliquer à un fichier ou le type de sortie à produire. |
| config/present/common/temp/uri | Spécifie l’URI du formulaire. |
| config/present/common/template/base | Fournit un emplacement de base pour les URI dans le design de formulaire. Lorsque cet élément est absent ou vide, l’emplacement du design de formulaire est utilisé comme base. |
| config/present/common/log/to | Contrôle l’emplacement dans lequel les données du journal ou les données de sortie sont écrites. |
| config/present/output/to | Contrôle l’emplacement dans lequel les données du journal ou les données de sortie sont écrites. |
| config/present/script/currentPage | Indique la page initiale à l’ouverture du document. |
| config/present/script/exclude | Informe le serveur AEM Forms et les API Communications des événements à ignorer. |
| config/present/pdf/linearized | Contrôle si le document PDF de sortie est linéarisé. |
| config/present/script/runScripts | Contrôle l’ensemble de scripts qu’AEM Forms exécute. |
| config/present/pdf/tagged | Contrôle l’inclusion de balises dans le document PDF de sortie. Les balises, dans le contexte d’un PDF, sont des informations supplémentaires incluses dans un document afin d’exposer la structure logique du document. Les balises aident à l’accessibilité et au reformatage. Par exemple, un numéro de page peut être balisé en tant qu’artefact afin qu’un lecteur d’écran ne l’indique pas au milieu du texte. Bien que les balises rendent un document plus utile, elles augmentent également sa taille et le temps de traitement pour le créer. |
| config/present/pdf/version | Spécifie la version du document PDF à générer. |


## Problèmes connus

* Vous ne pouvez utiliser un type de rendu spécifique (PDF, IMPRESSION) qu’une seule fois dans la liste des options d’impression. Par exemple, vous ne pouvez pas définir deux options IMPRESSION spécifiant chacune un type de rendu PCL.

* Pour une configuration de lot, une seule instance de combinaison de valeurs OutputType(PDF, PRINT) et RenderType (PostScript, PCL, IPL, ZPL, etc.) est autorisée.

* Pour les API asynchrones (traitement par lot), le niveau d’enregistrement par défaut est défini sur 2. Vous pouvez utiliser un fichier XCI personnalisé pour définir le niveau d’enregistrement sur 1.

* Lorsque le fichier XCI par défaut est configuré, il inclut le chemin d’accès jusqu’au rendu d’origine. Par exemple, `/content/dam/formsanddocuments/default.xci/jcr:content/renditions/original`



## Bonnes pratiques

* Adobe recommande d’héberger le magasin de conteneurs blob de fichiers de données dans la région cloud utilisée par AEM Cloud Service.

## Questions fréquemment posées  {#faq}

**Puis-je utiliser un dossier de contrôle ou d’autres mécanismes de stockage pour stocker les entrées et les sorties ?**

Actuellement, vous pouvez utiliser le stockage Azure Microsoft pour enregistrer les données d’entrée et les documents générés. Le stockage Microsoft Azure offre diverses options pour [automatiser les opérations de déplacement des données](https://docs.microsoft.com/fr-fr/azure/storage/common/storage-use-azcopy-v10).

**Un compte de stockage Azure Microsoft est-il inclus avec la licence Experience Manager Forms Cloud Service ?**

Le compte de stockage Microsoft Azure est indépendant de la licence Experience Manager Forms Cloud Service.

**Les API Communications stockent-elles des données sur les serveurs de Service Experience Manager Forms Cloud Service ?**

Les données d’entrée et de sortie sont enregistrées uniquement sur le stockage Microsoft Azure.

**Les API Communications sont-elles disponibles uniquement pour Experience Manager Forms Cloud Service ? Puis-je obtenir des fonctionnalités similaires dans un environnement On-Premise ?**

Vous pouvez utiliser le service AEM Forms Output pour combiner un modèle (XFA ou PDF) avec des données client afin de générer des documents aux formats PDF, PS, PCL et ZPL.

Par rapport à l’environnement On-Premise, le service cloud offre des avantages supplémentaires liés à la mise à l’échelle automatique et à la rentabilité.

<!--**Where is data processed?**

**Who has access to data?**

**Is data encrypted?**

**Where is data hosted?** -->

**Puis-je exécuter plusieurs opérations par lots simultanément ?**
Oui, vous pouvez exécuter plusieurs opérations par lots simultanément. Pour éviter tout conflit, utilisez toujours des dossiers source et de destination différents pour chaque opération.

>[!MORELIKETHIS]
>
>* [Présentation des communications as a Cloud Service AEM Forms](/help/forms/aem-forms-cloud-service-communications-introduction.md)
>* [&#x200B; Architecture as a Cloud Service AEM Forms pour les API de communication et de Forms adaptatifs](/help/forms/aem-forms-cloud-service-architecture.md)
>* [Traitement des communications - API synchrones](/help/forms/aem-forms-cloud-service-communications.md)
>* [Traitement des communications - API de lot](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)

