---
title: Quelles sont les améliorations apportées au VRE Invoke Service pour les formulaires basés sur les composants principaux ?
description: Améliorations du service Invoke pour l’éditeur de règles
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
keywords: Améliorations du service d’appel dans VRE, remplissage des options de liste déroulante à l’aide du service d’appel, Définition du panneau répétable à l’aide de la sortie du service d’appel, Définition du panneau à l’aide de la sortie du service d’appel, Utilisation du paramètre de sortie du service d’appel pour valider d’autres champs.
exl-id: 2ff64a01-acd8-42f2-aae3-baa605948cdd
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: tm+mt
source-wordcount: '1566'
ht-degree: 1%

---

# Utilisation du service d’appel dans l’éditeur visuel de règles pour les formulaires basés sur les composants principaux

L’éditeur visuel de règles d’un formulaire adaptatif prend en charge la fonctionnalité **Invoquer le service**, qui vous permet de sélectionner un service dans la liste des modèles de données de formulaire (FDM) configurés pour votre instance. Vous pouvez mapper des champs de formulaire directement aux paramètres d’entrée du service. Pour mapper des champs de formulaire aux paramètres de sortie, utilisez l’option de payload d’événement pour le service de modèle de données de formulaire spécifié. En outre, l’éditeur visuel de règles vous permet de créer des règles pour les gestionnaires de succès et d’échec des opérations **Invoke Service** en fonction de ses réponses de sortie. Les gestionnaires de succès gèrent la réussite de l’exécution de l’opération **Invoke Service**, tandis que les gestionnaires d’échec traitent les erreurs qui se produisent.

## Avantages de l’utilisation du service d’appel dans l’éditeur de règles du formulaire

L’utilisation de l’opération Invoke Service dans l’éditeur de règles d’un formulaire adaptatif présente les avantages suivants :

* **Intégration rationalisée** : l’éditeur de règles visuel simplifie le processus d’intégration de services ou d’API externes à votre Forms adaptative. En utilisant le **service Invoke**, vous pouvez facilement connecter des formulaires à différentes sources de données et services sans avoir à recourir à un codage complexe, ce qui rend l’intégration des formulaires plus efficace.

* **Gestion des réponses dynamiques** : vous pouvez gérer les réponses de succès et d’erreur en fonction des réponses de sortie du **Invoke Service**, ce qui permet aux formulaires de réagir dynamiquement à différents scénarios. Cela permet aux formulaires de gérer diverses conditions de manière appropriée, améliorant ainsi la flexibilité et le contrôle.

* **Amélioration de l’interaction utilisateur** : l’utilisation du **service d’appel** dans l’éditeur de règles permet la validation en temps réel dans vos formulaires, offrant ainsi une meilleure expérience utilisateur. Cela permet également de s’assurer que les données sont validées avec précision côté serveur, ce qui réduit les erreurs et améliore la fiabilité des formulaires.

## Appeler des gestionnaires de services pour les réponses de succès et d’échec

>[!NOTE]
>
> Vous pouvez utiliser les gestionnaires de succès et d’échec **Invoke Service** uniquement pour les formulaires basés sur les composants principaux. Forms basé sur les composants de base ne prend pas en charge les gestionnaires de succès et d’échec **Invoquer le service**.

L’éditeur visuel de règles vous permet de créer des règles pour les gestionnaires de succès et d’échec des opérations **Invoke Service** en fonction de ses réponses de sortie. L’image ci-dessous illustre le **service Invoke** dans l’éditeur visuel de règles pour un formulaire adaptatif :

![Appeler des gestionnaires de services](/help/forms/assets/invoke-service-rule-editor.png)

Pour ajouter un gestionnaire de succès ou d’échec, cliquez respectivement sur **[!UICONTROL Ajouter un gestionnaire de succès]** ou **[!UICONTROL Ajouter un gestionnaire d’échec]**.

Lorsque vous cliquez sur **[!UICONTROL Ajouter un gestionnaire de succès]**, l’éditeur de règles **[!UICONTROL Invoquer le gestionnaire de succès du service]** s’affiche et vous permet de spécifier des règles ou une logique pour gérer la réponse de sortie **Invoquer le service** lorsque l’opération réussit. Vous pouvez spécifier des règles même sans définir de conditions ; toutefois, vous pouvez ajouter des conditions pour le gestionnaire de succès en cliquant sur l’option **[!UICONTROL Ajouter une condition]**.

![Gestionnaire de succès Invoke Service](/help/forms/assets/invoke-service-success-handler.png)

Vous pouvez ajouter plusieurs règles pour gérer les réponses réussies de l’opération **Invoke Service** :

![Gestionnaire de succès multiple](/help/forms/assets/invoke-service-multiple-success-handlers.png){width=50%, height=50%}

De même, vous pouvez ajouter des règles pour gérer la réponse de sortie **Invoke Service** en cas d’échec de l’opération. L’image ci-dessous affiche l’éditeur de règles **[!UICONTROL Invoke Service Failure Handler]** :

![Gestionnaire d’échec du service d’appel](/help/forms/assets/invoke-service-failue-handler.png)

Vous pouvez également ajouter plusieurs règles pour gérer les réponses infructueuses de l’opération **Invoke Service**.

La fonction **Activer la validation d’erreur sur le serveur** permet les validations ajoutées par l’auteur lors de la conception d’un formulaire adaptatif à exécuter également sur le serveur.

## Conditions préalables à l’utilisation du service Invoke dans l’éditeur de règles

Vous trouverez ci-dessous les conditions préalables à remplir avant d’utiliser **Invoke Service** dans l’éditeur de règles :

* Assurez-vous d’avoir configuré une source de données. Pour obtenir des instructions sur la configuration d’une source de données, [cliquez ici](/help/forms/configure-data-sources.md).
* Créez un modèle de données de formulaire en utilisant la source de données configurée. Pour obtenir des conseils sur la création d’un modèle de données de formulaire, [cliquez ici](/help/forms/create-form-data-models.md).
* Assurez-vous que les composants principaux sont activés pour votre environnement. Pour obtenir des instructions détaillées sur la manière d’activer les composants principaux pour votre environnement, [cliquez ici](/help/forms/enable-adaptive-forms-core-components.md).

## Explorer le service Invoke à travers différents cas d’utilisation

Le **service d’appel** de l’éditeur visuel de règles vous permet d’effectuer plusieurs opérations utiles. Vous pouvez l’utiliser pour renseigner les options de liste déroulante, définir des panneaux répétables ou simples et valider les champs de formulaire, le tout en fonction de la réponse de sortie du **Appeler le service**. Cela permet d’améliorer la flexibilité et l’interactivité de vos formulaires.

Le tableau ci-dessous décrit quelques scénarios dans lesquels le **service Invoke** peut être utilisé :

| **Cas d’utilisation** | **Description** |
|----------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| **Renseigner les options de liste déroulante à l’aide de la sortie d’Invoke Service** | Renseigne les options de liste déroulante de manière dynamique en fonction des données extraites de la sortie du service Invoke. [Cliquez ici](#use-case-1-populate-dropdown-values-using-the-output-of-invoke-service) pour afficher l’implémentation. |
| **Définir le panneau répétable à l’aide de la sortie du service d’appel** | Configure un panneau répétable en utilisant les données de la sortie du service d’appel, ce qui permet d’utiliser des panneaux dynamiques. [Cliquez ici](#use-case-2-set-repeatable-panel-using-output-of-invoke-service) pour afficher l’implémentation. |
| **Définir le panneau à l’aide de la sortie du service Invoke** | Définit le contenu ou la visibilité d’un panneau à l’aide de valeurs spécifiques issues de la sortie du service Invoke. [Cliquez ici](#use-case-3-set-panel-using-output-of-invoke-service) pour afficher l’implémentation. |
| **Utilisez le paramètre de sortie du service d’appel pour valider d’autres champs** | Utilise des paramètres de sortie spécifiques du service d’appel pour valider les champs de formulaire. [Cliquez ici](#use-case-4-use-output-parameter-of-invoke-service-to-validate-other-fields) pour afficher l’implémentation. |

Créez un formulaire `Get Information` qui récupère des valeurs en fonction de l’entrée saisie dans la zone de texte `Pet ID`. La capture d’écran ci-dessous montre le formulaire utilisé dans ces cas d’utilisation :

![Formulaire d&#39;obtention d&#39;informations](/help/forms/assets/get-information-form.png)

**Champs de formulaire**

Ajoutez les champs suivants au formulaire :
* **Saisir l&#39;ID d&#39;animal domestique** : Zone de texte
* **Sélectionner des URL de photo** : liste déroulante
* **Balises** : Panneau
   * Nom : Zone de texte
   * ID : zone de texte
* **Catégorie** : Panneau
   * Nom : Zone de texte
* **Envoyer** : bouton Envoyer

>[!NOTE]
>
> Dans le champ **Référence de liaison** de la boîte de dialogue **Propriétés** des champs de formulaire, sélectionnez ![foldersearch_18](assets/folder-search-icon.svg) et accédez à la propriété binaire que vous avez ajoutée dans le modèle de données de formulaire (FDM).

**Configuration des panneaux**

Définissez les panneaux de manière répétitive avec les contraintes suivantes :
* Valeur minimale : 1
* Valeur maximale : 4

Vous pouvez ajuster les valeurs des panneaux répétitifs en fonction de vos besoins.

**Source de données**

Dans cet exemple, l’API [Swagger Petstore](https://petstore.swagger.io/) est utilisée pour configurer une source de données. Le [Modèle de données de formulaire](/help/forms/create-form-data-models.md) est configuré pour le service [getPetById](https://petstore.swagger.io/#/pet/getPetById) qui récupère les détails des animaux de compagnie en fonction de l’identifiant saisi.

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


Les règles et la logique sont mises en œuvre à l’aide de l’action **Invoquer le service** dans l’éditeur de règles de la zone de texte `Pet ID` pour démontrer les cas d’utilisation mentionnés.

Examinons maintenant en détail la mise en œuvre de chaque cas d’utilisation.

### Cas d’utilisation 1 : remplissage des valeurs de liste déroulante à l’aide de la sortie du service d’appel

Ce cas d’utilisation montre comment remplir les options de liste déroulante de manière dynamique en fonction de la sortie d’un `Invoke Service`.

#### Implémentation

Pour ce faire, créez une règle dans la zone de texte `Pet ID` pour appeler le service `getPetById`. Dans la règle, définissez la propriété `enum` de la liste déroulante `photo-url` sur `photoUrls` dans **[!UICONTROL Ajouter un gestionnaire de réussite]**.

![Définir la valeur de la liste déroulante](/help/forms/assets/set-dropdownoption.png)

#### Sortie

Saisissez `101` dans la zone de texte `Pet ID` pour renseigner dynamiquement les options de liste déroulante en fonction de la valeur saisie.

![Résultat](/help/forms/assets/output1.png)

### Cas d’utilisation 2 : définition du panneau répétable à l’aide de la sortie du service d’appel

Ce cas d’utilisation montre comment remplir dynamiquement les panneaux répétables en fonction de la sortie d’un **Invoke Service**.

#### Considérations

* Assurez-vous que le nom du panneau répétable correspond au paramètre du **service d’appel** pour lequel vous souhaitez définir le panneau.
* Le panneau se répète pour le nombre de valeurs renvoyées par le champ **Invoke Service** correspondant.

#### Implémentation

Créez une règle dans la zone de texte `Pet ID` pour appeler le service `getPetById`. Dans **[!UICONTROL Ajouter un gestionnaire de succès]**, ajoutez une autre réponse de gestionnaire de succès. Définissez la valeur du panneau `tags` à `tags` dans la règle.

![Créer une règle pour le panneau répétable](/help/forms/assets/create-rule-repeatable-panel.png)

#### Sortie

Saisissez `101` dans la zone de texte `Pet ID` pour remplir dynamiquement le panneau répétable en fonction de la valeur d’entrée.

![Output](/help/forms/assets/output2.png)

### Cas d’utilisation 3 : définition du panneau à l’aide de la sortie du service d’appel

Ce cas d’utilisation montre comment définir dynamiquement la valeur d’un panneau en fonction de la sortie d’un **Invoke Service**.

#### Considérations

* Assurez-vous que le nom du panneau correspond au paramètre du **service d’appel** pour lequel vous souhaitez définir le panneau.
* Le panneau se répète pour le nombre de valeurs renvoyées par le champ Invoke Service correspondant.

#### Implémentation

Créez une règle dans la zone de texte `Pet ID` pour appeler le service `getPetById`. Dans **[!UICONTROL Ajouter un gestionnaire de succès]**, ajoutez une autre réponse de gestionnaire de succès. Définissez la valeur de la zone de texte `categoryname` à `category.name` dans la règle.

![Créer une règle pour le panneau répétable](/help/forms/assets/set-panel-values.png)

#### Sortie

Saisissez `101` dans la zone de texte `Pet ID` pour remplir le panneau de manière dynamique en fonction de la valeur d’entrée.

![Output](/help/forms/assets/output3.png)

### Cas d’utilisation 4 : utilisation du paramètre de sortie du service d’appel pour valider d’autres champs

Ce cas d’utilisation montre comment utiliser la sortie d’un **Invoke Service** pour valider dynamiquement d’autres champs de formulaire.

#### Implémentation

Créez une règle dans la zone de texte `Pet ID` pour appeler le service `getPetById`. Dans **[!UICONTROL Ajouter un gestionnaire d’échec]**, ajoutez une réponse de gestionnaire d’échec. Masquez le bouton **Envoyer** si un `Pet ID` incorrect est saisi.

![Gestionnaire d’échecs](/help/forms/assets/create-rule-failure-handler.png)

#### Sortie

Saisissez `102` dans la zone de texte `Pet ID` et le bouton **Envoyer** est masqué.

![Output](/help/forms/assets/output4.png)

## Questions fréquentes

**Q : Que se passe-t-il si j’ai créé une règle à l’aide du service d’appel, puis que j’effectue une mise à niveau vers la dernière version des composants principaux ?**

**A :** lorsque vous effectuez une mise à niveau vers la dernière version des composants principaux, la règle **Invoke Service** est automatiquement mise à jour vers la dernière interface utilisateur, car elle est rétrocompatible.

**Q : Puis-je ajouter plusieurs règles pour gérer les réponses réussies ou en échec pour l’opération du service d’appel ?**

**A :** Oui, vous pouvez ajouter plusieurs règles pour gérer les réponses réussies ou en échec pour l’opération **Invoke Service**.

## Articles connexes

* [Configurer des sources de données](configure-data-sources.md)
* [Créer un modèle de données de formulaire (FDM)](create-form-data-models.md)
* [Utilisation d’un modèle de données de formulaire (FDM)](work-with-form-data-model.md)
* [Utilisation du modèle de données de formulaire (FDM)](using-form-data-model.md)


## Ressources supplémentaires

{{see-also-rule-editor}}
