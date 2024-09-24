---
title: Ajouter un nom de domaine personnalisé
description: Découvrez comment ajouter un nom de domaine personnalisé à l’aide de Cloud Manager.
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 2d1382c84d872719332986baa5829d1623d9d9a6
workflow-type: tm+mt
source-wordcount: '1489'
ht-degree: 22%

---


# Ajouter un nom de domaine personnalisé {#adding-cdn}

Découvrez comment ajouter un nom de domaine personnalisé à l’aide de Cloud Manager.

## Conditions requises {#requirements}

Renseignez ces exigences avant d’ajouter un nom de domaine personnalisé dans Cloud Manager.

* Vous devez avoir ajouté un certificat SSL de domaine pour le domaine que vous souhaitez ajouter avant d’ajouter un nom de domaine personnalisé comme décrit dans le document [Ajout d’un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md).
* Vous devez disposer du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour ajouter un nom de domaine personnalisé dans Cloud Manager.
* Utilisez le réseau de diffusion de contenu Fastly ou autre (CDN).

>[!IMPORTANT]
>
>Même si vous utilisez un réseau de diffusion de contenu non Adobe, vous devez toujours ajouter votre domaine à Cloud Manager.

## Où ajouter des noms de domaine personnalisés {#where-to-add-cdn}

Vous pouvez ajouter un nom de domaine personnalisé à partir des deux emplacements suivants dans Cloud Manager :

* [Page Paramètres du domaine](#adding-cdn-settings)
* [Page Environnements](#adding-cdn-environments)

Lors de l’ajout d’un nom de domaine personnalisé, le domaine est diffusé à l’aide du certificat valide le plus spécifique. Si plusieurs certificats ont le même domaine, la mise à jour la plus récente est choisie. Adobe recommande de gérer les certificats de sorte qu’il n’y ait pas de chevauchement de domaines.

Les étapes de l’une ou l’autre des méthodes décrites dans ce document sont basées sur Fastly. Si vous avez utilisé un autre CDN (réseau de diffusion de contenu), configurez votre domaine avec le CDN que vous avez choisi d’utiliser.

## Ajouter un nom de domaine personnalisé {#adding-cdn-settings}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Dans le menu latéral, sous **Services**, sélectionnez **Paramètres de domaine**.

   ![Fenêtre Paramètres du domaine](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. Près du coin supérieur droit de la page **Paramètres du domaine**, cliquez sur **Ajouter un domaine**.

1. Dans la boîte de dialogue **Ajouter un domaine**, dans le champ **Nom de domaine**, saisissez le nom de domaine personnalisé que vous utilisez.
N’incluez pas `http://`, `https://` ni d’espace lors de la saisie dans votre domaine.

1. Cliquez sur **Créer**.

1. Dans la boîte de dialogue **Vérifier le domaine**, dans le **Quel type de certificat prévoyez-vous d’utiliser avec ce domaine ?Sélectionnez l’une des options suivantes dans la liste déroulante** :

   | Option de type de certificat | Description |
   | --- | --- |
   | Certificat géré par Adobe | Sélectionnez cette option si vous souhaitez utiliser un certificat DV (Domain Validation). Cette option est idéale pour la plupart des cas, car elle fournit une validation de domaine de base. Adobe gère et renouvelle automatiquement le certificat. |
   | Certificat géré par le client ou la cliente | Sélectionnez cette option si vous souhaitez utiliser un certificat EV/OV. Cette option offre une sécurité améliorée avec EV (validation étendue) ou OV (validation d’organisation). Utilisez cette option si une vérification plus stricte, des niveaux de confiance plus élevés ou un contrôle personnalisé sur les certificats est requis. |

1. Dans la boîte de dialogue **Vérifier le domaine**, en fonction du type de certificat que vous avez sélectionné, effectuez l’une des opérations suivantes :

   | Si vous avez sélectionné le type de certificat | Description |
   | --- | ---  |
   | Certificat géré par Adobe | Exécutez les [ étapes Adobe des certificats gérés ](#adobe-managed-cert-steps) avant de passer à l’étape suivante. |
   | Certificat géré par le client ou la cliente | Suivez les [étapes du certificat géré par le client](#customer-managed-cert-steps) avant de passer à l’étape suivante. |

1. Cliquez sur **Vérifier**.

1. Vous êtes maintenant prêt à [ajouter un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md).

   >[!NOTE]
   >
   >Si vous utilisez un certificat SSL auto-géré et un fournisseur CDN auto-géré, vous pouvez ignorer cette étape et accéder directement à [Ajouter une configuration CDN](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md) une fois prêt.


### Étapes du certificat géré par Adobe {#adobe-managed-cert-steps}

Si vous avez sélectionné le type de certificat *Adobe managed certificate*, exécutez les étapes suivantes dans la boîte de dialogue **Vérifier le domaine** .

![Adobe des étapes de certificat géré](/help/implementing/cloud-manager/assets/cdn/cdn-create-adobe-dv-cert.png)

Pour vérifier le domaine utilisé, vous devez ajouter et vérifier un CNAME.

Un enregistrement `CNAME` ou A, une fois configuré, achemine tout le trafic Internet pour le domaine vers l’emplacement où il pointe. Si cet emplacement n’est pas configuré pour desservir le trafic, il y a une panne. S’il n’a pas été testé, il se peut que le contenu présente des erreurs. C’est pourquoi cette étape est toujours effectuée une fois le test terminé et que vous êtes prêt à passer en ligne.

Pour configurer ces paramètres, déterminez si un enregistrement `CNAME` ou apex doit être configuré pour pointer votre nom de domaine personnalisé vers le nom de domaine Cloud Manager. Les sections suivantes de ce document peuvent vous aider à déterminer le type d’enregistrement approprié à votre configuration DNS.

>[!NOTE]
>
>Pour les réseaux de diffusion de contenu gérés par Adobe, lors de l’utilisation de certificats DV (Domain Validation), seuls les sites avec validation ACME sont autorisés.

#### Conditions requises {#adobe-managed-cert-dv-requirements}

Renseignez ces exigences avant de configurer vos enregistrements DNS.

* Identifiez l’hôte ou le serveur d’enregistrement de votre domaine si vous ne le connaissez pas déjà.
* Vous pouvez modifier les enregistrements DNS pour le domaine de votre entreprise ou contacter la personne appropriée qui peut le faire.
* Vous devez avoir déjà vérifié le nom de domaine personnalisé que vous avez configuré comme décrit dans le document [Vérification de l’état du nom de domaine](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md).

#### Enregistrement CNAME {#adobe-managed-cert-cname-record}

Un enregistrement de nom canonique ou CNAME est un type d’enregistrement DNS qui mappe un nom d’alias à un nom de domaine réel ou canonique. Les enregistrements CNAME sont généralement utilisés pour mapper un sous-domaine tel que `www.example.com` au domaine hébergeant le contenu de ce sous-domaine.

Connectez-vous à votre fournisseur de services DNS et créez un enregistrement `CNAME` pour pointer votre nom de domaine personnalisé vers la cible, comme dans le tableau suivant.

| CNAME | Point d’entrée de domaine personnalisé à cibler |
| --- | --- |
| `www.customdomain.com` | `cdn.adobeaemcloud.com` |

#### enregistrement APEX {#adobe-managed-cert-apex-record}

Un domaine apex est un domaine personnalisé qui ne contient pas de sous-domaine, tel que `example.com`. Un domaine apex est configuré avec un enregistrement `A`, `ALIAS` ou `ANAME` via votre fournisseur DNS. Des domaines apex doivent pointer vers des adresses IP spécifiques.

Ajoutez les enregistrements `A` suivants aux paramètres DNS de votre domaine par l’intermédiaire de votre fournisseur de domaine.

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`


### Étapes du certificat géré par le client {#customer-managed-cert-steps}

Si vous avez sélectionné le type de certificat *Client managed certificate*, exécutez les étapes suivantes dans la boîte de dialogue **Vérifier le domaine** .

![ Étapes du certificat géré par le client](/help/implementing/cloud-manager/assets/cdn/cdn-create-customer-cert.png)

Pour vérifier le domaine utilisé, vous devez ajouter et vérifier un enregistrement TXT.

Un enregistrement texte (également appelé enregistrement TXT) est un type d’enregistrement de ressource dans le système de noms de domaine (DNS). Il vous permet d’associer du texte arbitraire à un nom d’hôte. Ce texte peut inclure des détails lisibles par l’utilisateur comme des informations sur le serveur ou le réseau.

Cloud Manager utilise un enregistrement TXT spécifique pour autoriser l’hébergement d’un domaine dans un service CDN. Créez un enregistrement TXT DNS dans la zone qui autorise Cloud Manager à déployer le service CDN avec le domaine personnalisé et à l’associer au service principal. Cette association reste entièrement sous votre contrôle et permet à Cloud Manager de diffuser du contenu du service vers un domaine. Cette autorisation peut être accordée et retirée. L’enregistrement TXT est spécifique au domaine et à l’environnement Cloud Manager.

#### Conditions requises {#customer-managed-cert-requirements}

Renseignez ces exigences avant d’ajouter un enregistrement TXT.

* Identifiez l’hôte ou le serveur d’enregistrement de votre domaine si vous ne le connaissez pas déjà.
* Vous pouvez modifier les enregistrements DNS pour le domaine de votre entreprise ou contacter la personne appropriée qui peut le faire.
* Tout d’abord, ajoutez un nom de domaine personnalisé comme décrit précédemment dans cet article.

#### Ajout d’un enregistrement TXT à des fins de vérification {#customer-managed-cert-verification}

1. Dans la boîte de dialogue **Vérifier le domaine**, Cloud Manager affiche le nom et la valeur TXT à utiliser pour la vérification. Copiez cette valeur.

1. Connectez-vous à votre fournisseur de services DNS et recherchez la section enregistrements DNS .

1. Ajoutez `aemverification.[yourdomainname]` comme **Nom** de la valeur et ajoutez la valeur TXT exactement comme elle apparaît dans le champ **Nom de domaine**.

   **Exemples d’enregistrements TXT**

   | Domaine | Nom | Valeur TXT |
   | --- | --- | --- |
   | `example.com` | `_aemverification.example.com` | Copiez la valeur entière affichée dans l’interface utilisateur de Cloud Manager. Cette valeur est spécifique au domaine et à l’environnement. Par exemple :<br>`adobe-aem-verification=example.com/[program]/[env]/..*` |
   | `www.example.com` | `_aemverification.www.example.com` | Copiez la valeur entière affichée dans l’interface utilisateur de Cloud Manager. Cette valeur est spécifique au domaine et à l’environnement. Par exemple :<br>`adobe-aem-verification=www.example.com/[program]/[env]/..*` |

1. Enregistrez l’enregistrement TXT sur l’hôte de votre domaine.

#### Vérification de l’enregistrement TXT {#customer-managed-cert-verify}

Une fois que vous avez terminé, vous pouvez vérifier le résultat en exécutant la commande suivante.

```shell
dig _aemverification.[yourdomainname] -t txt
```

Le résultat attendu doit afficher la valeur TXT fournie dans l’onglet **Verification** de la boîte de dialogue **Add Domain Name** de l’interface utilisateur de Cloud Manager.

Par exemple, si votre domaine est `example.com`, exécutez :

```shell
dig TXT _aemverification.example.com -t txt
```

>[!TIP]
>
>Plusieurs [outils de recherche DNS](https://www.ultratools.com/tools/dnsLookup) sont disponibles. Google DoH peut être utilisé pour rechercher des entrées d’enregistrement TXT et déterminer si l’enregistrement TXT est manquant ou erroné.

>[!NOTE]
>
>La vérification DNS peut prendre quelques heures en raison des délais de propagation du DNS.
>
>Cloud Manager vérifie la propriété et met à jour l’état, qui est visible dans le tableau Paramètres de domaine . Voir [Vérification de l’état du nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) pour plus d’informations.

<!--
## Next Steps {#next-steps}

Now that you created your TXT entry, you can verify your domain name status. Proceed to the document [Checking Domain Name Status](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) to continue setting up your custom domain name. -->

>[!TIP]
>
>L&#39;entrée TXT et le CNAME ou un enregistrement A peuvent être définis simultanément sur le serveur DNS qui gouverne, ce qui permet de gagner du temps.
>
><!-- To do this, review the entire process of setting up a custom domain name as detailed in the document [Introduction to custom domain names](/help/implementing/cloud-manager/custom-domain-names/introduction.md) taking special note of the document [help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) and update your DNS settings appropriately. -->


## Ajout d’un nom de domaine personnalisé à partir de la page Environnements {#adding-cdn-environments}

<!-- I DON'T SEE THIS ABILITY ANYMORE IN THE UI -->

Les étapes pour ajouter un nom de domaine personnalisé à partir de la page **Environments** sont les mêmes que lorsque [l’ajout d’un nom de domaine personnalisé à partir de la page Paramètres du domaine](#adding-cdn-settings), mais le point d’entrée diffère. Procédez comme suit pour ajouter un nom de domaine personnalisé à partir de la page **Environnements**.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à la page de détails **Environments Detail** pour l’environnement intéressant.

   ![Saisie d’un nom de domaine sur la page Détails de l’environnement](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. Utilisez le tableau **Noms de domaine** pour envoyer le nom de domaine personnalisé.

   1. Entrez le nom de domaine personnalisé.
   1. Sélectionnez le certificat SSL associé à ce nom dans la liste déroulante.
   1. Cliquez sur **+Ajouter**.

   ![Ajouter un nom de domaine personnalisé](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. La boîte de dialogue **Ajouter le nom de domaine** s’ouvre sur l’onglet **Nom de domaine**. Continuez comme vous le feriez pour [ajouter un nom de domaine personnalisé à partir de la page Paramètres du domaine](#adding-cdn-settings). —>
