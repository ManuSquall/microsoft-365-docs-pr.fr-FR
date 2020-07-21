---
title: Utiliser le contrôle d’application
description: ''
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
manager: laurawi
audience: ITpro
ms.topic: article
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 74cd1ec93058ed733e7d79da2d6932f04acfa5da
ms.sourcegitcommit: 63887d742c59cc660fc85537b335e98a9dc66fbe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "45170695"
---
# <a name="work-with-app-control"></a><span data-ttu-id="018e9-103">Utiliser le contrôle d’application</span><span class="sxs-lookup"><span data-stu-id="018e9-103">Work with app control</span></span>

<span data-ttu-id="018e9-104">Une fois que le contrôle d’application a été déployé dans votre environnement, vous et les opérations de bureau géré Microsoft ont des responsabilités permanentes.</span><span class="sxs-lookup"><span data-stu-id="018e9-104">Once app control has been deployed in your environment, both you and Microsoft Managed Desktop Operations have ongoing responsibilities.</span></span> <span data-ttu-id="018e9-105">Par exemple, vous pouvez ajouter une nouvelle application dans l’environnement ou ajouter (ou supprimer) un signataire approuvé.</span><span class="sxs-lookup"><span data-stu-id="018e9-105">For example, you might want to add a new app in the environment or add (or remove) a trusted signer.</span></span> <span data-ttu-id="018e9-106">Pour améliorer la sécurité, toutes les applications doivent être signées en code avant de les diffuser aux utilisateurs finaux.</span><span class="sxs-lookup"><span data-stu-id="018e9-106">To improve security, all apps should be code-signed before you release them to end users.</span></span> <span data-ttu-id="018e9-107">Les détails de l’éditeur d’une application incluent des informations sur le signataire.</span><span class="sxs-lookup"><span data-stu-id="018e9-107">An app's publisher details includes information about the signer.</span></span>


## <a name="add-a-new-app"></a><span data-ttu-id="018e9-108">Ajout d’une nouvelle application</span><span class="sxs-lookup"><span data-stu-id="018e9-108">Add a new app</span></span>

<span data-ttu-id="018e9-109">Pour ajouter une nouvelle application, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="018e9-109">To add a new app, follow these steps:</span></span>

1. <span data-ttu-id="018e9-110">Ajoutez l’application à [Microsoft Intune](https://docs.microsoft.com/mem/intune/apps/apps-win32-app-management).</span><span class="sxs-lookup"><span data-stu-id="018e9-110">Add the app to [Microsoft Intune](https://docs.microsoft.com/mem/intune/apps/apps-win32-app-management).</span></span>
2. <span data-ttu-id="018e9-111">Déployez l’application sur n’importe quel appareil de la sonnerie de test.</span><span class="sxs-lookup"><span data-stu-id="018e9-111">Deploy the app to any device in the Test ring.</span></span> 
3. <span data-ttu-id="018e9-112">Testez votre application en fonction de vos processus d’entreprise standard.</span><span class="sxs-lookup"><span data-stu-id="018e9-112">Test your app according to your standard business processes.</span></span> 
4. <span data-ttu-id="018e9-113">Consultez l’observateur d’événements sous **application et services Logs\Microsoft\Windows\AppLocker**, en recherchant les événements **8003** ou **8006** .</span><span class="sxs-lookup"><span data-stu-id="018e9-113">Check Event Viewer under **Application and Services Logs\Microsoft\Windows\AppLocker**, looking for any **8003** or **8006** events.</span></span> <span data-ttu-id="018e9-114">Ces événements indiquent que l’application est bloquée.</span><span class="sxs-lookup"><span data-stu-id="018e9-114">These events indicate that the app would be blocked.</span></span> <span data-ttu-id="018e9-115">Pour plus d’informations sur tous les événements de blocage d’application et leurs significations, consultez la rubrique [utilisation de l’observateur d’événements avec AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/using-event-viewer-with-applocker).</span><span class="sxs-lookup"><span data-stu-id="018e9-115">For more information about all App Locker events and their meanings, see [Using Event Viewer with AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/using-event-viewer-with-applocker).</span></span>
5. <span data-ttu-id="018e9-116">Si vous trouvez l’un de ces événements, ouvrez une demande de signataire avec Microsoft Managed Desktop Operations.</span><span class="sxs-lookup"><span data-stu-id="018e9-116">If you find any of these events, open a signer request with Microsoft Managed Desktop Operations.</span></span>

## <a name="add-or-remove-a-trusted-signer"></a><span data-ttu-id="018e9-117">Ajouter (ou supprimer) un signataire approuvé</span><span class="sxs-lookup"><span data-stu-id="018e9-117">Add (or remove) a trusted signer</span></span>

<span data-ttu-id="018e9-118">Lorsque vous ouvrez une demande de signataire, vous devez d’abord fournir des informations importantes sur l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="018e9-118">When you open a signer request, you'll need to provide some important publisher details first.</span></span> <span data-ttu-id="018e9-119">Ensuite, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="018e9-119">Then follow these steps:</span></span>

1. <span data-ttu-id="018e9-120">[Collecter les détails](#gather-publisher-details)de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="018e9-120">[Gather publisher details](#gather-publisher-details).</span></span>
2. <span data-ttu-id="018e9-121">Ouvrez un ticket avec Microsoft Managed Desktop Operations pour demander la règle de signataire et incluez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="018e9-121">Open a ticket with Microsoft Managed Desktop Operations to request the signer rule and include following details:</span></span>  
    - <span data-ttu-id="018e9-122">Nom de l’application</span><span class="sxs-lookup"><span data-stu-id="018e9-122">Application name</span></span> 
    - <span data-ttu-id="018e9-123">Version de l’application</span><span class="sxs-lookup"><span data-stu-id="018e9-123">Application version</span></span> 
    - <span data-ttu-id="018e9-124">Description</span><span class="sxs-lookup"><span data-stu-id="018e9-124">Description</span></span> 
    - <span data-ttu-id="018e9-125">Modifier le type (« ajouter » ou « supprimer »)</span><span class="sxs-lookup"><span data-stu-id="018e9-125">Change type ("add" or "remove")</span></span>  
    - <span data-ttu-id="018e9-126">Détails de l’éditeur (par exemple : "O = <publisher name> , L = <location> , S = État, C = pays")</span><span class="sxs-lookup"><span data-stu-id="018e9-126">Publisher details (for example: “O=<publisher name>,L=<location>,S=State,C=Country”)</span></span> 

> [!NOTE]
> <span data-ttu-id="018e9-127">Pour supprimer l’approbation d’une application, suivez les mêmes étapes, mais définissez le **type de modification** sur *supprimer*.</span><span class="sxs-lookup"><span data-stu-id="018e9-127">To remove trust for an app, follow the same steps, but set **Change type** to *remove*.</span></span>

<span data-ttu-id="018e9-128">Les opérations déploient progressivement des stratégies vers des groupes de déploiement suivant cette planification :</span><span class="sxs-lookup"><span data-stu-id="018e9-128">Operations will progressively deploy policies to deployment groups following this schedule:</span></span>


|<span data-ttu-id="018e9-129">Groupe de déploiement</span><span class="sxs-lookup"><span data-stu-id="018e9-129">Deployment group</span></span>  |<span data-ttu-id="018e9-130">Type de stratégie</span><span class="sxs-lookup"><span data-stu-id="018e9-130">Policy type</span></span>  |<span data-ttu-id="018e9-131">Calendrier</span><span class="sxs-lookup"><span data-stu-id="018e9-131">Timing</span></span>  |
|---------|---------|---------|
|<span data-ttu-id="018e9-132">Tester</span><span class="sxs-lookup"><span data-stu-id="018e9-132">Test</span></span>     |  <span data-ttu-id="018e9-133">Audit</span><span class="sxs-lookup"><span data-stu-id="018e9-133">Audit</span></span>       |  <span data-ttu-id="018e9-134">Jour 0</span><span class="sxs-lookup"><span data-stu-id="018e9-134">Day 0</span></span>       |
|<span data-ttu-id="018e9-135">Premier</span><span class="sxs-lookup"><span data-stu-id="018e9-135">First</span></span>     | <span data-ttu-id="018e9-136">Enforced</span><span class="sxs-lookup"><span data-stu-id="018e9-136">Enforced</span></span>        | <span data-ttu-id="018e9-137">Jour 1</span><span class="sxs-lookup"><span data-stu-id="018e9-137">Day 1</span></span>        |
|<span data-ttu-id="018e9-138">Rapide</span><span class="sxs-lookup"><span data-stu-id="018e9-138">Fast</span></span>     | <span data-ttu-id="018e9-139">Enforced</span><span class="sxs-lookup"><span data-stu-id="018e9-139">Enforced</span></span>        |  <span data-ttu-id="018e9-140">Jour 3</span><span class="sxs-lookup"><span data-stu-id="018e9-140">Day 3</span></span>       |
|<span data-ttu-id="018e9-141">Larges</span><span class="sxs-lookup"><span data-stu-id="018e9-141">Broad</span></span>     | <span data-ttu-id="018e9-142">Enforced</span><span class="sxs-lookup"><span data-stu-id="018e9-142">Enforced</span></span>        |  <span data-ttu-id="018e9-143">Jour 7</span><span class="sxs-lookup"><span data-stu-id="018e9-143">Day 7</span></span>       |


<span data-ttu-id="018e9-144">Vous pouvez suspendre ou restaurer le déploiement à tout moment pendant le déploiement.</span><span class="sxs-lookup"><span data-stu-id="018e9-144">You can pause or roll back the deployment at any time during the rollout.</span></span> <span data-ttu-id="018e9-145">Pour ce faire, ouvrez une autre demande de service avec des opérations.</span><span class="sxs-lookup"><span data-stu-id="018e9-145">To do this, open another service request with Operations.</span></span>

> [!NOTE]
> <span data-ttu-id="018e9-146">Si vous interrompez la publication d’une règle de signataire, cette règle doit être annulée ou terminée pour qu’un autre déploiement puisse démarrer.</span><span class="sxs-lookup"><span data-stu-id="018e9-146">If you pause the release of a signer rule, that rule must be either rolled back or completed before another rollout can start.</span></span>

## <a name="gather-publisher-details"></a><span data-ttu-id="018e9-147">Collecter les détails de l’éditeur</span><span class="sxs-lookup"><span data-stu-id="018e9-147">Gather publisher details</span></span>

<span data-ttu-id="018e9-148">Pour accéder aux données d’éditeur d’une application, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="018e9-148">To access the publisher data for an app, follow these steps:</span></span>

1. <span data-ttu-id="018e9-149">Recherchez un périphérique de bureau géré Microsoft dans l’anneau de test auquel une stratégie de mode audit est appliquée.</span><span class="sxs-lookup"><span data-stu-id="018e9-149">Find a Microsoft Managed Desktop device in the Test ring that has an Audit Mode policy applied.</span></span> 
2. <span data-ttu-id="018e9-150">Essayez d’installer l’application sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="018e9-150">Attempt to install the app on the device.</span></span>
3. <span data-ttu-id="018e9-151">Ouvrez l’observateur d’événements sur cet appareil.</span><span class="sxs-lookup"><span data-stu-id="018e9-151">Open Event Viewer on that device.</span></span> 
4. <span data-ttu-id="018e9-152">Dans l’observateur d’événements, accédez à **Logs\Microsoft\Windows d’applications et de services**, puis sélectionnez **AppLocker**.</span><span class="sxs-lookup"><span data-stu-id="018e9-152">In Event Viewer, navigate to **Application and Services Logs\Microsoft\Windows**, and then select **AppLocker**.</span></span> 
5. <span data-ttu-id="018e9-153">Recherchez un événement **8003** ou **8006** , puis copiez les informations à partir de l’événement :</span><span class="sxs-lookup"><span data-stu-id="018e9-153">Find any **8003** or **8006** event, and then copy information from the event:</span></span> 
    - <span data-ttu-id="018e9-154">Nom de l’application</span><span class="sxs-lookup"><span data-stu-id="018e9-154">Application name</span></span> 
    - <span data-ttu-id="018e9-155">Version de l’application</span><span class="sxs-lookup"><span data-stu-id="018e9-155">Application version</span></span> 
    - <span data-ttu-id="018e9-156">Description</span><span class="sxs-lookup"><span data-stu-id="018e9-156">Description</span></span> 
    - <span data-ttu-id="018e9-157">Détails de l’éditeur (par exemple : "O = <publisher name> , L = <location> , S = État, C = pays")</span><span class="sxs-lookup"><span data-stu-id="018e9-157">Publisher details (for example: “O=<publisher name>, L=<location>, S=State, C=Country”)</span></span> 