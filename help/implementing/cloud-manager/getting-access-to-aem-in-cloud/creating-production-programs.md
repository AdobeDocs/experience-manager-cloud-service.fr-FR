---
title: Création de programmes de production
description: Découvrez comment utiliser Cloud Manager pour créer votre propre programme de production afin d’héberger le trafic en direct.
exl-id: 4ccefb80-de77-4998-8a9d-e68d29772bb4
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 88b0479c44f6431a9f254551e51b1ce86af91d0f
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 34%

---


# Création de programmes de production {#create-production-program}

Un programme de production est destiné à un utilisateur qui connaît AEM et Cloud Manager et qui est prêt à se lancer dans l’écriture, la compilation et le test de code en vue de le déployer pour héberger du trafic en direct.

Découvrez-en plus sur les types de programme dans le document [Présentation des programmes et des types de programme.](program-types.md)

## Création d’un programme de production {#create}

Pour créer un programme de production, procédez comme suit. Notez que selon les droits de votre organisation, vous pouvez voir [autres options](#options) lors de l’ajout de votre programme.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Dans la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, appuyez ou cliquez sur **Ajouter un programme** dans le coin supérieur droit de l’écran.

   ![Page de destination de Cloud Manager](assets/log-in.png)

1. Sélectionnez **Configuration pour la production** dans l’assistant de création de programme pour créer un programme de production et fournissez un nom de programme.

   ![Créer un assistant de programme](assets/create-production-program.png)

1. Vous pouvez éventuellement ajouter une image au programme en faisant glisser un fichier image et en le déposant sur la cible **Ajouter une image de programme** ou en cliquant dessus pour sélectionner une image dans l’explorateur de fichiers. Sélectionnez **Continuer**.

1. Dans l’onglet **Solutions et modules complémentaires**, sélectionnez les solutions à inclure dans le programme.

   * Si vous ne savez pas si vous avez besoin d’un ou de plusieurs programmes pour les différentes solutions disponibles, sélectionnez celle qui vous intéresse le plus. Vous pouvez activer des solutions supplémentaires en [modifiant le programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md) plus tard. Consultez le [document Présentation des programmes de production](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md) pour plus de recommandations sur la configuration des programmes.
   * Au moins une solution est nécessaire pour la création du programme.
   * Si vous avez sélectionné l’option **[Activer la sécurité améliorée](#security)**, vous êtes autorisé à sélectionner uniquement autant de solutions pour lesquelles des droits HIPAA sont disponibles.

   ![Solutions sélectionnées](assets/setup-prod-select.png)

1. Cliquez sur le chevron situé avant les noms des solutions pour afficher les modules complémentaires facultatifs, comme la sélection de l’option de module complémentaire **Commerce** sous **Sites**.

   ![Sélectionner les modules complémentaires](assets/setup-prod-commerce.png)

1. Lorsque vos solutions et modules complémentaires sont sélectionnés, cliquez sur **Continuer**.

1. Dans l’onglet **Date de mise en production**, saisissez la date de mise en production de votre programme.

   ![Définir la date de mise en production planifiée](assets/set-up-go-live.png)

   * Cette date peut être modifiée à tout moment.
   * Cette date est destinée à un usage informatif uniquement. Elle déclenche le widget GoLive sur la [**page Aperçu du programme**](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#program-overview) afin de fournir des liens internes au produit vers la documentation des bonnes pratiques d’AEM as a Cloud Service dans les délais impartis pour s’aligner sur votre parcours, ce qui se traduit par une expérience GoLive réussie et fluide.

1. Cliquez sur **Créer**.

Votre programme est créé par Cloud Manager, s’affiche et peut être sélectionné dans la page de destination.

![Aperçu de Cloud Manager](assets/navigate-cm.png)

## Options de programme de production supplémentaires {#options}

En fonction des droits dont dispose votre organisation, vous disposez peut-être d’autres options lorsque vous créez un programme de production.

### Sécurité {#security}

Si vous disposez des droits nécessaires, l’onglet **Sécurité** s’affiche comme premier onglet dans la boîte de dialogue **Configuration pour la production**.

L’onglet **Sécurité** fournit les options permettant d’activer **HIPAA** et/ou la **protection WAF-DDOS** pour votre programme de production.

Adobe Conformité à la HIPAA et pare-feu d’applications web (WAF) facilite la sécurité dans le cloud dans le cadre d’une approche à plusieurs niveaux pour la protection contre les vulnérabilités.

* **HIPAA** - Cette option permet la mise en oeuvre de solutions prêtes pour l’HIPPA par l’Adobe.
   * [En savoir plus](https://www.adobe.com/go/hipaa-ready) sur la mise en œuvre de la solution conforme à la norme HIPAA d’Adobe.
   * HIPAA ne peut pas être activé ni désactivé après la création du programme.
* **Protection WAF-DDOS** - Cette option active le pare-feu d’application web via des règles pour protéger votre application.
   * Une fois activée, la protection WAF-DDOS peut être configurée en configurant un [pipeline hors production.](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)
   * Consultez le document [Règles de filtrage du trafic y compris les règles WAF](/help/security/traffic-filter-rules-including-waf.md) pour savoir comment gérer les règles de filtrage du trafic dans votre référentiel afin qu’elles soient déployées correctement.

![Options de sécurité](assets/create-production-program-security.png)

### SLA {#sla}

Si vous disposez des droits nécessaires, l’onglet **SLA** s’affiche comme deuxième ou troisième onglet dans la boîte de dialogue **Configuration pour la production**.

AEM Sites et Forms offrent un contrat de niveau de service (SLA) standard de 99,9 %. L’option **99.99% Service Level Agreement** active un pourcentage de temps de disponibilité minimal de 99,99% pour vos environnements de production pour Sites et/ou Forms.

Le contrat SLA de 99,99 % offre des avantages, notamment une disponibilité plus élevée et une latence plus faible, et nécessite une [région de publication supplémentaire](/help/implementing/cloud-manager/manage-environments.md#multiple-regions) à appliquer à l’environnement de production dans le programme.

![Options SLA](assets/create-production-program-sla.png)

Une fois que les [conditions requises](#sla-requirements) pour activer le contrat de niveau de service 99,99 % sont remplies, vous devez exécuter un [pipeline de pile complet](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) pour l’activer.

#### Conditions requises pour un contrat SLA de 99,99 % {#sla-requirements}

Outre les droits requis, 99,99 % des contrats de niveau de service (SLA) ont des exigences supplémentaires d’utilisation.

* L’organisation doit avoir accès aux droits SLA de 99,99 % et aux autres droits de région de publication au moment de l’application de 99,99 % SLA au programme.
* Pour appliquer un contrat SLA de 99,99 % au programme, Cloud Manager vérifie qu’un droit [région de publication supplémentaire](/help/implementing/cloud-manager/manage-environments.md#multiple-regions) non consommé est également disponible et peut être appliqué au programme.
* Lors de la modification d’un programme, s’il contient déjà un environnement de production avec au moins une région de publication supplémentaire, Cloud Manager vérifie uniquement la disponibilité d’un droit SLA de 99,99 %.
* Pour que le contrat SLA de 99,99 % et le reporting soient activés, l’ [environnement de production/d’évaluation](/help/implementing/cloud-manager/manage-environments.md#adding-environments) doit avoir été créé et au moins une région de publication supplémentaire doit avoir été appliquée à l’environnement de production/d’évaluation.
   * Si vous utilisez [une mise en réseau avancée,](/help/security/configuring-advanced-networking.md) assurez-vous de consulter le document [Ajout de plusieurs régions Publish à un nouvel environnement](/help/implementing/cloud-manager/manage-environments.md#adding-regions) pour obtenir des recommandations afin de maintenir la connectivité en cas d’échec régional.
* Au moins une région de publication supplémentaire doit rester dans votre programme SLA de 99,99 %. Les utilisateurs ne sont pas autorisés à supprimer la dernière région de publication supplémentaire de votre programme SLA 99,99 %.
* 99,99 % du contrat SLA est pris en charge pour les programmes de production pour lesquels la solution Sites ou Forms est activée.
* Vous devez exécuter un [pipeline de pile complet](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) pour activer (ou, lors de la modification d’un programme, désactiver) le contrat SLA de 99,99 %.

## Accès à votre programme {#accessing}

1. Lorsque la carte du programme s’affiche sur la landing page, cliquez sur le bouton représentant des points de suspension pour afficher les options de menu disponibles.

   ![Aperçu du programme](assets/program-overview.png)

1. Sélectionnez **Cloud Manager** pour accéder à la page **Aperçu** de Cloud Manager.

1. La carte principale d’appel à l’action de la page d’aperçu vous guide tout au long de la création d’un environnement, d’un pipeline hors production et, enfin, d’un pipeline de production.

   ![Aperçu du programme](assets/set-up-prod5.png)

>[!TIP]
>
>Consultez le document [Navigation dans l’interface utilisateur de Cloud Manager](/help/implementing/cloud-manager/navigation.md) pour plus d’informations sur la navigation dans Cloud Manager et sur la compréhension de la console **Mes programmes**.

>[!NOTE]
>
>Contrairement à un [programme Sandbox,](introduction-sandbox-programs.md#auto-creation) un programme de production nécessite que l’utilisateur possédant le rôle Cloud Manager approprié crée le projet et ajoute un environnement via l’interface utilisateur en libre-service.
