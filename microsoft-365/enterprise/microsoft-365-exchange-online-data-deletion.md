---
title: Microsoft 365 suppression des données Exchange Online
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Découvrez comment les suppressions de données conditionnelles et logicielles pour les boîtes aux lettres et les éléments dans les boîtes aux lettres sont gérées dans Exchange Online.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: d4b4d30da70001967ca73377f10a4cd417577b72
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "46695829"
---
# <a name="exchange-online-data-deletion-in-microsoft-365"></a><span data-ttu-id="fef9b-103">Suppression de données Exchange Online dans Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="fef9b-103">Exchange Online Data Deletion in Microsoft 365</span></span>

<span data-ttu-id="fef9b-104">Dans Exchange Online, il existe deux types de suppressions : les suppressions douces et les suppressions matérielles.</span><span class="sxs-lookup"><span data-stu-id="fef9b-104">Within Exchange Online, there are two kinds of deletions: soft deletions and hard deletions.</span></span> <span data-ttu-id="fef9b-105">Cela s’applique aux boîtes aux lettres et aux éléments d’une boîte aux lettres.</span><span class="sxs-lookup"><span data-stu-id="fef9b-105">This applies to both mailboxes and items within a mailbox.</span></span>

## <a name="soft-deleted-and-hard-deleted-mailboxes"></a><span data-ttu-id="fef9b-106">Boîtes aux lettres supprimées (récupérables) et supprimées de manière irréversible</span><span class="sxs-lookup"><span data-stu-id="fef9b-106">Soft-Deleted and Hard-Deleted Mailboxes</span></span>
<span data-ttu-id="fef9b-107">Une boîte aux lettres utilisateur supprimée (récupérable) est une boîte aux lettres qui a été supprimée à l’aide du centre d’administration 365 de Microsoft ou de la cmdlet Remove-Mailbox et qui se trouve toujours dans la corbeille Azure Active Directory pendant moins de 30 jours.</span><span class="sxs-lookup"><span data-stu-id="fef9b-107">A soft-deleted user mailbox is a mailbox that has been deleted using the Microsoft 365 admin center or the Remove-Mailbox cmdlet and has still been in the Azure Active Directory recycle bin for less than 30 days.</span></span> <span data-ttu-id="fef9b-108">Une boîte aux lettres peut être supprimée de manière récupérable de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="fef9b-108">A mailbox can become soft-deleted in any of the following ways:</span></span>
- <span data-ttu-id="fef9b-109">Le compte d’utilisateur Azure Active Directory associé à la boîte aux lettres utilisateur est supprimé de manière récupérable (l’objet utilisateur est hors de portée ou dans le conteneur de la corbeille).</span><span class="sxs-lookup"><span data-stu-id="fef9b-109">The user mailbox's associated Azure Active Directory user account is soft-deleted (the user object is out of scope or in the recycle bin container).</span></span>
- <span data-ttu-id="fef9b-110">Le compte d’utilisateur Azure Active Directory associé à la boîte aux lettres utilisateur a été supprimé de manière irréversible, mais la boîte aux lettres Exchange Online est en conservation pour litige ou en conservation eDiscovery.</span><span class="sxs-lookup"><span data-stu-id="fef9b-110">The user mailbox's associated Azure Active Directory user account has been hard-deleted but the Exchange Online mailbox is under a litigation hold or eDiscovery hold.</span></span>
- <span data-ttu-id="fef9b-111">Le compte d’utilisateur Azure Active Directory associé à la boîte aux lettres utilisateur a été purgé au cours des 30 derniers jours ; la longueur maximale de rétention Exchange Online permet de conserver la boîte aux lettres dans un état supprimé (récupérable) avant qu’elle ne soit définitivement purgée et irrécupérable.</span><span class="sxs-lookup"><span data-stu-id="fef9b-111">The user mailbox's associated Azure Active Directory user account has been purged within the last 30 days; which is the maximum retention length Exchange Online will keep the mailbox in a soft-deleted state before it is permanently purged and unrecoverable.</span></span>

<span data-ttu-id="fef9b-112">Une boîte aux lettres utilisateur supprimée de manière irréversible est une boîte aux lettres qui a été supprimée de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="fef9b-112">A hard-deleted user mailbox is a mailbox that has been deleted in one of the following ways:</span></span>
- <span data-ttu-id="fef9b-113">La boîte aux lettres utilisateur a été supprimée de manière récupérable pendant plus de 30 jours et l’utilisateur Azure Active Directory associé a été supprimé de manière irréversible.</span><span class="sxs-lookup"><span data-stu-id="fef9b-113">The user mailbox has been soft-deleted for more than 30 days, and the associated Azure Active Directory user has been hard-deleted.</span></span> <span data-ttu-id="fef9b-114">Tout le contenu des boîtes aux lettres, comme les courriers électroniques, les contacts et les fichiers, est définitivement supprimé.</span><span class="sxs-lookup"><span data-stu-id="fef9b-114">All mailbox content such as emails, contacts and files are permanently deleted.</span></span>
- <span data-ttu-id="fef9b-115">Le compte d’utilisateur associé à la boîte aux lettres de l’utilisateur a été supprimé de manière irréversible dans Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="fef9b-115">The user account associated with the user mailbox has been hard-deleted from the Azure Active Directory.</span></span> <span data-ttu-id="fef9b-116">La boîte aux lettres utilisateur est désormais supprimée de manière récupérable dans Exchange Online et reste en état de suppression récupérable pendant 30 jours.</span><span class="sxs-lookup"><span data-stu-id="fef9b-116">The user mailbox is now soft-deleted in Exchange Online and stays in a soft-deleted state for 30 days.</span></span> <span data-ttu-id="fef9b-117">Si, dans la période de 30 jours, un nouvel utilisateur Azure Active Directory est synchronisé à partir du compte de destinataire d’origine avec le même **ExchangeGuid** ou **ArchiveGuid**, et que le nouveau compte est concédé sous licence pour Exchange Online, une suppression matérielle de la boîte aux lettres de l’utilisateur d’origine sera effectuée.</span><span class="sxs-lookup"><span data-stu-id="fef9b-117">If in the 30-day period a new Azure Active Directory user is synchronized from the original recipient account with the same **ExchangeGuid** or **ArchiveGuid**, and that new account is licensed for Exchange Online, this will result in a hard deletion of the original user mailbox.</span></span> <span data-ttu-id="fef9b-118">Tout le contenu des boîtes aux lettres, comme les courriers électroniques, les contacts et les fichiers, est définitivement supprimé.</span><span class="sxs-lookup"><span data-stu-id="fef9b-118">All mailbox content such as emails, contacts and files are permanently deleted.</span></span>
- <span data-ttu-id="fef9b-119">Une boîte aux lettres supprimée (récupérable) est supprimée à l’aide de **Remove-Mailbox-PermanentlyDelete**.</span><span class="sxs-lookup"><span data-stu-id="fef9b-119">A soft-deleted mailbox is deleted using **Remove-Mailbox -PermanentlyDelete**.</span></span>

<span data-ttu-id="fef9b-120">Les scénarios de suppression ci-dessus supposent que la boîte aux lettres de l’utilisateur n’est pas dans l’un des États de suspension, comme la conservation pour litige ou la découverte électronique.</span><span class="sxs-lookup"><span data-stu-id="fef9b-120">The above deletion scenarios assume that the user mailbox isn't in any of the hold states, like Litigation hold or eDiscovery hold.</span></span> <span data-ttu-id="fef9b-121">S’il existe un type de conservation sur la boîte aux lettres, la boîte aux lettres ne peut pas être supprimée.</span><span class="sxs-lookup"><span data-stu-id="fef9b-121">If there is any type of hold on the mailbox, then the mailbox can't be deleted.</span></span> <span data-ttu-id="fef9b-122">Pour tous les types de destinataires de messagerie, tous les paramètres de [conservation](https://support.office.com/article/manage-legal-investigations-in-office-365-2e5fbe9f-ee4d-4178-8ff8-4356bc1b168e?ui=en-US&rs=en-US&ad=US) sont ignorés et n’ont aucun effet sur les suppressions ou suppressions logicielles.</span><span class="sxs-lookup"><span data-stu-id="fef9b-122">For all mail-user recipient types, any [Hold](https://support.office.com/article/manage-legal-investigations-in-office-365-2e5fbe9f-ee4d-4178-8ff8-4356bc1b168e?ui=en-US&rs=en-US&ad=US) settings are ignored and have no effect on hard-deletions or soft-deletions.</span></span>

## <a name="soft-deleted-and-hard-deleted-items"></a><span data-ttu-id="fef9b-123">Éléments supprimés et supprimés définitivement</span><span class="sxs-lookup"><span data-stu-id="fef9b-123">Soft-Deleted and Hard-Deleted Items</span></span>
<span data-ttu-id="fef9b-124">Lorsqu’un utilisateur supprime un élément de boîte aux lettres (par exemple, un message électronique, un contact, un rendez-vous de calendrier ou une tâche), l’élément est déplacé vers le dossier éléments récupérables et dans un sous-dossier nommé « suppressions ».</span><span class="sxs-lookup"><span data-stu-id="fef9b-124">When a user deletes a mailbox item (such as an email message, a contact, a calendar appointment, or a task), the item is moved to the Recoverable Items folder, and into a subfolder named "Deletions".</span></span> <span data-ttu-id="fef9b-125">Il s’agit d’une suppression douce.</span><span class="sxs-lookup"><span data-stu-id="fef9b-125">This is referred to as a soft deletion.</span></span> <span data-ttu-id="fef9b-126">La durée de conservation dans le dossier Suppressions des éléments supprimés dépend de la période de rétention des éléments supprimés qui est définie pour la boîte aux lettres.</span><span class="sxs-lookup"><span data-stu-id="fef9b-126">How long deleted items are kept in the Deletions folder depends on the deleted item retention period that is set for the mailbox.</span></span> <span data-ttu-id="fef9b-127">Une boîte aux lettres Exchange Online conserve les éléments supprimés pendant 14 jours par défaut, mais les administrateurs Exchange Online peuvent modifier ce paramètre pour augmenter la période maximale de 30 jours.</span><span class="sxs-lookup"><span data-stu-id="fef9b-127">An Exchange Online mailbox keeps deleted items for 14 days by default, but Exchange Online administrators can change this setting to increase the period up to a maximum of 30 days.</span></span> <span data-ttu-id="fef9b-128">(Pour obtenir la procédure détaillée d’augmentation de la période de rétention des éléments supprimés pour une boîte aux lettres Exchange Online, voir [modifier la durée de conservation des éléments supprimés définitivement pour une boîte aux lettres Exchange Online](https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-user-mailboxes/change-deleted-item-retention).) Les utilisateurs peuvent récupérer ou purger les éléments supprimés avant l’expiration du délai de rétention d’un élément supprimé.</span><span class="sxs-lookup"><span data-stu-id="fef9b-128">(For detailed steps to increase the deleted item retention period for an Exchange Online mailbox, see [Change how long permanently deleted items are kept for an Exchange Online mailbox](https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-user-mailboxes/change-deleted-item-retention).) Users can recover, or purge, deleted items before the retention time for a deleted item expires.</span></span> <span data-ttu-id="fef9b-129">Pour ce faire, ils utilisent la fonctionnalité récupérer les éléments supprimés dans Microsoft Outlook ou Outlook sur le Web.</span><span class="sxs-lookup"><span data-stu-id="fef9b-129">To do so, they use the Recover Deleted Items feature in Microsoft Outlook or Outlook on the web.</span></span>

<span data-ttu-id="fef9b-130">Si un utilisateur efface un élément supprimé à l’aide de la fonctionnalité récupérer les éléments supprimés dans Outlook ou Outlook sur le Web, il s’agit d’une suppression matérielle.</span><span class="sxs-lookup"><span data-stu-id="fef9b-130">If a user purges a deleted item by using the Recover Deleted Items feature in Outlook or Outlook on the web, this is known as a hard deletion.</span></span> <span data-ttu-id="fef9b-131">Dans Exchange Online, la récupération d’élément unique est activée par défaut lors de la création d’une nouvelle boîte aux lettres, de sorte qu’un administrateur peut toujours [récupérer](https://docs.microsoft.com/Exchange/recipients/user-mailboxes/recover-deleted-messages) des éléments supprimés définitivement avant l’expiration de la période de rétention des éléments supprimés.</span><span class="sxs-lookup"><span data-stu-id="fef9b-131">In Exchange Online, single item recovery is enabled by default when a new mailbox is created, so an administrator can still [recover](https://docs.microsoft.com/Exchange/recipients/user-mailboxes/recover-deleted-messages) hard-deleted items before the deleted item retention period expires.</span></span> <span data-ttu-id="fef9b-132">En outre, si un message est modifié par un utilisateur ou un processus, des copies de l'élément d'origine sont également conservées lorsque la fonctionnalité de récupération d'élément unique est activée.</span><span class="sxs-lookup"><span data-stu-id="fef9b-132">Also, if a message is changed by a user or a process, copies of the original item are also retained when single item recovery is enabled.</span></span>

## <a name="page-zeroing"></a><span data-ttu-id="fef9b-133">Mise à zéro des pages</span><span class="sxs-lookup"><span data-stu-id="fef9b-133">Page Zeroing</span></span>
<span data-ttu-id="fef9b-134">La mise à *zéro* est un mécanisme de sécurité qui écrit des zéros ou un modèle binaire sur les données supprimées de manière à ce que les données supprimées soient plus difficiles à récupérer.</span><span class="sxs-lookup"><span data-stu-id="fef9b-134">*Zeroing* is a security mechanism that writes either zeros or a binary pattern over deleted data so that the deleted data is more difficult to recover.</span></span> <span data-ttu-id="fef9b-135">Dans Exchange Online, les bases de données de boîtes aux lettres utilisent des *pages* comme leur unité de stockage et implémentent un processus de remplacement appelé mise à *zéro de page*.</span><span class="sxs-lookup"><span data-stu-id="fef9b-135">In Exchange Online, mailbox databases use *pages* as their unit of storage, and implement an overwriting process called *page zeroing*.</span></span> <span data-ttu-id="fef9b-136">La mise à zéro des pages est activée par défaut et ne peut pas être désactivée par les clients ou par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fef9b-136">Page zeroing is enabled by default, and it cannot be disabled by customers or by Microsoft.</span></span> <span data-ttu-id="fef9b-137">Les opérations de mise à zéro des pages sont enregistrées dans les fichiers journaux des transactions de sorte que toutes les copies d’une base de données donnée soient mises à zéro par page de la même manière.</span><span class="sxs-lookup"><span data-stu-id="fef9b-137">Page zeroing operations are recorded in the transaction log files so that all copies of a given database are page-zeroed in a similar manner.</span></span> <span data-ttu-id="fef9b-138">La mise à zéro d’une page sur une copie de base de données active fait en sorte que la page soit remise à zéro sur les copies passives de la base de données.</span><span class="sxs-lookup"><span data-stu-id="fef9b-138">Zeroing a page on an active database copy causes the page to get zeroed on passive copies of the database.</span></span>

<span data-ttu-id="fef9b-139">La mise à zéro des pages écrit un modèle binaire sur les enregistrements supprimés définitivement.</span><span class="sxs-lookup"><span data-stu-id="fef9b-139">Page zeroing writes a binary pattern over hard-deleted records.</span></span> <span data-ttu-id="fef9b-140">Le modèle de mise à zéro des pages est spécifique aux opérations ESE (Extensible Storage Engine) (le nom du moteur de base de données interne utilisé par les serveurs dans Exchange Online) et il est différent pour les opérations d’exécution et les opérations de maintenance de la base de données en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="fef9b-140">The page-zeroing pattern is specific to Extensible Storage Engine (ESE) operations (the name of the internal database engine used by servers in Exchange Online), and it is different for run-time operations versus background database maintenance operations.</span></span> <span data-ttu-id="fef9b-141">(La maintenance de base de données en arrière-plan est un processus qui analyse en continu et analyse chaque base de données.</span><span class="sxs-lookup"><span data-stu-id="fef9b-141">(Background database maintenance is a process that continuously checksums and scans each database.</span></span> <span data-ttu-id="fef9b-142">Sa fonction principale est de totaliser les pages de base de données, mais elle gère également le nettoyage des enregistrements et des pages qui n’ont pas été annulés en raison d’un blocage de la Banque.)</span><span class="sxs-lookup"><span data-stu-id="fef9b-142">Its primary function is to checksum database pages, but it also handles cleaning up space and zeroing out records and pages that were not zeroed out because of a Store crash.)</span></span>

<span data-ttu-id="fef9b-143">Le tableau suivant répertorie les schémas de remplissage qui correspondent à des opérations d'exécution particulières.</span><span class="sxs-lookup"><span data-stu-id="fef9b-143">The following table lists the fill patterns that correspond to specific run-time operations.</span></span>

| <span data-ttu-id="fef9b-144">Opération d’exécution d’ESE</span><span class="sxs-lookup"><span data-stu-id="fef9b-144">ESE run-time operation</span></span>   | <span data-ttu-id="fef9b-145">Modèle de remplissage</span><span class="sxs-lookup"><span data-stu-id="fef9b-145">Fill pattern</span></span> |
|--------------------------|--------------|
| <span data-ttu-id="fef9b-146">Remplacement</span><span class="sxs-lookup"><span data-stu-id="fef9b-146">Replace</span></span>                  | <span data-ttu-id="fef9b-147">R</span><span class="sxs-lookup"><span data-stu-id="fef9b-147">R</span></span>            |
| <span data-ttu-id="fef9b-148">Suppression d'enregistrement/de valeur longue</span><span class="sxs-lookup"><span data-stu-id="fef9b-148">Record/long value delete</span></span> | <span data-ttu-id="fef9b-149">D</span><span class="sxs-lookup"><span data-stu-id="fef9b-149">D</span></span>            |
| <span data-ttu-id="fef9b-150">Espace de page libéré</span><span class="sxs-lookup"><span data-stu-id="fef9b-150">Freed page space</span></span>         | <span data-ttu-id="fef9b-151">H</span><span class="sxs-lookup"><span data-stu-id="fef9b-151">H</span></span>            |


<span data-ttu-id="fef9b-152">Le tableau suivant répertorie les schémas de remplissage correspondant à des opérations spécifiques effectuées pendant une opération de maintenance de base de données ESE en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="fef9b-152">The following table lists the fill patterns that correspond to specific operations that occur during ESE background database maintenance.</span></span>

| <span data-ttu-id="fef9b-153">Opération de maintenance de base de données ESE en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="fef9b-153">ESE background database maintenance operation</span></span> | <span data-ttu-id="fef9b-154">Modèle de remplissage</span><span class="sxs-lookup"><span data-stu-id="fef9b-154">Fill pattern</span></span> |
|-----------------------------------------------|--------------|
| <span data-ttu-id="fef9b-155">Suppression d’enregistrement</span><span class="sxs-lookup"><span data-stu-id="fef9b-155">Record delete</span></span>                                 | <span data-ttu-id="fef9b-156">D</span><span class="sxs-lookup"><span data-stu-id="fef9b-156">D</span></span>            |
| <span data-ttu-id="fef9b-157">Suppression de valeur longue</span><span class="sxs-lookup"><span data-stu-id="fef9b-157">Long value delete</span></span>                             | <span data-ttu-id="fef9b-158">L</span><span class="sxs-lookup"><span data-stu-id="fef9b-158">L</span></span>            |
| <span data-ttu-id="fef9b-159">Espace libéré sur la page partiellement utilisée</span><span class="sxs-lookup"><span data-stu-id="fef9b-159">Freed page space of partially used page</span></span>       | <span data-ttu-id="fef9b-160">Z</span><span class="sxs-lookup"><span data-stu-id="fef9b-160">Z</span></span>            |
| <span data-ttu-id="fef9b-161">Espace libéré sur la page inutilisée</span><span class="sxs-lookup"><span data-stu-id="fef9b-161">Freed page space of unused page</span></span>               | <span data-ttu-id="fef9b-162">U</span><span class="sxs-lookup"><span data-stu-id="fef9b-162">U</span></span>            |


### <a name="page-zeroing-process"></a><span data-ttu-id="fef9b-163">Processus de mise à zéro des pages</span><span class="sxs-lookup"><span data-stu-id="fef9b-163">Page Zeroing Process</span></span>
<span data-ttu-id="fef9b-164">Le processus de mise à zéro des pages dépend du scénario de suppression.</span><span class="sxs-lookup"><span data-stu-id="fef9b-164">The process for page zeroing depends on the deletion scenario.</span></span> <span data-ttu-id="fef9b-165">Le tableau suivant décrit les scénarios de suppression de base de données et les circonstances dans lesquelles les fonctions de mise à zéro des pages sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="fef9b-165">The following table discusses database delete scenarios, and when page zeroing functions occur.</span></span>

| <span data-ttu-id="fef9b-166">Scénario de suppression de base de données</span><span class="sxs-lookup"><span data-stu-id="fef9b-166">Database delete scenario</span></span> | <span data-ttu-id="fef9b-167">Processus et délai nécessaire à ESE pour mettre à zéro les données de la base de données</span><span class="sxs-lookup"><span data-stu-id="fef9b-167">ESE process and timeframe to zero database data</span></span> |
|-----------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="fef9b-168">L’élément expire en fonction de la période de rétention des éléments supprimés.</span><span class="sxs-lookup"><span data-stu-id="fef9b-168">Item expires based on the deleted item retention period.</span></span> | <span data-ttu-id="fef9b-169">Un thread asynchrone écrit un masque binaire sur les données supprimées.</span><span class="sxs-lookup"><span data-stu-id="fef9b-169">An asynchronous thread writes a binary pattern over the deleted data.</span></span> <span data-ttu-id="fef9b-170">Cette action se produit dans les millisecondes suivant la suppression de l'enregistrement.</span><span class="sxs-lookup"><span data-stu-id="fef9b-170">This action occurs within milliseconds of the record deletion.</span></span> <span data-ttu-id="fef9b-171">Si le processus de banque se bloque alors que le travail de mise à zéro asynchrone est toujours en attente (ou le nettoyage du magasin de version est annulé en raison de la croissance du magasin de versions), la mise à zéro est effectuée lorsque la maintenance de base de données en arrière-plan traite cette section de la base de données.</span><span class="sxs-lookup"><span data-stu-id="fef9b-171">If the Store process crashes while the asynchronous zeroing work is still outstanding (or version store cleanup is canceled due to version store growth), the zeroing is completed when background database maintenance processes that section of the database.</span></span> |
| <span data-ttu-id="fef9b-172">Scénario d’affichage : expiration des éléments d’Outlook/Outlook sur l’affichage des dossiers Web (par exemple, affichage conversation)</span><span class="sxs-lookup"><span data-stu-id="fef9b-172">View Scenario: Expiration of items from Outlook/Outlook on the web folder view (for example, Conversation view)</span></span> | <span data-ttu-id="fef9b-173">La mise à zéro des données a lieu lorsque la maintenance de base de données en arrière-plan traite cette section de la base de données.</span><span class="sxs-lookup"><span data-stu-id="fef9b-173">Data zeroing occurs when background database maintenance processes that section of the database.</span></span> |
| <span data-ttu-id="fef9b-174">Déplacer une boîte aux lettres/supprimer un scénario de boîte aux lettres : boîte aux lettres source supprimée (expiration de la boîte aux lettres supprimée)</span><span class="sxs-lookup"><span data-stu-id="fef9b-174">Move Mailbox/Delete Mailbox Scenario: Source mailbox deleted (expiry of deleted mailbox)</span></span> | <span data-ttu-id="fef9b-175">La mise à zéro des données a lieu lorsque la maintenance de base de données en arrière-plan traite cette section de la base de données.</span><span class="sxs-lookup"><span data-stu-id="fef9b-175">Data zeroing occurs when background database maintenance processes that section of the database.</span></span> |

### <a name="mailbox-data-types-without-page-zeroing"></a><span data-ttu-id="fef9b-176">Types de données de boîte aux lettres sans mise à zéro des pages</span><span class="sxs-lookup"><span data-stu-id="fef9b-176">Mailbox Data Types without Page Zeroing</span></span>
<span data-ttu-id="fef9b-177">Les types de données de boîte aux lettres suivants n’ont aucune disposition pour la mise à zéro des pages :</span><span class="sxs-lookup"><span data-stu-id="fef9b-177">The following mailbox data types have no provisions for page zeroing:</span></span>
- <span data-ttu-id="fef9b-178">**Journaux de transactions de la base de données de boîtes aux lettres** : lorsque les journaux de transactions sont supprimés dans le cadre d’opérations normales, le système de fichiers n’est pas mis à zéro pour les blocs qui stockaient les fichiers journaux supprimés.</span><span class="sxs-lookup"><span data-stu-id="fef9b-178">**Mailbox database transaction logs** - When transaction logs are deleted as part of normal operations, there is no process to zero the blocks in the file system that stored the deleted log file(s).</span></span> <span data-ttu-id="fef9b-179">Il est probable que le système de fichiers réutilise rapidement cet espace disponible pour les journaux nouvellement créés, mais il n’y a aucune garantie que cela se produira.</span><span class="sxs-lookup"><span data-stu-id="fef9b-179">It's likely that the file system will quickly re-utilize that free space for newly created logs, but there is no guarantee that this will happen.</span></span>
- <span data-ttu-id="fef9b-180">**Fichiers du catalogue d’indexation de contenu** : Exchange Online utilise Search Foundation (également appelé Fast) pour la fonctionnalité d’indexation de la recherche.</span><span class="sxs-lookup"><span data-stu-id="fef9b-180">**Content index catalog files** - Exchange Online uses Search Foundation (also known as FAST) for search indexing functionality.</span></span> <span data-ttu-id="fef9b-181">Le catalogue d’index de recherche est composé de plusieurs douzaines de fichiers stockés sur le même volume que le fichier de base de données de boîtes aux lettres.</span><span class="sxs-lookup"><span data-stu-id="fef9b-181">The search index catalog is composed of several dozen files stored on the same volume as the mailbox database file.</span></span> <span data-ttu-id="fef9b-182">Lorsqu'un message est définitivement supprimé de la base de données de boîtes aux lettres, le contenu associé dans le catalogue de recherche n'est pas immédiatement supprimé.</span><span class="sxs-lookup"><span data-stu-id="fef9b-182">When a message is hard-deleted from the mailbox database, the associated content in the search catalog isn't immediately deleted.</span></span> <span data-ttu-id="fef9b-183">La suppression de contenu se produit lorsque Search Foundation effectue une fusion (ou une fusion principale) de nombreux petits fichiers de catalogue dans un fichier unique plus volumineux.</span><span class="sxs-lookup"><span data-stu-id="fef9b-183">Content deletion occurs when Search Foundation does a shadow (or master merge) of many small catalog files in to a single larger file.</span></span> <span data-ttu-id="fef9b-184">Une fois la fusion principale terminée, les fichiers de catalogue plus petits sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="fef9b-184">After the master merge completes, the smaller catalog files are deleted.</span></span> <span data-ttu-id="fef9b-185">Aucun processus de mise à zéro des blocs stockant les fichiers de catalogue supprimés.</span><span class="sxs-lookup"><span data-stu-id="fef9b-185">There is no process to zero the blocks which stored the deleted catalog files.</span></span>

## <a name="continuous-replication"></a><span data-ttu-id="fef9b-186">Réplication continue</span><span class="sxs-lookup"><span data-stu-id="fef9b-186">Continuous Replication</span></span>
<span data-ttu-id="fef9b-187">La réplication continue (également appelée envoi et relecture de journaux) est une technologie dans Exchange Online qui crée et gère des copies de chaque base de données de boîtes aux lettres pour fournir une haute disponibilité, la résilience de site et la récupération d’urgence.</span><span class="sxs-lookup"><span data-stu-id="fef9b-187">Continuous replication (also known as log shipping and replay) is technology in Exchange Online that creates and maintains copies of every mailbox database to provide high availability, site resilience, and disaster recovery.</span></span> <span data-ttu-id="fef9b-188">La réplication continue exploite la prise en charge de la récupération d’urgence de base de données Exchange Server pour fournir une technologie qui effectue la mise à jour asynchrone d’une ou plusieurs copies d’une base de données de boîtes aux lettres.</span><span class="sxs-lookup"><span data-stu-id="fef9b-188">Continuous replication leverages the Exchange Server database crash recovery support to provide technology that performs asynchronous updating of one or more copies of a mailbox database.</span></span> <span data-ttu-id="fef9b-189">Chaque serveur de boîtes aux lettres enregistre les mises à jour de base de données effectuées sur une base de données active (par exemple, l’activité de courrier électronique de l’utilisateur) sous la forme d’enregistrements de journal dans un ensemble séquentiel de fichiers journaux de transactions de 1 Mo.</span><span class="sxs-lookup"><span data-stu-id="fef9b-189">Each mailbox server records database updates made on an active database (for example, user email activity) as log records in a sequential set of 1 MB transaction log files.</span></span> <span data-ttu-id="fef9b-190">Cet ensemble de fichiers est appelé flux de journal.</span><span class="sxs-lookup"><span data-stu-id="fef9b-190">This set of files is referred to as the log stream.</span></span> <span data-ttu-id="fef9b-191">Dans une réplication continue, le flux de journal est également utilisé pour mettre à jour de manière asynchrone une ou plusieurs copies d’une base de données.</span><span class="sxs-lookup"><span data-stu-id="fef9b-191">In continuous replication, the log stream is also used to asynchronously update one or more copies of a database.</span></span> <span data-ttu-id="fef9b-192">Pour cela, il suffit de transmettre les journaux à un emplacement contenant une copie passive de la base de données active, puis de les relire dans la copie passive de la base de données.</span><span class="sxs-lookup"><span data-stu-id="fef9b-192">This is accomplished by transmitting the logs to a location containing a passive copy of the active database and then replaying them into the passive database copy.</span></span> <span data-ttu-id="fef9b-193">Si tous les journaux de la base de données active sont relus par rapport à une copie passive de la base de données, les deux bases de données sont équivalentes, ce qui explique que toute modification physique apportée à une base de données active est répliquée sur toutes les copies passives de cette base de données.</span><span class="sxs-lookup"><span data-stu-id="fef9b-193">If all logs from the active database are replayed against a passive copy of the database, then the two databases are equivalent, and it is through this process that any physical change made to an active database is replicated to all passive copies of that database.</span></span>

<span data-ttu-id="fef9b-194">Toute suppression d’une base de données de boîtes aux lettres, qu’il s’agisse d’un élément de boîte aux lettres ou d’une boîte aux lettres entière, et si une suppression récupérable ou une suppression définitive, représente une modification physique de la base de données active.</span><span class="sxs-lookup"><span data-stu-id="fef9b-194">Any deletion from a mailbox database, whether a mailbox item or an entire mailbox, and whether a soft-delete or a hard-delete, represents a physical change to the active database.</span></span> <span data-ttu-id="fef9b-195">La mise à zéro des pages implique également d’apporter des modifications physiques à la base de données active.</span><span class="sxs-lookup"><span data-stu-id="fef9b-195">Page zeroing also entails making physical changes to the active database.</span></span> <span data-ttu-id="fef9b-196">Ces modifications sont écrites dans les fichiers journaux par le biais d’un processus appelé réplication continue et, lorsque ces fichiers journaux sont relus par rapport à des copies passives de la base de données, les mêmes modifications physiques sont apportées à ces bases de données passives.</span><span class="sxs-lookup"><span data-stu-id="fef9b-196">These changes are written to the log files through a process called continuous replication, and when those log files are replayed against passive copies of the database, the same physical changes are made to those passive databases.</span></span>