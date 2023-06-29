---
title: Règlements sur la protection et la confidentialité des données – Préparation d’Adobe Experience Manager as a Cloud Service
description: Découvrez la prise en charge d’Adobe Experience Manager as a Cloud Service pour les différents règlements sur la protection et la confidentialité des données. Ces réglementations incluent le Règlement général sur la protection des données (RGPD) de l’UE, la loi sur la protection des consommateurs de Californie et la manière de se conformer lors de la mise en oeuvre d’un nouveau projet as a Cloud Service AEM.
exl-id: 5dfa353b-84c5-4b07-bfcd-b03c2d361553
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 45%

---

# Niveau de préparation d’Adobe Experience Manager as a Cloud Service aux réglementations sur la protection et la confidentialité des données {#aem-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>Le contenu de ce document ne constitue pas un avis juridique et ne vise pas à le remplacer.
>
>Consultez le service juridique de votre entreprise pour obtenir des conseils sur les réglementations relatives à la protection des données et à la confidentialité des données.

>[!NOTE]
>
>Pour plus d’informations sur la réponse de l’Adobe aux problèmes de confidentialité et sur ce que cette confidentialité signifie pour vous en tant que client Adobe, voir [Centre de traitement des données personnelles des Adobes](https://www.adobe.com/fr/privacy.html).

Adobe fournit de la documentation et des procédures (avec des API si elles sont disponibles) à l’administrateur de la confidentialité client ou à l’administrateur AEM. Cette documentation aide les administrateurs à gérer les demandes de protection des données et de confidentialité des données et aide les clients d’Adobe à se conformer à ces réglementations. Les procédures documentées permettent aux clients d’exécuter manuellement les demandes de réglementation ou d’appeler des API, le cas échéant, à partir d’un portail ou d’un service externe.

>[!CAUTION]
>
>Les détails documentés ici sont limités à Adobe Experience Manager as a Cloud Service.
>
>Les données d’un autre service On-demand Adobe, ainsi que toute demande d’accès à des informations personnelles associée, nécessitent des actions à entreprendre sur ce service.
>
>Pour plus d’informations, voir [Centre de traitement des données personnelles des Adobes](https://www.adobe.com/fr/privacy.html).

## Présentation {#introduction}

Les instances d’Adobe Experience Manager as a Cloud Service et les applications qui s’exécutent sur celles-ci sont détenues et exploitées par les clients Adobe.

Ainsi, les règlements relatifs à la protection des données, telles que le RGPD, le CCPA et d’autres, relèvent, en grande partie, de la responsabilité des clients.

En guise d’introduction, les réglementations relatives à la confidentialité et à la protection des données incluent de nouvelles règles qui seront suivies des rôles suivants :

* Entités commerciales (CCPA) et/ou Contrôleurs de données (RGPD)

* Prestataires (CCPA) et/ou Responsables du traitement des données (GDPR)

Les principales dispositions de ces règlements sont les suivantes :

1. Définition étendue des données personnelles pour inclure tous les identifiants uniques ; comme dans des données identifiables directement et indirectement.

2. Amélioration des exigences en matière de consentement.

3. Accent accru sur les droits de suppression (effacement des données).

4. Droit d’opposition (opt-out) à la vente des données.

Pour Adobe Experience Manager as a Cloud Service :

* Les instances et les applications qui s’exécutent sur ces instances sont détenues et exploitées par le client.

   * Cette propriété signifie de manière efficace que le client gère les rôles de réglementation, notamment les entités commerciales et les fournisseurs de services, le contrôleur de données et le responsable du traitement des données.

   * Adobe Experience Platform Privacy Service ne fait pas partie du workflow d’AEM, comme illustré dans le diagramme ci-dessous.

* AEM comprend la documentation et les procédures permettant à l’administrateur de confidentialité du client et/ou à l’administrateur AEM d’exécuter les demandes d’accès à des informations personnelles, le cas échéant, manuellement, ou par le biais d’API.

* Aucun nouveau service ou interface utilisateur n’a été ajouté.

   * Au lieu de cela, les procédures et les API sont documentées pour une utilisation par les interfaces utilisateur/portails du client qui gèrent les demandes relatives à la réglementation de la confidentialité.

* AEM n’inclut aucun outil prêt à l’emploi pour prendre en charge le workflow de demandes d’accès à des informations personnelles.

   * Adobe fournit de la documentation et des procédures à l’intention de l’administrateur de la confidentialité du client, de l’administrateur d’AEM, ou des deux, ce qui leur permet d’exécuter manuellement des requêtes liées aux réglementations de confidentialité.

Adobe fournit des procédures pour le traitement des demandes d’accès à des informations personnelles liées à l’accès, la suppression et l’exclusion pour Adobe Experience Manager as a Cloud Service. Il existe parfois des API disponibles qui peuvent être appelées à partir d’un portail développé par le client ou de scripts pour faciliter l’automatisation.

Le diagramme suivant illustre à quoi pourrait ressembler un workflow de demande d’accès à des informations personnelles (illustré à l’aide d’Adobe Experience Manager 6.5) :

![Protection et confidentialité des données](assets/data-protection-and-privacy-01.png)

## Adobe Experience Manager as a Cloud Service et préparation par rapport à la réglementation {#aem-as-a-cloud-service-and-regulatory-readiness}

Consultez les sections ci-dessous pour obtenir de la documentation sur la réglementation des domaines de produit d’AEM as a Cloud Service.

## Adobe Experience Manager as a Cloud Service Foundation {#aem-foundation}

Voir la section [Préparation d’AEM Foundation aux réglementations sur la protection et la confidentialité des données](/help/compliance/data-privacy-and-protection-readiness/foundation-readiness.md).

## Adobe Experience Manager Sites as a Cloud Service {#aem-sites}

Voir la section [Préparation d’AEM Sites aux réglementations sur la protection et la confidentialité des données](/help/compliance/data-privacy-and-protection-readiness/sites-readiness.md)

## Intégration d’Adobe Experience Manager as a Cloud Service avec Adobe Target et Adobe Analytics {#aem-integration-with-adobe-target-adobe-analytics}

Ces intégrations sur Adobe Experience Manager as a Cloud Service s’effectuent avec les services prêts pour la protection des données et la confidentialité (par exemple, le RGPD). Aucune donnée personnelle provenant d’Adobe Target ou d’Adobe Analytics n’est stockée dans AEM en lien avec les intégrations.
Pour en savoir plus, voir :

* [Adobe Target – Présentation de la confidentialité](https://experienceleague.adobe.com/docs/target-dev/developer/implementation/privacy/cmp-privacy-and-general-data-protection-regulation.html)

* [Processus relatif à la confidentialité des données Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/data-governance/an-gdpr-workflow.html)
