---
title: Règlement sur la protection des données et la confidentialité des données - Adobe Experience Manager en tant que service Cloud prêt
description: 'Découvrez Adobe Experience Manager en tant que support du service Cloud pour les différentes réglementations sur la protection des données et la confidentialité des données ; notamment le règlement général de l’UE sur la protection des données (RGPD), la loi sur la protection des renseignements personnels des consommateurs de Californie et la manière de se conformer lors de la mise en oeuvre d’un nouveau projet AEM as a Cloud Service. '
translation-type: tm+mt
source-git-commit: 2b7ee2b7b0ce351ed48aeb2f3135c947eafe7247
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 1%

---


# Adobe Experience Manager en tant que service Cloud Prêt pour la protection des données et la confidentialité des données {#aem-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>Le contenu de ce document ne constitue pas un conseil juridique et ne se substitue pas à un conseil juridique.
>
>Veuillez consulter le service juridique de votre société pour obtenir des conseils sur les réglementations relatives à la protection des données et à la confidentialité des données.

>[!NOTE]
>
>Pour plus d&#39;informations sur la réponse Adobe aux problèmes de confidentialité et sur ce que cela signifie pour vous en tant que client Adobe, consultez le Centre [de confidentialité](https://www.adobe.com/privacy.html)Adobe.

Adobe fournit de la documentation et des procédures (avec des API lorsqu’elles sont disponibles), afin que l’administrateur de la confidentialité des clients ou l’administrateur AEM puissent traiter les demandes de protection des données et de confidentialité des données et aider nos clients à se conformer à ces règles. Les procédures documentées permettront aux clients d&#39;exécuter les demandes de réglementation manuellement ou en appelant les API, le cas échéant, à partir d&#39;un portail ou d&#39;un service externe.

>[!CAUTION]
>
>Les détails décrits ici sont limités à Adobe Experience Manager en tant que service Cloud.
>
>Les données provenant d&#39;un autre service Adobe On-Demand Service, ainsi que toute demande de confidentialité connexe, exigeront que des mesures soient prises sur ce service.
>
>Pour plus d’informations, voir [Adobe Privacy Center](https://www.adobe.com/privacy.html).

## Présentation {#introduction}

Les instances d’Adobe Experience Manager en tant que service Cloud, ainsi que les applications qui s’exécutent dessus, appartiennent à nos clients et sont exploitées par eux.

En conséquence, les réglementations en matière de protection des données, telles que le RMPD, l&#39;ACCP et d&#39;autres, relèvent en grande partie de la responsabilité des clients.

En guise d&#39;introduction très brève, la réglementation relative à la protection et à la protection des données comporte de nouvelles règles qui seront suivies des rôles suivants :

* Entités commerciales (ACCP) et/ou contrôleurs de données (RMPD)

* Prestataires (CCPA) et/ou processeurs de données (GDPR)

Les principales dispositions de ces règlements sont les suivantes :

1. Définition élargie des données à caractère personnel pour inclure tous les identifiants uniques ; comme dans les données directement et indirectement identifiables.

2. Renforcement des exigences en matière de consentement.

3. Accentuation des droits de suppression (effacement des données).

4. Exclusion de la vente de données.

Pour Adobe Experience Manager en tant que service Cloud :

* Les instances et les applications qui s’exécutent sur elles sont détenues et exploitées par le client.

   * Cela signifie que le client gère efficacement les rôles de réglementation, notamment les entités commerciales et les Prestataires, le contrôleur de données et le processeur de données.

   * Le service de confidentialité de la plateforme Adobe Experience Platform ne fera pas partie du processus pour AEM, comme illustré dans le diagramme ci-dessous.

* AEM inclut la documentation et les procédures permettant à l’administrateur de la confidentialité du client et/ou à l’administrateur AEM d’exécuter les demandes de réglementation de la confidentialité ; soit manuellement, soit par le biais d’API, si disponible.

* Aucun nouveau service ou interface utilisateur n’a été ajouté.

   * En revanche, les procédures et les API sont documentées pour être utilisées par les interfaces utilisateur/portails client qui gèrent les demandes de réglementation de la confidentialité.

* AEM n’inclura aucun outil prêt à l’emploi pour prendre en charge le processus de demandes de confidentialité.

   * Adobe fournit de la documentation et des procédures à l’administrateur de la confidentialité du client et/ou à l’administrateur AEM, ce qui leur permet d’exécuter manuellement les requêtes liées aux règles de confidentialité.

Adobe fournit des procédures de traitement des demandes de confidentialité liées à Access, Delete and Opt-Out pour Adobe Experience Manager en tant que service Cloud. Dans certains cas, des API peuvent être appelées à partir d’un portail développé par le client ou de scripts pour faciliter l’automatisation.

Le diagramme suivant illustre à quoi peut ressembler un processus de demande de confidentialité (illustré à l’aide d’Adobe Experience Manager 6.5) :

![Protection des données et confidentialité](assets/data-protection-and-privacy-01.png)

## Adobe Experience Manager en tant que service Cloud et préparation réglementaire {#aem-as-a-cloud-service-and-regulatory-readiness}

Consultez les sections ci-dessous pour obtenir de la documentation sur la réglementation des zones de produits d’AEM as a Cloud Service.

## Adobe Experience Manager as a Cloud Service Foundation {#aem-foundation}

See [AEM Foundation Readiness for Data Protection and Data Privacy Regulations](/help/onboarding/data-privacy-and-protection-readiness/foundation-readiness.md).

## Adobe Experience Manager Sites as a Cloud Service {#aem-sites}

See [AEM Sites Readiness for Data Protection and Data Privacy Regulations.](/help/onboarding/data-privacy-and-protection-readiness/sites-readiness.md)

## Adobe Experience Manager en tant qu’intégration de services Cloud avec Adobe Cible et Adobe Analytics {#aem-integration-with-adobe-target-adobe-analytics}

Ces intégrations Adobe Experience Manager en tant que service Cloud s’inscrivent dans les services de protection des données et de confidentialité (par exemple, GDPR) prêts à l’emploi. Aucune donnée personnelle provenant d’Adobe Cible ou d’Adobe Analytics n’est stockée dans AEM par rapport aux intégrations.
Pour plus d’informations, voir :

* [Cible Adobe - Présentation de la confidentialité](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/privacy.html)

* [Processus de confidentialité des données Adobe Analytics](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/an-gdpr-workflow.html)
