---
title: AEM considérations de sécurité as a Cloud Service
description: En savoir plus sur les points importants liés à la sécurité lors de l’utilisation d’AEM as a Cloud Service
hidefromtoc: true
hide: true
source-git-commit: 39ffd826f5d1e9cea2e6a03a74f39c16647b45fa
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---


# AEM considérations de sécurité as a Cloud Service {#security-considerations}

## Trust Store AEM {#aem-trust-store}

Pour prendre en charge les opérations cryptographiques asymétriques, AEM stocke les certificats dans le référentiel de contenu, dans un trust-store global. Ses contenus sont publics et, par défaut, sont accessibles anonymement par tous sur les instances d’éditeur.

### Caractéristiques du Trust Store {#truststore-characteristics}

* Trust-Store se trouve sous `/etc/truststore` et se compose d’un fichier de stockage de clés Java, du mot de passe du stockage de clés et des métadonnées du référentiel. Notez que le mot de passe et le KeyStore lui-même sont chiffrés pour des raisons techniques, même si les certificats contenus sont accessibles à tous par défaut via l’API.
* Les certificats prêts à l’emploi sont utilisés uniquement pour la prise en charge HTTPS et SAML, et le magasin doit d’abord être créé manuellement.
* Les clients peuvent l’utiliser dans leur propre code par l’intermédiaire de la variable [API keystore](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/granite/keystore/KeyStoreService.html#getTrustStore-org.apache.sling.api.resource.ResourceResolver-)
* Trust-Store peut être géré via l’interface utilisateur à l’adresse **Outils** - **Sécurité** - **Trust Store** ou en accédant à *`https://serveraddress:serverport/libs/granite/security/content/truststore.html`*, comme illustré ci-dessous :

   ![Trust Store Management](/help/security/assets/global-trust-store-modified.png)

* L’accès au Trust-Store peut être restreint davantage par le contrôle d’accès au référentiel selon le cas d’utilisation.

>[!NOTE]
>
>Adobe recommande d’utiliser les contrôles d’accès par défaut pour le Trust Store, ce qui signifie qu’il reste accessible au public. Pour la configuration la plus sécurisée, vous pouvez utiliser une stratégie de refus de jcr:all pour tous.

<!--
Commenting out section for now as requested by Lars

## Anonymous Permission Hardening Package {#anonymous-permission-hardening-package}

For more information on the Anonymous Hardening Package, please see the [Security Checklist](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html#anonymous-permission-hardening-package).
-->
