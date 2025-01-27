---
title: Configuration de base légère
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/14/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
- seo-marvel-apr2020
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: Utilisez ce guide de laboratoire de test pour créer un environnement de test léger pour les tests Microsoft 365 entreprise.
ms.openlocfilehash: 2de0760cef7339f62229575b1e0a54b3c67a4e9f
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50909705"
---
# <a name="the-lightweight-base-configuration"></a>Configuration de base légère

*Ce guide de laboratoire de test peut être utilisé à la fois pour Microsoft 365'entreprise et Office 365 Entreprise environnements de test.*

Cet article explique comment créer un environnement simplifié avec un abonnement Microsoft 365 E5 et un ordinateur exécutant Windows 10 Entreprise.

![Environnement de test Microsoft 365 Entreprise léger](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase4.png)

La création d’un environnement de test léger implique cinq phases :
- [Phase 1 : Créer votre abonnement Microsoft 365 E5 abonnement](#phase-1-create-your-microsoft-365-e5-subscription)
- [Phase 2 : configuration de votre abonnement d’évaluation Office 365](#phase-2-configure-your-office-365-trial-subscription)
- [Phase 3 : Ajoutez un abonnement d’évaluation Microsoft 365 E5.](#phase-3-add-a-microsoft-365-e5-trial-subscription)
- [Phase 4 : Création d’un ordinateur Windows 10 Entreprise](#phase-4-create-a-windows-10-enterprise-computer)
- [Phase 5 : Association de votre ordinateur Windows 10 à Azure AD](#phase-5-join-your-windows-10-computer-to-azure-ad)

Utilisez l’environnement résultant pour tester les fonctionnalités de Microsoft 365 [entreprise.](https://www.microsoft.com/microsoft-365/enterprise)

![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)
  
> [!TIP]
> Pour obtenir une carte visuelle de tous les articles de la pile Microsoft 365 guide de laboratoire de test pour entreprise, voir Microsoft 365 [for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).

>[!NOTE]
>Nous vous recommandons d’imprimer cet article afin de consigner les informations dont vous aurez besoin dans cet environnement au cours des 30 jours de votre abonnement à la version d’évaluation Office 365. Vous pouvez facilement étendre l’abonnement d’évaluation pour une période supplémentaire de 30 jours. Pour un environnement de développement/test permanent, créez un nouvel abonnement payant avec un client Azure AD séparé et un nombre réduit de licences.

## <a name="phase-1-create-your-microsoft-365-e5-subscription"></a>Phase 1 : Créer votre abonnement Microsoft 365 E5 abonnement

Nous commençons par un abonnement Microsoft 365 E5 d’essai, puis nous y ajoutons Microsoft 365 E5'abonnement.

>[!NOTE]
>Nous vous recommandons de créer un abonnement d’essai de Office 365 afin que votre environnement de test dispose d’un client Azure AD distinct de tous les abonnements payants dont vous disposez actuellement. Cette séparation signifie que vous pouvez ajouter et supprimer des utilisateurs et des groupes dans le client test sans affecter vos abonnements de production.

Pour démarrer votre abonnement d’évaluation Microsoft 365 E5, vous avez besoin d’un nom d’entreprise fictif et d’un nouveau compte Microsoft.
  
1. Nous vous recommandons d’utiliser une variante du nom d’entreprise Contoso pour le nom de votre entreprise. Il s’agit d’une entreprise fictive utilisée dans le contenu d’exemple de Microsoft. Toutefois, cette étape n’est pas obligatoire. Indiquer le nom fictif de votre entreprise ici : ![Trait](../media/Common-Images/TableLine.png)
    
2. Pour ouvrir un nouveau compte Microsoft, accédez à [https://outlook.com](https://outlook.com) et créez un compte avec un nouveau compte de messagerie et une nouvelle adresse. Vous utiliserez ce compte pour vous inscrire à Office 365.
    
    - Enregistrez le prénom et le nom de famille utilisés pour votre nouveau compte ici : ![Trait](../media/Common-Images/TableLine.png)
    
    - Enregistrez l’adresse du nouveau compte de messagerie ici : ![Trait](../media/Common-Images/TableLine.png)@outlook.com
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>Inscription à un abonnement d’évaluation Office 365 E5

1. Dans votre navigateur, allez à [https://aka.ms/e5trial](https://aka.ms/e5trial) .
    
2. À l’étape 1 de la page Merci d’avoir choisi **Office 365 E5,** entrez votre nouvelle adresse de compte de messagerie.
3. À l’étape 2 du processus d’abonnement de piste, entrez les informations demandées, puis effectuez la vérification.
4. À l’étape 3, entrez un nom d’organisation, puis un nom de compte qui sera l’administrateur global de l’abonnement.
5. À l’étape 4, enregistrer l’URL de la page de connexion ici (sélectionnez-la et copiez-la) : ![Trait](../media/Common-Images/TableLine.png)
6. Enregistrez l’identifiant utilisateur ici : ![ligne](../media/Common-Images/TableLine.png).onmicrosoft.com  
   Enregistrez le mot de passe que vous avez entré dans un emplacement sécurisé.
   Cette valeur correspond au **nom de l’administrateur général**.
7. Sélectionnez **Aller au programme d’installation.**
8. In Office 365 E5 Setup, select **Continue using your *organization*.onmicrosoft.com for email and signing in,** and then select **Exit and continue later**.

Le Centre d’administration Microsoft 365 doit s’afficher.
    
## <a name="phase-2-configure-your-office-365-trial-subscription"></a>Phase 2 : configuration de votre abonnement d’évaluation Office 365

Durant cette phase, configurez votre abonnement en y ajoutant des utilisateurs supplémentaires et assignez-leur des licences Office 365 E5.
  
Pour vous connecter à votre abonnement avec le module Azure Active Directory PowerShell pour Graph à partir de votre ordinateur, utilisez les instructions de Connecter pour [Microsoft 365 avec PowerShell.](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)
    
Dans la **boîte Windows PowerShell demande d’informations** d’identification, entrez le nom de l’administrateur général *(par* exemple, jdoe@contosotoycompany.onmicrosoft.com ) et le mot de passe.
  
Remplissez le nom de votre organisation (par exemple, *contosotoycompany*), le code de pays à deux caractères de votre emplacement, un mot de passe de compte commun, puis exécutez les commandes suivantes à partir de l’invite PowerShell :

```powershell
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$commonPW="<common user account password>"
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPW

$userUPN= "user2@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 2" -GivenName User -SurName 2 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user2"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign

$userUPN= "user3@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 3" -GivenName User -SurName 3 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user3"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign

$userUPN= "user4@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 4" -GivenName User -SurName 4 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user4"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```
> [!NOTE]
> L’utilisation ici d’un mot de passe courant est destinée à l’automatisation et à la simplification de la configuration pour un environnement de test. Bien évidemment, cela est hautement déconseillé pour les abonnements de production. 

### <a name="record-key-information-for-future-reference"></a>Enregistrer les informations clés pour future référence

Si vous n’avez pas encore enregistré ces valeurs, enregistrez-les maintenant :
  
- Nom de l’administrateur général : ![Trait](../media/Common-Images/TableLine.png).onmicrosoft.com(à partir de l’étape 6 de la phase 1)
    
    Enregistrez également le mot de passe de ce compte dans un emplacement sécurisé.
    
- Nom de l’organisation bénéficiant de l’abonnement à la version d’évaluation : ![Trait](../media/Common-Images/TableLine.png) (à partir de l’étape 4 de la phase 1)
    
- Pour répertorier les comptes pour Utilisateur 2, Utilisateur 3, Utilisateur 4 et Utilisateur 5, exécutez la commande suivante à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :
    
  ```powershell
  Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    Enregistrez les noms de compte ici :
    
  - Nom du compte de l’utilisateur 2 : utilisateur2@![Trait](../media/Common-Images/TableLine.png).onmicrosoft.com
    
  - Nom du compte de l’utilisateur 3 : utilisateur3@![Trait](../media/Common-Images/TableLine.png).onmicrosoft.com
    
  - Nom du compte de l’utilisateur 4 : utilisateur4@![Trait](../media/Common-Images/TableLine.png).onmicrosoft.com
    
  - Nom du compte de l’utilisateur 5 : utilisateur5@![Trait](../media/Common-Images/TableLine.png).onmicrosoft.com
    
    Enregistrez également les mots de passe communs de ces comptes dans un emplacement sécurisé.
   
### <a name="using-an-office-365-test-environment"></a>Utilisation d’un environnement de test Office 365

Si vous n’avez besoin Office 365 environnement de test, vous n’avez pas besoin de lire le reste de cet article.

Pour obtenir des guides de laboratoire de test supplémentaires qui s’appliquent à Office 365 et Microsoft 365, voir Microsoft 365 guides de laboratoire de test pour [entreprise.](m365-enterprise-test-lab-guides.md)
  
## <a name="phase-3-add-a-microsoft-365-e5-trial-subscription"></a>Phase 3 : Ajoutez un abonnement d’évaluation Microsoft 365 E5.

Dans cette phase, vous vous inscrivez pour l’abonnement d’évaluation Microsoft 365 E5 et l’ajoutez à la même organisation que votre abonnement d’évaluation d’Office 365 E5.
  
Tout d’abord, ajoutez l’abonnement d’évaluation Microsoft 365 E5 et attribuez une licence Microsoft 365 à votre compte d’administrateur général.
  
1. Dans une fenêtre privée de navigateur Internet, utilisez vos informations d’identification de compte d’administrateur général pour vous Microsoft 365 centre d’administration à l’adresse [https://admin.microsoft.com](https://admin.microsoft.com) .
    
2. Dans la page **Microsoft 365 centre d’administration,** dans le navigation de gauche, sélectionnez **Facturation > acheter des services.**
    
3. Dans la page **Acheter des services,** **sélectionnez Microsoft 365 E5,** puis **sélectionnez Obtenir une version d’essai gratuite.**

4. Dans la page **Microsoft 365 E5** d’essai, décidez de recevoir un SMS ou un  appel téléphonique, entrez votre numéro de téléphone, puis sélectionnez M’envoyer un sms ou **m’appeler.** Effectuez la vérification.

5. Dans la page **Confirmer votre commande,** **sélectionnez Essayer maintenant.**

6. Dans la page **Reçu de** commande, sélectionnez **Continuer.**

7. Dans le centre Microsoft 365' administration, sélectionnez **Utilisateurs > utilisateurs actifs.**

8. Dans **les utilisateurs actifs,** sélectionnez votre compte d’administrateur.

9. Sélectionnez **licences et applications.**

10. Désactivez la licence pour Office 365 Entreprise E5 et activez la licence pour Microsoft 365 E5.

11. Sélectionnez **Enregistrer les modifications,** puis fermez le volet d’informations du compte d’utilisateur.

Ensuite, répétez les étapes 8 et 11 de la procédure précédente pour tous vos autres comptes (Utilisateur2, Utilisateur3, Utilisateur4 et Utilisateur5).
  
> [!NOTE]
> La durée de l’Microsoft 365 E5 d’essai est de 30 jours. Pour un environnement de test permanent, convertissez cet abonnement en abonnement payant avec un nombre réduit de licences.
  
Votre environnement de test comporte maintenant :
  
- Un abonnement d’évaluation de Microsoft 365 E5.
- Tous vos comptes d’utilisateur appropriés (l’administrateur général ou tous les cinq comptes d’utilisateur) sont activés pour utiliser Microsoft 365 E5.
    
Votre configuration résultante, qui ajoute des Microsoft 365 E5, se ressemble à ceci :
  
![Phase 3 de l’environnement de test Microsoft 365 Entreprise](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase2.png)
  
## <a name="phase-4-create-a-windows-10-enterprise-computer"></a>Phase 4 : Création d’un ordinateur Windows 10 Entreprise

Au cours de cette phase, vous allez créer un ordinateur autonome exécutant Windows 10 Entreprise sous forme d’un ordinateur physique, d’une machine virtuelle ou d’une machine virtuelle Azure.
  
### <a name="physical-computer"></a>Ordinateur physique

Sur un ordinateur personnel, installez Windows 10 Entreprise. Vous pouvez télécharger la version Windows 10 Entreprise [d’essai ici.](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)
  
### <a name="virtual-machine"></a>Machine virtuelle

Utilisez l’hyperviseur de votre choix pour créer une machine virtuelle, puis installez-Windows 10 Entreprise dessus. Vous pouvez télécharger la version Windows 10 Entreprise [d’essai ici.](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)
  
### <a name="virtual-machine-in-azure"></a>Machine virtuelle dans Azure

Pour créer une machine virtuelle exécutant Windows 10 dans Microsoft Azure, ***vous devez disposer d’un abonnement Visual Studio*** qui vous permet d’accéder à l’image pour Windows 10 Entreprise. D’autres types d’abonnements Azure, tels que les abonnements d’évaluation et payants, ne permettent pas d’accéder à cette image. Pour obtenir les informations les plus récentes, reportez-vous à l’article [Utilisation d’un client Windows dans Azure pour les scénarios de développement et/ou test](/azure/virtual-machines/windows/client-images).
  
> [!NOTE]
> [!REMARQUE] Les ensembles de commandes suivants utilisent la dernière version d'Azure PowerShell. Reportez-vous à la rubrique relative à la [prise en main des cmdlets Azure PowerShell](/powershell/azureps-cmdlets-docs/). Ces ensembles de commandes créent une machine virtuelle Windows 10 Entreprise nommée WIN10 ainsi que l’intégralité de son infrastructure requise, y compris un groupe de ressources, un compte de stockage et un réseau virtuel. Si vous êtes déjà familiarisé avec les services d’infrastructure Azure, adaptez ces instructions en fonction de votre infrastructure actuellement déployée.
  
Tout d’abord, lancez une invite Microsoft PowerShell.
  
Connectez-vous à votre compte Azure avec cette commande.
  
```powershell
Connect-AzAccount
```

Obtenez le nom de votre abonnement à l’aide de cette commande.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

Définissez votre abonnement Azure. Remplacez tout le texte entre guillemets, y compris les \< and > caractères, par le nom correct.
  
```powershell
$subscr="<subscription name>"
Get-AzSubscription -SubscriptionName $subscr | Select-AzSubscription
```

Ensuite, créez un nouveau groupe de ressources. Pour déterminer un nom de groupe de ressources unique, utilisez cette commande pour répertorier vos groupes de ressources existants.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Créez votre nouveau groupe de ressources avec ces commandes. Remplacez tout le texte entre guillemets, y compris les \< and > caractères, par les noms corrects.
  
```powershell
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzResourceGroup -Name $rgName -Location $locName
```

Ensuite, créez un réseau virtuel et la machine virtuelle WIN10 avec ces commandes. Lorsque vous y êtes invité, indiquez le nom et le mot de passe du compte d’administrateur local pour WIN10, et enregistrez ces informations dans un emplacement sécurisé.
  
```powershell
$corpnetSubnet=New-AzVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzVirtualNetwork -Name "M365Ent-TestLab" -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name "M365Ent-TestLab"
$nsg=Get-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
$pip=New-AzPublicIpAddress -Name WIN10-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name WIN10-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName WIN10 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for WIN10."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName WIN10 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsDesktop -Offer Windows-10 -Skus RS3-Pro -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name WIN10-TestLab-OSDisk -DiskSizeInGB 128 -CreateOption FromImage
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

## <a name="phase-5-join-your-windows-10-computer-to-azure-ad"></a>Phase 5 : Association de votre ordinateur Windows 10 à Azure AD

Lorsque l’ordinateur physique ou la machine virtuelle avec Windows 10 Entreprise est créée, connectez-vous avec un compte d’administrateur local.
  
> [!NOTE]
> Pour une machine virtuelle dans Azure, utilisez  [ces instructions](/azure/virtual-machines/windows/connect-logon) pour vous y connecter.
  
Ensuite, associez l’ordinateur WIN10 au client Azure AD de votre abonnement Microsoft 365 E5.
  
1. Sur le bureau de l’ordinateur WIN10, sélectionnez Démarrer > Paramètres > Comptes > Accès au travail **ou à l'> Connecter .**
    
2. Dans la **boîte de dialogue Configurer un compte** scolaire ou scolaire, sélectionnez Joindre cet appareil à **Azure Active Directory**.
    
3. Dans **le compte scolaire ou de travail,** entrez le nom du compte d’administrateur général de votre abonnement Microsoft 365 E5, puis sélectionnez **Suivant.**
    
4. Dans **Entrer le mot de** passe, entrez le mot de passe de votre compte d’administrateur général, puis sélectionnez Se **connectez.**
    
5. Lorsque vous êtes invité à vous assurer qu’il s’agit de votre organisation, sélectionnez **Rejoindre,** puis **terminé**.
    
6. Fermez la fenêtre Paramètres.
    
Ensuite, installez Applications Microsoft 365 pour les grandes entreprises sur l’ordinateur WIN10 :
  
1. Ouvrez le Microsoft Edge et connectez-vous au Centre [d’administration Microsoft 365](https://admin.microsoft.com) avec vos informations d’identification de compte d’administrateur général.
    
2. Sous **l’Microsoft Office Accueil,** **sélectionnez Installer Office**.
    
3. Lorsque vous y avez été invité, sélectionnez **Exécuter,** puis Oui **pour** **le contrôle de compte d’utilisateur.**
    
4. Attendez qu’Office termine l’installation. Lorsque vous voyez **que tout est prêt !**, sélectionnez Fermer **deux** fois.
    
Votre environnement résultant se ressemble à ceci :

![Phase 5 de l’environnement de test Microsoft 365 Entreprise](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase4.png)

Cela inclut l’ordinateur WIN10 avec :

- rejoint le client Azure AD de votre abonnement Microsoft 365 E5 ;
- été inscrit en tant que périphérique Azure AD dans Microsoft Intune (EMS) ;
- Applications Microsoft 365 pour les grandes entreprises installé.
  
Vous êtes maintenant prêt à tester des fonctionnalités supplémentaires de [Microsoft 365 entreprise.](https://www.microsoft.com/microsoft-365/enterprise)
  
## <a name="next-steps"></a>Étapes suivantes

Découvrez les nouveaux ensembles de guides pour les tests de laboratoire :
  
- [Identité](m365-enterprise-test-lab-guides.md#identity)
- [Gestion des appareils mobiles](m365-enterprise-test-lab-guides.md#mobile-device-management)
- [Protection des informations](m365-enterprise-test-lab-guides.md#information-protection)
   

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 Entreprise](/microsoft-365-enterprise/)