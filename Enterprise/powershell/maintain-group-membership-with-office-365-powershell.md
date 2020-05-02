---
title: Gestire l'appartenenza ai gruppi con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/06/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Informazioni su come utilizzare Office 365 PowerShell per mantenere l'appartenenza a gruppi per Office 365.
ms.openlocfilehash: 0e6c5f2e27f9d146bb2a053bd3bdb6694fb07276
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004629"
---
# <a name="maintain-group-membership-with-office-365-powershell"></a><span data-ttu-id="a1257-103">Gestire l'appartenenza ai gruppi con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a1257-103">Maintain group membership with Office 365 PowerShell</span></span>

<span data-ttu-id="a1257-104">È possibile utilizzare Office 365 PowerShell come alternativa all'interfaccia di amministrazione di Microsoft 365 per mantenere l'appartenenza al gruppo in Office 365.</span><span class="sxs-lookup"><span data-stu-id="a1257-104">You can use Office 365 PowerShell as an alternative to the Microsoft 365 admin center to maintain group membership in Office 365.</span></span> 

> [!TIP]
> <span data-ttu-id="a1257-105">Per generare i comandi di PowerShell pronti per l'esecuzione specificando account utente e nomi di gruppo, utilizzare questa [cartella di lavoro di Microsoft Excel](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx)per la manutenzione del gruppo.</span><span class="sxs-lookup"><span data-stu-id="a1257-105">To generate ready-to-run PowerShell commands by specifying user account and group names, use this [group maintenance Microsoft Excel workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx).</span></span> 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="a1257-106">Usare il modulo di Azure Active Directory PowerShell per Graph</span><span class="sxs-lookup"><span data-stu-id="a1257-106">Use the Azure Active Directory PowerShell for Graph module</span></span>
<span data-ttu-id="a1257-107">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="a1257-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="a1257-108">Aggiungere o rimuovere account utente come membri di un gruppo</span><span class="sxs-lookup"><span data-stu-id="a1257-108">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="a1257-109">**Per aggiungere un account utente dal relativo UPN**, inserire il nome dell'entità utente (UPN) dell'account utente (ad esempio: Belindan@contoso.com) e il nome visualizzato del gruppo, rimuovendo i caratteri "<" e ">" ed eseguire questi comandi nella finestra di PowerShell o nell'ambiente di script integrato di PowerShell (ISE).</span><span class="sxs-lookup"><span data-stu-id="a1257-109">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell Integrated Script Environment (ISE).</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="a1257-110">**Per aggiungere un account utente in base al nome visualizzato**, inserire il nome visualizzato dell'account utente (ad esempio: Belinda Newman) e il nome visualizzato del gruppo ed eseguire questi comandi nella finestra di PowerShell o in PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a1257-110">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="a1257-111">**Per rimuovere un account utente dal relativo UPN**, inserire l'UPN dell'account utente (ad esempio: Belindan@contoso.com) e il nome visualizzato del gruppo ed eseguire questi comandi nella finestra di PowerShell o in PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a1257-111">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="a1257-112">**Per rimuovere un account utente in base al relativo nome visualizzato**, inserire il nome visualizzato dell'account utente (ad esempio: Belinda Newman) e il nome visualizzato del gruppo ed eseguire questi comandi nella finestra di PowerShell o in PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a1257-112">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="a1257-113">Aggiungere o rimuovere gruppi come membri di un gruppo</span><span class="sxs-lookup"><span data-stu-id="a1257-113">Add or remove groups as members of a group</span></span>

<span data-ttu-id="a1257-114">I gruppi di sicurezza possono contenere altri gruppi come membri.</span><span class="sxs-lookup"><span data-stu-id="a1257-114">Security groups can contain other groups as members.</span></span> <span data-ttu-id="a1257-115">I gruppi di Office 365, tuttavia, non possono.</span><span class="sxs-lookup"><span data-stu-id="a1257-115">Office 365 groups, however, cannot.</span></span> <span data-ttu-id="a1257-116">In questa sezione sono inclusi i comandi di PowerShell per aggiungere o rimuovere gruppi solo per un gruppo di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="a1257-116">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="a1257-117">**Per aggiungere un gruppo in base al nome visualizzato**, inserire il nome visualizzato del gruppo che si desidera aggiungere e il nome visualizzato del gruppo che conterrà il gruppo di membri ed eseguire questi comandi nella finestra di PowerShell o in PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a1257-117">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="a1257-118">**Per rimuovere un gruppo in base al nome visualizzato**, inserire il nome visualizzato del gruppo che si desidera rimuovere e il nome visualizzato del gruppo che conterrà il gruppo di membri ed eseguire questi comandi nella finestra di PowerShell o in PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a1257-118">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="a1257-119">Usare il modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a1257-119">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="a1257-120">Prima di tutto, [connettersi al tenant di Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="a1257-120">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="a1257-121">Aggiungere o rimuovere account utente come membri di un gruppo</span><span class="sxs-lookup"><span data-stu-id="a1257-121">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="a1257-122">**Per aggiungere un account utente dal relativo UPN**, inserire il nome dell'entità utente (UPN) dell'account utente (ad esempio: Belindan@contoso.com) e il nome visualizzato del gruppo, rimuovendo i caratteri "<" e ">" ed eseguire questi comandi nella finestra di PowerShell o in PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a1257-122">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="a1257-123">**Per aggiungere un account utente in base al nome visualizzato**, inserire il nome visualizzato dell'account utente (ad esempio: Belinda Newman) e il nome visualizzato del gruppo ed eseguire questi comandi nella finestra di PowerShell o in PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a1257-123">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="a1257-124">**Per rimuovere un account utente dal relativo UPN**, inserire l'UPN dell'account utente (ad esempio: Belindan@contoso.com) e il nome visualizzato del gruppo ed eseguire questi comandi nella finestra di PowerShell o in PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a1257-124">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="a1257-125">**Per rimuovere un account utente in base al relativo nome visualizzato**, inserire il nome visualizzato dell'account utente (ad esempio: Belinda Newman) e il nome visualizzato del gruppo ed eseguire questi comandi nella finestra di PowerShell o in PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a1257-125">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="a1257-126">Aggiungere o rimuovere gruppi come membri di un gruppo</span><span class="sxs-lookup"><span data-stu-id="a1257-126">Add or remove groups as members of a group</span></span>

<span data-ttu-id="a1257-127">I gruppi di sicurezza possono contenere altri gruppi come membri.</span><span class="sxs-lookup"><span data-stu-id="a1257-127">Security groups can contain other groups as members.</span></span> <span data-ttu-id="a1257-128">I gruppi di Office 365, tuttavia, non possono.</span><span class="sxs-lookup"><span data-stu-id="a1257-128">Office 365 groups, however, cannot.</span></span> <span data-ttu-id="a1257-129">In questa sezione sono inclusi i comandi di PowerShell per aggiungere o rimuovere gruppi solo per un gruppo di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="a1257-129">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="a1257-130">**Per aggiungere un gruppo in base al nome visualizzato**, inserire il nome visualizzato del gruppo che si desidera aggiungere e il nome visualizzato del gruppo che conterrà il gruppo di membri ed eseguire questi comandi nella finestra di PowerShell o in PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a1257-130">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

<span data-ttu-id="a1257-131">**Per rimuovere un gruppo in base al nome visualizzato**, inserire il nome visualizzato del gruppo che si desidera rimuovere e il nome visualizzato del gruppo che conterrà il gruppo di membri ed eseguire questi comandi nella finestra di PowerShell o in PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a1257-131">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a><span data-ttu-id="a1257-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a1257-132">See also</span></span>

[<span data-ttu-id="a1257-133">Gestire gli account utente, le licenze e i gruppi con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a1257-133">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="a1257-134">Gestire Office 365 con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="a1257-134">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="a1257-135">Guida introduttiva a PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="a1257-135">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

