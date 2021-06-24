---
title: Configurer un connecteur pour archiver des Skype Entreprise de données dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
description: Découvrez comment configurer et utiliser un connecteur dans le Centre de conformité Microsoft 365 pour importer et archiver des données de Skype Entreprise à Microsoft 365.
ms.openlocfilehash: 93128af0c7f305cb2bef55efd5520de77555a222
ms.sourcegitcommit: fa9efab24a84f71fec7d001f2ad8949125fa8eee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53054834"
---
# <a name="set-up-a-connector-to-archive-skype-for-business-data-preview"></a><span data-ttu-id="dfd54-103">Configurer un connecteur pour archiver les Skype Entreprise données (aperçu)</span><span class="sxs-lookup"><span data-stu-id="dfd54-103">Set up a connector to archive Skype for Business data (preview)</span></span>

<span data-ttu-id="dfd54-104">Utilisez un connecteur Veritas dans le Centre de conformité Microsoft 365 pour importer et archiver des données à partir de la plateforme Skype Entreprise vers les boîtes aux lettres des utilisateurs de Microsoft 365 organisation.</span><span class="sxs-lookup"><span data-stu-id="dfd54-104">Use a Veritas connector in the Microsoft 365 compliance center to import and archive data from the Skype for Business platform to user mailboxes in your Microsoft 365 organization.</span></span> <span data-ttu-id="dfd54-105">Veritas fournit un connecteur [Skype Entreprise](https://www.veritas.com/en/au/insights/merge1/skype-for-business) qui est configuré pour capturer des éléments à partir de la source de données tierce (régulièrement) et importer ces éléments dans Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="dfd54-105">Veritas provides a [Skype for Business](https://www.veritas.com/en/au/insights/merge1/skype-for-business) connector that is configured to capture items from the third-party data source (on a regular basis) and import those items to Microsoft 365.</span></span> <span data-ttu-id="dfd54-106">Le connecteur convertit le contenu tel que les messages entre les utilisateurs, les conversations permanentes et les messages de conférence de Skype Entreprise au format de message électronique, puis importe ces éléments dans la boîte aux lettres de l’utilisateur dans Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="dfd54-106">The connector converts the content such as messages between users, persistent chats, and conference messages from Skype for Business to an email message format and then imports those items to the user’s mailbox in Microsoft 365.</span></span>

<span data-ttu-id="dfd54-107">Une fois Skype Entreprise données stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies de rétention et les étiquettes de rétention.</span><span class="sxs-lookup"><span data-stu-id="dfd54-107">After Skype for Business data is stored in user mailboxes, you can apply Microsoft 365 compliance features such as Litigation Hold, eDiscovery, retention policies and retention labels.</span></span> <span data-ttu-id="dfd54-108">L’utilisation d’Skype Entreprise pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.</span><span class="sxs-lookup"><span data-stu-id="dfd54-108">Using a Skype for Business connector to import and archive data in Microsoft 365 can help your organization stay compliant with government and regulatory policies.</span></span>

## <a name="overview-of-archiving-skype-for-business-data"></a><span data-ttu-id="dfd54-109">Vue d’ensemble de l’archivage Skype Entreprise données</span><span class="sxs-lookup"><span data-stu-id="dfd54-109">Overview of archiving Skype for Business data</span></span>

<span data-ttu-id="dfd54-110">La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données Skype Entreprise dans Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="dfd54-110">The following overview explains the process of using a connector to archive the Skype for Business data in Microsoft 365.</span></span>

![Flux de travail d’archivage pour Skype Entreprise données](../media/SkypeforBusinessConnectorWorkflow.png)

1. <span data-ttu-id="dfd54-112">Votre organisation collabore avec Skype Entreprise pour configurer et configurer un site Skype Entreprise web.</span><span class="sxs-lookup"><span data-stu-id="dfd54-112">Your organization works with Skype for Business to set up and configure a Skype for Business site.</span></span>

2. <span data-ttu-id="dfd54-113">Toutes les 24 heures, les Skype Entreprise sont copiés sur le site Veritas Merge1.</span><span class="sxs-lookup"><span data-stu-id="dfd54-113">Once every 24 hours, Skype for Business items are copied to the Veritas Merge1 site.</span></span> <span data-ttu-id="dfd54-114">Le connecteur convertit également les Skype Entreprise au format de message électronique.</span><span class="sxs-lookup"><span data-stu-id="dfd54-114">The connector also converts Skype for Business items to an email message format.</span></span>

3. <span data-ttu-id="dfd54-115">Le connecteur Skype Entreprise que vous créez dans le Centre de conformité Microsoft 365, se connecte au site Veritas Merge1 tous les jours et transfère le contenu Skype Entreprise vers un emplacement stockage Azure sécurisé dans le cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="dfd54-115">The Skype for Business connector that you create in the Microsoft 365 compliance center, connects to the Veritas Merge1 site every day, and transfers the Skype for Business content to a secure Azure Storage location in the Microsoft cloud.</span></span>

4. <span data-ttu-id="dfd54-116">Le connecteur importe les éléments convertis dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *Email* du mappage automatique des utilisateurs, comme décrit à l’étape [3.](#step-3-map-users-and-complete-the-connector-setup)</span><span class="sxs-lookup"><span data-stu-id="dfd54-116">The connector imports the converted items to the mailboxes of specific users using the value of the *Email* property of the automatic user mapping as described in [Step 3](#step-3-map-users-and-complete-the-connector-setup).</span></span> <span data-ttu-id="dfd54-117">Un sous-dossier du dossier Boîte de réception nommé **Skype Entreprise** est créé dans les boîtes aux lettres utilisateur et les éléments sont importés dans ce dossier.</span><span class="sxs-lookup"><span data-stu-id="dfd54-117">A subfolder in the Inbox folder named **Skype for Business** is created in the user mailboxes, and items are imported to that folder.</span></span> <span data-ttu-id="dfd54-118">Pour ce faire, le connecteur utilise la valeur de la *propriété Email.*</span><span class="sxs-lookup"><span data-stu-id="dfd54-118">The connector does this by using the value of the *Email* property.</span></span> <span data-ttu-id="dfd54-119">Chaque Skype Entreprise contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant de l’élément.</span><span class="sxs-lookup"><span data-stu-id="dfd54-119">Every Skype for Business item contains this property, which is populated with the email address of every participant of the item.</span></span>

## <a name="before-you-set-up-a-connector"></a><span data-ttu-id="dfd54-120">Avant de configurer un connecteur</span><span class="sxs-lookup"><span data-stu-id="dfd54-120">Before you set up a connector</span></span>

- <span data-ttu-id="dfd54-121">Créez un compte Merge1 pour les connecteurs Microsoft.</span><span class="sxs-lookup"><span data-stu-id="dfd54-121">Create a Merge1 account for Microsoft connectors.</span></span> <span data-ttu-id="dfd54-122">Pour ce faire, contactez le support [technique Veritas.](https://www.veritas.com/form/requestacall/ms-connectors-contact.html)</span><span class="sxs-lookup"><span data-stu-id="dfd54-122">To do this, contact [Veritas Customer Support](https://www.veritas.com/form/requestacall/ms-connectors-contact.html).</span></span> <span data-ttu-id="dfd54-123">Vous devez vous inscrire à ce compte lorsque vous créez le connecteur à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="dfd54-123">You need to sign into this account when you create the connector in Step 1.</span></span>

- <span data-ttu-id="dfd54-124">L’utilisateur qui crée le connecteur Skype Entreprise à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle Importation/Exportation de boîte aux lettres à l’Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="dfd54-124">The user who creates the Skype for Business connector in Step 1 (and completes it in Step 3) must be assigned to the Mailbox Import Export role in Exchange Online.</span></span> <span data-ttu-id="dfd54-125">Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans la Centre de conformité Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="dfd54-125">This role is required to add connectors on the **Data connectors** page in the Microsoft 365 compliance center.</span></span> <span data-ttu-id="dfd54-126">Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="dfd54-126">By default, this role is not assigned to any role group in Exchange Online.</span></span> <span data-ttu-id="dfd54-127">Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="dfd54-127">You can add the Mailbox Import Export role to the Organization Management role group in Exchange Online.</span></span> <span data-ttu-id="dfd54-128">Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres.</span><span class="sxs-lookup"><span data-stu-id="dfd54-128">Or you can create a role group, assign the Mailbox Import Export role, and then add the appropriate users as members.</span></span> <span data-ttu-id="dfd54-129">Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ». [](/Exchange/permissions-exo/role-groups#create-role-groups)</span><span class="sxs-lookup"><span data-stu-id="dfd54-129">For more information, see the [Create role groups](/Exchange/permissions-exo/role-groups#create-role-groups) or [Modify role groups](/Exchange/permissions-exo/role-groups#modify-role-groups) sections in the article "Manage role groups in Exchange Online".</span></span>

## <a name="step-1-set-up-the-skype-for-business-connector"></a><span data-ttu-id="dfd54-130">Étape 1 : Configurer le connecteur Skype Entreprise de connexion</span><span class="sxs-lookup"><span data-stu-id="dfd54-130">Step 1: Set up the Skype for Business connector</span></span>

<span data-ttu-id="dfd54-131">La première étape consiste à accéder à la page **Connecteurs** de données dans le Centre de conformité Microsoft 365 et à créer un connecteur pour Skype Entreprise données.</span><span class="sxs-lookup"><span data-stu-id="dfd54-131">The first step is to access to the **Data Connectors** page in the Microsoft 365 compliance center and create a connector for Skype for Business data.</span></span>

1. <span data-ttu-id="dfd54-132">Go to <https://compliance.microsoft.com> and click **Data connectors**  >  **Skype Entreprise**.</span><span class="sxs-lookup"><span data-stu-id="dfd54-132">Go to <https://compliance.microsoft.com> and click **Data connectors** > **Skype for Business**.</span></span>

2. <span data-ttu-id="dfd54-133">Dans la page **Skype Entreprise** description du produit, cliquez **sur Ajouter un connecteur.**</span><span class="sxs-lookup"><span data-stu-id="dfd54-133">On the **Skype for Business** product description page, click **Add connector**.</span></span>

3. <span data-ttu-id="dfd54-134">Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**</span><span class="sxs-lookup"><span data-stu-id="dfd54-134">On the **Terms of service** page, click **Accept**.</span></span>

4. <span data-ttu-id="dfd54-135">Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="dfd54-135">Enter a unique name that identifies the connector, and then click **Next**.</span></span>

5. <span data-ttu-id="dfd54-136">Connectez-vous à votre compte Merge1 pour configurer le connecteur.</span><span class="sxs-lookup"><span data-stu-id="dfd54-136">Sign in to your Merge1 account to configure the connector.</span></span>

## <a name="step-2-configure-the-skype-for-business-on-the-veritas-merge1-site"></a><span data-ttu-id="dfd54-137">Étape 2 : Configurer le Skype Entreprise sur le site Veritas Merge1</span><span class="sxs-lookup"><span data-stu-id="dfd54-137">Step 2: Configure the Skype for Business on the Veritas Merge1 site</span></span>

<span data-ttu-id="dfd54-138">La deuxième étape consiste à configurer le connecteur Skype Entreprise sur le site Veritas Merge1.</span><span class="sxs-lookup"><span data-stu-id="dfd54-138">The second step is to configure the Skype for Business connector on the Veritas Merge1 site.</span></span> <span data-ttu-id="dfd54-139">Pour plus d’informations sur la configuration du connecteur Skype Entreprise, voir [merge1 Third-Party Connectors User Guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Skype%20for%20Business%20%20User%20Guide.pdf).</span><span class="sxs-lookup"><span data-stu-id="dfd54-139">For information about how to configure the Skype for Business connector, see [Merge1 Third-Party Connectors User Guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Skype%20for%20Business%20%20User%20Guide.pdf).</span></span>

<span data-ttu-id="dfd54-140">Une fois que vous avez **cliqué sur &,** la **page** Mappage de l’utilisateur dans l’Assistant connecteur dans la Centre de conformité Microsoft 365 s’affiche.</span><span class="sxs-lookup"><span data-stu-id="dfd54-140">After you click **Save & Finish**, the **User mapping** page in the connector wizard in the Microsoft 365 compliance center is displayed.</span></span>

## <a name="step-3-map-users-and-complete-the-connector-setup"></a><span data-ttu-id="dfd54-141">Étape 3 : Masons les utilisateurs et terminez la configuration du connecteur</span><span class="sxs-lookup"><span data-stu-id="dfd54-141">Step 3: Map users and complete the connector setup</span></span>

<span data-ttu-id="dfd54-142">Pour ma cartographier les utilisateurs et terminer la configuration du connecteur dans le Centre de conformité Microsoft 365, suivez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="dfd54-142">To map users and complete the connector setup in the Microsoft 365 compliance center, follow these steps:</span></span>

1. <span data-ttu-id="dfd54-143">Dans la **page Ma Skype Entreprise aux utilisateurs Microsoft 365 utilisateurs,** activez le mappage utilisateur automatique.</span><span class="sxs-lookup"><span data-stu-id="dfd54-143">On the **Map Skype for Business users to Microsoft 365 users** page, enable automatic user mapping.</span></span> <span data-ttu-id="dfd54-144">Les Skype Entreprise incluent une propriété appelée *Email*, qui contient les adresses de messagerie des utilisateurs de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="dfd54-144">The Skype for Business items include a property called *Email*, which contains email addresses for users in your organization.</span></span> <span data-ttu-id="dfd54-145">Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.</span><span class="sxs-lookup"><span data-stu-id="dfd54-145">If the connector can associate this address with a Microsoft 365 user, the items are imported to that user’s mailbox.</span></span>

2. <span data-ttu-id="dfd54-146">Cliquez **sur** Suivant, examinez vos paramètres, puis allez à la page **Connecteurs** de données pour voir la progression du processus d’importation pour le nouveau connecteur.</span><span class="sxs-lookup"><span data-stu-id="dfd54-146">Click **Next**, review your settings, and then go to the **Data connectors** page to see the progress of the import process for the new connector.</span></span>

## <a name="step-4-monitor-the-skype-for-business-connector"></a><span data-ttu-id="dfd54-147">Étape 4 : Surveiller le connecteur Skype Entreprise de connexion</span><span class="sxs-lookup"><span data-stu-id="dfd54-147">Step 4: Monitor the Skype for Business connector</span></span>

<span data-ttu-id="dfd54-148">Après avoir créé le connecteur Skype Entreprise, vous pouvez afficher l’état du connecteur dans le Centre de conformité Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="dfd54-148">After you create the Skype for Business connector, you can view the connector status in the Microsoft 365 compliance center.</span></span>

1. <span data-ttu-id="dfd54-149">Go to <https://compliance.microsoft.com/> and click **Data connectors** in the left nav.</span><span class="sxs-lookup"><span data-stu-id="dfd54-149">Go to <https://compliance.microsoft.com/> and click **Data connectors** in the left nav.</span></span>

2. <span data-ttu-id="dfd54-150">Cliquez sur **l’onglet Connecteurs,** puis sélectionnez le **connecteur Skype Entreprise** pour afficher la page de présentation, qui contient les propriétés et les informations sur le connecteur.</span><span class="sxs-lookup"><span data-stu-id="dfd54-150">Click the **Connectors** tab and then select the **Skype for Business** connector to display the flyout page, which contains the properties and information about the connector.</span></span>

3. <span data-ttu-id="dfd54-151">Sous **État du connecteur avec source,** cliquez sur le lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur. </span><span class="sxs-lookup"><span data-stu-id="dfd54-151">Under **Connector status with source**, click the **Download log** link to open (or save) the status log for the connector.</span></span> <span data-ttu-id="dfd54-152">Ce journal contient des données qui ont été importées dans le cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="dfd54-152">This log contains data that has been imported to the Microsoft cloud.</span></span>

## <a name="known-issues"></a><span data-ttu-id="dfd54-153">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="dfd54-153">Known issues</span></span>

- <span data-ttu-id="dfd54-154">Pour l’instant, l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="dfd54-154">At this time, we don't support importing attachments or items that are larger than 10 MB.</span></span> <span data-ttu-id="dfd54-155">La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.</span><span class="sxs-lookup"><span data-stu-id="dfd54-155">Support for larger items will be available at a later date.</span></span>