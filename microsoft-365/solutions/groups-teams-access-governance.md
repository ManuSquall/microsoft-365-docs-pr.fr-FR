---
title: Administration des accès dans les groupes Microsoft 365, teams et SharePoint
ms.reviewer: ''
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-collaboration
ms.custom:
- M365solutions
f1.keywords: NOCSH
description: Découvrez comment régir l’accès dans les groupes Microsoft 365, teams et SharePoint.
ms.openlocfilehash: 8b58016ffa421328e3c1442d4ed2364f2eedc37b
ms.sourcegitcommit: 66f1f430b3dcae5f46cb362a32d6fb7da4cff5c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2020
ms.locfileid: "46662615"
---
# <a name="governing-access-in-microsoft-365-groups-teams-and-sharepoint"></a><span data-ttu-id="bad6a-103">Administration des accès dans les groupes Microsoft 365, teams et SharePoint</span><span class="sxs-lookup"><span data-stu-id="bad6a-103">Governing access in Microsoft 365 groups, Teams, and SharePoint</span></span>

<span data-ttu-id="bad6a-104">De nombreux contrôles vous permettent de contrôler la manière dont les utilisateurs accèdent aux ressources dans des groupes, des équipes et de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="bad6a-104">There are many controls that enable you to govern how people access resources in groups, teams, and SharePoint.</span></span> <span data-ttu-id="bad6a-105">Passez en revue ces options et réfléchissez à la façon dont elles correspondent à vos besoins professionnels, à la sensibilité de vos données et à l’étendue des personnes avec lesquelles vos utilisateurs doivent collaborer.</span><span class="sxs-lookup"><span data-stu-id="bad6a-105">Review these options and consider how they map to your business needs, the sensitivity of your data, and the scope of people that your users need to collaborate with.</span></span>

<span data-ttu-id="bad6a-106">Le tableau suivant fournit un guide de référence rapide pour les contrôles d’accès disponibles dans Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="bad6a-106">The following table provides a quick reference for the access controls available in Microsoft 365.</span></span> <span data-ttu-id="bad6a-107">Pour plus d’informations, reportez-vous aux sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="bad6a-107">Further information is provided in the following sections.</span></span>

|<span data-ttu-id="bad6a-108">Catégorie</span><span class="sxs-lookup"><span data-stu-id="bad6a-108">Category</span></span>|<span data-ttu-id="bad6a-109">Description</span><span class="sxs-lookup"><span data-stu-id="bad6a-109">Description</span></span>|<span data-ttu-id="bad6a-110">Référence</span><span class="sxs-lookup"><span data-stu-id="bad6a-110">Reference</span></span>|
|:-------|:----------|:--------|
|<span data-ttu-id="bad6a-111">Appartenance</span><span class="sxs-lookup"><span data-stu-id="bad6a-111">Membership</span></span>|||
||<span data-ttu-id="bad6a-112">Découverte de teams privées</span><span class="sxs-lookup"><span data-stu-id="bad6a-112">Discovery of private teams</span></span>|[<span data-ttu-id="bad6a-113">Gestion de la découverte de teams privées dans Microsoft teams</span><span class="sxs-lookup"><span data-stu-id="bad6a-113">Manage discovery of private teams in Microsoft Teams</span></span>](https://docs.microsoft.com/microsoftteams/manage-discovery-of-private-teams)|
||<span data-ttu-id="bad6a-114">Appartenance à un groupe dynamique basée sur des règles</span><span class="sxs-lookup"><span data-stu-id="bad6a-114">Dynamic group membership based on rules</span></span>|[<span data-ttu-id="bad6a-115">Créer ou mettre à jour un groupe dynamique dans Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="bad6a-115">Create or update a dynamic group in Azure Active Directory</span></span>](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-create-rule)|
||<span data-ttu-id="bad6a-116">Contrôlez les personnes qui peuvent partager des fichiers, des dossiers et des sites.</span><span class="sxs-lookup"><span data-stu-id="bad6a-116">Control who can share files, folders, and sites.</span></span>|[<span data-ttu-id="bad6a-117">Configurer et gérer les demandes d’accès</span><span class="sxs-lookup"><span data-stu-id="bad6a-117">Set up and manage access requests</span></span>](https://support.microsoft.com/office/94b26e0b-2822-49d4-929a-8455698654b3)|
|<span data-ttu-id="bad6a-118">Accès conditionnel</span><span class="sxs-lookup"><span data-stu-id="bad6a-118">Conditional access</span></span>|||
||<span data-ttu-id="bad6a-119">Authentification multifacteur</span><span class="sxs-lookup"><span data-stu-id="bad6a-119">Multi-Factor Authentication</span></span>|[<span data-ttu-id="bad6a-120">Azure Multi-Factor Authentication</span><span class="sxs-lookup"><span data-stu-id="bad6a-120">Azure Multi-Factor Authentication</span></span>](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks)|
||<span data-ttu-id="bad6a-121">Contrôler l’accès aux périphériques en fonction de la sensibilité du groupe, de l’équipe ou du site.</span><span class="sxs-lookup"><span data-stu-id="bad6a-121">Control device access based on group, team, or site sensitivity.</span></span>|[<span data-ttu-id="bad6a-122">Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint</span><span class="sxs-lookup"><span data-stu-id="bad6a-122">Use sensitivity labels to protect content in Microsoft Teams, Microsoft 365 groups, and SharePoint sites</span></span>](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites)|
||<span data-ttu-id="bad6a-123">Limitez l’accès au site pour les appareils non gérés.</span><span class="sxs-lookup"><span data-stu-id="bad6a-123">Limit site access for unmanaged devices.</span></span>|[<span data-ttu-id="bad6a-124">Contrôler l’accès à SharePoint à partir d’appareils non gérés</span><span class="sxs-lookup"><span data-stu-id="bad6a-124">Control SharePoint access from unmanaged devices</span></span>](https://docs.microsoft.com/sharepoint/control-access-from-unmanaged-devices)|
||<span data-ttu-id="bad6a-125">Contrôler l’accès au site en fonction de l’emplacement</span><span class="sxs-lookup"><span data-stu-id="bad6a-125">Control site access based on location</span></span>|[<span data-ttu-id="bad6a-126">Contrôler l’accès aux données SharePoint et OneDrive en fonction de l’emplacement réseau</span><span class="sxs-lookup"><span data-stu-id="bad6a-126">Control access to SharePoint and OneDrive data based on network location</span></span>](https://docs.microsoft.com/sharepoint/control-access-based-on-network-location)|
|<span data-ttu-id="bad6a-127">Accès invité</span><span class="sxs-lookup"><span data-stu-id="bad6a-127">Guest access</span></span>|||
||<span data-ttu-id="bad6a-128">Autoriser ou bloquer le partage SharePoint à partir de domaines spécifiés.</span><span class="sxs-lookup"><span data-stu-id="bad6a-128">Allow or block SharePoint sharing from specified domains.</span></span>|[<span data-ttu-id="bad6a-129">Restreindre le partage de contenu SharePoint et OneDrive par domaine</span><span class="sxs-lookup"><span data-stu-id="bad6a-129">Restrict sharing of SharePoint and OneDrive content by domain</span></span>](https://docs.microsoft.com/sharepoint/restricted-domains-sharing)|
||<span data-ttu-id="bad6a-130">Autoriser ou bloquer l’appartenance d’une équipe ou d’un groupe à des domaines spécifiés.</span><span class="sxs-lookup"><span data-stu-id="bad6a-130">Allow or block team or group membership from specified domains.</span></span>|[<span data-ttu-id="bad6a-131">Autoriser ou bloquer des invitations à des utilisateurs B2B d’organisations spécifiques</span><span class="sxs-lookup"><span data-stu-id="bad6a-131">Allow or block invitations to B2B users from specific organizations</span></span>](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)|
||<span data-ttu-id="bad6a-132">Empêcher le partage anonyme.</span><span class="sxs-lookup"><span data-stu-id="bad6a-132">Prevent anonymous sharing.</span></span>|[<span data-ttu-id="bad6a-133">Désactiver les liens Tout le monde</span><span class="sxs-lookup"><span data-stu-id="bad6a-133">Turn off Anyone links</span></span>](https://docs.microsoft.com/microsoft-365/solutions/share-limit-accidental-exposure#turn-off-anyone-links)|
||<span data-ttu-id="bad6a-134">Contrôler les autorisations pour les liens d’accès anonyme.</span><span class="sxs-lookup"><span data-stu-id="bad6a-134">Control the permissions for anonymous access links.</span></span>|[<span data-ttu-id="bad6a-135">Définir les autorisations de liens pour tous les liens</span><span class="sxs-lookup"><span data-stu-id="bad6a-135">Set link permissions for Anyone links</span></span>](https://docs.microsoft.com/microsoft-365/solutions/best-practices-anonymous-sharing#set-link-permissions)|
||<span data-ttu-id="bad6a-136">Contrôler l’expiration des liens de partage anonyme.</span><span class="sxs-lookup"><span data-stu-id="bad6a-136">Control the expiration of anonymous sharing links.</span></span>|[<span data-ttu-id="bad6a-137">Définir une date d’expiration pour les liens Tout le monde</span><span class="sxs-lookup"><span data-stu-id="bad6a-137">Set an expiration date for Anyone links</span></span>](https://docs.microsoft.com/microsoft-365/solutions/best-practices-anonymous-sharing#set-an-expiration-date-for-anyone-links)|
||<span data-ttu-id="bad6a-138">Contrôler le type de lien de partage affiché par défaut aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="bad6a-138">Control the type of sharing link shown to users by default.</span></span>|[<span data-ttu-id="bad6a-139">Modifier le type de lien par défaut d’un site</span><span class="sxs-lookup"><span data-stu-id="bad6a-139">Change the default link type for a site</span></span>](https://docs.microsoft.com/sharepoint/change-default-sharing-link)|
||<span data-ttu-id="bad6a-140">Limitez le partage externe à des personnes spécifiques.</span><span class="sxs-lookup"><span data-stu-id="bad6a-140">Limit external sharing to specific people.</span></span>|[<span data-ttu-id="bad6a-141">Limiter le partage externe aux groupes de sécurité spécifiés</span><span class="sxs-lookup"><span data-stu-id="bad6a-141">Limit external sharing to specified security groups</span></span>](https://docs.microsoft.com/microsoft-365/solutions/share-limit-accidental-exposure#limit-sharing-of-files-folders-and-sites-with-people-outside-your-organization-to-specified-security-groups)|
||<span data-ttu-id="bad6a-142">Contrôler l’accès invité à un groupe, une équipe ou un site en fonction de la sensibilité aux informations.</span><span class="sxs-lookup"><span data-stu-id="bad6a-142">Control guest access to a group, team, or site based on information sensitivity.</span></span>|[<span data-ttu-id="bad6a-143">Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint</span><span class="sxs-lookup"><span data-stu-id="bad6a-143">Use sensitivity labels to protect content in Microsoft Teams, Microsoft 365 groups, and SharePoint sites</span></span>](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites)|
||<span data-ttu-id="bad6a-144">Désactivez les options de partage.</span><span class="sxs-lookup"><span data-stu-id="bad6a-144">Turn off sharing options.</span></span>|[<span data-ttu-id="bad6a-145">Limiter le partage dans Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="bad6a-145">Limit sharing in Microsoft 365</span></span>](https://docs.microsoft.com/microsoft-365/solutions/microsoft-365-limit-sharing)|
|<span data-ttu-id="bad6a-146">Gestion des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="bad6a-146">User management</span></span>|||
||<span data-ttu-id="bad6a-147">Examinez les membres de l’équipe et du groupe régulièrement.</span><span class="sxs-lookup"><span data-stu-id="bad6a-147">Review team and group membership on a regular basis.</span></span>|[<span data-ttu-id="bad6a-148">Qu’est-ce que les révisions Azure AD Access ?</span><span class="sxs-lookup"><span data-stu-id="bad6a-148">What are Azure AD access reviews?</span></span>](https://docs.microsoft.com/azure/active-directory/governance/access-reviews-overview)|
||<span data-ttu-id="bad6a-149">Automatiser la gestion des accès aux groupes et aux équipes.</span><span class="sxs-lookup"><span data-stu-id="bad6a-149">Automate access management to groups and teams.</span></span>|[<span data-ttu-id="bad6a-150">Qu’est-ce que la gestion des droits Azure AD ?</span><span class="sxs-lookup"><span data-stu-id="bad6a-150">What is Azure AD entitlement management?</span></span>](https://docs.microsoft.com/azure/active-directory/governance/entitlement-management-overview)|
||<span data-ttu-id="bad6a-151">Autoriser ou empêcher des personnes de créer des canaux privés dans Teams.</span><span class="sxs-lookup"><span data-stu-id="bad6a-151">Allow or block people from creating private channels in Teams.</span></span>|[<span data-ttu-id="bad6a-152">Gérer le cycle de vie des canaux privés dans Microsoft teams</span><span class="sxs-lookup"><span data-stu-id="bad6a-152">Manage the life cycle of private channels in Microsoft Teams</span></span>](https://docs.microsoft.com/MicrosoftTeams/private-channels-life-cycle-management)|

## <a name="membership"></a><span data-ttu-id="bad6a-153">Appartenance</span><span class="sxs-lookup"><span data-stu-id="bad6a-153">Membership</span></span>

<span data-ttu-id="bad6a-154">L’appartenance aux équipes et aux groupes est contrôlée par les propriétaires.</span><span class="sxs-lookup"><span data-stu-id="bad6a-154">Membership of teams and groups is controlled by owners.</span></span> <span data-ttu-id="bad6a-155">Les membres peuvent inviter d’autres personnes, mais les invitations sont envoyées aux propriétaires pour approbation.</span><span class="sxs-lookup"><span data-stu-id="bad6a-155">Members can invite others, but the invitations are sent to owners for approval.</span></span> <span data-ttu-id="bad6a-156">Bien que les groupes et les équipes publiques soient détectables par tous les utilisateurs de l’organisation, vous pouvez contrôler si des équipes et des groupes privés sont détectables :</span><span class="sxs-lookup"><span data-stu-id="bad6a-156">While public teams and groups are discoverable by anyone in the organization, you can control whether private teams and groups are discoverable:</span></span>

- [<span data-ttu-id="bad6a-157">Gestion de la découverte de teams privées dans Microsoft teams</span><span class="sxs-lookup"><span data-stu-id="bad6a-157">Manage discovery of private teams in Microsoft Teams</span></span>](https://docs.microsoft.com/microsoftteams/manage-discovery-of-private-teams)

<span data-ttu-id="bad6a-158">Vous pouvez gérer l’appartenance d’un groupe ou d’une équipe de manière dynamique en fonction de certains critères, tels que le service.</span><span class="sxs-lookup"><span data-stu-id="bad6a-158">You can manage membership of a group or team dynamically based on some criteria, such as department.</span></span> <span data-ttu-id="bad6a-159">Dans ce cas, les membres et les propriétaires ne peuvent pas inviter des personnes à l’équipe.</span><span class="sxs-lookup"><span data-stu-id="bad6a-159">In this case, members and owners cannot invite people to the team.</span></span>

- [<span data-ttu-id="bad6a-160">Créer ou mettre à jour un groupe dynamique dans Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="bad6a-160">Create or update a dynamic group in Azure Active Directory</span></span>](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-create-rule)

<span data-ttu-id="bad6a-161">Les sites SharePoint offrent la possibilité d’ajouter des propriétaires, des membres et des visiteurs indépendamment de l’appartenance à un groupe ou d’une équipe.</span><span class="sxs-lookup"><span data-stu-id="bad6a-161">SharePoint sites provide the ability to add owners, members, and visitors apart from group or team membership.</span></span> <span data-ttu-id="bad6a-162">En fonction de vos besoins, vous pouvez décider qui peut inviter des personnes sur le site.</span><span class="sxs-lookup"><span data-stu-id="bad6a-162">Depending on your requirements, you may want to restrict who can invite people to the site.</span></span> <span data-ttu-id="bad6a-163">En outre, en fonction de la sensibilité des informations d’un site donné, vous pouvez limiter les personnes qui peuvent partager des fichiers et des dossiers.</span><span class="sxs-lookup"><span data-stu-id="bad6a-163">Also, depending on the sensitivity of the information in a given site, you may want to restrict who can share files and folder.</span></span> <span data-ttu-id="bad6a-164">Ces restrictions sont configurées par le propriétaire de l’équipe, du groupe ou du site :</span><span class="sxs-lookup"><span data-stu-id="bad6a-164">These restrictions are configured by the team, group, or site owner:</span></span>

- [<span data-ttu-id="bad6a-165">Configurer et gérer les demandes d’accès</span><span class="sxs-lookup"><span data-stu-id="bad6a-165">Set up and manage access requests</span></span>](https://support.microsoft.com/office/94b26e0b-2822-49d4-929a-8455698654b3)


## <a name="conditional-access"></a><span data-ttu-id="bad6a-166">Accès conditionnel</span><span class="sxs-lookup"><span data-stu-id="bad6a-166">Conditional access</span></span>

<span data-ttu-id="bad6a-167">Avec Microsoft 365, vous pouvez exiger l’authentification multifacteur pour les deux personnes à l’intérieur et à l’extérieur de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="bad6a-167">With Microsoft 365, you can require multi-factor authentication for both people inside and outside your organization.</span></span> <span data-ttu-id="bad6a-168">Il existe de nombreuses options pour les circonstances dans lesquelles les utilisateurs sont invités à spécifier un deuxième facteur d’authentification.</span><span class="sxs-lookup"><span data-stu-id="bad6a-168">There are many options for the circumstances when people are prompted for a second factor of authentication.</span></span> <span data-ttu-id="bad6a-169">Nous vous recommandons vivement de déployer l’authentification multifacteur pour votre organisation :</span><span class="sxs-lookup"><span data-stu-id="bad6a-169">We highly recommend that you deploy multi-factor authentication for your organization:</span></span>

- [<span data-ttu-id="bad6a-170">Azure Multi-Factor Authentication</span><span class="sxs-lookup"><span data-stu-id="bad6a-170">Azure Multi-Factor Authentication</span></span>](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks)

<span data-ttu-id="bad6a-171">Si vous avez des informations sensibles dans certains de vos groupes et équipes, vous pouvez appliquer des stratégies de gestion des appareils en fonction de l’étiquette de confidentialité d’une équipe ou d’un groupe.</span><span class="sxs-lookup"><span data-stu-id="bad6a-171">If you have sensitive information in some of your groups and teams, you can enforce device management policies based on a group or team's sensitivity label.</span></span> <span data-ttu-id="bad6a-172">Vous pouvez bloquer l’accès à partir d’appareils non gérés ou accorder un accès limité au Web uniquement :</span><span class="sxs-lookup"><span data-stu-id="bad6a-172">You can block access entirely from unmanaged devices, or allow limited, web only access:</span></span>

- [<span data-ttu-id="bad6a-173">Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint</span><span class="sxs-lookup"><span data-stu-id="bad6a-173">Use sensitivity labels to protect content in Microsoft Teams, Microsoft 365 groups, and SharePoint sites</span></span>](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites)

<span data-ttu-id="bad6a-174">Dans SharePoint, vous pouvez restreindre l’accès aux sites à partir des emplacements réseau spécifiés.</span><span class="sxs-lookup"><span data-stu-id="bad6a-174">In SharePoint, you can restrict access to sites from specified network locations.</span></span>

- [<span data-ttu-id="bad6a-175">Contrôler l’accès aux données SharePoint et OneDrive en fonction de l’emplacement réseau</span><span class="sxs-lookup"><span data-stu-id="bad6a-175">Control access to SharePoint and OneDrive data based on network location</span></span>](https://docs.microsoft.com/sharepoint/control-access-based-on-network-location)


<span data-ttu-id="bad6a-176">Ressources supplémentaires :</span><span class="sxs-lookup"><span data-stu-id="bad6a-176">Additional resources:</span></span>

- [<span data-ttu-id="bad6a-177">Planifier un déploiement d’accès conditionnel</span><span class="sxs-lookup"><span data-stu-id="bad6a-177">Plan a Conditional Access deployment</span></span>](https://docs.microsoft.com/azure/active-directory/conditional-access/plan-conditional-access)

- [<span data-ttu-id="bad6a-178">Vue d’ensemble de Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="bad6a-178">Microsoft Intune overview</span></span>](https://docs.microsoft.com/mem/intune/fundamentals/what-is-intune)

- [<span data-ttu-id="bad6a-179">Contrôler l’accès à SharePoint à partir d’appareils non gérés</span><span class="sxs-lookup"><span data-stu-id="bad6a-179">Control SharePoint access from unmanaged devices</span></span>](https://docs.microsoft.com/sharepoint/control-access-from-unmanaged-devices)


## <a name="guest-access"></a><span data-ttu-id="bad6a-180">Accès invité</span><span class="sxs-lookup"><span data-stu-id="bad6a-180">Guest access</span></span>

<span data-ttu-id="bad6a-181">Vous pouvez restreindre les invités en fonction du domaine de leur adresse de messagerie.</span><span class="sxs-lookup"><span data-stu-id="bad6a-181">You can restrict guests based on the domain of their email address.</span></span> <span data-ttu-id="bad6a-182">SharePoint propose des paramètres de restriction de domaine spécifiques à l’échelle de l’organisation et de votre site.</span><span class="sxs-lookup"><span data-stu-id="bad6a-182">SharePoint offers organization-wide and site-specific domain restriction settings.</span></span> <span data-ttu-id="bad6a-183">Les groupes et les équipes utilisent les listes d’autorisation et de refus de domaine dans Azure AD.</span><span class="sxs-lookup"><span data-stu-id="bad6a-183">Groups and Teams use the domain allow and deny lists in Azure AD.</span></span> <span data-ttu-id="bad6a-184">Veillez à configurer les deux paramètres pour éviter un partage indésirable et garantir une expérience utilisateur cohérente :</span><span class="sxs-lookup"><span data-stu-id="bad6a-184">Be sure to configure both settings to avoid unwanted sharing and ensure a consistent user experience:</span></span>

- [<span data-ttu-id="bad6a-185">Restreindre le partage de contenu SharePoint et OneDrive par domaine</span><span class="sxs-lookup"><span data-stu-id="bad6a-185">Restrict sharing of SharePoint and OneDrive content by domain</span></span>](https://docs.microsoft.com/sharepoint/restricted-domains-sharing)

- [<span data-ttu-id="bad6a-186">Autoriser ou bloquer des invitations à des utilisateurs B2B d’organisations spécifiques</span><span class="sxs-lookup"><span data-stu-id="bad6a-186">Allow or block invitations to B2B users from specific organizations</span></span>](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)

<span data-ttu-id="bad6a-187">Microsoft 365 autorise le partage anonyme de fichiers et de dossiers *à l’aide* de liens de partage.</span><span class="sxs-lookup"><span data-stu-id="bad6a-187">Microsoft 365 allows anonymous sharing of files and folders by using *Anyone* sharing links.</span></span> <span data-ttu-id="bad6a-188">Les liens *tout le monde* peuvent être transférés et quiconque disposant du lien peut accéder à l’élément partagé.</span><span class="sxs-lookup"><span data-stu-id="bad6a-188">*Anyone* links can be forwarded and anyone with the link can access the shared item.</span></span> <span data-ttu-id="bad6a-189">En fonction de la sensibilité de vos données, vous devez prendre en compte le mode d’utilisation des liens *tout le monde* , notamment leur désactivation complète, la restriction des autorisations de liaison en lecture seule ou la définition d’un délai d’expiration pour eux :</span><span class="sxs-lookup"><span data-stu-id="bad6a-189">Depending on the sensitivity of your data, consider governing how *Anyone* links are used - including turning them off entirely, restricting link permissions to read-only, or setting an expiration time for them:</span></span>

- [<span data-ttu-id="bad6a-190">Désactiver les liens Tout le monde</span><span class="sxs-lookup"><span data-stu-id="bad6a-190">Turn off Anyone links</span></span>](https://docs.microsoft.com/microsoft-365/solutions/share-limit-accidental-exposure#turn-off-anyone-links)

- [<span data-ttu-id="bad6a-191">Définir les autorisations de liens pour tous les liens</span><span class="sxs-lookup"><span data-stu-id="bad6a-191">Set link permissions for Anyone links</span></span>](https://docs.microsoft.com/microsoft-365/solutions/best-practices-anonymous-sharing#set-link-permissions)

- [<span data-ttu-id="bad6a-192">Définir une date d’expiration pour les liens Tout le monde</span><span class="sxs-lookup"><span data-stu-id="bad6a-192">Set an expiration date for Anyone links</span></span>](https://docs.microsoft.com/microsoft-365/solutions/best-practices-anonymous-sharing#set-an-expiration-date-for-anyone-links)

<span data-ttu-id="bad6a-193">Lors du partage de fichiers ou de dossiers, les utilisateurs ont le choix entre plusieurs types de liens.</span><span class="sxs-lookup"><span data-stu-id="bad6a-193">When sharing files or folders, users have several link types to choose from.</span></span> <span data-ttu-id="bad6a-194">Pour réduire le risque de partage accidentel inapproprié, vous pouvez modifier le type de lien par défaut présenté aux utilisateurs lorsqu’ils sont partagés.</span><span class="sxs-lookup"><span data-stu-id="bad6a-194">To reduce the risk of accidental inappropriate sharing, you can change the default link type presented to users when they share.</span></span> <span data-ttu-id="bad6a-195">Par exemple, la modification de la valeur par défaut à partir de liens *tout utilisateur* , qui autorise l’accès anonyme à des *personnes dans votre organisation* , permet de réduire le risque de partage externe indésirable d’informations sensibles :</span><span class="sxs-lookup"><span data-stu-id="bad6a-195">For example, changing the default from *Anyone* links - which allow anonymous access - to *People in your organization* links can reduce the risk of unwanted external sharing of sensitive information:</span></span>

- [<span data-ttu-id="bad6a-196">Modifier le type de lien par défaut d’un site</span><span class="sxs-lookup"><span data-stu-id="bad6a-196">Change the default link type for a site</span></span>](https://docs.microsoft.com/sharepoint/change-default-sharing-link)

<span data-ttu-id="bad6a-197">Si votre organisation a des données sensibles que vous devez partager avec des invités, mais que vous êtes préoccupé par le partage inapproprié, vous pouvez limiter le partage externe des fichiers et des dossiers aux membres des groupes de sécurité spécifiés.</span><span class="sxs-lookup"><span data-stu-id="bad6a-197">If your organization has sensitive data that you need to share with guests, but you're concerned about inappropriate sharing, you can limit external sharing of files and folders to the members of specified security groups.</span></span> <span data-ttu-id="bad6a-198">De cette manière, vous pouvez limiter le partage externe à un groupe spécifique de personnes ou demander à vos utilisateurs de suivre une formation sur le partage externe approprié avant de les ajouter au groupe de sécurité :</span><span class="sxs-lookup"><span data-stu-id="bad6a-198">In this way, you can restrict sharing externally to a specific group of people, or require your users to take training around appropriate external sharing before adding them to the security group:</span></span>

- [<span data-ttu-id="bad6a-199">Limiter le partage externe aux groupes de sécurité spécifiés</span><span class="sxs-lookup"><span data-stu-id="bad6a-199">Limit external sharing to specified security groups</span></span>](https://docs.microsoft.com/microsoft-365/solutions/share-limit-accidental-exposure#limit-sharing-of-files-folders-and-sites-with-people-outside-your-organization-to-specified-security-groups)

<span data-ttu-id="bad6a-200">Les groupes et les équipes ont un paramètre au niveau de l’organisation qui autorise ou refuse l’accès invité.</span><span class="sxs-lookup"><span data-stu-id="bad6a-200">Groups and Teams have organization-level setting that allow or deny guest access.</span></span> <span data-ttu-id="bad6a-201">Bien que vous puissiez [restreindre l’accès invité à des équipes ou à des groupes spécifiques à l’aide de Microsoft PowerShell](per-group-guest-access.md), nous vous recommandons d’effectuer cette opération par le biais d’une étiquette de sensibilité.</span><span class="sxs-lookup"><span data-stu-id="bad6a-201">While you can [restrict guest access to specific teams or groups by using Microsoft PowerShell](per-group-guest-access.md), we recommend doing this by means of a sensitivity label.</span></span> <span data-ttu-id="bad6a-202">Avec les étiquettes de sensibilité, vous pouvez autoriser ou refuser automatiquement l’accès invité en fonction de l’étiquette appliquée :</span><span class="sxs-lookup"><span data-stu-id="bad6a-202">With sensitivity labels you can automatically allow or deny guest access based on the label applied:</span></span>

- [<span data-ttu-id="bad6a-203">Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint</span><span class="sxs-lookup"><span data-stu-id="bad6a-203">Use sensitivity labels to protect content in Microsoft Teams, Microsoft 365 groups, and SharePoint sites</span></span>](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites)

<span data-ttu-id="bad6a-204">Microsoft 365 propose de nombreuses méthodes de partage d’informations.</span><span class="sxs-lookup"><span data-stu-id="bad6a-204">Microsoft 365 offers many different methods of sharing information.</span></span> <span data-ttu-id="bad6a-205">Si vous avez des informations sensibles et que vous souhaitez limiter la manière dont elles sont partagées, passez en revue les options permettant de limiter le partage :</span><span class="sxs-lookup"><span data-stu-id="bad6a-205">If you have sensitive information and you want to restrict how it's shared, review the options for limiting sharing:</span></span>

- [<span data-ttu-id="bad6a-206">Limiter le partage dans Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="bad6a-206">Limit sharing in Microsoft 365</span></span>](https://docs.microsoft.com/microsoft-365/solutions/microsoft-365-limit-sharing)

<span data-ttu-id="bad6a-207">Ressources supplémentaires :</span><span class="sxs-lookup"><span data-stu-id="bad6a-207">Additional resources:</span></span>

- [<span data-ttu-id="bad6a-208">Configurer la collaboration sécurisée avec Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="bad6a-208">Set up secure collaboration with Microsoft 365</span></span>](https://docs.microsoft.com/microsoft-365/solutions/setup-secure-collaboration-with-teams)

- [<span data-ttu-id="bad6a-209">Meilleures pratiques relatives au partage de fichiers et de dossiers avec des utilisateurs non authentifiés</span><span class="sxs-lookup"><span data-stu-id="bad6a-209">Best practices for sharing files and folders with unauthenticated users</span></span>](https://docs.microsoft.com/microsoft-365/solutions/best-practices-anonymous-sharing)

- [<span data-ttu-id="bad6a-210">Limiter l’exposition accidentelle de fichiers lors de partages avec des personnes extérieures à votre organisation</span><span class="sxs-lookup"><span data-stu-id="bad6a-210">Limit accidental exposure to files when sharing with people outside your organization</span></span>](https://docs.microsoft.com/microsoft-365/solutions/share-limit-accidental-exposure)

- [<span data-ttu-id="bad6a-211">Créer un environnement de partage sécurisé avec des invités</span><span class="sxs-lookup"><span data-stu-id="bad6a-211">Create a secure guest sharing environment</span></span>](https://docs.microsoft.com/microsoft-365/solutions/create-secure-guest-sharing-environment)

- [<span data-ttu-id="bad6a-212">Activer la collaboration externe B2B et gérer les personnes autorisées à inviter des invités</span><span class="sxs-lookup"><span data-stu-id="bad6a-212">Enable B2B external collaboration and manage who can invite guests</span></span>](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations)

## <a name="user-management"></a><span data-ttu-id="bad6a-213">Gestion des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="bad6a-213">User management</span></span>

<span data-ttu-id="bad6a-214">À mesure que les groupes et les équipes évoluent dans votre organisation, il est recommandé d’examiner régulièrement l’appartenance aux équipes et aux groupes.</span><span class="sxs-lookup"><span data-stu-id="bad6a-214">As groups and teams evolve in your organization, a good practice is to review team and group membership on a regular basis.</span></span> <span data-ttu-id="bad6a-215">Cela peut s’avérer particulièrement utile pour les équipes et les groupes qui changent d’appartenance, ceux qui contiennent des informations sensibles ou ceux qui incluent des invités.</span><span class="sxs-lookup"><span data-stu-id="bad6a-215">This may be particularly useful for teams and groups with a changing membership, those that contain sensitive information, or those that include guests.</span></span> <span data-ttu-id="bad6a-216">Envisagez de configurer les révisions d’accès pour ces équipes et ces groupes :</span><span class="sxs-lookup"><span data-stu-id="bad6a-216">Consider setting up access reviews for these teams and groups:</span></span>

- [<span data-ttu-id="bad6a-217">Qu’est-ce que les révisions Azure AD Access ?</span><span class="sxs-lookup"><span data-stu-id="bad6a-217">What are Azure AD access reviews?</span></span>](https://docs.microsoft.com/azure/active-directory/governance/access-reviews-overview)

<span data-ttu-id="bad6a-218">De nombreuses organisations ont des partenariats commerciaux avec d’autres organisations ou fournisseurs clés avec lesquels ils collaborent en profondeur.</span><span class="sxs-lookup"><span data-stu-id="bad6a-218">Many organizations have business partnerships with other organizations or key vendors with whom they collaborate in depth.</span></span> <span data-ttu-id="bad6a-219">La gestion des utilisateurs et l’accès aux ressources peuvent être difficiles à gérer dans ces scénarios.</span><span class="sxs-lookup"><span data-stu-id="bad6a-219">User management and access to resources can be challenging to manage in these scenarios.</span></span> <span data-ttu-id="bad6a-220">Envisagez d’automatiser certaines tâches de gestion des utilisateurs et même de les passer à votre organisation partenaire :</span><span class="sxs-lookup"><span data-stu-id="bad6a-220">Consider automating some of the user management tasks and even transitioning some of them to your partner organization:</span></span>

- [<span data-ttu-id="bad6a-221">Qu’est-ce que la gestion des droits Azure AD ?</span><span class="sxs-lookup"><span data-stu-id="bad6a-221">What is Azure AD entitlement management?</span></span>](https://docs.microsoft.com/azure/active-directory/governance/entitlement-management-overview)

<span data-ttu-id="bad6a-222">Les canaux privés dans teams autorisent les conversations et le partage de fichiers délimités entre un sous-ensemble de membres d’équipe.</span><span class="sxs-lookup"><span data-stu-id="bad6a-222">Private channels in Teams allow for scoped conversations and file sharing between a subset of team members.</span></span> <span data-ttu-id="bad6a-223">En fonction de vos besoins spécifiques, vous pouvez autoriser ou bloquer cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="bad6a-223">Depending on your specific business needs, you may want to allow or block this capability.</span></span>

- [<span data-ttu-id="bad6a-224">Canaux privés dans Microsoft teams</span><span class="sxs-lookup"><span data-stu-id="bad6a-224">Private channels in Microsoft Teams</span></span>](https://docs.microsoft.com/MicrosoftTeams/private-channels)

- [<span data-ttu-id="bad6a-225">Gérer le cycle de vie des canaux privés dans Microsoft teams</span><span class="sxs-lookup"><span data-stu-id="bad6a-225">Manage the life cycle of private channels in Microsoft Teams</span></span>](https://docs.microsoft.com/MicrosoftTeams/private-channels-life-cycle-management)

<span data-ttu-id="bad6a-226">Ressources supplémentaires :</span><span class="sxs-lookup"><span data-stu-id="bad6a-226">Additional resources:</span></span>

- [<span data-ttu-id="bad6a-227">Gouvernance d’identité Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="bad6a-227">Azure Active Directory Identity Governance</span></span>](https://docs.microsoft.com/azure/active-directory/governance)

## <a name="related-topics"></a><span data-ttu-id="bad6a-228">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bad6a-228">Related topics</span></span>

[<span data-ttu-id="bad6a-229">Sécurité et de la conformité dans Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="bad6a-229">Security and compliance in Microsoft Teams</span></span>](https://docs.microsoft.com/microsoftteams/security-compliance-overview)

[<span data-ttu-id="bad6a-230">Gérer les paramètres de partage dans SharePoint</span><span class="sxs-lookup"><span data-stu-id="bad6a-230">Manage sharing settings in SharePoint</span></span>](https://docs.microsoft.com/sharepoint/turn-external-sharing-on-or-off)

[<span data-ttu-id="bad6a-231">Créer et gérer un réseau externe dans Yammer</span><span class="sxs-lookup"><span data-stu-id="bad6a-231">Create and manage an external network in Yammer</span></span>](https://docs.microsoft.com/yammer/work-with-external-users/create-and-manage-an-external-network)

[<span data-ttu-id="bad6a-232">Configurer Teams avec trois niveaux de protection</span><span class="sxs-lookup"><span data-stu-id="bad6a-232">Configure Teams with three tiers of protection</span></span>](https://docs.microsoft.com/microsoft-365/solutions/configure-teams-three-tiers-protection)