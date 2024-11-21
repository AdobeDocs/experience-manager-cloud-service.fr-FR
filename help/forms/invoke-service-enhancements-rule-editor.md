---
title: Quelles sont les améliorations apportées au service Invoke VRE pour les formulaires basés sur les composants principaux ?
description: Améliorations du service Invoke pour l’éditeur de règles
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
keywords: Améliorations du service d’appel dans VRE, remplissage des options de liste déroulante à l’aide du service d’appel, définition du panneau répétable à l’aide de la sortie du service d’appel, définition du panneau à l’aide de la sortie du service d’appel, utilisation du paramètre de sortie du service d’appel pour valider un autre champ.
source-git-commit: f77e0cd03a63200cb86fada780f2fecff5fadf94
workflow-type: tm+mt
source-wordcount: '1582'
ht-degree: 1%

---


# Utilisation du service Invoke dans l’éditeur de règles visuel pour les formulaires basés sur les composants principaux

<span class="preview"> Il s’agit d’une fonctionnalité de préversion accessible par le biais de notre [canal de pré-version](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/release-notes/prerelease#new-features). </span>

L’éditeur de règles visuelles d’un formulaire adaptatif prend en charge la fonction **Invoke Service**, qui vous permet de sélectionner un service dans la liste de modèles de données de formulaire (FDM) configurés pour votre instance. Vous pouvez associer directement les champs de formulaire aux paramètres d’entrée du service. Pour mapper les champs de formulaire aux paramètres de sortie, utilisez l’option de payload d’événement pour le service de modèle de données de formulaire spécifié. En outre, l’éditeur de règles visuel vous permet de créer des règles pour les gestionnaires de succès et d’échec pour les opérations **Invoke Service** en fonction de ses réponses de sortie. Les gestionnaires de succès gèrent l’exécution réussie de l’opération **Invoke Service**, tandis que les gestionnaires d’échec corrigent les erreurs qui se produisent.

### Avantages de l’utilisation du service Invoke dans l’éditeur de règles de formulaire

Voici quelques avantages de l’utilisation de l’opération Invoke Service dans l’éditeur de règles d’un formulaire adaptatif :

* **Intégration rationalisée** : l’éditeur de règles visuel simplifie le processus d’intégration de services ou d’API externes dans votre Forms adaptatif. En utilisant le **service d’appel**, vous pouvez facilement connecter des formulaires à diverses sources de données et services sans avoir besoin de codage complexe, ce qui rend l’intégration des formulaires plus efficace.

* **Gestion dynamique des réponses** : vous pouvez gérer les réponses de succès et d’erreur en fonction des réponses de sortie du ****, ce qui permet aux formulaires de réagir dynamiquement à différents scénarios. Cela garantit que les formulaires gèrent les différentes conditions de manière appropriée, ce qui améliore la flexibilité et le contrôle.

* **Interaction utilisateur améliorée** : l’utilisation du **service d’appel** dans l’éditeur de règles active la validation en temps réel dans vos formulaires, offrant ainsi une meilleure expérience utilisateur. Elle garantit également la validation précise des données côté serveur, ce qui réduit les erreurs et améliore la fiabilité des formulaires.

## Appeler les gestionnaires de service pour les réponses de succès et d’échec

>[!NOTE]
>
> Vous pouvez utiliser les gestionnaires de succès et d’échec **Invoke Service** uniquement pour les formulaires basés sur des composants principaux. Forms basé sur les composants de base ne prend pas en charge les gestionnaires de succès et d’échec **Invoke Service**.

L’éditeur de règles visuel vous permet de créer des règles pour les gestionnaires de succès et d’échec pour les opérations **Invoke Service** en fonction de ses réponses en sortie. L’image ci-dessous illustre le **service Invoke** dans l’éditeur de règles visuelles pour un formulaire adaptatif :

![Appeler les gestionnaires de services](/help/forms/assets/invoke-service-rule-editor.png)

Pour ajouter un gestionnaire de succès ou d’échec, cliquez sur **[!UICONTROL Ajouter un gestionnaire de succès]** ou **[!UICONTROL Ajouter un gestionnaire d’échec]**, respectivement.

Lorsque vous cliquez sur **[!UICONTROL Ajouter un gestionnaire de succès]**, l’éditeur de règles **[!UICONTROL Invoke Service Success Handler]** s’affiche, ce qui vous permet de spécifier des règles ou une logique pour gérer la réponse de sortie **Invoke Service** lorsque l’opération est réussie. Vous pouvez spécifier des règles même sans définir de conditions. Cependant, vous pouvez ajouter des conditions pour le gestionnaire de succès en cliquant sur l’option **[!UICONTROL Ajouter une condition]** .

![Invoke service success hadler](/help/forms/assets/invoke-service-success-handler.png)

Vous pouvez ajouter plusieurs règles pour gérer les réponses réussies pour l’opération **Invoke Service** :

![Plusieurs gestionnaires de succès](/help/forms/assets/invoke-service-multiple-success-handlers.png){width=50%, height=50%}

De même, vous pouvez ajouter des règles pour gérer la réponse de sortie **Invoke Service** lorsque l’opération échoue. L’image ci-dessous affiche l’éditeur de règles **[!UICONTROL Invoke Service Failure Handler]** :

![Invoke service failure hadler](/help/forms/assets/invoke-service-failue-handler.png)

Vous pouvez également ajouter plusieurs règles pour gérer les réponses infructueuses à partir de l’opération **Invoke Service**.

La fonction **Activer la validation des erreurs sur le serveur** permet également aux validations ajoutées par l’auteur lors de la conception d’un formulaire adaptatif à exécuter sur le serveur.

## Conditions préalables à l’utilisation du service Invoke dans l’éditeur de règles

Vous trouverez ci-dessous les conditions préalables à remplir avant d’utiliser **Invoke Service** dans l’éditeur de règles :

* Assurez-vous d’avoir configuré une source de données. Pour obtenir des instructions sur la configuration d’une source de données, [cliquez ici](/help/forms/configure-data-sources.md).
* Créez un modèle de données de formulaire à l’aide de la source de données configurée. Pour plus d’informations sur la création d’un modèle de données de formulaire, [cliquez ici](/help/forms/create-form-data-models.md).
* Assurez-vous que les composants principaux sont activés pour votre environnement. Pour obtenir des instructions détaillées sur l’activation des composants principaux pour votre environnement, [cliquez ici](/help/forms/enable-adaptive-forms-core-components.md).

## Exploration du service Invoke à travers différents cas d’utilisation

Le **service d’appel** de l’éditeur de règles visuel vous permet d’effectuer plusieurs opérations utiles. Vous pouvez l’utiliser pour remplir les options de liste déroulante, définir des panneaux répétables ou simples et valider les champs du formulaire, le tout en fonction de la réponse de sortie du **service d’appel**. Vous améliorez ainsi la flexibilité et l’interactivité de vos formulaires.

Le tableau ci-dessous décrit quelques scénarios dans lesquels le **service Invoke** peut être utilisé :

| **Cas d’utilisation** | **Description** |
|----------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| **Renseigner les options de liste déroulante à l’aide de la sortie d’Invoke Service** | Renseigne dynamiquement les options de liste déroulante en fonction des données récupérées à partir de la sortie Invoke Service. [Cliquez ici](#use-case-1-populate-dropdown-values-using-the-output-of-invoke-service) pour voir la mise en oeuvre. |
| **Définition d’un panneau répétable à l’aide de la sortie du service d’appel** | Configure un panneau répétable à l’aide des données issues de la sortie Invoke Service, ce qui permet d’utiliser des panneaux dynamiques. [Cliquez ici](#use-case-2-set-repeatable-panel-using-output-of-invoke-service) pour voir la mise en oeuvre. |
| **Définir le panneau à l’aide de la sortie du service d’appel** | Définit le contenu ou la visibilité d’un panneau à l’aide de valeurs spécifiques issues de la sortie Invoke Service. [Cliquez ici](#use-case-3-set-panel-using-output-of-invoke-service) pour voir la mise en oeuvre. |
| **Utiliser le paramètre de sortie du service Invoke pour valider d’autres champs** | Utilise des paramètres de sortie spécifiques du service Invoke pour valider les champs de formulaire. [Cliquez ici](#use-case-4-use-output-parameter-of-invoke-service-to-validate-other-fields) pour voir la mise en oeuvre. |

Créez un formulaire `Get Information` qui récupère les valeurs en fonction de l’entrée saisie dans la zone de texte `Pet ID`. La capture d’écran ci-dessous montre le formulaire utilisé dans ces cas pratiques :

![Obtenir le formulaire d’information](/help/forms/assets/get-information-form.png)

**Champs de formulaire**

Ajoutez les champs suivants au formulaire :
* **Entrer l’identifiant de l’animal} : zone de texte**
* **Sélectionner les URL de photo** : liste déroulante
* **Balises** : Panneau
   * Nom : Textbox
   * ID : zone de texte
* **Catégorie** : panneau
   * Nom : Textbox
* **Submit** : bouton Envoyer

>[!NOTE]
>
> Dans le champ **Bind Reference** de la boîte de dialogue **Properties** des champs de formulaire, sélectionnez ![foldersearch_18](assets/folder-search-icon.svg) et accédez à la propriété binaire que vous avez ajoutée dans le modèle de données de formulaire (FDM).

**Configuration des panneaux**

Définissez les panneaux comme répétitifs avec les contraintes suivantes :
* Valeur minimale : 1
* Valeur maximale : 4

Vous pouvez ajuster les valeurs des panneaux répétitifs en fonction de vos besoins.

**Source de données**

Dans cet exemple, l’API [Swagger Petstore](https://petstore.swagger.io/) est utilisée pour configurer une source de données. Le [modèle de données de formulaire](/help/forms/create-form-data-models.md) est configuré pour le service [getPetById](https://petstore.swagger.io/#/pet/getPetById), qui récupère les détails de l’animal de compagnie en fonction de l’identifiant saisi.

Publions le fichier JSON suivant à l’aide du service [addPet](https://petstore.swagger.io/#/pet/addPet) dans l’API [Swagger Petstore](https://petstore.swagger.io/) :

```
{
        "id": 101,
        "category": {
            "id": 1,
            "name": "Labrador"
        },
        "name": "Lisa",
        "photoUrls": [
            "https://example.com/photos/lisa1.jpg",
            "https://example.com/photos/lisa2.jpg"
        ],
        "tags": [
            {
                "id": 1,
                "name": "vaccinated"
            },
            {
                "id": 2,
                "name": "friendly"
            },
            {
                "id": 3,
                "name": "house-trained"
            }
        ],
        "status": "available"
    }
```


Les règles et la logique sont implémentées à l’aide de l’action **Invoke Service** dans l’éditeur de règles sur la zone de texte `Pet ID` pour démontrer les cas d’utilisation mentionnés.

Examinons maintenant en détail la mise en oeuvre de chaque cas d’utilisation.

### Cas d’utilisation 1 : renseigner des valeurs de liste déroulante à l’aide de la sortie d’Invoke Service

Ce cas pratique montre comment renseigner dynamiquement les options de liste déroulante en fonction de la sortie d’un `Invoke Service`.

#### Implémentation

Pour ce faire, créez une règle sur la zone de texte `Pet ID` pour appeler le service `getPetById`. Dans la règle, définissez la propriété `enum` de la liste déroulante `photo-url` sur `photoUrls` dans **[!UICONTROL Ajouter un gestionnaire de succès]**.

![Définir la valeur de liste déroulante](/help/forms/assets/set-dropdownoption.png)

#### Sortie

Entrez `101` dans la zone de texte `Pet ID` pour remplir de manière dynamique les options de liste déroulante en fonction de la valeur saisie.

![Résultat](/help/forms/assets/output1.png)

### Cas d’utilisation 2 : définition d’un panneau répétable à l’aide de la sortie du service Invoke

Ce cas pratique montre comment renseigner dynamiquement des panneaux répétables en fonction de la sortie d’un **service d’appel**.

#### Considérations

* Assurez-vous que le nom du panneau répétable correspond au paramètre du **service d’appel** pour lequel vous souhaitez définir le panneau.
* Le panneau se répète pour le nombre de valeurs renvoyé par le champ **Invoke Service** correspondant.

#### Implémentation

Créez une règle sur la zone de texte `Pet ID` pour appeler le service `getPetById`. Dans **[!UICONTROL Ajouter un gestionnaire de succès]**, ajoutez une autre réponse de gestionnaire de succès. Définissez la valeur du panneau `tags` sur `tags` dans la règle.

![Créer une règle pour le panneau répétable](/help/forms/assets/create-rule-repeatable-panel.png)

#### Sortie

Entrez `101` dans la zone de texte `Pet ID` pour remplir dynamiquement le panneau répétable en fonction de la valeur d’entrée.

![Output](/help/forms/assets/output2.png)

### Cas d’utilisation 3 : définition d’un panneau à l’aide de la sortie d’Invoke Service

Ce cas pratique montre comment définir dynamiquement la valeur d’un panneau en fonction de la sortie d’un **Invoke Service**.

#### Considérations

* Assurez-vous que le nom du panneau correspond au paramètre du **service d’appel** pour lequel vous souhaitez définir le panneau.
* Le panneau se répète pour le nombre de valeurs renvoyé par le champ Invoke Service correspondant.

#### Implémentation

Créez une règle sur la zone de texte `Pet ID` pour appeler le service `getPetById`. Dans **[!UICONTROL Ajouter un gestionnaire de succès]**, ajoutez une autre réponse de gestionnaire de succès. Définissez la valeur de la zone de texte `categoryname` sur `category.name` dans la règle.

![Créer une règle pour le panneau répétable](/help/forms/assets/set-panel-values.png)

#### Sortie

Entrez `101` dans la zone de texte `Pet ID` pour remplir le panneau de manière dynamique en fonction de la valeur d’entrée.

![Output](/help/forms/assets/output3.png)

### Cas d’utilisation 4 : utilisation du paramètre de sortie du service Invoke pour valider d’autres champs

Ce cas pratique montre comment utiliser la sortie d’un **service d’appel** pour valider dynamiquement d’autres champs de formulaire.

#### Implémentation

Créez une règle sur la zone de texte `Pet ID` pour appeler le service `getPetById`. Dans **[!UICONTROL Ajouter un gestionnaire d’échec]**, ajoutez une réponse de gestionnaire d’échec. Masquez le bouton **Submit** si un `Pet ID` incorrect est saisi.

![Gestionnaire d’échec](/help/forms/assets/create-rule-failure-handler.png)

#### Sortie

Saisissez `102` dans la zone de texte `Pet ID` et le bouton **Submit** est masqué.

![Output](/help/forms/assets/output4.png)

## Questions fréquentes

**Q : Que se passe-t-il si j’ai créé une règle à l’aide du service Invoke et que j’ai ensuite effectué la mise à niveau vers la dernière version des composants principaux ?**

**A :** Lorsque vous effectuez une mise à niveau vers la dernière version des composants principaux, la règle **Invoke Service** est automatiquement mise à jour vers la dernière interface utilisateur, car elle est rétrocompatible.

**Q : Puis-je ajouter plusieurs règles pour gérer les réponses de succès ou d’échec pour l’opération Invoke Service ?**

**A :** Oui, vous pouvez ajouter plusieurs règles pour gérer les réponses de succès ou d’échec pour l’opération **Invoke Service**.

## Articles connexes

* [Configurer des sources de données](configure-data-sources.md)
* [Créer un modèle de données de formulaire (FDM)](create-form-data-models.md)
* [Utilisation du modèle de données de formulaire (FDM)](work-with-form-data-model.md)
* [Utilisation du modèle de données de formulaire (FDM)](using-form-data-model.md)


## Ressources supplémentaires

{{see-also-rule-editor}}

