---
title: Usare i cmdlet di PowerShell della distribuzione centralizzata per gestire i componenti aggiuntivi
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: Utilizzare i cmdlet di PowerShell per la distribuzione centralizzata per facilitare la distribuzione e la gestione dei componenti aggiuntivi di Office per l'organizzazione di Office 365.
ms.openlocfilehash: 34040d11a1ef4d5da2d7a0e980b28e7ef0eba7fb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070502"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="3aab6-103">Usare i cmdlet di PowerShell della distribuzione centralizzata per gestire i componenti aggiuntivi</span><span class="sxs-lookup"><span data-stu-id="3aab6-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="3aab6-104">Come amministratore di Office 365, è possibile distribuire i componenti aggiuntivi di Office agli utenti tramite la caratteristica di distribuzione centralizzata (vedere [Deploy Office Add-ins in the office 365 Admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)).</span><span class="sxs-lookup"><span data-stu-id="3aab6-104">As an Office 365 admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Deploy Office Add-ins in the Office 365 Admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)).</span></span> <span data-ttu-id="3aab6-105">Oltre a distribuire i componenti aggiuntivi di Office tramite l'interfaccia di amministrazione di Office 365, è anche possibile utilizzare Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3aab6-105">In addition to deploying Office add-ins via the Office 365 admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="3aab6-106">Installare il [modulo di distribuzione del componente aggiuntivo centralizzato di O365 per Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).</span><span class="sxs-lookup"><span data-stu-id="3aab6-106">Install the [O365 Centralized Add-In Deployment Module for Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).</span></span> 
    
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="3aab6-107">Connettersi utilizzando le credenziali di amministratore</span><span class="sxs-lookup"><span data-stu-id="3aab6-107">Connect using your admin credentials</span></span>

<span data-ttu-id="3aab6-108">Prima di poter utilizzare i cmdlet di distribuzione centralizzata, è necessario eseguire l'accesso.</span><span class="sxs-lookup"><span data-stu-id="3aab6-108">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="3aab6-109">Avviare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3aab6-109">Start PowerShell.</span></span>
    
2. <span data-ttu-id="3aab6-110">Connettersi a PowerShell mediante le credenziali di amministratore della società.</span><span class="sxs-lookup"><span data-stu-id="3aab6-110">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="3aab6-111">Eseguire il cmdlet seguente.</span><span class="sxs-lookup"><span data-stu-id="3aab6-111">Run the following cmdlet.</span></span>
    
  ```
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="3aab6-112">Nella pagina **Immetti le credenziali** , immettere le credenziali di amministratore globale di Office 365.</span><span class="sxs-lookup"><span data-stu-id="3aab6-112">In the **Enter Credentials** page, enter your Office 365 global admin credentials.</span></span> <span data-ttu-id="3aab6-113">In alternativa, è possibile immettere le credenziali direttamente nel cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3aab6-113">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="3aab6-114">Eseguire il cmdlet seguente specificando le credenziali di amministratore dell'azienda come oggetto PSCredential.</span><span class="sxs-lookup"><span data-stu-id="3aab6-114">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="3aab6-115">Per ulteriori informazioni sull'utilizzo di PowerShell, vedere [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span><span class="sxs-lookup"><span data-stu-id="3aab6-115">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="3aab6-116">Caricare un manifesto del componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="3aab6-116">Upload an add-in manifest</span></span>

<span data-ttu-id="3aab6-117">Eseguire il cmdlet New-Organizzazionecomponenti-in per caricare un manifesto del componente aggiuntivo da un percorso, che può essere un percorso o un URL di file.</span><span class="sxs-lookup"><span data-stu-id="3aab6-117">Run the New-OrganizationAdd-In cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="3aab6-118">Nell'esempio seguente viene illustrato un percorso di file per il valore del parametro _ManifestPath_ .</span><span class="sxs-lookup"><span data-stu-id="3aab6-118">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="3aab6-119">È inoltre possibile eseguire il cmdlet New-Organizzazionecomponenti-in per caricare un componente aggiuntivo e assegnarlo direttamente agli utenti o ai gruppi tramite il parametro _Members_ , come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="3aab6-119">You can also run the New-OrganizationAdd-In cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="3aab6-120">Separare gli indirizzi di posta elettronica dei membri con una virgola.</span><span class="sxs-lookup"><span data-stu-id="3aab6-120">Separate the email addresses of members with a comma.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="3aab6-121">Caricare un componente aggiuntivo da Office Store</span><span class="sxs-lookup"><span data-stu-id="3aab6-121">Upload an add-in from the Office Store</span></span>

<span data-ttu-id="3aab6-122">Eseguire il cmdlet New-OrganizationAddIn per caricare un manifesto da Office Store.</span><span class="sxs-lookup"><span data-stu-id="3aab6-122">Run the New-OrganizationAddIn cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="3aab6-123">Nell'esempio seguente, il cmdlet New-OrganizationAddIn consente di specificare il AssetId per un componente aggiuntivo per un sito e un mercato del contenuto degli Stati Uniti.</span><span class="sxs-lookup"><span data-stu-id="3aab6-123">In the following example, the New-OrganizationAddIn cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="3aab6-124">Per determinare il valore per il parametro _AssetID_ , è possibile copiarlo dall'URL della pagina Web di Office Store per il componente aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="3aab6-124">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="3aab6-125">AssetIds inizia sempre con "WA" seguito da un numero.</span><span class="sxs-lookup"><span data-stu-id="3aab6-125">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="3aab6-126">Nell'esempio precedente, ad esempio, l'origine per il valore AssetId di WA104099688 è l'URL della pagina Web di Office Store per il componente aggiuntivo: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span><span class="sxs-lookup"><span data-stu-id="3aab6-126">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="3aab6-127">I valori per il parametro _locale_ e per il parametro _ContentMarket_ sono identici e indicano il paese o l'area geografica in cui si sta tentando di installare il componente aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="3aab6-127">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="3aab6-128">Il formato è en-US, fr-FR.</span><span class="sxs-lookup"><span data-stu-id="3aab6-128">The format is en-US, fr-FR.</span></span> <span data-ttu-id="3aab6-129">e così via.</span><span class="sxs-lookup"><span data-stu-id="3aab6-129">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="3aab6-130">I componenti aggiuntivi caricati da Office Store vengono aggiornati automaticamente entro pochi giorni dall'ultimo aggiornamento disponibile in Office Store.</span><span class="sxs-lookup"><span data-stu-id="3aab6-130">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="3aab6-131">Ottenere informazioni dettagliate su un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="3aab6-131">Get details of an add-in</span></span>

<span data-ttu-id="3aab6-132">Eseguire il cmdlet Get-OrganizationAddIn come illustrato di seguito per ottenere informazioni dettagliate su tutti i componenti aggiuntivi caricati nel tenant, incluso un ID prodotto del componente aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="3aab6-132">Run the Get-OrganizationAddIn cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```
Get-OrganizationAddIn
```

<span data-ttu-id="3aab6-133">Eseguire il cmdlet Get-OrganizationAddIn con un valore per il parametro _ProductID_ per specificare il componente aggiuntivo di cui si desidera recuperare i dettagli.</span><span class="sxs-lookup"><span data-stu-id="3aab6-133">Run the Get-OrganizationAddIn cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="3aab6-134">Per ottenere informazioni complete su tutti i componenti aggiuntivi più gli utenti e i gruppi assegnati, eseguire il piping dell'output del cmdlet Get-OrganizationAddIn al cmdlet Format-List, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="3aab6-134">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the Get-OrganizationAddIn cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="3aab6-135">Attivazione o disattivazione di un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="3aab6-135">Turn on or turn off an add-in</span></span>

<span data-ttu-id="3aab6-136">Per disattivare un componente aggiuntivo in modo che gli utenti e i gruppi a esso assegnati non avranno più accesso, eseguire il cmdlet Set-OrganizationAddIn con il parametro _ProductID_ e il parametro _Enabled_ impostato su `$false`, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="3aab6-136">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the Set-OrganizationAddIn cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="3aab6-137">Per attivare di nuovo un componente aggiuntivo, eseguire lo stesso cmdlet con il parametro _Enabled_ impostato su `$true`.</span><span class="sxs-lookup"><span data-stu-id="3aab6-137">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="3aab6-138">Aggiungere o rimuovere utenti da un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="3aab6-138">Add or remove users from an add-in</span></span>

<span data-ttu-id="3aab6-139">Per aggiungere utenti e gruppi a un componente aggiuntivo specifico, eseguire il cmdlet Set-OrganizationAddInAssignments con i parametri _ProductID_, _Add_e _Members_ .</span><span class="sxs-lookup"><span data-stu-id="3aab6-139">To add users and groups to a specific add-in, run the Set-OrganizationAddInAssignments cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="3aab6-140">Separare gli indirizzi di posta elettronica dei membri con una virgola.</span><span class="sxs-lookup"><span data-stu-id="3aab6-140">Separate the email addresses of members with a comma.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="3aab6-141">Per rimuovere utenti e gruppi, eseguire lo stesso cmdlet utilizzando il parametro _Remove_ .</span><span class="sxs-lookup"><span data-stu-id="3aab6-141">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="3aab6-142">Per assegnare un componente aggiuntivo a tutti gli utenti nel tenant, eseguire lo stesso cmdlet utilizzando il parametro _AssignToEveryone_ con il valore impostato su `$true`.</span><span class="sxs-lookup"><span data-stu-id="3aab6-142">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="3aab6-143">Per non assegnare un componente aggiuntivo a tutti e ripristinare gli utenti e i gruppi precedentemente assegnati, è possibile eseguire lo stesso cmdlet e disattivare il parametro _AssignToEveryone_ impostando il relativo valore su `$false`.</span><span class="sxs-lookup"><span data-stu-id="3aab6-143">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="3aab6-144">Aggiornare un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="3aab6-144">Update an add-in</span></span>

<span data-ttu-id="3aab6-145">Per aggiornare un componente aggiuntivo da un manifesto, eseguire il cmdlet Set-OrganizationAddIn con i parametri _ProductID_, _ManifestPath_e _locale_ , come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="3aab6-145">To update an add-in from a manifest, run the Set-OrganizationAddIn cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="3aab6-146">I componenti aggiuntivi caricati da Office Store vengono aggiornati automaticamente entro pochi giorni dall'ultimo aggiornamento disponibile in Office Store.</span><span class="sxs-lookup"><span data-stu-id="3aab6-146">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="3aab6-147">Eliminare un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="3aab6-147">Delete an add-in</span></span>

<span data-ttu-id="3aab6-148">Per eliminare un componente aggiuntivo, eseguire il cmdlet Remove-OrganizationAddIn con il parametro _ProductID_ , come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="3aab6-148">To delete an add-in, run the Remove-OrganizationAddIn cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="3aab6-149">Ottenere informazioni dettagliate su ogni cmdlet</span><span class="sxs-lookup"><span data-stu-id="3aab6-149">Get detailed help for each cmdlet</span></span>

<span data-ttu-id="3aab6-150">È possibile esaminare la guida dettagliata per ogni cmdlet utilizzando il cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="3aab6-150">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="3aab6-151">Ad esempio, il cmdlet seguente fornisce informazioni dettagliate sul cmdlet Remove-OrganizationAddIn.</span><span class="sxs-lookup"><span data-stu-id="3aab6-151">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```
Get-help Remove-OrganizationAddIn -Full
```


