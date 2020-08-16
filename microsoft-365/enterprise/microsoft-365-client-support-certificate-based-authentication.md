---
title: Prise en charge des applications clientes Microsoft 365 — authentification basée sur les certificats
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: Office 365 Administration
localization_priority: Normal
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
search.appverid:
- MET150
f1.keywords:
- NOCSH
description: Dans cet article, vous trouverez des détails sur la prise en charge de l’application cliente Microsoft 365 pour l’authentification basée sur les certificats..
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 870e6f39c054752a2a07848c34eecd0996e1816c
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "46690215"
---
# <a name="microsoft-365-client-app-support--certificate-based-authentication"></a><span data-ttu-id="4b4c9-103">Prise en charge des applications clientes Microsoft 365 — authentification basée sur les certificats</span><span class="sxs-lookup"><span data-stu-id="4b4c9-103">Microsoft 365 Client App Support — Certificate-based Authentication</span></span>

<span data-ttu-id="4b4c9-104">*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*</span><span class="sxs-lookup"><span data-stu-id="4b4c9-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="4b4c9-105">L’authentification basée sur les certificats vous permet de vous authentifier auprès d’Azure Active Directory avec un certificat client sur des appareils Windows, Android ou iOS.</span><span class="sxs-lookup"><span data-stu-id="4b4c9-105">Certificate-based authentication enables you to authenticate to Azure Active Directory with a client certificate on Windows, Android, or iOS devices.</span></span> <span data-ttu-id="4b4c9-106">La configuration de cette fonctionnalité élimine le besoin d’entrer un nom d’utilisateur et un mot de passe dans certains messages et applications Microsoft Office sur votre appareil mobile.</span><span class="sxs-lookup"><span data-stu-id="4b4c9-106">Configuring this feature eliminates the need to enter a username and password combination into certain mail and Microsoft Office applications on your mobile device.</span></span>

<span data-ttu-id="4b4c9-107">En savoir plus sur [l’authentification basée sur les certificats](https://docs.microsoft.com/azure/active-directory/authentication/active-directory-certificate-based-authentication-get-started).</span><span class="sxs-lookup"><span data-stu-id="4b4c9-107">Learn more about [certificate-based authentication](https://docs.microsoft.com/azure/active-directory/authentication/active-directory-certificate-based-authentication-get-started).</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="4b4c9-108">Plateformes prises en charge</span><span class="sxs-lookup"><span data-stu-id="4b4c9-108">Supported platforms</span></span>

 - <span data-ttu-id="4b4c9-109">Bureau<sup>2</sup> Windows 10</span><span class="sxs-lookup"><span data-stu-id="4b4c9-109">Windows 10 Desktop<sup>2</sup></span></span>
 - <span data-ttu-id="4b4c9-110">Applications modernes Windows 10</span><span class="sxs-lookup"><span data-stu-id="4b4c9-110">Windows 10 Modern Apps</span></span>
 - <span data-ttu-id="4b4c9-111">Navigateurs Web<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4b4c9-111">Web browsers<sup>3</sup></span></span>
 - <span data-ttu-id="4b4c9-112">Android<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="4b4c9-112">Android<sup>4</sup></span></span>
 - <span data-ttu-id="4b4c9-113">iOS</span><span class="sxs-lookup"><span data-stu-id="4b4c9-113">iOS</span></span>
 - <span data-ttu-id="4b4c9-114">macOS<sup>1</sup> <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="4b4c9-114">macOS<sup>1</sup> <sup>2</sup></span></span>

<span data-ttu-id="4b4c9-115">Pour plus d’informations sur la prise en charge de la plateforme dans Microsoft 365, voir [System Requirements for microsoft 365](https://products.office.com/office-system-requirements).</span><span class="sxs-lookup"><span data-stu-id="4b4c9-115">For more information about platform support in Microsoft 365, see [System requirements for Microsoft 365](https://products.office.com/office-system-requirements).</span></span>

## <a name="supported-clients"></a><span data-ttu-id="4b4c9-116">Clients pris en charge</span><span class="sxs-lookup"><span data-stu-id="4b4c9-116">Supported clients</span></span>

<span data-ttu-id="4b4c9-117">Les versions les plus récentes des clients suivants prennent en charge l’authentification par certificat :</span><span class="sxs-lookup"><span data-stu-id="4b4c9-117">The latest versions of the following clients support certificate-based authentication:</span></span>

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| <span data-ttu-id="4b4c9-118">![Icône Access](../media/o365-access-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-118">![Access icon](../media/o365-access-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-119">Access</span><span class="sxs-lookup"><span data-stu-id="4b4c9-119">Access</span></span>](https://products.office.com/access) | <span data-ttu-id="4b4c9-120">![Icône Azure](../media/o365-azure-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-120">![Azure icon](../media/o365-azure-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-121">Portail Azure AD <br></span><span class="sxs-lookup"><span data-stu-id="4b4c9-121">Azure AD <br> Portal </span></span>](https://azure.microsoft.com/features/azure-portal/) | <span data-ttu-id="4b4c9-122">![Icône portail d’entreprise](../media/o365-microsoft-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-122">![Company portal icon](../media/o365-microsoft-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-123">Portail d’entreprise <br></span><span class="sxs-lookup"><span data-stu-id="4b4c9-123">Company <br> Portal </span></span>](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) | <span data-ttu-id="4b4c9-124">![Icône Delve](../media/o365-delve-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-124">![Delve icon](../media/o365-delve-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-125">Delve</span><span class="sxs-lookup"><span data-stu-id="4b4c9-125">Delve</span></span>](https://products.office.com/business/intelligent-search) | <span data-ttu-id="4b4c9-126">![Icône Dynamics 365](../media/o365-dynamics365-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-126">![Dynamics 365 icon](../media/o365-dynamics365-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-127">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="4b4c9-127">Dynamics 365</span></span>](https://dynamics.microsoft.com) 
| <span data-ttu-id="4b4c9-128">![Icône de serveur Edge](../media/o365-edge-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-128">![Edge icon](../media/o365-edge-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-129">Edge</span><span class="sxs-lookup"><span data-stu-id="4b4c9-129">Edge</span></span>](https://www.microsoft.com/windows/microsoft-edge) | <span data-ttu-id="4b4c9-130">![Icône Excel](../media/o365-excel-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-130">![Excel icon](../media/o365-excel-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-131">Excel</span><span class="sxs-lookup"><span data-stu-id="4b4c9-131">Excel</span></span>](https://products.office.com/excel) | <span data-ttu-id="4b4c9-132">![Icône Forms](../media/o365-forms-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-132">![Forms icon](../media/o365-forms-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-133">Forms</span><span class="sxs-lookup"><span data-stu-id="4b4c9-133">Forms</span></span>](https://flow.microsoft.com/connectors/shared_microsoftforms/microsoft-forms/) | <span data-ttu-id="4b4c9-134">![Icône Kaizala](../media/o365-kaizala-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-134">![Kaizala icon](../media/o365-kaizala-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-135">Kaizala</span><span class="sxs-lookup"><span data-stu-id="4b4c9-135">Kaizala</span></span>](https://products.office.com/en/business/microsoft-kaizala) | <span data-ttu-id="4b4c9-136">![Icône Office.com](../media/o365-office-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-136">![Office.com icon](../media/o365-office-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-137">Office.com</span><span class="sxs-lookup"><span data-stu-id="4b4c9-137">Office.com</span></span>](https://www.office.com/) 
| <span data-ttu-id="4b4c9-138">![Icône d’administrateur Office 365](../media/o365-o365admin-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-138">![Office 365 Admin icon](../media/o365-o365admin-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-139">Administrateur 365 Microsoft <br></span><span class="sxs-lookup"><span data-stu-id="4b4c9-139">Microsoft 365 <br> Admin</span></span>](https://products.office.com/business/manage-office-365-admin-app) | <span data-ttu-id="4b4c9-140">![Icône de l’objectif](../media/o365-lens-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-140">![Lens icon](../media/o365-lens-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-141">Office Lens</span><span class="sxs-lookup"><span data-stu-id="4b4c9-141">Office Lens</span></span>](https://www.microsoft.com/p/office-lens/9wzdncrfj3t8?activetab=pivot%3Aoverviewtab) | <span data-ttu-id="4b4c9-142">![Icône OneDrive entreprise](../media/o365-OneDrive-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-142">![OneDrive for Business icon](../media/o365-OneDrive-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-143">OneDrive<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="4b4c9-143">OneDrive<sup>1</sup></span></span>](https://products.office.com/onedrive-for-business/online-cloud-storage) |  <span data-ttu-id="4b4c9-144">![Icône OneNote](../media/o365-OneNote-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-144">![OneNote icon](../media/o365-OneNote-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-145">OneNote</span><span class="sxs-lookup"><span data-stu-id="4b4c9-145">OneNote</span></span>](https://products.office.com/onenote) | <span data-ttu-id="4b4c9-146">![Icône Outlook](../media/o365-outlook-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-146">![Outlook icon](../media/o365-outlook-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-147">Outlook</span><span class="sxs-lookup"><span data-stu-id="4b4c9-147">Outlook</span></span>](https://products.office.com/outlook) 
| <span data-ttu-id="4b4c9-148">![Icône planificateur](../media/o365-planner-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-148">![Planner icon](../media/o365-planner-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-149">Planner</span><span class="sxs-lookup"><span data-stu-id="4b4c9-149">Planner</span></span>](https://products.office.com/business/task-management-software) | <span data-ttu-id="4b4c9-150">![Icône PowerApp](../media/o365-powerapps-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-150">![PowerApps icon](../media/o365-powerapps-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-151">PowerApps<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4b4c9-151">PowerApps<sup>3</sup></span></span>](https://powerapps.microsoft.com) | <span data-ttu-id="4b4c9-152">![Icône de mise en marche automatique](../media/o365-flow-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-152">![Power Automate icon](../media/o365-flow-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-153">Automate d’alimentation <br></span><span class="sxs-lookup"><span data-stu-id="4b4c9-153">Power <br> Automate</span></span>](https://flow.microsoft.com) | <span data-ttu-id="4b4c9-154">![Icône PowerBI](../media/o365-powerbi-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-154">![PowerBI icon](../media/o365-powerbi-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-155">Power BI</span><span class="sxs-lookup"><span data-stu-id="4b4c9-155">Power BI</span></span>](https://powerbi.microsoft.com)| <span data-ttu-id="4b4c9-156">![Icône PowerPoint](../media/o365-powerpoint-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-156">![PowerPoint icon](../media/o365-powerpoint-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-157">PowerPoint</span><span class="sxs-lookup"><span data-stu-id="4b4c9-157">PowerPoint</span></span>](https://products.office.com/powerpoint) 
| <span data-ttu-id="4b4c9-158">![Icône Project](../media/o365-project-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-158">![Project icon](../media/o365-project-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-159">Project</span><span class="sxs-lookup"><span data-stu-id="4b4c9-159">Project</span></span>](https://products.office.com/project) | <span data-ttu-id="4b4c9-160">![Icône Publisher](../media/o365-publisher-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-160">![Publisher icon](../media/o365-publisher-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-161">Publisher</span><span class="sxs-lookup"><span data-stu-id="4b4c9-161">Publisher</span></span>](https://products.office.com/publisher) | <span data-ttu-id="4b4c9-162">![Icône de SharePoint](../media/o365-sharepoint-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-162">![SharePoint icon](../media/o365-sharepoint-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-163">SharePoint</span><span class="sxs-lookup"><span data-stu-id="4b4c9-163">Sharepoint</span></span>](https://products.office.com/sharepoint) | <span data-ttu-id="4b4c9-164">![Icône Skype Entreprise](../media/o365-skypeforbusiness-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-164">![Skype for Business icon](../media/o365-skypeforbusiness-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-165">Skype <br> entreprise</span><span class="sxs-lookup"><span data-stu-id="4b4c9-165">Skype for <br> Business</span></span>](https://www.skype.com/business/) | <span data-ttu-id="4b4c9-166">![Icône de pense-bête](../media/o365-stickynotes-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-166">![Sticky Notes icon](../media/o365-stickynotes-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-167">Notes du pense-bête</span><span class="sxs-lookup"><span data-stu-id="4b4c9-167">Sticky Notes</span></span>](https://www.microsoft.com/p/microsoft-sticky-notes/9nblggh4qghw) 
| <span data-ttu-id="4b4c9-168">![Icône Stream](../media/o365-stream-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-168">![Stream icon](../media/o365-stream-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-169">Stream</span><span class="sxs-lookup"><span data-stu-id="4b4c9-169">Stream</span></span>](https://stream.microsoft.com) | <span data-ttu-id="4b4c9-170">![Icône Sway](../media/o365-sway-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-170">![Sway icon](../media/o365-sway-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-171">Sway</span><span class="sxs-lookup"><span data-stu-id="4b4c9-171">Sway</span></span>](https://sway.com) | <span data-ttu-id="4b4c9-172">![Icône Teams](../media/o365-teams-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-172">![Teams icon](../media/o365-teams-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-173">Teams<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="4b4c9-173">Teams<sup>2</sup></span></span>](https://products.office.com/microsoft-teams/group-chat-software) | <span data-ttu-id="4b4c9-174">![Icône action](../media/o365-todo-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-174">![To Do icon](../media/o365-todo-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-175">Action</span><span class="sxs-lookup"><span data-stu-id="4b4c9-175">To Do</span></span>](https://todo.microsoft.com) | <span data-ttu-id="4b4c9-176">![Icône Visio](../media/o365-visio-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-176">![Visio icon](../media/o365-visio-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-177">Visio</span><span class="sxs-lookup"><span data-stu-id="4b4c9-177">Visio</span></span>](https://products.office.com/visio/flowchart-software) 
| <span data-ttu-id="4b4c9-178">![Icône de tableau blanc](../media/o365-whiteboard-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-178">![Whiteboard icon](../media/o365-whiteboard-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-179">Tableau blanc<sup>3</sup>,<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="4b4c9-179">Whiteboard<sup>3</sup>,<sup>4</sup></span></span>](https://whiteboard.microsoft.com/) | <span data-ttu-id="4b4c9-180">![Icône Word](../media/o365-word-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-180">![Word icon](../media/o365-word-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-181">Word</span><span class="sxs-lookup"><span data-stu-id="4b4c9-181">Word</span></span>](https://products.office.com/word) | <span data-ttu-id="4b4c9-182">![Icône Yammer](../media/o365-yammer-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-182">![Yammer icon](../media/o365-yammer-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-183">Yammer<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="4b4c9-183">Yammer<sup>2</sup></span></span>](https://products.office.com/yammer/yammer-overview) |

## <a name="supported-powershell-modules"></a><span data-ttu-id="4b4c9-184">Modules PowerShell pris en charge</span><span class="sxs-lookup"><span data-stu-id="4b4c9-184">Supported PowerShell modules</span></span>

| | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|
| <span data-ttu-id="4b4c9-185">![Icône Azure](../media/o365-azure-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-185">![Azure icon](../media/o365-azure-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-186">Azure AD <br> PowerShell</span><span class="sxs-lookup"><span data-stu-id="4b4c9-186">Azure AD <br> PowerShell</span></span>](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) | <span data-ttu-id="4b4c9-187">![Icône Exchange](../media/o365-exchange-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-187">![Exchange icon](../media/o365-exchange-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-188">Exchange Online <br> PowerShell</span><span class="sxs-lookup"><span data-stu-id="4b4c9-188">Exchange Online <br> PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) | <span data-ttu-id="4b4c9-189">![Icône de SharePoint](../media/o365-sharepoint-64x64.png)</span><span class="sxs-lookup"><span data-stu-id="4b4c9-189">![SharePoint icon](../media/o365-sharepoint-64x64.png)</span></span> <br> [<span data-ttu-id="4b4c9-190">SharePoint Online <br> PowerShell</span><span class="sxs-lookup"><span data-stu-id="4b4c9-190">SharePoint Online <br> PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

> [!NOTE]
> <span data-ttu-id="4b4c9-191"><sup>1</sup> la prise en charge de OneDrive sur MacOS est bientôt disponible.</span><span class="sxs-lookup"><span data-stu-id="4b4c9-191"><sup>1</sup> Support for OneDrive on macOS available soon.</span></span> <br>
> <span data-ttu-id="4b4c9-192"><sup>2</sup> la prise en charge de Yammer sur le bureau Windows et MacOS est bientôt disponible.</span><span class="sxs-lookup"><span data-stu-id="4b4c9-192"><sup>2</sup> Support for Yammer on Windows Desktop and macOS available soon.</span></span> <span data-ttu-id="4b4c9-193">Prise en charge de teams sur le bureau Windows bientôt disponible.</span><span class="sxs-lookup"><span data-stu-id="4b4c9-193">Support for Teams on Windows Desktop available soon.</span></span><br>
> <span data-ttu-id="4b4c9-194"><sup>3</sup> la prise en charge des PowerApp et du tableau blanc sur les applications Web est bientôt disponible.</span><span class="sxs-lookup"><span data-stu-id="4b4c9-194"><sup>3</sup> Support for PowerApps and Whiteboard on web apps available soon.</span></span> <br>
> <span data-ttu-id="4b4c9-195"><sup>4</sup> la prise en charge du tableau blanc sur Android est bientôt disponible.</span><span class="sxs-lookup"><span data-stu-id="4b4c9-195"><sup>4</sup> Support for Whiteboard on Android available soon.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b4c9-196">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b4c9-196">See also</span></span>

[<span data-ttu-id="4b4c9-197">Vue d’ensemble de Microsoft 365 Entreprise</span><span class="sxs-lookup"><span data-stu-id="4b4c9-197">Microsoft 365 Enterprise overview</span></span>](microsoft-365-overview.md)