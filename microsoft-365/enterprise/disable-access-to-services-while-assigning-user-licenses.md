---
title: Désactiver l’accès aux services Microsoft 365 lors de l’affectation de licences utilisateur
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/24/2020
audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: Découvrez comment attribuer des licences à des comptes d’utilisateur et désactiver des plans de service spécifiques en même temps à l’aide de PowerShell pour Microsoft 365.
ms.openlocfilehash: b027c805638284a78d4e49f4c65518be02e60392
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "46689838"
---
# <a name="disable-access-to-microsoft-365-services-while-assigning-user-licenses"></a><span data-ttu-id="fbd33-103">Désactiver l’accès aux services Microsoft 365 lors de l’affectation de licences utilisateur</span><span class="sxs-lookup"><span data-stu-id="fbd33-103">Disable access to Microsoft 365 services while assigning user licenses</span></span>

<span data-ttu-id="fbd33-104">*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*</span><span class="sxs-lookup"><span data-stu-id="fbd33-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="fbd33-105">Les abonnements Microsoft 365 sont accompagnés de plans de service pour des services individuels.</span><span class="sxs-lookup"><span data-stu-id="fbd33-105">Microsoft 365 subscriptions come with service plans for individual services.</span></span> <span data-ttu-id="fbd33-106">Les administrateurs de Microsoft 365 doivent souvent désactiver certains plans lors de l’attribution de licences aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="fbd33-106">Microsoft 365 administrators often need to disable certain plans when assigning licenses to users.</span></span> <span data-ttu-id="fbd33-107">Avec les instructions de cet article, vous pouvez attribuer une licence Microsoft 365 et désactiver des plans de service spécifiques à l’aide de PowerShell pour un compte d’utilisateur individuel ou plusieurs comptes d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="fbd33-107">With the instructions in this article, you can assign a Microsoft 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="fbd33-108">Utilisation du module Azure Active Directory PowerShell pour Graph</span><span class="sxs-lookup"><span data-stu-id="fbd33-108">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="fbd33-109">Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="fbd33-109">First, [connect to your Microsoft 365 tenant](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="fbd33-110">Ensuite, répertoriez les plans de licence pour votre client à l’aide de cette commande.</span><span class="sxs-lookup"><span data-stu-id="fbd33-110">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="fbd33-111">Ensuite, obtenez le nom de connexion du compte auquel vous souhaitez ajouter une licence, également appelé nom d’utilisateur principal (UPN).</span><span class="sxs-lookup"><span data-stu-id="fbd33-111">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="fbd33-112">Ensuite, compilez une liste de services à activer.</span><span class="sxs-lookup"><span data-stu-id="fbd33-112">Next, compile a list of services to enable.</span></span> <span data-ttu-id="fbd33-113">Pour obtenir la liste complète des plans de licence (également appelés noms de produits), de leurs plans de service inclus et de leurs noms conviviaux correspondants, consultez la rubrique [noms de produits et identificateurs de plan de service pour la gestion des licences](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="fbd33-113">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="fbd33-114">Pour le bloc de commande ci-dessous, renseignez le nom d’utilisateur principal du compte d’utilisateur, le numéro de référence SKU et la liste des plans de service pour activer et supprimer le texte explicatif et les \< and > caractères.</span><span class="sxs-lookup"><span data-stu-id="fbd33-114">For the command block below, fill in the user principal name of the user account, the SKU part number, and the list of service plans to enable and remove the explanatory text and the \< and > characters.</span></span> <span data-ttu-id="fbd33-115">Ensuite, exécutez les commandes qui en résultent à l’invite de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fbd33-115">Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$userUPN="<user account UPN>"
$skuPart="<SKU part number>"
$serviceList=<double-quoted enclosed, comma-separated list of enabled services>
$user = Get-AzureADUser -ObjectID $userUPN
$skuID= (Get-AzureADSubscribedSku  | Where {$_.SkuPartNumber -eq $skuPart}).SkuID
$SkuFeaturesToEnable = @($serviceList)
$StandardLicense = Get-AzureADSubscribedSku | Where {$_.SkuId -eq $skuID}
$SkuFeaturesToDisable = $StandardLicense.ServicePlans | ForEach-Object { $_ | Where {$_.ServicePlanName -notin $SkuFeaturesToEnable }}
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = $StandardLicense.SkuId
$License.DisabledPlans = $SkuFeaturesToDisable.ServicePlanId
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $user.ObjectId -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="fbd33-116">Utilisez le module Microsoft Azure Active Directory pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fbd33-116">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="fbd33-117">Tout d’abord, [Connectez-vous à votre client Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="fbd33-117">First, [connect to your Microsoft 365 tenant](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="fbd33-118">Ensuite, exécutez la commande suivante pour afficher vos abonnements en cours :</span><span class="sxs-lookup"><span data-stu-id="fbd33-118">Next, run this command to see your current subscriptions:</span></span>
  
```powershell
Get-MsolAccountSku
```

>[!Note]
><span data-ttu-id="fbd33-119">PowerShell Core ne prend pas en charge le module Microsoft Azure Active Directory pour Windows PowerShell et les applets de commande incluant **Msol** dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="fbd33-119">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="fbd33-120">Pour continuer à utiliser ces applets de commande, vous devez les exécuter à partir de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fbd33-120">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="fbd33-121">Dans l'affichage de la commande  `Get-MsolAccountSku` :</span><span class="sxs-lookup"><span data-stu-id="fbd33-121">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="fbd33-122">**AccountSkuId** est un abonnement pour votre organisation dans \<OrganizationName> : \<Subscription> format.</span><span class="sxs-lookup"><span data-stu-id="fbd33-122">**AccountSkuId** is a subscription for your organization in \<OrganizationName>:\<Subscription> format.</span></span> <span data-ttu-id="fbd33-123">Le \<OrganizationName> est la valeur que vous avez fournie lorsque vous êtes inscrit à Microsoft 365 et qui est unique pour votre organisation.</span><span class="sxs-lookup"><span data-stu-id="fbd33-123">The \<OrganizationName> is the value that you provided when you enrolled in Microsoft 365, and is unique for your organization.</span></span> <span data-ttu-id="fbd33-124">La \<Subscription> valeur est pour un abonnement spécifique.</span><span class="sxs-lookup"><span data-stu-id="fbd33-124">The \<Subscription> value is for a specific subscription.</span></span> <span data-ttu-id="fbd33-125">Par exemple, pour litwareinc:ENTERPRISEPACK, le nom de l’organisation est litwareinc, et le nom de l’abonnement est ENTERPRISEPACK (Office 365 Entreprise E3).</span><span class="sxs-lookup"><span data-stu-id="fbd33-125">For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="fbd33-126">**ActiveUnits** représente le nombre de licences que vous avez achetées pour l'abonnement.</span><span class="sxs-lookup"><span data-stu-id="fbd33-126">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="fbd33-127">**WarningUnits** représente le nombre de licences dans un abonnement que vous n'avez pas renouvelées et qui expireront après la période de grâce de 30 jours.</span><span class="sxs-lookup"><span data-stu-id="fbd33-127">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="fbd33-128">**ConsumedUnits** représente le nombre de licences que vous avez affectées à des utilisateurs de l'abonnement.</span><span class="sxs-lookup"><span data-stu-id="fbd33-128">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="fbd33-129">Notez le AccountSkuId pour votre abonnement Microsoft 365 qui contient les utilisateurs auxquels vous souhaitez accorder une licence.</span><span class="sxs-lookup"><span data-stu-id="fbd33-129">Note the AccountSkuId for your Microsoft 365 subscription that contains the users you want to license.</span></span> <span data-ttu-id="fbd33-130">Assurez-vous également qu’il y a suffisamment de licences à affecter (soustraire **ConsumedUnits** de **ActiveUnits** ).</span><span class="sxs-lookup"><span data-stu-id="fbd33-130">Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="fbd33-131">Ensuite, exécutez cette commande pour afficher les détails sur les plans de service Microsoft 365 disponibles dans tous vos abonnements :</span><span class="sxs-lookup"><span data-stu-id="fbd33-131">Next, run this command to see the details about the Microsoft 365 service plans that are available in all your subscriptions:</span></span>
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="fbd33-132">À partir de l’affichage de cette commande, déterminez les plans de service que vous souhaitez désactiver lorsque vous attribuez des licences aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="fbd33-132">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="fbd33-133">Voici une liste partielle des plans de service et de leurs services Microsoft 365 correspondants.</span><span class="sxs-lookup"><span data-stu-id="fbd33-133">Here is a partial list of service plans and their corresponding Microsoft 365 services.</span></span>

<span data-ttu-id="fbd33-134">Le tableau suivant présente les plans de service Microsoft 365 et leurs noms conviviaux pour les services les plus courants.</span><span class="sxs-lookup"><span data-stu-id="fbd33-134">The following table shows the Microsoft 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="fbd33-135">La liste de vos plans de services peut être différente.</span><span class="sxs-lookup"><span data-stu-id="fbd33-135">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="fbd33-136">**Plan de services**</span><span class="sxs-lookup"><span data-stu-id="fbd33-136">**Service plan**</span></span>|<span data-ttu-id="fbd33-137">**Description**</span><span class="sxs-lookup"><span data-stu-id="fbd33-137">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="fbd33-138">Sway</span><span class="sxs-lookup"><span data-stu-id="fbd33-138">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="fbd33-139">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="fbd33-139">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="fbd33-140">Yammer</span><span class="sxs-lookup"><span data-stu-id="fbd33-140">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="fbd33-141">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="fbd33-141">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="fbd33-142">Applications Microsoft 365 pour les entreprises *(précédemment nommé Office 365 ProPlus)*</span><span class="sxs-lookup"><span data-stu-id="fbd33-142">Microsoft 365 Apps for enterprise *(previously named Office 365 ProPlus)*</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="fbd33-143">Skype Entreprise Online</span><span class="sxs-lookup"><span data-stu-id="fbd33-143">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="fbd33-144">Office</span><span class="sxs-lookup"><span data-stu-id="fbd33-144">Office</span></span>   <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="fbd33-145">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="fbd33-145">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="fbd33-146">Exchange Online (plan 2)</span><span class="sxs-lookup"><span data-stu-id="fbd33-146">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="fbd33-147">Pour obtenir la liste complète des plans de licence (également appelés noms de produits), de leurs plans de service inclus et de leurs noms conviviaux correspondants, consultez la rubrique [noms de produits et identificateurs de plan de service pour la gestion des licences](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="fbd33-147">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>
   
<span data-ttu-id="fbd33-148">Maintenant que vous avez le paramètre AccountSkuId et les plans de service à désactiver, vous pouvez attribuer des licences pour un utilisateur ou plusieurs utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="fbd33-148">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
### <a name="for-a-single-user"></a><span data-ttu-id="fbd33-149">Pour un utilisateur unique</span><span class="sxs-lookup"><span data-stu-id="fbd33-149">For a single user</span></span>

<span data-ttu-id="fbd33-150">Pour un seul utilisateur, renseignez le nom d’utilisateur principal du compte d’utilisateur, le AccountSkuId et la liste des plans de service à désactiver et supprimez le texte explicatif et les \< and > caractères.</span><span class="sxs-lookup"><span data-stu-id="fbd33-150">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the \< and > characters.</span></span> <span data-ttu-id="fbd33-151">Ensuite, exécutez les commandes qui en résultent à l’invite de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fbd33-151">Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

<span data-ttu-id="fbd33-152">Voici un exemple de bloc de commande pour le compte nommé belindan@contoso.com, pour la licence contoso:ENTERPRISEPACK, et les plans de service à désactiver sont RMS_S_ENTERPRISE, SWAY, INTUNE_O365 et YAMMER_ENTERPRISE :</span><span class="sxs-lookup"><span data-stu-id="fbd33-152">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
```powershell
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

### <a name="for-multiple-users"></a><span data-ttu-id="fbd33-153">Pour plusieurs utilisateurs</span><span class="sxs-lookup"><span data-stu-id="fbd33-153">For multiple users</span></span>

<span data-ttu-id="fbd33-p109">Pour effectuer cette tâche d'administration pour plusieurs utilisateurs, créez un fichier texte de valeurs séparées par des virgules (CSV) qui contient les champs UserPrincipalName et UsageLocation. Voici un exemple :</span><span class="sxs-lookup"><span data-stu-id="fbd33-p109">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields. Here is an example:</span></span>
  
```powershell
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="fbd33-156">Ensuite, remplissez l’emplacement des fichiers CSV d’entrée et de sortie, l’ID de référence du compte et la liste des plans de service à désactiver, puis exécutez les commandes qui en résultent à l’invite de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fbd33-156">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

<span data-ttu-id="fbd33-157">Ce bloc de commande PowerShell :</span><span class="sxs-lookup"><span data-stu-id="fbd33-157">This PowerShell command block:</span></span>
  
- <span data-ttu-id="fbd33-158">affiche le nom d’utilisateur principal de chaque utilisateur ;</span><span class="sxs-lookup"><span data-stu-id="fbd33-158">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="fbd33-159">attribue des licences personnalisées à chaque utilisateur ;</span><span class="sxs-lookup"><span data-stu-id="fbd33-159">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="fbd33-160">crée un fichier CSV avec tous les utilisateurs qui ont été traités et affiche l’état de leur licence.</span><span class="sxs-lookup"><span data-stu-id="fbd33-160">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="fbd33-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbd33-161">See also</span></span>

[<span data-ttu-id="fbd33-162">Désactiver l’accès aux services Microsoft 365 avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="fbd33-162">Disable access to Microsoft 365 services with PowerShell</span></span>](disable-access-to-services-with-microsoft-365-powershell.md)
  
[<span data-ttu-id="fbd33-163">Désactiver l’accès à Sway avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="fbd33-163">Disable access to Sway with PowerShell</span></span>](disable-access-to-sway-with-microsoft-365-powershell.md)
  
[<span data-ttu-id="fbd33-164">Gérer les comptes d’utilisateurs, les licences et les groupes Microsoft 365 avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="fbd33-164">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[<span data-ttu-id="fbd33-165">Gestion de Microsoft 365 à l’aide de PowerShell</span><span class="sxs-lookup"><span data-stu-id="fbd33-165">Manage Microsoft 365 with PowerShell</span></span>](manage-microsoft-365-with-microsoft-365-powershell.md)