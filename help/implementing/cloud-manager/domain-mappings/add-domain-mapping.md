---
title: Ajouter un mappage de domaine
description: Découvrez comment ajouter un mappage de domaine pour un site Edge Delivery ou un environnement Cloud Manager.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
exl-id: 672513d7-ee0a-4f6e-9ef0-7a41fabbaf9a
source-git-commit: 4935fbf5f0eb10f2f17280fb32f07d99f69eb875
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 5%

---


# À propos de l’ajout d’un mappage de domaine {#add-domain-mapping}

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

1. Dans la boîte de dialogue **Mapper le domaine au réseau CDN**, sélectionnez l’un des types de réseau CDN suivants :

   * **Réseau CDN géré par Adobe (recommandé)** - Un réseau CDN géré par Adobe est utilisé pour cette configuration. Il comprend des fonctions de configuration et de gestion automatisées, ainsi que des fonctions de sécurité intégrées.
   * **Autre fournisseur de réseau CDN** - Un réseau de fournisseur de réseau CDN autogéré est utilisé pour cette configuration.

1. En fonction du type de réseau CDN sélectionné à l’étape précédente, procédez comme suit :

   * **Réseau CDN géré par Adobe**

     ![Boîte de dialogue Mapper le domaine au réseau CDN avec le bouton radio Adobe Managed CDN sélectionné](/help/implementing/cloud-manager/assets/cdn/map-domain-to-cdn-adobe-managed.png)

      1. Dans la liste déroulante **Origine**, sélectionnez l’une des options suivantes :

         | Liste déroulante Origine | Description |
         | --- | --- |
         | Sites | Sélectionnez un site Edge Delivery. |
         | Environnement | Sélectionnez un environnement Cloud Service spécifique que vous souhaitez cibler dans votre configuration AEM.<br>Dans la liste déroulante **Niveau**, sélectionnez l’une des options suivantes :<br>· Sélectionnez **Publier** pour cibler un environnement de production en ligne où le contenu est diffusé aux utilisateurs finaux et utilisatrices finales.<br>· Sélectionnez **Aperçu** pour les environnements d’évaluation ou hors production où vous testez les modifications avant qu’elles ne soient mises en ligne. |

      1. Dans la liste déroulante **Domaine**, sélectionnez le nom de domaine que vous souhaitez utiliser.<br>Aucun domaine vérifié disponible dans la liste déroulante ? Consultez [Ajouter un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).

      1. Dans la liste déroulante **certificat SSL**, sélectionnez un certificat que vous souhaitez utiliser.<br>Aucun certificat SSL disponible dans la liste déroulante ? Voir [&#x200B; Ajouter un certificat SSL &#x200B;](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md).

      1. Cliquez sur **Enregistrer**.

   * **Autre fournisseur de réseau CDN**

     ![Boîte de dialogue Mapper le domaine au réseau CDN avec le bouton radio Adobe Managed CDN sélectionné](/help/implementing/cloud-manager/assets/cdn/map-domain-to-cdn-other-provider.png)

     Suivez les étapes de configuration répertoriées pour appliquer les paramètres requis dans votre réseau CDN et confirmer le mappage. Voir aussi [Ajouter un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).

      1. Cliquez sur **J’ai configuré mon réseau CDN**.

   <!-- OLD IMAGE/UI (/help/implementing/cloud-manager/assets/configure-cdn-dialog.png)-->

   <!-- In the **Domain** field, enter the customer-facing hostname you want to serve (for example, `www.example.com`) -->

1. Adobe vous recommande de tester le mappage de domaine.

## Test du mappage de domaine {#test-domain-mapping}

Vous pouvez vérifier qu’un nouveau mappage de domaine est actif sur le réseau CDN géré par Adobe sans attendre la propagation du DNS public.

Exécutez une commande **curl** qui remplace la résolution DNS et pointe directement vers la périphérie du réseau CDN :

```bash
curl -svo /dev/null https://www.example.com \
--resolve www.example.com:443:151.101.3.10
```

* Remplacez `www.example.com` par votre domaine.
* L’adresse IP `151.101.3.10` est l’une des adresses IP qui peuvent être utilisées pour accéder à AEM Cloud Service. Voir aussi [enregistrement APEX](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md#adobe-managed-cert-apex-record).

L’indicateur `--resolve` force la requête à l’adresse IP spécifiée et renvoie un succès uniquement après l’installation correcte du certificat et du routage pour votre domaine.

