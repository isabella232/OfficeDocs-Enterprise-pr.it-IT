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
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: Utilizzare i cmdlet di PowerShell per la distribuzione centralizzata per facilitare la distribuzione e la gestione dei componenti aggiuntivi di Office per l'organizzazione di Office 365.
ms.openlocfilehash: 404085d79827664437f3ad327fac4a99166adcf4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071142"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="e3fe3-103">Usare i cmdlet di PowerShell della distribuzione centralizzata per gestire i componenti aggiuntivi</span><span class="sxs-lookup"><span data-stu-id="e3fe3-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="e3fe3-104">In qualità di amministratore di Office 365, è possibile distribuire i componenti aggiuntivi di Office agli utenti tramite la caratteristica di distribuzione centralizzata (vedere [gestire la distribuzione dei componenti aggiuntivi di office 365 nell'interfaccia di amministrazione di office 365](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)).</span><span class="sxs-lookup"><span data-stu-id="e3fe3-104">As an Office 365 admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Manage deployment of Office 365 add-ins in the Office 365 admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)).</span></span> <span data-ttu-id="e3fe3-105">Oltre a distribuire i componenti aggiuntivi di Office tramite l'interfaccia di amministrazione di Office 365, è anche possibile utilizzare Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-105">In addition to deploying Office add-ins via the Office 365 admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="e3fe3-106">[Scaricare](https://go.microsoft.com/fwlink/p/?linkid=850850) i cmdlet di PowerShell per la distribuzione centralizzata dall'area download Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-106">[Download](https://go.microsoft.com/fwlink/p/?linkid=850850) the Centralized Deployment PowerShell cmdlets from the Microsoft Download Center.</span></span> 
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="e3fe3-107">Operazione desiderata</span><span class="sxs-lookup"><span data-stu-id="e3fe3-107">What do you want to do?</span></span>

[<span data-ttu-id="e3fe3-108">Connettersi utilizzando le credenziali di amministratore</span><span class="sxs-lookup"><span data-stu-id="e3fe3-108">Connect using your admin credentials</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[<span data-ttu-id="e3fe3-109">Caricare un manifesto del componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="e3fe3-109">Upload an add-in manifest</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[<span data-ttu-id="e3fe3-110">Caricare un componente aggiuntivo da Office Store</span><span class="sxs-lookup"><span data-stu-id="e3fe3-110">Upload an add-in from the Office Store</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[<span data-ttu-id="e3fe3-111">Ottenere informazioni dettagliate su un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="e3fe3-111">Get details of an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[<span data-ttu-id="e3fe3-112">Attivazione o disattivazione di un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="e3fe3-112">Turn on or turn off an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[<span data-ttu-id="e3fe3-113">Aggiungere o rimuovere utenti da un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="e3fe3-113">Add or remove users from an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[<span data-ttu-id="e3fe3-114">Aggiornare un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="e3fe3-114">Update an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[<span data-ttu-id="e3fe3-115">Eliminare un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="e3fe3-115">Delete an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[<span data-ttu-id="e3fe3-116">Ottenere informazioni dettagliate su ogni cmdlet</span><span class="sxs-lookup"><span data-stu-id="e3fe3-116">Get detailed help for each cmdlet</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="e3fe3-117">Connettersi utilizzando le credenziali di amministratore</span><span class="sxs-lookup"><span data-stu-id="e3fe3-117">Connect using your admin credentials</span></span>
<span data-ttu-id="e3fe3-118"><a name="BKMK_Connect"> </a></span><span class="sxs-lookup"><span data-stu-id="e3fe3-118"></span></span>

<span data-ttu-id="e3fe3-119">Prima di poter utilizzare i cmdlet di distribuzione centralizzata, è necessario eseguire l'accesso.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-119">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="e3fe3-120">Avviare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-120">Start PowerShell.</span></span>
    
2. <span data-ttu-id="e3fe3-121">Connettersi a PowerShell mediante le credenziali di amministratore della società.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-121">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="e3fe3-122">Eseguire il cmdlet seguente.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-122">Run the following cmdlet.</span></span>
    
  ```
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="e3fe3-123">Nella pagina **Immetti le credenziali** , immettere le credenziali di amministratore globale di Office 365.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-123">In the **Enter Credentials** page, enter your Office 365 global admin credentials.</span></span> <span data-ttu-id="e3fe3-124">In alternativa, è possibile immettere le credenziali direttamente nel cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-124">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="e3fe3-125">Eseguire il cmdlet seguente specificando le credenziali di amministratore dell'azienda come oggetto PSCredential.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-125">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="e3fe3-126">Per ulteriori informazioni sull'utilizzo di PowerShell, vedere [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span><span class="sxs-lookup"><span data-stu-id="e3fe3-126">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="e3fe3-127">Caricare un manifesto del componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="e3fe3-127">Upload an add-in manifest</span></span>
<span data-ttu-id="e3fe3-128"><a name="BKMK_UploadManifest"> </a></span><span class="sxs-lookup"><span data-stu-id="e3fe3-128"></span></span>

<span data-ttu-id="e3fe3-129">Eseguire il cmdlet New-Organizzazionecomponenti-in per caricare un manifesto del componente aggiuntivo da un percorso, che può essere un percorso o un URL di file.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-129">Run the New-OrganizationAdd-In cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="e3fe3-130">Nell'esempio seguente viene illustrato un percorso di file per il valore del parametro _ManifestPath_ .</span><span class="sxs-lookup"><span data-stu-id="e3fe3-130">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="e3fe3-131">È inoltre possibile eseguire il cmdlet New-Organizzazionecomponenti-in per caricare un componente aggiuntivo e assegnarlo direttamente agli utenti o ai gruppi tramite il parametro _Members_ , come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-131">You can also run the New-OrganizationAdd-In cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="e3fe3-132">Separare gli indirizzi di posta elettronica dei membri con una virgola.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-132">Separate the email addresses of members with a comma.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="e3fe3-133">Caricare un componente aggiuntivo da Office Store</span><span class="sxs-lookup"><span data-stu-id="e3fe3-133">Upload an add-in from the Office Store</span></span>
<span data-ttu-id="e3fe3-134"><a name="BKMK_UploadAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="e3fe3-134"></span></span>

<span data-ttu-id="e3fe3-135">Eseguire il cmdlet New-OrganizationAddIn per caricare un manifesto da Office Store.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-135">Run the New-OrganizationAddIn cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="e3fe3-136">Nell'esempio seguente, il cmdlet New-OrganizationAddIn consente di specificare il AssetId per un componente aggiuntivo per un sito e un mercato del contenuto degli Stati Uniti.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-136">In the following example, the New-OrganizationAddIn cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="e3fe3-137">Per determinare il valore per il parametro _AssetID_ , è possibile copiarlo dall'URL della pagina Web di Office Store per il componente aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-137">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="e3fe3-138">AssetIds inizia sempre con "WA" seguito da un numero.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-138">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="e3fe3-139">Nell'esempio precedente, ad esempio, l'origine per il valore AssetId di WA104099688 è l'URL della pagina Web di Office Store per il componente aggiuntivo: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span><span class="sxs-lookup"><span data-stu-id="e3fe3-139">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="e3fe3-140">I valori per il parametro _locale_ e per il parametro _ContentMarket_ sono identici e indicano il paese o l'area geografica in cui si sta tentando di installare il componente aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-140">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="e3fe3-141">Il formato è en-US, fr-FR.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-141">The format is en-US, fr-FR.</span></span> <span data-ttu-id="e3fe3-142">e così via.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-142">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="e3fe3-143">I componenti aggiuntivi caricati da Office Store vengono aggiornati automaticamente entro pochi giorni dall'ultimo aggiornamento disponibile in Office Store.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-143">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="e3fe3-144">Ottenere informazioni dettagliate su un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="e3fe3-144">Get details of an add-in</span></span>
<span data-ttu-id="e3fe3-145"><a name="BKMK_GetDetails"> </a></span><span class="sxs-lookup"><span data-stu-id="e3fe3-145"></span></span>

<span data-ttu-id="e3fe3-146">Eseguire il cmdlet Get-OrganizationAddIn come illustrato di seguito per ottenere informazioni dettagliate su tutti i componenti aggiuntivi caricati nel tenant, incluso un ID prodotto del componente aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-146">Run the Get-OrganizationAddIn cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```
Get-OrganizationAddIn
```

<span data-ttu-id="e3fe3-147">Eseguire il cmdlet Get-OrganizationAddIn con un valore per il parametro _ProductID_ per specificare il componente aggiuntivo di cui si desidera recuperare i dettagli.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-147">Run the Get-OrganizationAddIn cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="e3fe3-148">Per ottenere informazioni complete su tutti i componenti aggiuntivi più gli utenti e i gruppi assegnati, eseguire il piping dell'output del cmdlet Get-OrganizationAddIn al cmdlet Format-List, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-148">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the Get-OrganizationAddIn cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="e3fe3-149">Attivazione o disattivazione di un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="e3fe3-149">Turn on or turn off an add-in</span></span>
<span data-ttu-id="e3fe3-150"><a name="BKMK_TurnOnOff"> </a></span><span class="sxs-lookup"><span data-stu-id="e3fe3-150"></span></span>

<span data-ttu-id="e3fe3-151">Per disattivare un componente aggiuntivo in modo che gli utenti e i gruppi a esso assegnati non avranno più accesso, eseguire il cmdlet Set-OrganizationAddIn con il parametro _ProductID_ e il parametro _Enabled_ impostato su `$false`, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-151">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the Set-OrganizationAddIn cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="e3fe3-152">Per attivare di nuovo un componente aggiuntivo, eseguire lo stesso cmdlet con il parametro _Enabled_ impostato su `$true`.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-152">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="e3fe3-153">Aggiungere o rimuovere utenti da un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="e3fe3-153">Add or remove users from an add-in</span></span>
<span data-ttu-id="e3fe3-154"><a name="BKMK_AddRemove"> </a></span><span class="sxs-lookup"><span data-stu-id="e3fe3-154"></span></span>

<span data-ttu-id="e3fe3-155">Per aggiungere utenti e gruppi a un componente aggiuntivo specifico, eseguire il cmdlet Set-OrganizationAddInAssignments con i parametri _ProductID_, _Add_e _Members_ .</span><span class="sxs-lookup"><span data-stu-id="e3fe3-155">To add users and groups to a specific add-in, run the Set-OrganizationAddInAssignments cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="e3fe3-156">Separare gli indirizzi di posta elettronica dei membri con una virgola.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-156">Separate the email addresses of members with a comma.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="e3fe3-157">Per rimuovere utenti e gruppi, eseguire lo stesso cmdlet utilizzando il parametro _Remove_ .</span><span class="sxs-lookup"><span data-stu-id="e3fe3-157">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="e3fe3-158">Per assegnare un componente aggiuntivo a tutti gli utenti nel tenant, eseguire lo stesso cmdlet utilizzando il parametro _AssignToEveryone_ con il valore impostato su `$true`.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-158">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="e3fe3-159">Per non assegnare un componente aggiuntivo a tutti e ripristinare gli utenti e i gruppi precedentemente assegnati, è possibile eseguire lo stesso cmdlet e disattivare il parametro _AssignToEveryone_ impostando il relativo valore su `$false`.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-159">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="e3fe3-160">Aggiornare un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="e3fe3-160">Update an add-in</span></span>
<span data-ttu-id="e3fe3-161"><a name="BKMK_UpdateAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="e3fe3-161"></span></span>

<span data-ttu-id="e3fe3-162">Per aggiornare un componente aggiuntivo da un manifesto, eseguire il cmdlet Set-OrganizationAddIn con i parametri _ProductID_, _ManifestPath_e _locale_ , come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-162">To update an add-in from a manifest, run the Set-OrganizationAddIn cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="e3fe3-163">I componenti aggiuntivi caricati da Office Store vengono aggiornati automaticamente entro pochi giorni dall'ultimo aggiornamento disponibile in Office Store.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-163">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="e3fe3-164">Eliminare un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="e3fe3-164">Delete an add-in</span></span>
<span data-ttu-id="e3fe3-165"><a name="BKMK_Delete"> </a></span><span class="sxs-lookup"><span data-stu-id="e3fe3-165"></span></span>

<span data-ttu-id="e3fe3-166">Per eliminare un componente aggiuntivo, eseguire il cmdlet Remove-OrganizationAddIn con il parametro _ProductID_ , come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-166">To delete an add-in, run the Remove-OrganizationAddIn cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="e3fe3-167">Ottenere informazioni dettagliate su ogni cmdlet</span><span class="sxs-lookup"><span data-stu-id="e3fe3-167">Get detailed help for each cmdlet</span></span>
<span data-ttu-id="e3fe3-168"><a name="BKMK_GetHelp"> </a></span><span class="sxs-lookup"><span data-stu-id="e3fe3-168"></span></span>

<span data-ttu-id="e3fe3-169">È possibile esaminare la guida dettagliata per ogni cmdlet utilizzando il cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-169">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="e3fe3-170">Ad esempio, il cmdlet seguente fornisce informazioni dettagliate sul cmdlet Remove-OrganizationAddIn.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-170">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```
Get-help Remove-OrganizationAddIn -Full
```


