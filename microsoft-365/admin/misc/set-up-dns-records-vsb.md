---
title: Connecter votre domaine à Microsoft 365
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
search.appverid:
- MET150
ROBOTS: NOINDEX, NOFOLLOW
description: Apprenez à vérifier votre domaine et à créer des enregistrements DNS avec Microsoft 365.
ms.custom:
- okr_smb
- AdminSurgePortfolio
ms.openlocfilehash: 206b435130e8e77ed1540432e3bbeff7f16463bf
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49658175"
---
# <a name="connect-your-domain-to-microsoft-365"></a><span data-ttu-id="f0212-103">Connecter votre domaine à Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="f0212-103">Connect your domain to Microsoft 365</span></span>

> [!NOTE]
> <span data-ttu-id="f0212-104">Si vous n’ajoutez pas de domaine, les membres de votre organisation utiliseront le domaine onmicrosoft.com pour leur adresse de messagerie jusqu’à ce que vous le fassiez.</span><span class="sxs-lookup"><span data-stu-id="f0212-104">If you don't add a domain, people in your organization will use the onmicrosoft.com domain for their email addresses until you do.</span></span> <span data-ttu-id="f0212-105">Il est important d’ajouter votre domaine avant d’ajouter des utilisateurs, de sorte que vous n’ayez pas à les reconfigurer.</span><span class="sxs-lookup"><span data-stu-id="f0212-105">It's important to add your domain before you add users, so you don't have to set them up twice.</span></span>

<span data-ttu-id="f0212-106">[Consultez la FAQ dédiée aux domaines](../setup/domains-faq.yml) si vous ne trouvez pas ci-dessous ce que vous recherchez .</span><span class="sxs-lookup"><span data-stu-id="f0212-106">[Check the Domains FAQ](../setup/domains-faq.yml) if you don't find what you're looking for below.</span></span>

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a><span data-ttu-id="f0212-107">Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft</span><span class="sxs-lookup"><span data-stu-id="f0212-107">Add an MX record so email for your domain will come to Microsoft</span></span>

<span data-ttu-id="f0212-108">Vous obtiendrez les informations relatives à l’enregistrement MX à partir de l’Assistant Configuration du domaine du centre d’administration.</span><span class="sxs-lookup"><span data-stu-id="f0212-108">You'll get the information for the MX record from the admin center domain setup wizard.</span></span>

<span data-ttu-id="f0212-109">Sur le site Web de votre fournisseur d’hébergement, créez un nouvel enregistrement MX.</span><span class="sxs-lookup"><span data-stu-id="f0212-109">On your hosting provider's website, add a new MX record.</span></span>
<span data-ttu-id="f0212-110">Vérifiez que les champs sont définis par les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="f0212-110">Make sure that the fields are set to the following values:</span></span>

- <span data-ttu-id="f0212-111">Type d’enregistrement : `MX`</span><span class="sxs-lookup"><span data-stu-id="f0212-111">Record Type: `MX`</span></span>
- <span data-ttu-id="f0212-112">Priorité : sélectionnez la valeur la plus élevée disponible, généralement `0`.</span><span class="sxs-lookup"><span data-stu-id="f0212-112">Priority: Set to the highest value available, typically `0`.</span></span>
- <span data-ttu-id="f0212-113">Nom de l’hôte : `@`</span><span class="sxs-lookup"><span data-stu-id="f0212-113">Host Name: `@`</span></span>
- <span data-ttu-id="f0212-114">Adresse de pointage : copiez la valeur à partir du centre d’administration et collez-la ici.</span><span class="sxs-lookup"><span data-stu-id="f0212-114">Points to address: Copy the value from the admin center and paste it here.</span></span>
- <span data-ttu-id="f0212-115">TTL : `3600‎` (ou votre fournisseur par défaut)</span><span class="sxs-lookup"><span data-stu-id="f0212-115">TTL: `3600‎` (or your provider default)</span></span>

<span data-ttu-id="f0212-116">Sauvegardez l’enregistrement et supprimez tous les autres enregistrements MX.</span><span class="sxs-lookup"><span data-stu-id="f0212-116">Save the record, and then remove any other MX records.</span></span>

## <a name="add-a-cname-record-to-connect-users-to-their-mailboxes"></a><span data-ttu-id="f0212-117">Ajouter un enregistrement CNAME pour connecter des utilisateurs à leurs boîtes aux lettres</span><span class="sxs-lookup"><span data-stu-id="f0212-117">Add a CNAME record to connect users to their mailboxes</span></span>
<span data-ttu-id="f0212-118">Vous obtiendrez les informations relatives aux enregistrements CNAME à partir de l’Assistant Configuration du domaine du centre d’administration.</span><span class="sxs-lookup"><span data-stu-id="f0212-118">You'll get the information for the CNAME records from the admin center domain setup wizard.</span></span>

<span data-ttu-id="f0212-119">Sur le site web de votre fournisseur d’hébergement, ajoutez l’enregistrement CNAME suivant.</span><span class="sxs-lookup"><span data-stu-id="f0212-119">On your hosting provider's website, add the following CNAME record.</span></span> <span data-ttu-id="f0212-120">Dans le nouvel enregistrement, vérifiez que chacun des champs sont définis par les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="f0212-120">Make sure that the fields are set to the following values for each:</span></span>

- <span data-ttu-id="f0212-121">Type d’enregistrement : `CNAME (Alias)`</span><span class="sxs-lookup"><span data-stu-id="f0212-121">Record Type: `CNAME (Alias)`</span></span>
- <span data-ttu-id="f0212-122">Hôte : collez les valeurs que vous copiez à partir du centre d’administration ici.</span><span class="sxs-lookup"><span data-stu-id="f0212-122">Host: Paste the values you copy from the admin center here.</span></span>
- <span data-ttu-id="f0212-123">Adresse de pointage : copiez la valeur à partir du centre d’administration et collez-la ici.</span><span class="sxs-lookup"><span data-stu-id="f0212-123">Points to address: Copy the value from the admin center and paste it here.</span></span>
- <span data-ttu-id="f0212-124">TTL : `3600‎` (ou votre fournisseur par défaut)</span><span class="sxs-lookup"><span data-stu-id="f0212-124">TTL: `3600‎` (or your provider default)</span></span>

## <a name="add-a-txt-record-to-help-prevent-spam"></a><span data-ttu-id="f0212-125">Ajouter un enregistrement TXT afin d'éviter le courrier indésirable</span><span class="sxs-lookup"><span data-stu-id="f0212-125">Add a TXT record to help prevent spam</span></span>
<span data-ttu-id="f0212-126">**Avant de commencer :** Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="f0212-126">**Before you begin:** If you already have an SPF record for your domain, don't create a new one for Microsoft 365.</span></span> <span data-ttu-id="f0212-127">Ajoutez plutôt les valeurs Microsoft 365 requises à l’enregistrement actuel sur le site Web de votre fournisseur d’hébergement de manière à n’avoir qu’un *seul* enregistrement SPF qui inclut les deux ensembles de valeurs.</span><span class="sxs-lookup"><span data-stu-id="f0212-127">Instead, add the required Microsoft 365 values to the current record on your hosting providers website so that you have a *single* SPF record that includes both sets of values.</span></span>

<span data-ttu-id="f0212-128">Sur le site web de votre fournisseur d’hébergement, modifiez l'enregistrement SPF existant ou créez un enregistrement SPF.</span><span class="sxs-lookup"><span data-stu-id="f0212-128">On your hosting provider's website, edit the existing SPF record or create an SPF record.</span></span>
<span data-ttu-id="f0212-129">Vérifiez que les champs sont définis par les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="f0212-129">Make sure that the fields are set to the following values:</span></span>

- <span data-ttu-id="f0212-130">Type d’enregistrement : `TXT (Text)`</span><span class="sxs-lookup"><span data-stu-id="f0212-130">Record Type: `TXT (Text)`</span></span>
- <span data-ttu-id="f0212-131">Hôte : `@`</span><span class="sxs-lookup"><span data-stu-id="f0212-131">Host: `@`</span></span>
- <span data-ttu-id="f0212-132">Valeur TXT :`v=spf1 include:spf.protection.outlook.com -all`</span><span class="sxs-lookup"><span data-stu-id="f0212-132">TXT Value: `v=spf1 include:spf.protection.outlook.com -all`</span></span>
- <span data-ttu-id="f0212-133">TTL : `3600‎` (ou votre fournisseur par défaut)</span><span class="sxs-lookup"><span data-stu-id="f0212-133">TTL: `3600‎` (or your provider default)</span></span>

<span data-ttu-id="f0212-134">Enregistrez l'enregistrement.</span><span class="sxs-lookup"><span data-stu-id="f0212-134">Save the record.</span></span>

<span data-ttu-id="f0212-135">Validez votre enregistrement SPF en utilisant l'un des [Outils de validation SPF](https://docs.microsoft.com/office365/admin/setup/domains-faq#how-can-i-validate-spf-records-for-my-domain) suivants</span><span class="sxs-lookup"><span data-stu-id="f0212-135">Validate your SPF record by using one of these [SPF validation tools](https://docs.microsoft.com/office365/admin/setup/domains-faq#how-can-i-validate-spf-records-for-my-domain)</span></span>

<span data-ttu-id="f0212-136">SPF est conçu pour lutter contre l’usurpation d’adresse, mais il existe des techniques d’usurpation d’adresse contre lesquelles SPF ne peut rien faire.</span><span class="sxs-lookup"><span data-stu-id="f0212-136">SPF is designed to help prevent spoofing, but there are spoofing techniques that SPF cannot protect against.</span></span> <span data-ttu-id="f0212-137">Pour vous protéger contre ces techniques, une fois que vous avez configuré votre SPF, vous devez également configurer DKIM et DMARC pour Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="f0212-137">To protect against these, once you've set up SPF, you should also set up DKIM and DMARC for Microsoft 365.</span></span>

<span data-ttu-id="f0212-138">Pour commencer, consultez la rubrique [Utilisation du DKIM pour valider les e-mails sortants envoyés à partir de votre domaine dans Microsoft 365](https://technet.microsoft.com/library/mt695945%28v=exchg.150%29.aspx) et [Utilisation du DMARC pour valider les e-mails dans Microsoft 365](https://technet.microsoft.com/library/mt734386%28v=exchg.150%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="f0212-138">To get started, see [Use DKIM to validate outbound email sent from your domain in Microsoft 365](https://technet.microsoft.com/library/mt695945%28v=exchg.150%29.aspx) and [Use DMARC to validate email in Microsoft 365](https://technet.microsoft.com/library/mt734386%28v=exchg.150%29.aspx).</span></span>

<span data-ttu-id="f0212-139">Pour finir, revenez à l’Assistant Configuration du domaine du centre d’administration pour terminer votre installation.</span><span class="sxs-lookup"><span data-stu-id="f0212-139">Finally, head back to the admin center domain setup wizard to complete your setup.</span></span>