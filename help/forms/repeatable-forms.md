---
description: Ce tutoriel comprend des instructions pour rendre une section d’un formulaire répétable.
title: Sections répétables dans les Edge Delivery Services
feature: Edge Delivery Services
source-git-commit: fd2e5df72e965ea6f9ad09b37983f815954f915c
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---


# Sections répétables dans la diffusion Edge

Une section répétable est un composant d’un formulaire qui est dupliqué ou répliqué plusieurs fois afin de collecter des informations pour plusieurs occurrences des mêmes données.

Prenons l’exemple d’un formulaire utilisé pour recueillir des informations auprès des utilisateurs demandant un prêt. Le formulaire permet aux utilisateurs de fournir des informations personnelles, y compris des détails sur les co-prêteurs. Les utilisateurs peuvent saisir des détails pour les co-candidats, cette section étant répétable.

![Sections répétables dans les formulaires](/help/forms/assets/eds-repeatable.png)

## Conditions préalables

Configurez le projet GitHub du service de diffusion Edge (EDS) à l’aide AEM standard et clonez le référentiel GitHub correspondant sur votre ordinateur local. Voir [tutoriel pour les développeurs](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/edge-delivery/build/tutorial.html) pour plus d’informations.

## Sections répétables dans la diffusion Edge

Prenons un exemple de formulaire de demande de prêt. Le formulaire permet aux utilisateurs de soumettre des informations personnelles. Vous pouvez inclure les détails du co-demandeur à l’aide de sections répétables, avec la possibilité d’ajouter un minimum et un maximum de trois sections co-demandeur.

>[!NOTE]
>
> * Vous pouvez créer un fichier Excel Microsoft sur votre site SharePoint ou lecteur Google pour que les jeux de champs puissent être répétés dans un formulaire.
> * Dans ce cas, nous prenons l’exemple d’une SharePoint Microsoft. Pour faire de votre dossier SharePoint la source de contenu, procédez comme décrit dans la section [Utilisation de SharePoint](https://www.aem.live/docs/setup-customer-sharepoint).


Pour ajouter des sections répétables dans la diffusion Edge :

1. [Créer un formulaire à l’aide de Microsoft Excel](#author-form)
2. [Aperçu et publication du formulaire](#preview-form)

### Créer un formulaire à l’aide de Microsoft Excel {#author-form}

1. Accédez à votre compte SharePoint Microsoft et ouvrez ou créez AEM répertoire de projet Edge Delivery.
2. Ouvrez un fichier Excel Microsoft existant ou créez-le.
Dans cet exemple, nous utilisons une feuille Excel nommée `loan-application.xlsx` créé dans Microsoft SharePoint Site.
3. Ajoutez de nouvelles colonnes intitulées `Repeatable`, `Min`, et `Max` dans votre fichier Excel Microsoft.
4. Spécifiez la valeur de la variable `Repeatable` column as `True` pour l’ensemble de champs que vous souhaitez rendre répétable.
5. Spécifiez les valeurs de la variable `Min` et `Max` colonnes. La variable `Min` représente le nombre minimum d’occurrences pour lesquelles le panneau se répète, tandis que la variable `Max` représente le nombre maximal d’occurrences pour lesquelles le panneau se répète.
6. Enregistrez votre fichier Excel Microsoft.

>[!NOTE]
>
> Voici la variable [Demande de prêt](/help/forms/assets/loan-application.xlsx) feuille Excel à titre de référence.

### Aperçu/publication du formulaire à l’aide de votre service de diffusion Edge

1. Ouvrez ou créez un fichier document dans un site Microsoft SharePoint afin d’y incorporer la feuille Excel à l’aide d’une `Form Block`. Par exemple, ouvrez le `index` et ajouter un `Form Block`.
2. Ouvrez l’invite de commande, accédez au répertoire de votre projet Edge Delivery AEM sur votre ordinateur local, puis exécutez la commande en tant que `aem up`.

Le formulaire est accessible à l’adresse `https://localhost:3000`, où vous cliquez sur le bouton `Add` ajoute une nouvelle section répétable pour saisir les détails du co-demandeur. Vous pouvez également supprimer la section répétable en cliquant sur le `Delete` bouton .

>[!NOTE]
>
> Si vous rencontrez une erreur &quot;Page introuvable&quot; lors de l’accès à votre formulaire à l’emplacement localhost, ajoutez le nom du répertoire du site SharePoint Microsoft devant l’URL où se trouve votre formulaire. Par exemple, `http://localhost:3000/<dir-name>/`.




