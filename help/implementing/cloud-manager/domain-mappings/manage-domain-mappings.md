---
title: Gérer les mappages de domaine
description: Découvrez comment utiliser Cloud Manager pour modifier, mettre à jour ou supprimer des configurations de réseau CDN pour un site Edge Delivery ou un environnement Cloud Manager.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
exl-id: 2ec16c91-0195-4732-a26d-ac223e10afb9
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 8%

---

# Gérer les mappages de domaine {#manage-domain-mappings}

Découvrez comment utiliser Cloud Manager pour modifier ou supprimer des configurations de réseau CDN pour un site Edge Delivery ou un environnement Cloud Manager.

## Modifier une configuration de réseau CDN à partir de la page Mappages de domaine {#edit-domain-mapping}

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

1. Dans la boîte de dialogue **Modifier le mappage de domaine**, définissez une ou plusieurs des options dans la liste déroulante correspondante.

   Les options affichées dans la boîte de dialogue varient selon que vous utilisez un réseau CDN géré par Adobe **** ou un **autre fournisseur de réseau CDN** (réseau CDN géré par le client).

1. Cliquez sur **Mettre à jour**.


## Préparation à la mise en production : configuration des paramètres DNS pour un domaine personnalisé {#go-live-readiness}

Avant qu’un domaine personnalisé puisse servir le trafic, vous devez effectuer la configuration DNS avec votre fournisseur DNS. Après avoir déployé un mappage de domaine et cliqué sur **Activer**, Cloud Manager affiche une boîte de dialogue qui vous guide tout au long du processus de configuration des enregistrements DNS. Vous avez la possibilité d’activer en ajoutant un type d’enregistrement CNAME ou A.

<!-- See also [APEX record](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md#adobe-managed-cert-cname-record#adobe-managed-cert-apex-record) and [CNAME record](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md#adobe-managed-cert-cname-record). -->

**Pour configurer la préparation à la mise en production, procédez comme suit**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.
1. Dans le menu de gauche, sous **Services**, cliquez sur ![Icône de réseau social](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **Mappages de domaine**.
1. Dans le tableau Mappages de domaine, cliquez sur **Activation** à la fin d’une ligne correspondant à un réseau CDN dont vous souhaitez configurer la préparation à l’activation.

   ![Boîte de dialogue de préparation à la mise en production](/help/implementing/cloud-manager/assets/domain-mappings-go-live-readiness.png)

1. Dans la boîte de dialogue **Préparation à la mise en production**, effectuez l’une des opérations suivantes :

   | Option | Étapes |
   | --- | --- |
   | Configurer un ENREGISTREMENT A | Recommandé pour les domaines racine tels que `example.com`<br><ol><li>Connectez-vous au portail de votre fournisseur de services DNS.<li>Accédez à la section Enregistrements DNS .<li>Créez un enregistrement A pour pointer vers toutes les adresses IP répertoriées.</li></ol> |
   | Configurer CNAME | Recommandé pour les domaines personnalisés tels que `www.example.com`<br><ol><li>Connectez-vous au portail du fournisseur de services DMS.<li>Accédez à la section Enregistrements DNS .<li>Mappez `cdn.adobeaemcloud.com` (enregistrement CNAME) dans l’enregistrement DNS du fournisseur de services DNS (votre domaine personnalisé). Ce mappage garantit que les requêtes reçues au niveau du domaine personnalisé sont redirigées vers le réseau CDN d’Adobe.</li></ol> |

1. Dans la boîte de dialogue **Préparation de la mise en production**, cliquez sur **OK** pour enregistrer l’enregistrement.

   Attendez la propagation du DNS ; cela peut prendre de quelques minutes à quelques heures.

   Lorsque la colonne **[!UICONTROL Statut]** du tableau Mappages de domaine est mise à jour sur **[!UICONTROL Vérifié]**, le domaine personnalisé est prêt à être utilisé. Vous devrez peut-être cliquer sur ![icône d’actualisation](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Refresh_18_N.svg) pour mettre à jour le statut.

## Suppression d’une configuration de réseau CDN {#delete-cdn}

Lorsque vous supprimez une configuration de réseau CDN géré par Adobe ou géré par le client dans Cloud Manager, les paramètres de routage et de certificat SSL du domaine associé sont supprimés. Le domaine n’utilise plus le réseau CDN pour la diffusion du trafic et toute amélioration de la sécurité ou des performances fournie par le réseau CDN est perdue. Le service peut être interrompu jusqu’à ce qu’une nouvelle configuration soit configurée, que ce soit pour rajouter le réseau CDN supprimé ou en ajouter un nouveau.

Un utilisateur doit disposer du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour terminer cette tâche.

**Pour supprimer une configuration de réseau CDN, procédez comme suit**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans le menu de gauche, sous **Services**, cliquez sur ![Icône de réseau social](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **Mappages de domaine**.

1. Dans le tableau Mappages de domaine, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à la fin d’une ligne correspondant au réseau CDN à supprimer, puis cliquez sur **Supprimer**.

1. Dans la boîte de dialogue **Supprimer le mappage de domaine**, cliquez sur **Supprimer**.

1. Cliquez de nouveau sur **Supprimer** pour confirmer la suppression du réseau CDN du site.


## Supprimer une configuration de réseau CDN de la page Environnements

Les étapes de suppression d’une configuration de réseau CDN de la page **Environnements** sont presque identiques à celles de la [suppression d’une configuration de réseau CDN de la page Mappages de domaine](#edit-cdn), mais le point d’entrée diffère.

**Pour supprimer une configuration de réseau CDN de la page Environnements :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Dans le menu de gauche, cliquez sur ![Icône de données](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **Environnements**.

1. Sur la page **Environnements**, sélectionnez un environnement qui vous intéresse.

1. Sur la page des détails de l’environnement, dans le regroupement **Mappages de domaine**, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) correspondant à la configuration de réseau CDN à supprimer, puis cliquez sur **Supprimer**.

1. Dans la boîte de dialogue **Supprimer le mappage de domaine**, cliquez sur **Supprimer**.

1. Cliquez de nouveau sur **Supprimer** pour confirmer la suppression du réseau CDN du site.
