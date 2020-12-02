---
title: Expérience client pendant la migration vers les services Office 365 dans les nouvelles régions de centre de données allemandes
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 12/01/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: 'Résumé : Découvrez l’expérience de passage de Microsoft Cloud Germany (Microsoft Cloud Deutschland) aux services Office 365 dans la nouvelle région de centre de connaissances allemande.'
ms.openlocfilehash: a44fbe504a9a710856deeb3baf258feb124ce7ae
ms.sourcegitcommit: 38d828ae8d4350ae774a939c8decf30cb36c3bea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "49551694"
---
# <a name="customer-experience-during-the-migration-to-office-365-services-in-the-new-german-datacenter-regions"></a>Expérience client pendant la migration vers les services Office 365 dans les nouvelles régions de centre de données allemandes

Les migrations client sont conçues pour avoir un impact minimal sur les administrateurs et les utilisateurs. Toutefois, il existe des facteurs à prendre en compte pour chaque charge de travail. Consultez les sections suivantes pour mieux comprendre l’expérience de migration pour les charges de travail.

Vous trouverez ci-dessous les principales différences entre Microsoft Cloud Deutschland et les services Office 365 dans les nouvelles régions de centre de connaissances allemand.

| Catégorie | Microsoft Cloud Deutschland (Microsoft Cloud Deutschland) | Services Office 365 dans les nouvelles régions de centre de données allemandes |
|:-------|:-----|:-------|
| Services Microsoft 365 disponibles pour un abonnement avec un seul client Office 365 | 15 services | 29 services <br><br> Pour plus d’informations, voir [qu’est-ce que la disponibilité du service entre les différentes offres de service Cloud Office 365 ?](ms-cloud-germany-transition.md#serv-avail). |
| Nouvelles fonctionnalités | Aucune nouvelle fonctionnalité n’est disponible. | Les nouvelles fonctionnalités seront disponibles conformément aux services Office 365. |
| Administrateur de données | Oui | Non |
| Collaboration entre clients Office 365 du monde entier | Non | Oui |
| Résidence des données client | Les données client seront stockées uniquement dans les centres de données allemands. | Microsoft stockera les données client suivantes au repos exclusivement en Allemagne : <ul><li> Contenu de boîte aux lettres Exchange Online (corps de courrier électronique, entrées de calendrier et contenu de pièces jointes) </li><li> Contenu de site SharePoint Online et fichiers stockés dans ce site, et fichiers téléchargés vers OneDrive entreprise </li></ul> |
| Conditions applicables | [Conditions des services en ligne](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46) avec ce [supplément](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=64) | [Conditions d’utilisation d’Online Services](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46) |
||||

## <a name="azure-active-directory"></a>Azure Active Directory

Ce qui ne change pas :

- Le domaine initial client (par exemple, `contoso.onmicrosoft.de` ) avec un ID de client (Guid) et des domaines personnalisés est conservé après la migration. 

- Les demandes d’authentification pour les ressources migrées vers les services Office 365 sont accordées par le service d’authentification Azure des services Office 365 ( `login.microsoftonline.com` ). Au cours de la migration, les ressources qui restent dans Office 365 Germany sont authentifiées par le service Allemagne Azure existant ( `login.microsoftonline.de` ).

Considérations à noter :

- Pour les comptes de domaine géré, une fois que la copie du client Azure Active Directory (Azure AD) initial est terminée (ce qui est la première étape de la migration Azure AD vers le service Azure AD service Office 365 services), les modifications de mot de passe, les modifications de réinitialisation de mot de passe 365 en libre-service et les réinitialisations de mot Les demandes de mise à jour des mots de passe à partir du service d’Allemagne ne réussissent pas à ce stade, car le client Azure AD a été migré vers les services Office 365. Les réinitialisations des mots de passe de domaine fédérés ne sont pas affectées, car elles sont terminées dans l’annuaire local.

- Les connexions Azure sont présentées dans le portail auquel l’utilisateur tente d’accéder. Les journaux d’audit sont disponibles uniquement à partir du point de terminaison des services Office 365 après une transition. Avant d’effectuer la migration jusqu’à la fin de la migration, vous devez enregistrer les journaux de connexion et d’audit à partir du portail Microsoft Cloud Deutschland.

- Les réinitialisations de mot de passe, les modifications de mot de passe, la réinitialisation du mot de passe par un administrateur pour les organisations gérées (qui n’utilisent pas Active Directory Federation Services) doivent être effectuées via le portail des services Office 365. Les tentatives des utilisateurs qui accèdent aux portails Microsoft Cloud Deutschland pour réinitialiser les mots de passe échoueront.

- General Data Protection Regulation (RGPD) les demandes des personnes concernées (DSR) sont exécutées à partir du portail d’administration Azure des services Office 365 pour les demandes ultérieures. Toute donnée de diagnostic héritée ou non client résidente dans Microsoft Cloud Deutschland est supprimée au moins 30 jours.

## <a name="subscriptions--licenses"></a>Abonnements & des licences

- Les abonnements Office 365 et Dynamics de Microsoft Cloud Deutschland sont transférés vers la région allemande avec le réadressage Azure AD. L’organisation est ensuite mise à jour pour refléter les nouveaux abonnements aux services Office 365. Lors du processus de transfert d’abonnement Brief, les modifications apportées aux abonnements sont bloquées.

- Le client étant transféré vers les services Office 365, ses abonnements et licences spécifiques à l’Allemagne sont standardisés avec les nouvelles offres de services Office 365. Les abonnements aux services Office 365 correspondants sont achetés pour les abonnements Germany transférés. Les utilisateurs disposant de licences Germany se verront attribuer des licences Office 365 services. Une fois l’opération terminée, les abonnements d’Allemagne hérités sont annulés et supprimés du client des services Office 365 actuels.

- Après la migration des charges de travail individuelles, des fonctionnalités supplémentaires sont mises à disposition via les services Office 365 (tels que le planificateur Microsoft et Microsoft Flow) en raison des nouveaux abonnements aux services Office 365. Si cela est approprié pour votre organisation, l’administrateur du client ou de la gestion des licences peut désactiver les nouveaux plans de service lorsque vous planifiez la gestion des modifications afin de présenter les nouveaux services. Pour obtenir des instructions sur la désactivation des plans de service attribués aux licences des utilisateurs, consultez la rubrique [désactiver l’accès aux services Microsoft 365 lors de l’affectation de licences utilisateur](https://docs.microsoft.com/office365/enterprise/powershell/disable-access-to-services-while-assigning-user-licenses).

## <a name="exchange-online"></a>Exchange Online

- Les URL de ressource Exchange passent du point de terminaison d’Allemagne hérité `outlook.office.de` au point de terminaison des services Office 365 `outlook.office365.com` après la migration. Vos utilisateurs peuvent accéder à leur boîte aux lettres migrée à l’aide de l’URL héritée jusqu’à ce que la migration soit terminée. Les clients doivent faire passer les utilisateurs à la nouvelle URL dès que possible après que la migration Exchange commence à éviter de gêner le retrait de l’environnement de l’Allemagne. Les URL des services Office 365 pour Outlook services deviennent disponibles uniquement après le début de la migration Exchange.

- Les boîtes aux lettres sont migrées en tant que processus principal. Les utilisateurs de votre organisation peuvent se trouver dans Microsoft Cloud Deutschland ou dans la région allemande pendant la transition et font partie de la même organisation Exchange (dans la même liste d’adresses globale).

- Les utilisateurs d’Outlook Web App qui accèdent au service à l’aide d’une URL où leur boîte aux lettres ne réside pas, voient une invite d’authentification supplémentaire. Par exemple, si la boîte aux lettres de l’utilisateur se trouve dans les services Office 365 et que la connexion Outlook Web App de l’utilisateur utilise le point de terminaison hérité `outlook.office.de` , l’utilisateur s’authentifie d’abord sur `login.microsoftonline.de` , puis sur `login.microsoftonline.com` . Une fois la migration terminée, l’utilisateur peut accéder à la nouvelle URL ( `https://outlook.office365.com` ) et il voit seulement la demande de connexion attendue. 

## <a name="office-services"></a>Services Office

Les services Office Online sont accessibles via `office.de` le, avant et Pendant la transition. Une fois que les boîtes aux lettres des utilisateurs sont transférées vers les services Office 365, les utilisateurs doivent commencer à utiliser les URL des services Office 365. À mesure que les charges de travail suivantes migrent vers les services Office 365, leur interface à partir du portail office.com commencera à fonctionner.

## <a name="exchange-online-protection"></a>Exchange Online Protection

- Les fonctionnalités Exchange Online Protection (EOP) principales sont copiées dans la nouvelle région Germany.
- Centre de sécurité et conformité Office 365 les utilisateurs doivent effectuer une transition vers l’utilisation d’URL globales, `https://protection.office.com` dans le cadre de la migration.

## <a name="skype-for-business-online"></a>Skype Entreprise Online

Les clients Skype Entreprise Online existants sont transférés vers Microsoft Teams. Pour plus d’informations, reportez-vous à [https://aka.ms/SkypeToTeams-Home](https://aka.ms/SkypeToTeams-Home) .

## <a name="office-365-video"></a>Office 365 Video

La vidéo Office 365 est supprimée le 1er mars, 2021 et la vidéo Office 365 ne sera pas prise en charge après la migration de SharePoint Online vers les nouvelles régions de centre de contenu allemand. Le contenu de la vidéo Office 365 sera migré dans le cadre de la migration de SharePoint Online. Toutefois, les vidéos de la vidéo Office 365 ne seront pas lues dans l’interface utilisateur vidéo Office 365 après la migration SharePoint. En savoir plus sur la chronologie de la migration sur la [transition vidéo Office 365 vers Microsoft Stream (classique) Overview](https://docs.microsoft.com/stream/migrate-from-office-365#microsoft-cloud-deutschland-timeline).

## <a name="next-step"></a>Étape suivante

[Comprendre les actions et les impacts des phases de migration](ms-cloud-germany-transition-phases.md)

## <a name="more-information"></a>Plus d’informations

Mise en route :

- [Migration de Microsoft Cloud Deutschland vers Office 365 services dans les nouvelles régions de centre de connaissances allemand](ms-cloud-germany-transition.md)
- [Aide à la migration de Microsoft Cloud Deutschland : ](https://aka.ms/germanymigrateassist)
- [Comment opter pour une migration](ms-cloud-germany-migration-opt-in.md)

Navigation par le biais de la transition :

- [Actions et impacts sur les phases de migration](ms-cloud-germany-transition-phases.md)
- [Pré-travail supplémentaire](ms-cloud-germany-transition-add-pre-work.md)
- Informations supplémentaires pour les [services](ms-cloud-germany-transition-add-general.md), les [appareils](ms-cloud-germany-transition-add-devices.md), les [expériences](ms-cloud-germany-transition-add-experience.md)et [AD FS](ms-cloud-germany-transition-add-adfs.md).

Applications Cloud :

- [Informations sur le programme de migration Dynamics 365](https://aka.ms/d365ceoptin)
- [Informations sur le programme de migration Power BI](https://aka.ms/pbioptin)
- [Prise en main de votre mise à niveau vers Microsoft Teams](https://aka.ms/SkypeToTeams-Home)