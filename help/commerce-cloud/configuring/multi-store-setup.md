---
title: Configuration de plusieurs magasins commerciaux
description: Découvrez comment faire correspondre plusieurs vues de stockage de Magento vers AEM. Cela permet aux projets de prendre en charge des cas d’utilisation à plusieurs clients et multilingues.
sub-product: Commerce
version: cloud-service
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 3046
thumbnail: 28952.jpg
exl-id: 7f6e04a2-89e9-4613-8ea8-9dac1acea30b
translation-type: tm+mt
source-git-commit: 577e5cb9d465c794f29e1b7ed11d26a954e1c072
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 90%

---

# Configuration de plusieurs magasins commerciaux {#multi-store}

Les composants principaux AEM CIF peuvent être utilisés sur plusieurs structures de site AEM et la mise en œuvre du client GraphQL sous-jacent peut se connecter à différents magasins/vues de magasin Magento. Cela permet aux projets de mettre en œuvre des configurations multi-magasin/multi-site complexes.

Présentation vidéo détaillant les options d’intégration de plusieurs vues de magasin Magento à Adobe Experience Manager Sites.

>[!VIDEO](https://video.tv.adobe.com/v/28952/?quality=12)

Les fonctions de gestion multi-site AEM de Live Copy et Language Copy sont utilisées conjointement avec Commerce Integration Framework pour gérer globalement les sites dans les régions et les paramètres régionaux.

La configuration recommandée consiste à utiliser une relation 1:1 entre le site AEM et la vue de magasin Magento.

Pour connecter un site AEM et les composants principaux AEM CIF à une vue de magasin dédiée, procédez comme suit :

## Configuration {#configuration}

1. Configurez plusieurs magasins et vues de magasin en fonction du modèle décrit dans [Sites web, magasins et vues Magento](https://docs.magento.com/m2/ce/user_guide/stores/websites-stores-views.html).

2. Assurez-vous que la connexion entre AEM et Magento fonctionne.

3. Créez une configuration enfant de la configuration de CIF Cloud Service en procédant comme suit :

   * Dans AEM, accédez à Outils > Général > [Explorateur de configurations](/help/implementing/developing/introduction/configurations.md#using-configuration-browser)
   * Sélectionnez la configuration de base que vous avez créée.
   * Créez une configuration en suivant les étapes décrites au point 2 ci-dessus.

   Cette nouvelle configuration sera créée en tant que configuration enfant de la configuration de base. Vous pouvez maintenant accéder à Outils -> Général -> Explorateur de configurations et créer les paramètres de configuration.

   >[!TIP]
   >
   > Les catalogues commerciaux peuvent être traités à l’aide d’ID ou d’UID. Les UID ont été introduits dans le Magento 2.4.2. Activez cette option uniquement si votre serveur principal de commerce prend en charge un schéma GraphQL de la version 2.4.2 ou ultérieure.

4. Affectez la configuration enfant à un site AEM

   * Accédez à la console AEM Sites.
   * Accédez à la racine de région ou de langue de la structure de votre site ; par exemple, /content/venia/us _ou_ /content/venia/us/en pour la page échantillon Venia.
   * Sélectionnez la page et ouvrez ses propriétés.
   * Sélectionnez l’onglet Avancé.
   * Dans la section `Configuration`, sélectionnez la configuration que vous avez créée à l’étape.

## Ressources supplémentaires

* [Sites web, magasins et vues Magento](https://docs.magento.com/m2/ce/user_guide/stores/websites-stores-views.html)
* [Composants principaux AEM CIF – Configuration multi-magasin/site](https://github.com/adobe/aem-core-cif-components/wiki/configuration#multi-store--site-configuration)
* [Utilisation de Multi Site Manager](https://docs.adobe.com/content/help/fr-FR/experience-manager-learn/sites/translation/multi-site-manager-feature-video-use.html)
* [Réutilisation de contenu : Multi Site Manager et Live Copy](/help/sites-cloud/administering/msm/overview.md)
