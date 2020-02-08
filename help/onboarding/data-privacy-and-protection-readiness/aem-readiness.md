---
title: Règlement sur la protection des données et la confidentialité des données - Adobe Experience Manager comme outil de préparation au service Cloud
description: 'Découvrez Adobe Experience Manager en tant que support du service Cloud pour les différentes réglementations sur la protection des données et la confidentialité des données ; y compris le règlement général de protection des données (RDPC) de l’UE, la loi sur la protection des renseignements personnels des consommateurs de Californie et la façon de s’y conformer lors de la mise en oeuvre d’un nouveau projet AEM en tant que service cloud. '
translation-type: tm+mt
source-git-commit: 2b7ee2b7b0ce351ed48aeb2f3135c947eafe7247

---


# Adobe Experience Manager comme outil de préparation au service Cloud pour la protection des données et la confidentialité des données {#aem-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>Le contenu de ce document ne constitue pas un avis juridique et ne se substitue pas à un avis juridique.
>
>Veuillez consulter le service juridique de votre entreprise pour obtenir des conseils concernant les règles de protection des données et de confidentialité des données.

>[!NOTE]
>
>Pour plus d’informations sur la réponse d’Adobe aux problèmes de confidentialité et sur ce que cela signifie pour vous en tant que client Adobe, consultez le Centre [de confidentialité d’](https://www.adobe.com/privacy.html)Adobe.

Adobe fournit de la documentation et des procédures (avec des API, le cas échéant), à l’administrateur de la confidentialité des clients ou à l’administrateur AEM pour qu’ils puissent traiter les demandes de protection des données et de confidentialité des données et aider nos clients à se conformer à ces règles. Les procédures documentées permettront aux clients d’exécuter les demandes de réglementation manuellement ou en appelant les API, le cas échéant, à partir d’un portail ou d’un service externe.

>[!CAUTION]
>
>Les détails décrits ici sont limités à Adobe Experience Manager en tant que service Cloud.
>
>Les données provenant d’un autre service à la demande Adobe, ainsi que toute demande de confidentialité associée, nécessiteront des actions à entreprendre sur ce service.
>
>Pour plus d’informations, consultez le Centre [de confidentialité d’](https://www.adobe.com/privacy.html)Adobe.

## Présentation {#introduction}

Les instances d’Adobe Experience Manager en tant que service Cloud et les applications qui s’exécutent dessus sont détenues et exploitées par nos clients.

Par conséquent, les règlements sur la protection des données, comme le RMCT, l&#39;ACCP et d&#39;autres, relèvent en grande partie de la responsabilité des clients.

En guise d&#39;introduction très brève, les règlements sur la protection et la confidentialité des données comprennent de nouvelles règles qui seront suivies des rôles suivants :

* Entités commerciales (ACCP) et/ou contrôleurs de données (RMMR)

* Fournisseurs de services (ACCP) et/ou Processeurs de données (RMMR)

Les principales dispositions de ces règlements sont les suivantes :

1. Définition étendue des données à caractère personnel pour inclure tous les identifiants uniques ; comme dans les données directement et indirectement identifiables.

2. Renforcement des exigences en matière de consentement.

3. Accent accru sur les droits de suppression (effacement des données).

4. Exclusion de la vente de données.

Pour Adobe Experience Manager en tant que service Cloud :

* Les instances et les applications qui s’exécutent dessus sont détenues et exploitées par le client.

   * Cela signifie que le client gère efficacement les rôles de réglementation, notamment les entités commerciales et les fournisseurs de services, le contrôleur de données et le processeur de données.

   * Le service de confidentialité d’Adobe Experience Platform ne fera pas partie du processus pour AEM, comme illustré dans le diagramme ci-dessous.

* AEM inclut la documentation et les procédures permettant à l’administrateur de la confidentialité du client et/ou à l’administrateur AEM d’exécuter les demandes de réglementation de la confidentialité ; soit manuellement, soit par le biais d’API, le cas échéant.

* Aucun nouveau service ou interface utilisateur n’a été ajouté.

   * Les procédures et les API sont plutôt documentées pour être utilisées par les interfaces utilisateur/portails du client qui gèrent les demandes de réglementation de la confidentialité.

* AEM n’inclut aucun outil prêt à l’emploi pour prendre en charge le flux de travaux des demandes de confidentialité.

   * Adobe fournit une documentation et des procédures à l’administrateur de la confidentialité du client et/ou à l’administrateur AEM, lui permettant ainsi d’exécuter manuellement les requêtes liées aux règles de confidentialité.

Adobe fournit des procédures pour traiter les demandes de confidentialité liées à Access, Delete et Opt-Out pour Adobe Experience Manager en tant que service Cloud. Dans certains cas, des API peuvent être appelées à partir d’un portail développé par le client ou de scripts pour faciliter l’automatisation.

Le diagramme suivant illustre l’aspect d’un processus de demande de confidentialité (illustré à l’aide d’Adobe Experience Manager 6.5) :

![Protection des données et confidentialité](assets/data-protection-and-privacy-01.png)

## Adobe Experience Manager en tant que service Cloud et état de préparation réglementaire {#aem-as-a-cloud-service-and-regulatory-readiness}

Consultez les sections ci-dessous pour obtenir de la documentation sur la réglementation des zones de produits d’AEM en tant que service Cloud.

## Adobe Experience Manager en tant que fondation de service cloud {#aem-foundation}

Reportez-vous à la page [AEM Foundation Readiness for Data Protection and Data Privacy Regulations](/help/onboarding/data-privacy-and-protection-readiness/foundation-readiness.md).

## Adobe Experience Manager en tant que sites de services Cloud {#aem-sites}

Reportez-vous à la page [AEM Sites Readiness for Data Protection and Data Privacy Regulations.](/help/onboarding/data-privacy-and-protection-readiness/sites-readiness.md)

## Intégration d’Adobe Experience Manager en tant que service Cloud avec Adobe Target et Adobe Analytics {#aem-integration-with-adobe-target-adobe-analytics}

Ces intégrations d’Adobe Experience Manager en tant que service Cloud s’accompagnent de services de protection des données et de confidentialité (par exemple, GDPR) prêts à l’emploi. Aucune donnée personnelle provenant d’Adobe Target ou d’Adobe Analytics n’est stockée dans AEM par rapport aux intégrations.
Pour plus d’informations, voir :

* [Adobe Target - Présentation de la confidentialité](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/privacy.html)

* [Flux de travaux de confidentialité des données Adobe Analytics](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/an-gdpr-workflow.html)
