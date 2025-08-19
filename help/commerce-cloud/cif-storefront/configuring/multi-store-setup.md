---
title: Configuration multi-magasin Commerce
description: Découvrez comment mapper plusieurs vues de magasin d’Adobe Commerce à Adobe Experience Manager. Cela permet aux projets de prendre en charge des cas d’utilisation à plusieurs clients et multilingues.
sub-product: Commerce
version: Experience Manager as a Cloud Service
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 3046
thumbnail: 28952.jpg
exl-id: 4385c9e5-2b25-4f95-952f-72349431cf94
role: Admin
index: false
source-git-commit: 856442039fcd25ec675a6258d182f7a35f590c3c
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 50%

---


# Configuration multi-magasin Commerce {#multi-store}

Les composants principaux CIF Adobe Experience Manager (AEM) peuvent être utilisés sur plusieurs structures de site AEM et l’implémentation du client GraphQL sous-jacent peut se connecter à différents magasins/vues de magasin Adobe Commerce. Cela permet aux projets de mettre en œuvre des configurations multi-magasin/multi-site complexes.

Présentation vidéo détaillant les options d’intégration de plusieurs vues de magasin Adobe Commerce à Adobe Experience Manager Sites.

>[!VIDEO](https://video.tv.adobe.com/v/32820/?quality=12&captions=fre_fr)

Les fonctionnalités de gestion multi-site AEM de Live Copy et Language Copy sont utilisées avec Commerce Integration Framework pour gérer globalement les sites dans les régions et les paramètres régionaux.

La configuration recommandée consiste à utiliser une relation 1:1 entre le site AEM et la vue du magasin Adobe Commerce.

Pour connecter un site AEM et les composants principaux AEM CIF à une vue de magasin dédiée, procédez comme suit :

## Configuration {#configuration}

1. Configurez plusieurs magasins et vues de magasin en fonction du modèle décrit dans [Sites web, magasins et vues Adobe Commerce.](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html?lang=fr)

1. Assurez-vous que la connexion entre AEM et Adobe Commerce fonctionne.

1. Créez une configuration enfant de la configuration de CIF Cloud Service en procédant comme suit :

   * Dans AEM, accédez à Outils > Général > [Explorateur de configurations.](/help/implementing/developing/introduction/configurations.md#using-configuration-browser)
   * Sélectionnez la configuration de base que vous avez créée.
   * Créez une configuration en suivant les étapes décrites au point 2 ci-dessus.

   Cette nouvelle configuration est créée en tant que configuration enfant de la configuration de base. Vous pouvez maintenant accéder à Outils  > Général  > Explorateur de configurations et créer les paramètres de configuration.

   >[!TIP]
   >
   > Les catalogues de commerce peuvent être traités à l’aide d’identifiants ou d’UID. Les UID ont été introduits dans Adobe Commerce 2.4.2. Activez cette option uniquement si votre serveur principal Commerce prend en charge un schéma GraphQL de la version 2.4.2 ou ultérieure.

1. Affectez la configuration enfant à un site AEM.

   * Accédez à la console AEM Sites.
   * Accédez à la racine de région ou de langue du fichier .structure de votre site. Par exemple, `/content/venia/us _or_ /content/venia/us/en` pour l’exemple de page Venia.
   * Sélectionnez la page et ouvrez les propriétés de page.
   * Sélectionnez l’onglet Avancé .
   * Dans la section `Configuration` , sélectionnez la configuration que vous avez créée à l’étape 3.

## Ressources supplémentaires {#additional-resources}

* [Sites web, magasins et vues Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html?lang=fr)
* [Composants principaux AEM CIF – Configuration multi-magasin/site](https://github.com/adobe/aem-core-cif-components/#multi-store--site-configuration?lang=fr)
* [Utilisation de Multi Site Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/translation/multi-site-manager-feature-video-use.html?lang=fr)
* [Réutilisation de contenu : Multi Site Manager et Live Copy](/help/sites-cloud/administering/msm/overview.md)
