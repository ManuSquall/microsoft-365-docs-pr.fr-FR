---
title: Configurer Microsoft 365 Business
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
f1_keywords:
- O365E_M365SetupBanner
- BCS365_M365SetupBanner
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- M365-subscription-management
ms.custom: OKR_SMB_M365
search.appverid:
- BCS160
- MET150
ms.assetid: 6e7a2dfd-8ec4-4eb7-8390-3ee103e5fece
description: Découvrez comment configurer Microsoft 365 Business.
ms.openlocfilehash: 4f31af3fa63416d3b1bd7281f7712313252ad437
ms.sourcegitcommit: cbf117a4cd92a907115c9f10752f3c557361e586
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2019
ms.locfileid: "37440591"
---
# <a name="set-up-microsoft-365-business-in-the-setup-wizard"></a>Configurer Microsoft 365 entreprise dans l’Assistant Installation

## <a name="add-your-domain-users-and-set-up-policies"></a>Ajouter votre domaine, vos utilisateurs et configurer des stratégies

[![Étiquette pour vous informer le centre d’administration change et vous trouverez plus de détails sur aka.ms/aboutM365preview.](media/m365admincenterchanging.png)](https://docs.microsoft.com/office365/admin/microsoft-365-admin-center-preview)

Lorsque vous achetez Microsoft 365 Business, vous avez la possibilité d’utiliser un domaine que vous possédez ou d’en acheter un lors de l' [inscription](sign-up.md).

- Si vous avez acheté un nouveau domaine lorsque vous vous êtes inscrit, votre domaine est configuré et vous pouvez le déplacer pour [Ajouter des utilisateurs et attribuer des licences](#add-users-and-assign-licenses).

### <a name="add-your-domain-to-personalize-sign-in"></a>Ajouter votre domaine pour personnaliser la connexion

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) à l’aide de vos informations d’identification d’administrateur général. 

2. Sélectionnez **Ajouter un domaine** ou **Ajouter des utilisateurs** pour démarrer l’Assistant.
    > [!IMPORTANT]
    > Si vous avez acheté un domaine lors de l’inscription, vous ne verrez pas **Ajouter une étape de domaine** ici. Accédez à [Ajouter des utilisateurs](#add-users-and-assign-licenses) à la place.

    ![Sélectionnez atteindre le programme d’installation.](media/gotosetupinadmincenter.png)
    
3. Dans l’Assistant, entrez le nom de domaine que vous souhaitez utiliser (par exemple, contoso.com).


    ![Capture d’écran de la page Personnalisez votre connexion.](media/personalizesignin.png)

    
4. Suivez les étapes de l’Assistant pour [créer des enregistrements DNS auprès d’un fournisseur d’hébergement DNS pour Office 365](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) qui vérifie que vous êtes propriétaire du domaine. Si vous êtes conscient de votre hôte de domaine, reportez-vous aux [instructions spécifiques](https://docs.microsoft.com/office365/admin/get-help-with-domains/set-up-your-domain-host-specific-instructions)de l’hôte.

    Si votre fournisseur d’hébergement est GoDaddy ou si un autre hôte est activé avec la [connexion au domaine](https://docs.microsoft.com/office365/admin/get-help-with-domains/domain-connect), le processus est facile et vous êtes automatiquement invité à vous connecter et à laisser Microsoft s’authentifier à votre place :

    ![Sur GoDaddy, sélectionnez Autoriser.](media/godaddyauth.png)

### <a name="add-users-and-assign-licenses"></a>Ajouter des utilisateurs et attribuer des licences

Vous pouvez ajouter des utilisateurs dans l’Assistant, mais vous pouvez également [Ajouter des utilisateurs ultérieurement](add-users-m365b.md) dans le centre d’administration. En outre, si vous disposez d’un contrôleur de domaine local, vous pouvez ajouter des utilisateurs avec [Azure ad Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-express).

#### <a name="add-users-in-the-wizard"></a>Ajouter des utilisateurs dans l’Assistant

Tous les utilisateurs que vous ajoutez dans l’Assistant reçoivent automatiquement une licence d’entreprise Microsoft 365.

![Capture d’écran de la page Ajouter de nouveaux utilisateurs dans l’Assistant](media/addnewuserspage.png)

1. Si votre abonnement professionnel Microsoft 365 comporte des utilisateurs existants (par exemple, si vous avez utilisé Azure AD Connect), vous avez la possibilité de leur attribuer des licences. Poursuivez et ajoutez des licences pour eux aussi.

2. Une fois que vous avez ajouté les utilisateurs, vous pouvez également partager les informations d’identification avec les nouveaux utilisateurs que vous avez ajoutés. Vous pouvez choisir de les imprimer, de les envoyer par e-mail ou de les télécharger.

3. Sur la création de teams pour votre organisation, vous pouvez choisir d’ajouter des équipes et d’y ajouter des utilisateurs. Vous pouvez également effectuer cette opération plus tard. Pour plus d’informations, consultez [la rubrique créer une équipe à l’échelle de l’entreprise](https://support.office.com/article/037bb27a-bcc9-48fe-8d72-44d9482420a3).

4. Ignorez la migration des messages e-mail et sélectionnez **Suivant** dans la page **Migrer les messages e-mail**. 

    Si vous effectuez une migration à partir d’un autre fournisseur de courrier et que vous souhaitez copier vos données ultérieurement, vous pouvez [migrer le courrier électronique et les contacts vers Office 365](https://support.office.com/article/a3e3bddb-582e-4133-8670-e61b9f58627e).


### <a name="connect-your-domain"></a>Sélectionner votre domaine

> [!NOTE]
> Si vous avez choisi d’utiliser le domaine. onmicrosoft ou si vous avez utilisé Azure AD Connect pour configurer des utilisateurs, vous ne verrez pas cette étape.
  
Pour configurer des services, vous devez mettre à jour des enregistrements au niveau de votre hôte DNS ou de votre bureau d'enregistrement de domaines.
  
1. L'Assistant Configuration détecte généralement votre bureau d'enregistrement et vous fournit un lien vers des instructions détaillées vous permettant de mettre à jour vos enregistrements NS sur le site web du bureau d'enregistrement. Si ce n’est pas le cas, [Modifiez les serveurs de noms pour configurer Office 365 avec n’importe quel](https://support.office.com/article/a8b487a9-2a45-4581-9dc4-5d28a47010a2)Bureau d’enregistrement de domaine. 

    - Si vous avez des enregistrements DNS existants, par exemple un site Web existant, mais que votre hôte DNS est activé pour la [connexion au domaine](https://docs.microsoft.com/office365/admin/get-help-with-domains/domain-connect), choisissez **Ajouter des enregistrements pour moi**. Sur la page **choisir vos services en ligne** , acceptez toutes les valeurs par défaut, cliquez sur **suivant**, puis choisissez **autoriser** sur la page de votre hôte DNS.
    - Si vous avez des enregistrements DNS existants avec d’autres hôtes DNS (non activé pour la connexion au domaine), vous devez gérer vos propres enregistrements DNS pour vous assurer que les services existants restent connectés. Pour plus d’informations, voir [notions de base](https://docs.microsoft.com/office365/admin/get-help-with-domains/dns-basics) sur le domaine.

        ![Connecter votre page de domaine avec je vais gérer mes propres enregistrements DNS.](media/connectyourdomainpage.png)

2. Suivez les étapes de l’Assistant et de la messagerie et d’autres services sont configurés pour vous.

### <a name="protect-data-and-devices"></a>Protéger les données et les appareils 

Les stratégies que vous configurez dans l’Assistant sont appliquées automatiquement à un [groupe de sécurité](https://docs.microsoft.com/office365/admin/create-groups/compare-groups#security-groups) appelé *tous les utilisateurs*. Vous pouvez également créer des groupes supplémentaires auxquels affecter des stratégies dans le centre d’administration.

1. Dans la case à cocher **protéger vos fichiers professionnels sur les appareils mobiles** , l’option **protéger les fichiers de travail lorsque les appareils sont perdus ou volés** est sélectionnée par défaut. Vous avez la possibilité d’activer **la gestion de la manière dont les utilisateurs accèdent aux fichiers Office sur les appareils mobiles**, ce qui est recommandé.

    ![Capture d’écran de la page protéger les fichiers de travail sur les appareils mobiles.](media/protectworkfilesondevices.png)

     - Développez **protéger les fichiers de travail en cas de perte ou de vol des appareils** pour afficher les [valeurs par défaut](protect-work-files-on-lost-or-stolen-device.md):

        ![Capture d’écran des valeurs par défaut pour la protection des fichiers sur les appareils perdus.](media/protectworkfilesondevicesdefault.png)

    - Sélectionnez **gérer la manière dont les utilisateurs accèdent aux fichiers Office sur les appareils mobiles** et développez-le pour afficher les [valeurs par défaut](manage-user-access-on-mobile-devices.md). Nous vous recommandons d’accepter les valeurs par défaut lors de l’installation pour créer des stratégies d’application pour Android, iOS et Windows 10 qui s’appliquent à tous les utilisateurs. Vous pouvez créer des stratégies supplémentaires une fois l'installation terminée.

        ![Capture d’écran des paramètres de protection pour les fichiers Office sur mobile.](media/useraccessonmobile.png)

2. La dernière étape sur la protection des données et des périphériques vous permet de configurer des stratégies pour sécuriser les appareils Windows 10. Ces paramètres sont appliqués automatiquement lorsque le Windows 10 d’un utilisateur se connecte à votre organisation. Vous pouvez développer des **appareils Windows 10 sécurisés** pour afficher et modifier les [valeurs par défaut](secure-windows-10-devices.md).
3. Vous pouvez également choisir d' [installer automatiquement Office](install-office-on-windows-10-during-setup.md) sur les appareils Windows 10.

    ![Capture d’écran de la page définir la configuration de l’appareil Windows 10.](media/setwin10config.png)


## <a name="deploy-office-365-client-apps"></a>Déployer des applications clientes Office 365

Si vous avez choisi d’installer automatiquement les applications Office dans lors de la configuration, les applications s’installeront sur les appareils Windows 10 une fois que les utilisateurs se sont connectés à Azure AD à partir de leurs appareils Windows avec leurs informations d’identification professionnelles.
Pour installer Office sur des appareils mobiles iOS ou Android, consultez la rubrique [configurer des appareils mobiles pour les utilisateurs professionnels de Microsoft 365](set-up-mobile-devices.md).

Vous pouvez également installer Office individuellement. Pour obtenir des instructions, voir [installer Office sur un PC ou un Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658) .
