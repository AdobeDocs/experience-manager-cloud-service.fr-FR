---
title: Règlements sur la protection et la confidentialité des données – Préparation d’Adobe Experience Manager as a Cloud Service
description: Découvrez la prise en charge d’Adobe Experience Manager as a Cloud Service relative aux différents règlements sur la protection et la confidentialité des données ; notamment le Règlement général sur la protection des données (RGPD) de l’UE et la Loi sur la protection de la vie privée des consommateurs de Californie, ainsi que la manière de se conformer à ces règlements lors de la mise en œuvre d’un nouveau projet AEM as a Cloud Service.
exl-id: 5dfa353b-84c5-4b07-bfcd-b03c2d361553
source-git-commit: e9c1ec6807f86ab00f89ef292a89a0c8efdf802b
workflow-type: tm+mt
source-wordcount: '729'
ht-degree: 100%

---

# Niveau de préparation d’Adobe Experience Manager as a Cloud Service aux réglementations sur la protection et la confidentialité des données {#aem-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>Le contenu de ce document ne constitue pas un avis juridique et ne vise pas à le remplacer.
>
>Consultez le service juridique de votre entreprise pour obtenir des conseils concernant les réglementations sur la protection des données et la confidentialité des données.

>[!NOTE]
>
>Pour plus d’informations sur la réponse d’Adobe à ces questions de données personnelles et sur ce que cela signifie pour vous en tant que client Adobe, consultez le [Centre de traitement des données personnelles d’Adobe](https://www.adobe.com/fr/privacy.html).

Adobe propose de la documentation et des procédures (avec des API si disponibles), afin que l’administrateur de confidentialité du client ou l’administrateur AEM traite la protection des données et les demandes d’accès à des informations personnelles et aide nos clients à se conformer à ces règlements. Les procédures décrites permettront aux clients d’exécuter les demandes légales manuellement ou en appelant les API, si disponibles, à partir d’un portail ou d’un service externe.

>[!CAUTION]
>
>Les détails documentés ici sont limités à Adobe Experience Manager as a Cloud Service.
>
>Les données d’un autre service à la demande d’Adobe, ainsi que toute demande associée d’accès à des informations personnelles, nécessiteront des actions relatives à ce service.
>
>Pour plus d’informations, voir la section [Centre de traitement des données personnelles d’Adobe](https://www.adobe.com/privacy.html).

## Présentation {#introduction}

Les instances d’Adobe Experience Manager as a Cloud Service, ainsi que les applications qui s’y exécutent, sont détenues et exploitées par nos clients.

Ainsi, les règlements relatifs à la protection des données, telles que le RGPD, le CCPA et d’autres, relèvent, en grande partie, de la responsabilité des clients.

En guise d’introduction succincte, les règlements relatifs à la confidentialité et à la protection des données incluent de nouvelles règles qui devront être appliquées par les entités exerçant les rôles suivants :

* Entités commerciales (CCPA) et/ou Contrôleurs de données (RGPD)

* Prestataires (CCPA) et/ou Responsables du traitement des données (GDPR)

Les principales dispositions de ces règlements sont les suivantes :

1. Définition étendue des données personnelles pour inclure tous les identifiants uniques ; comme dans des données identifiables directement et indirectement.

2. Amélioration des exigences en matière de consentement.

3. Accent accru sur les droits de suppression (effacement des données).

4. Droit d’opposition (opt-out) à la vente des données.

Pour Adobe Experience Manager as a Cloud Service :

* Les instances et les applications qui s’exécutent sur ces instances sont détenues et exploitées par le client.

   * Cela signifie effectivement que le client gère les rôles légaux, notamment les entités commerciales et les fournisseurs de services, le contrôleur de données et le responsable du traitement des données.

   * Adobe Experience Platform Privacy Service ne fait pas partie du workflow d’AEM, comme illustré dans le diagramme ci-dessous.

* AEM comprend la documentation et les procédures permettant à l’administrateur de confidentialité du client et/ou à l’administrateur AEM d’exécuter les demandes d’accès à des informations personnelles, le cas échéant, manuellement, ou par le biais d’API.

* Aucun nouveau service ou interface utilisateur n’a été ajouté.

   * Au lieu de cela, les procédures et les API sont documentées pour une utilisation par les interfaces utilisateur/portails du client qui gèrent les demandes relatives à la réglementation de la confidentialité.

* AEM n’inclura aucun outil prêt à l’emploi pour prendre en charge le workflow des demandes d’accès à des informations personnelles.

   * Adobe fournira une documentation et des procédures à l’administrateur de confidentialité du client et/ou à l’administrateur AEM, leur permettant d’exécuter manuellement les demandes liées à la réglementation de la confidentialité.

Adobe fournit des procédures pour le traitement des demandes d’accès à des informations personnelles liées à l’accès, à la suppression et au droit d’opposition pour Adobe Experience Manager as a Cloud Service. Dans certains cas, des API peuvent être appelées à partir d’un portail développé par le client ou de scripts pour faciliter l’automatisation.

Le diagramme suivant illustre à quoi pourrait ressembler un workflow de demande d’accès à des informations personnelles (illustré à l’aide d’Adobe Experience Manager 6.5) :

![Protection et confidentialité des données](assets/data-protection-and-privacy-01.png)

## Adobe Experience Manager as a Cloud Service et préparation par rapport à la réglementation {#aem-as-a-cloud-service-and-regulatory-readiness}

Consultez les sections ci-dessous pour en savoir plus sur la réglementation des domaines de produit d’AEM as a Cloud Service.

## Adobe Experience Manager as a Cloud Service Foundation {#aem-foundation}

Voir la section [Préparation d’AEM Foundation aux réglementations sur la protection et la confidentialité des données](/help/compliance/data-privacy-and-protection-readiness/foundation-readiness.md).

## Adobe Experience Manager Sites as a Cloud Service {#aem-sites}

Voir la section [Préparation d’AEM Sites aux réglementations sur la protection et la confidentialité des données.](/help/compliance/data-privacy-and-protection-readiness/sites-readiness.md)

## Intégration d’Adobe Experience Manager as a Cloud Service avec Adobe Target et Adobe Analytics {#aem-integration-with-adobe-target-adobe-analytics}

Ces intégrations d’Adobe Experience Manager as a Cloud Service sont compatibles avec les services relatifs à la protection et à la confidentialité des données (par exemple, RGPD). Aucune donnée personnelle provenant d’Adobe Target ou d’Adobe Analytics n’est stockée dans AEM en lien avec les intégrations.
Pour plus d’informations, voir :

* [Adobe Target – Présentation de la confidentialité](https://experienceleague.adobe.com/docs/target/using/implement-target/before-implement/privacy/privacy.html?lang=fr)

* [Processus relatif à la confidentialité des données Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/admin/data-governance/an-gdpr-workflow.html?lang=fr)
