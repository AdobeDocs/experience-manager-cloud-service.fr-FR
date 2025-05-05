---
title: Variables d’environnement dans Cloud Manager
description: Les variables d’environnement standard peuvent être configurées et gérées via Cloud Manager et fournies à l’environnement d’exécution, pour une utilisation dans les configurations OSGi.
exl-id: 5cdd5532-11fe-47a3-beb2-21967b0e43c6
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 2573eb5f8a8ff21a8e30b94287b554885cd1cd89
workflow-type: tm+mt
source-wordcount: '1185'
ht-degree: 29%

---


# Variables d’environnement dans Cloud Manager {#environment-variables}

Les variables d’environnement standard peuvent être configurées et gérées via Cloud Manager. Ils sont fournis à l’environnement d’exécution et peuvent être utilisés dans des configurations OSGi.

Les variables d’environnement peuvent être des valeurs spécifiques à un environnement ou des secrets d’environnement, en fonction de ce qui est modifié.

## À propos des variables d’environnement {#overview}

Les variables d’environnement offrent de nombreux avantages aux utilisateurs d’AEM as a Cloud Service, tels que :

* Elles permettent au comportement de votre code et de votre application de varier en fonction du contexte et de l’environnement. Par exemple, elles peuvent être utilisées pour activer différentes configurations dans l’environnement de développement par rapport aux environnements de production ou d’évaluation afin d’éviter des erreurs coûteuses.
* Elles ne doivent être configurées et paramétrées qu’une seule fois, et peuvent être mises à jour et supprimées si nécessaire.
* Leurs valeurs peuvent être mises à jour à tout moment et prennent effet immédiatement sans qu’il faille apporter de modifications au code ni procéder à des déploiements.
* Elles peuvent séparer le code de la configuration et supprimer la nécessité d’inclure des informations sensibles dans le contrôle de version.
* Elles améliorent la sécurité de l’application AEM as a Cloud Service puisqu’elles se trouvent en dehors du code.

Les cas d’utilisation types des variables d’environnement incluent les cas suivants :

* La connexion de votre application AEM avec différents points d’entrée externes.
* L’utilisation d’une référence lors du stockage des mots de passe au lieu de le faire directement dans la base de code.
* Lorsque plusieurs environnements de développement existent dans un programme et que certaines configurations diffèrent d’un environnement à l’autre.

## Ajout d’une variable d’environnement {#add-variables}

Si vous souhaitez ajouter plusieurs variables, Adobe vous recommande d’ajouter la première variable, puis d’utiliser ![Ajouter une icône](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg) **&#x200B;**&#x200B;dans la boîte de dialogue **Configuration de l’environnement** pour ajouter les variables supplémentaires. Cette méthode permet de les ajouter avec une mise à jour de l’environnement.

Pour ajouter, mettre à jour ou supprimer des variables d’environnement, vous devez être membre du rôle [**Deployment Manager**](/help/onboarding/cloud-manager-introduction.md#role-based-premissions).

**Pour ajouter une variable d&#39;environnement :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.
1. Dans la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez celui que vous souhaitez gérer.
1. Dans le menu latéral, cliquez sur **Environnements**.
1. Sur la page **Environments** , sélectionnez une ligne du tableau contenant l’environnement pour lequel vous souhaitez ajouter une variable d’environnement.
1. Sur la page des détails de l’environnement, cliquez sur l’onglet **Configuration** .
1. Cliquez sur ![Ajouter/Mettre à jour - Ajouter une icône de cercle](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **Ajouter/Mettre à jour**.
Si vous ajoutez une variable d’environnement pour la première fois, cliquez sur **Ajouter la configuration** au centre de la page.

   ![Onglet Configuration](assets/configuration-tab.png)

1. Dans la boîte de dialogue **Configuration de l’environnement**, saisissez les détails dans la première ligne du tableau.

   | Champ | Description |
   | --- | --- |
   | Nom | Nom unique de la variable de configuration. Il identifie la variable spécifique utilisée dans l’environnement. Elle doit respecter les conventions d’appellation suivantes :<ul><li>Les variables ne peuvent contenir que des caractères alphanumériques et un trait de soulignement (`_`).</li><li>Il existe une limite de 200 variables par environnement.</li><li>Chaque nom doit comporter 100 caractères ou moins.</li></ul> |
   | Valeur | La valeur contenue dans la variable. |
   | Étape appliquée | Sélectionnez le service auquel s’applique la variable. Sélectionnez **Tous** pour que la variable soit appliquée à tous les services.<ul><li>**Tous**</li><li>**Auteur**</li><li>**Publication**</li><li>**Aperçu**</li></ul> |
   | Type | Sélectionnez si la variable est normale ou secrète. |

   ![Ajouter une variable](assets/add-variable.png)

1. Cliquez sur ![Ajouter une icône](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg)**Ajouter**.

   Ajoutez d’autres variables si nécessaire.

1. Cliquez sur **Enregistrer**.

   Un compteur avec l’état **Mise à jour** s’affiche dans le coin supérieur droit du tableau. Un compteur s’affiche également à gauche de toutes les variables nouvellement ajoutées. Ces états indiquent que l’environnement est mis à jour avec la configuration. Une fois cette opération terminée, la nouvelle variable d’environnement est visible dans le tableau.

![Mettre à jour les variables](assets/updating-variables.png)

## Mise à jour d’une variable d’environnement {#update-variables}

Après avoir créé des variables d’environnement, vous pouvez les mettre à jour à l’aide de l’icône ![Ajouter/Mettre à jour - Ajouter un cercle](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **&#x200B;**&#x200B;pour ouvrir la boîte de dialogue **Configuration de l’environnement**.

Si vous souhaitez mettre à jour plusieurs variables, Adobe vous recommande d’utiliser la boîte de dialogue **Configuration de l’environnement** pour mettre à jour toutes les variables nécessaires à la fois avant de cliquer sur **Enregistrer**. De cette façon, vous pouvez les ajouter en une seule mise à jour de lʼenvironnement.

**Pour mettre à jour une variable d&#39;environnement :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.
1. Dans la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez celui que vous souhaitez gérer.
1. Dans le menu latéral, cliquez sur **Environnements**.
1. Sur la page **Environments** , sélectionnez une ligne du tableau contenant l’environnement pour lequel vous souhaitez mettre à jour une variable.
1. Sur la page des détails de l’environnement, cliquez sur l’onglet **Configuration** .
1. Cliquez sur ![Ajouter/Mettre à jour - Ajouter une icône de cercle](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **Ajouter/Mettre à jour**.
1. Dans la boîte de dialogue **Configuration de l’environnement**, cliquez sur ![Icône Ellipse - Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) dans la dernière colonne de la ligne de la variable que vous souhaitez modifier.
1. Dans le menu déroulant, cliquez sur **Modifier**.

   ![Modifier ou supprimer une variable](assets/edit-delete-variable.png)

1. Mettez à jour la valeur de la variable d’environnement si nécessaire.
Lors de la modification d’un secret, la valeur ne peut être mise à jour que et non affichée.

   ![Modifier la variable](assets/edit-variable.png)

1. Utilisez l’une des méthodes suivantes :

   * Cliquez sur ![Appliquer - Icône de coche](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg) pour appliquer la modification.
   * Cliquez sur ![Icône Annuler](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Undo_18_N.svg) pour annuler la modification.

1. Cliquez sur **Enregistrer**.

   Un compteur avec l’état **Mise à jour** s’affiche dans le coin supérieur droit du tableau. Un compteur s’affiche également à gauche de toutes les variables mises à jour. Ces états indiquent que l’environnement est mis à jour avec la configuration. Une fois l’opération terminée, la variable d’environnement mise à jour est visible dans le tableau.

## Suppression d’une variable d’environnement {#delete-env-variable}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.
1. Dans la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez celui que vous souhaitez gérer.
1. Dans le menu latéral, cliquez sur **Environnements**.
1. Sur la page **Environments** , sélectionnez une ligne du tableau contenant l’environnement pour lequel vous souhaitez mettre à jour une variable.
1. Sur la page des détails de l’environnement, cliquez sur l’onglet **Configuration** .
1. Cliquez sur ![Ajouter/Mettre à jour - Ajouter une icône de cercle](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **Ajouter/Mettre à jour**.
1. Dans la boîte de dialogue **Configuration de l’environnement**, cliquez sur ![Icône Ellipse - Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) dans la dernière colonne de la ligne de la variable que vous souhaitez modifier.
1. Dans le menu déroulant, cliquez sur **Supprimer** pour supprimer immédiatement la variable.
1. Cliquez sur **Enregistrer**.

## Utilisation de variables d’environnement {#using}

Les variables d’environnement peuvent rendre vos configurations `pom.xml` plus sécurisées et flexibles. Par exemple, les mots de passe n’ont pas besoin d’être codés en dur et votre configuration peut s’adapter en fonction des valeurs des variables d’environnement.

Vous pouvez accéder aux variables et secrets d&#39;environnement au moyen du code XML comme suit :

`${env.VARIABLE_NAME}`

Voir [Configuration d’un projet](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#password-protected-maven-repository-support-password-protected-maven-repositories) pour obtenir un exemple d’utilisation des deux types de variables dans un fichier `pom.xml`.

Pour plus d’informations, consultez également la [documentation officielle de Maven](https://maven.apache.org/settings.html#quick-overview) .

## Disponibilité des variables d’environnement {#availability}

Les variables d&#39;environnement peuvent être utilisées à plusieurs endroits comme suit :

| Où les variables d’environnement peuvent être utilisées | Description |
| --- | --- |
| Créer, prévisualiser et publier | Les variables d’environnement standard et les secrets peuvent être utilisés dans les environnements de création, de prévisualisation et de publication. |
| Dispatcher | Seules les variables d&#39;environnement standard peuvent être utilisées avec [le Dispatcher](https://experienceleague.adobe.com/fr/docs/experience-manager-dispatcher/using/dispatcher).<ul><li>Les secrets ne peuvent pas être utilisés.</li><li>Les variables d&#39;environnement ne peuvent pas être utilisées dans les directives `IfDefine`.</li><li>Vous devez valider l’utilisation des variables d’environnement avec le [Dispatcher localement](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools) avant le déploiement.</li></ul> |
| Configurations OSGi | Les variables d’environnement standard et les secrets peuvent être utilisés dans les [configurations OSGi](/help/implementing/deploying/configuring-osgi.md). |
| Variables de pipeline | Outre les variables d’environnement, il existe également des variables de pipeline, qui sont exposées pendant la phase de création. En savoir plus sur les variables de pipeline dans [l’environnement de génération](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#pipeline-variables). |

