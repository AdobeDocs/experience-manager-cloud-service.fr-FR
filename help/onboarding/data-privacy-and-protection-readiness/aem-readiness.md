---
title: Règlement sur la protection des données et la confidentialité des données - Adobe Experience Manager en tant que Cloud Service prêt
description: 'Découvrez Adobe Experience Manager comme un support Cloud Service pour les différentes réglementations sur la protection des données et la confidentialité des données ; y compris le règlement général de l''UE sur la protection des données (RGPD), la loi sur la protection des renseignements personnels des consommateurs de Californie et la façon de se conformer lors de la mise en oeuvre d''une nouvelle AEM en tant que projet Cloud Service. '
translation-type: tm+mt
source-git-commit: 2b7ee2b7b0ce351ed48aeb2f3135c947eafe7247
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 2%

---


# Adobe Experience Manager comme Cloud Service Readiness for Data Protection and Data Privacy Regulations {#aem-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>Le contenu de ce document ne constitue pas un conseil juridique et ne se substitue pas à un conseil juridique.
>
>Veuillez consulter le service juridique de votre société pour obtenir des conseils sur les réglementations relatives à la protection des données et à la confidentialité des données.

>[!NOTE]
>
>Pour plus d&#39;informations sur la réponse des Adobes aux questions de confidentialité et sur ce que cela signifie pour vous en tant que client d&#39;Adobe, voir [Centre de confidentialité des Adobes](https://www.adobe.com/privacy.html).

Adobe fournit de la documentation et des procédures (avec des API lorsqu&#39;elles sont disponibles), pour que l&#39;administrateur de la protection des données des clients ou l&#39;administrateur de l&#39;AEM puisse traiter les demandes de protection des données et de confidentialité des données et aider nos clients à se conformer à ces règles. Les procédures documentées permettront aux clients d&#39;exécuter les demandes de réglementation manuellement ou en appelant les API, le cas échéant, à partir d&#39;un portail ou d&#39;un service externe.

>[!CAUTION]
>
>Les détails documentés ici sont limités à Adobe Experience Manager en tant que Cloud Service.
>
>Les données provenant d&#39;un autre service à la demande d&#39;Adobe, ainsi que toute demande de confidentialité connexe, exigeront que des mesures soient prises à l&#39;égard de ce service.
>
>Pour plus d&#39;informations, voir [Adobe Privacy Center](https://www.adobe.com/privacy.html).

## Présentation {#introduction}

Les instances de Adobe Experience Manager en tant que Cloud Service, et les applications qui s&#39;y exécutent, sont la propriété et l&#39;exploitation de nos clients.

En conséquence, les réglementations en matière de protection des données, telles que le RMPD, l&#39;ACCP et d&#39;autres, relèvent en grande partie de la responsabilité des clients.

En guise d&#39;introduction très brève, la réglementation relative à la protection et à la protection des données comporte de nouvelles règles qui seront suivies des rôles suivants :

* Entités commerciales (ACCP) et/ou contrôleurs de données (RMPD)

* prestataires (CCPA) et/ou processeurs de données (GDPR)

Les principales dispositions de ces règlements sont les suivantes :

1. Définition élargie des données à caractère personnel pour inclure tous les identifiants uniques ; comme dans les données directement et indirectement identifiables.

2. Renforcement des exigences en matière de consentement.

3. Accentuation des droits de suppression (effacement des données).

4. Exclusion de la vente de données.

Pour Adobe Experience Manager en tant que Cloud Service :

* Les instances et les applications qui s’exécutent sur elles sont détenues et exploitées par le client.

   * Cela signifie que le client gère efficacement les rôles de réglementation, notamment les entités commerciales et les Prestataires, le contrôleur de données et le processeur de données.

   * L’Adobe Experience Platform Privacy Service ne fera pas partie du processus d’AEM, comme illustré dans le diagramme ci-dessous.

* aem comprend la documentation et les procédures permettant à l&#39;administrateur de la protection des renseignements personnels du client et/ou à l&#39;administrateur AEM d&#39;exécuter les demandes de réglementation de la protection des renseignements personnels ; soit manuellement, soit par le biais d’API, si disponible.

* Aucun nouveau service ou interface utilisateur n&#39;a été ajouté.

   * En revanche, les procédures et les API sont documentées pour être utilisées par les interfaces utilisateur/portails client qui gèrent les demandes de réglementation de la confidentialité.

* aem n’inclut aucun outil prêt à l’emploi pour prendre en charge le processus de demande de confidentialité.

   * L&#39;Adobe fournira de la documentation et des procédures à l&#39;administrateur de la confidentialité du client et/ou à l&#39;administrateur AEM, leur permettant d&#39;exécuter manuellement les demandes liées à la réglementation sur la confidentialité.

Adobe fournit des procédures pour traiter les demandes de confidentialité liées à Access, Delete and Opt-Out for Adobe Experience Manager en tant que Cloud Service. Dans certains cas, des API peuvent être appelées à partir d’un portail développé par le client ou de scripts pour faciliter l’automatisation.

Le diagramme suivant illustre à quoi peut ressembler un processus de demande de confidentialité (illustré à l’aide de Adobe Experience Manager 6.5) :

![Protection des données et confidentialité](assets/data-protection-and-privacy-01.png)

## Adobe Experience Manager en tant que Cloud Service et prêt réglementaire {#aem-as-a-cloud-service-and-regulatory-readiness}

Veuillez consulter les sections ci-dessous pour obtenir la documentation sur la réglementation des secteurs de produits de l&#39;AEM en tant que Cloud Service.

## Adobe Experience Manager as a Cloud Service Foundation {#aem-foundation}

Voir [AEM Règlement sur la préparation à la protection des données et la confidentialité des données](/help/onboarding/data-privacy-and-protection-readiness/foundation-readiness.md).

## Adobe Experience Manager Sites as a Cloud Service {#aem-sites}

Voir [AEM Sites Readiness for Data Protection and Data Privacy Regulations.](/help/onboarding/data-privacy-and-protection-readiness/sites-readiness.md)

## Adobe Experience Manager en tant qu&#39;intégration Cloud Service avec Adobe Target &amp; Adobe Analytics {#aem-integration-with-adobe-target-adobe-analytics}

Ces Adobe Experience Manager en tant que Cloud Service intégrations sont des services de protection des données et de protection de la vie privée (p. ex., RMMD) prêts à l’emploi. Aucune donnée personnelle provenant d&#39;Adobe Target ou d&#39;Adobe Analytics n&#39;est stockée en AEM par rapport aux intégrations.
Pour plus d’informations, voir :

* [Adobe Target - Présentation de la confidentialité](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/privacy.html)

* [Processus de confidentialité des données Adobe Analytics](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/an-gdpr-workflow.html)
