---
title: Variables d’environnement dans Cloud Manager
description: Les variables d’environnement standard peuvent être configurées et gérées via Cloud Manager. Elles sont fournies à l’environnement d’exécution pour une utilisation dans les configurations OSGi.
exl-id: 5cdd5532-11fe-47a3-beb2-21967b0e43c6
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1185'
ht-degree: 29%

---


# Variables d’environnement dans Cloud Manager {#environment-variables}

Les variables d’environnement standard peuvent être configurées et gérées via Cloud Manager. Ils sont fournis à l’environnement d’exécution et peuvent être utilisés dans des configurations OSGi.

Les variables d’environnement peuvent être des valeurs spécifiques à un environnement ou des secrets d’environnement, en fonction de ce qui est modifié.

## À propos des variables d’environnement {#overview}

Les variables d’environnement offrent de nombreux avantages aux utilisateurs d’AEM as a Cloud Service, notamment :

* Elles permettent au comportement de votre code et de votre application de varier en fonction du contexte et de l’environnement. Par exemple, elles peuvent être utilisées pour activer différentes configurations dans l’environnement de développement par rapport aux environnements de production ou d’évaluation, afin d’éviter des erreurs coûteuses.
* Elles ne doivent être configurées et paramétrées qu’une seule fois, et peuvent être mises à jour et supprimées si nécessaire.
* Leurs valeurs peuvent être mises à jour à tout moment et prennent effet immédiatement sans qu’il faille apporter de modifications au code ni procéder à des déploiements.
* Elles peuvent séparer le code de la configuration et supprimer la nécessité d’inclure des informations sensibles dans le contrôle de version.
* Elles améliorent la sécurité de l’application AEM as a Cloud Service puisqu’elles se trouvent en dehors du code.

Les cas d’utilisation standard des variables d’environnement incluent les suivants :

* La connexion de votre application AEM avec différents points d’entrée externes.
* L’utilisation d’une référence lors du stockage des mots de passe au lieu de le faire directement dans la base de code.
* Lorsque plusieurs environnements de développement existent dans un programme et que certaines configurations diffèrent d’un environnement à l’autre.

## Ajouter une variable d’environnement {#add-variables}

Si vous souhaitez ajouter plusieurs variables, Adobe vous recommande d’ajouter la première variable, puis d’utiliser ![icône Ajouter](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg) **Ajouter** dans la boîte de dialogue **Configuration de l’environnement** pour ajouter les variables supplémentaires. Cela signifie que vous pouvez les ajouter avec une seule mise à jour à l’environnement.

Pour ajouter, mettre à jour ou supprimer des variables d’environnement, vous devez être membre du rôle [**Responsable de déploiement**](/help/onboarding/cloud-manager-introduction.md#role-based-premissions).

**Pour ajouter une variable d’environnement, procédez comme suit**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.
1. Dans la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez celui que vous souhaitez gérer.
1. Dans le menu latéral, cliquez sur **Environnements**.
1. Sur la page **Environnements**, sélectionnez une ligne du tableau contenant l’environnement pour lequel vous souhaitez ajouter une variable d’environnement.
1. Sur la page de détails de l’environnement, cliquez sur l’onglet **Configuration**.
1. Cliquez sur ![Ajouter/Mettre à jour - Icône Ajouter un cercle](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **Ajouter/Mettre à jour**.
Si vous ajoutez une variable d’environnement pour la première fois, cliquez sur **Ajouter une configuration** au centre de la page.

   ![Onglet Configuration](assets/configuration-tab.png)

1. Dans la boîte de dialogue **Configuration de l’environnement**, saisissez les détails dans la première ligne du tableau.

   | Champ | Description |
   | --- | --- |
   | Nom | Nom unique de la variable de configuration. Il identifie la variable spécifique utilisée dans l’environnement. Il doit respecter les conventions de dénomination suivantes :<ul><li>Les variables ne peuvent contenir que des caractères alphanumériques et le trait de soulignement (`_`).</li><li>Il existe une limite de 200 variables par environnement.</li><li>Chaque nom doit comporter 100 caractères ou moins.</li></ul> |
   | Valeur | Valeur de la variable. |
   | Étape appliquée | Sélectionnez le service auquel la variable s’applique. Sélectionnez **Tous** pour appliquer la variable à tous les services.<ul><li>**Tous**</li><li>**Auteur**</li><li>**Publication**</li><li>**Prévisualisation**</li></ul> |
   | Type | Sélectionnez cette option si la variable est normale ou secrète. |

   ![Ajouter une variable](assets/add-variable.png)

1. Cliquez sur ![&#x200B; Ajouter une icône &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg)**Ajouter**.

   Ajoutez des variables supplémentaires si nécessaire.

1. Cliquez sur **Enregistrer**.

   Une double flèche avec le statut **Mise à jour en cours** s’affiche dans le coin supérieur droit du tableau. Une double flèche s’affiche également à gauche de toutes les variables nouvellement ajoutées. Ces statuts indiquent que l’environnement est en cours de mise à jour avec la configuration. Une fois cette opération terminée, la nouvelle variable d’environnement est visible dans le tableau.

![Mettre à jour les variables](assets/updating-variables.png)

## Mise à jour d’une variable d’environnement {#update-variables}

Après avoir créé des variables d’environnement, vous pouvez les mettre à jour à l’aide de l’icône ![Ajouter/mettre à jour - Ajouter un cercle](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **Ajouter/mettre à jour** pour ouvrir la boîte de dialogue **Configuration de l’environnement**.

Si vous souhaitez mettre à jour plusieurs variables, Adobe vous recommande d’utiliser la boîte de dialogue **Configuration de l’environnement** pour mettre à jour toutes les variables nécessaires en une seule fois avant de cliquer sur **Enregistrer**. De cette façon, vous pouvez les ajouter en une seule mise à jour de lʼenvironnement.

**Pour mettre à jour une variable d’environnement, procédez comme suit**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.
1. Dans la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez celui que vous souhaitez gérer.
1. Dans le menu latéral, cliquez sur **Environnements**.
1. Sur la page **Environnements**, sélectionnez une ligne du tableau contenant l’environnement pour lequel vous souhaitez mettre à jour une variable.
1. Sur la page de détails de l’environnement, cliquez sur l’onglet **Configuration**.
1. Cliquez sur ![Ajouter/Mettre à jour - Icône Ajouter un cercle](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **Ajouter/Mettre à jour**.
1. Dans la boîte de dialogue **Configuration de l’environnement**, cliquez sur ![icône Points de suspension - Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) dans la dernière colonne de la ligne de la variable à modifier.
1. Dans le menu déroulant, cliquez sur **Modifier**.

   ![Modifier ou supprimer une variable](assets/edit-delete-variable.png)

1. Mettez à jour la valeur de la variable d’environnement selon les besoins.
Lors de la modification d’un secret, la valeur peut uniquement être mise à jour, mais pas affichée.

   ![Modifier la variable](assets/edit-variable.png)

1. Utilisez l’une des méthodes suivantes :

   * Cliquez sur ![Appliquer - Icône de coche](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg) pour appliquer la modification.
   * Cliquez sur ![Icône Annuler](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Undo_18_N.svg) pour annuler la modification.

1. Cliquez sur **Enregistrer**.

   Une double flèche avec le statut **Mise à jour en cours** s’affiche dans le coin supérieur droit du tableau. Une double flèche s’affiche également à gauche de toutes les variables mises à jour. Ces statuts indiquent que l’environnement est en cours de mise à jour avec la configuration. Une fois l’opération terminée, la variable d’environnement mise à jour est visible dans le tableau.

## Suppression d’une variable d’environnement {#delete-env-variable}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.
1. Dans la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez celui que vous souhaitez gérer.
1. Dans le menu latéral, cliquez sur **Environnements**.
1. Sur la page **Environnements**, sélectionnez une ligne du tableau contenant l’environnement pour lequel vous souhaitez mettre à jour une variable.
1. Sur la page de détails de l’environnement, cliquez sur l’onglet **Configuration**.
1. Cliquez sur ![Ajouter/Mettre à jour - Icône Ajouter un cercle](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **Ajouter/Mettre à jour**.
1. Dans la boîte de dialogue **Configuration de l’environnement**, cliquez sur ![icône Points de suspension - Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) dans la dernière colonne de la ligne de la variable à modifier.
1. Dans le menu déroulant, cliquez sur **Supprimer** pour supprimer immédiatement la variable.
1. Cliquez sur **Enregistrer**.

## Utilisation des variables d’environnement {#using}

Les variables d’environnement peuvent rendre vos configurations `pom.xml` plus sécurisées et flexibles. Par exemple, les mots de passe n’ont pas besoin d’être codés en dur et votre configuration peut s’adapter en fonction des valeurs des variables d’environnement.

Vous pouvez accéder aux variables d’environnement et aux secrets par le biais du code XML comme suit :

`${env.VARIABLE_NAME}`

Consultez [Configuration d’un projet](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#password-protected-maven-repository-support-password-protected-maven-repositories) pour un exemple d’utilisation des deux types de variables dans un fichier `pom.xml`.

Consultez également la [documentation officielle de Maven](https://maven.apache.org/settings.html#quick-overview) pour plus d’informations.

## Disponibilité des variables d’environnement {#availability}

Les variables d’environnement peuvent être utilisées à plusieurs endroits comme suit :

| Où les variables d’environnement peuvent être utilisées | Description |
| --- | --- |
| Créer, prévisualiser et publier | Les variables d’environnement standard et les secrets peuvent être utilisés dans les environnements de création, de prévisualisation et de publication. |
| Dispatcher | Seules les variables d’environnement normales peuvent être utilisées avec [Dispatcher](https://experienceleague.adobe.com/fr/docs/experience-manager-dispatcher/using/dispatcher).<ul><li>Les secrets ne peuvent pas être utilisés.</li><li>Les variables d’environnement ne peuvent pas être utilisées dans les directives `IfDefine`.</li><li>Vous devez valider l’utilisation des variables d’environnement avec le [Dispatcher localement](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools) avant le déploiement.</li></ul> |
| Configurations OSGi | Les variables d’environnement normales et les secrets peuvent être utilisés dans les configurations [OSGi](/help/implementing/deploying/configuring-osgi.md). |
| Variables de pipeline | Outre les variables d’environnement, il existe également des variables de pipeline, qui sont exposées pendant la phase de création. En savoir plus sur les variables de pipeline dans [Environnement de création](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#pipeline-variables). |

