---
title: Affecter des stratégies Skype Entreprise Online par utilisateur avec PowerShell pour Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: 'Résumé : Utilisez PowerShell pour Microsoft 365 pour affecter des paramètres de communication par utilisateur avec Skype Entreprise online.'
ms.openlocfilehash: d7f369e96f3db95c741e6d4f2178eaf9032ab0bb
ms.sourcegitcommit: 4886457c0d4248407bddec56425dba50bb60d9c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2021
ms.locfileid: "53288082"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-powershell-for-microsoft-365"></a>Affecter des stratégies Skype Entreprise Online par utilisateur avec PowerShell pour Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

L’utilisation de PowerShell pour Microsoft 365 est un moyen efficace d’affecter des paramètres de communication par utilisateur avec des stratégies Skype Entreprise Online.
  
## <a name="prepare-to-run-the-powershell-commands"></a>Préparer l’exécuter

Suivez ces instructions pour exécuter les commandes (sautez les étapes que vous avez déjà effectuées) :
  
  > [!Note]
   > Le connecteur Skype Entreprise Online fait actuellement partie du dernier module PowerShell Teams. Si vous utilisez la version publique la plus récente de PowerShell Teams, vous n’avez pas besoin d’installer le connecteur Skype Entreprise Online.

1. Installer le [module PowerShell Teams](/microsoftteams/teams-powershell-install).
    
2. Ouvrez l’invite de commandes Windows PowerShell et exécutez les commandes suivantes : 
    
   ```powershell
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams
   ```

   Lorsque vous y êtes invité, entrez le nom utilisateur et le mot de passe de votre compte d'administrateur Skype Entreprise Online.
    
## <a name="updating-external-communication-settings-for-a-user-account"></a>Mise à jour des paramètres de communication externe d’un compte d’utilisateur

Supposons que vous souhaitiez modifier les paramètres de communication externe d’un compte d’utilisateur. Par exemple, vous souhaitez autoriser Alex à communiquer avec les utilisateurs fédérés (EnableFederationAccess est défini sur True), mais pas avec les utilisateurs Windows Live (EnablePublicCloudAccess est défini sur False). Pour cela, vous devez faire deux choses :
  
1. Trouver une stratégie d’accès externe qui réponde à nos critères.
    
2. Attribuer cette stratégie d’accès externe à Alex.
    
Comment déterminer la stratégie d’accès externe à attribuer à Alex ? La commande suivante renvoie toutes les stratégies d’accès externe où EnableFederationAccess a la valeur True et EnablePublicCloudAccess a la valeur False :
  
```powershell
Get-CsExternalAccessPolicy -Include All| Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

Sauf si vous avez créé des instances personnalisées d’ExternalAccessPolicy, cette commande renvoie une stratégie qui répond à nos critères (FederationOnly). Voici un exemple :
  
```powershell
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

Maintenant que vous savez quelle stratégie attribuer à Alex, vous pouvez le faire à l'aide de la cmdlet [Grant-CsExternalAccessPolicy](/powershell/module/skype/Get-CsExternalAccessPolicy). Voici un exemple :
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

Affecter une stratégie est la simplicité même : il vous suffit de spécifier l’identité de l’utilisateur et le nom de la stratégie à attribuer. 
  
Concernant les stratégies et leur attribution, vous n'êtes pas obligé de gérer les comptes d'utilisateur séparément. Supposons que vous ayez besoin d'une liste de tous les utilisateurs autorisés à communiquer avec les partenaires fédérés et les utilisateurs de Windows Live. Nous savons déjà que la stratégie d'accès utilisateur externe FederationAndPICDefault a été attribuée à ces utilisateurs. Sachant cela, vous pouvez afficher une liste de tous ces utilisateurs en exécutant une commande simple, que voici :
  
```powershell
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

En d'autres termes, afficher tous les utilisateurs dont la propriété ExternalAccessPolicy est définie sur FederationAndPICDefault. (En outre, afin de limiter la quantité d'informations affichées à l'écran, utilisez la cmdlet Select-Object pour n'afficher que le nom d'affichage de chaque utilisateur.) 
  
Pour configurer tous vos comptes d’utilisateur de manière à ce qu’ils utilisent la même stratégie, procédez comme suit :
  
```powershell
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

Cette commande utilise Get-CsOnlineUser pour renvoyer une collection de tous les utilisateurs qui ont été activés pour Lync, puis transmet toutes ces informations à la cmdlet Grant-CsExternalAccessPolicy, laquelle attribue la stratégie FederationAndPICDefault à chaque utilisateur de la collection.
  
Autre exemple : supposons que vous ayez déjà attribué la stratégie FederationAndPICDefault à Alex, mais que vous ayez changé d'avis et que vous souhaitiez désormais qu'il soit géré par la stratégie d'accès externe globale. Vous ne pouvez pas attribuer explicitement la stratégie globale à un utilisateur. Au lieu de cela, la stratégie globale est utilisée pour un utilisateur donné si aucune stratégie par utilisateur n’est affectée à cet utilisateur. Cela signifie que, si nous voulons qu'Alex soit géré par la stratégie globale, nous devons lui  *désattribuer*  toutes les stratégies spécifiques qui lui sont affectées. Voici un exemple de commande :
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

Cette commande définit le nom de la stratégie d'accès externe attribuée à Alex sur une valeur nulle ($Null). En d'autres termes, aucune stratégie d'accès externe n'est attribuée à Alex. Or, en l'absence de stratégie d'accès externe attribuée à un utilisateur, ce dernier est géré par la stratégie globale.

## <a name="managing-large-numbers-of-users"></a>Gestion d’un grand nombre d’utilisateurs

Pour gérer un grand nombre d’utilisateurs (1 000 ou plus), vous devez traitement par lots des commandes via un bloc de script à l’aide de la cmdlet [Invoke-Command.](/powershell/module/microsoft.powershell.core/invoke-command)  Dans les exemples précédents, chaque fois qu’une cmdlet est exécutée, elle doit configurer l’appel, puis attendre le résultat avant de le renvoyer.  Lorsque vous utilisez un bloc de script, cela permet aux cmdlets d’être exécutées à distance et, une fois terminées, de renvoyer les données.

```powershell
$users = Get-CsOnlineUser -Filter { ClientPolicy -eq $null } -ResultSize 500

$batch = 50
$filter = ''
$total = $users.Count
$count = 0
    $users | ForEach-Object {
    $upn = $_.UserPrincipalName
    $filter += "(UserPrincipalName -eq '$upn')"
    $batch--
    $count++
    if (($batch -eq 0) -or ($count -eq $total)) {
        $filterSB=[ScriptBlock]::Create($filter)
        Invoke-Command -Session $s -ScriptBlock {param($f) Get-CsOnlineUser -filter $f | Grant-CsClientPolicy -PolicyName "ClientPolicyNoIMURL" -Passthru | Grant-CsExternalAccessPolicy -PolicyName "FederationAndPICDefault"} -ArgumentList $filterSB

        # Reset
        $batch = 50
        $filter = ''
    } else {
        $filter += " -or "
    }
}
```

Cela permet de trouver 500 utilisateurs à la fois qui n’ont pas de stratégie de client. Il leur accorde la stratégie de client « ClientPolicyNoIMURL » et la stratégie d’accès externe « FederationAndPicDefault ». Les résultats sont par lots de 50 et chaque lot de 50 est ensuite envoyé à l’ordinateur distant.
  
## <a name="see-also"></a>Voir aussi

[Gestion de Skype Entreprise Online avec PowerShell](manage-skype-for-business-online-with-microsoft-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)