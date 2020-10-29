---
title: Configuration multi-magasin
description: Découvrez comment mettre en correspondance plusieurs vues de stockage du Magento à l’AEM. Cela permet aux projets de prendre en charge les cas d’utilisation multilocataires et multilingues.
sub-product: Commerce
version: cloud-service
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 3046
thumbnail: 28952.jpg
translation-type: tm+mt
source-git-commit: 4862a09b3a0ce2f7506f4fff10639c51792db1b7
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 4%

---


# Configuration multi-magasin {#multi-store}

Les composants AEM CIF Core Components peuvent être utilisés sur plusieurs structures de site AEM et l&#39;implémentation sous-jacente du client GraphQL peut se connecter à différentes vues de stockage/magasins Magento. Cela permet aux projets de mettre en oeuvre des configurations complexes multi-sites/multi-sites.

Présentation vidéo détaillant les options d’intégration de plusieurs Vues de stockage de Magento à Adobe Experience Manager Sites.

>[!VIDEO](https://video.tv.adobe.com/v/28952/?quality=12)

aem fonctions de gestion multisite de Live Copy et de la Copie de langue sont utilisées conjointement avec Commerce Integration Framework pour gérer globalement les sites dans les régions et les paramètres régionaux.

La configuration recommandée consiste à utiliser une relation 1:1 entre le site AEM et la vue de stockage Magento.

Pour connecter un site AEM et AEM CIF Core Components ainsi qu&#39;à une vue de stockage dédiée, procédez comme suit :

## Configuration {#configuration}

1. Configurez plusieurs magasins et vues de stockage en fonction du modèle décrit dans Sites Web, Magasins et Vues [Magento](https://docs.magento.com/m2/ce/user_guide/stores/websites-stores-views.html)

2. Assurez-vous que la connexion entre AEM et Magento fonctionne.

3. Créez une configuration enfant de la configuration du Cloud Service CIF en procédant comme suit :

   * Dans AEM accédez à Outils -> Général -> [Configuration Navigateur](/help/implementing/developing/introduction/configurations.md#using-configuration-browser)
   * Sélectionnez la configuration de base que vous avez créée.
   * Créer une nouvelle configuration en suivant les étapes décrites au point 2 ci-dessus

   Cette nouvelle configuration sera créée en tant que configuration enfant de la configuration de base. Vous pouvez maintenant accéder à Outils -> Général -> Navigateur de configuration et créer les paramètres de configuration.

4. Affecter la configuration enfant à un site AEM

   * Accéder à la console AEM Sites
   * Accédez à la région ou à la langue racine de la structure de votre site, par exemple. /content/venia/us _ou_ /content/venia/us/fr pour la page d’exemple Venia
   * Sélectionnez la page et ouvrez ses propriétés.
   * Sélectionnez l’onglet Avancé
   * Dans la `Configuration` section, sélectionnez la configuration que vous avez créée à l’étape

## Ressources supplémentaires

* [Sites Web, magasins et Vues Magento](https://docs.magento.com/m2/ce/user_guide/stores/websites-stores-views.html)
* [Composants principaux AEM CIF - Configuration de sites/magasins multiples](https://github.com/adobe/aem-core-cif-components/wiki/configuration#multi-store--site-configuration)
* [Utilisation de Multi-Site Manager](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/translation/multi-site-manager-feature-video-use.html)
* [Réutilisation de contenu : Multi Site Manager et Live Copy](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/msm.html)
