---
title: Exécuter et personnaliser des analyses à la demande dans Microsoft Defender AV
description: Exécuter et configurer des analyses à la demande à l'aide de PowerShell, Windows Management Instrumentation ou individuellement sur les points de terminaison avec l'application Sécurité Windows
keywords: analyse, à la demande, dos, intune, analyse instantanée
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 11/13/2020
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 2f60bdb0bbd8b87895547e608b5c3c92414ea834
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51690539"
---
# <a name="configure-and-run-on-demand-microsoft-defender-antivirus-scans"></a>Configurer et exécuter des analyses de l'Antivirus Microsoft Defender à la demande

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Vous pouvez exécuter une analyse à la demande sur des points de terminaison individuels. Ces analyses démarrent immédiatement et vous pouvez définir des paramètres pour l'analyse, tels que l'emplacement ou le type.

## <a name="quick-scan-versus-full-scan"></a>Analyse rapide et analyse complète

L'analyse rapide examine tous les emplacements où des programmes malveillants peuvent être enregistrés pour démarrer avec le système, tels que les clés de Registre et les dossiers de démarrage Windows connus.

> [!IMPORTANT]
> L'Antivirus Microsoft Defender s'exécute dans le contexte du [compte LocalSystem](/windows/win32/services/localsystem-account) lors de l'analyse locale. Pour les analyses réseau, il utilise le contexte du compte d'appareil. Si le compte d'appareil de domaine ne peut pas accéder au partage, l'analyse ne fonctionne pas. Assurez-vous que l'appareil dispose d'autorisations sur le partage réseau d'accès.

Combinée avec la fonctionnalité de [protection](configure-real-time-protection-microsoft-defender-antivirus.md)en temps réel toujours en cours (qui examine les fichiers lorsqu'ils sont ouverts et fermés, et chaque fois qu'un utilisateur navigue vers un dossier), une analyse rapide permet d'assurer une couverture solide à la fois pour les programmes malveillants qui commencent par le système et les programmes malveillants au niveau du noyau.  

Dans la plupart des cas, une analyse rapide permet de trouver des programmes malveillants qui n'ont pas été détectés par la protection en temps réel.

Une analyse complète peut être utile sur les points de terminaison qui ont signalé une menace de programmes malveillants. L'analyse peut identifier s'il existe des composants inactifs qui nécessitent un nettoyage plus approfondi. Cela est idéal si votre organisation exécute des analyses à la demande.

> [!NOTE]
> Par défaut, les analyses rapides s'exécutent sur des appareils amovibles montés, tels que des lecteurs USB.

## <a name="use-microsoft-endpoint-manager-to-run-a-scan"></a>Utiliser Microsoft Endpoint Manager pour exécuter une analyse

1. Go to the Microsoft Endpoint Manager admin center ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ) and log in.
2. Choisissez **l'Antivirus de sécurité des points de**  >  **terminaison.**
3. Dans la liste des onglets, sélectionnez les points de **terminaison Windows 10 défectueux.**
4. Dans la liste des actions fournies, sélectionnez **Analyse rapide** ou **Analyse complète.**

[![IMAGE ](images/mem-antivirus-scan-on-demand.png)](images/mem-antivirus-scan-on-demand.png#lightbox)

> [!TIP]
> Pour plus d'informations sur l'utilisation de Microsoft Endpoint Manager pour exécuter une analyse, voir [Tâches anti-programme](/configmgr/protect/deploy-use/endpoint-antimalware-firewall#how-to-perform-an-on-demand-scan-of-computers)malveillant et pare-feu : Comment effectuer une analyse à la demande .

## <a name="use-the-mpcmdrunexe-command-line-utility-to-run-a-scan"></a>Utiliser lmpcmdrun.exe de ligne de commande pour exécuter une analyse

Utilisez le paramètre `-scan` suivant :

```console
mpcmdrun.exe -scan -scantype 1
```

Pour plus d'informations sur l'utilisation de l'outil et des paramètres supplémentaires, notamment le démarrage d'une analyse complète ou la définition des chemins d'accès, voir Utiliser l'outil de ligne de commande mpcmdrun.exe pour configurer et gérer [l'Antivirus Microsoft Defender.](command-line-arguments-microsoft-defender-antivirus.md)

## <a name="use-microsoft-intune-to-run-a-scan"></a>Utiliser Microsoft Intune pour exécuter une analyse

1. Go to the Microsoft Endpoint Manager admin center ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ) and log in.
2. Dans la barre latérale, sélectionnez **Appareils > tous** les appareils et choisissez l'appareil que vous souhaitez analyser.
3. Sélectionnez **... Plus**. Dans les options, sélectionnez **Analyse rapide** ou **Analyse complète.**

## <a name="use-the-windows-security-app-to-run-a-scan"></a>Utiliser l'application Sécurité Windows pour exécuter une analyse

Voir [Exécuter une analyse dans l'application Sécurité Windows](microsoft-defender-security-center-antivirus.md) pour obtenir des instructions sur l'exécution d'une analyse sur des points de terminaison individuels.

## <a name="use-powershell-cmdlets-to-run-a-scan"></a>Utiliser les cmdlets PowerShell pour exécuter une analyse

Utilisez la cmdlet suivante :

```PowerShell
Start-MpScan
```

Pour plus d'informations sur l'utilisation de PowerShell avec l'Antivirus Microsoft Defender, voir Utiliser les [cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) pour configurer et exécuter l'Antivirus Microsoft Defender et les [cmdlets Defender.](/powershell/module/defender/)

## <a name="use-windows-management-instruction-wmi-to-run-a-scan"></a>Utiliser Windows Management Instruction (WMI) pour exécuter une analyse

Utilisez la [ **méthode Start** de](/previous-versions/windows/desktop/defender/start-msft-mpscan) la **MSFT_MpScan** classe.

Pour plus d'informations sur les paramètres autorisés, voir [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="related-articles"></a>Articles connexes

- [Configurer les options d'analyse de l'Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)
- [Configurer des analyses de l'Antivirus Microsoft Defender programmées](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)