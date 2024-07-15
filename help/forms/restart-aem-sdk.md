---
title: Comment redémarrer AEM SDK ?
description: Bonnes pratiques pour redémarrer AEM SDK
role: Admin, Developer, User
feature: Adaptive Forms
exl-id: 5fec2a93-1dda-4240-8690-24a6afae5c2b
source-git-commit: 62be3c6e98df9002cdfbeef50dd5475c4daa1576
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 19%

---

# Redémarrage du SDK AEM

Si vous redémarrez le SDK AEM en arrêtant les processus Java™, peut entraîner des incohérences dans l’environnement de développement AEM et une erreur se produit comme suit :

`javax.jcr.RepositoryException: Applying repoinit operation failed despite retry; set loglevel to DEBUG to see all exceptions. Last exception message was: Failed to set ACL (javax.jcr.ValueFormatException: Invalid type: 0) AclLine ALLOW {principals=[forms-xfa-writers], privileges=[jcr:modifyProperties]} restrictions=[rep:glob=[*/jcr:content/*], rep:itemNames=[xfaForm], fd:condition=[xfaForm, 1]]`

![Restart-aem-sdk-error](/help/forms/assets/restart-sdk-error.png)

## Solution

Pour redémarrer le SDK AEM, accédez à la fenêtre de commande active et appuyez sur la commande `Ctrl + C` pour redémarrer le SDK.

Il est recommandé d’utiliser la commande « Ctrl + C » pour redémarrer le SDK. Le redémarrage du SDK AEM à l’aide de méthodes alternatives, par exemple l’arrêt des processus Java™, peut entraîner des incohérences dans l’environnement de développement AEM.

## Voir également

* [Configuration de l’environnement de développement local pour AEM Forms](/help/forms/setup-local-development-environment.md)
* [Activer les composants principaux des formulaires adaptatifs](/help/forms/enable-adaptive-forms-core-components.md)
