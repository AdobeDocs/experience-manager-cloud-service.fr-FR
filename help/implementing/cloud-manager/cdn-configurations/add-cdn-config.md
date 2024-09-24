---
title: Ajouter une configuration CDN
description: Découvrez comment ajouter une configuration CDN pour un site Edge Delivery ou un environnement Cloud Manager.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 672513d7-ee0a-4f6e-9ef0-7a41fabbaf9a
source-git-commit: 2d1382c84d872719332986baa5829d1623d9d9a6
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 7%

---


# Ajout d’une configuration CDN (Content Delivery Network) {#add-cdn}

Pour lier un domaine à un certificat SSL sur le réseau de diffusion de contenu géré par l’Adobe dans votre programme, vous devez ajouter une configuration CDN (Content Delivery Network).

Pour les réseaux de diffusion de contenu gérés par Adobe, lors de l’utilisation de certificats DV, seuls les sites avec validation ACME sont autorisés.

>[!IMPORTANT]
>
>Avez-vous [ajouté un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) et [ajouté un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md), respectivement ? Dans le cas contraire, vous devez effectuer ces deux tâches avant de pouvoir ajouter une configuration CDN.

**Pour ajouter une configuration CDN :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Selon votre cas d’utilisation, effectuez l’une des opérations suivantes :

   | Cas d’utilisation | Étapes |
   | --- | --- |
   | Je souhaite ajouter une configuration CDN à un site Edge Delivery *existant* dans Cloud Manager | a. Dans le panneau de navigation de gauche, sous **Services**, cliquez sur **Edge Delivery Sites**.<br>b. Dans le tableau Edge Delivery, à la fin d’une ligne à laquelle aucun domaine n’est associé, cliquez sur les points de suspension.<br>c. Cliquez sur **Configurer CDN**.  ![ Cliquez sur Configurer le réseau de diffusion de contenu pour un site Edge Delivery ](/help/implementing/cloud-manager/assets/cm-eds-config-cdn.png) |
   | Je souhaite ajouter une configuration CDN dans Cloud Manager | a. Dans le panneau de navigation de gauche, sous **Services**, cliquez sur **Configurations CDN**.<br>b. Dans le coin supérieur droit de la page Configurations du réseau de diffusion de contenu, cliquez sur **Ajouter**. |

1. Dans la boîte de dialogue **Configurer CDN**, dans la liste déroulante **Origin**, sélectionnez l’une des options suivantes :

   ![Boîte de dialogue Configurer le réseau de diffusion de contenu](/help/implementing/cloud-manager/assets/configure-cdn-dialog.png)

   | Origine | Description |
   | --- | --- |
   | Sites | Sélectionnez un site Edge Delivery. |
   | Environnement | Sélectionnez un environnement de Cloud Service spécifique que vous souhaitez cibler dans votre configuration AEM.<br>Dans la liste déroulante **Niveau** , sélectionnez l’une des options suivantes : <br> ・ sélectionnez **Publish** pour cibler un environnement de production en ligne où le contenu est diffusé aux utilisateurs finaux.<br> ・ Sélectionnez **Aperçu** pour les environnements d’évaluation ou hors production dans lesquels vous testez les modifications avant qu’elles ne soient activées. |

1. Sélectionnez le type CDN et la configuration associée en sélectionnant l’une des options suivantes :

   | Type CDN | Détails de la configuration |
   | --- | --- |
   | Réseau CDN géré par Adobe | Sous **Détails de configuration**, procédez comme suit :<br>a. Dans la liste déroulante **Domaine** , sélectionnez le nom de domaine que vous souhaitez utiliser.<br>Aucun domaine vérifié n’est disponible dans la liste déroulante ? Voir [Ajout d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).<br>b. Dans la liste déroulante **Certificat SSL**, sélectionnez un certificat que vous souhaitez utiliser.<br>Aucun certificat SSL disponible dans la liste déroulante ? Voir [Ajout d’un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md). |
   | Autre fournisseur de réseau CDN | Sélectionnez cette option si vous utilisez votre propre fournisseur de réseau de diffusion de contenu et non le réseau de diffusion de contenu géré par l’Adobe qui vous est disponible.<br>Sous **Détails de configuration**, dans la liste déroulante **Domaine**, sélectionnez le nom de domaine que vous souhaitez utiliser.<br>Aucun domaine vérifié n’est disponible dans la liste déroulante ? Voir [Ajout d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). |

1. Cliquez sur **Enregistrer**.
