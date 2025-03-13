---
title: Ajouter un nom de domaine personnalisé
description: Découvrez comment ajouter un nom de domaine personnalisé à l’aide des paramètres de domaine dans Cloud Manager.
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d35610b204cc2e06fefa93e048c16940cf1c47c
workflow-type: tm+mt
source-wordcount: '1028'
ht-degree: 17%

---


# Ajouter un nom de domaine personnalisé {#adding-custom-domain-name}

Découvrez comment ajouter un nom de domaine personnalisé à l’aide de **Paramètres de domaine** dans Cloud Manager.

## Conditions requises {#requirements}

Remplissez ces conditions avant d’ajouter un nom de domaine personnalisé dans Cloud Manager.

* Vous devez avoir ajouté un certificat de domaine SSL pour le domaine que vous souhaitez ajouter *avant* d’ajouter un nom de domaine personnalisé, comme décrit dans le document [Ajouter un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md).
* Vous devez disposer du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour ajouter un nom de domaine personnalisé dans Cloud Manager.
* Utilisez Fastly ou un autre réseau de diffusion de contenu (CDN).

>[!IMPORTANT]
>
>Si vous utilisez un réseau CDN géré par Adobe, vous devez toujours ajouter votre domaine à Cloud Manager.

## Où ajouter des noms de domaine personnalisés {#where-to-add-custom-domain-name}

Vous pouvez ajouter un nom de domaine personnalisé à partir de la page [Paramètres du domaine](#adding-cdn-settings) dans Cloud Manager.

Lors de l’ajout d’un nom de domaine personnalisé, le domaine est diffusé en utilisant le certificat valide le plus spécifique. Si plusieurs certificats possèdent le même domaine, la mise à jour la plus récente est choisie. Adobe vous recommande de gérer les certificats de sorte qu’il n’y ait pas de domaines qui se chevauchent.

Les étapes des deux méthodes décrites dans ce document sont basées sur Fastly. Si vous avez utilisé un autre réseau de diffusion de contenu (CDN), configurez votre domaine avec le CDN que vous avez choisi d’utiliser.

## Ajouter un nom de domaine personnalisé {#adding-custom-domain-name-settings}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.

1. Dans le menu latéral, sous **Services**, cliquez sur ![Icône Paramètres](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Settings_18_N.svg) **Paramètres de domaine**.

   ![Fenêtre Paramètres du domaine](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. Dans le coin supérieur droit de la page **Paramètres du domaine**, cliquez sur **Ajouter un domaine**.

1. Dans la boîte de dialogue **Ajouter un domaine**, dans le champ **Nom de domaine**, saisissez le nom de domaine personnalisé que vous utilisez.
Lors de la saisie du nom de domaine, n’incluez pas de `http://`, de `https://` ou d’espaces.

   >[!NOTE]
   >
   >Si vous avez besoin des versions `www` et `non-www` d’un domaine, vous devez les ajouter séparément. Par exemple, `example.com` et `www.example.com`.
   <!-- Marius Petria on SLACK tmp-skyline-cdn-certificates - Actually  my opinion is that this option should be explicit in UI (that was present in the initial mocks of the design but for some reason it was dropped). I think when adding a domain there should be a check mark to also add www.domain. When adding example.com Customer should be prompted with the following options: Do you also want to add www.example.com and have a redirect example.com -> www.example.com?Do you also want to add www.example.com and have a redirect www.example.com -> example.com? -->

1. Cliquez sur **Créer**.

1. Dans la boîte de dialogue **Vérifier le domaine**, dans la zone **Quel type de certificat prévoyez-vous d’utiliser avec ce domaine ?** la liste déroulante, sélectionnez l’une des options suivantes :

   | Option de type de certificat | Description |
   | --- | --- |
   | Certificat SSL géré par Adobe (DV) | Sélectionnez ce type de certificat si vous souhaitez utiliser un certificat DV (Validation de domaine). Cette option est idéale dans la plupart des cas, car elle fournit une validation de domaine de base. Adobe gère et renouvelle automatiquement le certificat. |
   | Certificat SSL géré par le client (OV/EV) | Sélectionnez ce type de certificat si vous envisagez d’utiliser un certificat SSL EV/OV pour sécuriser le domaine. Cette option offre une sécurité renforcée avec OV (validation de l’organisation) ou EV (validation étendue). Utilisez si une vérification plus stricte, des niveaux de confiance plus élevés ou un contrôle personnalisé des certificats est requis. |

1. Dans la boîte de dialogue **Vérifier le domaine**, en fonction du type de certificat que vous avez sélectionné, effectuez l’une des opérations suivantes :

   | Si vous avez sélectionné le type de certificat | Description |
   | --- | ---  |
   | Certificat géré par Adobe | a. Effectuez les [étapes de certificat géré par Adobe](#adobe-managed-cert-steps) ci-dessous. Une fois les étapes terminées, dans la boîte de dialogue **Vérifier le domaine**, cliquez sur **Vérifier**.<ul><li>La vérification DNS peut prendre quelques heures en raison des délais de propagation du DNS.</li><li>Cloud Manager vérifie finalement la propriété du nom de domaine et met à jour le statut dans le tableau **Paramètres du domaine**. Voir [Vérification du statut du nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) pour plus d’informations.</li>![Vérification du statut du domaine](/help/implementing/cloud-manager/assets/domain-settings-verified.png)</li></ul>b. Vous êtes maintenant prêt à [ajouter un certificat SSL géré par Adobe (DV)](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#add-adobe-managed-ssl-cert).</li></ul> |
   | Certificat géré par le client ou la cliente | a. Cliquez sur **OK**.<br>b. Vous êtes maintenant prêt à [ajouter un certificat SSL géré par le client (OV/EV)](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#add-customer-managed-ssl-cert).<br>Après avoir ajouté le certificat, votre nom de domaine est marqué comme vérifié dans le tableau **Paramètres du domaine**. Voir [Vérification du statut du nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) pour plus d’informations.</li></ul><br>![Vérification du domaine pour un certificat EV/OV géré par un client ou une cliente](/help/implementing/cloud-manager/assets/verify-domain-customer-managed-step.png) |

   >[!NOTE]
   >
   >Si vous utilisez votre propre certificat SSL géré par le client (OV/EV ou DV), vous n’avez pas besoin d’ajouter de certificat SSL. Cette règle s’applique également si vous prévoyez d’utiliser un ***fournisseur*** de réseau de diffusion de contenu (CDN) géré par le client. Au lieu de cela, accédez directement à [ Ajouter une configuration de réseau CDN ](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md) lorsque vous êtes prêt(e).


### étapes de certificat géré par Adobe {#adobe-managed-cert-steps}

Si vous avez sélectionné le type de certificat *certificat géré par Adobe*, effectuez l’étape suivante dans la boîte de dialogue **Vérifier le domaine**.

![étapes de certificat géré par Adobe](/help/implementing/cloud-manager/assets/cdn/cdn-create-adobe-dv-cert.png)

Pour vérifier le domaine utilisé, vous devez ajouter et vérifier un CNAME.

Un type d’enregistrement `CNAME` ou `A`, une fois configuré, achemine tout le trafic Internet pour le domaine vers l’endroit où il pointe. Si cet emplacement n’est pas configuré pour desservir le trafic, il y a une panne. S’il n’a pas été testé, il se peut que le contenu présente des erreurs. C’est pourquoi cette étape est toujours effectuée une fois le test terminé et que vous êtes prêt à passer en ligne.

Pour configurer ces paramètres, déterminez si un enregistrement `CNAME` ou apex doit être configuré pour pointer votre nom de domaine personnalisé vers le nom de domaine Cloud Manager. Les sections suivantes de ce document peuvent vous aider à déterminer le type d’enregistrement approprié à votre configuration DNS.

>[!NOTE]
>
>Pour les réseaux de diffusion de contenu gérés par Adobe, lors de l’utilisation de certificats DV (Validation de domaine), seuls les sites avec validation ACME sont autorisés.

#### Conditions requises {#adobe-managed-cert-dv-requirements}

Remplissez ces conditions avant de configurer vos enregistrements DNS.

* Identifiez l’hôte ou le serveur d’enregistrement de votre domaine si vous ne le connaissez pas déjà.
* Être en mesure de modifier les enregistrements DNS du domaine de votre organisation ou contacter la personne appropriée qui peut le faire.
* Vous devez avoir déjà vérifié votre nom de domaine personnalisé configuré comme décrit dans le document [Vérification du statut du nom de domaine](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md).

#### Enregistrement CNAME {#adobe-managed-cert-cname-record}

Un enregistrement de nom canonique ou CNAME est un type d’enregistrement DNS qui mappe un nom d’alias à un nom de domaine réel ou canonique. Les enregistrements CNAME sont généralement utilisés pour mapper un sous-domaine tel que `www.example.com` au domaine hébergeant le contenu de ce sous-domaine.

Connectez-vous à votre fournisseur de services DNS et créez un enregistrement `CNAME` pour pointer votre nom de domaine personnalisé vers la cible, comme dans le tableau suivant.

| CNAME | Point d’entrée du domaine personnalisé vers la cible |
| --- | --- |
| `www.customdomain.com` | `cdn.adobeaemcloud.com` |

#### Enregistrement APEX {#adobe-managed-cert-apex-record}

Un domaine apex est un domaine personnalisé qui ne contient pas de sous-domaine, tel que `example.com`. Un domaine apex est configuré avec un enregistrement `A`, `ALIAS` ou `ANAME` via votre fournisseur DNS. Des domaines apex doivent pointer vers des adresses IP spécifiques.

Ajoutez les enregistrements `A` suivants aux paramètres DNS de votre domaine par le biais de votre fournisseur de domaine.

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`

>[!TIP]
>
>L’enregistrement *CNAME* ou *A* peut être défini sur le serveur DNS principal pour vous faire gagner du temps.

<!--
![Customer managed certificate steps](/help/implementing/cloud-manager/assets/cdn/cdn-create-customer-cert.png)

To verify the domain in use, you are required to add and verify a TXT record.

A text record (also known as a TXT record) is a type of resource record in the Domain Name System (DNS). It lets you associate arbitrary text with a hostname. This text could include human-readable details like server or network information.

Cloud Manager uses a specific TXT record to authorize a domain to be hosted in a CDN service. Create a DNS TXT record in the zone that authorizes Cloud Manager to deploy the CDN service with the custom domain and associate it with the backend service. This association is entirely under your control and authorizes Cloud Manager to serve content from the service to a domain. This authorization may be granted and withdrawn. The TXT record is specific to the domain and the Cloud Manager environment.

#### Requirements {#customer-managed-cert-requirements}

Fulfill these requirements before adding a TXT record.

* Identify your domain host or registrar if you do not know it already.
* Be able to edit the DNS records for your organization's domain, or contact the appropriate person who can.
* First, add a custom domain name as described earlier in this article.

#### Add a TXT record for verification {#customer-managed-cert-verification}

1. In the **Verify domain** dialog box, Cloud Manager displays the name and TXT value to use for verification. Copy this value.

1. Log in to your DNS service provider and find the DNS records section. 

1. Add `aemverification.[yourdomainname]` as the **Name** of the value and add the TXT value exactly as it appears in the **Domain Name** field.

   **TXT record examples**

   | Domain | Name | TXT Value |
   | --- | --- | --- |
   | `example.com` | `_aemverification.example.com` | Copy the entire value displayed in the Cloud Manager UI. This value is specific to the domain and the environment. For example:<br>`adobe-aem-verification=example.com/[program]/[env]/..*` |
   | `www.example.com` | `_aemverification.www.example.com` | Copy the entire value displayed in the Cloud Manager UI. This value is specific to the domain and the environment. For example:<br>`adobe-aem-verification=www.example.com/[program]/[env]/..*` |

1. Save the TXT record to your domain host.

#### Verify TXT record {#customer-managed-cert-verify}

When you are done, you can verify the result by running the following command.

```shell
dig _aemverification.[yourdomainname] -t txt
```

The expected result should display the TXT value provided on the **Verification** tab of the **Add Domain Name** dialog of the Cloud Manager UI.

For example, if your domain is `example.com`, then run:

```shell
dig TXT _aemverification.example.com -t txt
```


>[!TIP]
>
>There are several [DNS lookup tools](https://www.ultratools.com/tools/dnsLookup) available. Google DoH can be used to look up TXT record entries and identify if the TXT record is missing or erroneous.

-->



<!--
## Next Steps {#next-steps}

Now that you created your TXT entry, you can verify your domain name status. Proceed to the document [Checking Domain Name Status](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) to continue setting up your custom domain name. -->


><!-- The TXT entry and the CNAME or A Record can be set simultaneously on the governing DNS server, thus saving time. -->
>
><!-- To do this, review the entire process of setting up a custom domain name as detailed in the document [Introduction to custom domain names](/help/implementing/cloud-manager/custom-domain-names/introduction.md) taking special note of the document [help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) and update your DNS settings appropriately. -->


