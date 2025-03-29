---
title: Gérer les mappages de domaine
description: Découvrez comment utiliser Cloud Manager pour modifier, mettre à jour ou supprimer des configurations de réseau CDN pour un site Edge Delivery ou un environnement Cloud Manager.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 2ec16c91-0195-4732-a26d-ac223e10afb9
source-git-commit: 41155a724f48ad28a12aac615a3e9a13bb3afa26
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 8%

---

# Gérer les mappages de domaine {#manage-cdn-configurations}

Découvrez comment utiliser Cloud Manager pour modifier ou supprimer des configurations de réseau CDN pour un site Edge Delivery ou un environnement Cloud Manager.

## Modifier une configuration de réseau CDN à partir de la page Mappages de domaine {#edit-cdn}

Dans Adobe Cloud Manager, vous pouvez modifier une configuration de réseau CDN (Content Delivery Network), y compris le niveau d’environnement (Publication ou Prévisualisation) et le certificat SSL, pour plusieurs raisons.

* **Modifications de l’environnement** : l’ajustement du niveau permet de faire correspondre les paramètres du réseau CDN à l’environnement approprié, que ce soit pour la production en direct (publication) ou les tests (aperçu).
* **Améliorations de la sécurité** : la sélection d’un autre certificat SSL peut être nécessaire lors de la mise à jour des certificats ou pour répondre aux besoins de conformité et de sécurité.
* **Optimisation des performances** : la modification de la configuration garantit que les paramètres de réseau CDN corrects pour diffuser du contenu en fonction des besoins opérationnels changeants.

Vous pouvez modifier une configuration sans supprimer complètement la configuration existante. Les modifications s’appliquent à l’environnement sélectionné, par exemple l’environnement d’évaluation ou de production, et peuvent affecter la manière dont le contenu est diffusé et sécurisé.

Un utilisateur doit disposer du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour terminer cette tâche.

**Pour modifier une configuration de réseau CDN à partir de la page Mappages de domaine :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Dans le menu de gauche, sous **Services**, cliquez sur ![Icône de réseau social](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **Mappages de domaine**.
1. Dans le tableau **Mappages de domaine**, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à la fin d’une ligne dont vous souhaitez mettre à jour la configuration de réseau CDN.

1. Dans le menu déroulant, cliquez sur **Modifier**.

1. Dans la boîte de dialogue **Modifier la configuration du réseau de diffusion de contenu**, définissez une ou plusieurs des options dans la liste déroulante correspondante.

   Les options affichées dans la boîte de dialogue varient selon que vous utilisez un réseau CDN géré par Adobe **** ou un **autre fournisseur de réseau CDN** (réseau CDN géré par le client).

1. Cliquez sur **Mettre à jour**.

   Le statut du réseau CDN modifié est mis à jour dans le tableau **Mappages de domaine** pour refléter les modifications que vous avez apportées.


## Modifier une configuration de réseau CDN à partir de la page Environnements

Les étapes de modification d’une configuration de réseau CDN à partir de la page **Environnements** sont presque identiques à celles de la [modification d’une configuration de réseau CDN à partir de la page Mappages de domaine](#edit-cdn), mais le point d’entrée diffère.

**Pour modifier une configuration de réseau CDN à partir de la page Environnements :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans le menu de gauche, cliquez sur ![Icône de données](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **Environnements**.

1. Sur la page **Environnements**, sélectionnez un environnement qui vous intéresse.

1. Sur la page des détails de l’environnement, dans le groupe Mappages de domaine, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) qui correspond à la configuration de réseau CDN que vous souhaitez modifier.

1. Dans le menu pop-up, cliquez sur **Modifier**.

1. Dans la boîte de dialogue **Modifier la configuration du réseau de diffusion de contenu**, définissez une ou plusieurs des options dans la liste déroulante correspondante.

   Les options affichées dans la boîte de dialogue varient selon que vous utilisez un réseau CDN géré par Adobe **** ou un **autre fournisseur de réseau CDN** (réseau CDN géré par le client).

1. Cliquez sur **Mettre à jour**.

<!-- 
## Go live readiness: Configure DNS settings for a custom domain {#go-live-readiness} 

Before a custom domain can serve traffic in Adobe Cloud Manager, you must complete DNS configuration with your DNS provider. After deploying a domain mapping and clicking **Go live**, Cloud Manager displays a dialog box that guides you through the DNS record setup process. You have the option to go live by adding either a CNAME record type or an A record type representing Fastly's IPs, simplifying domain routing. This ability eliminates the restriction of relying solely on CNAME records for domain setup with Fastly.

MAYBE There is support for A record types to improve Go Live readiness for domains using CDN configurations in AEM Cloud Manager. MAYBE

See also [APEX record](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md#adobe-managed-cert-cname-record#adobe-managed-cert-apex-record) and [CNAME record](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md#adobe-managed-cert-cname-record).

**To configure Go live readiness:**

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. In the left side menu, under **Services**, click ![Social network icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **Domain Mappings**.

1. In the Domain Mappings table, click **Go live** near the end of a row that corresponds to a CDN whose Go Live readiness you want to configure. 

1. In the Go live readiness dialog box, do one of the following:

    | Configure  | Steps |
    | --- | --- |
    | A RECORD | Recommended for root domains like `example.com`<br><ol><li>Log in to your DNS service provider's portal.<li>Go to the DNS Records section.<li>Create an A record to point to all the listed IP addresses.<li>In the Go live readiness dialog box, click **OK**.<li>In the Domain Mappings table, under the **Status** column, click ![Refresh icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Refresh_18_N.svg).<br>The status is updated to **Verified** when the resolution is complete.</li></ol> |
    | CNAME | Recommended for custom domains like `www.example.com`<br><ol><li>Log in to your DMS service provider's portal.<li>Go to the DNS Records section.<li>Map [cdn.adobeaemcloud.com](http://cdn.adobeaemcloud.com/) (CNAME record) in the DNS record of the DNS service provider (your custom domain). This mapping ensures that requests received at the custom domain are redirected to Adobe's CDN.<li>In the **Go live readiness** dialog box, click **OK** to save the record.<br>Wait for DNS propogation (may take several minutes to a few hours). When the **[!UICONTROL Status]** column in the Domamin Mappings table updates to **[!UICONTROL Verified]**, the custom domain is ready to use. You may need to click ![Refresh icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Refresh_18_N.svg) to refresh the status.</li></ol> | 
    
-->

## Suppression d’une configuration de réseau CDN {#delete-cdn}

Lorsque vous supprimez une configuration de réseau CDN géré par Adobe ou géré par le client dans Cloud Manager, les paramètres de routage et de certificat SSL du domaine associé sont supprimés. Le domaine n’utilise plus le réseau CDN pour la diffusion du trafic et toute amélioration de la sécurité ou des performances fournie par le réseau CDN est perdue. Le service peut être interrompu jusqu’à ce qu’une nouvelle configuration soit configurée, que ce soit pour rajouter le réseau CDN supprimé ou en ajouter un nouveau.

Un utilisateur doit disposer du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour terminer cette tâche.

**Pour supprimer une configuration de réseau CDN, procédez comme suit**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans le menu de gauche, sous **Services**, cliquez sur ![Icône de réseau social](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **Mappages de domaine**.

1. Dans le tableau Mappages de domaine, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à la fin d’une ligne correspondant au réseau CDN à supprimer, puis cliquez sur **Supprimer**.

1. Dans la boîte de dialogue **Supprimer la configuration du réseau CDN**, cliquez sur **Supprimer**.

1. Cliquez de nouveau sur **Supprimer** pour confirmer la suppression du réseau CDN du site.


## Supprimer une configuration de réseau CDN de la page Environnements

Les étapes de suppression d’une configuration de réseau CDN de la page **Environnements** sont presque identiques à celles de la [suppression d’une configuration de réseau CDN de la page Mappages de domaine](#edit-cdn), mais le point d’entrée diffère.

**Pour supprimer une configuration de réseau CDN de la page Environnements :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans le menu de gauche, cliquez sur ![Icône de données](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **Environnements**.

1. Sur la page **Environnements**, sélectionnez un environnement qui vous intéresse.

1. Sur la page des détails de l’environnement, dans le regroupement **Mappages de domaine**, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) correspondant à la configuration de réseau CDN à supprimer, puis cliquez sur **Supprimer**.

1. Dans la boîte de dialogue **Supprimer la configuration du réseau CDN**, cliquez sur **Supprimer**.

1. Cliquez de nouveau sur **Supprimer** pour confirmer la suppression du réseau CDN du site.
