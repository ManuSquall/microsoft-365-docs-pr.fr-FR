---
title: Activer la fonctionnalité d'analyse périodique limitée de l'Antivirus Microsoft Defender
description: L'analyse périodique limitée vous permet d'utiliser l'Antivirus Microsoft Defender en plus de vos autres fournisseurs antivirus installés.
keywords: lps, limité, périodique, analyse, analyse, compatibilité, tiers, autre antivirus, désactiver
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 64b65363ff53773f73cbbdc33b05a0a1beaf7f92
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51690602"
---
# <a name="use-limited-periodic-scanning-in-microsoft-defender-antivirus"></a>Utiliser une analyse périodique limitée dans l'Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

L'analyse périodique limitée est un type spécial de détection et de correction des menaces qui peut être activé lorsque vous avez installé un autre produit antivirus sur un appareil Windows 10.

Il ne peut être activé que dans certaines situations. Pour plus d'informations sur l'analyse périodique limitée et le fonctionnement de l'Antivirus Microsoft Defender avec d'autres produits antivirus, voir Compatibilité de [l'Antivirus Microsoft Defender.](microsoft-defender-antivirus-compatibility.md)

**Microsoft ne recommande pas l'utilisation de cette fonctionnalité dans les environnements d'entreprise. Il s'agit d'une fonctionnalité principalement destinée aux consommateurs.** Cette fonctionnalité utilise uniquement un sous-ensemble limité des fonctionnalités de l'Antivirus Microsoft Defender pour détecter les programmes malveillants et ne peut pas détecter la plupart des programmes malveillants et des logiciels potentiellement indésirables. En outre, les fonctionnalités de gestion et de rapport seront limitées. Microsoft recommande aux entreprises de choisir leur solution antivirus principale et de l'utiliser exclusivement.

## <a name="how-to-enable-limited-periodic-scanning"></a>Comment activer l'analyse périodique limitée

Par défaut, l'Antivirus Microsoft Defender s'active sur un appareil Windows 10 si aucun autre produit antivirus n'est installé, ou si l'autre produit est périmé, a expiré ou ne fonctionne pas correctement.

Si l'Antivirus Microsoft Defender est activé, les options habituelles s'affichent pour le configurer sur cet appareil :

![Application sécurité Windows affichant les options de Microsoft Defender AV, y compris les options d'analyse, les paramètres et les options de mise à jour](images/vtp-wdav.png)

Si un autre produit antivirus est installé et fonctionne correctement, l'Antivirus Microsoft Defender se désactive lui-même. L'application Sécurité Windows modifie la section Protection contre les virus **&** contre les menaces pour afficher l'état du produit antivirus et fournit un lien vers les options de configuration du produit.

Sous les produits antivirus tiers, un nouveau lien s'affiche en tant qu'options de **l'Antivirus Microsoft Defender.** Cliquez sur ce lien pour afficher le bouton bascule qui permet une analyse périodique limitée. Notez que l'option périodique limitée est un basculement permettant d'activer ou de désactiver l'analyse périodique. 

Le fait de faire glisser le commutateur sur **On** affiche les options standard de l'Antivirus Microsoft Defender sous le produit antivirus tiers. L'option d'analyse périodique limitée apparaît en bas de la page.

## <a name="related-articles"></a>Articles connexes

- [Configurer la protection comportementale, heuristique et en temps réel](configure-protection-features-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)