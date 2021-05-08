---
title: 'Étape 7 : supprimer le compte d’utilisateur d’un ancien employé'
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
description: Suivez ces étapes pour supprimer le compte d’utilisateur d’un ancien employé.
ms.openlocfilehash: 0afa9b112919d2668d7553ac5bcf08e664bc1749
ms.sourcegitcommit: ff20f5b4e3268c7c98a84fb1cbe7db7151596b6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "52244234"
---
# <a name="step-7---delete-a-former-employees-user-account"></a><span data-ttu-id="5fbf2-103">Étape 7 : supprimer le compte d’utilisateur d’un ancien employé</span><span class="sxs-lookup"><span data-stu-id="5fbf2-103">Step 7 - Delete a former employee's user account</span></span>

<span data-ttu-id="5fbf2-104">Une fois que vous avez enregistré et consulté les données utilisateur de l'ancien employé, vous pouvez supprimer le compte de l'ancien employé.</span><span class="sxs-lookup"><span data-stu-id="5fbf2-104">After you've saved and accessed all the former employee's user data, you can delete the former employee's account.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5fbf2-p101">Ne supprimez pas le compte si vous avez configuré le transfert de courrier ou si vous l'avez converti en boîte aux lettres partagée. Les deux ont besoin du compte pour ancrer le transfert ou la boîte aux lettres partagée.</span><span class="sxs-lookup"><span data-stu-id="5fbf2-p101">Don't delete the account if you've set up email forwarding or converted it to a shared mailbox. Both need the account to anchor the forwarding or shared mailbox.</span></span>

1. <span data-ttu-id="5fbf2-107">Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.</span><span class="sxs-lookup"><span data-stu-id="5fbf2-107">In the admin center, go to the **Users** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Active users</a> page.</span></span>
2. <span data-ttu-id="5fbf2-108">Sélectionnez le nom de l’employé à supprimer.</span><span class="sxs-lookup"><span data-stu-id="5fbf2-108">Select the name of the employee that you want to delete.</span></span>
3. <span data-ttu-id="5fbf2-109">Sous le nom de l’utilisateur, sélectionnez **Supprimer l’utilisateur.**</span><span class="sxs-lookup"><span data-stu-id="5fbf2-109">Under the user's name, select **Delete user**.</span></span> <span data-ttu-id="5fbf2-110">Choisissez les options que vous souhaitez pour cet utilisateur, puis sélectionnez **Supprimer l’utilisateur.**</span><span class="sxs-lookup"><span data-stu-id="5fbf2-110">Choose the options you want for this user, and then select **Delete user**.</span></span> <span data-ttu-id="5fbf2-111">Si vous avez déjà accordé à un autre utilisateur l’accès aux e-mails et aux OneDrive de cet utilisateur, vous n’avez pas besoin de le faire à nouveau ici.</span><span class="sxs-lookup"><span data-stu-id="5fbf2-111">If you've already given another user access to this user's email and OneDrive, you don't have to do it again here.</span></span>

<span data-ttu-id="5fbf2-p103">Lorsque vous supprimez un utilisateur, le compte devient inactif pendant 30 jours environ. Vous disposez de cette durée pour restaurer le compte avant sa suppression définitive.</span><span class="sxs-lookup"><span data-stu-id="5fbf2-p103">When you delete a user, the account becomes inactive for approximately 30 days. You have until then to restore the account before it is permanently deleted.</span></span>
  
## <a name="does-your-organization-use-active-directory"></a><span data-ttu-id="5fbf2-114">Votre organisation utilise Active Directory ?</span><span class="sxs-lookup"><span data-stu-id="5fbf2-114">Does your organization use Active Directory?</span></span>

<span data-ttu-id="5fbf2-115">Si votre organisation synchronise les comptes d’utilisateur avec Microsoft 365 à partir d’un environnement Active Directory local, vous devez supprimer et restaurer ces comptes d’utilisateurs dans votre service Active Directory local.</span><span class="sxs-lookup"><span data-stu-id="5fbf2-115">If your organization synchronizes user accounts to Microsoft 365 from a local Active Directory environment, you must delete and restore those user accounts in your local Active Directory service.</span></span> <span data-ttu-id="5fbf2-116">Vous ne pouvez pas les supprimer et les restaurer dans Office 365.</span><span class="sxs-lookup"><span data-stu-id="5fbf2-116">You can't delete or restore them in Office 365.</span></span>

<span data-ttu-id="5fbf2-117">Pour découvrir comment supprimer et restaurer un compte d’utilisateur dans Active Directory, voir [Supprimer un compte d’utilisateur.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11))</span><span class="sxs-lookup"><span data-stu-id="5fbf2-117">To learn how to delete and restore user account in Active Directory, see [Delete a User Account](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11)).</span></span>
  
<span data-ttu-id="5fbf2-118">Si vous utilisez Azure Active Directory, voir l’cmdlet [Remove-MsolUser](https://go.microsoft.com/fwlink/?linkid=842230) PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5fbf2-118">If you're using Azure Active Directory, see the [Remove-MsolUser](https://go.microsoft.com/fwlink/?linkid=842230) PowerShell cmdlet.</span></span>
  
## <a name="what-you-need-to-know-about-terminating-an-employees-email-session"></a><span data-ttu-id="5fbf2-119">Ce que vous devez savoir sur la clôture d'une session de messagerie d'un employé</span><span class="sxs-lookup"><span data-stu-id="5fbf2-119">What you need to know about terminating an employee's email session</span></span>

<span data-ttu-id="5fbf2-120">Voici les informations sur la suppression de l'accès d'un employé au courrier électronique (Exchange).</span><span class="sxs-lookup"><span data-stu-id="5fbf2-120">Here's information about how to get an employee out of email (Exchange).</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="5fbf2-121">**Ce que vous pouvez faire**</span><span class="sxs-lookup"><span data-stu-id="5fbf2-121">**What you can do**</span></span> <br/> |<span data-ttu-id="5fbf2-122">**Procédure à suivre**</span><span class="sxs-lookup"><span data-stu-id="5fbf2-122">**How you do it**</span></span> <br/> |
|<span data-ttu-id="5fbf2-123">Clôturer une session (par exemple, Outlook sur le web, Outlook, Exchange Active Sync, etc.) et forcer à ouvrir une nouvelle session</span><span class="sxs-lookup"><span data-stu-id="5fbf2-123">Terminate a session (such as Outlook on the web, Outlook, Exchange active sync, etc.) and force to open a new session</span></span>  <br/> |<span data-ttu-id="5fbf2-124">Réinitialiser le mot de passe</span><span class="sxs-lookup"><span data-stu-id="5fbf2-124">Reset password</span></span>  <br/> |
|<span data-ttu-id="5fbf2-125">Clôturer une session et bloquer les sessions suivantes (pour tous les protocoles)</span><span class="sxs-lookup"><span data-stu-id="5fbf2-125">Terminate a session and block access to future sessions (for all protocols)</span></span>  <br/> |<span data-ttu-id="5fbf2-126">Désactivez le compte.</span><span class="sxs-lookup"><span data-stu-id="5fbf2-126">Disable the account.</span></span> <span data-ttu-id="5fbf2-127">Par exemple, (dans le centre d’administration Exchange ou à l’aide de PowerShell) :</span><span class="sxs-lookup"><span data-stu-id="5fbf2-127">For example, (in the Exchange admin center or using PowerShell):</span></span>  <br/>  `Set-Mailbox user@contoso.com -AccountDisabled:$true` <br/> |
|<span data-ttu-id="5fbf2-128">Clôturer la session pour un protocole particulier (par exemple, ActiveSync)</span><span class="sxs-lookup"><span data-stu-id="5fbf2-128">Terminate the session for a particular protocol (such as ActiveSync)</span></span>  <br/> |<span data-ttu-id="5fbf2-129">Désactivez le protocole.</span><span class="sxs-lookup"><span data-stu-id="5fbf2-129">Disable the protocol.</span></span> <span data-ttu-id="5fbf2-130">Par exemple, (dans le centre d’administration Exchange ou à l’aide de PowerShell) :</span><span class="sxs-lookup"><span data-stu-id="5fbf2-130">For example, (in the Exchange admin center or using PowerShell):</span></span>  <br/>  `Set-CASMailbox user@contoso.com -ActiveSyncEnabled:$false` <br/> |

<span data-ttu-id="5fbf2-131">Les opérations ci-dessus peuvent être réalisées à trois endroits :</span><span class="sxs-lookup"><span data-stu-id="5fbf2-131">The above operations can be done in three places:</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="5fbf2-132">**Si vous clôturez la session ici**</span><span class="sxs-lookup"><span data-stu-id="5fbf2-132">**If you terminate the session here**</span></span> <br/> |<span data-ttu-id="5fbf2-133">**Temps nécessaire**</span><span class="sxs-lookup"><span data-stu-id="5fbf2-133">**How long it takes**</span></span> <br/> |
|<span data-ttu-id="5fbf2-134">Dans le centre d'administration Exchange ou à l'aide de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5fbf2-134">In the Exchange admin center or using PowerShell</span></span>  <br/> |<span data-ttu-id="5fbf2-135">Le délai prévu est de moins de 30 minutes</span><span class="sxs-lookup"><span data-stu-id="5fbf2-135">Expected delay is within 30 min</span></span>  <br/> |
|<span data-ttu-id="5fbf2-136">Dans le centre d'administration Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="5fbf2-136">In the Azure Active Directory admin center</span></span>  <br/> |<span data-ttu-id="5fbf2-137">Le délai prévu est de 60 minutes</span><span class="sxs-lookup"><span data-stu-id="5fbf2-137">Expected delay is 60 min</span></span>  <br/> |
|<span data-ttu-id="5fbf2-138">Dans un environnement local</span><span class="sxs-lookup"><span data-stu-id="5fbf2-138">In an on-premises environment</span></span>  <br/> |<span data-ttu-id="5fbf2-139">Le délai prévu est de 3 heures ou plus</span><span class="sxs-lookup"><span data-stu-id="5fbf2-139">Expected delay is 3 hours or more</span></span>  <br/> |

### <a name="how-to-get-fastest-response-for-account-termination"></a><span data-ttu-id="5fbf2-140">Comment obtenir une réponse plus rapide à une demande de clôture de compte</span><span class="sxs-lookup"><span data-stu-id="5fbf2-140">How to get fastest response for account termination</span></span>

 <span data-ttu-id="5fbf2-p107">**Plus rapide**: utilisez le centre d'administration Exchange (avec PowerShell) ou le centre d'administration Azure Active Directory. Dans un environnement local, la synchronisation de la modification via DirSync peut prendre plusieurs heures.</span><span class="sxs-lookup"><span data-stu-id="5fbf2-p107">**Fastest**: Use the Exchange admin center (use PowerShell) or Azure Active Directory admin center. In an on-premises environment, it can take several hours to sync the change through DirSync.</span></span>
  
 <span data-ttu-id="5fbf2-p108">**Plus rapide pour un utilisateur ayant une présence locale et dans le centre de données Exchange**: clôturez la session via le centre d'administration Azure Active Directory/Exchange ET apportez la modification aussi dans l'environnement local. À défaut, la modification dans le centre d'administration Azure Active Directory/Exchange est remplacée par DirSync.</span><span class="sxs-lookup"><span data-stu-id="5fbf2-p108">**Fastest for a user with presence on-premises and in the Exchange Datacenter**: Terminate the session using Azure Active Directory admin center/Exchange admin center AND make the change in the on-premises environment as well. Otherwise, the change in Azure Active Directory admin center/Exchange admin center will be overwritten by DirSync.</span></span>
  
## <a name="related-articles"></a><span data-ttu-id="5fbf2-145">Articles connexes</span><span class="sxs-lookup"><span data-stu-id="5fbf2-145">Related articles</span></span>

[<span data-ttu-id="5fbf2-146">Restaurer un utilisateur</span><span class="sxs-lookup"><span data-stu-id="5fbf2-146">Restore a user</span></span>](restore-user.md)