---
title: Exécuter et personnaliser des analyses à la demande dans Antivirus Microsoft Defender
description: Exécuter et configurer des analyses à la demande à l’aide de PowerShell, Windows Management Instrumentation ou individuellement sur les points de terminaison avec l Sécurité Windows app.
keywords: analyse, à la demande, dos, intune, analyse instantanée
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 06/10/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: b2910f9fe1c49178b8696d1a421248156b0fc4c2
ms.sourcegitcommit: be929f79751c0c52dfa6bd98a854432a0c63faf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2021
ms.locfileid: "52925730"
---
# <a name="configure-and-run-on-demand-microsoft-defender-antivirus-scans"></a>Configurer et exécuter des analyses à la demande avec l’antivirus Microsoft Defender.

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Vous pouvez exécuter une analyse à la demande sur des points de terminaison individuels. Ces analyses démarrent immédiatement et vous pouvez définir des paramètres pour l’analyse, tels que l’emplacement ou le type. Lorsque vous exécutez une analyse, vous pouvez choisir parmi trois types : analyse rapide, analyse complète et analyse personnalisée. Dans la plupart des cas, utilisez une analyse rapide. Une analyse rapide examine tous les emplacements où des programmes malveillants peuvent être enregistrés pour démarrer avec le système, tels que les clés de Registre et les dossiers de démarrage Windows connus. 

Combinée à une protection toujours en temps réel, qui examine les fichiers lorsqu’ils sont ouverts et fermés, et chaque fois qu’un utilisateur navigue vers un dossier, une analyse rapide permet de fournir une protection forte contre les programmes malveillants qui commencent par le système et les programmes malveillants au niveau du noyau. Dans la plupart des cas, une analyse rapide est suffisante et constitue l’option recommandée pour les analyses programmées ou à la demande.  [En savoir plus sur les types d’analyse.](schedule-antivirus-scans.md#quick-scan-full-scan-and-custom-scan)

> [!IMPORTANT]
> Antivirus Microsoft Defender s’exécute dans le contexte du [compte LocalSystem](/windows/win32/services/localsystem-account) lors de l’analyse locale. Pour les analyses réseau, il utilise le contexte du compte d’appareil. Si le compte d’appareil de domaine ne peut pas accéder au partage, l’analyse ne fonctionne pas. Assurez-vous que l’appareil dispose d’autorisations sur le partage réseau d’accès.

## <a name="use-microsoft-endpoint-manager-to-run-a-scan"></a>Utiliser Microsoft Endpoint Manager pour exécuter une analyse

1. Go to the Microsoft Endpoint Manager admin center ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ) and log in.

2. Choisissez **l’Antivirus de sécurité des points de**  >  **terminaison.**

3. Dans la liste des onglets, sélectionnez Windows 10 points de **terminaison défectueux.**

4. Dans la liste des actions fournies, sélectionnez **Analyse rapide** (recommandée) ou **Analyse complète.**

[![IMAGE ](images/mem-antivirus-scan-on-demand.png)](images/mem-antivirus-scan-on-demand.png#lightbox)

> [!TIP]
> Pour plus d’informations sur l’utilisation Microsoft Endpoint Manager pour exécuter une analyse, voir [Tâches anti-programme](/configmgr/protect/deploy-use/endpoint-antimalware-firewall#how-to-perform-an-on-demand-scan-of-computers)malveillant et pare-feu : Comment effectuer une analyse à la demande .

## <a name="use-the-mpcmdrunexe-command-line-utility-to-run-a-scan"></a>Utiliser lmpcmdrun.exe de ligne de commande pour exécuter une analyse

Utilisez le paramètre `-scan` suivant :

```console
mpcmdrun.exe -scan -scantype 1
```

Pour plus d’informations sur l’utilisation de l’outil et des paramètres supplémentaires, notamment le démarrage d’une analyse complète ou la définition des chemins d’accès, voir Utiliser l’outil de ligne de commande mpcmdrun.exe pour configurer et gérer [Antivirus Microsoft Defender](command-line-arguments-microsoft-defender-antivirus.md).

## <a name="use-microsoft-intune-to-run-a-scan"></a>Utiliser Microsoft Intune pour exécuter une analyse

1. Go to the Microsoft Endpoint Manager admin center ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ) and log in.

2. Dans la barre latérale, sélectionnez **Appareils**  >  **tous les appareils** et choisissez l’appareil que vous souhaitez analyser.

3. Sélectionnez **... Plus**. Dans les options, sélectionnez **Analyse rapide** (recommandé) ou **Analyse complète.**

## <a name="use-the-windows-security-app-to-run-a-scan"></a>Utiliser l’application Sécurité Windows pour exécuter une analyse

Voir [Exécuter une analyse dans l’application Sécurité Windows pour](microsoft-defender-security-center-antivirus.md) obtenir des instructions sur l’exécution d’une analyse sur des points de terminaison individuels.

## <a name="use-powershell-cmdlets-to-run-a-scan"></a>Utiliser les cmdlets PowerShell pour exécuter une analyse

Utilisez la cmdlet suivante :

```PowerShell
Start-MpScan
```

Pour plus d’informations sur l’utilisation de PowerShell avec Antivirus Microsoft Defender, voir Utiliser les [cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) pour configurer et exécuter des [cmdlets](/powershell/module/defender/)Antivirus Microsoft Defender et Defender.

## <a name="use-windows-management-instruction-wmi-to-run-a-scan"></a>Utiliser Windows Management Instruction (WMI) pour exécuter une analyse

Utilisez la [ **méthode Start** de](/previous-versions/windows/desktop/defender/start-msft-mpscan) la **MSFT_MpScan** classe.

Pour plus d’informations sur les paramètres autorisés, voir [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

