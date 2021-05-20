---
title: Règlements sur la protection et la confidentialité des données - Adobe Experience Manager en tant que Cloud Service prêt
description: Découvrez la prise en charge d’Adobe Experience Manager en tant que Cloud Service pour les différents règlements sur la protection et la confidentialité des données ; notamment le règlement général sur la protection des données (RGPD) de l’UE, la loi sur la protection de la vie privée des consommateurs de Californie et la manière de se conformer lors de la mise en oeuvre d’une nouvelle AEM en tant que projet Cloud Service.
exl-id: 5dfa353b-84c5-4b07-bfcd-b03c2d361553
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 2%

---

# Adobe Experience Manager en tant que Cloud Service Préparation aux réglementations sur la protection et la confidentialité des données {#aem-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>Le contenu de ce document ne constitue pas un avis juridique et ne vise pas à remplacer un avis juridique.
>
>Veuillez consulter le service juridique de votre entreprise pour obtenir des conseils concernant les réglementations sur la protection des données et la confidentialité des données.

>[!NOTE]
>
>Pour plus d’informations sur la réponse de l’Adobe aux problèmes de confidentialité et sur ce que cela signifie pour vous en tant que client Adobe, voir [Centre de traitement des données personnelles de l’Adobe](https://www.adobe.com/privacy.html).

Adobe fournit de la documentation et des procédures (avec des API, le cas échéant), à l’administrateur de la confidentialité du client ou à l’administrateur AEM afin qu’il traite les demandes de protection des données et de confidentialité des données et aide nos clients à se conformer à ces réglementations. Les procédures documentées permettront aux clients d’exécuter les demandes de réglementation manuellement ou en appelant dans les API, le cas échéant, à partir d’un portail ou d’un service externe.

>[!CAUTION]
>
>Les détails documentés ici sont limités à Adobe Experience Manager en tant que Cloud Service.
>
>Les données d’un autre service On-demand Adobe, ainsi que toute demande d’accès à des informations personnelles associée, nécessiteront des actions à entreprendre sur ce service.
>
>Pour plus d’informations, voir [Centre de traitement des données personnelles des Adobes](https://www.adobe.com/privacy.html).

## Présentation {#introduction}

Les instances d’Adobe Experience Manager en tant que Cloud Service, ainsi que les applications qui s’exécutent dessus, sont détenues et exploitées par nos clients.

Par conséquent, les réglementations relatives à la protection des données, telles que le RGPD, le CCPA et d’autres, sont en grande partie de la responsabilité des clients.

En guise d’introduction très brève, les réglementations relatives à la confidentialité et à la protection des données incluent de nouvelles règles qui seront suivies des rôles suivants :

* Entités commerciales (CCPA) et/ou contrôleurs de données (RGPD)

* Prestataires (CCPA) et/ou Data Processors (GDPR)

Les principales dispositions de ce règlement sont les suivantes :

1. définition étendue des données personnelles pour inclure tous les identifiants uniques ; comme dans des données directement et indirectement identifiables.

2. Amélioration des exigences en matière de consentement.

3. Accent accru sur les droits de suppression (effacement des données).

4. Droit d’opposition (opt-out) à la vente des données.

Pour Adobe Experience Manager as a Cloud Service :

* Les instances et les applications qui s’exécutent sur ces instances sont détenues et exploitées par le client.

   * Cela signifie effectivement que le client gère les rôles de réglementation, notamment les entités commerciales et les fournisseurs de services, le contrôleur de données et le responsable du traitement des données.

   * Adobe Experience Platform Privacy Service ne fait pas partie du workflow d’AEM, comme illustré dans le diagramme ci-dessous.

* AEM comprend la documentation et les procédures permettant à l’administrateur de la confidentialité du client et/ou à l’administrateur AEM d’exécuter les demandes de réglementation sur la confidentialité ; le cas échéant, manuellement ou par le biais d’API.

* Aucun nouveau service ou interface utilisateur n’a été ajouté.

   * Au lieu de cela, les procédures et les API sont documentées pour une utilisation par les interfaces utilisateur/portails du client qui gèrent les demandes de réglementation de la confidentialité.

* AEM n’inclura aucun outil prêt à l’emploi pour prendre en charge le workflow de demandes d’accès à des informations personnelles.

   * Adobe fournira une documentation et des procédures à l’administrateur de la confidentialité du client et/ou à l’administrateur AEM, leur permettant d’exécuter manuellement les demandes liées aux réglementations de confidentialité.

Adobe fournit des procédures pour le traitement des demandes d’accès à des informations personnelles liées à Access, Delete et Opt-out pour Adobe Experience Manager en tant que Cloud Service. Dans certains cas, des API peuvent être appelées à partir d’un portail développé par le client ou de scripts pour faciliter l’automatisation.

Le diagramme suivant illustre à quoi pourrait ressembler un workflow de demande d’accès à des informations personnelles (illustré à l’aide d’Adobe Experience Manager 6.5) :

![Protection et confidentialité des données](assets/data-protection-and-privacy-01.png)

## Adobe Experience Manager en tant que Cloud Service et prêt en matière de réglementation {#aem-as-a-cloud-service-and-regulatory-readiness}

Consultez les sections ci-dessous pour obtenir de la documentation sur la réglementation des domaines de produit d’AEM en tant que Cloud Service.

## Adobe Experience Manager as a Cloud Service Foundation {#aem-foundation}

Voir [AEM Préparation de la base aux réglementations sur la protection et la confidentialité des données](/help/onboarding/data-privacy-and-protection-readiness/foundation-readiness.md).

## Adobe Experience Manager Sites as a Cloud Service {#aem-sites}

Voir [Préparation d’AEM Sites aux réglementations sur la protection et la confidentialité des données.](/help/onboarding/data-privacy-and-protection-readiness/sites-readiness.md)

## Intégration d’Adobe Experience Manager as a Cloud Service avec Adobe Target et Adobe Analytics {#aem-integration-with-adobe-target-adobe-analytics}

Ces intégrations d’Adobe Experience Manager as a Cloud Service sont compatibles avec les services prêts à l’emploi et la protection des données (par exemple, RGPD). Aucune donnée personnelle provenant d’Adobe Target ou d’Adobe Analytics n’est stockée dans AEM par rapport aux intégrations.
Pour plus d’informations, voir :

* [Adobe Target - Présentation de la confidentialité](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/privacy.html)

* [Processus relatif à la confidentialité des données Adobe Analytics](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/an-gdpr-workflow.html)
