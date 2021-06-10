---
title: Autorisations dans le Centre de sécurité Microsoft 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
ms.audience: Admin
ms.topic: article
audience: Admin
localization_priority: Priority
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Les administrateurs peuvent apprendre comment gérer les autorisations dans le Centre de sécurité Microsoft 365 pour toutes les tâches liées à la sécurité.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9c2d28510c25290921084e6a238fa8c781c35624
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "52772523"
---
# <a name="permissions-in-the-microsoft-365-security-center"></a><span data-ttu-id="e7b85-103">Autorisations dans le Centre de sécurité Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="e7b85-103">Permissions in the Microsoft 365 security center</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

<span data-ttu-id="e7b85-104">**S’applique à**</span><span class="sxs-lookup"><span data-stu-id="e7b85-104">**Applies to**</span></span>
- [<span data-ttu-id="e7b85-105">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="e7b85-105">Exchange Online Protection</span></span>](exchange-online-protection-overview.md)
- [<span data-ttu-id="e7b85-106">Microsoft Defender pour Office 365 : offre 1 et offre 2</span><span class="sxs-lookup"><span data-stu-id="e7b85-106">Microsoft Defender for Office 365 plan 1 and plan 2</span></span>](defender-for-office-365.md)
- [<span data-ttu-id="e7b85-107">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="e7b85-107">Microsoft 365 Defender</span></span>](../defender/microsoft-365-defender.md)

<span data-ttu-id="e7b85-108">Vous devez gérer des scénarios de sécurité qui couvrent tous les services de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="e7b85-108">You need to manage security scenarios that span all the Microsoft 365 services.</span></span> <span data-ttu-id="e7b85-109">Et vous aurez besoin de la flexibilité requise pour accorder les autorisations d’administrateur aux bonnes personnes de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="e7b85-109">And you need the flexibility to give the right admin permissions to the right people in your organization.</span></span>

<span data-ttu-id="e7b85-110">Le Centre de sécurité Microsoft 365 de <https://security.microsoft.com> prend en charge la gestion directe des autorisations pour les utilisateurs qui effectuent des tâches de sécurité dans Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="e7b85-110">The Microsoft 365 security center at <https://security.microsoft.com> supports directly managing permissions for users who perform security tasks in Microsoft 365.</span></span> <span data-ttu-id="e7b85-111">En utilisant le Centre de sécurité pour gérer les autorisations, vous pouvez gérer les autorisations de façon centralisée pour toutes les tâches liées à la sécurité.</span><span class="sxs-lookup"><span data-stu-id="e7b85-111">By using the security center to manage permissions, you can manage permissions centrally for all tasks related to security.</span></span>

<span data-ttu-id="e7b85-112">Pour gérer les autorisations dans le centre de sécurité, accédez à **Autorisations et rôles** ou <https://security.microsoft.com/securitypermissions>.</span><span class="sxs-lookup"><span data-stu-id="e7b85-112">To manage permissions in the security center, go to **Permissions & roles** or <https://security.microsoft.com/securitypermissions>.</span></span> <span data-ttu-id="e7b85-113">Vous devez être **administrateur général** ou membre du groupe de rôles **Gestion de l’organisation** dans le centre de sécurité.</span><span class="sxs-lookup"><span data-stu-id="e7b85-113">You need to be a **global administrator** or a member of the **Organization Management** role group in the security center.</span></span> <span data-ttu-id="e7b85-114">Plus précisément, le rôle **Gestion des rôles** permet aux utilisateurs d’afficher, de créer et de modifier des groupes de rôles dans le centre de sécurité. Par défaut, ce rôle est attribué uniquement au groupe de rôles **Gestion de l’organisation**.</span><span class="sxs-lookup"><span data-stu-id="e7b85-114">Specifically, the **Role Management** role allows users to view, create, and modify role groups in the security center, and by default, that role is assigned only to the **Organization Management** role group.</span></span>

## <a name="relationship-of-members-roles-and-role-groups"></a><span data-ttu-id="e7b85-115">Relation entre les membres, les rôles et les groupes de rôles</span><span class="sxs-lookup"><span data-stu-id="e7b85-115">Relationship of members, roles, and role groups</span></span>

<span data-ttu-id="e7b85-116">Les autorisations dans le centre de sécurité sont basées sur le modèle d’autorisations Contrôle d’accès en fonction du rôle (role-based access control ou RBAC).</span><span class="sxs-lookup"><span data-stu-id="e7b85-116">Permissions in the security center are based on the role-based access control (RBAC) permissions model.</span></span> <span data-ttu-id="e7b85-117">RBAC est le même modèle d’autorisations que celui utilisé par la plupart des services Microsoft 365. Par conséquent, si vous êtes familiarisé avec la structure d’autorisations dans ces services, l’octroi d’autorisations dans le centre de sécurité vous sera très familier.</span><span class="sxs-lookup"><span data-stu-id="e7b85-117">RBAC is the same permissions model that's used by most Microsoft 365 services, so if you're familiar with the permission structure in these services, granting permissions in the security center will be very familiar.</span></span>

<span data-ttu-id="e7b85-118">Un **rôle** accorde les autorisations nécessaires pour effectuer un ensemble de tâches.</span><span class="sxs-lookup"><span data-stu-id="e7b85-118">A **role** grants the permissions to do a set of tasks.</span></span>

<span data-ttu-id="e7b85-119">Un **groupe de rôles** est un ensemble de rôles qui permet aux utilisateurs d’effectuer leurs tâches dans le centre de sécurité.</span><span class="sxs-lookup"><span data-stu-id="e7b85-119">A **role group** is a set of roles that lets people do their jobs in the security center.</span></span> <span data-ttu-id="e7b85-120">Par exemple, le groupe de rôles Administrateurs du simulateur d’attaques inclut le rôle Administrateur du simulateur d’attaques pour créer et gérer tous les aspects de l’entraînement de simulation d’attaque.</span><span class="sxs-lookup"><span data-stu-id="e7b85-120">For example, the Attack Simulator Administrators role group includes the Attack Simulator Admin role to create and manage all aspects of attack simulation training.</span></span>

<span data-ttu-id="e7b85-121">Le centre de sécurité inclut des groupes de rôles par défaut pour les tâches et fonctions les plus courantes que vous devez assigner.</span><span class="sxs-lookup"><span data-stu-id="e7b85-121">The security center includes default role groups for the most common tasks and functions that you'll need to assign.</span></span> <span data-ttu-id="e7b85-122">En règle générale, nous vous recommandons d’ajouter simplement des personnes comme **membres** aux groupes de rôles par défaut.</span><span class="sxs-lookup"><span data-stu-id="e7b85-122">Generally, we recommend simply adding individual users as **members** to the default role groups.</span></span>

![Diagramme montrant la relation des groupes de rôles avec les rôles et les membres](../../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png)

## <a name="roles-and-role-groups-in-the-security-center"></a><span data-ttu-id="e7b85-124">Rôles et groupes de rôles dans le centre de sécurité</span><span class="sxs-lookup"><span data-stu-id="e7b85-124">Roles and role groups in the security center</span></span>

<span data-ttu-id="e7b85-125">Les types de rôles et de groupes de rôles suivants sont disponibles dans **Autorisations et rôles** dans le centre de sécurité :</span><span class="sxs-lookup"><span data-stu-id="e7b85-125">The following types of roles and role groups are available in **Permissions & roles** in the security center:</span></span>

- <span data-ttu-id="e7b85-126">**Rôles Azure AD**: vous pouvez afficher les rôles et les utilisateurs attribués, mais vous ne pouvez pas les gérer directement dans le centre de sécurité.</span><span class="sxs-lookup"><span data-stu-id="e7b85-126">**Azure AD roles**: You can view the roles and assigned users, but you can't manage them directly in the security center.</span></span> <span data-ttu-id="e7b85-127">Les rôles Azure AD sont des rôles centraux qui attribuent des autorisations pour **tous les services** Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="e7b85-127">Azure AD roles are central roles that assign permissions for **all** Microsoft 365 services.</span></span>

- <span data-ttu-id="e7b85-128">**Les rôles de messagerie et de collaboration**: il s’agit des mêmes groupes de rôles que ceux disponibles dans le Centre de sécurité et de conformité, mais vous pouvez les gérer directement dans le centre de sécurité.</span><span class="sxs-lookup"><span data-stu-id="e7b85-128">**Email & collaboration roles**: These are the same role groups that are available in the Security & Compliance Center, but you can manage them directly in the security center.</span></span> <span data-ttu-id="e7b85-129">Les autorisations que vous attribuez ici sont spécifiques au Centre de sécurité Microsoft 365, au Centre de conformité Microsoft 365 et au Centre de sécurité et de conformité, et ne couvrent pas toutes les autorisations nécessaires dans d’autres charges de travail Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="e7b85-129">The permissions that you assign here are specific to the Microsoft 365 security center, the Microsoft 365 compliance center, and the Security & Compliance Center, and don't cover all of the permissions that are needed in other Microsoft 365 workloads.</span></span>

![Page d’autorisations dans le Centre de sécurité Microsoft 365](../../media/m365-sc-permissions-and-roles-page.png)

### <a name="azure-ad-roles-in-the-security-center"></a><span data-ttu-id="e7b85-131">Les rôles Azure AD dans le Centre de sécurité</span><span class="sxs-lookup"><span data-stu-id="e7b85-131">Azure AD roles in the security center</span></span>

<span data-ttu-id="e7b85-132">Lorsque vous accédez à **Rôles de messagerie et de collaboration** \> **Autorisations et rôles** \> **Rôles Azure AD** \> **Rôles** (ou directement à <https://security.microsoft.com/aadpermissions>), vous voyez les rôles Azure AD décrits dans cette section.</span><span class="sxs-lookup"><span data-stu-id="e7b85-132">When you go **Email & collaboration roles** \> **Permissions & roles** \> **Azure AD roles** \> **Roles** (or directly to <https://security.microsoft.com/aadpermissions>) you'll see the Azure AD roles that are described in this section.</span></span>

<span data-ttu-id="e7b85-133">Lorsque vous sélectionnez un rôle, un menu volant d’informations contenant la description du rôle et les attributions d’utilisateurs s’affiche.</span><span class="sxs-lookup"><span data-stu-id="e7b85-133">When you select a role, a details flyout that contains the description of the role and the user assignments appears.</span></span> <span data-ttu-id="e7b85-134">Toutefois, pour gérer ces affectations, vous devez cliquer sur **Gérer les membres dans Azure AD** dans le menu volant des détails.</span><span class="sxs-lookup"><span data-stu-id="e7b85-134">But to manage those assignments, you need to click **Manage members in Azure AD** in the details flyout.</span></span>

![Lien pour gérer les autorisations dans Azure Active Directory](../../media/permissions-manage-in-azure-ad-link.png)

<span data-ttu-id="e7b85-136">Pour plus d’informations, consultez [Affichage et attribution des rôles d’administrateur dans Azure Active Directory](/azure/active-directory/users-groups-roles/directory-manage-roles-portal).</span><span class="sxs-lookup"><span data-stu-id="e7b85-136">For more information, see [View and assign administrator roles in Azure Active Directory](/azure/active-directory/users-groups-roles/directory-manage-roles-portal).</span></span>

<br>

****

|<span data-ttu-id="e7b85-137">Rôle</span><span class="sxs-lookup"><span data-stu-id="e7b85-137">Role</span></span>|<span data-ttu-id="e7b85-138">Description</span><span class="sxs-lookup"><span data-stu-id="e7b85-138">Description</span></span>|
|---|---|
|<span data-ttu-id="e7b85-139">**Administrateur général**</span><span class="sxs-lookup"><span data-stu-id="e7b85-139">**Global administrator**</span></span>|<span data-ttu-id="e7b85-140">Accède à toutes les fonctionnalités d’administration de tous les services Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="e7b85-140">Access to all administrative features in all Microsoft 365 services.</span></span> <span data-ttu-id="e7b85-141">Seuls les administrateurs généraux peuvent affecter d’autres rôles d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="e7b85-141">Only global administrators can assign other administrator roles.</span></span> <span data-ttu-id="e7b85-142">Pour plus d’informations, consultez la section [Administrateur Général / Administrateur d’entreprise](/azure/active-directory/roles/permissions-reference#global-administrator--company-administrator).</span><span class="sxs-lookup"><span data-stu-id="e7b85-142">For more information, see [Global Administrator / Company Administrator](/azure/active-directory/roles/permissions-reference#global-administrator--company-administrator).</span></span>|
|<span data-ttu-id="e7b85-143">**Administrateur de conformité des données**</span><span class="sxs-lookup"><span data-stu-id="e7b85-143">**Compliance data administrator**</span></span>|<span data-ttu-id="e7b85-144">Effectue un suivi des données de votre organisation dans Microsoft 365, vérifie qu’elles sont protégées et obtient des informations sur les problèmes liés à l’atténuation des risques.</span><span class="sxs-lookup"><span data-stu-id="e7b85-144">Keep track of your organization's data across Microsoft 365, make sure it's protected, and get insights into any issues to help mitigate risks.</span></span> <span data-ttu-id="e7b85-145">Pour en savoir plus, consultez la section [Administrateur de conformité des données](/azure/active-directory/roles/permissions-reference#compliance-data-administrator).</span><span class="sxs-lookup"><span data-stu-id="e7b85-145">For more information, see [Compliance Data Administrator](/azure/active-directory/roles/permissions-reference#compliance-data-administrator).</span></span>|
|<span data-ttu-id="e7b85-146">**Administrateur de conformité**</span><span class="sxs-lookup"><span data-stu-id="e7b85-146">**Compliance administrator**</span></span>|<span data-ttu-id="e7b85-147">Aide votre organisation à respecter les exigences réglementaires, gère les cas de découverte électronique et gère les stratégies de gouvernance des données sur les emplacements, les identités et les applications Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="e7b85-147">Help your organization stay compliant with any regulatory requirements, manage eDiscovery cases, and maintain data governance policies across Microsoft 365 locations, identities, and apps.</span></span> <span data-ttu-id="e7b85-148">Pour en savoir plus, consultez la section [Administrateur de conformité](/azure/active-directory/roles/permissions-reference#compliance-administrator).</span><span class="sxs-lookup"><span data-stu-id="e7b85-148">For more information, see [Compliance Administrator](/azure/active-directory/roles/permissions-reference#compliance-administrator).</span></span>|
|<span data-ttu-id="e7b85-149">**Opérateur de sécurité**</span><span class="sxs-lookup"><span data-stu-id="e7b85-149">**Security operator**</span></span>|<span data-ttu-id="e7b85-150">Consulter, examiner et répondre aux menaces actives envers vos utilisateurs, appareils et contenus Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="e7b85-150">View, investigate, and respond to active threats to your Microsoft 365 users, devices, and content.</span></span> <span data-ttu-id="e7b85-151">Pour plus d’informations, voir la section [Opérateur de sécurité](/azure/active-directory/roles/permissions-reference#security-operator).</span><span class="sxs-lookup"><span data-stu-id="e7b85-151">For more information, see [Security Operator](/azure/active-directory/roles/permissions-reference#security-operator).</span></span>|
|<span data-ttu-id="e7b85-152">**Lecteur de sécurité**</span><span class="sxs-lookup"><span data-stu-id="e7b85-152">**Security reader**</span></span>|<span data-ttu-id="e7b85-153">Consulte et examine les menaces actives envers vos utilisateurs, appareils et contenus Microsoft 365, mais, contrairement à l’opérateur de sécurité, il n’est pas autorisé à répondre par une action.</span><span class="sxs-lookup"><span data-stu-id="e7b85-153">View and investigate active threats to your Microsoft 365 users, devices, and content, but (unlike the Security operator) they do not have permissions to respond by taking action.</span></span> <span data-ttu-id="e7b85-154">Pour plus d’informations, voir la section [Lecteur de sécurité](/azure/active-directory/roles/permissions-reference#security-reader).</span><span class="sxs-lookup"><span data-stu-id="e7b85-154">For more information, see [Security Reader](/azure/active-directory/roles/permissions-reference#security-reader).</span></span>|
|<span data-ttu-id="e7b85-155">**Administrateur de sécurité**</span><span class="sxs-lookup"><span data-stu-id="e7b85-155">**Security administrator**</span></span>|<span data-ttu-id="e7b85-156">Contrôle la sécurité globale de votre organisation en gérant les stratégies de sécurité, en examinant les analyses de la sécurité et les rapports sur les produits Microsoft 365 et en se tenant à jour sur les menaces.</span><span class="sxs-lookup"><span data-stu-id="e7b85-156">Control your organization's overall security by managing security policies, reviewing security analytics and reports across Microsoft 365 products, and staying up-to-speed on the threat landscape.</span></span> <span data-ttu-id="e7b85-157">Pour plus d’informations, voir la section [Administrateur de sécurité](/azure/active-directory/roles/permissions-reference#security-administrator).</span><span class="sxs-lookup"><span data-stu-id="e7b85-157">For more information, see [Security Administrator](/azure/active-directory/roles/permissions-reference#security-administrator).</span></span>|
|<span data-ttu-id="e7b85-158">**Lecteur général**</span><span class="sxs-lookup"><span data-stu-id="e7b85-158">**Global reader**</span></span>|<span data-ttu-id="e7b85-159">Version en lecture seule du rôle **Administrateur général**.</span><span class="sxs-lookup"><span data-stu-id="e7b85-159">The read-only version of the **Global administrator** role.</span></span> <span data-ttu-id="e7b85-160">Affiche tous les paramètres et informations administratives dans Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="e7b85-160">View all settings and administrative information across Microsoft 365.</span></span> <span data-ttu-id="e7b85-161">Pour plus d’informations, consultez [Lecteur général](/azure/active-directory/roles/permissions-reference#global-reader).</span><span class="sxs-lookup"><span data-stu-id="e7b85-161">For more information, see [Global Reader](/azure/active-directory/roles/permissions-reference#global-reader).</span></span>|
|<span data-ttu-id="e7b85-162">**Administrateur de simulation d’attaque**</span><span class="sxs-lookup"><span data-stu-id="e7b85-162">**Attack simulation administrator**</span></span>|<span data-ttu-id="e7b85-163">Créez et gérez tous les aspects de la création[simulation d’attaque](attack-simulation-training.md), le lancement/la planification d’une simulation et l’examen des résultats de la simulation.</span><span class="sxs-lookup"><span data-stu-id="e7b85-163">Create and manage all aspects of [attack simulation](attack-simulation-training.md) creation, launch/scheduling of a simulation, and the review of simulation results.</span></span> <span data-ttu-id="e7b85-164">Pour plus d’informations, consultez [Administrateur de simulation d’attaques](/azure/active-directory/roles/permissions-reference#attack-simulation-administrator).</span><span class="sxs-lookup"><span data-stu-id="e7b85-164">For more information, see [Attack Simulation Administrator](/azure/active-directory/roles/permissions-reference#attack-simulation-administrator).</span></span>|
|<span data-ttu-id="e7b85-165">**Auteur de la charge utile d’attaque**</span><span class="sxs-lookup"><span data-stu-id="e7b85-165">**Attack payload author**</span></span>|<span data-ttu-id="e7b85-166">Créez des charges utiles d’attaque, mais ne les lancez pas ou ne planifiez pas réellement.</span><span class="sxs-lookup"><span data-stu-id="e7b85-166">Create attack payloads but not actually launch or schedule them.</span></span> <span data-ttu-id="e7b85-167">Pour plus d’informations, consultez [Auteur de charge utile d’attaque](/azure/active-directory/roles/permissions-reference#attack-payload-author).</span><span class="sxs-lookup"><span data-stu-id="e7b85-167">For more information, see [Attack Payload Author](/azure/active-directory/roles/permissions-reference#attack-payload-author).</span></span>|
|

### <a name="email--collaboration-roles-in-the-security-center"></a><span data-ttu-id="e7b85-168">Rôles de messagerie et de collaboration dans le centre de sécurité</span><span class="sxs-lookup"><span data-stu-id="e7b85-168">Email & collaboration roles in the security center</span></span>

<span data-ttu-id="e7b85-169">Lorsque vous accédez à **Rôles de messagerie et de collaboration** \> **Autorisations et rôles** \> **Rôles de messagerie et de collaboration** \> **Rôles** (ou directement à <https://security.microsoft.com/emailandcollabpermissions>), vous voyez les mêmes groupes de rôles disponibles dans le Centre de sécurité et de conformité.</span><span class="sxs-lookup"><span data-stu-id="e7b85-169">When you go to **Email & collaboration roles** \> **Permissions & roles** \> **Email & collaboration roles** \> **Roles** (or directly to <https://security.microsoft.com/emailandcollabpermissions>) you'll see the same role groups that are available in the Security & Compliance Center.</span></span>

<span data-ttu-id="e7b85-170">Pour plus d’informations sur ces groupes de rôles, consultez [Autorisations dans le Centre de Sécurité et de Conformité](permissions-in-the-security-and-compliance-center.md).</span><span class="sxs-lookup"><span data-stu-id="e7b85-170">For complete information about these role groups, see [Permissions in the Security & Compliance Center](permissions-in-the-security-and-compliance-center.md)</span></span>

#### <a name="modify-email--collaboration-role-membership-in-the-security-center"></a><span data-ttu-id="e7b85-171">Modifier l’appartenance au Rôle e-mail et collaboration dans le centre de sécurité</span><span class="sxs-lookup"><span data-stu-id="e7b85-171">Modify Email & collaboration role membership in the security center</span></span>

1. <span data-ttu-id="e7b85-172">Dans le centre de sécurité, accédez à **Rôles d’e-mail et de collaboration** \> **Autorisations et rôles** \> **Rôles d’e-mail et rôles de collaboration** \> **Rôles**.</span><span class="sxs-lookup"><span data-stu-id="e7b85-172">In the security center, go to **Email & collaboration roles** \> **Permissions & roles** \> **Email & collaboration roles** \> **Roles**.</span></span>

2. <span data-ttu-id="e7b85-173">Dans la page **Autorisations** qui s’ouvre, sélectionnez le groupe de rôles que vous souhaitez modifier dans la liste.</span><span class="sxs-lookup"><span data-stu-id="e7b85-173">In the **Permissions** page that opens, select the role group that you want to modify from the list.</span></span> <span data-ttu-id="e7b85-174">Vous pouvez cliquer sur l’en-tête de colonne **Nom** pour trier la liste par nom, ou cliquer sur **Rechercher** ![Icône rechercher](../../media/m365-cc-sc-search-icon.png) pour rechercher le groupe de rôles.</span><span class="sxs-lookup"><span data-stu-id="e7b85-174">You can click on the **Name** column header to sort the list by name, or you can click **Search** ![Search icon](../../media/m365-cc-sc-search-icon.png) to find the role group.</span></span>

3. <span data-ttu-id="e7b85-175">Dans le menu volant des détails de groupe de rôles qui s’affiche, cliquez sur **Modifier** dans la section **Membres**.</span><span class="sxs-lookup"><span data-stu-id="e7b85-175">In the role group details flyout that appears, click **Edit** in the **Members** section.</span></span>

4. <span data-ttu-id="e7b85-176">Dans la page **Modifier Choisir les membres** qui s’affiche, effectuez l’une des étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="e7b85-176">In the **Editing choose members** page that appears, do one of the following steps:</span></span>
   - <span data-ttu-id="e7b85-177">S’il n’existe aucun membre de groupe de rôles, cliquez sur **Choisir des membres**.</span><span class="sxs-lookup"><span data-stu-id="e7b85-177">If there are no role group members, click **Choose members**.</span></span>
   - <span data-ttu-id="e7b85-178">S’il existe des membres de groupe de rôles, cliquez sur **Modifier**.</span><span class="sxs-lookup"><span data-stu-id="e7b85-178">If there are existing role group members, click **Edit**</span></span>

5. <span data-ttu-id="e7b85-179">Dans la page **Choisir les membres** qui s’affiche, effectuez l’une des étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="e7b85-179">In the **Choose members** flyout that appears, do one of the following steps:</span></span>

   - <span data-ttu-id="e7b85-180">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="e7b85-180">Click **Add**.</span></span> <span data-ttu-id="e7b85-181">Dans la liste des utilisateurs qui s’affiche, sélectionnez un ou plusieurs utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="e7b85-181">In the list of users that appears, select one or more users.</span></span> <span data-ttu-id="e7b85-182">Vous pouvez également cliquer sur **Rechercher** ![Icône rechercher](../../media/m365-cc-sc-search-icon.png) pour rechercher et sélectionner des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="e7b85-182">Or, you can click **Search** ![Search icon](../../media/m365-cc-sc-search-icon.png) to find and select users.</span></span>

     <span data-ttu-id="e7b85-183">Une fois que vous avez sélectionné les utilisateurs que vous souhaitez ajouter, cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="e7b85-183">When you've selected the users that you want to add, click **Add**.</span></span>

   - <span data-ttu-id="e7b85-184">Cliquez sur **Supprimer**.</span><span class="sxs-lookup"><span data-stu-id="e7b85-184">Click **Remove**.</span></span> <span data-ttu-id="e7b85-185">Sélectionnez un ou plusieurs des membres existants.</span><span class="sxs-lookup"><span data-stu-id="e7b85-185">Select one or more of the existing members.</span></span> <span data-ttu-id="e7b85-186">Vous pouvez également cliquer sur **Rechercher** ![Icône rechercher](../../media/m365-cc-sc-search-icon.png) pour rechercher et sélectionner des membres.</span><span class="sxs-lookup"><span data-stu-id="e7b85-186">Or, you can click **Search** ![Search icon](../../media/m365-cc-sc-search-icon.png) to find and select members.</span></span>

     <span data-ttu-id="e7b85-187">Une fois que vous avez sélectionné les utilisateurs que vous souhaitez supprimer, cliquez sur **Supprimer**.</span><span class="sxs-lookup"><span data-stu-id="e7b85-187">When you've selected the users that you want to remove, click **Remove**.</span></span>

6. <span data-ttu-id="e7b85-188">De retour dans le menu volant **Choisir des membres** , cliquez sur **Terminé**.</span><span class="sxs-lookup"><span data-stu-id="e7b85-188">Back on the **Choose members** flyout, click **Done**.</span></span>

7. <span data-ttu-id="e7b85-189">Sur le page **Modifier Choisir les membres**, cliquez sur **Sauvegarder**.</span><span class="sxs-lookup"><span data-stu-id="e7b85-189">Back on the **Editing choose members** page, click **Save**.</span></span>

8. <span data-ttu-id="e7b85-190">Dans le menu volant détails du groupe de rôles, cliquez sur **Terminé**.</span><span class="sxs-lookup"><span data-stu-id="e7b85-190">Back on the role group details flyout, click **Done**.</span></span>