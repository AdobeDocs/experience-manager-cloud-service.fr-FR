---
title: Fenêtre HTTP Adobe AEM Target
description: 'Fenêtre HTTP Adobe AEM Target '
translation-type: tm+mt
source-git-commit: c193b38718622cd2e960a8e8833c2d295822dc33
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 100%

---


# Présentation {#introduction}

Cette page décrit les paramètres configurables présents dans la fenêtre HTTP Adobe AEM Target.

## Paramètres {#parameters}

![Fenêtre HTTP Target](assets/httpwindow.png "Fenêtre HTTP Target")

La fenêtre contient les paramètres configurables suivants :

| Paramètre | Description |
|---|---|
| URL de l’API Adobe Target | URL de l’API d’Adobe Target. |
| Activer l’URL absolue | Détermine si la partie hôte de l’URL ou l’URL complète est utilisée. Cochez la case si vous souhaitez utiliser l’URL complète. Par défaut, la case à cocher est désactivée. |
| Délai de connexion | Délai d’expiration (en millisecondes) jusqu’à ce qu’une connexion soit établie. La valeur par défaut est de 60 000 millisecondes. La valeur 0 est interprétée comme un délai d’expiration infini. |
| Dépassement de délai du socket | Délai (en millisecondes) d’attente des données ou période d’inactivité maximale entre deux paquets de données consécutifs. La valeur par défaut est de 30 000 millisecondes. |
| Expression régulière de remplacement de l’URL de recommandations Adobe Target avec jeton | Contrôle le jeton dans l’URL du point d’entrée Adobe Target qui doit être remplacé pour pointer vers l’URL de l’API de recommandations Target. |
| Remplacement de l’URL de recommandations Adobe Target avec jeton | Remplacement de l’expression régulière décrite dans le paramètre ci-dessus de façon à ce que l’URL résultante pointe vers l’API de recommandations Target. |
