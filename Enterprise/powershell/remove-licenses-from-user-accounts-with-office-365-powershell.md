---
title: Rimuovere le licenze dagli account utente con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
- DecEntMigration
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Viene illustrato come per rimuovere licenze di Office 365 che sono stati precedentemente assegnate agli utenti di Office 365 PowerShell.
ms.openlocfilehash: 90cae603a7a7cda0b7318571d3eb045f750fd58d
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="b27b6-103">Rimuovere le licenze dagli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b27b6-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="b27b6-104">**Riepilogo:** Viene illustrato come per rimuovere licenze di Office 365 che sono stati precedentemente assegnate agli utenti di Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b27b6-104">**Summary:** Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="b27b6-105">Informazioni preliminari</span><span class="sxs-lookup"><span data-stu-id="b27b6-105">Before you begin</span></span>

- <span data-ttu-id="b27b6-p101">Le procedure descritte in questo argomento richiedono all'utente di connettersi a PowerShell di Office 365. Per istruzioni, vedere [Connettersi a PowerShell di Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="b27b6-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="b27b6-108">Per visualizzare le informazioni sulla licenza piano ( **AccountSkuID** ) nella propria organizzazione, vedere gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="b27b6-108">To view the licensing plan ( **AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="b27b6-109">Visualizzare le licenze e i servizi con PowerShell di Office 365</span><span class="sxs-lookup"><span data-stu-id="b27b6-109">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="b27b6-110">Visualizzare la licenza dell'account e i dettagli di servizio con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b27b6-110">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
- <span data-ttu-id="b27b6-111">Se si utilizza il cmdlet **Get-MsolUser** senza utilizzare il _-tutti_ parametro, vengono restituiti solo i primi 500 account.</span><span class="sxs-lookup"><span data-stu-id="b27b6-111">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="b27b6-112">Versione breve (istruzioni senza spiegazioni)</span><span class="sxs-lookup"><span data-stu-id="b27b6-112">The short version (instructions without explanations)</span></span>
<span data-ttu-id="b27b6-113"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="b27b6-113"></span></span>

<span data-ttu-id="b27b6-p102">In questa sezione vengono illustrate le procedure in modo chiaro e senza informazioni superflue. Se si hanno altre domande o si desiderano ulteriori informazioni, è possibile leggere il resto dell'argomento.</span><span class="sxs-lookup"><span data-stu-id="b27b6-p102">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="b27b6-116">Per rimuovere le licenze da un account utente esistente, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="b27b6-116">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

<span data-ttu-id="b27b6-117">In questo esempio viene rimossa la `litwareinc:ENTERPRISEPACK` licenza (Office 365 Enterprise E3) dall'account utente BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="b27b6-117">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="b27b6-118">Per rimuovere le licenze da un gruppo di utenti con licenza esistenti, utilizzare uno dei metodi seguenti:</span><span class="sxs-lookup"><span data-stu-id="b27b6-118">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="b27b6-119">**Filtrare gli account in base a un attributo account esistente** A tale scopo, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="b27b6-119">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="b27b6-120">In questo esempio viene rimossa la `litwareinc:ENTERPRISEPACK` le licenze (Office 365 Enterprise E3) da tutti gli account per gli utenti del reparto vendite negli Stati Uniti.</span><span class="sxs-lookup"><span data-stu-id="b27b6-120">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="b27b6-121">**Utilizzare un elenco di account specifici** A tale scopo, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="b27b6-121">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="b27b6-122">Creare e salvare un file di testo contenente un account su ogni riga come riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="b27b6-122">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="b27b6-123">Utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="b27b6-123">Use the following syntax:</span></span>
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

<span data-ttu-id="b27b6-124">In questo esempio viene rimossa la `litwareinc:ENTERPRISEPACK` licenza (Office 365 Enterprise E3) gli account utente definito nel file C:\My Documents\Accounts.txt del testo.</span><span class="sxs-lookup"><span data-stu-id="b27b6-124">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

<span data-ttu-id="b27b6-125">Per rimuovere le licenze da tutti gli account utente esistenti, utilizzare la sintassi seguente:</span><span class="sxs-lookup"><span data-stu-id="b27b6-125">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="b27b6-126">In questo esempio viene rimossa la `litwareinc:ENTERPRISEPACK` licenza (Office 365 Enterprise E3) da tutti i membri esistenti con contratto multilicenza gli account utente.</span><span class="sxs-lookup"><span data-stu-id="b27b6-126">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="b27b6-127">Versione estesa (istruzioni con spiegazioni dettagliate)</span><span class="sxs-lookup"><span data-stu-id="b27b6-127">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="b27b6-128"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="b27b6-128"></span></span>

<span data-ttu-id="b27b6-p103">Nothing dura per sempre e che include le licenze di Office 365: prima o poi, vi entreranno volta quando è necessario rimuovere una licenza da un account utente. Forse l'utente sta succedendo lasciare; Forse l'utente non è più necessario licenza; forse -, esistono ovviamente svariati motivi per cui è possibile rimuovere una licenza utente.</span><span class="sxs-lookup"><span data-stu-id="b27b6-p103">Nothing lasts forever, and that includes Office 365 licenses: sooner or later, there will come a time when you need to remove a license from a user account. Maybe the user is going on leave; maybe the user no longer needs the license; maybe - well, there are obviously any number of reasons why you might want to remove a user license.</span></span>
  
<span data-ttu-id="b27b6-p104">Prima di continuare qualsiasi è importante tenere presente che è possibile, nonché la rimozione di una licenza richiede, rimuovere la licenza: disabilitazione di tutti i servizi relativi a una licenza non equivale alla rimozione di una licenza. Ad esempio, si supponga che è stata utilizzata backup di tutti i nostri licenze di Office 365; in altre parole, non si hanno alcuna licenza disponibile alcun tipo. Si decide di eseguire la procedura descritta in [disabilitare l'accesso ai servizi di Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) per disabilitare tutti i servizi, ad esempio, in account di Belinda Newman. Dopo che è stata eseguita che, come numero complessivo di licenze si avranno a nostra disposizione? Che è opportuno: zero. Sì, la procedura descritta in questo argomento verrà di *disabilitare* tutti i servizi in licenza di Belinda, ma non disabiliterà (vale a dire, eliminare) la licenza stesso. La licenza continueranno a essere valida e verrà assegnata a Belinda Newman. Sarà semplicemente non sarà in grado di utilizzare la licenza per accedere a tutti i servizi Office 365.</span><span class="sxs-lookup"><span data-stu-id="b27b6-p104">Before we go any further it's important to note that removing a license requires you to, well, remove the license: disabling all the services on a license is not the same thing as removing a license. For example, suppose we've used up all our Office 365 licenses; in other words, we have no licenses available whatsoever. You decide to follow the procedure in [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) to disable all the services, say, on Belinda Newman's account. After we do that, how many licenses will we have available to us? That's right: zero. Yes, the procedure from that topic will *disable*  all the services on Belinda's license, but it will not disable (i.e., delete) the license itself. The license will still be valid, and it will still be assigned to Belinda Newman. She just won't be able to use that license to access any Office 365 services.</span></span>
  
<span data-ttu-id="b27b6-p105">E che è importante: se si desidera rimuovere una licenza da un utente è necessario eseguire effettivamente *rimuovere* la licenza. Disattivazione di tutti i servizi impedisce all'utente di accedere a Office 365, ma non liberare il proprio licenza. Se si desidera riprendere il una licenza attualmente assegnato a un utente che è necessario eseguire un comando simile a questo, un comando che utilizza il parametro _RemoveLicenses_ realmente rimuovere la licenza precedentemente assegnata a Belinda:</span><span class="sxs-lookup"><span data-stu-id="b27b6-p105">And that's important: if you want to remove a license from a user you must actually  *remove*  the license. Disabling all the services will prevent the user from logging on to Office 365, but it won't free up his or her license. If you want to take back a license that's currently assigned to a user you need to run a command similar to this one, a command that uses the _RemoveLicenses_ parameter to actually remove the license previously assigned to Belinda:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="b27b6-142">Eseguire il comando e Belinda Newman non è più possibile licenza per l'utilizzo di Office 365.</span><span class="sxs-lookup"><span data-stu-id="b27b6-142">Run that command, and Belinda Newman will no longer be licensed to use Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b27b6-p106">Come si può notare, quando si utilizza il parametro _RemoveLicenses_ che è necessario specificare il nome della licenza da rimuovere. Se non si è certi che piano di licenze è stato utilizzato per assegnare una licenza per l'utente è sufficiente eseguita un comando simile al seguente:`Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`</span><span class="sxs-lookup"><span data-stu-id="b27b6-p106">As you can see, when you use the  _RemoveLicenses_ parameter you need to specify the name of the license to be removed. If you aren't sure which licensing plan was used to assign a license to the user just run a command like this:  `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`</span></span>
  
<span data-ttu-id="b27b6-145">Per verificare che la licenza è stata rimossa con successo, usa Get-MsolUser per controllare l'account utente in questione:</span><span class="sxs-lookup"><span data-stu-id="b27b6-145">To verify that the license really was removed, use the Get-MsolUser to check the user account in question:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

<span data-ttu-id="b27b6-146">Se l'operazione è riuscita in base alla pianificazione, la proprietà **isLicensed** di Belinda ora essere impostata `False`:</span><span class="sxs-lookup"><span data-stu-id="b27b6-146">If everything went according to plan, Belinda's **isLicensed** property will now be set to `False`:</span></span>
  
```
UserPrincipalName            DisplayName         isLicensed
-----------------            -----------         ----------
BelindaN@litwareinc.com      Newman, Belinda     False
```

<span data-ttu-id="b27b6-p107">Un altro modo per liberare una licenza è eliminando l'account utente. Per ulteriori informazioni, vedere [eliminare e ripristinare gli account utente con Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="b27b6-p107">Another way to free up a license is by deleting the user account. For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b27b6-149">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b27b6-149">See also</span></span>

<span data-ttu-id="b27b6-150">Vedere i seguenti argomenti aggiuntivi sulla gestione degli utenti con Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b27b6-150">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="b27b6-151">Creare account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b27b6-151">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="b27b6-152">Eliminare e ripristinare account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b27b6-152">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="b27b6-153">Bloccare gli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b27b6-153">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="b27b6-154">Assegnare le licenze agli account utente con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b27b6-154">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="b27b6-155">Per ulteriori informazioni sui cmdlet utilizzati in questa procedura, vedere i seguenti argomenti:</span><span class="sxs-lookup"><span data-stu-id="b27b6-155">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="b27b6-156">Get-Content</span><span class="sxs-lookup"><span data-stu-id="b27b6-156">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="b27b6-157">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="b27b6-157">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="b27b6-158">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="b27b6-158">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="b27b6-159">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="b27b6-159">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="b27b6-160">Where-Object</span><span class="sxs-lookup"><span data-stu-id="b27b6-160">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a><span data-ttu-id="b27b6-161">Nuovo utente di Office 365?</span><span class="sxs-lookup"><span data-stu-id="b27b6-161">New to Office 365?</span></span>

||
|:-----|
|<span data-ttu-id="b27b6-p108">![L'icona breve di apprendimento LinkedIn](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New a Office 365?**         Scopri corsi video gratuiti per [i professionisti IT e gli amministratori di Office 365](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), per offerto da Learning LinkedIn.</span><span class="sxs-lookup"><span data-stu-id="b27b6-p108">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), brought to you by LinkedIn Learning.</span></span> |
   

