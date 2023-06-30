---
title: Considérations relatives à la sécurité d’AEM as a Cloud Service
description: En savoir plus sur les considérations importantes relatives à la sécurité lors de l’utilisation d’AEM as a Cloud Service
hidefromtoc: true
hide: true
exl-id: d2dfde05-ce02-478e-8697-b939fb8740c3
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 93%

---

# Considérations relatives à la sécurité d’AEM as a Cloud Service {#security-considerations}

## Trust Store d’AEM {#aem-trust-store}

Pour prendre en charge les opérations cryptographiques asymétriques, AEM stocke les certificats dans le référentiel de contenu, dans un trust-store global. Ses contenus sont publics et accessibles par défaut et de façon anonyme par tous et toutes sur les instances d’éditeur.

### Caractéristiques du Trust Store {#truststore-characteristics}

* Le Trust Store se trouve sous `/etc/truststore` et se compose d’un fichier de stockage de clés Java, du mot de passe du stockage de clés et des métadonnées du référentiel. Notez que le mot de passe et le stockage de clés lui-même sont chiffrés pour des raisons techniques, même si les certificats contenus sont accessibles à tous et toutes par défaut via l’API.
* Les certificats prêts à l’emploi sont utilisés uniquement pour la prise en charge HTTPS et SAML et le magasin doit d’abord être créé manuellement.
* Les clients et clientes peuvent l’utiliser dans leur propre code par l’intermédiaire de l’[API Keystore](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/granite/keystore/KeyStoreService.html#getTrustStore-org.apache.sling.api.resource.ResourceResolver-)
* Le Trust Store peut être géré via l’interface utilisateur dans **Outils** - **Sécurité** - **Trust Store** ou en accédant à *`https://serveraddress:serverport/libs/granite/security/content/truststore.html`*, tel qu’illustré ci-dessous :

  ![Gestion du Trust Store](/help/security/assets/global-trust-store-modified.png)

* L’accès au Trust-Store peut être restreint davantage par le contrôle d’accès au référentiel selon le cas d’utilisation.

>[!NOTE]
>
>Adobe recommande d’utiliser les contrôles d’accès par défaut pour le Trust Store, c’est-à-dire de le laisser accessible au public. Pour la configuration la plus sécurisée, vous pouvez utiliser une politique de refus jcr:all pour tous et toutes.

<!--
Commenting out section for now as requested by Lars

## Anonymous Permission Hardening Package {#anonymous-permission-hardening-package}

For more information on the Anonymous Hardening Package, see [Security Checklist](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html#anonymous-permission-hardening-package).
-->
