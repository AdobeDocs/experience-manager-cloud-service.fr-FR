---
title: Utilisation de contenu ciblé sur plusieurs sites
description: Si vous devez gérer du contenu ciblé, tel que des activités, des expériences et des offres sur vos différents sites, vous pouvez profiter de la prise en charge de sites multiples intégrée à AEM pour le contenu ciblé
exl-id: 03d2d640-8de8-4c4c-8a1d-756bb2dc8457
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '2890'
ht-degree: 45%

---

# Utilisation de contenu ciblé sur plusieurs sites {#working-with-targeted-content-in-multisites}

Si vous devez gérer du contenu ciblé, tel que des activités, des expériences et des offres sur vos différents sites, vous pouvez profiter de la prise en charge de sites multiples intégrée à AEM pour le contenu ciblé.

>[!NOTE]
>
>L’utilisation de contenu ciblé sur plusieurs sites est une fonctionnalité avancée. Pour utiliser cette fonctionnalité, vous devez connaître [Multi Site Manager](/help/sites-cloud/administering/msm/overview.md) ainsi que l’[intégration d’Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md) à AEM.

Ce document contient les informations suivantes :

* Fournit un bref aperçu de la prise en charge AEM multisite du contenu ciblé.
* Décrit certains scénarios d’utilisation possibles sur la manière de lier des sites (dans une marque).
* Un exemple détaillé de l’utilisation que peuvent faire les spécialistes marketing de cette fonction
* Des instructions détaillées sur l’implémentation de la prise en charge de sites multiples pour le contenu ciblé.

Pour configurer la manière dont vos sites partagent du contenu personnalisé, vous devez effectuer les étapes suivantes :

1. [Création d’une zone](#creating-new-areas) ou [créer une zone comme Live Copy ;](#creating-new-areas). Une zone comprend toutes les activités disponibles pour une *area* de la page, c’est-à-dire l’emplacement sur la page où le composant est ciblé. La création d’une zone crée une zone vide, tandis que la création d’une zone en tant que Live Copy vous permet d’hériter du contenu entre les structures du site.

1. [Lier votre site ou votre page](#linking-sites-to-an-area) à une zone.

Vous pouvez à tout moment suspendre ou restaurer l’héritage. En outre, si vous ne souhaitez pas suspendre l’héritage, vous pouvez également créer des expériences locales. Par défaut, toutes les pages utilisent la zone de Principal, sauf indication contraire.

## Présentation de la prise en charge de sites multiples pour le contenu ciblé {#introduction-to-multisite-support-for-targeted-content}

La prise en charge de sites multiples pour le contenu ciblé est prête à l’emploi. Elle vous permet de pousser le contenu ciblé du gabarit que vous gérez via MSM vers une Live Copy locale ou de gérer des modifications globales et locales du contenu en question.

Vous gérez ces données dans une **zone**. Les zones délimitent le contenu ciblé (activités, expériences et offres) utilisé sur différents sites et fournissent un mécanisme reposant sur MSM afin de créer et de gérer l’héritage du contenu ciblé en même temps que l’héritage de site. Cela évite d’avoir à recréer du contenu ciblé dans les sites hérités.

Au sein d’une zone, seules les activités associées à cette même zone sont poussées comme des Live Copies. Par défaut, la zone de Principal est sélectionnée. Une fois que vous avez créé des zones supplémentaires, vous pouvez les lier à vos sites ou pages pour indiquer le contenu ciblé qui est envoyé.

Un site ou une Live Copy est lié à une zone contenant les activités qui doivent être disponibles sur ce site ou Live Copy. Par défaut, le lien du site ou de la Live Copy est dirigé vers la zone maître, mais vous pouvez lier d’autres zones.

>[!NOTE]
>
>Tenez compte des points suivants lorsque vous utilisez la prise en charge de sites multiples pour le contenu ciblé :
>
>* Lorsque vous utilisez des déploiements ou des Live Copies, une licence MSM est requise.
>* Lorsque vous utilisez la synchronisation avec Adobe Target, une licence Adobe Target est requise.
>

## Scénarios d’utilisation {#use-cases}

Selon votre cas d’utilisation, vous pouvez configurer la prise en charge de sites multiples pour le contenu ciblé de différentes manières. Cette section décrit comment cela fonctionnerait théoriquement avec une seule marque. En outre, dans [Exemple : ciblage de contenu basé sur la géographie](#example-targeting-content-based-on-geography), vous pouvez découvrir une application réelle du ciblage de contenu sur plusieurs sites.

Le contenu ciblé est encapsulé dans des zones appelées , qui définissent la portée des sites ou des pages. Ces zones sont définies au niveau de la marque. Une marque peut contenir plusieurs zones. Les zones peuvent être distinctes entre les marques. Bien qu’une marque ne contienne que la zone maître et soit donc partagée entre toutes les marques, une autre marque peut contenir plusieurs marques (par exemple, par région). Par conséquent, les marques n’ont pas besoin de refléter l’ensemble des zones entre elles.

Avec la prise en charge de sites multiples pour le contenu ciblé, vous pouvez, par exemple, avoir deux sites (ou plus) avec **one** marque qui possède l’une des caractéristiques suivantes :

* Un ensemble complètement *distinct* de contenu ciblé. La modification du contenu ciblé sur un site n’a pas d’incidence sur l’autre site. Les sites qui sont liés à des zones distinctes écrivent et lisent sur leur propre zone configurée. Par exemple :
   * Le site A est lié à la zone X
   * Le site B est lié à la zone Y
* Un ensemble *partagé* de contenu ciblé : la modification sur un site a un impact direct sur les deux sites. Cela est possible en configurant deux sites de façon à ce qu’ils fassent référence à la même zone. Les sites qui sont liés à la même zone partagent le contenu ciblé au sein de cette zone. Par exemple :
   * Le site A est lié à la zone X
   * Le site B est lié à la zone X
* Un ensemble distinct de contenu ciblé *hérité* d’un autre site via MSM : le contenu peut être déployé, dans une seule direction, du maître vers la Live Copy. Par exemple :
   * Le site A est lié à la zone X
   * Le site B est lié à la zone Y (qui est une Live Copy de la zone X)

Vous pouvez également **multiple** les marques utilisées sur un site, qui peuvent être plus complexes que cet exemple.

![Exemple de sites multiples](/help/sites-cloud/authoring/assets/multisite-example.png)

>[!NOTE]
>
>Pour une approche plus technique de cette fonction, consultez la section [Structure de la gestion multisite pour le contenu ciblé](/help/sites-cloud/authoring/personalization/multisite-structure.md).

## Exemple : ciblage de contenu basé sur la géographie {#example-targeting-content-based-on-geography}

L’utilisation de sites multiples pour le contenu ciblé vous permet de partager, déployer ou isoler du contenu de personnalisation. Pour mieux illustrer l’utilisation de cette fonctionnalité, imaginez un scénario dans lequel vous souhaitez contrôler la manière dont le contenu ciblé est déployé en fonction de la géographie, comme dans le scénario suivant :

Il existe quatre versions d’un même site en fonction de la géographie :

* La variable **États-Unis** se trouve dans le coin supérieur gauche et est le site maître. Dans cet exemple, il est ouvert en mode Ciblage.
* Les trois autres versions de ce site sont : **Canada**, **Grande-Bretagne**, et **Australie**, qui sont toutes des Live Copies. Ces sites sont ouverts en mode Aperçu.

![Versions de sites multiples](/help/sites-cloud/authoring/assets/multisite-versions.png)

Chaque site partage du contenu personnalisé dans des régions géographiques :

* Le Canada partage la zone maître avec les États-Unis.
* La Grande-Bretagne est liée à la zone européenne et hérite de la zone maître.
* L’Australie possède son propre contenu personnalisé, car elle se situe dans l’hémisphère sud et les produits de saison n’y sont pas pertinents.

![Diagramme de sites multiples](/help/sites-cloud/authoring/assets/multisite-diagram.png)

Pour l’hémisphère nord, une activité d’hiver a été créée, mais le spécialiste marketing en Amérique du Nord souhaiterait une image différente pour l’hiver pour le public masculin et il la modifie donc sur le site des États-Unis.

![Version américaine](/help/sites-cloud/authoring/assets/multisite-us.png)

Après avoir actualisé l’onglet, le site canadien passe à la nouvelle image sans que nous n’ayons aucune action de notre part. Il le fait parce qu&#39;il partage la zone maître avec les États-Unis. L’image ne change pas sur les sites de la Grande-Bretagne et de l’Australie.

![Modification des versions](/help/sites-cloud/authoring/assets/multisite-us-change.png)

Le spécialiste du marketing souhaite déployer ces modifications dans la région européenne et [Déploiement de la Live Copy](/help/sites-cloud/administering/msm/creating-live-copies.md) en appuyant ou en cliquant **Déployer la page**. Après actualisation de l’onglet, le site de la Grande-Bretagne dispose de la nouvelle image, car la région Europe hérite de la zone maître (après déploiement).

![Déploiement de la Live Copy](/help/sites-cloud/authoring/assets/multisite-roll-out.png)

L’image sur le site de l’Australie n’est pas affectée, ce qui est le comportement souhaité, car c’est l’été en Australie et le spécialiste marketing ne souhaite pas modifier ce contenu. Le site de l’Australie ne change pas car il ne partage pas de zone avec une autre région et il n’est pas non plus une Live Copy d’une autre région. Le spécialiste marketing n’a pas à se soucier que le contenu ciblé du site australien soit remplacé.

En outre, pour la Grande-Bretagne, dont la zone est une Live Copy de la zone maître, vous pouvez voir l’état d’héritage par l’indicateur vert en regard du nom de l’activité. Si une activité est héritée, vous ne pouvez pas la modifier, sauf si vous suspendez ou désolidarisez la Live Copy.

Vous pouvez à tout moment suspendre l’héritage ou l’effacer complètement. Vous pouvez également toujours ajouter des expériences locales qui ne sont disponibles que pour cette expérience sans suspendre l’héritage.

>[!NOTE]
>
>Pour une approche plus technique de cette fonction, voir [Structure de la gestion de sites multiples pour le contenu ciblé](/help/sites-cloud/authoring/personalization/multisite-structure.md).

### Comparaison de la création d’une zone simple et de la création d’une zone comme Live Copy {#creating-a-new-area-versus-creating-a-new-area-as-livecopy}

Dans AEM, vous avez la possibilité de créer une zone ou de créer une zone comme Live Copy. La création d’une zone regroupe les activités et tout ce qui appartient à ces activités, telles que les offres, les expériences, etc. Vous créez une zone lorsque vous souhaitez créer un ensemble complètement distinct de contenu ciblé ou partager un ensemble de contenu ciblé.

Si, toutefois, vous disposez d’un héritage configuré via le MSM entre les deux sites, vous pouvez hériter des activités. Dans ce cas, vous créez une zone comme Live Copy, où Y est une Live Copy de X et hérite donc également de toutes les activités.

>[!NOTE]
>
>Le déploiement par défaut déclenche des déploiements ultérieurs du contenu ciblé à chaque fois qu’une page est une Live Copy liée à une zone qui est également une Live Copy de la zone liée au plan directeur des pages.

Par exemple, dans le schéma suivant, deux des quatre sites partagent la zone maître (et toutes les activités qui font partie de cette zone), un site possède une zone qui est une Live Copy d’une zone de telle sorte qu’il partage les activités à mesure de leur déploiement et un autre site complètement distinct (qui nécessite par conséquent une zone pour ses activités).

![Détails du diagramme](/help/sites-cloud/authoring/assets/multisite-diagram-detail.png)

Pour ce faire en AEM, procédez comme suit :

* Le site A est lié à la zone de Principal ; aucune création de zone n’est nécessaire. L’option Zone de Principal est sélectionnée par défaut dans AEM. Les sites A et B partagent des activités, etc.
* Le site B est lié à la zone de Principal ; aucune création de zone n’est nécessaire. L’option Zone de Principal est sélectionnée par défaut dans AEM. Les sites A et B partagent des activités, etc.
* Le site C est lié à la zone héritée, qui est une Live Copy de la zone maître. Créez une zone comme Live Copy (avec une Live Copy reposant sur la zone maître). La zone héritée hérite des activités de la zone de Principal lors du déploiement.
* Le site D est lié à sa propre zone isolée : créez une zone dans laquelle vous créez une zone entièrement nouvelle sans aucune activité encore définie. La zone isolée ne partage aucune activité avec un autre site.

## Création de zones {#creating-new-areas}

Les zones peuvent couvrir des activités et des offres. Après avoir créé une zone dans l’une d’elles (par exemple, les activités), vous disposez également de la zone disponible dans l’autre (par exemple, les offres).

>[!NOTE]
>
>La zone par défaut appelée Zone principale est réduite par défaut lorsque vous appuyez ou cliquez sur le nom d’une marque **jusqu’à ce que** vous en créiez une autre. Ensuite, lorsque vous sélectionnez une marque dans la console **Activité** ou **Offres**, la console **Zone** s’affiche.

Pour créer une zone :

1. Accédez à **Personnalisation** > **Activités** ou **Offres** et sélectionnez ensuite votre marque.
1. Appuyez ou cliquez sur **Créer une zone**.

   ![Créer une zone](/help/sites-cloud/authoring/assets/multisite-create-area.png)

1. Cliquez sur le bouton **Zone** et cliquez sur **Suivant**.
1. Dans le **Titre** , saisissez le nom de la nouvelle zone. Vous pouvez également sélectionner des balises.
1. Appuyez ou cliquez sur **Créer**.

   AEM redirige vers la fenêtre de la marque, où elle répertorie toutes les zones créées. S’il existe une autre zone en plus de la zone de Principal, vous pouvez créer des zones directement dans la console Marque.

   ![Créer](/help/sites-cloud/authoring/assets/multisite-create.png)

## Création de zones comme Live Copies {#creating-areas-as-live-copies}

Vous créez une zone en tant que Live Copy pour hériter du contenu ciblé sur l’ensemble des structures du site.

Pour créer une zone comme Live Copy :

1. Accédez à **Personnalisation** > **Activités** ou **Offres** et sélectionnez ensuite votre marque.
1. Appuyez ou cliquez sur **Créer une zone comme Live Copy**.

   ![Créer une zone comme Live Copy](/help/sites-cloud/authoring/assets/multisite-area-as-livecopy.png)

1. Sélectionnez la zone dont vous souhaitez créer une Live Copy et cliquez sur **Suivant**.

   ![Créer une Live Copy](/help/sites-cloud/authoring/assets/multisite-livecopy.png)

1. Dans le champ **Nom**, saisissez le nom de la Live Copy. Par défaut, les sous-pages sont incluses, mais vous pouvez les exclure en sélectionnant la case **Exclure les sous-pages**.

   ![Créer une Live Copy](/help/sites-cloud/authoring/assets/multisite-create-livecopy.png)

1. Dans le menu déroulant **Configurations du déploiement**, sélectionnez la configuration appropriée.

   Voir [Configurations de déploiement installées](/help/sites-cloud/administering/msm/live-copy-sync-config.md#installed-and-custom-rollout-configurations) pour obtenir des descriptions de chaque option.

   Voir [Création et synchronisation des Live Copies](/help/sites-cloud/administering/msm/creating-live-copies.md) pour plus d’informations sur les Live Copies.

   >[!NOTE]
   >
   >Lorsqu’une page est déployée sur une Live Copy et que la zone configurée pour la page Plan directeur est également le plan directeur de la zone configurée pour les pages Live Copy, la LiveAction **personalizationContentRollout** déclenche un subRollout synchrone, qui fait partie de la **configuration standard de déploiement**.

1. Appuyez ou cliquez sur **Créer**.

   AEM redirige vers la fenêtre de la marque, où elle répertorie toutes les zones créées. S’il existe une autre zone en plus de la zone de Principal, vous pouvez créer des zones directement à partir de la fenêtre de la marque.

   ![Créer une zone](/help/sites-cloud/authoring/assets/multisite-create-2.png)

## Liaison de sites à une zone {#linking-sites-to-an-area}

Vous pouvez lier des zones à des pages ou à un site. Les zones sont héritées par toutes les sous-pages à moins que ces pages ne soient recouvertes par un mappage sur une sous-page. Toutefois, les liens sont généralement établis au niveau du site.

Lorsque vous liez, seules les activités, expériences et offres de la zone sélectionnée sont disponibles. Cela évite la confusion accidentelle du contenu géré de manière indépendante. Si aucune autre zone n’est configurée, la zone maître de chaque marque est utilisée.

>[!NOTE]
>
>Les pages ou les sites faisant référence à la même zone utilisent le *même* ensemble partagé d’activités, d’expériences et d’offres. La modification d’une activité, d’une expérience ou d’une offre commune à plusieurs sites affecte tous les sites.

Pour lier un site à une zone :

1. Accédez au site (ou à la page) que vous souhaitez lier à une zone.
1. Sélectionnez le site ou la page, puis appuyez ou cliquez sur **Afficher les propriétés**.
1. Appuyez ou cliquez sur l’onglet **Personnalisation**.
1. Dans le **Marque** sélectionnez la marque à laquelle vous souhaitez lier votre zone. Une fois la marque sélectionnée, les zones disponibles sont disponibles dans la **Référence de zone** .

   ![Liaison de sites](/help/sites-cloud/authoring/assets/multisite-english.png)

1. Sélectionnez la zone dans le menu déroulant **Référence de zone** et appuyez ou cliquez sur **Enregistrer**.

   ![Référence de zone](/help/sites-cloud/authoring/assets/multisite-area-reference.png)

## Désolidarisation d’une Live Copy ou suspension de l’héritage du contenu ciblé {#detaching-live-copy-or-suspending-inheritance-of-targeted-content}

Vous pouvez suspendre ou désolidariser l’héritage du contenu ciblé. La suspension ou la désolidarisation de la Live Copy est effectuée par activité. Par exemple, vous pouvez modifier des expériences dans votre activité, mais si cette activité est toujours liée à la copie héritée, vous ne pouvez pas modifier l’expérience ni les propriétés de l’activité.

La suspension de la Live Copy rompt temporairement l’héritage, mais vous pouvez ensuite le restaurer. La désolidarisation de la Live Copy rompt définitivement l’héritage.

Vous suspendez ou désolidarisez l’héritage du contenu ciblé en le restaurant dans une activité. Si une page ou un site est lié à une zone qui est une Live Copy, vous pouvez visualiser l’état d’héritage d’une activité.

Une activité qui hérite d’un autre site comporte une marque verte en regard de son nom. Un héritage suspendu est marqué en rouge et une activité créée localement ne comporte aucune icône.

>[!NOTE]
>
>* Vous pouvez uniquement suspendre ou désolidariser des Live Copies dans une activité.
>* Vous n’avez pas besoin de suspendre ou de désolidariser des Live Copies pour étendre une activité héritée. Vous pouvez toujours créer **new** expériences et offres locales pour cette activité. Si vous souhaitez modifier une activité existante, vous devez suspendre l’héritage.
>

### Suspension de l’héritage {#suspending-inheritance}

Pour suspendre ou désolidariser l’héritage du contenu ciblé dans une activité :

1. Accédez à la page sur laquelle vous souhaitez désolidariser ou suspendre l’héritage, puis appuyez ou cliquez sur **Ciblage** dans le menu déroulant du mode.
1. Si votre page est liée à une zone qui est une Live Copy, vous pouvez voir l’état d’héritage. Appuyez ou cliquez sur **Commencer le ciblage**.
1. Pour suspendre une activité, effectuez l’une des opérations suivantes :

   1. Sélectionnez un élément de l’activité, tel que l’audience. AEM affiche automatiquement une boîte de confirmation Suspendre la Live Copy . (Vous pouvez suspendre la Live Copy en appuyant ou en cliquant sur un élément tout au long du processus de ciblage.)
   1. Sélectionner **Suspension de la Live Copy** dans le menu déroulant de la barre d’outils.

   ![Suspendre la Live Copy](/help/sites-cloud/authoring/assets/multisite-suspend-livecopy.png)

1. Appuyez ou cliquez sur **Suspendre** pour suspendre l’activité. Les activités suspendues apparaissent en rouge.

   ![Live Copy suspendue](/help/sites-cloud/authoring/assets/multisite-suspended.png)

### Rupture de l’héritage {#breaking-inheritance}

Pour rompre l’héritage du contenu ciblé dans une activité :

1. Accédez à la page sur laquelle vous souhaitez désolidariser la Live Copy du gabarit, puis appuyez ou cliquez sur **Ciblage** dans le menu déroulant du mode.
1. Si votre page est liée à une zone qui est une Live Copy, vous pouvez voir l’état d’héritage. Appuyez ou cliquez sur **Commencer le ciblage**.
1. Sélectionnez **Désolidariser une Live Copy** dans le menu déroulant de la barre d’outils. AEM confirme que vous souhaitez détacher la Live Copy.
1. Appuyez ou cliquez sur **Désolidariser** pour désolidariser la Live Copy de l’activité. Une fois la désolidarisation effectuée, le menu déroulant relatif à l’héritage disparaît. L’activité est désormais une activité locale.

   ![Activité locale](/help/sites-cloud/authoring/assets/multisite-winter.png)

## Restauration de l’héritage du contenu ciblé {#restoring-inheritance-of-targeted-content}

Si vous avez suspendu l’héritage du contenu ciblé dans une activité, vous pouvez le restaurer à tout moment. Cependant, si vous avez désolidarisé la Live Copy, vous ne pouvez pas restaurer l’héritage.

Pour restaurer l’héritage du contenu ciblé dans une activité :

1. Accédez à la page sur laquelle vous souhaitez restaurer l’héritage et appuyez ou cliquez sur **Ciblage** dans le menu déroulant de mode.
1. Appuyez ou cliquez sur **Commencer le ciblage**.
1. Sélectionnez **Reprendre la Live Copy** dans le menu déroulant de la barre d’outils.

   ![Reprise de la Live Copy](/help/sites-cloud/authoring/assets/multisite-resume.png)

1. Appuyez ou cliquez sur **Reprendre** pour confirmer que vous souhaitez reprendre l’héritage de la Live Copy. Toutes les modifications apportées à l’activité actuelle sont perdues si vous reprenez l’héritage.

## Suppression de zones {#deleting-areas}

Lorsque vous supprimez une zone, vous supprimez toutes les activités qu’elle contient. AEM vous avertit avant de pouvoir supprimer une zone. Si vous supprimez une zone à laquelle un site est lié, le mappage de cette marque sera automatiquement redéfini sur la zone maître.

Pour supprimer une zone :

1. Accédez à **Personnalisation** > **Activités** ou **Offres** et sélectionnez ensuite votre marque.
1. Appuyez ou cliquez sur l’icône en regard de la zone à supprimer.
1. Appuyez ou cliquez sur **Supprimer** et confirmez que vous souhaitez supprimer la zone.
