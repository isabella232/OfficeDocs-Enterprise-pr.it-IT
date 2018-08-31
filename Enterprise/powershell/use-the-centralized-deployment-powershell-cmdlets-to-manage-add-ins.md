---
title: Utilizzare i cmdlet PowerShell di distribuzione centralizzato per gestire i componenti aggiuntivi
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: Utilizzare i cmdlet PowerShell di distribuzione centralizzato per distribuire e gestire Office componenti aggiuntivi per l'organizzazione Office 365.
ms.openlocfilehash: f15bd1048d9240a125a1ae8245c773d83c6c935d
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541143"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="85dd1-103">Utilizzare i cmdlet PowerShell di distribuzione centralizzato per gestire i componenti aggiuntivi</span><span class="sxs-lookup"><span data-stu-id="85dd1-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="85dd1-p101">Come un amministratore di Office 365, è possibile distribuire i componenti aggiuntivi di Office per gli utenti tramite la distribuzione centralizzata funzionalità (vedere [gestire la distribuzione di componenti aggiuntivi a Office 365 nell'interfaccia di amministrazione di Office 365](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)). Oltre a distribuzione di componenti aggiuntivi a Office tramite l'interfaccia di amministrazione di Office 365, è inoltre possibile utilizzare Microsoft PowerShell. [Scaricare](https://go.microsoft.com/fwlink/p/?linkid=850850) i cmdlet di PowerShell distribuzione centralizzati da Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="85dd1-p101">As an Office 365 admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Manage deployment of Office 365 add-ins in the Office 365 admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)). In addition to deploying Office add-ins via the Office 365 admin center, you can also use Microsoft PowerShell. [Download](https://go.microsoft.com/fwlink/p/?linkid=850850) the Centralized Deployment PowerShell cmdlets from the Microsoft Download Center.</span></span> 
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="85dd1-107">Per saperne di più</span><span class="sxs-lookup"><span data-stu-id="85dd1-107">What do you want to do?</span></span>

[<span data-ttu-id="85dd1-108">Connettersi utilizzando le credenziali di amministrazione</span><span class="sxs-lookup"><span data-stu-id="85dd1-108">Connect using your admin credentials</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[<span data-ttu-id="85dd1-109">Caricare un manifesto del componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="85dd1-109">Upload an add-in manifest</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[<span data-ttu-id="85dd1-110">Caricare un componente aggiuntivo da Office Store</span><span class="sxs-lookup"><span data-stu-id="85dd1-110">Upload an add-in from the Office Store</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[<span data-ttu-id="85dd1-111">Ottenere i dettagli di un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="85dd1-111">Get details of an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[<span data-ttu-id="85dd1-112">Attivare o disattivare un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="85dd1-112">Turn on or turn off an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[<span data-ttu-id="85dd1-113">Aggiungere o rimuovere utenti dal componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="85dd1-113">Add or remove users from an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[<span data-ttu-id="85dd1-114">Aggiornare un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="85dd1-114">Update an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[<span data-ttu-id="85dd1-115">Elimina un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="85dd1-115">Delete an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[<span data-ttu-id="85dd1-116">Ottenere informazioni dettagliate per ogni cmdlet</span><span class="sxs-lookup"><span data-stu-id="85dd1-116">Get detailed help for each cmdlet</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="85dd1-117">Connettersi utilizzando le credenziali di amministrazione</span><span class="sxs-lookup"><span data-stu-id="85dd1-117">Connect using your admin credentials</span></span>
<span data-ttu-id="85dd1-118"><a name="BKMK_Connect"> </a></span><span class="sxs-lookup"><span data-stu-id="85dd1-118"></span></span>

<span data-ttu-id="85dd1-119">Prima di poter utilizzare i cmdlet di distribuzione centralizzata, è necessario eseguire l'accesso.</span><span class="sxs-lookup"><span data-stu-id="85dd1-119">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="85dd1-120">Avviare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="85dd1-120">Start PowerShell.</span></span>
    
2. <span data-ttu-id="85dd1-p102">Connettersi a PowerShell utilizzando le credenziali di amministratore di società. Eseguire il cmdlet seguente.</span><span class="sxs-lookup"><span data-stu-id="85dd1-p102">Connect to PowerShell by using your company admin credentials. Run the following cmdlet.</span></span>
    
  ```
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="85dd1-p103">Nella pagina **Immettere le credenziali** , immettere le credenziali di amministratore globale di Office 365. In alternativa, è possibile immettere le credenziali direttamente nel cmdlet.</span><span class="sxs-lookup"><span data-stu-id="85dd1-p103">In the **Enter Credentials** page, enter your Office 365 global admin credentials. Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="85dd1-125">Eseguire il cmdlet seguente che specifica la società le credenziali di amministratore come un oggetto PSCredential.</span><span class="sxs-lookup"><span data-stu-id="85dd1-125">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="85dd1-126">Per ulteriori informazioni sull'utilizzo di PowerShell, vedere [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span><span class="sxs-lookup"><span data-stu-id="85dd1-126">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="85dd1-127">Caricare un manifesto del componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="85dd1-127">Upload an add-in manifest</span></span>
<span data-ttu-id="85dd1-128"><a name="BKMK_UploadManifest"> </a></span><span class="sxs-lookup"><span data-stu-id="85dd1-128"></span></span>

<span data-ttu-id="85dd1-p104">Eseguire il cmdlet New-OrganizationAdd-In per caricare un manifesto del componente aggiuntivo da un percorso, che può essere un percorso o URL. Nell'esempio seguente viene illustrato un percorso di file per il valore del parametro _ManifestPath_ .</span><span class="sxs-lookup"><span data-stu-id="85dd1-p104">Run the New-OrganizationAdd-In cmdlet to upload an add-in manifest from a path, which can be either a file location or URL. The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="85dd1-p105">È inoltre possibile eseguire il cmdlet New-OrganizationAdd-In per caricare un componente aggiuntivo e assegnarlo a utenti o gruppi in modo diretto utilizzando il parametro _Members_ , come illustrato nell'esempio seguente. Separare gli indirizzi di posta elettronica dei membri con una virgola.</span><span class="sxs-lookup"><span data-stu-id="85dd1-p105">You can also run the New-OrganizationAdd-In cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example. Separate the email addresses of members with a comma.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="85dd1-133">Caricare un componente aggiuntivo da Office Store</span><span class="sxs-lookup"><span data-stu-id="85dd1-133">Upload an add-in from the Office Store</span></span>
<span data-ttu-id="85dd1-134"><a name="BKMK_UploadAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="85dd1-134"></span></span>

<span data-ttu-id="85dd1-135">Eseguire il cmdlet New-OrganizationAddIn per caricare un manifesto da Office Store.</span><span class="sxs-lookup"><span data-stu-id="85dd1-135">Run the New-OrganizationAddIn cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="85dd1-136">Nell'esempio seguente, il cmdlet New-OrganizationAddIn specifica AssetId per un componente aggiuntivo per il mercato percorso e il contenuto degli Stati Uniti.</span><span class="sxs-lookup"><span data-stu-id="85dd1-136">In the following example, the New-OrganizationAddIn cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="85dd1-p106">Per determinare il valore del parametro _AssetId_ , è possibile copiarlo dall'URL dell'archivio di Office a pagina Web per il componente aggiuntivo AssetIds iniziano sempre con "WA" seguito da un numero. Nell'esempio precedente, ad esempio, l'origine per il valore AssetId del WA104099688 è l'URL della pagina Web di Office Store per il componente aggiuntivo: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span><span class="sxs-lookup"><span data-stu-id="85dd1-p106">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in. AssetIds always begin with "WA" followed by a number. For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="85dd1-p107">I valori per il parametro _Locale_ e il parametro _ContentMarket_ sono identici e indicano il paese/area geografica da che si sta tentando di installare il componente aggiuntivo. Il formato è en-US, fr-FR. e così via.</span><span class="sxs-lookup"><span data-stu-id="85dd1-p107">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from. The format is en-US, fr-FR. and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="85dd1-143">Componenti aggiuntivi caricati da Office Store verranno aggiornata automaticamente entro pochi giorni dalla data dell'ultimo aggiornamento viene disponibili in Office Store.</span><span class="sxs-lookup"><span data-stu-id="85dd1-143">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="85dd1-144">Ottenere i dettagli di un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="85dd1-144">Get details of an add-in</span></span>
<span data-ttu-id="85dd1-145"><a name="BKMK_GetDetails"> </a></span><span class="sxs-lookup"><span data-stu-id="85dd1-145"></span></span>

<span data-ttu-id="85dd1-146">Eseguire il cmdlet Get-OrganizationAddIn come indicato di seguito per visualizzare i dettagli di tutti i componenti aggiuntivi caricati tenant, incluso ID del prodotto. di un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="85dd1-146">Run the Get-OrganizationAddIn cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```
Get-OrganizationAddIn
```

<span data-ttu-id="85dd1-147">Eseguire il cmdlet Get-OrganizationAddIn con un valore per il parametro _IDProdotto_ per specificare quali componenti aggiuntivi che si desidera recuperare dettagli relativi a.</span><span class="sxs-lookup"><span data-stu-id="85dd1-147">Run the Get-OrganizationAddIn cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="85dd1-148">Per ottenere informazioni dettagliate su tutti i componenti aggiuntivi oltre l'assegnati agli utenti e gruppi, eseguire il piping dell'output del cmdlet Get-OrganizationAddIn al cmdlet Format-List, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="85dd1-148">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the Get-OrganizationAddIn cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="85dd1-149">Attivare o disattivare un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="85dd1-149">Turn on or turn off an add-in</span></span>
<span data-ttu-id="85dd1-150"><a name="BKMK_TurnOnOff"> </a></span><span class="sxs-lookup"><span data-stu-id="85dd1-150"></span></span>

<span data-ttu-id="85dd1-151">Per disattivare un componente aggiuntivo in modo che gli utenti e gruppi che sono assegnati a esso non disporrà più accesso, eseguire il cmdlet Set-OrganizationAddIn con il parametro _ProductId_ e il parametro _Enabled_ impostato su `$false`, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="85dd1-151">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the Set-OrganizationAddIn cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="85dd1-152">Per riattivare un componente aggiuntivo, eseguire il cmdlet stesso con il parametro _Enabled_ impostato su `$true`.</span><span class="sxs-lookup"><span data-stu-id="85dd1-152">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="85dd1-153">Aggiungere o rimuovere utenti dal componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="85dd1-153">Add or remove users from an add-in</span></span>
<span data-ttu-id="85dd1-154"><a name="BKMK_AddRemove"> </a></span><span class="sxs-lookup"><span data-stu-id="85dd1-154"></span></span>

<span data-ttu-id="85dd1-p108">Per aggiungere utenti e gruppi a un componente aggiuntivo specifico, eseguire il cmdlet Set-OrganizationAddInAssignments con i parametri _IDProdotto_, _Aggiungi_e _membri_ . Separare gli indirizzi di posta elettronica dei membri con una virgola.</span><span class="sxs-lookup"><span data-stu-id="85dd1-p108">To add users and groups to a specific add-in, run the Set-OrganizationAddInAssignments cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters. Separate the email addresses of members with a comma.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="85dd1-157">Per rimuovere utenti e gruppi, eseguire il cmdlet stesso utilizzando il parametro _rimuovere_ .</span><span class="sxs-lookup"><span data-stu-id="85dd1-157">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="85dd1-158">Per assegnare un componente aggiuntivo a tutti gli utenti del tenant, eseguire il cmdlet stesso utilizzando il parametro _AssignToEveryone_ con il valore impostato su `$true`.</span><span class="sxs-lookup"><span data-stu-id="85dd1-158">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="85dd1-159">Per non assegnare un componente aggiuntivo per tutti gli utenti e ripristinare precedentemente assegnati agli utenti e gruppi, è possibile eseguire il cmdlet stesso e consente di disattivare il parametro _AssignToEveryone_ impostando il valore su `$false`.</span><span class="sxs-lookup"><span data-stu-id="85dd1-159">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="85dd1-160">Aggiornare un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="85dd1-160">Update an add-in</span></span>
<span data-ttu-id="85dd1-161"><a name="BKMK_UpdateAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="85dd1-161"></span></span>

<span data-ttu-id="85dd1-162">Per aggiornare un componente aggiuntivo da un manifesto, eseguire il cmdlet Set-OrganizationAddIn con _IDProdotto_, _ManifestPath_e parametri _delle impostazioni locali_ , come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="85dd1-162">To update an add-in from a manifest, run the Set-OrganizationAddIn cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="85dd1-163">Componenti aggiuntivi caricati da Office Store verranno aggiornata automaticamente entro pochi giorni dalla data dell'ultimo aggiornamento viene disponibili in Office Store.</span><span class="sxs-lookup"><span data-stu-id="85dd1-163">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="85dd1-164">Elimina un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="85dd1-164">Delete an add-in</span></span>
<span data-ttu-id="85dd1-165"><a name="BKMK_Delete"> </a></span><span class="sxs-lookup"><span data-stu-id="85dd1-165"></span></span>

<span data-ttu-id="85dd1-166">Per eliminare un componente aggiuntivo, eseguire il cmdlet Remove-OrganizationAddIn con il parametro _ProductId_ , come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="85dd1-166">To delete an add-in, run the Remove-OrganizationAddIn cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="85dd1-167">Ottenere informazioni dettagliate per ogni cmdlet</span><span class="sxs-lookup"><span data-stu-id="85dd1-167">Get detailed help for each cmdlet</span></span>
<span data-ttu-id="85dd1-168"><a name="BKMK_GetHelp"> </a></span><span class="sxs-lookup"><span data-stu-id="85dd1-168"></span></span>

<span data-ttu-id="85dd1-p109">È possibile esaminare la Guida dettagliata relativi a ciascun cmdlet utilizzando il cmdlet Get-help. Ad esempio, il cmdlet seguente vengono fornite informazioni dettagliate sul cmdlet Remove-OrganizationAddIn.</span><span class="sxs-lookup"><span data-stu-id="85dd1-p109">You can look at detailed help for each cmdlet by using the Get-help cmdlet. For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```
Get-help Remove-OrganizationAddIn -Full
```


