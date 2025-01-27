---
title: Déployer les applications sur les appareils
description: Informations pour l’ajout et le déploiement d’applications sur Bureau géré Microsoft appareils.
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation, applications, applications métier, applications métier
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 8bfc53d46bdcb91c16e9f4a1ddbc8ab3f6dfb47e
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50922025"
---
# <a name="deploy-apps-to-devices"></a>Déployer les applications sur les appareils
Une partie de l’intégration à Bureau géré Microsoft inclut l’ajout et le déploiement d’applications sur les appareils de vos utilisateurs. Une fois que vous utilisez le portail Bureau géré Microsoft, vous pouvez ajouter et déployer vos applications. 

Le processus global ressemble à ceci :
1. [Ajoutez](#1) des applications au portail Bureau géré Microsoft : il peut s’y trouver des applications métier existantes ou des applications de Microsoft Store pour Entreprises que vous avez synchronisées avec Intune. 
2. [Créez Azure Active Directory groupes (AD)](#2) pour l’affectation d’application : vous utiliserez ces groupes pour gérer l’affectation d’application.
3. [Affecter des applications à vos utilisateurs](#3)

<span id="1" />

## <a name="step-1-add-apps-to-microsoft-managed-desktop-portal"></a>Étape 1 : Ajouter des applications au portail Bureau géré Microsoft web
Vous pouvez ajouter [Win32 ou Windows applications MSI](#lob-apps)ou Microsoft Store pour Entreprises [applications](#msfb-apps) à Bureau géré Microsoft, puis les déployer sur Bureau géré Microsoft appareils.

<span id="lob-apps">

###  <a name="win32-or-windows-msi-based-apps-to-microsoft-managed-desktop"></a>Win32 ou Windows applications MSI à Bureau géré Microsoft

Vous pouvez ajouter vos applications métier à votre Bureau géré Microsoft web. Pour plus d’informations sur les conditions requises pour les applications installées Bureau géré Microsoft appareils mobiles, voir [Bureau géré Microsoft’application requise.](../service-description/mmd-app-requirements.md)

Dans cette procédure, vous allez sélectionner le type d’application que vous souhaitez ajouter, puis configurer et télécharger la source de l’application. 

**Pour ajouter votre application LOB ou votre Windows à Bureau géré Microsoft portail**

Vous pouvez vous Bureau géré Microsoft portail, ou vous connectez à Intune, puis rechercher des Bureau géré Microsoft. Nous allons vous montrer la Bureau géré Microsoft portail. 

1.    Connectez-vous [Bureau géré Microsoft portail d’administration.](https://aka.ms/mmdportal) 
2.    Sous **Inventaire,** sélectionnez **Applications.**
3.    Dans la charge de travail applications, sélectionnez **Ajouter.**
4.    Dans **Ajouter une application,** sélectionnez **application** métier ou Windows **application (Win32).**
    - Si vous avez sélectionné une application **métier,** voir Ajouter une application métier Windows à [Microsoft Intune](/intune/lob-apps-windows) pour obtenir des instructions sur l’ajout et la configuration d’applications métier.
    - Si vous avez sélectionné **Windows application (Win32),** voir Gestion des applications [Win32](/intune/apps-win32-app-management) pour obtenir des instructions sur l’ajout et la configuration Windows applications.

<span id="msfb-apps">

### <a name="microsoft-store-for-business-apps"></a>Microsoft Store pour Entreprises applications
Si vous ne vous êtes pas inscrit à Microsoft Store pour Entreprises, vous pouvez vous inscrire lorsque vous achetez des applications. Une fois que vous avez vos applications, vous pouvez les synchroniser avec Bureau géré Microsoft. 

**Pour acheter des applications à partir du Microsoft Store pour Entreprises**

1. Connectez-vous [Microsoft Store pour Entreprises](https://businessstore.microsoft.com) avec votre compte Microsoft Store pour Entreprises administrateur.
2. Sélectionnez **Acheter pour mon groupe.**
3. Utilisez la recherche pour rechercher l’application de votre choix, puis sélectionnez l’application.
4. Dans les détails du produit, **sélectionnez Obtenir l’application.** Microsoft Store ajoute l’application **à vos produits** pour votre organisation.

**Pour forcer une synchronisation entre Intune et Microsoft Store pour Entreprises**
1. Connectez-vous au [centre Microsoft Endpoint Manager’administration.](https://go.microsoft.com/fwlink/?linkid=2109431)
2. Sélectionnez **les**  >  **connecteurs et jetons d’administration**  >  **des Microsoft Store pour Entreprises**.
3. Sélectionnez **Synchroniser** pour obtenir les applications que vous avez achetées auprès du Microsoft Store dans Intune.

**Pour vérifier qu’une synchronisation entre Intune et Microsoft Store pour Entreprises est active**
1. Connectez-vous [Microsoft Store pour Entreprises](https://businessstore.microsoft.com) avec votre compte Microsoft Store pour Entreprises administrateur.
2. Sélectionnez **Gérer**.
3. Sélectionnez **Paramètres** puis **distribuer.**
4. Sous **Outils de** gestion, vérifiez qu’Intune est répertorié et que l’état est **Actif.**  

<span id="2" />

## <a name="step-2-create-azure-ad-groups"></a>Étape 2 : Créer des groupes Azure AD

Créez trois groupes Azure AD pour chaque application. Ce tableau présente les groupes dont vous aurez besoin (disponible, obligatoire et désinstallé). 

Type d’affectation d’application |    Utilisation de groupe    | Exemple de nom Azure AD
--- | --- | ---
Available |  L’application sera disponible à partir Portail d’entreprise’application ou du site web. | MMD – *nom de l’application* – Disponible
Obligatoire |  L’application est installée sur les appareils des groupes sélectionnés. | MMD – *nom de l’application* – Obligatoire
Désinstaller |  L’application est désinstallée des appareils des groupes sélectionnés. | MMD – *nom de l’application* – Désinstaller

Ajoutez vos utilisateurs à ces groupes pour rendre l’application disponible, installer l’application ou supprimer l’application de Bureau géré Microsoft appareil. 

<span id="3" />

## <a name="step-3-assign-apps-to-your-users"></a>Étape 3 : Attribuer des applications à vos utilisateurs

**Pour affecter l’application à vos utilisateurs**

1. Connectez-vous [Bureau géré Microsoft portail d’administration.](https://aka.ms/mmdportal)
2. Dans le volet Bureau géré, sélectionnez **Applications.**
3. Dans la charge de travail applications, sélectionnez l’application à qui vous souhaitez affecter des utilisateurs et **sélectionnez Affecter des groupes d’utilisateurs.**
4. Pour l’application spécifique, sélectionnez un type d’affectation (Disponible, Obligatoire, Désinstaller) et affectez le groupe approprié.
5. Dans le volet Attribuer des applications, sélectionnez **OK.**


## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Étapes de mise en Bureau géré Microsoft

1. [Ajouter et vérifier des contacts d’administrateur dans le portail d’administration](add-admin-contacts.md)
2. [Ajuster l’accès conditionnel](conditional-access.md)
3. [Affecter des licences](assign-licenses.md)
4. [Déployer le portail d’entreprise Intune](company-portal.md)
5. [Activer Enterprise State Roaming](enterprise-state-roaming.md)
6. [Configurer les appareils](set-up-devices.md)
7. [Préparer vos utilisateurs à l’utilisation les appareils](get-started-devices.md)
8. Déployer des applications (cette rubrique)


<!--# Preparing apps for Microsoft Managed Desktop

This topic is the target for 2 "Learn more" links in the Admin Portal (aka.ms/app-overview;app-package); also target for link from Online resources (aka.ms/app-overviewmmd-app-prep) do not delete.

-->