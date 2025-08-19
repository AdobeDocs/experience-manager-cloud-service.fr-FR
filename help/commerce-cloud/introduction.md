---
title: Présentation et vue d’ensemble
description: Comprendre les différentes options de storefront
thumbnail: introducing-aem-commerce.jpg
exl-id: 29410f76-a63f-4b0a-b817-2ed724ad1a3c
feature: Commerce Integration Framework
role: Admin
source-git-commit: 80f1c9548b8b87dc6280e0e95988d84a8376f7ab
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 1%

---


# Content and Commerce {#content-commerce}

À mesure que les attentes des clients concernant les expériences commerciales basées sur les intentions et hautement performantes augmentent, les marques subissent une pression pour diffuser plus de contenu plus rapidement, sans sacrifier la qualité. Avec Adobe Experience Manager, les marques peuvent évoluer et innover plus rapidement pour créer des expériences commerciales immersives, capter plus de trafic et augmenter les dépenses en ligne.

Adobe Experience Manager propose des outils puissants pour créer et gérer des expériences client personnalisées et riches en contenu. En intégrant AEM à une solution de commerce, telle qu’Adobe Commerce, Salesforce Commerce, SAP Commerce Cloud ou toute autre solution, les marques peuvent unifier le contenu et le commerce pour offrir des parcours d’achat transparents sur l’ensemble des canaux.

## Présentation des approches de storefront {#overview}

AEM peut vous aider en fonction de votre situation et de vos préférences. Suivez les conseils suivants pour choisir l’approche qui vous convient :

* [Utiliser Edge Delivery Services (recommandé)](#edge)
* [Utiliser votre propre storefront (intégration d’AEM découplé)](#own-storefront)
* [Utilisation du storefront AEM CIF](#cif)

### Utiliser Edge Delivery Services (Recommandé) {#edge}

Si votre entreprise souhaite la vitrine la plus rapide et la plus conviviale pour l&#39;IA sur le web et que vos développeurs souhaitent une expérience de développement à la pointe de la technologie, utilisez [Edge Delivery Services.](../edge/overview.md) Edge Delivery Services répond à toutes les exigences d’aujourd’hui et de demain. Selon notre serveur principal et notre solution, vous disposez de différentes options :

#### &#x200B;1. Intégration à Adobe Commerce as a Cloud Service {#acaacs}

Adobe recommande d’utiliser Edge Delivery et [Adobe Commerce Storefront](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=fr) comme point de départ. Le storefront s’accompagne d’un standard préintégré aux services et API Adobe Commerce et propose divers composants de dépôt Commerce pour créer rapidement un storefront.

Ajustement : expérience de storefront typique avec Adobe Commerce as a Cloud Service

#### &#x200B;2. Intégration à Adobe Commerce Optimizer (pour toute solution tierce) {#aco}

Adobe Si vous souhaitez intégrer votre solution de commerce existante et améliorer les performances de votre catalogue, nous vous recommandons d’utiliser [Adobe Commerce Optimizer](https://experienceleague.adobe.com/fr/docs/commerce-learn/tutorials/adobe-commerce-optimizer/overview) comme couche d’intégration moderne. Commerce Optimizer améliore votre solution commerciale grâce à des services SaaS haute performance de catalogue et de marchandisage. Comme pour Adobe Commerce as a Cloud Service, [le storefront Adobe Commerce](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=fr) fonctionne avec celui-ci prêt à l’emploi.

Des intégrations à des solutions de commerce telles que Salesforce Commerce sont disponibles. Contactez votre représentant Adobe.

Adaptation : expérience de storefront typique avec une solution de commerce existante

#### &#x200B;3. Intégration personnalisée {#custom}

Adobe recommande également d’utiliser Edge Delivery Services si vous souhaitez créer une intégration personnalisée. Vous pouvez soit commencer à partir de zéro, soit réutiliser les composants commerciaux JS-framework existants (par exemple, pour la partie transactionnelle) dans votre storefront Edge Delivery. De cette façon, vos clients obtiendront une expérience d&#39;achat incroyablement rapide et conviviale pour les agents, tandis que vous pourrez réutiliser vos investissements existants pour augmenter la télévision. Votre point de départ est le [modèle Edge Delivery par défaut](https://www.aem.live/developer/tutorial).

Ajustement : faible valeur du storefront de diffusion Edge

### Utiliser votre propre storefront (intégration d’AEM découplé) {#own-storefront}

Vous disposez déjà d’un storefront (par exemple, créé avec React JS) et souhaitez utiliser Adobe Experience Manager pour la gestion et la diffusion de contenu (fragments de contenu), les ressources, ainsi que la modification contextuelle (éditeur universel). Votre point de départ pour une intégration est [Présentation de Adobe Experience Manager as a Headless CMS](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/headless/introduction) et le module complémentaire [CIF](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/content-and-commerce/storefront/authoring/enrich-product-associated-content). Le module complémentaire CIF permet une intégration transparente des données de vos produits dans AEM (recherche, navigation et recherche de produits dans l’interface utilisateur d’AEM) que vous pouvez utiliser pour créer des expériences spécifiques au commerce.

### storefront AEM CIF {#cif}

L’architecture de recommandation et de référence d’Adobe doit utiliser Edge Delivery Services. Le storefront CIF et ses composants principaux AEM CIF sont désormais en mode de maintenance et ne doivent pas être utilisés dans les nouveaux projets. Pour référence, consultez la documentation de [CIF.](/help/commerce-cloud/cif-storefront/introduction.md)

>[!NOTE]
>
>Les clients existants qui souhaitent tirer parti des nouvelles fonctionnalités d’AEM/Commerce doivent déplacer leur site web vers Edge Delivery. Un modèle courant consiste à commencer par déplacer uniquement un sous-ensemble de pages vers Edge Delivery et à exécuter côte à côte les pages Diffusion Edge et CIF. Il est également possible de remplacer les composants AEM CIF par les nouveaux composants de liste déroulante [Commerce](https://experienceleague.adobe.com/developer/commerce/storefront/dropins/all/introduction/?lang=fr) afin de tirer parti des nouvelles fonctionnalités de Commerce.
