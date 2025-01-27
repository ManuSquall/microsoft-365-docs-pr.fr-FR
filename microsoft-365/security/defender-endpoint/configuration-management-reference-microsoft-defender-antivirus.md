---
title: Gérer Windows Defender dans votre entreprise
description: Découvrez comment utiliser la stratégie de groupe, Configuration Manager, PowerShell, WMI, Intune et la ligne de commande pour gérer Microsoft Defender AV
keywords: stratégie de groupe, gpo, gestionnaire de config, sccm, scep, powershell, wmi, intune, defender, antivirus, anti-programme malveillant, sécurité, protection
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 05/06/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.openlocfilehash: 2265f3680e425ade062d444685fbd8873eaa02ca
ms.sourcegitcommit: 51b316c23e070ab402a687f927e8fa01cb719c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2021
ms.locfileid: "52274963"
---
# <a name="manage-microsoft-defender-antivirus-in-your-business"></a>Gérer Antivirus Microsoft Defender dans votre entreprise

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Vous pouvez gérer et configurer les Antivirus Microsoft Defender à l’aide des outils suivants :

- [Microsoft Intune](/mem/intune/protect/endpoint-security-antivirus-policy) (fait désormais partie de Microsoft Endpoint Manager)
- [Microsoft Endpoint Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-protection-configure) (fait désormais partie de Microsoft Endpoint Manager)
- [Stratégie de groupe](./use-group-policy-microsoft-defender-antivirus.md)
- [Cmdlets PowerShell](./use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [WMI (Windows Management Instrumentation)](./use-wmi-microsoft-defender-antivirus.md)
- Utilitaire [de ligne de commande](./command-line-arguments-microsoft-defender-antivirus.md) microsoft de protection contre les programmes malveillants (appelé utilitaire *mpcmdrun.exe* logiciel

Les articles suivants fournissent des informations supplémentaires, des liens et des ressources pour l’utilisation de ces outils pour gérer et configurer Antivirus Microsoft Defender.

| Article | Description |
|:---|:---|
|[Gérer Antivirus Microsoft Defender avec Microsoft Intune et Microsoft Endpoint Configuration Manager](use-intune-config-manager-microsoft-defender-antivirus.md)|Informations sur l’utilisation d’Intune et de Configuration Manager pour déployer, gérer, signaler et configurer Antivirus Microsoft Defender |
|[Gérer les Antivirus Microsoft Defender avec les paramètres de stratégie de groupe](use-group-policy-microsoft-defender-antivirus.md)|Liste de tous les paramètres de stratégie de groupe situés dans les modèles ADMX |
|[Gérer Antivirus Microsoft Defender avec les cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md)|Instructions d’utilisation des cmdlets PowerShell pour gérer les Antivirus Microsoft Defender, ainsi que des liens vers la documentation pour toutes les cmdlets et paramètres autorisés |
|[Gérer Antivirus Microsoft Defender avec Windows Management Instrumentation (WMI)](use-wmi-microsoft-defender-antivirus.md)| Instructions d’utilisation de WMI pour gérer les Antivirus Microsoft Defender, ainsi que des liens vers la documentation pour les API WMIv2 (y compris toutes les classes, méthodes et propriétés) |
|[Gérer Antivirus Microsoft Defender’aide de lmpcmdrun.exe de ligne de commande](command-line-arguments-microsoft-defender-antivirus.md)|Instructions sur l’utilisation de l’outil en ligne de commande dédié pour gérer et utiliser Antivirus Microsoft Defender |