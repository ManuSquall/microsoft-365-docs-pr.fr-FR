---
title: Méthodes et propriétés du score
description: Récupère le score d’exposition de votre organisation, le score de sécurisation de l’appareil et le score d’exposition par groupe d’appareils
keywords: api, api de graphique, api pris en charge, score, score d’exposition, score de sécurité de l’appareil, score d’exposition par groupe d’appareils
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 89012dce4aa5b74d09f071b23f7709b4bd0bf03c
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "52771428"
---
# <a name="score-resource-type"></a>Type de ressource Score

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>Méthodes

Méthode |Type renvoyé |Description
:---|:---|:---
[Obtenir un score d'exposition](get-exposure-score.md) | [Score](score.md) | Obtenir le score d’exposition de l’organisation.
[Obtenir un score sécurisé d’appareil](get-device-secure-score.md) | [Score](score.md) | Obtenez le score de sécurité de l’appareil de l’organisation.
[Liste du score d’exposition par groupe d’appareils](get-machine-group-exposure-score.md)| [Score](score.md) | Liste des scores par groupe d’appareils.

## <a name="properties"></a>Propriétés

Propriété |  Type    |   Description
:---|:---|:---
Niveau | Double | Score actuel.
Temps | Date/heure | Date et heure à laquelle l’appel de cette API a été effectué.
RbacGroupName | String | Nom du groupe d’appareils.
