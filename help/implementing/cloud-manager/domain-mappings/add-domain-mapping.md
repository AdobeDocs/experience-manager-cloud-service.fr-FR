---
title: Ajouter un mappage de domaine
description: Découvrez comment ajouter un mappage de domaine pour un site Edge Delivery ou un environnement Cloud Manager.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 672513d7-ee0a-4f6e-9ef0-7a41fabbaf9a
source-git-commit: c2229d040c8df7c9089d141d57ca59ff2f4ce8a7
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 9%

---


# Ajouter un mappage de domaine {#add-domain-mapping}

Pour lier un domaine à un certificat SSL sur le réseau CDN géré par Adobe dans votre programme, vous devez ajouter une configuration de réseau CDN (Content Delivery Network).

Pour les réseaux de diffusion de contenu gérés par Adobe, lors de l’utilisation d’un certificat SSL DV, seuls les sites avec validation ACME sont autorisés.

>[!IMPORTANT]
>
>Avez-vous [ajouté un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) et [ajouté un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md), respectivement ? Dans le cas contraire, vous devez effectuer ces deux tâches avant de pouvoir ajouter une configuration de réseau CDN.

Consultez également la section [Réseau CDN géré par Adobe](https://www.aem.live/docs/byo-cdn-adobe-managed).

**Pour ajouter un mappage de domaine, procédez comme suit**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Selon votre cas d’utilisation, effectuez l’une des opérations suivantes :

   | Cas d’utilisation | Étapes |
   | --- | --- |
   | Je souhaite ajouter une configuration de réseau CDN à un site *existant* Edge Delivery dans Cloud Manager | a. Dans le menu de gauche, sous **Services**, cliquez sur ![Icône Pages web](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery Sites**.<br>b. Dans le tableau Edge Delivery, au bout d’une ligne à laquelle aucun domaine n’est associé, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).<br>c. Cliquez sur **Configurer le réseau CDN**. |
   | Je souhaite ajouter une configuration de réseau CDN dans Cloud Manager | a. Dans le menu de gauche, sous **Services**, cliquez sur ![Icône de réseau social](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **Mappages de domaine**.<br>b. Dans le coin supérieur droit de la page Mappages de domaine, cliquez sur **Ajouter**. |

1. Dans la boîte de dialogue **Configurer le réseau CDN**, dans la liste déroulante **Origine**, sélectionnez l’une des options suivantes :

   ![Boîte de dialogue Configurer le réseau CDN](/help/implementing/cloud-manager/assets/configure-cdn-dialog.png)

   | Origine | Description |
   | --- | --- |
   | Sites | Sélectionnez un site Edge Delivery. |
   | Environnement | Sélectionnez un environnement Cloud Service spécifique que vous souhaitez cibler dans votre configuration AEM.<br>Dans la liste déroulante **Niveau**, sélectionnez l’une des options suivantes :<br>· Sélectionnez **Publier** pour cibler un environnement de production en ligne où le contenu est diffusé aux utilisateurs finaux et utilisatrices finales.<br>· Sélectionnez **Aperçu** pour les environnements d’évaluation ou hors production où vous testez les modifications avant qu’elles ne soient mises en ligne. |

1. Sélectionnez votre type de réseau CDN et la configuration associée en sélectionnant l’une des options suivantes :

   | Type de réseau CDN | Détails de la configuration |
   | --- | --- |
   | Réseau CDN géré par Adobe | Sous **Détails de la configuration**, procédez comme suit :<br>a. Dans la liste déroulante **Domaine**, sélectionnez le nom de domaine que vous souhaitez utiliser.<br>Aucun domaine vérifié disponible dans la liste déroulante ? Consultez [Ajouter un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).<br>b. Dans la liste déroulante **certificat SSL**, sélectionnez un certificat que vous souhaitez utiliser.<br>Aucun certificat SSL disponible dans la liste déroulante ? Voir [ Ajouter un certificat SSL ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md). |
   | Autre fournisseur de réseau CDN | Sélectionnez cette option si vous utilisez votre propre fournisseur de réseau CDN et non le réseau CDN géré par Adobe disponible.<br>Sous **Détails de configuration**, dans la liste déroulante **Domaine**, sélectionnez le nom de domaine à utiliser.<br>Aucun domaine vérifié disponible dans la liste déroulante ? Consultez [Ajouter un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). |

1. Cliquez sur **Enregistrer**.
