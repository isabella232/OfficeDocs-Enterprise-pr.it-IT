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
ms.openlocfilehash: c63a48d212bba4eda25fb6b8843f6321892dc54b
ms.sourcegitcommit: d53033c2d2d41d52047e3e2644d77373d4a5dd9a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/18/2019
ms.locfileid: "35791251"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="a8d69-103">Usare i cmdlet di PowerShell della distribuzione centralizzata per gestire i componenti aggiuntivi</span><span class="sxs-lookup"><span data-stu-id="a8d69-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="a8d69-104">In qualità di Microsoft 365 Global o amministratore di Exchange, è possibile distribuire i componenti aggiuntivi di Office agli utenti tramite la caratteristica di distribuzione centralizzata (vedere [Deploy Office Add-ins in the Admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)).</span><span class="sxs-lookup"><span data-stu-id="a8d69-104">As a Microsoft 365 global, or Exchange admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Deploy Office Add-ins in the admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)).</span></span> <span data-ttu-id="a8d69-105">Oltre a distribuire i componenti aggiuntivi di Office tramite l'interfaccia di amministrazione di Microsoft 365, è anche possibile utilizzare Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a8d69-105">In addition to deploying Office add-ins via the Microsoft 365 admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="a8d69-106">Installare il [modulo di distribuzione del componente aggiuntivo centralizzato di O365 per Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).</span><span class="sxs-lookup"><span data-stu-id="a8d69-106">Install the [O365 Centralized Add-In Deployment Module for Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).</span></span> 

<span data-ttu-id="a8d69-107">Dopo aver scaricato il modulo, aprire una normale finestra di Windows PowerShell ed eseguire il cmdlet seguente:</span><span class="sxs-lookup"><span data-stu-id="a8d69-107">After you download the module, open a regular Windows PowerShell window and run the following cmdlet:</span></span>

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```
    
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="a8d69-108">Connettersi utilizzando le credenziali di amministratore</span><span class="sxs-lookup"><span data-stu-id="a8d69-108">Connect using your admin credentials</span></span>

<span data-ttu-id="a8d69-109">Prima di poter utilizzare i cmdlet di distribuzione centralizzata, è necessario eseguire l'accesso.</span><span class="sxs-lookup"><span data-stu-id="a8d69-109">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="a8d69-110">Avviare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a8d69-110">Start PowerShell.</span></span>
    
2. <span data-ttu-id="a8d69-111">Connettersi a PowerShell mediante le credenziali di amministratore della società.</span><span class="sxs-lookup"><span data-stu-id="a8d69-111">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="a8d69-112">Eseguire il cmdlet seguente.</span><span class="sxs-lookup"><span data-stu-id="a8d69-112">Run the following cmdlet.</span></span>
    
  ```powershell
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="a8d69-113">Nella pagina **Immetti le credenziali** , immettere le credenziali di amministratore globale di Office 365.</span><span class="sxs-lookup"><span data-stu-id="a8d69-113">In the **Enter Credentials** page, enter your Office 365 global admin credentials.</span></span> <span data-ttu-id="a8d69-114">In alternativa, è possibile immettere le credenziali direttamente nel cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a8d69-114">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="a8d69-115">Eseguire il cmdlet seguente specificando le credenziali di amministratore dell'azienda come oggetto PSCredential.</span><span class="sxs-lookup"><span data-stu-id="a8d69-115">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="a8d69-116">Per ulteriori informazioni sull'utilizzo di PowerShell, vedere [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span><span class="sxs-lookup"><span data-stu-id="a8d69-116">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="a8d69-117">Caricare un manifesto del componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="a8d69-117">Upload an add-in manifest</span></span>

<span data-ttu-id="a8d69-118">Eseguire il cmdlet **New-organizzazionecomponenti-in** per caricare un manifesto del componente aggiuntivo da un percorso, che può essere un percorso o un URL di file.</span><span class="sxs-lookup"><span data-stu-id="a8d69-118">Run the **New-OrganizationAdd-In** cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="a8d69-119">Nell'esempio seguente viene illustrato un percorso di file per il valore del parametro _ManifestPath_ .</span><span class="sxs-lookup"><span data-stu-id="a8d69-119">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="a8d69-120">È inoltre possibile eseguire il cmdlet **New-organizzazionecomponenti-in** per caricare un componente aggiuntivo e assegnarlo direttamente agli utenti o ai gruppi tramite il parametro _Members_ , come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="a8d69-120">You can also run the **New-OrganizationAdd-In** cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="a8d69-121">Separare gli indirizzi di posta elettronica dei membri con una virgola.</span><span class="sxs-lookup"><span data-stu-id="a8d69-121">Separate the email addresses of members with a comma.</span></span> 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="a8d69-122">Caricare un componente aggiuntivo da Office Store</span><span class="sxs-lookup"><span data-stu-id="a8d69-122">Upload an add-in from the Office Store</span></span>

<span data-ttu-id="a8d69-123">Eseguire il cmdlet **New-OrganizationAddIn** per caricare un manifesto da Office Store.</span><span class="sxs-lookup"><span data-stu-id="a8d69-123">Run the **New-OrganizationAddIn** cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="a8d69-124">Nell'esempio seguente, il cmdlet **New-OrganizationAddIn** consente di specificare il AssetID per un componente aggiuntivo per un sito e un mercato del contenuto degli Stati Uniti.</span><span class="sxs-lookup"><span data-stu-id="a8d69-124">In the following example, the **New-OrganizationAddIn** cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="a8d69-125">Per determinare il valore per il parametro _AssetID_ , è possibile copiarlo dall'URL della pagina Web di Office Store per il componente aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="a8d69-125">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="a8d69-126">AssetIds inizia sempre con "WA" seguito da un numero.</span><span class="sxs-lookup"><span data-stu-id="a8d69-126">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="a8d69-127">Nell'esempio precedente, ad esempio, l'origine per il valore AssetId di WA104099688 è l'URL della pagina Web di Office Store per il componente aggiuntivo: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span><span class="sxs-lookup"><span data-stu-id="a8d69-127">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="a8d69-128">I valori per il parametro _locale_ e per il parametro _ContentMarket_ sono identici e indicano il paese o l'area geografica in cui si sta tentando di installare il componente aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="a8d69-128">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="a8d69-129">Il formato è en-US, fr-FR.</span><span class="sxs-lookup"><span data-stu-id="a8d69-129">The format is en-US, fr-FR.</span></span> <span data-ttu-id="a8d69-130">e così via.</span><span class="sxs-lookup"><span data-stu-id="a8d69-130">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="a8d69-131">I componenti aggiuntivi caricati da Office Store vengono aggiornati automaticamente entro pochi giorni dall'ultimo aggiornamento disponibile in Office Store.</span><span class="sxs-lookup"><span data-stu-id="a8d69-131">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="a8d69-132">Ottenere informazioni dettagliate su un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="a8d69-132">Get details of an add-in</span></span>

<span data-ttu-id="a8d69-133">Eseguire il cmdlet **Get-OrganizationAddIn** come illustrato di seguito per ottenere informazioni dettagliate su tutti i componenti aggiuntivi caricati nel tenant, incluso un ID prodotto del componente aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="a8d69-133">Run the **Get-OrganizationAddIn** cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```powershell
Get-OrganizationAddIn
```

<span data-ttu-id="a8d69-134">Eseguire il cmdlet **Get-OrganizationAddIn** con un valore per il parametro _ProductID_ per specificare il componente aggiuntivo di cui si desidera recuperare i dettagli.</span><span class="sxs-lookup"><span data-stu-id="a8d69-134">Run the **Get-OrganizationAddIn** cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="a8d69-135">Per ottenere informazioni complete su tutti i componenti aggiuntivi più gli utenti e i gruppi assegnati, eseguire il piping dell'output del cmdlet **Get-OrganizationAddIn** al cmdlet Format-List, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="a8d69-135">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the **Get-OrganizationAddIn** cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```powershell
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="a8d69-136">Attivazione o disattivazione di un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="a8d69-136">Turn on or turn off an add-in</span></span>

<span data-ttu-id="a8d69-137">Per disattivare un componente aggiuntivo in modo che gli utenti e i gruppi a esso assegnati non avranno più accesso, eseguire il cmdlet **set-OrganizationAddIn** con il parametro _ProductID_ e il parametro _Enabled_ impostato su `$false`, come illustrato nell'esempio seguente. .</span><span class="sxs-lookup"><span data-stu-id="a8d69-137">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the **Set-OrganizationAddIn** cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="a8d69-138">Per attivare di nuovo un componente aggiuntivo, eseguire lo stesso cmdlet con il parametro _Enabled_ impostato su `$true`.</span><span class="sxs-lookup"><span data-stu-id="a8d69-138">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="a8d69-139">Aggiungere o rimuovere utenti da un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="a8d69-139">Add or remove users from an add-in</span></span>

<span data-ttu-id="a8d69-140">Per aggiungere utenti e gruppi a un componente aggiuntivo specifico, eseguire il cmdlet **set-OrganizationAddInAssignments** con i parametri _ProductID_, _Add_e _Members_ .</span><span class="sxs-lookup"><span data-stu-id="a8d69-140">To add users and groups to a specific add-in, run the **Set-OrganizationAddInAssignments** cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="a8d69-141">Separare gli indirizzi di posta elettronica dei membri con una virgola.</span><span class="sxs-lookup"><span data-stu-id="a8d69-141">Separate the email addresses of members with a comma.</span></span> 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="a8d69-142">Per rimuovere utenti e gruppi, eseguire lo stesso cmdlet utilizzando il parametro _Remove_ .</span><span class="sxs-lookup"><span data-stu-id="a8d69-142">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="a8d69-143">Per assegnare un componente aggiuntivo a tutti gli utenti nel tenant, eseguire lo stesso cmdlet utilizzando il parametro _AssignToEveryone_ con il valore impostato su `$true`.</span><span class="sxs-lookup"><span data-stu-id="a8d69-143">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="a8d69-144">Per non assegnare un componente aggiuntivo a tutti e ripristinare gli utenti e i gruppi precedentemente assegnati, è possibile eseguire lo stesso cmdlet e disattivare il parametro _AssignToEveryone_ impostando il relativo valore su `$false`.</span><span class="sxs-lookup"><span data-stu-id="a8d69-144">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="a8d69-145">Aggiornare un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="a8d69-145">Update an add-in</span></span>

<span data-ttu-id="a8d69-146">Per aggiornare un componente aggiuntivo da un manifesto, eseguire il cmdlet **set-OrganizationAddIn** con i parametri _ProductID_, _ManifestPath_e _locale_ , come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="a8d69-146">To update an add-in from a manifest, run the **Set-OrganizationAddIn** cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="a8d69-147">I componenti aggiuntivi caricati da Office Store vengono aggiornati automaticamente entro pochi giorni dall'ultimo aggiornamento disponibile in Office Store.</span><span class="sxs-lookup"><span data-stu-id="a8d69-147">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="a8d69-148">Eliminare un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="a8d69-148">Delete an add-in</span></span>

<span data-ttu-id="a8d69-149">Per eliminare un componente aggiuntivo, eseguire il cmdlet **Remove-OrganizationAddIn** con il parametro _ProductID_ , come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="a8d69-149">To delete an add-in, run the **Remove-OrganizationAddIn** cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```powershell
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="customize-microsoft-store-add-ins-for-your-organization"></a><span data-ttu-id="a8d69-150">Personalizzare i componenti aggiuntivi di Microsoft Store per l'organizzazione</span><span class="sxs-lookup"><span data-stu-id="a8d69-150">Customize Microsoft Store add-ins for your organization</span></span>

<span data-ttu-id="a8d69-151">È necessario personalizzare il componente aggiuntivo prima di distribuirlo nell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="a8d69-151">You must customize the add-in before you deploy it to your organization.</span></span> <span data-ttu-id="a8d69-152">I componenti aggiuntivi precedenti alla versione 1,1 non sono supportati da questa funzionalità.</span><span class="sxs-lookup"><span data-stu-id="a8d69-152">Add-ins older than version 1.1 are not supported by this feature.</span></span> 

<span data-ttu-id="a8d69-153">Tenere presente anche le restrizioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="a8d69-153">Note also the following restrictions:</span></span>
- <span data-ttu-id="a8d69-154">Tutti gli URL devono essere assoluti (Includi http o HTTPS) e validi.</span><span class="sxs-lookup"><span data-stu-id="a8d69-154">All URLs must be absolute (include http or https) and valid.</span></span>
- <span data-ttu-id="a8d69-155">*DisplayName* non deve superare 125 caratteri</span><span class="sxs-lookup"><span data-stu-id="a8d69-155">*DisplayName* must not exceed 125 characters</span></span> 
- <span data-ttu-id="a8d69-156">*DisplayName*, \*\* Resources and *AppDomains* non deve includere i caratteri seguenti:</span><span class="sxs-lookup"><span data-stu-id="a8d69-156">*DisplayName*, *Resources* and *AppDomains* must not include the following characters:</span></span> 
 
    - \<
    -  \>
    -  <span data-ttu-id="a8d69-157">;</span><span class="sxs-lookup"><span data-stu-id="a8d69-157"></span></span>
    -  =   

<span data-ttu-id="a8d69-158">Se si desidera personalizzare un componente aggiuntivo distribuito, è necessario disinstallarlo nell'interfaccia di amministrazione e vedere [rimuovere un componente aggiuntivo dalla cache locale](#remove-an-add-in-from-local-cache) per i passaggi da rimuovere da ogni computer in cui è stata distribuita.</span><span class="sxs-lookup"><span data-stu-id="a8d69-158">If you want to customize an add-in that has been deployed, you have to uninstall it in the admin center, and see [remove an add-in from local cache](#remove-an-add-in-from-local-cache) for steps to remove it from each computer it has been deployed to.</span></span>

<span data-ttu-id="a8d69-159">Per personalizzare un componente aggiuntivo, eseguire il cmdlet **set-OrganizationAddInOverrides** con il *ProductID* come parametro, seguito dal tag che si desidera sovrascrivere e dal nuovo valore.</span><span class="sxs-lookup"><span data-stu-id="a8d69-159">To customize an add-in, run the **Set –OrganizationAddInOverrides** cmdlet with the *ProductId* as a parameter, followed by the tag you want to overwrite and the new value.</span></span> <span data-ttu-id="a8d69-160">Per informazioni su come ottenere il *ProductID* , vedere [ottenere i dettagli di un componente aggiuntivo](#get-details-of-an-add-in) in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="a8d69-160">To find out how to get the *ProductId* see [get details of an add-in](#get-details-of-an-add-in) in this article.</span></span> <span data-ttu-id="a8d69-161">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="a8d69-161">For example:</span></span>

```powershell
 Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -IconUrl "http://site.com/img.jpg" 
```
<span data-ttu-id="a8d69-162">Per personalizzare più tag per un componente aggiuntivo, aggiungere tali tag alla riga di comando:</span><span class="sxs-lookup"><span data-stu-id="a8d69-162">To customize multiple tags for an add-in, add those tags to the commandline:</span></span>

```powershell
Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -Hosts h1, 2 -DisplayName "New DocuSign W" -IconUrl "http://site.com/img.jpg" 
```

> [!IMPORTANT]
> <span data-ttu-id="a8d69-163">È necessario applicare più tag personalizzati a un componente aggiuntivo come un comando.</span><span class="sxs-lookup"><span data-stu-id="a8d69-163">You must apply multiple customized tags to one add-in as one command.</span></span> <span data-ttu-id="a8d69-164">Se si personalizzano i tag uno alla volta, verrà applicata solo l'ultima personalizzazione.</span><span class="sxs-lookup"><span data-stu-id="a8d69-164">If you customize tags one by one, only the last customization will be applied.</span></span> <span data-ttu-id="a8d69-165">Inoltre, se si personalizza un tag per errore, è necessario rimuovere tutte le personalizzazioni e ricominciare.</span><span class="sxs-lookup"><span data-stu-id="a8d69-165">Additionally, if you customize a tag by mistake, you must remove all customizations and start over.</span></span>

### <a name="tags-you-can-customize"></a><span data-ttu-id="a8d69-166">Tag che è possibile personalizzare</span><span class="sxs-lookup"><span data-stu-id="a8d69-166">Tags you can customize</span></span>

| <span data-ttu-id="a8d69-167">Tag</span><span class="sxs-lookup"><span data-stu-id="a8d69-167">Tag</span></span>                  | <span data-ttu-id="a8d69-168">Descrizione</span><span class="sxs-lookup"><span data-stu-id="a8d69-168">Description</span></span>          |
| :------------------- | :------------------- |
| <span data-ttu-id="a8d69-169">\<> di IconURL</span><span class="sxs-lookup"><span data-stu-id="a8d69-169">\<IconURL></span></span>   </br>| <span data-ttu-id="a8d69-170">URL dell'immagine utilizzata come icona del componente aggiuntivo (nell'interfaccia di amministrazione).</span><span class="sxs-lookup"><span data-stu-id="a8d69-170">The URL of the image used as the add-in’s icon (in admin center).</span></span> </br> |
| <span data-ttu-id="a8d69-171">\<> DisplayName</span><span class="sxs-lookup"><span data-stu-id="a8d69-171">\<DisplayName></span></span>| <span data-ttu-id="a8d69-172">Il titolo del componente aggiuntivo (nell'interfaccia di amministrazione).</span><span class="sxs-lookup"><span data-stu-id="a8d69-172">The title of the add-in  (in admin center).</span></span>|
| <span data-ttu-id="a8d69-173">\<> host</span><span class="sxs-lookup"><span data-stu-id="a8d69-173">\<Hosts></span></span>| <span data-ttu-id="a8d69-174">Elenco delle app che supportano il componente aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="a8d69-174">List of apps that will support the add-in.</span></span>|
| <span data-ttu-id="a8d69-175">\<> di SourceLocation</span><span class="sxs-lookup"><span data-stu-id="a8d69-175">\<SourceLocation></span></span> | <span data-ttu-id="a8d69-176">URL di origine a cui si connette il componente aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="a8d69-176">The source URL that the add-in will connect to.</span></span>| 
| <span data-ttu-id="a8d69-177">\<> AppDomain</span><span class="sxs-lookup"><span data-stu-id="a8d69-177">\<AppDomains></span></span> | <span data-ttu-id="a8d69-178">Un elenco di domini in cui il componente aggiuntivo è in grado di connettersi.</span><span class="sxs-lookup"><span data-stu-id="a8d69-178">A list of domains that the add-in can connect with.</span></span> | 
| <span data-ttu-id="a8d69-179">\<> di SupportURL</span><span class="sxs-lookup"><span data-stu-id="a8d69-179">\<SupportURL></span></span>| <span data-ttu-id="a8d69-180">URL che gli utenti possono utilizzare per accedere alla guida e al supporto tecnico.</span><span class="sxs-lookup"><span data-stu-id="a8d69-180">The URL users can use to access help and support.</span></span> | 
| <span data-ttu-id="a8d69-181">\<> risorse</span><span class="sxs-lookup"><span data-stu-id="a8d69-181">\<Resources></span></span>  | <span data-ttu-id="a8d69-182">Questo tag contiene una serie di elementi, inclusi titoli, descrizioni comandi e icone di dimensioni diverse.</span><span class="sxs-lookup"><span data-stu-id="a8d69-182">This tag contains a number of elements including titles, tooltips, and icons of different sizes.</span></span>| 
|
### <a name="customize-resources-tag"></a><span data-ttu-id="a8d69-183">Personalizza Tag risorse</span><span class="sxs-lookup"><span data-stu-id="a8d69-183">Customize Resources tag</span></span>

<span data-ttu-id="a8d69-184">Qualsiasi elemento del <Resources> tag del manifesto può essere personalizzato in modo dinamico.</span><span class="sxs-lookup"><span data-stu-id="a8d69-184">Any element in the <Resources> tag of the manifest can be customized dynamically.</span></span> <span data-ttu-id="a8d69-185">Prima di tutto, è necessario controllare il manifesto per individuare l'ID elemento a cui assegnare un nuovo valore.</span><span class="sxs-lookup"><span data-stu-id="a8d69-185">You first need to check the manifest to find the element id to which you want to assign a new value.</span></span> <span data-ttu-id="a8d69-186">Il <Resources> tag è simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="a8d69-186">The <Resources> tag looks like this:</span></span>

```
<Resources>  
    <bt:Images> 
          <bt:Image id=”img16icon” DefaultValue=”http://site.com/img.jpg” 
    </bt:Images> 
</Resources> 
``` 
<span data-ttu-id="a8d69-187">In questo caso, l'ID elemento dell'immagine è "img16icon" e il valore associato è "http:<i></i>//site. <i> </i>com/img. jpg ".</span><span class="sxs-lookup"><span data-stu-id="a8d69-187">In this case, the element id for the image is “img16icon” and the value associated with it is “http:<i></i>//site.<i></i>com/img.jpg.”</span></span>

<span data-ttu-id="a8d69-188">Dopo aver identificato gli elementi che si desidera personalizzare, utilizzare il seguente comando in PowerShell per assegnare nuovi valori agli elementi:</span><span class="sxs-lookup"><span data-stu-id="a8d69-188">Once you have identified the elements you want to customize, use the following command in Powershell to assign new values to the elements:</span></span>

```powershell
Set-OrganizationAddInOverrides -Resources @{“ElementID” = “New Value”; “NextElementID” = “Next New Value”} 
```

<span data-ttu-id="a8d69-189">È possibile personalizzare il numero di elementi con il comando che è necessario.</span><span class="sxs-lookup"><span data-stu-id="a8d69-189">You can customize as many elements with the command as you need to.</span></span>

### <a name="remove-customization-from-an-add-in"></a><span data-ttu-id="a8d69-190">Rimuovere la personalizzazione da un componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="a8d69-190">Remove customization from an add-in</span></span>

<span data-ttu-id="a8d69-191">L'unica opzione attualmente disponibile per l'eliminazione delle personalizzazioni consiste nell'eliminarle tutte contemporaneamente:</span><span class="sxs-lookup"><span data-stu-id="a8d69-191">The only option currently available for deleting customizations is to delete all of them at once:</span></span>

```powershell
Remove-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="view-add-in-customizations"></a><span data-ttu-id="a8d69-192">Visualizzare le personalizzazioni del componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="a8d69-192">View add-in customizations</span></span>

<span data-ttu-id="a8d69-193">Per visualizzare un elenco delle personalizzazioni applicate, eseguire il cmdlet **Get-OrganizationAddInOverrides** .</span><span class="sxs-lookup"><span data-stu-id="a8d69-193">To view a list of applied customizations, run the **Get-OrganizationAddInOverrides** cmdlet.</span></span> <span data-ttu-id="a8d69-194">Se viene eseguito **Get-OrganizationAddInOverrides** senza un *ProductID* , viene restituito un elenco di tutti i componenti aggiuntivi con sostituzioni applicate.</span><span class="sxs-lookup"><span data-stu-id="a8d69-194">If **Get-OrganizationAddInOverrides** is run without a *ProductId* then a list of all add-ins with applied overrides are returned.</span></span>  

```powershell
Get-OrganizationAddInOverrides 
```
<span data-ttu-id="a8d69-195">Se ProductId è specificato, viene restituito un elenco di sostituzioni applicato al componente aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="a8d69-195">If ProductId is specified, then a list of overrides applied to that add-in is returned.</span></span> 

```powershell
Get-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="remove-an-add-in-from-local-cache"></a><span data-ttu-id="a8d69-196">Rimuovere un componente aggiuntivo dalla cache locale</span><span class="sxs-lookup"><span data-stu-id="a8d69-196">Remove an add-in from local cache</span></span>

<span data-ttu-id="a8d69-197">Se è stato distribuito un componente aggiuntivo, è necessario rimuoverlo dalla cache in ogni computer prima che possa essere personalizzato.</span><span class="sxs-lookup"><span data-stu-id="a8d69-197">If an add-in has been deployed, it has to be removed from the cache in each computer before it can be customized.</span></span> <span data-ttu-id="a8d69-198">Per Remive un componente aggiuntivo dalla cache:</span><span class="sxs-lookup"><span data-stu-id="a8d69-198">To remive an add-in from cache:</span></span>

1. <span data-ttu-id="a8d69-199">Passare alla cartella "utenti" in C:</span><span class="sxs-lookup"><span data-stu-id="a8d69-199">Navigate to the “Users” folder in C:</span></span>\ 
1. <span data-ttu-id="a8d69-200">Passare alla cartella utente</span><span class="sxs-lookup"><span data-stu-id="a8d69-200">Go to your user folder</span></span>
1. <span data-ttu-id="a8d69-201">Passare a AppData\Local\Microsoft\Office e selezionare la cartella associata alla versione di Office</span><span class="sxs-lookup"><span data-stu-id="a8d69-201">Navigate to AppData\Local\Microsoft\Office and select the folder associated with your version of Office</span></span>
1. <span data-ttu-id="a8d69-202">Nella cartella *WEF* eliminare la cartella *manifests* .</span><span class="sxs-lookup"><span data-stu-id="a8d69-202">In the *Wef* folder delete the *Manifests* folder.</span></span>

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="a8d69-203">Ottenere informazioni dettagliate su ogni cmdlet</span><span class="sxs-lookup"><span data-stu-id="a8d69-203">Get detailed help for each cmdlet</span></span>

<span data-ttu-id="a8d69-204">È possibile esaminare la guida dettagliata per ogni cmdlet utilizzando il cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="a8d69-204">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="a8d69-205">Ad esempio, il cmdlet seguente fornisce informazioni dettagliate sul cmdlet Remove-OrganizationAddIn.</span><span class="sxs-lookup"><span data-stu-id="a8d69-205">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```powershell
Get-help Remove-OrganizationAddIn -Full
```


