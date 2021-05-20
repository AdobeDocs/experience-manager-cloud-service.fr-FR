---
title: Préparation du contenu à traduire
description: Découvrez comment préparer le contenu à traduire.
feature: Copie de la langue
role: Administrator
exl-id: afc577a2-2791-481a-ac77-468011e4302e
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 46%

---

# Préparation du contenu à traduire {#preparing-content-for-translation}

Les sites web multilingues fournissent généralement une certaine quantité de contenu dans plusieurs langues. Le site est créé dans une langue, puis traduit dans d’autres langues. En général, les sites multilingues comportent des branches de pages, chaque branche contenant les pages du site dans une langue distincte.

Le [site de tutoriel WKND](/help/implementing/developing/introduction/develop-wknd-tutorial.md) comprend plusieurs branches de langue et utilise la structure suivante :

```text
/content
    |- wknd
        |- language-masters
            |- en
            |- de
            |- es
            |- fr
            |- it
        |- us
            |- en
            |- es
        |- ca
            |- en
            |- fr
        |- ch
            |- de
            |- fr
            |- it
        |- de
            |- de
        |- fr
            |- fr
        |- es
            |- es
        |- it
            |- it
```

La copie de langue pour laquelle vous créez initialement le contenu du site est le gabarit de langue. Le gabarit de langue est la source qui est traduite dans d’autres langues.

Chaque branche de langue d’un site est appelée « copie de langue ». La page racine d’une copie de langue, appelée « racine de langue », identifie la langue du contenu de la copie de langue. Par exemple, `/content/wknd/fr` est la racine de langue de la copie en français. Les copies de langue doivent utiliser une [racine de langue configurée correctement](preparation.md#creating-a-language-root) afin que la langue appropriée soit ciblée lorsque des sources sont traduites.

Pour préparer la traduction du site, procédez comme suit :

1. Créez la racine de langue de votre gabarit de langue. Par exemple, la racine de langue du site de démonstration WKND en anglais est `/content/wknd/language-masters/en`. Assurez-vous que la racine de langue est correctement configurée conformément aux informations de la section [Création d’une racine de langue](preparation.md#creating-a-language-root).
1. Créez le contenu de votre gabarit de langue.
1. Créez la racine de langue de chaque copie de langue pour votre site. Par exemple, la copie en français de l’exemple de site WKND est `/content/wknd/language-masters/fr`.

Après avoir préparé le contenu à traduire, vous pouvez créer automatiquement les pages manquantes dans les copies de langue et les projets de traduction associés. (Voir [Création d’un projet de traduction](managing-projects.md).) Pour une présentation du processus de traduction de contenu dans AEM, voir [Traduction de contenu pour les sites web multilingues](overview.md).

## Création d’une racine de langue {#creating-a-language-root}

Créez une racine de langue comme page racine d’une copie de langue qui identifie la langue du contenu. Après avoir créé la racine de langue, vous pouvez créer des projets de traduction incluant la copie de langue.

Pour créer la racine de langue, vous créez une page et utilisez un code de langue ISO comme valeur de la propriété **Name**. Le code de la langue doit être dans l’un des formats suivants :

* `<language-code>` - Le code de langue pris en charge est un code à deux lettres tel que défini par la norme ISO-639-1, par exemple  `en`.
* `<language-code>_<country-code>` ou  `<language-code>-<country-code>`  - Le code de pays pris en charge est un code à deux lettres en minuscules ou en majuscules, tel que défini par la norme ISO 3166, par exemple  `en_US`,  `en_us`,  `en_GB`,  `en-gb`.

Vous pouvez utiliser l’un de ces formats en fonction de la structure choisie pour votre site international.  Par exemple, la page racine de la copie en français du site WKND présente `fr` comme propriété **Name**. Notez que la propriété **Name** est utilisée comme nom du noeud de page dans le référentiel et détermine donc le chemin d’accès de la page (`http://<host>:<4502>/content/wknd/language-masters/fr.html`).

1. Accédez aux sites.
1. Cliquez ou appuyez sur le site pour lequel vous souhaitez créer une copie de langue.
1. Cliquez ou appuyez sur **Créer**, puis sur **Page**.

   ![Créer une page](../assets/create-page.png)

1. Sélectionnez le modèle de page, puis cliquez ou appuyez sur **Suivant**.
1. Dans le champ **Nom**, saisissez le code de pays au format `<language-code>` ou `<language-code>_<country-code>`, par exemple `en`, `en_US`, `en_us`, `en_GB`, `en_gb`. Saisissez un titre pour la page.

   ![Créer une page racine de langue](../assets/create-language-root.png)

1. Cliquez ou appuyez sur **Créer**. Dans la boîte de dialogue de confirmation, cliquez ou appuyez sur **Terminé** pour revenir à la console Sites ou sur **Ouvrir** pour ouvrir la copie de langue.

## Affichage de l’état des racines de langue {#seeing-the-status-of-language-roots}

AEM fournit un rail **Références** qui affiche la liste des racines de langue qui ont été créées.

![Racines linguistiques](../assets/language-roots.png)

Utilisez la procédure suivante pour afficher les copies de langue d’une page à l’aide du sélecteur de rail [.](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector)

1. Dans la console Sites, sélectionnez une page du site, puis cliquez ou appuyez sur **Références**.

   ![Ouvrir le rail de références](../assets/opening-references-rail.png)

1. Dans le rail de références, cliquez ou appuyez sur **Copies de langue**. Le rail affiche les copies de langue du site web.

## Copies de langue à plusieurs niveaux {#multiple-levels}

Les racines de langue peuvent également être regroupées sous des noeuds, par exemple par région, tout en étant encore reconnues comme racines de copies de langue.

```text
/content
    |- wknd
        |- language-masters
            |- europe
                |- de
                |- fr
                |- it
                |- es
                ]- pt
            |- americas
                |- en
                |- es
                |- fr
                |- pt
            |- asia
                |- ...
            |- africa
                |- ...
            |- oceania
                |- ...
        |- europe
        |- americas
        |- asia
        |- africa
        |- oceania            
```

>[!NOTE]
>
>Un seul niveau est autorisé. Par exemple, les éléments suivants n’autorisent pas la résolution de la page `es` vers une copie de langue :
>
>* `/content/wknd/language-masters/en`
>* `/content/wknd/language-masters/americas/central-america/es`

>
> 
Cette `es` copie de langue ne sera pas détectée, car elle se trouve à 2 niveaux (`americas/central-america`) du noeud `en`.

>[!TIP]
>
>Dans une telle configuration, les racines de langue peuvent avoir n’importe quel nom de page, plutôt que simplement le code ISO de la langue. AEM vérifie toujours d’abord le chemin et le nom, mais si le nom de page n’identifie pas de langue, AEM vérifie la propriété `cq:language` de la page pour l’identification de la langue.
