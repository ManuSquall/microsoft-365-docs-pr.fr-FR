---
title: Activer et configurer les fonctionnalités de protection de l'Antivirus Microsoft Defender
description: Activez la protection en temps réel, heuristique et basée sur le comportement dans Microsoft Defender AV.
keywords: heuristique, machine learning, moniteur de comportement, protection en temps réel, toujours en action, Antivirus Microsoft Defender, logiciel anti-programme malveillant, sécurité, defender
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 7a0e0571445e8ec753c3813a81dbcca9c698e7df
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51690333"
---
# <a name="configure-behavioral-heuristic-and-real-time-protection"></a>Configurer la protection comportementale, heuristique et en temps réel

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

L'Antivirus Microsoft Defender utilise plusieurs méthodes pour fournir une protection contre les menaces :

- Protection cloud pour la détection et le blocage quasi instantanés des menaces nouvelles et émergentes
- Analyse toujours continue, à l'aide de la surveillance du comportement des fichiers et des processus et d'autres heuristiques (également appelée « protection en temps réel »)
- Mises à jour de la protection dédiées, fondées sur l’apprentissage automatique, l’analyse humaine et automatisée du Big Data, et des recherches approfondies sur la résistance aux menaces

Vous pouvez configurer la façon dont l'Antivirus Microsoft Defender utilise ces méthodes avec la stratégie de groupe, System Center Configuration Manage, les cmdlets PowerShell et Windows Management Instrumentation (WMI).

Cette section couvre la configuration de l'analyse toujours en ligne, notamment la détection et le blocage des applications qui sont considérées comme non sûres, mais qui peuvent ne pas être détectées comme des programmes malveillants.

Voir [Utiliser les technologies de l'Antivirus Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md) de nouvelle génération via la protection cloud pour savoir comment activer et configurer la protection de l'antivirus Microsoft Defender dans le cloud.

## <a name="in-this-section"></a>Dans cette section

 Rubrique | Description
---|---
[Détecter et bloquer les applications potentiellement indésirables](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md) | Détecter et bloquer les applications qui peuvent être indésirables sur votre réseau, telles que les logiciels publicitaires, les modificateurs de navigateur et les barres d'outils, ainsi que les applications antivirus malveillantes ou factices
[Activer et configurer les fonctionnalités de protection de l'Antivirus Microsoft Defender](configure-real-time-protection-microsoft-defender-antivirus.md) | Activer et configurer la protection en temps réel, l'heuristique et d'autres fonctionnalités de surveillance de l'Antivirus Microsoft Defender toujours actives