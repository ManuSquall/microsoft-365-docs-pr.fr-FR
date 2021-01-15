---
title: Ajouter votre domaine Google Workspace
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- adminvideo
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment déplacer votre domaine de Google Workspace vers Microsoft 365 pour les entreprises.
ms.openlocfilehash: 1abc05867147d2b52e26804918e8247053b5e1d5
ms.sourcegitcommit: 9833f95ab6ab95aea20d68a277246dca2223f93d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2021
ms.locfileid: "49794676"
---
# <a name="add-your-google-workspace-domain-to-microsoft-365"></a><span data-ttu-id="8aa92-103">Ajouter votre domaine Google Workspace à Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="8aa92-103">Add your Google Workspace domain to Microsoft 365</span></span>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LWKT?autoplay=false]

<span data-ttu-id="8aa92-104">Ajoutez votre domaine Google Workspace à Microsoft 365 pour les entreprises afin de continuer à utiliser votre adresse de messagerie professionnelle.</span><span class="sxs-lookup"><span data-stu-id="8aa92-104">Add your Google Workspace domain to Microsoft 365 for business so you can keep using your business email address.</span></span>

## <a name="try-it"></a><span data-ttu-id="8aa92-105">Essayez !</span><span class="sxs-lookup"><span data-stu-id="8aa92-105">Try it!</span></span>

1. <span data-ttu-id="8aa92-106">Go to the [Microsoft 365 admin center](https://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="8aa92-106">Go to the [Microsoft 365 admin center](https://admin.microsoft.com).</span></span>
1. <span data-ttu-id="8aa92-107">In the Microsoft 365 Admin Center, in the left nav, select **Show all**, **Settings** and then **Domains**.</span><span class="sxs-lookup"><span data-stu-id="8aa92-107">In the Microsoft 365 Admin Center, in the left nav, select **Show all**, **Settings** and then **Domains**.</span></span>
1. <span data-ttu-id="8aa92-108">Choisissez **Ajouter un domaine,** entrez votre nom de domaine, puis **sélectionnez Utiliser ce domaine.**</span><span class="sxs-lookup"><span data-stu-id="8aa92-108">Choose **Add domain**, enter your domain name then select **Use this domain**.</span></span> 
1. <span data-ttu-id="8aa92-109">Choose, **Add a TXT record to the domains DNS records,** select **Continue**, and copy the TXT value.</span><span class="sxs-lookup"><span data-stu-id="8aa92-109">Choose, **Add a TXT record to the domains DNS records**, select **Continue**, and copy the TXT value.</span></span> 
1. <span data-ttu-id="8aa92-110">Revenir à la [console d’administration Google,](https://admin.google.com)choisissez **Domaines,** Gérer les domaines, Afficher les **détails,** Gérer le domaine, **DNS,** puis faites défiler vers le bas jusqu’aux enregistrements de ressources **personnalisés.**  </span><span class="sxs-lookup"><span data-stu-id="8aa92-110">Go back to the [Google Admin Console](https://admin.google.com), choose **Domains**, **Manage domains**, **View Details**, **Manage domain**, **DNS**, and  then scroll down to **Custom resource records**.</span></span> 
1. <span data-ttu-id="8aa92-111">Ouvrez la drop-down du type d’enregistrement, choisissez **TXT**, collez la valeur TXT que vous avez copiée, puis sélectionnez **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="8aa92-111">Open the record type drop-down, choose **TXT**, paste the TXT value you copied then select **Add**.</span></span> 

    <span data-ttu-id="8aa92-112">La mise à jour prend généralement quelques minutes, mais peut prendre jusqu’à 48 heures.</span><span class="sxs-lookup"><span data-stu-id="8aa92-112">The update usually takes a fact within a few minutes but may take up to 48 hours.</span></span> 
1. <span data-ttu-id="8aa92-113">Revenir au Centre d’administration Microsoft 365, **sélectionnez Vérifier,** puis **Fermez.**</span><span class="sxs-lookup"><span data-stu-id="8aa92-113">Return to the Microsoft 365 Admin Center, select **Verify**,and then **Close**.</span></span> 
1. <span data-ttu-id="8aa92-114">Pour définir votre domaine comme courrier électronique principal pour vos utilisateurs, dans le navigation de gauche, sélectionnez **Utilisateurs**  >  **actifs.**</span><span class="sxs-lookup"><span data-stu-id="8aa92-114">To set your domain as the primary email for your users, in the left nav, select **Users** > **Active users**.</span></span> 
1. <span data-ttu-id="8aa92-115">Choisissez un utilisateur, sélectionnez Gérer le nom **d’utilisateur** et le courrier électronique, **Modifier,** sélectionner votre domaine dans la liste modifiable, puis sélectionner Terminé **et** enregistrer **les modifications.**</span><span class="sxs-lookup"><span data-stu-id="8aa92-115">Choose a user, select **Manage username and email**, **Edit**, select your domain from the dropdown, then select **Done** and **Save changes**.</span></span> 
1. <span data-ttu-id="8aa92-116">Répétez ce processus pour chaque utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8aa92-116">Repeat this process for each user.</span></span> 

    <span data-ttu-id="8aa92-117">Lorsque vous avez terminé, vous êtes prêt à installer les applications Office et à migrer vos éléments de courrier et de calendrier vers Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="8aa92-117">When you're finished, you'll be ready to install Office apps and migrate your email and calendar items to Microsoft 365.</span></span> 