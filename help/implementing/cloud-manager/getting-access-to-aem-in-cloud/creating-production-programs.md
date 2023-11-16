---
title: Création de programmes de production
description: Découvrez comment utiliser Cloud Manager pour créer votre propre programme de production afin d’héberger le trafic en direct.
exl-id: 4ccefb80-de77-4998-8a9d-e68d29772bb4
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '601'
ht-degree: 73%

---


# Création de programmes de production {#create-production-program}

Un programme de production est destiné à un utilisateur qui connaît AEM et Cloud Manager et qui est prêt à se lancer dans l’écriture, la compilation et le test de code en vue de le déployer pour héberger du trafic en direct.

Découvrez-en plus sur les types de programme dans le document [Présentation des programmes et des types de programme.](program-types.md)

## Création d’un programme de production {#create}

Pour créer un programme de production, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur **Ajout d’un programme** dans le coin supérieur droit de l’écran.

   ![Page de destination de Cloud Manager](assets/log-in.png)

1. Sélectionnez **Configuration pour la production** dans l’assistant de création de programme pour créer un programme de production et fournissez un nom de programme.

   ![Créer un assistant de programme](assets/create-production-program.png)

1. Vous pouvez éventuellement ajouter une image au programme en faisant glisser un fichier image et en le déposant sur la cible **Ajouter une image de programme** ou en cliquant dessus pour sélectionner une image dans l’explorateur de fichiers. Cliquez ou appuyez sur **Continuer**.

1. Si vous disposez des droits nécessaires, la variable **Sécurité** s’affiche et permet d’activer **HIPAA** et/ou **Protection WAF-DDOS** pour votre programme de production. Si le programme que vous créez est requis, cochez la ou les options applicables, puis appuyez ou cliquez sur **Continuer**.

   * HIPAA ne peut pas être activé ni désactivé après la création du programme.
      * [En savoir plus](https://www.adobe.com/go/hipaa-ready) sur la mise en œuvre de la solution conforme à la norme HIPAA d’Adobe.
   * Une fois activée, la protection WAF-DDOS peut ensuite être configurée en configurant une [pipeline hors production.](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)

   {{waf-limited-release}}

   ![Options de sécurité](assets/create-production-program-security.png)

1. Dans l’onglet **Solutions et modules complémentaires**, sélectionnez les solutions à inclure dans le programme.

   * Si vous ne savez pas si vous avez besoin d’un ou de plusieurs programmes pour les différentes solutions disponibles, sélectionnez celle qui vous intéresse le plus. Vous pouvez activer des solutions supplémentaires en [modifiant le programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md) plus tard. Consultez le [document Présentation des programmes de production](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md) pour plus de recommandations sur la configuration des programmes.
   * Si vous avez coché la case **Activer la sécurité renforcée** à l’étape précédente, vous ne pourrez sélectionner que les solutions conformes à la norme HIPAA.

   ![Solutions sélectionnées](assets/setup-prod-select.png)

1. Cliquez sur le chevron situé avant les noms des solutions pour afficher les modules complémentaires facultatifs, tels que la sélection de la variable **Commerce** option de module complémentaire sous **Sites**.

   ![Sélectionner les modules complémentaires](assets/setup-prod-commerce.png)

1. Lorsque vos solutions et modules complémentaires sont sélectionnés, cliquez sur **Continuer**.

1. Dans l’onglet **Date de mise en production**, saisissez la date de mise en production de votre programme.

   ![Définir la date de mise en production planifiée](assets/setup-go-live.png)

   * Cette date peut être modifiée à tout moment.
   * Cette date est uniquement à usage informatif et déclenche le widget de mise en production sur la page de présentation du programme dans le but de fournir des liens internes au produit vers la documentation sur les bonnes pratiques d’AEM as a Cloud Service en temps opportun, afin de vous aligner sur votre parcours, offrant ainsi une expérience de mise en production réussie et fluide.

1. Cliquez sur **Créer**.

Votre programme est créé par Cloud Manager, s’affiche et peut être sélectionné dans la page de destination.

![Aperçu de Cloud Manager](assets/navigate-cm.png)

## Accès à votre programme {#accessing}

1. Lorsque la carte du programme s’affiche sur la landing page, cliquez sur le bouton représentant des points de suspension pour afficher les options de menu disponibles.

   ![Aperçu du programme](assets/program-overview.png)

1. Sélectionnez **Cloud Manager** pour accéder à la page **Aperçu** de Cloud Manager.

1. La carte principale d’appel à l’action de la page d’aperçu vous guide tout au long de la création d’un environnement, d’un pipeline hors production et, enfin, d’un pipeline de production.

   ![Aperçu du programme](assets/set-up-prod5.png)

Si, à tout moment, vous devez passer à un autre programme ou revenir à la page d’aperçu pour créer un autre programme, cliquez sur le nom de votre programme dans le coin supérieur gauche de l’écran pour afficher la variable **Accédez à** .

![Accéder à ](assets/create-program-a1.png)

>[!NOTE]
>
>Contrairement à un [programme Sandbox,](introduction-sandbox-programs.md#auto-creation) un programme de production nécessite que l’utilisateur possédant le rôle Cloud Manager approprié crée le projet et ajoute un environnement via l’interface utilisateur en libre-service.
