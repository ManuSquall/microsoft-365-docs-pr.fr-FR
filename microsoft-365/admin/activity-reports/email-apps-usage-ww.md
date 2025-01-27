---
title: Microsoft 365 Rapports dans le Centre d’administration - Utilisation des applications de messagerie
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
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: c2ce12a2-934f-4dd4-ba65-49b02be4703d
description: Découvrez comment obtenir le rapport d’utilisation des applications de messagerie pour en savoir plus sur les applications de messagerie qui se connectent Exchange Online et la version Outlook utilisateurs utilisent.
ms.openlocfilehash: f2a7b79a00b47896dac4427c532f85dccb931c60
ms.sourcegitcommit: 7ecd10b302b3b3dfa4ba3be3a6986dd3c189fbff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/21/2021
ms.locfileid: "49921952"
---
# <a name="microsoft-365-reports-in-the-admin-center---email-apps-usage"></a>Microsoft 365 Rapports dans le Centre d’administration - Utilisation des applications de messagerie

Le tableau de bord Microsoft 365 **rapports de** gestion des données vous présente la vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Voir [la rubrique Présentation des rapports](activity-reports.md). Dans le rapport d’utilisation des applications de messagerie, vous pouvez voir le nombre d’applications de messagerie qui se connectent à Exchange Online. Vous pouvez également afficher les informations relatives à la version des applications Outlook utilisées, ce qui vous permet d'assurer le suivi des personnes utilisant des versions non prises en charge pour installer les versions prises en charge d'Outlook.
  
> [!NOTE]
> Vous devez être administrateur général, lecteur général ou lecteur de rapports dans Microsoft 365 ou administrateur Exchange, SharePoint, service Teams, Teams Communications ou administrateur Skype Entreprise pour consulter les rapports.  
 
## <a name="how-to-get-to-the-email-apps-report"></a>Comment obtenir le rapport des applications de messagerie

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.
2. Sélectionnez **Afficher plus sous** Activité de **messagerie.** 
3. Dans la liste **de listes** de listes des activités de messagerie, sélectionnez  \> **Exchange’utilisation** des applications de messagerie.
  
## <a name="interpret-the-email-apps-report"></a>Interpréter le rapport des applications de messagerie

Vous pouvez obtenir une vue de l’activité des applications de messagerie en regardant **les** graphiques Utilisateurs **et clients.** 
  
![Clients de messagerie utilisés](../../media/d78af7db-2b41-4d37-8b6e-bc7e47edd1dd.png)
  
|Item|Description|
|:-----|:-----|
|1.  <br/> |Le **rapport d’utilisation** des applications de messagerie permet d’afficher les tendances des 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau (7) affiche les données jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).  <br/> |
|2.  <br/> |Les données de chaque rapport couvrent généralement jusqu’aux dernières 24 à 48 heures.  <br/> |
|3.  <br/> |L'affichage **Utilisateurs** indique le nombre d'utilisateurs uniques connectés à Exchange Online à l'aide d'une application de messagerie.  <br/> |
|4.  <br/> |L'affichage **Applications** indique le nombre d'utilisateurs uniques par application sur la période sélectionnée.  <br/> |
|5.  <br/> |**L’affichage Versions** indique le nombre d’utilisateurs uniques pour chaque version Outlook dans Windows.  <br/> |
|6.  <br/> | Sur le graphique **Utilisateurs**, l'axe Y représente le nombre total d'utilisateurs uniques connectés à une application n'importe quel jour de la période du rapport.  <br/>  Sur le graphique **Utilisateurs**, l'axe X représente le nombre d'utilisateurs uniques à avoir utilisé l'application pendant la période du rapport.  <br/>  Sur le graphique **Applications**, l'axe Y représente le nombre total d'utilisateurs uniques à avoir utilisé une application spécifique pendant la période du rapport.  <br/>  Sur le graphique **Applications**, l'axe X répertorie les applications de votre organisation.  <br/>  Sur le graphique **Versions**, l'axe Y représente le nombre total d'utilisateurs uniques utilisant une version de bureau spécifique d'Outlook. Si le rapport ne peut pas résoudre le numéro de version Outlook, la quantité s’affiche **comme indéterminée.**  <br/>  Sur le graphique **Versions**, l'axe X répertorie les applications de votre organisation.  <br/> |
|7.  <br/> |Vous pouvez filtrer les séries que vous voyez sur le graphique en sélectionnant un élément dans la légende.  <br/> |
|8.  <br/> | Vous ne voyez pas forcément tous les éléments dans la liste en dessous des colonnes jusqu'à ce que vous les ajoutiez.<br/> **Le nom** d’utilisateur est le nom du propriétaire de l’application de messagerie.  <br/> **La date de la** dernière activité est la date la plus récente à laquelle l’utilisateur a lu ou envoyé un message électronique.  <br/> **Mac Mail**, **Mac Outlook**, **Outlook**, **Outlook Mobile** et **Outlook sur le web** sont des exemples d'applications de messagerie dont vous pouvez disposer dans votre organisation.  <br/>  Si la politique de votre organisation vous empêche de consulter les rapports sur lesquels figurent des informations propres aux utilisateurs, vous pouvez modifier les paramètres de confidentialité de tous ces rapports. Consultez la section **Comment puis-je masquer les détails** au niveau de l’utilisateur ? dans les rapports d’activité [dans Microsoft 365 centre d’administration.](activity-reports.md)  <br/> |
|9.  <br/> |Sélectionnez **Sélectionner des colonnes** pour ajouter ou supprimer des colonnes dans le rapport.  <br/> ![Rapport d’utilisation des applications de messagerie - Choisir les colonnes](../../media/041bd6ff-27e8-409d-9608-282edcfa2316.png)|
|10.  <br/> |Vous pouvez également exporter les données du rapport dans un Excel .csv, en sélectionnant le lien **Exporter.** Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter.  <br/> |
|||
   
