---
title: 'Étape 1 : empêcher un employé de se connecter à Microsoft 365'
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
description: Empêcher un ancien employé de se connecter et bloquer l’accès Microsoft 365 services.
ms.openlocfilehash: 60f4cf6b5c9a0b5dc2023b3ef7b6460685142d07
ms.sourcegitcommit: ff20f5b4e3268c7c98a84fb1cbe7db7151596b6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "52244251"
---
# <a name="step-1---prevent-a-former-employee-from-logging-in-and-block-access-to-microsoft-365-services"></a><span data-ttu-id="3e8ec-103">Étape 1 : empêcher un ancien employé de se connecter et bloquer l’accès Microsoft 365 services</span><span class="sxs-lookup"><span data-stu-id="3e8ec-103">Step 1 - Prevent a former employee from logging in and block access to Microsoft 365 services</span></span>

<span data-ttu-id="3e8ec-104">Si vous devez empêcher immédiatement l’accès à la signature d’un utilisateur, vous devez réinitialiser son mot de passe.</span><span class="sxs-lookup"><span data-stu-id="3e8ec-104">If you need to immediately prevent a user's sign-in access, you should reset their password.</span></span> <span data-ttu-id="3e8ec-105">Dans cette étape, forcez la sortie de l’utilisateur de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="3e8ec-105">In this step, force a sign out of the user from Microsoft 365.</span></span>

1. <span data-ttu-id="3e8ec-106">Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.</span><span class="sxs-lookup"><span data-stu-id="3e8ec-106">In the admin center, go to the **Users** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Active users</a> page.</span></span>
2. <span data-ttu-id="3e8ec-107">Sélectionnez la case à côté du nom de l’utilisateur, puis sélectionnez **Réinitialiser le mot de passe.**</span><span class="sxs-lookup"><span data-stu-id="3e8ec-107">Select the box next to the user's name, and then select **Reset password**.</span></span>
3. <span data-ttu-id="3e8ec-108">Entrez un nouveau mot de passe, puis sélectionnez **Réinitialiser.**</span><span class="sxs-lookup"><span data-stu-id="3e8ec-108">Enter a new password, and then select **Reset**.</span></span> <span data-ttu-id="3e8ec-109">(Ne leur envoyez pas de message.)</span><span class="sxs-lookup"><span data-stu-id="3e8ec-109">(Don't send it to them.)</span></span>
4. <span data-ttu-id="3e8ec-110">Sélectionnez le nom de l’utilisateur pour aller  dans le volet de propriétés, puis sous l’onglet Compte, sélectionnez Lancer **la signature.**</span><span class="sxs-lookup"><span data-stu-id="3e8ec-110">Select the user's name to go to their properties pane, and on the **Account** tab, select **Initiate sign-out**.</span></span>

<span data-ttu-id="3e8ec-111">Dans l’heure qui s’affiche( ou après avoir quitté la page de Microsoft 365 en cours), ils sont invités à se ré-inscrire.</span><span class="sxs-lookup"><span data-stu-id="3e8ec-111">Within an hour - or after they leave the current Microsoft 365 page they are on - they're prompted to sign in again.</span></span> <span data-ttu-id="3e8ec-112">Un jeton d’accès est bon pendant une heure, donc la chronologie dépend du temps qui reste sur ce jeton et de la façon dont il quitte la page web actuelle.</span><span class="sxs-lookup"><span data-stu-id="3e8ec-112">An access token is good for an hour, so the timeline depends on how much time is left on that token, and whether they navigate out of their current webpage.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="3e8ec-113">Si l’utilisateur est Outlook sur le web, il se peut qu’il ne soit pas immédiatement mis hors de l’application en cliquant dans sa boîte aux lettres.</span><span class="sxs-lookup"><span data-stu-id="3e8ec-113">If the user is in Outlook on the web, just clicking around in their mailbox, they may not be kicked out immediately.</span></span> <span data-ttu-id="3e8ec-114">Dès qu’ils sélectionnent une autre vignette, telle que OneDrive, ou actualisent leur navigateur, la signature est lancée.</span><span class="sxs-lookup"><span data-stu-id="3e8ec-114">As soon as they select a different tile, such as OneDrive, or refresh their browser, the sign-out is initiated.</span></span>
  
<span data-ttu-id="3e8ec-115">Pour utiliser PowerShell pour décrémenter un utilisateur immédiatement, consultez l’cmdlet [Revoke-AzureADUserAllRefreshToken.](/powershell/module/azuread/revoke-azureaduserallrefreshtoken)</span><span class="sxs-lookup"><span data-stu-id="3e8ec-115">To use PowerShell to sign out a user immediately, see the [Revoke-AzureADUserAllRefreshToken](/powershell/module/azuread/revoke-azureaduserallrefreshtoken) cmdlet.</span></span>
  
<span data-ttu-id="3e8ec-116">Pour plus d'informations sur le temps nécessaire pour supprimer l'accès d'un utilisateur au courrier électronique, voir [Ce que vous devez savoir sur la clôture d'une session de messagerie d'un employé](remove-former-employee-step-7.md#what-you-need-to-know-about-terminating-an-employees-email-session).</span><span class="sxs-lookup"><span data-stu-id="3e8ec-116">For more information about how long it takes to get someone out of email, see [What you need to know about terminating an employee's email session](remove-former-employee-step-7.md#what-you-need-to-know-about-terminating-an-employees-email-session).</span></span>

## <a name="block-a-former-employees-access-to-microsoft-365-services"></a><span data-ttu-id="3e8ec-117">Bloquer l’accès d’un ancien employé Microsoft 365 services</span><span class="sxs-lookup"><span data-stu-id="3e8ec-117">Block a former employee's access to Microsoft 365 services</span></span>

> [!IMPORTANT]
 > <span data-ttu-id="3e8ec-118">Le blocage d’un compte peut prendre jusqu’à 24 heures.</span><span class="sxs-lookup"><span data-stu-id="3e8ec-118">Blocking an account can take up to 24 hours to take effect.</span></span> <span data-ttu-id="3e8ec-119">Si vous devez empêcher immédiatement l’accès à la signature d’un utilisateur, suivez les étapes ci-dessus et réinitialisez son mot de passe.</span><span class="sxs-lookup"><span data-stu-id="3e8ec-119">If you need to immediately prevent a user's sign-in access, follow the steps above and reset their password.</span></span>

1. <span data-ttu-id="3e8ec-120">Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.</span><span class="sxs-lookup"><span data-stu-id="3e8ec-120">In the admin center, go to the **Users** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Active users</a> page.</span></span>
2. <span data-ttu-id="3e8ec-121">Sélectionnez le nom de l’employé que vous souhaitez bloquer, puis sous le nom de l’utilisateur, sélectionnez le symbole bloquer **cet utilisateur.**</span><span class="sxs-lookup"><span data-stu-id="3e8ec-121">Select the name of the employee that you want to block, and under the user's name, select the symbol for **Block this user**.</span></span>
3. <span data-ttu-id="3e8ec-122">Sélectionnez **Bloquer la signature de l’utilisateur,** puis sélectionnez **Enregistrer.**</span><span class="sxs-lookup"><span data-stu-id="3e8ec-122">Select **Block the user from signing in**, and then select **Save**.</span></span>

## <a name="block-a-former-employees-access-to-email-exchange-online"></a><span data-ttu-id="3e8ec-123">Bloquer l'accès d'un ancien employé aux courriers (Exchange Online)</span><span class="sxs-lookup"><span data-stu-id="3e8ec-123">Block a former employee's access to email (Exchange Online)</span></span>

<span data-ttu-id="3e8ec-124">Si vous avez des messages électroniques dans le cadre de votre abonnement Microsoft 365, connectez-vous au Centre d’administration Exchange et suivez ces étapes pour empêcher votre ancien employé d’accéder à son courrier électronique.</span><span class="sxs-lookup"><span data-stu-id="3e8ec-124">If you have email as part of your Microsoft 365 subscription, sign in to the Exchange admin center and follow these steps to block your former employee from accessing their email.</span></span>
  
1. <span data-ttu-id="3e8ec-125">Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>.</span><span class="sxs-lookup"><span data-stu-id="3e8ec-125">Go to the <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange admin center</a>.</span></span>
2. <span data-ttu-id="3e8ec-126">Dans le Centre d'administration Exchange, accédez à **Destinataires** \> **Boîtes aux lettres**.</span><span class="sxs-lookup"><span data-stu-id="3e8ec-126">In the Exchange admin center, navigate to **Recipients** \> **Mailboxes**.</span></span>
3. <span data-ttu-id="3e8ec-127">Double-cliquez sur l’utilisateur et consultez la page **Fonctionnalités de boîte aux lettres.**</span><span class="sxs-lookup"><span data-stu-id="3e8ec-127">Double-click the user and go to the **Mailbox features** page.</span></span> <span data-ttu-id="3e8ec-128">Sous **Appareils mobiles,** sélectionnez Désactiver Exchange ActiveSync et Désactiver OWA pour les   **appareils,** puis répondez Oui aux deux lorsque vous y répondrez.</span><span class="sxs-lookup"><span data-stu-id="3e8ec-128">Under **Mobile Devices**, select **Disable Exchange ActiveSync** and **Disable OWA for Devices,** and answer **Yes** to both when prompted.</span></span>
4. <span data-ttu-id="3e8ec-129">Sous **Connectivité de messagerie,** **sélectionnez Désactiver et** **répondez Oui** à l’invite.</span><span class="sxs-lookup"><span data-stu-id="3e8ec-129">Under **Email Connectivity**, select **Disable** and answer **Yes** when prompted.</span></span>