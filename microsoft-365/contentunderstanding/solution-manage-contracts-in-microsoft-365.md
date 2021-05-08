---
title: Gérer les contrats à l’aide d’Microsoft 365 solution
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.date: 05/10/2021
ms.prod: microsoft-365-enterprise
ms.collection: m365solution-managecontracts
search.appverid: ''
localization_priority: None
ROBOTS: NOINDEX, NOFOLLOW
description: Découvrez comment gérer les contrats à l’aide Microsoft 365 solution SharePoint Syntex, Microsoft Teams et Power Automate.
ms.openlocfilehash: 806ea9fd048dec198a19fa79f3b60f3f3cb81018
ms.sourcegitcommit: 8e4c107e4da3a00be0511b05bc655a98fe871a54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2021
ms.locfileid: "52281183"
---
# <a name="manage-contracts-using-a-microsoft-365-solution"></a><span data-ttu-id="496f5-103">Gérer les contrats à l’aide d’Microsoft 365 solution</span><span class="sxs-lookup"><span data-stu-id="496f5-103">Manage contracts using a Microsoft 365 solution</span></span>

<span data-ttu-id="496f5-104">Cet article explique comment créer une solution de gestion des contrats pour votre organisation à l’aide SharePoint Syntex et des composants de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="496f5-104">This article describes how to create a contracts management solution for your organization by using SharePoint Syntex and components of Microsoft 365.</span></span> <span data-ttu-id="496f5-105">Il vous fournit une infrastructure pour vous aider à planifier et à créer une solution qui répond aux besoins uniques de votre entreprise.</span><span class="sxs-lookup"><span data-stu-id="496f5-105">It provides you with a framework to help you plan and create a solution that fits your unique business needs.</span></span> <span data-ttu-id="496f5-106">Même si cette solution ne convient pas à l’ensemble de votre entreprise, une partie de celle-ci peut être adoptée dans votre planification de création d’une solution de gestion de contrat personnalisée.</span><span class="sxs-lookup"><span data-stu-id="496f5-106">Even if this solution doesn't suit your business needs as a whole, parts of it can be adopted in your planning to create a custom contract management solution.</span></span>

## <a name="identify-the-business-problem"></a><span data-ttu-id="496f5-107">Identifier le problème d’entreprise</span><span class="sxs-lookup"><span data-stu-id="496f5-107">Identify the business problem</span></span>

<span data-ttu-id="496f5-108">La première étape de la planification de votre système de gestion des contrats consiste à comprendre le problème que vous essayez de résoudre.</span><span class="sxs-lookup"><span data-stu-id="496f5-108">The first step in planning your contract management system is to understand the problem you're trying to solve.</span></span> <span data-ttu-id="496f5-109">Pour cette solution, quatre problèmes clés doivent être résolus :</span><span class="sxs-lookup"><span data-stu-id="496f5-109">For this solution, four key issues need to be addressed:</span></span>

- <span data-ttu-id="496f5-110">**Identifier les contrats**.</span><span class="sxs-lookup"><span data-stu-id="496f5-110">**Identify contracts**.</span></span> <span data-ttu-id="496f5-111">Votre organisation travaille avec de nombreux documents, tels que des factures, des contrats, des déclarations de travail, etc.</span><span class="sxs-lookup"><span data-stu-id="496f5-111">Your organization works with many documents, such as invoices, contracts, statements of work, and so on.</span></span>  <span data-ttu-id="496f5-112">Certains sont des biens numériques envoyés par courrier électronique, d’autres des biens papier envoyés par courrier électronique traditionnel.</span><span class="sxs-lookup"><span data-stu-id="496f5-112">Some are digital assets sent through email, and some are paper assets sent through traditional mail.</span></span> <span data-ttu-id="496f5-113">Vous avez besoin d’un moyen d’identifier tous les contrats client de tous les autres documents, puis de les classer comme tels.</span><span class="sxs-lookup"><span data-stu-id="496f5-113">You need a way to identify all customer contracts from all other documents, and then classifying them as such.</span></span>

- <span data-ttu-id="496f5-114">**Suivi de l’historique des approbations de contrat.**</span><span class="sxs-lookup"><span data-stu-id="496f5-114">**Track the history of contract approvals**.</span></span> <span data-ttu-id="496f5-115">Votre organisation a besoin d’un moyen fiable pour déterminer si les contrats ont été approuvés ou rejetés, et si le paiement a été effectué.</span><span class="sxs-lookup"><span data-stu-id="496f5-115">Your organization needs a reliable way to find whether contracts have been either approved or rejected, and whether payment has been processed.</span></span> 

- <span data-ttu-id="496f5-116">**Site pour gérer les approbations de contrat.**</span><span class="sxs-lookup"><span data-stu-id="496f5-116">**Site to manage contract approvals**.</span></span> <span data-ttu-id="496f5-117">Votre organisation doit configurer un site de collaboration dans lequel toutes les parties prenantes requises peuvent facilement examiner les contrats.</span><span class="sxs-lookup"><span data-stu-id="496f5-117">Your organization needs to set up a collaborative site in which all required stakeholders can easily review contracts.</span></span> <span data-ttu-id="496f5-118">Les parties prenantes doivent pouvoir examiner l’ensemble du contrat si nécessaire, mais se soucient principalement de voir plusieurs champs clés de chaque contrat (par exemple, le nom du client, le numéro de bon de service et le coût total).</span><span class="sxs-lookup"><span data-stu-id="496f5-118">Stakeholders should be able to review the whole contract if needed, but mostly care about seeing several key fields from each contract (for example, customer name, PO number, and total cost).</span></span> <span data-ttu-id="496f5-119">Les parties prenantes doivent pouvoir facilement approuver ou rejeter les contrats entrants.</span><span class="sxs-lookup"><span data-stu-id="496f5-119">Stakeholders should be able to easily approve or reject incoming contracts.</span></span>

- <span data-ttu-id="496f5-120">**Contrats révisés d’itinéraire.**</span><span class="sxs-lookup"><span data-stu-id="496f5-120">**Route reviewed contracts**.</span></span> <span data-ttu-id="496f5-121">Les contrats approuvés et rejetés doivent être acheminés via un flux de travail spécifique.</span><span class="sxs-lookup"><span data-stu-id="496f5-121">Approved and rejected contracts need to be routed through a specific workflow.</span></span> <span data-ttu-id="496f5-122">Les contrats approuvés doivent être acheminés vers une application tierce pour le traitement des paiements.</span><span class="sxs-lookup"><span data-stu-id="496f5-122">Approved contracts need to be routed to a third-party application for payment processing.</span></span> <span data-ttu-id="496f5-123">Les contrats rejetés doivent être acheminés pour une révision supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="496f5-123">Rejected contracts need to be routed for additional review.</span></span>

## <a name="overview-of-the-solution"></a><span data-ttu-id="496f5-124">Vue d’ensemble de la solution</span><span class="sxs-lookup"><span data-stu-id="496f5-124">Overview of the solution</span></span>

  ![Diagramme de la solution utilisant SharePoint Syntex, SharePoint listes, Teams et Power Automate.](../media/content-understanding/syntex-solution-manage-contracts-setup-steps.png)

<span data-ttu-id="496f5-126">Cette solution de gestion des contrats comprend quatre composants de Microsoft 365 :</span><span class="sxs-lookup"><span data-stu-id="496f5-126">This contract management solution guidance includes four components of Microsoft 365:</span></span>

- <span data-ttu-id="496f5-127">**Microsoft SharePoint Syntex**: créez des modèles pour identifier et classer vos fichiers de contrat, puis extrayez les données appropriées à partir de ces derniers.</span><span class="sxs-lookup"><span data-stu-id="496f5-127">**Microsoft SharePoint Syntex**: Create models to identify and classify your contract files and then extract the appropriate data from them.</span></span>

- <span data-ttu-id="496f5-128">**Listes SharePoint Microsoft**: utilisez la mise en forme disponible dans les listes SharePoint modernes pour présenter les contrats dans un format commercial convivial.</span><span class="sxs-lookup"><span data-stu-id="496f5-128">**Microsoft SharePoint lists**: Use the formatting available in modern SharePoint lists to present contracts in a business-friendly format.</span></span>

- <span data-ttu-id="496f5-129">**Microsoft Teams**: utilisez les fonctionnalités d’un canal Teams et des onglets associés pour permettre à vos parties prenantes de réviser et de gérer les contrats.</span><span class="sxs-lookup"><span data-stu-id="496f5-129">**Microsoft Teams**: Use the functionality of a Teams channel and associated tabs to allow your stakeholders to review and manage contracts.</span></span>

- <span data-ttu-id="496f5-130">**Power Automate**: utilisez des flux pour guider les contrats dans le processus d’approbation, puis vers une application tierce pour le paiement.</span><span class="sxs-lookup"><span data-stu-id="496f5-130">**Power Automate**: Use flows to guide contracts through the approval process, and then to a third-party application for payment.</span></span>

### <a name="how-it-all-works"></a><span data-ttu-id="496f5-131">Fonctionnement</span><span class="sxs-lookup"><span data-stu-id="496f5-131">How it all works</span></span>

  ![Diagramme de la solution montrant le flux de travail pour télécharger des documents, extraire des données, avertir les parties prenantes et approuver ou rejeter le contrat.](../media/content-understanding/syntex-solution-manage-contracts-overview.png)

1. <span data-ttu-id="496f5-133">Les documents sont téléchargés vers une bibliothèque SharePoint documents.</span><span class="sxs-lookup"><span data-stu-id="496f5-133">Documents are uploaded to a SharePoint document library.</span></span> <span data-ttu-id="496f5-134">Un SharePoint de compréhension de document Syntex a été appliqué à la bibliothèque de documents.</span><span class="sxs-lookup"><span data-stu-id="496f5-134">A SharePoint Syntex document understanding model has been applied to the document library.</span></span> <span data-ttu-id="496f5-135">Il vérifie chaque fichier pour voir si un type de contenu « contrat » correspond à ce qu’il est entraîné à rechercher.</span><span class="sxs-lookup"><span data-stu-id="496f5-135">It checks each file to see if any match a "contract" content type it's trained to look for.</span></span> <span data-ttu-id="496f5-136">S’il trouve une correspondance, il classifie le fichier en tant que « contrat » et met à jour le type de contenu pour le document.</span><span class="sxs-lookup"><span data-stu-id="496f5-136">If it finds a match, it classifies the file as a "contract" and updates the content type for the document.</span></span>

2. <span data-ttu-id="496f5-137">Le modèle tire également des données spécifiques de chaque fichier de contrat que les parties prenantes souhaitent voir, telles que le *client,* le coût et le montant *des frais.*</span><span class="sxs-lookup"><span data-stu-id="496f5-137">The model also pulls out specific data from each contract file that stakeholders are interested in seeing, such as the *Client*, *Contractor*, and *Fee amount*.</span></span>

    <span data-ttu-id="496f5-138">La page suivante est un exemple de contrat que le modèle est formé pour identifier.</span><span class="sxs-lookup"><span data-stu-id="496f5-138">The following page is an example of a contract that the model is trained to identify.</span></span>

      ![Exemple de contrat.](../media/content-understanding/contract.png)

3. <span data-ttu-id="496f5-140">Dans Microsoft Teams, toutes les parties prenantes sont membres d’un canal Teams sécurisé dans lequel tous les contrats dans la bibliothèque de documents sont visibles pour approbation ou rejet.</span><span class="sxs-lookup"><span data-stu-id="496f5-140">In Microsoft Teams, all stakeholders are members of a secure Teams channel in which all contracts in the document library are visible for approval or rejection.</span></span> <span data-ttu-id="496f5-141">À l’Teams, toutes les parties prenantes sont averties lorsque de nouveaux contrats doivent être révisés.</span><span class="sxs-lookup"><span data-stu-id="496f5-141">By using Teams functionality, all stakeholders are notified when new contracts need to be reviewed.</span></span>
 
4. <span data-ttu-id="496f5-142">À l’Power Automate, les contrats sont déplacés via le processus d’approbation dans Teams canal.</span><span class="sxs-lookup"><span data-stu-id="496f5-142">By using Power Automate, contracts are moved through the approval process in the Teams channel.</span></span> <span data-ttu-id="496f5-143">Lorsqu’un membre approuve un contrat, l’état du contrat est modifié pour approuver, tous les membres sont avertis par le biais d’un billet Teams et un élément de ligne est créé pour montrer que le contrat est prêt pour le paiement.</span><span class="sxs-lookup"><span data-stu-id="496f5-143">When a member approves a contract, the contract status is changed to approve, all members are notified through a Teams post, and a line item is created to show that the contract is ready for payout.</span></span> <span data-ttu-id="496f5-144">Ce processus peut être étendu pour écrire directement dans une application financière tierce pour paiement.</span><span class="sxs-lookup"><span data-stu-id="496f5-144">This process can be extended to write directly to a third-party financial application for payment.</span></span>

5.  <span data-ttu-id="496f5-145">Lorsqu’un membre rejette un contrat, l’état est rejeté et tous les membres sont avertis par le biais d’Teams billet.</span><span class="sxs-lookup"><span data-stu-id="496f5-145">When a member rejects a contract, the status is changed to rejected, and all members are notified through a Teams post.</span></span>

## <a name="create-the-solution"></a><span data-ttu-id="496f5-146">Créer la solution</span><span class="sxs-lookup"><span data-stu-id="496f5-146">Create the solution</span></span>

<span data-ttu-id="496f5-147">Les sections suivantes détailleront la configuration de votre solution de gestion des contrats.</span><span class="sxs-lookup"><span data-stu-id="496f5-147">The next sections will go into detail about how to configure your contracts management solution.</span></span> <span data-ttu-id="496f5-148">Il est divisé en trois étapes :</span><span class="sxs-lookup"><span data-stu-id="496f5-148">It's divided into three steps:</span></span>

- [<span data-ttu-id="496f5-149">Étape 1. Utiliser SharePoint Syntex pour identifier les fichiers de contrat et extraire des données</span><span class="sxs-lookup"><span data-stu-id="496f5-149">Step 1. Use SharePoint Syntex to identify contract files and extract data</span></span>](solution-manage-contracts-step1.md)
- [<span data-ttu-id="496f5-150">Étape 2. Utiliser Microsoft Teams pour créer votre canal de gestion de contrat</span><span class="sxs-lookup"><span data-stu-id="496f5-150">Step 2. Use Microsoft Teams to create your contract management channel</span></span>](solution-manage-contracts-step2.md)
- [<span data-ttu-id="496f5-151">Étape 3. Utiliser Power Automate pour créer votre flux pour traiter vos contrats</span><span class="sxs-lookup"><span data-stu-id="496f5-151">Step 3. Use Power Automate to create your flow to process your contracts</span></span>](solution-manage-contracts-step3.md)