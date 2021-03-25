---
title: Configurer les fonctionnalités de Microsoft Defender ATP pour Android
description: Décrit comment configurer Microsoft Defender ATP pour Android
keywords: microsoft, defender, atp, android, configuration
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 4325020e653f14898ece4192e03cbf8b90131136
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51163446"
---
# <a name="configure-defender-for-endpoint-for-android-features"></a>Configurer Defender pour les fonctionnalités Endpoint pour Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="conditional-access-with-defender-for-endpoint-for-android"></a>Accès conditionnel avec Defender pour point de terminaison pour Android  
Microsoft Defender pour le point de terminaison pour Android, ainsi que Microsoft Intune et Azure Active Directory permettent d’appliquer des stratégies de conformité et d’accès conditionnel aux appareils en fonction des niveaux de risque de l’appareil. Defender pour point de terminaison est une solution de défense contre les menaces mobiles que vous pouvez déployer pour tirer parti de cette fonctionnalité via Intune.

Pour plus d’informations sur la façon de configurer Defender pour endpoint pour Android et l’accès conditionnel, voir [Defender pour Endpoint et Intune.](https://docs.microsoft.com/mem/intune/protect/advanced-threat-protection)

## <a name="configure-custom-indicators"></a>Configurer des indicateurs personnalisés  

> [!NOTE]
> Defender pour le point de terminaison pour Android prend uniquement en charge la création d’indicateurs personnalisés pour les adresses IP et les URL/domaines.

Defender pour le point de terminaison pour Android permet aux administrateurs de configurer des indicateurs personnalisés pour prendre en charge également les appareils Android. Pour plus d’informations sur la configuration des indicateurs personnalisés, voir [Gérer les indicateurs.](manage-indicators.md)

## <a name="configure-web-protection"></a>Configurer la protection web
Defender pour le point de terminaison pour Android permet aux administrateurs informatiques de configurer la fonctionnalité de protection web. Cette fonctionnalité est disponible dans le Centre d’administration Microsoft Endpoint Manager.

> [!NOTE]
> Defender pour le point de terminaison pour Android utiliserait un VPN pour fournir la fonctionnalité de protection web. Il ne s’agit pas d’un VPN normal et d’un VPN local/en boucle autonome qui ne prend pas le trafic en dehors de l’appareil. Pour plus d’informations, voir [Configurer la protection web sur les appareils qui exécutent Android.](https://docs.microsoft.com/mem/intune/protect/advanced-threat-protection-manage-android)

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble de Microsoft Defender pour point de terminaison pour Android](microsoft-defender-endpoint-android.md)
- [Déployer Microsoft Defender pour endpoint pour Android avec Microsoft Intune](android-intune.md)